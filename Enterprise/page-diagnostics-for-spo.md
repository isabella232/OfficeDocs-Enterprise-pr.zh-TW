---
title: 使用 SharePoint Online 頁面診斷工具
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
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
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540170"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a>使用 SharePoint Online 頁面診斷工具

本文說明如何使用頁面診斷工具來分析您的傳統發佈的頁面和針對**SharePoint Online**中的建議作法的子集的傳統小組網站上的頁面。 
  
不需要啟用的發佈功能的小組網站無法利用的 Cdn 但所有的其餘規則都適用。發佈新增額外負荷，不要開啟只是要為它將會造成負面影響頁面載入次數取得 CDN 功能的發佈功能。
  
> [!IMPORTANT]
> 頁面診斷工具不會執行對文件庫或 system 頁面為此工具的設計檢閱 SharePoint 網站] 頁面。*Allitems.aspx*頁面為系統頁面。如果您嘗試在系統] 頁面上執行工具，您會收到讀取"此應用程式應該只在執行 SharePoint 頁面。 」 訊息 >![必須在 SharePoint 頁面上執行](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)
  
> 這是不工具中的錯誤如下在評估文件庫或系統頁面沒有值。請瀏覽至 [非系統 SharePoint] 頁面上使用此工具。如果您想要提供意見反應給相關工具請按一下 [關於] 索引標籤並依照[提供意見反應] 連結](https://go.microsoft.com/fwlink/?linkid=874109)。 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a>如何使用頁面診斷工具
<a name="useit"> </a>

1. 使用 Chrome 瀏覽器中，請直接開啟[連結至工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 瀏覽器網站儲存](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中開啟 [搜尋並安裝瀏覽器延伸模組。 
    
    請檢閱中提供的存放區中的 [描述] 頁面上的使用者隱私權原則。
    
    當您的瀏覽器中加入工具，將會看到下列權限通知。
    
    ![Chrome 儲存區權限](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    此通知是備妥因為頁面可能包含來自 SharePoint 外部位置的網頁組件與自訂項目] 頁面上的視的內容。這表示此工具會讀取要求和回應按一下 [開始] 按鈕時，而且只能用於使用中的 [SharePoint] 索引標籤上執行此工具。該資訊會擷取本機的網頁瀏覽器並透過 [匯出至 JSON 連結工具中使用。**未傳送至或由 Microsoft 所擷取資訊。**
    
    > [!IMPORTANT]
    > Microsoft 不會不會讀取資料或造訪、 網站及我們不擷取任何個人資訊、 網站或下載此工具資訊。此工具所記錄的唯一資訊是租用戶名稱、 計數以及是否支援記錄選項有使用此工具會在執行規則。此資訊是 Microsoft 分析何種挑戰正在發生我們客戶及確保未被誤用支援記錄功能。
  
此工具會遵守 Microsoft 隱私權原則可存取[此處](https://go.microsoft.com/fwlink/p/?linkid=857875)。 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. （選用）如果您想要使用此工具 Chrome incognito 模式中，瀏覽至 [副檔名並按一下 [允許在 incognito]。
    
3. 瀏覽至 [SharePoint 傳統發佈頁面上的 SharePoint Online 您想要檢閱。
    
    > [!IMPORTANT]
    > 我們已允許"延遲載入"的頁面 ； 上的項目因此，**工具不會自動停止**。如果您想要停止集合，您可以按一下 [**停止**。（這是根據跟著所有頁面負載案例的設計） 
  
按一下 [**停止**之前，請確定已完成的網路追蹤資料。否則，您必須部分追蹤。 
  
此外，此工具是瀏覽器延伸模組，開啟多個索引標籤或 windows 只允許一個作用中的工具]，一次執行執行個體。這是在瀏覽器延伸模組的限制。 
  
4. 按一下 [副檔名標誌 ![頁面診斷 for SharePoint 標誌](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) 要載入的工具和您將呈現與下列副檔名快顯視窗： 
    
    ![頁面診斷工具快顯功能表](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    啟動及停止作業 follow 會開始當您按一下 [的開始] 頁面會重新載入和集合的基本概念。
    
5. 第一個連結是**相關**連結提供一般指引和回本文包括連結工具的詳細資料。它也包括 SharePoint 效能建議、 第三方通知及提供有關工具的意見反應] 選項的直接連結。 
    
6. 請先檢閱**相互關聯識別碼、 SPRequestDuration、 SPIISLatency** **、 頁面載入時間與 URL**資訊。（此區段會參考和可用於幾個用途）。 
    
  - **CorrelationID**為重要元件時使用它可讓這些額外的診斷資料 Microsoft 支援小組。 
    
  - **SPRequestDuration**是處理] 頁面上所需的伺服器時間。如果這次是 long，它不一定表示伺服器已執行錯誤，但可以也反映通話數目和載入推送] 頁面上的伺服器如結構化導覽列中，大型圖像、 大量 API 呼叫無法參與較長的伺服器時間. 
    
  - **SPIISLatency**是以毫秒為單位收到將要求重新載入頁面時在 Web 前端伺服器上所花費的時間。這是要開始處理] 頁面上的延遲的指標，不包括回應的 web 應用程式所需的時間。 
    
  - **頁面載入時間**是所要求的時間來回應已接收和讀取瀏覽器的時間開始頁碼記錄的時間。任何其他時間會影響效能的電腦和瀏覽器載入所花費的時間。 
    
  - **URL** （統一資源定位器） 是目前頁面的網頁位址。 
    
7. **診斷] 索引標籤**會列出規則而如果任一加以標示紅色![跨](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)，然後在頁面上所指定的問題。
    
    每個規則有其本身的 「 更多資訊"連結如果您按一下 [在其上時為紅色。會將會前往背後的規則以及如何修復問題的詳細資料。
    
    ![診斷紅色-開啟的規則](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. 檢查執行為標準使用者
  
檢查頁面效能不應該執行時以登入服務帳戶、 系統管理員或網站集合管理員亦帳戶以提高權限的權限。其他的指令碼和功能會載入特別針對這些類型的帳戶並將不會提供的頁面效能，則為 true 表示法。
    
2. Sharepoint 的核取要求
  
資料並向伺服器提出的要求數量應該限制為多載] 頁面上會遇到的效能低落。這項檢查驗證 SharePoint 做的要求數目與要求超過 6 要求時將通知。大部分的要求應快取與因此不呼叫每次載入頁面。快取應安裝及使用至少 15 分鐘來減少每個使用者] 頁面上的通話。這是常見的問題並在大多數情況下資料只能變更每天但] 頁面上會檢查並擷取資料的這通常是不必要的每位使用者每個頁面每次。
    
3. 檢查使用 Cdn
  
內容傳遞網路已提供 Microsoft 與稱過以下是 SharePoint Online 內容傳遞網路。有可用的多種類型以及 like SharePoint Cdn 然後 Cdn Azure 中的不同 CDN 服務。[使用下列指導](https://go.microsoft.com/fwlink/?linkid=873250)。
    
4. 檢查大型圖像大小
  
圖像應該適合透過較佳的 web 型別 PNG 如網頁。圖像轉譯您也應該利用以及可使用 SharePoint 中直接。圖像 / 大於 100 kb 將反白顯示的圖像轉譯成無法進行最佳化的網頁。[使用下列指導最佳化的影像](https://go.microsoft.com/fwlink/?linkid=873251)。
    
5. 檢查結構化導覽
  
結構化導覽原本被設計用於 SharePoint 內部部署位置無法使用物件快取。結構化導覽不建議用於 SharePoint Online 和應該變更為受管理導覽或自訂提供者。[最佳化導覽使用下列指導方針。](https://go.microsoft.com/fwlink/?linkid=873247)
    
6. 檢查 CBQ 網頁組件 (CBQ-內容查詢網頁組件)
  
當它周遊每位使用者的每一台載入頁面，查詢中的所有項目內容查詢網頁組件就會產生高的 SQL 負載。不同內部部署安裝、 可用來限制填入此網頁組件所需的查詢數目沒有快取。因此 CBQ 執行速度慢，且會影響整體頁面效能這就是為什麼不應該使用。內容搜尋網頁組件 (CSWP) 作為內容查詢網頁組件的取代。[使用下列指導相關內容搜尋網頁組件](https://go.microsoft.com/fwlink/?linkid=873245)。
    
8. **網路追蹤] 索引標籤**提供 * * * 來建立頁面時接收到回應要求相關詳細資訊。每個要求和回應的效能的色彩編碼根據其影響整個頁面效能亦綠色\<500 毫秒、 黃色 500 1000ms 與紅色\>1000ms。 
    
    在這個索引標籤上有匯出至 JSON 選項應您想要下載和共用要求及回應詳細資料。
    
    > [!IMPORTANT]
    > 將滑鼠停留在縮短 URL，以檢視完整的 URL。 
  
    ![網路追蹤](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    在此影像中紅色的頁面本身和這將會永遠顯示紅色除非中載入頁面\<1000ms （亦即 1 秒鐘）。
    
    在某些情況下*會有無時間或色彩標記因為項目已由瀏覽器快取*。正確地測試此、 開啟頁面、 清除瀏覽器快取和 [**啟動**的會強制"冷 「 頁面負載和是，則為 true 的反射的初始頁面負載。這應該再是相較於"暖 「 頁面負載為，也可協助決定哪些項目會在頁面快取。 
    
9. 如果您想要與您的開發人員或支援人員共用這些詳細資料] 或 [資訊然後您可以按一下 「 匯出 JSON"如同上面的圖像及，將會下載結果。請注意該檔案可以再開啟使用 JSON 檔檢視器。
    
    > [!IMPORTANT]
    > 這些結果將會包含的 URL 與因此包含 PII （個人身分資訊） 與您應該遵循貴公司指導方針之前散佈該資訊。 
  
10. 我們已包含應該使用直接支援案例上效能時只使用**Microsoft 的支援層級功能**。利用這項功能會提供任何福利您在不支援團隊。它將事實上，使執行大幅慢頁面並繼續的使用的功能可能會視為"誤用"的服務。沒有額外資訊時使用此功能在工具的其他資訊新增至服務的記錄。 
    
    不變更為可見不同之處在於您是否已啟用它與由大幅變慢網頁效能通知時間 2-3 的已啟用而造成效能緩慢。它只會相關的特定頁面與該作用中的工作階段。此原因，這應謹慎使用及只有當主動體驗 「 支援小組。
    
    若要啟用此功能請開啟 「 工具並使用 ALT-Shift-L 其中會顯示"啟用支援層級記錄 」。按一下 [核取方塊，然後按一下 [開始重新載入頁面，並產生分析的支援的詳細資訊記錄]。
    
    ![啟用的支援選項](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    重要元素的這是 CorrelationID 支援小組會再使用該號碼若要解壓縮所需的資訊。請將複製的相互關聯識別碼並提供可支援為他們無法執行所需的工作不完整的識別碼。
    

