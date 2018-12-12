---
title: 存取圖表-Microsoft Lync 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在技術圖表可存取的文字版本。
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504086"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="f388c-103">存取圖表-Microsoft Lync 2013 平台選項</span><span class="sxs-lookup"><span data-stu-id="f388c-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="f388c-104">**摘要：** 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在[技術圖表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)可存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="f388c-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="f388c-105">此海報說明 business decision makers (Bdm) 和架構師需要知道什麼有關 Lync Online (Office 365) 和 Lync Server 部署並包括：</span><span class="sxs-lookup"><span data-stu-id="f388c-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="f388c-106">四個不同的部署選項的比較： Lync Online (Office 365)、 Lync Online/伺服器混合 Lync Server 和 Provider-Hosted Lync Server。</span><span class="sxs-lookup"><span data-stu-id="f388c-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="f388c-107">部署 Lync 2013 的兩個範例案例。</span><span class="sxs-lookup"><span data-stu-id="f388c-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="f388c-108">四個不同的部署的 Lync 2013 平台的比較</span><span class="sxs-lookup"><span data-stu-id="f388c-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="f388c-109">比較提供下列區域中的每個部署] 選項的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="f388c-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="f388c-110">不同的部署功能的概觀</span><span class="sxs-lookup"><span data-stu-id="f388c-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="f388c-111">實作每個部署選項的優點</span><span class="sxs-lookup"><span data-stu-id="f388c-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="f388c-112">授權需求</span><span class="sxs-lookup"><span data-stu-id="f388c-112">Licensing requirements</span></span>
    
- <span data-ttu-id="f388c-113">必要的架構工作</span><span class="sxs-lookup"><span data-stu-id="f388c-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="f388c-114">IT 專業人員責任實作每個部署選項</span><span class="sxs-lookup"><span data-stu-id="f388c-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="f388c-115">概觀</span><span class="sxs-lookup"><span data-stu-id="f388c-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="f388c-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f388c-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="f388c-117">您的入侵效率和最佳化的 Office 365 multitenant 計劃的成本。</span><span class="sxs-lookup"><span data-stu-id="f388c-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="f388c-118">隨附圖 Lync Online 搭配 Azure Active Directory 承租人，以同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間。</span><span class="sxs-lookup"><span data-stu-id="f388c-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="f388c-119">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="f388c-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f388c-120">軟體即服務 (SaaS)。</span><span class="sxs-lookup"><span data-stu-id="f388c-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="f388c-121">豐富型功能永遠是最新的設定。</span><span class="sxs-lookup"><span data-stu-id="f388c-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="f388c-122">包括可與其他應用程式的線上帳戶的 Azure Active Directory 租用戶。</span><span class="sxs-lookup"><span data-stu-id="f388c-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="f388c-123">目錄整合包括同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間。</span><span class="sxs-lookup"><span data-stu-id="f388c-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="f388c-124">如果單一登入 (SSO) 是需求，就必須實作 Active Directory Federation Services (AD FS)。</span><span class="sxs-lookup"><span data-stu-id="f388c-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="f388c-125">透過網際網路的用戶端通訊會加密及驗證。</span><span class="sxs-lookup"><span data-stu-id="f388c-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="f388c-126">舊版的電話設備公用交換電話網路 (PSTN)、 連線是可透過協力廠商提供者。</span><span class="sxs-lookup"><span data-stu-id="f388c-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="f388c-127">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="f388c-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="f388c-128">您可以結合 Office 365 的優點與 Lync 2013 的內部部署。</span><span class="sxs-lookup"><span data-stu-id="f388c-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="f388c-p101">隨附的圖表顯示 Office 365 with Lync Online 其中某些使用者所隸屬於內部部署和某些使用者的主伺服器皆線上。也會顯示內部部署 Edge Server。</span><span class="sxs-lookup"><span data-stu-id="f388c-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="f388c-131">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="f388c-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f388c-132">某些使用者位於內部部署與某些使用者的主伺服器皆線上，但使用者都共用同一個 SIP 網域 （例如 contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="f388c-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="f388c-133">利用您現有的 Lync Server 2013 基礎結構，包括 PSTN 連線。</span><span class="sxs-lookup"><span data-stu-id="f388c-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="f388c-134">新增新的 Lync Online 使用者輕鬆時不需要 PSTN。</span><span class="sxs-lookup"><span data-stu-id="f388c-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="f388c-135">＜ migrate from Lync 內部 Lync online 一段時間，在您的排程。</span><span class="sxs-lookup"><span data-stu-id="f388c-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="f388c-136">與其他 Office 365 應用程式，包括 Exchange Online 和 SharePoint Online 的整合。</span><span class="sxs-lookup"><span data-stu-id="f388c-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="f388c-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-137">Lync Server</span></span>

