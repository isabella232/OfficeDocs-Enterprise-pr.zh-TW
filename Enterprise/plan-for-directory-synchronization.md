---
title: Office 365 的混合式身分識別與目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 說明 Office 365、 Active Directory 網域服務清除與 Azure Active Directory Connect 工具的目錄同步處理。
ms.openlocfilehash: 31fcd8baaccabf5d3f4f0cf47c7573c43f7cd40b
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102486"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a>Office 365 的混合式身分識別與目錄同步處理

根據業務需求與技術需求，混合式身分識別模型與目錄同步處理之後會採用 Office 365 的企業客戶的常見選擇。 目錄同步處理可讓您管理您 Active Directory 網域服務 (AD DS) 中的身分識別和所有更新將使用者帳戶、 群組及連絡人同步都處理至 Office 365 訂閱的 Azure Active Directory (Azure AD) 租用戶。


>[!Note]
>第一次同步處理 AD DS 使用者帳戶，它們都不會自動指派 Office 365 授權，而無法存取 Office 365 服務，例如電子郵件。 您必須透過群組成員資格，個別或動態指派授權給這些使用者帳戶。
>

## <a name="authentication-for-hybrid-identity"></a>驗證混合式身分識別

使用混合式身分識別模型時，有兩種驗證類型：

- 管理的驗證

  Azure AD 處理的驗證程序，使用本機儲存的密碼雜湊的版本，或將認證傳送至內部軟體代理程式來驗證內部部署的 AD DS。

- 同盟的驗證

  Azure AD 會重新導向的用戶端電腦要求驗證連絡另一個身分識別提供者。

### <a name="managed-authentication"></a>管理的驗證

有兩種類型的受管理的驗證：

- 密碼雜湊同步處理 (PHS)

  Azure AD 會執行本身的驗證。

- 傳遞驗證 (PTA)

  Azure AD 具有 AD DS 執行驗證。


#### <a name="password-hash-synchronization"></a>密碼雜湊同步處理

使用密碼雜湊同步處理 (PHS)，您可以與 Office 365 同步處理 AD DS 使用者帳戶及管理您內部使用者。 使用者密碼雜湊同步處理從 AD DS 到 Azure AD 如此，使用者擁有相同的密碼與內部及雲端中。 這是最簡單的方式，以啟用 Azure AD 中的 AD DS 身分識別驗證。 

![](./media/plan-for-directory-synchronization/phs-authentication.png)

當密碼已變更，或重設為內部時，新的密碼雜湊同步處理到 Azure AD，讓您的使用者一定可以使用相同的密碼雲端資源和內部部署資源。 使用者密碼永遠不會傳送到 Azure AD 或儲存在 Azure AD 以純文字。 Azure AD，例如 Identity Protection 的部分進階功能需要的 PHS 不論其選取驗證方法。
  
請參閱 <<c0>選擇 PHS了解更多。
  
#### <a name="pass-through-authentication"></a>傳遞驗證

通過驗證 (PTA) 提供用來驗證使用者直接與您的 AD DS 的一或多個內部部署伺服器上執行的軟體代理程式的 Azure AD 驗證服務的簡單密碼驗證。 使用傳遞驗證 (PTA)，您可以與 Office 365 同步處理 AD DS 使用者帳戶及管理您內部使用者。 

![](./media/plan-for-directory-synchronization/pta-authentication.png)

PTA 可讓您的使用者登入內部部署和 Office 365 資源並使用其內部部署帳戶和密碼的應用程式。 此組態會驗證使用者密碼，直接對您內部部署 AD DS，而不儲存在 Azure AD 中的密碼雜湊。 

PTA 也適用於組織的安全性需求來立即強制執行內部部署使用者帳戶狀態、 密碼原則和登入時間。 
  
請參閱 <<c0>選擇 PTA了解更多。
  
### <a name="federated-authentication"></a>同盟的驗證

同盟的驗證是主要使用於大型企業組織更複雜的驗證需求。 使用 Office 365 同步處理 AD DS 身分識別和使用者帳戶為受管理的內部部署。 利用同盟驗證，使用者有相同的密碼與內部及雲端中並不需要再次登入才能使用 Office 365。 

