---
title: Contoso 的 IT 基礎結構與需求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: 摘要： 了解 Contoso 的基本結構內部 IT 基礎結構和如何其商務需要可符合由 Microsoft cloud 方案。
ms.openlocfilehash: e500aa1f3105c1e605d0d3c1d5f66651acb82b34
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915728"
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="986c3-103">Contoso 的 IT 基礎結構與需求</span><span class="sxs-lookup"><span data-stu-id="986c3-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="986c3-104">**摘要：** 了解 Contoso 的基本結構內部 IT 基礎結構和如何其商務需要可符合由 Microsoft cloud 方案。</span><span class="sxs-lookup"><span data-stu-id="986c3-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="986c3-105">Contoso 正從內部部署轉換、 至雲端 （含） 的一個納入雲端式個人產能工作量、 應用程式以及混合式案例的集中式的 IT 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="986c3-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="986c3-106">Contoso 現有的 IT 基礎結構</span><span class="sxs-lookup"><span data-stu-id="986c3-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="986c3-107">Contoso 使用多半集中式內部 IT 基礎結構與 Paris headquarters 中的應用程式資料中心。</span><span class="sxs-lookup"><span data-stu-id="986c3-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="986c3-108">**圖 1： Contoso 的現有 IT 基礎結構**</span><span class="sxs-lookup"><span data-stu-id="986c3-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Contoso 現有的 IT 基礎結構](media/Contoso-Poster/Existing-IT.png)
  
<span data-ttu-id="986c3-110">圖 1 顯示 headquarters office 應用程式資料中心、 DMZ 與網際網路。</span><span class="sxs-lookup"><span data-stu-id="986c3-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="986c3-111">在 [Contoso 的 DMZ 不同的伺服器集提供：</span><span class="sxs-lookup"><span data-stu-id="986c3-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="986c3-112">遠端存取 contoso 公司內部網路和網頁代理 Paris headquarters 的工作者。</span><span class="sxs-lookup"><span data-stu-id="986c3-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="986c3-113">架設 Contoso 公用網站中，從哪些客戶可以排序產品、 組件、 或供應。</span><span class="sxs-lookup"><span data-stu-id="986c3-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="986c3-114">架設 Contoso 合作夥伴外部合作夥伴的通訊與共同作業。</span><span class="sxs-lookup"><span data-stu-id="986c3-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="986c3-115">Contoso 的業務需求</span><span class="sxs-lookup"><span data-stu-id="986c3-115">Contoso's business needs</span></span>

<span data-ttu-id="986c3-116">以下是會依照優先順序 Contoso 的業務需求：</span><span class="sxs-lookup"><span data-stu-id="986c3-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="986c3-117">遵守區域法規需求</span><span class="sxs-lookup"><span data-stu-id="986c3-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="986c3-118">若要防止罰並維持與本機政府良好的關係，請 Contoso 必須確定遵守資料儲存區與加密規定。</span><span class="sxs-lookup"><span data-stu-id="986c3-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="986c3-119">改善廠商和協力廠商的管理</span><span class="sxs-lookup"><span data-stu-id="986c3-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="986c3-p101">合作夥伴外部已過時且最耗費成本來維護。Contoso 想要取代使用同盟的驗證的雲端架構解決方案。</span><span class="sxs-lookup"><span data-stu-id="986c3-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="986c3-122">改善行動工作團隊的生產力、 裝置管理和存取</span><span class="sxs-lookup"><span data-stu-id="986c3-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="986c3-123">Contoso 的僅限行動工作團隊會展開並需要裝置管理可確保財產保護及更有效率資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="986c3-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="986c3-124">減少遠端存取基礎結構</span><span class="sxs-lookup"><span data-stu-id="986c3-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="986c3-125">移至雲端的遠端工作者常存取的資源，Contoso 將儲存 money 降低其遠端存取解決方案維護和支援成本。</span><span class="sxs-lookup"><span data-stu-id="986c3-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="986c3-126">向內部部署資料中心下向內</span><span class="sxs-lookup"><span data-stu-id="986c3-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="986c3-127">Contoso 資料中心都包含數百個部份只會執行影響 IT 人員從維護高的商務值工作負載的舊版或封存功能的伺服器。</span><span class="sxs-lookup"><span data-stu-id="986c3-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="986c3-128">結束一季處理的向外延展運算和儲存資源</span><span class="sxs-lookup"><span data-stu-id="986c3-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="986c3-129">結束一季財務會計和預測處理以及庫存管理需要短期增加伺服器及存放區。</span><span class="sxs-lookup"><span data-stu-id="986c3-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="986c3-130">對應 Contoso 的商務需要 Microsoft cloud 方案</span><span class="sxs-lookup"><span data-stu-id="986c3-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="986c3-131">根據 Microsoft cloud 方案，Contoso 的分析的 IT 部門會決定下列對應：</span><span class="sxs-lookup"><span data-stu-id="986c3-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="986c3-132">**軟體即服務 (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="986c3-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="986c3-133">**以服務 (Azure PaaS) 的平台**</span><span class="sxs-lookup"><span data-stu-id="986c3-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="986c3-134">**基礎架構以服務 (Azure IaaS)**</span><span class="sxs-lookup"><span data-stu-id="986c3-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="986c3-135">**Office 365：** 在雲端中主要個人及群組的產能應用程式。</span><span class="sxs-lookup"><span data-stu-id="986c3-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="986c3-136">業務需求： 1 3 5</span><span class="sxs-lookup"><span data-stu-id="986c3-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="986c3-137">主控銷售和支援文件並使用雲端應用程式的資訊系統。</span><span class="sxs-lookup"><span data-stu-id="986c3-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="986c3-138">業務需求： 3</span><span class="sxs-lookup"><span data-stu-id="986c3-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="986c3-139">將封存與舊版系統移至雲端架構的伺服器。</span><span class="sxs-lookup"><span data-stu-id="986c3-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="986c3-140">業務需求： 5</span><span class="sxs-lookup"><span data-stu-id="986c3-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="986c3-p102">**Dynamics 365:** 使用雲端式客戶與廠商管理。移除網路 DMZ 中的協力廠商。</span><span class="sxs-lookup"><span data-stu-id="986c3-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="986c3-143">業務需求： 2</span><span class="sxs-lookup"><span data-stu-id="986c3-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="986c3-144">行動應用程式的雲端式而不是 Paris 資料中心架構。</span><span class="sxs-lookup"><span data-stu-id="986c3-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="986c3-145">業務需求： 3 4</span><span class="sxs-lookup"><span data-stu-id="986c3-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="986c3-146">移轉使用率低的應用程式和不在內部部署資料中心的資料。</span><span class="sxs-lookup"><span data-stu-id="986c3-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="986c3-147">業務需求： 5</span><span class="sxs-lookup"><span data-stu-id="986c3-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="986c3-148">**Intune/EMS:** 管理 iOS 及 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="986c3-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="986c3-149">業務需求： 3</span><span class="sxs-lookup"><span data-stu-id="986c3-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="986c3-150">新增暫時伺服器和結束一季處理需求的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="986c3-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="986c3-151">商務需要： 6</span><span class="sxs-lookup"><span data-stu-id="986c3-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="986c3-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="986c3-152">See Also</span></span>

[<span data-ttu-id="986c3-153">Microsoft 雲端中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="986c3-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="986c3-154">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="986c3-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="986c3-155">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="986c3-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


