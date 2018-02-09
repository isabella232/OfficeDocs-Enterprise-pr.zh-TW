---
title: "Microsoft 混合雲端案例的架構"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "摘要： 了解 Microsoft 的混合式雲端方案的架構。"
ms.openlocfilehash: f1c234026324b2c507dd4369cb98306e7e83a775
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="3d92b-103">Microsoft 混合雲端案例的架構</span><span class="sxs-lookup"><span data-stu-id="3d92b-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="3d92b-104">**摘要：**了解 Microsoft 的混合式雲端方案的架構。</span><span class="sxs-lookup"><span data-stu-id="3d92b-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="3d92b-105">若要規劃並實作搭配 Microsoft 雲端服務與平台的混合式雲端案例使用架構的方法。</span><span class="sxs-lookup"><span data-stu-id="3d92b-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="3d92b-106">**圖 1： Microsoft 混合雲端堆疊**</span><span class="sxs-lookup"><span data-stu-id="3d92b-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft 混合式雲端堆疊](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
<span data-ttu-id="3d92b-108">圖 1 顯示 Microsoft 混合雲端堆疊和其階層，其中包含內部部署、 網路、 身分識別、 應用程式和案例，以及雲端服務 （Microsoft SaaS、 Azure PaaS 和 Azure PaaS） 的類別。</span><span class="sxs-lookup"><span data-stu-id="3d92b-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="3d92b-p101">應用程式與案例層包含此模型中的其他文章中詳述的特定混合式雲端案例。身分識別、 網路和內部部署圖層] 可以是公用雲端服務 （SaaS、 PaaS 或 PaaS） 的類別。</span><span class="sxs-lookup"><span data-stu-id="3d92b-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="3d92b-111">內部部署</span><span class="sxs-lookup"><span data-stu-id="3d92b-111">On-premises</span></span>
    
    <span data-ttu-id="3d92b-p102">混合式案例的內部部署基礎結構可以包含伺服器的 SharePoint、 Exchange、 Skype for Business 和營運系統應用程式。它也可以包含資料儲存區 （資料庫、 清單、 檔案）。不含 ExpressRoute 連線的存取權的內部部署資料存放區必須允許透過反向 proxy 或以存取在您 DMZ 或外部網路伺服器或資料。</span><span class="sxs-lookup"><span data-stu-id="3d92b-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="3d92b-115">工作列最右邊的網路</span><span class="sxs-lookup"><span data-stu-id="3d92b-115">Network</span></span>
    
    <span data-ttu-id="3d92b-p103">有兩個選擇 Microsoft cloud 平台及服務的連線： 您的現有 Internet 管道和 ExpressRoute。如果可預測的效能，請務必使用 ExpressRoute 連線。您可以使用一個 ExpressRoute 連線至直接連接到 Microsoft saas 和服務 （Office 365 和 Dynamics 365）、 Azure PaaS 服務及 Azure PaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="3d92b-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure PaaS services.</span></span>
    
- <span data-ttu-id="3d92b-119">身分識別</span><span class="sxs-lookup"><span data-stu-id="3d92b-119">Identity</span></span>
    
    <span data-ttu-id="3d92b-p104">雲端身分識別基礎結構，有兩種方式可以移，根據 Microsoft cloud 平台。SaaS 和 Azure PaaS、 整合與 Azure AD 的內部部署身分識別基礎結構或與您的內部識別基礎結構或協力廠商身分識別提供者結盟。針對執行 Azure 中的 Vm，您可以擴充到您的 Vm 所在虛擬網路 (VNets) 的 Windows Server AD，例如您的內部身分識別基礎結構。</span><span class="sxs-lookup"><span data-stu-id="3d92b-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="3d92b-123">三階段雲端採用程序的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="3d92b-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="3d92b-p105">許多企業，包括 Microsoft 的、 使用採用雲端的三階段方法。混合式雲端案例可以在每個階段中扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="3d92b-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="3d92b-126">將產能工作量移至 saas 和</span><span class="sxs-lookup"><span data-stu-id="3d92b-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="3d92b-127">產能工作量目前或必須保持在最內部部署的混合式案例允許他們與與其雲端對應項目進行整合。</span><span class="sxs-lookup"><span data-stu-id="3d92b-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="3d92b-128">開發新的和現代 Azure PaaS 中的應用程式</span><span class="sxs-lookup"><span data-stu-id="3d92b-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="3d92b-129">Azure PaaS 混合式應用程式可以安全地運用內部伺服器或儲存資源。</span><span class="sxs-lookup"><span data-stu-id="3d92b-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="3d92b-130">移動 Azure IaaS 現有的應用程式</span><span class="sxs-lookup"><span data-stu-id="3d92b-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="3d92b-131">增益 shift 並在雲端建立案例的伺服器端 Azure Vm 上執行的應用程式提供簡單佈建與縮放比例。</span><span class="sxs-lookup"><span data-stu-id="3d92b-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="3d92b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d92b-132">See Also</span></span>

[<span data-ttu-id="3d92b-133">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="3d92b-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="3d92b-134">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="3d92b-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="3d92b-135">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="3d92b-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



