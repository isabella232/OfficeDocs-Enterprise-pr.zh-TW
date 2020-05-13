---
title: 使用 Office 365 PowerShell 管理 Microsoft 團隊
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要：使用 Office 365 PowerShell 管理您的 Microsoft 團隊。
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209117"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="8df06-103">使用 Office 365 PowerShell 管理 Microsoft 團隊</span><span class="sxs-lookup"><span data-stu-id="8df06-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="8df06-104">您可以使用 Office 365 PowerShell 管理 Microsoft 團隊。</span><span class="sxs-lookup"><span data-stu-id="8df06-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="8df06-105">首先，安裝[Microsoft 小組模組](https://www.powershellgallery.com/packages/MicrosoftTeams/)。</span><span class="sxs-lookup"><span data-stu-id="8df06-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="8df06-106">使用使用者名稱和密碼登入</span><span class="sxs-lookup"><span data-stu-id="8df06-106">Sign in with a user name and password</span></span>

<span data-ttu-id="8df06-107">針對 Office 365 全球（+ GCC）雲端：</span><span class="sxs-lookup"><span data-stu-id="8df06-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="8df06-108">針對 Office 365 美國政府 DoD cloud：</span><span class="sxs-lookup"><span data-stu-id="8df06-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="8df06-109">對於 Office 365 美國政府版 GCC 高 cloud：</span><span class="sxs-lookup"><span data-stu-id="8df06-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="8df06-110">使用多重要素驗證（MFA）登入</span><span class="sxs-lookup"><span data-stu-id="8df06-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="8df06-111">針對 Office 365 全球（+ GCC）雲端：</span><span class="sxs-lookup"><span data-stu-id="8df06-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="8df06-112">針對 Office 365 美國政府 DoD cloud：</span><span class="sxs-lookup"><span data-stu-id="8df06-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="8df06-113">對於 Office 365 美國政府版 GCC 高 cloud：</span><span class="sxs-lookup"><span data-stu-id="8df06-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="8df06-114">與 Microsoft 團隊中斷連線</span><span class="sxs-lookup"><span data-stu-id="8df06-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="8df06-115">請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="8df06-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="8df06-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8df06-116">See also</span></span>

[<span data-ttu-id="8df06-117">小組 PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="8df06-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="8df06-118">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="8df06-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8df06-119">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8df06-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

