
# 【學習】自動化、MCP 和 Vibe Coding

---

AI 玩意也更新太快了吧，資訊從我開始寫到發文都更新不知道幾輪了==

## TGDF

今年也有去，懶得整理筆記但還是寫進來紀錄。筆記可以到 [Notion](https://www.notion.so/TGDF-22b64707f2db80ef964cca3301a822fc?pvs=21) 看，但很零碎就是了。

這次只提印象最深的一場：為《九日》而研發的狀態機架構《MonoFSM》。印象深的原因是內容蠻出乎意料的，關於九日中的狀態機架構。

他們的行為狀態機都是用 Prefab 組裝的，動畫也是直接在 unity time animator 上做。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_59.jpg)

就是...emm…沒想到會用那麼樸素的方式，但有效，而且效果很好，這樣做的好處是物件的狀態能從 Hierarchy 直接看到，而且非程式人員也能除錯，甚至直接用 Prefab 組裝物件行為。

老實說蠻衝擊的，因為我在之前一段時間中其實蠻癡迷讓程式碼擺脫對 Unity 的依賴，想要純 C# 搞定一切，而且還有點走火入魔。

所以聽完演講讓我改變蠻多想法，或許依賴 Unity 會有一些限制，但重點是能做出、做好東西，畢竟工具在那邊不就是拿來給你用的嗎？

之後畢專的程式寫法應該會有一些改變，也不是就要回到以前的做法，就是更知道怎麼權衡了吧。

## 更多自動化

**※知識庫**

其實沒什麼新東西，就稍微題一下。原本搬運還想說把舊的筆記都分類放好，但最後後來決定通通丟進封存區，裡面不少超舊的筆記真的用不太到了，反正知識庫的文件是流動的，等需要什麼文件再從封存庫拿回其他區域就好。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_5.jpg)

改成這樣後寫一些東西感覺也自在多了，我在 Notion 寫東西的時候其實會有一種怕被看到的顧慮，雖然單純是心裡因素造成的？

因為我 Notion 會到處打開來用，電腦、手機或在學校都會開，太方便就有種不安全感。

但這個知識庫基本上只會一個人、在家裡用電腦寫，加上現在的分類方式中 Project 與 Area 本身就是偏向隱私文件，所以寫一些東西也會更誠實，對未來真正的想法，或一些自我觀察之類的。

