---
title: 易於存取的圖表-Microsoft Lync 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在技術圖表易於存取的文字版本。
ms.openlocfilehash: a62fb6d1e1ee7fbddb79b0aec4ddafea4b07b4fe
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030597"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="7fee1-103">易於存取的圖表-Microsoft Lync 2013 平台選項</span><span class="sxs-lookup"><span data-stu-id="7fee1-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="7fee1-104">**摘要：** 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在[技術圖表](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)易於存取的文字版本。</span><span class="sxs-lookup"><span data-stu-id="7fee1-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="7fee1-105">此海報說明 business decision makers (Bdm) 和架構設計人員需要瞭解哪些有關 Lync Online (Office 365) 和 Lync Server 部署，並包括：</span><span class="sxs-lookup"><span data-stu-id="7fee1-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="7fee1-106">四個不同的部署選項的比較： Lync Online (Office 365)、 Lync Online/伺服器混合式、 Lync Server 和 Provider-Hosted Lync Server。</span><span class="sxs-lookup"><span data-stu-id="7fee1-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="7fee1-107">部署 Lync 2013 的兩個範例案例。</span><span class="sxs-lookup"><span data-stu-id="7fee1-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="7fee1-108">四個不同的部署的 Lync 2013 平台的比較</span><span class="sxs-lookup"><span data-stu-id="7fee1-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="7fee1-109">比較提供下列項目的每個部署選項的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="7fee1-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="7fee1-110">不同的部署功能的概觀</span><span class="sxs-lookup"><span data-stu-id="7fee1-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="7fee1-111">實作每個部署選項的優點</span><span class="sxs-lookup"><span data-stu-id="7fee1-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="7fee1-112">授權需求</span><span class="sxs-lookup"><span data-stu-id="7fee1-112">Licensing requirements</span></span>
    
- <span data-ttu-id="7fee1-113">必要的架構工作</span><span class="sxs-lookup"><span data-stu-id="7fee1-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="7fee1-114">IT 專業人員負責實作每個部署選項</span><span class="sxs-lookup"><span data-stu-id="7fee1-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="7fee1-115">概觀</span><span class="sxs-lookup"><span data-stu-id="7fee1-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="7fee1-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7fee1-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="7fee1-117">您取得效率，並最佳化的成本與 Office 365 多租用戶計劃。</span><span class="sxs-lookup"><span data-stu-id="7fee1-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="7fee1-118">隨附圖表顯示 Lync Online 與 Azure Active Directory 承租人，以同步處理帳戶名稱和內部部署 Active Directory 網域服務 (AD DS) 環境與 Azure Active Directory 租用戶之間的密碼。</span><span class="sxs-lookup"><span data-stu-id="7fee1-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="7fee1-119">描述的特性與功能：</span><span class="sxs-lookup"><span data-stu-id="7fee1-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7fee1-120">軟體即服務 (SaaS)。</span><span class="sxs-lookup"><span data-stu-id="7fee1-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="7fee1-121">豐富型功能永遠是最新的設定。</span><span class="sxs-lookup"><span data-stu-id="7fee1-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="7fee1-122">包含可搭配其他應用程式的線上帳戶 Azure Active Directory 租用戶。</span><span class="sxs-lookup"><span data-stu-id="7fee1-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="7fee1-123">Directory 整合包括同步處理帳戶名稱和內部部署 Active Directory 網域服務 (AD DS) 環境與 Azure Active Directory 租用戶之間的密碼。</span><span class="sxs-lookup"><span data-stu-id="7fee1-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="7fee1-124">如果單一登入 (SSO) 是需求，必須實作 Active Directory Federation Services (AD FS)。</span><span class="sxs-lookup"><span data-stu-id="7fee1-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="7fee1-125">在網際網路上的用戶端通訊是加密與驗證。</span><span class="sxs-lookup"><span data-stu-id="7fee1-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="7fee1-126">舊版的電話設備公用交換電話網路 (PSTN)，連線是可透過協力廠商提供者。</span><span class="sxs-lookup"><span data-stu-id="7fee1-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7fee1-127">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="7fee1-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="7fee1-128">您可以合併 Office 365 的優點與 Lync 2013 的內部部署。</span><span class="sxs-lookup"><span data-stu-id="7fee1-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="7fee1-129">隨附圖表顯示 Office 365 with Lync Online 其中部分使用者為隸屬於內部部署，有些使用者位於線上。</span><span class="sxs-lookup"><span data-stu-id="7fee1-129">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="7fee1-130">也會顯示內部部署 Edge Server。</span><span class="sxs-lookup"><span data-stu-id="7fee1-130">An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="7fee1-131">描述的特性與功能：</span><span class="sxs-lookup"><span data-stu-id="7fee1-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7fee1-132">某些使用者位於內部部署和部分使用者位於線上使用，但使用者共用相同的 SIP 網域 （例如 contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="7fee1-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="7fee1-133">利用您現有的 Lync Server 2013 基礎結構，包括 PSTN 連線。</span><span class="sxs-lookup"><span data-stu-id="7fee1-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="7fee1-134">新增新的 Lync Online 使用者輕鬆地時不需要 PSTN。</span><span class="sxs-lookup"><span data-stu-id="7fee1-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="7fee1-135">經過一段時間，在您的排程上，從 Lync 內部部署移轉至 Lync Online。</span><span class="sxs-lookup"><span data-stu-id="7fee1-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="7fee1-136">與其他 Office 365 應用程式，包括 Exchange Online 和 SharePoint Online 整合。</span><span class="sxs-lookup"><span data-stu-id="7fee1-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7fee1-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7fee1-137">Lync Server</span></span>

