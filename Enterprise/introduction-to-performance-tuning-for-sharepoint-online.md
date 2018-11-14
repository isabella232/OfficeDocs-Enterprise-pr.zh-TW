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
description: 本文說明設計的 SharePoint Online 中的最佳效能頁面時需要考量您需要何種特定部分。
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219873"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="c5a15-103">SharePoint Online 效能調整的簡介</span><span class="sxs-lookup"><span data-stu-id="c5a15-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="c5a15-104">本文說明設計的 SharePoint Online 中的最佳效能頁面時需要考量您需要何種特定部分。</span><span class="sxs-lookup"><span data-stu-id="c5a15-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="c5a15-105">SharePoint Online 度量資訊</span><span class="sxs-lookup"><span data-stu-id="c5a15-105">SharePoint Online metrics</span></span>

<span data-ttu-id="c5a15-106">下列廣泛的 SharePoint Online 度量值提供有關效能的實際環境資料：</span><span class="sxs-lookup"><span data-stu-id="c5a15-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="c5a15-107">頁面載入速度</span><span class="sxs-lookup"><span data-stu-id="c5a15-107">How fast pages load</span></span>
    
- <span data-ttu-id="c5a15-108">每頁所需來回行程次數</span><span class="sxs-lookup"><span data-stu-id="c5a15-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="c5a15-109">服務的問題</span><span class="sxs-lookup"><span data-stu-id="c5a15-109">Issues with the service</span></span>
    
- <span data-ttu-id="c5a15-110">導致效能降低的其他事項</span><span class="sxs-lookup"><span data-stu-id="c5a15-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="c5a15-111">資料所導出的結論</span><span class="sxs-lookup"><span data-stu-id="c5a15-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="c5a15-112">資料會告訴我們：</span><span class="sxs-lookup"><span data-stu-id="c5a15-112">The data tells us:</span></span>
  
- <span data-ttu-id="c5a15-113">大部分頁面在 SharePoint Online 上的執行狀況良好。</span><span class="sxs-lookup"><span data-stu-id="c5a15-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="c5a15-114">非自訂頁面載入速度很快。</span><span class="sxs-lookup"><span data-stu-id="c5a15-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="c5a15-115">商務用 OneDrive、小組網站和系統頁面 (如 _layouts 等) 載入速度都很快。</span><span class="sxs-lookup"><span data-stu-id="c5a15-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="c5a15-116">最慢的 1% SharePoint Online 頁面載入時間需要超過 5000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="c5a15-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="c5a15-p101">您可使用的一項簡單基準測試是透過比較您的入口網站載入時間和商務用 OneDrive 首頁載入時間來測量效能，因其使用的自訂功能不多。在進行網路效能問題疑難排解時，這通常是支援人員要求您完成的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="c5a15-119">檢查效能時使用的標準使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c5a15-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="c5a15-120">網站集合管理員、 網站擁有者、 編輯器或參與者屬於其他安全性群組、 具有其他權限，且因此 SharePoint 會載入頁面的其他元素。</span><span class="sxs-lookup"><span data-stu-id="c5a15-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="c5a15-121">這是適用於 SharePoint 內部部署和 SharePoint Online 但內部部署案例中的差異便不會輕鬆發現如 SharePoint Online 所示。</span><span class="sxs-lookup"><span data-stu-id="c5a15-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="c5a15-122">才能正確地評估] 頁面上將如何執行使用者，您應該使用標準的使用者帳戶以避免載入撰寫控制項與其他安全性群組與相關的流量。</span><span class="sxs-lookup"><span data-stu-id="c5a15-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="c5a15-123">效能調整的連線類別</span><span class="sxs-lookup"><span data-stu-id="c5a15-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="c5a15-p102">您可將伺服器與使用者之間的連線分類成三種主要元件。在設計 SharePoint Online 頁面以深入瞭解載入時間時，請將這些元件納入考量。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="c5a15-126">**伺服器**Microsoft 主控的資料中心伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5a15-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="c5a15-127">**網路**Microsoft network、 網際網路及內部網路之間的資料中心與您的使用者。</span><span class="sxs-lookup"><span data-stu-id="c5a15-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="c5a15-128">**瀏覽器**其中載入頁面。</span><span class="sxs-lookup"><span data-stu-id="c5a15-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="c5a15-p103">在這三種連線中，通常有五個原因會造成 95% 的頁面緩滿情形。本文將討論這些原因：</span><span class="sxs-lookup"><span data-stu-id="c5a15-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="c5a15-131">瀏覽問題</span><span class="sxs-lookup"><span data-stu-id="c5a15-131">Navigation issues</span></span>
    
