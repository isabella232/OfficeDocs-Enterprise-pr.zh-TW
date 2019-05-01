---
title: SharePoint Online 效能調整的簡介
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: 本文將告訴您需要考慮當設計的 SharePoint Online 中的最佳效能頁面的特定事項。
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487155"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="cb005-103">SharePoint Online 效能調整的簡介</span><span class="sxs-lookup"><span data-stu-id="cb005-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="cb005-104">本文將告訴您需要考慮當設計的 SharePoint Online 中的最佳效能頁面的特定事項。</span><span class="sxs-lookup"><span data-stu-id="cb005-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="cb005-105">SharePoint Online 度量資訊</span><span class="sxs-lookup"><span data-stu-id="cb005-105">SharePoint Online metrics</span></span>

<span data-ttu-id="cb005-106">SharePoint online 的廣泛計量提供有關效能的實際環境資料：</span><span class="sxs-lookup"><span data-stu-id="cb005-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="cb005-107">頁面載入速度</span><span class="sxs-lookup"><span data-stu-id="cb005-107">How fast pages load</span></span>
    
- <span data-ttu-id="cb005-108">每頁所需來回行程次數</span><span class="sxs-lookup"><span data-stu-id="cb005-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="cb005-109">服務的問題</span><span class="sxs-lookup"><span data-stu-id="cb005-109">Issues with the service</span></span>
    
- <span data-ttu-id="cb005-110">會導致效能降低的其他事項</span><span class="sxs-lookup"><span data-stu-id="cb005-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="cb005-111">結論資料</span><span class="sxs-lookup"><span data-stu-id="cb005-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="cb005-112">資料會告訴我們：</span><span class="sxs-lookup"><span data-stu-id="cb005-112">The data tells us:</span></span>
  
- <span data-ttu-id="cb005-113">大部分頁面以及 SharePoint Online 上執行。</span><span class="sxs-lookup"><span data-stu-id="cb005-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="cb005-114">非自訂頁面載入速度很快。</span><span class="sxs-lookup"><span data-stu-id="cb005-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="cb005-115">商務用 OneDrive、 小組網站和系統頁面，例如 _layouts 等是所有快速載入。</span><span class="sxs-lookup"><span data-stu-id="cb005-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="cb005-116">速度最慢的 1%SharePoint Online 頁面需要載入超過 5000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="cb005-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="cb005-117">您可以使用一個簡單的基準測試是測量效能藉由比較針對商務首頁 OneDrive 的載入時間自己入口網站的載入時間，因為它會使用幾個自訂的功能。</span><span class="sxs-lookup"><span data-stu-id="cb005-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="cb005-118">這通常是支援會要求您完成疑難排解網路效能問題時的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="cb005-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="cb005-119">檢查效能時，使用標準的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cb005-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="cb005-120">網站集合管理員、 網站擁有人、 編輯器或參與者隸屬於其他安全性群組，具有其他權限，因此 SharePoint 載入頁面的其他項目。</span><span class="sxs-lookup"><span data-stu-id="cb005-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="cb005-121">這是適用於 SharePoint 內部部署和 SharePoint Online，但在內部部署案例差異便不會為輕鬆地發現如 SharePoint Online 所示。</span><span class="sxs-lookup"><span data-stu-id="cb005-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="cb005-122">才能正確地評估的使用者] 頁面上會執行方式，您應該使用標準的使用者帳戶，以避免載入安全性群組與相關的其他流量與製作的控制項。</span><span class="sxs-lookup"><span data-stu-id="cb005-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="cb005-123">效能調整的連線類別</span><span class="sxs-lookup"><span data-stu-id="cb005-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="cb005-124">您可以將伺服器和使用者之間的連線到三個主要元件加以分類。</span><span class="sxs-lookup"><span data-stu-id="cb005-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="cb005-125">設計 SharePoint Online 的深入的頁面載入時間時，請考慮這些選項。</span><span class="sxs-lookup"><span data-stu-id="cb005-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="cb005-126">**伺服器**Microsoft 會代管的資料中心伺服器。</span><span class="sxs-lookup"><span data-stu-id="cb005-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="cb005-127">**網路**Microsoft 網路、 網際網路及您的內部網路之間的資料中心和您的使用者。</span><span class="sxs-lookup"><span data-stu-id="cb005-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="cb005-128">**瀏覽器**其中載入頁面。</span><span class="sxs-lookup"><span data-stu-id="cb005-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="cb005-129">下列三個連線有通常會導致 95%的速度很慢的頁面的五個原因。</span><span class="sxs-lookup"><span data-stu-id="cb005-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="cb005-130">本文將討論每個這些原因是：</span><span class="sxs-lookup"><span data-stu-id="cb005-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="cb005-131">瀏覽問題</span><span class="sxs-lookup"><span data-stu-id="cb005-131">Navigation issues</span></span>
    
