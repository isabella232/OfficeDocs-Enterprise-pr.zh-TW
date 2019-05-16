---
title: 使用 Office 365 PowerShell 檢視授權與服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
description: 說明如何使用 Office 365 PowerShell 來檢視有關授權方案、 服務和 Office 365 組織中可用的授權資訊。
ms.openlocfilehash: 9e84797de29337d9414d9a578a98f6799ee816cb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071089"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="1714d-103">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="1714d-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="1714d-104">**摘要：** 說明如何使用 Office 365 PowerShell 來檢視有關授權方案、 服務和 Office 365 組織中可用的授權資訊。</span><span class="sxs-lookup"><span data-stu-id="1714d-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="1714d-105">每個 Office 365 訂閱是由下列元素所組成：</span><span class="sxs-lookup"><span data-stu-id="1714d-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="1714d-106">**授權計劃**這些是所謂的授權方案或 Office 365 計劃。</span><span class="sxs-lookup"><span data-stu-id="1714d-106">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="1714d-107">授權計劃定義使用者可用的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="1714d-107">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="1714d-108">Office 365 訂閱可能包含多個授權計劃。</span><span class="sxs-lookup"><span data-stu-id="1714d-108">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="1714d-109">範例授權計劃將 Office 365 企業版 E3。</span><span class="sxs-lookup"><span data-stu-id="1714d-109">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="1714d-110">**服務**這些是也稱為服務計劃。</span><span class="sxs-lookup"><span data-stu-id="1714d-110">**Services** These are also known as service plans.</span></span> <span data-ttu-id="1714d-111">服務是 Office 365 產品、 功能及可用功能中每個授權計劃，例如 Exchange Online 和 Office 專業增強版。</span><span class="sxs-lookup"><span data-stu-id="1714d-111">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="1714d-112">使用者可以有多個授權指派給他們從不同的授權方案，授與存取權不同的服務。</span><span class="sxs-lookup"><span data-stu-id="1714d-112">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="1714d-113">**授權**每個授權計劃包含您購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1714d-113">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="1714d-114">讓他們可以使用 Office 365 服務所定義的授權方案，您可以指派給使用者的授權。</span><span class="sxs-lookup"><span data-stu-id="1714d-114">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="1714d-115">每個使用者帳戶需要從某個授權計劃的至少一個授權，讓他們可以登入 Office 365，並使用的服務。</span><span class="sxs-lookup"><span data-stu-id="1714d-115">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="1714d-116">您可以使用 Office 365 PowerShell 來檢視 Office 365 組織中的可用授權計劃、 授權及服務的詳細。</span><span class="sxs-lookup"><span data-stu-id="1714d-116">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="1714d-117">如需產品、 功能和不同 Office 365 訂閱中可用的服務的詳細資訊，請參閱 < <b0>Office 365 方案選項</b0>。</span><span class="sxs-lookup"><span data-stu-id="1714d-117">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="1714d-118">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="1714d-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="1714d-119">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="1714d-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="1714d-120">若要檢視您目前的授權方案以及每個方案可用授權的摘要資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1714d-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="1714d-121">結果包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="1714d-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="1714d-122">**Skupartnumber 劃：** 顯示貴組織的可用授權計劃。</span><span class="sxs-lookup"><span data-stu-id="1714d-122">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="1714d-123">例如，`ENTERPRISEPACK`是 Office 365 企業版 E3 授權計劃名稱。</span><span class="sxs-lookup"><span data-stu-id="1714d-123">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="1714d-124">**啟用：** 您已為特定授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1714d-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="1714d-125">**ConsumedUnits:** 您已從特定的授權計劃指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1714d-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="1714d-126">若要檢視 Office 365 服務的可用的授權計劃中的所有相關的詳細資訊，請先顯示一份授權計劃。</span><span class="sxs-lookup"><span data-stu-id="1714d-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="1714d-127">下一步]，儲存在變數中的授權計劃資訊。</span><span class="sxs-lookup"><span data-stu-id="1714d-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="1714d-128">接下來，在特定的授權計劃中顯示的服務。</span><span class="sxs-lookup"><span data-stu-id="1714d-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlans
````

