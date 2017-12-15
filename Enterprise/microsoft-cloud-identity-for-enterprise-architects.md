---
title: Microsoft Cloud Identity for Enterprise Architects
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "摘要： 為您的 Microsoft 雲端服務與平台設計識別身分解決方案。"
ms.openlocfilehash: f581711345b043d61de503360d101fbcc09de82e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="ea7c9-103">Microsoft Cloud Identity for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="ea7c9-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="ea7c9-104">**摘要：** 為您的 Microsoft 雲端服務與平台設計識別身分解決方案。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="ea7c9-p101">此文章說明 IT 結構設計師在使用 Microsoft 雲端服務和平台，來設計組織的身分識別時，需要了解的資訊。您也可以 5 頁海報的形式檢視本文，並且列印 tabloid 格式 (也稱為總帳 11 x 17 或 A3)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="ea7c9-107">[![Microsoft 雲端身分識別模型縮圖影像](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="ea7c9-108">![PDF 檔案](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio 檔案](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![請參閱其他語言版本的頁面](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[更多語言](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="ea7c9-109">您可以也看到所有的[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)模型及透過往撥動[Microsoft 企業雲端藍圖： IT 決策者的資源](https://aka.ms/cloudarchitecture)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ea7c9-p102">本文會反映年 1 月 2016年版本的**Microsoft 雲端身分識別的企業架構師**海報 （英文）。它不包含的年 4 月 2016年變更或更新版本的海報。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="ea7c9-112">設計 Microsoft 雲端的識別</span><span class="sxs-lookup"><span data-stu-id="ea7c9-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="ea7c9-p103">將您的識別與 Microsoft 雲端整合，讓您可以選擇存取各種服務和雲端平台。其中有兩個主要選項︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="ea7c9-p104">您可以與 Microsoft Azure Active Directory (AD) 整合。這牽涉到將內部部署帳戶同步處理至 Azure AD (Microsoft 雲端的識別提供者)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="ea7c9-117">您可以將內部部署的 Active Directory 網域服務 (AD DS) 環境，延伸到 Microsoft Azure 基礎結構服務中所運行的虛擬機器上。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![供您在雲端設定身分識別的選項](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="ea7c9-119">**圖 1：供您在雲端設定身分識別的選項**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="ea7c9-120">圖 1 顯示 Azure AD 如何提供 Microsoft 軟體即服務 (SaaS) 服務和 Azure 平台即服務(PaaS) 應用程式的身分識別，以及適用於企業營運的應用程式可以怎樣使用內部部署的 AD DS。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="ea7c9-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="ea7c9-121">Azure Active Directory</span></span>

