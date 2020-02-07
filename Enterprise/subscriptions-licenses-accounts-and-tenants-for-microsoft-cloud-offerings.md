---
title: >
  Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 摘要：了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。
ms.openlocfilehash: 65922f3ab8a88056ebc63d12cc0dcad37d6c49c8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843974"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="b03c3-103">Microsoft 雲端供應項目的訂用帳戶、授權、帳戶及租用戶
</span><span class="sxs-lookup"><span data-stu-id="b03c3-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="b03c3-104">**摘要：** 了解所有 Microsoft 雲端供應項目上的組織、訂用帳戶、授權、使用者帳戶、租用戶之間的關係。</span><span class="sxs-lookup"><span data-stu-id="b03c3-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="b03c3-105">Microsoft 提供了組織、訂用帳戶、授權、使用者帳戶的階層，讓您在所有雲端供應項目中能使用一致的身分識別和計費方式：
</span><span class="sxs-lookup"><span data-stu-id="b03c3-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="b03c3-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="b03c3-106">Microsoft Office 365</span></span>
- <span data-ttu-id="b03c3-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b03c3-107">Microsoft Azure</span></span>
- <span data-ttu-id="b03c3-108">Microsoft Intune 與 Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="b03c3-108">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
- <span data-ttu-id="b03c3-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b03c3-109">Microsoft Dynamics 365</span></span>

<span data-ttu-id="b03c3-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) 將 Office 365、EMS 和 Windows 10 企業版整合到單一訂閱和整合式服務集合中。</span><span class="sxs-lookup"><span data-stu-id="b03c3-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combines Office 365, EMS, and Windows 10 Enterprise into a single subscription and set of integrated services.</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="b03c3-111">階層的元素</span><span class="sxs-lookup"><span data-stu-id="b03c3-111">Elements of the hierarchy</span></span>

<span data-ttu-id="b03c3-112">以下是階層的元素：</span><span class="sxs-lookup"><span data-stu-id="b03c3-112">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="b03c3-113">組織</span><span class="sxs-lookup"><span data-stu-id="b03c3-113">Organization</span></span>

<span data-ttu-id="b03c3-p101">組織代表正在使用 Microsoft 雲端供應項目的商業實體，通常是用一個或多個公用網域名稱 (DNS)，例如 contoso.com 加以識別。組織是訂用帳戶的容器。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="b03c3-116">訂閱</span><span class="sxs-lookup"><span data-stu-id="b03c3-116">Subscriptions</span></span>

<span data-ttu-id="b03c3-117">訂閱是與 Microsoft 簽訂使用一或多個 Microsoft 雲端平台或服務的合約，其費用會根據每位使用者的授權費用或雲端資源使用量而產生。</span><span class="sxs-lookup"><span data-stu-id="b03c3-117">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="b03c3-118">Microsoft 的軟體即服務 (SaaS) 型雲端供應項目 (Office 365、Intune/EMS 和 Dynamics 365) 是依每位使用者授權費用來收費。</span><span class="sxs-lookup"><span data-stu-id="b03c3-118">Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="b03c3-119">Microsoft 的平台即服務 (PaaS) 和基礎結構即服務 (IaaS) 雲端供應項目 (Azure) 是根據雲端資源的使用量來收費。</span><span class="sxs-lookup"><span data-stu-id="b03c3-119">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="b03c3-p102">您也可以使用試用版的訂用帳戶，但在使用特定一段時間或耗用量之後，訂用帳戶便到期。您可以將試用版訂用帳戶轉換為付費訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="b03c3-122">組織可有多個訂用帳戶，用於 Microsoft 的多個雲端供應項目。</span><span class="sxs-lookup"><span data-stu-id="b03c3-122">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="b03c3-123">圖 1 顯示單一組織有多個 Office 365 訂用帳戶、一個 Intune 訂用帳戶、一個 Dynamics 365 訂用帳戶、多個 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-123">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="b03c3-124">**圖 1：組織的多個訂用帳戶範例**</span><span class="sxs-lookup"><span data-stu-id="b03c3-124">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![具有多個 Microsoft 雲端供應項目訂用帳戶的組織範例。](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a><span data-ttu-id="b03c3-126">授權</span><span class="sxs-lookup"><span data-stu-id="b03c3-126">Licenses</span></span>

