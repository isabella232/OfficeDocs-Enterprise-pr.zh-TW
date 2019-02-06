---
title: 使用 PowerShell 管理 Office 365 群組
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 上次更新 18 年 4 月、 2018
ms.openlocfilehash: 518f845099a72d9addac13388d1b281ca63ee408
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741216"
---
# <a name="manage-office-365-groups-with-powershell"></a>使用 PowerShell 管理 Office 365 群組

 *上次更新 18 年 4 月、 2018* 
  
本文提供的群組中使用 Microsoft PowerShell 執行一般管理工作的步驟。它也會列出之群組的 PowerShell cmdlet。管理 SharePoint 網站的相關資訊，請參閱[管理小組網站及使用 PowerShell 通訊網站](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87)。
  
## <a name="common-tasks-for-managing-office-365-groups"></a>管理 Office 365 群組的一般工作

- [在 Outlook 中將通訊群組清單升級至 Office 365 群組](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [管理能建立 Office 365 群組的使用者](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [管理 Office 365 群組的來賓存取權](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [以動態方式在 Azure Active Directory 中管理群組](https://go.microsoft.com/fwlink/?linkid=847632)
    
- 將數百或數千個使用者新增至 Office 365 群組、 使用[Add UnifiedGroupLinks 指令程式](https://go.microsoft.com/fwlink/p/?LinkId=616191)。
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>連結至 Office 365 群組使用方式指導方針
<a name="BK_LinkToGuideLines"> </a>

當使用者[建立 Outlook 的群組](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102)，即可顯示他們您的組織使用指南的連結。例如，如果您需要特定首碼或尾碼新增至群組名稱。
  
使用 Azure Active Directory PowerShell 使用者指向 Office 365 群組您的組織使用指南。請參閱[設定群組的 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484)並遵循定義使用方式的指導方針超連結**目錄層級建立設定**] 中的步驟。一次您執行 AAD 指令程式，使用者將會看到連結至您的指導方針當使用者建立或編輯在 Outlook 中的群組。 
  
![與使用指引連結建立新的群組](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![按一下 [查看您的組織 Office 365 群組準則的群組使用方式指導方針](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>允許使用者傳送為 Office 365 群組
<a name="BK_LinkToGuideLines"> </a>

您也可以達成此目的在 Exchange 系統管理中心。請參閱[允許以下列傳送或傳送代表群組的成員](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590)。
  
如果您想要讓您的 Office 365 群組至 「 傳送為 」、 使用[Add Add-recipientpermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)和[取得 Add-recipientpermission](https://go.microsoft.com/fwlink/p/?LinkId=733239)指令程式進行此設定。一旦您啟用此設定時，Office 365 群組使用者可以使用 Outlook 或 Outlook web 上的傳送及回覆的電子郵件做為 Office 365 的群組。使用者可以移到群組中，建立新的電子郵件，以及 「 傳送為 」 欄位變更群組的電子郵件地址。 
  
> [!NOTE]
> 您需要當您在撰寫使郵件傳送至群組，並將顯示群組交談中的 「 傳送為 」 電子郵件將群組電子郵件地址加入到 [**副本**] 欄位。 
  
在此階段中，若要更新之信箱原則的唯一方式是透過[PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)。
  
- 使用此命令可設定群組的別名。
    
  ```
  $groupAlias = "TestSendAs"
  ```

- 使用此命令可設定使用者別名。
    
  ```
  $userAlias = "User"
  ```

- 使用此命令將 groupalias 傳遞給 Get-recipient 指令程式來取得收件者的詳細資訊。
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- 然後 （群組名稱） 的目標收件者名稱必須傳遞給 Add Add-recipientpermission 指令程式。其 sendas 權限會授與 useralias 會指派給-者參數。
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- 一旦執行此指令程式時，使用者可以移至 Outlook 或 Outlook web 上的為群組傳送群組電子郵件地址加入至 [**從**] 欄位。 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>在組織中建立之 Office 群組分類
<a name="BKMK_CreateClassification"> </a>

您可以建立您的組織中的使用者可以設定當他們所建立的 Office 365 群組的分類。例如，您可以讓使用者在他們所建立的群組設定"Standard"、"Secret"及"頂端密碼 」。預設不設群組分類和您需要建立設定該使用者的順序。使用 Azure Active Directory PowerShell 使用者指向 Office 365 群組您的組織使用指南。
  
取出[的設定群組的 Azure Active Directory cmdlet](https://go.microsoft.com/fwlink/?LinkID=827484)並遵循**Create 層級的設定目錄**來定義的分類為 Office 365 群組中的步驟。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

若要建立關聯的描述您可以使用每個分類設定此屬性*ClassificationDescriptions*定義。 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

例如：
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

執行上述的 Azure Active Directory 指令程式來設定您的分類之後，執行[組 UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet，如果您想要設定一組特定的分類。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

或分類建立新的群組。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

如需詳細資訊上使用 Exchange Online PowerShell 查看[使用 PowerShell 與 Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831)和[Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) 。 
  
一旦啟用這些設定之後，群組擁有者可以從下拉式清單中的網頁和 Outlook 中，在 Outlook 中的功能表中選擇分類並將其儲存在 [**編輯**群組] 頁面。 
  
![選擇 Office 365 群組分類](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>隱藏 GAL 中的 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

您可以指定 Office 365 群組是否會出現在全域通訊清單 (GAL) 和其他組織中的清單。例如，如果您不想要在 [位址] 清單中顯示法務部門群組，您可以停止 GAL 中顯示該群組。執行 Set-Unified 群組指令程式，以隱藏像這樣的通訊清單的群組：
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>只允許內部使用者傳送訊息到 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

如果您不想從另一個組織至 Office 365 群組傳送電子郵件的使用者，您可以變更該群組的設定。它會允許僅限內部使用者將電子郵件傳送給您群組。如果外部的使用者嘗試將郵件傳送給該群組會被拒絕。
  
執行設定 UnifiedGroup 指令程式，來更新此設定，如下：
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>將寄件提醒新增至 Office 365 群組
<a name="BKMK_CreateClassification"> </a>

每當寄件者會嘗試將電子郵件傳送至 Office 365 群組、 郵件提示可以顯示給他。
  
執行 Set-Unified 群組指令程式，以新增至群組的郵件提示：
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

郵件提示，以及您也可以設定 MailTipTranslations，這會指定要從其他語言的郵件提示。假設您想要出現西班牙文翻譯，請執行下列命令：
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>變更 Office 365 群組的顯示名稱
<a name="BKMK_CreateClassification"> </a>

顯示名稱指定 Office 365 群組的名稱。您可以在 exchange 系統管理中心或 o365 系統入口網站中看到此名稱。您可以編輯群組的顯示名稱或執行組 UnifiedGroup 命令，將顯示名稱指派給現有 Office 365 群組：
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>管理 Office 365 群組中的使用者相片
<a name="BKMK_CreateClassification"> </a>

| |
|**Cmdlet 名稱**|**描述**|
|:-----|:-----|
|[取得 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |用來檢視與帳戶相關聯之使用者相片相關的資訊。使用者相片儲存在 Active Directory  <br/> |
|[設定 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |用來將使用者相片關聯的帳戶。使用者相片儲存在 Active Directory  <br/> |
|[移除 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |移除 Office 365 群組的相片  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>變更 outlook 的 Office 365 群組的預設設定為公用或私人
<a name="BKMK_CreateClassification"> </a>

Office 365 在 Outlook 中建立群組私人為預設值。如果您的組織想 Outlook 預設 （或回復至私人） 被建立為公開的 Office 365 群組，使用下列 PowerShell cmdlet 的語法：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
若要設定為私人：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
若要確認設定： 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
若要深入了解，請參閱[Set-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871816)和[Get-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871817)。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 群組指令程式

下列指令程式所最近供 Office 365 群組。如果您不能使用這些群組，您的 Office 365 訂閱已不更新的這項功能尚未。檢查您的訊息中心和[Office 365 藍圖](http://roadmap.office.com/en-us)。
  
| |
|**Cmdlet 名稱**|**描述**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |使用此指令程式來查詢現有的 Office 365 群組，並檢視 group 物件的屬性  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |更新特定的 Office 365 群組的屬性  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |建立新的 Office 365 群組。此指令程式提供一組最少的參數，可設定已擴充屬性的值會使用組 UnifiedGroup 建立新的群組之後  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |刪除現有的 Office 365 群組  <br/> |
|[取得 UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |擷取 Office 365 群組的成員資格與擁有者的資訊  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |新增數百或數千個使用者或新的擁有人、 以現有的 Office 365 群組  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |移除現有的 Office 365 群組的擁有者和成員  <br/> |
   
## <a name="for-more-information"></a>如需詳細資訊

- [使用 PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [套用或移除信箱上的 Outlook Web App 信箱原則](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [Office 365 群組命名原則](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

