---
title: Azure PaaS 的混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 摘要： 了解混合式架構與案例的 Microsoft 平台即服務 (PaaS)-以 Azure 中的雲端供應項目。
ms.openlocfilehash: fcc335d0e53463dea4e7ac73c3885b39734db38e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067529"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="dac15-103">Azure PaaS 的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="dac15-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="dac15-104">**摘要：** 了解混合式架構與案例 Microsoft 平台即服務 (PaaS)-以 Azure 中的雲端供應項目。</span><span class="sxs-lookup"><span data-stu-id="dac15-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="dac15-105">組合內部的資料或運算資源與新的或已轉換的應用程式可以善加利用的 Azure PaaS 中執行雲端效能、 可靠性和小數位數及為行動使用者提供較佳的支援。</span><span class="sxs-lookup"><span data-stu-id="dac15-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="dac15-106">Azure PaaS 混合案例結構</span><span class="sxs-lookup"><span data-stu-id="dac15-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="dac15-107">圖 1 顯示在 Azure 中的 Microsoft PaaS 型混合式案例的架構。</span><span class="sxs-lookup"><span data-stu-id="dac15-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="dac15-108">**圖 1: Microsoft PaaS 型混合式案例，在 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="dac15-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中的 Microsoft PaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="dac15-110">每個圖層的架構：</span><span class="sxs-lookup"><span data-stu-id="dac15-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="dac15-111">應用程式和案例</span><span class="sxs-lookup"><span data-stu-id="dac15-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="dac15-112">混合式 PaaS 應用程式會在 Azure 中執行，並使用內部 compute 或儲存資源。</span><span class="sxs-lookup"><span data-stu-id="dac15-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="dac15-113">身分識別</span><span class="sxs-lookup"><span data-stu-id="dac15-113">Identity</span></span>
    
    <span data-ttu-id="dac15-114">包含目錄同步處理或同盟協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="dac15-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="dac15-115">網路</span><span class="sxs-lookup"><span data-stu-id="dac15-115">Network</span></span>
    
    <span data-ttu-id="dac15-116">包含您現有的網際網路管道或與公用對等以 Azure PaaS 的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="dac15-116">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS.</span></span> <span data-ttu-id="dac15-117">您必須包含 Azure PaaS 應用程式存取內部部署 compute 或存放裝置資源的方式。</span><span class="sxs-lookup"><span data-stu-id="dac15-117">You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="dac15-118">內部部署</span><span class="sxs-lookup"><span data-stu-id="dac15-118">On-premises</span></span>
    
    <span data-ttu-id="dac15-119">身分識別與安全性基礎結構和企業營運 (LOB) 應用程式或資料庫伺服器、 Azure PaaS 應用程式可以安全地存取現有行所組成。</span><span class="sxs-lookup"><span data-stu-id="dac15-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="dac15-120">Azure PaaS 混合應用程式</span><span class="sxs-lookup"><span data-stu-id="dac15-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="dac15-121">圖 2 顯示在 Azure 中執行混合式應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="dac15-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="dac15-122">**圖 2: Azure PaaS 型混合式應用程式**</span><span class="sxs-lookup"><span data-stu-id="dac15-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Azure PaaS 型混合式應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="dac15-124">圖 2 內部部署網路主控存放裝置或應用程式伺服器和 DMZ 包含 proxy 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="dac15-124">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server.</span></span> <span data-ttu-id="dac15-125">它會保持連線至 Azure PaaS 服務透過網際網路或 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="dac15-125">It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="dac15-126">組織可以進行計算或存放裝置資源可在 Azure PaaS 混合應用程式：</span><span class="sxs-lookup"><span data-stu-id="dac15-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="dac15-127">主控 DMZ 中的伺服器上的資源。</span><span class="sxs-lookup"><span data-stu-id="dac15-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="dac15-128">主控 DMZ 中的反向 proxy 伺服器，讓已驗證、 輸入、 HTTPS 型要求送至位於內部部署的資源。</span><span class="sxs-lookup"><span data-stu-id="dac15-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="dac15-129">Azure 應用程式可以使用認證：</span><span class="sxs-lookup"><span data-stu-id="dac15-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="dac15-130">Azure AD，可向內部部署身分識別提供者，例如 Active Directory 網域服務 (AD DS) 同步處理。</span><span class="sxs-lookup"><span data-stu-id="dac15-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="dac15-131">協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="dac15-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="dac15-132">範例 Azure PaaS 混合應用程式</span><span class="sxs-lookup"><span data-stu-id="dac15-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="dac15-133">圖 3 顯示在 Azure 中執行範例混合式應用程式。</span><span class="sxs-lookup"><span data-stu-id="dac15-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="dac15-134">**圖 3: 範例 Azure PaaS 型混合式應用程式**</span><span class="sxs-lookup"><span data-stu-id="dac15-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Azure PaaS 型混合式應用程式的範例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="dac15-136">圖 3 中，在內部部署網路主控 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dac15-136">In Figure 3, an on-premises network hosts an LOB app.</span></span> <span data-ttu-id="dac15-137">Azure PaaS 主控自訂的行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="dac15-137">Azure PaaS hosts a custom mobile app.</span></span> <span data-ttu-id="dac15-138">智慧型手機在網際網路上的存取 Azure，將資料要求傳送至內部部署 LOB 應用程式中的自訂行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="dac15-138">A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="dac15-139">這則範例 Azure PaaS 混合應用程式是自訂的行動應用程式上的員工提供最新的連絡人資訊。</span><span class="sxs-lookup"><span data-stu-id="dac15-139">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees.</span></span> <span data-ttu-id="dac15-140">端對端混合式案例所組成：</span><span class="sxs-lookup"><span data-stu-id="dac15-140">The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="dac15-141">智慧型手機應用程式需要驗證，內部部署認證來執行。</span><span class="sxs-lookup"><span data-stu-id="dac15-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="dac15-142">自訂的行動裝置 app，要求從使用者的智慧型手機 app 查詢為基礎的特定員工的相關資訊的 Azure PaaS 中執行。</span><span class="sxs-lookup"><span data-stu-id="dac15-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="dac15-143">驗證自訂的行動應用程式，並將要求轉寄 DMZ 中的反向 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="dac15-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="dac15-144">連絡人的要求，使用者帳戶的權限受到服務 LOB 應用程式伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="dac15-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="dac15-145">因為已與 Azure AD 同步處理內部部署身分識別提供者，自訂的行動應用程式和 LOB 應用程式可以驗證提出要求的使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="dac15-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dac15-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dac15-146">See Also</span></span>

[<span data-ttu-id="dac15-147">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="dac15-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="dac15-148">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="dac15-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

