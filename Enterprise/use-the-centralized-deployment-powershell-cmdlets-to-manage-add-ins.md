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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="95e99-103">使用集中式部署 PowerShell cmdlet 來管理增益集</span><span class="sxs-lookup"><span data-stu-id="95e99-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="95e99-104">身為 Office 365 系統管理員，您可以對透過集中式部署的使用者部署 Office 增益集的功能 （請參閱[部署 Office 增益集在 Office 365 系統管理中心中](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)）。</span><span class="sxs-lookup"><span data-stu-id="95e99-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="95e99-105">除了部署 Office 增益集透過 Office 365 系統管理中心，您也可以使用 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="95e99-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="95e99-106">安裝的[O365 集中式的 Windows PowerShell 的增益集部署模組](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)。</span><span class="sxs-lookup"><span data-stu-id="95e99-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="95e99-107">使用您的系統管理員認證來連線</span><span class="sxs-lookup"><span data-stu-id="95e99-107">Connect using your admin credentials</span></span>

<span data-ttu-id="95e99-108">您可以使用集中式部署 cmdlet 之前，您需要登入。</span><span class="sxs-lookup"><span data-stu-id="95e99-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="95e99-109">啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="95e99-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="95e99-110">使用您的公司系統管理員認證連線到 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="95e99-110">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="95e99-111">執行下列 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95e99-111">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="95e99-112">在 [**輸入認證**] 頁面上，輸入您的 Office 365 全域系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="95e99-112">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="95e99-113">或者，您可以直接在指令程式輸入您的認證。</span><span class="sxs-lookup"><span data-stu-id="95e99-113">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="95e99-114">請執行下列 cmdlet 指定您的公司系統管理員認證的 PSCredential 物件。</span><span class="sxs-lookup"><span data-stu-id="95e99-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="95e99-115">如需使用 PowerShell 的詳細資訊，請參閱 < <b0>Connect to Office 365 PowerShell</b0>。</span><span class="sxs-lookup"><span data-stu-id="95e99-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="95e99-116">上傳增益集資訊清單</span><span class="sxs-lookup"><span data-stu-id="95e99-116">Upload an add-in manifest</span></span>

<span data-ttu-id="95e99-117">執行新增 OrganizationAdd 中指令程式上傳增益集資訊清單從可以是檔案的位置或 URL 的路徑。</span><span class="sxs-lookup"><span data-stu-id="95e99-117">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="95e99-118">下列範例會顯示_ManifestPath_參數的值的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="95e99-118">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="95e99-119">您也可以執行新增 OrganizationAdd 中指令程式上傳增益集，並將其指派給使用者或群組直接使用_Members_參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="95e99-119">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="95e99-120">請使用逗號分隔成員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="95e99-120">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="95e99-121">上傳增益集從 Office 市集</span><span class="sxs-lookup"><span data-stu-id="95e99-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="95e99-122">執行新增 OrganizationAddIn cmdlet，從 Office 市集的資訊清單上載。</span><span class="sxs-lookup"><span data-stu-id="95e99-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="95e99-123">在下列範例中，新增 OrganizationAddIn 指令程式會指定增益集的美國位置和內容市場 AssetId。</span><span class="sxs-lookup"><span data-stu-id="95e99-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="95e99-124">若要判斷_AssetId_參數的值，您可以將它複製從增益集之 Office 市集網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="95e99-124">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="95e99-125">AssetIds 一律的開頭"WA"後面接著一個數字。</span><span class="sxs-lookup"><span data-stu-id="95e99-125">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="95e99-126">例如，在前一個範例中，WA104099688 AssetId 值的來源是增益集的 Office 市集網頁 URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="95e99-126">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="95e99-127">_Locale_參數和_ContentMarket_參數的值相同，並指出您嘗試安裝增益集從國家/地區。</span><span class="sxs-lookup"><span data-stu-id="95e99-127">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="95e99-128">格式是 EN-US，FR-FR。</span><span class="sxs-lookup"><span data-stu-id="95e99-128">The format is en-US, fr-FR.</span></span> <span data-ttu-id="95e99-129">依此類推。</span><span class="sxs-lookup"><span data-stu-id="95e99-129">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="95e99-130">增益集從 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。</span><span class="sxs-lookup"><span data-stu-id="95e99-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="95e99-131">取得增益集的詳細資料</span><span class="sxs-lookup"><span data-stu-id="95e99-131">Get details of an add-in</span></span>

