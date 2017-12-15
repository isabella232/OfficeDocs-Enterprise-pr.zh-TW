---
title: "使用 Office 365 PowerShell 停用服務存取權"
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "說明如何使用 Office 365 PowerShell 新增或移除組織中的 Office 365 服務使用者的存取權。"
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="68bd5-103">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="68bd5-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="68bd5-104">**摘要：**說明如何使用 Office 365 PowerShell 新增或移除組織中的 Office 365 服務使用者的存取權。</span><span class="sxs-lookup"><span data-stu-id="68bd5-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="68bd5-p101">當 Office 365 帳戶已指派授權的授權方案時、 Office 365 服務是供使用者從該授權。不過，您可以控制使用者可以存取 Office 365 服務。例如，即使授權允許存取 SharePoint Online，您可以停用其存取權。事實上，您可以使用 Office 365 PowerShell 停用的存取權的服務之任何數字：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="68bd5-109">個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="68bd5-109">An individual account.</span></span>
    
- <span data-ttu-id="68bd5-110">一組帳戶。</span><span class="sxs-lookup"><span data-stu-id="68bd5-110">A group of accounts.</span></span>
    
- <span data-ttu-id="68bd5-111">您組織中的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="68bd5-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="68bd5-112">**內容：**[簡短的版本 （不含說明指示）](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[長版本 （詳細說明與指示）](disable-access-to-services-with-office-365-powershell.md#LongVersion)[另請參閱](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="68bd5-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="68bd5-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="68bd5-113">Before you begin</span></span>
<span data-ttu-id="68bd5-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="68bd5-114"></span></span>

- <span data-ttu-id="68bd5-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="68bd5-p103">您可以使用**Get-msolaccountsku**指令程式來檢視您可用的授權方案，以及這些計劃中可用的 Office 365 服務。如需詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="68bd5-119">若要查看前後本主題中的程序的結果，請參閱[檢視帳戶授權及服務的詳細資訊與 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="68bd5-p104">PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="68bd5-123">如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="68bd5-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="68bd5-124">簡短版本 (不含說明的指示)</span><span class="sxs-lookup"><span data-stu-id="68bd5-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="68bd5-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="68bd5-125"></span></span>

