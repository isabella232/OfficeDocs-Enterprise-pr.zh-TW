---
title: 設定商務用 OneDrive 多地理位置的搜尋
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 深入了解如何設定多地理位置環境中的搜尋。
ms.openlocfilehash: c56e7d310dd6ece53fdea36df4ad94e2ebbc64cb
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "26705457"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="29b97-103">設定商務用 OneDrive 多地理位置的搜尋</span><span class="sxs-lookup"><span data-stu-id="29b97-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="29b97-104">在商務用 OneDrive 多地理位置環境中，組織可以有一個 Office 365 租用戶，但將其 OneDrive 內容儲存在多個地理位置 (一個中央位置與一或多個衛星位置) 中。</span><span class="sxs-lookup"><span data-stu-id="29b97-104">In a OneDrive for Business Multi-Geo environment, an organization can have one Office 365 tenant, but store their OneDrive content in multiple geographical locations - one central location and one or more satellite locations.</span></span>

<span data-ttu-id="29b97-p101">每個地理位置有其專屬的搜尋索引和搜尋中心。當使用者搜尋時，系統會將查詢展開傳送到所有索引，並合併傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-p101">Each geo location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="29b97-p102">例如，單一地理位置中的使用者可以搜尋儲存在其他地理位置的內容，或限制為不同地理位置之 SharePoint 網站上的內容。如果使用者可存取此內容，搜尋會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="29b97-109">哪些搜尋用戶端可以在多地理位置中運作？</span><span class="sxs-lookup"><span data-stu-id="29b97-109">Which search clients work in a multi-geo environment?</span></span>

<span data-ttu-id="29b97-110">這些用戶端可以從所有地理位置傳回結果：</span><span class="sxs-lookup"><span data-stu-id="29b97-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="29b97-111">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="29b97-111">OneDrive for Business</span></span>

-   <span data-ttu-id="29b97-112">Delve</span><span class="sxs-lookup"><span data-stu-id="29b97-112">Delve</span></span>

-   <span data-ttu-id="29b97-113">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="29b97-113">The SharePoint home page</span></span>

-   <span data-ttu-id="29b97-114">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="29b97-114">The Search Center</span></span>

-   <span data-ttu-id="29b97-115">使用 SharePoint 搜尋 API 的自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="29b97-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="29b97-116">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="29b97-116">OneDrive for Business</span></span>

<span data-ttu-id="29b97-117">多地理位置環境一設定好之後，在 OneDrive 中搜尋的使用者就會取得來自所有地理位置的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-117">As soon as the multi-geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="29b97-118">Delve</span><span class="sxs-lookup"><span data-stu-id="29b97-118">Delve</span></span>

<span data-ttu-id="29b97-119">多地理位置環境一設定好之後，在 Delve 中搜尋的使用者就會取得來自所有地理位置的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-119">As soon as the multi-geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="29b97-p103">Delve 摘要和設定檔卡只會顯示在**中央**位置中儲存之檔案的預覽。針對儲存在衛星地理位置的檔案，則會改為顯示檔案類型的圖示。</span><span class="sxs-lookup"><span data-stu-id="29b97-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="29b97-122">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="29b97-122">The SharePoint home page</span></span>

<span data-ttu-id="29b97-p104">多地理位置環境一設定好，使用者就會在 SharePoint 首頁上看到來自多個地理位置的最新消息、最新動向及追蹤網站。如果他們使用 SharePoint 首頁上的 [搜尋] 方塊，他們會收到來自多個地理位置合併的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-p104">As soon as the multi-geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="29b97-125">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="29b97-125">The Search Center</span></span>

