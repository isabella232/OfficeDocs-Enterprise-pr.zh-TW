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
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539937"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="8558d-103">SharePoint Online 效能調整的簡介</span><span class="sxs-lookup"><span data-stu-id="8558d-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="8558d-104">本文說明設計的 SharePoint Online 中的最佳效能頁面時需要考量您需要何種特定部分。</span><span class="sxs-lookup"><span data-stu-id="8558d-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="8558d-105">本文內容</span><span class="sxs-lookup"><span data-stu-id="8558d-105">In this article</span></span>

- <span data-ttu-id="8558d-106">[SharePoint Online 的評量](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics)和[結論達到因為資料](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="8558d-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="8558d-107">檢查效能時使用的標準使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8558d-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="8558d-108">[連線類別的效能調整](introduction-to-performance-tuning-for-sharepoint-online.md#connect)：[伺服器的連線](introduction-to-performance-tuning-for-sharepoint-online.md#server)、[網路連線](introduction-to-performance-tuning-for-sharepoint-online.md#network)和[瀏覽器連線](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="8558d-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="8558d-109">SharePoint Online 度量資訊</span><span class="sxs-lookup"><span data-stu-id="8558d-109">SharePoint Online metrics</span></span>
<span data-ttu-id="8558d-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-110"></span></span>

<span data-ttu-id="8558d-111">下列廣泛的 SharePoint Online 度量值提供有關效能的實際環境資料：</span><span class="sxs-lookup"><span data-stu-id="8558d-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="8558d-112">頁面載入速度</span><span class="sxs-lookup"><span data-stu-id="8558d-112">How fast pages load</span></span>
    
- <span data-ttu-id="8558d-113">每頁所需來回行程次數</span><span class="sxs-lookup"><span data-stu-id="8558d-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="8558d-114">服務的問題</span><span class="sxs-lookup"><span data-stu-id="8558d-114">Issues with the service</span></span>
    
- <span data-ttu-id="8558d-115">導致效能降低的其他事項</span><span class="sxs-lookup"><span data-stu-id="8558d-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="8558d-116">資料所導出的結論</span><span class="sxs-lookup"><span data-stu-id="8558d-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="8558d-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-117"></span></span>

<span data-ttu-id="8558d-118">資料會告訴我們：</span><span class="sxs-lookup"><span data-stu-id="8558d-118">The data tells us:</span></span>
  
- <span data-ttu-id="8558d-119">大部分頁面在 SharePoint Online 上的執行狀況良好。</span><span class="sxs-lookup"><span data-stu-id="8558d-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="8558d-120">非自訂頁面載入速度很快。</span><span class="sxs-lookup"><span data-stu-id="8558d-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="8558d-121">商務用 OneDrive、小組網站和系統頁面 (如 _layouts 等) 載入速度都很快。</span><span class="sxs-lookup"><span data-stu-id="8558d-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="8558d-122">最慢的 1% SharePoint Online 頁面載入時間需要超過 5000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="8558d-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="8558d-p101">您可使用的一項簡單基準測試是透過比較您的入口網站載入時間和商務用 OneDrive 首頁載入時間來測量效能，因其使用的自訂功能不多。在進行網路效能問題疑難排解時，這通常是支援人員要求您完成的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="8558d-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="8558d-125">檢查效能時使用的標準使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8558d-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="8558d-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-126"></span></span>

<span data-ttu-id="8558d-127">網站集合管理員、 網站擁有者、 編輯器或參與者屬於其他安全性群組、 具有其他權限，且因此 SharePoint 會載入頁面的其他元素。</span><span class="sxs-lookup"><span data-stu-id="8558d-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="8558d-128">這是適用於 SharePoint 內部部署和 SharePoint Online 但內部部署案例中的差異便不會輕鬆發現如 SharePoint Online 所示。</span><span class="sxs-lookup"><span data-stu-id="8558d-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="8558d-129">才能正確地評估] 頁面上將如何執行使用者，您應該使用標準的使用者帳戶以避免載入撰寫控制項與其他安全性群組與相關的流量。</span><span class="sxs-lookup"><span data-stu-id="8558d-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="8558d-130">效能調整的連線類別</span><span class="sxs-lookup"><span data-stu-id="8558d-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="8558d-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-131"></span></span>

