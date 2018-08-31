---
title: 使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online
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
description: 本文說明如何在 SharePoint Server 2013 和 SharePoint Online 內容搜尋網頁組件以取代 「 內容查詢網頁組件以提升效能。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540247"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="7aeb6-103">使用，而不內容查詢網頁組件的內容搜尋網頁組件來增進效能的 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7aeb6-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="7aeb6-104">本文說明如何在 SharePoint Server 2013 和 SharePoint Online 內容搜尋網頁組件以取代 「 內容查詢網頁組件以提升效能。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="7aeb6-p101">其中一個最強大的新功能的 SharePoint Server 2013 和 SharePoint Online 是內容搜尋網頁組件 (CSWP)。此網頁組件會使用搜尋索引快速地擷取會向使用者顯示的結果。用於內容搜尋網頁組件，而不是內容查詢網頁組件 (CQWP) 頁面中的使用者提升效能。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="7aeb6-p102">透過 「 內容查詢網頁組件中使用 「 內容搜尋網頁組件幾乎一定會產生大幅改善 SharePoint Online 上的頁面負載效能。有一點的其他設定即可使用取得正確的查詢，但獎賞改善的效能而且滿足使用者。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="7aeb6-110">比較您取得無法使用內容搜尋網頁組件而不內容查詢網頁組件的效能提升</span><span class="sxs-lookup"><span data-stu-id="7aeb6-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="7aeb6-p103">下列範例顯示當您使用 「 內容搜尋網頁組件而不是 「 內容查詢網頁組件可能會收到相對的效能提升。效果會更明顯與複雜的網站結構和非常廣泛的內容查詢。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="7aeb6-113">此範例網站都具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="7aeb6-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="7aeb6-114">8 的層級的子網站。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="7aeb6-115">列出使用自訂"水果 」 內容類型。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="7aeb6-116">在 [網頁組件中的內容查詢是廣泛，傳回所有的項目與"水果 」 內容類型。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="7aeb6-p104">範例只會使用 8 網站之間的 50 項目。效果會為更為明顯的網站具有多個內容之用。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="7aeb6-119">以下是內容查詢網頁組件的結果的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![顯示網頁組件內容查詢的圖形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="7aeb6-p105">在 Internet Explorer 中，使用 F12 開發人員工具的 [**網路**] 索引標籤來查看回應標頭的詳細資料。下列螢幕擷取畫面中，載入此頁面**SPRequestDuration**的值會是 924 （毫秒）。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![顯示 924 要求期間的螢幕擷取畫面](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="7aeb6-p106">**SPRequestDuration**表示要準備] 頁面上的伺服器上的已完成的工作數量。切換內容搜尋網頁組件的內容查詢網頁組件可大幅減少轉譯頁面所花費的時間。相較之下，對等的內容搜尋網頁組件] 頁面上，傳回相同的結果數具有 106 （毫秒） 此螢幕擷取畫面所示的**SPRequestDuration**值：</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![顯示 106 要求期間的螢幕擷取畫面](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="7aeb6-128">新增內容搜尋網頁組件在 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7aeb6-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="7aeb6-p107">新增內容搜尋網頁組件是非常類似於在規則的內容查詢網頁組件。請參閱] 區段中[設定內容搜尋網頁組件在 SharePoint 中](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)的 *「 新增內容搜尋網頁組件 」* 。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="7aeb6-131">建立正確的搜尋查詢的內容搜尋網頁組件</span><span class="sxs-lookup"><span data-stu-id="7aeb6-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="7aeb6-p108">一旦您已經新增內容搜尋網頁組件，您可精簡搜尋及傳回您想要的項目。如需如何執行這項作業的詳細指示，請參閱] 區段中，[設定內容搜尋網頁組件在 SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *「 設定內容搜尋網頁組件的進階的查詢顯示內容 」* 。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="7aeb6-134">查詢建立及測試工具</span><span class="sxs-lookup"><span data-stu-id="7aeb6-134">Query building and testing tool</span></span>

<span data-ttu-id="7aeb6-135">建立及測試複雜查詢工具，請參閱 Codeplex 上的[搜尋查詢工具](https://sp2013searchtool.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="7aeb6-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

