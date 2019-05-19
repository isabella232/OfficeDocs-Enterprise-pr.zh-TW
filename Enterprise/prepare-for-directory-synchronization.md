---
title: 準備目錄同步處理至 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何準備將使用者佈建到 Office 365 使用目錄同步處理及使用此方法的長期效益。
ms.openlocfilehash: 2361f4484f00d61fda90fed407bf3c287bbc2bc1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162466"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a>準備目錄同步處理至 Office 365

混合式身分識別與目錄同步處理優點組織包括：
  
- 減少您組織中的系統管理程式
- （選用） 啟用單一登入案例
- 自動化 Office 365 中的帳戶變更
    
如需詳細的使用目錄同步處理優點的相關資訊，請參閱[目錄同步處理藍圖]( https://go.microsoft.com/fwlink/p/?LinkId=525398)及[Office 365 的混合式身分識別](plan-for-directory-synchronization.md)。

不過，目錄同步處理需要規劃和準備，以確保您 Active Directory 網域服務 (AD DS) 同步處理至 Office 365 訂閱的 Azure Active Directory (Azure AD) 租用戶最少要有的錯誤。 

請遵循下列步驟，為了獲得最佳結果順序。
  
## <a name="1-directory-cleanup-tasks"></a>1.目錄清理工作

將 AD DS 同步處理到 Azure AD 租用戶之前，您需要清除您的 AD DS。

> [!IMPORTANT]
> 如果您不執行 AD DS 清除，再進行同步處理，可以有重大的負面影響，在部署程序。 它可能需要數天，或甚至週，透過目錄同步處理，用來識別錯誤，以及重新同步處理的週期。 
  
在 AD DS 中，完成下列清理工作每個使用者帳戶，將被指派 Office 365 授權：
  
1. 請確定之**proxyAddresses**屬性中有效且唯一的電子郵件地址。 
    
2. **ProxyAddresses**屬性中移除任何重複的值。 
    
3.  如果可能的話，請確定使用者的**使用者**物件中的**userPrincipalName**屬性有效且唯一值。 為了最佳的同步處理體驗，請確定 AD DS UPN 符合 Azure AD UPN。 如果使用者沒有**userPrincipalName**屬性的值，**使用者**物件必須包含有效且唯一的**sAMAccountName**屬性值。 **UserPrincipalName**屬性中移除任何重複的值。 
    
4. 為了充分利用全域通訊清單 (GAL)，請確定下列屬性中的 AD DS 使用者帳戶的資訊正確：
    
  - givenName
  - 姓氏
  - displayName
  - 職稱
  - 部門
  - 辦公室
  - 辦公室電話
  - 行動電話
  - 傳真號碼
  - 街道地址
  - 城市
  - 州/省
  - 郵遞區號
  - 國家或地區
    
## <a name="2-directory-object-and-attribute-preparation"></a>2.目錄物件和屬性準備

成功執行目錄同步處理 AD DS 與 Office 365 之間需要適當準備您的 AD DS 屬性。 例如，您需要確保特定字元不使用同步處理與 Office 365 環境特定屬性。 未預期的字元，不會造成目錄同步處理失敗，但可能會傳回一則警告。 無效的字元將會造成目錄同步作業失敗。
  
目錄同步處理時，也會失敗如果某些 AD DS 使用者具有一或多個重複屬性。 每位使用者必須具有唯一的屬性。
  
您需要準備的屬性都會列在這裡：
  
- **displayName**
    
  - 如果此屬性存在於使用者物件中，將會同步處理與 Office 365。
  - 如果此屬性存在於使用者物件，必須是它的值。 亦即屬性必須不是空白。
  - 字元數上限： 256
    
- **givenName**
    
  - 如果此屬性存在於使用者物件中，會與 Office 365 同步處理，但 Office 365 不需要或使用它。
  - 字元數上限： 64
    
- **mail**
    
  - 屬性值必須是唯一在目錄內。
    
    > [!NOTE]
    > 如果沒有重複的值，會同步處理具有值的第一個使用者。 後續的使用者不會出現在 Office 365。 您必須修改 Office 365 中的其中一個值，或修改這兩個 AD DS 中兩個使用者在 Office 365 中顯示的順序中的值。 
  
- **mailNickname**（Exchange 別名） 
    
  - 屬性值不能以句點 （.） 開頭。
  - 屬性值必須是唯一在目錄內。
    
- **proxyAddresses**
    
  - 多重值屬性
  - 每個值的字元數上限： 256
  - 屬性值不得包含空格。
  - 屬性值必須是唯一在目錄內。
  - 無效字元： \< \> （);, [ ] "
    
    請注意，無效的字元會套用至下列類型的分隔符號字元和 「: 」，使得允許 SMTP:User@contso.com，但是 SMTP:user:M@contoso.com 不支援。
    
    > [!IMPORTANT]
    > 所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。 如果重複或不想要的地址存在，請參閱[在 Exchange 中移除重複而不想要的 proxy 位址](https://go.microsoft.com/fwlink/?LinkId=293860)的說明主題。 
  
- **sAMAccountName**
    
  - 字元數上限： 20
  - 屬性值必須是唯一在目錄內。
  - 無效字元: [\"|，/: \< \> + =;？ \* ]
  - 如果使用者具有**sAMAccountName**屬性無效但**userPrincipalName**屬性有效，Office 365 中建立使用者帳戶。 
  - 如果**sAMAccountName**和**userPrincipalName**均為無效，則必須更新 AD DS **userPrincipalName**屬性。 
    
- **sn**（姓氏） 
    
  - 如果此屬性存在於使用者物件中，會與 Office 365 同步處理，但 Office 365 不需要或使用它。
    
- **targetAddress**
    
    此為必填入使用者的**targetAddress**屬性 (例如，SMTP:tom@contoso.com) 必須出現在 Office 365 GAL。 在第三方訊息移轉案例中，這會需要 Office 365 架構延伸模組的 AD DS。 Office 365 架構延伸模組也會新增其他有用的屬性，以管理填入使用目錄同步作業工具，從 AD DS 的 Office 365 物件。 例如，將會新增**msExchHideFromAddressLists**屬性，來管理隱藏的信箱或通訊群組。 
   
  - 字元數上限： 256
  - 屬性值不得包含空格。
  - 屬性值必須是唯一在目錄內。
  - 無效字元: \ \< \> （);, [ ] "
  - 所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。
    
- **userPrincipalName**
    
  - **UserPrincipalName**屬性必須是網際網路樣式登入格式的使用者名稱，後面接著 at (@) 和網域名稱： 例如，user@contoso.com。 所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。
  - **UserPrincipalName**屬性的字元數目上限是 113。 為特定的字元數之前和之後，允許 at (@)、，如下所示： 
  - 是前面的使用者名稱的字元數上限 at (@): 64
  - 最大數目的網域名稱字元 at (@): 48
  - 無效字元: \ % &amp; \* + / =？ { } | \< \> ( ) ; : , [ ] "
  - 母音也是無效的字元。
  - @ 字元所需要的是每個**userPrincipalName**值。 
  - @ 字元不能是每個**userPrincipalName**值的第一個字元。 
  - 使用者名稱無法當做尾以英文句點 （.）、 連字號 (&amp;)、 空格，或依 at (@)。
  - 使用者名稱不得包含任何空格。
  - 必須使用可路由的網域。例如，無法使用 local 或 internal 的網域。
  - Unicode 字元會轉換為底線字元。
  - **userPrincipalName**不能包含任何重複的值在目錄中。 

請參閱[使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)使用 IdFIx 工具來識別屬性的 AD DS 中的錯誤。
    
## <a name="2-prepare-the-userprincipalname-attribute"></a>2.準備 userPrincipalName 屬性

Active Directory 被為了讓您的組織藉由使用 [ **sAMAccountName** ] 或 [ **userPrincipalName**登入您的目錄中的使用者。 同樣地，使用者可以使用他們的公司使用者主體名稱 (UPN) 登入 Office 365 或學校帳戶。 目錄同步處理會嘗試在 Azure Active Directory 中建立新的使用者使用位於 AD SD.相同 UPN UPN 的格式類似的電子郵件地址。 

在 Office 365 UPN 是用來產生的電子郵件地址的預設屬性。 很容易在**proxyAddresses**設定為不同的值取得**userPrincipalName** （AD DS 中和 Azure AD） 和主要電子郵件地址。 當其設定為不同的值時，可以是系統管理員和使用者的混淆。 
  
最好對齊這些屬性，以減少混淆。 若要符合需求的單一登入與 Active Directory Federation Services (AD FS) 2.0 中，您需要確保在 Azure Active Directory 與 AD DS Upn 相符，而且所使用的有效的網域命名空間。
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4.將替代的 UPN 尾碼新增至 AD DS

您可能需要新增至使用者的公司認證關聯的 Office 365 環境替代的 UPN 尾碼。 UPN 尾碼是 @ 字元右側的 UPN 部分。 用於單一登入的 UPN 可包含字母、數字、句號、虛線和底線，但不得包含其他字元類型。
  
如需有關如何將替代的 UPN 尾碼新增至 Active Directory 的詳細資訊，請參閱 <<c0>為目錄同步作業做好準備。
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a>5.符合 AD DS UPN 與 Office 365 UPN

如果您已經設定目錄同步處理，Office 365 使用者的 UPN 可能不符合您的 AD DS 中定義的使用者的 AD DS UPN。 若使用者在網域經過驗證之前即獲得指派授權，就可能發生這種情形。 若要修正此問題，請使用[PowerShell 修正 upn 重複的問題](https://go.microsoft.com/fwlink/p/?LinkId=396730)來更新使用者的 UPN，以確保 Office 365 UPN 相符的公司的使用者名稱和網域。 如果您要更新的 AD DS 中的 UPN，可能會想要同步處理與 Azure Active Directory 身分識別，您需要在 Office 365 中移除使用者的授權之前在 AD DS 中進行的變更。 
  
也請參閱[How to 準備目錄同步處理的非可路由網域 （例如.local 網域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。


## <a name="next-steps"></a>後續步驟

請參閱[使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)以協助您修正前目錄同步處理 AD DS 的屬性中的錯誤。

如果您已更正 IdFix 工具用來識別的所有屬性錯誤，並已完成步驟 1 到 5 上述，請參閱 <<c0>設定目錄同步處理。
