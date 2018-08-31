---
title: Contoso 公司的訂用帳戶、授權及使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 摘要： 了解與結構的 Contoso 的雲端訂閱、 授權、 使用者帳戶的承租人。
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915508"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="05cff-103">Contoso 公司的訂用帳戶、授權及使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="05cff-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="05cff-104">**摘要：** 了解與結構的 Contoso 的雲端訂閱、 授權、 使用者帳戶的承租人。</span><span class="sxs-lookup"><span data-stu-id="05cff-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="05cff-105">若要提供用於所有雲端方案一致的身分識別和計費、 Microsoft 提供組織/訂閱/授權/使用者帳戶階層：</span><span class="sxs-lookup"><span data-stu-id="05cff-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="05cff-106">組織</span><span class="sxs-lookup"><span data-stu-id="05cff-106">Organization</span></span>
    
    <span data-ttu-id="05cff-107">使用 Microsoft cloud 方案，通常是由公用 DNS 網域名稱，例如 contoso.com 識別商務實體。</span><span class="sxs-lookup"><span data-stu-id="05cff-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="05cff-108">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="05cff-108">Subscriptions</span></span>
    
    <span data-ttu-id="05cff-p101">對於 Microsoft saas 和雲端方案 （Office 365、 Intune/EMS 和 Dynamics 365）、 訂閱會為某項特定產品和使用者授權購買的組。Azure、 訂閱允許組織使用的雲端服務的帳單。</span><span class="sxs-lookup"><span data-stu-id="05cff-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="05cff-111">授權</span><span class="sxs-lookup"><span data-stu-id="05cff-111">Licenses</span></span>
    
    <span data-ttu-id="05cff-p102">Microsoft saas 和雲端方案、 授權允許使用雲端服務的特定使用者帳戶。Azure、 軟體授權之內建到服務定價，但是在某些情況下需要購買額外軟體授權。</span><span class="sxs-lookup"><span data-stu-id="05cff-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="05cff-114">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="05cff-114">User accounts</span></span>
    
    <span data-ttu-id="05cff-115">使用者帳戶儲存在 Azure AD 租用戶和以進行同步處理在內部身分識別提供者的 Windows Server AD 例如。</span><span class="sxs-lookup"><span data-stu-id="05cff-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="05cff-116">Contoso 的結構</span><span class="sxs-lookup"><span data-stu-id="05cff-116">Contoso's structure</span></span>

<span data-ttu-id="05cff-117">Contoso 取決於組織其訂閱、 授權、 帳戶、 及租用戶的下列結構：</span><span class="sxs-lookup"><span data-stu-id="05cff-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="05cff-118">**圖 1： Contoso 的組織、 訂閱、 授權、 使用者帳戶及承租人**</span><span class="sxs-lookup"><span data-stu-id="05cff-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Contoso 的組織、訂用帳戶授權、使用者帳戶及租用戶](media/Contoso-Poster/Subscriptions.png)
  
<span data-ttu-id="05cff-120">圖 1 顯示如何 Contoso 組織包含多個訂閱便繫結至一般的 Azure AD 租用戶包含從 contoso.com Windows Server AD 樹系同步處理之使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="05cff-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="05cff-121">**組織**其公用網域名成稱為 contoso.com 可識別的 Contoso Corporation。</span><span class="sxs-lookup"><span data-stu-id="05cff-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="05cff-122">**訂閱和授權**Contoso Corporation 會使用下列：</span><span class="sxs-lookup"><span data-stu-id="05cff-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="05cff-123">使用 5000 授權 Office 365 企業版 E3 產品</span><span class="sxs-lookup"><span data-stu-id="05cff-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="05cff-124">使用 200 授權 Office 365 企業版 E5 產品</span><span class="sxs-lookup"><span data-stu-id="05cff-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="05cff-125">使用 5000 授權 EMS 產品</span><span class="sxs-lookup"><span data-stu-id="05cff-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="05cff-126">使用 100 授權 Dynamics 365 產品</span><span class="sxs-lookup"><span data-stu-id="05cff-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="05cff-127">多個 Azure 訂閱根據區域 （英文）</span><span class="sxs-lookup"><span data-stu-id="05cff-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="05cff-128">**使用者帳戶**常見的 Azure AD 租用戶包含使用者帳戶的清單及群組使用的 Contoso 的訂閱，除了開發/測試所有 Azure 訂閱。</span><span class="sxs-lookup"><span data-stu-id="05cff-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="05cff-129">為 Contoso 的承租人：</span><span class="sxs-lookup"><span data-stu-id="05cff-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="05cff-p103">Saas 和雲端方案、 租用戶是提供雲端服務伺服器設施區域性位置。Contoso 選擇來裝載其 Office 365、 EMS 及 Dynamics 365 租用戶的歐洲地區。</span><span class="sxs-lookup"><span data-stu-id="05cff-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="05cff-p104">Azure PaaS 服務與應用程式及 IaaS IT 工作量可以在任何 Azure 資料中心內租用在全世界。Azure AD 租用戶是含有帳戶和群組的 Azure AD 的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="05cff-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="05cff-134">常見的 Azure AD 租用戶包含 Contoso Windows Server AD 樹系的同步處理的帳戶提供跨 Microsoft cloud 方案 IDaaS。</span><span class="sxs-lookup"><span data-stu-id="05cff-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="05cff-135">如需詳細資訊，請參閱[訂閱、 授權、 帳戶、 及 Microsoft cloud 方案的承租人](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)。</span><span class="sxs-lookup"><span data-stu-id="05cff-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="05cff-136">Contoso 的 Azure 訂閱</span><span class="sxs-lookup"><span data-stu-id="05cff-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="05cff-137">圖 2 顯示 Contoso 的 Azure 訂閱的階層式設計：</span><span class="sxs-lookup"><span data-stu-id="05cff-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="05cff-138">**圖 2： Azure 訂閱 Contoso 的結構**</span><span class="sxs-lookup"><span data-stu-id="05cff-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Contoso 的 Azure 訂用帳戶結構](media/Contoso-Poster/Subscriptions-Nested.png)
  
- <span data-ttu-id="05cff-140">Contoso 是在上方，根據與 Microsoft 其 Enterprise 合約。</span><span class="sxs-lookup"><span data-stu-id="05cff-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="05cff-141">有一組根據 Contoso 的 Windows Server AD 樹系的網域 Contoso Corporation 在全世界的不同區域對應的帳戶。</span><span class="sxs-lookup"><span data-stu-id="05cff-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="05cff-142">每個區域中，有一或多個區域的開發、 測試及生產部署需求為基礎的訂閱。</span><span class="sxs-lookup"><span data-stu-id="05cff-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="05cff-p105">每個 Azure 訂閱可以與單一相關聯 Azure AD 租用戶包含驗證和授權 Azure 服務的使用者帳戶和群組。實際執行訂閱使用一般的 Contoso Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="05cff-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="05cff-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05cff-145">See Also</span></span>

[<span data-ttu-id="05cff-146">Microsoft 雲端中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="05cff-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="05cff-147">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="05cff-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="05cff-148">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="05cff-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