然後 Notion 現在出離線版了，謝了噢 (´・ω・`)

**※日誌保存**

上篇【學習】有提到我用 AI 搞了一些 Notion 轉換工具，這次也是接著搞，但搞的是日誌的備份。我現在的日誌也都是在 Notion 寫的，不過每篇寫完後就不會碰了，放在表格裡，還有一些 Notion 前的小屋重要文章也被我複製到表格保存。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_2.jpg)

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_17.jpg)

比較長的累積到現在也要一百五十篇了，前陣子弄知識庫的時候就有考慮把日誌也轉移到知識的封存區，目的之一也是轉移長期留存的位置。

還有想辦法減輕 Notion 的負面影響，他寫文很方便沒錯，但 Notion

真的

很

慢 !!!!

那篇六週年的文我光打開就要花超過十秒，然後文件量多了之後 Table 也很卡，有時操作功能還會壞掉，像 Toggle 按不了之類的==

**※子模組 Submodule**

為了方便管理，我沒有直接把日誌丟入知識庫的 Repo，而是另外建了兩個，日誌封存 (diary-archive) 和日誌貼文封存 (diary-archive-posts)。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_28.jpg)

diary-archive 是整個封存系統的主專案庫，包括一些轉換工具和日誌的圖片，diary-archive-posts 則只用來存日誌的 md 文字檔，透過 git submodule 附加在主專案庫下面。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_39.jpg)

把 md 文件獨立庫存後，我也能用相同的 git submodule 手段把日誌嵌入知識庫中，但不用連超大量的照片圖檔都同步過去。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_50.jpg)

轉換工具也只放在主專案庫，功能跟上次差不多，就是用 Python 批次把 Notion 導出的日誌和圖片重新命名、放到對應路徑，然後替換文件中圖片嵌入的 URL。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_55.jpg)

一樣是靠 ChatGPT Vibe Coding，自動化的 python 腳本我一行都沒寫。

前幾版的功能都寫在同一個腳本中，後來為了方便維護（方便 AI 維護）還是想拆成多個腳本。但 ChatGPT 不太能處理，所以這次改用 Gemini CLI 重構。

效果蠻不錯的，他還會先計畫過才問我要不要開始。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_56.jpg)

然後就是給他修改專案資料夾和執行 cmd (shell) 命令的權限，他就一次幫我重構，然後我在執行確認結果正不正確，不像用 GPT 我還得手動複製貼上測試。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_57.jpg)

後面我也有嘗試用 Copilot 的 CHAT 功能修改效果，感覺效果差不多，但介面比 Gemini CLI 的 CMD Terminal 好多了，而且他還會幫我執行腳本測試效果（如果要求 Gemini CLI 的話應該也會）。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_58.jpg)

這也是我第一次用 Copilot Chat 的新的 Agent 功能 ，之前都只用 code complete 輔助，還有 Inline Rewrite 功能而已。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_7.jpg)

最後就讓他們幫我補齊剩餘功能，建立子資料夾、重新命名前綴、壓縮圖片之類的就差不多了，現在日誌也有 github repository 儲存。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_8.jpg)

Copilot 執行命令時，預設會需要使用者每次都做授權，如果嫌麻煩可以到設置調整成預設同意。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_60.jpg)

**※發佈格式轉換**

但這次除了留存，另一方也是想解決圖床跟發文的效率問題。

Imgur 現在不能用，好像會擋臺灣 IP ，前陣子找了一些替代但效果或操作上都不太方便。再來就是發文效率，雖然文是先在 Notion 寫好，但每次上傳圖床 + 搬運到巴哈可能要快一小時。

對，光轉發就一小時。

因為不能直接整篇從 Notion 複製，然後貼到巴哈上，會有跑版跟圖片嵌入問題，所以我都是一段一段複製，上傳圖床，然後手動插入圖片的…一小時。

雖然一個月只要一到兩次，但重複動作還是很煩==

所以我把巴哈編輯器的文章原始碼給 GPT 看，要他寫一個轉換腳本。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_9.jpg)

然後就是手動除錯 + 補充我要的功能，例如指定輸出的資料夾、清單顯示、**粗體**_斜體_~~刪除線~~（底線沒辦法）、圖片嵌入、大中小標題，以及把換行風格改成我常用的樣子。

還有限制圖片高度，巴哈的圖片嵌入其實可以加上 height= 來控制顯示高度，之前很多長寬比太大的圖片都是我動填參數調整的，避免一張圖佔光（電腦版）閱讀版面。

像這樣：[img=URL height=350]

然後把轉換完的文字和圖片用我要的格式放進另一個用於發佈的 submodule，Push 到公開的 github repository 就能當圖床用了。（其實我個人網站的文章就是這樣做）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_10.jpg)

圖片也是 github 的公開網址（如果 Repo 是公開的），能直接訪問跟嵌入文章，像這樣：
[https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_07_01-travel-philippines_trip/image_1.jpg](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_07_01-travel-philippines_trip/image_1.jpg)

最後我只要把生出的原始碼貼整段到巴哈就行了，擺脫重複工作，從遊記那篇開始我就是就是用這種方式發的，你們正在讀的則是新方法的第四篇。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_11.jpg)

改成這樣的優點很多，不用外部圖床、不用手動上傳到圖床、不用手動一段段搬到巴哈。但缺點嘛…就是如果我動到資料夾結構就會讓所有圖死光光 www

菲律賓那篇我就改了兩次結構，所以發文後其實重貼了幾次，但之後應該不用再改了。

應該啦。

上面兩段算超級輕描淡寫了，過程也發生過不少意外，像 AI 意外刪除某些東西、清除 submodule 的 git 資料之類的，強烈建議用任何本地 AI 之前一定要多做手動的雲端版控。

對，讓 AI 操作的空間最好都有「雲端」版控在，只存本地小心他連整個 .git 資料夾都給你揚了。

然後什麼叫做你看漏了阿 ==

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_12.jpg)

除此之外還沒遇到什麼問題吧，這段時間用 GPT, Gemini CLI 和 Copilot 的 Python Vibe Coding 體驗還算不錯。

但要用到 Unity 就比較麻煩了，涉及引擎之類的外部工具，然後程式碼架構跟規模也會大很多，之後（文章後面）再試試看效果。

總之日誌封存東西應該就到這，把一小時的重複動作縮短到五分鐘已經很夠了，除非未來我要在幾十個平台同步發文，不然也沒必要多弄啥自動發文機器人。

## MCP

對 MCP，這玩意出現也幾個月了，暑假期間我也嘗試摸了一下，主要也是 Unity 的。使用的是 [unity-mcp](https://github.com/justinpbarnett/unity-mcp) ，有興趣的可以參考這篇文 [\*\*Unity MCP 架設方法](https://www.unityflow.dev/unity-mcp/)，\*\*這裡就不教學了。

總之 MCP（Model Context Protocol） 是一種讓語言模型跟各種玩意溝通的協議，透過他就能讓你的 AI 操作其他各種軟體，包括 blender 或 unity。

Youtube 上也有一部用 MCP 做出開車遊戲的縮時影片，蠻有趣的，可以去看看。

[https://youtu.be/Wr2QiA7FqcE](https://youtu.be/Wr2QiA7FqcE)

[https://youtu.be/Wr2QiA7FqcE](https://youtu.be/Wr2QiA7FqcE)

查不少資料，好像大多 Unity MCP 都是用 Claude 做的。

我沒訂閱 Claude，但翻文檔發現它也直接支援 Copilot（Gemini CLI 應該也可以，但要做一些手動配置）。總之導入 Package 後打開面板，按下 Auto Config VScode with GitHub Copilot 就自動完成配置了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_13.jpg)

註：後來發現免費 claude 也能 MCP，只是容易撞到限制。

然後開 VSCode 的 Copilot Chat Agent 叫他幫我生出一個 cube，於是他讀了場景文件，然後把 cube 資訊寫進文件中。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_6.jpg)

欸不對，MCP 好像不是這樣運作的==

後來我把連線斷掉，做一些實驗後發現 Copilot 是用 VSCode 本身提供的權限訪問場景資料，然後用文字編輯的方式建立 Cube，沒經過 MCP。

後來釐清區別，指定 Copilot 使用 packge 中提供的接口後，他才知道正確的做法。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_14.jpg)

正確的執行應該會在 terminal 中執行這種命令，成功就可以讀到 Unity Editor 的各種資訊，包括資料夾結構、場景、Debug Console 和編輯器的狀態（像是否為 Play Mode）。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_15.jpg)

然後我丟了一個場景需求單給 Copilot，他就依照需求單幫我生了物件在場景。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_16.jpg)

但 Hierarchy 完全錯，他全部生在場景 Root 底下，但需求單中是有子父層級的。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_18.jpg)

我要他修正層級問題，但卡了好久都沒成功，調用一堆命令或寫一些程式後都無效，VSCode 直接跳出提示要我重試。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_19.jpg)

後來是叫 Copilot 去「看清楚」原始碼中有沒有提供修改方式，找到正確做法後就成功了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_20.jpg)

但建好物件後，又發現物件底下的 Component 缺東漏西，可以在要 Copilot 補上，但添加 Component 又要進行超多次的 MCP 命令調用。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_21.jpg)

調用很多次命令會怎麼樣？

你的 Token 用量會消耗很快，比一般的 Vibe Coding 快很多，因為這個 Unity MCP 讓 AI 跟 Untiy 溝通的資訊格式是 Json。

除了調用 MCP 的方式是透過 Json 打包參數的命令之外，Unity 回傳的資訊也是 Json。這是一次場景物件資訊請求的命令（有顏色的部分），以及取得上面那個場景後回傳的資訊（白色部分）。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_22.jpg)

Copilot 讀完場景資訊，發現物件內容跟清單要求不符後（因為我刪了東西），又執行了幾個命令把物件加回去。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_23.jpg)

然後再讓 Unity 回傳一次場景資訊，這「場景」甚至不包含任何美術物件。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_24.jpg)

這樣一來一回，就花了我 Copilot 用量的 0.3% ，我不確定申請的學生版用是給什麼方案，但至少是 Pro 以上的（每月 10 USD）。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_25.jpg)

到這裡大概花了一天研究吧，不算難，我也要 Copilot 生一個幫後續 Agent 能快速理解狀況的 prompt 文件，讀完這個就能直接跳過上面的各種試錯環節了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_26.jpg)

至於感想嘛……要用是絕對可以，只是有幾個難題在。

第一就是**冗餘資訊**太多了，原始命令提供的是泛用的資料讀寫方式，會回傳很多當前情況不需要的資訊，要是場景結構更「真實情況」一點，用不了多久 Token 用量就榨乾。

當然，如果打算直接升級 AI 的訂閱方案就可以忽略。（但餵太多無關資訊還是會汙染 Context 就是了）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_1.jpg)

第二就是需求描述的問題，上面 YT 影片雖然蠻有趣的，但也只是讓 AI 隨意發揮，並不是實際生產環境會遇到的情況。

要讓 AI 照自己的意思建立場景也不容易，需要有非常——非常具體的規格文件，因為她不像我們一樣有 Unity Editor 的基本「操作」常識，而且（至少目前）也用不了 Unity 集成很多功能的 GUI，只能透過純文字命令做一步步的動作。

那麼具體的規格文件不太可能讓人寫，成本會比直接搭場景還高 N 倍，可能要讓另一個 AI 生，所以 Unity MCP 可能會在某個 AI 流水線的下游。

第三就是 MCP 的場景編輯也沒辦法涉及美術工作，因為很顯然 MCP 「看」不到場景的美術樣貌，而大語言模型也沒又真正意義上的美學概念（LLM 只有語言概念，其他形式的資料都會轉換成語言形式才能訓練）。

所以這樣算下來，比較合理的使用情境＆條件應該是：

- 要優化 MCP 命令的輸入輸出，讓傳輸的資訊有更高針對性、更緊湊、精準
- 要有某個 AI 流水線的上游生能出非常具體的場景物件規格書
- 用在白箱測試（_white_-_box_ testing）的原型階段，不涉及任何美術內容，或是用在不涉及美術的物件設置需求。

**※修改 MCP 命令**

隔天，我花了整天嘗試修改或擴展 mcp 的命令，希望在不碰原始碼的情況添下加一些自訂命令，但都失敗了，要嘛是得 focus unity 介面才能觸發動作，不然就是讓 Copilot 的 MCP 命令變的更冗長，本末倒置。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_27.jpg)

反正非常規的修改擴展方式失敗了，要就只能改原始碼，因為他的命令是直接寫死的，不是自動註冊，也沒有提供從外部註冊的接口。

（聽說有某些能攔截編譯然後插入程式碼的方法，但我沒學啦。）

進一步研究原始碼，發現裡面還藏了另一份 python server 的系列腳本，蠻疑惑的，因為用 package manager 導入時沒有出現在 Unity 中。

但後來做了一些實驗和重構，發現那好像是用來定義 mcp 接口的腳本，會自動載到本機 appdata 中，所以如果只改 C# 部分的話會出問題。（也難怪不能自動註冊）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_29.jpg)

放棄，純 C# 還好說，但 python 就真的沒轍，看來要魔改 mcp 的玩意是遠超我能力範圍了，所以第一個情境是解決不了了，只能靠其他大神。

token 問題就…要嘛鈔能力，要嘛白嫖 claude 的免費用量吧。

## AI 教材

反向工程再進一步，上次有提到可以把其他遊戲的程式反編譯給 AI 分析，這次嘗試用了 ChatGPT 的深度研究功能製作客製化教材讓我學。

我先把自己的幾個 Repo 給 GPT 做第一次深度研究，做出一份當前能力的評估報告。但總覺得被 GPT 吹的有點高，有些蠻常識的點也被列出來，應該要他用更嚴苛的標準才對。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_30.jpg)

然後我拿能力評估報告 + 拆包出來的 Rimworld 的原始碼（和另一份 Rimworld 模組技術分析總結）給 GPT 做第二次深度研究，規劃出一個多階段的學習路徑規劃。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_31.jpg)

然後再拿路徑規劃做第三次（和後面 N 次）深度研究，做出各章節的具體教材，以及針對疑惑點做出補充教材，帶有小數點的就是補充教材。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_32.jpg)

這份教材 + 實做真的讓我學到不少東西，但篇幅問題就不全寫了，只紀錄一些重點片段。

但澄清一下，GPT 能生那麼多內容其實不是因為看原始碼，而是他去找 Rimworld 的 Wiki 才能寫那麼詳細的，Rimworld 官方就提供有很具體的教學了，GPT 比較像針對我的需求摘要而已。

**※載入**

有些知識之前就學過了，像資料驅動、反射之類的，我也根據教材實做了一個 XML 定義檔載入框架，還有透過反射載入外部 dll 行為過展的方法。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_33.jpg)

dll 是透過 Visual Studio 的 C# 類別庫建立的，可以建立一個專案，讀取 Unity 專案的 Assembly-CSharp.dll 引用 Unity 專案的程式庫，編寫外部類別庫後建置成一個獨立的 dll。

研究環境設置也花了不少時間，版本調半天一直出問題，結果是選錯東西== （感謝 Rimworld 模組大大青葉協助。）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_34.jpg)

另外是一個 Unity Domain Reload 的坑，Unity 有個設定可以關閉每次進 Play 前的 Reload Domain，為了省時間我現在都關掉了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_35.jpg)

沒有 Reload Domain 會造成一些 static 變數沒被重置，算是一個隱藏的坑，之前看放肆大大好像也踩過 ww

而我這裡踩到的則是 Assembly.Load 的坑，載入的外部 dll 不會在退出 Play 時自動卸載，而進入 Play 時如果之前已經載入過也不會重新載入一次。

所以就導致如果沒有 Reload Domain，重新 build 的 dll 也不會被正確載入，

解決方式就是讓 AI 寫一個檢測 dll 檔案有沒有更新，然後自動觸發 Reload Domain 的 Editor 腳本，還有加一個手動 Reload 的 MenuItem。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_36.jpg)

**※Harmony**

之前就很好奇 Rimworld 是怎麼讓模組能直接覆寫遊戲本體的功能的，這次讀教材 + 實做也總算搞懂了，主要是靠一個叫 **Harmony** 的程式碼補丁函式庫做到的。

這玩意有個 Prefix, Postfix 功能，能夠在「任意」Public 函式的前後插上補丁程式碼。

範例像這樣，我有個 public InitNewGame 函式會 Print 一段訊息，然後遊戲初始化會載入 harmony Patch，他會自動找所有有 HarmonyPatch Attribute 的 static class 補丁，把裡面實做的 Prefix, Postfix Patch 到指定目標上。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_37.jpg)

這裡就是用 Postfix 打上的補丁後綴 log 訊息。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_38.jpg)

還有前綴 Prefix，他可以回傳一個 bool 代表要不要繼續執行其他 Prefix 以及原始函式，用這種方式就能完全跳過原本的程式碼。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_40.jpg)

這什麼神器！！！？？？？？

原始碼不用特別給每個功能提供什麼接口，只要有載入 dll 和補丁的方式就能讓 Modder 直接修改、攔截或覆寫原始的遊戲功能。

感覺大腦在星爆。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_4.jpg)

她還有更進階的 Transpiler ，能透過修改 Intermediate Language 達成精確修改原始程式碼某個片段的功能，但太複雜就先不碰了。

**※測試**

實做的模組框架中有定義檔的載入流程，包括載入 XML、驗證、合併文件、繼承資料、補丁操作，大多腳本我也是讓 AI 寫的（GPT, Copilot, Gemini 混用），然後自己進 Play Mode 測試看 Inspector 顯示的結果對不對。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_41.jpg)

但測試用的 XML 都超長，處理流程又有好幾部，每次都從最終結果看超難除錯。直到某刻開始無法維護，一直測不出定義檔繼承錯誤的原因，讓 Copilot 修了 N 次還是失敗。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_42.jpg)

過程中看到 Copilot 為了測試，寫了一堆暴力玩意檢查繼承效果對不對，然後用 Debug.Log Print 出來。

雖然還是沒修好，但倒是給了我新的方向，是時候回去學單元測試了！

一樣過程就不具體講了，總之我重看了 RStar 大大的單元測試影片，然後加上一段時間的嘗試後，也讓 AI 幫我寫了對各個系統的測試。（對，當然還是給 AI 寫）

[https://youtu.be/DD7cuSGvu98](https://youtu.be/DD7cuSGvu98)

[https://youtu.be/DD7cuSGvu98](https://youtu.be/DD7cuSGvu98)

也是寫測試後發現原本流程跟架構還有些問題，所以又重新開始，但這次就直接把功能做單元測試，每個部分直接 Run 就能發現問題，不用一個個手動檢查了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_43.jpg)

過程遇到最坑的 Bug 是除錯資訊沒有正確 Print，我測試中有包括檢查 Logger 有沒有正確 Print 指定的訊息，但就遇到個詭異的情況，定義檔覆寫時應該要報錯訊息，但沒有報，但定義檔的內容又有被正確覆寫。

後來才發現是 IEnumerable + Remove + Linq.Any 導致覆寫有正確執行但回傳 false，所以上層把 logger 資訊拋棄，才導致測試不通過。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_44.jpg)

後來是加上 ToList 修好的，幹這 bug 要是沒單元測試誰會注意到啦==

現在是先生出程式才寫測試的，多少有點先射箭再畫靶的嫌疑，等之後更熟悉說不定能往 TDD 學？

## 心得

這次的心得要寫更長一段了，這四個月（兩篇【學習】期間）用 AI 工具做了不少東西，讓我發現自己可能也要重新思考自己應該花時間在什麼事情上。

備註一下，後續心得都是針對 AI 寫程式噢，其他用途這裡不討論。還有 AI 的東西真的更新太快了，有些心得可能等我發就過時了，所以也提醒一下這些是過去兩個月累積的內容，不是月底才一口氣寫的。

**※轉變**

大量接觸 AI 後對我影響蠻大的，前陣子有研究說使用 AI 的學生大腦活躍度較低，或是導致大腦退化之類的，不知道你們怎麼想，但我蠻認同這個結論。

畢竟大腦總是會走耗能最小的路徑。

AI 寫程式是快，但總覺得看那些生成的程式碼時，知識更難進入自己的大腦，尤其是由本地 Agent 直接寫入專案的程式。

而且，老實說我也能明顯的感覺自己的大腦發生什麼變化了，很難形容，就是某些思考迴路好像很難再走了，或者說感覺大腦很不想再走那些舊路。

~~就是一種嚐到賭博甜頭後沒辦法在用正常手段賺錢的概念~~

**我能明顯感覺到自己動手寫或構想某些程式時動力減少很多**

但我也同時在想，這真的是壞事嗎？

是我真的怠惰了，還是其實沒必要窮忙？

**「因為實際上，不只有效率差異，AI 的程式也真的能寫比我還好。」**

我指的不是「幫我寫一個賽車遊戲」這種寫，而是 「我想要把 DefinitionInstanter 的各種 type 的 deserializer 分離，然後用反射自動抓取對應的 deserailzier」（然後加上整份 md 的 Agent 角色扮演提詞）這種情況。

大多時候， AI 表現不好是因為連我自己都還不清楚要做什麼。

重構是 AI 表現最好的工作，因為原本的程式碼就表達了你想做的事，比起聽我描述， AI 看程式了解意圖可能更準確，只要加一些關鍵字 AI 就知道要怎麼改了。

而像是前面的 Python 自動化腳本 Vibe Coding，因為範圍很小 + 不用維護 + 不用考慮效能或其他限制，所以讓 AI 生出我完全不懂的程式也沒差，只要運作結果符合預期就好。

不過涉及比較有規模的遊戲開發時，可能就沒辦法讓 AI 生出能有更長期維護效益的程式。

…至少我原本是這樣想的。

但對 SOLID 概念更清楚、接觸單元測試後發現好像又不是問題？

AI 寫出的程式碼品質是取決於自身能力的，而且可以「稍微」超出我的能力邊界一點點，在上面那個 Rimworld 模組架構的研究中我碰到不少根本沒聽過的東西。

GPT 現在還多了個學習與研究，算低配版的深入研究？在遇到那些新東西時，我就讓 GPT 給我解釋或用深入研究寫一份補充教材，讀完（和實做完）之後那些東西也進入自己的能力邊界了。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_45.jpg)

而除錯部分，有單元測試也讓 AI 很好排查錯誤（應該說讓所有人都好排查），因為測試能提供很具體的資訊，只要把錯誤訊息轉給 AI，他們幾乎一次就能修好問題。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_46.jpg)

總之這些嘗試讓我發現，AI 的能力絕對比自己還好，只是我有沒有辦法發揮而已。

因為我的能力邊界（知識邊界）就是使用的 AI 時的表現上限，跟團隊合作中的木桶理論相同，但短板是使用者自己，而非 AI。（除非已經踏入最前沿的領域了）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_61.jpg)

當 AI 寫出超出自身能力範圍的程式碼時，出錯自己就沒辦法排查問題，雖然能交給 AI 修，但也可能發生 AI 花半天也找不出問題的情況，這樣就真的沒人能修 bug 了。

給 AI 除錯只是省時間而已，當 AI 也解決不了問題（或開始失控）時就得自己接手。

但能給 AI 的我也真的就給 AI 寫了

懶的自己寫程式可能會造成某些問題，但現在也回不去了 (´・ω・`)

