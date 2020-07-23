---
title: 使用 PowerShell 管理 Microsoft 365 使用者帳戶、授權和群組
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
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 摘要：瞭解如何使用 PowerShell 來管理 Microsoft 365 使用者帳戶、授權和群組。
ms.openlocfilehash: 26da0d13ecc9c14be4abe059943bd91d88126f1e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230409"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="b0031-103">使用 PowerShell 管理 Microsoft 365 使用者帳戶、授權和群組</span><span class="sxs-lookup"><span data-stu-id="b0031-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="b0031-104">*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="b0031-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b0031-105">任何 Microsoft 365 系統管理員的主要工作之一是管理使用者帳戶、授權和群組。</span><span class="sxs-lookup"><span data-stu-id="b0031-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="b0031-106">雖然您可以在 Microsoft 365 系統管理中心完成這些工作的大部分，但其他工作使用 PowerShell 會更快速且更容易。</span><span class="sxs-lookup"><span data-stu-id="b0031-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="b0031-107">如需詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="b0031-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="b0031-108">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-108">User accounts</span></span>

- [<span data-ttu-id="b0031-109">建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-110">檢視使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-111">設定使用者帳戶設定</span><span class="sxs-lookup"><span data-stu-id="b0031-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-112">指派角色給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-113">刪除和還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-114">封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="b0031-115">授權與服務</span><span class="sxs-lookup"><span data-stu-id="b0031-115">Licenses and services</span></span>
- [<span data-ttu-id="b0031-116">檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="b0031-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-117">檢視授權和未授權使用者</span><span class="sxs-lookup"><span data-stu-id="b0031-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-118">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="b0031-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-119">檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="b0031-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-120">停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="b0031-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="b0031-121">停用 Sway 存取權</span><span class="sxs-lookup"><span data-stu-id="b0031-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="b0031-122">停用服務存取權，並指派使用者授權</span><span class="sxs-lookup"><span data-stu-id="b0031-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="b0031-123">從使用者帳戶移除授權</span><span class="sxs-lookup"><span data-stu-id="b0031-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="b0031-124">群組</span><span class="sxs-lookup"><span data-stu-id="b0031-124">Groups</span></span>
- [<span data-ttu-id="b0031-125">維護群組成員資格</span><span class="sxs-lookup"><span data-stu-id="b0031-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="b0031-126">管理 Microsoft 365 群組</span><span class="sxs-lookup"><span data-stu-id="b0031-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

