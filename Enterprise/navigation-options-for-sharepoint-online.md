---
title: SharePoint Online 的導覽選項
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文說明導覽選項網站與 SharePoint 發佈 SharePoint Online 中啟用。 選擇及設定導覽會大幅影響的效能和延展性的 SharePoint Online 中的網站。
ms.openlocfilehash: 9bf2010000f14b173b63574fab4ee77cb772b3f4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069939"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="9cb1b-104">SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="9cb1b-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="9cb1b-105">本文說明導覽選項網站與 SharePoint 發佈 SharePoint Online 中啟用。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-105">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="9cb1b-106">選擇及設定導覽會大幅影響的效能和延展性的 SharePoint Online 中的網站。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-106">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="9cb1b-107">概觀</span><span class="sxs-lookup"><span data-stu-id="9cb1b-107">Overview</span></span>

<span data-ttu-id="9cb1b-108">導覽提供者設定可能大幅影響效能的整個網站，並仔細考量必須採取挑選導覽提供者和組態有效率地調整 SharePoint 網站的需求。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-108">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="9cb1b-109">有兩個的方塊出導覽提供者，以及自訂導覽實作。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-109">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="9cb1b-110">第一個選項[**（中繼資料） 的受管理導覽**](#using-managed-navigation-and-metadata-in-sharepoint-online)，建議使用，且 SharePoint Online; 中的預設選項的其中一個不過，我們建議，除非有必要，停用安全性調整。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-110">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="9cb1b-111">安全性調整啟用安全--預設設定為此導覽提供者;不過，許多網站不需要安全性調整由於導覽元素通常是一致的網站的所有使用者的額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-111">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="9cb1b-112">若要停用安全性修剪的建議組態，此導覽提供者不需要列舉網站結構與延展性極高與可接受的效能影響。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-112">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="9cb1b-113">第二個選項，[**結構式導覽**](#using-structural-navigation-in-sharepoint-online)，**不在 SharePoint Online 中的建議瀏覽選項**。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-113">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="9cb1b-114">這個導覽提供者所設計的內部拓撲有受限於 SharePoint Online 中的支援。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-114">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="9cb1b-115">雖然它會提供一些額外組的功能與其他導覽選項，這些功能，包括安全性修剪和網站結構列舉型別，有其代價過多的伺服器的呼叫並影響延展性和效能時使用它。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-115">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="9cb1b-116">使用 structed 瀏覽的網站會耗用過多的資源，可能會受到節流。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-116">Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="9cb1b-117">除了的方塊出導覽提供者，許多客戶已成功實作替代自訂導覽實作。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-117">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="9cb1b-118">一種常見的自訂巡覽實作類別樂於儲存瀏覽節點的本機快取的用戶端呈現設計圖樣。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-118">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="9cb1b-119">（請參閱**[搜尋導向用戶端指令碼](#using-search-driven-client-side-scripting)** 本文中）。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-119">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="9cb1b-120">這些導覽提供者有幾個重要的優點：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="9cb1b-121">它們通常適用於回應] 頁面上的設計。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="9cb1b-122">它們是極延展性和效能低落因為他們可以呈現與任何資源成本 （和重新整理逾時之後在背景中的）。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="9cb1b-123">這些導覽提供者可以擷取使用各種不同的策略，範圍從簡單的靜態設定到不同的動態資料提供者的瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="9cb1b-124">資料提供者的範例為使用**搜尋導向導覽**，可讓列舉瀏覽節點和處理安全性有效率地調整的彈性。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="9cb1b-125">有其他常用的選項來建立**自訂導覽提供者**。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-125">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="9cb1b-126">請檢閱[SharePoint Online 入口網站的導覽解決方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)進一步上建置的自訂導覽提供者的指引。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-126">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="9cb1b-127">優點和缺點的 SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="9cb1b-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="9cb1b-128">下表摘要說明每個選項的優缺點。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="9cb1b-129">受管理導覽</span><span class="sxs-lookup"><span data-stu-id="9cb1b-129">Managed navigation</span></span>  |<span data-ttu-id="9cb1b-130">結構式導覽</span><span class="sxs-lookup"><span data-stu-id="9cb1b-130">Structural navigation</span></span>  |<span data-ttu-id="9cb1b-131">搜尋導向導覽</span><span class="sxs-lookup"><span data-stu-id="9cb1b-131">Search-driven navigation</span></span>  |<span data-ttu-id="9cb1b-132">自訂導覽提供者</span><span class="sxs-lookup"><span data-stu-id="9cb1b-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="9cb1b-133">Pros:</span><span class="sxs-lookup"><span data-stu-id="9cb1b-133">Pros:</span></span><br/><br/><span data-ttu-id="9cb1b-134">易於維護</span><span class="sxs-lookup"><span data-stu-id="9cb1b-134">Easy to maintain</span></span><br/><span data-ttu-id="9cb1b-135">建議的選項</span><span class="sxs-lookup"><span data-stu-id="9cb1b-135">Recommended option</span></span><br/>     |<span data-ttu-id="9cb1b-136">Pros:</span><span class="sxs-lookup"><span data-stu-id="9cb1b-136">Pros:</span></span><br/><br/><span data-ttu-id="9cb1b-137">容易設定</span><span class="sxs-lookup"><span data-stu-id="9cb1b-137">Easy to configure</span></span><br/><span data-ttu-id="9cb1b-138">安全性調整</span><span class="sxs-lookup"><span data-stu-id="9cb1b-138">Security trimmed</span></span><br/><span data-ttu-id="9cb1b-139">當內容會新增自動更新</span><span class="sxs-lookup"><span data-stu-id="9cb1b-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="9cb1b-140">Pros:</span><span class="sxs-lookup"><span data-stu-id="9cb1b-140">Pros:</span></span><br/><br/><span data-ttu-id="9cb1b-141">安全性調整</span><span class="sxs-lookup"><span data-stu-id="9cb1b-141">Security trimmed</span></span><br/><span data-ttu-id="9cb1b-142">當新增網站時會自動更新</span><span class="sxs-lookup"><span data-stu-id="9cb1b-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="9cb1b-143">快速載入時間，並在本機上快取的導覽結構</span><span class="sxs-lookup"><span data-stu-id="9cb1b-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="9cb1b-144">Pros:</span><span class="sxs-lookup"><span data-stu-id="9cb1b-144">Pros:</span></span><br/><br/><span data-ttu-id="9cb1b-145">寬的選擇，可用的選項</span><span class="sxs-lookup"><span data-stu-id="9cb1b-145">Wider choice of options available</span></span><br/><span data-ttu-id="9cb1b-146">快速載入時快取正確使用</span><span class="sxs-lookup"><span data-stu-id="9cb1b-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="9cb1b-147">有許多選項適用於回應頁面設計</span><span class="sxs-lookup"><span data-stu-id="9cb1b-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="9cb1b-148">缺點：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-148">Cons:</span></span><br/><br/><span data-ttu-id="9cb1b-149">不會自動更新以反映網站結構</span><span class="sxs-lookup"><span data-stu-id="9cb1b-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="9cb1b-150">如果已啟用安全性調整的影響效能</span><span class="sxs-lookup"><span data-stu-id="9cb1b-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="9cb1b-151">缺點：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-151">Cons:</span></span><br/><br/><span data-ttu-id="9cb1b-152">**不建議使用**</span><span class="sxs-lookup"><span data-stu-id="9cb1b-152">**Not recommended**</span></span><br/><span data-ttu-id="9cb1b-153">**影響效能和延展性**</span><span class="sxs-lookup"><span data-stu-id="9cb1b-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="9cb1b-154">**受到節流限制**</span><span class="sxs-lookup"><span data-stu-id="9cb1b-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="9cb1b-155">缺點：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-155">Cons:</span></span><br/><br/><span data-ttu-id="9cb1b-156">沒有輕鬆排序網站的能力</span><span class="sxs-lookup"><span data-stu-id="9cb1b-156">No ability to easily order sites</span></span><br/><span data-ttu-id="9cb1b-157">需要自訂主版頁面 （必須具備技能）</span><span class="sxs-lookup"><span data-stu-id="9cb1b-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="9cb1b-158">缺點：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-158">Cons:</span></span><br/><br/><span data-ttu-id="9cb1b-159">自訂開發，則需要</span><span class="sxs-lookup"><span data-stu-id="9cb1b-159">Custom development is required</span></span><br/><span data-ttu-id="9cb1b-160">外部資料來源需要儲存的快取 / 例如 Azure</span><span class="sxs-lookup"><span data-stu-id="9cb1b-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="9cb1b-161">網站需求及您技術的功能取決於您網站的最適當的選項。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-161">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="9cb1b-162">如果您想可擴充的方塊出導覽提供者，受管理導覽與停用安全性修剪是很好的選項。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-162">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="9cb1b-163">受管理導覽選項可以透過維護組態中，沒有牽涉到程式碼的自訂檔案，而且可大幅比結構式導覽。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-163">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="9cb1b-164">如果您需要進行安全性調整習慣使用自訂的主版頁面，並維護的 SharePoint Online 中的預設主版頁面可能發生的變更在組織中有某些功能，然後搜尋導向選項可能會產生更好使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-164">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="9cb1b-165">如果您有更複雜的需求，自訂的導覽提供者可能會選擇。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-165">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="9cb1b-166">不建議使用結構式導覽。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-166">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="9cb1b-167">最後，務必注意，SharePoint 會新增額外的導覽提供者和新式的 SharePoint 網站架構，利用多簡維的網站階層和具有 SharePoint 中樞站台的中樞與支點模型的功能。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-167">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="9cb1b-168">這可讓許多案例，以達成不需要使用的 SharePoint 發佈功能，以及這些導覽設定已針對延展性和延遲內 SharePoint Online 進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-168">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="9cb1b-169">請注意，套用相同的原則-簡化呈現的結構，SharePoint 發佈網站整體結構通常可以幫助的整體效能，以及調整。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-169">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="9cb1b-170">這表示是，而不是有數百個站台 （子網站） 的單一網站集合，更好的方法有許多具有極少的子網站 （子網站） 的網站集合。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-170">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="9cb1b-171">在 SharePoint Online 中使用受管理的導覽與中繼資料</span><span class="sxs-lookup"><span data-stu-id="9cb1b-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="9cb1b-172">受管理的導覽是功能的另一個的方塊擴充選項您可以用來重新建立大部分的結構式導覽相同。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-172">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="9cb1b-173">受管理的中繼資料可以設定為已啟用或停用安全性修剪。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-173">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="9cb1b-174">設定停用的安全性調整，受管理的導覽時很有效率載入常數多個伺服器的呼叫的導覽連結時。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-174">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="9cb1b-175">啟用安全性調整，不過，否定受管理導覽的優點，客戶可以選擇瀏覽其中一個自訂導覽解決方案的最佳效能及延展性。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-175">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="9cb1b-176">許多網站不需要進行安全性調整，瀏覽結構通常都是一致的網站的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-176">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="9cb1b-177">如果已停用安全性修剪和連結新增至導覽並非所有使用者都擁有存取權，連結仍然會顯示，但會導致拒絕存取訊息。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-177">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="9cb1b-178">沒有任何不慎內容的存取權的風險。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-178">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="9cb1b-179">如何實作受管理的導覽和結果</span><span class="sxs-lookup"><span data-stu-id="9cb1b-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="9cb1b-180">有幾篇文章 Docs.Microsoft.com 上受管理導覽的詳細資訊，例如，請參閱[在 SharePoint Server 中受管理導覽的概觀](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="9cb1b-181">為了實作受管理的導覽，您設定條款與 Url 對應至網站的導覽結構。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-181">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="9cb1b-182">若要取代在許多情況下的結構式導覽可以甚至是手動 curated 受管理的導覽。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-182">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="9cb1b-183">例如：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-183">For example:</span></span>

![SharePoint Online 網站結構](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="9cb1b-185">下列範例會顯示使用受管理的導覽的複雜導覽效能。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![使用受管理的導覽的複雜導覽的效能](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="9cb1b-187">一致地使用受管理的導覽改善效能要優於結構式導覽方法雷同。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="9cb1b-188">在 SharePoint Online 中使用結構式導覽</span><span class="sxs-lookup"><span data-stu-id="9cb1b-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="9cb1b-189">這是使用預設的全新的瀏覽和是最簡單的解決方案，但如此有昂貴的效能的代價。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-189">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="9cb1b-190">它不需要任何自訂非技術使用者也可以和也輕鬆新增項目、 隱藏項目，從 [設定] 頁面管理導覽。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-190">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="9cb1b-191">這是針對受管理導覽，所以建議使用受管理導覽為 true 也可輕鬆地管理及控制也與不過也改善效能。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-191">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![具有顯示選取的子網站的結構式導覽](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="9cb1b-193">開啟 SharePoint Online 中的結構式導覽</span><span class="sxs-lookup"><span data-stu-id="9cb1b-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="9cb1b-194">若要說明如何使用結構式導覽和顯示標準 SharePoint Online 方案中的效能子選項開啟。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-194">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="9cb1b-195">以下是設定在 [**網站設定**] 頁面上找到的螢幕擷取畫面\>**導覽**。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-195">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![顯示子網站的螢幕擷取畫面](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="9cb1b-197">分析 SharePoint Online 中的結構式導覽效能</span><span class="sxs-lookup"><span data-stu-id="9cb1b-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="9cb1b-198">若要分析 SharePoint 網頁的效能，請在 Internet Explorer 中使用 F12 開發人員工具的 [**網路**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![顯示 F12 dev 工具網路索引標籤的螢幕擷取畫面](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="9cb1b-200">[**網路**] 索引標籤中，按一下正在載入的.aspx 頁面，然後按一下 [**詳細資料**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="9cb1b-201">![顯示詳細資料索引標籤的螢幕擷取畫面](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="9cb1b-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="9cb1b-202">按一下 [**回應標頭**]。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="9cb1b-203">![[詳細資料] 索引標籤的螢幕擷取畫面](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="9cb1b-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="9cb1b-204">SharePoint 會在其回應標頭中傳回一些有用的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="9cb1b-205">下列其中一項最有用是資訊的**SPRequestDuration**這是資訊的值，以毫秒為單位的時間長度要求所需的伺服器上的程序。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-205">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="9cb1b-206">下列螢幕擷取畫面**顯示子網站**未選取的結構式導覽。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-206">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="9cb1b-207">這表示在全域導覽是僅限網站集合] 連結：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-207">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="9cb1b-208">![將載入時間顯示為要求持續時間的螢幕擷取畫面](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="9cb1b-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="9cb1b-209">**SPRequestDuration**機碼具有值為 245 （毫秒）。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-209">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="9cb1b-210">這表示它可傳回要求所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-210">This represents the time it took to return the request.</span></span> <span data-ttu-id="9cb1b-211">由於在網站上只有一個導覽項目，這會是如何 SharePoint Online 會執行而不頻繁的瀏覽的良好基準。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-211">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="9cb1b-212">下一個螢幕擷取畫面顯示如何在子網站中新增影響此機碼。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-212">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="9cb1b-213">![顯示 2502 毫秒要求持續時間的螢幕擷取畫面](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="9cb1b-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="9cb1b-214">新增子網站大幅增加傳回此相當簡單的範例網站頁面要求所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-214">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="9cb1b-215">複雜的網站階層，其中包括頁面導覽中，以及其他組態和拓撲選項能夠大幅增加此影響更進一步。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-215">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="9cb1b-216">使用搜尋導向用戶端指令碼</span><span class="sxs-lookup"><span data-stu-id="9cb1b-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="9cb1b-217">您可以使用搜尋利用背景使用連續編目會內建的索引。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-217">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="9cb1b-218">在搜尋結果提取自搜尋索引和結果是經過安全性調整。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-218">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="9cb1b-219">需要進行安全性調整時，這是通常較快的方塊出導覽提供者。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-219">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="9cb1b-220">使用結構式導覽的搜尋，尤其是如果您的複雜網站結構，會加速的頁面載入時間很。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-220">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="9cb1b-221">這段受管理導覽的主要優點是享有安全性調整。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-221">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="9cb1b-222">此方法涉及建立自訂的主版頁面及使用自訂的 HTML 取代的全新的瀏覽程式碼。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-222">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="9cb1b-223">遵循此程序所述在下列範例中要取代的瀏覽程式碼檔案中`seattle.html`。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-223">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="9cb1b-224">在這個範例中，您將會開啟`seattle.html`檔案，並取代整個元素`id=”DeltaTopNavigation”`具有自訂的 HTML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-224">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="9cb1b-225">範例： 取代在主版頁面中的全新的瀏覽程式碼</span><span class="sxs-lookup"><span data-stu-id="9cb1b-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="9cb1b-226">瀏覽至 [網站設定] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="9cb1b-227">按一下 [**主版頁面**，以開啟主版頁面圖庫。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="9cb1b-228">您可以從這裡瀏覽文件庫，並下載檔案`seattle.master`。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="9cb1b-229">編輯程式碼使用文字編輯器，並刪除下列螢幕擷取畫面中的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![刪除所示的程式碼區塊](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="9cb1b-231">移除之間的程式碼`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`標記，並以下列程式碼片段取代：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. <span data-ttu-id="9cb1b-232">取代中載入的 URL 影像開頭具有網站集合中載入影像連結的錨點標記。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-232">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="9cb1b-233">您所做的變更之後，重新命名檔案，然後將其上傳至主版頁面圖庫。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-233">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="9cb1b-234">這會產生新的.master 檔案。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-234">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="9cb1b-235">此 HTML 是從 JavaScript 程式碼傳回的搜尋結果會填入的基本標記。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-235">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="9cb1b-236">您想要編輯若要變更的值為 var 根程式碼 = 「 網站集合 URL 」 的下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-236">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="9cb1b-237">結果會指派給 self.nodes 陣列及使用 linq.js 將輸出指派給陣列 self.hierarchy 物件超出內建階層。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-237">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="9cb1b-238">此陣列是繫結至 HTML 的物件。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-238">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="9cb1b-239">完成此工作的 toggleView() 函式中藉由將自我物件傳遞至 ko.applyBinding() 函式。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-239">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="9cb1b-240">然後，這樣會使繫結至下列的 HTML 階層陣列：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="9cb1b-241">事件處理常式`mouseenter`和`mouseexit`新增至最上層的導覽，以處理子網站下拉式功能表中完成`addEventsToElements()`函式。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="9cb1b-242">在我們複雜的導覽的範例，而不從基準的結構式導覽若要取得的受管理的導覽方法類似結果在伺服器上所花費的時間剪本機快取顯示載入新鮮的頁面。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="9cb1b-243">關於 JavaScript 檔案...]</span><span class="sxs-lookup"><span data-stu-id="9cb1b-243">About the JavaScript file...</span></span>

<span data-ttu-id="9cb1b-244">整個 JavaScript 檔案如下所示：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-244">The entire JavaScript file is as follows:</span></span>

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="9cb1b-245">若要將摘要說明在上述程式碼`jQuery $(document).ready`函數有`viewModel object`建立，然後`loadNavigationNodes()`來呼叫函式，該物件上的。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-245">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="9cb1b-246">此函數可以載入儲存在用戶端瀏覽器 HTML5 本機儲存體中先前內建的導覽階層或它會呼叫函式`queryRemoteInterface()`。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-246">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="9cb1b-247">`QueryRemoteInterface()`建置要求使用`getRequest()`函式查詢參數稍早在指令碼中定義並再從伺服器傳回資料。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-247">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="9cb1b-248">此資料是基本上是陣列的資料傳輸物件具有各種屬性，以表示網站集合中的所有網站。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-248">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="9cb1b-249">然後剖析此資料到先前定義`SPO.Models.NavigationNode`物件使用這個`Knockout.js`資料值繫結到我們先前定義的 HTML 建立用於觀察到的屬性。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="9cb1b-250">物件是然後放入結果陣列。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-250">The objects are then put into a results array.</span></span> <span data-ttu-id="9cb1b-251">此陣列是剖析成 JSON 使用油墨廓清且儲存在本機瀏覽器儲存在未來的頁面載入改善效能。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-251">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="9cb1b-252">這個方法的優點</span><span class="sxs-lookup"><span data-stu-id="9cb1b-252">Benefits of this approach</span></span>

<span data-ttu-id="9cb1b-253">[此方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)的主要好處之一是，藉由使用 HTML5 本機存放區，導覽會儲存在本機使用者下次載入頁面的下一個時間。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-253">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="9cb1b-254">我們會從使用結構式導覽; 搜尋 API 取得主要的效能改進不過，它會採用一些技術的功能，以執行及自訂這項功能。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-254">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="9cb1b-255">在[範例實作](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)，網站會排序的方塊出結構式導覽; 為相同的方式依字母順序排列順序。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-255">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="9cb1b-256">如果您想要從這個順序以外，它就會以開發和維護更複雜。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-256">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="9cb1b-257">此外，此方法需要您支援的主版頁面以外。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-257">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="9cb1b-258">如果自訂主版頁面並不會維護，您的網站會錯過更新和 Microsoft 對主版頁面的增強功能。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-258">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="9cb1b-259">[上述程式碼](#about-the-javascript-file)具有下列相依性：</span><span class="sxs-lookup"><span data-stu-id="9cb1b-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="9cb1b-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="9cb1b-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="9cb1b-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="9cb1b-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="9cb1b-262">Linq.js- http://linqjs.codeplex.com/，或 github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="9cb1b-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="9cb1b-263">目前版本的 LinqJS 不包含在上面的程式碼中使用的 ByHierarchy 方法，並將會中斷瀏覽程式碼。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-263">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="9cb1b-264">若要修正此問題，請將下列方法新增至一行之前 Linq.js 檔案`Flatten: function ()`。</span><span class="sxs-lookup"><span data-stu-id="9cb1b-264">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="9cb1b-265">相關主題</span><span class="sxs-lookup"><span data-stu-id="9cb1b-265">Related topics</span></span>

[<span data-ttu-id="9cb1b-266">SharePoint Server 中受管理導覽的概觀</span><span class="sxs-lookup"><span data-stu-id="9cb1b-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

