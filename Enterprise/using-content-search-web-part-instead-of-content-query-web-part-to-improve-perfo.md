---
title: 使用內容搜尋網頁組件而不內容查詢網頁組件，來改善 SharePoint Online 中的效能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 本文說明如何取代內容搜尋網頁組件，SharePoint Server 2013 和 SharePoint Online 中的 「 內容查詢網頁組件以提升效能。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492158"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="ee6e8-103">使用內容搜尋網頁組件而不內容查詢網頁組件，來改善 SharePoint Online 中的效能</span><span class="sxs-lookup"><span data-stu-id="ee6e8-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="ee6e8-104">本文說明如何取代內容搜尋網頁組件，SharePoint Server 2013 和 SharePoint Online 中的 「 內容查詢網頁組件以提升效能。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="ee6e8-105">SharePoint Server 2013 和 SharePoint Online 的最強大的新功能之一是內容搜尋網頁組件 (CSWP)。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="ee6e8-106">此網頁組件會使用搜尋索引來快速地擷取向使用者顯示的結果。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="ee6e8-107">用於內容搜尋網頁組件而不是內容查詢網頁組件 (CQWP) 頁面中的使用者提升效能。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="ee6e8-108">透過 「 內容查詢網頁組件使用內容搜尋網頁組件會幾乎總是導致 SharePoint Online 上的大幅改善頁面載入效能。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="ee6e8-109">沒有少許額外的設定，以取得正確的查詢，卻報酬改善的效能和滿足使用者。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="ee6e8-110">比較，就無法使用內容搜尋網頁組件，而不內容查詢網頁組件的效能提升</span><span class="sxs-lookup"><span data-stu-id="ee6e8-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="ee6e8-111">下列範例顯示當您使用內容搜尋網頁組件而不是 「 內容查詢網頁組件時，您可能會收到相對的效能提升。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="ee6e8-112">效果會更明顯的複雜網站結構與非常廣泛的內容查詢。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="ee6e8-113">此範例網站具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="ee6e8-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="ee6e8-114">8 層級的子網站。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="ee6e8-115">列出使用自訂 「 水果 」 內容類型。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="ee6e8-116">在 [網頁組件內容查詢是廣泛，傳回與 「 水果 」 內容類型的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="ee6e8-117">此範例只會使用 50 項目 8 網站之間。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="ee6e8-118">效果，將會更為明顯的網站具有更多的內容之用。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="ee6e8-119">以下是 「 內容查詢網頁組件的結果的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![顯示網頁組件內容查詢的圖形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="ee6e8-121">在 Internet Explorer 中，使用 F12 開發人員工具的 [**網路**] 索引標籤，查看回應標頭的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="ee6e8-122">下列螢幕擷取畫面中，載入此頁面**SPRequestDuration**的值會是 924 毫秒。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![顯示 924 要求期間的螢幕擷取畫面](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="ee6e8-124">**SPRequestDuration**指出準備網頁伺服器上完成的工作數量。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="ee6e8-125">切換使用內容搜尋網頁組件內容查詢網頁組件可大幅減少轉譯] 頁面上所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="ee6e8-126">相較之下，對等的內容搜尋網頁組件] 頁面上，傳回相同的結果數目具有**SPRequestDuration**值的 106 毫秒這個螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="ee6e8-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![顯示 106 要求期間的螢幕擷取畫面](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="ee6e8-128">新增內容搜尋網頁組件中 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ee6e8-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="ee6e8-129">新增內容搜尋網頁組件是非常類似於一般的內容查詢網頁組件。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="ee6e8-130">請參閱[設定內容搜尋網頁組件 SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *「 新增內容搜尋網頁組件 」* 一節。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="ee6e8-131">建立正確的搜尋查詢的內容搜尋網頁組件</span><span class="sxs-lookup"><span data-stu-id="ee6e8-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="ee6e8-132">一旦您已新增內容搜尋網頁組件，您可以縮小搜尋範圍，並傳回您想要的項目。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="ee6e8-133">如需如何執行這項操作的詳細指示，請參閱 <] 區段中，<b1>設定在 SharePoint 中的內容搜尋網頁組件</b1>中的<b0>「 藉由設定內容搜尋網頁組件中的進階的查詢顯示內容 」</b0> 。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="ee6e8-134">查詢建置和測試工具</span><span class="sxs-lookup"><span data-stu-id="ee6e8-134">Query building and testing tool</span></span>

<span data-ttu-id="ee6e8-135">一套工具來建置和測試複雜的查詢，請參閱 Codeplex 上的[搜尋查詢工具](https://sp2013searchtool.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="ee6e8-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