<span data-ttu-id="b03c3-127">針對 Microsoft SaaS 雲端供應項目，授權可讓特定使用者帳戶使用雲端供應項目服務。</span><span class="sxs-lookup"><span data-stu-id="b03c3-127">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="b03c3-128">會向您收取每月固定的訂閱費用。</span><span class="sxs-lookup"><span data-stu-id="b03c3-128">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="b03c3-129">系統管理員會將授權指派給訂閱中的個別使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-129">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="b03c3-130">如圖 2 所示範例，Contoso Corporation 擁有包含 100 個授權的 Office 365 企業版 E5 訂閱，可讓最多 100 個個別使用者帳戶使用 Office 365 企業版 E5 的功能與服務。</span><span class="sxs-lookup"><span data-stu-id="b03c3-130">For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Office 365 Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="b03c3-131">**圖 2：SaaS 型訂用帳戶中的組織授權**</span><span class="sxs-lookup"><span data-stu-id="b03c3-131">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft SaaS 型雲端供應項目訂用帳戶中多個授權的範例。](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="b03c3-133">使用 Azure PaaS 型雲端服務時，服務費用已包含軟體授權。</span><span class="sxs-lookup"><span data-stu-id="b03c3-133">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="b03c3-p105">使用 Azure IaaS  型虛擬機器時，可能會需要額外的授權來使用安裝在虛擬機器映像上的軟體或應用程式。部分虛擬機器映像已安裝軟體的授權版本，費用是由伺服器的每一分鐘費率涵蓋。例如 SQL Server 2014 和 SQL Server 2016 的虛擬機器映像。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="b03c3-p106">部分虛擬機器映像已安裝試用版應用程式，在試用期間過後需要額外的軟體應用程式授權。例如，SharePoint Server 2016 試用版的虛擬機器映像包含預先安裝的 SharePoint Server 2016 試用版。若要在試用到期日之後繼續使用 SharePoint Server 2016，您必須向 Microsoft 購買 SharePoint Server 2016 授權和用戶端授權。這些費用和 Azure 訂用帳戶是分開的，且仍需支付執行虛擬機器的每一分鐘費率。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="b03c3-141">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b03c3-141">User accounts</span></span>

<span data-ttu-id="b03c3-142">所有 Microsoft 雲端供應項目的使用者帳戶都儲存在 Azure Active Directory (Azure AD) 租用戶中，其中包含使用者帳戶和群組。</span><span class="sxs-lookup"><span data-stu-id="b03c3-142">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="b03c3-143">Azure AD 租用戶可以使用 Azure AD Connect 這個 Windows 伺服器型服務，與您現有的 Active Directory 網域服務 (AD DS) 帳戶進行同步。</span><span class="sxs-lookup"><span data-stu-id="b03c3-143">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="b03c3-144">這稱為目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="b03c3-144">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="b03c3-145">圖 3 顯示組織的多個訂用帳戶使用同一個 Azure AD 租用戶，租用戶包含組織的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-145">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="b03c3-146">**圖 3：組織的多個訂用帳戶使用相同 Azure AD 租用戶的範例。**</span><span class="sxs-lookup"><span data-stu-id="b03c3-146">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![多個訂用帳戶皆使用相同 Azure AD 租用戶的組織範例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="b03c3-148">租用戶</span><span class="sxs-lookup"><span data-stu-id="b03c3-148">Tenants</span></span>

<span data-ttu-id="b03c3-p108">使用 SaaS 雲端供應項目時，租用戶是指存放提供雲端服務的伺服器的區域位置。例如，Contoso 公司選擇以歐洲區域來裝載它的 Office 365、EMS、Dynamics 365 租用戶，供其巴黎總公司的 15,000 名員工使用。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="b03c3-p109">Azure PaaS 服務和虛擬機器的工作負載裝載於 Azure IaaS 中，可以將租用戶放在世界各地的 Azure 資料中心內。當您建立 Azure PaaS 應用程式或服務或 IaaS 工作負載的元素時，由您指定 Azure 資料中心 (稱為「位置」)。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="b03c3-p110">Azure AD 租用戶是包含帳戶和群組的 Azure AD 的特定執行個體。付費版或試用版的 Office 365、Dynamics 365 或 Intune/EMS 訂用帳戶包含一個免費 Azure AD 租用戶。這個 Azure AD 租用戶不包含其他 Azure 服務，和 Azure 試用版或付費版訂用帳戶不同。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="b03c3-156">階層摘要</span><span class="sxs-lookup"><span data-stu-id="b03c3-156">Summary of the hierarchy</span></span>

