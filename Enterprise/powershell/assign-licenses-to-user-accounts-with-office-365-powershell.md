---
title: 將授權指派給使用 Office 365 PowerShell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/05/2019
audience: Admin
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
search.appverid:
- MET150
description: 如何使用 Office 365 PowerShell 來將 Office 365 授權指派給未經授權的使用者。
ms.openlocfilehash: c244e60016cb04008e27e2df444703ac7e41db12
ms.sourcegitcommit: 6c3003380491fba6dacb299754716901c20ba629
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "36198645"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f2545-103">將授權指派給使用 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f2545-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f2545-104">**摘要：** 如何使用 Office 365 PowerShell 來將 Office 365 授權指派給未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="f2545-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="f2545-105">使用者無法使用任何 Office 365 服務，直到其帳戶具有已指派授權給授權計劃。</span><span class="sxs-lookup"><span data-stu-id="f2545-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="f2545-106">您可以使用 Office 365 PowerShell 來快速將授權指派給未經授權的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f2545-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="f2545-107">使用者帳戶必須被指派的位置。</span><span class="sxs-lookup"><span data-stu-id="f2545-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="f2545-108">您可以從 Microsoft 365 系統管理中心中的使用者帳戶的屬性或 PowerShell 來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="f2545-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f2545-109">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2545-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f2545-110">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="f2545-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="f2545-111">接下來，列出您的租用戶使用此命令的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="f2545-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="f2545-112">接下來，取得您想要新增的授權，也稱為使用者主體名稱 (UPN) 的帳戶登入名稱。</span><span class="sxs-lookup"><span data-stu-id="f2545-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="f2545-113">接下來，請確定的使用者帳戶擁有指派的使用狀況位置。</span><span class="sxs-lookup"><span data-stu-id="f2545-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="f2545-114">如果沒有指派未使用位置，您可以指派一個使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="f2545-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="f2545-115">最後，指定使用者登入名稱及授權計劃名稱，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="f2545-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f2545-116">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="f2545-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f2545-117">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="f2545-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="f2545-118">執行**Get-msolaccountsku**命令，以檢視您組織中每個計劃可用的授權計劃與可用授權數量。</span><span class="sxs-lookup"><span data-stu-id="f2545-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="f2545-119">在每個方案可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。</span><span class="sxs-lookup"><span data-stu-id="f2545-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="f2545-120">如需有關授權方案、 授權及服務的詳細資訊，請參閱[檢視授權與服務的 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f2545-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="f2545-121">若要在組織中尋找未經授權的帳戶，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="f2545-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="f2545-122">您只可以將授權指派給使用者帳戶，已將**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2http 國碼/地區碼。</span><span class="sxs-lookup"><span data-stu-id="f2545-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="f2545-123">例如，US 代表美國、FR 代表法國。</span><span class="sxs-lookup"><span data-stu-id="f2545-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="f2545-124">在某些國家/地區中，某些 Office 365 服務無法使用。</span><span class="sxs-lookup"><span data-stu-id="f2545-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="f2545-125">如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="f2545-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="f2545-126">若要找出沒有**UsageLocation**值的帳戶，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="f2545-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="f2545-127">若要設定**UsageLocation**值帳戶，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="f2545-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="f2545-128">例如：</span><span class="sxs-lookup"><span data-stu-id="f2545-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="f2545-129">如果您使用 **Get-MsolUser** Cmdlet，而不使用 **-All**參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="f2545-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="f2545-130">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f2545-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="f2545-131">若要指派授權給使用者，請在 Office 365 PowerShell 中使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="f2545-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="f2545-132">本範例會從**litwareinc: enterprisepack** (Office 365 企業版 E3) 授權計劃授權的使用者**belindan@litwareinc.com**指派授權：</span><span class="sxs-lookup"><span data-stu-id="f2545-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="f2545-133">若要將授權指派給多位未經授權的使用者，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="f2545-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="f2545-134">您不能指派給使用者的多個授權從相同的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="f2545-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="f2545-135">如果您沒有足夠的可用授權，授權指派給他們正在直到可用的授權用完**Get-msoluser** cmdlet 所傳回的順序中的使用者。</span><span class="sxs-lookup"><span data-stu-id="f2545-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="f2545-136">此範例會將授權從**litwareinc: enterprisepack** (Office 365 企業版 E3) 授權計劃指派給所有未經授權的使用者：</span><span class="sxs-lookup"><span data-stu-id="f2545-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="f2545-137">此範例會將相同的授權指派給在美國境內銷售部門中未經授權的使用者：</span><span class="sxs-lookup"><span data-stu-id="f2545-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="f2545-138">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="f2545-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="f2545-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2545-139">See also</span></span>

[<span data-ttu-id="f2545-140">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f2545-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f2545-141">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="f2545-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f2545-142">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2545-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
