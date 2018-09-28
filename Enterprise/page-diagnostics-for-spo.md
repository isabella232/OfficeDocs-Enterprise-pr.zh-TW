---
title: 使用 SharePoint Online 頁面診斷工具
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
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
description: 使用 SharePoint 工具] 頁面上診斷來分析傳統根據建議的最佳作法頁面的 SharePoint Online。
ms.openlocfilehash: 0fc2e16867b54e644d00c57fbfc41d4f7d042f88
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975161"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>使用 SharePoint Online 頁面診斷工具

本文說明如何使用頁面診斷工具來分析您的傳統發佈的頁面和針對**SharePoint Online**中的建議作法的子集的傳統小組網站上的頁面。 
  
不需要啟用的發佈功能的小組網站無法利用的 Cdn 但所有的其餘規則都適用。發佈新增額外負荷，不要開啟只是要為它將會造成負面影響頁面載入次數取得 CDN 功能的發佈功能。
  
> [!IMPORTANT]
> 頁面診斷工具不會執行對文件庫或 system 頁面為此工具的設計檢閱 SharePoint 網站] 頁面。*Allitems.aspx*頁面為系統頁面。如果您嘗試在系統] 頁面上執行工具，您會收到讀取郵件、"此應用程式應只執行 SharePoint 頁面上。 」<br/> ![必須在 SharePoint 頁面上執行](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)<br/>這是不工具中的錯誤如下在評估文件庫或系統頁面沒有值。請瀏覽至 [非系統 SharePoint] 頁面上使用此工具。如果您想要提供意見反應給相關工具請按一下 [關於] 索引標籤並依照[提供意見反應] 連結](https://go.microsoft.com/fwlink/?linkid=874109)。 
  
## <a name="install-the-page-diagnostic-tool"></a>安裝] 頁面上診斷工具

> [!IMPORTANT]
> Microsoft 不會不會讀取資料或造訪、 網站及我們不擷取任何個人資訊、 網站或下載此工具資訊。此工具所記錄的唯一資訊是租用戶名稱、 計數以及是否支援記錄選項有使用此工具會在執行規則。此資訊是 Microsoft 分析何種挑戰正在發生我們客戶及確保未被誤用支援記錄功能。

