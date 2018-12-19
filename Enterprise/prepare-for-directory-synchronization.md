---
title: 準備透過 Office 365 的目錄同步佈建使用者
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何準備使用目錄同步作業及使用此方法的長期效益佈建到 Office 365 的使用者。
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371117"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>準備透過 Office 365 的目錄同步佈建使用者

佈建使用目錄同步處理的使用者需要更多的規劃和準備比只管理 Office 365 中直接您工作或學校帳戶。其他的規劃和準備工作所需以確保您的內部部署 Active Directory 同步至 Azure Active Directory 正確處理。若您的組織要新增的好處包括：
  
- 減少您組織中的系統管理程式
- （選用） 啟用單一登入案例
- 自動化 Office 365 中的帳戶變更
    
如需使用目錄同步處理的優點的相關資訊，請參閱[目錄同步處理藍圖]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[了解 Office 365 身分識別和 Azure Active Directory。](about-office-365-identity.md)
  
若要決定哪些案例是最適合您的組織，請檢閱[目錄整合工具比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)。
  
## <a name="directory-cleanup-tasks"></a>目錄清理工作

開始同步處理目錄之前，您需要清理目錄。
  
請檢閱[屬性由 Azure AD 連接的 Azure Active directory 同步處理](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)。
  
> [!IMPORTANT]
> 如果您不執行目錄清理同步處理之前，可以是嚴重的負面影響的部署程序。它可能需要數天，或偶數週，透過目錄同步處理，用來識別錯誤及重新同步處理的週期。 
  
在內部部署目錄中，完成下列清理工作：
  
1. 請確保每位將被指派 Office 365 服務方案的使用者在 **proxyAddresses** 屬性中都具有一個有效且唯一的電子郵件地址。 
    
2. 移除 **proxyAddresses** 屬性中的任何重複值。 
    
3.  請儘可能確定將被指派 Office 365 服務方案的每個使用者在使用者的**使用者**物件中具有**userPrincipalName**屬性有效且唯一值。最佳的同步處理體驗，請確定內部部署 Active Directory UPN 符合雲端 UPN。如果使用者不具有**userPrincipalName**屬性的值，**使用者**物件必須包含有效且唯一的**sAMAccountName**屬性值。**UserPrincipalName**屬性中移除任何重複值。 
    
4. 為了充分利用全域通訊清單 (GAL)，請確定下列屬性中的資訊正確：
    
  - givenName 
  - surname
  - displayName
  - 職稱
  - 部門
  - 辦公室
  - 辦公室電話
  - 行動電話
  - 傳真號碼
  - 路/街
  - 市或鎮
  - 州或省
  - 郵遞區號
  - 國家或地區
    
## <a name="directory-object-and-attribute-preparation"></a>目錄物件和屬性準備

您的內部部署目錄和 Office 365 之間順利目錄同步處理需要已適當地準備您的內部部署目錄屬性。例如，您需要確定特定字元不用於特定會與 Office 365 環境進行同步處理的屬性。未預期的字元不會造成目錄同步處理失敗，但是可能會傳回一則警告訊息。無效字元將會造成目錄同步作業失敗。
  
如果您的部分 Active Directory 使用者有一或多個重複屬性也會失敗目錄同步處理。每位使用者必須具有唯一的屬性。
  
以下列出您需要準備屬性：
  
 **附註：** 您也可以使用[IdFix 工具](install-and-run-idfix.md)以更方便此程序。 
  
- **displayName**
    
  - 如果此屬性存在於使用者物件中，則會與 Office 365 同步處理。
  - 如果此屬性存在於使用者物件中，該屬性必須有值。也就是說，屬性不能空白。
  - 字元數上限：256
    
- **givenName **
    
  - 如果屬性存在於使用者物件中，該屬性會與 Office 365 同步處理，但 Office 365 不需要或不會使用該屬性。
  - 字元數上限：64
    
- **mail**
    
  - 屬性值在目錄內必須是唯一的。
    
    > [!NOTE]
    > 如果有重複值，此值的第一個使用者會同步處理。後續的使用者將不會出現在 Office 365 中。您必須修改 Office 365 中的其中一個值或修改兩個兩個使用者會出現在 Office 365 中的順序中的內部部署目錄中的值。 
  
- **mailNickname** (Exchange 別名) 
    
  - 屬性值不能以句點 （.） 開頭。
  - 屬性值在目錄內必須是唯一的。
    
