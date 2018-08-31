---
title: Office 365 的效能疑難排解規劃
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 4/26/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
description: 您需要知道要找出並修正 lags、 擱置，與 SharePoint Online、 OneDrive for Business、 Exchange Online 或 Skype 商務 online 與您的用戶端電腦之間的效能低落所採取的步驟嗎？連絡支援之前，這篇文章可協助您疑難排解 Office 365 的效能問題及即使修正的一些常見的問題。
ms.openlocfilehash: c7eed9498920c601b3b345e8d1879ddbb16c56c3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540091"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Office 365 的效能疑難排解規劃

您需要知道要找出並修正 lags、 擱置，與 SharePoint Online、 OneDrive for Business、 Exchange Online 或 Skype 商務 online 與您的用戶端電腦之間的效能低落所採取的步驟嗎？連絡支援之前，這篇文章可協助您疑難排解 Office 365 的效能問題及即使修正的一些常見的問題。
  
本文是實際範例動作計劃可用來擷取效能問題的相關的寶貴資料原狀新鮮事。本文也會包含一些前幾名問題。
    
如果您是新的網路效能並想要讓監控用戶端機器與 Office 365 之間的效能的長期計劃，請查看[Office 365 效能調整及疑難排解-管理員及 IT 專業人員](performance-tuning-using-baselines-and-history.md)。
  
## <a name="sample-performance-troubleshooting-action-plan"></a>範例效能疑難排解動作計劃

此巨集指令計劃包含兩個部分 ；準備階段，並記錄時期。如果您正，有效能問題，您需要執行資料收集您可以啟動立即使用此計劃。
  
 **準備用戶端電腦**
  
- 尋找可重現效能問題的用戶端電腦。這部電腦將用於疑難排解期間。
    
- 記下會導致效能問題，才能讓您準備好要測試時所發生的步驟。
    
- 收集和記錄資訊的工具安裝：
    
  - 安裝[Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) （或使用相等的網路追蹤工具）。 
    
  - 安裝可用的基本版本的[HTTPWatch](https://www.httpwatch.com/download/) （或使用相等的網路追蹤工具）。 
    
  - 使用螢幕錄製或執行以保留記錄的測試期間所採取的步驟而言具有 Windows Vista 和更新版本、 步驟錄製器 (PSR.exe)。
    
 **記錄檔的效能問題**
  
- 關閉所有無關的網際網路瀏覽器。
    
- 啟動步驟錄製器或另一個畫面中錄製。
    
- 啟動 Netmon 擷取 （或網路追蹤工具）。
    
- 輸入 ipconfig /flushdns 來清除您在用戶端電腦從命令列上的 DNS 快取。
    
- 啟動新的瀏覽器工作階段並開啟 HTTPWatch。
    
- 選用： 如果您要測試 Exchange Online、 Exchange 用戶端效能 Analyzer 工具從執行 Office 365 系統管理主控台。
    
- 重現會導致效能問題的確切步驟。
    
- 停止在 Netmon 或其他工具追蹤。
    
- 在命令列上執行追蹤路由傳送至您的 Office 365 訂閱輸入下列命令後按 ENTER：
    
    `tracert \< *subscriptionname*  \>.onmicrosoft.com` 
    
- 停止步驟錄製並儲存的視訊。請務必包含的日期和時間擷取及是否示範良好或不正確的效能。
    
- 儲存追蹤檔案。同樣地，請務必包含的日期和時間擷取及是否示範良好或不正確的效能。
    
如果您不熟悉執行本文中提及的工具，請不要擔心因為我們接下來提供這些步驟。如果您已經習慣來執行此類網路擷取，您可以略過[如何收集基準線](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)，其中會說明篩選以及讀取記錄檔。 
  
## <a name="flush-the-dns-cache-first"></a>先清除 DNS 快取

為何？來取出的 DNS 快取清除中您正在測試開頭乾淨的版面。清除快取，您正在重新設定 DNS 解決程式內容的最新的項目。請記得 flush 不會移除主機檔案項目。如果您是廣泛使用主機檔案項目，您應該將這些項目複製至另一個目錄中的檔案，然後清空主機檔案。
  
 **清除 DNS 解決程式快取**
  
1. 開啟命令提示字元 (**開始**任一\>**執行** \> **cmd**或**Windows 鍵** \> **cmd**)。
    
2. 輸入下列命令並按 ENTER：`ipconfig /flushdns`
    
## <a name="netmon"></a>Netmon

Microsoft 的網路監視工具 ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) 分析封包的傳遞在網路上的電腦之間的流量。藉由使用 Netmon 追蹤與 Office 365 您可以擷取、 檢視、 流量和閱讀封包標頭、 識別而且裝置、 檢查重要設定網路硬體上的，尋找捨棄封包，並遵循流量傳送之間上您公司的電腦網路與 Office 365。因為已加密的流量實際本文，亦即其 （透過 SSL/TLS 的連接埠 443 上旅行您無法讀取所傳送的檔案。而是您要取得之路徑的封包取得可協助您追蹤問題行為篩選的追蹤。
  
請確定您不要在此時間套用篩選器。而完成的步驟執行，並示範之前停止追蹤和儲存的問題。
  
安裝 Netmon 3.4 之後，請開啟工具並執行下列步驟：
  
 **取得 Netmon 追蹤並重現問題**
  
