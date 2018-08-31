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
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a><span data-ttu-id="04e40-103">使用 SharePoint Online 頁面診斷工具</span><span class="sxs-lookup"><span data-stu-id="04e40-103">Use the Page Diagnostics tool for SharePoint Online</span></span>

<span data-ttu-id="04e40-104">本文說明如何使用頁面診斷工具來分析您的傳統發佈的頁面和針對**SharePoint Online**中的建議作法的子集的傳統小組網站上的頁面。</span><span class="sxs-lookup"><span data-stu-id="04e40-104">This article describes how you can use the Page Diagnostic tool to analyze your classic publishing pages and pages on classic team sites, against a subset of recommended practices in **SharePoint Online**.</span></span> 
  
<span data-ttu-id="04e40-p101">不需要啟用的發佈功能的小組網站無法利用的 Cdn 但所有的其餘規則都適用。發佈新增額外負荷，不要開啟只是要為它將會造成負面影響頁面載入次數取得 CDN 功能的發佈功能。</span><span class="sxs-lookup"><span data-stu-id="04e40-p101">Team sites that don't have Publishing enabled cannot make use of CDNs but all of the remaining rules are applicable. Publishing adds additional overhead so do not turn on Publishing just to get the CDN functionality as it will negatively impact page load times.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="04e40-p102">頁面診斷工具不會執行對文件庫或 system 頁面為此工具的設計檢閱 SharePoint 網站] 頁面。*Allitems.aspx*頁面為系統頁面。如果您嘗試在系統] 頁面上執行工具，您會收到讀取"此應用程式應該只在執行 SharePoint 頁面。 」 訊息 >![必須在 SharePoint 頁面上執行](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</span><span class="sxs-lookup"><span data-stu-id="04e40-p102">The Page Diagnostics tool will not run against document libraries or system pages, as the tool is designed to review SharePoint site pages. An  *allitems.aspx*  page is a system page. If you attempt to run the tool on a system page, you will get a message that reads, "This application should only be run on SharePoint pages." > ![Must run on a  SharePoint page](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</span></span>
  