<span data-ttu-id="7fee1-138">在此部署中，您所擁有的所有項目。</span><span class="sxs-lookup"><span data-stu-id="7fee1-138">In this deployment, you own everything.</span></span> <span data-ttu-id="7fee1-139">隨附的圖表會顯示使用者對位於的內部的所在的內部部署 Active Directory 網域服務 (AD DS) 環境與 Lync Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7fee1-139">The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="7fee1-140">描述的特性與功能：</span><span class="sxs-lookup"><span data-stu-id="7fee1-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7fee1-141">容量計劃及調整大小。</span><span class="sxs-lookup"><span data-stu-id="7fee1-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="7fee1-142">伺服器擷取和設定。</span><span class="sxs-lookup"><span data-stu-id="7fee1-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="7fee1-143">部署。</span><span class="sxs-lookup"><span data-stu-id="7fee1-143">Deployment.</span></span>
    
- <span data-ttu-id="7fee1-144">向外延展、 修補和作業。</span><span class="sxs-lookup"><span data-stu-id="7fee1-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="7fee1-145">備份資料。</span><span class="sxs-lookup"><span data-stu-id="7fee1-145">Backing up data.</span></span>
    
- <span data-ttu-id="7fee1-146">維護容錯移轉及災害復原。</span><span class="sxs-lookup"><span data-stu-id="7fee1-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="7fee1-147">將您的 Lync Server 2013 基礎結構連線至 PSTN。</span><span class="sxs-lookup"><span data-stu-id="7fee1-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="7fee1-148">與現有的電話設備，例如專用交換機 (Pbx) 整合。</span><span class="sxs-lookup"><span data-stu-id="7fee1-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7fee1-149">提供者主控的 Lync 伺服器</span><span class="sxs-lookup"><span data-stu-id="7fee1-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="7fee1-150">在此部署中，您的提供者會擁有的所有項目。</span><span class="sxs-lookup"><span data-stu-id="7fee1-150">In this deployment, your provider owns everything.</span></span> <span data-ttu-id="7fee1-151">隨附圖表顯示包含其伺服器和設備連線到內部部署環境的提供者的網路。</span><span class="sxs-lookup"><span data-stu-id="7fee1-151">The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="7fee1-152">描述的特性與功能：</span><span class="sxs-lookup"><span data-stu-id="7fee1-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="7fee1-153">容量計劃及調整大小。</span><span class="sxs-lookup"><span data-stu-id="7fee1-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="7fee1-154">伺服器擷取和設定。</span><span class="sxs-lookup"><span data-stu-id="7fee1-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="7fee1-155">部署。</span><span class="sxs-lookup"><span data-stu-id="7fee1-155">Deployment.</span></span>
    
