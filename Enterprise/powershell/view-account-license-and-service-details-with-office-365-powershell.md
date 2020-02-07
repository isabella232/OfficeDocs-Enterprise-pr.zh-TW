---
title: 使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。
ms.openlocfilehash: a21b64ac3bbccd88a87f3498153c1efd5054c82a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844164"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="777c0-103">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="777c0-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="777c0-104">在 Office 365 授權從授權計劃 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。</span><span class="sxs-lookup"><span data-stu-id="777c0-104">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans.</span></span> <span data-ttu-id="777c0-105">不過，使用者可能無法存取目前指派給他們的授權中可用的所有服務。</span><span class="sxs-lookup"><span data-stu-id="777c0-105">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="777c0-106">您可以使用 Office 365 PowerShell 來檢視使用者帳戶之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="777c0-106">You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="777c0-107">如需有關授權方案、 授權及服務的詳細資訊，請參閱[檢視授權與服務的 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="777c0-107">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="777c0-108">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="777c0-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="777c0-109">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="777c0-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="777c0-110">接下來，列出您的租用戶使用此命令的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="777c0-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="777c0-111">使用以下命令以列出每個授權計劃中提供的服務。</span><span class="sxs-lookup"><span data-stu-id="777c0-111">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="777c0-112">使用以下命令以列出指派給使用者帳戶的授權。</span><span class="sxs-lookup"><span data-stu-id="777c0-112">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="777c0-113">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="777c0-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="777c0-114">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="777c0-114">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="777c0-115">接著，執行此命令以列出您的組織中可用的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="777c0-115">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="777c0-116">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="777c0-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="777c0-117">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="777c0-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="777c0-118">接著，執行此命令以列出每個授權的計劃中提供的服務，而且它們的順序列出 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="777c0-118">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="777c0-119">使用此命令來列出已指派給使用者的授權，而且它們的順序列出 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="777c0-119">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="777c0-120">若要檢視服務的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="777c0-120">To view services for a user account</span></span>

<span data-ttu-id="777c0-121">若要檢視使用者有權存取的所有 Office 365 服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="777c0-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="777c0-122">本範例會顯示使用者 BelindaN@litwareinc.com 具有存取的服務。</span><span class="sxs-lookup"><span data-stu-id="777c0-122">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="777c0-123">這會顯示與所有的授權指派給其帳戶相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="777c0-123">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="777c0-124">本範例會顯示該使用者 BelindaN@litwareinc.com 有從指派給其帳戶 （索引編號為 0） 的第一個授權存取的服務。</span><span class="sxs-lookup"><span data-stu-id="777c0-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="777c0-125">若要檢視已被指派*多個授權*的使用者的所有服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="777c0-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="777c0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="777c0-126">See also</span></span>

[<span data-ttu-id="777c0-127">管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組</span><span class="sxs-lookup"><span data-stu-id="777c0-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="777c0-128">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="777c0-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="777c0-129">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="777c0-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
