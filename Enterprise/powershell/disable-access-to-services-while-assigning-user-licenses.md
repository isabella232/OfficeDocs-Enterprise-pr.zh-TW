---
title: 停用服務存取權時指派使用者授權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何將授權指派給使用者帳戶，並在同時使用 Office 365 PowerShell 停用特定的服務計劃。
ms.openlocfilehash: c93f54fcd5716a0ea53290c24a2594b8bc63cecf
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001846"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="c43aa-103">停用服務存取權時指派使用者授權</span><span class="sxs-lookup"><span data-stu-id="c43aa-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="c43aa-104">**摘要：** 了解如何將授權指派給使用者帳戶，並在同時使用 Office 365 PowerShell 停用特定的服務計劃。</span><span class="sxs-lookup"><span data-stu-id="c43aa-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="c43aa-105">Office 365 訂閱隨附的個別服務的服務計劃。</span><span class="sxs-lookup"><span data-stu-id="c43aa-105">Office 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="c43aa-106">Office 365 系統管理員通常需要將授權指派給使用者時，停用特定計劃。</span><span class="sxs-lookup"><span data-stu-id="c43aa-106">Office 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="c43aa-107">透過本文中的指示，您可以同時停用特定的服務計劃使用 PowerShell 個別使用者帳戶或多個使用者帳戶指派 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="c43aa-107">With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c43aa-108">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="c43aa-108">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c43aa-109">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c43aa-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="c43aa-110">接著，執行此命令，以檢視您目前訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="c43aa-110">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="c43aa-111">在顯示的`Get-MsolAccountSku`命令：</span><span class="sxs-lookup"><span data-stu-id="c43aa-111">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="c43aa-112">**AccountSkuId**是您組織中的訂閱\<OrganizationName>:\<Subscription> 格式。</span><span class="sxs-lookup"><span data-stu-id="c43aa-112">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="c43aa-113">\<OrganizationName> 是您提供當您在 Office 365 中註冊，並為您的組織是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="c43aa-113">The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="c43aa-114">\<Subscription> 值是針對特定的訂閱。</span><span class="sxs-lookup"><span data-stu-id="c43aa-114">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="c43aa-115">例如，如 litwareinc: enterprisepack，組織名稱為 litwareinc，且訂閱名稱 ENTERPRISEPACK (Office 365 企業版 E3)。</span><span class="sxs-lookup"><span data-stu-id="c43aa-115">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="c43aa-116">**Activeunits 作用**是您已購買訂閱的授權數目。</span><span class="sxs-lookup"><span data-stu-id="c43aa-116">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="c43aa-117">**WarningUnits**是，您還沒有更新，並，將會在 30 天寬限期後過期的訂閱中的授權數目。</span><span class="sxs-lookup"><span data-stu-id="c43aa-117">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="c43aa-118">**ConsumedUnits**是已指派給使用者的訂閱的授權數目。</span><span class="sxs-lookup"><span data-stu-id="c43aa-118">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="c43aa-119">請注意您 Office 365 訂用帳戶，包含您想要授權的使用者 AccountSkuId。</span><span class="sxs-lookup"><span data-stu-id="c43aa-119">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="c43aa-120">此外，請確定有足夠的授權可以指派 （由欄位刪減從**ActiveUnits** **ConsumedUnits** ）。</span><span class="sxs-lookup"><span data-stu-id="c43aa-120">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="c43aa-121">接著，執行此命令，以檢視有關您所有的訂閱中可用的 Office 365 服務計劃的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="c43aa-121">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="c43aa-122">從顯示的以下命令，決定您想要指派授權給使用者時，停用哪些服務方案。</span><span class="sxs-lookup"><span data-stu-id="c43aa-122">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="c43aa-123">以下是服務計劃和其對應的 Office 365 服務的部分清單。</span><span class="sxs-lookup"><span data-stu-id="c43aa-123">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="c43aa-124">下表顯示 Office 365 服務計劃及最常見的服務的好記的名稱。</span><span class="sxs-lookup"><span data-stu-id="c43aa-124">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="c43aa-125">您的服務計劃清單可能會不同。</span><span class="sxs-lookup"><span data-stu-id="c43aa-125">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="c43aa-126">**服務計劃**</span><span class="sxs-lookup"><span data-stu-id="c43aa-126">**Service plan**</span></span>|<span data-ttu-id="c43aa-127">**描述**</span><span class="sxs-lookup"><span data-stu-id="c43aa-127">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="c43aa-128">Sway</span><span class="sxs-lookup"><span data-stu-id="c43aa-128">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="c43aa-129">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c43aa-129">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="c43aa-130">Yammer</span><span class="sxs-lookup"><span data-stu-id="c43aa-130">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="c43aa-131">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="c43aa-131">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="c43aa-132">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="c43aa-132">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="c43aa-133">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="c43aa-133">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="c43aa-134">Office Online</span><span class="sxs-lookup"><span data-stu-id="c43aa-134">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="c43aa-135">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c43aa-135">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="c43aa-136">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="c43aa-136">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="c43aa-137">為授權計劃 （也稱為產品名稱） 的完整清單，其包含的服務計劃和其對應的易記名稱，請參閱[產品名稱和授權的服務方案識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="c43aa-137">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="c43aa-138">現在，您有 AccountSkuId 和停用服務計劃，您可以指派授權的個別使用者或多個使用者。</span><span class="sxs-lookup"><span data-stu-id="c43aa-138">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="c43aa-139">單一使用者</span><span class="sxs-lookup"><span data-stu-id="c43aa-139">For a single user</span></span>

