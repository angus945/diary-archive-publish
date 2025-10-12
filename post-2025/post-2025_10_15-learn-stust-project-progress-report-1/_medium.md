
# 【專題】一審進度報告 10/1

大家好，我們是南臺科大多樂系的畢專遊戲團隊《4AM 就寢》，這篇文是我們 10/1 的專題一審簡報 + 逐字稿分享。

直接進正文，其他東西等文末再補充。

## 一審報告

**※封面**

大家好，評審老師們好，我們是第 13 組，4AM 就寢。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_10.jpg)

**※組員**

我們組一共有六人，指導老師是 OO 老師（謝老師）。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_11.jpg)

### **基本資訊**

我們的遊戲名稱是《西洋劍少爺與垃圾神話》，遊戲類型是俯視角動作 Rouge、遊玩人數為單人、平台 PC ，目標客群是輕度動作玩家和 Rouge 玩家。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_12.jpg)

但考量時間跟展場性，畢專原型會先以編排過的關卡作為 Demo，也不會做出兩種 Rouge 類型的差異。（逐字稿有這段，但上台時我好像跳過了）

**※遊戲概念**

玩家要拿著拖把杆，在回收場中把會動的垃圾們串起來當武器，利用垃圾生物的能力擊敗所有阻礙者。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_13.jpg)

**※故事概念**

主角是一個被拋棄到垃圾回收場的西洋劍少爺，為了重回原本的地位，他必須在這裡取得一把神器，那是一把只有串滿十萬垃圾靈魂的後才能得到的「垃圾聖劍」。

故事的舞台是一座奇幻垃圾回收場，裡面充滿了各種有自我意識的垃圾生物，但因為對焚化神與壓縮神的信仰而分裂成兩種對立的意識形態，衝突似乎正在越演越烈。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_14.jpg)

那麼，一位曾經擁有權力卻被拋棄的人類，與一群被拋棄但建立新秩序的物品們，究竟會產生什麼樣的火花？對錯、信仰與價值觀，玩家又要如何選擇？

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_15.jpg)

### **遊戲特色**

**※豐富的敵人技能**

因為回收場與垃圾生物的設定，我們的敵人是透過資源回收分類的類別去設計的，並且每個類別都有自己的對應技能。

例如電池電器類敵人可以產生爆炸、紙類可以產生視覺干擾，而玩家也能在用武器把敵人串起來之後，使用他們的能力戰鬥。

**※荒謬的視覺呈現**

遊戲會像塊魂那樣，直接讓玩家把敵人黏在武器上，玩家可以黏一堆敵人，到最後武器看起來就會像一大陀東西，可以提供遊戲畫面一種荒唐的喜感。

**※有趣的互動對話**

遊戲的各種垃圾生物，包括敵人 與 NCP 都有很多有趣的對話可以讓玩家挖掘。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_16.jpg)

## 核心機制

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_17.jpg)

※攻擊

在玩家撿起武器，或者說拖把杆之後，就能透過普通攻擊打擊敵人，但這把武器目前還無法造成任何傷害。

※魔力

當玩家使用武器直接擊中敵人時會獲得一個特殊資源，我們先暫時稱呼為「魔力」，是可以用來串接敵人的關鍵資源。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_1.jpg)

**※投擲武器**

玩家可以把手上的武器往指定方向扔出，如果魔力足夠的話武器就會卡在敵人身上

**※召回**

玩家可以把投擲出的武器吸回自己身邊，如果武器卡在敵人身上，那被卡住的敵人也會一起拉回來，然後玩家就能連著卡住的敵人「整隻撿起來」當武器用。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_2.jpg)

（投擲武器的圖放錯了，當時報告就想說怎麼怪怪的，應該是這張才對==）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_9.jpg)

**※攻擊器加成**

串著敵人的武器會獲得攻擊力加成，這再攻擊就能造成有效傷害了。

**※特殊技能**

除了攻擊力之外，玩家還能在揮動武器時，發動被串上的敵人的技能。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_3.jpg)

**※多重串接**

