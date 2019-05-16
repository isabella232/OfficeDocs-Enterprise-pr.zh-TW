---
title: 設計 Microsoft SaaS 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要： 了解如何最佳化您的網路存取 Microsoft 的 SaaS 服務，包括 Office 365、 Microsoft Intune 和 Dynamics 365。
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067769"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="b6aec-103">設計 Microsoft SaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="b6aec-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="b6aec-104">**摘要：** 了解如何最佳化您的網路存取 Microsoft 的 SaaS 服務，包括 Office 365、 Microsoft Intune 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="b6aec-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="b6aec-105">針對 Microsoft SaaS 服務將您的網路最佳化時，必須將內部和邊緣裝置設定為將不同類別的流量路由傳送至 Microsoft SaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="b6aec-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="b6aec-106">步驟來準備用於 Microsoft SaaS 服務的網路</span><span class="sxs-lookup"><span data-stu-id="b6aec-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="b6aec-107">請遵循下列步驟來最佳化您的網路以 Microsoft SaaS 服務：</span><span class="sxs-lookup"><span data-stu-id="b6aec-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="b6aec-108">經過[Microsoft 雲端連線能力的共同元素](common-elements-of-microsoft-cloud-connectivity.md)中的**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="b6aec-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="b6aec-109">新增至每個您的分公司的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="b6aec-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="b6aec-110">請確定所有的網際網路連線的 Isp，使用具有本機 IP 位址的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b6aec-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="b6aec-111">檢查您的網路 hairpin 以取得，基於雲端的安全性服務，例如中介目的地，並且盡可能刪除它們。</span><span class="sxs-lookup"><span data-stu-id="b6aec-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="b6aec-112">設定您的邊緣裝置能夠略過處理針對最佳化和允許類別的 Microsoft SaaS 流量。</span><span class="sxs-lookup"><span data-stu-id="b6aec-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="b6aec-113">Microsoft 的 SaaS 服務最佳化流量</span><span class="sxs-lookup"><span data-stu-id="b6aec-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="b6aec-114">有三種類別的 Microsoft SaaS 流量：</span><span class="sxs-lookup"><span data-stu-id="b6aec-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="b6aec-115">最佳化</span><span class="sxs-lookup"><span data-stu-id="b6aec-115">Optimize</span></span>

  <span data-ttu-id="b6aec-116">所需的連線至每個 Microsoft SaaS 服務與代表超過 75%的 Microsoft SaaS 頻寬、 連線及資料量。</span><span class="sxs-lookup"><span data-stu-id="b6aec-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="b6aec-117">允許</span><span class="sxs-lookup"><span data-stu-id="b6aec-117">Allow</span></span>

  <span data-ttu-id="b6aec-118">所需的連線至特定 Microsoft SaaS 服務和功能但不是對網路效能和延遲不如最佳化類別中敏感。</span><span class="sxs-lookup"><span data-stu-id="b6aec-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="b6aec-119">預設</span><span class="sxs-lookup"><span data-stu-id="b6aec-119">Default</span></span>

  <span data-ttu-id="b6aec-120">代表 Microsoft SaaS 服務並不需要任何最佳化的相依性。</span><span class="sxs-lookup"><span data-stu-id="b6aec-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="b6aec-121">您可以將視為像是一般網際網路流量的預設類別流量。</span><span class="sxs-lookup"><span data-stu-id="b6aec-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="b6aec-122">**圖 1： 建議的針對 Microsoft SaaS 流量的所有辦公室的組態**</span><span class="sxs-lookup"><span data-stu-id="b6aec-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![圖 1： 建議的針對 Microsoft SaaS 流量的所有辦公室的組態](media/Network-Poster/SaaS1.png)

<span data-ttu-id="b6aec-124">圖 1 顯示所有辦公室，包括分公司和地區或管理中心的在其中建議的組態的設定：</span><span class="sxs-lookup"><span data-stu-id="b6aec-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="b6aec-125">**預設**類別和一般網際網路流量路由傳送至有 proxy 伺服器和其他邊緣裝置提供保護針對網際網路型安全性風險的辦公室。</span><span class="sxs-lookup"><span data-stu-id="b6aec-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="b6aec-126">**最佳化**和**允許**類別流量會轉送直接向 Microsoft 網路前端包含連線的使用者，略過 proxy 伺服器和其他邊緣裝置在辦公室，最靠近的邊緣。</span><span class="sxs-lookup"><span data-stu-id="b6aec-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="b6aec-127">軟體定義的廣域網路 (SD WAN) 的網路裝置分公司中分隔流量以便：</span><span class="sxs-lookup"><span data-stu-id="b6aec-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="b6aec-128">**預設**類別和一般網際網路流量前往透過 WAN 骨幹中央或地區辦公室。</span><span class="sxs-lookup"><span data-stu-id="b6aec-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="b6aec-129">**最佳化**和**允許**類別流量前往 ISP 提供當地網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="b6aec-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="b6aec-130">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="b6aec-130">For more information, see:</span></span>
  
- [<span data-ttu-id="b6aec-131">網路連線原則</span><span class="sxs-lookup"><span data-stu-id="b6aec-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="b6aec-132">Office 365 的網路和移轉規劃</span><span class="sxs-lookup"><span data-stu-id="b6aec-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="b6aec-133">下一步</span><span class="sxs-lookup"><span data-stu-id="b6aec-133">Next step</span></span>

[<span data-ttu-id="b6aec-134">設計 Microsoft Azure PaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="b6aec-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="b6aec-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6aec-135">See also</span></span>

[<span data-ttu-id="b6aec-136">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="b6aec-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="b6aec-137">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="b6aec-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

