---
title: 將 Office 365 授權指派給使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何將 Office 365 授權指派給使用者帳戶，或是個別或根據群組成員資格。
ms.openlocfilehash: 169f5a3c0bf75bf807c40338542e0ba15b79a1bc
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813381"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="59a05-103">將 Office 365 授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="59a05-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="59a05-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="59a05-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="59a05-105">僅限雲端身分識別模型的可以將 Office 365 授權指派給使用者帳戶為他們所建立，根據您建立的方式。</span><span class="sxs-lookup"><span data-stu-id="59a05-105">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="59a05-106">對於混合式身分識別模型中，第一次同步處理 Active Directory 網域服務 (AD DS) 的使用者帳戶時它們不會自動指派 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="59a05-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="59a05-107">在任一情況中，您必須指派授權給使用者帳戶讓您的使用者可以存取 Office 365 服務，例如電子郵件和 Microsoft Teams。</span><span class="sxs-lookup"><span data-stu-id="59a05-107">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="59a05-108">您可以透過群組成員資格，個別或自動指派授權給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="59a05-108">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="59a05-109">若要將 Office 365 授權指派給個別使用者帳戶，您可以使用：</span><span class="sxs-lookup"><span data-stu-id="59a05-109">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="59a05-110">Microsoft 365 系統管理中心</span><span class="sxs-lookup"><span data-stu-id="59a05-110">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="59a05-111">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59a05-111">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="59a05-112">自動授權指派]，請參閱[在 Azure AD 群組為基礎的授權](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="59a05-112">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="59a05-113">後續步驟</span><span class="sxs-lookup"><span data-stu-id="59a05-113">Next steps</span></span>

<span data-ttu-id="59a05-114">已指派授權的使用者帳戶的完整設定之後，現在已準備要：</span><span class="sxs-lookup"><span data-stu-id="59a05-114">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="59a05-115">實作的安全性</span><span class="sxs-lookup"><span data-stu-id="59a05-115">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="59a05-116">部署用戶端軟體，例如 Office 365 專業增強版</span><span class="sxs-lookup"><span data-stu-id="59a05-116">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="59a05-117">設定 Office 365 中的行動裝置管理</span><span class="sxs-lookup"><span data-stu-id="59a05-117">Set up Mobile Device Management in Office 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="59a05-118">設定服務及應用程式</span><span class="sxs-lookup"><span data-stu-id="59a05-118">Configure services and applications</span></span>](configure-services-and-applications.md)