- <span data-ttu-id="7fee1-156">向外延展、 修補和作業。</span><span class="sxs-lookup"><span data-stu-id="7fee1-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="7fee1-157">備份資料。</span><span class="sxs-lookup"><span data-stu-id="7fee1-157">Backing up data.</span></span>
    
- <span data-ttu-id="7fee1-158">維護容錯移轉及災害復原。</span><span class="sxs-lookup"><span data-stu-id="7fee1-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="7fee1-159">與現有的電話設備，例如專用交換機 (Pbx) 整合。</span><span class="sxs-lookup"><span data-stu-id="7fee1-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="7fee1-160">此外，提供者可以：</span><span class="sxs-lookup"><span data-stu-id="7fee1-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="7fee1-161">與您的內部部署 （實線） 連線自己網路中安裝其伺服器和設備。</span><span class="sxs-lookup"><span data-stu-id="7fee1-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="7fee1-162">在您內部部署 （虛線） 上安裝其伺服器。</span><span class="sxs-lookup"><span data-stu-id="7fee1-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="7fee1-163">實作每個部署選項的優點</span><span class="sxs-lookup"><span data-stu-id="7fee1-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="7fee1-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7fee1-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="7fee1-165">內部部署伺服器或伺服器軟體的任何作業負擔。</span><span class="sxs-lookup"><span data-stu-id="7fee1-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="7fee1-166">Lync Server 2013 作為雲端式服務的通訊功能。</span><span class="sxs-lookup"><span data-stu-id="7fee1-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="7fee1-167">Lync 顯示狀態、 立即訊息、 音訊和視訊通話、 豐富的線上會議，以及多樣的 web 會議功能。</span><span class="sxs-lookup"><span data-stu-id="7fee1-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="7fee1-168">與地理位置分散的組織或主要行動員工使用。</span><span class="sxs-lookup"><span data-stu-id="7fee1-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7fee1-169">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="7fee1-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="7fee1-170">使用 Lync Online 的遠端使用者和與商務合作夥伴的整合。</span><span class="sxs-lookup"><span data-stu-id="7fee1-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="7fee1-171">促進從 Lync 內部部署移轉至 Lync Online。</span><span class="sxs-lookup"><span data-stu-id="7fee1-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="7fee1-172">而不需使用 branch office appliance 支援遠端站台。</span><span class="sxs-lookup"><span data-stu-id="7fee1-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="7fee1-173">新增新的商務收購的 Lync 支援容易。</span><span class="sxs-lookup"><span data-stu-id="7fee1-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7fee1-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7fee1-174">Lync Server</span></span>

- <span data-ttu-id="7fee1-175">私人雲端解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="7fee1-176">高度自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="7fee1-177">具有協力廠商元件，取決於硬體和軟體所 Lync Online 不支援的舊版解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="7fee1-178">防止同步處理的 AD DS 帳戶與 Office 365 的隱私權限制。</span><span class="sxs-lookup"><span data-stu-id="7fee1-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="7fee1-179">想要控制整個平台和解決方案的組織。</span><span class="sxs-lookup"><span data-stu-id="7fee1-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="7fee1-180">與 Lync 企業語音 PBX 取代。</span><span class="sxs-lookup"><span data-stu-id="7fee1-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7fee1-181">提供者主控的 Lync 伺服器</span><span class="sxs-lookup"><span data-stu-id="7fee1-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="7fee1-182">想要讓 Lync Server 功能，但想要將其部署及維護的組織。</span><span class="sxs-lookup"><span data-stu-id="7fee1-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="7fee1-183">提供者為基礎的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="7fee1-184">高度自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="7fee1-185">具有協力廠商元件，取決於硬體和軟體所 Lync Online 不支援的舊版解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="7fee1-186">與 Lync 企業語音 PBX 取代。</span><span class="sxs-lookup"><span data-stu-id="7fee1-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="7fee1-187">授權需求</span><span class="sxs-lookup"><span data-stu-id="7fee1-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="7fee1-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7fee1-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="7fee1-189">訂閱模型。</span><span class="sxs-lookup"><span data-stu-id="7fee1-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7fee1-190">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="7fee1-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="7fee1-191">Office 365-訂閱模型。</span><span class="sxs-lookup"><span data-stu-id="7fee1-191">Office 365 — Subscription model.</span></span> <span data-ttu-id="7fee1-192">不需要額外的授權。</span><span class="sxs-lookup"><span data-stu-id="7fee1-192">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="7fee1-193">內部 — 所有的內部部署授權套用。</span><span class="sxs-lookup"><span data-stu-id="7fee1-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="7fee1-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7fee1-194">Lync Server</span></span>