- **proxyAddresses **
    
  - 多重值屬性
  - 每個值的字元數上限：256
  - 屬性值不得包含空格。
  - 屬性值在目錄內必須是唯一的。
  - 無效字元： \< \> （);, [ ] "
    
    附註的無效字元套用到下列類型的分隔字元的字元與":"，因而可以看允許 SMTP:User@contso.com，但不是 SMTP:user:M@contoso.com。
    
    > [!IMPORTANT]
    > 所有的簡易郵件傳輸通訊協定 (SMTP) 位址均應遵循電子郵件傳訊標準。如果存在重複或不想要的地址，請參閱[Exchange 中移除重複並不需要 proxy 位址](https://go.microsoft.com/fwlink/?LinkId=293860)的說明主題。 
  
- **sAMAccountName**
    
  - 字元數上限：20
  - 屬性值在目錄內必須是唯一的。
  - 無效字元： [\"|，/: \< \> + =;？\* ]
  - 如果使用者的 **sAMAccountName** 屬性無效，但 **userPrincipalName** 屬性有效，則會在 Office 365 中建立使用者帳戶。 
  - 若**sAMAccountName**及**userPrincipalName**均為無效，則必須更新內部部署 Active Directory **userPrincipalName**屬性。 
    
- **sn** (姓氏) 
    
  - 如果屬性存在於使用者物件中，該屬性會與 Office 365 同步處理，但 Office 365 不需要或不會使用該屬性。
    
- **targetAddress**
    
    有必要便會填入使用者的**targetAddress**屬性 (例如 SMTP:tom@contoso.com) 必須出現在 Office 365 GAL。在第三方訊息移轉案例中這會需要擴充 Office 365 架構內部部署目錄。擴充 Office 365 架構也會新增其他有用的屬性來管理 Office 365 填入使用目錄同步作業工具從內部部署目錄的物件。例如，且無法新增**msExchHideFromAddressLists**屬性來管理隱藏的信箱或通訊群組。 
   
  - 字元數上限：256
  - 屬性值不得包含空格。
  - 屬性值在目錄內必須是唯一的。
  - 無效字元： \ \< \> （);, [ ] "
  - 所有 Simple Mail Transport Protocol (SMTP) 位址都要符合電子郵件傳訊標準。
    
- **userPrincipalName**
    
  - **UserPrincipalName**屬性必須是網際網路樣式登入格式的使用者名稱後面其中 at 符號 (@) 和網域名稱： 例如 user@contoso.com。所有的簡易郵件傳輸通訊協定 (SMTP) 位址均應遵循電子郵件傳訊標準。
  - **userPrincipalName** 屬性的字元數上限為 113。@ 符號前後允許的特定字元數如下： 
  - @ 符號之前的使用者名稱字元數上限：64
  - @ 符號之後的網域名稱字元數上限：48
  - 無效字元： \ % &amp; \* + / =？{ } |\< \> ( ) ;: , [ ] "
  - 母音也是無效的字元。
  - 字元必須要有 @ 每個**userPrincipalName**值。 
  - 每個 **userPrincipalName** 值皆不可以 @ 字元做為第一個字元。 
  - 使用者名稱結尾不得句點 （.）、 & 符號 (&amp;)、 空格，或參閱註冊 (@)。
  - 使用者名稱不得包含任何空格。
  - 必須使用可路由的網域 ；例如，不能使用 local 或 internal 的網域。
  - Unicode 字元會轉換為底線字元。
  - **userPrincipalName** 不可包含任何在目錄中會重複的值。 
    
## <a name="prepare-the-userprincipalname-attribute"></a>準備 userPrincipalName 屬性

Active Directory 的設計允許您的組織可以使用 [ **sAMAccountName** ] 或 [ **userPrincipalName**登入您的目錄中的使用者。同樣地，使用者可以使用其工作的使用者主體名稱 (UPN) 登入 Office 365 或學校帳戶。使用您的內部部署目錄中的相同 UPN Azure Active Directory 中建立新的使用者嘗試目錄同步處理。UPN 格式類似電子郵件地址。 

在 Office 365 UPN 是用來產生電子郵件地址的預設屬性。很容易取得**userPrincipalName** (內部和 Azure Active Directory 中) 及**proxyAddresses**設為不同的值的主要電子郵件地址。當已設為不同的值時，可以是系統管理員和使用者混淆。 
  
最好對齊以減少混淆這些屬性。若要符合需求的單一登入與 Active Directory Federation Services (AD FS) 2.0、 您需要確定 Azure Active Directory 與您在內部部署 Active Directory Upn 相符，並使用有效的網域命名空間。
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>將替代的 UPN 尾碼新增至 AD DS

您可能需要新增至使用者的公司認證關聯的 Office 365 環境替代的 UPN 尾碼。UPN 尾碼屬於右邊的 UPN @ 字元。單一登入所用的 Upn 可以包含字母、 數字、 期間、 虛線、 和底線，但沒有其他類型的字元。
  
如需有關如何將替代的 UPN 尾碼新增至 Active Directory 的詳細資訊，請參閱[為目錄同步作業的準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>使內部部署 UPN 與 Office 365 UPN

如果您已設定目錄同步處理，Office 365 使用者的 UPN 可能不符合您的內部部署目錄服務中定義的使用者的內部部署 UPN。當使用者已指派授權已驗證網域之前可以發生此情況。若要修正此問題，使用[PowerShell 修正重複 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)更新以確保 Office 365 UPN 相符的公司的使用者名稱與網域使用者的 UPN。如果您要更新的內部部署目錄服務中的 UPN 並想要同步處理與 Azure Active Directory 身分識別，您需要在 Office 365 中移除使用者的授權之前先進行變更內部。 
  
另請參閱[如何準備非-路由傳送的網域 （例如.local 網域） 進行目錄同步作業](prepare-a-non-routable-domain-for-directory-synchronization.md)。
  
## <a name="directory-integration-tools"></a>目錄整合工具

目錄物件 （使用者、 群組及連絡人） 從內部部署 Active Directory 環境至 Office 365 目錄基礎結構、 Azure Active Directory 同步處理的目錄同步處理。請參閱[目錄整合工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)的可用的工具和功能的清單。[Microsoft Azure Active Directory 連線](https://go.microsoft.com/fwlink/p/?LinkID=510956)是建議的工具。如需 Azure 作用中的目錄連線的詳細資訊，請參閱[Azure Active Directory 與您的內部身分識別的整合](https://go.microsoft.com/fwlink/p/?LinkId=527969)。
  
當使用者帳戶與 Office 365 目錄第一次同步處理時，則會標示為為未啟動。他們無法傳送或接收電子郵件，以及它們不取用訂閱授權。當您準備好要指派給特定使用者的 Office 365 訂閱時，您必須選取並啟動其[指派給 Office 365 中的商務使用者的授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。
  
您也可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)指派授權。請參閱自動化解決方案[如何使用 PowerShell 自動將授權指派給您的 Office 365 使用者](https://go.microsoft.com/fwlink/p?LinkID=329805)。