1. 使用 Chrome 瀏覽器中，請直接開啟[連結至工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 瀏覽器網站儲存](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中開啟 [搜尋並安裝瀏覽器延伸模組。請檢閱中提供的存放區中的 [描述] 頁面上的使用者隱私權原則。當您的瀏覽器中加入工具，將會看到下列權限通知。<br/>![Chrome 儲存區權限](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)<br/>   此通知是備妥因為頁面可能包含來自 SharePoint 外部位置的網頁組件與自訂項目] 頁面上的視的內容。這表示此工具會讀取要求和回應按一下 [開始] 按鈕時，而且只能用於使用中的 [SharePoint] 索引標籤上執行此工具。該資訊會擷取本機的網頁瀏覽器並透過 [匯出至 JSON 連結工具中使用。**未傳送至或由 Microsoft 所擷取資訊。**（此工具會遵守 Microsoft 隱私權原則可存取[此處](https://go.microsoft.com/fwlink/p/?linkid=857875)。）<br/><br/>在工具中的 「 匯出 JSON"功能也是為何需要管理您的下載項目] 權限。請遵循貴公司自己的隱私指導方針之前為結果包含 Url 及可共用您的組織外部的 JSON 檔案可分類為 PII （個人身分資訊）。
    
2. （這是選用的）如果您想要使用此工具 Chrome incognito 模式中，瀏覽至 [副檔名並按一下 [**允許 incognito 中**。
    
3. 瀏覽至 [SharePoint 傳統發佈頁面上的 SharePoint Online 您想要檢閱。我們已允許"延遲載入"的頁面 ； 上的項目因此，**工具不會自動停止**。如果您想要停止集合，您可以按一下 [**停止**。（這是根據跟著所有頁面負載案例的設計）。按一下 [**停止**之前，請確定已完成的網路追蹤資料。否則，您必須部分追蹤。此外，此工具是瀏覽器延伸模組，開啟多個索引標籤或 windows 只允許一個作用中的工具]，一次執行執行個體。這是在瀏覽器延伸模組的限制。 
  
4. 按一下 [副檔名標誌 ![頁面診斷 for SharePoint 標誌](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) 要載入的工具和您將呈現與下列副檔名快顯視窗：<br/> ![頁面診斷工具快顯功能表](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)<br/>啟動及停止作業 follow 會開始當您按一下 [的開始] 頁面會重新載入和集合的基本概念。

請閱讀以下小節以了解更多有關此工具所提供的資訊。

## <a name="what-youll-see-in-the-page-diagnostics-tool"></a>會看到下列內容] 頁面上診斷工具
    
1. [**關於**] 連結將會提供一般指引及本文章包含連結的工具的詳細資料。它也包括 SharePoint 效能建議、 第三方通知及提供有關工具的意見反應] 選項的直接連結。 
    
2. **相互關聯識別碼、 SPRequestDuration、 SPIISLatency**、**頁面載入時間**和**URL**詳細資料資訊且可用於幾個用途。 
    
  - **CorrelationID**為重要元件時使用它可讓這些額外的診斷資料 Microsoft 支援小組。 
    
  - **SPRequestDuration**是處理] 頁面上所需的伺服器時間。如果這次是 long，它不一定表示伺服器已執行錯誤，但可以也反映通話數目和載入推送] 頁面上的伺服器如結構化導覽列中，大型圖像、 大量 API 呼叫無法參與較長的伺服器時間. 
    
  - **SPIISLatency**是以毫秒為單位收到將要求重新載入頁面時在 Web 前端伺服器上所花費的時間。這是要開始處理] 頁面上的延遲的指標，不包括回應的 web 應用程式所需的時間。 
    
  - **頁面載入時間**是所要求的時間來回應已接收和讀取瀏覽器的時間開始頁碼記錄的時間。任何其他時間會影響效能的電腦和瀏覽器載入所花費的時間。 
    
  - **URL** （統一資源定位器） 是目前頁面的網頁位址。 
    
3. [**診斷**] 索引標籤](#how-to-use-the-diagnostic-tab)會列出規則而如果任一加以標示紅色![跨](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)，然後在頁面上所指定的問題。<br/>每個規則具有您按一下 [如果項目為紅色自己 」 的詳細資訊 」 連結。會將會前往背後的規則以及如何修復問題的詳細資料。<br/>![診斷紅色-開啟的規則](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)

4. [**網路追蹤**] 索引標籤](#how-to-use-the-network-trace-tab)會提供詳細資訊] 頁面上建置要求和回應。

## <a name="how-to-use-the-diagnostic-tab"></a>如何使用 [診斷] 索引標籤

1. **標準使用者所執行的核取** 檢查頁面效能不應該執行時為服務帳戶、 系統管理員或網站集合管理員或任何具有較高的權限的帳戶登入。其他的指令碼和功能會載入特別針對這些類型的帳戶，因此不會結果] 頁面上的效能，則為 true 表示法。
    
2. **檢查要求送至 SharePoint** 資料並向伺服器提出的要求數量應該限制為多載] 頁面上會遇到的效能低落。這項檢查驗證 SharePoint 做的要求數目與要求超過 6 要求時將通知。大部分的要求應快取與因此不呼叫每次載入頁面。快取應安裝及使用至少 15 分鐘來減少每個使用者] 頁面上的通話。這是常見的問題並在大多數情況下資料只能變更每天但] 頁面上會檢查並擷取資料的這通常是不必要的每位使用者每個頁面每次。
    