- <span data-ttu-id="cb005-132">內容彙總</span><span class="sxs-lookup"><span data-stu-id="cb005-132">Content roll up</span></span>
    
- <span data-ttu-id="cb005-133">大型檔案</span><span class="sxs-lookup"><span data-stu-id="cb005-133">Large files</span></span>
    
- <span data-ttu-id="cb005-134">伺服器的要求太多</span><span class="sxs-lookup"><span data-stu-id="cb005-134">Many requests to the server</span></span>
    
- <span data-ttu-id="cb005-135">網頁組件處理</span><span class="sxs-lookup"><span data-stu-id="cb005-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="cb005-136">伺服器連線</span><span class="sxs-lookup"><span data-stu-id="cb005-136">Server connection</span></span>

<span data-ttu-id="cb005-137">許多影響 SharePoint 內部部署效能的問題也適用於 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="cb005-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="cb005-138">如您所預期，您會有更多控制權伺服器如何執行與內部部署 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="cb005-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="cb005-139">使用 SharePoint Online 事項會稍微不同。</span><span class="sxs-lookup"><span data-stu-id="cb005-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="cb005-140">多工作您，讓伺服器執行的時間就越長轉譯頁面。</span><span class="sxs-lookup"><span data-stu-id="cb005-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="cb005-141">SharePoint 中，在這方面的最大發生錯誤之有複雜的頁面，具有多個網頁組件。</span><span class="sxs-lookup"><span data-stu-id="cb005-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="cb005-142">SharePoint Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="cb005-142">SharePoint Server on-premises</span></span>
  
