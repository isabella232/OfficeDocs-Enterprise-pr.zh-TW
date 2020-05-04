---
title: 將 Office 365 授權指派給使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何將 Office 365 授權指派給使用者帳戶（個別或根據群組成員資格）。
ms.openlocfilehash: 77e6f6c20e9eeff11487a31cb2d616abbed42601
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009378"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="9cda6-103">將 Office 365 授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9cda6-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="9cda6-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="9cda6-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="9cda6-105">針對僅限雲端的身分識別模型，您可以根據建立的方式，將 Office 365 授權指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9cda6-105">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="9cda6-106">針對混合式識別模型，當您第一次同步處理 Active Directory 網域服務（AD DS）使用者帳戶時，系統不會自動指派 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="9cda6-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="9cda6-107">在這兩種情況下，您必須指派授權給使用者帳戶，讓您的使用者能夠存取 Office 365 服務，例如電子郵件和 Microsoft 團隊。</span><span class="sxs-lookup"><span data-stu-id="9cda6-107">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="9cda6-108">您可以透過群組成員資格個別或自動將授權指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9cda6-108">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="9cda6-109">若要將 Office 365 授權指派給個別使用者帳戶，您可以使用：</span><span class="sxs-lookup"><span data-stu-id="9cda6-109">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="9cda6-110">Microsoft 365 系統管理中心</span><span class="sxs-lookup"><span data-stu-id="9cda6-110">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="9cda6-111">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9cda6-111">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="9cda6-112">若要進行自動授權指派，請參閱[在 AZURE AD 中以群組為基礎的授權](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="9cda6-112">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9cda6-113">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9cda6-113">Next steps</span></span>

<span data-ttu-id="9cda6-114">透過已獲指派授權的完整使用者帳戶，您現在可以：</span><span class="sxs-lookup"><span data-stu-id="9cda6-114">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="9cda6-115">實施安全性</span><span class="sxs-lookup"><span data-stu-id="9cda6-115">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="9cda6-116">部署用戶端軟體，例如 Microsoft 365 應用程式</span><span class="sxs-lookup"><span data-stu-id="9cda6-116">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="9cda6-117">在 Office 365 中設定行動裝置管理</span><span class="sxs-lookup"><span data-stu-id="9cda6-117">Set up Mobile Device Management in Office 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="9cda6-118">設定服務和應用程式</span><span class="sxs-lookup"><span data-stu-id="9cda6-118">Configure services and applications</span></span>](configure-services-and-applications.md)
