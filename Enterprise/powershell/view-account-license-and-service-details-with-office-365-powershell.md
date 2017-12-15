---
title: "使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- DecEntMigration
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。"
ms.openlocfilehash: 59a6444e0f6618fd837e8eae567661499e795c69
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="bb8f9-103">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="bb8f9-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="bb8f9-104">**摘要：**說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="bb8f9-p101">在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。不過，使用者可能無法存取所有目前已指派給他們的授權中可用的服務。您可以使用 Office 365 PowerShell 檢視的使用者帳戶之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="bb8f9-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="bb8f9-108">Before you begin</span></span>
<span data-ttu-id="bb8f9-109"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="bb8f9-109"></span></span>

- <span data-ttu-id="bb8f9-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bb8f9-112">使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`尋找下列資訊：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-112">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="bb8f9-113">您的組織可用的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-113">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="bb8f9-114">每個授權計劃中可用的服務，以及其列出的順序 (索引編號)。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-114">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="bb8f9-115">如需授權方案、 授權、 及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-115">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bb8f9-116">使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`尋找的授權指派給使用者和的順序，其中所列 （索引編號）。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-116">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="bb8f9-117">如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-117">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="bb8f9-118">簡短版本 (不含說明的指示)</span><span class="sxs-lookup"><span data-stu-id="bb8f9-118">The short version (instructions without explanations)</span></span>
<span data-ttu-id="bb8f9-119"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="bb8f9-119"></span></span>

<span data-ttu-id="bb8f9-120">若要檢視所有使用者有權存取 Office 365 PowerShell 服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-120">To view all the Office 365 PowerShell services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="bb8f9-p103">此範例會顯示使用者 BelindaN@litwareinc.com 具有存取服務。這會顯示指派至她帳戶的所有授權與相關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="bb8f9-123">本範例顯示使用者 BelindaN@litwareinc.com 有權存取的服務，從指派給其帳戶的第一個授權 (索引編號為 0) 開始。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-123">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="bb8f9-124">若要尋找已啟用或未啟用特定服務的所有授權使用者，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-124">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="bb8f9-125">這些範例使用下列資訊：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-125">These examples use the following information:</span></span>
  
- <span data-ttu-id="bb8f9-126">提供我們感興趣的 Office 365 服務的存取授權已指派給 （索引編號為 0） 的所有使用者的第一個授權。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-126">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="bb8f9-p104">我們感興趣的 Office 365 服務是 Skype 商務 Online 與 Exchange Online。相關聯的授權方案授權，Skype 商務 online 是 6 列出的服務 （索引編號為 5），與 Exchange Online 是 9th 服務列出 （索引編號為 8）。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="bb8f9-129">此範例會傳回所有已獲授權的商務 Online 與 Exchange Online Skype 所啟用的使用者。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-129">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="bb8f9-130">此範例會傳回所有已獲授權的使用者未啟用 Skype 商務 Online 或 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-130">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="bb8f9-131">冗長版本 (包含詳細說明的指示)</span><span class="sxs-lookup"><span data-stu-id="bb8f9-131">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="bb8f9-132"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="bb8f9-132"></span></span>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a><span data-ttu-id="bb8f9-133">尋找 Office 365 PowerShell 服務使用者有權存取</span><span class="sxs-lookup"><span data-stu-id="bb8f9-133">Find the Office 365 PowerShell services that a user has access to</span></span>

