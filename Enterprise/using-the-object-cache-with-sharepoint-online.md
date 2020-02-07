---
title: 使用 SharePoint Online 的物件快取
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: 本文說明使用物件快取 SharePoint Server 2013 內部部署和 SharePoint Online 中的差異。
ms.openlocfilehash: 24d58b692667c897d2f25d41d4216a74382a5390
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841042"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="1257c-103">使用 SharePoint Online 的物件快取</span><span class="sxs-lookup"><span data-stu-id="1257c-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="1257c-104">本文說明使用物件快取 SharePoint Server 2013 內部部署和 SharePoint Online 中的差異。</span><span class="sxs-lookup"><span data-stu-id="1257c-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="1257c-105">沒有顯著的依賴物件快取中 SharePoint Online 部署的負面影響。</span><span class="sxs-lookup"><span data-stu-id="1257c-105">There is significant negative impact of relying on the object cache in SharePoint Online deployment.</span></span> <span data-ttu-id="1257c-106">在 SharePoint Online 中的物件快取上任何相依性可減少您] 頁面上的可靠性。</span><span class="sxs-lookup"><span data-stu-id="1257c-106">Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="1257c-107">如何在 SharePoint Online 和 SharePoint Server 2013 物件快取運作</span><span class="sxs-lookup"><span data-stu-id="1257c-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="1257c-108">主控的內部部署 SharePoint Server 2013 時，客戶可以主控物件快取的專用的前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="1257c-108">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache.</span></span> <span data-ttu-id="1257c-109">這表示快取專用於一位客戶，而且僅受限於多少記憶體可供使用且配置的物件快取。</span><span class="sxs-lookup"><span data-stu-id="1257c-109">This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache.</span></span> <span data-ttu-id="1257c-110">因為只有一個客戶提供內部部署案例中前端網頁伺服器通常會有重複提出要求同一個網站的使用者。</span><span class="sxs-lookup"><span data-stu-id="1257c-110">Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over.</span></span> <span data-ttu-id="1257c-111">這表示快取完整快速取得並保持完整的清單查詢結果和您的使用者要求以規則為基礎的 SharePoint 物件。</span><span class="sxs-lookup"><span data-stu-id="1257c-111">This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![顯示到內部部署前端網頁伺服器的流量和負載](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="1257c-113">因此，使用者造訪] 頁面上，第二次頁面載入時間可改善。</span><span class="sxs-lookup"><span data-stu-id="1257c-113">As a result, the second time a user visits a page, the page load time improves.</span></span> <span data-ttu-id="1257c-114">之後的四種負載相同頁面的最低限度下，是快取在所有前端網頁伺服器上的網頁。</span><span class="sxs-lookup"><span data-stu-id="1257c-114">After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="1257c-115">相反地，在 SharePoint Online 中有更多伺服器，但也很多的多個網站。</span><span class="sxs-lookup"><span data-stu-id="1257c-115">In contrast, in SharePoint Online there are many more servers but also many more sites.</span></span> <span data-ttu-id="1257c-116">每個使用者可能連接至沒有填入快取的其他前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="1257c-116">Each user may connect to a different front-end web server that doesn't have the cache populated.</span></span> <span data-ttu-id="1257c-117">或者，或許快取未填入伺服器，但的下一個使用者] 頁面上的該前端網頁伺服器要求從不同的站台。</span><span class="sxs-lookup"><span data-stu-id="1257c-117">Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site.</span></span> <span data-ttu-id="1257c-118">或者，即使下一個使用者在其上一個瀏覽上要求同一個頁面，其快取中沒有該頁面的不同的前端網頁伺服器負載平衡。</span><span class="sxs-lookup"><span data-stu-id="1257c-118">Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache.</span></span> <span data-ttu-id="1257c-119">在最後一個案例中，快取不會協助使用者在所有。</span><span class="sxs-lookup"><span data-stu-id="1257c-119">In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="1257c-120">在下圖中，每個點會代表] 頁面上的使用者要求該快取的位置。</span><span class="sxs-lookup"><span data-stu-id="1257c-120">In the following figure, each dot represents a page that a user is requesting and where it cached.</span></span> <span data-ttu-id="1257c-121">不同顏色表示不同的客戶共用用法的 SaaS 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="1257c-121">Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![顯示 SharePoint Online 中的物件快取結果](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="1257c-123">您可以看到從圖表，是輕型達到次具有其] 頁面上的快取版本的伺服器的任何特定使用者的機會。</span><span class="sxs-lookup"><span data-stu-id="1257c-123">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim.</span></span> <span data-ttu-id="1257c-124">此外，由於大型輸送量與伺服器會在多個網站之間共用的事實，快取不會姓氏 long 因為沒有可用的僅限說空間來快取。</span><span class="sxs-lookup"><span data-stu-id="1257c-124">Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="1257c-125">對於所有的這些原因，依賴使用者取得快取的物件不是有效的方法，以確保良好使用者經驗和頁面載入 SharePoint Online 中的時間。</span><span class="sxs-lookup"><span data-stu-id="1257c-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="1257c-126">如果我們無法依賴物件快取以改善 SharePoint Online 中的效能，我們該用什麼改為？</span><span class="sxs-lookup"><span data-stu-id="1257c-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="1257c-127">因為您不應該依賴 SharePoint Online 中快取，您應該評估使用物件快取的 SharePoint 自訂的替代設計方法。</span><span class="sxs-lookup"><span data-stu-id="1257c-127">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache.</span></span> <span data-ttu-id="1257c-128">這表示效能問題，請勿依賴物件快取才能產生良好結果提供給使用者的使用方式。</span><span class="sxs-lookup"><span data-stu-id="1257c-128">This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users.</span></span> <span data-ttu-id="1257c-129">這部分本系列中的其他文章所述，包括：</span><span class="sxs-lookup"><span data-stu-id="1257c-129">This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="1257c-130">SharePoint Online 的瀏覽選項</span><span class="sxs-lookup"><span data-stu-id="1257c-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="1257c-131">SharePoint Online 中的縮製和統合</span><span class="sxs-lookup"><span data-stu-id="1257c-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="1257c-132">使用內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="1257c-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="1257c-133">在 SharePoint Online 中延遲載入圖片與 JavaScript</span><span class="sxs-lookup"><span data-stu-id="1257c-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