- <span data-ttu-id="c5a15-132">內容彙總</span><span class="sxs-lookup"><span data-stu-id="c5a15-132">Content roll up</span></span>
    
- <span data-ttu-id="c5a15-133">大型檔案</span><span class="sxs-lookup"><span data-stu-id="c5a15-133">Large files</span></span>
    
- <span data-ttu-id="c5a15-134">對伺服器的要求太多</span><span class="sxs-lookup"><span data-stu-id="c5a15-134">Many requests to the server</span></span>
    
- <span data-ttu-id="c5a15-135">網頁組件處理</span><span class="sxs-lookup"><span data-stu-id="c5a15-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="c5a15-136">伺服器連線</span><span class="sxs-lookup"><span data-stu-id="c5a15-136">Server connection</span></span>

<span data-ttu-id="c5a15-137">許多影響 SharePoint 內部部署效能的問題也會在 SharePoint Online 上出現。</span><span class="sxs-lookup"><span data-stu-id="c5a15-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="c5a15-p104">一如預期，您有許多手段可控制伺服器在內部部署 SharePoint 中的執行效能。但在 SharePoint Online 上，情形略有不同。您讓伺服器執行的工作越多，呈現頁面所需的時間就越長。而在 SharePoint 中，含有多個網頁組件的複雜頁面才是造成這方面問題的最大禍首。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="c5a15-142">SharePoint Server 的內部</span><span class="sxs-lookup"><span data-stu-id="c5a15-142">SharePoint Server on-premises</span></span>
  