感覺要重新評估自己該把時間花在什麼東西上，想起之前報告中有寫到（意識到） AI 的應對方法是扎實自身理論知識，現在算是親身體驗到了。

還有哪些東西絕對不能讓 AI 接手，像是日誌，日誌是絕對只有自己來寫才有意義的，這些文章都是我一字一句打下來的，至今我也沒有讓 AI 幫我寫過或修飾過。

我也得承認，現在 AI 資訊那麼多，進步那麼快，其實我也感覺蠻焦慮或 overwhelmed 的，尤其 FB 有加一位用 AI 寫程式用的很強的前輩，雖然都是很片段的分享，但也是那些文讓我感覺這次好像真的不跟上不行。

實際接觸後也覺得確實如此

不是因為 AI 能幫我做什麼成品，或是讓我在一週内上架什麼 Vibe Coding 出的遊戲暴富。

而是因為 AI 是一個能力放大器，這陣子我程式寫的相對少，但實際能力卻往上跳了一大步。

**因為 Vibe Coding 過程反而可以非常「激進」的探索能力邊界**，很多自己學沒注意到的資訊都會被 AI 提出來，而且又剛好是那種「接下來可以學」的東西，所以又都學的會，而做完這些之後，學到的一切又會回到自己身上。

不屬於 AI，而是確實屬於自己的能力。