玩家可以丟出串著武器的敵人，然後把更多敵人串到武器上，但每多疊一層，需要的魔力成本也會增加。

**※強化疊加**

每個串著的敵人都會提供武器額外攻擊力和攻擊範圍，除此之外，在玩家使用武器時，上面敵人的技能也會被一併觸發。所以串越多敵人的武器，除了能造成更多基本傷害之外，也會有更多種效果。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_4.jpg)

**※代價** 

力量是有代價的，串越多敵人雖然讓武器更強，但武器也會變得更笨重，這會導致玩家的行動變困難，減慢移動和攻擊速度。

**※風險**

而當串接的敵人累積到一定數量後武器會進入一個不穩定狀態，如果玩家這個情況下受到傷害，串再武器上的敵人都會被噴飛回場地，加入對玩家的戰鬥。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_5.jpg)

**※耐久度**

武器上的敵人也有耐久度，或者說就是敵人的血量，玩家每次攻擊都會消耗他們的血量，如果血量歸零敵人就會死亡並從武器上脫落.

**※拋射**

玩家也可以選擇主動釋放武器上的敵人，透過「重擊」可以把武器上的敵人往指定方向拋射出去，會對砸到的其他敵人造成大量傷害並觸發技能。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_6.jpg)

**※其他**

至於其他的 Rogue 相關機制，技能、隨機、商店或劇情什麼的就再依製作狀況評估。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_18.jpg)

### 遊戲迴圈

核心迴圈就是普通的動作 Rogue 迴圈。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_19.jpg)

開始一局遊戲後，玩家會進入由多個房間構成的關卡，玩家要探索這些房間。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_20.jpg)

在戰鬥房中玩家必須打敗所有敵人才能離開。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_21.jpg)

戰鬥完後玩家會獲得一些獎勵，像是貨幣，能用來買一些技能跟道具。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_22.jpg)

當玩家完成某些階段目標後，就會推動全局的劇情進度。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_23.jpg)

然後獲得永久強化、解鎖道具，或開啟新的區域讓玩家探索，重複這個過程直到完成遊戲指定的最終目標。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_24.jpg)

## 美術風格

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_25.jpg)

我們的角色、敵人、NPC 等活動生物會用 2.5D 紙片人顯示，並採用市場接受度更高的通用的 Q 版畫風繪製，而場景則是 3D 採用有輪廓線與硬邊陰影的風格化渲染。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_26.jpg)

這裡是主角設計圖，包括概念形象、遊戲中的預期樣貌設計動作設計，這裡停三秒給大家欣賞一下（對，我報告的時候這樣講）

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_27.jpg)

 （左邊兩張是由概念美術 Avis Shih 繪製，最用右邊是美術設計 izumige 繪製，後續動畫會由她負責。）

這裡是遊戲中廢料生物的設計圖，一樣停三秒。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_28.jpg)

（由組員 HuaShang 和 Natsu37 繪製的怪物設計）

這是我們的測試渲染畫面截圖。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_29.jpg)

（組員 ChiyukiO3O 拿素材搭建的測試場景，我再爆力減面後放進 Unity 測試） 

### 趣味性設計

然後是一些趣味性設計補充。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_30.jpg)

**※荒誕的視覺效果**

首先是視覺效果，就像開頭說的，武器串起的敵人都會真的黏在武器上，除此之外還會有各種誇張的表現手法，像是紙片人的飛散或翻滾。

這樣能讓遊戲畫面會充滿喜感，即使在展場，只要觀眾路過看到一眼就能被荒唐的表現形式吸引注目光。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_7.jpg)

**※聒噪的敵人**

再來是敵人，戰鬥中的垃圾生物是會講話的，或是更誇張一點，他們在被串到玩家武器上的敵人也還會繼續講話。他們可能抱怨、嘴砲玩家玩的爛或是跟武器上的其他垃圾生物吵架。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_31.jpg)

**※垃圾話**

遊戲中的敵人與 NPC 有時會講出一些聽起來沒道理…….而確實也沒道理的垃圾話，例如「時間不是線，而是塑膠袋理纏繞不開的死結」、「蒼蠅在我身上盤旋，那不是腐敗，是信徒的朝聖」。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_32.jpg)