<span data-ttu-id="f388c-p102">在本部署中，擁有每個項目。隨附的圖顯示內部部署 Active Directory 網域服務 (AD DS) 環境如果使用者是所隸屬於內部部署 Lync Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="f388c-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="f388c-140">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="f388c-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f388c-141">容量規劃及調整大小。</span><span class="sxs-lookup"><span data-stu-id="f388c-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="f388c-142">伺服器擷取及安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f388c-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="f388c-143">部署。</span><span class="sxs-lookup"><span data-stu-id="f388c-143">Deployment.</span></span>
    
- <span data-ttu-id="f388c-144">向外延展、 修補及作業。</span><span class="sxs-lookup"><span data-stu-id="f388c-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="f388c-145">備份資料。</span><span class="sxs-lookup"><span data-stu-id="f388c-145">Backing up data.</span></span>
    
- <span data-ttu-id="f388c-146">維護容錯移轉及災害復原。</span><span class="sxs-lookup"><span data-stu-id="f388c-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="f388c-147">將您的 Lync Server 2013 基礎結構連線至 PSTN。</span><span class="sxs-lookup"><span data-stu-id="f388c-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="f388c-148">與現有的電話設備，例如專用交換機 (Pbx) 整合。</span><span class="sxs-lookup"><span data-stu-id="f388c-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="f388c-149">提供者主控 Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="f388c-p103">在本部署中，您的提供者擁有每個項目。隨附的圖表顯示包含其伺服器和設備連線至內部部署環境的提供者的網路。</span><span class="sxs-lookup"><span data-stu-id="f388c-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="f388c-152">功能和功用描述：</span><span class="sxs-lookup"><span data-stu-id="f388c-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f388c-153">容量規劃及調整大小。</span><span class="sxs-lookup"><span data-stu-id="f388c-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="f388c-154">伺服器擷取及安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f388c-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="f388c-155">部署。</span><span class="sxs-lookup"><span data-stu-id="f388c-155">Deployment.</span></span>
    
- <span data-ttu-id="f388c-156">向外延展、 修補及作業。</span><span class="sxs-lookup"><span data-stu-id="f388c-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="f388c-157">備份資料。</span><span class="sxs-lookup"><span data-stu-id="f388c-157">Backing up data.</span></span>
    
- <span data-ttu-id="f388c-158">維護容錯移轉及災害復原。</span><span class="sxs-lookup"><span data-stu-id="f388c-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="f388c-159">與現有的電話設備，例如專用交換機 (Pbx) 整合。</span><span class="sxs-lookup"><span data-stu-id="f388c-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="f388c-160">此外，可以提供者：</span><span class="sxs-lookup"><span data-stu-id="f388c-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="f388c-161">在您內部部署 （實線） 的連線與他們自己網路安裝其伺服器和設備。</span><span class="sxs-lookup"><span data-stu-id="f388c-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="f388c-162">在您內部部署 （虛線） 安裝其伺服器。</span><span class="sxs-lookup"><span data-stu-id="f388c-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="f388c-163">實作每個部署選項的優點</span><span class="sxs-lookup"><span data-stu-id="f388c-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="f388c-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f388c-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="f388c-165">在內部伺服器或伺服器軟體的任何作業負擔。</span><span class="sxs-lookup"><span data-stu-id="f388c-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="f388c-166">Lync Server 2013 以雲端架構服務通訊功能。</span><span class="sxs-lookup"><span data-stu-id="f388c-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="f388c-167">Lync 顯示狀態、 立即訊息、 音訊和視訊呼叫豐富的線上會議和廣泛的 web 會議功能。</span><span class="sxs-lookup"><span data-stu-id="f388c-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="f388c-168">依地理位置分散的組織或與主要行動裝置的員工使用。</span><span class="sxs-lookup"><span data-stu-id="f388c-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="f388c-169">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="f388c-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="f388c-170">使用 Lync Online 的遠端使用者與業務合作夥伴與整合。</span><span class="sxs-lookup"><span data-stu-id="f388c-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="f388c-171">促進 Lync 內部將移轉至 Lync Online。</span><span class="sxs-lookup"><span data-stu-id="f388c-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="f388c-172">不使用 branch office appliance 支援遠端站台。</span><span class="sxs-lookup"><span data-stu-id="f388c-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="f388c-173">簡化的新增的新營業併 Lync 支援。</span><span class="sxs-lookup"><span data-stu-id="f388c-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="f388c-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-174">Lync Server</span></span>