而自己的能力被擴展後，又能再利用 AI 的瘋狂效率完成自己能力邊界內的工作，產生一種正循環。

這一個月 $600 的 GPT Plus 真的花的很值。

當然還是得說，這都是我的「個人」「現在」的心得，可能不久後又會推翻，而我也沒辦法保證你們看了這篇後去嘗試會有相同體驗，~~除非你們現就在加入我新開的線上課程。~~

沒，我是指這一切成立的前提可能包括以前自學累積的經驗、習慣，跟一些運氣，我也沒辦法回到過去用出學時的思維講解這些，只能用現在會的、熟悉的知識紀錄當下認為的重點，希望能給剛好在適用範圍中的人一點啟發。

※比較

最後來一些比較，比比這陣子用的三大 AI 工具。

GeminiCLI, VSCode Copilot, Claude Code 或 Cursor 這種 “Vibe Code” 工具，因為他們能訪問專案資料夾、關聯關腳本、翻需要的程式碼，所以在依賴關係比較複雜時工作起來比較理想，像是重構或給已經有的系統添加、移除什麼功能，但目標要單一。

而 Gemini CLI 與 Copilot 比較的話（用相同 Agent 提詞配置時），Gemini 的計劃性會更好，而 Copilot 會很衝動，程式碼更新的很激進了，而且會有很嚴重的 over design。

