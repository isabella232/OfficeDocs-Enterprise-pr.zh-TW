---
title: 存取圖表-Microsoft Exchange 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: 本文是圖表的名為 Microsoft Exchange 2013 平台選項，這是圖表的可在技術圖表可存取的文字版本。
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503126"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="c9a7a-103">存取圖表-Microsoft Exchange 2013 平台選項</span><span class="sxs-lookup"><span data-stu-id="c9a7a-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="c9a7a-104">**摘要：** 本文是圖表的名為 Microsoft Exchange 2013 平台選項，這是圖表的可在[技術圖表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)可存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="c9a7a-105">此海報說明 business decision makers (Bdm) 和架構師需要知道什麼有關 Exchange Online 與 Exchange Server 部署並包括：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="c9a7a-106">Exchange 2013 的四個可用的平台選項的比較： Exchange Online (Office 365)、 Exchange 混合式 Exchange 伺服器上部署、 和 Provider-Hosted Exchange。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="c9a7a-107">Exchange 2013 中的三種全新或更新功能的說明。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="c9a7a-108">四個不同的部署的 Exchange 2013 平台的比較</span><span class="sxs-lookup"><span data-stu-id="c9a7a-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="c9a7a-109">比較提供下列區域中的每個部署] 選項的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="c9a7a-110">不同的部署功能的概觀</span><span class="sxs-lookup"><span data-stu-id="c9a7a-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="c9a7a-111">實作每個部署選項的優點</span><span class="sxs-lookup"><span data-stu-id="c9a7a-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="c9a7a-112">授權需求</span><span class="sxs-lookup"><span data-stu-id="c9a7a-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="c9a7a-113">必要的架構工作</span><span class="sxs-lookup"><span data-stu-id="c9a7a-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="c9a7a-114">IT 專業人員責任實作每個部署選項</span><span class="sxs-lookup"><span data-stu-id="c9a7a-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="c9a7a-115">概觀</span><span class="sxs-lookup"><span data-stu-id="c9a7a-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="c9a7a-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="c9a7a-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="c9a7a-117">您的入侵效率並降低與 Office 365 的成本。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="c9a7a-p101">使用 Azure Active Directory 承租人以同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間隨附的圖表顯示 Exchange Online。Active Directory Federation Services (AD FS) 是必要的單一登入。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="c9a7a-120">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="c9a7a-121">伺服器和伺服器軟體的作業是由 Microsoft 處理。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="c9a7a-122">豐富型功能集的 Exchange Server 2013 以雲端架構服務。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="c9a7a-123">永遠保持其最新的最新的功能。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="c9a7a-124">Exchange Online Protection (EOP) 是包含反-垃圾郵件/反惡意程式碼保護。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="c9a7a-125">內建的高可用性與達 99.9%服務層級協議 (SLA)。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="c9a7a-p102">目錄同步作業包括內部部署 Active Directory 網域服務 (AD DS) 與 Azure Active Directory 租用戶之間的密碼。Active Directory Federation Services (AD FS) 是必要的單一登入。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="c9a7a-128">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="c9a7a-128">Exchange Hybrid</span></span>

<span data-ttu-id="c9a7a-129">維護 Exchange Server 內部部署時，您可以運用 Office 365 的優點。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="c9a7a-p103">隨附的圖表顯示 Office 365 與 Exchange Online 其中某些使用者隸屬於內部部署，且某些使用者的主伺服器皆線上。它也會顯示 Azure Active Directory 承租人以同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="c9a7a-132">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="c9a7a-133">某些使用者隸屬於內部部署和某些使用者的主伺服器皆線上，且使用者共用相同的電子郵件地址空間。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="c9a7a-134">如何運用現有的 Exchange Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="c9a7a-135">一段時間，在您的排程上，從 Exchange 內部部署移轉至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="c9a7a-136">與其他 Office 365 應用程式，包括 Lync Online 和 SharePoint Online 的整合。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="c9a7a-137">Exchange Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="c9a7a-137">Exchange Server on-premises</span></span>

