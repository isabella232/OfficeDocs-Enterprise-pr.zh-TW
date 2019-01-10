---
title: 使用 Office 365 PowerShell 檢視授權與服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 說明如何使用 Office 365 PowerShell 檢視授權的計劃、 服務及 Office 365 組織中可用的授權的相關資訊。
ms.openlocfilehash: 8efc123e2820560b4bd8547f4c99bccae242956f
ms.sourcegitcommit: 96313c3c812bae47819f603af995839f4da034c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "27786149"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="bf070-103">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="bf070-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="bf070-104">**摘要：** 說明如何使用 Office 365 PowerShell 檢視授權的計劃、 服務及 Office 365 組織中可用的授權的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf070-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="bf070-105">每個 Office 365 訂閱包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="bf070-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="bf070-p101">**授權計劃**這些也稱為是授權方案或 Office 365 計劃。授權方案定義使用者可用的 Office 365 服務。您的 Office 365 訂閱可能包含多個授權方案。範例的授權方案就是 Office 365 企業版 E3。</span><span class="sxs-lookup"><span data-stu-id="bf070-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="bf070-p102">**服務**這些也稱為是服務計劃。服務是 Office 365 產品、 功能及可用功能的每個授權的計畫，例如 Exchange Online 與 Office Professional Plus。使用者可以從不同的授權方案所授與不同的服務權限指派給他們的多個授權。</span><span class="sxs-lookup"><span data-stu-id="bf070-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="bf070-p103">**授權**每個授權方案包含您所購買的授權數。指派授權給使用者，以便他們可以使用 Office 365 服務授權方案所定義。每個使用者帳戶需要從一個授權計劃至少一個授權，讓他們可以登入 Office 365 並使用的服務。</span><span class="sxs-lookup"><span data-stu-id="bf070-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="bf070-p104">您可以使用 Office 365 PowerShell Office 365 組織中檢視可用的授權方案、 授權及服務的相關的詳細資料。如需產品、 功能及不同 Office 365 訂閱中可用的服務的詳細資訊，請參閱[Office 365 計劃選項](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="bf070-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bf070-118">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf070-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="bf070-119">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="bf070-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="bf070-120">若要檢視目前的授權方案和每種計劃可用授權的摘要資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bf070-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="bf070-121">結果包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="bf070-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="bf070-p105">**Skupartnumber 劃：** 會顯示您的組織可用的授權方案。例如，`ENTERPRISEPACK`是 Office 365 企業版 E3 系統名稱。</span><span class="sxs-lookup"><span data-stu-id="bf070-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="bf070-124">**啟用：** 您已為特定的授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="bf070-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="bf070-125">**ConsumedUnits:** 您已從特定的授權方案指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="bf070-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="bf070-126">若要檢視關於所有授權計劃中都可用的 Office 365 服務的詳細資訊，請先顯示授權計劃的清單。</span><span class="sxs-lookup"><span data-stu-id="bf070-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="bf070-127">下一步] 儲存在變數中的授權計劃資訊。</span><span class="sxs-lookup"><span data-stu-id="bf070-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="bf070-128">下一步] 顯示特定授權計劃中的服務。</span><span class="sxs-lookup"><span data-stu-id="bf070-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="bf070-129">\<索引 > 會指定從顯示的授權方案的列數的整數`Get-AzureADSubscribedSku | Select SkuPartNumber`command 減 1。</span><span class="sxs-lookup"><span data-stu-id="bf070-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="bf070-130">例如，如果顯示`Get-AzureADSubscribedSku | Select SkuPartNumber`命令這是：</span><span class="sxs-lookup"><span data-stu-id="bf070-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="bf070-131">然後命令以顯示 ENTERPRISEPREMIUM 授權方案的服務是：</span><span class="sxs-lookup"><span data-stu-id="bf070-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="bf070-p106">ENTERPRISEPREMIUM 是第三列。因此的索引值是 (3-1） 或 2。</span><span class="sxs-lookup"><span data-stu-id="bf070-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="bf070-134">如需授權計劃 （也稱為產品名稱）、 其包含的服務計劃和其對應的易記名稱的完整清單，請參閱[產品名稱和授權的服務計劃識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="bf070-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="bf070-135">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="bf070-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="bf070-136">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="bf070-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="bf070-p107">PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bf070-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="bf070-140">若要檢視目前的授權方案和每種計劃可用授權的摘要資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bf070-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="bf070-141">結果包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="bf070-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="bf070-p108">**AccountSkuId:** 使用下列的語法來顯示您的組織可用的授權方案`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_ 為您提供當您在 Office 365 中註冊並為您的組織是唯一的值。_<LicensingPlan>_ 值是每個人都相同。例如，在此值`litwareinc:ENTERPRISEPACK`、 公司名稱是`litwareinc`、 和授權的計劃名稱`ENTERPRISEPACK`，這是 Office 365 企業版 E3 系統名稱。</span><span class="sxs-lookup"><span data-stu-id="bf070-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="bf070-146">**ActiveUnits:** 您已為特定的授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="bf070-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="bf070-147">**WarningUnits:** 您尚未已更新，並將期限 30 天的寬限期期間的授權方案中的授權數目。</span><span class="sxs-lookup"><span data-stu-id="bf070-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="bf070-148">**ConsumedUnits:** 您已從特定的授權方案指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="bf070-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="bf070-149">若要檢視關於所有授權計劃中都可用的 Office 365 服務的詳細資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bf070-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="bf070-p109">下表顯示 Office 365 服務計劃和最常見的服務及其易記名稱。您的服務計劃清單可能會不同。</span><span class="sxs-lookup"><span data-stu-id="bf070-p109">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="bf070-152">**服務計劃**</span><span class="sxs-lookup"><span data-stu-id="bf070-152">**Service plan**</span></span>|<span data-ttu-id="bf070-153">**描述**</span><span class="sxs-lookup"><span data-stu-id="bf070-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="bf070-154">Sway</span><span class="sxs-lookup"><span data-stu-id="bf070-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="bf070-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bf070-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="bf070-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="bf070-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="bf070-157">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="bf070-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="bf070-158">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="bf070-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="bf070-159">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="bf070-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="bf070-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="bf070-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="bf070-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf070-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="bf070-162">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="bf070-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="bf070-163">如需授權計劃 （也稱為產品名稱）、 其包含的服務計劃和其對應的易記名稱的完整清單，請參閱[產品名稱和授權的服務計劃識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="bf070-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="bf070-164">若要檢視特定的授權方案中可用的 Office 365 服務相關的詳細資訊，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="bf070-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="bf070-165">此範例會顯示 litwareinc: enterprisepack (Office 365 企業版 E3) 的授權方案中可用的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="bf070-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="bf070-166">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="bf070-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="bf070-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf070-167">See also</span></span>


[<span data-ttu-id="bf070-168">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="bf070-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="bf070-169">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="bf070-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="bf070-170">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf070-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