<span data-ttu-id="b03c3-157">以下是重點複習：</span><span class="sxs-lookup"><span data-stu-id="b03c3-157">Here is a quick recap:</span></span>
  
- <span data-ttu-id="b03c3-158">組織可以有多個訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-158">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="b03c3-159">訂用帳戶可以有多個授權。</span><span class="sxs-lookup"><span data-stu-id="b03c3-159">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="b03c3-160">授權可以指派給個別使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-160">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="b03c3-161">使用者帳戶儲存在 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-161">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="b03c3-162">以下是組織、訂用帳戶、授權、使用者帳戶的關係範例：</span><span class="sxs-lookup"><span data-stu-id="b03c3-162">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="b03c3-163">組織由其公用網域名稱加以識別。
</span><span class="sxs-lookup"><span data-stu-id="b03c3-163">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="b03c3-164">Office 365 企業版 E3 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="b03c3-164">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="b03c3-165">Office 365 企業版 E5 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="b03c3-165">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="b03c3-166">EMS 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="b03c3-166">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="b03c3-167">Dynamics 365 訂用帳戶包含使用者授權。</span><span class="sxs-lookup"><span data-stu-id="b03c3-167">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="b03c3-168">多個 Azure 訂用帳戶。
</span><span class="sxs-lookup"><span data-stu-id="b03c3-168">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="b03c3-169">組織的使用者帳戶在同一 Azure AD 租用戶中。</span><span class="sxs-lookup"><span data-stu-id="b03c3-169">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="b03c3-170">多個 Microsoft 雲端供應項目訂用帳戶可以使用作為共同身分識別提供者的相同 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-170">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="b03c3-171">內含內部部署 AD DS 的同步處理帳戶的中央 Azure AD 租用戶，可為組織提供雲端型的身分識別即服務 (IDaaS)。</span><span class="sxs-lookup"><span data-stu-id="b03c3-171">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="b03c3-172">**圖 4： 組織同步處理的內部部署帳戶和 IDaaS**</span><span class="sxs-lookup"><span data-stu-id="b03c3-172">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![組織的身分識別即服務 (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="b03c3-p112">在圖 4 中，Microsoft 的 SaaS 雲端供應項目、Azure PaaS 應用程式、使用 Azure AD 網域服務的 Azure IaaS 中的虛擬機器，三者使用同一個 Azure AD 租用戶。Azure AD Connect 將內部部署的 AD DS 樹系和 Azure AD 租用戶同步。</span><span class="sxs-lookup"><span data-stu-id="b03c3-p112">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="b03c3-176">合併多個 Microsoft 雲端供應項目的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="b03c3-176">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="b03c3-177">下表說明如何以已有的一種雲端供應項目的一個訂用帳戶為本，合併多個 Microsoft 雲端供應項目 (表中的第一個直列)，以及如何為不同的雲端供應項目新增訂用帳戶 (表中的橫行)。</span><span class="sxs-lookup"><span data-stu-id="b03c3-177">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="b03c3-178">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="b03c3-178">**Office 365**</span></span>|<span data-ttu-id="b03c3-179">**Azure**</span><span class="sxs-lookup"><span data-stu-id="b03c3-179">**Azure**</span></span>|<span data-ttu-id="b03c3-180">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="b03c3-180">**Intune/EMS**</span></span>|<span data-ttu-id="b03c3-181">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="b03c3-181">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="b03c3-182">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="b03c3-182">**Office 365**</span></span> <br/> |<span data-ttu-id="b03c3-183">NA</span><span class="sxs-lookup"><span data-stu-id="b03c3-183">NA</span></span>  <br/> |<span data-ttu-id="b03c3-184">您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-184">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="b03c3-185">您可以透過 Microsoft 365 系統管理中心為組織新增 Intune/EMS 訂閱。</span><span class="sxs-lookup"><span data-stu-id="b03c3-185">You add an Intune/EMS subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |<span data-ttu-id="b03c3-186">您可以透過 Microsoft 365 系統管理中心為組織新增 Dynamics 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="b03c3-186">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="b03c3-187">**Azure**</span><span class="sxs-lookup"><span data-stu-id="b03c3-187">**Azure**</span></span> <br/> |<span data-ttu-id="b03c3-188">您為組織新增 Office 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-188">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b03c3-189">NA</span><span class="sxs-lookup"><span data-stu-id="b03c3-189">NA</span></span>  <br/> |<span data-ttu-id="b03c3-190">您為組織新增 Intune/EMS 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-190">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b03c3-191">您為組織新增 Dynamics 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-191">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="b03c3-192">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="b03c3-192">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="b03c3-193">您為組織新增 Office 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b03c3-194">您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-194">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="b03c3-195">NA</span><span class="sxs-lookup"><span data-stu-id="b03c3-195">NA</span></span>  <br/> |<span data-ttu-id="b03c3-196">您為組織新增 Dynamics 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="b03c3-197">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="b03c3-197">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="b03c3-198">您為組織新增 Office 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b03c3-199">您在 Azure 入口網站中為組織新增 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="b03c3-200">您為組織新增 Intune/EMS 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-200">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="b03c3-201">NA</span><span class="sxs-lookup"><span data-stu-id="b03c3-201">NA</span></span>  <br/> |
   
