---
title: "停用時指派使用者授權的服務存取權"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "了解如何將授權指派給使用者帳戶及使用 Office 365 PowerShell 的同時停用特定的服務計劃。"
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="cd148-103">停用時指派使用者授權的服務存取權</span><span class="sxs-lookup"><span data-stu-id="cd148-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="cd148-104">**摘要：** 了解如何將授權指派給使用者帳戶及使用 Office 365 PowerShell 的同時停用特定的服務計劃。</span><span class="sxs-lookup"><span data-stu-id="cd148-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="cd148-p101">Office 365 訂閱隨附的個別服務的服務計劃。Office 365 系統管理員通常需要將授權指派給使用者時，停用特定計劃。使用本文中的指示，您可以將 Office 365 授權指派時停用特定的服務計劃使用 PowerShell for 個別的使用者帳戶或多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cd148-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cd148-108">本文根據 Siddhartha Parmar，Microsoft 支援呈報工程師的工作。</span><span class="sxs-lookup"><span data-stu-id="cd148-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="cd148-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="cd148-109">Before you begin</span></span>

<span data-ttu-id="cd148-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="cd148-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="cd148-112">收集資訊訂閱及服務計劃</span><span class="sxs-lookup"><span data-stu-id="cd148-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="cd148-113">執行此命令來查看目前訂閱：</span><span class="sxs-lookup"><span data-stu-id="cd148-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="cd148-114">在顯示`Get-MsolAccountSku`命令：</span><span class="sxs-lookup"><span data-stu-id="cd148-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="cd148-p103">**AccountSkuId**是您組織中的訂閱\<OrganizationName >:\<訂閱 > 格式。\<OrganizationName > 為您提供當您在 Office 365 中註冊並為您的組織是唯一的值。\<訂閱 > 值是針對特定的訂閱。例如，如 litwareinc: enterprisepack、 組織名稱是 litwareinc，而訂閱名稱是 ENTERPRISEPACK (Office 365 企業版 E3)。</span><span class="sxs-lookup"><span data-stu-id="cd148-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="cd148-119">**ActiveUnits**是您已購買訂閱的授權數。</span><span class="sxs-lookup"><span data-stu-id="cd148-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="cd148-120">**WarningUnits**是尚未已更新，並將期限 30 天寬限期訂閱中的授權數。</span><span class="sxs-lookup"><span data-stu-id="cd148-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="cd148-121">**ConsumedUnits**是已指派給使用者訂閱授權數目。</span><span class="sxs-lookup"><span data-stu-id="cd148-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="cd148-p104">請注意包含您想要授權的使用者在 Office 365 訂閱 AccountSkuId。此外，請確定有足夠授權指派給指派 （減去從**ActiveUnits** **ConsumedUnits** ）。</span><span class="sxs-lookup"><span data-stu-id="cd148-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="cd148-124">接下來，執行此命令以查看關於所有訂閱中可用的 Office 365 服務計劃的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="cd148-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="cd148-125">從這個命令的顯示，判斷您想要停用時指派授權給使用者的服務計劃。</span><span class="sxs-lookup"><span data-stu-id="cd148-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="cd148-126">以下為部分服務計劃和其對應的 Office 365 服務的清單。</span><span class="sxs-lookup"><span data-stu-id="cd148-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="cd148-127">**服務計劃**</span><span class="sxs-lookup"><span data-stu-id="cd148-127">**Service plan**</span></span>|<span data-ttu-id="cd148-128">**描述**</span><span class="sxs-lookup"><span data-stu-id="cd148-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cd148-129">SWAY</span><span class="sxs-lookup"><span data-stu-id="cd148-129">SWAY</span></span>  <br/> |<span data-ttu-id="cd148-130">Sway</span><span class="sxs-lookup"><span data-stu-id="cd148-130">Sway</span></span>  <br/> |
|<span data-ttu-id="cd148-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="cd148-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="cd148-132">Office 365 的行動裝置管理</span><span class="sxs-lookup"><span data-stu-id="cd148-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="cd148-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="cd148-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="cd148-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="cd148-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="cd148-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="cd148-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="cd148-136">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="cd148-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="cd148-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cd148-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="cd148-138">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="cd148-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="cd148-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="cd148-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="cd148-140">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="cd148-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="cd148-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="cd148-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="cd148-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="cd148-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="cd148-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="cd148-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="cd148-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cd148-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="cd148-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="cd148-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="cd148-146">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="cd148-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="cd148-147">既然有 AccountSkuId 及停用的服務計劃，您可以指派個別使用者或多個使用者的授權。</span><span class="sxs-lookup"><span data-stu-id="cd148-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="cd148-148">單一使用者</span><span class="sxs-lookup"><span data-stu-id="cd148-148">For a single user</span></span>

<span data-ttu-id="cd148-p105">單一使用者的填滿中的使用者帳戶、 AccountSkuId、 和服務計劃清單停用或移除的說明文字的使用者主體名稱和\<和 > 字元。然後，在 PowerShell 命令提示字元執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="cd148-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="cd148-151">以下是用於 contoso:ENTERPRISEPACK 授權，名為 belindan@contoso.com、 帳戶範例命令封鎖且以停用的服務計劃 RMS_S_ENTERPRISE、 SWAY、 INTUNE_O365 及 YAMMER_ENTERPRISE：</span><span class="sxs-lookup"><span data-stu-id="cd148-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a><span data-ttu-id="cd148-152">多個使用者</span><span class="sxs-lookup"><span data-stu-id="cd148-152">For multiple users</span></span>

<span data-ttu-id="cd148-p106">若要執行這項管理工作的多個使用者，建立包含 UserPrincipalName 和 UsageLocation 欄位的逗號分隔值 (CSV) 文字檔案。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cd148-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="cd148-155">接下來，填入的輸入和輸出 CSV 檔案、 SKU 識別碼的帳戶及服務計劃來停用清單的位置和 PowerShell 命令提示字元執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="cd148-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="cd148-156">此 PowerShell 命令區塊：</span><span class="sxs-lookup"><span data-stu-id="cd148-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="cd148-157">會顯示每個使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="cd148-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="cd148-158">將自訂的授權指派給每位使用者。</span><span class="sxs-lookup"><span data-stu-id="cd148-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="cd148-159">建立已處理的所有使用者的 CSV 檔案並顯示其授權狀態。</span><span class="sxs-lookup"><span data-stu-id="cd148-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="cd148-160">See also</span><span class="sxs-lookup"><span data-stu-id="cd148-160">See also</span></span>

#### 

[<span data-ttu-id="cd148-161">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="cd148-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="cd148-162">停用 Sway 與 Office 365 PowerShell 存取</span><span class="sxs-lookup"><span data-stu-id="cd148-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="cd148-163">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cd148-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="cd148-164">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="cd148-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

