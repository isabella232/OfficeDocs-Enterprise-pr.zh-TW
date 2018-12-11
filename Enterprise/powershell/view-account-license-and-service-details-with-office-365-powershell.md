---
title: 使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
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
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213950"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="9b910-103">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="9b910-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="9b910-104">**摘要：** 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="9b910-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="9b910-p101">在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。不過，使用者可能無法存取所有目前已指派給他們的授權中可用的服務。您可以使用 Office 365 PowerShell 檢視的使用者帳戶之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="9b910-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="9b910-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="9b910-108">Before you begin</span></span>

- <span data-ttu-id="9b910-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9b910-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="9b910-111">使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`尋找下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9b910-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="9b910-112">您的組織可用的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="9b910-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="9b910-113">每個授權計劃中可用的服務，以及其列出的順序 (索引編號)。</span><span class="sxs-lookup"><span data-stu-id="9b910-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="9b910-114">如需授權方案、 授權、 及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9b910-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="9b910-115">使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`尋找的授權指派給使用者和的順序，其中所列 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="9b910-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="9b910-116">如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="9b910-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="9b910-117">若要檢視服務的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9b910-117">To view services for a user account</span></span>

<span data-ttu-id="9b910-118">若要檢視所有使用者有權存取 Office 365 服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="9b910-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="9b910-p103">此範例會顯示使用者 BelindaN@litwareinc.com 具有存取服務。這會顯示指派至她帳戶的所有授權與相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="9b910-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="9b910-121">本範例顯示使用者 BelindaN@litwareinc.com 有權存取的服務，從指派給其帳戶的第一個授權 (索引編號為 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="9b910-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="9b910-122">若要檢視已被指派*多個授權*之使用者的所有服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="9b910-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

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

  
## <a name="see-also"></a><span data-ttu-id="9b910-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b910-123">See also</span></span>

<span data-ttu-id="9b910-124">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="9b910-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="9b910-125">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9b910-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9b910-126">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9b910-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9b910-127">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9b910-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9b910-128">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="9b910-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9b910-129">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="9b910-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="9b910-130">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9b910-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="9b910-131">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="9b910-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="9b910-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="9b910-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="9b910-133">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="9b910-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="9b910-134">選取物件</span><span class="sxs-lookup"><span data-stu-id="9b910-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="9b910-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="9b910-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="9b910-136">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="9b910-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]