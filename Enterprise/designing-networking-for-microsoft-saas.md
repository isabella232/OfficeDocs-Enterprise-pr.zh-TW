---
title: 設計 Microsoft SaaS 的網路
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要： 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872264"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="608e1-103">設計 Microsoft SaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="608e1-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="608e1-104">**摘要：** 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="608e1-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="608e1-105">最佳化您的網路 Microsoft saas 和服務要求的內部的設定資料庫和路由傳送到 Microsoft saas 和服務的流量的不同類別的邊緣裝置。</span><span class="sxs-lookup"><span data-stu-id="608e1-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="608e1-106">準備您的網路 Microsoft saas 和服務的步驟</span><span class="sxs-lookup"><span data-stu-id="608e1-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="608e1-107">請遵循這些步驟以最佳化您的網路 Microsoft saas 和服務：</span><span class="sxs-lookup"><span data-stu-id="608e1-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="608e1-108">經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="608e1-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="608e1-109">將網際網路連線新增至每個您辦公室。</span><span class="sxs-lookup"><span data-stu-id="608e1-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="608e1-110">請確認所有網際網路連線的 Isp 本機的 IP 位址搭配使用的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="608e1-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="608e1-111">檢查網路 hairpins、 雲端式安全性服務等的中介目的地，並盡可能避免它們。</span><span class="sxs-lookup"><span data-stu-id="608e1-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="608e1-112">設定您的 edge 裝置略過最佳化的處理，讓 Microsoft saas 和流量的類別。</span><span class="sxs-lookup"><span data-stu-id="608e1-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="608e1-113">最佳化給 Microsoft 的 saas 和服務的流量</span><span class="sxs-lookup"><span data-stu-id="608e1-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="608e1-114">有三個類別的 Microsoft saas 和流量：</span><span class="sxs-lookup"><span data-stu-id="608e1-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="608e1-115">最佳化</span><span class="sxs-lookup"><span data-stu-id="608e1-115">Optimize</span></span>

  <span data-ttu-id="608e1-116">所需的每一個 Microsoft saas 和服務，以及代表超過 75%的 Microsoft saas 和頻寬、 連線和大量的資料連線。</span><span class="sxs-lookup"><span data-stu-id="608e1-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="608e1-117">允許</span><span class="sxs-lookup"><span data-stu-id="608e1-117">Allow</span></span>

  <span data-ttu-id="608e1-118">所需的連線至特定 Microsoft saas 和服務和功能 （英文） 但不是以受到網路效能和外出最佳化類別中的延遲。</span><span class="sxs-lookup"><span data-stu-id="608e1-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="608e1-119">預設</span><span class="sxs-lookup"><span data-stu-id="608e1-119">Default</span></span>

  <span data-ttu-id="608e1-p101">代表 Microsoft saas 和服務並不需要任何最佳化的相依性。您可以將類似標準網際網路流量的預設類別流量。</span><span class="sxs-lookup"><span data-stu-id="608e1-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="608e1-122">**圖 1： 適用於建議設定的所有分公司的 Microsoft saas 和流量**</span><span class="sxs-lookup"><span data-stu-id="608e1-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![圖 1： 適用於建議設定的所有分公司的 Microsoft saas 和流量](media/Network-Poster/SaaS1.png)

<span data-ttu-id="608e1-124">圖 1 顯示的所有分公司，包括分公司和地區或中央 api，在其中的建議的設定：</span><span class="sxs-lookup"><span data-stu-id="608e1-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="608e1-125">**預設**類別與一般網際網路的流量路由傳送至具有 proxy 伺服器和其他 edge 裝置提供保護對網際網路型安全性風險的辦公室。</span><span class="sxs-lookup"><span data-stu-id="608e1-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="608e1-126">**最佳化**] 和 [**允許**類別流量遞給直接 Microsoft 網路前端包含連線的使用者，略過 proxy 伺服器和其他 edge 裝置 office，最靠近的邊緣。</span><span class="sxs-lookup"><span data-stu-id="608e1-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="608e1-127">在分公司的軟體定義廣域網路 (SD WAN) 的網路裝置分隔流量使：</span><span class="sxs-lookup"><span data-stu-id="608e1-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="608e1-128">**預設**類別與一般透過 WAN 骨幹網際網路的流量會移到中央或地區的辦公室。</span><span class="sxs-lookup"><span data-stu-id="608e1-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="608e1-129">**最佳化**] 和 [**允許**類別流量前往 ISP 提供本機網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="608e1-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="608e1-130">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="608e1-130">For more information, see:</span></span>
  
- [<span data-ttu-id="608e1-131">網路連線原則</span><span class="sxs-lookup"><span data-stu-id="608e1-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="608e1-132">Office 365 的網路和移轉規劃</span><span class="sxs-lookup"><span data-stu-id="608e1-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="608e1-133">下一步</span><span class="sxs-lookup"><span data-stu-id="608e1-133">Next step</span></span>

[<span data-ttu-id="608e1-134">設計 Microsoft Azure PaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="608e1-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="608e1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="608e1-135">See also</span></span>

[<span data-ttu-id="608e1-136">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="608e1-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="608e1-137">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="608e1-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

