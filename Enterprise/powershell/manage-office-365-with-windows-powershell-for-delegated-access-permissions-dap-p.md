---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 管理 Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 摘要：新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴可以使用 Windows PowerShell 來管理 Office 365 客戶租用戶。
ms.openlocfilehash: 5e3fb67cad453593119347e2de07222f35d03f56
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844204"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ce873-103">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="ce873-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="ce873-104">**摘要：** 新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴可以使用 Windows PowerShell 來管理 Office 365 客戶租用戶。</span><span class="sxs-lookup"><span data-stu-id="ce873-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="ce873-105">委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="ce873-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="ce873-106">他們通常是其他公司的網路或電信服務提供者。</span><span class="sxs-lookup"><span data-stu-id="ce873-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="ce873-107">他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="ce873-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="ce873-108">當他們銷售 Office 365 訂閱時，會自動將管理代表 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。</span><span class="sxs-lookup"><span data-stu-id="ce873-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="ce873-109">最佳情況下，這是很困難又費時若要在 Microsoft 365 系統管理中心中執行。</span><span class="sxs-lookup"><span data-stu-id="ce873-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="ce873-110">透過 Windows PowerShell for Office 365，他們能輕鬆地執行如列出所有客戶 **TenantId** 和其網域，或識別客戶租用中的所有使用者及指派的授權等系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="ce873-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="ce873-111">在某些情況下，他們只能在 Windows PowerShell for Office 365 中執行這些管理工作。</span><span class="sxs-lookup"><span data-stu-id="ce873-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="ce873-112">以下是新聞訂閱方式和 CSP 合作夥伴最常用來管理客戶租用的範例案例：</span><span class="sxs-lookup"><span data-stu-id="ce873-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="ce873-113">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 管理 Office 365 租用戶</span><span class="sxs-lookup"><span data-stu-id="ce873-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="ce873-114">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域</span><span class="sxs-lookup"><span data-stu-id="ce873-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="ce873-115">利用適用於委派存取權限 (DAP) 合作夥伴的遠端 Windows PowerShell 連線至 Exchange Online 租用戶</span><span class="sxs-lookup"><span data-stu-id="ce873-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="ce873-116">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 擷取客戶租用戶報告資料</span><span class="sxs-lookup"><span data-stu-id="ce873-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

