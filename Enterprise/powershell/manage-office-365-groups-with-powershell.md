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
description: 了解如何在 Microsoft PowerShell 中的 Office 365 群組執行一般管理工作。
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491748"
---
# <a name="manage-office-365-groups-with-powershell"></a>使用 PowerShell 管理 Office 365 群組

 *上次更新 18 年 4 月，： 2018 2018年* 
  
本文提供的 Microsoft PowerShell 中的群組執行的常見管理工作的步驟。 它也會列出群組的 PowerShell cmdlet。 管理 SharePoint 網站的相關資訊，請參閱[使用 PowerShell 管理 SharePoint Online 網站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>連結至您的 Office 365 群組使用指導方針
<a name="BK_LinkToGuideLines"> </a>

當使用者[建立或編輯 Outlook 中的群組](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)，您可以顯示這些連結貴組織的使用指導方針。 例如，如果您需要特定首碼或尾碼新增至群組名稱。
  
使用 PowerShell 的 Azure Active Directory 使用者指向您的組織使用的指導方針 Office 365 群組。 取出[的群組設定 Azure Active Directory 指令程式](https://go.microsoft.com/fwlink/?LinkID=827484)，並遵循的步驟中**建立目錄層級的設定**，以定義的使用指導方針超連結。 一次您執行的 AAD 指令程式時，使用者將會看到連結您的指導方針當他們建立或編輯 Outlook 中的群組。 
  
![建立新的群組與使用指引連結](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![按一下 [群組] 使用方針，若要查看您的組織 Office 365 群組指導方針](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>允許使用者傳送為 Office 365 群組
<a name="BK_LinkToGuideLines"> </a>
  
如果您想要啟用您的 Office 365 群組，以 「 傳送為 」，使用[Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)和[Get-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)指令程式來設定此。 一旦您啟用此設定時，Office 365 群組使用者可以使用 Outlook 網頁版傳送及回覆的電子郵件做為 Office 365 群組。 使用者可以移至群組時，建立新的電子郵件，以及 「 傳送為 」 欄位變更群組的電子郵件地址。 

（[您也可以此 Exchange 系統管理中心中](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)）。
  
使用下列指令碼，取代*\<GroupAlias\>* 與您想要更新，群組的別名和*\<UserAlias\>* 與您要授與使用權之使用者的別名。 若要執行此指令碼以[連線至 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

一旦執行 cmdlet 時，使用者可以移至 Outlook 或 outlook 網頁版傳送為] 群組中，將群組電子郵件地址新增至 [**從**] 欄位。 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>在您的組織中建立 Office 群組的分類

您可以建立您組織中的使用者可以設定在建立 Office 365 群組時的分類。 例如，您可以允許使用者在他們所建立的群組設定"Standard"、"Secret"和"頂端 Secret"。 群組分類不能設定預設情況下，您需要建立為了讓您的使用者可將其設定。 使用 Azure Active Directory PowerShell 為您的使用者指向您的組織使用的指導方針 Office 365 群組。
  
取出[的群組設定 Azure Active Directory 指令程式](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)，並遵循的步驟中**建立目錄層級的設定**，以定義 Office 365 群組的分類。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

若要建立關聯的描述您可以使用每一個分類設定此屬性*ClassificationDescriptions*來定義。
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

其中分類符合 ClassificationList 中的字串。

範例：
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

執行上述的 Azure Active Directory 指令程式，來設定您分類之後，請執行[Set-unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet，如果您想要設定特定群組的分類。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

或建立新的群組與分類。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

如需使用 Exchange Online PowerShell 的更多詳細資訊請參閱[Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)和[Exchange Online PowerShell 連線到](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。 
  
一旦啟用這些設定之後，群組擁有者可以從 Outlook 中，與 Web 上於 Outlook 中的下拉式功能表選擇分類，並將其儲存在 [**編輯**群組] 頁面。 
  
![選擇 [Office 365 群組分類](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>從 GAL 隱藏 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

您可以指定 Office 365 群組是否會出現在全域通訊清單 (GAL) 和其他組織中的清單。 例如，如果您有法務部門群組，您不想要顯示在 [位址] 清單中，您可以停止該群組出現在 GAL 中。 執行 Set-Unified 群組指令程式從隱藏群組就像這樣的通訊清單：
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>只允許內部的使用者傳送郵件給 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

如果您不想從其他組織使用者傳送電子郵件給 Office 365 群組，您可以變更該群組的設定。 它會允許僅內部使用者傳送電子郵件給您的群組。 如果外部使用者嘗試將郵件傳送給該群組，他們會被拒絕。
  
執行 Set-unifiedgroup cmdlet，以更新此設定，就像這樣：

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>將郵件提示新增至 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

每當寄件者嘗試傳送電子郵件給 Office 365 群組時，「 郵件提示 」 可顯示給他們。
  
執行 Set-Unified 群組指令程式將 「 郵件提示 」 新增至群組：

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

郵件提示、 以及您也可以設定 MailTipTranslations，指定其他語言的郵件提示。 假設您想要有西班牙文翻譯，然後執行下列命令：
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>變更 Office 365 群組的顯示名稱

顯示名稱指定 Office 365 群組的名稱。 您可以看到此名稱在您的 exchange 系統管理中心或 Office 365 系統管理入口網站。 您可以編輯群組的顯示名稱，或指派給現有的 Office 365 群組的顯示名稱，藉由執行 Set-unifiedgroup 命令：

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>適用於 Outlook 的 Office 365 群組的預設設定變更為公用或私人
<a name="BKMK_CreateClassification"> </a>

Office 365 群組在 Outlook 中的預設會建立為私人。 如果您的組織想要建立為公開預設 （或回到私人），請使用此 PowerShell 指令程式語法的 Office 365 群組：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
若要設定為 [私人：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
若要確認設定： 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
若要深入了解，請參閱[Set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)和[Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 群組 cmdlet

下列指令程式可以搭配 Office 365 群組。
  
|**Cmdlet 名稱**|**描述**|
|:-----|:-----|
|[取得 UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |使用此指令程式，以查看現有的 Office 365 群組，並檢視群組物件的屬性  <br/> |
|[Set-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |更新特定的 Office 365 群組的屬性  <br/> |
|[新 UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |建立新的 Office 365 群組。 此 cmdlet 會提供一組最少的參數，設定擴充屬性的值，請使用在建立新的群組之後的 Set-unifiedgroup  <br/> |
|[Remove-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |刪除現有的 Office 365 群組  <br/> |
|[取得 UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |擷取 Office 365 群組的成員資格與擁有者的資訊  <br/> |
|[新增 UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |新增數百或數千個使用者或新的擁有者，與現有的 Office 365 群組  <br/> |
|[移除 UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |移除現有的 Office 365 群組的擁有者與成員  <br/> |
|[取得 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |用來檢視與帳戶相關聯之使用者相片相關的資訊。 使用者相片會儲存在 Active Directory  <br/> |
|[設定 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |用來將使用者相片關聯的帳戶。 使用者相片會儲存在 Active Directory  <br/> |
|[移除 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |移除 Office 365 群組的相片  <br/> |

## <a name="related-topics"></a>相關主題

[通訊群組清單升級至 Office 365 群組](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[管理誰能建立 Office 365 群組](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[管理 Office 365 群組的來賓存取權](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[若要在動態變更靜態的群組成員資格](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
