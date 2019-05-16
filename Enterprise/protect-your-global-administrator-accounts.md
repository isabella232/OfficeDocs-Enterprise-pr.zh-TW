---
title: 保護您的 Office 365 全域系統管理員帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
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
description: 保護全域系統管理員存取您的 Office 365 訂用帳戶包含下列三個步驟。
ms.openlocfilehash: bb1b19a7ac0ec8e32c23303e8acf2b7ee42f0532
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071019"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>保護您的 Office 365 全域系統管理員帳戶

 **摘要：** 保護您的 Office 365 訂閱不根據洩露的全域系統管理員帳戶的攻擊。 
  
Office 365 訂閱，包括資訊蒐集和網路釣魚攻擊的安全性破壞通常即可危害 Office 365 全域系統管理員帳戶的認證。 在雲端中的安全性是您與 Microsoft 之間的合作關係：
  
- Microsoft 雲端服務會信任] 與 [安全性 foundation 上建置。 Microsoft 提供安全性控制和功能，協助您保護您的資料和應用程式。
    
- 您擁有您的資料和身分識別和保護它們，您的內部部署資源的安全性和您控制的雲端元件的安全性的責任。
    
Microsoft 提供功能來協助保護您的組織，但它們有效只有當您使用它們。 如果您不使用它們，您可能容易受到攻擊。 若要保護您的全域系統管理員帳戶，Microsoft 是以下詳細指示，以協助您：
  
1. 建立專用的 Office 365 全域系統管理員帳戶，並使用它們只在需要時。
    
2. 設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證。
    
3. 啟用及設定 Office 365 雲端 App 安全性來監視可疑的全域系統管理員帳戶活動。
    
> [!NOTE]
> 雖然本文著重於全域系統管理員帳戶，您也應該考慮是否其他帳戶具有廣泛的權限來存取您的訂閱，例如 eDiscovery 系統管理員或安全性或規範中的資料系統管理員帳戶，都必須保護相同的方式。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>步驟 1。 建立專用的 Office 365 全域系統管理員帳戶和使用它們只在需要時

有相對很少的管理工作，例如將角色指派給需要全域系統管理員權限的使用者帳戶。 因此，而不是使用已指派全域系統管理員角色的日常使用者帳戶，請執行下列步驟：
  
1. 判斷已指派全域系統管理員角色的使用者帳戶的集合。 您可以使用此命令在 Microsoft Azure Active Directory 模組的 Windows PowerShell 命令提示字元來這麼做：
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. 登入 Office 365 訂閱已被指派全域系統管理員角色的使用者帳戶。
    
3. 建立至少一個與最多五個最多的專用全域系統管理員使用者帳戶。 **使用強式密碼，至少有 12 個字元。** 如需詳細資訊，請參閱[建立強式密碼](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。 將新帳戶的密碼儲存在安全的位置。 
    
4. 將全域系統管理員角色指派給每個新增專用的全域系統管理員使用者帳戶。
    
5. 登出 Office 365。
    
6. 使用下列其中一個新的專用全域系統管理員使用者帳戶登入。
    
7. 針對每個現有使用者帳戶具有已被指派全域系統管理員角色從步驟 1:
    
  - 移除全域系統管理員角色。
    
  - 適用於該使用者的工作的功能和責任的帳戶指派系統管理員角色。 如需有關 Office 365 中的各種系統管理員角色的詳細資訊，請參閱 <<c0>關於 Office 365 系統管理員角色。
    
8. 登出 Office 365。
    
應該結果：
  
- 您的訂閱中唯一擁有全域系統管理員角色的使用者帳戶，就是新建立的一組專用全域系統管理員帳戶。 確認這搭配下列 PowerShell 命令：
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- 管理您訂閱的所有其他日常使用者帳戶擁有指派的系統管理員角色，這些角色會與他們的工作職責相關聯。
    
從 + 這一點時間，您使用登入專用的全域系統管理員帳戶僅適用於需要全域系統管理員權限的工作。 所有其他 Office 365 系統管理工作必須執行其他系統管理角色指派給使用者帳戶。
  
> [!NOTE]
> 是的這需要額外的步驟，為您的日常使用者帳戶登出並使用專用的全域系統管理員帳戶登入。 但這只需要完成的有時會針對全域系統管理員的作業。 請考慮的全域系統管理員帳戶外洩，需要更多的步驟之後，可用來復原您的 Office 365 訂閱。 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>步驟 2。 設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證

您的全域系統管理員帳戶的多重要素驗證 (MFA) 需要以外的帳戶名稱和密碼的其他資訊。 Office 365 支援下列驗證方法：
  
- 電話
    
- 隨機產生的密碼
    
- 智慧卡 (虛擬或實體)
    
- 生物特徵辨識裝置
    
如果您使用只能在雲端 （雲端身分識別模型） 中儲存的使用者帳戶的小型企業版，請使用下列步驟來設定 MFA 使用電話撥號或傳送到智慧電話的文字郵件驗證碼：
  
1. [啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. 若要設定每個[設定的 Office 365 2 雙步驟驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用電話或文字訊息的全域系統管理員帳戶的驗證方法。 
    
如果您使用 Office 365 混合式身分識別模型較大型組織，您會有更多的驗證選項。 如果您已經就緒更強的次要驗證方法有安全性基礎結構，請使用下列步驟：
  
1. [啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. 若要設定每個[設定 2 雙步驟驗證 Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用全域系統管理員帳戶適當的驗證方法。 
    
如果想要更強的驗證方法的安全性基礎結構不是在位置及運作的 Office 365 MFA，我們強烈建議您在使用 MFA 設定專用的全域系統管理員帳戶使用電話或文字訊息作為過渡期的安全性考量，傳送給智慧型手機的全域管理員帳戶的驗證碼。 不要讓您專用的全域系統管理員帳戶沒有 MFA 所提供的額外保護。
  
如需更多資訊，請參閱 [Office 365 部署的多重要素驗證方案](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。
  
若要連線至 Office 365 服務具有 MFA 和 PowerShell，請參閱[這篇文章](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>步驟 3。 監視可疑的全域系統管理員帳戶活動

Office 365 雲端 App 安全性可讓您建立原則，以通知您的訂閱中的可疑行為。 Cloud App Security 內建於 Office 365 E5，但也可做為個別的服務。 例如，如果您沒有 Office 365 E5，您可以購買個別的 Cloud App Security 授權的使用者帳戶的全域系統管理員、 安全性系統管理員和符合性系統管理員角色指派。
  
如果您有雲端 App 安全性中 Office 365 訂閱，請使用下列步驟：
  
1. 登入 Microsoft 365 系統管理中心以指派安全性系統管理員或符合性系統管理員角色的帳戶。
    
2. [開啟 Office 365 雲端 App 安全性](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。
    
3. 檢閱您的[Office 365 雲端 App 安全性中的異常偵測原則](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)以異常模式的特殊權限的系統管理活動的電子郵件通知您。 
    
若要新增的安全性管理員角色的使用者帳戶，[連線至 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3)與專用的全域系統管理員帳戶的 MFA，填寫使用者主體名稱的使用者帳戶，並再執行這些命令： 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

若要將使用者帳戶新增至 「 合規性管理員 」 角色的使用者帳戶後，使用者主體名稱，填寫，然後執行下列命令：
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>對於企業組織的額外保護

步驟 1-3，使用這些額外的方法，以確保您的全域系統管理員帳戶，並使用它執行的設定之後，會盡可能的安全。
  
### <a name="privileged-access-workstation-paw"></a>特殊權限的存取工作站 （爪）

若要確保高權工作的執行會儘可能安全，使用爪。 不是爪只適用於機密組態工作，例如需要全域系統管理員帳戶的 Office 365 設定專用的電腦。 這部電腦不是每日的網際網路瀏覽或電子郵件，因為它更妥善地保護從網際網路攻擊與潛在威脅。
  
如需如何設定爪指示，請參閱[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD 有權限 Identity Management (PIM)

而不是您要永久地指派全域系統管理員角色的全域系統管理員帳戶，您可以使用 Azure AD PIM 必要時，啟用全域系統管理員角色的隨選、 剛時間工作分派。
  
而不是您要永久的系統管理員的全域系統管理員帳戶，他們會成為合格的系統管理員。 需要有人之後，才不在作用中的全域系統管理員角色。 然後，您完成新增至全域系統管理員帳戶的全域系統管理員角色，在預定時間的啟用程序。 當到期時間時，PIM 會移除全域系統管理員帳戶的全域系統管理員角色。
  
使用 PIM，此程序會大幅降低您的全域系統管理員帳戶容易受到攻擊和惡意使用者所使用的時間量。
  
如需詳細資訊，請參閱[設定 Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。
  
> [!NOTE]
> PIM 是隨附於 Azure Active Directory 進階版 P2，也就是隨附 Enterprise Mobility + Security (EMS) E5，或者您可以購買個別授權您的全域系統管理員帳戶。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 記錄的安全性資訊和事件管理 (SIEM) 軟體

在伺服器上執行的 SIEM 軟體執行即時分析安全性提醒及建立的應用程式和網路硬體的事件。 若要允許 SIEM 伺服器加入 Office 365 安全性提醒及事件在其分析和報告功能，整合這些 SIEM 系統中：
  
- Azure AD
    
    如需詳細資訊，請參閱 <<c0>整合項目記錄從 Azure 到 SIEM 系統資源。
    
- Office 365 雲端 App 安全性
    
    如需詳細資訊，請參閱[整合 Office 365 雲端 App 安全性與 SIEM 伺服器](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。
    
## <a name="next-step"></a>下一步

請參閱[Office 365 的安全性最佳做法](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。
  