<span data-ttu-id="b03c3-202">要將 Microsoft SaaS 服務的訂用帳戶新增到組織，簡單的做法是透過系統管理中心：</span><span class="sxs-lookup"><span data-stu-id="b03c3-202">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="b03c3-203">使用您的全域系統管理員帳戶登入 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))。</span><span class="sxs-lookup"><span data-stu-id="b03c3-203">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="b03c3-204">在 **[管理中心]** 首頁的導覽窗格中，按一下 **[計費]**，然後按一下 **[購買服務]**。</span><span class="sxs-lookup"><span data-stu-id="b03c3-204">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="b03c3-205">在 **[購買服務]** 頁面上，購買新的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-205">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="b03c3-206">系統管理中心會將組織和 Office 365 訂用帳戶的 Azure AD 租用戶，指派給 SaaS 雲端供應項目的新訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b03c3-206">The admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="b03c3-207">使用與 Office 365 訂用帳戶相同的組織和 Azure AD 租用戶進行新增：</span><span class="sxs-lookup"><span data-stu-id="b03c3-207">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="b03c3-208">使用 Office 365 全域管理員帳戶登入 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="b03c3-208">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="b03c3-209">在左側導覽窗格中，按一下 **[訂用帳戶]**，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="b03c3-209">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="b03c3-210">在 **[新增訂用帳戶]** 頁面上，選取供應項目，並填寫付款資訊和合約。</span><span class="sxs-lookup"><span data-stu-id="b03c3-210">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="b03c3-211">如果您已另外購買 Azure 與 Office 365 訂閱，並想要從您的 Azure 訂用帳戶存取 Office 365 Azure AD 租用戶，請參閱[將現有的 Azure 訂用帳戶新增到您的 Azure Active Directory 租用戶](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) 中的指示。</span><span class="sxs-lookup"><span data-stu-id="b03c3-211">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="b03c3-212">請參閱</span><span class="sxs-lookup"><span data-stu-id="b03c3-212">See also</span></span>

[<span data-ttu-id="b03c3-213">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="b03c3-213">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="b03c3-214">適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型</span><span class="sxs-lookup"><span data-stu-id="b03c3-214">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="b03c3-215">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="b03c3-215">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="b03c3-216">下一步</span><span class="sxs-lookup"><span data-stu-id="b03c3-216">Next step</span></span>

[<span data-ttu-id="b03c3-217">評估 Office 365 的網路連線能力</span><span class="sxs-lookup"><span data-stu-id="b03c3-217">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
