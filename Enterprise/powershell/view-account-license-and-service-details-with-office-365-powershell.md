---
title: 使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。
ms.openlocfilehash: 113107df75880a21210991d5b301245d75c5c739
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052967"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="6fa15-103">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="6fa15-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="6fa15-104">**摘要：** 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="6fa15-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="6fa15-p101">在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。不過，使用者可能無法存取所有目前已指派給他們的授權中可用的服務。您可以使用 Office 365 PowerShell 檢視的使用者帳戶之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="6fa15-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="6fa15-108">如需授權方案、 授權、 及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="6fa15-108">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="6fa15-109">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="6fa15-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="6fa15-110">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="6fa15-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="6fa15-111">接下來，列出您使用此命令的租用戶授權計劃。</span><span class="sxs-lookup"><span data-stu-id="6fa15-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="6fa15-112">若要列出每個授權方案中可用的服務使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="6fa15-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

<span data-ttu-id="6fa15-113">使用這些命令來列出已指派給使用者帳戶的授權。</span><span class="sxs-lookup"><span data-stu-id="6fa15-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6fa15-114">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="6fa15-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6fa15-115">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="6fa15-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="6fa15-116">接著，執行此命令以列出您組織中可用的授權方案。</span><span class="sxs-lookup"><span data-stu-id="6fa15-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```
Get-MsolAccountSku
```

<span data-ttu-id="6fa15-117">接著，執行此命令以列出每個授權的計劃中可用的服務和所屬的順序列出 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="6fa15-117">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
<span data-ttu-id="6fa15-118">使用此命令以列出指派給使用者的授權和所屬的順序列出 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="6fa15-118">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
><span data-ttu-id="6fa15-119">如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="6fa15-119">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="6fa15-120">若要檢視服務的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6fa15-120">To view services for a user account</span></span>

<span data-ttu-id="6fa15-121">若要檢視所有使用者有權存取 Office 365 服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6fa15-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="6fa15-p102">此範例會顯示使用者 BelindaN@litwareinc.com 具有存取服務。這會顯示指派至她帳戶的所有授權與相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="6fa15-p102">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="6fa15-124">本範例顯示使用者 BelindaN@litwareinc.com 有權存取的服務，從指派給其帳戶的第一個授權 (索引編號為 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="6fa15-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="6fa15-125">若要檢視已被指派*多個授權*之使用者的所有服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6fa15-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a><span data-ttu-id="6fa15-126">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="6fa15-126">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="6fa15-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fa15-127">See also</span></span>

[<span data-ttu-id="6fa15-128">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6fa15-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6fa15-129">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="6fa15-129">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6fa15-130">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6fa15-130">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
