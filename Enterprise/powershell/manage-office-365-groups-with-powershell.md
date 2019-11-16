---
title: 使用 PowerShell 管理 Office 365 群組
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 了解如何在 Microsoft PowerShell 中的 Office 365 群組執行一般管理工作。
ms.openlocfilehash: 94aa95de79099b45ea05533e7c22959b9bdf7669
ms.sourcegitcommit: 8027254ab4b9ed44a5b0c336f714049859f93f3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2019
ms.locfileid: "38030998"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="7d79e-103">使用 PowerShell 管理 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="7d79e-104">*上次更新 18 年 4 月，： 2018 2018年*</span><span class="sxs-lookup"><span data-stu-id="7d79e-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="7d79e-105">本文提供的 Microsoft PowerShell 中的群組執行的常見管理工作的步驟。</span><span class="sxs-lookup"><span data-stu-id="7d79e-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="7d79e-106">它也會列出群組的 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d79e-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="7d79e-107">管理 SharePoint 網站的相關資訊，請參閱[使用 PowerShell 管理 SharePoint Online 網站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。</span><span class="sxs-lookup"><span data-stu-id="7d79e-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="7d79e-108">連結至您的 Office 365 群組使用指導方針</span><span class="sxs-lookup"><span data-stu-id="7d79e-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="7d79e-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="7d79e-109"></span></span>

<span data-ttu-id="7d79e-110">當使用者[建立或編輯 Outlook 中的群組](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)，您可以顯示這些連結貴組織的使用指導方針。</span><span class="sxs-lookup"><span data-stu-id="7d79e-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="7d79e-111">例如，如果您需要特定首碼或尾碼新增至群組名稱。</span><span class="sxs-lookup"><span data-stu-id="7d79e-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="7d79e-112">使用 PowerShell 的 Azure Active Directory 使用者指向您的組織使用的指導方針 Office 365 群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-112">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="7d79e-113">取出[的群組設定 Azure Active Directory 指令程式](https://go.microsoft.com/fwlink/?LinkID=827484)，並遵循的步驟中**建立目錄層級的設定**，以定義的使用指導方針超連結。</span><span class="sxs-lookup"><span data-stu-id="7d79e-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="7d79e-114">一次您執行的 AAD 指令程式時，使用者將會看到連結您的指導方針當他們建立或編輯 Outlook 中的群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![建立新的群組與使用指引連結](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![按一下 [群組] 使用方針，若要查看您的組織 Office 365 群組指導方針](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="7d79e-117">允許使用者傳送為 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="7d79e-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="7d79e-118"></span></span>
  
<span data-ttu-id="7d79e-119">如果您想要啟用您的 Office 365 群組，以 「 傳送為 」，使用[Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)和[Get-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)指令程式來設定此。</span><span class="sxs-lookup"><span data-stu-id="7d79e-119">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="7d79e-120">一旦您啟用此設定時，Office 365 群組使用者可以使用 Outlook 網頁版傳送及回覆的電子郵件做為 Office 365 群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-120">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="7d79e-121">使用者可以移至群組時，建立新的電子郵件，以及 「 傳送為 」 欄位變更群組的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="7d79e-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="7d79e-122">（[您也可以此 Exchange 系統管理中心中](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)）。</span><span class="sxs-lookup"><span data-stu-id="7d79e-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="7d79e-123">使用下列指令碼，取代*\<GroupAlias\>* 與您想要更新，群組的別名和*\<UserAlias\>* 與您要授與使用權之使用者的別名。</span><span class="sxs-lookup"><span data-stu-id="7d79e-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions.</span></span> <span data-ttu-id="7d79e-124">若要執行此指令碼以[連線至 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="7d79e-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="7d79e-125">一旦執行 cmdlet 時，使用者可以移至 Outlook 或 outlook 網頁版傳送為] 群組中，將群組電子郵件地址新增至 [**從**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="7d79e-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="7d79e-126">在您的組織中建立 Office 群組的分類</span><span class="sxs-lookup"><span data-stu-id="7d79e-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="7d79e-127">您可以建立您組織中的使用者可以設定在建立 Office 365 群組時的分類。</span><span class="sxs-lookup"><span data-stu-id="7d79e-127">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="7d79e-128">例如，您可以允許使用者在他們所建立的群組設定"Standard"、"Secret"和"頂端 Secret"。</span><span class="sxs-lookup"><span data-stu-id="7d79e-128">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="7d79e-129">群組分類不能設定預設情況下，您需要建立為了讓您的使用者可將其設定。</span><span class="sxs-lookup"><span data-stu-id="7d79e-129">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="7d79e-130">使用 Azure Active Directory PowerShell 為您的使用者指向您的組織使用的指導方針 Office 365 群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-130">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="7d79e-131">取出[的群組設定 Azure Active Directory 指令程式](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)，並遵循的步驟中**建立目錄層級的設定**，以定義 Office 365 群組的分類。</span><span class="sxs-lookup"><span data-stu-id="7d79e-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="7d79e-132">若要建立關聯的描述您可以使用每一個分類設定此屬性*ClassificationDescriptions*來定義。</span><span class="sxs-lookup"><span data-stu-id="7d79e-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="7d79e-133">其中分類符合 ClassificationList 中的字串。</span><span class="sxs-lookup"><span data-stu-id="7d79e-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="7d79e-134">範例：</span><span class="sxs-lookup"><span data-stu-id="7d79e-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="7d79e-135">執行上述的 Azure Active Directory 指令程式，來設定您分類之後，請執行[Set-unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet，如果您想要設定特定群組的分類。</span><span class="sxs-lookup"><span data-stu-id="7d79e-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="7d79e-136">或建立新的群組與分類。</span><span class="sxs-lookup"><span data-stu-id="7d79e-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="7d79e-137">如需使用 Exchange Online PowerShell 的更多詳細資訊請參閱[Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)和[Exchange Online PowerShell 連線到](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="7d79e-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="7d79e-138">一旦啟用這些設定之後，群組擁有者可以從 Outlook 中，與 Web 上於 Outlook 中的下拉式功能表選擇分類，並將其儲存在 [**編輯**群組] 頁面。</span><span class="sxs-lookup"><span data-stu-id="7d79e-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![選擇 [Office 365 群組分類](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="7d79e-140">從 GAL 隱藏 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="7d79e-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7d79e-141"></span></span>

<span data-ttu-id="7d79e-142">您可以指定 Office 365 群組是否會出現在全域通訊清單 (GAL) 和其他組織中的清單。</span><span class="sxs-lookup"><span data-stu-id="7d79e-142">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="7d79e-143">例如，如果您有法務部門群組，您不想要顯示在 [位址] 清單中，您可以停止該群組出現在 GAL 中。</span><span class="sxs-lookup"><span data-stu-id="7d79e-143">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="7d79e-144">執行 Set-Unified 群組指令程式從隱藏群組就像這樣的通訊清單：</span><span class="sxs-lookup"><span data-stu-id="7d79e-144">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="7d79e-145">只允許內部的使用者傳送郵件給 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="7d79e-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7d79e-146"></span></span>

<span data-ttu-id="7d79e-147">如果您不想從其他組織使用者傳送電子郵件給 Office 365 群組，您可以變更該群組的設定。</span><span class="sxs-lookup"><span data-stu-id="7d79e-147">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="7d79e-148">它會允許僅內部使用者傳送電子郵件給您的群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-148">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="7d79e-149">如果外部使用者嘗試將郵件傳送給該群組，他們會被拒絕。</span><span class="sxs-lookup"><span data-stu-id="7d79e-149">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="7d79e-150">執行 Set-unifiedgroup cmdlet，以更新此設定，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="7d79e-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="7d79e-151">將郵件提示新增至 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="7d79e-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7d79e-152"></span></span>

<span data-ttu-id="7d79e-153">每當寄件者嘗試傳送電子郵件給 Office 365 群組時，「 郵件提示 」 可顯示給他們。</span><span class="sxs-lookup"><span data-stu-id="7d79e-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="7d79e-154">執行 Set-Unified 群組指令程式將 「 郵件提示 」 新增至群組：</span><span class="sxs-lookup"><span data-stu-id="7d79e-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="7d79e-155">郵件提示、 以及您也可以設定 MailTipTranslations，指定其他語言的郵件提示。</span><span class="sxs-lookup"><span data-stu-id="7d79e-155">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="7d79e-156">假設您想要有西班牙文翻譯，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7d79e-156">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="7d79e-157">變更 Office 365 群組的顯示名稱</span><span class="sxs-lookup"><span data-stu-id="7d79e-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="7d79e-158">顯示名稱指定 Office 365 群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d79e-158">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="7d79e-159">您可以看到此名稱在您的 exchange 系統管理中心或 Office 365 系統管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="7d79e-159">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="7d79e-160">您可以編輯群組的顯示名稱，或指派給現有的 Office 365 群組的顯示名稱，藉由執行 Set-unifiedgroup 命令：</span><span class="sxs-lookup"><span data-stu-id="7d79e-160">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="7d79e-161">適用於 Outlook 的 Office 365 群組的預設設定變更為公用或私人</span><span class="sxs-lookup"><span data-stu-id="7d79e-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="7d79e-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7d79e-162"></span></span>

<span data-ttu-id="7d79e-163">Office 365 群組在 Outlook 中的預設會建立為私人。</span><span class="sxs-lookup"><span data-stu-id="7d79e-163">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="7d79e-164">如果您的組織想要建立為公開預設 （或回到私人），請使用此 PowerShell 指令程式語法的 Office 365 群組：</span><span class="sxs-lookup"><span data-stu-id="7d79e-164">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="7d79e-165">若要設定為 [私人：</span><span class="sxs-lookup"><span data-stu-id="7d79e-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="7d79e-166">若要確認設定：</span><span class="sxs-lookup"><span data-stu-id="7d79e-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="7d79e-167">若要深入了解，請參閱[Set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)和[Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)。</span><span class="sxs-lookup"><span data-stu-id="7d79e-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="7d79e-168">Office 365 群組 cmdlet</span><span class="sxs-lookup"><span data-stu-id="7d79e-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="7d79e-169">下列指令程式可以搭配 Office 365 群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="7d79e-170">**Cmdlet 名稱**</span><span class="sxs-lookup"><span data-stu-id="7d79e-170">**Cmdlet name**</span></span>|<span data-ttu-id="7d79e-171">**描述**</span><span class="sxs-lookup"><span data-stu-id="7d79e-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="7d79e-172">取得 UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="7d79e-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="7d79e-173">使用此指令程式，以查看現有的 Office 365 群組，並檢視群組物件的屬性</span><span class="sxs-lookup"><span data-stu-id="7d79e-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="7d79e-174">Set-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="7d79e-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="7d79e-175">更新特定的 Office 365 群組的屬性</span><span class="sxs-lookup"><span data-stu-id="7d79e-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7d79e-176">新 UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="7d79e-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="7d79e-177">建立新的 Office 365 群組。</span><span class="sxs-lookup"><span data-stu-id="7d79e-177">Create a new Office 365 group.</span></span> <span data-ttu-id="7d79e-178">此 cmdlet 會提供一組最少的參數，設定擴充屬性的值，請使用在建立新的群組之後的 Set-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="7d79e-178">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="7d79e-179">Remove-unifiedgroup</span><span class="sxs-lookup"><span data-stu-id="7d79e-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="7d79e-180">刪除現有的 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7d79e-181">取得 UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="7d79e-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="7d79e-182">擷取 Office 365 群組的成員資格與擁有者的資訊</span><span class="sxs-lookup"><span data-stu-id="7d79e-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7d79e-183">新增 UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="7d79e-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="7d79e-184">新增數百或數千個使用者或新的擁有者，與現有的 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7d79e-185">移除 UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="7d79e-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="7d79e-186">移除現有的 Office 365 群組的擁有者與成員</span><span class="sxs-lookup"><span data-stu-id="7d79e-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7d79e-187">取得 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="7d79e-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="7d79e-188">用來檢視與帳戶相關聯之使用者相片相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="7d79e-188">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="7d79e-189">使用者相片會儲存在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="7d79e-189">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="7d79e-190">設定 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="7d79e-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="7d79e-191">用來將使用者相片關聯的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7d79e-191">Used to associate a user photo with an account.</span></span> <span data-ttu-id="7d79e-192">使用者相片會儲存在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="7d79e-192">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="7d79e-193">移除 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="7d79e-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="7d79e-194">移除 Office 365 群組的相片</span><span class="sxs-lookup"><span data-stu-id="7d79e-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="7d79e-195">相關主題</span><span class="sxs-lookup"><span data-stu-id="7d79e-195">Related topics</span></span>

[<span data-ttu-id="7d79e-196">通訊群組清單升級至 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="7d79e-197">管理誰能建立 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="7d79e-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="7d79e-198">管理 Office 365 群組的來賓存取權</span><span class="sxs-lookup"><span data-stu-id="7d79e-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="7d79e-199">若要在動態變更靜態的群組成員資格</span><span class="sxs-lookup"><span data-stu-id="7d79e-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
