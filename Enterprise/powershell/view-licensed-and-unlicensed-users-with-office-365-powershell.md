---
title: 使用 Office 365 PowerShell 檢視經授權與未經授權的使用者
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123360"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 檢視經授權與未經授權的使用者

**摘要：** 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。
  
在您的 Office 365 組織中的使用者帳戶，可能具有從組織的可用授權方案指派給他們的部分授權、全部授權或完全沒有授權。您可以使用 Office 365 PowerShell 快速尋找組織中的經授權和未經授權的使用者。
  
## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 如果您使用 **Get-MsolUser** Cmdlet，而不使用 _-All_參數，則只會傳回前 500 個帳戶。
    
## <a name="viewing-licensed-and-unlicensed-users"></a>檢視授權和未授權使用者

若要檢視您組織中所有使用者帳戶及其授權狀態的清單，在 Office 365 PowerShell 中執行下列命令：
  
```
Get-MsolUser -All
```

若要檢視您組織中所有未經授權使用者帳戶的清單，執行下列命令：
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

若要檢視您組織中所有經授權使用者帳戶的清單，執行下列命令：
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>另請參閱

如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