**※競品和參考**

我們的主要競品和對象是這三款，《進擊羔羊傳說》我們是參考他們的視覺風格和戰鬥手感，而另外兩款《Going Under》和《萬物皆武器的 RPG》則是參考遊戲與機制設計。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_33.jpg)

### 規劃 & 進度

目前我們完成了：核心機制原型、核心系統架構、主角形象設計、敵人設計、敵人分類技能種類設計

正在進行的包括：主角動作設計、敵人動作設計、場景物件製作、場景渲染研究

之後要規劃的有：動畫設計、NPC 設計、場景設計、敵人程式設計、其他 Rogue 機制設計和開發

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_34.jpg)

### 原型展示

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_35.jpg)

（就是播影片，影片沒有聲音，所以報告當下我是播影片的同時講那些進度跟規劃）

[https://youtu.be/9RZXbTML6sU](https://youtu.be/9RZXbTML6sU)

[https://youtu.be/9RZXbTML6sU](https://youtu.be/9RZXbTML6sU)

我們的報告到此結束，謝謝大家。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_36.jpg)

## 心得

也不是真的心得，只是我想不到用什麼標題分隔所以寫心得。

總之以上是我們專題一審 10/1 的報告內容，我把簡報跟逐字稿都轉發過來，直接當專案介紹了。

現在雖然有原型，但那版還少很多必要回饋，所以先不提供試玩連結，等後續重構完程式、把基礎體驗完整到一定程度會再公開試玩，這裡先放專題進度審查交的影片（就原型展示那個）。

**※報告**

報告是 10/1 整天，學生全體出席，分上午與下午場、中間各有一次休息，每組提報時間 10 分鐘、老師講評 5 分鐘，報告組全員都要上台，但主要負責表演...咳...報告的是我。

當然了，不然還有誰呢 (´・ω・`)

原稿也不是長上面那樣，這篇有針對文章形式組織成長句，稿子實際上是逐行寫的。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_37.jpg)

還有雖然說是「逐字稿」，但我也不是真的照著背，文字稿只是大概規劃一下自己要講的東西（跟簡報同時做），等演練到一定程度後就不會再看稿了，一方面是要記住內容，另一方面是要根據實際唸起來的語感改詞，或跳過一些贅句。

簡報是 9/24 繳交，報告前一週我就不時去讀，然後前兩天再比較密集演練，其他事基本也做不了。演練也有計時測試，最後實際上台大概在 8 分鐘左右結束。

**※簡報**

簡報是我先在 Canva 把每頁要有的東西放上去，規劃文字、圖片跟簡報架構（同時規劃講稿），然後給組員 HuaShang 幫忙排版。然後副隊長 ChiyukiO3O 檢查後又幫我多補上了中間 Storyboard 的幾頁，我原本想偷懶跳過說 :P

不確定簡報在文章中感覺怎樣，但應該能看出我們的字跟圖片是幾乎滿版的，有把字體加大加粗、調高色彩對比，當時特別要求組員把字加的盡可能大。

為什麼要那麼大？

因為這是報告的場地，整年級快百人會坐到第九排，而且報告當天沒有關燈，簡報字體、顏色沒調好的後排看就跟麵糊一樣。我們的簡報理論上到講廳最後一排都能看清楚，如果觀眾沒近視的話。

![圖片](https://raw.githubusercontent.com/angus945/diary-archive-publish/refs/heads/main/post-2025/post-2025_10_15-learn-stust-project-progress-report-1/image_8.jpg)

啊為什麼我知道？

因為一年級參加簡報比賽就見識過，雖然是不同場地，但舞台的投影幕也是狗幹小。雖然低標只要第一排老師能看到就好，但我還是希望簡報能有該有的樣子，畢竟要站在前面講話的是我啊 RRR

總之一審就這樣，之後再看有沒有時間，我想補一篇從暑假發想到這個最終方向的演變歷程。

至於感想就…等下一篇【生活】再一起說吧 |:

還有這篇原本應該轉到 FB 的，但我 FB 沒了==