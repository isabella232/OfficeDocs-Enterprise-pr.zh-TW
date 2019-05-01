---
title: 設計 Microsoft Azure PaaS 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 摘要： 了解如何最佳化您存取 Microsoft Azure PaaS 的網路。
ms.openlocfilehash: 49096276a0e8356a11e52bc8765cc796eec32510
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491358"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="d7737-103">設計 Microsoft Azure PaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="d7737-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="d7737-104">**摘要：** 了解如何最佳化您存取 Microsoft Azure PaaS 的網路。</span><span class="sxs-lookup"><span data-stu-id="d7737-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="d7737-105">若要針對 Azure PaaS 應用程式最佳化網路，必須具備充足的網際網路頻寬，且可能需要跨多個站台或應用程式分散網路流量。</span><span class="sxs-lookup"><span data-stu-id="d7737-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="d7737-106">規劃步驟裝載在 Azure 中的組織 PaaS 應用程式</span><span class="sxs-lookup"><span data-stu-id="d7737-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="d7737-107">經過[Microsoft 雲端連線能力的共同元素](common-elements-of-microsoft-cloud-connectivity.md)中的**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="d7737-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="d7737-108">最佳化網際網路頻寬使用步驟 2 到 4 的**步驟來準備您的網路以 Microsoft SaaS 服務**] 區段中，在[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)。</span><span class="sxs-lookup"><span data-stu-id="d7737-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="d7737-109">決定您是否需要 Azure ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="d7737-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="d7737-110">適用於 web 型工作負載，決定您是否需要 Azure 應用程式閘道。</span><span class="sxs-lookup"><span data-stu-id="d7737-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="d7737-111">針對分散在不同資料中心中的不同端點的流量，決定您是否需要 Azure 流量管理員。</span><span class="sxs-lookup"><span data-stu-id="d7737-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="d7737-112">組織 PaaS 應用程式的網際網路頻寬</span><span class="sxs-lookup"><span data-stu-id="d7737-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="d7737-113">裝載在 Azure PaaS 中的組織應用程式需要內部網路使用者的網際網路頻寬。</span><span class="sxs-lookup"><span data-stu-id="d7737-113">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users.</span></span> <span data-ttu-id="d7737-114">其中有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="d7737-114">There are two options:</span></span>
  
- <span data-ttu-id="d7737-115">**選項 1:** 使用您現有的管道，以具有足夠容量處理尖峰負載的網際網路流量最佳化。</span><span class="sxs-lookup"><span data-stu-id="d7737-115">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads.</span></span> <span data-ttu-id="d7737-116">網際網路邊緣、 用戶端流量及 IT 作業考量，請參閱[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)。</span><span class="sxs-lookup"><span data-stu-id="d7737-116">See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="d7737-117">**選項 2:** 高頻寬或低延遲需求，會使用 Azure ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="d7737-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="d7737-118">**圖 1： 連接的 Azure PaaS 服務的連線選項**</span><span class="sxs-lookup"><span data-stu-id="d7737-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![圖 1：Azure PaaS 服務的連線選項](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="d7737-120">圖 1 顯示透過網際網路管道或 ExpressRoute 連線到 Azure PaaS 服務的內部網路。</span><span class="sxs-lookup"><span data-stu-id="d7737-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="d7737-121">Azure 應用程式閘道</span><span class="sxs-lookup"><span data-stu-id="d7737-121">Azure Application Gateway</span></span>

<span data-ttu-id="d7737-122">應用程式層級路由和負載平衡服務，可讓您建置可延展及高可用 web 前端在 Azure 中的 web 應用程式、 雲端服務和虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="d7737-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="d7737-123">**圖 2: Azure 應用程式閘道**</span><span class="sxs-lookup"><span data-stu-id="d7737-123">**Figure 2: Azure Application Gateway**</span></span>

![圖 2：Azure 應用程式閘道服務](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="d7737-125">圖 2 顯示 Azure 應用程式閘道和使用者從網際網路的要求路由至 Azure 的 web 應用程式、 雲端服務時或虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="d7737-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="d7737-126">應用程式閘道目前支援層級 7 應用程式傳遞下列：</span><span class="sxs-lookup"><span data-stu-id="d7737-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="d7737-127">HTTP 負載平衡</span><span class="sxs-lookup"><span data-stu-id="d7737-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="d7737-128">Cookie 為主的工作階段親和性</span><span class="sxs-lookup"><span data-stu-id="d7737-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="d7737-129">SSL 卸載</span><span class="sxs-lookup"><span data-stu-id="d7737-129">SSL offload</span></span>
    
<span data-ttu-id="d7737-130">如需詳細資訊，請參閱 < <b0>Application Gateway</b0>。</span><span class="sxs-lookup"><span data-stu-id="d7737-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="d7737-131">Azure 流量管理員</span><span class="sxs-lookup"><span data-stu-id="d7737-131">Azure Traffic Manager</span></span>

<span data-ttu-id="d7737-132">分散到不同的端點，可以包含雲端服務或位於不同的資料中心] 或 [外部端點的 Azure 的 web 應用程式的流量。</span><span class="sxs-lookup"><span data-stu-id="d7737-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="d7737-133">流量管理員會使用下列的路由方法：</span><span class="sxs-lookup"><span data-stu-id="d7737-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="d7737-134">**容錯移轉：** 端點是在相同或不同的 Azure 資料中心，而您想要使用的主要端點的所有流量，但提供備份，以防主要或備份端點會無法使用。</span><span class="sxs-lookup"><span data-stu-id="d7737-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="d7737-135">**循環配置資源：** 您想要將負載分散給一群在相同資料中心的端點或跨越不同的資料中心。</span><span class="sxs-lookup"><span data-stu-id="d7737-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="d7737-136">**效能：** 您必須在不同地理位置的端點，而且您想要求用戶端使用方面的最低延遲的 「 最接近的 「 端點。</span><span class="sxs-lookup"><span data-stu-id="d7737-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="d7737-137">以下是三個地理位置分散的 web 應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="d7737-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="d7737-138">**圖 3：Azure 流量管理員**</span><span class="sxs-lookup"><span data-stu-id="d7737-138">**Figure 3: Azure Traffic Manager**</span></span>

![圖 3：Azure 流量管理員](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="d7737-140">圖 3 顯示基本程序流量管理員用以在美國、 歐洲及亞洲的三個不同的 Azure web 應用程式要求路由傳送。</span><span class="sxs-lookup"><span data-stu-id="d7737-140">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia.</span></span> <span data-ttu-id="d7737-141">在範例中：</span><span class="sxs-lookup"><span data-stu-id="d7737-141">In the example:</span></span>
  
1. <span data-ttu-id="d7737-142">URL 取得導向至 Azure 流量管理員] 中，會傳回區域的 web 應用程式的名稱，網站使用者 DNS 查詢為基礎的效能路由方法。</span><span class="sxs-lookup"><span data-stu-id="d7737-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="d7737-143">從使用者起始與歐洲地區的 web 應用程式的流量。</span><span class="sxs-lookup"><span data-stu-id="d7737-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="d7737-144">如需詳細資訊，請參閱[Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。</span><span class="sxs-lookup"><span data-stu-id="d7737-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="d7737-145">下一步</span><span class="sxs-lookup"><span data-stu-id="d7737-145">Next step</span></span>

[<span data-ttu-id="d7737-146">設計 Microsoft Azure IaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="d7737-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="d7737-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7737-147">See also</span></span>

[<span data-ttu-id="d7737-148">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="d7737-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="d7737-149">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="d7737-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

