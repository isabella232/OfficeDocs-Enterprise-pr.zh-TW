---
title: 使用 PowerShell 管理 Microsoft 團隊
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要：使用 PowerShell 來管理 Microsoft 團隊。
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429190"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="f1d3f-103">使用 PowerShell 管理 Microsoft 團隊</span><span class="sxs-lookup"><span data-stu-id="f1d3f-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="f1d3f-104">*本文適用於 Microsoft 365 企業版和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="f1d3f-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f1d3f-105">您可以使用 PowerShell 來管理 Microsoft 團隊。</span><span class="sxs-lookup"><span data-stu-id="f1d3f-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="f1d3f-106">首先，安裝[Microsoft 小組模組](https://www.powershellgallery.com/packages/MicrosoftTeams/)。</span><span class="sxs-lookup"><span data-stu-id="f1d3f-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="f1d3f-107">使用使用者名稱和密碼登入</span><span class="sxs-lookup"><span data-stu-id="f1d3f-107">Sign in with a user name and password</span></span>

<span data-ttu-id="f1d3f-108">針對 Office 365 全球（+ GCC）雲端：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="f1d3f-109">針對 Office 365 美國政府 DoD cloud：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="f1d3f-110">對於 Office 365 美國政府版 GCC 高 cloud：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="f1d3f-111">使用多重要素驗證（MFA）登入</span><span class="sxs-lookup"><span data-stu-id="f1d3f-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="f1d3f-112">針對 Office 365 全球（+ GCC）雲端：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="f1d3f-113">針對 Office 365 美國政府 DoD cloud：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="f1d3f-114">對於 Office 365 美國政府版 GCC 高 cloud：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="f1d3f-115">與 Microsoft 團隊中斷連線</span><span class="sxs-lookup"><span data-stu-id="f1d3f-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="f1d3f-116">請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="f1d3f-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="f1d3f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1d3f-117">See also</span></span>

[<span data-ttu-id="f1d3f-118">小組 PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="f1d3f-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="f1d3f-119">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f1d3f-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f1d3f-120">開始使用適用於 Microsoft 365 的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1d3f-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

