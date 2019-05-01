---
title: Microsoft 雲端連線的共同項目
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 摘要： 了解常見的網路基礎結構元素，以及如何準備您的網路。
ms.openlocfilehash: e00ad8820ef37c818c270323cf2aa036bb86a804
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490192"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="995bc-103">Microsoft 雲端連線的共同項目</span><span class="sxs-lookup"><span data-stu-id="995bc-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="995bc-104">**摘要：** 了解常見的網路基礎結構元素，以及如何準備您的網路。</span><span class="sxs-lookup"><span data-stu-id="995bc-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="995bc-105">將您的網路與 Microsoft 雲端整合，提供各種服務的最佳存取途徑。</span><span class="sxs-lookup"><span data-stu-id="995bc-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="995bc-106">步驟來準備用於 Microsoft 雲端服務的網路</span><span class="sxs-lookup"><span data-stu-id="995bc-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="995bc-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="995bc-107"></span></span>

<span data-ttu-id="995bc-108">在內部網路：</span><span class="sxs-lookup"><span data-stu-id="995bc-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="995bc-109">分析的用戶端電腦，並最佳化網路硬體、 軟體驅動程式、 通訊協定設定，以及網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="995bc-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="995bc-110">分析您的內部網路流量延遲與最佳路由傳送至網際網路邊緣裝置。</span><span class="sxs-lookup"><span data-stu-id="995bc-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="995bc-111">分析網際網路邊緣裝置的效能與容量，並更高層級的流量最佳化。</span><span class="sxs-lookup"><span data-stu-id="995bc-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="995bc-112">針對您的網際網路連線：</span><span class="sxs-lookup"><span data-stu-id="995bc-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="995bc-113">分析您的網際網路邊緣裝置 （例如外部防火牆） 與您所要連線的 Microsoft 雲端服務將區域位置之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="995bc-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="995bc-114">分析的容量與您目前的網際網路連線使用率，並新增容量，如有需要。</span><span class="sxs-lookup"><span data-stu-id="995bc-114">Analyze the capacity and utilization of your current Internet connection and add capacity if needed.</span></span> <span data-ttu-id="995bc-115">或者，新增的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="995bc-115">Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="995bc-116">Microsoft 雲端連線能力選項</span><span class="sxs-lookup"><span data-stu-id="995bc-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="995bc-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="995bc-117"></span></span>

<span data-ttu-id="995bc-118">使用您現有的網際網路管道或 ExpressRoute 連線到 Office 365、 Azure 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="995bc-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="995bc-119">**圖 1: Microsoft 雲端連線能力的選項**</span><span class="sxs-lookup"><span data-stu-id="995bc-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![圖 1：Microsoft Cloud 連線能力選項](media/Network-Poster/CommonElements.png)

  
<span data-ttu-id="995bc-121">圖 1 顯示如何在內部網路可以連線至 Microsoft 雲端供應項目使用其現有的網際網路管道或 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="995bc-121">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute.</span></span> <span data-ttu-id="995bc-122">網際網路管道代表 DMZ 和可以有下列元件：</span><span class="sxs-lookup"><span data-stu-id="995bc-122">The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="995bc-123">**內部防火牆：** 信任的網路和不受信任的一間障礙。</span><span class="sxs-lookup"><span data-stu-id="995bc-123">**Internal firewall:** A barrier between your trusted network and an untrusted one.</span></span> <span data-ttu-id="995bc-124">執行流量篩選 （根據規則） 與監視。</span><span class="sxs-lookup"><span data-stu-id="995bc-124">Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="995bc-125">**外部的工作負載：** 網站或其他工作負載可供外部使用者在網際網路上。</span><span class="sxs-lookup"><span data-stu-id="995bc-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="995bc-126">**Proxy 伺服器：** 服務代表內部網路使用者的網站內容的要求。</span><span class="sxs-lookup"><span data-stu-id="995bc-126">**Proxy server:** Services requests for web content on behalf of intranet users.</span></span> <span data-ttu-id="995bc-127">反向 proxy，允許來路不明的輸入的要求。</span><span class="sxs-lookup"><span data-stu-id="995bc-127">A reverse proxy permits unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="995bc-128">**外部防火牆：** 允許的輸出流量及指定的輸入的流量。</span><span class="sxs-lookup"><span data-stu-id="995bc-128">**External firewall:** Allows outbound traffic and specified inbound traffic.</span></span> <span data-ttu-id="995bc-129">可以執行位址轉譯、 封包檢查、 SSL 會自動換行和檢查或資料遺失防護。</span><span class="sxs-lookup"><span data-stu-id="995bc-129">Can perform address translation, packet inspection, SSL Break and Inspect, or data loss prevention.</span></span>
    
- <span data-ttu-id="995bc-130">**WAN 連線的 ISP:** 電訊廠商型的 ISP，具有網際網路連線和路由的對等連線。</span><span class="sxs-lookup"><span data-stu-id="995bc-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="995bc-131">通用的所有 Microsoft 雲端服務的網路中的區域</span><span class="sxs-lookup"><span data-stu-id="995bc-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="995bc-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="995bc-132"></span></span>

<span data-ttu-id="995bc-133">您必須採用任何 Microsoft 雲端服務時，請考慮這些區域的網路。</span><span class="sxs-lookup"><span data-stu-id="995bc-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="995bc-134">**內部網路效能：** 如果您的內部網路，包括用戶端電腦，無法進行最佳化，會降低效能，以網際網路為基礎的資源。</span><span class="sxs-lookup"><span data-stu-id="995bc-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="995bc-135">**Edge 裝置：** 在您網路的邊緣裝置的出口點，而且可以包括網路位址轉譯 (Nat)、 （包括反向 proxy） 的 proxy 伺服器、 防火牆、 入侵偵測裝置或兩者。</span><span class="sxs-lookup"><span data-stu-id="995bc-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="995bc-136">**網際網路連線：** 您的 WAN 連線到您的 ISP 和網際網路應有足夠的容量來處理尖峰負載。</span><span class="sxs-lookup"><span data-stu-id="995bc-136">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads.</span></span> <span data-ttu-id="995bc-137">您也可以使用 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="995bc-137">You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="995bc-138">**網際網路 DNS:** A、 AAAA、 CNAME、 MX、 PTR 和其他記錄來找出 Microsoft 雲端或您雲端中主控的服務。</span><span class="sxs-lookup"><span data-stu-id="995bc-138">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud.</span></span> <span data-ttu-id="995bc-139">例如，您可能需要的 CNAME 記錄您在 Azure PaaS 中裝載的應用程式。</span><span class="sxs-lookup"><span data-stu-id="995bc-139">For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="995bc-140">下一步</span><span class="sxs-lookup"><span data-stu-id="995bc-140">Next step</span></span>

[<span data-ttu-id="995bc-141">Microsoft 雲端連線 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="995bc-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="995bc-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="995bc-142">See also</span></span>

<span data-ttu-id="995bc-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="995bc-143"></span></span>

[<span data-ttu-id="995bc-144">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="995bc-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="995bc-145">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="995bc-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


