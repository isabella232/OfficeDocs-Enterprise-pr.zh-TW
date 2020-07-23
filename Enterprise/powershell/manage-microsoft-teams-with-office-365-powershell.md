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
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230609"
---
# <a name="manage-microsoft-teams-with-powershell"></a>使用 PowerShell 管理 Microsoft 團隊

*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*

您可以使用 PowerShell 來管理 Microsoft 團隊。
  
首先，安裝[Microsoft 小組模組](https://www.powershellgallery.com/packages/MicrosoftTeams/)。
    
## <a name="sign-in-with-a-user-name-and-password"></a>使用使用者名稱和密碼登入

針對 Office 365 全球（+ GCC）雲端：

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

針對 Office 365 美國政府 DoD cloud： 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

對於 Office 365 美國政府版 GCC 高 cloud：

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>使用多重要素驗證（MFA）登入

針對 Office 365 全球（+ GCC）雲端：

```powershell
Connect-MicrosoftTeams
```

針對 Office 365 美國政府 DoD cloud： 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

對於 Office 365 美國政府版 GCC 高 cloud：

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>與 Microsoft 團隊中斷連線

請使用下列命令：

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>請參閱

[小組 PowerShell 概述](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 的 PowerShell 快速入門](getting-started-with-office-365-powershell.md)

