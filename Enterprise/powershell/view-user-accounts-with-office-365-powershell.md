---
title: 檢視與 Office 365 PowerShell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: 摘要： 檢視、 清單或顯示您的使用者帳戶的各種方式與 Office 365 PowerShell。
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730318"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>檢視與 Office 365 PowerShell 的使用者帳戶

**摘要：** 使用 Office 365 PowerShell 的各種方式檢視您的使用者帳戶。
  
雖然您可以使用 Office 365 系統管理中心檢視您的 Office 365 租用戶帳戶，您也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 圖模組

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
### <a name="view-all-accounts"></a>檢視所有的帳戶

若要顯示的使用者帳戶的完整清單，請執行下列命令：
  
```
Get-AzureADUser
```

您應該會看到與下面類似的資訊：
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>檢視特定的帳戶

若要顯示特定的使用者帳戶，登入帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN) 中的填滿移除"<"和">"字元並執行下列命令：
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

範例如下：
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>檢視其他屬性值為特定帳戶

根據預設，**取得 AzureADUser**指令程式只會顯示帳戶 ObjectID、 DisplayName 及 UserPrincipalName 屬性。

為多個選擇性相關的屬性來顯示清單您可以使用**Select-object**指令程式一起**Get AzureADUser**指令程式。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Azure Active Directory PowerShell 進行一個命令的結果，並將其傳送給下一個命令的圖表。以下是範例命令會顯示每個使用者帳戶的 DisplayName、 部門及 UsageLocation：
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。
  
若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

另一個範例，您可以檢查啟用的狀態之特定使用者帳戶具有下列命令：
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>檢視一些常見的屬性為基礎的帳戶

為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get AzureADUser**指令程式。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Azure Active Directory PowerShell 進行一個命令的結果，並將其傳送給下一個命令的圖表。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

此命令會指示的 Graph 設為 Azure Active Directory PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

例如，此清單中，從**City**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 會針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人 **-lt** 。 [值] 是一般的字串 （的字母、 數字及其他任何字元序列）、 數字值或 **$Null**未指定 > 查看[Where-object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)如需詳細資訊。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模組

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="view-all-accounts"></a>檢視所有的帳戶

若要顯示的使用者帳戶的完整清單，請執行下列命令：
  
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

篩選顯示的其他參數的詳細資訊的一組使用者帳戶顯示，請參閱[Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。
  

### <a name="view-a-specific-account"></a>檢視特定的帳戶

若要顯示特定的使用者帳戶，登入的使用者帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN) 中的填滿移除"<"和">"字元並執行下列命令：
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>檢視一些常見的屬性為基礎的帳戶

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
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

例如，此清單中，從**City**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**. [比較運算子] 是針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人 **-lt** 。 [值] 是通常 （的字母、 數字及其他任何字元序列） 的字串、 數字值或 **$Null**未指定。如需詳細資訊，請參閱[Where 物件](https://technet.microsoft.com/en-us/library/hh849715.aspx)。
  
您可以檢查封鎖的狀態之使用者帳戶具有下列命令：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>檢視其他屬性值的帳戶

根據預設**Get-msoluser** cmdlet 會顯示使用者帳戶的三個的屬性：
  
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
Scott Wallace           Operations
```

**Select-object**指令程式可讓您挑選您想要顯示的命令的屬性。若要查看所有的使用者帳戶屬性，使用萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
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

如果您使用目錄同步作業來建立及管理 Office 365 使用者，可以顯示 Office 365 使用者具有已預估來自哪個本機帳戶。下列假設 Azure AD 連接有已設定為使用預設來源錨點的 objectguid 資訊 (如需設定來源錨點的詳細資訊，請參閱[Azure AD 連線： 設計概念](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) 和假設有 powershell 的 Active Directory 模組已安裝 （請參閱[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