<span data-ttu-id="bb8f9-p105">務必做了明顯改善您知道哪些使用者已核發給 Office 365 授權和哪些使用者尚未。（請參閱[檢視授權和未授權使用者與 Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)如需詳細資訊）。不過，只要擁有 [Office 365 授權不會告訴您不要有關該使用者可以實際怎麼與 Office 365。可以一次使用 Exchange Online 或 Skype 商務 online 吗？可以這位使用者存取 SharePoint Online 吗？沒有他就可以存取 Office Professional Plus 吗？具有授權只是表示使用者有可能會存取這些服務。不過，使用者可用的功能取決於已啟用其授權的服務。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p105">It's obviously important for you to know which users have been issued Office 365 licenses and which users haven't. (See the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) for more information). However, simply having an Office 365 license doesn't tell you anything about what that user can actually do with Office 365. Can he or she use Exchange Online or Skype for Business Online? Can this user access SharePoint Online? Does he or she have access to Office Professional Plus? Having a license simply means that the user has the potential to access these services. However, the capabilities available to a user depend on the services that have been enabled on his or her license.</span></span>
  
<span data-ttu-id="bb8f9-p106">那要如何判斷其 Office 365 功能的使用者具有存取權？若要我們必須執行類似這一個命令：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p106">So how can we determine which Office 365 features a user has access to? To do that we need to run a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

<span data-ttu-id="bb8f9-144">在此命令中，我們將使用**Get-msoluser** cmdlet 可傳回 BelindaN@litwareinc.com 的帳戶資訊。我們已傳回該資訊，我們再帳戶將資料傳送到**Select-object**指令程式並要求**Select-object**來 「 展開 」**授權**屬性的值：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-144">In this command, we're using the **Get-MsolUser** cmdlet to return information about the account BelindaN@litwareinc.com. Once we've returned that information, we then pipe the account data to the **Select-Object** cmdlet and ask **Select-Object** to "expand" the value of the **Licenses** property:</span></span>
  
 `Select-Object -ExpandProperty Licenses`
  
<span data-ttu-id="bb8f9-p107">為什麼這麼做？依預設，**授權**屬性只能告訴我們授權套件 Belinda 的授權來源的名稱：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p107">Why do we do that? Well, by default the **Licenses** property only tells us the name of the licensing pack where Belinda's license came from:</span></span>
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

<span data-ttu-id="bb8f9-147">「 展開 」**授權**屬性可為我們一點點的資訊：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-147">"Expanding" the **Licenses** property gives us a little more information:</span></span>
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

<span data-ttu-id="bb8f9-148">然後藉由展開**ServiceStatus**屬性可以收到更多資訊：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-148">And then by expanding the **ServiceStatus** property we can get back even more information:</span></span>
  
|<span data-ttu-id="bb8f9-149">服務計劃 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-149">****Service plan****</span></span>|<span data-ttu-id="bb8f9-150">描述 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-150">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="bb8f9-151">Sway</span><span class="sxs-lookup"><span data-stu-id="bb8f9-151">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="bb8f9-152">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bb8f9-152">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-153">Yammer</span><span class="sxs-lookup"><span data-stu-id="bb8f9-153">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-154">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="bb8f9-154">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="bb8f9-155">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="bb8f9-155">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="bb8f9-156">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-156">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="bb8f9-157">Office Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-157">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="bb8f9-158">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-158">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-159">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="bb8f9-159">Exchange Online Plan 2</span></span>  <br/> |
   
> [!NOTE]
> <span data-ttu-id="bb8f9-p108">您說這樣要輸入太多吗？如果您可以一點的 Windows PowerShell 含糊性，您可以忍受命令的這個精簡的版本改： >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p108">You say that's too much typing? Well, if you can put up with a little Windows PowerShell obtuseness, you can run this condensed version of the command instead: >  `(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`</span></span>
  
<span data-ttu-id="bb8f9-p109">您想知道，我們可以 「 展開 」**授權**屬性因為**授權**是多重值的屬性： 它是可儲存多個值的單一屬性。當我們展開屬性值我們只是向下切入至取得這些額外的值，預設不會顯示於螢幕上。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p109">In case you're wondering, we can "expand" the **Licenses** property because **Licenses** is a multivalued property: it's a single property that can store multiple values. When we expand a property value we simply drill down to get at these additional values that, by default, are not displayed onscreen.</span></span>
  
> [!NOTE]
> <span data-ttu-id="bb8f9-p110">您應該要知道值是多重值的屬性那要如何？以找出，請嘗試執行如下的命令： > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> **get-member**指令程式會傳回物件本身 ； 的詳細資訊在此例中屬性的相關資訊值的使用者帳戶物件組成。以下是 [ **Get-member**有**授權**屬性的看法： > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> 如果屬性定義對於合集有一些涵義 (在此例中`System.Collections.Generic.List`) 那麼您會知道您正在處理一個多重值屬性。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p110">So how are you supposed to know that a value is a multivalued property? Well, to find that out, try running a command similar to this: >  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> The **Get-member** cmdlet returns information about the object itself; in this case, information about the property values that make up a user account object. Here's what **Get-Member** has to say about the **Licenses** property:>  `Licenses Property System.Collections.Generic.List[Microsoft.On...`> If the property definition says something about collections (in this case,  `System.Collections.Generic.List`) then you know you're dealing with a multivalued property.</span></span> 
  
<span data-ttu-id="bb8f9-p111">所以什麼意思此？若要回答，我們先看另一個**Get-msoluser** cmdlet 所傳回的資訊：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p111">So what does all this mean? To answer that, let's first take another look at the information returned by the **Get-MsolUser** cmdlet:</span></span>
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

<span data-ttu-id="bb8f9-169">與我們也看看一下表格，這些詭異命名服務計畫確實代表什麼：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-169">And let's also take a look at a table that explains what these oddly-named service plans really represent:</span></span>
  
|<span data-ttu-id="bb8f9-170">服務計劃 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-170">****Service plan****</span></span>|<span data-ttu-id="bb8f9-171">描述 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-171">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="bb8f9-172">Sway</span><span class="sxs-lookup"><span data-stu-id="bb8f9-172">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="bb8f9-173">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bb8f9-173">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-174">Yammer</span><span class="sxs-lookup"><span data-stu-id="bb8f9-174">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-175">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="bb8f9-175">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="bb8f9-176">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="bb8f9-176">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="bb8f9-177">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-177">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="bb8f9-178">Office Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-178">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="bb8f9-179">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-179">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-180">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="bb8f9-180">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="bb8f9-p112">所有的該你吗？ `MCOSTANDARD`剛程式設計的內部名稱 Skype 為線上商務時`OFFICESUSBCRIPTION`只是內部程式設計名稱 Office Professional plus。不在全球的最直覺性項重點但只要您保留此表格方便使用您將不會有許多問題時有使用 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p112">Got all that?  `MCOSTANDARD` is just an internal programming name for Skype for Business Online, while `OFFICESUSBCRIPTION` is just the internal programming name for Office Professional Plus. It's not the most intuitive thing in the world, but as long as you keep this table handy you won't have many problems when it comes to working with Office 365 services.</span></span>
  
<span data-ttu-id="bb8f9-p113">但等待： 沒有更多。當我們學會文章[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)，如果**ProvisioningStatus**設為`Success`這表示已完全啟用服務 ；例如如果`MCOSTANDARD`設為`Success`這表示使用者可以存取 Skype 商務 online。如果**ProvisioningStatus**設為`PendingInput`也就是說 Office 365 仍在處理服務要求;不過，使用者通常可以登入並要求完成處理的同時存取服務。(`YAMMER_ENTERPRISE`永遠會顯示為`PendingInput`，但 [確定]： 可將不會停止登入 Yammer 中的使用者)。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p113">But wait: there's more. As we learned in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md), if the **ProvisioningStatus** is set to `Success` that means that the service has been fully enabled; for example if `MCOSTANDARD` is set to `Success` that means that the user can access Skype for Business Online. If the **ProvisioningStatus** is set to `PendingInput` that means that Office 365 is still processing the service request; however, the user can typically log on and access the service while the request finishes processing. ( `YAMMER_ENTERPRISE` will always be shown as `PendingInput`, but that's OK: that won't stop a user from logging on to Yammer).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="bb8f9-188">使用者可安裝和啟動新的 Office Professional Plus 安裝時`OFFICESUBSCRIPTION`處於`PendingInput`狀態。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-188">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="bb8f9-189">與不用說，是 [服務設定為 「 `Disabled` ，表示此服務有問題且無法供使用者。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-189">And, needless to say, is a service is set to  `Disabled` that means that the service in question is not available to the user.</span></span>
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a><span data-ttu-id="bb8f9-190">尋找具有特定 Office 365 PowerShell 服務存取權的使用者</span><span class="sxs-lookup"><span data-stu-id="bb8f9-190">Find users that have access to specific Office 365 PowerShell services</span></span>

<span data-ttu-id="bb8f9-p114">在不同的文章，我們看到如何使用 Office 365 PowerShell 停用使用者存取服務。（如果您未接的文章，請參閱[停用 Office 365 powershell 的服務存取權](disable-access-to-services-with-office-365-powershell.md)）。之負責人明顯的問題： 是否有任何方法來決定哪些*使用者*(也就是一個以上的使用者) 已啟用或停用的服務？</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p114">In a separate article, we saw how you can use Office 365 PowerShell to disable user access to services. (If you missed that article, see [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). That leads to an obvious question: is there any way to determine which  *users*  (that is, more than one user) have which services enabled or disabled?</span></span>
  
<span data-ttu-id="bb8f9-p115">我們已希望希望有人會。若要回答這個問題，請檢閱我們先看文章[檢視授權和 services 與 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)中的我們唯一可用的授權方案的服務的表格`litwareinc:ENTERPRISEPACK`：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p115">We were hoping that someone would ask that. In order to answer that question, let's review the table of services that we first looked at in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) for our only available licensing plan `litwareinc:ENTERPRISEPACK`:</span></span>
  
|<span data-ttu-id="bb8f9-196">服務計劃 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-196">****Service plan****</span></span>|<span data-ttu-id="bb8f9-197">描述 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-197">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="bb8f9-198">Sway</span><span class="sxs-lookup"><span data-stu-id="bb8f9-198">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="bb8f9-199">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bb8f9-199">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-200">Yammer</span><span class="sxs-lookup"><span data-stu-id="bb8f9-200">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-201">Azure 版權管理 (RMS)</span><span class="sxs-lookup"><span data-stu-id="bb8f9-201">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="bb8f9-202">Office 專業增強版</span><span class="sxs-lookup"><span data-stu-id="bb8f9-202">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="bb8f9-203">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-203">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="bb8f9-204">Office Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-204">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="bb8f9-205">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bb8f9-205">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="bb8f9-206">Exchange Online Plan 2</span><span class="sxs-lookup"><span data-stu-id="bb8f9-206">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="bb8f9-p116">回想一下可能、 服務計劃只不過是一項產品; 內部程式設計名稱例如， `OFFICESUBSCRIPTION`，其中 [名稱] 是 Office Professional Plus 的內部程式設計名稱。如果`OFFICESUBSCRIPTION`顯示成`SUCCESS`於使用者的服務計劃，然後這表示使用者可以存取 Office Professional Plus。如果`EXCHANGE_S_ENTERPRISE`已列為`DISABLED`這表示使用者無法使用 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p116">As you might recall, the service plan is nothing more than the internal programming name for a product; for example,  `OFFICESUBSCRIPTION`, to name one, is the internal programming name for Office Professional Plus. If  `OFFICESUBSCRIPTION` shows up as `SUCCESS` on a user's service plan, then that means that the user is allowed to access Office Professional Plus. If `EXCHANGE_S_ENTERPRISE` is listed as `DISABLED` that means the user can't use Exchange Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="bb8f9-210">使用者可安裝和啟動新的 Office Professional Plus 安裝時`OFFICESUBSCRIPTION`處於`PendingInput`狀態。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-210">Users can install and activate a new Office Professional Plus installation while  `OFFICESUBSCRIPTION` is in the `PendingInput` state.</span></span>
  
<span data-ttu-id="bb8f9-p117">現在是時間所在變得極為重要服務的顯示的順序。Windows PowerShell 將每個項目清單中的索引編號。第一個項目是 0 下, 一個項目是 1，依此類推。結果是下表所述：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p117">Now is the time where the order in which the services appear is extremely important. Windows PowerShell assigns an index number to each entry in the list. The first entry is 0, the next entry is 1, and so on. The results are explained in the following table:</span></span>
  
|<span data-ttu-id="bb8f9-215">索引編號 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-215">****Index number****</span></span>|<span data-ttu-id="bb8f9-216">服務計劃 * * *</span><span class="sxs-lookup"><span data-stu-id="bb8f9-216">****Service plan****</span></span>|
|:-----|:-----|
|<span data-ttu-id="bb8f9-217">0</span><span class="sxs-lookup"><span data-stu-id="bb8f9-217">0</span></span>  <br/> | `SWAY` <br/> |
|<span data-ttu-id="bb8f9-218">1</span><span class="sxs-lookup"><span data-stu-id="bb8f9-218">1</span></span>  <br/> | `INTUNE_O365` <br/> |
|<span data-ttu-id="bb8f9-219">2</span><span class="sxs-lookup"><span data-stu-id="bb8f9-219">2</span></span>  <br/> | `YAMMER_ENTERPRISE` <br/> |
|<span data-ttu-id="bb8f9-220">3</span><span class="sxs-lookup"><span data-stu-id="bb8f9-220">3</span></span>  <br/> | `RMS_S_ENTERPRISE` <br/> |
|<span data-ttu-id="bb8f9-221">4</span><span class="sxs-lookup"><span data-stu-id="bb8f9-221">4</span></span>  <br/> | `OFFICESUBSCRIPTION` <br/> |
|<span data-ttu-id="bb8f9-222">5</span><span class="sxs-lookup"><span data-stu-id="bb8f9-222">5</span></span>  <br/> | `MCOSTANDARD` <br/> |
|<span data-ttu-id="bb8f9-223">6</span><span class="sxs-lookup"><span data-stu-id="bb8f9-223">6</span></span>  <br/> | `SHAREPOINTWAC` <br/> |
|<span data-ttu-id="bb8f9-224">7</span><span class="sxs-lookup"><span data-stu-id="bb8f9-224">7</span></span>  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|<span data-ttu-id="bb8f9-225">8</span><span class="sxs-lookup"><span data-stu-id="bb8f9-225">8</span></span>  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
<span data-ttu-id="bb8f9-226">如您所見，`SWAY`第一個服務列，讓它會取得指派 0 的索引編號。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-226">As you can see,  `SWAY` is the first service listed, so it gets assigned index number 0.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="bb8f9-p118">為什麼要選擇 0 及 1 不？這是程式設計的事。程式設計語言中的索引會告訴您最項目"位移"一開始的陣列。第一個項目陣列的*為*開頭，所以其 offset 為 0。第二個項目是陣列的 1 個項目一開始，所以其位移是陣列的 1。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p118">Why 0 and not 1? That's a programming thing. In programming languages indices tell you how far an item is "offset" from the beginning of the array. The first item  *is*  the beginning of the array, so its offset is 0. The second item is 1 item from the beginning of the array, so its offset is 1.</span></span>
  
<span data-ttu-id="bb8f9-p119">我們嘗試範例。假設我們想尚未啟用 Exchange Online 的所有已獲授權使用者的清單。若要這樣做，我們可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p119">Let's try an example. Suppose we'd like a list of all the licensed users who have not been enabled for Exchange Online. To do that, we can use the following command:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="bb8f9-p120">不可否認，即難懂的外觀的一點命令，讓我們需要數分鐘來說明其運作方式。這是實際上兩組件] 命令，與第一個部分是很簡單： 我們使用**Get-msoluser** cmdlet 可傳回所有適用的 Office 365 使用者的集合 （已獲授權和未授權）：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p120">Admittedly, that's a cryptic-looking little command, so let's take a minute to explain how it works. This is actually a two-part command, and the first part is very simple: we use the **Get-MsolUser** cmdlet to return a collection of all our Office 365 users (both licensed and unlicensed):</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="bb8f9-p121">然後將該資訊傳送到**Where-object**指令程式。**Where-object**會通過的所有使用者帳戶並尋找這些帳戶的同時滿足下列準則：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p121">That information is then piped to the **Where-Object** cmdlet. **Where-Object** goes through all the user accounts and looks for those accounts that meet both of the following criteria:</span></span>
  
- <span data-ttu-id="bb8f9-p122">會**尋找 isLicensed**內容等於 ( `-eq`) `True` ( `$true`)。這可讓我們快速清除未授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p122">The **isLicensed** property is equal to ( `-eq`)  `True` ( `$true`). That enables us to weed out the unlicensed users.</span></span>
    
- <span data-ttu-id="bb8f9-p123">**授權 [0] 的值。ServiceStatus [8]。ProvisioningStatus**屬性等於 ( `-eq`) `Disabled`。基於我們立即，此龐大的屬性名稱的重要部分是：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p123">The value of the **Licenses[0].ServiceStatus[8].ProvisioningStatus** property is equal to ( `-eq`)  `Disabled`. For our immediate purposes, the important part of this unwieldy property name is this:</span></span>
    
     `ServiceStatus[8]`
    
    <span data-ttu-id="bb8f9-p124">`[8]`代表 Exchange Online 的索引編號。（我們知道可從查看表格前幾分鐘）。如果我們想要尋找 Skype 商務 online 啟用的所有使用者吗？Skype 商務 Online 的索引編號是的 5 中，因此我們會使用此語法：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p124">The  `[8]` represents the index number for Exchange Online. (We know that from looking at the table a few minutes ago). What if we wanted to find all the users enabled for Skype for Business Online? Well, the index number for Skype for Business Online is 5, so we'd use this syntax:</span></span>
    
     `ServiceStatus[5]`
    
    <span data-ttu-id="bb8f9-247">以此類推。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-247">Etc., etc.</span></span>
    
    <span data-ttu-id="bb8f9-p125">順便一提，`Licenses[0]`表示我們想要查看的授權方案。由於我們測試網域只能有一個授權方案這不會更加它們。但假設我們有已被指派授權從兩個不同的授權方案的使用者。在此情況下，`Licenses[0]`就代表第一個的授權方案和`Licenses[1]`就代表第二個的授權方案。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p125">Incidentally,  `Licenses[0]` indicates the licensing plan that we want to look at. Since our test domain only has one licensing plan this doesn't matter much. But suppose we had a user who has been assigned licenses from two different licensing plans. In that case, `Licenses[0]` would represent the first licensing plan, and `Licenses[1]` would represent the second licensing plan.</span></span>
    
    <span data-ttu-id="bb8f9-252">若要尋找指派給使用者的授權，以及其列出的順序，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-252">To find the licenses that are assigned to a user, and the order in which they are listed, run the following command:</span></span>
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

<span data-ttu-id="bb8f9-p126">您看到這一切的運作方式？Office Professional plus 的索引編號是 4;因此，此命令會傳回所有尚未啟用 Office Professional plus 的使用者清單：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p126">Do you see how this all works? The index number for Office Professional Plus is 4; therefore, this command returns a list of all the users who have not been enabled for Office Professional Plus:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="bb8f9-p127">與如果我們想要的已*啟用*Office Professional Plus 的使用者清單吗？如果您已啟用則**ServiceStatus**您將會是以及`PendingInput`或`Success`;換句話說，將會在**ServiceStatus** *不*等於 ( `-ne`) `Disabled`。這表示我們只需要為取得我們上一個命令並再分出分頁出`-eq`運算子`-ne`運算子：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p127">And what if we wanted a list of users who have been  *enabled*  for Office Professional Plus? Well, if you've been enabled then your **ServiceStatus** will either be `PendingInput` or `Success`; in other words, your **ServiceStatus** will *not*  equal ( `-ne`)  `Disabled`. That means all we have to do is take our previous command and swap out the  `-eq` operator for the `-ne` operator:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="bb8f9-p128">此一說移，該程式碼可能不會 win 許多優點競賽。與真偽會告知、 程式碼可以取得更多纏。例如，假設我們要尋找已啟用這兩個 Skype 商務 Online 與 Exchange Online 的使用者：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p128">As the saying goes, that code probably won't win many beauty contests. And, truth be told, the code can get even more tangled. For example, suppose we want to look for users who have been enabled for both Skype for Business Online and Exchange Online:</span></span>
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="bb8f9-p129">但不要擔心太多關於如何 gnarly 所可能具有的外觀： 重要的是以較少，您可以擷取此資訊。您無法取得在使用 Office 365 系統管理中心這個相同的資訊嗎？理論上，是但，以實用的字詞、 否]。若要取得這個相同的資訊使用 Office 365 系統管理中心於就必須查看每個使用者的授權資訊、 一次一位使用者與然後手動追蹤誰已啟用的*X*及人員還沒有。會將運作，但事實上： 如果您有超過 10 或 11 使用者，您不些為達成此目的。它是方式太面對那樣既繁瑣又耗時。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p129">But don't worry too much about how gnarly that might look: the important thing is that, with relatively little effort, you can retrieve this information. Can't you get at this same information using the Office 365 admin center? In theory, yes but, in practical terms, no. To get at this same information using the Office 365 admin center you'd need to look at the licensing information for each user, one user at a time, and then manually keep track of who'd been enabled for  *X*  and who hadn't. That would work, but let's be honest: if you have more than 10 or 11 users, you're not going to do this. It's way too tedious and time-consuming.</span></span>
  
<span data-ttu-id="bb8f9-267">它會當然，是為什麼我們有 Windows PowerShell： Windows PowerShell 協助讓您免於面對那樣既繁瑣又耗時的工作。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-267">Which, of course, is why we have Windows PowerShell: Windows PowerShell helps save you from tedious and time-consuming tasks such as that.</span></span>
  
<span data-ttu-id="bb8f9-268">我們活躍於它，以下是用於檢視服務資訊的最終命令：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-268">While we're at it, here's the ultimate command for viewing service information:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

<span data-ttu-id="bb8f9-p130">沒錯，是非常瘋狂尋找命令。但是它會建立 CSV 檔案顯示所有使用者及所有其服務狀態。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p130">And yes, that's a very crazy-looking command. But it creates a CSV file showing all of your users and all of their service statuses.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="bb8f9-271">See also</span><span class="sxs-lookup"><span data-stu-id="bb8f9-271">See also</span></span>
<span data-ttu-id="bb8f9-272"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="bb8f9-272"></span></span>

<span data-ttu-id="bb8f9-273">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-273">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="bb8f9-274">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="bb8f9-274">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bb8f9-275">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="bb8f9-275">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bb8f9-276">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="bb8f9-276">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bb8f9-277">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="bb8f9-277">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="bb8f9-278">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="bb8f9-278">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="bb8f9-279">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="bb8f9-279">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="bb8f9-280">ConvertTo Html</span><span class="sxs-lookup"><span data-stu-id="bb8f9-280">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="bb8f9-281">格式清單</span><span class="sxs-lookup"><span data-stu-id="bb8f9-281">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="bb8f9-282">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="bb8f9-282">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="bb8f9-283">選取物件</span><span class="sxs-lookup"><span data-stu-id="bb8f9-283">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="bb8f9-284">Where-Object</span><span class="sxs-lookup"><span data-stu-id="bb8f9-284">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="bb8f9-285">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="bb8f9-285">New to Office 365?</span></span>


||
|:-----|
|<span data-ttu-id="bb8f9-p131">![簡短 LinkedIn 學習圖示](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png)**新增至 Office 365？**        [Office 365 系統管理員及 IT 專業人員](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，傳送給您的 LinkedIn 學習探索免費的視訊課程。</span><span class="sxs-lookup"><span data-stu-id="bb8f9-p131">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   

