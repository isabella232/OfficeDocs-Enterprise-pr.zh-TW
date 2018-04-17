---
title: 設定搜尋 onedrive for Business 多重地理位置
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何在多個地理位置環境中設定搜尋。
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="74806-103">設定搜尋 onedrive for Business 多重地理位置</span><span class="sxs-lookup"><span data-stu-id="74806-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="74806-104">在多個地理位置 SharePoint Online (SPO) 環境中，組織可以有一個 Office 365 租用戶，但其 SharePoint 內容儲存在多個地理位置-一個集中位置及一或多衛星地理位置。</span><span class="sxs-lookup"><span data-stu-id="74806-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="74806-p101">每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時，查詢扇形至所有索引，並傳回的結果會合併。</span><span class="sxs-lookup"><span data-stu-id="74806-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="74806-p102">例如地理位置中的使用者可以搜尋的內容儲存在另一個地理位置，或限制到不同地理位置的 SharePoint 網站上的內容。如果使用者可以存取此內容，搜尋會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="74806-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="74806-109">其中中的搜尋用戶端的多重地理位置環境？</span><span class="sxs-lookup"><span data-stu-id="74806-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="74806-110">這些用戶端可以從所有地理位置傳回的結果：</span><span class="sxs-lookup"><span data-stu-id="74806-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="74806-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="74806-111">OneDrive for Business</span></span>

-   <span data-ttu-id="74806-112">Delve</span><span class="sxs-lookup"><span data-stu-id="74806-112">Delve</span></span>

-   <span data-ttu-id="74806-113">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="74806-113">The SharePoint home page</span></span>

-   <span data-ttu-id="74806-114">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="74806-114">The Search Center</span></span>

-   <span data-ttu-id="74806-115">使用 SharePoint 搜尋 API 的自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="74806-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="74806-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="74806-116">OneDrive for Business</span></span>

<span data-ttu-id="74806-117">多個地理位置環境已設定，如搜尋 OneDrive 中的使用者會從所有地理位置取得結果。</span><span class="sxs-lookup"><span data-stu-id="74806-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="74806-118">Delve</span><span class="sxs-lookup"><span data-stu-id="74806-118">Delve</span></span>

<span data-ttu-id="74806-119">多個地理位置環境已設定，如搜尋 Delve 中的使用者會從所有地理位置取得結果。</span><span class="sxs-lookup"><span data-stu-id="74806-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="74806-p103">Delve 摘要與設定檔卡片只會顯示儲存在**中央**位置的檔案的預覽。衛星地理位置中儲存的檔案，該檔案類型的圖示顯示改用。</span><span class="sxs-lookup"><span data-stu-id="74806-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="74806-122">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="74806-122">The SharePoint home page</span></span>

<span data-ttu-id="74806-p104">為多個地理位置環境已設定，使用者會看到新聞、 從在其 SharePoint 首頁] 頁面上的多個地理位置的最新和追蹤網站。如果他們在 SharePoint 首頁] 頁面上使用 [搜尋] 方塊中，他們將來自多個地理位置取得合併後的結果。</span><span class="sxs-lookup"><span data-stu-id="74806-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="74806-125">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="74806-125">The Search Center</span></span>

