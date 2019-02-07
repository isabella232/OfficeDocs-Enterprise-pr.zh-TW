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
# <a name="manage-office-365-groups-with-powershell"></a>使用 PowerShell 管理 Office 365 群組

 *上次更新 18 年 4 月、 2018* 
  
本文提供的群組中使用 Microsoft PowerShell 執行一般管理工作的步驟。它也會列出之群組的 PowerShell cmdlet。管理 SharePoint 網站的相關資訊，請參閱[使用 PowerShell 管理 SharePoint Online 網站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>連結至 Office 365 群組使用方式指導方針
<a name="BK_LinkToGuideLines"> </a>

當使用者[建立或編輯在 Outlook 中的群組](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)，即可顯示他們您的組織使用指南的連結。例如，如果您需要特定首碼或尾碼新增至群組名稱。
  
使用 Azure Active Directory PowerShell 使用者指向 Office 365 群組您的組織使用指南。請參閱[設定群組的 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484)並遵循定義使用方式的指導方針超連結**目錄層級建立設定**] 中的步驟。一次您執行 AAD 指令程式，使用者將會看到連結至您的指導方針當使用者建立或編輯在 Outlook 中的群組。 
  
![與使用指引連結建立新的群組](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![按一下 [查看您的組織 Office 365 群組準則的群組使用方式指導方針](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>允許使用者傳送為 Office 365 群組
<a name="BK_LinkToGuideLines"> </a>
  
如果您想要讓您的 Office 365 群組至 「 傳送為 」、 使用[Add Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)和[取得 Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)指令程式進行此設定。一旦您啟用此設定時，Office 365 群組使用者可以使用 Outlook 或 Outlook web 上的傳送及回覆的電子郵件做為 Office 365 的群組。使用者可以移到群組中，建立新的電子郵件，以及 「 傳送為 」 欄位變更群組的電子郵件地址。 

（[您也可以進行這在 Exchange 系統管理中心中](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)）。
  
使用下列指令碼，並取代*\<GroupAlias\>* 別名為您想要更新的群組和*\<UserAlias\>* 與您要授與使用權之使用者的別名。若要執行此指令碼[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

一旦執行此指令程式時，使用者可以移至 Outlook 或 Outlook web 上的為群組傳送群組電子郵件地址加入至 [**從**] 欄位。 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>在組織中建立之 Office 群組分類

您可以建立您的組織中的使用者可以設定當他們所建立的 Office 365 群組的分類。例如，您可以讓使用者在他們所建立的群組設定"Standard"、"Secret"及"頂端密碼 」。預設不設群組分類和您需要建立設定該使用者的順序。使用 Azure Active Directory PowerShell 使用者指向 Office 365 群組您的組織使用指南。
  
取出[的設定群組的 Azure Active Directory cmdlet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)並遵循**Create 層級的設定目錄**來定義的分類為 Office 365 群組中的步驟。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

若要建立關聯的描述您可以使用每個分類設定此屬性*ClassificationDescriptions*定義。
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

如果有分類符合 ClassificationList 中的字串。

範例：
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

執行上述的 Azure Active Directory 指令程式來設定您的分類之後，執行[組 UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet，如果您想要設定一組特定的分類。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

或分類建立新的群組。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

如需詳細資訊上使用 Exchange Online PowerShell 查看[使用 PowerShell 與 Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)和[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。 
  
一旦啟用這些設定之後，群組擁有者可以從下拉式清單中的網頁和 Outlook 中，在 Outlook 中的功能表中選擇分類並將其儲存在 [**編輯**群組] 頁面。 
  
![選擇 Office 365 群組分類](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>隱藏 GAL 中的 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

您可以指定 Office 365 群組是否會出現在全域通訊清單 (GAL) 和其他組織中的清單。例如，如果您不想要在 [位址] 清單中顯示法務部門群組，您可以停止 GAL 中顯示該群組。執行 Set-Unified 群組指令程式來隱藏像這樣的通訊清單的群組：
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>只允許內部使用者傳送訊息到 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

如果您不想從另一個組織至 Office 365 群組傳送電子郵件的使用者，您可以變更該群組的設定。它會允許僅限內部使用者將電子郵件傳送給您群組。如果外部的使用者嘗試將郵件傳送給該群組會被拒絕。
  
執行設定 UnifiedGroup 指令程式來更新此設定，如下：

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>將寄件提醒新增至 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

每當寄件者會嘗試將電子郵件傳送至 Office 365 群組，其會顯示郵件提示。
  
執行 Set-Unified 群組指令程式新增至群組的郵件提示：

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

郵件提示，以及您也可以設定 MailTipTranslations、 指定其他語言的郵件提示。假設您想要出現西班牙文翻譯，請執行下列命令：
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>變更 Office 365 群組的顯示名稱

顯示名稱指定 Office 365 群組的名稱。您可以看到此名稱在 exchange 系統管理中心或 Office 365 系統管理入口網站。您可以編輯群組的顯示名稱或執行組 UnifiedGroup 命令，將顯示名稱指派給現有的 Office 365 群組：

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>變更 outlook 的 Office 365 群組的預設設定為公用或私人
<a name="BKMK_CreateClassification"> </a>

Office 365 在 Outlook 中建立群組私人為預設值。如果您的組織想 Office 365 群組建立為公用預設 （或回到私人），請使用下列 PowerShell cmdlet 的語法：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
若要設定為私人：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
若要確認設定： 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
若要深入了解，請參閱[Set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)和[Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 群組指令程式

以下 cmdlet 可搭配 Office 365 群組。
  
|**Cmdlet 名稱**|**描述**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |使用此指令程式來查詢現有的 Office 365 群組，並檢視 group 物件的屬性  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |更新特定的 Office 365 群組的屬性  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |建立新的 Office 365 群組。此指令程式提供一組最少的參數，可設定已擴充屬性的值會使用組 UnifiedGroup 建立新的群組之後  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |刪除現有的 Office 365 群組  <br/> |
|[取得 UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |擷取 Office 365 群組的成員資格與擁有者的資訊  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |新增數百或數千個使用者或新的擁有人、 以現有的 Office 365 群組  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |移除現有的 Office 365 群組的擁有者和成員  <br/> |
|[取得 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |用來檢視與帳戶相關聯之使用者相片相關的資訊。使用者相片儲存在 Active Directory  <br/> |
|[設定 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |用來將使用者相片關聯的帳戶。使用者相片儲存在 Active Directory  <br/> |
|[移除 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |移除 Office 365 群組的相片  <br/> |

## <a name="related-topics"></a>相關主題

[Office 365 群組升級的通訊群組清單](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[管理能建立 Office 365 群組的使用者](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[管理 Office 365 群組的來賓存取權](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[若要在動態變更靜態群組成員資格](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