<span data-ttu-id="c9a7a-138">您可以設計及管理自己的 Exchange Server 2013 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="c9a7a-139">隨附的圖顯示內部部署 Active Directory 網域服務 (AD DS) 環境如果使用者是所隸屬於內部部署 Exchange Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="c9a7a-140">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="c9a7a-141">最大程度控制項及自訂設定的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="c9a7a-142">在維護工作階段親和性的負載平衡層在沒有相依性。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="c9a7a-143">簡單高可用性和站台恢復使用資料庫可用性群組 (DAGs)。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="c9a7a-144">受管理的可用性，可協助您更好的使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="c9a7a-145">運用現有的硬體和存放區基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="c9a7a-146">提供者主控 Exchange</span><span class="sxs-lookup"><span data-stu-id="c9a7a-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="c9a7a-147">您可以將您的 Exchange Server 工作負載的 Exchange Server 解決方案提供者。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="c9a7a-148">隨附圖 21vianet 且由供應商維護 Exchange Server 環境。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="c9a7a-149">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="c9a7a-150">伺服器和伺服器軟體的作業會處理您的提供者。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="c9a7a-151">規劃、 大小、 縮放比例、 及維護 Exchange Server 基礎結構的委派給您的提供者。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="c9a7a-152">服務維護會處理您的提供者。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="c9a7a-153">Exchange 功能集僅限於提供者所部署的軟體版本。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="c9a7a-154">實作每個部署選項的優點</span><span class="sxs-lookup"><span data-stu-id="c9a7a-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="c9a7a-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="c9a7a-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="c9a7a-156">此部署選項最適合的：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="c9a7a-157">尋找以減少作業成本的內部部署組織的 Exchange 部署。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="c9a7a-158">規劃利用其他 Office 365 方案，例如 SharePoint Online 與 Lync Online 的組織。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="c9a7a-159">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="c9a7a-159">Exchange Hybrid</span></span>

<span data-ttu-id="c9a7a-160">此部署選項最適合的：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="c9a7a-161">協助從 Exchange 內部部署移轉至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="c9a7a-162">不含演變在分公司的基礎結構支援遠端站台。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="c9a7a-163">與子公司需要資料至位於內部部署的跨國企業。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="c9a7a-164">Exchange Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="c9a7a-164">Exchange Server on-premises</span></span>

<span data-ttu-id="c9a7a-165">此部署選項最適合的：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="c9a7a-166">高度自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="c9a7a-167">與協力廠商的項目都取決於硬體及軟體的元件不支援的 Exchange Online 的舊版方案。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="c9a7a-168">組織主旨至需要至位於內部部署資料的資料控管規定。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="c9a7a-169">想要保留控制整個平台和解決方案的組織。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="c9a7a-170">提供者主控 Exchange</span><span class="sxs-lookup"><span data-stu-id="c9a7a-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="c9a7a-171">此部署選項最適合的：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="c9a7a-172">需要 Exchange Server 功能，但想要將其部署及維護外包的組織。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="c9a7a-173">需要個人化的支援選項的組織。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="c9a7a-174">自訂的解決方案，以與提供者所提供的自訂應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="c9a7a-175">與協力廠商的項目都取決於硬體及軟體的元件不支援的 Exchange Online 的舊版方案。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="c9a7a-176">授權需求</span><span class="sxs-lookup"><span data-stu-id="c9a7a-176">License requirements</span></span>

<span data-ttu-id="c9a7a-177">下表詳細說明每個部署選項的授權需求。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="c9a7a-178">**部署選項**</span><span class="sxs-lookup"><span data-stu-id="c9a7a-178">**Deployment option**</span></span>|<span data-ttu-id="c9a7a-179">**授權需求**</span><span class="sxs-lookup"><span data-stu-id="c9a7a-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c9a7a-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="c9a7a-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="c9a7a-181">訂閱模型</span><span class="sxs-lookup"><span data-stu-id="c9a7a-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="c9a7a-182">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="c9a7a-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="c9a7a-183">Office 365-訂閱模型</span><span class="sxs-lookup"><span data-stu-id="c9a7a-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="c9a7a-184">內部-所有內部部署授權套用 （檢閱授權交換伺服器內部部署）</span><span class="sxs-lookup"><span data-stu-id="c9a7a-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="c9a7a-185">混合伺服器授權 \*</span><span class="sxs-lookup"><span data-stu-id="c9a7a-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="c9a7a-186">Exchange Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="c9a7a-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="c9a7a-187">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="c9a7a-187">Server Operating System</span></span> <br/>  <span data-ttu-id="c9a7a-188">Exchange 2013 伺服器授權</span><span class="sxs-lookup"><span data-stu-id="c9a7a-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="c9a7a-189">Exchange 2013 用戶端存取授權</span><span class="sxs-lookup"><span data-stu-id="c9a7a-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="c9a7a-190">提供者主控 Exchange</span><span class="sxs-lookup"><span data-stu-id="c9a7a-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="c9a7a-191">成本根據與提供者協議</span><span class="sxs-lookup"><span data-stu-id="c9a7a-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="c9a7a-192">架構工作</span><span class="sxs-lookup"><span data-stu-id="c9a7a-192">Architecture tasks</span></span>

