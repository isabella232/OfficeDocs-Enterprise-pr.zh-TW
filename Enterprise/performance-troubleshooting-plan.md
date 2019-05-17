---
title: Office 365 的效能疑難排解規劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: 您需要知道要找出並修正下降、 擱置，以及 SharePoint Online、 商務、 Exchange Online 或商務用 Skype 線上商務用 OneDrive 與您的用戶端電腦之間的效能降低所採取的步驟嗎？ 連絡支援人員之前，這篇文章可協助您疑難排解 Office 365 的效能問題，甚至修正一些最常見的問題。
ms.openlocfilehash: afa24144c1595fd55477e45f4368d99bd4274aca
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069579"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Office 365 的效能疑難排解規劃

您需要知道要找出並修正下降、 擱置，以及 SharePoint Online、 商務、 Exchange Online 或商務用 Skype 線上商務用 OneDrive 與您的用戶端電腦之間的效能降低所採取的步驟嗎？ 連絡支援人員之前，這篇文章可協助您疑難排解 Office 365 的效能問題，甚至修正一些最常見的問題。
  
本文是實際範例巨集指令計劃，您可以使用擷取的效能問題的相關重要的資料，就像情形。 本文也會包含一些上方的問題。

如果您是初次使用網路效能和想要讓長期計劃監視用戶端電腦與 Office 365 之間的效能，看看在[Office 365 效能調整和疑難排解的系統管理員和 IT 專業人員](performance-tuning-using-baselines-and-history.md)。
  
## <a name="sample-performance-troubleshooting-action-plan"></a>範例效能疑難排解行動計畫

此巨集指令計劃包含兩個部分;準備階段，並記錄階段。 如果您有效能問題是現在不用]，且您不必執行資料集合，您可以開始立即使用此計劃。
  
### <a name="prepare-the-client-computer"></a>準備用戶端電腦
  
- 尋找也發生效能問題的用戶端電腦。 此電腦將用於疑難排解的過程中。
- 請記下會造成效能問題，才能讓您準備好提到時間進行測試時，即會發生的步驟。
- 安裝收集和記錄資訊的工具：
  - 安裝[Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) （或使用對等網路追蹤工具）。
  - 安裝[HTTPWatch](https://www.httpwatch.com/download/)免費基本版 （或使用對等網路追蹤工具）。
  - 使用螢幕錄製器，或執行步驟收錄程式 (PSR.exe) 隨附在 Windows vista 及更新版本中，以保留記錄的測試期間所採取的步驟。

### <a name="log-the-performance-issue"></a>記錄效能問題
  
- 關閉所有無關的網際網路瀏覽器。
- 啟動步驟收錄程式或另一個螢幕錄製。
- 啟動您的 Netmon 擷取 （或網路追蹤工具）。
- 清除您的 DNS 快取，用戶端電腦從命令列上輸入 ipconfig /flushdns。
- 啟動新的瀏覽器工作階段，並開啟 HTTPWatch。
- 選用： 如果您正在測試 Exchange Online，執行 Exchange 用戶端效能分析器工具從 Office 365 系統管理主控台。
- 重現會造成效能問題的確切步驟。
- 停止您 Netmon 或其他工具追蹤。
- 在命令列中，執行追蹤路由傳送至您的 Office 365 訂閱中輸入下列命令並按 ENTER:

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- 停止步驟收錄程式，並儲存的視訊。 請務必包含的日期和時間擷取及是否會示範良好或不正確的效能。
- 儲存追蹤檔案。 同樣地，請務必包含的日期和時間擷取及是否會示範良好或不正確的效能。

如果您不熟悉執行本文中提及的工具，不用擔心因為我們會提供這些步驟下一步]。 如果您已經習慣執行這類擷取網路，您可以略過[如何收集基準](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)，其中會說明篩選和讀取記錄檔。
  
### <a name="flush-the-dns-cache-first"></a>先清除 DNS 快取

為什麼？ 藉由出 DNS 快取清除中您要從頭開始測試。 藉由清除快取，您正在重 DNS 解析程式內容設為最新的項目。 請記住，儲存變更並不會移除 HOSTs 檔案項目。 如果廣泛使用主機檔案項目，您應該將這些項目複製到另一個目錄中的檔案，並再清空主機檔案。
  
#### <a name="flush-your-dns-resolver-cache"></a>清除您的 DNS 解析程式快取
  
1. 開啟命令提示字元 (**啟動**任一\>**執行** \> **cmd**或**Windows 鍵** \> **cmd**)。
2. 輸入下列命令，然後按 ENTER：

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Microsoft 的網路監視工具 ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) 會分析封包，是在網路上的電腦之間傳送的流量。 使用追蹤流量與 Office 365 您可以擷取，檢視中，並讀取封包標頭、 識別中間的裝置，請檢查網路硬體上的重要設定 Netmon，尋找捨棄封包，並遵循上您公司的電腦之間的流量傳送網路和 Office 365。 因為實際的主體的流量加密，也就是它 （透過 SSL/TLS 的連接埠 443 上旅行您無法讀取檔案傳送。 相反地，您會收到未篩選的追蹤的封包採取可協助您追蹤問題行為的路徑。
  
請確定您未在此階段套用篩選。 相反地，完成的步驟執行，並示範之前停止追蹤和儲存的問題。
  
在您安裝 Netmon 3.4 之後，開啟工具]，並採取下列步驟：
  
### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>Netmon 追蹤並重現問題
  
