---
title: 使用 SharePoint Online 的物件快取
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 本文說明使用 SharePoint Server 2013 內部部署和 SharePoint Online 中的物件快取的差異。
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 7cd210c44622ea2de5fb0e8e91c7be4839c80205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "24056162"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="6c439-103">使用 SharePoint Online 的物件快取</span><span class="sxs-lookup"><span data-stu-id="6c439-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="6c439-104">本文說明使用 SharePoint Server 2013 內部部署和 SharePoint Online 中的物件快取的差異。</span><span class="sxs-lookup"><span data-stu-id="6c439-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="6c439-p101">在 SharePoint Online 部署中依賴物件快取有明顯的負面影響。在 SharePoint Online 中依賴物件快取會降低頁面可靠性。</span><span class="sxs-lookup"><span data-stu-id="6c439-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="6c439-107">SharePoint Online 和 SharePoint Server 2013 物件快取運作</span><span class="sxs-lookup"><span data-stu-id="6c439-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="6c439-p102">託管在內部部署 SharePoint Server 2013 時，客戶可以主控物件快取的專用的前端網頁伺服器。這表示快取專用於一位客戶及僅限於多少記憶體功能並配置給物件快取。因為只有一個客戶提供服務的內部部署案例中的前端網頁伺服器通常必須一再同一個網站發出要求的使用者。這表示快取完整快速取得並維持完整清單查詢結果與您的使用者要求規則為基礎的 SharePoint 物件。</span><span class="sxs-lookup"><span data-stu-id="6c439-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![顯示到內部部署前端網頁伺服器的流量和負載](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="6c439-p103">因此，使用者第二次造訪頁面時，其載入時間會獲得改善。相同網頁至少載入四次後，所有前端 Web 伺服器皆會快取到該頁面。</span><span class="sxs-lookup"><span data-stu-id="6c439-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="6c439-p104">相較之下，SharePoint Online 中有許多更多的伺服器，但也許多的多個網站。每位使用者可能連接至其他前端網頁伺服器以沒有填入的快取。或或許快取沒有取得填入伺服器，但該前端網頁伺服器至下一個使用者要求] 頁面上從不同的網站。或者，即使下一個使用者要求相同頁面在其上一個造訪上，其會以其快取中沒有該頁面的其他前端網頁伺服器負載平衡。在最後一個案例中，快取不會協助使用者在所有。</span><span class="sxs-lookup"><span data-stu-id="6c439-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="6c439-p105">在下圖中，每個點代表使用者正在要求的頁面及其快取位置。不同顏色代表共用 SaaS 基礎結構的不同客戶。</span><span class="sxs-lookup"><span data-stu-id="6c439-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![顯示 SharePoint Online 中的物件快取結果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="6c439-p106">如您從圖表，方式與使用者的頁面的快取版本的伺服器來點擊任何指定使用者的機會所見輕型。此外，因為大型輸送量與伺服器會在許多網站之間共用的事實、 快取不會姓氏長自有可用的僅是過多空間的快取。</span><span class="sxs-lookup"><span data-stu-id="6c439-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="6c439-125">基於上述所有原因，依賴使用者取得快取物件並不是確保在 SharePoint Online 中提供良好使用者經驗和頁面載入時間的有效方法。</span><span class="sxs-lookup"><span data-stu-id="6c439-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="6c439-126">如果我們無法依賴物件快取來提升 SharePoint Online 中的效能，我們該用什麼來代替？</span><span class="sxs-lookup"><span data-stu-id="6c439-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="6c439-p107">由於不應在 SharePoint Online 中依賴快取，因此您應該評估使用物件快取的 SharePoint 自訂的替代設計方法。這表示要使用不依賴物件快取的效能問題解決方法來讓使用者獲得良好結果。這方面的說明請參閱此系列文章的其他幾篇，包括：</span><span class="sxs-lookup"><span data-stu-id="6c439-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="6c439-130">SharePoint Online 的導覽選項</span><span class="sxs-lookup"><span data-stu-id="6c439-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="6c439-131">SharePoint Online 中的縮製及統合技術</span><span class="sxs-lookup"><span data-stu-id="6c439-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="6c439-132">使用內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="6c439-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="6c439-133">延遲載入 SharePoint Online 中的影像和 JavaScript</span><span class="sxs-lookup"><span data-stu-id="6c439-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

