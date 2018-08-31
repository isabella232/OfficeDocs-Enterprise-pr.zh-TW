---
title: 使用集中式部署 PowerShell cmdlet 管理的增益集
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 可協助您部署及管理 Office 增益集的 Office 365 組織中使用的集中式部署 PowerShell cmdlet。
ms.openlocfilehash: 6199ad2d37a11166155b898b52d52304836599d0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540174"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>使用集中式部署 PowerShell cmdlet 管理的增益集

為 Office 365 系統管理員，您可對透過集中式部署的使用者部署 Office 增益集 （請參閱[部署 Office 增益集在 Office 365 系統管理中心](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)） 的功能。除了部署 Office 增益集透過 Office 365 系統管理中心，您也可以使用 Microsoft PowerShell。[下載](https://go.microsoft.com/fwlink/p/?linkid=850850)從 Microsoft 下載中心的集中式部署 PowerShell cmdlet。 
    
## <a name="connect-using-your-admin-credentials"></a>使用系統管理認證連線

您可以使用集中式部署 cmdlet 之前，您必須登入。
  
1. 啟動 PowerShell。
    
2. 使用您公司的系統管理認證連線至 PowerShell。執行下列 cmdlet。
    
  ```
  Connect-OrganizationAddInService
  ```

3. 在 [**輸入認證**] 頁面上，輸入您的 Office 365 全域管理員認證。或者，您可以在指令程式會將直接輸入您的認證。 
    
    執行下列 cmdlet 以指定您的公司系統管理員認證以 PSCredential 物件。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> 如需使用 PowerShell 的詳細資訊，請參閱 ＜ [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。 
  
## <a name="upload-an-add-in-manifest"></a>上傳的增益集資訊清單

執行新增 OrganizationAdd 中指令程式上傳的增益集資訊清單可以是檔案位置或 URL 路徑中。下列範例會顯示_ManifestPath_參數的值的檔案位置。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

您也可以執行新增 OrganizationAdd 中指令程式上傳增益集並將其指派給使用者或群組直接使用_Members_參數，如下列範例所示。請使用逗號分隔成員的電子郵件地址。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>上傳增益集來自 Office 市集

執行新增 OrganizationAddIn 指令程式上傳來自 Office 市集資訊清單。
  
在下列範例中，新增 OrganizationAddIn 指令程式會指定增益集的美國位置及內容市場的 AssetId。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

若要判斷_AssetId_參數的值，您可以從 Office 市集的增益集 AssetIds 網頁一律開始"WA"後面的號碼與 URL 複製。例如，在先前的範例中，WA104099688 AssetId 值的來源是 Office 市集網頁 URL 增益集： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_Locale_參數與_ContentMarket_參數的值是相同的並指出您嘗試安裝增益集從國家/地區。格式為 EN-US、 fr FR.等等。 
  
> [!NOTE]
> 增益集來自 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。 
  
## <a name="get-details-of-an-add-in"></a>取得增益集的詳細資料

執行如下所示 Get OrganizationAddIn 指令程式取得上傳至租用戶，所有增益集的詳細資料包含增益集的產品識別碼。
  
```
Get-OrganizationAddIn
```

執行 Get OrganizationAddIn cmdlet _ProductId_參數來指定的增益集您想要擷取的詳細資料的值。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

若要取得之所有增益集加上指定的使用者和群組的完整詳細資料，管道輸出至 Format-list 指令程式，取得 OrganizationAddIn 指令程式在下列範例所示。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>開啟或關閉 [增益集

若要關閉增益集，讓使用者和群組指派給它將不再有存取] 設 OrganizationAddIn 指令程式_ProductId_參數且執行_Enabled_參數設為`$false`，如下列範例所示。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

若要重新打開增益集，執行相同的指令程式使用_Enabled_參數設為`$true`。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>新增或移除使用者增益集

若要將使用者及群組新增至特定的增益集，執行_ProductId_、 _Add_、 和_成員_的參數組 OrganizationAddInAssignments 指令程式。請使用逗號分隔成員的電子郵件地址。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要移除的使用者與群組，執行相同 cmdlet_移除_參數。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要指派增益集租用戶的所有使用者，執行相同的指令程式使用_AssignToEveryone_參數值設為`$true`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

不將增益集指派給任何人並還原先前指派的使用者和群組，您可以執行相同的指令程式並將其值設定為關閉_AssignToEveryone_參數`$false`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>更新增益集

若要更新增益集資訊清單中，執行組 OrganizationAddIn cmdlet _ProductId_、 _ManifestPath_、 和_地區設定_參數，如下列範例所示。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> 增益集來自 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。 
  
## <a name="delete-an-add-in"></a>刪除增益集

若要刪除增益集，執行移除 OrganizationAddIn 指令程式與 [ _ProductId_ ] 參數，如下列範例所示。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>取得詳細的說明每個指令程式

您可以使用 get-help 指令程式來查看每個 cmdlet 的詳細說明。例如，下列指令程式提供移除 OrganizationAddIn 指令程式的詳細的資訊。
  
```
Get-help Remove-OrganizationAddIn -Full
```


