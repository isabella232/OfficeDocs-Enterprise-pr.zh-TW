---
title: SharePoint Online 的導覽選項
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: 本文說明與 SharePoint 發佈啟用在 SharePoint Online 中的導覽選項的網站。選擇及導覽的設定會大幅影響效能及延展性的 SharePoint Online 中的網站。
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547175"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="83c2e-104">SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="83c2e-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="83c2e-p102">本文說明與 SharePoint 發佈啟用在 SharePoint Online 中的導覽選項的網站。選擇及導覽的設定會大幅影響效能及延展性的 SharePoint Online 中的網站。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="83c2e-107">概觀</span><span class="sxs-lookup"><span data-stu-id="83c2e-107">Overview</span></span>

<span data-ttu-id="83c2e-p103">導覽提供者設定可能大幅影響效能的整個網站，並仔細考慮必須採取挑選導覽提供者與調整有效的 SharePoint 網站需求的設定。有兩個的方塊 （英文） 導覽提供者，如自訂導覽實作。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="83c2e-p104">第一個選項[**（中繼資料） 的受管理導覽**](#using-managed-navigation-and-metadata-in-sharepoint-online)，建議和是其中一個 SharePoint Online; 中的預設選項不過，我們建議除非有必要停用安全性修剪。安全性調整安全--預設設定為啟用此功能提供者 ；不過，許多網站不需要安全性調整自導覽元素通常是一致的所有使用者之網站的額外的負荷。若要停用安全性修剪的建議設定，此導覽提供者不需要列舉網站結構，且是可接受的效能影響具高度。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="83c2e-p105">第二個選項、[**結構化導覽**](#using-structural-navigation-in-sharepoint-online)，**不在 SharePoint Online 中的建議的導覽選項**。這個導覽提供者被設計用於內部部署拓撲有限的 SharePoint Online 支援。當它提供功能與其他導覽選項一些其他設定時，這些功能，包括安全性修剪和網站結構列舉的是有代價過多的伺服器的電話及影響延展性和效能時加以使用。取用過多的資源使用 structed 瀏覽網站可能會受限於節流設定。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="83c2e-p106">除了的方塊 （英文） 導覽提供者許多客戶已成功實作替代自訂導覽實作。一種常見的自訂導覽實作類別包含了前所未見儲存導覽節點本機快取的用戶端呈現設計模式。（請參閱**[搜尋導向的用戶端指令碼](#using-search-driven-client-side-scripting)** 在本文中）。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="83c2e-120">這些功能提供者有幾個重要優點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="83c2e-121">它們通常也與回應頁面設計搭配運作。</span><span class="sxs-lookup"><span data-stu-id="83c2e-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="83c2e-122">他們是極佳和效能低落因為他們可以呈現不具資源成本 （及重新整理逾時之後在背景中的）。</span><span class="sxs-lookup"><span data-stu-id="83c2e-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="83c2e-123">這些功能提供者可以擷取使用不同的策略，從簡單的靜態組態延伸到不同的動態資料提供者的瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="83c2e-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="83c2e-124">資料提供者的範例是使用**搜尋導向導覽**，讓列舉導覽節點及處理安全性調整有效率的彈性。</span><span class="sxs-lookup"><span data-stu-id="83c2e-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="83c2e-p107">還有其他常用的選項來建立**自訂導覽提供者**。請如需進一步上建置自訂導覽提供者的指導，檢閱[的 SharePoint Online 的入口網站的導覽解決方案](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="83c2e-127">專業人員和缺點 SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="83c2e-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="83c2e-128">下表摘要說明每個選項的優缺點。</span><span class="sxs-lookup"><span data-stu-id="83c2e-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="83c2e-129">受管理導覽</span><span class="sxs-lookup"><span data-stu-id="83c2e-129">Managed navigation</span></span>  |<span data-ttu-id="83c2e-130">結構式導覽</span><span class="sxs-lookup"><span data-stu-id="83c2e-130">Structural navigation</span></span>  |<span data-ttu-id="83c2e-131">搜尋導向導覽</span><span class="sxs-lookup"><span data-stu-id="83c2e-131">Search-driven navigation</span></span>  |<span data-ttu-id="83c2e-132">自訂導覽提供者</span><span class="sxs-lookup"><span data-stu-id="83c2e-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="83c2e-133">優點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-133">Pros:</span></span><br/><br/><span data-ttu-id="83c2e-134">易於維護</span><span class="sxs-lookup"><span data-stu-id="83c2e-134">Easy to maintain</span></span><br/><span data-ttu-id="83c2e-135">建議您選擇</span><span class="sxs-lookup"><span data-stu-id="83c2e-135">Recommended option</span></span><br/>     |<span data-ttu-id="83c2e-136">優點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-136">Pros:</span></span><br/><br/><span data-ttu-id="83c2e-137">容易設定</span><span class="sxs-lookup"><span data-stu-id="83c2e-137">Easy to configure</span></span><br/><span data-ttu-id="83c2e-138">安全性調整</span><span class="sxs-lookup"><span data-stu-id="83c2e-138">Security trimmed</span></span><br/><span data-ttu-id="83c2e-139">自動更新為新增內容</span><span class="sxs-lookup"><span data-stu-id="83c2e-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="83c2e-140">優點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-140">Pros:</span></span><br/><br/><span data-ttu-id="83c2e-141">安全性調整</span><span class="sxs-lookup"><span data-stu-id="83c2e-141">Security trimmed</span></span><br/><span data-ttu-id="83c2e-142">當新增網站時會自動更新</span><span class="sxs-lookup"><span data-stu-id="83c2e-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="83c2e-143">載入時間快速以及本機快取的導覽結構</span><span class="sxs-lookup"><span data-stu-id="83c2e-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="83c2e-144">優點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-144">Pros:</span></span><br/><br/><span data-ttu-id="83c2e-145">更廣泛選擇的可用選項</span><span class="sxs-lookup"><span data-stu-id="83c2e-145">Wider choice of options available</span></span><br/><span data-ttu-id="83c2e-146">Fast 載入時快取正確使用</span><span class="sxs-lookup"><span data-stu-id="83c2e-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="83c2e-147">許多選項以及使用回應頁面設計</span><span class="sxs-lookup"><span data-stu-id="83c2e-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="83c2e-148">缺點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-148">Cons:</span></span><br/><br/><span data-ttu-id="83c2e-149">不會自動更新來反映網站結構</span><span class="sxs-lookup"><span data-stu-id="83c2e-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="83c2e-150">如果已啟用安全性調整的影響效能</span><span class="sxs-lookup"><span data-stu-id="83c2e-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="83c2e-151">缺點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-151">Cons:</span></span><br/><br/><span data-ttu-id="83c2e-152">**不建議使用**</span><span class="sxs-lookup"><span data-stu-id="83c2e-152">**Not recommended**</span></span><br/><span data-ttu-id="83c2e-153">**影響效能和延展性**</span><span class="sxs-lookup"><span data-stu-id="83c2e-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="83c2e-154">**受限於節流**</span><span class="sxs-lookup"><span data-stu-id="83c2e-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="83c2e-155">缺點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-155">Cons:</span></span><br/><br/><span data-ttu-id="83c2e-156">沒有輕鬆排序網站的能力</span><span class="sxs-lookup"><span data-stu-id="83c2e-156">No ability to easily order sites</span></span><br/><span data-ttu-id="83c2e-157">需要自訂主版頁面 (必須具備技能)</span><span class="sxs-lookup"><span data-stu-id="83c2e-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="83c2e-158">缺點：</span><span class="sxs-lookup"><span data-stu-id="83c2e-158">Cons:</span></span><br/><br/><span data-ttu-id="83c2e-159">自訂開發為必要</span><span class="sxs-lookup"><span data-stu-id="83c2e-159">Custom development is required</span></span><br/><span data-ttu-id="83c2e-160">外部資料來源需要儲存快取 / 例如 Azure</span><span class="sxs-lookup"><span data-stu-id="83c2e-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="83c2e-p108">網站需求及技術的功能取決於您網站的最適當的選項。如果您想可擴充的方塊 （英文） 導覽提供者、 受管理導覽與停用安全性修剪是非常好] 選項。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="83c2e-p109">受管理導覽選項可以透過維護組態，不包含程式碼的自訂檔案和它會比結構化導覽大幅快。如果您需要安全性修剪和會知道如何使用自訂主版頁面及維護 SharePoint Online 的預設主版頁面中可能發生的變更組織中有某些功能，然後搜尋導向選項可能會產生更好使用者經驗。如果您有較複雜的需求，自訂導覽提供者可能會是正確的選擇。不建議使用結構化導覽。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="83c2e-p110">最後，務必注意 SharePoint 新增其他導覽提供者和現代運用多扁平化的網站階層和中樞與支點模型與 SharePoint 中樞站台的 SharePoint 網站架構的功能。這可讓許多案例，可達到不需要 SharePoint 發佈功能的使用與這些導覽設定最佳化以具備延展性和 SharePoint Online 中的延遲。請注意套用相同的基本原則-簡化呈現的結構、 SharePoint 發佈網站的整體結構通常可以幫助的整體效能及擴充，以及。這意味著，而不是交談含有數百個站台 （子網站） 的單一網站集合，以更好的方法是有許多網站集合具有很少的子網站 （子網站）。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="83c2e-171">在 SharePoint Online 中使用受管理的導覽與中繼資料</span><span class="sxs-lookup"><span data-stu-id="83c2e-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="83c2e-p111">受管理的導覽是功能的另一個的方塊 （英文） 選項可用來重新建立大部分的結構化導覽相同。受管理的中繼資料可以設定為已啟用或停用安全性修剪。當設定已停用安全性修剪、 受管理的導覽是許多常用它載入和常數之伺服器的電話號碼的所有導覽連結。啟用安全性調整，但是可以取消某些受管理導覽的優點與客戶可以選擇探索其中一個自訂導覽方案的最佳效能及延展性。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="83c2e-p112">許多網站不需要安全性調整為導覽結構通常是一致的網站的所有使用者。如果已停用安全性修剪和連結新增至不是所有使用者都擁有存取權的導覽、 連結仍會顯示但拒絕存取訊息將會導致。沒有由於意外存取內容的風險。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="83c2e-179">如何實作受管理的導覽和結果</span><span class="sxs-lookup"><span data-stu-id="83c2e-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="83c2e-180">有數個文章 Docs.Microsoft.com 受管理導覽的詳細資訊例如，請參閱[SharePoint Server 中的受管理導覽的概觀](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)。</span><span class="sxs-lookup"><span data-stu-id="83c2e-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="83c2e-p113">若要實作受管理的導覽，您設定合約 url 對應至網站的導覽結構。取代在許多情況下的結構化導覽可以甚至是手動 curated 受管理的導覽。例如：</span><span class="sxs-lookup"><span data-stu-id="83c2e-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![SharePoint Online 網站結構](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="83c2e-185">下列範例顯示使用受管理導覽的複雜導覽效能。</span><span class="sxs-lookup"><span data-stu-id="83c2e-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![使用受管理的導覽的複雜導覽的效能](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="83c2e-187">使用受管理的導覽持續改善效能相較於結構化導覽方法。</span><span class="sxs-lookup"><span data-stu-id="83c2e-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="83c2e-188">在 SharePoint Online 中使用結構式導覽</span><span class="sxs-lookup"><span data-stu-id="83c2e-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="83c2e-p114">這是使用預設的方塊 （英文） 導覽及是最簡單的解決方案但如此具有昂貴的效能取捨。不需要任何自訂以及非使用者的還輕鬆地新增項目、 隱藏項目，從 [設定] 頁面上的管理功能。這是不過也也可輕鬆地管理及控制也與受管理導覽所以建議使用受管理的導覽為 true 會改善效能。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![具有顯示選取的子網站的結構化導覽](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="83c2e-193">開啟 SharePoint Online 中的結構式導覽</span><span class="sxs-lookup"><span data-stu-id="83c2e-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="83c2e-p115">為了說明如何使用結構化導覽和顯示標準 SharePoint Online 解決方案的效能子網站] 選項開啟。以下是設定在 [**網站設定**] 頁面上找到的螢幕擷取畫面\>**導覽**。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![顯示子網站的螢幕擷取畫面](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="83c2e-197">分析 SharePoint Online 中的結構式導覽效能</span><span class="sxs-lookup"><span data-stu-id="83c2e-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="83c2e-198">若要分析 SharePoint 網頁的效能，使用 Internet Explorer 中的 F12 開發人員工具的 [**網路**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="83c2e-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![顯示 F12 dev 工具網路索引標籤的螢幕擷取畫面](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="83c2e-200">在 **[網路]** 索引標籤上，按一下正在載入的.aspx 頁面，然後按一下 **[詳細資料]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="83c2e-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="83c2e-201">![顯示詳細資料索引標籤的螢幕擷取畫面](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="83c2e-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="83c2e-202">按一下 **[回應標頭]**。</span><span class="sxs-lookup"><span data-stu-id="83c2e-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="83c2e-203">![[詳細資料] 索引標籤的螢幕擷取畫面](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="83c2e-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="83c2e-204">SharePoint 傳回在其回應標頭中一些有用的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="83c2e-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="83c2e-p116">其中一項最有用是資訊的**SPRequestDuration**是資訊的值的要求所花的伺服器上的程序 （毫秒）。在下列螢幕擷取畫面**顯示子網站**是未核取結構化導覽。這表示全域導覽中是僅限網站集合] 連結：</span><span class="sxs-lookup"><span data-stu-id="83c2e-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="83c2e-208">![將載入時間顯示為要求持續時間的螢幕擷取畫面](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="83c2e-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="83c2e-p117">**SPRequestDuration**金鑰已 245 （毫秒） 的值。這代表傳回要求所花的時間。由於網站上沒有只有一個導覽項目，這會是很好的基準針對如何 SharePoint Online 執行不頻繁的導覽。下一步的螢幕擷取畫面顯示在子網站中新增如何影響此機碼。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="83c2e-213">![顯示 2502 毫秒要求持續時間的螢幕擷取畫面](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="83c2e-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="83c2e-p118">新增子網站有大幅增加傳回此可以相對簡單範例網站頁面要求所花費的時間。複雜的網站階層，包括頁面導覽，和其他設定及拓撲選項可大幅增加此影響更進一步。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="83c2e-216">使用搜尋導向用戶端指令碼</span><span class="sxs-lookup"><span data-stu-id="83c2e-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="83c2e-p119">您可以使用搜尋運用使用連續編目的背景內建的索引。從搜尋索引已取出的搜尋結果與結果的安全性調整。這是第通常較快的方塊 （英文） 導覽提供者安全性調整在必要時。使用搜尋結構化導覽，特別是如果您有複雜網站結構，將會加速頁面載入時間許多。透過受管理導覽的主要優點的這是獲益安全性調整。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="83c2e-p120">這個方法需要建立的自訂主版頁面及以自訂的 HTML 取代的方塊 （英文） 導覽程式碼。請遵循此程序在下列範例中取代導覽中的程式碼檔案概述`seattle.html`。在這個範例中，您將會開啟`seattle.html`檔案和取代整個元素`id=”DeltaTopNavigation”`具有自訂的 HTML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="83c2e-225">範例： 取代的方塊 （英文） 導覽中的程式碼的主版頁面</span><span class="sxs-lookup"><span data-stu-id="83c2e-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="83c2e-226">導覽至 [網站設定] 頁面。</span><span class="sxs-lookup"><span data-stu-id="83c2e-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="83c2e-227">按一下 **[主版頁面]** 來開啟主版頁面圖庫。</span><span class="sxs-lookup"><span data-stu-id="83c2e-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="83c2e-228">您可以從這裡瀏覽整份文件庫並下載檔案`seattle.master`。</span><span class="sxs-lookup"><span data-stu-id="83c2e-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="83c2e-229">使用文字編輯器編輯程式碼，刪除下列螢幕擷取畫面中的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="83c2e-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![刪除所示的程式碼區塊](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="83c2e-231">移除之間的程式碼`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`和`<\SharePoint:AjaxDelta>`標記並取代下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="83c2e-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="83c2e-p121">取代的 URL 中載入影像開頭包含連結至網站集合中載入影像的錨點標記。進行的變更之後，重新命名檔案並再將其上傳到主版頁面圖庫。這會產生新的以.master 檔案。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="83c2e-p122">這個 HTML 都將會填入的搜尋結果傳回從 JavaScript 程式碼的基本標記。您必須編輯程式碼來變更 var 根值 ="網站集合 URL"如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="83c2e-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="83c2e-p123">結果會指派給 self.nodes 陣列和不在使用 linq.js 將輸出指派給陣列 self.hierarchy 物件的內建階層。此陣列是繫結至 HTML 物件。做法是 toggleView() 函數中自我物件傳遞至 ko.applyBinding() 函數。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="83c2e-240">然後這會使要繫結至下列 HTML 的階層陣列：</span><span class="sxs-lookup"><span data-stu-id="83c2e-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="83c2e-241">事件處理常式的`mouseenter`和`mouseexit`新增至要處理的子網站下拉式清單功能表中完成的最上層導覽`addEventsToElements()`函數。</span><span class="sxs-lookup"><span data-stu-id="83c2e-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="83c2e-242">在我們複雜導覽的範例，沒有基準結構化導覽列中取得的受管理的導覽方法類似結果之伺服器上所花費的時間剪本機快取顯示載入全新的頁面。</span><span class="sxs-lookup"><span data-stu-id="83c2e-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="83c2e-243">關於 JavaScript 檔案...]</span><span class="sxs-lookup"><span data-stu-id="83c2e-243">About the JavaScript file...</span></span>

<span data-ttu-id="83c2e-244">整個 JavaScript 檔案如下所示：</span><span class="sxs-lookup"><span data-stu-id="83c2e-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="83c2e-p124">若要摘要說明在上面所示的程式碼`jQuery $(document).ready`函數有`viewModel object`建立然後`loadNavigationNodes()`呼叫該物件上的函數。此函數也會載入 HTML5 的本機存放區的用戶端瀏覽器中儲存的先前內建的導覽階層或它會呼叫此函數`queryRemoteInterface()`。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="83c2e-p125">`QueryRemoteInterface()`是以要求使用`getRequest()`函數與查詢參數定義稍早在指令碼，然後傳回從伺服器的 [資料。此資料是基本上以使用各種屬性的資料傳輸物件表示之網站集合中的所有網站的陣列。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="83c2e-249">然後剖析此資料至先前定義`SPO.Models.NavigationNode`物件使用`Knockout.js`來建立資料繫結到我們稍早所定義的 HTML 的值可觀察屬性使用。</span><span class="sxs-lookup"><span data-stu-id="83c2e-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="83c2e-p126">物件是然後放入結果陣列。此陣列是剖析至 JSON 使用油墨廓清並儲存在本機瀏覽器儲存在未來的頁面載入改善效能。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="83c2e-252">這個方法的優點</span><span class="sxs-lookup"><span data-stu-id="83c2e-252">Benefits of this approach</span></span>

<span data-ttu-id="83c2e-p127">[這個方法](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)一主要優點是藉由使用 HTML5 的本機存放區，瀏覽會儲存在本機使用者他們載入頁面，下一次。我們要從使用結構化導覽 ； 搜尋 API 取得主要效能改良功能不過，花費一些技術功能來執行和自訂這項功能。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="83c2e-p128">以的方塊 （英文） 結構化導覽; 相同的方式來排序[範例實作](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)網站字母順序排列。若您想要此順序以外，是說過更複雜開發及維護。此外，這個方法需要以外支援的主版頁面。如果不保留的自訂主版頁面，您的網站會錯過更新和 Microsoft 對主版頁面的增強功能。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="83c2e-259">[上面的程式碼](#about-the-javascript-file)具有下列相依性：</span><span class="sxs-lookup"><span data-stu-id="83c2e-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="83c2e-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="83c2e-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="83c2e-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="83c2e-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="83c2e-262">Linq.js- http://linqjs.codeplex.com/，或 github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="83c2e-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="83c2e-p129">LinqJS 的目前版本不包含在上面的程式碼中使用的 ByHierarchy 方法並將會自動換行導覽程式碼。若要修正此問題，檔案中新增下列方法 Linq.js 一行之前`Flatten: function ()`。</span><span class="sxs-lookup"><span data-stu-id="83c2e-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="83c2e-265">相關主題</span><span class="sxs-lookup"><span data-stu-id="83c2e-265">Related topics</span></span>

[<span data-ttu-id="83c2e-266">SharePoint Server 中受管理導覽的概觀</span><span class="sxs-lookup"><span data-stu-id="83c2e-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

