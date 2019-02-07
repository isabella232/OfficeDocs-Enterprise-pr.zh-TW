---
title: 使用 PowerShell 管理 Office 365 群組
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
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
description: 了解如何執行一般管理工作的 Microsoft PowerShell 中的 Office 365 群組。
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760055"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="cbf65-103">使用 PowerShell 管理 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="cbf65-104">*上次更新 18 年 4 月、 2018*</span><span class="sxs-lookup"><span data-stu-id="cbf65-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="cbf65-p101">本文提供的群組中使用 Microsoft PowerShell 執行一般管理工作的步驟。它也會列出之群組的 PowerShell cmdlet。管理 SharePoint 網站的相關資訊，請參閱[使用 PowerShell 管理 SharePoint Online 網站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="cbf65-108">連結至 Office 365 群組使用方式指導方針</span><span class="sxs-lookup"><span data-stu-id="cbf65-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="cbf65-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="cbf65-109"></span></span>

<span data-ttu-id="cbf65-p102">當使用者[建立或編輯在 Outlook 中的群組](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)，即可顯示他們您的組織使用指南的連結。例如，如果您需要特定首碼或尾碼新增至群組名稱。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="cbf65-p103">使用 Azure Active Directory PowerShell 使用者指向 Office 365 群組您的組織使用指南。請參閱[設定群組的 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484)並遵循定義使用方式的指導方針超連結**目錄層級建立設定**] 中的步驟。一次您執行 AAD 指令程式，使用者將會看到連結至您的指導方針當使用者建立或編輯在 Outlook 中的群組。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![與使用指引連結建立新的群組](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![按一下 [查看您的組織 Office 365 群組準則的群組使用方式指導方針](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="cbf65-117">允許使用者傳送為 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="cbf65-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="cbf65-118"></span></span>
  
<span data-ttu-id="cbf65-p104">如果您想要讓您的 Office 365 群組至 「 傳送為 」、 使用[Add Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)和[取得 Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)指令程式進行此設定。一旦您啟用此設定時，Office 365 群組使用者可以使用 Outlook 或 Outlook web 上的傳送及回覆的電子郵件做為 Office 365 的群組。使用者可以移到群組中，建立新的電子郵件，以及 「 傳送為 」 欄位變更群組的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="cbf65-122">（[您也可以進行這在 Exchange 系統管理中心中](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)）。</span><span class="sxs-lookup"><span data-stu-id="cbf65-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="cbf65-p105">使用下列指令碼，並取代*\<GroupAlias\>* 別名為您想要更新的群組和*\<UserAlias\>* 與您要授與使用權之使用者的別名。若要執行此指令碼[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="cbf65-125">一旦執行此指令程式時，使用者可以移至 Outlook 或 Outlook web 上的為群組傳送群組電子郵件地址加入至 [**從**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="cbf65-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="cbf65-126">在組織中建立之 Office 群組分類</span><span class="sxs-lookup"><span data-stu-id="cbf65-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="cbf65-p106">您可以建立您的組織中的使用者可以設定當他們所建立的 Office 365 群組的分類。例如，您可以讓使用者在他們所建立的群組設定"Standard"、"Secret"及"頂端密碼 」。預設不設群組分類和您需要建立設定該使用者的順序。使用 Azure Active Directory PowerShell 使用者指向 Office 365 群組您的組織使用指南。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="cbf65-131">取出[的設定群組的 Azure Active Directory cmdlet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)並遵循**Create 層級的設定目錄**來定義的分類為 Office 365 群組中的步驟。</span><span class="sxs-lookup"><span data-stu-id="cbf65-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="cbf65-132">若要建立關聯的描述您可以使用每個分類設定此屬性*ClassificationDescriptions*定義。</span><span class="sxs-lookup"><span data-stu-id="cbf65-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="cbf65-133">如果有分類符合 ClassificationList 中的字串。</span><span class="sxs-lookup"><span data-stu-id="cbf65-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="cbf65-134">範例：</span><span class="sxs-lookup"><span data-stu-id="cbf65-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="cbf65-135">執行上述的 Azure Active Directory 指令程式來設定您的分類之後，執行[組 UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet，如果您想要設定一組特定的分類。</span><span class="sxs-lookup"><span data-stu-id="cbf65-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="cbf65-136">或分類建立新的群組。</span><span class="sxs-lookup"><span data-stu-id="cbf65-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="cbf65-137">如需詳細資訊上使用 Exchange Online PowerShell 查看[使用 PowerShell 與 Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)和[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="cbf65-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="cbf65-138">一旦啟用這些設定之後，群組擁有者可以從下拉式清單中的網頁和 Outlook 中，在 Outlook 中的功能表中選擇分類並將其儲存在 [**編輯**群組] 頁面。</span><span class="sxs-lookup"><span data-stu-id="cbf65-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![選擇 Office 365 群組分類](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="cbf65-140">隱藏 GAL 中的 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="cbf65-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cbf65-141"></span></span>

<span data-ttu-id="cbf65-p107">您可以指定 Office 365 群組是否會出現在全域通訊清單 (GAL) 和其他組織中的清單。例如，如果您不想要在 [位址] 清單中顯示法務部門群組，您可以停止 GAL 中顯示該群組。執行 Set-Unified 群組指令程式來隱藏像這樣的通訊清單的群組：</span><span class="sxs-lookup"><span data-stu-id="cbf65-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="cbf65-145">只允許內部使用者傳送訊息到 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="cbf65-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cbf65-146"></span></span>

<span data-ttu-id="cbf65-p108">如果您不想從另一個組織至 Office 365 群組傳送電子郵件的使用者，您可以變更該群組的設定。它會允許僅限內部使用者將電子郵件傳送給您群組。如果外部的使用者嘗試將郵件傳送給該群組會被拒絕。</span><span class="sxs-lookup"><span data-stu-id="cbf65-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="cbf65-150">執行設定 UnifiedGroup 指令程式來更新此設定，如下：</span><span class="sxs-lookup"><span data-stu-id="cbf65-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="cbf65-151">將寄件提醒新增至 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="cbf65-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cbf65-152"></span></span>

<span data-ttu-id="cbf65-153">每當寄件者會嘗試將電子郵件傳送至 Office 365 群組，其會顯示郵件提示。</span><span class="sxs-lookup"><span data-stu-id="cbf65-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="cbf65-154">執行 Set-Unified 群組指令程式新增至群組的郵件提示：</span><span class="sxs-lookup"><span data-stu-id="cbf65-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="cbf65-p109">郵件提示，以及您也可以設定 MailTipTranslations、 指定其他語言的郵件提示。假設您想要出現西班牙文翻譯，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="cbf65-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="cbf65-157">變更 Office 365 群組的顯示名稱</span><span class="sxs-lookup"><span data-stu-id="cbf65-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="cbf65-p110">顯示名稱指定 Office 365 群組的名稱。您可以看到此名稱在 exchange 系統管理中心或 Office 365 系統管理入口網站。您可以編輯群組的顯示名稱或執行組 UnifiedGroup 命令，將顯示名稱指派給現有的 Office 365 群組：</span><span class="sxs-lookup"><span data-stu-id="cbf65-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="cbf65-161">變更 outlook 的 Office 365 群組的預設設定為公用或私人</span><span class="sxs-lookup"><span data-stu-id="cbf65-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="cbf65-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="cbf65-162"></span></span>

<span data-ttu-id="cbf65-p111">Office 365 在 Outlook 中建立群組私人為預設值。如果您的組織想 Office 365 群組建立為公用預設 （或回到私人），請使用下列 PowerShell cmdlet 的語法：</span><span class="sxs-lookup"><span data-stu-id="cbf65-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="cbf65-165">若要設定為私人：</span><span class="sxs-lookup"><span data-stu-id="cbf65-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="cbf65-166">若要確認設定：</span><span class="sxs-lookup"><span data-stu-id="cbf65-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="cbf65-167">若要深入了解，請參閱[Set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)和[Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)。</span><span class="sxs-lookup"><span data-stu-id="cbf65-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="cbf65-168">Office 365 群組指令程式</span><span class="sxs-lookup"><span data-stu-id="cbf65-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="cbf65-169">以下 cmdlet 可搭配 Office 365 群組。</span><span class="sxs-lookup"><span data-stu-id="cbf65-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="cbf65-170">**Cmdlet 名稱**</span><span class="sxs-lookup"><span data-stu-id="cbf65-170">**Cmdlet name**</span></span>|<span data-ttu-id="cbf65-171">**描述**</span><span class="sxs-lookup"><span data-stu-id="cbf65-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="cbf65-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cbf65-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="cbf65-173">使用此指令程式來查詢現有的 Office 365 群組，並檢視 group 物件的屬性</span><span class="sxs-lookup"><span data-stu-id="cbf65-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="cbf65-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cbf65-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="cbf65-175">更新特定的 Office 365 群組的屬性</span><span class="sxs-lookup"><span data-stu-id="cbf65-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cbf65-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cbf65-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="cbf65-p112">建立新的 Office 365 群組。此指令程式提供一組最少的參數，可設定已擴充屬性的值會使用組 UnifiedGroup 建立新的群組之後</span><span class="sxs-lookup"><span data-stu-id="cbf65-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="cbf65-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="cbf65-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="cbf65-180">刪除現有的 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cbf65-181">取得 UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="cbf65-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="cbf65-182">擷取 Office 365 群組的成員資格與擁有者的資訊</span><span class="sxs-lookup"><span data-stu-id="cbf65-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cbf65-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="cbf65-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="cbf65-184">新增數百或數千個使用者或新的擁有人、 以現有的 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="cbf65-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cbf65-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="cbf65-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="cbf65-186">移除現有的 Office 365 群組的擁有者和成員</span><span class="sxs-lookup"><span data-stu-id="cbf65-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="cbf65-187">取得 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="cbf65-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="cbf65-p113">用來檢視與帳戶相關聯之使用者相片相關的資訊。使用者相片儲存在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="cbf65-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="cbf65-190">設定 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="cbf65-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="cbf65-p114">用來將使用者相片關聯的帳戶。使用者相片儲存在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="cbf65-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="cbf65-193">移除 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="cbf65-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="cbf65-194">移除 Office 365 群組的相片</span><span class="sxs-lookup"><span data-stu-id="cbf65-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="cbf65-195">相關主題</span><span class="sxs-lookup"><span data-stu-id="cbf65-195">Related topics</span></span>

[<span data-ttu-id="cbf65-196">Office 365 群組升級的通訊群組清單</span><span class="sxs-lookup"><span data-stu-id="cbf65-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="cbf65-197">管理能建立 Office 365 群組的使用者</span><span class="sxs-lookup"><span data-stu-id="cbf65-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="cbf65-198">管理 Office 365 群組的來賓存取權</span><span class="sxs-lookup"><span data-stu-id="cbf65-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="cbf65-199">若要在動態變更靜態群組成員資格</span><span class="sxs-lookup"><span data-stu-id="cbf65-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
