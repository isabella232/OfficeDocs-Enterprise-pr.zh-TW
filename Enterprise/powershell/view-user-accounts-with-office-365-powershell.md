---
title: "檢視與 Office 365 PowerShell 的使用者帳戶"
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "摘要： 檢視、 清單或顯示您的使用者帳戶的各種方式與 Office 365 PowerShell。"
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a>檢視與 Office 365 PowerShell 的使用者帳戶

 **摘要：**檢視、 清單或顯示您的使用者帳戶的各種方式與 Office 365 PowerShell。
  
雖然您可以使用 Office 365 系統管理中心檢視您的 Office 365 租用戶帳戶，您也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。
  
## <a name="before-you-begin"></a>開始之前

本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="display-office-365-user-account-information"></a>顯示 Office 365 使用者帳戶資訊

若要顯示的使用者帳戶的完整清單，請在您的 Office 365 PowerShell 命令提示字元或 PowerShell 整合式指令碼環境 (ISE) 執行此命令。
  
```
Get-MsolUser
```

您應該會看到與下面類似的資訊：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-msoluser** cmdlet 也會有一組參數來篩選顯示的使用者帳戶的設定。例如，未授權使用者 （使用者已加入至 Office 365 但尚未尚未被授權使用任何服務） 的清單，請執行此命令。
  
```
Get-MsolUser -UnlicensedUsersOnly
```

您應該會看到與下面類似的資訊：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

篩選顯示的其他參數的詳細資訊的一組使用者帳戶顯示，請參閱[Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) 。
  
為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get-msoluser** cmdlet。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Office 365 PowerShell 進行一個命令的結果，並將其傳送給下一個命令。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
您應該會看到與下面類似的資訊：
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

例如，此清單中，從**City**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 會針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人**-lt** > [值] 通常是一個字串 （的字母、 數字及其他任何字元序列），未指定的數值或**$Null**的 > 查看[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx)如需詳細資訊。
  
您可以檢查封鎖的狀態之使用者帳戶具有下列命令：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>選取要顯示的使用者帳戶內容

根據預設[Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet 會顯示使用者帳戶的三個的屬性：
  
- UserPrincipalName
    
- DisplayName
    
- 尋找 isLicensed
    
如果您需要額外的內容，例如使用者的部門和使用者使用 Office 365 服務的所在國家/地區您可以執行**Get-msoluser**一起**Select-object**指令程式來指定的使用者帳戶清單屬性。以下是範例：
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。
    
您應該會看到與下面類似的資訊：
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

**Select-object**指令程式可讓您挑選您想要顯示的命令的屬性。若要查看所有的使用者帳戶屬性，使用萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

若要為多個選擇性有關要顯示的帳戶清單您也可以使用**Where-object**指令程式。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
- 顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。
    
您應該會看到與下面類似的資訊：
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>使用 Azure Active Directory V2 PowerShell 模組來顯示使用者帳戶

若要顯示的使用者帳戶使用 Azure Active Directory V2 PowerShell 模組屬性，您可以使用[Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0)指令程式。但首先，您必須連線到您的訂閱。指示，請參閱[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
### <a name="display-office-365-user-account-information"></a>顯示 Office 365 使用者帳戶資訊

若要顯示的使用者帳戶的完整清單，請在您的 Office 365 PowerShell 命令提示字元或 PowerShell 整合式指令碼環境 (ISE) 執行此命令。
  
```
Get-AzureADUser
```

依預設**取得 AzureADUser**指令程式將顯示使用者帳戶的三個的屬性：
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get AzureADUser**指令程式。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Office 365 PowerShell 進行一個命令的結果，並將其傳送給下一個命令。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （*） 來顯示其所有針對特定的使用者帳戶，一次 （**更多**） 一個頁面。以下是範例：
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

例如， **-市/鎮**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 會針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人**-lt** > [值] 通常是一個字串 （的字母、 數字及其他任何字元序列），未指定的數值或**$Null**的 > 查看[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx)如需詳細資訊。
  
### <a name="select-the-user-account-properties-to-display"></a>選取要顯示的使用者帳戶內容

依預設**取得 AzureADUser**指令程式會顯示使用者帳戶 ObjectID、 DisplayName 及 UserPrincipalName 屬性。如果您需要額外的內容，例如使用者的部門和使用者使用 Office 365 服務的所在國家/地區您可以執行**Get AzureADUser**一起**Select-object**指令程式來指定使用者的清單帳戶的屬性。以下是範例：
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。
    
若要為多個選擇性有關要顯示的帳戶清單您也可以使用**Where-object**指令程式。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
- 顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。
    
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

