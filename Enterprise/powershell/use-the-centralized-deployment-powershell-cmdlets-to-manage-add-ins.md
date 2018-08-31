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
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 可協助您部署及管理 Office 增益集的 Office 365 組織中使用的集中式部署 PowerShell cmdlet。
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539955"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="f37b0-103">使用集中式部署 PowerShell cmdlet 管理的增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="f37b0-p101">為 Office 365 系統管理員，您可對透過集中式部署的使用者部署 Office 增益集 （請參閱[管理部署的 Office 365 增益集在 Office 365 系統管理中心](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)） 的功能。除了部署 Office 增益集透過 Office 365 系統管理中心，您也可以使用 Microsoft PowerShell。[下載](https://go.microsoft.com/fwlink/p/?linkid=850850)從 Microsoft 下載中心的集中式部署 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="f37b0-107">您要執行的工作</span><span class="sxs-lookup"><span data-stu-id="f37b0-107">What do you want to do?</span></span>

[<span data-ttu-id="f37b0-108">使用系統管理認證連線</span><span class="sxs-lookup"><span data-stu-id="f37b0-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="f37b0-109">上傳的增益集資訊清單</span><span class="sxs-lookup"><span data-stu-id="f37b0-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="f37b0-110">上傳增益集來自 Office 市集</span><span class="sxs-lookup"><span data-stu-id="f37b0-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="f37b0-111">取得增益集的詳細資料</span><span class="sxs-lookup"><span data-stu-id="f37b0-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
<span data-ttu-id="f37b0-112">[開啟或關閉 [增益集](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)</span><span class="sxs-lookup"><span data-stu-id="f37b0-112">[Turn on or turn off an add-in](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)</span></span>
  
[<span data-ttu-id="f37b0-113">新增或移除使用者增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="f37b0-114">更新增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="f37b0-115">刪除增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="f37b0-116">取得詳細的說明每個指令程式</span><span class="sxs-lookup"><span data-stu-id="f37b0-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="f37b0-117">使用系統管理認證連線</span><span class="sxs-lookup"><span data-stu-id="f37b0-117">Connect using your admin credentials</span></span>
<span data-ttu-id="f37b0-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-118"></span></span>

<span data-ttu-id="f37b0-119">您可以使用集中式部署 cmdlet 之前，您必須登入。</span><span class="sxs-lookup"><span data-stu-id="f37b0-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="f37b0-120">啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f37b0-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="f37b0-p102">使用您公司的系統管理認證連線至 PowerShell。執行下列 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="f37b0-p103">在 [**輸入認證**] 頁面上，輸入您的 Office 365 全域管理員認證。或者，您可以在指令程式會將直接輸入您的認證。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="f37b0-125">執行下列 cmdlet 以指定您的公司系統管理員認證以 PSCredential 物件。</span><span class="sxs-lookup"><span data-stu-id="f37b0-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="f37b0-126">如需使用 PowerShell 的詳細資訊，請參閱 ＜ [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="f37b0-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="f37b0-127">上傳的增益集資訊清單</span><span class="sxs-lookup"><span data-stu-id="f37b0-127">Upload an add-in manifest</span></span>
<span data-ttu-id="f37b0-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-128"></span></span>

<span data-ttu-id="f37b0-p104">執行新增 OrganizationAdd 中指令程式上傳的增益集資訊清單可以是檔案位置或 URL 路徑中。下列範例會顯示_ManifestPath_參數的值的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="f37b0-p105">您也可以執行新增 OrganizationAdd 中指令程式上傳增益集並將其指派給使用者或群組直接使用_Members_參數，如下列範例所示。請使用逗號分隔成員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="f37b0-133">上傳增益集來自 Office 市集</span><span class="sxs-lookup"><span data-stu-id="f37b0-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="f37b0-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-134"></span></span>

<span data-ttu-id="f37b0-135">執行新增 OrganizationAddIn 指令程式上傳來自 Office 市集資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f37b0-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="f37b0-136">在下列範例中，新增 OrganizationAddIn 指令程式會指定增益集的美國位置及內容市場的 AssetId。</span><span class="sxs-lookup"><span data-stu-id="f37b0-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="f37b0-p106">若要判斷_AssetId_參數的值，您可以從 Office 市集的增益集 AssetIds 網頁一律開始"WA"後面的號碼與 URL 複製。例如，在先前的範例中，WA104099688 AssetId 值的來源是 Office 市集網頁 URL 增益集： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="f37b0-p107">_Locale_參數與_ContentMarket_參數的值是相同的並指出您嘗試安裝增益集從國家/地區。格式為 EN-US、 fr FR.等等。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="f37b0-143">增益集來自 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。</span><span class="sxs-lookup"><span data-stu-id="f37b0-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="f37b0-144">取得增益集的詳細資料</span><span class="sxs-lookup"><span data-stu-id="f37b0-144">Get details of an add-in</span></span>
<span data-ttu-id="f37b0-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-145"></span></span>

<span data-ttu-id="f37b0-146">執行如下所示 Get OrganizationAddIn 指令程式取得上傳至租用戶，所有增益集的詳細資料包含增益集的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="f37b0-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="f37b0-147">執行 Get OrganizationAddIn cmdlet _ProductId_參數來指定的增益集您想要擷取的詳細資料的值。</span><span class="sxs-lookup"><span data-stu-id="f37b0-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="f37b0-148">若要取得之所有增益集加上指定的使用者和群組的完整詳細資料，管道輸出至 Format-list 指令程式，取得 OrganizationAddIn 指令程式在下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f37b0-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="f37b0-149">開啟或關閉 [增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="f37b0-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-150"></span></span>

<span data-ttu-id="f37b0-151">若要關閉增益集，讓使用者和群組指派給它將不再有存取] 設 OrganizationAddIn 指令程式_ProductId_參數且執行_Enabled_參數設為`$false`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f37b0-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="f37b0-152">若要重新打開增益集，執行相同的指令程式使用_Enabled_參數設為`$true`。</span><span class="sxs-lookup"><span data-stu-id="f37b0-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="f37b0-153">新增或移除使用者增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="f37b0-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-154"></span></span>

<span data-ttu-id="f37b0-p108">若要將使用者及群組新增至特定的增益集，執行_ProductId_、 _Add_、 和_成員_的參數組 OrganizationAddInAssignments 指令程式。請使用逗號分隔成員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="f37b0-157">若要移除的使用者與群組，執行相同 cmdlet_移除_參數。</span><span class="sxs-lookup"><span data-stu-id="f37b0-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="f37b0-158">若要指派增益集租用戶的所有使用者，執行相同的指令程式使用_AssignToEveryone_參數值設為`$true`。</span><span class="sxs-lookup"><span data-stu-id="f37b0-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="f37b0-159">不將增益集指派給任何人並還原先前指派的使用者和群組，您可以執行相同的指令程式並將其值設定為關閉_AssignToEveryone_參數`$false`。</span><span class="sxs-lookup"><span data-stu-id="f37b0-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="f37b0-160">更新增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-160">Update an add-in</span></span>
<span data-ttu-id="f37b0-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-161"></span></span>

<span data-ttu-id="f37b0-162">若要更新增益集資訊清單中，執行組 OrganizationAddIn cmdlet _ProductId_、 _ManifestPath_、 和_地區設定_參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f37b0-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="f37b0-163">增益集來自 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。</span><span class="sxs-lookup"><span data-stu-id="f37b0-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="f37b0-164">刪除增益集</span><span class="sxs-lookup"><span data-stu-id="f37b0-164">Delete an add-in</span></span>
<span data-ttu-id="f37b0-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-165"></span></span>

<span data-ttu-id="f37b0-166">若要刪除增益集，執行移除 OrganizationAddIn 指令程式與 [ _ProductId_ ] 參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f37b0-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="f37b0-167">取得詳細的說明每個指令程式</span><span class="sxs-lookup"><span data-stu-id="f37b0-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="f37b0-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="f37b0-168"></span></span>

<span data-ttu-id="f37b0-p109">您可以使用 get-help 指令程式來查看每個 cmdlet 的詳細說明。例如，下列指令程式提供移除 OrganizationAddIn 指令程式的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


