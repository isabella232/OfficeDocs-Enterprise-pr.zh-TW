---
title: 保護您的 Office 365 全域系統管理員帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: 保護您的 Office 365 訂閱的全域系統管理員存取。
ms.openlocfilehash: 293044fc508c89b5e08234aa62633c6c4490ba6d
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072205"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>保護您的 Office 365 全域系統管理員帳戶

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

Office 365 訂閱，包括資訊蒐集和網路釣魚攻擊的安全性破壞通常即可危害 Office 365 全域系統管理員帳戶的認證。 在雲端中的安全性是您與 Microsoft 之間的合作關係：
  
- Microsoft 雲端服務會信任] 與 [安全性 foundation 上建置。 Microsoft 提供安全性控制和功能，協助您保護您的資料和應用程式。
    
- 您擁有您的資料和身分識別和保護它們，您的內部部署資源的安全性和您控制的雲端元件的安全性的責任。
    
Microsoft 提供功能來協助保護您的組織，但它們有效只有當您使用它們。 如果您不使用它們，您可能容易受到攻擊。 若要保護您的全域系統管理員帳戶，Microsoft 是以下詳細指示，以協助您：
  
1. 建立專用的 Office 365 全域系統管理員帳戶，並使用它們只在需要時。
    
2. 設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證。
    
> [!NOTE]
> 雖然本文著重於全域系統管理員帳戶，您應該考慮是否其他帳戶具有廣泛的權限來存取您的訂閱，例如 eDiscovery 管理員 」 或 「 安全性 」 或 「 合規性管理員中的資料帳戶，都必須保護相同的方式。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>步驟 1。 建立專用的 Office 365 全域系統管理員帳戶和使用它們只在需要時

有相對很少的管理工作，例如將角色指派給需要全域系統管理員權限的使用者帳戶。 因此，而不是使用已指派全域系統管理員角色的日常使用者帳戶，請執行下列步驟：
  
1. 判斷已指派全域系統管理員角色的使用者帳戶的集合。 您可以利用 Graph 命令 PowerShell 的 Azure Active (Azure AD) Directory 來進行此作業：
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. 登入 Office 365 訂閱已被指派全域系統管理員角色的使用者帳戶。
    
3. 建立至少一個與最多五個最多的專用全域系統管理員使用者帳戶。 **使用強式密碼，至少有 12 個字元。** 如需詳細資訊，請參閱[建立強式密碼](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。 將新帳戶的密碼儲存在安全的位置。 
    
4. 將全域系統管理員角色指派給每個新增專用的全域系統管理員使用者帳戶。
    
5. 登出 Office 365。
    
6. 使用下列其中一個新的專用全域系統管理員使用者帳戶登入。
    
7. 針對每個現有使用者帳戶具有已被指派全域系統管理員角色從步驟 1:
    
  - 移除全域系統管理員角色。
    
  - 適用於該使用者的工作的功能和責任的帳戶指派系統管理員角色。 如需各種 Office 365 中的系統管理員角色的詳細資訊，請參閱[關於系統管理員角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)。
    
8. 登出 Office 365。
    
應該結果：
  
- 您的訂閱中唯一擁有全域系統管理員角色的使用者帳戶，就是新建立的一組專用全域系統管理員帳戶。 確認這搭配下列 PowerShell 命令：
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- 管理您訂閱的所有其他日常使用者帳戶擁有指派的系統管理員角色，這些角色會與他們的工作職責相關聯。
    
從 + 這一點時間，您使用登入專用的全域系統管理員帳戶僅適用於需要全域系統管理員權限的工作。 所有其他 Office 365 系統管理工作必須執行其他系統管理角色指派給使用者帳戶。
  
> [!NOTE]
> 這需要額外的步驟，為您的日常使用者帳戶登出並使用專用的全域系統管理員帳戶登入。 但這只需要完成的有時會針對全域系統管理員的作業。 請考慮的全域系統管理員帳戶外洩，需要更多的步驟之後，可用來復原您的 Office 365 訂閱。
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>步驟 2。 設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證

多重要素驗證 (MFA) 需要以外的帳戶名稱和密碼的其他資訊。 Office 365 支援下列驗證方法：
  
- 電話
    
- 隨機產生的密碼
    
- 智慧卡 (虛擬或實體)
    
- 生物特徵辨識裝置
    
如果您使用只能在雲端 （僅限雲端身分識別模型） 中儲存的使用者帳戶的小型企業版，請，使用下列步驟來設定 MFA 使用電話撥號或傳送到智慧電話的文字郵件驗證碼：
  
1. [設定 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。
    
2. 若要設定每個[設定的 Office 365 2 雙步驟驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用電話或文字訊息的全域系統管理員帳戶的驗證方法。 
    
如果您使用 Office 365 混合式身分識別模型較大型組織，您會有更多的驗證選項。 如果您已經就緒更強的次要驗證方法有安全性基礎結構，請使用下列步驟：
  
1. [設定 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。
    
2. 若要設定每個[設定 2 雙步驟驗證 Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用全域系統管理員帳戶適當的驗證方法。 
    
如果想要更強的驗證方法的安全性基礎結構不是在位置及運作的 Office 365 MFA，我們強烈建議您在使用 MFA 設定專用的全域系統管理員帳戶使用電話或文字訊息作為過渡期的安全性考量，傳送給智慧型手機的全域管理員帳戶的驗證碼。 不要讓您專用的全域系統管理員帳戶沒有 MFA 所提供的額外保護。
  
如需更多資訊，請參閱 [Office 365 部署的多重要素驗證方案](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)。
  
若要連線至 Office 365 服務具有 MFA 和 PowerShell，請參閱下列文章：

- [Office 365 PowerShell 的使用者帳戶、 群組和授權](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [商務用 Skype Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>對於企業組織的額外保護

步驟 1 和 2 中，使用這些額外的方法，以確保您的全域系統管理員帳戶，並使用它執行的設定之後，會盡可能的安全。
  
### <a name="privileged-access-workstation"></a>特殊權限的存取工作站

若要確保高權工作的執行會儘可能安全，使用的特殊權限的存取工作站 （爪）。 不是爪只適用於機密組態工作，例如需要全域系統管理員帳戶的 Office 365 設定專用的電腦。 這部電腦不是每日的網際網路瀏覽或電子郵件，因為它更妥善地保護從網際網路攻擊與潛在威脅。
  
如需如何設定爪指示，請參閱[https://aka.ms/cyberpaw](https://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

而不是您要永久地指派全域系統管理員角色的全域系統管理員帳戶，您可以使用 Azure AD Privileged Identity Management (PIM) 時，它會啟用全域系統管理員角色的隨選、 剛時間指派所需。
  
而不是您要永久的系統管理員的全域系統管理員帳戶，他們會成為合格的系統管理員。 需要有人之後，才不在作用中的全域系統管理員角色。 然後，您完成新增至全域系統管理員帳戶的全域系統管理員角色，在預定時間的啟用程序。 當到期時間時，PIM 會移除全域系統管理員帳戶的全域系統管理員角色。
  
使用 PIM，此程序會大幅降低您的全域系統管理員帳戶容易受到攻擊和惡意使用者所使用的時間量。
  
如需詳細資訊，請參閱[Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。
  
> [!NOTE]
> PIM 是隨附於 Azure AD Premium P2，隨附於 Microsoft 365 企業版 E5 或 Enterprise Mobility + Security (EMS) E5，或者您可以購買個別授權您的全域系統管理員帳戶。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 記錄的安全性資訊和事件管理 (SIEM) 軟體

在伺服器上執行的 SIEM 軟體執行即時分析安全性提醒及建立的應用程式和網路硬體的事件。 若要允許 SIEM 伺服器加入 Office 365 安全性提醒及事件在其分析和報告功能，將 Azure AD 整合到您 SEIM。 請參閱[Azure 記錄整合的簡介](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。

## <a name="next-step"></a>下一步

如果您要設定 Office 365 訂用帳戶的身分識別，請參閱：

- [僅限雲端身分識別](cloud-only-identities.md)如果您正在使用的僅限雲端身分識別
- [準備目錄同步處理](prepare-for-directory-synchronization.md)如果您使用混合式身分識別

  
## <a name="see-also"></a>另請參閱

[Office 365 安全性藍圖](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。