![內部部署伺服器的螢幕擷取畫面](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="c5a15-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c5a15-144">SharePoint Online</span></span>
  
![伺服器連線的螢幕擷取畫面](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="c5a15-p105">在 SharePoint Online 上，某些網頁要求可能實際上最後會呼叫多部伺服器。原本只是一個要求，最後卻可能演變成涉及多部伺服器的多個要求。從頁面載入的觀點來看，這些互動不僅成本昂貴且會讓效率變慢。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="c5a15-149">這些伺服器對伺服器的互動範例如下：</span><span class="sxs-lookup"><span data-stu-id="c5a15-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="c5a15-150">Web 對 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c5a15-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="c5a15-151">Web 對應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="c5a15-151">Web to application servers</span></span>
    
<span data-ttu-id="c5a15-p106">另一個導致伺服器互動速度變慢的因素是快取遺漏。不同於內部部署 SharePoint，雖然機率微乎其微，但您有可能會叫用相同伺服器來取得之前造訪的頁面；這個情形會讓物件快取過時。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="c5a15-154">網路連線</span><span class="sxs-lookup"><span data-stu-id="c5a15-154">Network connection</span></span>

<span data-ttu-id="c5a15-p107">使用不會利用的 WAN 的內部部署 SharePoint，您可能會使用資料中心及使用者之間的高速連線。一般而言，事項很容易管理觀點的網路。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="c5a15-157">在 SharePoint Online 上，則還要再考慮幾個因素，例如：</span><span class="sxs-lookup"><span data-stu-id="c5a15-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="c5a15-158">Microsoft 網路</span><span class="sxs-lookup"><span data-stu-id="c5a15-158">The Microsoft network</span></span>
    
- <span data-ttu-id="c5a15-159">網際網路</span><span class="sxs-lookup"><span data-stu-id="c5a15-159">The Internet</span></span>
    
- <span data-ttu-id="c5a15-160">ISP</span><span class="sxs-lookup"><span data-stu-id="c5a15-160">The ISP</span></span>
    
<span data-ttu-id="c5a15-161">不論您使用哪個 SharePoint (和那個網路) 版本，會導致網路忙碌的因素通常包括：</span><span class="sxs-lookup"><span data-stu-id="c5a15-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="c5a15-162">承載過大</span><span class="sxs-lookup"><span data-stu-id="c5a15-162">Large payload</span></span>
    
- <span data-ttu-id="c5a15-163">檔案太多</span><span class="sxs-lookup"><span data-stu-id="c5a15-163">Many files</span></span>
    
- <span data-ttu-id="c5a15-164">與伺服器的實體距離太遠</span><span class="sxs-lookup"><span data-stu-id="c5a15-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="c5a15-p108">您可以運用 SharePoint Online 中的其中一個功能是 Microsoft CDN （內容傳遞網路）。CDN 基本上是跨多個資料中心部署伺服器的分散式的集合。CDN 與頁面上的內容可以架設在接近用戶端的伺服器上即使用戶端遠從原始的 SharePoint 伺服器。Microsoft 將會使用此更未來來儲存的頁面以無法自訂，例如 SharePoint Online 的管理首頁上的本機執行個體。如需 Cdn 的詳細資訊，請參閱 ＜[內容傳遞網路](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="c5a15-p109">您必須注意但可能無能為力的因素是您的 ISP 連線速度。簡單的速度測試工具會告訴您連線速度。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="c5a15-172">瀏覽器連線</span><span class="sxs-lookup"><span data-stu-id="c5a15-172">Browser connection</span></span>

<span data-ttu-id="c5a15-173">從效能的觀點來看，有幾個與網頁瀏覽器有關的因素要考慮進去。</span><span class="sxs-lookup"><span data-stu-id="c5a15-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="c5a15-p110">非常複雜的頁面都會影響效能。大多數的瀏覽器只能有小快取 (筆 90 MB)，同時平均網頁通常是筆 1.6 MB。這不需要長取得用於。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="c5a15-p111">頻寬也可能發生問題。例如，如果使用者觀看這支影片另一個工作階段中，這會影響您的 SharePoint 頁面的效能。雖然您無法防止使用者媒體資料流，您可以控制的使用者會載入頁面的方式。</span><span class="sxs-lookup"><span data-stu-id="c5a15-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="c5a15-180">請參閱下列文章的不同的 SharePoint Online 頁面自訂技巧及其他最佳作法，協助您達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="c5a15-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="c5a15-181">SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="c5a15-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-182">使用 SharePoint Online 頁面診斷工具</span><span class="sxs-lookup"><span data-stu-id="c5a15-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="c5a15-183">SharePoint Online 的影像最佳化</span><span class="sxs-lookup"><span data-stu-id="c5a15-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-184">延遲載入 SharePoint Online 中的影像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="c5a15-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-185">SharePoint Online 中的縮製及統合技術</span><span class="sxs-lookup"><span data-stu-id="c5a15-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-186">使用內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="c5a15-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-187">使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c5a15-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="c5a15-188">容量規劃和測試 SharePoint Online 的負載</span><span class="sxs-lookup"><span data-stu-id="c5a15-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-189">診斷 SharePoint Online 的效能問題</span><span class="sxs-lookup"><span data-stu-id="c5a15-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-190">使用 SharePoint Online 的物件快取</span><span class="sxs-lookup"><span data-stu-id="c5a15-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="c5a15-191">操作方法：如何避免在 SharePoint Online 中受到節流控制或封鎖</span><span class="sxs-lookup"><span data-stu-id="c5a15-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

