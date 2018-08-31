---
title: 使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
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
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223105"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="6a221-103">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="6a221-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="6a221-104">**摘要：** 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="6a221-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="6a221-p101">在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。不過，使用者可能無法存取所有目前已指派給他們的授權中可用的服務。您可以使用 Office 365 PowerShell 檢視的使用者帳戶之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="6a221-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="6a221-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="6a221-108">Before you begin</span></span>

- <span data-ttu-id="6a221-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="6a221-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6a221-111">使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`尋找下列資訊：</span><span class="sxs-lookup"><span data-stu-id="6a221-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="6a221-112">您的組織可用的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="6a221-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="6a221-113">每個授權計劃中可用的服務，以及其列出的順序 (索引編號)。</span><span class="sxs-lookup"><span data-stu-id="6a221-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="6a221-114">如需授權方案、 授權、 及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="6a221-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6a221-115">使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`尋找的授權指派給使用者和的順序，其中所列 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="6a221-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="6a221-116">如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="6a221-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="6a221-117">若要檢視服務的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6a221-117">To view services for a user account</span></span>

<span data-ttu-id="6a221-118">若要檢視所有使用者有權存取 Office 365 服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6a221-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="6a221-p103">此範例會顯示使用者 BelindaN@litwareinc.com 具有存取服務。這會顯示指派至她帳戶的所有授權與相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="6a221-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="6a221-121">本範例顯示使用者 BelindaN@litwareinc.com 有權存取的服務，從指派給其帳戶的第一個授權 (索引編號為 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="6a221-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="6a221-122">若要尋找已啟用或未啟用特定服務的所有授權使用者，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6a221-122">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="6a221-123">這些範例使用下列資訊：</span><span class="sxs-lookup"><span data-stu-id="6a221-123">These examples use the following information:</span></span>
  
- <span data-ttu-id="6a221-124">提供我們感興趣的 Office 365 服務的存取授權已指派給 （索引編號為 0） 的所有使用者的第一個授權。</span><span class="sxs-lookup"><span data-stu-id="6a221-124">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="6a221-p104">我們感興趣的 Office 365 服務是 Skype 商務 Online 與 Exchange Online。相關聯的授權方案授權，Skype 商務 online 是 6 列出的服務 （索引編號為 5），與 Exchange Online 是 9th 服務列出 （索引編號為 8）。</span><span class="sxs-lookup"><span data-stu-id="6a221-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="6a221-127">此範例會傳回所有已獲授權的商務 Online 與 Exchange Online Skype 所啟用的使用者。</span><span class="sxs-lookup"><span data-stu-id="6a221-127">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="6a221-128">此範例會傳回所有已獲授權的使用者未啟用 Skype 商務 Online 或 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="6a221-128">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="6a221-129">若要檢視已被指派*多個授權*之使用者的所有服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6a221-129">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

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

  
## <a name="see-also"></a><span data-ttu-id="6a221-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a221-130">See also</span></span>

<span data-ttu-id="6a221-131">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="6a221-131">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="6a221-132">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6a221-132">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a221-133">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6a221-133">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a221-134">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6a221-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a221-135">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6a221-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6a221-136">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="6a221-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="6a221-137">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="6a221-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="6a221-138">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="6a221-138">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="6a221-139">Format-List</span><span class="sxs-lookup"><span data-stu-id="6a221-139">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="6a221-140">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="6a221-140">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="6a221-141">選取物件</span><span class="sxs-lookup"><span data-stu-id="6a221-141">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="6a221-142">Where-Object</span><span class="sxs-lookup"><span data-stu-id="6a221-142">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="6a221-143">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="6a221-143">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]