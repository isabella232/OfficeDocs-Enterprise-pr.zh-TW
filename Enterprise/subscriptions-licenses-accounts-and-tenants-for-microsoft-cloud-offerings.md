---
title: >
  Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。
ms.openlocfilehash: 53d2f7f32402d8c05d22c0661a0f625c756da6d4
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319214"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="70b82-103">Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶
</span><span class="sxs-lookup"><span data-stu-id="70b82-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="70b82-104">**摘要：** 了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。</span><span class="sxs-lookup"><span data-stu-id="70b82-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="70b82-105">Microsoft 提供了組織、訂用帳戶、授權、使用者帳戶的階層，讓您在所有雲端供應項目中能使用一致的身分識別和計費方式：
</span><span class="sxs-lookup"><span data-stu-id="70b82-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="70b82-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="70b82-106">Microsoft Office 365</span></span>
    
    <span data-ttu-id="70b82-107">詳細資訊請參閱[企業方案與價格](https://products.office.com/business/compare-office-365-for-business-plans)。</span><span class="sxs-lookup"><span data-stu-id="70b82-107">See [business plans and pricing](https://products.office.com/business/compare-office-365-for-business-plans) for more information.</span></span>
    
- <span data-ttu-id="70b82-108">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="70b82-108">Microsoft Azure</span></span>
    
    <span data-ttu-id="70b82-109">詳細資訊請參閱 [Azure 價格](https://azure.microsoft.com/pricing/)。</span><span class="sxs-lookup"><span data-stu-id="70b82-109">See [Azure pricing](https://azure.microsoft.com/pricing/) for more information.</span></span>
    
- <span data-ttu-id="70b82-110">Microsoft Intune 與 Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="70b82-110">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
    
    <span data-ttu-id="70b82-111">詳細資訊請參閱 [Intune 價格](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)。</span><span class="sxs-lookup"><span data-stu-id="70b82-111">See [Intune pricing](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) for more information.</span></span>
    
- <span data-ttu-id="70b82-112">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="70b82-112">Microsoft Dynamics 365</span></span>
    
    <span data-ttu-id="70b82-113">詳細資訊請參閱 [Dynamics 365 價格](https://dynamics.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="70b82-113">See [Dynamics 365 pricing](https://dynamics.microsoft.com/) for more information.</span></span>
    
## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="70b82-114">階層的元素</span><span class="sxs-lookup"><span data-stu-id="70b82-114">Elements of the hierarchy</span></span>

<span data-ttu-id="70b82-115">以下是階層的元素：</span><span class="sxs-lookup"><span data-stu-id="70b82-115">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="70b82-116">組織</span><span class="sxs-lookup"><span data-stu-id="70b82-116">Organization</span></span>

<span data-ttu-id="70b82-p101">組織代表正在使用 Microsoft 雲端供應項目的商業實體，通常是用一個或多個公用網域名稱 (DNS)，例如 contoso.com 加以識別。組織是訂用帳戶的容器。</span><span class="sxs-lookup"><span data-stu-id="70b82-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by a public Domain Name System (DNS) domain name such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="70b82-119">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="70b82-119">Subscriptions</span></span>

<span data-ttu-id="70b82-p102">訂用帳戶是與 Microsoft 的協議，同意使用一或多個 Microsoft 雲端平台或服務，並根據每個使用者授權費用或雲端資源耗用量來累算費用。Microsoft 的「軟體即服務」(SaaS) 雲端供應項目 (Office 365、Intune/EMS、Dynamics 365) 會依據每個使用者授權費用收費。Microsoft 的「平台即服務」(PaaS) 和「基礎結構即服務」(IaaS) 雲端供應項目 (Azure) 會依據雲端資源耗用量收費。</span><span class="sxs-lookup"><span data-stu-id="70b82-p102">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption. Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees. Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
  
<span data-ttu-id="70b82-p103">您也可以使用試用版的訂用帳戶，但在使用特定一段時間或耗用量之後，訂用帳戶便到期。您可以將試用版訂用帳戶轉換為付費訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-p103">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="70b82-p104">組織可有多個訂用帳戶，用於 Microsoft 的多個雲端供應項目。圖 1 為其範例。</span><span class="sxs-lookup"><span data-stu-id="70b82-p104">Organizations can have multiple subscriptions for Microsoft's cloud offerings. Figure 1 shows an example.</span></span>
  
<span data-ttu-id="70b82-127">**圖 1：組織的多個訂用帳戶範例**</span><span class="sxs-lookup"><span data-stu-id="70b82-127">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![具有多個 Microsoft 雲端供應項目訂用帳戶的組織範例。](images/Subscriptions/Subscriptions_Fig1.png)

  
<span data-ttu-id="70b82-129">圖 1 顯示單一組織有多個 Office 365 訂用帳戶、一個 Intune 訂用帳戶、一個 Dynamics 365 訂用帳戶、多個 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-129">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>
  
### <a name="licenses"></a><span data-ttu-id="70b82-130">授權</span><span class="sxs-lookup"><span data-stu-id="70b82-130">Licenses</span></span>

<span data-ttu-id="70b82-p105">使用 Microsoft 的 SaaS 雲端供應項目時，授權允許特定使用者帳戶使用該雲端供應項目的服務。固定的每月費用是訂用帳戶的其中一環。系統管理員將授權指派給訂用帳戶中的個別使用者帳戶。在圖 2 的範例中，Contoso 公司有 100 個 Office 365 企業版 E5 的授權， 可讓最多 100 個個別使用者帳戶使用企業版 E5 的功能與服務。</span><span class="sxs-lookup"><span data-stu-id="70b82-p105">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering. You are charged a fixed monthly fee as part of your subscription. Administrators assign licenses to individual user accounts in the subscription. For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="70b82-135">**圖 2：SaaS 型訂用帳戶中的組織授權**</span><span class="sxs-lookup"><span data-stu-id="70b82-135">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft SaaS 型雲端供應項目訂用帳戶中多個授權的範例。](images/Subscriptions/Subscriptions_Fig2.png)
  
<span data-ttu-id="70b82-137">使用 Azure PaaS 型雲端服務時，服務費用已包含軟體授權。</span><span class="sxs-lookup"><span data-stu-id="70b82-137">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="70b82-p106">使用 Azure IaaS  型虛擬機器時，可能會需要額外的授權來使用安裝在虛擬機器映像上的軟體或應用程式。部分虛擬機器映像已安裝軟體的授權版本，費用是由伺服器的每一分鐘費率涵蓋。例如 SQL Server 2014 和 SQL Server 2016 的虛擬機器映像。</span><span class="sxs-lookup"><span data-stu-id="70b82-p106">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="70b82-p107">部分虛擬機器映像已安裝試用版應用程式，在試用期間過後需要額外的軟體應用程式授權。例如，SharePoint Server 2016 試用版的虛擬機器映像包含預先安裝的 SharePoint Server 2016 試用版。若要在試用到期日之後繼續使用 SharePoint Server 2016，您必須向 Microsoft 購買 SharePoint Server 2016 授權和用戶端授權。這些費用和 Azure 訂用帳戶是分開的，且仍需支付執行虛擬機器的每一分鐘費率。</span><span class="sxs-lookup"><span data-stu-id="70b82-p107">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="70b82-145">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="70b82-145">User accounts</span></span>

<span data-ttu-id="70b82-p108">所有 Microsoft 雲端供應項目的使用者帳戶都儲存在 Azure Active Directory (AD) 租用戶，此租用戶包含使用者帳戶和群組。Azure AD Connect 是 Windows 的伺服器型服務，可以將 Azure AD 租用戶與您的現有 Windows Server AD 帳戶同步。這就是所謂的目錄同步處理 (DirSync)。</span><span class="sxs-lookup"><span data-stu-id="70b82-p108">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups. An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service. This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="70b82-149">圖 3 顯示組織的多個訂用帳戶使用同一個 Azure AD 租用戶，租用戶包含組織的帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-149">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="70b82-150">**圖 3：組織的多個訂用帳戶使用相同 Azure AD 租用戶的範例。**</span><span class="sxs-lookup"><span data-stu-id="70b82-150">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![多個訂用帳戶皆使用相同 Azure AD 租用戶的組織範例。](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="70b82-152">租用戶</span><span class="sxs-lookup"><span data-stu-id="70b82-152">Tenants</span></span>

<span data-ttu-id="70b82-p109">使用 SaaS 雲端供應項目時，租用戶是指存放提供雲端服務的伺服器的區域位置。例如，Contoso 公司選擇以歐洲區域來裝載它的 Office 365、EMS、Dynamics 365 租用戶，供其巴黎總公司的 15,000 名員工使用。</span><span class="sxs-lookup"><span data-stu-id="70b82-p109">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="70b82-p110">Azure PaaS 服務和虛擬機器的工作負載裝載於 Azure IaaS 中，可以將租用戶放在世界各地的 Azure 資料中心內。當您建立 Azure PaaS 應用程式或服務或 IaaS 工作負載的元素時，由您指定 Azure 資料中心 (稱為「位置」)。</span><span class="sxs-lookup"><span data-stu-id="70b82-p110">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="70b82-p111">Azure AD 租用戶是包含帳戶和群組的 Azure AD 的特定執行個體。付費版或試用版的 Office 365、Dynamics 365 或 Intune/EMS 訂用帳戶包含一個免費 Azure AD 租用戶。這個 Azure AD 租用戶不包含其他 Azure 服務，和 Azure 試用版或付費版訂用帳戶不同。</span><span class="sxs-lookup"><span data-stu-id="70b82-p111">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="70b82-160">階層摘要</span><span class="sxs-lookup"><span data-stu-id="70b82-160">Summary of the hierarchy</span></span>

<span data-ttu-id="70b82-161">以下是重點複習：</span><span class="sxs-lookup"><span data-stu-id="70b82-161">Here is a quick recap:</span></span>
  
- <span data-ttu-id="70b82-162">組織可以有多個訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-162">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="70b82-163">訂用帳戶可以有多個授權。</span><span class="sxs-lookup"><span data-stu-id="70b82-163">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="70b82-164">授權可以指派給個別使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-164">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="70b82-165">使用者帳戶儲存在 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-165">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="70b82-166">以下是組織、訂用帳戶、授權、使用者帳戶的關係範例：</span><span class="sxs-lookup"><span data-stu-id="70b82-166">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="70b82-167">組織由其公用網域名稱加以識別。
</span><span class="sxs-lookup"><span data-stu-id="70b82-167">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="70b82-168">Office 365 企業版 E3 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="70b82-168">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="70b82-169">Office 365 企業版 E5 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="70b82-169">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="70b82-170">EMS 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="70b82-170">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="70b82-171">Dynamics 365 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="70b82-171">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="70b82-172">多個 Azure 訂用帳戶。
</span><span class="sxs-lookup"><span data-stu-id="70b82-172">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="70b82-173">組織的使用者帳戶在同一 Azure AD 租用戶中。</span><span class="sxs-lookup"><span data-stu-id="70b82-173">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="70b82-p112">多個 Microsoft 雲端供應項目的訂用帳戶可以使用相同 Azure AD 租用戶作為共同的身分識別提供者。集中的 Azure AD 租用戶包含內部部署 Windows Server AD 同步處理的帳戶，可為組織提供雲端上的身分識別即服務 (IDaaS)。如圖 4 所示。</span><span class="sxs-lookup"><span data-stu-id="70b82-p112">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider. A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization. This is shown in Figure 4.</span></span>
  
<span data-ttu-id="70b82-177">**圖 4： 組織同步處理的內部部署帳戶和 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="70b82-177">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![組織的身分識別即服務 (IaaS) IDaaS。](images/Subscriptions/Subscriptions_Fig4.png)
  
<span data-ttu-id="70b82-p113">在圖 4 中，Microsoft 的 SaaS 雲端供應項目、Azure PaaS 應用程式、使用 Azure AD 網域服務的 Azure IaaS 中的虛擬機器，三者使用同一個 Azure AD 租用戶。Azure AD Connect 將內部部署的 Windows Server AD 樹系和 Azure AD 租用戶同步。</span><span class="sxs-lookup"><span data-stu-id="70b82-p113">Figure 4 shows how a common Azure AD tenant is utilized by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="70b82-181">有關 Microsoft 雲端供應項目的身分識別整合，詳細資訊請參閱[企業架構的 Microsoft 雲端身分識別](https://aka.ms/cloudarchidentity)。</span><span class="sxs-lookup"><span data-stu-id="70b82-181">For more information about identity integration across Microsoft's cloud offerings, see [Microsoft Cloud Identity for Enterprise Architects](https://aka.ms/cloudarchidentity).</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="70b82-182">合併多個 Microsoft 雲端供應項目的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="70b82-182">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="70b82-183">下表說明如何以已有的一種雲端供應項目的一個訂用帳戶為本，合併多個 Microsoft 雲端供應項目 (表中的第一個直列)，以及如何為不同的雲端供應項目新增訂用帳戶 (表中的橫行)。</span><span class="sxs-lookup"><span data-stu-id="70b82-183">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="70b82-184">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="70b82-184">**Office 365**</span></span>|<span data-ttu-id="70b82-185">**Azure**</span><span class="sxs-lookup"><span data-stu-id="70b82-185">**Azure**</span></span>|<span data-ttu-id="70b82-186">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="70b82-186">**Intune/EMS**</span></span>|<span data-ttu-id="70b82-187">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="70b82-187">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="70b82-188">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="70b82-188">**Office 365**</span></span> <br/> |<span data-ttu-id="70b82-189">NA</span><span class="sxs-lookup"><span data-stu-id="70b82-189">NA</span></span>  <br/> |<span data-ttu-id="70b82-190">您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-190">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="70b82-191">您在  Office 365 入口網站中為組織新增 Intune/EMS 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-191">You add an Intune/EMS subscription to your organization from the Office 365 portal.</span></span>  <br/> |<span data-ttu-id="70b82-192">您在  Office 365 入口網站中為組織新增 Dynamics 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-192">You add a Dynamics 365 subscription to your organization from the Office 365 portal.</span></span>  <br/> |
|<span data-ttu-id="70b82-193">**Azure**</span><span class="sxs-lookup"><span data-stu-id="70b82-193">**Azure**</span></span> <br/> |<span data-ttu-id="70b82-194">您為組織新增 Office 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-194">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="70b82-195">NA</span><span class="sxs-lookup"><span data-stu-id="70b82-195">NA</span></span>  <br/> |<span data-ttu-id="70b82-196">您為組織新增 Intune/EMS 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-196">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="70b82-197">您為組織新增 Dynamics 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-197">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="70b82-198">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="70b82-198">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="70b82-199">您為組織新增 Office 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-199">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="70b82-200">您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-200">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="70b82-201">NA</span><span class="sxs-lookup"><span data-stu-id="70b82-201">NA</span></span>  <br/> |<span data-ttu-id="70b82-202">您為組織新增 Dynamics 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-202">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="70b82-203">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="70b82-203">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="70b82-204">您為組織新增 Office 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-204">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="70b82-205">您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-205">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="70b82-206">您為組織新增 Intune/EMS 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-206">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="70b82-207">NA</span><span class="sxs-lookup"><span data-stu-id="70b82-207">NA</span></span>  <br/> |
   
<span data-ttu-id="70b82-208">要將 Microsoft SaaS 服務的訂用帳戶新增到組織，簡單的做法是透過 Office 365 管理中心：</span><span class="sxs-lookup"><span data-stu-id="70b82-208">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="70b82-209">使用全域系統管理員帳戶登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com))，然後按一下 [管理]****。</span><span class="sxs-lookup"><span data-stu-id="70b82-209">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with your global administrator account, and then click **Admin**.</span></span>
    
2. <span data-ttu-id="70b82-210">在 [管理中心]**** 首頁的導覽窗格中，按一下 [計費]****，然後按一下 [購買服務]****。</span><span class="sxs-lookup"><span data-stu-id="70b82-210">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="70b82-211">在 [購買服務]**** 頁面上，購買新的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-211">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="70b82-212">Office 365 管理中心會將組織和 Office 365 訂用帳戶的 Azure AD 租用戶，指派給 SaaS 雲端供應項目的新訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="70b82-212">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="70b82-213">使用與 Office 365 訂用帳戶相同的組織和 Azure AD 租用戶進行新增：</span><span class="sxs-lookup"><span data-stu-id="70b82-213">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="70b82-214">使用 Office 365 全域管理員帳戶登入 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="70b82-214">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="70b82-215">在左側導覽窗格中，按一下 [訂用帳戶]****，然後按一下 [新增]****。</span><span class="sxs-lookup"><span data-stu-id="70b82-215">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="70b82-216">在 [新增訂用帳戶]**** 頁面上，選取供應項目，並填寫付款資訊和合約。</span><span class="sxs-lookup"><span data-stu-id="70b82-216">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="70b82-217">如果您已另外購買 Azure 與 Office 365 訂用帳戶，想要從您的 Azure 訂用帳戶存取 Office 365 Azure AD 租用戶，請參閱[建立 Office 365 租用戶與 Azure 訂用帳戶的關聯](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)中的指示。</span><span class="sxs-lookup"><span data-stu-id="70b82-217">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscription](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="70b82-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b82-218">See Also</span></span>

[<span data-ttu-id="70b82-219">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="70b82-219">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="70b82-220">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="70b82-220">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="70b82-221">適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型</span><span class="sxs-lookup"><span data-stu-id="70b82-221">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="70b82-222">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="70b82-222">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="70b82-223">Contoso 公司的訂用帳戶、授權及使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="70b82-223">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