1. 啟動 Netmon 3.4。
在 [**開始**] 頁面上有三個窗格：**最近擷取**、**選取 [網路**和**與 Microsoft Network Monitor 3.4 快速入門。請注意**。 選取 [網路] 面板也會提供您的您可以從中擷取預設網路清單。 請確定網路卡此處所選。

2. 按一下 [頂端的 [**開始**] 頁面上的 [**新擷取**]。 這會新增名為**擷取 1**的**開始**頁面索引標籤旁的新索引標籤。
![Netmon 的使用者介面與新擷取，開始，並停止反白顯示的按鈕。](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. 若要執行簡單擷取，按一下 [**開始**] 工具列上。

4. 重現呈現的效能問題的步驟。

5. 按一下 [**停止** \> **檔案** \> **另存為**。 請記得提供的日期和時間的時區，並涵蓋如果它會示範不正確或良好的效能。

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/)有充電，和免費版。 免費的基本版涵蓋您需要這項測試的所有項目。 HTTPWatch 監視網路流量以及頁面載入時間直接從瀏覽器視窗。 HTTPWatch 是要以圖形方式說明效能的 Internet Explorer 的外掛程式。 分析可儲存及 HTTPWatch Studio 中檢視。
  
> [!NOTE]
> 如果您使用另一個瀏覽器，例如 Firefox、 Google Chrome 或您不能安裝 HTTPWatch Internet Explorer 中，開啟新的瀏覽器視窗，並按下鍵盤上的 F12。 您應該會看到開發人員工具快顯視窗底部的瀏覽器。 如果您使用 Opera，Web 檢查員按 CTRL + SHIFT + I，然後按一下 [**網路**] 索引標籤再完成以下所述的測試。 資訊會稍有不同，但仍會顯示載入時間 （毫秒）。 > HTTPWatch 也是很有用的 SharePoint Online 頁面載入時間的問題。
  
### <a name="run-httpwatch-and-reproduce-the-issue"></a>執行 HTTPWatch 和重現問題
  
HTTPWatch 是瀏覽器外掛程式，因此公開在瀏覽器工具會稍有不同的每個版本的 Internet Explorer。 一般而言，您可以在命令列的下方找到 HTTPWatch Internet Explorer 瀏覽器中。 如果您沒有看到外掛程式 HTTPWatch 瀏覽器視窗中，檢查您的瀏覽器的版本即可**協助** \> **有關**，或在更新版本的 Internet Explorer，按一下 [齒輪符號**關於 Internet Explorer**。 若要啟動的**命令**列，Internet Explorer 中的功能表列上按一下滑鼠右鍵，然後按一下**命令列**。

在過去，HTTPWatch 已相關命令與瀏覽器列中，因此一次您安裝時，如果您沒有立即看到檢查**工具**，以及您工具列圖示的圖示 （即使後重新開機）。 請記住，您可以自訂工具列，選項可將它們加入。

![Internet Explorer 的命令工具列顯示的 HTTPWatch 圖示。](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
1. 啟動 Internet Explorer 瀏覽器視窗中的 HTTPWatch。 它會顯示固定至該視窗底部的瀏覽器。 按一下 [**記錄**]。

2. 重現參與效能問題的的確切步驟。 按一下 [HTTPWatch 中的 [**停止**] 按鈕。

3. HTTPWatch 或**傳送的電子郵件**，[**儲存**]。 請記得，使其包含的日期和時間的資訊和指示您的監看是否包含的良好或不正確的效能示範做為檔案名稱。

![HTTPWatch，顯示 Office 365 首頁的頁面載入之 [網路] 索引標籤。](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

這個螢幕擷取畫面會從 HTTPWatch 專業版。 您可以開啟含有專業版的電腦上的基本版本中所採取的追蹤項目和那里讀取。 額外的資訊可能會提供追蹤透過該方法。

## <a name="problem-steps-recorder"></a>問題步驟收錄程式

步驟收錄程式或 PSR.exe，可讓您記錄問題，因為它們發生。 這是很有用的工具和非常簡單，執行。
  
### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>執行問題步驟收錄程式 (PSR.exe) 來記錄您的工作
  
1. 使用**開始** \> **執行**\>輸入**PSR.exe** \> **[確定]**，或者按一下 [ **Windows 鍵**\>輸入**PSR.exe** \> ，然後按 ENTER。

2. 小型 PSR.exe 視窗出現時，按一下 [**開始錄製**並重現重現效能問題的步驟。 如有需要按一下 [**新增註解**，您可以新增註解。

3. 當您已完成的步驟，請按一下 [**停止記錄**]。 ] 頁面上呈現效能問題時，等候轉譯之前停止錄製] 頁面。

4. 按一下 [儲存]****。

![步驟收錄程式或 PSR.exe 的螢幕擷取畫面。](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
為您記錄的日期和時間。 此連結您 PSR Netmon 追蹤及 HTTPWatch 的時間，並協助精確度疑難排解。 PSR 記錄中的時間與日期可以顯示一分鐘的傳遞登入與例如瀏覽的 URL 及管理網站中，部分轉譯之間。
  
## <a name="read-your-traces"></a>讀取您追蹤

因為不可能教導每個項目網路和效能問題的疑難排解的相關的其他人必須知道透過文章。 取得在效能良好採用體驗，而您的網路的運作方式與通常會執行的知識。 但可能要無條件進位的頂端的問題清單，並顯示如何工具可以讓更容易，以消除最常見的問題。
  
如果您想要揀選技術閱讀 Office 365 網站的網路追蹤，沒有任何更好教師比定期建立的頁面載入追蹤和取得讀取它們的經驗。 例如，當您有機會，載入 Office 365 服務和追蹤程序。 篩選追蹤 DNS 流量，或搜尋 FrameData 您瀏覽之服務的名稱。 掃描的追蹤，以了解發生服務載入時的步驟。 這可協助您了解哪些 normal 載入頁面的外觀和若是進行疑難排解，周圍的效能，尤其是比較好到錯誤的追蹤項目可以教您很多。
  
Netmon 會使用 Microsoft Intellisense 中顯示篩選器] 欄位。 Intellisense 或智慧型程式碼完成時，為該手法您在一段中輸入，並在下拉式清單選取項目] 方塊中顯示所有可用的選項。 如果，例如，您擔心 TCP 視窗縮放，您可以找到您對篩選器的方式 (例如： `.protocol.tcp.window < 100`) 用這種方法。
  
![螢幕擷取畫面的 Netmon，顯示的 [顯示篩選器] 欄位使用 intellisense。](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Netmon 追蹤項目可以有大量的流量。 如果您不熟悉讀取它們，很可能會是淹沒開啟追蹤第一次。 第一件事是接收的訊號隔開追蹤背景噪音。 比照 Office 365，也就是您想要查看的流量。 如果您是使用巡覽追蹤，您可能不需要此清單。
  
用戶端和 Office 365 之間的流量流經透過 TLS，這表示流量的本文將會受到加密，並在一般的 Netmon 追蹤不容易閱讀。 效能分析不需要知道的封包中的資訊細節。 不過，非常感興趣的封包標頭和所包含的資訊。
  
### <a name="tips-to-get-a-good-trace"></a>若要取得的良好的追蹤的祕訣
  
- 了解您的用戶端電腦的 IPv4 或 IPv6 位址的值。 您可以透過此命令提示字元中輸入**IPConfig** ，然後按 ENTER 鍵。 了解這個地址會讓您一眼告訴是否追蹤中的流量直接牽涉到您的用戶端電腦。 如果沒有已知的 proxy，ping 它並取得其 IP 位址。

- 清除您的 DNS 解析程式快取，如果可能，請關閉所有瀏覽器的那一您執行測試。 如果您不能這麼做，例如，如果支援使用某些瀏覽器型的工具若要查看您的用戶端電腦桌面，就會準備好篩選您追蹤。

- 忙線中的追蹤，找出您正在使用的 Office 365 服務。 如果您已經很少或永遠不會看到您之前的流量，這是與其他網路噪音分隔效能問題很有幫助步驟。 有幾種方式可以這麼做。 直接之前您的測試，您可以使用_ping_或_PsPing_針對特定服務的 URL (`ping outlook.office365.com`或`psping -4 microsoft-my.sharepoint.com:443`，例如)。 您可以也輕鬆尋找該 ping 或 PsPing Netmon 追蹤 （其處理程序名稱）。 會將提供您理想的起點尋找。

如果您只使用 Netmon 追蹤問題的時間，也沒關係太。 若要引導您自己，使用類似的篩選器`ContainsBin(FrameData, ASCII, "office")`或`ContainsBin(FrameData, ASCII, "outlook")`。 您可以將記錄從追蹤檔案您圖文框的號碼。 您也可能會想要捲動到最右邊的_框架摘要_] 窗格，並尋找交談識別碼] 欄中的色彩。 沒有為此特定對話視窗中，您也可以記錄，然後查看在稍後隔離的識別碼有指定的數字。 請記得在套用任何其他篩選之前先移除此篩選。

> [!TIP]
> Netmon 有很有幫助的內建篩選。 請試著頂端的 [_顯示_篩選窗格的 [ **Load Filter** ] 按鈕。
  
![在命令列上的用戶端電腦使用 PSPing，以尋找您 IP。](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Netmon 追蹤從用戶端透過 TCP 的篩選器中顯示的相同 PSPing 命令。Flags.Syn = = 1。](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
熟悉您的流量，並了解如何找到所需的資訊。 例如，了解如何判斷哪一個封包追蹤中的有您正在使用 （例如 「 Outlook 」) 的 Office 365 服務的第一個參照。

取得 Office 365 Outlook Online 做為範例，流量開始可能類似如下：
  
- 標準的 DNS 查詢和使用比對 QueryIDs outlook.office365.com 的 DNS 回應。 請務必注意這個開啟的因應措施，以及為 where 領域中 Office 365 全域 DNS 的時間位移傳送之要求的名稱解析。 理想狀況下，為可行的而非跨越世界各地的如同在本機上。

- HTTP 取得要求的狀態報告已永久移動 (301)

- RWS 流量包括 RWS 連線要求，以及連線回覆。 （這是供您進行連線的遠端 Winsock）。

- TCP SYN-RCVD 和 TCP SYN-RCVD/ACK 交談。 很多此交談中的設定會影響效能。

- 接著一系列的 TLS:TLS 流量也就是 TLS 信號交換和 TLS 憑證交談採取適當的地方。 （請記住會透過 SSL/TLS 加密的資料）。

所有的組件的流量重要與連線，但小型的某些部分的追蹤包含方面效能問題的疑難排解，尤其重要的資訊，因此我們將重點放在這些區域。 此外，因為我們已經完成不足，無法在 Microsoft，以編譯頂端十個清單的常見問題疑難排解的 Office 365 效能，我們將專注於這些問題以及如何使用的工具，我們有查明下一步]。
  
如果您尚未安裝已經準備好，下列矩陣會讓使用數種工具。 請儘可能。 連結提供安裝點。 清單包含常見的網路追蹤工具，像是[Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865)和[Wireshark](https://www.wireshark.org/)，但使用任何追蹤工具，您可以執行對象]，並在其中您正在習慣篩選網路流量。 當您正在測試時，請記得：
  
- *關閉您的瀏覽器，並測試只能有一個執行的瀏覽器搭配*-這會降低您所擷取的整體流量。 它會針對較不忙碌中的追蹤。
- *清除您的 DNS 解析程式快取的用戶端電腦上*-這可讓您從頭採取更簡潔的追蹤您擷取，啟動時。

## <a name="common-issues"></a>常見問題

也可能會遇到一些常見的問題以及如何找到您的網路追蹤。

### <a name="tcp-windows-scaling"></a>TCP 視窗縮放比例

位於 SYN-RCVD-SYN-RCVD/通知 舊版或過時的硬體不可能會利用 TCP 視窗縮放比例。  沒有適當的 TCP 視窗縮放比例設定，預設 16 位元緩衝區 TCP 標頭中的會填入以毫秒為單位。  流量不能繼續傳送直到用戶端收到認可，已收到的原始資料，而造成延遲。

#### <a name="tools"></a>工具

- Netmon
- 在 Wireshark

#### <a name="what-to-look-for"></a>要尋找的項目

尋找 SYN-RCVD-SYN-RCVD/ACK 流量網路追蹤中。  在 Netmon，使用類似的篩選器`tcp.flags.syn == 1`。 此篩選器是 Wireshark 中相同。  

![在 Netmon 或 Wireshark 篩選 Syn-rcvd 封包的這兩種工具： TCP。Flags.Syn = = 1。](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

請注意，針對每個 SYN-RCVD 有來源 （來源） 的連接埠號碼符合目的地連接埠 (DstPort) 的相關通知 (SYN-RCVD/ACK) 中。

若要檢視您的網路連線由 Windows 調整值，請依序展開 [第一次 SYN-RCVD，然後按一下 [相關的 SYN-RCVD/通知  

![圖形，顯示如何符合與 DstPort 來源中的追蹤，以取得時間差異。](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>TCP 閒置時間設定

在過去，大部分的周邊網路設定暫時性的連線，這表示閒置連線通常會終止。 閒置 TCP 工作階段可以藉由 proxy 和防火牆在大於 100 到 300 秒終止。 這是問題，Outlook online 因為它會建立並使用長期的連線，無論或不是閒置。  

當連線會終止 proxy 或防火牆裝置，用戶端明智，並不嘗試使用 Outlook 線上將表示用戶端電腦會嘗試，便會重複替換，恢復從之前先製作一個新的連線。 您可能會在載入頁面上看到擱置中的產品、 提示或效能降低。

#### <a name="tools"></a>工具

- Netmon
- 在 Wireshark

#### <a name="what-to-look-for"></a>要尋找的項目

在 Netmon，查看來回行程時間位移欄位。 來回行程是將要求傳送至伺服器和接收回應回用戶端之間的時間。 檢查用戶端與輸出點 （例如。 用戶端-\> Proxy)，或 Office 365 用戶端 (用戶端-\> Office 365)。 您可以看到此許多封包的類型。

例如，在 Netmon 中的篩選可能看起來像`.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`，或在 Wireshark， `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`。  

> [!TIP]
> 不知道您追蹤中的 IP 位址是否屬於您的 DNS 伺服器？ 請試著查閱在命令列。 按一下 [**開始** \> **執行**\>和輸入**cmd**，或按下**Windows 鍵** \> ，然後輸入**cmd**。 在提示處輸入`nslookup <the IP address from the network trace>`。 若要測試，請使用 nslookup 針對您自己的電腦 IP 位址。 <b0>Office 365 Url 和 IP 位址範圍</b0>，請參閱 < &gt; 以查看 Microsoft 的 IP 範圍的清單。

問題時，預期長時間位移出現，在此情況下 (Outlook Online)，特別是在 TLS:TLS 封包所顯示的應用程式資料傳送過程中 (例如，在 Netmon 中您可以尋找應用程式資料封包透過`.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`)。 您應該會看到的時間內順利進程整個工作階段。 如果重新整理您 Outlook 線上時，您會看到長時間延遲，這可能因重設傳送高程度。

### <a name="latencyround-trip-time"></a>延遲/來回中斷時間

延遲是可以變更根據許多變數，這類升級過時裝置，將大量的使用者新增至網路，以及上的網路連線的其他工作所耗用的整體頻寬百分比的花費量值。

有可用的 Office 365 的頻寬計算器從此[網路規劃和效能調整的 Office 365](network-planning-and-performance.md)頁面。  

測量的連線或您的 ISP 連線頻寬速度的需要嗎？ 請嘗試此網站 （或類似的網站）： [Speedtest 官方網站](https://www.speedtest.net/)及[Pingtest](http://www.pingtest.net/)。

#### <a name="tools"></a>工具

- Ping
- PsPing
- Netmon
- 在 Wireshark

#### <a name="what-to-look-for"></a>要尋找的項目

若要追蹤中追蹤的延遲，您獲益具有 Office 365 中記錄的用戶端電腦 IP 位址和 DNS 伺服器的 IP 位址。 這是目的更輕鬆地追蹤篩選。 如果您透過 proxy 連線，您會需要您用戶端電腦的 IP 位址、 proxy/輸出 IP 位址，以及 Office 365 DNS IP 位址，以方便的工作。  

傳送給 outlook.office365.com 的 ping 要求會告訴您收到要求，資料中心的名稱即使 ping*可能*無法連線至連續 ICMP 封包傳送商標。 如果您使用特定連接埠 (443) 和 PsPing （下載的免費工具），而且可能是使用 IPv4 (-4) 就會平均 round 來回時間傳送封包。 這會適合此 Office 365 服務中，其他 Url like `psping -4 yourSite.sharepoint.com:443`。 事實上，您可以指定的數目較大的範例為取得您平均的嘗試類似的 ping `psping -4 -n 20 yourSite-my.sharepoint.com:443`。  

> [!NOTE]
> PsPing 不會傳送 ICMP 封包。 它會偵測與 TCP 封包透過特定連接埠，所以您可以使用您知道要開啟任何一個。 在 Office 365 中，它會使用 SSL/TLS，請嘗試附加連接埠： 443 以您 PsPing。

![螢幕擷取畫面顯示 ping 與進行相同，但回報 6.5 m s 平均 RTT 443 解析 outlook.office365.com，與 PSPing。](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

如果您進行網路追蹤時載入緩慢執行的 Office 365] 頁面上，您應該篩選的 Netmon 或 Wireshark 追蹤`DNS`。 這是下列其中一個我們要尋找 Ip。  

以下是以篩選要取得的 IP 位址 （和看看 DNS 延遲） 您 Netmon 所採取的步驟。 此範例使用 outlook.office365.com，但也可以使用 SharePoint Online 租用戶 (例如 hithere.sharepoint.com) 的 URL。  

1. Ping URL`ping outlook.office365.com`並在結果中，記錄的名稱和 ping 要求傳送至 DNS 伺服器 IP 位址。
2. 網路追蹤開啟頁面，或執行巨集指令，可讓您的效能問題，或如果您看到 ping，本身，高延遲網路追蹤它。
3. 開啟 DNS 中 Netmon 及篩選追蹤 (此篩選器也在 Wireshark 中, 運作，但寫`-- dns`)。 既然您知道 DNS 伺服器的名稱，從您的 ping 您可能也會篩選像這樣的多個能快速在 Netmon:`DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`像這樣的 Wireshark dns 中，圖文框包含"namnorthwest"。<br/>開啟回應封包，並在 Netmon**圖文框詳細資料**] 視窗中，按一下 [ **DNS** ]，以展開 [如需詳細資訊。 在 [DNS 資訊您可以找到要求皆以在 Office 365 的 DNS 伺服器的 IP 位址。 您將需要這個 IP 位址的下一個步驟 （PsPing 工具）。 移除篩選，以滑鼠右鍵按一下 Netmon 中的 DNS 回應 (**框架摘要** \> **尋找交談** \> **DNS**) 若要查看 DNS 查詢和回應-並存。
4. 在 Netmon，也請注意 [時間位移] 欄中的 DNS 要求和回應之間。 在下一個步驟、 易於安裝和使用[PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx)工具更為非常實用，同時由於 ICMP 通常會封鎖在防火牆，而且 PsPing 精細追蹤延遲 （毫秒）。 PsPing 完成 TCP 連線到地址和連接埠 （在我們案例開啟連接埠 443）。
5. 安裝 PsPing。
6. 開啟命令提示字元 (啟動\>執行\>輸入 cmd 或 Windows 鍵\>輸入 cmd)，將目錄變更至 PsPing 執行 PsPing 命令的安裝所在的目錄。 在 [我的範例中您可以看到我所進行的 c 根目錄 'Qfe' 資料夾您可以執行相同的快速存取。
7. 類型命令，讓您在先前 Netmon 追蹤，包括連接埠號碼，對您針對 Office 365 DNS 伺服器的 IP 位址 PsPing like `psping -n 20 132.245.24.82:445`。 這會為您提供的 20 ping 取樣，而且當 PsPing 停駐點的平均延遲。

如果您正在透過 proxy 伺服器移至 Office 365，是略有不同的步驟。 以您的 proxy 伺服器，以取得平均延遲值以毫秒為單位 proxy/輸出和上一步]，將第一個 PsPing，然後 [執行 PsPing proxy，或電腦上有直接的網際網路連線，以取得缺少的值 （一個 Office 365 和上一步）。  

如果您選擇執行 proxy PsPing，您將有兩個毫秒值： proxy 伺服器或輸出點及 proxy 伺服器到 Office 365 用戶端電腦。 和大功告成 ！ 嗯，還是錄製值。  

如果您在另一個具有直接連線至網際網路的用戶端電腦上執行 PsPing，也就是 proxy，而您會有兩個毫秒值： proxy 伺服器或輸出點，與 Office 365 用戶端電腦的用戶端電腦。 在此情況下，proxy 伺服器或輸出點到 Office 365 用戶端電腦的值減去用戶端電腦的值必須 RTT 數字從您的用戶端電腦將 proxy 伺服器或輸出點，並從 [proxy 伺服器或輸出指向 Office 365。

不過，如果您可以在受影響的位置，直接連線，或略過 proxy 找到的用戶端電腦，您可能會選擇查看是否問題重現那里一開始先和測試之後使用。

延遲，視為 Netmon 追蹤，這些額外的毫秒可以加總，如果有足夠的它們在任何指定的工作階段。  

![Netmon 中的一般延遲，並將 Netmon 預設時間差異欄位新增至框架摘要。](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> 您的 IP 位址可能會不同於 IPs 如下所示，例如，您 ping 可能會傳回類似詳細 157.56.0.0/16 或類似的範圍。 如需 Office 365 所使用的範圍的清單，請參閱[Office 365 Url 和 IP 位址範圍](https://technet.microsoft.com/en-us/library/hh373144.aspx)。

如果您想要搜尋，例如 132.245，請記得要展開 （在此頂端沒有] 按鈕） 的所有節點。

### <a name="proxy-authentication"></a>Proxy 驗證

這僅適用於您如果要透過 proxy 伺服器。 如果不是，您可以略過這些步驟。 運作正常，proxy 驗證應該會發生以毫秒為單位，一致。 您不應該 （例如） 請參閱間歇性效能不佳尖峰使用量時段。  

如果 Proxy 驗證，每當您對 Office 365 以取得資訊進行新的 TCP 連線，您需要通過驗證程序在幕後。 因此，例如時從行事曆切換到 Outlook Online 中的郵件，您會進行驗證。 和在 SharePoint Online 中，如果] 頁面上顯示媒體或資料從多個網站] 或 [位置] 中，您會驗證的每個不同的 TCP 連線所需才能轉譯資料。  

在 Outlook Online 中，您可能會遇到緩慢的載入時間每當您切換行事曆與您的信箱，或 SharePoint Online 中載入速度很慢的頁面。 不過，還有其他此處未列出的徵狀。

Proxy 驗證是在您的輸出 proxy 伺服器上的設定。 如果它與 Office 365 造成的效能問題，您必須請洽詢您網路的小組。  

#### <a name="tools"></a>工具

- Netmon
- 在 Wireshark

#### <a name="what-to-look-for"></a>要尋找的項目

Proxy 驗證發生於每當必須向上，開始新的 TCP 工作階段，通常為檔案或資訊從伺服器要求，或提供資訊。 例如，您可能會看到周圍 HTTP GET 或 HTTP POST 要求的 proxy 驗證。 如果您想要查看您其中的驗證要求您追蹤中的框架，' NTLMSSP 摘要 ' 資料行新增至 Netmon 及篩選的`.property.NTLMSSPSummary`。 若要查看驗證正在多久，新增時間差異欄位。

若要將欄新增至 Netmon:

1. 例如： **Description**欄上按一下滑鼠右鍵。
2. 按一下 [**選擇資料行**。
3. 在清單中找出_NTLMSSP 摘要_和_時間差異_，然後按一下 [**新增]**。
4. 進入新的資料行的位置之前的前面或後面 [_描述_] 欄讓您可以閱讀它們並排顯示。
5. 按一下 [確定]****。

即使您不新增資料行，將運作 Netmon 篩選器。 但您疑難排解更加容易，如果您可以看到您在哪個階段的驗證。

要尋找的執行個體的 Proxy 驗證，務必是 NTLM 的挑戰，或驗證訊息的研究所有的圖文框時出現。 如有必要，以滑鼠右鍵按一下某一種流量和尋找交談\>TCP。 請注意這些交談中的時間差異值。

![Netmon 追蹤顯示 proxy 驗證，由交談篩選。](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

在 proxy 驗證的 4 秒延遲，如 Wireshark 中。 **從上一個顯示的圖文框的時間差異**欄位進行透過以滑鼠右鍵按一下圖文框詳細資料中的相同名稱的欄位和做為資料行中選取 [新增。  <br/> ![Wireshark 中, 您可以透過以滑鼠右鍵按一下圖文框詳細資料中的相同名稱的欄位和做為資料行中選取 [新增進行 '從上一個顯示的圖文框的時間差異' 欄。](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>DNS 的效能

名稱解析 works 最佳和最快速時所花費的地方最用戶端的國家/地區盡可能接近。

如果 DNS 名稱解析正在進行載運到海外，它可以新增頁面載入秒數。 理想狀況下，名稱解析會發生在小於 100 毫秒。 如果不是，您應該進行進一步調查。

> [!TIP]
> 不確定用戶端連線能力在 Office 365 中的運作方式？ 看看的用戶端連線能力參考文件[在這裡](https://technet.microsoft.com/en-us/library/dn741250.aspx)。

#### <a name="tools"></a>工具

- Netmon
- 在 Wireshark
- PsPing

#### <a name="what-to-look-for"></a>要尋找的項目

分析 DNS 的效能是通常是另一項工作的網路追蹤。 不過，PsPing 也是統治，回或取出、 可能的原因很有幫助。

DNS 流量根據 TCP 及 UDP 要求和回應清楚標示出使用識別碼，以符合其特定回應的特定要求協助。 您會看到 DNS 流量，例如，SharePoint Online 使用時的網路名稱或 URL 在網頁上。 為法則，大部分的此流量，除了當轉接區域，執行透過 UDP。

在 Netmon 和 Wireshark 中，將可讓您查看 DNS 流量的最基本篩選只是`dns`。 請務必指定篩選條件時，使用小寫。 清除您的 DNS 解析程式快取，以重現問題，您的用戶端電腦上所顯示的之前，請記得。 例如，如果您有 [首頁] 頁面上的速度很慢 SharePoint Online 頁面載入時，您應該關閉所有瀏覽器、 開啟新的瀏覽器、 啟動追蹤、 清除您的 DNS 解析程式快取，以及瀏覽至您的 SharePoint Online 網站。 一旦整頁解析後，您應該停止，並儲存追蹤。

![在 Netmon 中，DNS 的基本篩選器是 DNS。](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

您想要查看以下位移的時間。 並可能很有幫助將**時間差異**欄位新增至 Netmon 您可以藉由完成下列步驟執行：

1. 例如： **Description**欄上按一下滑鼠右鍵。
2. 按一下 [**選擇資料行**。
3. 在清單中找出_時間差異_，然後按一下 [**新增]**。
4. 進入新欄位置之前的前面或後面 [_描述_] 欄，也可以閱讀並排顯示。
5. 按一下 [確定]****。

如果您發現感興趣的查詢，請考慮隔離以滑鼠右鍵按一下該查詢的圖文框的詳細資訊] 面板中，選擇 [**尋找交談** \> **DNS**。 請注意網路交談面板跳轉 UDP 流量的特定對話其記錄檔中的權限。

![由 DNS、 篩選和使用尋找交談然後 DNS 來縮小結果的 Outlook 線上負載 Netmon 追蹤。](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

在 Wireshark 中您可以讓欄 DNS 時間。 需要您追蹤 （或開啟追蹤） 中 Wireshark 及 filter by `dns`，或更多好心`dns.time`。 按一下任何 DNS 查詢，並在面板中顯示的詳細資訊，請依序展開 [`Domain Name System (response)`詳細資料。 您會看到一個欄位的時間 (例如， `[Time: 0.001111100 seconds]`。 這段時間上按一下滑鼠右鍵，然後選取 [**套用] 做為資料行**。 這會讓您**時間**資料行您追蹤的速度較快排序。 若要排序依遞減值以查看其 DNS 呼叫新資料行上的按一下 [時間最長解決。

[在 Wireshark 中由 (小寫) dns.time 篩選的 SharePoint Online 瀏覽，時間起點為將詳細資料納入欄位和遞增排序起。](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

如果您想要執行的 DNS 解析時間更多調查，請嘗試針對使用 TCP 的 DNS 連接埠的 PsPing (例如， `psping <IP address of DNS server>:53`)。 您仍看到的效能問題？ 如果您這麼做，問題是特定的很可能是特定的更廣泛的網路發出問題比您又打如何解析的 DNS 應用程式。 也值得一提，同樣地，，以 outlook.office365.com 的 ping 會告訴您其中的 Outlook 線上的 DNS 名稱解析正在進行中 (例如，namnorthwest.office365.com outlook)。

如果此問題： 看起來要特定的 DNS，它可能需要連絡您的 IT 部門，以查看 DNS 組態和 DNS 轉寄站進一步調查此問題。

### <a name="proxy-scalability"></a>Proxy 延展性

Office 365 Outlook Online 等服務授與用戶端長期的多個連接。 因此，每位使用者可能使用多個需要較長的生命週期的連線。  

#### <a name="tools"></a>工具

數學  

#### <a name="what-to-look-for"></a>要尋找的項目

沒有網路追蹤或疑難排解工具專屬於這。 相反地，它會根據指定限制和其他變數的頻寬計算。  

### <a name="tcp-max-segment-size"></a>TCP 最大區段大小

位於 SYN-RCVD-SYN-RCVD/通知  執行這項檢查您已採取來確定 TCP 封包會設為執行的最大可能的資料量任何效能網路追蹤中。

請參閱 < 的 1460 位元組資料傳輸的 MSS 為目標。 如果您正在背後的 proxy，或您使用 NAT，請記得在執行這項測試，從用戶端到 proxy/輸出/NAT 和 proxy/輸出/NAT 到 Office 365 為了獲得最佳結果 ！ 這些是不同的 TCP 工作階段。

#### <a name="tools"></a>工具

Netmon

#### <a name="what-to-look-for"></a>要尋找的項目

TCP 最大區段大小 (MSS) 是另一個參數的三種方式信號交換在您的網路追蹤，表示您可以在 SYN-RCVD-SYN-RCVD/ACK 封包中找到所需的資料。 MSS 是若要查看實際相當簡單。

開啟任何效能網路追蹤您有並找出您想要了解，連線或來示範效能問題。

> [!NOTE]
> 如果您查看追蹤，且需要來尋找您交談相關的流量，會依用戶端的 IP 或 proxy 伺服器或輸出點，或兩者的 IP 篩選。 直接移，您將需要 ping 您正在所測試的 Office 365 中的追蹤和篩選器的 IP 位址的 URL。

查看 second-hand 追蹤嗎？ 請嘗試使用篩選器來引導您自己。 在 Netmon，執行搜尋，根據 URL，例如： `Containsbin(framedata, ascii, "sphybridExample")`，記下數目的圖文框。

在 Wireshark 中使用的是`frame contains "sphybridExample"`。 如果您注意到您已經找到 （它可能會顯示為 [PSH，ACK] Wireshark 中） 的遠端 Winsock (RWS) 流量，請記得 RWS 連線可以查看相關 SYN-RCVD-SYN-RCVD/認可之前，即稍早所述。

此時，記錄的圖文框號碼、 卸除篩選、 按一下 [若要查看最接近 SYN.Netmon 中的 [網路交談] 視窗中的**所有流量**

重要的，如果您未收到任何追蹤當時的 IP 位址資訊，請尋找 URL 追蹤中 (的一部分`sphybridExample-my.sharepoint.com`，例如)，可讓您篩選依據的 IP 位址。

追蹤您感興趣看到中尋找的連線。 您可能會由篩選透過 IP 位址，或選取特定的交談 Id 使用網路交談視窗在 Netmon 中的任一掃描追蹤，來執行這項操作。 一旦您已經找到 SYN-RCVD 封包，展開 [TCP （在 Netmon) 或傳輸控制通訊協定 （在 Wireshark) 中 [圖文框的詳細資訊] 面板。 展開 [TCP 選項及 MaxSegmentSize。 找出相關的接收圖文框，依序展開 [TCP 選項和 MaxSegmentSize。 較小的兩個值會是您最大區段大小。 此圖中，我請使用名為 TCP 疑難排解 Netmon 中的內建欄。  

![使用內建欄在 Netmon 中篩選的網路追蹤。](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

內建欄是頂端的 [**圖文框的詳細資訊**] 面板。 （若要切換回標準檢視，再按一下 [**欄**]，，然後選擇 [**時間的時區**）。

![在欄位下拉式清單中尋找 TCP 疑難排解選項 (在框架摘要的頂端)。](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

以下是在 Wireshark 中的已篩選的追蹤。 沒有特定的 MSS 值的篩選器 ( `tcp.options.mss`)。 SYN-RCVD、 SYN-RCVD/ACK、 ACK 信號交換的框架連結底部的 Wireshark 等於圖文框的詳細資訊 （因此框架 47 ACK、 46 SYN-RCVD/ACK 連結、 43 SYN-RCVD 連結） 以方便這類的工作。

![在 Wireshark 中由 tcp.options.mss 篩選的最大區段大小 (MSS) 的篩選的追蹤。](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

如果您需要檢查**選擇性認可**（此矩陣中的下一個主題），不要關閉您追蹤 ！

### <a name="selective-acknowledgment"></a>選擇性認可

位於 SYN-RCVD-SYN-RCVD/通知 必須報告為 SYN-RCVD 和 SYN-RCVD/通知中的許可 選擇性認可 (SACK) 可讓更順暢地重新傳輸的資料封包或封包移遺失時。 裝置可以停用此功能，可能會導致效能問題。

如果您正在背後的 proxy，或您使用 NAT，請記得在執行這項測試，從用戶端到 proxy/輸出/NAT 和 proxy/輸出/NAT 到 Office 365 為了獲得最佳結果 ！ 這些是不同的 TCP 工作階段。

#### <a name="tools"></a>工具

Netmon

#### <a name="what-to-look-for"></a>要尋找的項目

選擇性認可 (SACK) 是另一個參數中的 SYN-RCVD/接收信號交換。 您可以篩選 SYN-RCVD-SYN-RCVD/ACK 許多方式您追蹤。

追蹤您感興趣由掃描追蹤，請參閱篩選的 IP 位址，或按一下 [使用網路交談視窗在 Netmon 中的交談 ID 中尋找的連線。 一旦您已經找到 SYN-RCVD 封包，展開 [TCP 在 Netmon 或 Wireshark 中框架詳細資料] 區段中的傳輸控制通訊協定。 展開 [TCP 選項，然後 SACK。 找出相關的接收圖文框和展開 TCP 選項，以及其 SACK] 欄位。 請確定 SACK 允許 SYN-RCVD 和 SYN-RCVD/通知 Netmon 及 Wireshark 中所見，以下是 SACK 值。

![選擇性認可 (SACK) 在 Netmon 中結果的 tcp.flags.syn = = 1。](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![Wireshark 中所示的 SACK 及篩選器 tcp.flags.syn == 1。](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>DNS Geolocation

其中領域中 Office 365 會嘗試解決您的 DNS 呼叫效果您的連線速度。

在 Outlook Online 中，第一個 DNS 查閱完成後，該 DNS 的位置將用來連線到最接近的資料中心。 您將會連線到 Outlook 線上 CAS 伺服器，用以骨幹網路連線到資料中心 (dC) 儲存您的資料。 這是更快。

當存取 SharePoint Online、 強人出差的使用者會被導向到其作用中的資料中心-，其位置根據其 SPO 租用戶 dC 的首頁基底 (因此，在美國 dC 如果使用者如果 USA 為基礎)。

Lync online 中一個以上的 dC 有作用中的節點，一次。 要求時傳送的 Lync online 執行個體，Microsoft 的 DNS 會決定在世界要求來自何處，並傳回 IP 位址從最接近的地區 dC 其中 Lync online 是作用中。

> [!TIP]
> 若要深入了解用戶端如何連線到 Office 365 的需要嗎？ 看看[用戶端連線](https://technet.microsoft.com/en-us/library/dn741250.aspx)參考文章 （和其很有幫助的圖形）。

#### <a name="tools"></a>工具

- Ping
- PsPing

#### <a name="what-to-look-for"></a>要尋找的項目

在大部分情況下結果中傳回地區性資料中心 (dC) 的 IP 位址的 Microsoft DNS 中應從用戶端的 DNS 伺服器的名稱解析到 Microsoft 的 DNS 伺服器的要求。 這代表您什麼？ 如果您總部位於班加羅爾 （印度），但您的瀏覽器的 Outlook 線上提出要求時，在出差在美國，，Microsoft 的 DNS 伺服器應該處理您的 IP 位址在美國境內-地區性資料中心的資料中心。 如果郵件來自 Outlook 需要時，該資料將會流經 Microsoft 的快速骨幹網路資料中心之間。

如果完成名稱解析為最接近使用者位置開始儘可能 DNS 的運作最快。 如果您是歐洲地區，您要移至 Microsoft 的 DNS 中歐洲 （理想狀況下） 處理歐洲地區資料中心。 移至 [DNS 及 America 的資料中心歐洲的用戶端的效能將會變慢。

對 outlook.office365.com 至判斷其中領域中您的 DNS 要求被路由傳送執行 Ping 工具。 如果您位於歐洲時，您應該會看到類似於 outlook emeawest.office365.com 的回覆。 美洲，預期 outlook namnorthwest.office365.com 類似。

開啟命令提示字元中，用戶端電腦上 (透過開始\>執行\>cmd 或 Windows 鍵\>輸入 cmd)。 輸入 ping outlook.office365.com，然後按 ENTER 鍵。 請記住，如果您想要指定透過 IPv4 ping 指定-4。 您可能無法從 ICMP 封包，取得回覆，但您應該會看到的要求被路由傳送的 DNS 名稱。 如果您想要看到此連線的延遲號碼會嘗試由 ping 傳回伺服器的 IP 位址 PsPing。  

![outlook.office365.com 的 Ping，顯示 outlook-namnorthwest 中的解析。](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![由 ping 傳回給 outlook.office365.com 顯示平均 28 毫秒的延遲的 IP 位址 PSPing。](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 應用程式疑難排解

#### <a name="tools"></a>工具

- Netmon
- HTTPWatch
- 在瀏覽器中的 F12 主控台

我們不涵蓋中特定應用程式疑難排解特定網路的本文中所使用的工具。 您可以找到的資源，但您*可以*使用[此頁面上](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)。

## <a name="related-topics"></a>相關主題

[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)