提詞有要求他們先提出計畫，等我同意才能繼續，啊兩個 AI 都會問，但 Copilot 問了也不會等我同意就直接開始了== （Copilot 可以選模型，可能是模型差異導致的，跟 Copilot 本身無關？）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_47.jpg)

還有，無論哪個 AI 的 Chat 內容長到一定程度就要開新對話了，不然 context 汙染很嚴重，做到後面他們會忘記原本的目標是啥，GPT 也是。

插個補充資料，Context, Context 汙染或 Context Engineering 的概念可以參考這部影片

[https://www.youtube.com/watch?v=-8Ygq9AVWZ8](https://www.youtube.com/watch?v=-8Ygq9AVWZ8)

而使用起來最穩定的我覺得還是 ChatGPT ，因為對話限制？或習慣的問題，他的回應會更具體在單一項目，可以先確認寫出來的東西跟預期相符，或是先花一些時間跟 GPT 討論架構，不會像前兩者就嘩啦嘩啦寫一堆可能不是我要的東西。（而且 AI 直接改專案腳本真的很可怕==）

GPT 做完一部分東西後，要新功能（或重構）直接開新對話，如果有程式碼依賴就把關聯腳本上傳給他當 context。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_48.jpg)

但…就算 GPT 還是會發生失控的情況，如果討論的過程發現目標（需求）涉及比較複雜的方案，GPT 會同時想完成所有需求，導致 context 汙染，丟出的東西也會多到超出我的認知負荷量。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_49.jpg)

