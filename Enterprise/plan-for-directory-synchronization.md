---
title: < Plan for Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
description: 說明 Office 365、 Active Directory 清理] 中，與 Azure Active Directory Connect 工具的目錄同步處理。
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492079"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>< Plan for Office 365 的目錄同步處理

根據業務需求與技術需求，目錄同步處理會是最常見的佈建選擇移至 Office 365 的企業客戶的。 目錄同步處理可讓內部部署 Active Directory 中受管理的身分識別和所有更新該身分識別同步都處理至 Office 365。
  
有幾個事項請記住，當您規劃實作的目錄同步處理，包括目錄準備的需求和 Azure Active Directory 的功能。 目錄準備涵蓋很多領域。 它們包括屬性更新、 稽核和規劃網域控制站。 規劃需求和功能，包括決定所需，規劃多 forest/directory 案例中、 容量規劃，及雙向同步處理權限。
  
## <a name="office-365-identity-models"></a>Office 365 身分識別模型

Office 365 會使用兩個主要的驗證與身分識別模型： 雲端驗證和同盟的驗證。
  
### <a name="cloud-authentication"></a>雲端驗證

[雲端身分識別](about-office-365-identity.md)-建立及管理[Microsoft 365 系統管理中心](https://admin.microsoft.com)中的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory，來管理您的使用者。
  
[密碼雜湊同步處理與無縫單一登入](about-office-365-identity.md)-啟用內部部署目錄物件的 [驗證]，在 Azure AD 中的最簡單方式。 使用密碼雜湊同步處理 (PHS)，您可以與 Office 365 同步處理您的內部部署 Active Directory 使用者帳戶物件及管理您內部使用者。
  
[無縫單一登入與通過驗證](about-office-365-identity.md)-提供使用一或多個內部部署伺服器上執行的軟體代理程式來驗證直接與使用者的 Azure AD 驗證服務的簡單密碼驗證您內部部署 Active Directory。
  
### <a name="federated-authentication"></a>同盟的驗證

[與 Active Directory Federation Services AD FS 的同盟身分識別](about-office-365-identity.md)-主要使用於具有較複雜的驗證需求，大型企業組織內部部署與 Office 365 同步處理目錄物件和使用者帳戶受管理的內部。
  
[協力廠商驗證與身分識別提供者](about-office-365-identity.md)的內部部署目錄物件可能會同步至 Office 365 部署及雲端資源存取主要是由協力廠商身分識別提供者 (Isp) 所管理。
  
## <a name="active-directory-cleanup"></a>Active Directory 清理

為了協助確保使用同步處理順暢地轉換到 Office 365，我們強烈建議您準備您的 Active Directory 樹系，再開始 Office 365 目錄同步處理部署。
  
當您[設定 Office 365 中的目錄同步處理](set-up-directory-synchronization.md)，其中一個步驟是[下載並執行 IdFix 工具](install-and-run-idfix.md)。 您可以使用 IdFix 工具以協助進行[目錄清理](prepare-directory-attributes-for-synch-with-idfix.md)。
  
目錄清理應該要著重於下列工作：

- 移除重複的**proxyAddress**和**userPrincipalName**屬性。
- 使用有效的**userPrincipalName**屬性更新空白及無效的**userPrincipalName**屬性。
- **GivenName**、 姓氏 ( **sn** )、 **sAMAccountName**、 **displayName**、**郵件**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中移除無效，且有疑問的字元屬性。 如需準備屬性的詳細資訊，請參閱 <<c0>清單的屬性，會同步處理的 Azure Active Directory 同步作業工具。

    > [!NOTE]
    > 這些都是相同 Azure AD Connect 同步資料的屬性。 
  
## <a name="multi-forest-deployment-considerations"></a>多樹系部署考量

針對多個樹系與 SSO 選項，使用[自訂安裝的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
  
如果您的組織有多個樹系進行驗證 （登入樹系），我們強烈建議如下：
  
- **評估合併在樹系。** 一般而言，沒有更多維護多個樹系所需的額外負荷。 除非您的組織有安全性限制，指示不同樹系的需求，否則請簡化您的內部部署環境。
- **只有在您的主要登入樹系中使用。** 請考慮部署只能在您的 Office 365 在首度發行的主要登入樹系中的 Office 365。 

如果您無法合併您的多樹系 Active Directory 部署，或使用其他目錄服務管理身分識別，您可能無法同步處理這些 Microsoft 或合作夥伴的協助。
  
如需詳細資訊，請參閱 <<c0>多樹系目錄同步處理與單一登入案例。
  
## <a name="directory-integration-tools"></a>目錄整合工具

目錄同步處理的 Office 365 目錄基礎結構從內部部署 Active Directory 環境是同步處理的目錄物件 （使用者、 群組和連絡人）。 請參閱如需可用的工具和功能的清單的[目錄整合工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。 若要使用建議的工具是[Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)。
  
當使用者帳戶會與 Office 365 目錄同步處理，第一次時，他們會標示為非啟動。 無法傳送或接收電子郵件，以及它們不會耗用訂閱授權。 當您準備好要指派給特定使用者的 Office 365 訂閱時，您必須選取並啟動它們藉由指定有效的授權。
  
目錄同步作業所需的下列特性與功能：
  
- SSO
- Skype 共存
- Exchange 混合式部署，包括：
  - 您在內部部署 Exchange 環境與 Office 365 之間的完全共用全域通訊清單 (GAL)。
  - 從不同的郵件系統的同步處理 GAL 資訊。
  - 將使用者加入及移除使用者從 Office 365 服務方案的能力。 這需要下列項目：
  - 目錄同步處理安裝期間，必須設定雙向同步處理。 根據預設，目錄同步處理工具的目錄資訊寫入僅雲端。 當您設定雙向同步處理時，以便有限的數量的物件的屬性會複製從雲端，並覆寫這些回您的本機 Active Directory 啟用回寫功能。 回寫也稱為 Exchange 混合式模式。 
  - 內部部署 Exchange 混合式部署
  - 在保留其他使用者信箱在內部將部分使用者信箱移至 Office 365 功能。
  - 安全的寄件者和封鎖寄件者的內部會複寫至 Office 365。
  - 基本委派及代理傳送的電子郵件功能。
  - 您有內部整合式的智慧卡或多重要素驗證方案。
- 相片、 縮圖、 會議室及安全性群組同步處理