<span data-ttu-id="95e99-132">執行 Get OrganizationAddIn 指令程式，如下所示要上傳至租用戶，所有增益集的詳細資料包含增益集的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="95e99-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="95e99-133">執行 Get OrganizationAddIn 指令程式搭配_ProductId_參數，以指定的增益集您想要擷取的詳細資料的值。</span><span class="sxs-lookup"><span data-stu-id="95e99-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="95e99-134">若要取得的所有增益集加上指定的使用者和群組的完整詳細資料，將輸出內容輸送到 Format-list 指令程式，取得 OrganizationAddIn 指令程式在下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="95e99-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="95e99-135">開啟或關閉 [增益集</span><span class="sxs-lookup"><span data-stu-id="95e99-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="95e99-136">若要讓使用者和群組指派給它，將不再有存取，請開啟關閉增益集，請執行組 OrganizationAddIn 指令程式搭配_ProductId_參數和將_Enabled_參數設為`$false`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="95e99-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="95e99-137">若要開啟的增益集後，請執行相同的指令程式搭配將_Enabled_參數設為`$true`。</span><span class="sxs-lookup"><span data-stu-id="95e99-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="95e99-138">新增或移除使用者的增益集</span><span class="sxs-lookup"><span data-stu-id="95e99-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="95e99-139">若要將使用者和群組新增至特定的增益集，請使用_ProductId_、_新增_、 和_成員_的參數執行組 OrganizationAddInAssignments 指令程式。</span><span class="sxs-lookup"><span data-stu-id="95e99-139">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="95e99-140">請使用逗號分隔成員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="95e99-140">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="95e99-141">若要移除使用者和群組，執行相同的指令程式使用_移除_參數。</span><span class="sxs-lookup"><span data-stu-id="95e99-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="95e99-142">若要將增益集指派給租用戶上的所有使用者，執行相同的指令程式使用_AssignToEveryone_參數具有值設定為`$true`。</span><span class="sxs-lookup"><span data-stu-id="95e99-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="95e99-143">不將增益集指派給所有人，並還原先前指派的使用者和群組，您可以執行相同的指令程式，並關閉_AssignToEveryone_參數，其值設定為`$false`。</span><span class="sxs-lookup"><span data-stu-id="95e99-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="95e99-144">更新增益集</span><span class="sxs-lookup"><span data-stu-id="95e99-144">Update an add-in</span></span>

<span data-ttu-id="95e99-145">若要更新的增益集資訊清單中，執行組 OrganizationAddIn cmdlet _ProductId_、 與_ManifestPath_，_地區設定_的參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="95e99-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="95e99-146">增益集從 Office 市集上傳將會自動更新的最新可用更新的 Office 存放區上的幾天內。</span><span class="sxs-lookup"><span data-stu-id="95e99-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="95e99-147">刪除增益集</span><span class="sxs-lookup"><span data-stu-id="95e99-147">Delete an add-in</span></span>

<span data-ttu-id="95e99-148">若要刪除增益集，如下列範例所示，[ _ProductId_ ] 參數，以執行移除 OrganizationAddIn 指令程式。</span><span class="sxs-lookup"><span data-stu-id="95e99-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="95e99-149">取得每個 cmdlet 的詳細的說明</span><span class="sxs-lookup"><span data-stu-id="95e99-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="95e99-150">您可以使用 get-help 指令程式來查看每個 cmdlet 的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="95e99-150">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="95e99-151">例如，下列指令程式提供移除 OrganizationAddIn cmdlet 的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="95e99-151">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


