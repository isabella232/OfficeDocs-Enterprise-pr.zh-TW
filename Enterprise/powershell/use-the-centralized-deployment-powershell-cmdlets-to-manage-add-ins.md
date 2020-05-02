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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="ae265-103">使用集中式部署 PowerShell Cmdlet 來管理增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="ae265-104">做為 Office 365 系統管理員，您可以透過集中式部署功能，將 Office 增益集部署給使用者（請參閱[在系統管理中心中管理 office 365 增益集的部署](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)）。</span><span class="sxs-lookup"><span data-stu-id="ae265-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="ae265-105">除了透過系統管理中心部署 Office 增益集之外，您也可以使用 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ae265-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="ae265-106">從 Microsoft 下載中心[下載](https://go.microsoft.com/fwlink/p/?linkid=850850)集中式部署 PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae265-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="ae265-107">您要執行的工作</span><span class="sxs-lookup"><span data-stu-id="ae265-107">What do you want to do?</span></span>

[<span data-ttu-id="ae265-108">使用您的系統管理員認證進行連線</span><span class="sxs-lookup"><span data-stu-id="ae265-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="ae265-109">上傳增益集資訊清單</span><span class="sxs-lookup"><span data-stu-id="ae265-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="ae265-110">從 Office Store 上載增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="ae265-111">取得增益集的詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae265-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="ae265-112">開啟或關閉增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="ae265-113">新增或移除增益集中的使用者</span><span class="sxs-lookup"><span data-stu-id="ae265-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="ae265-114">更新增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="ae265-115">刪除增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="ae265-116">取得每個 Cmdlet 的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ae265-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="ae265-117">使用您的系統管理員認證進行連線</span><span class="sxs-lookup"><span data-stu-id="ae265-117">Connect using your admin credentials</span></span>
<span data-ttu-id="ae265-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="ae265-119">在您可以使用集中式部署 Cmdlet 之前，您必須先登入。</span><span class="sxs-lookup"><span data-stu-id="ae265-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="ae265-120">開始 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ae265-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="ae265-121">使用您公司的系統管理員認證來連線至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ae265-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="ae265-122">執行下列 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae265-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="ae265-123">在 [**輸入認證**] 頁面中，輸入您的 Office 365 全域系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="ae265-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="ae265-124">或者，您也可以直接在 Cmdlet 中輸入認證。</span><span class="sxs-lookup"><span data-stu-id="ae265-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="ae265-125">執行下列 Cmdlet，將您的公司系統管理員認證指定為 PSCredential 物件。</span><span class="sxs-lookup"><span data-stu-id="ae265-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="ae265-126">如需使用 PowerShell 的詳細資訊，請參閱[Connect To Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585)。</span><span class="sxs-lookup"><span data-stu-id="ae265-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="ae265-127">上傳增益集資訊清單</span><span class="sxs-lookup"><span data-stu-id="ae265-127">Upload an add-in manifest</span></span>
<span data-ttu-id="ae265-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="ae265-129">執行新的 OrganizationAdd Cmdlet，從路徑（可以是檔案位置或 URL）上傳增益集資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ae265-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="ae265-130">下列範例會顯示_ManifestPath_參數值的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="ae265-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="ae265-131">您也可以執行新的 OrganizationAdd Cmdlet，以上傳增益集，並使用_Members_參數直接將其指派給使用者或群組，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae265-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="ae265-132">以逗號分隔成員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="ae265-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="ae265-133">從 Office Store 上載增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="ae265-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="ae265-135">執行 OrganizationAddIn 指令程式，以從 Office 存放區上傳資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ae265-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="ae265-136">在下列範例中，OrganizationAddIn Cmdlet 會為美國位置和內容市場的增益集指定 AssetId。</span><span class="sxs-lookup"><span data-stu-id="ae265-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="ae265-137">若要決定_AssetId_參數的值，您可以從增益集的 Office STORE 網頁 URL 進行複製。</span><span class="sxs-lookup"><span data-stu-id="ae265-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="ae265-138">AssetIds 永遠以 "WA" 開頭，後面接數位。</span><span class="sxs-lookup"><span data-stu-id="ae265-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="ae265-139">例如，在上一個範例中，WA104099688 的 AssetId 值來源為增益集的 Office Store 網頁 URL： [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="ae265-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="ae265-140">_Locale_參數和_ContentMarket_參數的值相同，並指出您嘗試安裝增益集的國家/地區。</span><span class="sxs-lookup"><span data-stu-id="ae265-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="ae265-141">格式為 en-US，fr-FR。</span><span class="sxs-lookup"><span data-stu-id="ae265-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="ae265-142">等等。</span><span class="sxs-lookup"><span data-stu-id="ae265-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="ae265-143">從 Office Store 上傳的增益集會在 Office 市集中的最新更新可用幾天內自動更新。</span><span class="sxs-lookup"><span data-stu-id="ae265-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="ae265-144">取得增益集的詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae265-144">Get details of an add-in</span></span>
<span data-ttu-id="ae265-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="ae265-146">執行 OrganizationAddIn 指令程式（如下所示），以取得上傳至租使用者的所有增益集的詳細資料，包括增益集的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="ae265-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="ae265-147">使用_ProductId_參數的值來執行 OrganizationAddIn 指令程式，以指定您要從中取得詳細資料的增益集。</span><span class="sxs-lookup"><span data-stu-id="ae265-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="ae265-148">若要取得所有增益集的完整詳細資料以及所指派的使用者和群組，請將 OrganizationAddIn 指令程式的輸出輸送至 Format-List Cmdlet，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae265-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="ae265-149">開啟或關閉增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="ae265-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="ae265-151">若要關閉增益集，讓指派給它的使用者和群組不再具有存取權，請使用_ProductId_參數和_Enabled_參數設定為`$false`，以執行 OrganizationAddIn 指令程式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae265-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="ae265-152">若要將增益集重新開啟，請執行與_Enabled_參數設定為`$true`相同的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae265-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="ae265-153">新增或移除增益集中的使用者</span><span class="sxs-lookup"><span data-stu-id="ae265-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="ae265-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="ae265-155">若要將使用者和群組新增至特定增益集，請使用_ProductId_、 _add_和_Members_參數執行 OrganizationAddInAssignments Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae265-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="ae265-156">以逗號分隔成員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="ae265-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="ae265-157">若要移除使用者和群組，請使用_移除_參數來執行相同的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae265-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="ae265-158">若要將增益集指派給租使用者上的所有使用者，請使用_AssignToEveryone_參數設定為`$true`，以執行相同的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae265-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="ae265-159">若要將增益集指派給所有人，並回復至先前指派的使用者和群組，您可以執行相同的指令程式，並將_AssignToEveryone_參數的值設為`$false`，以關閉參數。</span><span class="sxs-lookup"><span data-stu-id="ae265-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="ae265-160">更新增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-160">Update an add-in</span></span>
<span data-ttu-id="ae265-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="ae265-162">若要從資訊清單更新增益集，請使用_ProductId_、 _ManifestPath_及_Locale_參數執行 OrganizationAddIn 指令程式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae265-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="ae265-163">從 Office Store 上傳的增益集會在 Office 市集中的最新更新可用幾天內自動更新。</span><span class="sxs-lookup"><span data-stu-id="ae265-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="ae265-164">刪除增益集</span><span class="sxs-lookup"><span data-stu-id="ae265-164">Delete an add-in</span></span>
<span data-ttu-id="ae265-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="ae265-166">若要刪除增益集，請使用_ProductId_參數執行 Remove-OrganizationAddIn Cmdlet，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae265-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="ae265-167">取得每個 Cmdlet 的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ae265-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="ae265-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="ae265-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="ae265-169">您可以使用 Get-help 指令程式，查看每個 Cmdlet 的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="ae265-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="ae265-170">例如，下列 Cmdlet 提供有關 OrganizationAddIn Cmdlet 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ae265-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