同盟的驗證可支援其他驗證需求，例如智慧卡型驗證或協力廠商的多重要素驗證時，則通常需要組織尚未驗證需求原生支援 Azure AD。
 
請參閱 < 若要了解更多的 [<b0>選擇同盟的驗證</b0>。
  
#### <a name="third-party-authentication-and-identity-providers"></a>協力廠商驗證與身分識別提供者

內部部署目錄物件可能會同步至 Office 365 和雲端資源存取主要是由協力廠商身分識別提供者 (Isp)。 如果您的組織使用同盟協力廠商解決方案，您可以設定登入與該解決方案搭配運作的 Office 365 提供協力廠商同盟解決方案會與 Azure AD 相容。
  
若要了解更多的[Azure AD 同盟相容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)，請參閱。
  
## <a name="ad-ds-cleanup"></a>AD DS 清理

為了協助確保順暢地轉換到 Office 365 使用同步處理，您必須在 Office 365 目錄同步處理部署之前準備您的 AD DS 樹系。
  
當您[設定 Office 365 中的目錄同步處理](set-up-directory-synchronization.md)，其中一個步驟是[下載並執行 IdFix 工具](install-and-run-idfix.md)。 您可以使用 IdFix 工具以協助進行[目錄清理](prepare-directory-attributes-for-synch-with-idfix.md)。
  
目錄清理應該要著重於下列工作：

- 移除重複的**proxyAddress**和**userPrincipalName**屬性。
- 使用有效的**userPrincipalName**屬性更新空白及無效的**userPrincipalName**屬性。
- **GivenName**、 姓氏 ( **sn** )、 **sAMAccountName**、 **displayName**、**郵件**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中移除無效，且有疑問的字元屬性。 如需準備屬性的詳細資訊，請參閱 <<c0>清單的屬性，會同步處理的 Azure Active Directory 同步作業工具。

    > [!NOTE]
    > 這些都是相同 Azure AD Connect 同步處理的屬性。 
  
## <a name="multi-forest-deployment-considerations"></a>多樹系部署考量

針對多個樹系與 SSO 選項，使用[自訂安裝的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
  
如果您的組織有多個樹系進行驗證 （登入樹系），我們強烈建議如下：
  
- **請考慮將合併在樹系。** 一般而言，沒有更多維護多個樹系所需的額外負荷。 除非您的組織有安全性限制，指示不同樹系的需求，否則請簡化您的內部部署環境。
- **只有在您的主要登入樹系中使用。** 請考慮部署只能在您的 Office 365 在首度發行的主要登入樹系中的 Office 365。 

如果您無法合併您多樹系的 AD DS 部署，或使用其他目錄服務管理身分識別，您可能無法同步處理這些 Microsoft 或合作夥伴的協助。
  
如需詳細資訊，請參閱[使用單一登入案例的多樹系目錄同步](https://go.microsoft.com/fwlink/p/?LinkId=525321)。
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>取決於目錄同步作業的功能
  
目錄同步作業所需的下列特性與功能：
  
- Azure AD 無縫單一登入 (SSO)
- Skype 共存
- Exchange 混合式部署，包括：
  - 您在內部部署 Exchange 環境與 Office 365 之間的完全共用全域通訊清單 (GAL)。
  - 從不同的郵件系統的同步處理 GAL 資訊。
  - 將使用者加入及移除使用者從 Office 365 服務方案的能力。 這需要下列項目：
  - 目錄同步處理安裝期間，必須設定雙向同步處理。 根據預設，目錄同步處理工具的目錄資訊寫入僅雲端。 當您設定雙向同步處理時，以便有限的數量的物件的屬性會複製從雲端，並覆寫這些回本機的 AD DS 啟用回寫功能。 回寫也稱為 Exchange 混合式模式。 
  - 內部部署 Exchange 混合式部署
  - 在保留其他使用者信箱在內部將部分使用者信箱移至 Office 365 功能。
  - 安全的寄件者和封鎖寄件者的內部會複寫至 Office 365。
  - 基本委派及代理傳送的電子郵件功能。
  - 您有內部整合式的智慧卡或多重要素驗證方案。
- 相片、 縮圖、 會議室及安全性群組同步處理

## <a name="next-step"></a>下一步

當您準備好要部署混合式身分識別時，請參閱 <<c0>準備佈建使用者。
  