<span data-ttu-id="74806-p105">在多個地理位置之後環境具有已設定從他們自己的地理位置的每個搜尋中心會繼續只顯示結果。系統管理員必須從所有地理位置取得結果的 [[變更每個搜尋中心的設定](#_Set_up_a_1)。之後，在搜尋中心搜尋使用者從所有地理位置取得結果。</span><span class="sxs-lookup"><span data-stu-id="74806-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="74806-129">自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="74806-129">Custom search applications</span></span>

<span data-ttu-id="74806-p106">像平常一樣自訂搜尋應用程式互動的搜尋索引使用現有的 SharePoint 搜尋 REST Api。若要從所有或部分的地理位置取得結果，將應用程式必須[呼叫 API 並加入新的多個地理位置查詢參數](#_Get_custom_search)要求中。這會觸發風扇移出所有地理位置的查詢。</span><span class="sxs-lookup"><span data-stu-id="74806-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="74806-133">什麼是關於多個地理位置環境中的搜尋不同？</span><span class="sxs-lookup"><span data-stu-id="74806-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="74806-134">您可能會先熟悉、 部分搜尋功能以不同方式運作多重地理位置環境中。</span><span class="sxs-lookup"><span data-stu-id="74806-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="74806-135"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="74806-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="74806-136"><strong>它的運作方式</strong></span><span class="sxs-lookup"><span data-stu-id="74806-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="74806-137"><strong>因應措施</strong></span><span class="sxs-lookup"><span data-stu-id="74806-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-138">升級的結果</span><span class="sxs-lookup"><span data-stu-id="74806-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="74806-p107">您可以建立查詢規則升級的結果的不同層級： 整個租用戶、 網站集合或網站。在多個地理位置環境中，定義<strong>租用戶</strong>層級升級的結果如果您想要升級到<strong>所有</strong>地理位置中的搜尋中心的結果。如果您<strong>只</strong>想要提升結果在搜尋中心網站集合或網站的地理位置中，定義結果在<strong>網站集合</strong>或<strong>網站</strong>層級。</span><span class="sxs-lookup"><span data-stu-id="74806-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="74806-142">如果您不需要不同升級的結果每個地理位置，例如不同的規則出差，建議您定義升級的租用戶層級的結果。</span><span class="sxs-lookup"><span data-stu-id="74806-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74806-143">搜尋精簡器</span><span class="sxs-lookup"><span data-stu-id="74806-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="74806-p108">搜尋傳回從租用戶的所有地理位置的精簡器與然後彙總。彙總為最佳的能力，這表示精簡器計數可能不正確的 100%。對於大部分搜尋導向的情況，此正確性 」 即足以。</span><span class="sxs-lookup"><span data-stu-id="74806-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="74806-147">搜尋導向應用程式相依於精簡器完整性的查詢每個地理位置單獨而不需使用多個地理位置送出。</span><span class="sxs-lookup"><span data-stu-id="74806-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="74806-148">多個地理位置搜尋不支援動態值區數值精簡器。</span><span class="sxs-lookup"><span data-stu-id="74806-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="74806-149"><a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize"參數</a>使用的數字的精簡器。</span><span class="sxs-lookup"><span data-stu-id="74806-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74806-150">文件識別碼</span><span class="sxs-lookup"><span data-stu-id="74806-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="74806-151">如果您正在開發搜尋導向的應用程式的文件識別碼而定，請注意在多個地理位置環境中的文件識別碼不唯一所有地理位置，他們是唯一的每個地理位置。</span><span class="sxs-lookup"><span data-stu-id="74806-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="74806-p109">我們已新增欄可識別的地理位置。若要達到重複使用此資料行。此欄名為"GeoLocationSource"。</span><span class="sxs-lookup"><span data-stu-id="74806-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-155">結果數目</span><span class="sxs-lookup"><span data-stu-id="74806-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="74806-156">[搜尋結果] 頁面上顯示合併的結果的地理位置，但不能超過 500 結果] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="74806-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="74806-157">在多個地理位置環境中的搜尋不支援項目？</span><span class="sxs-lookup"><span data-stu-id="74806-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="74806-158">一些您可能會先熟悉、 搜尋功能不支援多個地理位置環境中。</span><span class="sxs-lookup"><span data-stu-id="74806-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="74806-159"><strong>搜尋功能</strong></span><span class="sxs-lookup"><span data-stu-id="74806-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="74806-160"><strong>注意事項</strong></span><span class="sxs-lookup"><span data-stu-id="74806-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-161">僅限應用程式的驗證</span><span class="sxs-lookup"><span data-stu-id="74806-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="74806-162">僅限應用程式的驗證 （從服務的權限存取） 不支援在多個地理位置搜尋。</span><span class="sxs-lookup"><span data-stu-id="74806-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74806-163">訪客使用者</span><span class="sxs-lookup"><span data-stu-id="74806-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="74806-164">訪客使用者只取得的地理位置，它們從搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="74806-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="74806-165">實務搜尋的運作方式在多個地理位置環境中</span><span class="sxs-lookup"><span data-stu-id="74806-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="74806-166">**所有**搜尋用戶端使用現有的 SharePoint 搜尋 REST Api 互動搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="74806-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="74806-167">搜尋用戶端會呼叫 EnableMultiGeoSearch 查詢屬性的搜尋 REST 端點 = true。</span><span class="sxs-lookup"><span data-stu-id="74806-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="74806-168">查詢會傳送到租用戶中的所有地理位置。</span><span class="sxs-lookup"><span data-stu-id="74806-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="74806-169">每個地理位置的搜尋結果會合併並排名。</span><span class="sxs-lookup"><span data-stu-id="74806-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="74806-170">用戶端取得整合的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="74806-170">The client gets unified search results.</span></span>



<span data-ttu-id="74806-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>請注意我們不合併搜尋結果直到我們已收到來自所有地理位置的結果。這表示多個地理位置的搜尋具有額外的延遲比較在只有一部地理位置的環境中的搜尋。</span><span class="sxs-lookup"><span data-stu-id="74806-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="74806-173">要取得以顯示所有地理位置的結果在搜尋中心</span><span class="sxs-lookup"><span data-stu-id="74806-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="74806-174">每個搜尋中心具有數個區域且您可以個別設定每個類別。</span><span class="sxs-lookup"><span data-stu-id="74806-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="74806-175">請確定您執行這些步驟以具有編輯搜尋結果頁面和搜尋結果網頁組件的權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="74806-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="74806-176">瀏覽至 [搜尋結果頁面 （請參閱[清單中](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)的搜尋結果頁面）</span><span class="sxs-lookup"><span data-stu-id="74806-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="74806-p111">選取 [垂直若要設定，按一下 [**設定**齒輪圖示右上角，然後按一下 [**編輯頁面]**。在編輯模式中開啟的搜尋結果頁面。</span><span class="sxs-lookup"><span data-stu-id="74806-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="74806-p112">在搜尋結果網頁組件，將滑鼠指標移至左上右上角的 [網頁組件按一下箭頭，然後再按一下其功能表上的 [**編輯網頁組件**。搜尋結果網頁組件工具窗格隨即開啟 [功能區中頂端右上方的頁面。![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="74806-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="74806-181">在網頁組件] 工具窗格的 [**設定**] 區段的 [**結果控制設定**，請在選取**顯示多個地理位置結果**來取得搜尋結果網頁組件以顯示所有地理位置的結果。</span><span class="sxs-lookup"><span data-stu-id="74806-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="74806-182">按一下**[確定]**以儲存變更並關閉 [網頁組件工具窗格。</span><span class="sxs-lookup"><span data-stu-id="74806-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="74806-183">檢查您的變更搜尋結果網頁組件至主功能表的 [頁面] 索引標籤上按一下 [**存回**。</span><span class="sxs-lookup"><span data-stu-id="74806-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="74806-184">使用中頁面頂端的附註所提供的連結發佈所做的變更。</span><span class="sxs-lookup"><span data-stu-id="74806-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="74806-185">取得要顯示的所有或部分的地理位置結果的自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="74806-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="74806-p113">自訂搜尋應用程式與 SharePoint 搜尋 REST API 來要求指定查詢參數從所有或一些、 地理位置取得結果。根據的查詢參數，該查詢會扇形的所有地理位置，或某些地理位置。例如，如果您只需要查詢以尋找相關資訊的地理位置的子集，您可以控制延展至只有這些風扇。如果要求成功，SharePoint 搜尋 REST API 傳回回應資料。</span><span class="sxs-lookup"><span data-stu-id="74806-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="74806-190">查詢參數</span><span class="sxs-lookup"><span data-stu-id="74806-190">Query parameters</span></span>

<span data-ttu-id="74806-p114">EnableMultiGeoSearch-這是 Boolean 值，會指定是否查詢應扇形的其他地理位置的多個地理位置租用戶的索引。將它設為**true**可扇形查詢;**false**不扇形查詢。預設值為**false**。如果您未包含此參數，查詢是**不**扇形的其他地理位置。如果您不是多重地理位置環境中使用此參數，則會忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="74806-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="74806-p115">ClientType-這是一個字串。輸入每個搜尋應用程式的唯一用戶端名稱。如果您未包含此參數，查詢是**不**扇形的其他地理位置。</span><span class="sxs-lookup"><span data-stu-id="74806-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="74806-p116">MultiGeoSearchConfiguration-這是選用清單中的哪個地理位置中多個地理位置承租人查詢扇形至**EnableMultiGeoSearch**時**，則為 true**。如果您未加上此參數，或保留空白，查詢被扇形所有地理位置的。針對每個地理位置 JSON 格式來輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="74806-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="74806-202">項目</span><span class="sxs-lookup"><span data-stu-id="74806-202">Item</span></span></th>
<th align="left"><span data-ttu-id="74806-203">描述</span><span class="sxs-lookup"><span data-stu-id="74806-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="74806-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="74806-205">地理位置，例如名稱。</span><span class="sxs-lookup"><span data-stu-id="74806-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74806-206">端點</span><span class="sxs-lookup"><span data-stu-id="74806-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="74806-207">連線至，例如端點https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="74806-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="74806-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="74806-209">結果來源，例如 B81EAB55-3140-4312-B0F4-9459D1B4FFEE 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="74806-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="74806-p117">若您省略 DataLocation 或端點，或重複 DataLocation、 要求就會失敗。[您可以取得的使用 Microsoft Graph 租用戶地理位置端點的相關資訊](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery)。</span><span class="sxs-lookup"><span data-stu-id="74806-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="74806-212">回應資料</span><span class="sxs-lookup"><span data-stu-id="74806-212">Response data</span></span>

<span data-ttu-id="74806-p118">MultiGeoSearchStatus – 這是 「 SharePoint 搜尋 API 傳回以回應要求的屬性。屬性的值是一個字串並提供下列有關 SharePoint 搜尋 API 傳回結果的資訊：</span><span class="sxs-lookup"><span data-stu-id="74806-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="74806-215">值</span><span class="sxs-lookup"><span data-stu-id="74806-215">Value</span></span></th>
<th align="left"><span data-ttu-id="74806-216">描述</span><span class="sxs-lookup"><span data-stu-id="74806-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-217">完整</span><span class="sxs-lookup"><span data-stu-id="74806-217">Full</span></span></td>
<td align="left"><span data-ttu-id="74806-218">完整的<strong>所有</strong>結果的地理位置。</span><span class="sxs-lookup"><span data-stu-id="74806-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="74806-219">部分</span><span class="sxs-lookup"><span data-stu-id="74806-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="74806-p119">從一或多個地理位置的部分結果。結果就是暫時性錯誤導致未完成。</span><span class="sxs-lookup"><span data-stu-id="74806-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="74806-222">使用 REST 服務的查詢</span><span class="sxs-lookup"><span data-stu-id="74806-222">Query using the REST service</span></span>

<span data-ttu-id="74806-p120">與 GET 要求，您可以指定查詢參數的 URL。與 POST 要求，您可以傳遞查詢參數的內文中 JavaScript Object Notation (JSON) 格式。</span><span class="sxs-lookup"><span data-stu-id="74806-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="74806-225">要求標頭</span><span class="sxs-lookup"><span data-stu-id="74806-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="74806-226">名稱</span><span class="sxs-lookup"><span data-stu-id="74806-226">Name</span></span></th>
<th align="left"><span data-ttu-id="74806-227">值</span><span class="sxs-lookup"><span data-stu-id="74806-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="74806-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="74806-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="74806-229">應用程式/json ； odata = 詳細資訊</span><span class="sxs-lookup"><span data-stu-id="74806-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="74806-230">扇形**所有**地理位置的範例 GET 要求</span><span class="sxs-lookup"><span data-stu-id="74806-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="74806-231">https://\<租用戶\>/\_api/搜尋/query?querytext = 'sharepoint' 屬性 = 'EnableMultiGeoSearch:true' & ClientType =' 我\_用戶端\_識別碼 '</span><span class="sxs-lookup"><span data-stu-id="74806-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="74806-232">範例 GET 要求來扇形**一些**地理位置</span><span class="sxs-lookup"><span data-stu-id="74806-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="74806-233">https:// <tenant>/_api/search/query?querytext = '網站' & ClientType = 'my_client_id' 屬性 ='EnableMultiGeoSearch:true、 MultiGeoSearchConfiguration: [{DataLocation\:"名稱"\,端點\:"https\:contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"可以"\,端點\:"https\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="74806-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="74806-234">扇形**所有**地理位置的範例 POST 要求</span><span class="sxs-lookup"><span data-stu-id="74806-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="74806-235">扇形**一些**地理位置的範例 POST 要求</span><span class="sxs-lookup"><span data-stu-id="74806-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="74806-236">使用 CSOM 的查詢</span><span class="sxs-lookup"><span data-stu-id="74806-236">Query using CSOM</span></span>

<span data-ttu-id="74806-237">以下是對**所有**地理位置扇形範例 CSOM 查詢：</span><span class="sxs-lookup"><span data-stu-id="74806-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