<span data-ttu-id="c9a7a-193">本節列出每個部署選項的架構工作。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="c9a7a-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="c9a7a-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="c9a7a-195">規劃及設計目錄同步作業。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="c9a7a-196">確定網路容量和透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結的連線。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="c9a7a-197">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="c9a7a-197">Exchange Hybrid</span></span>

<span data-ttu-id="c9a7a-198">除了 Office 365 與內部部署環境的架構工作：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="c9a7a-199">決定是否要提供單一登入經驗。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="c9a7a-200">決定是否要透過內部部署組織或 Exchange Online Protection 的輸入的網際網路郵件路由傳送。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="c9a7a-201">Exchange Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="c9a7a-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="c9a7a-202">設計 Exchange 拓撲。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="c9a7a-203">規劃伺服器硬體的容量。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="c9a7a-204">設計郵件路由拓撲。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="c9a7a-205">設計負載平衡的用戶端存取伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="c9a7a-206">規劃高可用性使用資料庫可用性群組。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="c9a7a-207">提供者主控 Exchange</span><span class="sxs-lookup"><span data-stu-id="c9a7a-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="c9a7a-208">確定網路容量和可用性透過防火牆、 proxy 伺服器、 閘道，且跨 WAN 連結可至提供者。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="c9a7a-209">IT 專業人員的責任</span><span class="sxs-lookup"><span data-stu-id="c9a7a-209">IT Pro responsibilities</span></span>

<span data-ttu-id="c9a7a-210">本節列出每個部署選項以 IT 專業人員的責任。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="c9a7a-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="c9a7a-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="c9a7a-212">實作目錄同步處理計劃。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="c9a7a-213">規劃及實作內部和外部 DNS 記錄和路由。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="c9a7a-214">設定 proxy 伺服器或防火牆的 Office 365 IP 位址及 URL 需求。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="c9a7a-215">管理使用者帳戶和 Exchange Online 的設定。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="c9a7a-216">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="c9a7a-216">Exchange Hybrid</span></span>

<span data-ttu-id="c9a7a-217">除了 Office 365 與內部部署環境的 IT 專業人員的責任：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="c9a7a-218">設定單一登入的 Active Directory Federation Services (AD FS) 上，（若有需要）。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="c9a7a-219">設定 Exchange 2013 伺服器與 Office 365 之間的安全通訊的 Exchange 憑證。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="c9a7a-220">設定 DNS 記錄的所需的內送網際網路郵件路徑。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="c9a7a-221">Exchange Server 內部部署</span><span class="sxs-lookup"><span data-stu-id="c9a7a-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="c9a7a-222">設定 Exchange 服務所需的憑證。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="c9a7a-223">佈建伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-223">Provision the servers.</span></span>
    
- <span data-ttu-id="c9a7a-224">實作 Exchange 郵件路由拓撲。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="c9a7a-225">實作資料庫可用性群組。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="c9a7a-226">更新及維護 Exchange 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="c9a7a-227">根據使用率、 新增或移除伺服器所需。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="c9a7a-228">提供者主控 Exchange</span><span class="sxs-lookup"><span data-stu-id="c9a7a-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="c9a7a-229">提供者的責任包括：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="c9a7a-230">系統及服務維護。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="c9a7a-231">功能部署。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="c9a7a-232">資料保護和嚴重損壞修復。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="c9a7a-233">在組織中的 IT 人員責任包括建立和管理使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="c9a7a-234">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c9a7a-234">More information</span></span>

