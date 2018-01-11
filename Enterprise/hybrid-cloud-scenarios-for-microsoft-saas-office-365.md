---
title: "Microsoft SaaS (Office 365) 的混合式雲端案例"
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
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "摘要： 瞭解混合架構與案例的 Microsoft 的 saas 和型雲端方案 (Office 365)。"
ms.openlocfilehash: 63126d694817f8323494e584f1f497a1a732c678
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="32777-103">Microsoft SaaS (Office 365) 的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="32777-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="32777-104">**摘要：**了解混合式架構與案例的 Microsoft 的 saas 和型雲端方案 (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="32777-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="32777-105">合併與與其對應的雲端移轉或長期整合策略的一部分的 Office 365 中的內部部署 Exchange、 SharePoint、 或 Skype for Business。</span><span class="sxs-lookup"><span data-stu-id="32777-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="32777-106">Microsoft saas 和混合式案例的架構</span><span class="sxs-lookup"><span data-stu-id="32777-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="32777-107">圖 1 顯示的 Office 365 Microsoft SaaS 為基礎的混合式案例的架構。</span><span class="sxs-lookup"><span data-stu-id="32777-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="32777-108">**圖 1： Office 365 的 Microsoft SaaS 為基礎的混合式案例**</span><span class="sxs-lookup"><span data-stu-id="32777-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Office 365 的 Microsoft IaaS 型混合式案例](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="32777-110">之架構的每個圖層：</span><span class="sxs-lookup"><span data-stu-id="32777-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="32777-111">應用程式與案例</span><span class="sxs-lookup"><span data-stu-id="32777-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="32777-112">有各種 saas 和型混合式案例，對齊繞 Office Server 產品和其 Office 365 對應項目：</span><span class="sxs-lookup"><span data-stu-id="32777-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="32777-113">Exchange Server 結合與 Exchange Online （Exchange Server 混合）</span><span class="sxs-lookup"><span data-stu-id="32777-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="32777-114">Skype Business server 與 Skype 結合商務線上和新的雲端 PBX 與雲端連接器 Edition 案例</span><span class="sxs-lookup"><span data-stu-id="32777-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="32777-115">SharePoint Server 2016 或 SharePoint Server 2013 與 SharePoint Online （多個案例） 合併</span><span class="sxs-lookup"><span data-stu-id="32777-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="32777-116">也有 Exchange Online 與 Skype for Business Server 內部部署、 跨產品混合式案例。</span><span class="sxs-lookup"><span data-stu-id="32777-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="32777-117">身分識別</span><span class="sxs-lookup"><span data-stu-id="32777-117">Identity</span></span>
    
    <span data-ttu-id="32777-p101">可以包含與內部部署 Windows Server AD 目錄同步處理。或者，您可以設定和協力廠商身分識別提供者結盟的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="32777-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="32777-120">工作列最右邊的網路</span><span class="sxs-lookup"><span data-stu-id="32777-120">Network</span></span>
    
    <span data-ttu-id="32777-121">與 Microsoft Office 365 或 Dynamics 365 對等包含您現有的網際網路管道或 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="32777-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="32777-122">內部部署</span><span class="sxs-lookup"><span data-stu-id="32777-122">On-premises</span></span>
    
    <span data-ttu-id="32777-p102">可以包含現有伺服器的 Exchange、 SharePoint 及 Skype for Business，應該更新其最新版本。您可以結合它們與 Office 365 與對應的混合式案例。</span><span class="sxs-lookup"><span data-stu-id="32777-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="32777-125">設定您自己的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="32777-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="32777-126">Skype 商務 2015年混合式</span><span class="sxs-lookup"><span data-stu-id="32777-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="32777-p103">Skype 商務 2015年混合式可讓您將現有的內部部署與 Skype 合併商務 online。某些使用者位於的內部和某些使用者的主伺服器皆線上，但使用者共用相同的工作階段初始通訊協定 (SIP) 網域，例如 contoso.com。您可以使用此混合式組態移轉從內部部署到 Office 365 一段時間，在您的排程。也可以與 Exchange Online 整合的商務 2015 Skype。</span><span class="sxs-lookup"><span data-stu-id="32777-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="32777-130">**圖 2： Skype 商務 2015年混合組態**</span><span class="sxs-lookup"><span data-stu-id="32777-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![商務用 Skype 2015 混合式組態](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="32777-132">圖 2 顯示組成商務 2015年前端集區與 edge server 通訊的 Skype 商務 Online 在 Office 365 中的內部部署 Skype Skype 商務 2015年混合式設定。</span><span class="sxs-lookup"><span data-stu-id="32777-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="32777-133">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="32777-133">For more information, see:</span></span>
  
- [<span data-ttu-id="32777-134">規劃 Business server Skype 與 Skype 商務 online 之間的混合式連線</span><span class="sxs-lookup"><span data-stu-id="32777-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="32777-135">支援混合式組態 Business Server 2015 Skype</span><span class="sxs-lookup"><span data-stu-id="32777-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="32777-136">Skype 商務混合式</span><span class="sxs-lookup"><span data-stu-id="32777-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="32777-137">含商務用 Skype Server 的雲端 PBX</span><span class="sxs-lookup"><span data-stu-id="32777-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="32777-138">雲端 PBX 與 Skype Business server 可讓您以利 Business Server 內部部署拓撲的現有 Skype 與內部部署公用交換電話網路 (PSTN) 連線。</span><span class="sxs-lookup"><span data-stu-id="32777-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="32777-139">**圖 3: Cloud PBX 與 Skype Business server**</span><span class="sxs-lookup"><span data-stu-id="32777-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![含商務用 Skype Server 的雲端 PBX](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="32777-141">圖 3 是雲端 PBX 與 Skype Business Server 設定、 組成的內部現有的 PBX 或電話閘道、 Skype 商務伺服器和 PSTN 連線至 Office 365，其中包含 Skype for Business 中 Microsoft Cloud PBX線上。</span><span class="sxs-lookup"><span data-stu-id="32777-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="32777-142">位於雲端組織中的使用者可以接收專用交換機 (pbx) 服務從 Microsoft cloud 包含訊號和語音信箱，但可 PSTN 連線能力 （撥號音） 透過提供企業語音從內部Skype 商務伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="32777-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="32777-p104">這是更好的範例可讓您逐步移轉至雲端架構服務的混合式組態。您可以在您開始進行商務 Online 將其移至 Skype 保留使用者的語音功能。您可以移動使用者在自己步調，了解其語音功能會繼續否專家隸屬的。</span><span class="sxs-lookup"><span data-stu-id="32777-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="32777-146">如需詳細資訊，請參閱[規劃 Skype Business Server 和 Skype 商務 Online 或 Lync Server 2013 之間的混合式連線](https://technet.microsoft.com/library/jj205403.aspx)。</span><span class="sxs-lookup"><span data-stu-id="32777-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="32777-147">如果您已經沒有現有的 Lync Server 或 Skype 商務伺服器部署，您可以使用 Skype Business Cloud 連接器 edition、 封裝的虛擬機器 (Vm) 實作內部部署 PSTN 連線能力與雲端 PBX 的一組。</span><span class="sxs-lookup"><span data-stu-id="32777-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="32777-148">如需詳細資訊，請參閱 ＜ [Plan for Business Cloud 連接器 edition Skype](https://technet.microsoft.com/library/mt605227.aspx)。</span><span class="sxs-lookup"><span data-stu-id="32777-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="32777-149">SharePoint 混合式</span><span class="sxs-lookup"><span data-stu-id="32777-149">SharePoint Hybrid</span></span>

<span data-ttu-id="32777-150">SharePoint 混合式應 SharePoint Online 在 Office 365 搭配內部部署 SharePoint 伺服器陣列的最佳運用這兩者的、 連線經驗。</span><span class="sxs-lookup"><span data-stu-id="32777-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="32777-151">**圖 4： SharePoint 混合式設定**</span><span class="sxs-lookup"><span data-stu-id="32777-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint 混合式組態](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="32777-153">圖 4 顯示組成通訊的 SharePoint Online 在 Office 365 中內部部署 SharePoint 伺服器陣列的 SharePoint 混合式組態。</span><span class="sxs-lookup"><span data-stu-id="32777-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="32777-154">SharePoint 混合式案例：</span><span class="sxs-lookup"><span data-stu-id="32777-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="32777-155">混合式 OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="32777-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="32777-156">混合式小組網站</span><span class="sxs-lookup"><span data-stu-id="32777-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="32777-157">混合式外部網路 B2B</span><span class="sxs-lookup"><span data-stu-id="32777-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="32777-158">混合式搜尋</span><span class="sxs-lookup"><span data-stu-id="32777-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="32777-159">混合式設定檔</span><span class="sxs-lookup"><span data-stu-id="32777-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="32777-160">混合式選擇器</span><span class="sxs-lookup"><span data-stu-id="32777-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="32777-161">很容易啟用使用自動化可從 SharePoint Online 系統管理中心在 Office 365 的混合式組態精靈的混合式案例。</span><span class="sxs-lookup"><span data-stu-id="32777-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="32777-162">可延伸的混合式應用程式啟動器</span><span class="sxs-lookup"><span data-stu-id="32777-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="32777-163">可讓使用者檢視及使用 Office 365 影片和 Delve 應用程式與經驗內其內部部署 SharePoint 伺服器陣列的頁面。</span><span class="sxs-lookup"><span data-stu-id="32777-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="32777-164">這些 SharePoint 混合式案例，可延伸的混合式應用程式啟動器、 以外的所有可用的 SharePoint 2016 與 SharePoint 2013 的使用者。</span><span class="sxs-lookup"><span data-stu-id="32777-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="32777-165">如需詳細資訊，請參閱[SharePoint 混合式](http://hybrid.office.com/sharepoint/)。</span><span class="sxs-lookup"><span data-stu-id="32777-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="32777-166">Exchange Server 2016 混合式</span><span class="sxs-lookup"><span data-stu-id="32777-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="32777-167">與 Exchange Server 2016 混合，您可以了解 online 使用者的 Exchange Online Office 365 的優點時的內部使用者繼續使用現有的 Exchange Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="32777-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="32777-168">**圖 5： Exchange 2016 混合組態**</span><span class="sxs-lookup"><span data-stu-id="32777-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 混合式組態](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="32777-170">圖 5 顯示通訊與 Exchange Online Protection 和 Office 365 中的信箱的內部部署 Exchange 信箱伺服器所組成的 Exchange 2016 混合式組態。</span><span class="sxs-lookup"><span data-stu-id="32777-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="32777-171">某些使用者擁有的內部部署電子郵件伺服器及某些使用者使用 Exchange Online 中，但所有使用者都共用相同的電子郵件地址空間。</span><span class="sxs-lookup"><span data-stu-id="32777-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="32777-172">此混合式組態：</span><span class="sxs-lookup"><span data-stu-id="32777-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="32777-173">當您移轉至 Exchange Online 一段時間，在您的排程上時如何運用現有的 Exchange Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="32777-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="32777-174">可讓您以支援遠端站台不含演變在分公司的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="32777-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="32777-175">可讓您透過 Exchange Online Protection 的內送網際網路電子郵件路由 Office 365 中。</span><span class="sxs-lookup"><span data-stu-id="32777-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="32777-176">您能跨國子公司需要資料至位於內部部署組織的需求。</span><span class="sxs-lookup"><span data-stu-id="32777-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="32777-177">您也可以與其他 Microsoft Office 365 應用程式，包括 Skype 商務 Online 與 SharePoint Online 整合此混合式組態。</span><span class="sxs-lookup"><span data-stu-id="32777-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="32777-178">如需詳細資訊，請參閱[Exchange Server 混合式部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)與[Exchange 混合](http://hybrid.office.com/exchange/)。</span><span class="sxs-lookup"><span data-stu-id="32777-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="32777-179">請參閱</span><span class="sxs-lookup"><span data-stu-id="32777-179">See Also</span></span>

[<span data-ttu-id="32777-180">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="32777-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="32777-181">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="32777-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="32777-182">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="32777-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