<span data-ttu-id="ea7c9-p105">Microsoft Azure AD 是 Microsoft 裝載在雲端的身分識別及存取管理服務。位於 Microsoft 雲端服務與平台的中心。與 Azure AD 整合，讓您可以使用目前的帳戶和密碼集合，存取所有的 Microsoft SaaS 服務。該整合也提供 Azure PaaS 應用程式的雲端式身分識別。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="ea7c9-126">Azure AD 無法取代對於企業組織內部部署的 AD DS 的需求，或對於 Azure 基礎結構即服務 (IaaS) 中所運行以 Windows 為主的虛擬機器的需求。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="ea7c9-127">Azure AD 有三個版本︰「免費」、「基本」與「進階」。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="ea7c9-128">**免費**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-128">**Free**</span></span> <br/> |<span data-ttu-id="ea7c9-129">**基本**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-129">**Basic**</span></span> <br/> |<span data-ttu-id="ea7c9-130">**進階**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="ea7c9-131">管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ea7c9-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="ea7c9-132">與內部部署的目錄同步</span><span class="sxs-lookup"><span data-stu-id="ea7c9-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="ea7c9-133">在 Azure、Office 365 和數千種熱門的 SaaS 應用程式 (例如 Salesforce、Workday、Concur、DocuSign、Google Apps、Box、ServiceNow、Dropbox 等等) 之間，進行單一登入。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="ea7c9-134">包括免費版中的所有功能，再加上：</span><span class="sxs-lookup"><span data-stu-id="ea7c9-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="ea7c9-135">公司品牌推廣</span><span class="sxs-lookup"><span data-stu-id="ea7c9-135">Company branding</span></span> <br/>  <span data-ttu-id="ea7c9-136">以群組為基礎的應用程式存取</span><span class="sxs-lookup"><span data-stu-id="ea7c9-136">Group-based application access</span></span> <br/>  <span data-ttu-id="ea7c9-137">自助式密碼重設</span><span class="sxs-lookup"><span data-stu-id="ea7c9-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="ea7c9-138">99.9% 的企業 SLA</span><span class="sxs-lookup"><span data-stu-id="ea7c9-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="ea7c9-139">包括免費版和基本版的所有功能，再加上：</span><span class="sxs-lookup"><span data-stu-id="ea7c9-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="ea7c9-140">自助式群組管理</span><span class="sxs-lookup"><span data-stu-id="ea7c9-140">Self-service group management</span></span> <br/>  <span data-ttu-id="ea7c9-141">進階的安全性報告及警示</span><span class="sxs-lookup"><span data-stu-id="ea7c9-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="ea7c9-142">Multi-factor authentication</span><span class="sxs-lookup"><span data-stu-id="ea7c9-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="ea7c9-143">藉由寫回至內部部署 AD DS 的方式，重新設定密碼</span><span class="sxs-lookup"><span data-stu-id="ea7c9-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="ea7c9-144">Azure AD Connect 工具雙向同步</span><span class="sxs-lookup"><span data-stu-id="ea7c9-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="ea7c9-145">Azure AD 應用程式 Proxy</span><span class="sxs-lookup"><span data-stu-id="ea7c9-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="ea7c9-146">Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="ea7c9-147">如需有關版本的詳細資訊，請參閱[Azure Active Directory 的版本](https://go.microsoft.com/fwlink/p/?LinkId=524280)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="ea7c9-148">選項 1：與 Azure Active Directory 整合</span><span class="sxs-lookup"><span data-stu-id="ea7c9-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="ea7c9-p106">大部分的組織會將標準的物件和屬性集合，同步到組織的 Azure AD 租用戶。Azure AD Connect 工具可在您內部部署的 AD DS 帳戶，與 Azure AD 租用戶的帳戶之間，進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![與 Azure AD 整合](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="ea7c9-152">**圖 2：與 Azure AD 整合**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="ea7c9-p107">圖 2 顯示 Azure AD Connect 工具如何取得 AD DS 的變更，並將其傳送到您的 Azure AD 租用戶。在此案例中，您的 Azure AD 租用戶是內部部署的基本目錄裝載在雲端的複本。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="ea7c9-p108">許多組織會使用 AD DS，作為其內部部署的識別提供者。您可以使用不同類型的識別提供者內部部署 (例如使用 LDAP)，並將其同步到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="ea7c9-157">選項 2：將 AD DS 延伸至 Azure</span><span class="sxs-lookup"><span data-stu-id="ea7c9-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="ea7c9-p109">將 AD DS 延伸到 Azure 基礎結構服務中的虛擬機器上；比起與 Azure AD 同步，這樣可支援一套不同的解決方案和應用程式。這裡有兩個範例︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="ea7c9-160">支援雲端式解決方案 (需要 NTLM 或 Kerberos 驗證，或已加入網域的 AD DS 虛擬機器)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="ea7c9-161">對於跨 Microsoft 雲端服務與平台的雲端服務和應用程式，可增加額外的整合可能性。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![將 AD DS 延伸至 Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="ea7c9-163">**圖 3：將 AD DS 延伸到 Azure**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="ea7c9-p110">圖 3 顯示 AD DS 網域控制站，透過內部部署的 VPN 裝置和 Azure VPN 閘道，連線到 Azure 虛擬網路。Azure 虛擬網路包含適用於企業營運的應用程式伺服器，及其本身的網域控制站集合。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="ea7c9-166">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ea7c9-166">More Information</span></span>

- [<span data-ttu-id="ea7c9-167">以 Office 365 同步處理目錄很容易</span><span class="sxs-lookup"><span data-stu-id="ea7c9-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="ea7c9-168">資訊圖表：雲端識別和存取管理</span><span class="sxs-lookup"><span data-stu-id="ea7c9-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="ea7c9-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="ea7c9-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="ea7c9-170">將您的內部部署 AD DS 帳戶與 Microsoft Azure AD 整合</span><span class="sxs-lookup"><span data-stu-id="ea7c9-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="ea7c9-171">將您的內部部署 AD DS 帳戶與 Azure AD 同步，您的使用者就可以使用其內部部署 AD DS 帳戶，存取︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="ea7c9-172">所有的 Microsoft SaaS 服務 (Office 365、Microsoft Intune 和 Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="ea7c9-173">您在 Azure PaaS 中執行的應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="ea7c9-174">有兩種方式來設定這項整合︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="ea7c9-175">目錄與密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="ea7c9-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="ea7c9-176">同盟和單一登入</span><span class="sxs-lookup"><span data-stu-id="ea7c9-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="ea7c9-p111">從符合您的需求而最簡單的選項開始。如有需要，您可以在這些選項之間進行切換。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ea7c9-179">對於企業規模的組織，不建議使用雲端專用帳戶 (未與內部部署 AD DS 整合)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="ea7c9-180">目錄與密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="ea7c9-180">Directory and password synchronization</span></span>

<span data-ttu-id="ea7c9-181">這是最簡單的選項，而且只需要執行 Azure AD Connect 工具的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![目錄與密碼同步處理組態](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="ea7c9-183">**圖 4：目錄與密碼同步處理組態**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="ea7c9-p112">圖 4 顯示具有 AD DS 網域控制站的內部部署或私人雲端資料中心。執行 Azure AD Connect 工具的伺服器，會將帳戶名稱清單與 Azure AD 同步。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="ea7c9-186">使用此選項︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-186">With this option:</span></span>
  
- <span data-ttu-id="ea7c9-p113">使用者帳戶會從內部部署的 AD DS (或其他識別提供者) 同步到您的 Azure AD 租用戶。內部部署目錄會保留帳戶的系統授權來源，您可以從中管理帳戶的所有變更。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="ea7c9-189">Azure AD 會針對以 Microsoft SaaS 為基礎的服務和 Azure PaaS 應用程式，執行所有的驗證。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="ea7c9-190">您也可以設定多個 AD DS 樹系的同步處理。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="ea7c9-191">使用密碼同步處理︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-191">With password synchronization:</span></span>
  
- <span data-ttu-id="ea7c9-192">使用者在存取雲端服務時，會看到輸入密碼的提示，此處的密碼與他們在內部部署資源中所使用的密碼相同。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="ea7c9-p114">使用者密碼絕對不會以純文字傳送到 Azure AD。相反地，系統會使用密碼雜湊。無法透過密碼編譯以解密，或對密碼雜湊進行反向工程以取得純文字密碼。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="ea7c9-196">使用多重要素驗證 (MFA)：</span><span class="sxs-lookup"><span data-stu-id="ea7c9-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="ea7c9-197">您可以利用 Office 365 提供的基本 MFA 功能。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="ea7c9-198">Azure PaaS 應用程式開發人員可利用 Azure Multi-Factor Authentication 服務。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="ea7c9-199">目錄同步處理並不會進行與內部部署 MFA 解決方案的整合。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="ea7c9-200">同盟和單一登入</span><span class="sxs-lookup"><span data-stu-id="ea7c9-200">Federation and single sign-on</span></span>

<span data-ttu-id="ea7c9-201">這個選項需要額外的伺服器和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-201">This option requires additional servers and infrastructure.</span></span> 
  
![同盟驗證所需的伺服器](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="ea7c9-203">**圖 5：同盟驗證所需的伺服器**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="ea7c9-p115">圖 5 顯示同盟驗證所需的元件集合。Azure AD 會連絡 Web 應用程式 Proxy，後者會將驗證要求轉送給 Active Directory 同盟服務 (AD FS) 伺服器，該伺服器會再將要求轉送給 AD DS 網域控制站，以供評估和回應。執行 Azure AD Connect 工具的伺服器，會將帳戶名稱清單從 AD DS 同步到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="ea7c9-207">同盟提供會以下額外的企業功能︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="ea7c9-208">所有傳送到 Azure AD 的驗證要求，都會透過 AD FS 轉送給內部部署的識別提供者，並對其執行。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="ea7c9-209">與非 Microsoft 身分識別提供者搭配運作。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="ea7c9-210">密碼雜湊同步處理可以當做同盟登入的備用登入 (例如，若同盟驗證失敗時)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="ea7c9-211">在以下情況使用同盟：</span><span class="sxs-lookup"><span data-stu-id="ea7c9-211">Use federation if:</span></span>
  
- <span data-ttu-id="ea7c9-p116">單一登入是必要時。有了單一登入，使用者在存取雲端服務時，就不會看到輸入任何認證 (使用者名稱或密碼) 的提示。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="ea7c9-214">已部署 AD FS 時。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="ea7c9-215">您使用協力廠商身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="ea7c9-216">您使用 Forefront Identity Manager 2010 R2 (不支援密碼雜湊同步處理) 時。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="ea7c9-217">您具有內部部署整合式智慧卡或其他 MFA 解決方案。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="ea7c9-218">您需要登入稽核和/或停用帳戶時。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="ea7c9-219">您的組織需要按照網路位置或工作時間，進行用戶端登入限制時。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="ea7c9-220">您必須遵循美國聯邦資訊處理標準 (FIPS) 時。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="ea7c9-221">若要進行同盟驗證，需要針對基礎結構內部部署進行更多投資。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="ea7c9-p117">內部部署伺服器必須能夠透過公司的防火牆而存取網際網路。Microsoft 建議使用在您的周邊網路中，所部署的 Web 應用程式 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="ea7c9-224">需要硬體、授權，以及運作中的 AD FS 伺服器、AD FS Proxy 或 Web 應用程式 Proxy 伺服器、防火牆和負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="ea7c9-225">可用性和效能對於確保使用者可存取 Office 365 和其他雲端應用程式而言，極為重要。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="ea7c9-226">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ea7c9-226">More Information</span></span>

- [<span data-ttu-id="ea7c9-227">以 Office 365 同步處理目錄很容易</span><span class="sxs-lookup"><span data-stu-id="ea7c9-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="ea7c9-228">準備透過目錄同步作業將使用者佈建至 Office 365</span><span class="sxs-lookup"><span data-stu-id="ea7c9-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="ea7c9-229">Office 365 的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="ea7c9-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="ea7c9-230">Azure Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="ea7c9-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="ea7c9-231">TechEd 2014：目錄整合：使用 Active Directory 和 Azure Active Directory 建立單一目錄</span><span class="sxs-lookup"><span data-stu-id="ea7c9-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="ea7c9-232">將 AD DS 延伸至 Azure</span><span class="sxs-lookup"><span data-stu-id="ea7c9-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="ea7c9-233">將 AD DS 延伸到 Azure，是支援 Azure 基礎結構服務中所運行的虛擬機器上，適用於企業營運的應用程式的第一步，可提供：</span><span class="sxs-lookup"><span data-stu-id="ea7c9-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="ea7c9-234">支援雲端式解決方案 (需要 NTLM 或 Kerberos 驗證，或已加入網域的 AD DS 虛擬機器)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="ea7c9-235">對於雲端服務和應用程式，可提供額外的整合可能性，且可隨時新增。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![將 AD DS 延伸至 Azure 虛擬網路](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="ea7c9-237">**圖 6：將 AD DS 延伸至 Azure 虛擬網路**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="ea7c9-p118">圖 6 顯示顯示具有 AD DS 的內部部署或私人雲端資料中心，使用站台對站台 VPN 或 ExpressRoute 連線方式，連線到 Azure 虛擬網路。Azure 虛擬網路包含適用於企業營運的應用程式伺服器，及其本身的網域控制站集合。此設定是 AD DS 內部部署以及在 Azure 基礎結構服務中的混合式部署。此設定需要︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="ea7c9-242">Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="ea7c9-243">內部部署虛擬私人網路 (VPN) 裝置或路由器，以及 Azure VPN 閘道之間的連線。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="ea7c9-244">將您內部部署 IP 位址空間的一部分，用於虛擬網路中的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="ea7c9-245">於指定為通用類別目錄伺服器 (降低 VPN 連線的輸出流量) 的虛擬網路，部署一或多個網域控制站。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="ea7c9-246">比起與 Azure AD 同步，這個識別架構可支援一套不同的解決方案和應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="ea7c9-247">內部部署與 Azure 的連線選項</span><span class="sxs-lookup"><span data-stu-id="ea7c9-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="ea7c9-248">若要將您的內部部署網路連線到 Azure 虛擬網路，您可以使用︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="ea7c9-249">站台對站台 VPN 連線，能將 1-10 個網站 (包括其他 Azure 虛擬網路) 連接到單一 Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="ea7c9-p119">ExpressRoute，這是透過合作夥伴網路和資料中心服務提供者的私人安全 WAN 連結。ExpressRoute 連線可提供更高的可靠性、更大的頻寬，以及更低的延遲。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="ea7c9-252">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ea7c9-252">More Information</span></span>

- [<span data-ttu-id="ea7c9-253">虛擬網路的交叉部署連線能力</span><span class="sxs-lookup"><span data-stu-id="ea7c9-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="ea7c9-254">ExpressRoute 技術概觀</span><span class="sxs-lookup"><span data-stu-id="ea7c9-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="ea7c9-255">在 Azure 虛擬機器部署 Windows Server Active Directory 的指導方針</span><span class="sxs-lookup"><span data-stu-id="ea7c9-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="ea7c9-256">將您的應用程式與雲端身分識別整合</span><span class="sxs-lookup"><span data-stu-id="ea7c9-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="ea7c9-p120">當設計和開發在雲端執行的應用程式時，您應該設法保持在驗證程序上使用者經驗的一致性，包括必要的認證集合。例如，使用 Windows 認證時，無論是對 Azure AD 或延伸的 AD DS，都請確保使用者可以快速驗證，並專注於他們的工作。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![將您的應用程式與雲端身分識別整合](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="ea7c9-260">**圖 7：將您的應用程式與雲端身分識別整合**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="ea7c9-261">圖 7 顯示將您的應用程式與雲端身分識別整合的三個選項。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="ea7c9-262">將裝載在雲端的應用程式登錄到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="ea7c9-p121">請參閱 MSDN 文件[將應用程式與 Azure Active Directory 整合](https://go.microsoft.com/fwlink/p/?LinkId=524303)。這可讓您使用 Azure AD 驗證您的 PaaS 應用程式，同時也讓使用者或管理員可以授與對您應用程式的存取權限，以便代表他們從其他的雲端服務 (例如 Office 365) 存取內容。如需更多詳細資料和程式碼範例，請參閱 MSDN 文章[Azure Active Directory 的驗證案例](https://go.microsoft.com/fwlink/p/?LinkId=524304)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="ea7c9-266">應用程式如果需要以程式設計方式驗證，才能存取受到 AD SD、Windows Server 2012 R2 上的 AD FS，或 Azure AD 保護的的應用程式，則可使用︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="ea7c9-267">[Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="ea7c9-268">Active Directory 驗證程式庫 (ADAL)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="ea7c9-p122">Azure AD Graph API 支援 OAuth 和 OpenID Connect。也會使用 PaaS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="ea7c9-p123">設定內部部署的應用程式，或在 Azure 虛擬網路中的虛擬機器上所執行，適用於企業營運的應用程式，以便直接使用 Windows 驗證 (NTLM 或 Kerberos)。這對使用者以及需要最少設定的伺服器應用程式開發人員來說，會是最佳的經驗。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="ea7c9-273">應用程式整合範例</span><span class="sxs-lookup"><span data-stu-id="ea7c9-273">Application integration example</span></span>

<span data-ttu-id="ea7c9-p124">組織建置了 ASP.NET 應用程式，用以公開 REST 端點，供其他應用程式在那裡取得最新的銷售資料。對該 REST 端點的存取受到 Azure AD 的保護。應用程式必須提供可由 Azure AD 驗證的認證，之後 ASP.NET 應用程式才會傳送要求的資料。然後，在組織中的其他開發人員就可以撰寫自己的應用程式，以使用來自 REST 端點的銷售資料。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="ea7c9-p125">為了讓 Azure AD 驗證並擷取資料，ADAL 會管理使用者驗證程並將存取權杖遞交給應用程式，使其可以用來取得銷售資料的存取權限。ADAL 可讓取得並剖析權杖、OAuth 流程及其他元素的複雜過程變得簡單。ADAL 是另一種正在迅速變化的技術解決方案，因此開發人員應該在 NuGet 上尋找最新的版本。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="ea7c9-281">在 Azure 中部署目錄元件</span><span class="sxs-lookup"><span data-stu-id="ea7c9-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="ea7c9-p126">您可以在 Azure 虛擬網路中，而不是內部部署的資料中心上，部署目錄元件 (例如用於密碼同步處理或同盟驗證的伺服器)。請考慮其優點，尤其是您打算將 AD DS 延伸到 Azure 時。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="ea7c9-284">以下是可以置於 Azure 虛擬網路中的目錄元件︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="ea7c9-285">Azure AD Connect 工具</span><span class="sxs-lookup"><span data-stu-id="ea7c9-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="ea7c9-286">同盟驗證元件</span><span class="sxs-lookup"><span data-stu-id="ea7c9-286">Federated authentication components</span></span>
    
- <span data-ttu-id="ea7c9-287">獨立式 AD DS 環境</span><span class="sxs-lookup"><span data-stu-id="ea7c9-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="ea7c9-288">AD Connect 工具</span><span class="sxs-lookup"><span data-stu-id="ea7c9-288">AD Connect tool</span></span>

<span data-ttu-id="ea7c9-p127">Azure AD Connect 工具可裝載於 Azure 虛擬網路中的雲端。將此工作負載部署到 Azure 時，請考慮這些優點︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="ea7c9-291">您可能可以加速佈建以及降低作業成本</span><span class="sxs-lookup"><span data-stu-id="ea7c9-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="ea7c9-292">提高可用性</span><span class="sxs-lookup"><span data-stu-id="ea7c9-292">Increased availability</span></span>
    
![在 Azure 基礎結構服務上運行的 AD Connect 工具](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="ea7c9-294">**圖 8：在 Azure 中執行的 AD Connect 工具**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="ea7c9-p128">圖 8 顯示在 Azure 虛擬網路中的虛擬機器上所執行的 AD Connect 工具，會查詢內部部署的 AD DS 網域控制站，以取得帳戶變更，然後將這些變更傳送到 Office 365。此解決方案適用於︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="ea7c9-297">Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-297">Office 365 services.</span></span>
    
- <span data-ttu-id="ea7c9-298">網際網路上可用的 Azure PaaS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="ea7c9-299">Azure 中適用於企業營運的應用程式，可從內部部署環境透過站台對站台 VPN 或 ExpressRoute 連線方式使用。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="ea7c9-300">如需詳細資訊，請參閱[將內部部署識別與 Azure Active Directory 整合](https://go.microsoft.com/fwlink/p/?LinkId=524307)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="ea7c9-301">同盟驗證基礎結構</span><span class="sxs-lookup"><span data-stu-id="ea7c9-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="ea7c9-302">如果您尚未內部部署 AD FS，請考慮將此工作負載部署到 Azure 的優點：</span><span class="sxs-lookup"><span data-stu-id="ea7c9-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="ea7c9-303">為雲端服務的驗證 (無內部部署相依性) 提供自主性</span><span class="sxs-lookup"><span data-stu-id="ea7c9-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="ea7c9-304">減少由伺服器和工具主控的內部部署</span><span class="sxs-lookup"><span data-stu-id="ea7c9-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="ea7c9-305">使用雙節點容錯移轉叢集上的站台對站台 VPN 閘道連線到 Azure (新)</span><span class="sxs-lookup"><span data-stu-id="ea7c9-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="ea7c9-306">使用 ACL 以確保 Web 應用程式 Proxy 伺服器只能與 AD FS 通訊，而無法直接與網域控制站或其他伺服器通訊</span><span class="sxs-lookup"><span data-stu-id="ea7c9-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![在 Azure 部署您的同盟驗證基礎結構](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="ea7c9-308">**圖 9：在 Azure 部署您的同盟驗證基礎結構**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="ea7c9-p129">圖 9 顯示內部部署的網域控制站集合，複寫 Azure 虛擬網路中網域控制站集合的 AD DS 資訊。在 Azure 虛擬網路中的伺服器上所執行的 Azure AD Connect 工具，會查詢本機網域控制站以取得變更，然後將這些變更傳送到 Azure AD。從 Microsoft SaaS 服務、Azure PaaS 應用程式和其他雲端應用程式，傳入 Azure AD 的驗證要求，會轉送給外部負載平衡器，後者會將要求轉送給 Web 應用程式 Proxy 伺服器集合。Web 應用程式 Proxy 伺服器會將要求轉送給內部負載平衡器，後者會將要求轉送給 AD FS 伺服器集合。接著 AD FS 伺服器會將要求轉送給網域控制站，以驗證傳送的認證。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="ea7c9-314">此解決方案適用於︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-314">This solution works with:</span></span>
  
- <span data-ttu-id="ea7c9-315">需要 Kerberos 的應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="ea7c9-316">所有 Microsoft 的 SaaS 服務</span><span class="sxs-lookup"><span data-stu-id="ea7c9-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="ea7c9-317">Azure 中網際網路對應的應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="ea7c9-318">Azure IaaS 或 PaaS 中，需要採用您組織的 AD DS 帳戶集合進行驗證的應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="ea7c9-319">如需詳細資訊，請參閱[將內部部署識別與 Azure Active Directory 整合](https://go.microsoft.com/fwlink/p/?LinkId=524307)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="ea7c9-320">Azure 虛擬網路中的獨立式 AD DS 環境</span><span class="sxs-lookup"><span data-stu-id="ea7c9-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="ea7c9-p130">您不必每次都將雲端應用程式與內部部署環境整合。例如，在 Azure 虛擬網路中的獨立式 AD DS 網域，會支援公眾對應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![供伺服器型應用程式使用的獨立 AD DS 環境](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="ea7c9-324">**圖 10：供伺服器型應用程式使用的獨立 AD DS 環境**</span><span class="sxs-lookup"><span data-stu-id="ea7c9-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="ea7c9-p131">圖 10 顯示裝載 AD DS 伺服器的 Azure 虛擬網路，以裝載應用程式的伺服器集合，提供 AD DS 和 DNS 服務。此解決方案適用於︰</span><span class="sxs-lookup"><span data-stu-id="ea7c9-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="ea7c9-327">網際網路對應的網站和應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="ea7c9-328">需要 NTLM 或 Kerberos 驗證的應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="ea7c9-329">需要 AD DS 並在以 Windows 為主的伺服器上執行的應用程式</span><span class="sxs-lookup"><span data-stu-id="ea7c9-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="ea7c9-330">如需詳細資訊，請參閱[將內部部署識別與 Azure Active Directory 整合](https://go.microsoft.com/fwlink/p/?LinkId=524307)。</span><span class="sxs-lookup"><span data-stu-id="ea7c9-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ea7c9-331">See Also</span><span class="sxs-lookup"><span data-stu-id="ea7c9-331">See Also</span></span>

[<span data-ttu-id="ea7c9-332">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="ea7c9-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="ea7c9-333">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="ea7c9-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