1. 啟動 Netmon 3.4。
    
    在 **[開始**] 頁面上有三個窗格：**最近擷取**、**選取 [網路**和**與 Microsoft Network Monitor 3.4 快速入門。請注意**。[選取 [網路] 面板中也會提供您可以擷取預設網路的清單。請務必張網路卡此處所選。
    
2. 按一下上方的 [**開始**] 頁面上的 [**新擷取**。這會新增新的索引標籤旁呼叫**擷取 1**的**開始**頁面索引標籤。
    
    ![Nemon 的使用者介面與新擷取、 開始，並停止醒目提示] 按鈕。](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)
  
3. 要採取簡單擷取、 按一下 [**開始**] 工具列上。 
    
4. 重現呈現的效能問題的步驟。
    
5. 按一下 [**停止** \> **檔案** \> **另存為**。請記住授與的日期和時間的時區與提如果示範不正確或良好的效能。
    
## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/)有付費，以及可用的版本。免費的基本 Edition 涵蓋了這項測試所需的所有項目。HTTPWatch 監視器瀏覽器視窗中的網路流量及頁面載入時間。HTTPWatch 是要以圖形方式是指效能的 Internet Explorer 的外掛程式。分析可儲存及 HTTPWatch Studio 中檢視。 
  
> [!NOTE]
> 如果您使用另一個瀏覽器，例如 Firefox、 Google Chrome 或您不能安裝 HTTPWatch Internet Explorer 中，開啟新的瀏覽器視窗，並鍵盤上按下 F12。您應該會看到底部的瀏覽器快顯 「 開發人員工具。如果您使用 Opera、 Web inspector 按 CTRL + SHIFT + I、 再按一下 [**網路**] 索引標籤及完成概述如下的測試。資訊會稍有不同，但仍會顯示載入時間 （毫秒）。> HTTPWatch 也是非常有用的 SharePoint Online 頁面載入時間的問題。 
  
 **執行 HTTPWatch 和重現問題**
  
1. HTTPWatch 是瀏覽器外掛程式，因此公開工具在瀏覽器中的每個版本的 Internet Explorer 稍微不同。一般而言，您可以下的命令列中找到 HTTPWatch Internet Explorer 瀏覽器中。</br></br>如果您沒有看到外掛程式 HTTPWatch 瀏覽器視窗中，檢查您的瀏覽器版本藉由按一下 [說明]\>有關，或者在更新版本的 Internet Explorer 中，按一下 [齒輪符號和有關 Internet Explorer。若要啟動的**命令**列、 Internet Explorer 中的功能表列上按一下滑鼠右鍵，按一下 [**命令列**。在過去，HTTPWatch 已產生關聯命令與瀏覽器列中，所以一次安裝，如果您立即未看見 （即使後重新開機） 檢查**工具**] 和圖示在工具列的圖示。請記住可自訂工具列和選項可新增到它們。</br>
    ![Internet Explorer 命令工具列顯示 HTTPWatch 圖示。](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
2. 啟動 HTTPWatch Internet Explorer 瀏覽器視窗中。它會顯示固定至該視窗底部瀏覽器。按一下 [**記錄**]。
    
3. 重現參與效能問題的的確切步驟。按一下 [HTTPWatch 中的 [**停止**] 按鈕。 
    
4. **儲存**HTTPWatch 或**電子郵件來傳送**。請記得的檔案名稱，使其包含日期及時間的資訊和指示您的監看是否包含的示範良好或不正確的效能。</br></br>![HTTPWatch，顯示 Office 365 首頁的頁面載入之 [網路] 索引標籤。](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</br></br>
    這個螢幕擷取畫面會從 HTTPWatch 專業版。您可以開啟採取基本版本的電腦上以專業版中的追蹤項目和那里讀取。額外的資訊可能可從透過該方法將追蹤檔。
    
## <a name="problem-steps-recorder"></a>問題步驟錄製

步驟錄製或 PSR.exe，可讓您可記錄時所發生的問題。這是非常有用的工具和執行很簡單。
  
 **執行問題步驟錄製 (PSR.exe) 來記錄您的工作**
  
1. 其中一個使用**啟動** \> **執行**\>輸入**PSR.exe** \> **[確定**] 或按一下 [ **Windows 鍵**\>輸入**PSR.exe** \> ，然後按 ENTER。 
    
2. 小型 PSR.exe 視窗出現時，按一下 [**開始記錄**和重現重現效能問題的步驟。您可依需要，依序按一下 [**新增註解**新增註解。
    
3. 當您完成步驟按一下 [**停止記錄**。如果頁面轉譯效能問題，等待轉譯之前停止錄製] 頁面。 
    
4. 按一下 [儲存]****。
    
![步驟錄製或 PSR.exe 的螢幕擷取畫面。](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
您的會記錄的日期和時間。這在 PSR Netmon 追蹤和 HTTPWatch 時間，及連結的精確度疑難排解協助。日期及時間 PSR 記錄中的可以顯示分鐘傳遞登入及瀏覽 URL 和部分的轉譯的系統管理網站，例如之間。
  
## <a name="read-your-traces"></a>讀取您追蹤項目

無法教導每個項目網路及疑難排解效能相關的某個人必須知道透過文章。取得在效能良好採用體驗，而您網路的運作方式與通常會執行的知識。但是很可能進位前幾名問題的清單並顯示如何工具可方便您才不致使最常見的問題。
  
如果您想要挑選技能閱讀 Office 365 網站的網路追蹤，有超過定期建立的頁面載入追蹤及取得經驗閱讀這些沒有較佳老師。例如，當您有機會，載入 Office 365 服務，並追蹤程序。篩選的 DNS 流量追蹤或搜尋 FrameData 您瀏覽之服務的名稱。掃描 [取得服務載入時所發生的步驟粗略追蹤]。這可協助您了解哪些一般頁面負載的外觀和指疑難排解、 特別環繞效能比較好故障追蹤可以教您許多。
  
Netmon 使用 Microsoft Intellisense 中顯示的 [篩選] 欄位。Intellisense 或智慧型程式碼完成時，為該輪其中您在一段中輸入與下拉式選取] 方塊中顯示所有可用的選項。如果，例如您擔心 TCP 視窗調整，您可以找到您能夠在篩選器 (例如`.protocol.tcp.window < 100`) 此方法。
  
![這個螢幕擷取畫面的 Netmon 顯示 [顯示篩選欄位] 使用 intellisense。](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Netmon 追蹤可以在其有許多的流量。如果您不具有讀取其經驗，很可能會是混亂開啟追蹤第一次。執行動作的第一個項重點是接收的訊號隔開中追蹤背景雜音。比照 Office 365 中，而您想要查看的流量。如果您是使用巡覽追蹤，您可能不需要此清單。
  
透過 TLS，這表示本文的流量會加密和不在一般的 Netmon 追蹤可讀取一起出差用戶端與 Office 365 之間的流量。效能分析不需要知道封包中資訊的特定資訊。是，但非常興趣封包標頭及其中所包含的資訊。
  
 **若要取得良好的追蹤的秘訣**
  
- 了解在用戶端電腦的 IPv4 或 IPv6 位址的值。您可以從命令提示字元處取得此輸入**IPConfig**命令後按 ENTER。了解這個位址會讓您告訴一覽是否將追蹤檔中的流量直接牽涉到您的用戶端電腦。如果沒有已知的 proxy，ping 它與要取得其 IP 位址。 
    
- 清除 DNS 解決程式快取並儘可能關閉所有瀏覽器除了您執行測試。如果您不能為達成此目的，例如，如果支援使用某些瀏覽器為基礎的工具來查看您的用戶端電腦桌面是準備篩選您追蹤。
    
- 在忙碌中的追蹤，找出您正在使用的 Office 365 服務。如果您已經永不或很少看到您之前的流量，這是來自其他網路雜訊分隔效能問題很有幫助步驟。有幾種執行這項作業。直接之前測試，您可以使用 ping 或 PsPing、 特定服務的 url (`ping outlook.office365.com`和/或`psping -4 microsoft-my.sharepoint.com:443`，如需範例)。您可以在也容易找到該 PsPing Netmon 追蹤 （由其處理程序名稱） 中的。會將會提供您啟動要尋找的位置。
    
    如果您只使用 Netmon 追蹤問題的時間，這是外觀可以太。若要調整自行，使用類似的篩選器`ContainsBin(FrameData, ASCII, "office")`或`ContainsBin(FrameData, ASCII, "outlook")`。您可以記錄追蹤檔從您圖文框的號碼。您也可能會想要捲動到最右邊的框架摘要] 窗格，並尋找交談識別碼] 欄中的色彩。有數字表示有您也可記錄並在稍後隔離查看此特定交談 id。請記得套用任何其他篩選之前先移除此篩選器。
    
> [!TIP]
> Netmon 有許多的實用的內建篩選器。嘗試上方**顯示**篩選窗格的 ["Load Filter"] 按鈕。 
  
![在命令列上的用戶端電腦使用 PSPing 來尋找您 IP。](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![從用戶端透過 TCP 的篩選顯示在同一個 PSPing 命令 Netmon 追蹤。Flags.Syn = = 1。](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
先熟悉您流量，並了解如何找出所需的資訊。例如，了解如何判斷哪些封包追蹤中的有您使用 （例如"Outlook") 的 Office 365 服務的第一個參照。
    
取得 Office 365 Outlook Online 做為範例流量一開始會類似：
  
- 標準的 DNS 查詢和相符 QueryIDs outlook.office365.com 的 DNS 回應。請務必注意針對此 turn-周圍，作為 where 世界的 Office 365 全域 DNS 的以及時間位移傳送之要求的名稱解析。在理想狀況下，為可能的而不是在全世界的半方式在本機。(這可能後面加上一些 DNS 流量 online 登入。)
    
- HTTP 取得要求之狀態報表已永久移動 (301)
    
- 包括 RWS 連線要求及 Connect 回覆 RWS 流量。（這是您進行連線的遠端 Winsock）。
    
- TCP SYN 和 TCP SYN ACK 交談。許多的此交談中的設定會影響您的效能。
    
- 再一系列的這是 TLS 信號交換與 TLS 憑證交談 TLS:TLS 流量進行。（請記住透過 SSL/TLS 加密資料）。
    
所有組件的流量重要及連線，但小型的某些部分的追蹤包含資訊特別重要方面的疑難排解效能，因此我們會將焦點這些方面。此外，由於我們已完成 microsoft 編譯頂端十個清單常見問題疑難排解足夠 Office 365 效能，我們會將這些問題以及如何使用我們需要查明下一步] 工具在焦點。
  
若您尚未安裝所有好下列矩陣進行多項工具的使用。請儘可能。連結會提供給安裝點。清單會包含一般網路追蹤工具[Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865)和[Wireshark](https://www.wireshark.org/)，但使用您所感到，並在其中您正在習慣篩選網路流量任何追蹤工具。當您正在測試時，請記得：
  
-  *關閉您的瀏覽器及測試執行只有一個瀏覽器*-這會減少擷取的整體流量。它會針對較少忙碌追蹤。 
    
-  *清除用戶端電腦上的您 DNS 解決程式快取*-這會提供您全新平板才會在擷取、 簡潔追蹤的啟動時。 
    
## <a name="some-top-issues"></a>某些前幾名問題

您可能會面臨的一些常見問題以及如何在您的網路追蹤中找到這些。

### <a name="tcp-windows-scaling"></a>TCP Windows 縮放比例

位於 SYN-SYN/通知舊版或過時硬體可能不充分運用 TCP windows 縮放比例。 不調整設定適當的 TCP windows、 TCP 標頭中的預設 16 位元緩衝區填滿以毫秒為單位。 流量無法繼續傳送直到用戶端收到指的已接收的原始資料，而造成延遲。

#### <a name="tools"></a>工具：

- Netmon
- Wireshark 

#### <a name="what-youre-looking-for"></a>您要尋找的：

尋找 SYN-SYN/ACK 流量的網路追蹤。 在 Netmon，使用類似的篩選器`tcp.flags.syn == 1`。此篩選會在 Wireshark 相同。  

![篩選適用於這兩種工具的 Syn 封包 Netmon 或 Wireshark： TCP。Flags.Syn = = 1。](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)         
請注意針對每個 SYN 有相關的確認通知 (SYN/ACK) 的目的地連接埠 (DstPort) 中比對來源 （來源） 的連接埠號碼。 

若要查看您的網路連線所使用的 Windows 調整值，依序展開 [先 SYN，然後按一下 [相關的 SYN/通知  

![圖形會顯示如何將符合 DstPort 的來源中的追蹤，以取得時間差異。](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>TCP 閒置時間設定

在過去，大部分的周邊網路中已暫時性的連線，這表示閒置連線通常會終止。可以由 proxy 和防火牆在大於 100 到 300 秒終止 TCP 的閒置工作階段。這是 Outlook Online 的問題因為它會建立並使用長期連線其是否為閒置或不。  

當連線會終止 proxy 或防火牆裝置，用戶端不是發生的事情，並嘗試使用 Outlook Online 表示可在用戶端電腦會嘗試，便會重複替換、 恢復從之前先進行一份新連線。您可能會在載入頁面上看到擱置中的產品、 提示或效能低落。

#### <a name="tools"></a>工具：

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>要尋找的功能：

在 Netmon，查看的來回行程時間位移] 欄位。來回行程是用戶端將要求傳送至伺服器並接收到回應後的間隔時間。檢查用戶端與輸出點之間 (例如用戶端-\> Proxy)，或 Office 365 用戶端 (用戶端-\> Office 365)。您可以看到此許多封包的類型。 

例如，Netmon 中的篩選器可能看起來`.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`，或在 Wireshark、 `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`。  

> [!TIP]
> 不知道您追蹤中的 IP 位址是否屬於您的 DNS 伺服器吗？嘗試查閱在命令列。按一下 [**開始** \> **執行**\>與輸入**cmd**，或按**Windows 鍵**\>輸入**cmd**。在提示處輸入`nslookup <the IP address from the network trace>`。若要測試，請使用 nslookup 針對您自己的電腦 IP 位址。> 若 Microsoft 的 IP 範圍的清單，請參閱[Office 365 Url 和 IP 位址範圍](https://technet.microsoft.com/en-us/library/hh373144.aspx)。 

問題時，預期長時間會位移看起來，在此例中 (Outlook Online)，特別是在 TLS:TLS 封包所顯示的應用程式資料傳送過程中 (例如 Netmon 您可以在尋找應用程式資料封包透過`.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`)。您應該會看到順利進程時間的不同工作階段。如果您看到長時間延遲重新整理您 Outlook Online 時，這可能是重設傳送高程度所造成。 

### <a name="latencyround-trip-time"></a>延遲/循中斷時間 

延遲就可以根據許多變數、 這類升級過時裝置、 將大量的使用者新增至網路與網路連接上的其他工作所耗用的整體頻寬的百分比的許多變更量值。 

有可從這個[網路規劃與 Office 365 的效能調整](network-planning-and-performance.md)] 頁面上的 Office 365 的頻寬計算器。  

需要來測量的連線或您的 ISP 連線頻寬速度吗？嘗試這個網站 （或其類似的網站）： [Speedtest 官方網站](https://www.speedtest.net/)及[Pingtest](http://www.pingtest.net/)。

#### <a name="tools"></a>工具：

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>要尋找的功能：

若要追蹤中追蹤的延遲，將會受益擁有在 Office 365 中記錄的用戶端電腦 IP 位址和 DNS 伺服器的 IP 位址。這是基於更輕鬆地追蹤篩選。如果您透過 proxy 連線，您必須在用戶端電腦 IP 位址、 proxy/輸出 IP 位址] 中，與 Office 365 DNS IP 位址，以方便工時。  

Ping 要求傳送至 outlook.office365.com 會告訴您收到要求的資料中心名稱即使 ping*可能*無法連線至傳送商標連續 ICMP 封包。如果您使用 PsPing （下載免費工具），以及特定連接埠 (443) 和或許使用 IPv4 (-4) 將會收到平均 round 來回時間傳送封包。這可像在 Office 365 服務中，其他 Url 的運作這`psping -4 yourSite.sharepoint.com:443`。事實上，您可以指定取得較大的範例您 average try 類似如下的 ping 數： `psping -4 -n 20 yourSite-my.sharepoint.com:443`。  

> [!NOTE]
> PsPing 不會傳送 ICMP 封包。它會偵測使用 TCP 封包透過特定連接埠，因此您可以使用任何一個您知道開啟。在 Office 365，它會使用 SSL/TLS，請嘗試附加連接埠： 至您 PsPing 443。

![螢幕擷取畫面顯示與 443 進行相同，但也報告 6.5ms年平均 RTT 解析 outlook.office365.com、 和 PSPing ping。](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)        

如果您同時執行網路追蹤載入速度過慢執行的 Office 365] 頁面上，您應該篩選 Netmon 或 Wireshark 追蹤`DNS`。這是一個我們要尋找 Ip。  

以下是篩選以取得 IP 位址 （並仔細 DNS 延遲） 您 Netmon 所採取的步驟。本範例會使用 outlook.office365.com，但也可以使用 SharePoint Online 的租用戶 (例如 hithere.sharepoint.com) 的 URL。  

1. Ping URL`ping outlook.office365.com`和結果中的名稱和記錄的 DNS 伺服器來傳送 ping 要求的 IP 位址。 
2. 網路追蹤 [開啟] 頁面上，或執行巨集指令可讓您的效能問題，或如果您看到高延遲 ping 本身，在網路追蹤它。 
3. Netmon 和篩選器中開啟追蹤的 DNS (此篩選器也運作中 Wireshark，但會區分大小寫`-- dns`)。由於您知道您 ping 從的 DNS 伺服器的名稱也可能會篩選類似的多個能快速以 Netmon:`DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`且哪一個看起來如下 Wireshark dns 中圖文框包含"namnorthwest"。</br>開啟回應封包及在框架詳細資料視窗中的 Netmon，按一下 [DNS 展開如需詳細資訊。您會發現要求至 Office 365-中發生的 DNS 伺服器的 IP 位址的 DNS 資訊在您將需要此 IP 位址 （PsPing 工具） 的下一個步驟。移除篩選，請以滑鼠右鍵按一下 Netmon 的框架摘要中的 DNS 回應\>尋找交談\>DNS 以查看 DNS 查詢和回應-並排。 
4. 在 Netmon，也請注意之間的 DNS 要求及回應時間位移] 欄。在下一步、 輕鬆安裝及使用[PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx)工具有非常實用同時 ICMP 通常會封鎖在防火牆，因為和 PsPing 精細追蹤延遲 （毫秒）。PsPing 完成 TCP 連線到位址及連接埠 （在我們 case 開啟連接埠 443）。 
5. 安裝 PsPing。 
6. 開啟命令提示字元 (啟動\>執行\>輸入 cmd 或 Windows 鍵\>輸入 cmd) 並將目錄變更為 PsPing 執行 PsPing 命令的安裝所在的目錄。在 「 我的範例您可以看到我做 'Qfe' 資料夾上根目錄的 c。您可以執行相同的快速存取。 
7. 輸入命令，讓您針對 Office 365 的 DNS 伺服器的 IP 位址 PsPing 進行從舊版的 Netmon 追蹤--若要新增的連接埠號碼，請記得。 </br>換句話說， `psping -n 20 132.245.24.82:445`。這會提供您的 20 ping 取樣並時 PsPing 停駐點的平均延遲。 

如果您正在透過 proxy 伺服器移至 Office 365、 所有點不同的步驟。您將第一個 PsPing 至 proxy 伺服器，以取得平均延遲值以毫秒為單位 proxy/輸出後再回復，然後再其中一個執行 PsPing proxy 或取得遺失值 （有一個 Office 365 後再回復） 的直接網際網路連線的電腦上。  

如果您選擇從 proxy 執行 PsPing，需要兩個毫秒值： 對 proxy 伺服器或輸出點與 Office 365 的 proxy 伺服器的用戶端電腦。與完成 ！繼續錄製值。  

如果您有直接連線至網際網路的另一個用戶端電腦上執行 PsPing，也就是 proxy，而您也都有兩個毫秒值： 對 proxy 伺服器或輸出點與 Office 365 用戶端電腦的用戶端電腦。在此例中減去的用戶端電腦的值為 proxy 伺服器或輸出點至 Office 365 的用戶端電腦的值與您將必須 RTT 號碼從用戶端電腦的 proxy 伺服器或輸出點並從 proxy 伺服器或輸出指向 Office 365。 

不過，如果您可以在受影響的位置直接連線或略過 proxy 找到的用戶端電腦，您可能會查看如果問題重現那里首先，選擇 [並測試之後，使用。 

延遲視為 Netmon 追蹤，這些額外毫秒可以新增向上中, 如有足夠的任何指定的工作階段。  

![Netmon 中的一般延遲，並將 Netmon 預設時間差異欄位新增至框架摘要。](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> 您的 IP 位址可能不同於此處顯示，例如您 ping 可能會傳回類似詳細如下 157.56.0.0/16 或類似範圍 Ip。如需 Office 365 所使用的範圍的清單，請參閱[Office 365 Url 和 IP 位址範圍](https://technet.microsoft.com/en-us/library/hh373144.aspx)。 

如果您想要搜尋的例如 132.245，記住展開 （這頂端有一個按鈕） 的所有節點。

### <a name="proxy-authentication"></a>Proxy 驗證

這僅適用於您如果您經由 proxy 伺服器。如果不是，您可以略過這些步驟。正常運作時 proxy 驗證應進行毫秒一致。您不應該 （例如） 請參閱尖峰用量期間間歇性錯誤的效能。  

只有在 Proxy 驗證位於的每當您進行新的 TCP 連線至 Office 365 以取得資訊，您需要通過幕後驗證程序。如此，例如從行事曆切換至 Outlook Online 中的郵件，當您將會進行驗證。與 SharePoint Online 中如果 」 頁面會顯示媒體或將資料從多個網站或位置，您會驗證轉譯資料時所需每個不同 TCP 連線。  

在 Outlook Online 中，您可能會遇到每當您行事曆和您的信箱之間切換或 SharePoint Online 中的速度過慢的頁面載入的速度過慢的載入時間。不過，還有其他未列在這裡的徵狀。 

Proxy 驗證是在輸出 proxy 伺服器上的設定。如果它與 Office 365 導致的效能問題，您必須請洽詢您的網路小組。  

#### <a name="tool"></a>工具： 

- Netmon
- Wireshark 

#### <a name="what-to-look-for"></a>要尋找的功能：

Proxy 驗證發生於每當新的 TCP 工作階段必須旋轉完畢之後，通常為向伺服器要求的檔案或資訊或提供資訊。例如，您可能會看到 HTTP GET 或 HTTP POST 要求周圍的 proxy 驗證。如果您想要查看您所進行的要求驗證您追蹤中的框架、 將 ' NTLMSSP 摘要 」 資料行新增至 Netmon 及篩選的`.property.NTLMSSPSummary`。若要查看多久驗證正在進行，新增 [時間差異] 欄中。 

若要將欄新增至 Netmon： 
1. 以滑鼠右鍵按一下例如描述資料行。 
2. 按一下 [選擇資料行。 
3. 在清單中尋找 NTLMSSP 摘要和時間差異並按一下 [新增]。 
4. 移動新欄到位置之前的前面或後面 [描述] 欄以便讀取並排顯示。
5. 按一下 [確定]。 

即使您沒有加入資料行、 Netmon 篩選器會運作。但是您疑難排解會是您可以看到您正處於何種驗證階段的更加簡便。 

要尋找的執行個體的 Proxy 驗證務必研究所有的圖文框有 NTLM 挑戰，或的驗證訊息時出現。如有必要，以滑鼠右鍵按一下流量和尋找交談的特定片段\>TCP。請注意下列交談中的時間差異值。 

![Netmon 追蹤顯示 proxy 驗證篩選依交談。](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)        

四個秒延遲 proxy 驗證視為 Wireshark。**從舊的顯示圖文框的時間差異**欄進行透過圖文框詳細資料中的相同名稱的欄位上按一下滑鼠右鍵並選取 [做為資料行的 [新增。<br/> ![在 Wireshark，'從舊的顯示圖文框的時間差異' 欄可以進行透過圖文框詳細資料中的相同名稱的欄位上按一下滑鼠右鍵並選取 [做為資料行的 [新增。](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)        

### <a name="dns-performance"></a>DNS 效能

名稱解析 works 最佳以及最快速當它接近用戶端的國家/地區為可能的位置。 

如果 DNS 名稱解析為進行 overseas，它可以新增頁面載入秒數。理想狀況下，名稱解析發生的情況下 100ms年中。如果不應進行進一步調查。 

> [!TIP]
> 不確定如何在 Office 365 中的用戶端連線運作？仔細的用戶端連線參考文件[此處](https://technet.microsoft.com/en-us/library/dn741250.aspx)。           

#### <a name="tools"></a>工具： 

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>要尋找的功能：
分析 DNS 的效能是通常是另一個網路追蹤工作。不過，PsPing 十分有用的統治、 回或取出、 可能的原因。 

DNS 流量根據 TCP 及 UDP 要求和回應清楚標示協助以符合其特定的回應特定要求的識別碼。您會看見 DNS 時，例如 SharePoint Online 使用的任何網路名稱或 URL 網頁上的流量。為規則的縮圖中，大部分的此流量 excepting 時傳送區域執行透過 UDP。 

Netmon 和 Wireshark 中最基本篩選，將可讓您查看 DNS 流量只是`dns`。請務必在指定篩選條件時使用小寫。請記得重現問題用戶端電腦上的所顯示的之前清除 DNS 解析快取。例如，如果您有很慢 SharePoint Online 載入頁面的 [首頁] 頁面上，您應關閉所有瀏覽器、 開啟新的瀏覽器、 啟動追蹤、 清除 DNS 解決程式快取及瀏覽至您的 SharePoint Online 網站。一旦解析為整頁，您應該停止並儲存追蹤。

![在 Netmon 中，DNS 的基本篩選器是 DNS。](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

您想要查看以下位移的時間。並將可能會有幫助將**時間差異**資料行新增至 Netmon 您可以藉由完成下列步驟執行： 
1. 以滑鼠右鍵按一下例如描述資料行。 
2. 按一下 [選擇資料行。 
3. 在清單中尋找時間差異並按一下 [新增]。 
4. 移動新欄到位置之前的前面或後面 [描述] 欄以便讀取並排顯示。
5. 按一下 [確定]。 

如果您發現感興趣的查詢，請考慮隔離以滑鼠右鍵按一下該圖文框的詳細資訊] 面板中，選擇 [**尋找交談**中的查詢\> **DNS**。請注意網路交談面板跳右 UDP 流量及其記錄檔中的特定對話。 

![Netmon 追蹤的 DNS，並使用篩選過的 Outlook Online 負載尋找交談則 DNS 縮減結果。](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)        

Wireshark 您可以將一欄的 DNS 時間。取得您追蹤 （或開啟追蹤） 中 Wireshark 及 filter by `dns`，或更多好心`dns.time`。按一下 [在任何的 DNS 查詢和在 [顯示詳細資料] 面板中，展開`Domain Name System (response)`詳細資料。您會看到所有欄位的時間 (例如` [Time: 0.001111100 seconds] `。以滑鼠右鍵按一下此時間，並選取 [**套用] 做為資料行**。這會提供您的**時間**資料行您追蹤的速度較快排序。按一下 [在新的資料行來排序遞減值來查看 DNS 呼叫萬一最長的時間來解決。 

[在 Wireshark 中由 (小寫) dns.time 篩選的 SharePoint Online 瀏覽，時間起點為將詳細資料納入欄位和遞增排序起。](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

如果您想要執行的 DNS 解析時間更多調查，嘗試針對使用 TCP 的 DNS 連接埠 PsPing (例如`psping <IP address of DNS server>:53`)。您仍看到的效能問題嗎吗？如果問題是特定的更多可能是特定的更廣泛的網路問題問題比又打執行解析度 DNS 應用程式。也值得再次提及，該 ping 以 outlook.office365.com 會告訴您其中 DNS 名稱解析為 Outlook Online 正在進行 (例如 namnorthwest.office365.com outlook)。<br/> 如果設為特定的 DNS 尋找問題，則可能需要連絡您的 IT 部門來查看 DNS 組態和 DNS 轉寄站進一步調查這個問題。 

### <a name="proxy-scalability"></a>Proxy 延展性

像 Outlook Online 在 Office 365 服務授與用戶端多個長期連線。因此，每位使用者可能會使用多個需要較長的生命週期的連線。  

> [!TIP]
> 需要因為您即將許多使用者新增至 Office 365 的頻寬使用量計劃嗎？試用[Office 365 的網際網路頻寬使用量計劃](https://technet.microsoft.com/en-us/library/hh852542.aspx)。有可用頻寬計算器發生。

#### <a name="tool"></a>工具：
 
數學  

#### <a name="what-to-look-for"></a>要尋找的功能： 

沒有網路追蹤或疑難排解工具專屬於這。而根據其授與限制及其他變數的頻寬計算。  

### <a name="tcp-max-segment-size"></a>TCP Max 區段大小

位於 SYN-SYN/通知 執行這項檢查中已過以確定 TCP 封包設定為執行可能的資料數量上限任何效能網路追蹤。 

目標是以查看 1460 位元組的資料傳輸的 MSS。如果您正在背後的 proxy 或使用 NAT，請一定要執行這項測試從用戶端 proxy/輸出/NAT 和 proxy/輸出/至 Office 365 的 NAT 獲得最佳結果 ！這些是不同的 TCP 工作階段。

#### <a name="tool"></a>工具： 

Netmon

#### <a name="what-to-look-for"></a>要尋找的功能：

TCP Max 區段大小 (MSS) 是另一個參數的三種方式信號交換在您的網路追蹤，這表示您將 SYN-SYN/ACK 封包中找到所需的資料。MSS 是以查看其實很簡單。 

開啟任何效能網路追蹤您部署及尋找你好奇、 連線或所示範的效能問題。 

> [!NOTE]
> 如果您要查看追蹤並需要尋找與您交談相關的流量，篩選的用戶端 IP 或 proxy 伺服器或輸出點或兩個 IP。直接升級，您將需要 ping 正在測試的 Office 365 中的追蹤，與篩選器的 IP 位址由它的 URL。 

查看 second-hand 追蹤吗？嘗試使用篩選器的方式放置自己。執行 Netmon，根據 URL，例如搜尋`Containsbin(framedata, ascii, "sphybridExample")`，記下框架數。 

在 Wireshark 使用類似如下`frame contains "sphybridExample"`。如果您注意到您已經找到遠端 Winsock (RWS) 流量 （它可能顯示為 [PSH、 ACK] 中 Wireshark），請記得 RWS 連線可以稍後再相關 SYN-SYN/認可呈現稍早所述。 

此時，記錄的圖文框號碼、 drop 篩選、 按一下 [網路交談] 視窗中查看最接近 SYN.Netmon 中的所有流量 

重要的，如果您未收到任何追蹤時間的 IP 位址資訊，請尋找您的 URL 中追蹤 (的一部分`sphybridExample-my.sharepoint.com`、 例如)，將會提供您所篩選的 IP 位址。 

追蹤您感興趣看不到中找到的連線。您可以篩選的 IP 位址或選取特定的交談 Id 使用網路交談視窗中 Netmon 任一掃描追蹤，來執行這項作業。一旦您已經找到 SYN 封包，展開 [TCP （在 Netmon) 或傳輸控制通訊協定 （在 Wireshark) 台中之圖文框的詳細資訊。展開 [TCP 選項及 MaxSegementSize。尋找相關的接收圖文框並依序展開 [TCP 選項及 MaxSegmentSize。較小的兩個值會是最大的區段大小。在此圖片中，讓使用中稱為 [TCP 疑難排解 Netmon 的內建欄。  

![Netmon 使用內建欄篩選的網路追蹤。](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

內建欄是頂端的**圖文框的詳細資訊**面板。（切換回至在標準模式，再按一下 [欄]，，然後選擇 [時區）。 

![在欄位下拉式清單中尋找 TCP 疑難排解選項 (在框架摘要的頂端)。](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)           
以下是篩選過的追蹤 Wireshark 中。有特定的 MSS 值的篩選器 ( `tcp.options.mss`)。下方的 Wireshark 等於圖文框的詳細資訊連結的框架 SYN SYN/ACK、 ACK 信號交換 （所以包圍 47 ACK、 46 SYN/ACK 連結、 連結 43 SYN） 以方便這種工作。 

![追蹤 Wireshark 中由 tcp.options.mss 的最大區段大小 (MSS) 的篩選。](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)         
如果您需要檢查選擇性指 （在此矩陣中的下一個主題），不會關閉您追蹤 ！

### <a name="selective-acknowledgment"></a>選擇性指

位於 SYN-SYN/通知必須報告為許可 SYN 和 SYN/通知選擇性指 (SACK) 中的允許更順暢地呈現資料時的封包重新傳輸或封包移遺失。裝置可以停用這項功能可能會導致效能問題。 

如果您正在背後的 proxy 或使用 NAT，請一定要執行這項測試從用戶端 proxy/輸出/NAT 和 proxy/輸出/至 Office 365 的 NAT 獲得最佳結果 ！這些是不同的 TCP 工作階段。

#### <a name="tool"></a>工具： 

Netmon 

#### <a name="what-to-look-for"></a>要尋找的功能：

選擇性指 (SACK) 是另一個參數中的 SYN/接收信號交換。您可以篩選 SYN-SYN/ACK 許多方法可讓您追蹤。 

追蹤您感興趣看不到 [掃描追蹤篩選的 IP 位址或依序按一下 [使用網路交談視窗中 Netmon 交談 ID 之中找到連線。一旦您已經找到 SYN 封包，展開 [TCP 中 Netmon 或 Wireshark 圖文框詳細資料] 區段中的傳輸控制通訊協定。展開 [TCP 選項，然後 SACK。尋找相關的接收圖文框並依序展開 [TCP 選項和其 SACK] 欄位。讓特定 SACK 允許在 SYN 和 SYN/通知以下是 SACK 值視為 Netmon 和 Wireshark 中。

![選擇性指 (SACK) 中 Netmon 結果的 tcp.flags.syn = = 1。](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)           <br/> ![Wireshark 中所示的 SACK 及篩選器 tcp.flags.syn == 1。](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)        

### <a name="dns-geolocation"></a>DNS 地理位置 

其中世界的 Office 365 會嘗試解析 DNS 呼叫效果連線速度。 

Outlook Online 中第一個 DNS 查閱完成後，該 DNS 的位置會用以連線至最接近的資料中心。您會連線至 Outlook Online CAS 伺服器，將會使用骨幹網路連線至資料中心內 (dC) 儲存您的資料。這是更快。

當存取 SharePoint Online、 出國出差的使用者會將您導向到其作用中資料中心-屬於其位置根據其 SPO 租用戶 dC 的常用基底 (賣中 USA dC 如果使用者如果 USA 型)。  <br/>  Lync online 會有作用中節點中多個 dC 一次。要求時傳送的 Lync online 執行個體中，Microsoft 的 DNS 會決定在全球要求來自哪個位置，並傳回 IP 位址從最接近地區性 dC 其中 Lync online 是使用中。 

> [!TIP]
> 需要更了解用戶端如何連線至 Office 365？請查看下列[用戶端連線](https://technet.microsoft.com/en-us/library/dn741250.aspx)參考文章 （和其很有幫助圖形）。           
#### <a name="tools"></a>工具：

- Ping
- PsPing

#### <a name="what-to-look-for"></a>要尋找的功能：

在大多數情況下結果中傳回的地區資料中心 (dC) 的 IP 位址的 Microsoft DNS 應該從用戶端的 DNS 伺服器的名稱解析 Microsoft 的 DNS 伺服器的要求。這代表您什麼？如果您 headquarters 班加羅爾 （印度），但在美國，當瀏覽器中的 Outlook Online 提出要求時所出差、 Microsoft 的 DNS 伺服器應該另一方面您的 IP 位址至美國-地區資料中心中的資料中心。視郵件是從 Outlook，該資料會透過 Microsoft 的快速骨幹網路旅行社之間的資料中心。

名稱解析完成接近使用者位置盡位置時的 DNS 運作速度最快。如果您是在歐洲、 您要移至 [歐洲、 Microsoft DNS 與 （理想的情況下） 處理歐洲地區資料中心。從用戶端的 Europe 移至 DNS 和 America 中的資料中心的效能會較慢。

若要判斷出世界中您的 DNS 要求目前正在路由 outlook.office365.com 針對執行 Ping 工具。如果您是在歐洲，您應該會看到類似如下 outlook emeawest.office365.com 的回覆。在美洲預期類似如下 outlook namnorthwest.office365.com。 

開啟命令提示字元中用戶端電腦上 (透過開始\>執行\>cmd 或 Windows 鍵\>輸入 cmd)。輸入 ping outlook.office365.com 並按 ENTER。請記住，如果您想要指定 ping IPv4 透過指定-4。您可能會失敗回覆跳 ICMP 封包，但您應該會看到的要求已路由傳送的 DNS 名稱。如果您想要查看此連線的延遲號碼 PsPing 嘗試 ping 所傳回之伺服器的 IP 位址。  

![outlook.office365.com 的 Ping，顯示 outlook-namnorthwest 中的解析。](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)           
![PSPing ping 回到 outlook.office365.com 顯示平均 28 毫秒延遲的 IP 位址。](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)           
### <a name="office-365-application-troubleshooting"></a>Office 365 的應用程式疑難排解

#### <a name="tools"></a>工具： 

- Netmon
- HTTPWatch
- 在瀏覽器 F12 主控台

我們不涵蓋中特定應用程式疑難排解特定網路的本文中所使用的工具。可找到資源，但是您*可以*使用[此頁面上](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)。
   
## <a name="related-topics"></a>相關主題

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  

