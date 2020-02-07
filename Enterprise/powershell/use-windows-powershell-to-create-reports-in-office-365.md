---
title: 使用 Windows PowerShell 在 Office 365 中建立報告
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/22/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 摘要：使用 Office 365 PowerShell 來建立無法在 Microsoft 365 系統管理中心內產生的報告。
ms.openlocfilehash: 3a20c47e462bb522e1fb98ba28fb8c7cee89408c
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841240"
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="0692c-103">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="0692c-103">Use Windows PowerShell to create reports in Office 365</span></span>

<span data-ttu-id="0692c-104">Microsoft 365 系統管理中心內有許多不同的報表可供使用。</span><span class="sxs-lookup"><span data-stu-id="0692c-104">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="0692c-105">不過，這些報告只提供如此多的資訊，但有時候您需要更多。</span><span class="sxs-lookup"><span data-stu-id="0692c-105">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="0692c-106">這是當您需要 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0692c-106">That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="0692c-107">這些文章描述如何使用 Office 365 PowerShell 從您的 Office 365 租用戶取得資訊︰</span><span class="sxs-lookup"><span data-stu-id="0692c-107">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="0692c-108">使用 Office 365 PowerShell 快速入門報告：</span><span class="sxs-lookup"><span data-stu-id="0692c-108">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="0692c-109">Office 365 PowerShell 可以揭露使用系統管理中心看不到的其他資訊</span><span class="sxs-lookup"><span data-stu-id="0692c-109">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="0692c-110">Office 365 PowerShell 十分適合篩選資料</span><span class="sxs-lookup"><span data-stu-id="0692c-110">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="0692c-111">Office 365 PowerShell 可讓您輕鬆地列印或儲存資料</span><span class="sxs-lookup"><span data-stu-id="0692c-111">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="0692c-112">使用者帳戶和授權的報告：</span><span class="sxs-lookup"><span data-stu-id="0692c-112">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="0692c-113">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="0692c-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="0692c-114">使用 Office 365 PowerShell 檢視經授權與未經授權的使用者</span><span class="sxs-lookup"><span data-stu-id="0692c-114">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="0692c-115">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="0692c-115">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="0692c-116">檢視與 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="0692c-116">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="0692c-117">SharePoint Online 的報告：</span><span class="sxs-lookup"><span data-stu-id="0692c-117">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="0692c-118">使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組</span><span class="sxs-lookup"><span data-stu-id="0692c-118">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="0692c-119">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0692c-119">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="0692c-120">Exchange Online 的報告：</span><span class="sxs-lookup"><span data-stu-id="0692c-120">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="0692c-121">Display Exchange Online mailbox information with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0692c-121">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="0692c-122">Display Exchange Online reports with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0692c-122">Display Exchange Online reports with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="0692c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0692c-123">See also</span></span>

[<span data-ttu-id="0692c-124">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="0692c-124">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0692c-125">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0692c-125">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="0692c-126">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="0692c-126">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="0692c-127">管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組</span><span class="sxs-lookup"><span data-stu-id="0692c-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