<span data-ttu-id="1714d-129">\<index> 為 integer，指定從顯示的授權計劃中的列數`Get-AzureADSubscribedSku | Select SkuPartNumber`命令，減 1。</span><span class="sxs-lookup"><span data-stu-id="1714d-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="1714d-130">例如，如果顯示`Get-AzureADSubscribedSku | Select SkuPartNumber`命令如下：</span><span class="sxs-lookup"><span data-stu-id="1714d-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="1714d-131">然後命令，以顯示 ENTERPRISEPREMIUM 授權計劃的服務如下：</span><span class="sxs-lookup"><span data-stu-id="1714d-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlans
````

<span data-ttu-id="1714d-132">ENTERPRISEPREMIUM 是第三列。</span><span class="sxs-lookup"><span data-stu-id="1714d-132">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="1714d-133">因此，索引值是 (3-1），或 2。</span><span class="sxs-lookup"><span data-stu-id="1714d-133">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="1714d-134">為授權計劃 （也稱為產品名稱） 的完整清單，其包含的服務計劃和其對應的易記名稱，請參閱[產品名稱和授權的服務方案識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="1714d-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="1714d-135">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="1714d-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="1714d-136">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="1714d-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="1714d-137">PowerShell 指令碼可供使用，會自動執行本主題中所述的程序。</span><span class="sxs-lookup"><span data-stu-id="1714d-137">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="1714d-138">具體而言，指令碼可讓您檢視及停用您 Office 365 組織，包括 Sway 中的服務。</span><span class="sxs-lookup"><span data-stu-id="1714d-138">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="1714d-139">如需詳細資訊，請參閱[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1714d-139">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="1714d-140">若要檢視您目前的授權方案以及每個方案可用授權的摘要資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1714d-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="1714d-141">結果包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="1714d-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="1714d-142">**AccountSkuId:** 藉由使用語法來顯示貴組織的可用授權計劃`<CompanyName>:<LicensingPlan>`。</span><span class="sxs-lookup"><span data-stu-id="1714d-142">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="1714d-143">_<CompanyName>_ 是您提供當您在 Office 365 中註冊，並為您的組織是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="1714d-143">_<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="1714d-144">_<LicensingPlan>_ 值是每個人都相同。</span><span class="sxs-lookup"><span data-stu-id="1714d-144">The _<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="1714d-145">例如，在值`litwareinc:ENTERPRISEPACK`，公司名稱是`litwareinc`，和授權計劃名稱`ENTERPRISEPACK`，也就是 Office 365 企業版 E3 的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="1714d-145">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="1714d-146">**ActiveUnits:** 您已為特定授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1714d-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="1714d-147">**WarningUnits:** 您還沒有更新，及，將會在 30 天寬限期後過期的授權計劃中的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1714d-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="1714d-148">**ConsumedUnits:** 您已從特定的授權計劃指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1714d-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="1714d-149">若要檢視 Office 365 服務的可用的授權計劃中的所有相關的詳細資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1714d-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="1714d-150">下表顯示 Office 365 服務計劃及最常見的服務的好記的名稱。</span><span class="sxs-lookup"><span data-stu-id="1714d-150">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="1714d-151">您的服務計劃清單可能會不同。</span><span class="sxs-lookup"><span data-stu-id="1714d-151">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="1714d-152">**服務計劃**</span><span class="sxs-lookup"><span data-stu-id="1714d-152">**Service plan**</span></span>|<span data-ttu-id="1714d-153">**描述**</span><span class="sxs-lookup"><span data-stu-id="1714d-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="1714d-154">Sway</span><span class="sxs-lookup"><span data-stu-id="1714d-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="1714d-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1714d-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="1714d-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="1714d-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="1714d-157">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="1714d-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="1714d-158">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="1714d-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="1714d-159">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="1714d-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="1714d-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="1714d-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="1714d-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1714d-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="1714d-162">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="1714d-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="1714d-163">為授權計劃 （也稱為產品名稱） 的完整清單，其包含的服務計劃和其對應的易記名稱，請參閱[產品名稱和授權的服務方案識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="1714d-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="1714d-164">若要檢視特定的授權計劃中提供的 Office 365 服務相關的詳細資訊，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="1714d-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="1714d-165">本範例顯示 litwareinc: enterprisepack (Office 365 企業版 E3) 授權計劃中提供的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="1714d-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="1714d-166">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="1714d-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="1714d-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1714d-167">See also</span></span>


[<span data-ttu-id="1714d-168">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="1714d-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="1714d-169">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="1714d-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1714d-170">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1714d-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
