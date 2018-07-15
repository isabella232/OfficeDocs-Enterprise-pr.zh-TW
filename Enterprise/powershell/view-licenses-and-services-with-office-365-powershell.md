---
title: 使用 Office 365 PowerShell 檢視授權與服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2018
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
ms.openlocfilehash: 4ee4a5d0173f97520075f146e50bd234e767cc95
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319254"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="fcc68-103">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="fcc68-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="fcc68-104">**摘要：** 說明如何使用 Office 365 PowerShell 檢視授權的計劃、 服務及 Office 365 組織中可用的授權的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fcc68-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="fcc68-105">每個 Office 365 訂閱包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="fcc68-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="fcc68-p101">**授權計劃**這些也是已知 aslicense 計劃或 Office 365 計劃。授權方案定義使用者可用的 Office 365 服務。您的 Office 365 訂閱可能包含多個授權方案。範例的授權方案就是 Office 365 企業版 E3。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="fcc68-p102">**服務**這些也是已知的 asservice 計劃。服務是 Office 365 產品、 功能及可用功能的每個授權的計畫，例如 Exchange Online 與 Office Professional Plus。使用者可以從不同的授權方案所授與不同的服務權限指派給他們的多個授權。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="fcc68-p103">**授權**每個授權方案包含您所購買的授權數。指派授權給使用者，以便他們可以使用 Office 365 服務授權方案所定義。每個使用者帳戶需要從一個授權計劃至少一個授權，讓他們可以登入 Office 365 並使用的服務。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="fcc68-p104">您可以使用 Office 365 PowerShell Office 365 組織中檢視可用的授權方案、 授權及服務的相關的詳細資料。如需產品、 功能及不同 Office 365 訂閱中可用的服務的詳細資訊，請參閱[Office 365 計劃選項](https://go.microsoft.com/fwlink/p/?LinkId=691147)。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="fcc68-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="fcc68-118">Before you begin</span></span>

- <span data-ttu-id="fcc68-p105">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fcc68-p106">PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="fcc68-124">檢視關於授權計劃與可用授權的資訊</span><span class="sxs-lookup"><span data-stu-id="fcc68-124">View information about licensing plans and the available licenses</span></span>

<span data-ttu-id="fcc68-125">若要檢視目前的授權方案和每種計劃可用授權的摘要資訊，請在 Office 365 PowerShell 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="fcc68-125">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="fcc68-126">結果包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="fcc68-126">The results contain the following information:</span></span>
  
- <span data-ttu-id="fcc68-p107">**AccountSkuId:** 使用下列的語法來顯示您的組織可用的授權方案`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_ 為您提供當您在 Office 365 中註冊並為您的組織是唯一的值。_<LicensingPlan>_ 值是每個人都相同。例如，在此值`litwareinc:ENTERPRISEPACK`、 公司名稱是`litwareinc`、 和授權的計劃名稱`ENTERPRISEPACK`，這是 Office 365 企業版 E3 系統名稱。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p107">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="fcc68-131">**ActiveUnits:** 您已針對特定的授權方案購買的授權數目。</span><span class="sxs-lookup"><span data-stu-id="fcc68-131">**ActiveUnits:** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="fcc68-132">**WarningUnits:** 您尚未已更新，並將期限 30 天的寬限期期間的授權方案中的授權數目。</span><span class="sxs-lookup"><span data-stu-id="fcc68-132">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="fcc68-133">**ConsumedUnits:** 您已從特定的授權方案指派給使用者的授權數目。</span><span class="sxs-lookup"><span data-stu-id="fcc68-133">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="fcc68-134">若要檢視關於所有授權計劃中都可用的 Office 365 服務的詳細資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="fcc68-134">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="fcc68-p108">下表顯示 Office 365 服務計劃和最常見的服務及其易記名稱。您的服務計劃清單可能會不同。如需服務計劃和其好記名稱的完整清單，請連絡[商務使用者的支援選項](https://support.microsoft.com/gp/support-options-for-business)。</span><span class="sxs-lookup"><span data-stu-id="fcc68-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different. For a complete list of service plans and their friendly names, contact [Support options for business users](https://support.microsoft.com/gp/support-options-for-business).</span></span>
  
|<span data-ttu-id="fcc68-138">**服務計劃**</span><span class="sxs-lookup"><span data-stu-id="fcc68-138">**Service plan**</span></span>|<span data-ttu-id="fcc68-139">**描述**</span><span class="sxs-lookup"><span data-stu-id="fcc68-139">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="fcc68-140">Sway</span><span class="sxs-lookup"><span data-stu-id="fcc68-140">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="fcc68-141">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="fcc68-141">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="fcc68-142">Yammer</span><span class="sxs-lookup"><span data-stu-id="fcc68-142">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="fcc68-143">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="fcc68-143">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="fcc68-144">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="fcc68-144">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="fcc68-145">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="fcc68-145">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="fcc68-146">Office Online</span><span class="sxs-lookup"><span data-stu-id="fcc68-146">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="fcc68-147">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fcc68-147">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="fcc68-148">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="fcc68-148">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="fcc68-149">若要檢視特定的授權方案中可用的 Office 365 服務相關的詳細資訊，請使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="fcc68-149">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="fcc68-150">此範例會顯示 litwareinc: enterprisepack (Office 365 企業版 E3) 的授權方案中可用的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="fcc68-150">This example shows the Office 365 services that are available in the  litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="fcc68-151">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="fcc68-151">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="fcc68-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcc68-152">See also</span></span>

- [<span data-ttu-id="fcc68-153">使用 Office 365 PowerShell 檢視經授權與未經授權的使用者</span><span class="sxs-lookup"><span data-stu-id="fcc68-153">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="fcc68-154">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="fcc68-154">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="fcc68-155">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="fcc68-155">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