- <span data-ttu-id="7fee1-195">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="7fee1-195">Server Operating System</span></span>
    
- <span data-ttu-id="7fee1-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7fee1-196">SQL Server</span></span>
    
- <span data-ttu-id="7fee1-197">Lync 2013 Server 授權</span><span class="sxs-lookup"><span data-stu-id="7fee1-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="7fee1-198">Lync 2013 用戶端存取授權</span><span class="sxs-lookup"><span data-stu-id="7fee1-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7fee1-199">提供者主控的 Lync 伺服器</span><span class="sxs-lookup"><span data-stu-id="7fee1-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="7fee1-200">成本根據您的 Lync 解決方案提供者合約。</span><span class="sxs-lookup"><span data-stu-id="7fee1-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="7fee1-201">架構工作</span><span class="sxs-lookup"><span data-stu-id="7fee1-201">Architecture tasks</span></span>

<span data-ttu-id="7fee1-202">此章節將列出每個部署選項的架構工作。</span><span class="sxs-lookup"><span data-stu-id="7fee1-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="7fee1-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7fee1-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="7fee1-204">< Plan and design 目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="7fee1-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="7fee1-205">請確定網路容量和透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結的可用性。</span><span class="sxs-lookup"><span data-stu-id="7fee1-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="7fee1-206">取得第三方 SSL 憑證，以提供 Office 365 服務方案的企業安全性。</span><span class="sxs-lookup"><span data-stu-id="7fee1-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="7fee1-207">決定是否您想要連線到 Office 365 與網際網路通訊協定第 6 版 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="7fee1-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7fee1-208">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="7fee1-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="7fee1-209">除了 Office 365 與內部部署環境的工作：</span><span class="sxs-lookup"><span data-stu-id="7fee1-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="7fee1-210">決定您想要使用多少功能整合內部部署和線上版本的 Exchange Server 和 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="7fee1-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="7fee1-211">如有需要，判斷哪一個 proxy 伺服器裝置將用於從 Office 365 的要求。</span><span class="sxs-lookup"><span data-stu-id="7fee1-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7fee1-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7fee1-212">Lync Server</span></span>

<span data-ttu-id="7fee1-213">設計現有內部部署環境中的 Lync 環境：</span><span class="sxs-lookup"><span data-stu-id="7fee1-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="7fee1-214">管理中心的 Lync 拓撲和分公司。</span><span class="sxs-lookup"><span data-stu-id="7fee1-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="7fee1-215">伺服器硬體，包括虛擬化。</span><span class="sxs-lookup"><span data-stu-id="7fee1-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="7fee1-216">Active Directory 網域服務 (AD DS) 與整合和 DNS。</span><span class="sxs-lookup"><span data-stu-id="7fee1-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="7fee1-217">負載平衡的 Lync 伺服器集區。</span><span class="sxs-lookup"><span data-stu-id="7fee1-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="7fee1-218">容錯移轉及災害復原。</span><span class="sxs-lookup"><span data-stu-id="7fee1-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7fee1-219">提供者主控的 Lync 伺服器</span><span class="sxs-lookup"><span data-stu-id="7fee1-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="7fee1-220">針對雲端型安裝，決定服務提供者的網路連線。</span><span class="sxs-lookup"><span data-stu-id="7fee1-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="7fee1-221">內部部署安裝，判斷您網路上的提供者的 Lync 伺服器的位置。</span><span class="sxs-lookup"><span data-stu-id="7fee1-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="7fee1-222">對於這兩種類型，判斷 AD DS 與 PBX 設備的整合。</span><span class="sxs-lookup"><span data-stu-id="7fee1-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="7fee1-223">IT 專業人員的責任</span><span class="sxs-lookup"><span data-stu-id="7fee1-223">IT Pro responsibilities</span></span>