<span data-ttu-id="29b97-p105">在多地理位置環境設定好之後，每個搜尋中心都會繼續只顯示來自本身地理位置的結果。系統管理員必須[變更每個搜尋中心的設定](#_Set_up_a_1)，以取得來自所有地理位置的結果。之後，在搜尋中心中搜尋的使用者會取得來自所有地理位置的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-p105">After the multi-geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="29b97-129">自訂搜尋應用程式</span><span class="sxs-lookup"><span data-stu-id="29b97-129">Custom search applications</span></span>

<span data-ttu-id="29b97-p106">按慣例，自訂搜尋應用程式會使用現有的 SharePoint 搜尋 REST API 與搜尋索引互動。若要取得來自全部或部分地理位置的結果，應用程式必須在要求中[呼叫 API，並包含新多地理位置查詢參數](#_Get_custom_search)。這會觸發將查詢展開傳送至所有地理位置。</span><span class="sxs-lookup"><span data-stu-id="29b97-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="29b97-133">在多地理位置環境中搜尋的差異為何？</span><span class="sxs-lookup"><span data-stu-id="29b97-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="29b97-134">您可能已經熟悉的部分搜尋功能在多地理位置環境中的運作方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="29b97-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="29b97-135"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="29b97-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="29b97-136"><strong>它如何運作？</strong></span><span class="sxs-lookup"><span data-stu-id="29b97-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="29b97-137"><strong>因應措施</strong></span><span class="sxs-lookup"><span data-stu-id="29b97-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-138">升階的結果</span><span class="sxs-lookup"><span data-stu-id="29b97-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="29b97-p107">您可以在不同層級建立含升階結果的查詢規則：針對整個租用戶、網站集合或網站。在多地理位置環境中，如果您想要將結果升級至<strong>所有</strong>地理位置中的搜尋中心，請在<strong>租用戶</strong>層級定義升階結果。如果您<strong>只</strong>想要升級搜尋中心內的結果，該結果就位於網站集合或網站的地理位置中，請以<strong>網站集合</strong>或<strong>網站</strong>層級定義結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a multi-geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="29b97-142">如果您不需要每個地理位置的其他升階結果 (例如出差的不同規則)，我們建議您在租用戶層級定義升階結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="29b97-143">搜尋精簡器</span><span class="sxs-lookup"><span data-stu-id="29b97-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="29b97-p108">搜尋會傳回來自某租用戶所有地理位置的精簡器，然後會對它們進行彙總。彙總是最大努力的結果，這表示精簡器計數可能不是 100% 正確的。在大部分以搜尋為導向的情況下，此精確度就已足夠。 </span><span class="sxs-lookup"><span data-stu-id="29b97-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="29b97-147">針對依賴精簡器完整性且以搜尋為導向的應用程式，查詢每個地理位置都是獨立的，而不需使用多地理位置展開傳送。</span><span class="sxs-lookup"><span data-stu-id="29b97-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using multi-geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="29b97-148">多地理位置搜尋不支援數字精簡器的動態貯體。</span><span class="sxs-lookup"><span data-stu-id="29b97-148">Multi-geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="29b97-149">將<a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">「分隔」參數</a>用於數字精簡器。</span><span class="sxs-lookup"><span data-stu-id="29b97-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="29b97-150">文件識別碼</span><span class="sxs-lookup"><span data-stu-id="29b97-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="29b97-151">如果您要開發依賴文件識別碼且以搜尋為導向的應用程式，請注意，在多地理位置環境中的文件識別碼在跨地理位置間不是唯一的，每個地理位置的文件識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="29b97-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a multi-geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="29b97-p109">我們新增了可識別地理位置的欄。使用此欄來達到唯一性。此欄名為 “GeoLocationSource”。</span><span class="sxs-lookup"><span data-stu-id="29b97-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-155">結果數目</span><span class="sxs-lookup"><span data-stu-id="29b97-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="29b97-156">搜尋結果頁面會顯示來自地理位置的合併結果，但頁面無法顯示超過 500 個結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="29b97-157">多地理位置環境中的搜尋不支援哪些項目？</span><span class="sxs-lookup"><span data-stu-id="29b97-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="29b97-158">您可能已經熟悉的部分搜尋功能在多地理位置環境中不受支援。</span><span class="sxs-lookup"><span data-stu-id="29b97-158">Some of the search features you might be familiar with, aren’t supported in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="29b97-159"><strong>搜尋功能</strong></span><span class="sxs-lookup"><span data-stu-id="29b97-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="29b97-160"><strong>附註</strong></span><span class="sxs-lookup"><span data-stu-id="29b97-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-161">僅 App 驗證</span><span class="sxs-lookup"><span data-stu-id="29b97-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="29b97-162">在多地理位置搜尋中不支援僅 App 驗證 (來自服務的特殊權限存取)。</span><span class="sxs-lookup"><span data-stu-id="29b97-162">App-only authentication (privileged access from services) isn’t supported in multi-geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="29b97-163">來賓使用者</span><span class="sxs-lookup"><span data-stu-id="29b97-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="29b97-164">來賓使用者只能取得他們在其中搜尋之地理位置的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="29b97-165">搜尋在多地理位置環境中的運作方式？</span><span class="sxs-lookup"><span data-stu-id="29b97-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="29b97-166">**所有**搜尋用戶端都會使用現有 SharePoint 搜尋 REST API 與搜尋索引互動。</span><span class="sxs-lookup"><span data-stu-id="29b97-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="29b97-167">搜尋用戶端會使用查詢屬性 EnableMultiGeoSearch = true 來呼叫搜尋 REST 端點。</span><span class="sxs-lookup"><span data-stu-id="29b97-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="29b97-168">系統會將查詢傳送至租用戶中的所有地理位置中。</span><span class="sxs-lookup"><span data-stu-id="29b97-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="29b97-169">來自每個地理位置的搜尋結果會合併並排名。</span><span class="sxs-lookup"><span data-stu-id="29b97-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="29b97-170">用戶端會取得整合的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-170">The client gets unified search results.</span></span>



<span data-ttu-id="29b97-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>請注意，直到收到來自所有地理位置的結果前，我們不會合併搜尋結果。這表示多地理位置會有額外的延遲 (與在僅含單一地理位置之環境中的搜尋相比)。</span><span class="sxs-lookup"><span data-stu-id="29b97-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="29b97-173">取得搜尋中心以顯示來自所有地理位置的結果</span><span class="sxs-lookup"><span data-stu-id="29b97-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="29b97-174">每個搜尋中心都提供數種類別，而且您必須個別設定每個類別。</span><span class="sxs-lookup"><span data-stu-id="29b97-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="29b97-175">請務必使用有權編輯搜尋結果網頁與搜尋結果網頁組件的帳戶來執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="29b97-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="29b97-176">瀏覽至 [搜尋結果] 頁面 (請參閱搜尋結果頁面的[清單](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213))</span><span class="sxs-lookup"><span data-stu-id="29b97-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="29b97-p111">選取要設定的類別，請按一下右上角的 [設定]\*\*\*\* 圖示，然後按一下 [編輯頁面] \*\*\*\*。在編輯模式中搜尋結果網頁會開啟。</span><span class="sxs-lookup"><span data-stu-id="29b97-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="29b97-p112">在搜尋結果網頁組件中，請將指標移至右上角的 [網頁組件]，按一下箭號，然後按一下功能表上的 [編輯網頁組件]\*\*\*\* 。搜尋結果網頁組件工具窗格隨即在頁面左上方的功能區中開啟。![](media/configure-search-for-multi-geo-image3.png)</span><span class="sxs-lookup"><span data-stu-id="29b97-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo-image3.png)</span></span>

1.  <span data-ttu-id="29b97-181">在網頁組件工具窗格 [設定]\*\*\*\* 區段中，在 [結果控制設定]\*\*\*\*，請選取 [顯示多地理位置結果]\*\*\*\* 以取得搜尋結果網頁組件，以顯示來自所有地理位置的結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="29b97-182">按一下 [確定]\*\*\*\* 以儲存變更並且關閉網頁組件工具窗格。</span><span class="sxs-lookup"><span data-stu-id="29b97-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="29b97-183">檢查您對搜尋結果網頁組件所做的變更，請在主功能表的 [頁面] 索引標籤上按一下 [存回]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29b97-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="29b97-184">使用頁面頂端之附註中提供的連結發佈變更。</span><span class="sxs-lookup"><span data-stu-id="29b97-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="29b97-185">取得自訂搜尋應用程式，以顯示來自全部或部分地理位置的結果</span><span class="sxs-lookup"><span data-stu-id="29b97-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="29b97-p113">自訂搜尋應用程式會透過指定含對 SharePoint 搜尋 REST API 之要求的查詢參數，以取得來自全部或部分地理位置的結果。視查詢參數而定，系統會將查詢展開傳送至所有地理位置或部分的地理位置。例如，如果您只需要查詢地理位置的子集來尋找相關資訊，您可以控制只對這些項目進行展開傳送。如果要求成功，SharePoint 搜尋 REST API 會傳回回應資料。</span><span class="sxs-lookup"><span data-stu-id="29b97-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

#### <a name="requirement"></a><span data-ttu-id="29b97-190">需求</span><span class="sxs-lookup"><span data-stu-id="29b97-190">Requirement</span></span> #### 
<span data-ttu-id="29b97-p114">對於每個地理位置，您必須確保組織中的所有使用者都已被授予根網站的**讀取**權限層級 (例如contoso**APAC**.sharepoint.com/ 和 contoso**EU**.sharepoint.com/)。[了解權限](https://support.office.com/zh-TW/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848)。</span><span class="sxs-lookup"><span data-stu-id="29b97-p114">For each geo location, you must ensure that all users in the organization have been granted the **Read** permission level for the root website (for example contoso**APAC**.sharepoint.com/ and contoso**EU**.sharepoint.com/). [Learn about permissions](https://support.office.com/zh-TW/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).</span></span>

### <a name="query-parameters"></a><span data-ttu-id="29b97-193">查詢參數</span><span class="sxs-lookup"><span data-stu-id="29b97-193">Query parameters</span></span>

<span data-ttu-id="29b97-p115">EnableMultiGeoSearch - 這是布林值，它會指出是否應該將查詢展開傳送至多地理位置租用戶的其他地理位置之索引。將它設定為 **true** 以展開傳送查詢；設定為 **false** 則不展開傳送查詢。預設值是 **false**。如果您不包含此參數，系統**不**會將查詢展開傳送至其他地理位置。如果您在非多地理位置環境中使用該參數，則該參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="29b97-p115">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="29b97-p116">ClientType - 這是一個字串。輸入每個搜尋應用程式的唯一用戶端名稱。如果您不包含此參數，則系統**不**會將查詢展開傳送至其他地理位置。</span><span class="sxs-lookup"><span data-stu-id="29b97-p116">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="29b97-p117">MultiGeoSearchConfiguration - 這是在 **EnableMultiGeoSearch** 為 **true** 時，要將查詢展開傳送至多地理位置租用戶中哪些地理位置的選用清單。如果您不包含此參數，或將它留白，則系統會將查詢展開傳送至所有地理位置。針對每個地理位置，請以 JSON 格式輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="29b97-p117">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the multi-geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="29b97-205">項目</span><span class="sxs-lookup"><span data-stu-id="29b97-205">Item</span></span></th>
<th align="left"><span data-ttu-id="29b97-206">描述</span><span class="sxs-lookup"><span data-stu-id="29b97-206">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-207">DataLocation</span><span class="sxs-lookup"><span data-stu-id="29b97-207">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="29b97-208">地理位置，例如NAM。</span><span class="sxs-lookup"><span data-stu-id="29b97-208">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="29b97-209">端點</span><span class="sxs-lookup"><span data-stu-id="29b97-209">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="29b97-210">要連線的端點，例如 https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="29b97-210">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-211">SourceId</span><span class="sxs-lookup"><span data-stu-id="29b97-211">SourceId</span></span></td>
<td align="left"><span data-ttu-id="29b97-212">結果來源的 GUID，例如 B81EAB55-3140-4312-B0F4-9459D1B4FFEE。</span><span class="sxs-lookup"><span data-stu-id="29b97-212">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="29b97-p118">如果您省略 DataLocation 或EndPoint，或者 DataLocation 是重複的，要求將會失敗。[您可以透過 Microsoft Graph 來取得租用戶地理位置的端點相關資訊](https://docs.microsoft.com/zh-TW/sharepoint/dev/solution-guidance/multigeo-discovery)。</span><span class="sxs-lookup"><span data-stu-id="29b97-p118">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/zh-TW/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="29b97-215">回應資料</span><span class="sxs-lookup"><span data-stu-id="29b97-215">Response data</span></span>

<span data-ttu-id="29b97-p119">MultiGeoSearchStatus – 這是 SharePoint 搜尋 API 在回應中傳回至要求的屬性。屬性的值是字串，並提供 SharePoint 搜尋 API 傳回之結果的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="29b97-p119">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="29b97-218">值</span><span class="sxs-lookup"><span data-stu-id="29b97-218">Value</span></span></th>
<th align="left"><span data-ttu-id="29b97-219">描述</span><span class="sxs-lookup"><span data-stu-id="29b97-219">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-220">Full</span><span class="sxs-lookup"><span data-stu-id="29b97-220">Full</span></span></td>
<td align="left"><span data-ttu-id="29b97-221">來自<strong>所有</strong>地理位置的完整結果。</span><span class="sxs-lookup"><span data-stu-id="29b97-221">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="29b97-222">Partial</span><span class="sxs-lookup"><span data-stu-id="29b97-222">Partial</span></span></td>
<td align="left"><span data-ttu-id="29b97-p120">從一或多個地理位置的部分結果。結果會因為暫時性錯誤而不完整。</span><span class="sxs-lookup"><span data-stu-id="29b97-p120">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="29b97-225">使用 REST 服務的查詢</span><span class="sxs-lookup"><span data-stu-id="29b97-225">Query using the REST service</span></span>

<span data-ttu-id="29b97-p121">使用 GET 要求時，您可以在 URL 中指定查詢參數。使用 POST 要求時，您能以 JavaScript 物件標記法 (JSON) 格式在內文中傳遞查詢參數。</span><span class="sxs-lookup"><span data-stu-id="29b97-p121">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="29b97-228">要求標頭</span><span class="sxs-lookup"><span data-stu-id="29b97-228">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="29b97-229">名稱</span><span class="sxs-lookup"><span data-stu-id="29b97-229">Name</span></span></th>
<th align="left"><span data-ttu-id="29b97-230">值</span><span class="sxs-lookup"><span data-stu-id="29b97-230">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="29b97-231">Content-Type</span><span class="sxs-lookup"><span data-stu-id="29b97-231">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="29b97-232">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="29b97-232">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="29b97-233">已展開傳送至**所有**地理位置的範例 GET 要求</span><span class="sxs-lookup"><span data-stu-id="29b97-233">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="29b97-234">https://\<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="29b97-234">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="29b97-235">要展開傳送至**部分**地理位置的範例 GET 要求</span><span class="sxs-lookup"><span data-stu-id="29b97-235">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="29b97-236">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="29b97-236">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="29b97-p122">MultiGeoSearchConfiguration 屬性的地理位置清單中的逗號和冒號前面會加上**反斜線**字元。這是因為 GET 要求使用冒號來分隔屬性，並使用逗號來分隔屬性的引數。若未使用反斜線做為逸出字元，就會發生 MultiGeoSearchConfiguration 屬性解讀錯誤的問題。</span><span class="sxs-lookup"><span data-stu-id="29b97-p122">Commas and colons in the list of geo-locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="29b97-240">已展開傳送至**所有**地理位置的範例 POST 要求</span><span class="sxs-lookup"><span data-stu-id="29b97-240">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="29b97-241">已展開傳送至**部分**地理位置的範例 POST 要求</span><span class="sxs-lookup"><span data-stu-id="29b97-241">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="29b97-242">使用 CSOM 的查詢</span><span class="sxs-lookup"><span data-stu-id="29b97-242">Query using CSOM</span></span>

<span data-ttu-id="29b97-243">此為已展開傳送至**所有**地理位置的範例 POST 要求：</span><span class="sxs-lookup"><span data-stu-id="29b97-243">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

