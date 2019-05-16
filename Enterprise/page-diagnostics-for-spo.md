---
title: 使用 SharePoint Online 頁面診斷工具
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: 使用 SharePoint 工具] 頁面上診斷 SharePoint Online 的分析傳統頁面以建議的最佳作法。
ms.openlocfilehash: a188b5dbe52a92cd536ef7145534288345b74c22
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069509"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>使用 SharePoint Online 頁面診斷工具

本文說明如何使用] 頁面上的診斷工具來分析您的傳統的發佈頁面和頁面傳統的小組在網站上，對**SharePoint Online**中的建議作法子集。 
  
不需要啟用發佈的小組網站不能使用 Cdn 但的其餘規則皆適用。 發佈增加額外負荷，因此不會開啟發佈只以取得 CDN 的功能，因為它會造成負面影響頁面載入時間。

**V1.05 已發行的請注意，因此請更新您的擴充，如果您有它已經安裝**。 如果您不確定您有哪些版本然後請按一下 「 關於 」 連結以確認它。
  
> [!IMPORTANT]
> 頁面診斷工具不會執行對文件庫或系統頁面，因為此工具設計來檢閱 SharePoint 網站頁面。 *Allitems.aspx*頁面是系統頁面。 如果您嘗試在系統] 頁面上執行工具，您會收到讀取郵件、 「 此應用程式應該只執行 SharePoint 頁面上。 」 <br/> ![必須在 SharePoint 頁面上執行](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>在評估文件庫或系統頁面沒有任何值時，這是不工具中的錯誤。 請瀏覽至要使用此工具的非系統 SharePoint 頁面。 如果發生此情況 SharePoint 頁面上然後請檢查主版頁面如我們討論過客戶移除 SharePoint 中繼標籤，然後 [] 頁面上已經不再 SharePoint 頁面。 如果您想要提供的相關意見反應工具請按一下 [關於] 索引標籤，並依照[給予意見] 連結](https://go.microsoft.com/fwlink/?linkid=874109)。 
  
## <a name="install-the-page-diagnostic-tool"></a>安裝] 頁面上的診斷工具

> [!IMPORTANT]
> Microsoft 不會讀取或您造訪的網站的資料和我們無法擷取任何個人資訊、 網站或下載使用此工具的資訊。 僅工具所記錄的資訊是租用戶的名稱，規則計數，以及是否支援記錄的選項有使用時執行此工具。 這項資訊適用於 Microsoft 分析哪些挑戰所經歷我們的客戶，並確定不被誤用支援記錄功能。

1. 使用 Chrome 瀏覽器，請直接開啟[連結至工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 瀏覽器網站儲存](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中開啟搜尋並安裝瀏覽器延伸模組。 請檢閱中提供的存放區中的 [描述] 頁面上的使用者隱私權原則。 當將工具新增至您的瀏覽器中，您會看到下列權限會注意到。<br/>![Chrome 儲存區權限](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   通知是就地，因為頁面可能包含位於 SharePoint 之外根據的網頁組件和自訂項目] 頁面上的位置的內容。 這表示，則工具會讀取要求和回應按下 [開始] 按鈕時，僅適用於使用中的 [SharePoint] 索引標籤上執行此工具。 該資訊的網頁瀏覽器在本機上擷取，並可供您透過 「 匯出工具中的 JSON 連結至。 **未傳送至或由 Microsoft 擷取資訊。** （此工具會遵守 Microsoft 隱私權原則可存取[此處](https://go.microsoft.com/fwlink/p/?linkid=857875)。）<br/><br/>此工具中的 「 匯出至 JSON 」 功能也是為何需要 「 管理您的下載項目 」 權限。 請為結果包含 Url 以及共用您的組織外部的 JSON 檔案可歸類為 PII （個人識別資訊） 之前，遵循貴公司專屬的隱私權指導方針。
    
2. （這是選用的）如果您想要使用此工具 Chrome incognito 模式中，瀏覽至副檔名，然後按一下 [**允許 incognito 中**。
    
3. 瀏覽至 SharePoint 傳統 SharePoint Online 上您想要檢閱的發佈頁面。 我們已允許 「 延遲載入 「 頁面; 上的項目因此，**工具不會自動停止**。 如果您想要停止集合，您可以按一下 [**停止**。 （這是經過設計的所有頁面負載案例跟著）。按一下 [**停止**之前，請確定網路追蹤資料已完成。 否則，您會有部分追蹤。 此外，工具所述的瀏覽器延伸模組，並開啟多個索引標籤或 windows 只允許一個作用中一次執行工具的執行個體。 這是在瀏覽器中的擴充功能的限制。 
  
4. 按一下此分機標誌 ![頁面診斷 for SharePoint 標誌](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) 若要載入的工具，以及您將會出現下列副檔名快顯視窗：<br/> ![頁面診斷工具快顯功能表](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>啟動及停止當您按一下 [的開始] 頁面會重新載入與集合的基本概念會開始的作業追蹤。

請閱讀以下小節以深入了解工具所提供的資訊。

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>您會看到在頁面診斷工具
    
1. [**關於**] 連結將會提供一般指引，包括連結工具的詳細資料回到本文章。 它還包含 SharePoint 效能建議、 協力廠商通知並提供意見反應工具的相關選項的直接連結。 
    
2. **相互關聯識別碼、 SPRequestDuration、 SPIISLatency**、**頁面載入時間**，以及**URL**詳細資料會提供資訊，並可用於幾個用途。 
    
  - **CorrelationID**是一個重要項目時使用 Microsoft 支援小組，因為它可讓他們提取其他診斷資料。 
    
  - **SPRequestDuration**是所採取的處理程序] 頁面上的伺服器時間。 如果這段時間很長，並不一定代表伺服器已不執行，但可以也反映出的通話數和載入推入的網頁伺服器例如結構式導覽列中，大型圖像、 API 呼叫的大量可以參與較長的伺服器時間. 
    
  - **SPIISLatency**是以毫秒為單位收到要求以載入頁面時，在 Web 前端伺服器上所採取的時間。 這是若要開始處理] 頁面上的延遲的指標，而且不會納入的 web 應用程式，以回應所花費的時間。 
    
  - **頁面載入時間**為所要求的時間從頁面以時間已接收到回應，並將其瀏覽器讀取記錄的時間。 任何其他的時間會受到電腦和瀏覽器載入所需時間的效能。 
    
  - **URL** （統一資源定位器） 是目前頁面的網頁地址。 
    
3. [**診斷**] 索引標籤](#how-to-use-the-diagnostic-tab)會列出規則和如果有任何這些標示紅色的![跨](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)，然後在] 頁面上所識別的問題。<br/>每個規則具有您按一下 [如果項目為紅色自己 」 的詳細資訊 」 連結。 會將帶您前往背後該規則，以及如何修復問題的詳細資料。<br/>![診斷紅色-開啟的規則](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. [**網路追蹤**] 索引標籤](#how-to-use-the-network-trace-tab)提供詳細資料] 頁面上的建立要求和回應。

## <a name="how-to-use-the-diagnostic-tab"></a>如何使用 [診斷] 索引標籤

1. **以標準使用者執行的核取** 檢查] 頁面上的效能不應執行時以服務帳戶、 系統管理員或網站集合管理員或任何具有較高權限的帳戶登入。 其他的指令碼和功能會載入特別針對這些類型的帳戶，讓結果不會] 頁面上的效能，則為 true 表示法。
    
2. **請檢查 SharePoint 的要求** 為多載] 頁面上會發生效能不佳，資料並對伺服器的要求數量應該會受到限制。 這項檢查驗證進行至 SharePoint 的要求數目，並要求超過 6 要求時將會通知。 大部分的要求應該快取，因此不會每次載入頁面的呼叫。 快取應該是安裝程式，並利用至少 15 分鐘才會減少的每個使用者] 頁面上的通話。 這是常見的問題並在大多數情況下資料只變更每日但] 頁面上檢查並擷取的資料通常是不需要每位使用者每個頁面每次。
    