<span data-ttu-id="7fee1-224">此章節將列出每個部署選項的 IT 專業人員的責任。</span><span class="sxs-lookup"><span data-stu-id="7fee1-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="7fee1-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7fee1-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="7fee1-226">部署及管理 Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="7fee1-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="7fee1-227">實作目錄同步處理計劃。</span><span class="sxs-lookup"><span data-stu-id="7fee1-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="7fee1-228">規劃及實作內部和外部 DNS 記錄和路由。</span><span class="sxs-lookup"><span data-stu-id="7fee1-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="7fee1-229">設定您的 proxy 或防火牆的 Office 365 IP 位址和 URL 需求。</span><span class="sxs-lookup"><span data-stu-id="7fee1-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="7fee1-230">管理使用者帳戶和 Lync Online 設定。</span><span class="sxs-lookup"><span data-stu-id="7fee1-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="7fee1-231">Lync Online/伺服器混合 （分割網域）</span><span class="sxs-lookup"><span data-stu-id="7fee1-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="7fee1-232">除了 Office 365 與內部部署環境的工作：</span><span class="sxs-lookup"><span data-stu-id="7fee1-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="7fee1-233">如有必要，請設定 proxy 伺服器的裝置。</span><span class="sxs-lookup"><span data-stu-id="7fee1-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="7fee1-234">內部部署與 Exchange Server 與 SharePoint online 的版本設定功能整合。</span><span class="sxs-lookup"><span data-stu-id="7fee1-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="7fee1-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="7fee1-235">Lync Server</span></span>

<span data-ttu-id="7fee1-236">在部署和管理 Lync Server 內部部署環境：</span><span class="sxs-lookup"><span data-stu-id="7fee1-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="7fee1-237">佈建伺服器。</span><span class="sxs-lookup"><span data-stu-id="7fee1-237">Provision the servers.</span></span>
    
- <span data-ttu-id="7fee1-238">部署 Lync 拓撲。</span><span class="sxs-lookup"><span data-stu-id="7fee1-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="7fee1-239">更新 Lync server。</span><span class="sxs-lookup"><span data-stu-id="7fee1-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="7fee1-240">新增或移除拓撲伺服器需要根據使用率。</span><span class="sxs-lookup"><span data-stu-id="7fee1-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="7fee1-241">實作容錯移轉及災害復原環境。</span><span class="sxs-lookup"><span data-stu-id="7fee1-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="7fee1-242">提供者主控的 Lync 伺服器</span><span class="sxs-lookup"><span data-stu-id="7fee1-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="7fee1-243">使用提供者：</span><span class="sxs-lookup"><span data-stu-id="7fee1-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="7fee1-244">將 Lync Server 整合到您的網路。</span><span class="sxs-lookup"><span data-stu-id="7fee1-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="7fee1-245">將 Lync Server 整合與其他 Microsoft 產品或自訂的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7fee1-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="7fee1-246">提供者服務層次協議 (SLA) 與嚴格監視該。</span><span class="sxs-lookup"><span data-stu-id="7fee1-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="7fee1-247">部署 Lync 2013 的兩個範例案例</span><span class="sxs-lookup"><span data-stu-id="7fee1-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="7fee1-248">在 Microsoft Azure 中的目錄同步處理元件</span><span class="sxs-lookup"><span data-stu-id="7fee1-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="7fee1-249">部署 Office 365 目錄同步處理元件，在 Azure 中的更快速地是因為部署虛擬機器上隨選的能力。</span><span class="sxs-lookup"><span data-stu-id="7fee1-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="7fee1-250">隨附圖表顯示 Lync Online 與 Azure Active Directory 承租人，以同步處理帳戶名稱和內部部署 Active Directory 環境與 Azure Active Directory 租用戶之間的密碼。</span><span class="sxs-lookup"><span data-stu-id="7fee1-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="7fee1-251">**僅限目錄同步處理伺服器**。</span><span class="sxs-lookup"><span data-stu-id="7fee1-251">**Directory synchronization server only**.</span></span> <span data-ttu-id="7fee1-252">而不是部署在內部部署環境中的 64 位元目錄同步處理伺服器，您可以提供 Azure 中的虛擬機器在網際網路上。</span><span class="sxs-lookup"><span data-stu-id="7fee1-252">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="7fee1-253">**目錄同步處理 + AD FS**。</span><span class="sxs-lookup"><span data-stu-id="7fee1-253">**Directory synchronization + AD FS**.</span></span> <span data-ttu-id="7fee1-254">此選項可讓您支援 Office 365 同盟身分識別 (SSO)，不會新增至您的內部部署基礎結構的硬體。</span><span class="sxs-lookup"><span data-stu-id="7fee1-254">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="7fee1-255">它也提供恢復能力，如果內部部署 Active Directory 環境無法使用。</span><span class="sxs-lookup"><span data-stu-id="7fee1-255">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> <span data-ttu-id="7fee1-256">此選項的功能包括：</span><span class="sxs-lookup"><span data-stu-id="7fee1-256">The features of this option include:</span></span>
  
