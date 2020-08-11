---
title: 以 PowerShell 管理 Microsoft 365 使用者帳戶、授權和群組
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 在本文中，您將瞭解如何使用 PowerShell 來管理 Microsoft 365 使用者帳戶、授權和群組。
ms.openlocfilehash: b5a2d43ad4dee3a70f934f9fc52b93e7c99f3644
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605879"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="de4aa-103">以 PowerShell 管理 Microsoft 365 使用者帳戶、授權和群組</span><span class="sxs-lookup"><span data-stu-id="de4aa-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="de4aa-104">*本文適用於 Microsoft 365 企業版和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="de4aa-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="de4aa-105">任何 Microsoft 365 系統管理員的主要工作之一是管理使用者帳戶、授權和群組。</span><span class="sxs-lookup"><span data-stu-id="de4aa-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="de4aa-106">雖然您可以在 Microsoft 365 系統管理中心完成這些工作的大部分，但其他工作使用 PowerShell 會更快速且更容易。</span><span class="sxs-lookup"><span data-stu-id="de4aa-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="de4aa-107">如需詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="de4aa-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="de4aa-108">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-108">User accounts</span></span>

- [<span data-ttu-id="de4aa-109">建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-110">檢視使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-111">設定使用者帳戶設定</span><span class="sxs-lookup"><span data-stu-id="de4aa-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-112">指派角色給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-113">刪除和還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-114">封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="de4aa-115">授權與服務</span><span class="sxs-lookup"><span data-stu-id="de4aa-115">Licenses and services</span></span>
- [<span data-ttu-id="de4aa-116">檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="de4aa-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-117">檢視授權和未授權使用者</span><span class="sxs-lookup"><span data-stu-id="de4aa-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-118">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="de4aa-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-119">檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="de4aa-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-120">停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="de4aa-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="de4aa-121">停用 Sway 存取權</span><span class="sxs-lookup"><span data-stu-id="de4aa-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="de4aa-122">停用服務存取權，並指派使用者授權</span><span class="sxs-lookup"><span data-stu-id="de4aa-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="de4aa-123">從使用者帳戶移除授權</span><span class="sxs-lookup"><span data-stu-id="de4aa-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="de4aa-124">群組</span><span class="sxs-lookup"><span data-stu-id="de4aa-124">Groups</span></span>
- [<span data-ttu-id="de4aa-125">維護群組成員資格</span><span class="sxs-lookup"><span data-stu-id="de4aa-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="de4aa-126">管理 Microsoft 365 群組</span><span class="sxs-lookup"><span data-stu-id="de4aa-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