3. **請使用 Cdn** 內容傳遞網路 (Cdn) 已提供 Microsoft 與參照的下面是 SharePoint Online 內容傳遞網路。 有不同的 CDN 服務，例如 SharePoint Cdn，然後在 Azure 中的 Cdn 以及可用的多個類型。 [使用下列指導](https://go.microsoft.com/fwlink/?linkid=873250)。
    
4. **檢查大型圖像大小** 圖像應該利用更好的 web 型別，如 PNG 最佳化 web。 影像轉譯您也應該利用，並且是提供在 SharePoint 中直接。 影像 / 大於 100 kb 會反白顯示的圖像轉譯為未最佳化，致使網頁。 [使用下列指導最佳化的影像](https://go.microsoft.com/fwlink/?linkid=873251)。
    
5. **檢查結構式導覽** 結構式導覽原本已設計用於 SharePoint 內部部署位置無法使用物件快取。 結構式導覽建議您不要使用 SharePoint Online 中，而且應該變更為受管理導覽或自訂提供者。 [使用下列指導，以最佳化導覽。](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **檢查有 CBQ 網頁組件**(CBQ-內容查詢網頁組件) 在每個使用者周遊每個載入的頁面，在查詢中的所有項目，則內容查詢網頁組件就會產生高的 SQL 負載。 不同內部部署安裝中，沒有可用的填入此網頁組件所需的查詢數目限制快取。 因此 CBQ 執行速度緩慢，並會影響整體這就是為什麼不應用於利用網頁效能。 請使用內容搜尋網頁組件 (CSWP) 取代了內容查詢網頁組件。 [使用下列指導相關內容搜尋網頁組件](https://go.microsoft.com/fwlink/?linkid=873245)。

## <a name="how-to-use-the-network-trace-tab"></a>如何使用網路追蹤] 索引標籤
    
[**網路追蹤**] 索引標籤提供建立] 頁面上，以及所收到的回應要求的詳細的資訊。 

1. **尋找項目載入時間標示為紅色**。 每個要求和回應的效能會以色彩標示，根據其對整體網頁效能的影響，如下所示：
- 綠色： \< 500 毫秒
- 黃色： 500 1000ms
- 紅色： \> 1000ms
<br/>![網路追蹤](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/> 在上面顯示的圖像，紅色的項目相關的預設頁面。 它將一律顯示紅色除非中載入頁面\<1000ms （少於 1 秒）。

2. **測試項目載入時間**。 在某些情況下會沒有時間] 或 [色彩標記因為項目已由瀏覽器快取。 若要正確測試，開啟 [] 頁面上，清除瀏覽器快取，然後按一下**啟動**時，會強制載入 「 寒冷 」 頁面，而且是初始頁面載入，則為 true 反映。 這應該然後比較 」 暖 「 頁面負載時，也可協助判斷哪些項目會在頁面上快取。 
    
3. **共用與他人可以幫助調查問題的相關詳細資料**。 若要共用的詳細資料或資訊與您的開發人員或技術支援人員提供工具中，按一下 [**匯出至 JSON （如上述影像所示）。** 可讓您將結果，檢視使用 JSON 檔案檢視器下載。

> [!IMPORTANT]
> 這些結果包含的 Url 和，可以分類為 PII （個人識別資訊）。 請務必遵循貴組織的指導方針之前散佈該資訊。 

## <a name="engaging-with-microsoft-support"></a>吸引與 Microsoft 支援服務
   
我們已包含**Microsoft 的支援層級功能**，您應該只能利用直接對效能支援案例。 運用這項功能，將會為您無我們支援小組時提供帶來任何效益。 事實上，它會使執行速度明顯變慢的頁面，並繼續的使用的功能可能會被視為 」 濫用 」 服務。 在工具中使用這項功能，當其他資訊新增至服務中的記錄時，沒有其他資訊。 

不會變更為可見，不同之處在於您是否已啟用它與您] 頁面上的效能將會大幅降低藉由將會通知您 2-3 次較慢的效能，而，已啟用。 它只會與相關的特定頁面及該作用中的工作階段。 基於這個理由，這應該謹慎使用，只有當主動投入與我們的支援小組。

### <a name="to-enable-the-microsoft-support-level-feature"></a>若要啟用 Microsoft 的支援層級功能

1. 開啟網頁診斷工具。
2. 在鍵盤上按下 l Shift alt 鍵。 這會顯示**啟用的支援層級記錄**。 
3. 選取核取方塊，，然後按一下 [**開始**重新載入頁面，並產生分析的支援的詳細資訊記錄。<br/>![啟用的支援選項](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
此重要元素是 CorrelationID 支援小組會接著利用該號碼若要解壓縮所需的資訊。 請將複製的相互關聯識別碼 （位於頁面診斷工具的頂端），然後，提供給支援人員，因為他們不能執行必要的工作而沒有完成的識別碼。
    
## <a name="related-topics"></a>相關主題

[調整 SharePoint Online 效能](tune-sharepoint-online-performance.md)

[調整 Office 365 效能](tune-office-365-performance.md)

[內容傳遞網路](content-delivery-networks.md)
