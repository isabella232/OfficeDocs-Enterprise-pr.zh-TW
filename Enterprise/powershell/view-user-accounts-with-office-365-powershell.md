---
title: 檢視與 Office 365 PowerShell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 摘要： 檢視、 清單，或使用 Office 365 PowerShell 的各種方式顯示您的使用者帳戶。
ms.openlocfilehash: ca4bd7effea39632f8a30c192e0f703a289c7b71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844124"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>檢視與 Office 365 PowerShell 的使用者帳戶

雖然您可以使用 Microsoft 365 系統管理中心，來檢視您的 Office 365 租用戶帳戶，也可以使用 Office 365 PowerShell 並執行動作無法在系統管理中心的一些事項。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
### <a name="view-all-accounts"></a>檢視所有帳戶

若要顯示的使用者帳戶的完整清單，請執行下列命令：
  
```powershell
Get-AzureADUser
```

您應該會看到類似的資訊：
  
```powershell
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

若要顯示特定的使用者帳戶，請填寫登入帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN)、 移除 「 < 」 及 「 > 」 字元，並執行此命令：
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

範例如下：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>檢視為特定帳戶的其他屬性值

根據預設，**取得 AzureADUser**指令程式只會顯示帳戶 ObjectID、 DisplayName 及 UserPrincipalName 屬性。

為多個選擇性相關的屬性若要顯示，清單您可以使用**選取**cmdlet**取得 AzureADUser**指令程式搭配。 若要合併的兩個 cmdlet，我們使用 「 管道 」 字元"| 」，這會告知 Azure Active Directory PowerShell 的一個命令的結果並將它傳送給下一個命令的圖表。 以下是範例命令，會顯示名稱、 部門和 UsageLocation 顯示每個使用者帳戶：
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 顯示僅限的使用者帳戶名稱、 部門和使用位置 （ **Select DisplayName、 Department、 UsageLocation** ）。
  
若要查看所有的使用者帳戶的內容，用於**選取**指令程式和萬用字元 （*） 來顯示其所有特定使用者帳戶。 範例如下：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

另一個範例，您可以檢查啟用的狀態的特定使用者帳戶使用下列命令：
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>檢視一些常見屬性為基礎的帳戶

若要為多個選擇性的帳戶來顯示，清單的相關您可以使用**其中**cmdlet**取得 AzureADUser**指令程式搭配。 若要合併的兩個 cmdlet，我們使用 「 管道 」 字元"| 」，這會告知 Azure Active Directory PowerShell 的一個命令的結果並將它傳送給下一個命令的圖表。 以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

此命令會指示 Azure Active Directory PowerShell 的 Graph 設為：
  
- 取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 尋找所有使用者帳戶具有未指定的使用狀況的位置 (**其中 {$\_。UsageLocation-eq $Null}** )。 在大括弧，此命令會指示 Office 365 PowerShell 來只尋找一組帳戶順序 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
**UsageLocation**屬性可以是其中一個使用者帳戶相關聯的許多屬性。 若要查看所有的使用者帳戶的內容，用於**選取**指令程式和萬用字元 （*） 來顯示其所有特定使用者帳戶。 範例如下：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

例如，此清單中，從**縣/市**是使用者帳戶屬性的名稱。 這表示您可以使用下列命令來列出所有住倫敦在使用者的使用者帳戶：
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  下列範例所示的**其中**cmdlet 的語法如下**其中 {$\_。** [使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 是 **-eq**等於、 **-ne 代表**不等於、 **-lt 代表**小於、 **-gt**大於，針對與其他人。  [值] 通常是 （字母、 數字及其他字元序列） 的字串、 數值或 **$Null**如未指定的>，如需詳細資訊[，](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1)請參閱。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="view-all-accounts"></a>檢視所有帳戶

若要顯示的使用者帳戶的完整清單，請執行下列命令：
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

您應該會看到類似的資訊：
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-msoluser** cmdlet 也會有一組參數來篩選顯示的使用者帳戶的集合。 例如，如未經授權的使用者 （使用者已新增至 Office 365，但尚未尚未被授權使用任何服務） 的清單，請執行此命令。
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

您應該會看到類似的資訊：
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

如需其他參數來篩選顯示一組使用者帳戶顯示，請參閱[Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。
  
### <a name="view-a-specific-account"></a>檢視特定的帳戶

若要顯示特定的使用者帳戶，請填寫登入的使用者帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN)、 移除 「 < 」 及 「 > 」 字元，並執行此命令：
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>檢視一些常見屬性為基礎的帳戶

為多個選擇性的帳戶來顯示，清單的相關您可以使用**其中**cmdlet 搭配**Get-msoluser** cmdlet。 若要合併的兩個 cmdlet，我們使用 「 管道 」 字元"|"，可告訴 Office 365 PowerShell 來執行一個命令的結果，並將其傳送至下一個命令。 以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 尋找所有使用者帳戶具有未指定的使用狀況的位置 (**其中 {$\_。UsageLocation-eq $Null}** )。 在大括弧，此命令會指示 Office 365 PowerShell 來只尋找一組帳戶順序 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
您應該會看到類似的資訊：
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation**屬性可以是其中一個使用者帳戶相關聯的許多屬性。 若要查看所有的使用者帳戶的內容，用於**選取**指令程式和萬用字元 （*） 來顯示其所有特定使用者帳戶。 範例如下：
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

例如，此清單中，從**縣/市**是使用者帳戶屬性的名稱。 這表示您可以使用下列命令來列出所有住倫敦在使用者的使用者帳戶：
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  下列範例所示的**其中**cmdlet 的語法如下**其中 {$\_。** [使用者帳戶屬性名稱][比較運算子][值]**}**.  [比較運算子] 是 **-eq**等於、 **-ne 代表**不等於、 **-lt 代表**小於、 **-gt**大於，針對與其他人。  [值] 是通常 （字母、 數字及其他字元序列） 的字串、 數值或 **$Null**未指定。 如需詳細資訊[，](https://technet.microsoft.com/library/hh849715.aspx)請參閱。
  
您可以檢查封鎖的狀態的使用者帳戶使用下列命令：
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>檢視其他屬性值的帳戶

**Get-msoluser** cmdlet，依預設會顯示使用者帳戶的三個的屬性：
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
如果您需要額外的內容，例如使用者適用於部門與使用者使用 Office 365 服務所在的國家/地區您可以執行**Get-msoluser**搭配**選取**的指令程式在指定的使用者帳戶內容清單。 範例如下：
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 顯示僅限的使用者帳戶名稱、 部門和使用位置 （ **Select DisplayName、 Department、 UsageLocation** ）。
    
您應該會看到類似的資訊：
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

**選取**指令程式可讓您挑選您想要命令，以顯示的內容。 若要查看所有的使用者帳戶的內容，使用萬用字元 （*） 來顯示全部的特定使用者帳戶。 範例如下：
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

為多個選擇性相關清單中的帳戶來顯示，您也可以使用**其中**指令程式。 以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 尋找所有使用者帳戶具有未指定的使用狀況的位置 (**其中 {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。 在大括弧，此命令會指示 Office 365 PowerShell 來只尋找一組帳戶順序 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。
    
- 顯示僅限的使用者帳戶名稱、 部門和使用位置 （ **Select DisplayName、 Department、 UsageLocation** ）。
    
您應該會看到類似的資訊：
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

如果您使用目錄同步處理來建立及管理 Office 365 使用者，您可以顯示 Office 365 使用者具有已規劃從哪個本機帳戶。 下列假設 Azure AD Connect，已設定要使用的 ObjectGUID 預設來源錨點 (如需設定來源錨點的詳細資訊，請參閱[Azure AD Connect： 設計概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts))，並假設已安裝 PowerShell 的 Active Directory 網域服務模組 （請參閱[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>另請參閱

[管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

