---
title: Office 365 僅限雲端身分識別
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
description: 說明如何建立使用者和群組，您的 Office 365 訂閱使用僅限雲端身分識別時。
ms.openlocfilehash: 5991ec838321187b58f913e1707efb2ede9912fb
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072275"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="227f8-103">Office 365 僅限雲端身分識別</span><span class="sxs-lookup"><span data-stu-id="227f8-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="227f8-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="227f8-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="227f8-105">僅限雲端身分識別，所有您的使用者、 群組和連絡人會儲存在您的 Office 365 訂閱的 Azure Active Directory (Azure AD) 租用戶。</span><span class="sxs-lookup"><span data-stu-id="227f8-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="227f8-106">以下是僅限雲端身分識別的基本元件。</span><span class="sxs-lookup"><span data-stu-id="227f8-106">Here are the basic components of cloud-only identity.</span></span>
 
![僅限雲端身分識別的基本元件](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="227f8-108">使用者和其組織中的使用者帳戶可以數種方式進行分類。</span><span class="sxs-lookup"><span data-stu-id="227f8-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="227f8-109">例如，有些是員工，而且已永久的狀態。</span><span class="sxs-lookup"><span data-stu-id="227f8-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="227f8-110">有些是廠商、 承包商或協力廠商的暫時狀態。</span><span class="sxs-lookup"><span data-stu-id="227f8-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="227f8-111">有些是不有任何使用者帳戶，但必須仍可存取權授與特定的服務和資源，以支援互動與共同作業的外部使用者。</span><span class="sxs-lookup"><span data-stu-id="227f8-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="227f8-112">例如：</span><span class="sxs-lookup"><span data-stu-id="227f8-112">For example:</span></span>

- <span data-ttu-id="227f8-113">租用戶帳戶代表您為雲端服務授權之組織內的使用者</span><span class="sxs-lookup"><span data-stu-id="227f8-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="227f8-114">企業對企業 (B2B) 帳戶代表您邀請參與共同作業採取庫存類型的使用者至您的組織中您組織外的使用者。</span><span class="sxs-lookup"><span data-stu-id="227f8-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="227f8-115">什麼是群組？</span><span class="sxs-lookup"><span data-stu-id="227f8-115">What are the groupings?</span></span> <span data-ttu-id="227f8-116">例如，您可以至您的組織群組的使用者使用高階的函數或用途。</span><span class="sxs-lookup"><span data-stu-id="227f8-116">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="227f8-p104">此外，某些雲端服務可以與組織外的使用者共用，而不需使用任何使用者帳戶。您也必須識別使用者的這些群組。</span><span class="sxs-lookup"><span data-stu-id="227f8-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="227f8-119">您可以使用群組為了簡化管理雲端環境的幾個 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="227f8-119">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="227f8-120">例如，Azure AD 群組，您可以進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="227f8-120">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="227f8-121">使用以群組為基礎來指派授權運作的 Office 365 到您的使用者帳戶會自動為他們新增授權。</span><span class="sxs-lookup"><span data-stu-id="227f8-121">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="227f8-122">根據使用者帳戶屬性 (例如部門) 以動態方式將使用者帳戶新增至特定群組。</span><span class="sxs-lookup"><span data-stu-id="227f8-122">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="227f8-123">為軟體即服務 (SaaS) 應用程式自動佈建使用者，並透過多重要素驗證和其他條件式存取規則來保護對這些應用程式的存取權。</span><span class="sxs-lookup"><span data-stu-id="227f8-123">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="227f8-124">佈建權限和 SharePoint Online 小組網站的存取層級。</span><span class="sxs-lookup"><span data-stu-id="227f8-124">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="227f8-125">您可以建立新的***使用者***使用：</span><span class="sxs-lookup"><span data-stu-id="227f8-125">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="227f8-126">Microsoft 365 系統管理中心</span><span class="sxs-lookup"><span data-stu-id="227f8-126">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="227f8-127">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="227f8-127">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="227f8-128">您可以建立新的***群組***與：</span><span class="sxs-lookup"><span data-stu-id="227f8-128">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="227f8-129">Microsoft 365 系統管理中心</span><span class="sxs-lookup"><span data-stu-id="227f8-129">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="227f8-130">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="227f8-130">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="227f8-131">僅限雲端身分識別的下一個步驟</span><span class="sxs-lookup"><span data-stu-id="227f8-131">Next step for cloud-only identities</span></span>

[<span data-ttu-id="227f8-132">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="227f8-132">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