![內部部署伺服器的螢幕擷取畫面](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="cb005-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb005-144">SharePoint Online</span></span>
  
![伺服器連線的螢幕擷取畫面](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="cb005-146">使用 SharePoint Online，某些頁面要求可能會實際最後呼叫多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="cb005-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="cb005-147">您無法結尾的個別要求的伺服器之間的要求矩陣。</span><span class="sxs-lookup"><span data-stu-id="cb005-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="cb005-148">這些互動從] 頁面上的負載觀點昂貴且會讓事情變慢。</span><span class="sxs-lookup"><span data-stu-id="cb005-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="cb005-149">這些伺服器對伺服器互動的範例如下：</span><span class="sxs-lookup"><span data-stu-id="cb005-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="cb005-150">Web 對 SQL Server</span><span class="sxs-lookup"><span data-stu-id="cb005-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="cb005-151">Web 對應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="cb005-151">Web to application servers</span></span>
    
<span data-ttu-id="cb005-152">可以減慢伺服器互動的其他一件事是快取遺漏。</span><span class="sxs-lookup"><span data-stu-id="cb005-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="cb005-153">不同內部部署 SharePoint，沒有就會叫用相同的伺服器] 頁面上，瀏覽過先前; 非常輕型機率這會讓物件快取已過時。</span><span class="sxs-lookup"><span data-stu-id="cb005-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="cb005-154">網路連線</span><span class="sxs-lookup"><span data-stu-id="cb005-154">Network connection</span></span>

<span data-ttu-id="cb005-155">不會讓使用 WAN 的內部部署 sharepoint，您可以使用資料中心與使用者之間的高速連線。</span><span class="sxs-lookup"><span data-stu-id="cb005-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="cb005-156">一般而言，項目皆可輕鬆地從網路的觀點來管理。</span><span class="sxs-lookup"><span data-stu-id="cb005-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="cb005-157">使用 SharePoint Online，有幾個因素考慮;例如：</span><span class="sxs-lookup"><span data-stu-id="cb005-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="cb005-158">Microsoft 網路</span><span class="sxs-lookup"><span data-stu-id="cb005-158">The Microsoft network</span></span>
    
- <span data-ttu-id="cb005-159">網際網路</span><span class="sxs-lookup"><span data-stu-id="cb005-159">The Internet</span></span>
    
- <span data-ttu-id="cb005-160">ISP</span><span class="sxs-lookup"><span data-stu-id="cb005-160">The ISP</span></span>
    
<span data-ttu-id="cb005-161">不論哪一個版本的 SharePoint （和那個網路） 使用，通常會導致網路忙碌的時間，包括：</span><span class="sxs-lookup"><span data-stu-id="cb005-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="cb005-162">承載過大</span><span class="sxs-lookup"><span data-stu-id="cb005-162">Large payload</span></span>
    
- <span data-ttu-id="cb005-163">許多檔案</span><span class="sxs-lookup"><span data-stu-id="cb005-163">Many files</span></span>
    
- <span data-ttu-id="cb005-164">伺服器的實體距離太</span><span class="sxs-lookup"><span data-stu-id="cb005-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="cb005-165">您可以利用 SharePoint Online 中的一項功能是 Microsoft CDN 內容傳遞網路 （）。</span><span class="sxs-lookup"><span data-stu-id="cb005-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="cb005-166">CDN 基本上是跨多個資料中心部署的伺服器的分散式的集合。</span><span class="sxs-lookup"><span data-stu-id="cb005-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="cb005-167">使用 CDN，頁面上的內容可以主控接近用戶端伺服器上即使用戶端是遠從原始的 SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="cb005-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="cb005-168">Microsoft 會使用此多未來要儲存的頁面無法加以自訂，例如 SharePoint Online 的系統管理首頁上的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb005-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="cb005-169">如需 Cdn 的詳細資訊，請參閱 <<c0>內容傳遞網路。</span><span class="sxs-lookup"><span data-stu-id="cb005-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="cb005-170">您需要知悉的但不是能執行許多動作相關的內容是您的 ISP 的連線速度。</span><span class="sxs-lookup"><span data-stu-id="cb005-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="cb005-171">簡單的速度測試工具會告訴您的連線速度。</span><span class="sxs-lookup"><span data-stu-id="cb005-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="cb005-172">瀏覽器連線</span><span class="sxs-lookup"><span data-stu-id="cb005-172">Browser connection</span></span>

<span data-ttu-id="cb005-173">有幾個因素来考慮使用網頁瀏覽器效能的觀點而言。</span><span class="sxs-lookup"><span data-stu-id="cb005-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="cb005-174">造訪複雜的頁面會影響效能。</span><span class="sxs-lookup"><span data-stu-id="cb005-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="cb005-175">大部分的瀏覽器只需要使用小型的快取 (大約 90 MB)，同時平均網頁通常是大約 1.6 MB。</span><span class="sxs-lookup"><span data-stu-id="cb005-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="cb005-176">這不會採取長，取得用於。</span><span class="sxs-lookup"><span data-stu-id="cb005-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="cb005-177">頻寬可能也會發生問題。</span><span class="sxs-lookup"><span data-stu-id="cb005-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="cb005-178">例如，如果使用者觀賞影片，另一個工作階段中，這會影響您的 SharePoint 網頁的效能。</span><span class="sxs-lookup"><span data-stu-id="cb005-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="cb005-179">雖然您無法防止使用者媒體資料流，您可以控制使用者會載入頁面的方式。</span><span class="sxs-lookup"><span data-stu-id="cb005-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="cb005-180">請參閱以下文章中的不同的 SharePoint Online 頁面自訂技術和其他最佳作法，以協助您達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="cb005-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="cb005-181">SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="cb005-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-182">使用 SharePoint Online 頁面診斷工具</span><span class="sxs-lookup"><span data-stu-id="cb005-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="cb005-183">SharePoint Online 的影像最佳化</span><span class="sxs-lookup"><span data-stu-id="cb005-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-184">延遲載入 SharePoint Online 中的影像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="cb005-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-185">縮製及統合在 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb005-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-186">使用內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="cb005-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-187">使用內容搜尋網頁組件而不內容查詢網頁組件，來改善 SharePoint Online 中的效能</span><span class="sxs-lookup"><span data-stu-id="cb005-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="cb005-188">容量規劃和負載測試 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cb005-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-189">診斷 SharePoint Online 的效能問題</span><span class="sxs-lookup"><span data-stu-id="cb005-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-190">使用 SharePoint Online 的物件快取</span><span class="sxs-lookup"><span data-stu-id="cb005-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="cb005-191">操作方法：如何避免在 SharePoint Online 中受到節流控制或封鎖</span><span class="sxs-lookup"><span data-stu-id="cb005-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

