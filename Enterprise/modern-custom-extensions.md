---
title: 在 SharePoint Online 新式網站頁面中最佳化自訂延伸模組
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: 深入了解如何在 SharePoint Online 新式網站頁面中最佳化自訂延伸模組的效能。
ms.openlocfilehash: bdc05c4e786d07a18c49766bf37aca7f4fde56da
ms.sourcegitcommit: c024b48115cebfdaadfbc724acc2d065394156e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "42603817"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="6dfaa-103">在 SharePoint Online 新式網站頁面中最佳化自訂延伸模組的效能</span><span class="sxs-lookup"><span data-stu-id="6dfaa-103">Optimize custom extension performance in SharePoint Online modern site pages</span></span>

<span data-ttu-id="6dfaa-104">本文可協助您了解如何判斷自訂延伸模組如何影響使用者察覺延遲，以及如何修復常見問題。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-104">This article will help you understand how to determine how custom extensions affect user perceived latency, and how to remediate common issues.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a><span data-ttu-id="6dfaa-105">使用「適用於 SharePoint 的頁面診斷」工具來分析自訂延伸模組</span><span class="sxs-lookup"><span data-stu-id="6dfaa-105">Use the Page Diagnostics for SharePoint tool to analyze custom extensions</span></span>

<span data-ttu-id="6dfaa-106">適用於 SharePoint 的頁面診斷工具是全新 Microsoft Edge (https://www.microsoft.com/edge) 和 Chrome 瀏覽器的擴充功能，可以用來分析 SharePoint Online 新式入口網站與傳統發佈網站頁面。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-106">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="6dfaa-107">該工具會針對每個分析頁面提供一份報告，顯示頁面如何針對定義的效能準則組執行。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-107">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="6dfaa-108">若要安裝及了解「適用於 SharePoint 的頁面診斷」工具，請造訪[使用適用於 SharePoint Online 的頁面診斷工具](page-diagnostics-for-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-108">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="6dfaa-109">網頁診斷工具只能用於 SharePoint Online，且無法在 SharePoint 系統頁面使用。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-109">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="6dfaa-110">當您使用「適用於 SharePoint 的頁面診斷」工具分析 SharePoint 網站頁面時，您可以在 [診斷測試]__ 窗格的 [自訂延伸模組影響載入時間]\*\*\*\* 結果中，看到超過基準計量的自訂延伸模組相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-110">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about custom extensions that exceed the baseline metric in the **Extensions are impacting load time** result in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="6dfaa-111">可能的結果包括：</span><span class="sxs-lookup"><span data-stu-id="6dfaa-111">Possible results include:</span></span>

- <span data-ttu-id="6dfaa-112">**需要注意** (紅色)：載入耗時比**兩**秒還要久的任何_自訂_延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-112">**Attention required** (red): Any _custom_ extension that takes longer than **one** second to load.</span></span> <span data-ttu-id="6dfaa-113">測試結果中顯示的載入時間總計會依據模組載入和初始來細分。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-113">Total load time as displayed in test results is broken down by module load and init.</span></span>
- <span data-ttu-id="6dfaa-114">**不需要任何動作** (綠色)：沒有任何延伸模組載入耗時超過一秒。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-114">**No action required** (green): No extension is taking longer than one second to load.</span></span>

<span data-ttu-id="6dfaa-115">如果延伸模組影響頁面載入時間，結果會顯示在 [需要注意]\*\*\*\* 區段中。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-115">If an extension is impacting page load time, the result appears in the **Attention required** section of the results.</span></span> <span data-ttu-id="6dfaa-116">按一下結果以查看載入緩慢的延伸模組詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-116">Click the result to see details about which extension is loading slowly.</span></span> <span data-ttu-id="6dfaa-117">未來「適用於 SharePoint 的頁面診斷」工具的更新可能會包含分析規則的更新，因此請確保永遠擁有最新版本的工具。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-117">Future updates to the Page Diagnostics for SharePoint tool may include updates to analysis rules, so please ensure you always have the latest version of the tool.</span></span>

![頁面載入時間結果](media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

<span data-ttu-id="6dfaa-119">結果中提供的資訊包括：</span><span class="sxs-lookup"><span data-stu-id="6dfaa-119">Information available in the results includes:</span></span>

- <span data-ttu-id="6dfaa-120">[名稱和識別碼]\*\*\*\* 顯示可協助您在頁面上尋找延伸模組的識別資訊</span><span class="sxs-lookup"><span data-stu-id="6dfaa-120">**Name and ID** shows identifying information that can help you find the extension on the page</span></span>
- <span data-ttu-id="6dfaa-121">[總計]\*\*\*\* 顯示延伸模組初始和載入的時間總計</span><span class="sxs-lookup"><span data-stu-id="6dfaa-121">**Total** shows the total time for the extension to initialize and load</span></span>
- <span data-ttu-id="6dfaa-122">[模組載入]\*\*\*\* 顯示擷取和載入延伸模組所需的時間</span><span class="sxs-lookup"><span data-stu-id="6dfaa-122">**Module Load** shows the time taken to fetch and load the extension</span></span>
- <span data-ttu-id="6dfaa-123">[初始]\*\*\*\* 顯示延伸模組初始化所需的時間</span><span class="sxs-lookup"><span data-stu-id="6dfaa-123">**Init** shows the time taken for the extension to initialize</span></span>

<span data-ttu-id="6dfaa-124">系統會提供此資訊，協助設計人員和開發人員對問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-124">This information is provided to help designers and developers troubleshoot issues.</span></span> <span data-ttu-id="6dfaa-125">此資訊應提供給您的設計和開發小組。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-125">This information should be provided to your design and development team.</span></span>

## <a name="overview-of-extensions"></a><span data-ttu-id="6dfaa-126">延伸模組的概觀</span><span class="sxs-lookup"><span data-stu-id="6dfaa-126">Overview of extensions</span></span>

<span data-ttu-id="6dfaa-127">SharePoint 架構 (SPFx) 延伸模組可用於延伸 SharePoint 使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-127">SharePoint Framework (SPFx) Extensions can be used to extend the SharePoint user experience.</span></span> <span data-ttu-id="6dfaa-128">透過 SharePoint 架構延伸模組，您可以自訂 SharePoint 體驗的更多層面，包括通知區域、工具列及清單資料檢視。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-128">With SharePoint Framework Extensions, you can customize more facets of the SharePoint experience, including notification areas, toolbars, and list data views.</span></span>

<span data-ttu-id="6dfaa-129">延伸模組對 SharePoint 頁面的效能有不良影響，因為這也會佔用 CPU 和網路資源來執行必要的工作。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-129">Extensions can have a bad influence on the performance of a SharePoint page as it also takes CPU and network resources to do required work.</span></span>

<span data-ttu-id="6dfaa-130">延伸模組有四種類型：</span><span class="sxs-lookup"><span data-stu-id="6dfaa-130">There are four types of extensions:</span></span>

- <span data-ttu-id="6dfaa-131">**應用程式自訂員**會在頁面中新增指令碼，並存取已知 HTML 元素預留位置，並以自訂轉譯進行延伸。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-131">**Application Customizers** adds scripts to the page, and accesses well-known HTML element placeholders and extends them with custom renderings.</span></span>
- <span data-ttu-id="6dfaa-132">**欄位自訂員**提供清單中欄位資料的修改檢視。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-132">**Field Customizers** provides modified views to data for fields within a list.</span></span>
- <span data-ttu-id="6dfaa-133">**命令集**延伸 SharePoint 命令面來新增新動作，並提供您可用來實作行為的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-133">**Command Sets** extend the SharePoint command surfaces to add new actions, and provides client-side code that you can use to implement behaviors.</span></span>
- <span data-ttu-id="6dfaa-134">**搜尋查詢修改程式 (僅供預覽)** 會在執行搜尋查詢前被叫用。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-134">**Search Query Modifier (preview only)** are invoked just before the search query is executed.</span></span>

## <a name="remediate-extension-performance-issues"></a><span data-ttu-id="6dfaa-135">修復延伸模組效能問題</span><span class="sxs-lookup"><span data-stu-id="6dfaa-135">Remediate extension performance issues</span></span>

<span data-ttu-id="6dfaa-136">按照本節的指導方針進行，以找出 [延伸模組影響頁面載入時間]\*\*\*\* 結果中列出的延伸模組效能問題，並加以修復。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-136">Follow the guidance in this section to identify and remediate performance issues with extensions listed in the **Extensions are impacting page load time** results.</span></span>

>[!NOTE]
><span data-ttu-id="6dfaa-137">在頁面生命週期的早期階段中，可能會執行應用程式自訂員，因此可能會影響頁面上其他延伸模組的效能。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-137">Application customizers may be executed in the early stage during the lifecycle of a page and it may influence the performance of other extensions on the page.</span></span>

<span data-ttu-id="6dfaa-138">頁面診斷工具中的稽核結果會顯示兩個執行延伸模組的階段，以便協助找出潛在的效能影響。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-138">The audit results in the Page Diagnostic Tool will display two stages of executing an extension in order to help identify the potential performance impact.</span></span>

- <span data-ttu-id="6dfaa-139">**模組載入時間**是載入延伸模組所需的時間，這會受到延伸模組的大小影響，因此建議您只組合延伸模組中的必要資料庫，並選擇較輕量的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-139">**Module load** is how long it takes to load the extension, which is impacted by the size of an extension so it is a good idea to only bundle the necessary libraries in the extension and to also choose lighter libraries.</span></span>
- <span data-ttu-id="6dfaa-140">**初始**是延伸模組和延伸模組開發人員的初始化時間，應考慮延伸模組是否在初始階段期間執行不必要的工作，或執行太多命令。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-140">**Init** is the initialization time of the extension and extension developers should consider whether the extension is doing unnecessary work or executing too many commands during the initializing stage.</span></span>

<span data-ttu-id="6dfaa-141">頁面作者也可以使用稽核結果，查看頁面上是否有太多延伸模組，因為延伸太多會對頁面的效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-141">Page authors can also use the audit result to see whether a page has too many extensions as too many extensions will negatively impact the performance of a page.</span></span>

- <span data-ttu-id="6dfaa-142">**延伸模組大小和相依性**</span><span class="sxs-lookup"><span data-stu-id="6dfaa-142">**Extension size and dependencies**</span></span>
  - <span data-ttu-id="6dfaa-143">若要下載最佳的靜態資源，需要使用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-143">Use of the Office 365 CDN is required for optimal static resource download.</span></span> <span data-ttu-id="6dfaa-144">公用 CDN 來源適用於 _js/css_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-144">Public CDN origins are preferable for _js/css_ files.</span></span> <span data-ttu-id="6dfaa-145">如需使用 Office 365 CDN 的詳細資訊，請參閱[使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-145">For more information about using the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="6dfaa-146">重複使用架構，例如隨附於 SharePoint 架構 (SPFx) 的 _React_ 和 _Fabric imports_。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-146">Reuse frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx).</span></span> <span data-ttu-id="6dfaa-147">如需詳細資訊，請參閱 [SharePoint 架構的概觀](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview) (英文)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-147">For more information, see [Overview of the SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview).</span></span>
  - <span data-ttu-id="6dfaa-148">請確保使用最新版本的 SharePoint 架構，並且在新版本可用時升級。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-148">Ensure that you are using the latest version of the SharePoint Framework, and upgrade to new versions as they become available.</span></span>
- <span data-ttu-id="6dfaa-149">**資料擷取/快取**</span><span class="sxs-lookup"><span data-stu-id="6dfaa-149">**Data fetching/caching**</span></span>
  - <span data-ttu-id="6dfaa-150">如果延伸模組依賴額外伺服器呼叫，以擷取資料進行顯示，請確保這些伺服器 API 是快速的及/或實作用戶端快取 (例如針對大型集合使用 _localStorage_ 或 _IndexDB_)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-150">If the extension relies on extra server calls to fetch data for display, ensure those server APIs are fast and/or implement client side caching (such as using _localStorage_ or _IndexDB_ for larger sets).</span></span>
  - <span data-ttu-id="6dfaa-151">如果需要多個呼叫來轉譯重要資料，請考量在伺服器上進行批次處理，或者將要求合併至單一呼叫的其他方法。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-151">If multiple calls are required to render critical data, consider batching on the server or other methods of consolidating requests to a single call.</span></span>
  - <span data-ttu-id="6dfaa-152">或者，如果資料的某些元素需要較慢的 API，但是對於初始轉譯並不重要，請將這些項目分離為個別呼叫，在重要資料轉譯之後執行。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-152">Alternatively, if some elements of data require a slower API, but are not critical to initial rendering, decouple these to a separate call that is executed after critical data is rendered.</span></span>
  - <span data-ttu-id="6dfaa-153">如果多個組件使用相同的資料，請利用共用資料層來避免重複呼叫。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-153">If multiple parts use the same data, utilize a common data layer to avoid duplicate calls.</span></span>
- <span data-ttu-id="6dfaa-154">**轉譯時間**</span><span class="sxs-lookup"><span data-stu-id="6dfaa-154">**Rendering time**</span></span>
  - <span data-ttu-id="6dfaa-155">任何媒體來源 (例如影像和影片) 的大小應該調整為容器、裝置及/或網路的限制，以避免下載不必要的大型資產。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-155">Any media sources like images and videos should be sized to the limits of the container, device and/or network to avoid downloading unnecessary large assets.</span></span> <span data-ttu-id="6dfaa-156">如需內容相依性的詳細資訊，請參閱[使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online](use-office-365-cdn-with-spo.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-156">For more information about content dependencies, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="6dfaa-157">避免造成自動重排、複雜 CSS 規則或複雜動畫的 API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-157">Avoid API calls that cause re-flow, complex CSS rules or complicated animations.</span></span> <span data-ttu-id="6dfaa-158">如需詳細資訊，請參閱[最小化瀏覽器自動重排](https://developers.google.com/speed/docs/insights/browser-reflow) (英文)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-158">For more information, see [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow).</span></span>
  - <span data-ttu-id="6dfaa-159">避免使用鏈結長時間執行工作。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-159">Avoid use of chained long running tasks.</span></span> <span data-ttu-id="6dfaa-160">相反地，將長時間執行工作分開至個別佇列。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-160">Instead, break long running tasks apart into separate queues.</span></span> <span data-ttu-id="6dfaa-161">如需詳細資訊，請參閱[最佳化 JavaScript 執行](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-161">For more information, see [Optimize JavaScript Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).</span></span>
  - <span data-ttu-id="6dfaa-162">為非同步轉譯媒體或視覺元件保留對應空間，以避免略過畫面格數和間斷 (也稱為 _jank_)。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-162">Reserve corresponding space for asynchronously rendering media or visual elements to avoid skipped frames and stuttering (also known as _jank_).</span></span>
  - <span data-ttu-id="6dfaa-163">如果特定瀏覽器不支援轉譯中使用的功能，則載入 polyfill 或排除執行相依程式碼。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-163">If a certain browser doesn't support a feature used in rendering, either load a polyfill or exclude running dependent code.</span></span> <span data-ttu-id="6dfaa-164">如果功能不重要，請以事件處理常式的形式來處理資源，以避免記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-164">If the feature is not critical, dispose resources such as event handlers to avoid memory leaks.</span></span>

<span data-ttu-id="6dfaa-165">在您進行頁面修訂以修復效能問題之前，請記下分析結果中的頁面載入時間。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-165">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="6dfaa-166">在修訂後再次執行工具，以查看新結果是否在基準標準內，並檢查新頁面的載入時間，以查看是否有改善。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-166">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![頁面載入時間結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="6dfaa-168">頁面載入時間會因為各種因素而有所不同，例如網路負載、一天的時間及其他暫時條件。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-168">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="6dfaa-169">您應該在進行變更前後測試幾次頁面載入時間，以協助您計算結果的平均值。</span><span class="sxs-lookup"><span data-stu-id="6dfaa-169">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="6dfaa-170">相關主題</span><span class="sxs-lookup"><span data-stu-id="6dfaa-170">Related topics</span></span>

[<span data-ttu-id="6dfaa-171">調整 SharePoint Online 效能</span><span class="sxs-lookup"><span data-stu-id="6dfaa-171">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="6dfaa-172">調整 Office 365 效能</span><span class="sxs-lookup"><span data-stu-id="6dfaa-172">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="6dfaa-173">SharePoint 新式體驗中的效能</span><span class="sxs-lookup"><span data-stu-id="6dfaa-173">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="6dfaa-174">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="6dfaa-174">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="6dfaa-175">使用 Office 365 內容傳遞網路 (CDN) 搭配 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6dfaa-175">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)