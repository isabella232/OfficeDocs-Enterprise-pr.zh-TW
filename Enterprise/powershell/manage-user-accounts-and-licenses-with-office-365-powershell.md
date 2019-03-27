---
title: 使用 Office 365 PowerShell 管理使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 摘要：了解如何使用 Office 365 PowerShell 來管理使用者帳戶和授權。
ms.openlocfilehash: 604f0e6926936473f4b8e13546cdf0d7d839c667
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573887"
---
# <a name="manage-user-accounts-and-licenses-with-office-365-powershell"></a><span data-ttu-id="c1a63-103">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-103">Manage user accounts and licenses with Office 365 PowerShell</span></span>

 <span data-ttu-id="c1a63-104">**摘要：** 了解如何使用 Office 365 PowerShell 來管理使用者帳戶和授權。</span><span class="sxs-lookup"><span data-stu-id="c1a63-104">**Summary:** Learn how to manage user accounts and licenses with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="c1a63-105">任何 Office 365 系統管理員的其中一個主要工作是管理使用者帳戶和授權。</span><span class="sxs-lookup"><span data-stu-id="c1a63-105">One of the primary tasks of any Office 365 administrator is managing user accounts and licenses.</span></span> <span data-ttu-id="c1a63-106">雖然您可以在 Microsoft 365 系統管理中心中完成其中一些工作，但是使用 Office 365 PowerShell 可以更快速、更輕鬆地完成其他工作。</span><span class="sxs-lookup"><span data-stu-id="c1a63-106">Although you can accomplish some of these tasks in the Office 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell.</span></span> <span data-ttu-id="c1a63-107">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="c1a63-107">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="c1a63-108">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="c1a63-108">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-109">使用 Office 365 PowerShell 檢視經授權與未經授權的使用者</span><span class="sxs-lookup"><span data-stu-id="c1a63-109">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-110">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-110">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-111">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="c1a63-111">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-112">將角色指派給 Office 365 powershell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-112">Assign roles to user accounts with Office 365 PowerShell</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-113">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="c1a63-113">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-114">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="c1a63-114">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-115">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-115">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-116">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-116">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-117">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-117">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-118">檢視與 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c1a63-118">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c1a63-119">使用 Office 365 PowerShell 中設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="c1a63-119">Configure user account properties with Office 365 PowerShell</span></span>](configure-user-account-properties-with-office-365-powershell.md)
    

