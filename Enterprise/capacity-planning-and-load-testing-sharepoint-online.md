---
title: 容量規劃和測試 SharePoint Online 的負載
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文說明如何部署至 SharePoint Online 而不執行傳統負載測試由於不允許使用。
ms.openlocfilehash: 06649942f20dc18abfcae0e56df7e3ea56ed9165
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540201"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="8d1b8-103">容量規劃和測試 SharePoint Online 的負載</span><span class="sxs-lookup"><span data-stu-id="8d1b8-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="8d1b8-104">本文說明如何部署至 SharePoint Online 而不執行傳統負載測試由於不允許使用。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is not permitted.</span></span>
  
<span data-ttu-id="8d1b8-105">雖然作用中的負載測試 SharePoint Online 上不鼓勵、 有其他方法可以確保的站台將不會產生不良的使用者經驗時啟動網站。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="8d1b8-p101">與 SharePoint Online 您不需要執行容量規劃，這是完成您我們服務可以的一部分。內部部署環境負載測試用來驗證規模假設並最終尋找伺服器陣列 ； 中斷點由飽和它負載。與 SharePoint Online 我們需要以不同方式執行的動作。我們正在多承租人環境，必須保護所有租用戶中相同的伺服器陣列，因此我們將會自動節流處理任何負載測試。這表示您會收到令人失望和可能誤導的結果如果您嘗試載入測試您的環境。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="8d1b8-p102">其中一個 SharePoint online 透過內部部署的主要好處是雲端的 elasticity。我們大型環境是設定服務數以百萬計的使用者每天以便很重要我們處理容量有效地以自動伺服器陣列時所需。本文說明我們如何規劃容量的成長和向外擴充備妥。本文也涵蓋方法讓您使用不包含負載測試。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="8d1b8-115">Office 365 的預測負載和展開容量</span><span class="sxs-lookup"><span data-stu-id="8d1b8-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="8d1b8-116">SharePoint Online 伺服器容量管理工作是透過兩種方法：</span><span class="sxs-lookup"><span data-stu-id="8d1b8-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="8d1b8-117">容量預測</span><span class="sxs-lookup"><span data-stu-id="8d1b8-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="8d1b8-118">在單一伺服器陣列上負載平衡</span><span class="sxs-lookup"><span data-stu-id="8d1b8-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="8d1b8-p103">不同於針對內部部署環境，在 SharePoint Online 中的容量來預測的規劃我們要能夠編譯統計資料和圖形在任何指定的伺服器] 群組中的潛在需求。彙總需求可能看起來類似的要求 （其中一個區域是 SharePoint 伺服器陣列群組） 的區域中下面的影像的成長一行：</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![顯示預測容量的圖表：預測](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="8d1b8-p104">雖然增長即無法預測任何一個伺服器陣列中的區域中的要求彙總的總和的可預測。藉由識別 SharePoint Online 的成長趨勢，我們可以規劃未來的擴充。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="8d1b8-p105">才能有效率地使用容量及處理未預期的成長、 中任何伺服器陣列中，我們有追蹤前端負載和比例調整備妥、 時所需的自動化。我們使用的訊號前端擴充結束的主要計量是 CPU 負載。我們的目標是保留尖峰 CPU 負載下 40%。這是為了有足夠的緩衝區吸收未預期的暴增。Load 方法 40%穩定狀態中，我們中新增前端伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![顯示預測容量的圖表：管理伺服器陣列](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="8d1b8-130">在其他伺服器可以快速地新增至伺服器陣列中使用這些先前新增到預測的使用狀況的區域。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="8d1b8-131">如何規劃針對網站啟動？</span><span class="sxs-lookup"><span data-stu-id="8d1b8-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="8d1b8-p106">您應可預期的伺服器陣列啟動新的網站自動要監控以便讓新增新的前端伺服器，如前文所述。此原因，我們不需要任何新的網站啟動的通知。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="8d1b8-134">接在 SharePoint Online 上的單一] 頁面上的其他最佳作法是可能性即使 100000 名使用者至新網站啟動會造成任何影響到伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="8d1b8-p107">有幾個版本的新的 SharePoint Online 網站規劃的策略。下圖所示，通常是大幅高於實際使用網站的受邀的使用者數量。此圖顯示如何導入版本的策略。此方法不只有助於效能載入但也可協助您識別之前大型大部分的使用者看到的改善 SharePoint 網站的方式。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![顯示受邀和作用中使用者的圖形](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="8d1b8-p108">在前導階段中，它是很好的使用者組織信任和知道要體驗會取得意見反應。如此一來有可能量測系統正在使用方式，以及執行的方式。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="8d1b8-p109">之後，一開始會聯播 （英文） 出波浪; 中的所有使用者取得意見反應及定期檢閱效能。這有緩慢簡介 （英文） 系統和系統取得更多使用如進行改良功能的優點。這也可讓我們為網站導更多與更多使用者負載增加回應。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="8d1b8-p110">最後時所禁止負載測試，, 客戶可能會想要設定期刊 ping 要測量可用性和延遲性服務中。這會識別針對其網站的基準。不過，這些必須保留至低頻率以避免節流先前所述的問題。</span><span class="sxs-lookup"><span data-stu-id="8d1b8-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

