---
title: 保護您的 Office 365 全域管理員帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
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
description: 保護您的 Office 365 訂閱與以下三個步驟的全域系統管理員存取。
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540182"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>保護您的 Office 365 全域管理員帳戶

 **摘要：** 保護您的 Office 365 訂閱從全域管理員帳戶的危害為基礎的攻擊。 
  
Office 365 訂閱包括資訊蒐集和網路釣魚攻擊的安全性缺口通常由影響之下的 Office 365 全域管理員帳戶的認證。在雲端中的安全性是您與 Microsoft 之間合作關係：
  
- Microsoft 雲端服務之內建信任] 與 [安全性的基礎。Microsoft 提供的安全性控制項和功能，可協助您保護您的資料和應用程式。
    
- 您擁有資料及身分識別和保護其、 您內部部署的資源、 安全性及雲端元件您控制的安全性責任。
    
Microsoft 提供的功能，可協助保護您的組織，但他們有效只有當您使用的方法。如果您不使用它們，您可能遭受攻擊。若要保護您的全域管理員帳戶，Microsoft 這裡是以協助您進行詳細指示：
  
1. 建立專用的 Office 365 全域管理員帳戶並只在必要時加以使用。
    
2. 設定專用的 Office 365 全域管理員帳戶的多重要素驗證及使用的次要驗證最強大的表單。
    
3. 啟用及設定 Office 365 雲端可疑的全域管理員帳戶活動的監視的應用程式安全性。
    
> [!NOTE]
> 雖然本文著重於全域管理員帳戶，您也應該考量是否其他帳戶具備廣泛的權限以存取您的訂閱，例如 eDiscovery 管理員或安全性或規範資料系統管理員帳戶應該保護相同的方式。 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>步驟 1。建立專用的 Office 365 全域管理員帳戶及使用它們只有在必要時

有較少的管理工作，例如指派角色給需要全域系統管理員權限的使用者帳戶。因此，而不是使用已指派的全域管理員角色日常的使用者帳戶，執行下列步驟：
  
1. 判斷已指派的全域管理員角色的使用者帳戶的集合。您可以使用下列命令在 Microsoft Azure Active Directory Module for Windows PowerShell 命令提示字元來這麼做：
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. 登入您的 Office 365 訂閱以已指派的全域管理員角色的使用者帳戶。
    
3. 建立至少一個和最多五個專用全域管理員的使用者帳戶。**使用強式密碼至少 12 個字元長。** 如需詳細資訊，請參閱[建立強式密碼](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。儲存在安全的位置之新帳戶的密碼。 
    
4. 將全域管理員角色指派給每個新專用的全域系統管理員使用者帳戶。
    
5. 不在 Office 365 登入。
    
6. 使用其中一個新的專用的全域系統管理員使用者帳戶登入。
    
7. 針對每個現有使用者帳戶有已指派全域管理員角色的步驟 1：
    
  - 全域管理員角色中移除。
    
  - 將系統管理員角色指派給該使用者的工作函數和責任適當的帳戶。如需 Office 365 中的各種管理角色的詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。
    
8. 不在 Office 365 登入。
    
結果應該是：
  
- 您的訂閱中具有全域管理員角色的唯一使用者帳戶是一組新的專用的全域管理員帳戶。確認這與下列 PowerShell 命令：
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- 管理您訂閱的所有其他日常使用者帳戶擁有指派的系統管理員角色，這些角色會與他們的工作職責相關聯。
    
從 [開始這個可用您登入專用的全域管理員帳戶僅針對需要全域系統管理員權限的作業。所有其他 Office 365 管理必須將其他系統管理角色指派給使用者帳戶來完成。
  
> [!NOTE]
> 是，這需要其他步驟以做為日常的使用者帳戶登出及使用專用的全域管理員帳戶登入。但這只需要有時會完成的全域管理員作業。請考慮的復原您的 Office 365 訂閱之後全域管理員帳戶破壞需要更多的步驟。 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>步驟 2。設定專用的 Office 365 全域管理員帳戶的多重要素驗證及使用的次要驗證最強大的表單

全域管理員帳戶的多重要素驗證 (MFA) 需要以外的帳戶名稱和密碼的其他資訊。Office 365 支援下列驗證方法：
  
- 撥打的電話
    
- 隨機產生的複雜的程式碼
    
- 智慧卡 （虛擬或實體）
    
- 生物特徵裝置
    
如果您使用的使用者帳戶儲存在雲端 （雲端身分識別模型） 僅適用於小型企業，使用下列步驟來設定 MFA 使用電話或傳送至智慧型手機文字郵件驗證碼：
  
1. [啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. [Set up Office 365 步驟 2 驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)設定每個專用電話通話或文字訊息的全域管理員的帳戶作為驗證方法。 
    
如果您使用 Office 365 的混合式身分識別模型的較大型組織，您有多個驗證選項。如果您已經備妥更有力的次要驗證方法有安全性基礎結構，請使用下列步驟：
  
1. [啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。
    
2. [Set up Office 365 步驟 2 驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)設定每個專用全域管理員帳戶適當的驗證方法。 
    
如果想要更有力的驗證方法的安全性基礎結構不是位置和 for Office 365 MFA 運作中，我們強烈建議 MFA 設有專用的全域管理員帳戶使用電話或文字訊息中期安全防護的形式傳送至智慧型手機全域管理員帳戶的驗證碼。請勿將您專用的全域管理員帳戶沒有 MFA 所提供的額外保護。
  
如需更多資訊，請參閱 [Office 365 部署的多重要素驗證方案](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。
  
若要連線至 Office 365 服務與 MFA 和 PowerShell，請參閱[本文](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>步驟 3。可疑的全域管理員帳戶活動的監視器

Office 365 雲端應用程式安全性可讓您建立原則來通知您在您的訂閱可疑的行為。雲端應用程式安全性內建於 Office 365 E5，但也有提供不同的服務。例如，如果您沒有 Office 365 E5，則可以購買個別的雲端應用程式安全性授權的使用者帳戶的全域管理員、 安全性管理員和規範系統管理員角色指派。
  
如果您的雲端應用程式安全性 Office 365 訂閱中，使用下列步驟：
  
1. 登入 Office 365 入口網站與指定給安全性管理員或規範系統管理員角色的帳戶。
    
2. [在 Office 365 的雲端應用程式安全性開啟](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。
    
3. 檢閱您的[Office 365 雲端應用程式安全性異常偵測原則](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)來通知您的電子郵件的權限的系統管理活動的異常模式。 
    
若要將使用者帳戶新增至安全性管理員角色、 專用的全域管理員帳戶和 MFA[連線至 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3)中，填入使用者帳戶的使用者主體名稱並再執行下列命令： 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

新增使用者帳戶為規範系統管理員角色、 填滿的使用者帳戶的使用者主體名稱，然後執行這些命令：
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>企業組織的其他保護設定

步驟 1-3 使用這些額外的方法來確認您的全域管理員帳戶，並使用它所執行的設定後，會盡可能的安全。
  
### <a name="privileged-access-workstation-paw"></a>權限的存取工作站 （爪）

若要確保執行的高度權限的工作會盡可能的安全，使用爪。爪是只適用於敏感組態工作，例如 Office 365 設定所需的全域管理員帳戶的專用的電腦。此電腦不會使用每日的網際網路瀏覽或電子郵件，因為它更妥善地受到來自網際網路的攻擊和威脅。
  
如需如何設定爪指示，請參閱[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Azure AD 權限的身分識別管理 (PIM)

而不是具有您要永久指派全域管理員角色的全域管理員帳戶，您可以使用 Azure AD PIM 視需要啟用全域管理員角色的隨選、 剛剛-時間工作分派。
  
而不是您要永久系統全域管理員帳戶，會變成合格的系統管理員。全域管理員角色為非作用中，直到某人需求。然後完成的啟用程序新增至全域管理員帳戶的全域管理員角色的預先定義的時間長度。到期時間、 時 PIM 會移除全域管理員帳戶的全域管理員角色。
  
使用 PIM 與此程序可大幅減少的全域管理員帳戶會遭受攻擊和惡意使用者所使用的時間長度。
  
如需詳細資訊，請參閱[設定 Azure AD 權限的身分識別管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。
  
> [!NOTE]
> PIM 隨附 Azure Active Directory Premium P2，也就是包含企業行動性 + 安全性 （EMS） E5，或您可以購買個別授權全域管理員帳戶。 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Office 365 記錄的安全性資訊和事件管理 (SIEM) 軟體

在伺服器上執行的 SIEM 軟體執行即時分析安全性提醒及建立的應用程式及網路硬體的事件。若要允許您要在其分析和報告功能包含 Office 365 安全性提醒及事件的 SIEM 伺服器，將這些 SIEM 系統中整合：
  
- Azure AD
    
    如需詳細資訊，請參閱[Azure 資源到 SIEM 系統整合記錄檔](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。
    
- Office 365 雲端 App 安全性
    
    如需詳細資訊，請參閱 ＜[整合您 SIEM 的伺服器與 Office 365 雲端應用程式安全性](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。
    
## <a name="next-step"></a>下一步

請參閱 ＜ [Security for Office 365 的最佳作法](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。
  