- <span data-ttu-id="f388c-175">私人雲端解決方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="f388c-176">高度自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="f388c-177">與協力廠商的項目都取決於硬體及軟體的元件不支援的 Lync Online 的舊版方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="f388c-178">隱私權導致無法同步處理的 AD DS 帳戶與 Office 365 的限制。</span><span class="sxs-lookup"><span data-stu-id="f388c-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="f388c-179">想要控制整個平台和解決方案的組織。</span><span class="sxs-lookup"><span data-stu-id="f388c-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="f388c-180">與 Lync Enterprise Voice PBX 替換。</span><span class="sxs-lookup"><span data-stu-id="f388c-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="f388c-181">提供者主控 Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="f388c-182">需要 Lync Server 功能，但想要將其部署及維護的組織。</span><span class="sxs-lookup"><span data-stu-id="f388c-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="f388c-183">提供者為基礎的方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="f388c-184">高度自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="f388c-185">與協力廠商的項目都取決於硬體及軟體的元件不支援的 Lync Online 的舊版方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="f388c-186">與 Lync Enterprise Voice PBX 替換。</span><span class="sxs-lookup"><span data-stu-id="f388c-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="f388c-187">授權需求</span><span class="sxs-lookup"><span data-stu-id="f388c-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="f388c-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f388c-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="f388c-189">訂閱模型。</span><span class="sxs-lookup"><span data-stu-id="f388c-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="f388c-190">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="f388c-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="f388c-p104">Office 365-訂閱模型。無需額外的授權。</span><span class="sxs-lookup"><span data-stu-id="f388c-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="f388c-193">內部 — 所有的內部部署授權套用。</span><span class="sxs-lookup"><span data-stu-id="f388c-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="f388c-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-194">Lync Server</span></span>

- <span data-ttu-id="f388c-195">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="f388c-195">Server Operating System</span></span>
    
- <span data-ttu-id="f388c-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f388c-196">SQL Server</span></span>
    
- <span data-ttu-id="f388c-197">Lync 2013 Server 授權</span><span class="sxs-lookup"><span data-stu-id="f388c-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="f388c-198">Lync 2013 用戶端存取授權</span><span class="sxs-lookup"><span data-stu-id="f388c-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="f388c-199">提供者主控 Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="f388c-200">成本根據 Lync 解決方案提供者合約。</span><span class="sxs-lookup"><span data-stu-id="f388c-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="f388c-201">架構工作</span><span class="sxs-lookup"><span data-stu-id="f388c-201">Architecture tasks</span></span>

<span data-ttu-id="f388c-202">本節列出每個部署選項的架構工作。</span><span class="sxs-lookup"><span data-stu-id="f388c-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="f388c-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f388c-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="f388c-204">規劃與設計目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="f388c-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="f388c-205">確定網路容量和可用性透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結。</span><span class="sxs-lookup"><span data-stu-id="f388c-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="f388c-206">取得 Office 365 服務方案提供企業級的安全性的第三方 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="f388c-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="f388c-207">決定您是否要連線至 Office 365 與網際網路通訊協定第 6 版 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="f388c-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="f388c-208">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="f388c-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="f388c-209">除了 Office 365 與內部部署環境的工作：</span><span class="sxs-lookup"><span data-stu-id="f388c-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="f388c-210">決定您想要使用多少功能整合在內部部署與線上版本的 Exchange Server 與 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="f388c-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="f388c-211">如有需要，決定哪一個 proxy 伺服器裝置將用於 Office 365 的要求。</span><span class="sxs-lookup"><span data-stu-id="f388c-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="f388c-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-212">Lync Server</span></span>

