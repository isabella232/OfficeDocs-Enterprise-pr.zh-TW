---
title: "Microsoft 雲端連線的常見的元素"
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "摘要： 了解一般的網路基礎結構元素，以及如何準備您的網路。"
ms.openlocfilehash: 9dffcae28283c9f8b8c219284554225645435e0a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="de07c-103">Microsoft 雲端連線的常見的元素</span><span class="sxs-lookup"><span data-stu-id="de07c-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="de07c-104">**摘要：**了解一般的網路基礎結構元素，以及如何準備您的網路。</span><span class="sxs-lookup"><span data-stu-id="de07c-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="de07c-105">將您的網路與 Microsoft 雲端整合，提供各種服務的最佳存取途徑。</span><span class="sxs-lookup"><span data-stu-id="de07c-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="de07c-106">若要準備您的網路 Microsoft 雲端服務的步驟</span><span class="sxs-lookup"><span data-stu-id="de07c-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="de07c-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="de07c-107"></span></span>

<span data-ttu-id="de07c-108">為您的內部網路：</span><span class="sxs-lookup"><span data-stu-id="de07c-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="de07c-109">分析您的用戶端電腦和最佳化網路硬體、 軟體驅動程式、 通訊協定設定及網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="de07c-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="de07c-110">分析您的內部網路流量延遲和最佳路由傳送至網際網路 edge 裝置。</span><span class="sxs-lookup"><span data-stu-id="de07c-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="de07c-111">分析的容量和效能網際網路 edge 裝置並最佳化的較高的層級的流量。</span><span class="sxs-lookup"><span data-stu-id="de07c-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="de07c-112">網際網路連線：</span><span class="sxs-lookup"><span data-stu-id="de07c-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="de07c-113">分析您的網際網路 edge 裝置 （例如外部防火牆） 與您所連接之 Microsoft 雲端服務將區域位置之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="de07c-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="de07c-p101">分析的容量和您目前的網際網路連線的使用情況並視新增容量。或者，新增 [ExpressRoute 連線]。</span><span class="sxs-lookup"><span data-stu-id="de07c-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="de07c-116">Microsoft 雲端連線選項</span><span class="sxs-lookup"><span data-stu-id="de07c-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="de07c-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="de07c-117"></span></span>

<span data-ttu-id="de07c-118">使用您現有的網際網路管道或 Office 365、 Azure、 和 Dynamics 365 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="de07c-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="de07c-119">**圖 1： Microsoft cloud 連線選項**</span><span class="sxs-lookup"><span data-stu-id="de07c-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![圖 1：Microsoft Cloud 連線能力選項](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="de07c-p102">圖 1 顯示如何在內部網路可以連線至 Microsoft cloud 方案使用其現有的網際網路管道或 ExpressRoute。網際網路管道代表 DMZ，且可有下列元件：</span><span class="sxs-lookup"><span data-stu-id="de07c-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="de07c-p103">**內部防火牆：**信任的網路與未受信任的其中一個之間門檻。執行流量篩選 （根據規則） 和監控。</span><span class="sxs-lookup"><span data-stu-id="de07c-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="de07c-125">**外部工作量：**網站或其他工作負載供外部使用者在網際網路上。</span><span class="sxs-lookup"><span data-stu-id="de07c-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="de07c-p104">**Proxy 伺服器：**服務要求代表內部網路使用者的 web 內容。反向 proxy 允許來路不明的輸入的要求。</span><span class="sxs-lookup"><span data-stu-id="de07c-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="de07c-p105">**外部防火牆：**允許輸出流量及指定的輸入的流量。可執行位址轉譯。</span><span class="sxs-lookup"><span data-stu-id="de07c-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="de07c-130">**WAN 連線的 ISP:**ISP 具有網際網路連線能力與路由的對等電信業者式連線。</span><span class="sxs-lookup"><span data-stu-id="de07c-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="de07c-131">範圍的所有 Microsoft 雲端服務一般網路區域</span><span class="sxs-lookup"><span data-stu-id="de07c-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="de07c-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="de07c-132"></span></span>

<span data-ttu-id="de07c-133">您需要時要考慮這些方面的網路採用任何 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="de07c-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="de07c-134">**內部網路效能：**如果您的內部網路，包括用戶端電腦無法進行最佳化，會降低效能網際網路架構的資源。</span><span class="sxs-lookup"><span data-stu-id="de07c-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="de07c-135">**Edge 裝置：**在您的網路邊緣的裝置輸出點且可包含網路位址轉譯器 (Nat)、 proxy 伺服器 （包括反向 proxy）、 防火牆、 入侵偵測裝置或組合。</span><span class="sxs-lookup"><span data-stu-id="de07c-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="de07c-p106">**網際網路連線：**您的 WAN 連線至您的 ISP 和網際網路應該有足夠的容量來處理尖峰負載。您也可以使用 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="de07c-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="de07c-p107">**網際網路 DNS：**A、 AAAA、 CNAME、 MX、 PTR 及其他記錄以找出 Microsoft cloud 或雲端服務。例如，您可能需要 CNAME 記錄為您的應用程式架設在 Azure PaaS。</span><span class="sxs-lookup"><span data-stu-id="de07c-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="de07c-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="de07c-140">See Also</span></span>

<span data-ttu-id="de07c-141"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="de07c-141"></span></span>

[<span data-ttu-id="de07c-142">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="de07c-142">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="de07c-143">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="de07c-143">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="de07c-144">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="de07c-144">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