<span data-ttu-id="8558d-p102">您可將伺服器與使用者之間的連線分類成三種主要元件。在設計 SharePoint Online 頁面以深入瞭解載入時間時，請將這些元件納入考量。</span><span class="sxs-lookup"><span data-stu-id="8558d-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="8558d-134">**伺服器。** Microsoft 主控的資料中心伺服器。</span><span class="sxs-lookup"><span data-stu-id="8558d-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="8558d-135">**網路。** Microsoft network、 網際網路及內部網路之間的資料中心與您的使用者。</span><span class="sxs-lookup"><span data-stu-id="8558d-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="8558d-136">**瀏覽器。** 其中載入頁面。</span><span class="sxs-lookup"><span data-stu-id="8558d-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="8558d-p103">在這三種連線中，通常有五個原因會造成 95% 的頁面緩滿情形。本文將討論這些原因：</span><span class="sxs-lookup"><span data-stu-id="8558d-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="8558d-139">瀏覽問題</span><span class="sxs-lookup"><span data-stu-id="8558d-139">Navigation issues</span></span>
    
- <span data-ttu-id="8558d-140">內容彙總</span><span class="sxs-lookup"><span data-stu-id="8558d-140">Content roll up</span></span>
    
- <span data-ttu-id="8558d-141">大型檔案</span><span class="sxs-lookup"><span data-stu-id="8558d-141">Large files</span></span>
    
- <span data-ttu-id="8558d-142">對伺服器的要求太多</span><span class="sxs-lookup"><span data-stu-id="8558d-142">Many requests to the server</span></span>
    
- <span data-ttu-id="8558d-143">網頁組件處理</span><span class="sxs-lookup"><span data-stu-id="8558d-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="8558d-144">伺服器連線</span><span class="sxs-lookup"><span data-stu-id="8558d-144">Server connection</span></span>
<span data-ttu-id="8558d-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-145"></span></span>

<span data-ttu-id="8558d-146">許多影響 SharePoint 內部部署效能的問題也會在 SharePoint Online 上出現。</span><span class="sxs-lookup"><span data-stu-id="8558d-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="8558d-p104">一如預期，您有許多手段可控制伺服器在內部部署 SharePoint 中的執行效能。但在 SharePoint Online 上，情形略有不同。您讓伺服器執行的工作越多，呈現頁面所需的時間就越長。而在 SharePoint 中，含有多個網頁組件的複雜頁面才是造成這方面問題的最大禍首。</span><span class="sxs-lookup"><span data-stu-id="8558d-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="8558d-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8558d-151">SharePoint Online</span></span>
  