這種情況我就會放棄目前的對話串跟程式進度，開新對話串，然後把自己整理過的舊內容給 GPT 參考，定出範圍比較具體的新目標，重新開始實做。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_51.jpg)

我提詞寫的很隨便~~（因為懶）~~，但程式寫出來是理想的，這是因為有上傳腳本和「易於擴展」、「單元測試」的關鍵字，加上 GPT 還會拿其他對話、記憶當 context，所以知道我要的程度在哪。

而就算不理想，我也能在過程中逐步修正描述，要什麼、不要什麼，最後也可能調整成期望的樣子…當然也可能不會，尤其對話 context 一長後容易爆走，我就得先用自己期望的樣子寫或是把目標拆的更細，然後再開新對話讓 AI 接續完成。

**重點還是在自己的知識儲備夠不夠，知不知道自己想要啥。**

所以綜合下來，目前最偏好的還是用 GPT，因為與其說是單純的 Vibe Coding 工具，不如說是他是對我有足夠了解的 Programmer 分身 + 家教。

而且多了複製貼上的步驟對理解程式碼的效率其實有蠻大差距，明明是相同程度的內容，但我感覺讓 Agent 直接寫的程式就是更難吸收進腦中。

~~至於 Codex 我直接放棄，那玩意的操作效率真的太可撥了==~~