<span data-ttu-id="c43aa-140">單一使用者，填入使用者主體名稱的使用者帳戶、 AccountSkuId 和服務計劃的清單來停用並移除的說明文字和\<和 > 字元。</span><span class="sxs-lookup"><span data-stu-id="c43aa-140">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="c43aa-141">然後，在 PowerShell 命令提示字元執行產生的命令。</span><span class="sxs-lookup"><span data-stu-id="c43aa-141">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="c43aa-142">以下是範例命令區塊，帳戶 belindan@contoso.com，一個用於名為 contoso: enterprisepack 的授權，而若要停用服務計劃為 RMS_S_ENTERPRISE、 SWAY，INTUNE_O365 和 YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="c43aa-142">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

### <a name="for-multiple-users"></a><span data-ttu-id="c43aa-143">多個使用者</span><span class="sxs-lookup"><span data-stu-id="c43aa-143">For multiple users</span></span>

<span data-ttu-id="c43aa-144">若要執行這項管理工作的多個使用者，建立逗點分隔值 (CSV) 文字檔，其中包含 [UserPrincipalName 和 UsageLocation] 欄位。</span><span class="sxs-lookup"><span data-stu-id="c43aa-144">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields.</span></span> <span data-ttu-id="c43aa-145">範例如下：</span><span class="sxs-lookup"><span data-stu-id="c43aa-145">Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="c43aa-146">接下來，填寫輸入和輸出 CSV 檔案、 SKU 識別碼的帳戶及服務計劃要停用，清單的位置，然後再執行 PowerShell 命令提示字元處的 [產生的命令。</span><span class="sxs-lookup"><span data-stu-id="c43aa-146">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="c43aa-147">此 PowerShell 命令區塊：</span><span class="sxs-lookup"><span data-stu-id="c43aa-147">This PowerShell command block:</span></span>
  
- <span data-ttu-id="c43aa-148">會顯示每位使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="c43aa-148">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="c43aa-149">將自訂的授權指派給每位使用者。</span><span class="sxs-lookup"><span data-stu-id="c43aa-149">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="c43aa-150">與已處理的所有使用者建立 CSV 檔案，並顯示其授權狀態。</span><span class="sxs-lookup"><span data-stu-id="c43aa-150">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="c43aa-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c43aa-151">See also</span></span>

[<span data-ttu-id="c43aa-152">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="c43aa-152">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="c43aa-153">使用 Office 365 PowerShell 停用 Sway 的存取權</span><span class="sxs-lookup"><span data-stu-id="c43aa-153">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="c43aa-154">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c43aa-154">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c43aa-155">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="c43aa-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

