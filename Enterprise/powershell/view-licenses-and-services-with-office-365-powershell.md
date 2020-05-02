---
title: 使用 Office 365 PowerShell 檢視授權與服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 說明如何使用 Office 365 PowerShell 來查看您的 Office 365 組織中提供的授權方案、服務和授權的相關資訊。
ms.openlocfilehash: a130faef640e875bde864ff26e46863e82f6df7a
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004136"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="68f6c-103">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="68f6c-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="68f6c-104">每個 Office 365 訂閱包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="68f6c-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="68f6c-105">**授權方案**這些也稱為授權計畫或 Office 365 方案。</span><span class="sxs-lookup"><span data-stu-id="68f6c-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="68f6c-106">授權計畫定義使用者可以使用的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="68f6c-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="68f6c-107">您的 Office 365 訂閱可能包含多個授權計畫。</span><span class="sxs-lookup"><span data-stu-id="68f6c-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="68f6c-108">授權方案範例是 Office 365 Enterprise E3。</span><span class="sxs-lookup"><span data-stu-id="68f6c-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="68f6c-109">**服務**這些也稱為服務方案。</span><span class="sxs-lookup"><span data-stu-id="68f6c-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="68f6c-110">服務是每個授權計畫中可用的 Office 365 產品、功能和功能，例如 Exchange Online 和 Office 365 ProPlus。</span><span class="sxs-lookup"><span data-stu-id="68f6c-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office 365 ProPlus.</span></span> <span data-ttu-id="68f6c-111">使用者可以將多個授權指派給他們，以不同授權方案授與不同服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="68f6c-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="68f6c-112">**授權**每個授權方案都包含您購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="68f6c-112">**Licenses** Each licensing plan contains the number of licenses that you purchased.</span></span> <span data-ttu-id="68f6c-113">您可以將授權指派給使用者，讓他們可以使用授權方案所定義的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="68f6c-113">You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan.</span></span> <span data-ttu-id="68f6c-114">每個使用者帳戶至少需要一個授權方案的授權，這樣他們才能登入 Office 365 並使用服務。</span><span class="sxs-lookup"><span data-stu-id="68f6c-114">Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="68f6c-115">您可以使用 Office 365 PowerShell 來查看 Office 365 組織中可用授權方案、授權及服務的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="68f6c-115">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization.</span></span> <span data-ttu-id="68f6c-116">如需有關不同 Office 365 訂閱中可用之產品、功能和服務的詳細資訊，請參閱[Office 365 方案選項](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-116">For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="68f6c-117">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="68f6c-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="68f6c-118">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="68f6c-119">若要查看您目前授權計畫的摘要資訊，以及每個計畫可用的授權，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="68f6c-119">To view summary information about your current licensing plans and the available licenses for each plan, run this command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="68f6c-120">結果包含：</span><span class="sxs-lookup"><span data-stu-id="68f6c-120">The results contain:</span></span>
  
- <span data-ttu-id="68f6c-121">**SkuPartNumber：** 顯示您的組織可用的授權方案。</span><span class="sxs-lookup"><span data-stu-id="68f6c-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="68f6c-122">例如， `ENTERPRISEPACK` 「Office 365 企業版 E3」的授權方案名稱。</span><span class="sxs-lookup"><span data-stu-id="68f6c-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="68f6c-123">**已啟用：** 您為特定授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="68f6c-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="68f6c-124">**ConsumedUnits：** 您已從特定授權方案中指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="68f6c-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="68f6c-125">若要查看所有授權方案中可用之 Office 365 服務的詳細資訊，請先顯示您的授權方案清單。</span><span class="sxs-lookup"><span data-stu-id="68f6c-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="68f6c-126">接下來，將授權計畫資訊儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="68f6c-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="68f6c-127">接下來，顯示特定授權方案中的服務。</span><span class="sxs-lookup"><span data-stu-id="68f6c-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="68f6c-128">\<index> 是整數，它會指定授權方案的列數，從`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的顯示減1。</span><span class="sxs-lookup"><span data-stu-id="68f6c-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="68f6c-129">例如，如果`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的顯示如下：</span><span class="sxs-lookup"><span data-stu-id="68f6c-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="68f6c-130">顯示 ENTERPRISEPREMIUM 授權方案之服務的命令如下：</span><span class="sxs-lookup"><span data-stu-id="68f6c-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="68f6c-131">ENTERPRISEPREMIUM 是第三列。</span><span class="sxs-lookup"><span data-stu-id="68f6c-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="68f6c-132">因此，索引值為（3-1）或2。</span><span class="sxs-lookup"><span data-stu-id="68f6c-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="68f6c-133">如需授權方案（也稱為產品名稱）、其包含的服務方案及其對應的易記名稱的完整清單，請參閱[產品名稱和服務方案識別碼取得授權](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="68f6c-134">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="68f6c-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="68f6c-135">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="68f6c-136">PowerShell 指令碼可供使用，會自動執行本主題中所述的程序。</span><span class="sxs-lookup"><span data-stu-id="68f6c-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="68f6c-137">具體說來，此腳本可讓您在 Office 365 組織中查看及停用服務，包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="68f6c-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="68f6c-138">如需詳細資訊，請參閱[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="68f6c-139">若要查看您目前授權計畫的摘要資訊，以及每個計畫可用的授權，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="68f6c-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="68f6c-140">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="68f6c-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="68f6c-141">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="68f6c-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="68f6c-142">結果包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="68f6c-142">The results contain the following information:</span></span>
  
- <span data-ttu-id="68f6c-143">**AccountSkuId：** 使用語法`<CompanyName>:<LicensingPlan>`顯示組織可用的授權方案。</span><span class="sxs-lookup"><span data-stu-id="68f6c-143">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.</span></span>  <span data-ttu-id="68f6c-144">CompanyName>是您在 Office 365 中登記時所提供的值，且對您的組織而言是唯一的。 _ \< _</span><span class="sxs-lookup"><span data-stu-id="68f6c-144">_\<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="68f6c-145">所有人的_ \<LicensingPlan>_ 值都是相同的。</span><span class="sxs-lookup"><span data-stu-id="68f6c-145">The _\<LicensingPlan>_ value is the same for everyone.</span></span> <span data-ttu-id="68f6c-146">例如，在值`litwareinc:ENTERPRISEPACK`、公司名稱`litwareinc`以及授權方案名稱`ENTERPRISEPACK`，也就是 Office 365 企業版 E3 的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="68f6c-146">For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="68f6c-147">**ActiveUnits：** 您為特定授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="68f6c-147">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="68f6c-148">**WarningUnits：** 授權方案中尚未更新，且30天寬限期後會到期的授權數目。</span><span class="sxs-lookup"><span data-stu-id="68f6c-148">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="68f6c-149">**ConsumedUnits：** 您已從特定授權方案中指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="68f6c-149">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="68f6c-150">若要查看所有授權方案中可用之 Office 365 服務的詳細資料，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="68f6c-150">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="68f6c-151">下表顯示 Office 365 服務方案及其最常見服務的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="68f6c-151">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="68f6c-152">您的服務方案清單可能不同。</span><span class="sxs-lookup"><span data-stu-id="68f6c-152">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="68f6c-153">**服務計劃**</span><span class="sxs-lookup"><span data-stu-id="68f6c-153">**Service plan**</span></span>|<span data-ttu-id="68f6c-154">**描述**</span><span class="sxs-lookup"><span data-stu-id="68f6c-154">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="68f6c-155">Sway</span><span class="sxs-lookup"><span data-stu-id="68f6c-155">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="68f6c-156">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="68f6c-156">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="68f6c-157">Yammer</span><span class="sxs-lookup"><span data-stu-id="68f6c-157">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="68f6c-158">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="68f6c-158">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="68f6c-159">Office 365 專業增強版</span><span class="sxs-lookup"><span data-stu-id="68f6c-159">Office 365 ProPlus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="68f6c-160">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="68f6c-160">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="68f6c-161">辦公室</span><span class="sxs-lookup"><span data-stu-id="68f6c-161">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="68f6c-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="68f6c-162">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="68f6c-163">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="68f6c-163">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="68f6c-164">如需授權方案（也稱為產品名稱）、其包含的服務方案及其對應的易記名稱的完整清單，請參閱[產品名稱和服務方案識別碼取得授權](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。</span><span class="sxs-lookup"><span data-stu-id="68f6c-164">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="68f6c-165">若要查看特定授權方案中可用之 Office 365 服務的詳細資料，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="68f6c-165">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="68f6c-166">此範例會顯示 litwareinc:ENTERPRISEPACK （Office 365 企業版 E3）授權計畫中可用的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="68f6c-166">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a><span data-ttu-id="68f6c-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f6c-167">See also</span></span>

[<span data-ttu-id="68f6c-168">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="68f6c-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="68f6c-169">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="68f6c-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="68f6c-170">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="68f6c-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
