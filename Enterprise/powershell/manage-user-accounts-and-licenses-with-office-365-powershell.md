---
title: 使用 Office 365 PowerShell 管理使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 摘要： 了解如何管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組。
ms.openlocfilehash: ebc3038cf244c651ebbf98c10bb7992268d8f5dd
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886452"
---
# <a name="manage-user-accounts-licenses-and-groups-with-office-365-powershell"></a><span data-ttu-id="9e01e-103">管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組</span><span class="sxs-lookup"><span data-stu-id="9e01e-103">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="9e01e-104">下列其中一個任何 Office 365 系統管理員的主要工作管理使用者帳戶、 授權及群組。</span><span class="sxs-lookup"><span data-stu-id="9e01e-104">One of the primary tasks of any Office 365 administrator is managing user accounts, licenses, and group.</span></span> <span data-ttu-id="9e01e-105">雖然您可以完成這些工作的 Microsoft 365 系統管理中心中的大部分層面，其他工作將會更快且更容易使用 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e01e-105">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell.</span></span> 

<span data-ttu-id="9e01e-106">如需詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="9e01e-106">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="9e01e-107">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-107">User accounts</span></span>

- [<span data-ttu-id="9e01e-108">建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-108">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-109">檢視使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-109">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-110">設定使用者帳戶設定</span><span class="sxs-lookup"><span data-stu-id="9e01e-110">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-111">指派角色給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-111">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-112">刪除和還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-112">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-113">封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-113">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="9e01e-114">授權與服務</span><span class="sxs-lookup"><span data-stu-id="9e01e-114">Licenses and services</span></span>
- [<span data-ttu-id="9e01e-115">檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="9e01e-115">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-116">檢視授權和未授權使用者</span><span class="sxs-lookup"><span data-stu-id="9e01e-116">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-117">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9e01e-117">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-118">檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e01e-118">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-119">停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="9e01e-119">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="9e01e-120">停用 Sway 存取權</span><span class="sxs-lookup"><span data-stu-id="9e01e-120">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="9e01e-121">停用服務存取權，並指派使用者授權</span><span class="sxs-lookup"><span data-stu-id="9e01e-121">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="9e01e-122">從使用者帳戶移除授權</span><span class="sxs-lookup"><span data-stu-id="9e01e-122">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="9e01e-123">群組</span><span class="sxs-lookup"><span data-stu-id="9e01e-123">Groups</span></span>
- [<span data-ttu-id="9e01e-124">維護群組成員資格</span><span class="sxs-lookup"><span data-stu-id="9e01e-124">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="9e01e-125">管理 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="9e01e-125">Manage Office 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