3. **檢查使用 Cdn** 內容傳遞網路 (Cdn) 已提供 Microsoft 與稱過以下是 SharePoint Online 內容傳遞網路。有可用的多種類型以及 like SharePoint Cdn 然後 Cdn Azure 中的不同 CDN 服務。[使用下列指導](https://go.microsoft.com/fwlink/?linkid=873250)。
    
4. **檢查大型圖像大小** 圖像應該適合透過較佳的 web 型別 PNG 如網頁。圖像轉譯您也應該利用以及可使用 SharePoint 中直接。圖像 / 大於 100 kb 將反白顯示的圖像轉譯成無法進行最佳化的網頁。[使用下列指導最佳化的影像](https://go.microsoft.com/fwlink/?linkid=873251)。
    
5. **檢查結構化導覽** 結構化導覽原本被設計用於 SharePoint 內部部署位置無法使用物件快取。結構化導覽不建議用於 SharePoint Online 和應該變更為受管理導覽或自訂提供者。[最佳化導覽使用下列指導方針。](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. **檢查 CBQ 網頁組件**(CBQ-內容查詢網頁組件) 當它周遊每位使用者的每一台載入頁面，查詢中的所有項目內容查詢網頁組件就會產生高的 SQL 負載。不同內部部署安裝、 可用來限制填入此網頁組件所需的查詢數目沒有快取。因此 CBQ 執行速度慢，且會影響整體頁面效能這就是為什麼不應該使用。內容搜尋網頁組件 (CSWP) 作為內容查詢網頁組件的取代。[使用下列指導相關內容搜尋網頁組件](https://go.microsoft.com/fwlink/?linkid=873245)。

## <a name="how-to-use-the-network-trace-tab"></a>如何使用網路追蹤] 索引標籤
    
**網路追蹤**] 索引標籤提供建立頁面時接收到回應要求的詳細的資訊。 

1. **尋找標示為紅色的項目載入時間**。每個要求和回應的效能的色彩編碼，根據其對] 頁面上的整體效能的影響，如下所示：
- 綠色： \< 500 毫秒
- 黃色： 500 1000ms
- 紅色： \> 1000ms
<br/>![網路追蹤](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)<br/>在上面所示映像，紅色的項目用於至預設頁面。它會永遠顯示紅色除非中載入頁面\<1000ms （少於 1 秒）。

2. **測試項目載入時間**。在某些情況下將會有無時間或色彩標記因為項目已由瀏覽器快取。正確地測試此、 開啟頁面、 清除瀏覽器快取和 [**啟動**的會強制"冷 「 頁面負載和是，則為 true 的反射的初始頁面負載。這應該再是相較於"暖 「 頁面負載為，也可協助決定哪些項目會在頁面快取。 
    
3. **共用與其他人可以尋求協助的人員調查問題的相關詳細資料**。若要共用的詳細資訊或與您的開發人員或技術支援人員提供工具中的資訊，請按一下 [**匯出至 JSON** （如上述影像所示）。可讓您下載的結果使用 JSON 檔檢視器可檢視。

> [!IMPORTANT]
> 這些結果包含 Url 與之可分類為 PII （個人身分資訊）。請務必遵循貴組織的指導方針之前散佈該資訊。 

## <a name="engaging-with-microsoft-support"></a>Microsoft 技術支援人員積極參與
   
我們已包含應該使用直接支援案例上效能時只使用**Microsoft 的支援層級功能**。利用這項功能會提供任何福利您在不支援團隊。它將事實上，使執行大幅慢頁面並繼續的使用的功能可能會視為"誤用"的服務。沒有額外資訊時使用此功能在工具的其他資訊新增至服務的記錄。 

不變更為可見不同之處在於您是否已啟用它與由大幅變慢網頁效能通知時間 2-3 的已啟用而造成效能緩慢。它只會相關的特定頁面與該作用中的工作階段。此原因，這應謹慎使用及只有當主動體驗 「 支援小組。

### <a name="to-enable-the-microsoft-support-level-feature"></a>若要啟用 Microsoft 支援層級功能

1. 開啟頁面診斷工具。
2. 在您的鍵盤上按下 l Shift alt 鍵。這會顯示**啟用的支援層級記錄**。 
3. 選取的核取方塊，然後按一下 [**啟動**載入頁面，並產生分析的支援的詳細資訊記錄。<br/>![啟用的支援選項](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
重要元素的這是 CorrelationID 支援小組會再使用該號碼若要解壓縮所需的資訊。請複製 （位於頂端的頁面診斷工具） CorrelationID 並提供可支援為他們無法執行所需的工作不完整的識別碼。
    
## <a name="related-topics"></a>相關主題

[調整 SharePoint Online 效能](tune-sharepoint-online-performance.md)

[調整 Office 365 效能](tune-office-365-performance.md)

[內容傳遞網路](content-delivery-networks.md)
