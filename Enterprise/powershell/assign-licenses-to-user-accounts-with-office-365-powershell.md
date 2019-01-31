---
title: 使用 Office 365 PowerShell 指派授權至使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651177"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="24a28-103">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="24a28-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="24a28-104">**摘要：** 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="24a28-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="24a28-p101">使用者無法使用任何 Office 365 服務之前其帳戶已指派授權的授權方案。您可以使用 Office 365 PowerShell 快速地將授權指派給未授權的帳戶。</span><span class="sxs-lookup"><span data-stu-id="24a28-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="24a28-107">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="24a28-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="24a28-108">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="24a28-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="24a28-109">接下來，列出您使用此命令的租用戶授權計劃。</span><span class="sxs-lookup"><span data-stu-id="24a28-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="24a28-110">接下來，取得您要新增的授權，又稱為使用者主體名稱 (UPN) 的帳戶登入名稱。</span><span class="sxs-lookup"><span data-stu-id="24a28-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="24a28-111">最後，指定的使用者登入名稱和授權計劃名稱並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="24a28-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="24a28-112">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="24a28-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="24a28-113">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="24a28-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="24a28-p102">執行**Get-msolaccountsku**命令來檢視您組織中每個計劃中可用的授權方案和可用授權數量。每個計劃中的可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。如需授權方案、 授權及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="24a28-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="24a28-117">若要在組織中尋找未授權的帳戶，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="24a28-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="24a28-p103">您只可以將授權指派給**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2 國家/地區碼的使用者帳戶。例如，我們美國、 和法國的 FR。某些 Office 365 服務都無法提供在某些國家/地區。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="24a28-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="24a28-122">若要尋找沒有**UsageLocation**值的帳戶，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="24a28-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="24a28-123">若要設定**UsageLocation**值帳戶上，執行此命令。</span><span class="sxs-lookup"><span data-stu-id="24a28-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="24a28-124">例如：</span><span class="sxs-lookup"><span data-stu-id="24a28-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="24a28-125">如果您使用 **Get-MsolUser** Cmdlet，而不使用 **-All**參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="24a28-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="24a28-126">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="24a28-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="24a28-127">若要將授權指派給使用者，請在 Office 365 PowerShell 中使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="24a28-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="24a28-128">此範例會將授權指派從**litwareinc: enterprisepack** (Office 365 企業版 E3) 授權授權的使用者**belindan@litwareinc.com**計劃：</span><span class="sxs-lookup"><span data-stu-id="24a28-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="24a28-129">若要將授權指派給未授權使用者，執行此命令。</span><span class="sxs-lookup"><span data-stu-id="24a28-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="24a28-p104">您不能指派給使用者的多個授權從相同的授權方案。如果您沒有足夠可用的授權，授權指派給使用者他們正在可用授權執行之前**Get-msoluser** cmdlet 所傳回的順序。</span><span class="sxs-lookup"><span data-stu-id="24a28-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="24a28-132">此範例會將授權從**litwareinc: enterprisepack** (Office 365 企業版 E3) 的授權方案指派給未授權的所有使用者：</span><span class="sxs-lookup"><span data-stu-id="24a28-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="24a28-133">此範例會將這些相同的授權指派給未授權使用者在美國銷售部門中：</span><span class="sxs-lookup"><span data-stu-id="24a28-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="24a28-134">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="24a28-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="24a28-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24a28-135">See also</span></span>

[<span data-ttu-id="24a28-136">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="24a28-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="24a28-137">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="24a28-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="24a28-138">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="24a28-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