<span data-ttu-id="68bd5-p105">本節僅呈現程序，但不提供詳盡或多餘的說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="68bd5-128">若要停用 Office 365 服務讓使用者從單一的授權方案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="68bd5-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="68bd5-129">識別授權的計劃中的非預期的服務使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="68bd5-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="68bd5-130">此範例會建立名為授權計劃中停用的 Office Online 和 SharePoint Online 服務**LicenseOptions**物件`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="68bd5-131">使用步驟 1 中的**LicenseOptions**物件上一或多個使用者。</span><span class="sxs-lookup"><span data-stu-id="68bd5-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="68bd5-132">若要建立已停用服務的新帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="68bd5-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="68bd5-133">本範例會為指派授權及停用步驟 1 所述服務的 Allie Bellew 建立新帳戶。</span><span class="sxs-lookup"><span data-stu-id="68bd5-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="68bd5-134">如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="68bd5-135">若要停用現有授權使用者的服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="68bd5-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="68bd5-136">本範例會停用使用者 BelindaN@litwareinc.com 的服務。</span><span class="sxs-lookup"><span data-stu-id="68bd5-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="68bd5-137">若要停用的所有現有的授權使用者在步驟 1 中所述的服務，指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack** )，顯示名稱，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="68bd5-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="68bd5-138">若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：</span><span class="sxs-lookup"><span data-stu-id="68bd5-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="68bd5-139">**篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="68bd5-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="68bd5-140">此範例會為美國境內銷售部門中的使用者停用服務。</span><span class="sxs-lookup"><span data-stu-id="68bd5-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="68bd5-141">**使用特定帳戶的清單**若要這樣做，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="68bd5-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="68bd5-142">建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="68bd5-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="68bd5-143">在此範例中的文字檔案是 c:\\我的文件\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="68bd5-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="68bd5-144">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="68bd5-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="68bd5-145">當您要指派它們至授權計劃停用 Office 365 服務的使用者，請參閱 ＜[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="68bd5-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="68bd5-146">若要停用使用者的 Office 365 服務中所有可用的授權方案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="68bd5-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="68bd5-147">複製此指令碼，並將其貼入 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="68bd5-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="68bd5-148">為您的環境自訂下列值：</span><span class="sxs-lookup"><span data-stu-id="68bd5-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="68bd5-149">_<UndesirableService>_在這個範例中，我們將使用 Office Online 和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="68bd5-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="68bd5-150">_<Account>_在這個範例中，我們將使用 belindan@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="68bd5-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="68bd5-151">自訂的指令碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="68bd5-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="68bd5-p106">儲存為指令碼`RemoveO365Services.ps1`中更容易尋找的位置。此範例中，我們將儲存在檔案" `C:\\O365 Scripts`"。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="68bd5-154">使用下列命令在 Office 365 PowerShell 中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="68bd5-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="68bd5-155">若要反向的任何這些程序 (亦即重新啟用已停用的服務)、 重新執行此程序，但使用值`$null` _DisabledPlans_參數。</span><span class="sxs-lookup"><span data-stu-id="68bd5-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="68bd5-156">返回頁首</span><span class="sxs-lookup"><span data-stu-id="68bd5-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="68bd5-157">冗長版本 (包含詳細說明的指示)</span><span class="sxs-lookup"><span data-stu-id="68bd5-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="68bd5-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="68bd5-158"></span></span>

<span data-ttu-id="68bd5-p107">根據預設，當您使用 Office 365 PowerShell 發出授權啟用所有服務。與這通常是很好的事： 也就是說您可以快速又輕鬆地將授權指派給使用者而不指定每個服務能夠隨時。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="68bd5-p108">具有說的但它也是如此您可能會想要將您的部分使用者 ； 限制可用服務例如，也許某些使用者應該可以存取 Office Professional Plus] Skype 商務 Online 和 Exchange Online 中，但這些相同的使用者不應該具有存取 SharePoint Online 或 Office Online。您可以限制的方式中的帳戶吗？顯示，您還可以。為了說明此的運作方式，讓我們採取兩步驟方法來處理這個問題：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="68bd5-165">指派給使用者的所有服務會自動都啟用 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="68bd5-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="68bd5-166">執行兩個停用該使用者的指定的服務的 Office 365 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="68bd5-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="68bd5-p109">我們已經已經處理的步驟 1： 我們使用者 (Belinda Newman) 具有存取所有的 Office 365 服務會提供她的 Office 365 授權。不過，我們想要使其沒有 access to SharePoint Online 修改 Belinda 的帳戶 ( `SHAREPOINTENTERPRISE`) 或 Office Online ( `SHAREPOINTWAC`)。但如何我們會假設若要這樣做？</span><span class="sxs-lookup"><span data-stu-id="68bd5-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="68bd5-p110">以下是如何。首先，我們會使用**新 MsolLicenseOptions**指令程式來建立**LicenseOption**物件包含我們想要停用的服務。我們想要停用 Belinda 的案例中`SHAREPOINTENTERPRISE`和`SHAREPOINTWAC`，因此我們會使用此命令：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="68bd5-p111">請參閱如何運作？指定授權方案 ( `litwareinc:ENTERPRISEPACK`)，然後指出每個服務您想要停用，請使用逗號分隔這些服務。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="68bd5-p112">請確定您儲存新的**LicenseOption**物件的變數。在上述範例中，我們使用`$x`、 雖然您可以使用任何有效的 Windows PowerShell 變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="68bd5-177">此時我們可以使用下列命令以停用 Belinda 的存取權的兩個服務：</span><span class="sxs-lookup"><span data-stu-id="68bd5-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="68bd5-p113">不太新潮 here 任一： 我們只要呼叫**Set-msoluserlicense** cmdlet，並包含_LicenseOptions_參數，以及變數 ( `$x`) 包含我們想要停用的計劃。與執行我們看到的內容現在是否我們看一下 Belinda 的授權資訊執行命令： `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`？我們可以看到：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="68bd5-p114">很酷吧吗？然後當然，我們可以執行這個相同的事情給多位使用者如果我們想要。例如，下列命令停用相同的兩項服務的所有我們已獲授權使用者。指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack** )，顯示的名稱，然後執行它們。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="68bd5-p115">請記住 Belinda 仍有有效的 Office 365 授權;它是便是這麼做現在她具有較少的服務存取權。我們停用這兩項服務之前，Belinda 那新聞、 OneDrive 及 SharePoint Online 網站：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![具有 SharePoint 存取權的使用者。](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="68bd5-188">現在，她則無法再使用這些選項：</span><span class="sxs-lookup"><span data-stu-id="68bd5-188">Now those options are no longer available to her:</span></span>
  
![沒有 SharePoint 存取權的使用者。](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="68bd5-190">這正是我們預期會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="68bd5-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="68bd5-p116">如果我們稍後變更適用下列事項： 有可能重新啟用這些服務吗？您答案是肯定。若要重新啟用使用者的所有服務，只是使用此命令來建立下列**LicenseOption**物件：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="68bd5-p117">該命令做什麼？若要開始使用 Windows PowerShell 常數`$null`表示 「 不 」。（或稍有更多技術語言，就表示"null 值"。）為您重新叫用，當我們使用**New MsolLicenseOptions** cmdlet 我們已指定我們想要停用的服務。在此例中，我們不想要任何要停用服務。可能會導致您相信我們可以使用下列項目，我們沒有在此指定_DisabledPlans_參數的值的命令如下命令：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="68bd5-p118">但是，將無法運作。但是，則會產生錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="68bd5-201">幸運地是，將參數值設定為`$null`確實有用：</span><span class="sxs-lookup"><span data-stu-id="68bd5-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="68bd5-202">這些明白表示，當我們執行**Set-msoluserlicense** cmdlet 時，我們告訴**Set-msoluserlicense**我們不想要將任何服務停用 Belinda 的：</span><span class="sxs-lookup"><span data-stu-id="68bd5-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="68bd5-203">並且，相當符合邏輯地，如果沒有任何服務遭到停用，就必定表示所有服務皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="68bd5-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="68bd5-p119">既然您了解這一切的運作方式，讓我們為您示範如何您可以選擇發行授權並停用指定服務及所有具有相同的命令。很酷的聲音，但要不需要真正它： 只在同一個命令中包含_AddLicenses_和_LicenseOptions_參數。換句話說，您先建立**LicenseOption**物件：</span><span class="sxs-lookup"><span data-stu-id="68bd5-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="68bd5-207">而且然後如先前所述，使用_AddLicenses_和_LicenseOptions_參數在您的命令：</span><span class="sxs-lookup"><span data-stu-id="68bd5-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="68bd5-208">該命令會發給 Belinda Newman 一個新的授權，但是在哪些 Skype 授權的商務 Online ( `SHAREPOINTWAC`) 和 SharePoint Online ( `SHAREPOINTENTERPRISE`) 這兩個停用。</span><span class="sxs-lookup"><span data-stu-id="68bd5-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="68bd5-209">返回頁首</span><span class="sxs-lookup"><span data-stu-id="68bd5-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="68bd5-210">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="68bd5-210">New to Office 365?</span></span>
<span data-ttu-id="68bd5-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="68bd5-211"></span></span>

||
|:-----|
|<span data-ttu-id="68bd5-p120">![簡短 LinkedIn 學習圖示](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png)**新增至 Office 365？**        **Office 365 系統管理員及 IT 專業人員**，傳送給您的 LinkedIn 學習探索免費的視訊課程。</span><span class="sxs-lookup"><span data-stu-id="68bd5-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="68bd5-214">See also</span><span class="sxs-lookup"><span data-stu-id="68bd5-214">See also</span></span>
<span data-ttu-id="68bd5-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="68bd5-215"></span></span>

<span data-ttu-id="68bd5-216">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="68bd5-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="68bd5-217">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="68bd5-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="68bd5-218">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="68bd5-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="68bd5-219">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="68bd5-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="68bd5-220">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="68bd5-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="68bd5-221">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="68bd5-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="68bd5-222">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="68bd5-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="68bd5-223">Get-content</span><span class="sxs-lookup"><span data-stu-id="68bd5-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="68bd5-224">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="68bd5-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="68bd5-225">新 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="68bd5-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="68bd5-226">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="68bd5-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="68bd5-227">New-msoluser</span><span class="sxs-lookup"><span data-stu-id="68bd5-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="68bd5-228">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="68bd5-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="68bd5-229">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="68bd5-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="68bd5-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="68bd5-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="68bd5-231">返回頁首</span><span class="sxs-lookup"><span data-stu-id="68bd5-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

