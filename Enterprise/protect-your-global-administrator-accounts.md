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
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897516"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="85bbf-103">保護您的 Office 365 全域管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="85bbf-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="85bbf-104">**摘要：** 保護您的 Office 365 訂閱從全域管理員帳戶的危害為基礎的攻擊。</span><span class="sxs-lookup"><span data-stu-id="85bbf-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="85bbf-p101">Office 365 訂閱包括資訊蒐集和網路釣魚攻擊的安全性缺口通常由影響之下的 Office 365 全域管理員帳戶的認證。在雲端中的安全性是您與 Microsoft 之間合作關係：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="85bbf-p102">Microsoft 雲端服務之內建信任] 與 [安全性的基礎。Microsoft 提供的安全性控制項和功能，可協助您保護您的資料和應用程式。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="85bbf-109">您擁有資料及身分識別和保護其、 您內部部署的資源、 安全性及雲端元件您控制的安全性責任。</span><span class="sxs-lookup"><span data-stu-id="85bbf-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="85bbf-p103">Microsoft 提供的功能，可協助保護您的組織，但他們有效只有當您使用的方法。如果您不使用它們，您可能遭受攻擊。若要保護您的全域管理員帳戶，Microsoft 這裡是以協助您進行詳細指示：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="85bbf-113">建立專用的 Office 365 全域管理員帳戶並只在必要時加以使用。</span><span class="sxs-lookup"><span data-stu-id="85bbf-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="85bbf-114">設定專用的 Office 365 全域管理員帳戶的多重要素驗證及使用的次要驗證最強大的表單。</span><span class="sxs-lookup"><span data-stu-id="85bbf-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="85bbf-115">啟用及設定 Office 365 雲端可疑的全域管理員帳戶活動的監視的應用程式安全性。</span><span class="sxs-lookup"><span data-stu-id="85bbf-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="85bbf-116">雖然本文著重於全域管理員帳戶，您也應該考量是否其他帳戶具備廣泛的權限以存取您的訂閱，例如 eDiscovery 管理員或安全性或規範資料系統管理員帳戶應該保護相同的方式。</span><span class="sxs-lookup"><span data-stu-id="85bbf-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="85bbf-p104">步驟 1。建立專用的 Office 365 全域管理員帳戶及使用它們只有在必要時</span><span class="sxs-lookup"><span data-stu-id="85bbf-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="85bbf-p105">有較少的管理工作，例如指派角色給需要全域系統管理員權限的使用者帳戶。因此，而不是使用已指派的全域管理員角色日常的使用者帳戶，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="85bbf-p106">判斷已指派的全域管理員角色的使用者帳戶的集合。您可以使用下列命令在 Microsoft Azure Active Directory Module for Windows PowerShell 命令提示字元來這麼做：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="85bbf-123">登入您的 Office 365 訂閱以已指派的全域管理員角色的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="85bbf-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="85bbf-p107">建立至少一個和最多五個專用全域管理員的使用者帳戶。**使用強式密碼至少 12 個字元長。** 如需詳細資訊，請參閱[建立強式密碼](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。儲存在安全的位置之新帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="85bbf-128">將全域管理員角色指派給每個新專用的全域系統管理員使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="85bbf-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="85bbf-129">不在 Office 365 登入。</span><span class="sxs-lookup"><span data-stu-id="85bbf-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="85bbf-130">使用其中一個新的專用的全域系統管理員使用者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="85bbf-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="85bbf-131">針對每個現有使用者帳戶有已指派全域管理員角色的步驟 1：</span><span class="sxs-lookup"><span data-stu-id="85bbf-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="85bbf-132">全域管理員角色中移除。</span><span class="sxs-lookup"><span data-stu-id="85bbf-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="85bbf-p108">將系統管理員角色指派給該使用者的工作函數和責任適當的帳戶。如需 Office 365 中的各種管理角色的詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="85bbf-135">不在 Office 365 登入。</span><span class="sxs-lookup"><span data-stu-id="85bbf-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="85bbf-136">結果應該是：</span><span class="sxs-lookup"><span data-stu-id="85bbf-136">The result should be:</span></span>
  
- <span data-ttu-id="85bbf-p109">您的訂閱中具有全域管理員角色的唯一使用者帳戶是一組新的專用的全域管理員帳戶。確認這與下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="85bbf-139">管理您訂閱的所有其他日常使用者帳戶擁有指派的系統管理員角色，這些角色會與他們的工作職責相關聯。</span><span class="sxs-lookup"><span data-stu-id="85bbf-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="85bbf-p110">從 [開始這個可用您登入專用的全域管理員帳戶僅針對需要全域系統管理員權限的作業。所有其他 Office 365 管理必須將其他系統管理角色指派給使用者帳戶來完成。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="85bbf-p111">是，這需要其他步驟以做為日常的使用者帳戶登出及使用專用的全域管理員帳戶登入。但這只需要有時會完成的全域管理員作業。請考慮的復原您的 Office 365 訂閱之後全域管理員帳戶破壞需要更多的步驟。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="85bbf-p112">步驟 2。設定專用的 Office 365 全域管理員帳戶的多重要素驗證及使用的次要驗證最強大的表單</span><span class="sxs-lookup"><span data-stu-id="85bbf-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="85bbf-p113">全域管理員帳戶的多重要素驗證 (MFA) 需要以外的帳戶名稱和密碼的其他資訊。Office 365 支援下列驗證方法：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="85bbf-149">電話</span><span class="sxs-lookup"><span data-stu-id="85bbf-149">A phone call</span></span>
    
- <span data-ttu-id="85bbf-150">隨機產生的密碼</span><span class="sxs-lookup"><span data-stu-id="85bbf-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="85bbf-151">智慧卡 (虛擬或實體)</span><span class="sxs-lookup"><span data-stu-id="85bbf-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="85bbf-152">生物特徵辨識裝置</span><span class="sxs-lookup"><span data-stu-id="85bbf-152">A biometric device</span></span>
    
<span data-ttu-id="85bbf-153">如果您使用的使用者帳戶儲存在雲端 （雲端身分識別模型） 僅適用於小型企業，使用下列步驟來設定 MFA 使用電話或傳送至智慧型手機文字郵件驗證碼：</span><span class="sxs-lookup"><span data-stu-id="85bbf-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="85bbf-154">[啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="85bbf-155">[Set up Office 365 步驟 2 驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)設定每個專用電話通話或文字訊息的全域管理員的帳戶作為驗證方法。</span><span class="sxs-lookup"><span data-stu-id="85bbf-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="85bbf-p114">如果您使用 Office 365 的混合式身分識別模型的較大型組織，您有多個驗證選項。如果您已經備妥更有力的次要驗證方法有安全性基礎結構，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="85bbf-158">[啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="85bbf-159">[Set up Office 365 步驟 2 驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)設定每個專用全域管理員帳戶適當的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="85bbf-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="85bbf-p115">如果想要更有力的驗證方法的安全性基礎結構不是位置和 for Office 365 MFA 運作中，我們強烈建議 MFA 設有專用的全域管理員帳戶使用電話或文字訊息中期安全防護的形式傳送至智慧型手機全域管理員帳戶的驗證碼。請勿將您專用的全域管理員帳戶沒有 MFA 所提供的額外保護。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="85bbf-162">如需更多資訊，請參閱 [Office 365 部署的多重要素驗證方案](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="85bbf-163">若要連線至 Office 365 服務與 MFA 和 PowerShell，請參閱[本文](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="85bbf-p116">步驟 3。可疑的全域管理員帳戶活動的監視器</span><span class="sxs-lookup"><span data-stu-id="85bbf-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="85bbf-p117">Office 365 雲端應用程式安全性可讓您建立原則來通知您在您的訂閱可疑的行為。雲端應用程式安全性內建於 Office 365 E5，但也有提供不同的服務。例如，如果您沒有 Office 365 E5，則可以購買個別的雲端應用程式安全性授權的使用者帳戶的全域管理員、 安全性管理員和規範系統管理員角色指派。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="85bbf-169">如果您的雲端應用程式安全性 Office 365 訂閱中，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="85bbf-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="85bbf-170">登入 Office 365 入口網站與指定給安全性管理員或規範系統管理員角色的帳戶。</span><span class="sxs-lookup"><span data-stu-id="85bbf-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="85bbf-171">[在 Office 365 的雲端應用程式安全性開啟](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="85bbf-172">檢閱您的[Office 365 雲端應用程式安全性異常偵測原則](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)來通知您的電子郵件的權限的系統管理活動的異常模式。</span><span class="sxs-lookup"><span data-stu-id="85bbf-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="85bbf-173">若要將使用者帳戶新增至安全性管理員角色、 專用的全域管理員帳戶和 MFA[連線至 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3)中，填入使用者帳戶的使用者主體名稱並再執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="85bbf-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="85bbf-174">新增使用者帳戶為規範系統管理員角色、 填滿的使用者帳戶的使用者主體名稱，然後執行這些命令：</span><span class="sxs-lookup"><span data-stu-id="85bbf-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="85bbf-175">企業組織的其他保護設定</span><span class="sxs-lookup"><span data-stu-id="85bbf-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="85bbf-176">步驟 1-3 使用這些額外的方法來確認您的全域管理員帳戶，並使用它所執行的設定後，會盡可能的安全。</span><span class="sxs-lookup"><span data-stu-id="85bbf-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="85bbf-177">權限的存取工作站 （爪）</span><span class="sxs-lookup"><span data-stu-id="85bbf-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="85bbf-p118">若要確保執行的高度權限的工作會盡可能的安全，使用爪。爪是只適用於敏感組態工作，例如 Office 365 設定所需的全域管理員帳戶的專用的電腦。此電腦不會使用每日的網際網路瀏覽或電子郵件，因為它更妥善地受到來自網際網路的攻擊和威脅。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="85bbf-181">如需如何設定爪指示，請參閱[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="85bbf-182">Azure AD 權限的身分識別管理 (PIM)</span><span class="sxs-lookup"><span data-stu-id="85bbf-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="85bbf-183">而不是具有您要永久指派全域管理員角色的全域管理員帳戶，您可以使用 Azure AD PIM 視需要啟用全域管理員角色的隨選、 剛剛-時間工作分派。</span><span class="sxs-lookup"><span data-stu-id="85bbf-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="85bbf-p119">而不是您要永久系統全域管理員帳戶，會變成合格的系統管理員。全域管理員角色為非作用中，直到某人需求。然後完成的啟用程序新增至全域管理員帳戶的全域管理員角色的預先定義的時間長度。到期時間、 時 PIM 會移除全域管理員帳戶的全域管理員角色。</span><span class="sxs-lookup"><span data-stu-id="85bbf-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="85bbf-188">使用 PIM 與此程序可大幅減少的全域管理員帳戶會遭受攻擊和惡意使用者所使用的時間長度。</span><span class="sxs-lookup"><span data-stu-id="85bbf-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="85bbf-189">如需詳細資訊，請參閱[設定 Azure AD 權限的身分識別管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="85bbf-190">PIM 隨附 Azure Active Directory Premium P2，也就是包含企業行動性 + 安全性 （EMS） E5，或您可以購買個別授權全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="85bbf-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="85bbf-191">Office 365 記錄的安全性資訊和事件管理 (SIEM) 軟體</span><span class="sxs-lookup"><span data-stu-id="85bbf-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="85bbf-p120">在伺服器上執行的 SIEM 軟體執行即時分析安全性提醒及建立的應用程式及網路硬體的事件。若要允許您要在其分析和報告功能包含 Office 365 安全性提醒及事件的 SIEM 伺服器，將這些 SIEM 系統中整合：</span><span class="sxs-lookup"><span data-stu-id="85bbf-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="85bbf-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="85bbf-194">Azure AD</span></span>
    
    <span data-ttu-id="85bbf-195">如需詳細資訊，請參閱[Azure 資源到 SIEM 系統整合記錄檔](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="85bbf-196">Office 365 雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="85bbf-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="85bbf-197">如需詳細資訊，請參閱 ＜[整合您 SIEM 的伺服器與 Office 365 雲端應用程式安全性](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="85bbf-198">下一步</span><span class="sxs-lookup"><span data-stu-id="85bbf-198">Next step</span></span>

<span data-ttu-id="85bbf-199">請參閱 ＜ [Security for Office 365 的最佳作法](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。</span><span class="sxs-lookup"><span data-stu-id="85bbf-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