> <span data-ttu-id="04e40-p103">這是不工具中的錯誤如下在評估文件庫或系統頁面沒有值。請瀏覽至 [非系統 SharePoint] 頁面上使用此工具。如果您想要提供意見反應給相關工具請按一下 [關於] 索引標籤並依照[提供意見反應] 連結](https://go.microsoft.com/fwlink/?linkid=874109)。</span><span class="sxs-lookup"><span data-stu-id="04e40-p103">This is not an error in the tool as there is no value in assessing libraries or system pages. Please navigate to a non-system SharePoint page to use the tool. Should you wish to give feedback about the tool please click the About tab and follow the [give feedback link](https://go.microsoft.com/fwlink/?linkid=874109).</span></span> 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a><span data-ttu-id="04e40-114">如何使用頁面診斷工具</span><span class="sxs-lookup"><span data-stu-id="04e40-114">How to use the Page Diagnostic tool</span></span>
<span data-ttu-id="04e40-115"><a name="useit"> </a></span><span class="sxs-lookup"><span data-stu-id="04e40-115"></span></span>

1. <span data-ttu-id="04e40-116">使用 Chrome 瀏覽器中，請直接開啟[連結至工具](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)或[Chrome 瀏覽器網站儲存](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint)中開啟 [搜尋並安裝瀏覽器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="04e40-116">Using a Chrome browser, open the [link to the tool](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) directly or open the Search in the [Chrome Browser WebStore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) and install the browser extension.</span></span> 
    
    <span data-ttu-id="04e40-117">請檢閱中提供的存放區中的 [描述] 頁面上的使用者隱私權原則。</span><span class="sxs-lookup"><span data-stu-id="04e40-117">Please review the User Privacy Policy provided on the description page in the store.</span></span>
    
    <span data-ttu-id="04e40-118">當您的瀏覽器中加入工具，將會看到下列權限通知。</span><span class="sxs-lookup"><span data-stu-id="04e40-118">When adding the tool to your browser, you will see the following permissions notice.</span></span>
    
    ![Chrome 儲存區權限](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    <span data-ttu-id="04e40-p104">此通知是備妥因為頁面可能包含來自 SharePoint 外部位置的網頁組件與自訂項目] 頁面上的視的內容。這表示此工具會讀取要求和回應按一下 [開始] 按鈕時，而且只能用於使用中的 [SharePoint] 索引標籤上執行此工具。該資訊會擷取本機的網頁瀏覽器並透過 [匯出至 JSON 連結工具中使用。**未傳送至或由 Microsoft 所擷取資訊。**</span><span class="sxs-lookup"><span data-stu-id="04e40-p104">This notice is in place because a page may contain content from locations outside of SharePoint depending on the webparts and customizations on the page. This means that the tool will read the requests and responses when the start button is clicked and only for the active SharePoint tab where the tool is running. That information is captured locally by the web browser and is available to you via the Export to JSON link in the tool. **The information is not sent to or captured by Microsoft.**</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="04e40-p105">Microsoft 不會不會讀取資料或造訪、 網站及我們不擷取任何個人資訊、 網站或下載此工具資訊。此工具所記錄的唯一資訊是租用戶名稱、 計數以及是否支援記錄選項有使用此工具會在執行規則。此資訊是 Microsoft 分析何種挑戰正在發生我們客戶及確保未被誤用支援記錄功能。</span><span class="sxs-lookup"><span data-stu-id="04e40-p105">Microsoft does not read the data or websites you visit, and we do not capture any personal information, website or download information with this tool. The only information logged by the tool is the Tenant name, Rule count and whether the support logging option has been utilized when the tool is run. This information is for Microsoft to analyze what challenges are being experienced by our Customers and to ensure the Support logging capability is not being misused.</span></span>
  
<span data-ttu-id="04e40-127">此工具會遵守 Microsoft 隱私權原則可存取[此處](https://go.microsoft.com/fwlink/p/?linkid=857875)。</span><span class="sxs-lookup"><span data-stu-id="04e40-127">The tool respects the Microsoft Privacy policy accessible [here](https://go.microsoft.com/fwlink/p/?linkid=857875).</span></span> 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. <span data-ttu-id="04e40-128">（選用）如果您想要使用此工具 Chrome incognito 模式中，瀏覽至 [副檔名並按一下 [允許在 incognito]。</span><span class="sxs-lookup"><span data-stu-id="04e40-128">(Optional) If you want to use the tool in Chrome incognito mode, navigate to the extension and click "allow in incognito".</span></span>
    
3. <span data-ttu-id="04e40-129">瀏覽至 [SharePoint 傳統發佈頁面上的 SharePoint Online 您想要檢閱。</span><span class="sxs-lookup"><span data-stu-id="04e40-129">Navigate to the SharePoint classic publishing page on SharePoint Online that you would like to review.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="04e40-p106">我們已允許"延遲載入"的頁面 ； 上的項目因此，**工具不會自動停止**。如果您想要停止集合，您可以按一下 [**停止**。（這是根據跟著所有頁面負載案例的設計）</span><span class="sxs-lookup"><span data-stu-id="04e40-p106">We have allowed for "delay loading" of items on pages; therefore, the **tool will not stop automatically**. Should you wish to stop collection, you can click **Stop**. (This is by design to cater for all page load scenarios)</span></span> 
  
<span data-ttu-id="04e40-p107">按一下 [**停止**之前，請確定已完成的網路追蹤資料。否則，您必須部分追蹤。</span><span class="sxs-lookup"><span data-stu-id="04e40-p107">Before you click **Stop**, make sure that the network trace data is complete. Otherwise, you will have a partial trace.</span></span> 
  
<span data-ttu-id="04e40-p108">此外，此工具是瀏覽器延伸模組，開啟多個索引標籤或 windows 只允許一個作用中的工具]，一次執行執行個體。這是在瀏覽器延伸模組的限制。</span><span class="sxs-lookup"><span data-stu-id="04e40-p108">Additionally, the tool is a Browser Extension, and opening multiple tabs or windows will only allow one active instance of the tool to be run at one time. This is a limitation of extensions in the browser.</span></span> 
  
4. <span data-ttu-id="04e40-137">按一下 [副檔名標誌</span><span class="sxs-lookup"><span data-stu-id="04e40-137">Click on the Extension logo</span></span> ![頁面診斷 for SharePoint 標誌](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) <span data-ttu-id="04e40-139">要載入的工具和您將呈現與下列副檔名快顯視窗：</span><span class="sxs-lookup"><span data-stu-id="04e40-139">to load the tool and you will be presented with the following extension popup window:</span></span> 
    
    ![頁面診斷工具快顯功能表](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    <span data-ttu-id="04e40-141">啟動及停止作業 follow 會開始當您按一下 [的開始] 頁面會重新載入和集合的基本概念。</span><span class="sxs-lookup"><span data-stu-id="04e40-141">Start and stop operations follow the basic concept of when you click start the page will reload and collection will begin.</span></span>
    
5. <span data-ttu-id="04e40-p109">第一個連結是**相關**連結提供一般指引和回本文包括連結工具的詳細資料。它也包括 SharePoint 效能建議、 第三方通知及提供有關工具的意見反應] 選項的直接連結。</span><span class="sxs-lookup"><span data-stu-id="04e40-p109">The first link is the **About** link and will provide general guidance and details regarding the tool including a link back to this article. It also includes a direct link to SharePoint Performance recommendations, a Third Party notice and an option to provide feedback about the tool.</span></span> 
    
6. <span data-ttu-id="04e40-p110">請先檢閱**相互關聯識別碼、 SPRequestDuration、 SPIISLatency** **、 頁面載入時間與 URL**資訊。（此區段會參考和可用於幾個用途）。</span><span class="sxs-lookup"><span data-stu-id="04e40-p110">Review the **Correlation ID, SPRequestDuration, SPIISLatency** **, Page load time and URL** information. (This section is informational and can be used for a few purposes.)</span></span> 
    
  - <span data-ttu-id="04e40-146">**CorrelationID**為重要元件時使用它可讓這些額外的診斷資料 Microsoft 支援小組。</span><span class="sxs-lookup"><span data-stu-id="04e40-146">**CorrelationID** is an important element when working with the Microsoft Support Teams as it allows them to pull additional diagnostic data.</span></span> 
    
  - <span data-ttu-id="04e40-p111">**SPRequestDuration**是處理] 頁面上所需的伺服器時間。如果這次是 long，它不一定表示伺服器已執行錯誤，但可以也反映通話數目和載入推送] 頁面上的伺服器如結構化導覽列中，大型圖像、 大量 API 呼叫無法參與較長的伺服器時間.</span><span class="sxs-lookup"><span data-stu-id="04e40-p111">**SPRequestDuration** is the server time taken to process the page. If this time is long, it does not necessarily mean that the server was performing badly but can also reflect the number of calls and load pushed by the page to the server e.g. Structural Navigation, large images, lots of API calls could all contribute to longer server time.</span></span> 
    
  - <span data-ttu-id="04e40-p112">**SPIISLatency**是以毫秒為單位收到將要求重新載入頁面時在 Web 前端伺服器上所花費的時間。這是要開始處理] 頁面上的延遲的指標，不包括回應的 web 應用程式所需的時間。</span><span class="sxs-lookup"><span data-stu-id="04e40-p112">**SPIISLatency** is the time in milliseconds taken on the Web Front End Server when it receives the request to load the page. This is an indicator of latency to start processing the page and does not include the time taken for the web application to respond.</span></span> 
    
  - <span data-ttu-id="04e40-p113">**頁面載入時間**是所要求的時間來回應已接收和讀取瀏覽器的時間開始頁碼記錄的時間。任何其他時間會影響效能的電腦和瀏覽器載入所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="04e40-p113">**Page load time** is the time recorded by the page from the time of the request to the time the response was received and read by the browser. Any additional time is affected by the performance of the computer and the time it takes for the browser to load.</span></span> 
    
  - <span data-ttu-id="04e40-153">**URL** （統一資源定位器） 是目前頁面的網頁位址。</span><span class="sxs-lookup"><span data-stu-id="04e40-153">The **URL** (Uniform Resource Locator) is the web address of the current page.</span></span> 
    
7. <span data-ttu-id="04e40-154">**診斷] 索引標籤**會列出規則而如果任一加以標示紅色![跨](media/9859ac84-be43-4eae-984c-e0e827f5a228.png)，然後在頁面上所指定的問題。</span><span class="sxs-lookup"><span data-stu-id="04e40-154">The **Diagnostic tab** will list the rules and if any of them are marked with a red ![Cross](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), then there are issues identified on the page.</span></span>
    
    <span data-ttu-id="04e40-p114">每個規則有其本身的 「 更多資訊"連結如果您按一下 [在其上時為紅色。會將會前往背後的規則以及如何修復問題的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="04e40-p114">Each rule has its own "more info" link if you click on it when it is red. That will take you to the details behind that rule and how to remediate the issue.</span></span>
    
    ![診斷紅色-開啟的規則](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. <span data-ttu-id="04e40-158">檢查執行為標準使用者</span><span class="sxs-lookup"><span data-stu-id="04e40-158">Check Running as Standard User</span></span>
  
<span data-ttu-id="04e40-p115">檢查頁面效能不應該執行時以登入服務帳戶、 系統管理員或網站集合管理員亦帳戶以提高權限的權限。其他的指令碼和功能會載入特別針對這些類型的帳戶並將不會提供的頁面效能，則為 true 表示法。</span><span class="sxs-lookup"><span data-stu-id="04e40-p115">Checking page performance should not be performed when logged in as a Service Account, Administrator or Site Collection Administrator i.e. an account with elevated privileges. Additional scripts and functionality is loaded specifically for those types of accounts and will not provide a true representation of the page performance.</span></span>
    
2. <span data-ttu-id="04e40-161">Sharepoint 的核取要求</span><span class="sxs-lookup"><span data-stu-id="04e40-161">Check Requests to SharePoint</span></span>
  
<span data-ttu-id="04e40-p116">資料並向伺服器提出的要求數量應該限制為多載] 頁面上會遇到的效能低落。這項檢查驗證 SharePoint 做的要求數目與要求超過 6 要求時將通知。大部分的要求應快取與因此不呼叫每次載入頁面。快取應安裝及使用至少 15 分鐘來減少每個使用者] 頁面上的通話。這是常見的問題並在大多數情況下資料只能變更每天但] 頁面上會檢查並擷取資料的這通常是不必要的每位使用者每個頁面每次。</span><span class="sxs-lookup"><span data-stu-id="04e40-p116">The amount of data and requests made to the server should be limited as an overloaded page will experience poor performance. This check verifies the number of requests being made to SharePoint and will advise when the requests exceed 6 requests. Most requests should be cached and therefore not called for every page load. Cache should be setup and utilized for at least 15 minutes to reduce the amount of calls to a page by each and every User. This is a common problem and in most cases data only changes daily but the page checks and fetches data each time for each page for each user which is often unnecessary.</span></span>
    
3. <span data-ttu-id="04e40-167">檢查使用 Cdn</span><span class="sxs-lookup"><span data-stu-id="04e40-167">Check using CDNs</span></span>
  
<span data-ttu-id="04e40-p117">內容傳遞網路已提供 Microsoft 與稱過以下是 SharePoint Online 內容傳遞網路。有可用的多種類型以及 like SharePoint Cdn 然後 Cdn Azure 中的不同 CDN 服務。[使用下列指導](https://go.microsoft.com/fwlink/?linkid=873250)。</span><span class="sxs-lookup"><span data-stu-id="04e40-p117">Content Delivery networks have been provided by Microsoft and the ones referred to here are the SharePoint Online Content Delivery Networks. There are multiple types available as well as different CDN services like SharePoint CDNs and then CDNs in Azure. [Use the following guidance](https://go.microsoft.com/fwlink/?linkid=873250).</span></span>
    
4. <span data-ttu-id="04e40-171">檢查大型圖像大小</span><span class="sxs-lookup"><span data-stu-id="04e40-171">Check for Large Image Sizes</span></span>
  
<span data-ttu-id="04e40-p118">圖像應該適合透過較佳的 web 型別 PNG 如網頁。圖像轉譯您也應該利用以及可使用 SharePoint 中直接。圖像 / 大於 100 kb 將反白顯示的圖像轉譯成無法進行最佳化的網頁。[使用下列指導最佳化的影像](https://go.microsoft.com/fwlink/?linkid=873251)。</span><span class="sxs-lookup"><span data-stu-id="04e40-p118">Images should be optimized for web by utilizing better web types like PNG. Image renditions should also be utilized and is available in SharePoint directly. Images / image renditions larger than 100kb will be highlighted as not optimized for web. [Use the following guidance for optimizing images](https://go.microsoft.com/fwlink/?linkid=873251).</span></span>
    
5. <span data-ttu-id="04e40-176">檢查結構化導覽</span><span class="sxs-lookup"><span data-stu-id="04e40-176">Check for Structural Navigation</span></span>
  
<span data-ttu-id="04e40-p119">結構化導覽原本被設計用於 SharePoint 內部部署位置無法使用物件快取。結構化導覽不建議用於 SharePoint Online 和應該變更為受管理導覽或自訂提供者。[最佳化導覽使用下列指導方針。](https://go.microsoft.com/fwlink/?linkid=873247)</span><span class="sxs-lookup"><span data-stu-id="04e40-p119">Structural Navigation was originally designed for use in SharePoint on-Premises where object cache could be utilized. Structural Navigation is not recommended for use in SharePoint Online and should be changed to Managed Navigation or a Custom Provider. [Use the following guidance for optimizing navigation.](https://go.microsoft.com/fwlink/?linkid=873247)</span></span>
    
6. <span data-ttu-id="04e40-180">檢查 CBQ 網頁組件 (CBQ-內容查詢網頁組件)</span><span class="sxs-lookup"><span data-stu-id="04e40-180">Check for CBQ WebPart (CBQ - Content by Query WebPart)</span></span>
  
<span data-ttu-id="04e40-p120">當它周遊每位使用者的每一台載入頁面，查詢中的所有項目內容查詢網頁組件就會產生高的 SQL 負載。不同內部部署安裝、 可用來限制填入此網頁組件所需的查詢數目沒有快取。因此 CBQ 執行速度慢，且會影響整體頁面效能這就是為什麼不應該使用。內容搜尋網頁組件 (CSWP) 作為內容查詢網頁組件的取代。[使用下列指導相關內容搜尋網頁組件](https://go.microsoft.com/fwlink/?linkid=873245)。</span><span class="sxs-lookup"><span data-stu-id="04e40-p120">The Content by Query WebPart generates a high SQL load as it traverses all items in the query for each and every page load, for each User. Unlike an on-Premises installation, there is no cache available to limit the number of queries needed to populate this WebPart. As such CBQ performs slowly and impacts overall page performance which is why it should not be utilized. Please use the Content Search WebPart (CSWP) as the replacement for the Content Query WebPart. [Use the following guidance related to the Content Search WebPart](https://go.microsoft.com/fwlink/?linkid=873245).</span></span>
    
8. <span data-ttu-id="04e40-p121">**網路追蹤] 索引標籤**提供 \* \* \* 來建立頁面時接收到回應要求相關詳細資訊。每個要求和回應的效能的色彩編碼根據其影響整個頁面效能亦綠色\<500 毫秒、 黃色 500 1000ms 與紅色\>1000ms。</span><span class="sxs-lookup"><span data-stu-id="04e40-p121">The **Network Trace tab** provides **** detailed information about the requests to build the page as well as the responses received. The performance of each request and response are color coded based on their impact on the overall page performance i.e. Green \< 500ms, Yellow 500-1000ms and Red \> 1000ms.</span></span> 
    
    <span data-ttu-id="04e40-188">在這個索引標籤上有匯出至 JSON 選項應您想要下載和共用要求及回應詳細資料。</span><span class="sxs-lookup"><span data-stu-id="04e40-188">On this tab there is an Export to JSON option should you wish to download and share the request and response details.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="04e40-189">將滑鼠停留在縮短 URL，以檢視完整的 URL。</span><span class="sxs-lookup"><span data-stu-id="04e40-189">Hover over the shortened URL to view the complete URL.</span></span> 
  
    ![網路追蹤](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    <span data-ttu-id="04e40-191">在此影像中紅色的頁面本身和這將會永遠顯示紅色除非中載入頁面\<1000ms （亦即 1 秒鐘）。</span><span class="sxs-lookup"><span data-stu-id="04e40-191">In this image the Red is the page itself and that will always show red unless the page loads in \< 1000ms (i.e. 1 second).</span></span>
    
    <span data-ttu-id="04e40-p122">在某些情況下*會有無時間或色彩標記因為項目已由瀏覽器快取*。正確地測試此、 開啟頁面、 清除瀏覽器快取和 [**啟動**的會強制"冷 「 頁面負載和是，則為 true 的反射的初始頁面負載。這應該再是相較於"暖 「 頁面負載為，也可協助決定哪些項目會在頁面快取。</span><span class="sxs-lookup"><span data-stu-id="04e40-p122">In some cases  *there will be no time or color indicator because the items have already been cached by the browser*  . To test this correctly, open the page, clear browser cache, and then click **Start** as that will force a "cold" page load and be a true reflection of the initial page load. This should then be compared to the "warm" page load as that will also help determine what items are being cached on the page.</span></span> 
    
9. <span data-ttu-id="04e40-p123">如果您想要與您的開發人員或支援人員共用這些詳細資料] 或 [資訊然後您可以按一下 「 匯出 JSON"如同上面的圖像及，將會下載結果。請注意該檔案可以再開啟使用 JSON 檔檢視器。</span><span class="sxs-lookup"><span data-stu-id="04e40-p123">If you wish to share these details or information with your developers or a Support person then you can click "Export to JSON" as per the above image and that will download the results. Please note that the file can then be opened using a JSON file viewer.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="04e40-197">這些結果將會包含的 URL 與因此包含 PII （個人身分資訊） 與您應該遵循貴公司指導方針之前散佈該資訊。</span><span class="sxs-lookup"><span data-stu-id="04e40-197">These results will contain the URL's and therefore contains PII (Personally Identifiable Information) and you should follow your Company guidelines before distributing that information.</span></span> 
  
10. <span data-ttu-id="04e40-p124">我們已包含應該使用直接支援案例上效能時只使用**Microsoft 的支援層級功能**。利用這項功能會提供任何福利您在不支援團隊。它將事實上，使執行大幅慢頁面並繼續的使用的功能可能會視為"誤用"的服務。沒有額外資訊時使用此功能在工具的其他資訊新增至服務的記錄。</span><span class="sxs-lookup"><span data-stu-id="04e40-p124">We have included a **Microsoft Support level feature** that should only be utilized when working directly on a Support Case for performance. Utilizing this feature will provide no benefit to you when used without our Support team. It will in fact make the page perform significantly slower and continued use of the feature may be considered "misuse" of the service. There is no additional information when using this feature in the tool as the additional information is added to the logging in the service.</span></span> 
    
    <span data-ttu-id="04e40-p125">不變更為可見不同之處在於您是否已啟用它與由大幅變慢網頁效能通知時間 2-3 的已啟用而造成效能緩慢。它只會相關的特定頁面與該作用中的工作階段。此原因，這應謹慎使用及只有當主動體驗 「 支援小組。</span><span class="sxs-lookup"><span data-stu-id="04e40-p125">No change is visible except that you will be notified that you have enabled it and your page performance will be significantly degraded by 2-3 times slower performance whilst that is enabled. It will only be relevant for the particular page and that active session. For this reason, this should be used sparingly and only when actively engaged with our Support Team.</span></span>
    
    <span data-ttu-id="04e40-p126">若要啟用此功能請開啟 「 工具並使用 ALT-Shift-L 其中會顯示"啟用支援層級記錄 」。按一下 [核取方塊，然後按一下 [開始重新載入頁面，並產生分析的支援的詳細資訊記錄]。</span><span class="sxs-lookup"><span data-stu-id="04e40-p126">To enable the feature please open the tool and use ALT-Shift-L which will then display "Enable support level logging". Click the checkbox and then click start to reload the page and generate verbose logging for Support to analyze.</span></span>
    
    ![啟用的支援選項](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    <span data-ttu-id="04e40-p127">重要元素的這是 CorrelationID 支援小組會再使用該號碼若要解壓縮所需的資訊。請將複製的相互關聯識別碼並提供可支援為他們無法執行所需的工作不完整的識別碼。</span><span class="sxs-lookup"><span data-stu-id="04e40-p127">An important element for this is the CorrelationID as the Support team will then utilize that number to extract the information needed. Please copy the CorrelationID and provide that to Support as they cannot perform the required work without the complete ID.</span></span>
    

