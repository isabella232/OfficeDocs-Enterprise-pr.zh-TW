---
title: 在 SharePoint Online 新式網站頁面中最佳化網頁組件效能
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/6/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 深入了解如何在 SharePoint Online 新式網站頁面中最佳化 網頁組件效能。
ms.openlocfilehash: 00a21adbd7971e86d23e1e45ee850ab52f46004a
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814201"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="bbbae-103">在 SharePoint Online 新式網站頁面中最佳化網頁組件效能</span><span class="sxs-lookup"><span data-stu-id="bbbae-103">Optimize web part performance in SharePoint Online modern site pages</span></span>

<span data-ttu-id="bbbae-104">SharePoint Online 新式網站頁面包含網頁組件，對整體頁面載入時間有影響。</span><span class="sxs-lookup"><span data-stu-id="bbbae-104">SharePoint Online modern site pages contain web parts that can contribute to overall page load times.</span></span> <span data-ttu-id="bbbae-105">本文可協助您了解如何判斷頁面中的網頁組件如何影響使用者察覺延遲，以及如何修復常見問題。</span><span class="sxs-lookup"><span data-stu-id="bbbae-105">This article will help you understand how to determine how web parts in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="bbbae-106">如需有關 SharePoint Online 新式入口網站效能的詳細資訊，請參閱 [SharePoint 新式體驗中的效能](https://docs.microsoft.com/sharepoint/modern-experience-performance)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a><span data-ttu-id="bbbae-107">使用「適用於 SharePoint 的頁面診斷」工具來分析網頁組件</span><span class="sxs-lookup"><span data-stu-id="bbbae-107">Use the Page Diagnostics for SharePoint tool to analyze web parts</span></span>

<span data-ttu-id="bbbae-108">**適用於 SharePoint 的頁面診斷工具**是 Chrome 和 [Microsoft Edge 77 版或更新版本](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)的瀏覽器擴充功能，您可以用來分析 SharePoint 新式與傳統發佈網站頁面。</span><span class="sxs-lookup"><span data-stu-id="bbbae-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="bbbae-109">該工具會針對每個分析頁面提供一份報告，顯示頁面如何針對定義的效能準則組執行。</span><span class="sxs-lookup"><span data-stu-id="bbbae-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="bbbae-110">若要安裝及了解「適用於 SharePoint 的頁面診斷」工具，請造訪[使用適用於 SharePoint Online 的頁面診斷工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="bbbae-111">當您使用「適用於 SharePoint 的頁面診斷」工具分析 SharePoint 網站頁面時，您可以在 [診斷測試]__ 窗格的 [網頁組件影響頁面載入時間]\*\*\*\* 結果中，看到超過基準計量的網頁組件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bbbae-111">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts that exceed the baseline metric in the **Web parts are impacting page load time** result in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="bbbae-112">可能的結果包括：</span><span class="sxs-lookup"><span data-stu-id="bbbae-112">Possible results include:</span></span>

- <span data-ttu-id="bbbae-113">**需要注意** (紅色)：載入耗時比**兩**秒還要久的任何_自訂_網頁組件。</span><span class="sxs-lookup"><span data-stu-id="bbbae-113">**Attention required** (red): Any _custom_ web part that takes longer than **two** seconds to load.</span></span> <span data-ttu-id="bbbae-114">測試結果中顯示的載入時間總計會依據模組載入、消極式載入、初始、轉譯來細分。</span><span class="sxs-lookup"><span data-stu-id="bbbae-114">Total load time as displayed in test results is broken down by module load, lazy load, init and render.</span></span>
- <span data-ttu-id="bbbae-115">**改善機會** (黃色)：可能會影響頁面載入時間的項目會顯示在此區段，應該加以檢閱及監控。</span><span class="sxs-lookup"><span data-stu-id="bbbae-115">**Improvement opportunities** (yellow): Items that may be impacting page load time are shown in this section and should be reviewed and monitored.</span></span> <span data-ttu-id="bbbae-116">包含「現成 (OOTB)」Microsoft 網頁組件。</span><span class="sxs-lookup"><span data-stu-id="bbbae-116">This may include "out of the box" (OOTB) Microsoft web parts.</span></span> <span data-ttu-id="bbbae-117">此區段中顯示的任何 Microsoft 網頁組件結果，會自動向 Microsoft 報告，因此**不需要任何動作**。</span><span class="sxs-lookup"><span data-stu-id="bbbae-117">Results for any Microsoft web parts shown in this section are automatically reported to Microsoft, so **no action is required**.</span></span> <span data-ttu-id="bbbae-118">如果您遇到頁面效能緩慢的情形，且頁面上**所有 Microsoft 網頁組件**顯示在**改善機會**區段的結果中，您應該只記錄支援票證以進行調查。</span><span class="sxs-lookup"><span data-stu-id="bbbae-118">You should only log a support ticket for investigation if you are experiencing very slow performance on the page and **all Microsoft web parts** on the page appear in the results in the **Improvement opportunities** section.</span></span> <span data-ttu-id="bbbae-119">請注意，未來「頁面診斷」工具更新會根據 Microsoft 網頁組件的特定組態，進一步細分結果。</span><span class="sxs-lookup"><span data-stu-id="bbbae-119">Note that a future Page Diagnostics tool update will further break down the results based on the specific configuration of the Microsoft web part.</span></span>
- <span data-ttu-id="bbbae-120">**不需要任何動作** (綠色)：沒有任何網頁組件傳回資料耗時超過**兩**秒。</span><span class="sxs-lookup"><span data-stu-id="bbbae-120">**No action required** (green): No web part is taking longer than **two** seconds to return data.</span></span>

<span data-ttu-id="bbbae-121">如果 [網頁組件影響頁面載入時間]\*\*\*\* 結果顯示在結果的 [需要注意]\*\*\*\* 或 [改善機會]\*\*\*\* 區段中，請按一下結果以查看哪些網頁組件導致載入緩慢的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bbbae-121">If the **Web parts are impacting page load time** result appears in either the **Attention required** or **Improvement opportunities** section of the results, click the result to see details about which web parts are loading slowly.</span></span> <span data-ttu-id="bbbae-122">未來「適用於 SharePoint 的頁面診斷」工具的更新可能會包含分析規則的更新，因此請確保永遠擁有最新版本的工具。</span><span class="sxs-lookup"><span data-stu-id="bbbae-122">Future updates to the Page Diagnostics for SharePoint tool may include updates to analysis rules, so please ensure you always have the latest version of the tool.</span></span>

![頁面診斷工具結果](media/modern-portal-optimization/pagediag-web-part.png)

<span data-ttu-id="bbbae-124">結果中提供的資訊包括：</span><span class="sxs-lookup"><span data-stu-id="bbbae-124">Information available in the results includes:</span></span>

- <span data-ttu-id="bbbae-125">[製作者]\*\*\*\* 顯示網頁組件是自訂或 Microsoft OOTB</span><span class="sxs-lookup"><span data-stu-id="bbbae-125">**Made by** shows whether the web part is custom or Microsoft OOTB</span></span>
- <span data-ttu-id="bbbae-126">[名稱和識別碼]\*\*\*\* 顯示可協助您在頁面上尋找網頁組件的識別資訊</span><span class="sxs-lookup"><span data-stu-id="bbbae-126">**Name and ID** shows identifying information that can help you find the web part on the page</span></span>
- <span data-ttu-id="bbbae-127">[總計]\*\*\*\* 顯示網頁組件載入的時間總計</span><span class="sxs-lookup"><span data-stu-id="bbbae-127">**Total** shows the total time for the web part to load</span></span>
- <span data-ttu-id="bbbae-128">[模組載入]\*\*\*\* 顯示提取和載入網頁組件元件所需的時間</span><span class="sxs-lookup"><span data-stu-id="bbbae-128">**Module Load** shows the time taken to fetch and load the web part components</span></span>
- <span data-ttu-id="bbbae-129">[消極式載入]\*\*\*\* 顯示在頁面主要區段中未顯示網頁元件的延遲載入時間</span><span class="sxs-lookup"><span data-stu-id="bbbae-129">**Lazy Load** shows the time for deferred loading of web parts not seen in the main section of the page</span></span>
- <span data-ttu-id="bbbae-130">[初始]\*\*\*\* 顯示網頁元件初始化所需的時間</span><span class="sxs-lookup"><span data-stu-id="bbbae-130">**Init** shows the time taken for web part initialization</span></span>
- <span data-ttu-id="bbbae-131">[轉譯]\*\*\*\* 顯示網頁元件提取及轉譯結果所需的時間</span><span class="sxs-lookup"><span data-stu-id="bbbae-131">**Render** shows the time taken for the web part to fetch and render results</span></span>

<span data-ttu-id="bbbae-132">系統會提供此資訊，協助設計人員和開發人員對問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="bbbae-132">This information is provided to help designers and developers troubleshoot issues.</span></span> <span data-ttu-id="bbbae-133">此資訊應提供給您的設計和開發小組。</span><span class="sxs-lookup"><span data-stu-id="bbbae-133">This information should be provided to your design and development team.</span></span>

## <a name="remediate-web-part-performance-issues"></a><span data-ttu-id="bbbae-134">修復網頁組件效能問題</span><span class="sxs-lookup"><span data-stu-id="bbbae-134">Remediate web part performance issues</span></span>

<span data-ttu-id="bbbae-135">按照本節的指導方針進行，以找出 [網頁組件影響頁面載入時間]\*\*\*\* 結果中列出的網頁組件效能問題，並加以修復。</span><span class="sxs-lookup"><span data-stu-id="bbbae-135">Follow the guidance in this section to identify and remediate performance issues with web parts listed in the **Web parts are impacting page load time** results.</span></span>

<span data-ttu-id="bbbae-136">網頁組件效能不佳有三種可能的原因。</span><span class="sxs-lookup"><span data-stu-id="bbbae-136">There are three categories of possible causes for poor web part performance.</span></span> <span data-ttu-id="bbbae-137">使用下列資訊以判斷您的案例適用的問題，並進行修復。</span><span class="sxs-lookup"><span data-stu-id="bbbae-137">Use the information below to determine which issues apply to your scenario and remediate them.</span></span>

- <span data-ttu-id="bbbae-138">網頁組件指令碼大小和相依性</span><span class="sxs-lookup"><span data-stu-id="bbbae-138">Web part script size and dependencies</span></span>
  - <span data-ttu-id="bbbae-139">最佳化初始指令碼，該指令碼會將主要行案例轉譯為_僅限檢視模式_。</span><span class="sxs-lookup"><span data-stu-id="bbbae-139">Optimize the initial script that renders the mainline scenario for _view mode only_.</span></span>
  - <span data-ttu-id="bbbae-140">使用 _import()_ 陳述式，移動較少使用的案例，並且編輯模式程式碼 (例如屬性窗格) 以分隔區塊。</span><span class="sxs-lookup"><span data-stu-id="bbbae-140">Move the less frequent scenarios and edit mode code (like the property pane) to separate chunks using the _import()_ statement.</span></span>
  - <span data-ttu-id="bbbae-141">檢閱 _package.json_ 檔案的相依性，以完全移除任何無作用程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbbae-141">Review dependencies of the _package.json_ file to remove any dead code completely.</span></span> <span data-ttu-id="bbbae-142">將任何僅限測試/建置相依性移至 devDependencies。</span><span class="sxs-lookup"><span data-stu-id="bbbae-142">Move any test/build only dependencies to devDependencies.</span></span>
  - <span data-ttu-id="bbbae-143">若要下載最佳的靜態資源，需要使用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="bbbae-143">Use of the Office 365 CDN is required for optimal static resource download.</span></span> <span data-ttu-id="bbbae-144">公用 CDN 來源適用於 _js/css_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="bbbae-144">Public CDN origins are preferable for _js/css_ files.</span></span> <span data-ttu-id="bbbae-145">如需使用 Office 365 CDN 的詳細資訊，請參閱[使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-145">For more information about using the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="bbbae-146">重複使用架構，例如隨附於 SharePoint 架構 (SPFx) 的 _React_ 和 _Fabric imports_。</span><span class="sxs-lookup"><span data-stu-id="bbbae-146">Reuse frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx).</span></span> <span data-ttu-id="bbbae-147">如需詳細資訊，請參閱 [SharePoint 架構的概觀](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview) (英文)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-147">For more information, see [Overview of the SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview).</span></span>
  - <span data-ttu-id="bbbae-148">請確保使用最新版本的 SharePoint 架構，並且在新版本可用時升級。</span><span class="sxs-lookup"><span data-stu-id="bbbae-148">Ensure that you are using the latest version of the SharePoint Framework, and upgrade to new versions as they become available.</span></span>
- <span data-ttu-id="bbbae-149">資料提取/快取</span><span class="sxs-lookup"><span data-stu-id="bbbae-149">Data fetching/caching</span></span>
  - <span data-ttu-id="bbbae-150">如果網頁組件依賴額外伺服器呼叫，以提取資料進行顯示，請確保這些伺服器 API 是快速的及/或實作用戶端快取 (例如針對大型集合使用 _localStorage_ 或 _IndexDB_)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-150">If the web part relies on extra server calls to fetch data for display, ensure those server APIs are fast and/or implement client side caching (such as using _localStorage_ or _IndexDB_ for larger sets).</span></span>
  - <span data-ttu-id="bbbae-151">如果需要多個呼叫來轉譯重要資料，請考量在伺服器上進行批次處理，或者將要求合併至單一呼叫的其他方法。</span><span class="sxs-lookup"><span data-stu-id="bbbae-151">If multiple calls are required to render critical data, consider batching on the server or other methods of consolidating requests to a single call.</span></span>
  - <span data-ttu-id="bbbae-152">或者，如果資料的某些元素需要較慢的 API，但是對於初始轉譯並不重要，請將這些項目分離為個別呼叫，在重要資料轉譯之後執行。</span><span class="sxs-lookup"><span data-stu-id="bbbae-152">Alternatively, if some elements of data require a slower API, but are not critical to initial rendering, decouple these to a separate call that is executed after critical data is rendered.</span></span>
  - <span data-ttu-id="bbbae-153">如果多個組件使用相同的資料，請利用共用資料層來避免重複呼叫。</span><span class="sxs-lookup"><span data-stu-id="bbbae-153">If multiple parts use the same data, utilize a common data layer to avoid duplicate calls.</span></span>
- <span data-ttu-id="bbbae-154">轉譯時間</span><span class="sxs-lookup"><span data-stu-id="bbbae-154">Rendering time</span></span>
  - <span data-ttu-id="bbbae-155">任何媒體來源 (例如影像和影片) 的大小應該調整為容器、裝置及/或網路的限制，以避免下載不必要的大型資產。</span><span class="sxs-lookup"><span data-stu-id="bbbae-155">Any media sources like images and videos should be sized to the limits of the container, device and/or network to avoid downloading unnecessary large assets.</span></span> <span data-ttu-id="bbbae-156">如需內容相依性的詳細資訊，請參閱[使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-156">For more information about content dependencies, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="bbbae-157">避免造成自動重排、複雜 CSS 規則或複雜動畫的 API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="bbbae-157">Avoid API calls that cause re-flow, complex CSS rules or complicated animations.</span></span> <span data-ttu-id="bbbae-158">如需詳細資訊，請參閱[最小化瀏覽器自動重排](https://developers.google.com/speed/docs/insights/browser-reflow) (英文)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-158">For more information, see [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow).</span></span>
  - <span data-ttu-id="bbbae-159">避免使用鏈結長時間執行工作。</span><span class="sxs-lookup"><span data-stu-id="bbbae-159">Avoid use of chained long running tasks.</span></span> <span data-ttu-id="bbbae-160">相反地，將長時間執行工作分開至個別佇列。</span><span class="sxs-lookup"><span data-stu-id="bbbae-160">Instead, break long running tasks apart into separate queues.</span></span> <span data-ttu-id="bbbae-161">如需詳細資訊，請參閱[最佳化 JavaScript 執行](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-161">For more information, see [Optimize JavaScript Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).</span></span>
  - <span data-ttu-id="bbbae-162">為非同步轉譯媒體或視覺元件保留對應空間，以避免略過畫面格數和間斷 (也稱為 _jank_)。</span><span class="sxs-lookup"><span data-stu-id="bbbae-162">Reserve corresponding space for asynchronously rendering media or visual elements to avoid skipped frames and stuttering (also known as _jank_).</span></span>
  - <span data-ttu-id="bbbae-163">如果特定瀏覽器不支援轉譯中使用的功能，則載入 polyfill 或排除執行相依程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbbae-163">If a certain browser doesn't support a feature used in rendering, either load a polyfill or exclude running dependent code.</span></span> <span data-ttu-id="bbbae-164">如果功能不重要，請以事件處理常式的形式來處理資源，以避免記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="bbbae-164">If the feature is not critical, dispose resources such as event handlers to avoid memory leaks.</span></span>

<span data-ttu-id="bbbae-165">在您進行頁面修訂以修復效能問題之前，請記下分析結果中的頁面載入時間。</span><span class="sxs-lookup"><span data-stu-id="bbbae-165">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="bbbae-166">在修訂後再次執行工具，以查看新結果是否在基準標準內，並檢查新頁面的載入時間，以查看是否有改善。</span><span class="sxs-lookup"><span data-stu-id="bbbae-166">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![頁面載入時間結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="bbbae-168">頁面載入時間會因為各種因素而有所不同，例如網路負載、一天的時間及其他暫時條件。</span><span class="sxs-lookup"><span data-stu-id="bbbae-168">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="bbbae-169">您應該在進行變更前後測試幾次頁面載入時間，以協助您計算結果的平均值。</span><span class="sxs-lookup"><span data-stu-id="bbbae-169">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="bbbae-170">相關主題</span><span class="sxs-lookup"><span data-stu-id="bbbae-170">Related topics</span></span>

[<span data-ttu-id="bbbae-171">調整 SharePoint Online 效能</span><span class="sxs-lookup"><span data-stu-id="bbbae-171">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="bbbae-172">調整 Office 365 效能</span><span class="sxs-lookup"><span data-stu-id="bbbae-172">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="bbbae-173">SharePoint 新式體驗中的效能</span><span class="sxs-lookup"><span data-stu-id="bbbae-173">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="bbbae-174">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="bbbae-174">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="bbbae-175">使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bbbae-175">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