<span data-ttu-id="c9a7a-235">若要深入了解 Exchange Online (Office 365)，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="c9a7a-236">Exchange Online 服務說明</span><span class="sxs-lookup"><span data-stu-id="c9a7a-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="c9a7a-237">TechNet 上的 Exchange Online 文件庫</span><span class="sxs-lookup"><span data-stu-id="c9a7a-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="c9a7a-238">Exchange Online 的入口網站</span><span class="sxs-lookup"><span data-stu-id="c9a7a-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="c9a7a-239">若要深入了解 Exchange 的混合，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="c9a7a-p104">[Exchange 2013 混合部署](https://aka.ms/ExchangeHybrid)。您應該注意的混合伺服器授權為只需要在下列情況： Exchange 2010 組織與 Exchange 2013 混合式伺服器和 Exchange 2007 組織與 Exchange 2013 或 Exchange 2010 混合伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="c9a7a-242">Office 365 登入</span><span class="sxs-lookup"><span data-stu-id="c9a7a-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="c9a7a-243">若要深入了解 Exchange Server 內部部署，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="c9a7a-244">TechNet 上的 Exchange Server 2013 文件庫</span><span class="sxs-lookup"><span data-stu-id="c9a7a-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="c9a7a-245">Exchange Server 2013 入口網站</span><span class="sxs-lookup"><span data-stu-id="c9a7a-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="c9a7a-246">Exchange Server 2013 架構</span><span class="sxs-lookup"><span data-stu-id="c9a7a-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="c9a7a-247">若要深入了解 Provider-Hosted Exchange，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="c9a7a-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="c9a7a-248">Exchange Server 2013 主控與多重租用解決方案和指引</span><span class="sxs-lookup"><span data-stu-id="c9a7a-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="c9a7a-249">Exchange 2013 中的三種全新或更新功能的說明</span><span class="sxs-lookup"><span data-stu-id="c9a7a-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="c9a7a-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="c9a7a-250">Exchange Online Protection</span></span>

<span data-ttu-id="c9a7a-p105">Exchange Online Protection (EOP) 提供任何部署的反垃圾郵件和反惡意程式碼的保護提供一層的部署跨資料中心的通用網路的保護功能。這有助於您簡化的訊息環境的管理。EOP 隨附於 Exchange Online 訂閱，但您也可以運用它混合式和內部部署。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="c9a7a-254">隨附的圖表說明 Exchange Online、 Exchange 混合部署和部署的 Exchange 內部部署中通用網路包含 EOP 圖層。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="c9a7a-255">Exchange Server 部署助理</span><span class="sxs-lookup"><span data-stu-id="c9a7a-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="c9a7a-p106">Exchange Server 部署助理是 web 式工具，詢問您目前的環境的幾個問題，然後再產生自訂逐步檢查清單可協助您部署 Exchange Server 不同類型的案例。是否從舊版 Exchange 至 Exchange 2013 的升級、 移轉至 Exchange Online 或規劃混合式基礎結構 Exchange Server 部署助理會建立自訂的部署檢查表您的案例。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="c9a7a-258">隨附的螢幕擷取畫面顯示使用 Exchange Server 部署助理建立範例檢查清單。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="c9a7a-259">與 Lync 和 SharePoint 整合</span><span class="sxs-lookup"><span data-stu-id="c9a7a-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="c9a7a-p107">Exchange Server 2013 包含整合 Lync Server 2013 與 SharePoint Server 2013 的許多功能。在一起，這些產品提供一組豐富型功能並提升整個組織共同作業。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="c9a7a-262">隨附的圖表顯示伺服器對伺服器驗證海報並包含海報的連結。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="c9a7a-263">封存、 保留和 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="c9a7a-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="c9a7a-264">網站信箱</span><span class="sxs-lookup"><span data-stu-id="c9a7a-264">Site mailboxes</span></span>
    
- <span data-ttu-id="c9a7a-265">整合聯絡資料儲存</span><span class="sxs-lookup"><span data-stu-id="c9a7a-265">Unified contact store</span></span>
    
- <span data-ttu-id="c9a7a-266">高解析度的使用者相片</span><span class="sxs-lookup"><span data-stu-id="c9a7a-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="c9a7a-267">Outlook 和 Outlook Web App 中的 Lync 顯示狀態</span><span class="sxs-lookup"><span data-stu-id="c9a7a-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="c9a7a-268">伺服器對伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="c9a7a-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="c9a7a-269">語音信箱</span><span class="sxs-lookup"><span data-stu-id="c9a7a-269">Voicemail</span></span>
    
- <span data-ttu-id="c9a7a-270">會議錄製</span><span class="sxs-lookup"><span data-stu-id="c9a7a-270">Meeting recordings</span></span>
    
- <span data-ttu-id="c9a7a-271">Exchange 工作同步處理</span><span class="sxs-lookup"><span data-stu-id="c9a7a-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="c9a7a-272">隨附的圖表顯示 Exchange Server 2013 SP1 架構海報 （英文） 並包含海報的連結。</span><span class="sxs-lookup"><span data-stu-id="c9a7a-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