- <span data-ttu-id="7fee1-257">Azure 虛擬機器以執行目錄整合元件。</span><span class="sxs-lookup"><span data-stu-id="7fee1-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="7fee1-258">AD FS 發佈至 Azure 虛擬機器以執行的 AD FS proxy 透過網際網路。</span><span class="sxs-lookup"><span data-stu-id="7fee1-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="7fee1-259">從任何位置連線的使用者的用戶端驗證流量是由 AD FS 伺服器與 Azure 虛擬機器與部署的 proxy 處理。</span><span class="sxs-lookup"><span data-stu-id="7fee1-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="7fee1-260">Lync 整合 Exchange 與 Office 365 中的 SharePoint</span><span class="sxs-lookup"><span data-stu-id="7fee1-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="7fee1-261">Lync Server 與 Exchange Online 和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7fee1-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="7fee1-262">隨附圖表顯示 Office 365 與 Exchange Online 和 SharePoint Online 連線到內部部署 Lync Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="7fee1-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="7fee1-263">此部署的優點可讓您：</span><span class="sxs-lookup"><span data-stu-id="7fee1-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="7fee1-264">使用 Lync Server 2013 的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="7fee1-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="7fee1-265">利用您現有內部部署電話設備，例如 Pbx。</span><span class="sxs-lookup"><span data-stu-id="7fee1-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="7fee1-266">使用 Exchange Online 電子郵件，卸載內部電子郵件伺服器及儲存的負擔。</span><span class="sxs-lookup"><span data-stu-id="7fee1-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="7fee1-267">使用 SharePoint Online 進行共同作業，卸載的維護負擔內部部署 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7fee1-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="7fee1-268">使用 Lync、 Exchange 和 SharePoint 整合功能，包括整合通訊 (UM) 在 Office 365 中。</span><span class="sxs-lookup"><span data-stu-id="7fee1-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="7fee1-269">Exchange Server 與 Lync Online</span><span class="sxs-lookup"><span data-stu-id="7fee1-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="7fee1-270">隨附的圖表會顯示與 Lync Online 的 Office 365 連線到內部部署 Exchange Server 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="7fee1-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="7fee1-271">此部署的優點可讓您：</span><span class="sxs-lookup"><span data-stu-id="7fee1-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="7fee1-272">利用您現有的 Exchange 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7fee1-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="7fee1-273">使用 Lync Online 的目前狀態、 立即訊息和會議功能。</span><span class="sxs-lookup"><span data-stu-id="7fee1-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

