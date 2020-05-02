---
title: 使用集中式部署 PowerShell Cmdlet 來管理增益集
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
- MET150
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 使用集中式部署 PowerShell Cmdlet，協助您部署及管理 Office 365 組織的 Office 增益集。
ms.openlocfilehash: 3e3ca622f4c7a84d1fb267880ebf13cc56ad9373
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004496"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>使用集中式部署 PowerShell Cmdlet 來管理增益集

做為 Office 365 系統管理員，您可以透過集中式部署功能，將 Office 增益集部署給使用者（請參閱[在系統管理中心中管理 office 365 增益集的部署](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)）。 除了透過系統管理中心部署 Office 增益集之外，您也可以使用 Microsoft PowerShell。 從 Microsoft 下載中心[下載](https://go.microsoft.com/fwlink/p/?linkid=850850)集中式部署 PowerShell Cmdlet。 
  
## <a name="what-do-you-want-to-do"></a>您要執行的工作

[使用您的系統管理員認證進行連線](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[上傳增益集資訊清單](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[從 Office Store 上載增益集](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[取得增益集的詳細資料](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[開啟或關閉增益集](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[新增或移除增益集中的使用者](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[更新增益集](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[刪除增益集](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[取得每個 Cmdlet 的詳細資訊](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>使用您的系統管理員認證進行連線
<a name="BKMK_Connect"> </a>

在您可以使用集中式部署 Cmdlet 之前，您必須先登入。
  
1. 開始 PowerShell。
    
2. 使用您公司的系統管理員認證來連線至 PowerShell。 執行下列 Cmdlet。
    
  ```
  Connect-OrganizationAddInService
  ```

3. 在 [**輸入認證**] 頁面中，輸入您的 Office 365 全域系統管理員認證。 或者，您也可以直接在 Cmdlet 中輸入認證。 
    
    執行下列 Cmdlet，將您的公司系統管理員認證指定為 PSCredential 物件。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> 如需使用 PowerShell 的詳細資訊，請參閱[Connect To Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。 
  
## <a name="upload-an-add-in-manifest"></a>上傳增益集資訊清單
<a name="BKMK_UploadManifest"> </a>

執行新的 OrganizationAdd Cmdlet，從路徑（可以是檔案位置或 URL）上傳增益集資訊清單。 下列範例會顯示_ManifestPath_參數值的檔案位置。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

您也可以執行新的 OrganizationAdd Cmdlet，以上傳增益集，並使用_Members_參數直接將其指派給使用者或群組，如下列範例所示。 以逗號分隔成員的電子郵件地址。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>從 Office Store 上載增益集
<a name="BKMK_UploadAddin"> </a>

執行 OrganizationAddIn 指令程式，以從 Office 存放區上傳資訊清單。
  
在下列範例中，OrganizationAddIn Cmdlet 會為美國位置和內容市場的增益集指定 AssetId。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

若要決定_AssetId_參數的值，您可以從增益集的 Office STORE 網頁 URL 進行複製。 AssetIds 永遠以 "WA" 開頭，後面接數位。 例如，在上一個範例中，WA104099688 的 AssetId 值來源為增益集的 Office Store 網頁 URL： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_Locale_參數和_ContentMarket_參數的值相同，並指出您嘗試安裝增益集的國家/地區。 格式為 en-US，fr-FR。 等等。 
  
> [!NOTE]
> 從 Office Store 上傳的增益集會在 Office 市集中的最新更新可用幾天內自動更新。 
  
## <a name="get-details-of-an-add-in"></a>取得增益集的詳細資料
<a name="BKMK_GetDetails"> </a>

執行 OrganizationAddIn 指令程式（如下所示），以取得上傳至租使用者的所有增益集的詳細資料，包括增益集的產品識別碼。
  
```
Get-OrganizationAddIn
```

使用_ProductId_參數的值來執行 OrganizationAddIn 指令程式，以指定您要從中取得詳細資料的增益集。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

若要取得所有增益集的完整詳細資料以及所指派的使用者和群組，請將 OrganizationAddIn 指令程式的輸出輸送至 Format-List Cmdlet，如下列範例所示。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>開啟或關閉增益集
<a name="BKMK_TurnOnOff"> </a>

若要關閉增益集，讓指派給它的使用者和群組不再具有存取權，請使用_ProductId_參數和_Enabled_參數設定為`$false`，以執行 OrganizationAddIn 指令程式，如下列範例所示。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

若要將增益集重新開啟，請執行與_Enabled_參數設定為`$true`相同的 Cmdlet。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>新增或移除增益集中的使用者
<a name="BKMK_AddRemove"> </a>

若要將使用者和群組新增至特定增益集，請使用_ProductId_、 _add_和_Members_參數執行 OrganizationAddInAssignments Cmdlet。 以逗號分隔成員的電子郵件地址。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要移除使用者和群組，請使用_移除_參數來執行相同的 Cmdlet。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

若要將增益集指派給租使用者上的所有使用者，請使用_AssignToEveryone_參數設定為`$true`，以執行相同的 Cmdlet。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

若要將增益集指派給所有人，並回復至先前指派的使用者和群組，您可以執行相同的指令程式，並將_AssignToEveryone_參數的值設為`$false`，以關閉參數。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>更新增益集
<a name="BKMK_UpdateAddin"> </a>

若要從資訊清單更新增益集，請使用_ProductId_、 _ManifestPath_及_Locale_參數執行 OrganizationAddIn 指令程式，如下列範例所示。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> 從 Office Store 上傳的增益集會在 Office 市集中的最新更新可用幾天內自動更新。 
  
## <a name="delete-an-add-in"></a>刪除增益集
<a name="BKMK_Delete"> </a>

若要刪除增益集，請使用_ProductId_參數執行 Remove-OrganizationAddIn Cmdlet，如下列範例所示。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>取得每個 Cmdlet 的詳細資訊
<a name="BKMK_GetHelp"> </a>

您可以使用 Get-help 指令程式，查看每個 Cmdlet 的詳細說明。 例如，下列 Cmdlet 提供有關 OrganizationAddIn Cmdlet 的詳細資訊。
  
```
Get-help Remove-OrganizationAddIn -Full
```


