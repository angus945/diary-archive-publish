
# 【學習】專題後面的一些 Shader 紀錄

這篇是專題後面，從頭來過之後的一些 Shader 紀錄。

### 草地

找了現成的 Shell Rendering Shader 來用 [UnityFurURP](https://github.com/hecomi/UnityFurURP)，參考影片

[https://youtu.be/UA3WSTnIH5c](https://youtu.be/UA3WSTnIH5c)

但那個腳本只能渲染純色，我想加一點筆觸或漸變給草地，所以翻出關鍵腳本先給 GPT 分析了一下。GTP 有給一些程式，但試了幾種不太理想就放棄了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_44.jpg)

最後是自己在 fragment shader 加上一些 world position 的筆觸採樣 + 混色。Shell Shader 不像 geometry 或 gpu instance 那種根跟分明的草，比較像毛毯，看起來軟綿綿的。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_8.jpg)

### 傳送門

遊戲的風格偏向夢核 dreamcore，最標誌性的物件是門框，所以遊玩的時候玩家也會透過走入門框前往不同房間。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_19.jpg)

我不想讓玩家「啪」的一下畫面就跳到另一個房間，所以針對穿越做了簡單的 corssfade 效果，有了這個讓穿越房間的手感舒服很多。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_6.jpg)

運作原理就是多一個攝影機保持追蹤和渲染玩家傳送前相對位置的運動和畫面，然後用 RenderFeature 後處理計算過度，覆蓋到畫面上。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_30.jpg)

效果簡單，但實作上還是花不少些心力確保能用在遊戲中，中間也踩不少坑。

像是這個，我發現畫面右上角的亮部會在穿越時然閃一下（突然變暗），這一點小異常就完全破壞漸變的意義了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_5.jpg)

花了幾個小時排查，原本以為是 PostProcessing 導致問題，所以改了 Pass 的執行順序，後來發現是 HDR 打開時才會發生…關掉就沒事了，但會導致很多後處理渲染效果失效。

最後才發現，是因為第二個攝影機的色彩深度不夠，預設建立的 RT 只有 8bit 深度，後來改成最高深度的 32bitFloat 就好了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_38.jpg)

