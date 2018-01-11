---
title: "設計 Microsoft Azure PaaS 的網路"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "摘要： 了解如何最佳化您的網路存取 Microsoft Azure PaaS。"
ms.openlocfilehash: 8ea344b5c18f9224b1a939a05c6e5a4eda2eeec5
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="3e1e5-103">設計 Microsoft Azure PaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="3e1e5-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="3e1e5-104">**摘要：**了解如何最佳化您的網路存取 Microsoft Azure PaaS。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="3e1e5-105">若要針對 Azure PaaS 應用程式最佳化網路，必須具備充足的網際網路頻寬，且可能需要跨多個站台或應用程式分散網路流量。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="3e1e5-106">規劃步驟裝載在 Azure 中的組織 PaaS 應用程式</span><span class="sxs-lookup"><span data-stu-id="3e1e5-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="3e1e5-107">在此處插入區段主體。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="3e1e5-108">經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="3e1e5-109">最佳化您的網際網路頻寬使用中[設計的 Microsoft saas 和網路](designing-networking-for-microsoft-saas.md)的**步驟來準備您的網路 Microsoft saas 和服務的**一節的步驟 2 到 4。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-109">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="3e1e5-110">決定您是否需要 Azure ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="3e1e5-111">針對 web 式工作量，決定您是否需要 Azure Application Gateway。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="3e1e5-112">針對散佈至不同的資料中心中的不同端點流量，決定您是否需要 Azure 流量管理員。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="3e1e5-113">組織 PaaS 應用程式的網際網路頻寬</span><span class="sxs-lookup"><span data-stu-id="3e1e5-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="3e1e5-p101">架設在 Azure PaaS 的組織應用程式的內部網路的使用者需要的網際網路頻寬。有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="3e1e5-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="3e1e5-p102">**選項 1:**使用您現有的管道、 最佳化處理尖峰負載的容量與網際網路流量。請參閱[設計的 Microsoft saas 和網路](designing-networking-for-microsoft-saas.md)網際網路 edge、 用戶端使用狀況和 IT 作業考量。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="3e1e5-118">**選項 2：**高頻寬或低延遲需求使用 Azure ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="3e1e5-119">**圖 1： 連接 Azure PaaS 服務的連線選項**</span><span class="sxs-lookup"><span data-stu-id="3e1e5-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![圖 1：Azure PaaS 服務的連線選項](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="3e1e5-121">圖 1 顯示透過網際網路管道或 ExpressRoute Azure PaaS 服務連線至內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="3e1e5-122">Azure Application Gateway</span><span class="sxs-lookup"><span data-stu-id="3e1e5-122">Azure Application Gateway</span></span>

<span data-ttu-id="3e1e5-123">應用程式層級路由和負載平衡的服務，可讓您建立可擴充及高度可用的 web 前端 Azure 中的 web 應用程式、 雲端服務與虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="3e1e5-124">**圖 2： Azure Application Gateway**</span><span class="sxs-lookup"><span data-stu-id="3e1e5-124">**Figure 2: Azure Application Gateway**</span></span>

![圖 2：Azure 應用程式閘道服務](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="3e1e5-126">圖 2 顯示 Azure Application Gateway 以及使用者要求來自網際網路的方式可以轉接至 Azure 的 web 應用程式、 雲端服務或虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="3e1e5-127">Application Gateway 目前支援階層 7 應用程式傳遞下列：</span><span class="sxs-lookup"><span data-stu-id="3e1e5-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="3e1e5-128">HTTP 負載平衡</span><span class="sxs-lookup"><span data-stu-id="3e1e5-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="3e1e5-129">Cookie 為主的工作階段親和性</span><span class="sxs-lookup"><span data-stu-id="3e1e5-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="3e1e5-130">SSL 卸載</span><span class="sxs-lookup"><span data-stu-id="3e1e5-130">SSL offload</span></span>
    
<span data-ttu-id="3e1e5-131">如需詳細資訊，請參閱[Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-131">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="3e1e5-132">Azure 流量管理員</span><span class="sxs-lookup"><span data-stu-id="3e1e5-132">Azure Traffic Manager</span></span>

<span data-ttu-id="3e1e5-133">散佈至不同的端點，可以包含 cloud services 或 Azure 的 web 應用程式位於不同的資料中心] 或 [外部端點的流量。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="3e1e5-134">流量管理員會使用下列的路由方法：</span><span class="sxs-lookup"><span data-stu-id="3e1e5-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="3e1e5-135">**容錯移轉：**端點的相同或不同的 Azure 資料中心，且您想要使用的所有流量的主要端點，但提供備份主要索引器或備份端點已無法使用。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="3e1e5-136">**循環配置資源：**您想要在相同的資料中心的端點一組或跨越不同的資料中心散佈負載。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="3e1e5-137">**效能：**必須在不同地理位置端點和您要要求用戶端使用方面的最低的延遲 」 最接近"的端點。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="3e1e5-138">以下是三個地理位置分散的 web 應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="3e1e5-139">**圖 3： Azure 流量管理員**</span><span class="sxs-lookup"><span data-stu-id="3e1e5-139">**Figure 3: Azure Traffic Manager**</span></span>

![圖 3：Azure 流量管理員](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="3e1e5-p103">圖 3 是基本程序將要求路由傳送至美國、 歐洲和亞洲中的三個不同的 Azure web 應用程式使用流量管理員。在範例：</span><span class="sxs-lookup"><span data-stu-id="3e1e5-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="3e1e5-143">網站 URL 取得導向至 Azure 流量管理員] 中，這會傳回區域的 web 應用程式的名稱、 使用者 DNS 查詢根據效能的路由方法。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="3e1e5-144">使用者會具有歐洲地區的 web 應用程式的流量。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="3e1e5-145">如需詳細資訊，請參閱[流量管理員](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。</span><span class="sxs-lookup"><span data-stu-id="3e1e5-145">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3e1e5-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e1e5-146">See Also</span></span>

[<span data-ttu-id="3e1e5-147">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="3e1e5-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="3e1e5-148">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="3e1e5-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="3e1e5-149">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="3e1e5-149">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