![伺服器連線的螢幕擷取畫面](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="8558d-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="8558d-153">SharePoint</span></span>
  
![內部部署伺服器的螢幕擷取畫面](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="8558d-p105">在 SharePoint Online 上，某些網頁要求可能實際上最後會呼叫多部伺服器。原本只是一個要求，最後卻可能演變成涉及多部伺服器的多個要求。從頁面載入的觀點來看，這些互動不僅成本昂貴且會讓效率變慢。</span><span class="sxs-lookup"><span data-stu-id="8558d-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="8558d-158">這些伺服器對伺服器的互動範例如下：</span><span class="sxs-lookup"><span data-stu-id="8558d-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="8558d-159">Web 對 SQL Server</span><span class="sxs-lookup"><span data-stu-id="8558d-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="8558d-160">Web 對應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="8558d-160">Web to application servers</span></span>
    
<span data-ttu-id="8558d-p106">另一個導致伺服器互動速度變慢的因素是快取遺漏。不同於內部部署 SharePoint，雖然機率微乎其微，但您有可能會叫用相同伺服器來取得之前造訪的頁面；這個情形會讓物件快取過時。</span><span class="sxs-lookup"><span data-stu-id="8558d-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="8558d-163">網路連線</span><span class="sxs-lookup"><span data-stu-id="8558d-163">Network connection</span></span>
<span data-ttu-id="8558d-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-164"></span></span>

<span data-ttu-id="8558d-p107">使用不會利用的 WAN 的內部部署 SharePoint，您可能會使用資料中心及使用者之間的高速連線。一般而言，事項很容易管理觀點的網路。</span><span class="sxs-lookup"><span data-stu-id="8558d-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="8558d-167">在 SharePoint Online 上，則還要再考慮幾個因素，例如：</span><span class="sxs-lookup"><span data-stu-id="8558d-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="8558d-168">Microsoft 網路</span><span class="sxs-lookup"><span data-stu-id="8558d-168">The Microsoft network</span></span>
    
- <span data-ttu-id="8558d-169">網際網路</span><span class="sxs-lookup"><span data-stu-id="8558d-169">The Internet</span></span>
    
- <span data-ttu-id="8558d-170">ISP</span><span class="sxs-lookup"><span data-stu-id="8558d-170">The ISP</span></span>
    
<span data-ttu-id="8558d-171">不論您使用哪個 SharePoint (和那個網路) 版本，會導致網路忙碌的因素通常包括：</span><span class="sxs-lookup"><span data-stu-id="8558d-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="8558d-172">承載過大</span><span class="sxs-lookup"><span data-stu-id="8558d-172">Large payload</span></span>
    
- <span data-ttu-id="8558d-173">檔案太多</span><span class="sxs-lookup"><span data-stu-id="8558d-173">Many files</span></span>
    
- <span data-ttu-id="8558d-174">與伺服器的實體距離太遠</span><span class="sxs-lookup"><span data-stu-id="8558d-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="8558d-p108">您可以運用 SharePoint Online 中的其中一個功能是 Microsoft CDN （內容傳遞網路）。CDN 基本上是跨多個資料中心部署伺服器的分散式的集合。CDN 與頁面上的內容可以架設在接近用戶端的伺服器上即使用戶端遠從原始的 SharePoint 伺服器。Microsoft 將會使用此更未來來儲存的頁面以無法自訂，例如 SharePoint Online 的管理首頁上的本機執行個體。如需 Cdn 的詳細資訊，請參閱 ＜[內容傳遞網路](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)。</span><span class="sxs-lookup"><span data-stu-id="8558d-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="8558d-p109">您必須注意但可能無能為力的因素是您的 ISP 連線速度。簡單的速度測試工具會告訴您連線速度。</span><span class="sxs-lookup"><span data-stu-id="8558d-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="8558d-182">瀏覽器連線</span><span class="sxs-lookup"><span data-stu-id="8558d-182">Browser connection</span></span>
<span data-ttu-id="8558d-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="8558d-183"></span></span>

<span data-ttu-id="8558d-184">從效能的觀點來看，有幾個與網頁瀏覽器有關的因素要考慮進去。</span><span class="sxs-lookup"><span data-stu-id="8558d-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="8558d-p110">非常複雜的頁面都會影響效能。大多數的瀏覽器只能有小快取 (筆 90 MB)，同時平均網頁通常是筆 1.6 MB。這不需要長取得用於。</span><span class="sxs-lookup"><span data-stu-id="8558d-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="8558d-p111">頻寬也可能發生問題。例如，如果使用者觀看這支影片另一個工作階段中，這會影響您的 SharePoint 頁面的效能。雖然您無法防止使用者媒體資料流，您可以控制的使用者會載入頁面的方式。</span><span class="sxs-lookup"><span data-stu-id="8558d-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="8558d-191">請參閱下列文章的不同的 SharePoint Online 頁面自訂技巧及其他最佳作法，協助您達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="8558d-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="8558d-192">SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="8558d-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-193">使用 SharePoint Online 頁面診斷工具</span><span class="sxs-lookup"><span data-stu-id="8558d-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="8558d-194">SharePoint Online 的影像最佳化</span><span class="sxs-lookup"><span data-stu-id="8558d-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-195">延遲載入 SharePoint Online 中的影像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="8558d-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-196">SharePoint Online 中的縮製及統合技術</span><span class="sxs-lookup"><span data-stu-id="8558d-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-197">使用內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="8558d-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-198">使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8558d-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="8558d-199">容量規劃和測試 SharePoint Online 的負載</span><span class="sxs-lookup"><span data-stu-id="8558d-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-200">診斷 SharePoint Online 的效能問題</span><span class="sxs-lookup"><span data-stu-id="8558d-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-201">使用 SharePoint Online 的物件快取</span><span class="sxs-lookup"><span data-stu-id="8558d-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="8558d-202">操作方法：如何避免在 SharePoint Online 中受到節流控制或封鎖</span><span class="sxs-lookup"><span data-stu-id="8558d-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