還有其他零碎的排查跟優化就不提了，多了漸變的體驗真的舒服…但不特別講可能沒人會注意到吧 (´;ω;`)

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_2.jpg)

缺點就是 Camera Movement 只能是硬追蹤或固定位置，不能有任何緩動效果，因為兩個 Cinemachine 的運動效果會對不上。

### 鏡子

參考這部影片 [Coding Adventure: Portals](https://youtu.be/cWpFZbjtSQg) 做的鏡子效果，就是用多一個攝影機從鏡子裡面照出來，然後用 RT 渲染在材質上而已。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_39.jpg)

但…後來發現一個蠻大的問題，玩家是用紙片渲染的，但紙片只能朝向主攝影機，這會導致鏡子裡的玩家紙片的方向在鏡中有問題。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_7.jpg)

所以鏡子只能放水平的，至於實際要用在哪…也還不確定，反正是蠻早做了的效果。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_3.jpg)

## 後處理效果 Post Processing

從 URP 之後，查一些自定後處理的資料基本上都是走 RenderFeature，可以寫自己的 Feature，或是直接用官方提供的 Full Screen Pass Render Feature 渲染。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_40.jpg)

至於 Shader 本身可以用 URP 的 FullScreen shader graph 做，也能自己寫 hlsl，寫法不提了，就是畫面處理的基礎知識。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_41.jpg)

這是網路 (主要是 YT) 上能查到最簡單和普遍的做法，但缺點是 Render Feature 會作用在全域，雖然可以在運行中用程式調整參數或開關，但還是不方便調整效果。

不過 Unity 還有另一個後處理方案是 Post Processing Volume，裡面已經預設了不少效果、光暈、混色、景深之類的。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_42.jpg)

最重要的是 Volume 可以在場景裡編輯，你可以根據不同場景或區域設置不同效果，還能有優先度、權重和過度。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_4.jpg)

所以我也花了一些時間研究怎麼把自製的 PostProcessing Shader 整合進 Volume 管線。

翻了不少資料，包括其他 Asset Package 的程式碼、官方的 Unity6 URP 文擋 [introduction-to-urp-advanced-creators-unity-6](https://unity.com/cn/resources/introduction-to-urp-advanced-creators-unity-6) 和跟 AI 雞同鴨講的討論。

幾番折騰後，總算整合出一個自己的擴展框架了。

寫 Shader 的部分就跟平常一樣，這裡省略，而 Volume 的 Editor 介面只需要一個繼承 VolumeComponent 和 IPostProcessComponent 的 class。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_43.jpg)

在裡面宣告 Volume 專用的參數欄位

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_9.jpg)

然後在 class 上面加上 [VolumeComponentMenu]

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_10.jpg)

這樣他就會出現在 Volume Override 的目錄中了，還有各種參數欄位，這部分倒蠻方便的。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_11.jpg)

當然光這樣只是加上 Override 的選項而已，也不會真正渲染，我還寫了一個負責處理渲染管線相關工作的 Render Feature。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_12.jpg)

他會用反射抓在我框架下擴展的 VolumeComponent，然後自動載入 Shader, 生成材質球, 註冊 RenderPass, 讀取 VolumeComponent 的參數，最後渲染效果。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_1.jpg)

有這個框架之後，我就能蠻輕鬆的把各種自己寫或網路上抓的 PostProcessing Shader 整合進 Volume 管線了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_13.jpg)

但我還是優先找現成的搞定，github 分享的免費腳本，或 AssetStore 花錢買 Package 也行，錢能解決的都不是問題，真的不得已才自己寫效果==

專題我就買了一個很讚的後處理包 [\*\*VolFx - VFX Toolkit (Post Processing, Timeline Tracks, Shaders, Tools)](https://assetstore.unity.com/packages/vfx/shaders/fullscreen-camera-effects/volfx-vfx-toolkit-post-processing-timeline-tracks-shaders-tools-300643)，\*\*蠻多效果我就直接用現成的了。不便宜，但各種效果真很完善。

[https://youtu.be/0Byz2CEw-y8](https://youtu.be/0Byz2CEw-y8)

### 踩坑

也是這個實作讓我比較懂 Unity PostProcessing 的運作原理，畢竟過程也踩了一些坑==

基本上，Unity 場景上的 Volume 都是添加「效果的覆寫」(Add Override)。

為什麼是覆寫? 因為他會有某個預設的配置存在，就是 DefaultVolumeProvile，這玩意會偷偷的藏在你的專案資料夾裡。

DefaultVolume 會儲存「所有」後處理效果的預設參數，而你在場景添加的 Volume 就會覆寫他們。

在不清楚這個 Default Volume 存在的情況下，我以為把 Volume 上面的 Toggle 取消掉代表「關掉」這個效果，但其實不是，關掉只代表不覆寫參數，使用 Default Volume 中的預設值。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_14.jpg)

踩到的坑就是，我不知道為什麼 PostProcessing 的效果一直開著，明明我把他「關掉」了（至少我以為是關掉）。

花了不少時間排查，檢查我的 Component 腳本、檢查 Shader、檢查 Render Feature, Render Pass 有沒有寫錯。

後才發現這個 Default Volume 的存在，還有我的 Volume Component 的預設參數跑掉了之後，才懂他的原理。

簡而言之，如果你發現某個 PostProcessing 效果關不掉，可能是動到 default volume 了 ==

### 踩坑 2

我的 PostProcessing 框架運作良好...直到 Build 後，遊戲直接黑畫面，只能看到 UI。

幹又是這種超他媽難排查的 Build only bug。

總之，我先先簡單加了一個開關各個 pass 的測試腳本，以為是我的 post processing pass 腳本執行時會出錯，產生某種 render target unclear 導致的畫面重複疊加。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_15.jpg)

但其實不是，只是我好死不死用有問題的效果測==

進一步排查發現是我手寫的 Shader 效果在我的框架上 Build 時才會有問題，如果用 URP 預設的 Feature 渲染正常，而且 Unity ShaderGraph 的 FullScreenShader 在兩者都運作正常。

用條列的可能比較好明白：

- ShaderGraph + 我的框架 = 正常
- 手寫 Shader + 預設 RenderFeature = 正常
- 手寫 Shader + 我的框架 + Editor 環境 = 正常
- 手寫 Shader + 我的框架 + Build 後 = 黑畫面

就真是見鬼了，後來我翻了 ShaderGraph 生成的腳本，發現他有兩個 Pass，DrawProcedural 和 Blit。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_16.jpg)

然後也去翻了 URP 預設 FullScreenPassRenderFeature, RenderPass 的腳本，發現他的關鍵渲染函式裡面用 DrawProcedural，透過渲染 Mesh 的命令渲染。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_17.jpg)

但我的自定 Pass 是走 Blit 命令。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_18.jpg)

而那個手寫的 Shader 是網路上找 + 自己修改出的模板，他的 Vertex Shader 他是針對 DrawProcedural 的計算。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_20.jpg)

所以在預設 Feature 下能正常渲染，但在我的框架下會有問題…至於為什麼在 editor 能正常渲染就是個迷，照理來說 editor 也應該有問題才對。

最後，一番思索下解決方案大概有三種。

1. 重寫整個框架，也改走 DrawProcedural
2. 改 Shader code，多加一個 BlitPass
3. 改成用 ShaderGraph

方案一的成本太高、方案二我找不出怎麼寫==

所以最後只能三，把關鍵計算轉移到 chginc 腳本，用 ShaderGraph 的 CustomFunction 調用。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_21.jpg)

然後修的過程還發現 VolumeComponent 裡面的 Active 判定都寫錯了== 有些不該啟用的 Pass 一直開著，才導致一個有問題的效果炸爛整個渲染。

這段讀下來可能花三十秒，但我用了一整天排查才修好==

## 局部後處理

針對特定物件、特定 Layer 的後處理，原本弄這個是因為我想做後處理的邊界混合效果…嚴格來說是我看到現成的 code，但只支援 Unity6 的 Bulit-in 管線，所以我想研究怎麼魔改讓 URP 能用。插件是這個: [Mesh Seam Blending](https://assetstore.unity.com/packages/vfx/shaders/fullscreen-camera-effects/mesh-seam-blending-326839)

比起 PostProcessing 框架，這才是真的麻煩。

因為 Unity6 URP 的資料太新， Copilot 的 auto suggestions 和 GPT 都是各種胡言亂語。

至於網路資料，我找到有用的只有這兩個，教怎麼在 URP 繪製物件的文擋 [Draw objects in the render graph system in URP](https://docs.unity3d.com/Manual/urp/render-graph-draw-objects-in-a-pass.html) ，還有一個 Unity 6 RenderFeature, RenderGraph 的教學。

[https://www.youtube.com/watch?v=U8PygjYAF7A](https://www.youtube.com/watch?v=U8PygjYAF7A)

總之，URP 相關的自定 Pass 管線大改，之前版本的資料都過時了。一些小設定搞錯可能就完全無效，或天差地遠，要排查幾小時。

我還去翻了 Unity URP 本身的腳本，看別人的程式真的是最低效率的學法…但走到什麼資料都沒有的時候就真的只能翻原始碼參考了

……

好吧我不全是靠自己翻，我是找到相關的原始碼丟給 GPT 要他幫我看。如果是範例腳本還好說，但那些實際引擎的 API 要兼容一堆東西真的又臭又長。（後來才發現 URP 有 Sample 可以下載==）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_22.jpg)

也嘗試讓 GPT 生腳本，但基本上還是得自己一步步排查、除錯。光是想把指定物件渲染進 TextureHandle 就花了半天，然後再花半天研究怎把 TextureHandle 傳遞進其他 Pass 。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_23.jpg)

截圖做紀念，但對你們來說沒意義就是了，是我的測試而已。簡單說左邊那張是第一個把指定 Layer 物件渲染進 RT 的 pass，右邊是另一個 blit pass,，用負片方便確認效果，如果沒成功的話會是全黑的。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_24.jpg)

花了一堆時間把管線工作處理好了…但把 Shader 套上去後發現沒效==

哭阿

而且這玩意還很不穩定，容易把整個渲染管線炸掉

最後還是拋棄了，直接刷了相同作者做的 pro 版 [Mesh Seam Blending Pro](https://assetstore.unity.com/packages/vfx/shaders/fullscreen-camera-effects/mesh-seam-blending-pro-330717) 。真的，錢能解決的都不是問題==

## 光照問題

專題遇到的問題，因為遊戲的關卡是用無縫？轉場的，就是關卡之間會有個中繼的房間，玩家進入後會卸載上一關、載入一下一關。

問題就在，主光源 (Directional Light) 放在關卡中，所以中繼房間卸載關卡時會發生突然沒光的情況，直到下一關的光源載入。

為了解決這個也是東摸西摸了一番，然後發現渲染設定中有個 Rendering Layers 的功能，可以指定哪些物件受到哪些光照 (Layer) 的影響。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_25.jpg)

打開 Use Rendering Layer 後，就會把 Physics Layer (預設的 Layer系統) 跟 Render Layer 分開，可以到 Tags&Layers 設定有哪些光照 Layer。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_26.jpg)

這樣我就能在轉場場景加一個自己的 Light Source，只要把場景的物件區分不同 RenderingLayer 就好，讓多個場景的多個光源不互相影響。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_27.jpg)

但…這設置起來很麻煩，妳得針對每個 MeshRendere 手動（或寫腳本自動）設置 Layer。之前就疑惑，為什麼 Unity 要把 Physics layer 跟 render layer 共用，現在能理解了，因為設定起來很繁瑣==

而且我後來也發現，就算能用 RenderLayer 區分 directional light 的光源，shadow map 還是只會針對一個光原生成陰影。

所以最後放棄，還是用一個全域共用的光照場景共享 Directional Light，完美解決所有問題。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_28.jpg)

## 程式

程式部分都做差不多了，最後就剩遊戲流程，我參考阿星的流程控制系統做了一套。沒記錯的話，他的流程分層四層，階段 Phase, 序列 Sequence, 步驟 Step 和實際的行動 Action，我也是直接參考這套。

[https://youtu.be/Q4BQAJLzqt0](https://youtu.be/Q4BQAJLzqt0)

流程的實際行為都是靠最下層的行動構成的，每個行動只做單一行為，載入場景、等待場景、延遲、觸發轉場、等待轉場。這樣的好處是某些相同的行動可以定義一次，然後在不同流程中重用。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_29.jpg)

然後透過 Builder Pattern 把流程建立出來，基本上就是定義各種階段、步驟以及最下層要執行的行動 Action。分多層的意義是可以方便跳到某個指定的點執行，但專題沒這個需求就先 pass 了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_31.jpg)

反正就是把遊戲循環會有的各種流程建立出來，進入關卡、重置關卡、返回主畫面等等。然後流程管理器只要在對應時機切換到不同的流程，流程內部定義的行動就會逐步跑完。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_32.jpg)

## 模組化

專題程式告一段落，應該不會有什麼新的系統了，也開始把這段時間寫的程式整理起來。

首先是整頓 github，把自學期間的一些學習專案、GameJam、大二跟同學玩的一週專案、沒任何留言的個人網站的留言板都刪除了，一口氣清了十幾個 repo。專題、產學相關的會暫時留著，等畢業後一段時間再看怎麼打算吧。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_33.jpg)

然後我建了一個模組包的主專案，把專題或更之前留下的、可能派的上用場的程式碼統一整頓。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_34.jpg)

其實蠻多設計失敗、過度設計的模組都被刪了，像專題前期的那些（而且那時還沒摸熟 DDD），或是一些超老，以前覺得不錯但現在看來不值一題的程式，或是一些專案性過強，沒什麼重用價值的也清掉。

剩下的像是 EventBus, Logger, DI, Time 之類的 Platform Infrastructure ，之後每個專案幾乎絕對會用到的基礎設施。

還有一些常用系統，流程控制、存讀擋、對話系統、Unity 場景管理和工具、文章上面說到的 PostProcessing 框架、還有近期研究的一些 AI 工具就會整理成工具包。

最後拆成幾個不同的 git submodule 各自儲存，須要就當插件插進 Repository 中。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_35.jpg)

我也想過用 Unity 的 UPM Package 格式，能更方便的跟 Unity Package Manager 生態整合，不過他有自己要的求資料夾結構，但我想維持自己的 DDD 架構所以就算了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_36.jpg)

我也想過用 CICD 的方式生成 Package，這樣就能維持我喜歡的樣子開發，並兼容 UPM 生態。

但但又有另一個問題是，我的模組化程式包現在還不完善、不穩定，如果走 CICD 的話沒辦法在應用專案中同時擴展、修改或維護，必須回到模組包的主專案修好 Push > CICD Build > 應用專案 Updte 才能更新。

所以想來想去，還是原始的 Submodule 好，我可以給每個專案添加一個 branch，等某時要整合再回主專案 merge。

但但但問題就變成 git 操作本身很煩瑣了，每個 submodule 發生修改的時候都得獨立做一次 commit, push。

原本想寫一套輔助管理 Submodule 的工具，理論、技術跟現實上都是可行的，不過寫著發現那程式真是又臭又長。

同時又想到最近一直在研究怎麼讓 Codex CLI 用起來更方便，還做了個輔助工具，於是直接測試能不能把管理 Submdule 的工作交給 AI。

顯然，完全可以，無論是檢查缺失、導入指定的 submodule 或是自動 commit, push 所有模組的更動到指定分支上都沒問題。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_45.jpg)

天阿我還寫什麼工具，用 AI 不香嗎，一個月六百就是花在這的，而且還能自動處理各種例外狀況，修正路徑錯誤或啥。

就醬

至於這些程式包…目前還不打算把他們公開，未來也不確定，可能選擇性會公開 (開源) 某些，可能也不會

就以後再說吧 ¯\*(ツ)\*/¯

順帶一題，不知道有多少人注意到 Fork 有新年彩蛋ww

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2026/post-2026_02_28-learn-stust-project-shaders/image_37.jpg)
