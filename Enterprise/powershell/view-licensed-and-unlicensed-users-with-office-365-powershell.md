---
title: 使用 Office 365 PowerShell 檢視經授權與未經授權的使用者
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.openlocfilehash: d182e53992b189e8ede52e6d133b864a17ba7232
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914868"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 檢視經授權與未經授權的使用者

**摘要：** 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。
  
在您的 Office 365 組織中的使用者帳戶，可能具有從組織的可用授權方案指派給他們的部分授權、全部授權或完全沒有授權。您可以使用 Office 365 PowerShell 快速尋找組織中的經授權和未經授權的使用者。
  
## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 如果您使用 **Get-MsolUser** Cmdlet，而不使用 _-All_參數，則只會傳回前 500 個帳戶。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡短版本 (不含說明的指示)

本節僅呈現程序，但不提供詳盡或多餘的說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。
  
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

## <a name="the-long-version-instructions-with-detailed-explanations"></a>冗長版本 (包含詳細說明的指示)

Office 365 使用者帳戶和 Office 365 授權不需要有一對一的對應關係： 很可能有不具有 Office 365 授權、 Office 365 使用者很可能已尚未被指派給使用者的 Office 365 授權。（事實上，單一使用者帳戶可以即使有*多個*Office 365 的授權）。當您建立新的 Office 365 使用者帳戶 （請參閱下列文章[指派授權指派給 Office 365 powershell 的使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)的詳細資訊） 您沒有指派授權給使用者： 新的使用者會具有有效的帳戶，但他就是看不到簽章Office 365 中 n。如果嘗試登入，他們看到類似：
  
![沒有有效 Office 365 授權的使用者。](media/o365-powershell-no-license.png)
  
同樣地，您可能會有使用者請長假，或許是學術休假或產假/陪產假。在那樣的情況下，您可以移除該使用者的授權，但是維持使用者帳戶原封不動 (也就是將其地址、電話號碼等所有屬性值維持原樣)。如此一來，您就可以將該授權指派給其他人 (例如替補請假人員的臨時員工)。當該使用者返回工作崗位時，您可以發給他們新的授權，他們將能夠繼續工作，彷彿從未離開過一般。
  
這明白表示了，是的，您可以讓使用者擁有帳戶但沒有授權。反之亦然。
  
[使用 Office 365 PowerShell 檢視授權與服務](view-licenses-and-services-with-office-365-powershell.md) 一文說明如何判斷您的組織已購買的 Office 365 授權數，以及其中有多少個授權已指派給使用者。這是很重要的資訊。但同樣重要的是，要如何得知您的哪些使用者已被指派這些授權，哪些沒有？本文將告訴您如何得知這些資訊。
  
您可能知道， **Get-MsolUser** 指令程式會傳回與您所有的 Office 365 使用者帳戶有關的資訊。想要快速取得您所有 Office 365 使用者的相關資訊？請在 Office 365 PowerShell 中執行此命令：
  
```
Get-MsolUser
```

接著，Get-MsolUser 會傳回類似以下的資料：
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

如您所見，其中一個傳回的屬性值是 **isLicensed** 屬性的值。如果 **isLicensed** 等於 `False`，表示使用者沒有 Office 365 的授權。換句話說，如果您想要的話，只要捲動使用者清單並挑出 **isLicensed** 屬性設定為 `False` 的使用者即可。
  
無論如何，只要您的使用者數目相對較少，就適合採用捲動使用者清單並嘗試挑出未授權之使用者的方式。不過，如果您有大量的使用者，捲動清單充其量將會非常冗長乏味。(並且，就 Windows PowerShell 的設定方式而言，可能完全不可能。這是因為，Windows PowerShell 主控台在任一時間點能夠顯示的輸出行數是有限制的。)
  
考量到這一點，若要列出您的未授權使用者，更好的方法是改為執行這個命令：
  
```
Get-MsolUser -UnlicensedUsersOnly
```

這個命令只會傳回沒有 Office 365 授權的使用者。換句話說：
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

如您所見，我們有一位未授權的使用者。而我們想要的不正是 *授權*  使用者清單嗎？那是更複雜的細節，但差異總在細節中：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

那個會尋找 **isLicensed** 內容等於 `True` 的所有使用者帳戶的命令，傳回如下資訊：
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

如您所見，其中並未傳回 Belinda Newman 的資訊。為什麼？您知道的：因為 Belinda 的帳戶未將 **isLicensed** 屬性設為 `True`。
  
## <a name="see-also"></a>另請參閱

如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