<span data-ttu-id="f388c-213">設計現有內部部署環境中的 Lync 環境：</span><span class="sxs-lookup"><span data-stu-id="f388c-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="f388c-214">管理中心的 Lync 拓撲和分公司。</span><span class="sxs-lookup"><span data-stu-id="f388c-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="f388c-215">伺服器硬體，包括虛擬化。</span><span class="sxs-lookup"><span data-stu-id="f388c-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="f388c-216">Active Directory 網域服務 (AD DS) 與整合和 DNS。</span><span class="sxs-lookup"><span data-stu-id="f388c-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="f388c-217">負載平衡的 Lync server 集區。</span><span class="sxs-lookup"><span data-stu-id="f388c-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="f388c-218">容錯移轉及災害復原。</span><span class="sxs-lookup"><span data-stu-id="f388c-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="f388c-219">提供者主控 Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="f388c-220">雲端型安裝，判斷服務提供者的網路連線。</span><span class="sxs-lookup"><span data-stu-id="f388c-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="f388c-221">內部部署安裝，判斷您的網路上的提供者的 Lync 伺服器的位置。</span><span class="sxs-lookup"><span data-stu-id="f388c-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="f388c-222">針對這兩種類型，決定 AD DS 與 PBX 設備的整合。</span><span class="sxs-lookup"><span data-stu-id="f388c-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="f388c-223">IT 專業人員的責任</span><span class="sxs-lookup"><span data-stu-id="f388c-223">IT Pro responsibilities</span></span>

<span data-ttu-id="f388c-224">本節列出每個部署選項以 IT 專業人員的責任。</span><span class="sxs-lookup"><span data-stu-id="f388c-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="f388c-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f388c-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="f388c-226">部署及管理 Lync Online (Office 365)：</span><span class="sxs-lookup"><span data-stu-id="f388c-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="f388c-227">實作目錄同步處理計劃。</span><span class="sxs-lookup"><span data-stu-id="f388c-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="f388c-228">規劃及實作內部和外部 DNS 記錄和路由。</span><span class="sxs-lookup"><span data-stu-id="f388c-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="f388c-229">設定 proxy 或防火牆的 Office 365 IP 位址及 URL 需求。</span><span class="sxs-lookup"><span data-stu-id="f388c-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="f388c-230">管理使用者帳戶和 Lync Online 設定。</span><span class="sxs-lookup"><span data-stu-id="f388c-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="f388c-231">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="f388c-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="f388c-232">除了 Office 365 與內部部署環境的工作：</span><span class="sxs-lookup"><span data-stu-id="f388c-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="f388c-233">視需要設定 proxy 伺服器裝置。</span><span class="sxs-lookup"><span data-stu-id="f388c-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="f388c-234">設定內部部署與線上版本的 Exchange Server 與 SharePoint 的功能整合。</span><span class="sxs-lookup"><span data-stu-id="f388c-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="f388c-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-235">Lync Server</span></span>

<span data-ttu-id="f388c-236">部署及管理 Lync Server 的內部部署環境中：</span><span class="sxs-lookup"><span data-stu-id="f388c-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="f388c-237">佈建伺服器。</span><span class="sxs-lookup"><span data-stu-id="f388c-237">Provision the servers.</span></span>
    
