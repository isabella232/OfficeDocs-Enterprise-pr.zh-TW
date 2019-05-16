---
title: 使用集中式部署 PowerShell cmdlet 來管理增益集
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
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
description: 使用集中式部署 PowerShell cmdlet 來協助您部署及管理 Office 增益集的 Office 365 組織。
ms.openlocfilehash: 34040d11a1ef4d5da2d7a0e980b28e7ef0eba7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070499"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>使用集中式部署 PowerShell cmdlet 來管理增益集

身為 Office 365 系統管理員，您可以對透過集中式部署的使用者部署 Office 增益集的功能 （請參閱[部署 Office 增益集在 Office 365 系統管理中心中](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)）。 除了部署 Office 增益集透過 Office 365 系統管理中心，您也可以使用 Microsoft PowerShell。 安裝的[O365 集中式的 Windows PowerShell 的增益集部署模組](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)。 
    
## <a name="connect-using-your-admin-credentials"></a>使用您的系統管理員認證來連線

您可以使用集中式部署 cmdlet 之前，您需要登入。
  
1. 啟動 PowerShell。
    
2. 使用您的公司系統管理員認證連線到 PowerShell。 執行下列 cmdlet。
    
  ```
  Connect-OrganizationAddInService
  ```

3. 在 [**輸入認證**] 頁面上，輸入您的 Office 365 全域系統管理員認證。 或者，您可以直接在指令程式輸入您的認證。 
    
    請執行下列 cmdlet 指定您的公司系統管理員認證的 PSCredential 物件。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> 如需使用 PowerShell 的詳細資訊，請參閱 < <b0>Connect to Office 365 PowerShell</b0>。 
  
## <a name="upload-an-add-in-manifest"></a>上傳增益集資訊清單

執行新增 OrganizationAdd 中指令程式上傳增益集資訊清單從可以是檔案的位置或 URL 的路徑。 下列範例會顯示_ManifestPath_參數的值的檔案位置。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

您也可以執行新增 OrganizationAdd 中指令程式上傳增益集，並將其指派給使用者或群組直接使用_Members_參數，如下列範例所示。 請使用逗號分隔成員的電子郵件地址。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>上傳增益集從 Office 市集

執行新增 OrganizationAddIn cmdlet，從 Office 市集的資訊清單上載。
  
在下列範例中，新增 OrganizationAddIn 指令程式會指定增益集的美國位置和內容市場 AssetId。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

若要判斷_AssetId_參數的值，您可以將它複製從增益集之 Office 市集網頁的 URL。 AssetIds 一律的開頭"WA"後面接著一個數字。 例如，在前一個範例中，WA104099688 AssetId 值的來源是增益集的 Office 市集網頁 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_Locale_參數和_ContentMarket_參數的值相同，並指出您嘗試安裝增益集從國家/地區。 格式是 EN-US，FR-FR。 依此類推。 
  
> [!NOTE]
> 增益集從 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。 
  
## <a name="get-details-of-an-add-in"></a>取得增益集的詳細資料

執行 Get OrganizationAddIn 指令程式，如下所示要上傳至租用戶，所有增益集的詳細資料包含增益集的產品識別碼。
  
```
Get-OrganizationAddIn
```

執行 Get OrganizationAddIn 指令程式搭配_ProductId_參數，以指定的增益集您想要擷取的詳細資料的值。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

若要取得的所有增益集加上指定的使用者和群組的完整詳細資料，將輸出內容輸送到 Format-list 指令程式，取得 OrganizationAddIn 指令程式在下列範例所示。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>開啟或關閉 [增益集

若要讓使用者和群組指派給它，將不再有存取，請開啟關閉增益集，請執行組 OrganizationAddIn 指令程式搭配_ProductId_參數和將_Enabled_參數設為`$false`，如下列範例所示。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

若要開啟的增益集後，請執行相同的指令程式搭配將_Enabled_參數設為`$true`。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>新增或移除使用者的增益集

若要將使用者和群組新增至特定的增益集，請使用_ProductId_、_新增_、 和_成員_的參數執行組 OrganizationAddInAssignments 指令程式。 請使用逗號分隔成員的電子郵件地址。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要移除使用者和群組，執行相同的指令程式使用_移除_參數。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要將增益集指派給租用戶上的所有使用者，執行相同的指令程式使用_AssignToEveryone_參數具有值設定為`$true`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

不將增益集指派給所有人，並還原先前指派的使用者和群組，您可以執行相同的指令程式，並關閉_AssignToEveryone_參數，其值設定為`$false`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>更新增益集

若要更新的增益集資訊清單中，執行組 OrganizationAddIn cmdlet _ProductId_、 與_ManifestPath_，_地區設定_的參數，如下列範例所示。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> 增益集從 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。 
  
## <a name="delete-an-add-in"></a>刪除增益集

若要刪除增益集，如下列範例所示，[ _ProductId_ ] 參數，以執行移除 OrganizationAddIn 指令程式。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>取得每個 cmdlet 的詳細的說明

您可以使用 get-help 指令程式來查看每個 cmdlet 的詳細說明。 例如，下列指令程式提供移除 OrganizationAddIn cmdlet 的詳細的資訊。
  
```
Get-help Remove-OrganizationAddIn -Full
```