欸 Codex 也有 [CLI](https://github.com/openai/codex) 了，跟 Gemini CLI 一樣可以裝下來在本地終端執行，修改文件，這樣才對嘛，網頁版那什麼鬼互動效率 ==

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_52.jpg)

（讓 Codex 生成畢專專案的摘要 System Prompt，存在 AGENTS.md 。）

但像前面說的，我現在習慣的還是 GPT 複製貼上，希望畢業前能把想把更進階的 Vibe Coding 技能也練起來，讓幾種本地 Agent 協作開發程式，自己則是架構師或 Manager 的角色。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_53.jpg)

順帶一提

我也有嘗試用 Rider 寫程式，但它什麼都好，就是 Copilot 反應很慢，尤其是 auto complete 出現太慢，而且 Copilot Chat Agent 的回應效果也不太理想。

我能明白為什麼朋友之前說有 Copilot 感覺沒啥差 ，應該是 Rider 的鍋 ) :

所以最後還是決定回到 VScode ，我已經是 Copilot 的形狀了，Copilot 在哪我就在哪。

就這樣，是說前陣子那個 Grok 不是挺紅的嗎？

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_54.jpg)

但老實說我也沒那麼在乎，因為我的心早就屬於 [Lapwing](https://youtu.be/oOIztBXox60) 了。 There is no Ryan Gosling reaction image that can fully convey the feels.

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_08_31-learn-automation_mcp_and_vibe_coding/image_3.jpg)

