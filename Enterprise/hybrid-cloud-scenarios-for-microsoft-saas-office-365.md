---
title: Microsoft SaaS (Office 365) 混合式雲端案例
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 摘要： 瞭解混合式架構與案例的 Microsoft 的 SaaS 型雲端供應項目 (Office 365)。
ms.openlocfilehash: 84092fe419ab31fca7763f434e328eb855d46835
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067219"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="d6bdb-103">Microsoft SaaS (Office 365) 混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="d6bdb-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="d6bdb-104">**摘要：** 了解混合式架構與案例的 Microsoft 的 SaaS 型雲端供應項目 (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="d6bdb-105">合併與與其對應雲端移轉或長期的整合策略的一部分的 Office 365 中的內部部署的 Exchange、 SharePoint 或商務用 Skype。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="d6bdb-106">Microsoft SaaS 混合案例結構</span><span class="sxs-lookup"><span data-stu-id="d6bdb-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="d6bdb-107">圖 1 顯示 Office 365 的 Microsoft Iaas 型混合式案例的架構。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="d6bdb-108">**圖 1: Office 365 的 Microsoft Iaas 型混合式案例**</span><span class="sxs-lookup"><span data-stu-id="d6bdb-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Office 365 的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="d6bdb-110">每個圖層的架構：</span><span class="sxs-lookup"><span data-stu-id="d6bdb-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="d6bdb-111">應用程式和案例</span><span class="sxs-lookup"><span data-stu-id="d6bdb-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="d6bdb-112">有各種 SaaS 為基礎的混合式案例，對齊繞 Office Server 產品和其 Office 365 對應項目：</span><span class="sxs-lookup"><span data-stu-id="d6bdb-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="d6bdb-113">Exchange 伺服器組合與 Exchange Online （Exchange Server 混合式）</span><span class="sxs-lookup"><span data-stu-id="d6bdb-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="d6bdb-114">Skype 商務 Server 結合 Skype 商務線上和新的雲端 PBX 與雲端連接器 Edition 案例</span><span class="sxs-lookup"><span data-stu-id="d6bdb-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="d6bdb-115">SharePoint Server 2019、 SharePoint Server 2016 或 SharePoint Server 2013 結合使用 SharePoint Online （多個案例）</span><span class="sxs-lookup"><span data-stu-id="d6bdb-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="d6bdb-116">另外還有 Exchange Online 與 Skype Business Server 內部部署，跨產品混合式案例。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="d6bdb-117">身分識別</span><span class="sxs-lookup"><span data-stu-id="d6bdb-117">Identity</span></span>
    
    <span data-ttu-id="d6bdb-118">可以包含您內部部署 Active Directory 網域服務 (AD DS) 與目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="d6bdb-119">或者，您可以設定 Azure AD 以使用協力廠商身分識別提供者同盟。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="d6bdb-120">網路</span><span class="sxs-lookup"><span data-stu-id="d6bdb-120">Network</span></span>
    
    <span data-ttu-id="d6bdb-121">與 Microsoft Office 365 或 Dynamics 365 對等包含您現有的網際網路管道或 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="d6bdb-122">內部部署</span><span class="sxs-lookup"><span data-stu-id="d6bdb-122">On-premises</span></span>
    
    <span data-ttu-id="d6bdb-123">可以包含現有的伺服器的 Exchange、 SharePoint 和 Skype for Business，應該更新至最新的版本。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-123">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions.</span></span> <span data-ttu-id="d6bdb-124">您可以結合其與 Office 365 與對應的混合式案例。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-124">You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="d6bdb-125">設定您的 Office 365 開發/測試環境，請參閱[Office 365 測試實驗室指南](cloud-adoption-test-lab-guides-tlgs.md)。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="d6bdb-126">混合式商務用 Skype</span><span class="sxs-lookup"><span data-stu-id="d6bdb-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="d6bdb-127">混合式商務用 Skype 可讓您結合現有內部部署與 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="d6bdb-128">某些使用者為隸屬於內部部署和部分使用者位於線上使用，但使用者共用相同的工作階段初始通訊協定 (SIP) 網域，例如 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="d6bdb-129">您可以使用此混合式組態移轉從內部部署到 Office 365 一段時間，在您的排程。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="d6bdb-130">商務用 Skype 也可以與[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)整合。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="d6bdb-131">**圖 2: 商務用 Skype 商務混合式組態**</span><span class="sxs-lookup"><span data-stu-id="d6bdb-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Skype 商務混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="d6bdb-133">圖 2 顯示商務用 Skype 商務混合式組態，商務前端集區與 edge 伺服器通訊與 Skype for Business Online 在 Office 365 中內部部署商務用 Skype 所組成。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="d6bdb-134">如需詳細資訊，請參閱 <<c0>規劃 Skype for Business Server 與 Skype for Business Online 之間的混合式連線。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="d6bdb-135">含商務用 Skype Server 的雲端 PBX</span><span class="sxs-lookup"><span data-stu-id="d6bdb-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="d6bdb-136">雲端 PBX 與 Skype for Business Server 可讓您轉換 Business Server 內部部署的拓樸現有商務用 Skype 內部部署公用交換電話網路 (PSTN) 連線。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="d6bdb-137">**圖 3: Cloud PBX 與 Skype for Business Server**</span><span class="sxs-lookup"><span data-stu-id="d6bdb-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![含商務用 Skype Server 的雲端 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="d6bdb-139">圖 3 顯示商務伺服器組態，組成內部現有的 PBX 或電信公司閘道、 Skype for Business 伺服器和 PSTN 連線至 Microsoft Cloud PBX，在 Office 365 中，其中包含商務用 Skype 用 Skype 雲端 PBX線上。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="d6bdb-140">隸屬於雲端組織中的使用者可以從 Microsoft cloud 包含訊號和語音信箱，會收到專用交換機 (pbx) 服務，但 PSTN 連線能力 （撥號音） 透過 Enterprise Voice 提供從內部Skype 商務伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="d6bdb-141">這是混合式組態，可讓您逐步移轉至雲端式服務的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="d6bdb-142">當您開始將它們移至 Skype for Business Online，您可以保留使用者的語音功能。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="d6bdb-143">您可以移動您的使用者，在您自己的步調，了解其語音功能仍無專家所隸屬的位置。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="d6bdb-144">如需詳細資訊，請參閱 <<c0>規劃 Skype for Business Server 與 Skype for Business Online 之間的混合式連線。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="d6bdb-145">如果您還沒有現有的 Lync Server 或 Skype for Business 伺服器部署，您可以使用 Skype 版商務雲端連接器，一組封裝的虛擬機器 (Vm) 中實作 Cloud pbx 的內部部署 PSTN 連線能力。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="d6bdb-146">如需詳細資訊，請參閱 < <b0>skype for Business 雲端連接器版計劃</b0>。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="d6bdb-147">SharePoint 混合式</span><span class="sxs-lookup"><span data-stu-id="d6bdb-147">SharePoint Hybrid</span></span>

<span data-ttu-id="d6bdb-148">SharePoint 混合式結合了 Office 365 中 SharePoint Online 與內部部署 SharePoint 伺服器陣列的最佳運用這兩者的已連線的體驗。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="d6bdb-149">**圖 4: SharePoint 混合式組態**</span><span class="sxs-lookup"><span data-stu-id="d6bdb-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="d6bdb-151">圖 4 顯示 SharePoint 混合式設定，與 Office 365 中 SharePoint Online 進行通訊的內部部署 SharePoint 伺服器陣列所組成。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="d6bdb-152">SharePoint 混合式案例：</span><span class="sxs-lookup"><span data-stu-id="d6bdb-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="d6bdb-153">混合式商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="d6bdb-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="d6bdb-154">混合式外部網路 B2B</span><span class="sxs-lookup"><span data-stu-id="d6bdb-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="d6bdb-155">混合搜尋</span><span class="sxs-lookup"><span data-stu-id="d6bdb-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="d6bdb-156">混合式設定檔</span><span class="sxs-lookup"><span data-stu-id="d6bdb-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="d6bdb-157">混合式選擇器</span><span class="sxs-lookup"><span data-stu-id="d6bdb-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="d6bdb-158">很容易啟用混合式案例使用自動化可從 Office 365 中 SharePoint Online 系統管理中心的混合式組態精靈。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="d6bdb-159">可延伸混合式 App 啟動器</span><span class="sxs-lookup"><span data-stu-id="d6bdb-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="d6bdb-160">可讓使用者檢視和使用 Office 365 影片和 Delve 應用程式和其內部部署 SharePoint 伺服器陣列的網頁中體驗。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="d6bdb-161">所有這些 SharePoint 混合式案例中，除了可延伸混合式 app 啟動器，可供 SharePoint 2016 和 SharePoint 2013 的使用者。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="d6bdb-162">Exchange Server 2016 混合式</span><span class="sxs-lookup"><span data-stu-id="d6bdb-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="d6bdb-163">使用 Exchange Server 2016 混合式，您可以實現 online 使用者的 Office 365 中的 Exchange Online 優勢，同時讓內部部署使用者繼續使用現有的 Exchange 伺服器基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="d6bdb-164">**圖 5: Exchange 2016 混合式組態**</span><span class="sxs-lookup"><span data-stu-id="d6bdb-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="d6bdb-166">圖 5 顯示 Exchange 2016 混合式組態，與 Exchange Online Protection 和 Office 365 中的信箱進行通訊的內部部署 Exchange 信箱伺服器所組成。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="d6bdb-167">部分使用者擁有內部部署電子郵件伺服器和某些使用者使用 Exchange Online 中，但所有使用者都共用相同的電子郵件地址空間。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="d6bdb-168">此混合式組態：</span><span class="sxs-lookup"><span data-stu-id="d6bdb-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="d6bdb-169">當您移轉至 Exchange Online 一段時間，在您的排程時，會運用您現有的 Exchange 伺服器基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="d6bdb-170">可讓您沒有投資分公司的基礎結構支援遠端站台。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="d6bdb-171">可讓您在 Office 365 中路由傳送到 Exchange Online Protection 的內送網際網路電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="d6bdb-172">只用來跨國子公司需要資料至位於內部部署組織的需求。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="d6bdb-173">您也可以與其他 Microsoft Office 365 應用程式，包括 Skype for Business Online 和 SharePoint Online 整合此混合式組態。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="d6bdb-174">如需詳細資訊，請參閱 < <b0>Exchange Server Hybrid Deployments</b0>。</span><span class="sxs-lookup"><span data-stu-id="d6bdb-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d6bdb-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6bdb-175">See Also</span></span>

[<span data-ttu-id="d6bdb-176">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="d6bdb-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="d6bdb-177">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="d6bdb-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