- <span data-ttu-id="f388c-238">部署 Lync 拓撲。</span><span class="sxs-lookup"><span data-stu-id="f388c-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="f388c-239">Lync 伺服器更新。</span><span class="sxs-lookup"><span data-stu-id="f388c-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="f388c-240">新增或移除拓撲伺服器所需根據使用率。</span><span class="sxs-lookup"><span data-stu-id="f388c-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="f388c-241">實作容錯移轉和嚴重損壞修復環境。</span><span class="sxs-lookup"><span data-stu-id="f388c-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="f388c-242">提供者主控 Lync Server</span><span class="sxs-lookup"><span data-stu-id="f388c-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="f388c-243">使用之提供者：</span><span class="sxs-lookup"><span data-stu-id="f388c-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="f388c-244">將 Lync Server 整合到您的網路。</span><span class="sxs-lookup"><span data-stu-id="f388c-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="f388c-245">將 Lync Server 整合與其他 Microsoft 產品或自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="f388c-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="f388c-246">提供者服務層次協議 (SLA) 具有嚴格監視該。</span><span class="sxs-lookup"><span data-stu-id="f388c-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="f388c-247">部署 Lync 2013 的兩個範例案例</span><span class="sxs-lookup"><span data-stu-id="f388c-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="f388c-248">Microsoft Azure 中的目錄同步處理元件</span><span class="sxs-lookup"><span data-stu-id="f388c-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="f388c-249">部署在 Azure 中的 Office 365 目錄同步處理元件能夠部署虛擬機器隨選因為會較快。</span><span class="sxs-lookup"><span data-stu-id="f388c-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="f388c-250">隨附圖 Lync Online 搭配 Azure Active Directory 承租人，以同步處理帳戶名稱和密碼的內部部署 Active Directory 環境及 Azure Active Directory 租用戶之間。</span><span class="sxs-lookup"><span data-stu-id="f388c-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="f388c-p105">**僅限目錄同步處理伺服器**。而不是部署在內部部署環境中的 64 位元目錄同步處理伺服器，您可透過網際網路提供在 Azure 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="f388c-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="f388c-p106">**目錄同步作業 + AD FS**。此選項可讓您不透過新增至您的內部部署基礎結構的硬體支援 Office 365 同盟身分識別 (SSO)。如果內部部署 Active Directory 環境無法使用也提供恢復能力。此選項的功能包括：</span><span class="sxs-lookup"><span data-stu-id="f388c-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="f388c-257">以 Azure 虛擬機器執行目錄整合元件。</span><span class="sxs-lookup"><span data-stu-id="f388c-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="f388c-258">AD FS 發佈至網際網路 Azure 虛擬機器時所執行的 AD FS proxy 透過。</span><span class="sxs-lookup"><span data-stu-id="f388c-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="f388c-259">用戶端驗證流量的連接的任何位置的使用者會處理的 AD FS 伺服器和部署為 「 Azure 虛擬機器的 proxy。</span><span class="sxs-lookup"><span data-stu-id="f388c-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="f388c-260">與 Exchange 和 SharePoint Office 365 中的 Lync 整合</span><span class="sxs-lookup"><span data-stu-id="f388c-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="f388c-261">Lync Server 與 Exchange Online 和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f388c-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="f388c-262">隨附圖與 Exchange Online 和 SharePoint Online 的 Office 365 連線至內部部署 Lync Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="f388c-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="f388c-263">此部署的優點可讓您：</span><span class="sxs-lookup"><span data-stu-id="f388c-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="f388c-264">使用 Lync Server 2013 的完整的功能集。</span><span class="sxs-lookup"><span data-stu-id="f388c-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="f388c-265">利用您現有的內部電話設備，例如 Pbx。</span><span class="sxs-lookup"><span data-stu-id="f388c-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="f388c-266">使用 Exchange Online 電子郵件、 卸載內部電子郵件伺服器及儲存的負擔。</span><span class="sxs-lookup"><span data-stu-id="f388c-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="f388c-267">使用 SharePoint Online 進行共同作業、 卸載的維護負擔內部部署 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f388c-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="f388c-268">使用 Lync、 Exchange 和 SharePoint 整合功能，包括整合通訊 (UM) Office 365 中。</span><span class="sxs-lookup"><span data-stu-id="f388c-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="f388c-269">使用 Lync Online 的 Exchange Server</span><span class="sxs-lookup"><span data-stu-id="f388c-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="f388c-270">隨附圖與 Lync Online 的 Office 365 連線至內部部署 Exchange 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="f388c-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="f388c-271">此部署的優點可讓您：</span><span class="sxs-lookup"><span data-stu-id="f388c-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="f388c-272">運用現有的 Exchange 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="f388c-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="f388c-273">使用 Lync Online 的目前狀態、 im 和會議功能。</span><span class="sxs-lookup"><span data-stu-id="f388c-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