**※方向**

總之暑假前半就白天學我的東西，晚上跟組員開會發想專題，週休二日。而等教授打掉兩次方向、終於在第三次放行後，已經剩一個月就要開學了。

最終的方向是確實蠻有意思的，而且團隊狀況也在步入正軌，之前踩過的雷都盡可能避開了。

但篇幅問題先不細講，等十月底的文吧。（如果【生活】的內容太少也可能下個月就發）

文末就提一嘴自己對方向的新想法。

隨著畢業將近，自己對專業方向的想法也逐漸清晰吧，主要專業的方向究竟要選什麼，畢竟時間是有限的，全都要這種選項還是太過虛幻，擺脫有毒價值觀後總算能好好做出決定了。

程式或技美…

我應該會選程式當第一專業 : )

雖然這幾年來一直在往技美方向探索，做了不少實驗和小成果，也問過一些前輩的建議和經驗，技美基本上就是一個粥少僧更少的的職位，一個搶手又高薪的專業，而當然也是有理由的，要說困難可能還輕描淡寫了。

但難也不是我選程式的原因，畢竟技美的 Skill Tree 也確實累積出能至少一看的專業了，而且我也很享受研究渲染、圖學和美術玩意的過程。

只是技美累積的點數相對沒那麼多，程式才是我投注最多時間的領域，雖然途中也花過不少時間體驗和擴展其他專業，企劃、專案管理、3D 美術、甚至故事寫作，但仍遠比不上程式。

更何況，這一切的起點都是程式，從高職選資訊科到後來在家自學的起點都是程式。

為了做遊戲，為了最初的夢。

所有的一切都只是手段罷了，程式則是我有的眾多手段中最突出的一項，也是做出遊戲至關重要的一項。

而且

**即使選程式，我也是一個懂渲染和圖學的程式，身上有技美的綜合知識，對 3D 美術、建模、貼圖、骨架、動畫與特效都有概念，除此之外還帶領過專題團隊、做過企劃、專案管理、寫過小說。**

這些選項本來就不相斥，只是有優先順序而已，只是要決定順序而已，而且隨時要改都行，不代表我得真的捨棄什麼。

**無論選哪條路，過去的一切都是確實積累在自己身上的。**

尤其是程式，老實說，也是走了那麼遠，認知到以前的價值觀帶來多大阻礙，想辦法擺脫後才有辦法真的對自己感到自信。

雖然還在讀大學，但我已經不是什麼新人，或許早就不是了，雖然那些根深蒂固的自卑沒辦法馬上擺脫，但也是時候承認自己的進步了。

所以對我來說，畢專不只是大學四年的結尾，還要加上高中和自學的五年，是九年下來的總驗收。

相信自己能交出令人驚豔的成果 :D

就醬

一週後開學就升上四年級了

時光飛逝啊

最後一年

大學進度 80%

大學篇章的終章，敬請期待
