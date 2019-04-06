---
title: Microsoft 混合式雲端案例的架構
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 摘要： 了解 Microsoft 的混合式雲端供應項目的的架構。
ms.openlocfilehash: f5493c0f008b22af412ee95ccb8b7581eee71476
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038007"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="26c4d-103">Microsoft 混合式雲端案例的架構</span><span class="sxs-lookup"><span data-stu-id="26c4d-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="26c4d-104">**摘要：** 了解 Microsoft 的混合式雲端供應項目的的架構。</span><span class="sxs-lookup"><span data-stu-id="26c4d-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="26c4d-105">用於規劃及實作 Microsoft 雲端服務與平台的混合式雲端案例的架構的方法。</span><span class="sxs-lookup"><span data-stu-id="26c4d-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="26c4d-106">**圖 1: Microsoft 混合式雲端堆疊**</span><span class="sxs-lookup"><span data-stu-id="26c4d-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft 混合式雲端堆疊](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="26c4d-108">圖 1 顯示 Microsoft 混合式雲端堆疊和其圖層，其中包含內部部署、 網路、 身分識別、 應用程式與案例中和雲端服務 （Microsoft SaaS、 Azure PaaS 和 Azure PaaS） 的類別。</span><span class="sxs-lookup"><span data-stu-id="26c4d-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="26c4d-109">應用程式和案例圖層有此模型中的其他文章會詳細說明的特定混合式雲端案例。</span><span class="sxs-lookup"><span data-stu-id="26c4d-109">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model.</span></span> <span data-ttu-id="26c4d-110">身分識別、 網路和內部部署層可以是常見的雲端服務 （SaaS、 PaaS 或 PaaS） 的類別。</span><span class="sxs-lookup"><span data-stu-id="26c4d-110">The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="26c4d-111">內部部署</span><span class="sxs-lookup"><span data-stu-id="26c4d-111">On-premises</span></span>
    
    <span data-ttu-id="26c4d-112">混合式案例的內部部署基礎結構可以包含伺服器用於 SharePoint、 Exchange、 Skype for Business 和商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="26c4d-112">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications.</span></span> <span data-ttu-id="26c4d-113">它也可以包含的資料存放區 （資料庫、 清單、 檔案）。</span><span class="sxs-lookup"><span data-stu-id="26c4d-113">It can also include data stores (databases, lists, files).</span></span> <span data-ttu-id="26c4d-114">ExpressRoute 連線，而必須透過反向 proxy 或讓伺服器或資料，可在您 DMZ 上存取或外部網路允許存取內部部署資料存放區。</span><span class="sxs-lookup"><span data-stu-id="26c4d-114">Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="26c4d-115">工作列最右邊的網路</span><span class="sxs-lookup"><span data-stu-id="26c4d-115">Network</span></span>
    
    <span data-ttu-id="26c4d-116">有兩種選擇進行 Microsoft 雲端平台及服務的連線： 您的現有 Internet 管道和 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="26c4d-116">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute.</span></span> <span data-ttu-id="26c4d-117">如果可預測的效能非常重要，請使用 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="26c4d-117">Use an ExpressRoute connection if predictable performance is important.</span></span> <span data-ttu-id="26c4d-118">您可以使用一個 ExpressRoute 連線直接連線至 Microsoft SaaS 服務 （Office 365 和 Dynamics 365）、 Azure PaaS 服務和 Azure IaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="26c4d-118">You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="26c4d-119">身分識別</span><span class="sxs-lookup"><span data-stu-id="26c4d-119">Identity</span></span>
    
    <span data-ttu-id="26c4d-120">雲端身分識別基礎結構，有兩種方式可移，根據 Microsoft 雲端平台。</span><span class="sxs-lookup"><span data-stu-id="26c4d-120">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform.</span></span> <span data-ttu-id="26c4d-121">為 SaaS、 Azure PaaS，與 Azure AD 整合您的內部部署身分識別基礎結構或您內部部署身分識別基礎結構或協力廠商身分識別提供者同盟。</span><span class="sxs-lookup"><span data-stu-id="26c4d-121">For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers.</span></span> <span data-ttu-id="26c4d-122">在 Azure 中執行的 vm，您可以擴充到您的 Vm 的所在位置的虛擬網路 (Vnet) 的 Active Directory 網域服務 (AD DS)，例如您內部部署身分識別基礎結構。</span><span class="sxs-lookup"><span data-stu-id="26c4d-122">For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Active Directory Domain Services (AD DS), to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="26c4d-123">三個階段雲端採用程序的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="26c4d-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="26c4d-124">許多企業，包括 Microsoft 的則會使用採用雲端的三個階段方法。</span><span class="sxs-lookup"><span data-stu-id="26c4d-124">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud.</span></span> <span data-ttu-id="26c4d-125">混合式雲端案例可以每個階段中扮演重要角色。</span><span class="sxs-lookup"><span data-stu-id="26c4d-125">Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="26c4d-126">Saas 移動生產力工作負載</span><span class="sxs-lookup"><span data-stu-id="26c4d-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="26c4d-127">目前或必須保持內部部署的生產力工作負載，混合式案例允許他們與與其雲端對應項目進行整合。</span><span class="sxs-lookup"><span data-stu-id="26c4d-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="26c4d-128">開發新的和新式的應用程式，在 Azure PaaS 中</span><span class="sxs-lookup"><span data-stu-id="26c4d-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="26c4d-129">Azure PaaS 混合應用程式可以安全地利用內部部署伺服器或儲存資源。</span><span class="sxs-lookup"><span data-stu-id="26c4d-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="26c4d-130">移至 Azure IaaS 的現有應用程式</span><span class="sxs-lookup"><span data-stu-id="26c4d-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="26c4d-131">增益 shift 和在雲端建立案例中，執行於 Azure Vm 的伺服器型應用程式會提供簡單佈建和縮放比例。</span><span class="sxs-lookup"><span data-stu-id="26c4d-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="26c4d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26c4d-132">See Also</span></span>

[<span data-ttu-id="26c4d-133">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="26c4d-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="26c4d-134">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="26c4d-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

