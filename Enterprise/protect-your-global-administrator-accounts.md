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
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="cba55-103">保護您的 Office 365 全域系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="cba55-103">Protect your Office 365 global administrator accounts</span></span>

<span data-ttu-id="cba55-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="cba55-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="cba55-105">Office 365 訂閱，包括資訊蒐集和網路釣魚攻擊的安全性破壞通常即可危害 Office 365 全域系統管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="cba55-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="cba55-106">在雲端中的安全性是您與 Microsoft 之間的合作關係：</span><span class="sxs-lookup"><span data-stu-id="cba55-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="cba55-107">Microsoft 雲端服務會信任] 與 [安全性 foundation 上建置。</span><span class="sxs-lookup"><span data-stu-id="cba55-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="cba55-108">Microsoft 提供安全性控制和功能，協助您保護您的資料和應用程式。</span><span class="sxs-lookup"><span data-stu-id="cba55-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="cba55-109">您擁有您的資料和身分識別和保護它們，您的內部部署資源的安全性和您控制的雲端元件的安全性的責任。</span><span class="sxs-lookup"><span data-stu-id="cba55-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="cba55-110">Microsoft 提供功能來協助保護您的組織，但它們有效只有當您使用它們。</span><span class="sxs-lookup"><span data-stu-id="cba55-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="cba55-111">如果您不使用它們，您可能容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="cba55-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="cba55-112">若要保護您的全域系統管理員帳戶，Microsoft 是以下詳細指示，以協助您：</span><span class="sxs-lookup"><span data-stu-id="cba55-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="cba55-113">建立專用的 Office 365 全域系統管理員帳戶，並使用它們只在需要時。</span><span class="sxs-lookup"><span data-stu-id="cba55-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="cba55-114">設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證。</span><span class="sxs-lookup"><span data-stu-id="cba55-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
> [!NOTE]
> <span data-ttu-id="cba55-115">雖然本文著重於全域系統管理員帳戶，您應該考慮是否其他帳戶具有廣泛的權限來存取您的訂閱，例如 eDiscovery 管理員 」 或 「 安全性 」 或 「 合規性管理員中的資料帳戶，都必須保護相同的方式。</span><span class="sxs-lookup"><span data-stu-id="cba55-115">Although this article is focused on global administrator accounts, you should consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="cba55-116">步驟 1。</span><span class="sxs-lookup"><span data-stu-id="cba55-116">Step 1.</span></span> <span data-ttu-id="cba55-117">建立專用的 Office 365 全域系統管理員帳戶和使用它們只在需要時</span><span class="sxs-lookup"><span data-stu-id="cba55-117">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="cba55-118">有相對很少的管理工作，例如將角色指派給需要全域系統管理員權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-118">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="cba55-119">因此，而不是使用已指派全域系統管理員角色的日常使用者帳戶，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cba55-119">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="cba55-120">判斷已指派全域系統管理員角色的使用者帳戶的集合。</span><span class="sxs-lookup"><span data-stu-id="cba55-120">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="cba55-121">您可以利用 Graph 命令 PowerShell 的 Azure Active (Azure AD) Directory 來進行此作業：</span><span class="sxs-lookup"><span data-stu-id="cba55-121">You can do this with Azure Active (Azure AD) Directory PowerShell for Graph  command:</span></span>
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. <span data-ttu-id="cba55-122">登入 Office 365 訂閱已被指派全域系統管理員角色的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-122">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="cba55-123">建立至少一個與最多五個最多的專用全域系統管理員使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-123">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="cba55-124">**使用強式密碼，至少有 12 個字元。**</span><span class="sxs-lookup"><span data-stu-id="cba55-124">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="cba55-125">如需詳細資訊，請參閱[建立強式密碼](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。</span><span class="sxs-lookup"><span data-stu-id="cba55-125">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="cba55-126">將新帳戶的密碼儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="cba55-126">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="cba55-127">將全域系統管理員角色指派給每個新增專用的全域系統管理員使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-127">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="cba55-128">登出 Office 365。</span><span class="sxs-lookup"><span data-stu-id="cba55-128">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="cba55-129">使用下列其中一個新的專用全域系統管理員使用者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="cba55-129">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="cba55-130">針對每個現有使用者帳戶具有已被指派全域系統管理員角色從步驟 1:</span><span class="sxs-lookup"><span data-stu-id="cba55-130">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="cba55-131">移除全域系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="cba55-131">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="cba55-132">適用於該使用者的工作的功能和責任的帳戶指派系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="cba55-132">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="cba55-133">如需各種 Office 365 中的系統管理員角色的詳細資訊，請參閱[關於系統管理員角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="cba55-133">For more information about various admin roles in Office 365, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span></span>
    
8. <span data-ttu-id="cba55-134">登出 Office 365。</span><span class="sxs-lookup"><span data-stu-id="cba55-134">Sign out of Office 365.</span></span>
    
<span data-ttu-id="cba55-135">應該結果：</span><span class="sxs-lookup"><span data-stu-id="cba55-135">The result should be:</span></span>
  
- <span data-ttu-id="cba55-136">您的訂閱中唯一擁有全域系統管理員角色的使用者帳戶，就是新建立的一組專用全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-136">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="cba55-137">確認這搭配下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="cba55-137">Verify this with the following PowerShell command:</span></span>
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- <span data-ttu-id="cba55-138">管理您訂閱的所有其他日常使用者帳戶擁有指派的系統管理員角色，這些角色會與他們的工作職責相關聯。</span><span class="sxs-lookup"><span data-stu-id="cba55-138">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="cba55-139">從 + 這一點時間，您使用登入專用的全域系統管理員帳戶僅適用於需要全域系統管理員權限的工作。</span><span class="sxs-lookup"><span data-stu-id="cba55-139">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="cba55-140">所有其他 Office 365 系統管理工作必須執行其他系統管理角色指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-140">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cba55-141">這需要額外的步驟，為您的日常使用者帳戶登出並使用專用的全域系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="cba55-141">This does require additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="cba55-142">但這只需要完成的有時會針對全域系統管理員的作業。</span><span class="sxs-lookup"><span data-stu-id="cba55-142">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="cba55-143">請考慮的全域系統管理員帳戶外洩，需要更多的步驟之後，可用來復原您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="cba55-143">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span>
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="cba55-144">步驟 2。</span><span class="sxs-lookup"><span data-stu-id="cba55-144">Step 2.</span></span> <span data-ttu-id="cba55-145">設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證</span><span class="sxs-lookup"><span data-stu-id="cba55-145">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="cba55-146">多重要素驗證 (MFA) 需要以外的帳戶名稱和密碼的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="cba55-146">Multi-factor authentication (MFA) requires additional information beyond the account name and password.</span></span> <span data-ttu-id="cba55-147">Office 365 支援下列驗證方法：</span><span class="sxs-lookup"><span data-stu-id="cba55-147">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="cba55-148">電話</span><span class="sxs-lookup"><span data-stu-id="cba55-148">A phone call</span></span>
    
- <span data-ttu-id="cba55-149">隨機產生的密碼</span><span class="sxs-lookup"><span data-stu-id="cba55-149">A randomly generated pass code</span></span>
    
- <span data-ttu-id="cba55-150">智慧卡 (虛擬或實體)</span><span class="sxs-lookup"><span data-stu-id="cba55-150">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="cba55-151">生物特徵辨識裝置</span><span class="sxs-lookup"><span data-stu-id="cba55-151">A biometric device</span></span>
    
<span data-ttu-id="cba55-152">如果您使用只能在雲端 （僅限雲端身分識別模型） 中儲存的使用者帳戶的小型企業版，請，使用下列步驟來設定 MFA 使用電話撥號或傳送到智慧電話的文字郵件驗證碼：</span><span class="sxs-lookup"><span data-stu-id="cba55-152">If you are a small business that is using user accounts stored only in the cloud (the cloud-only identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="cba55-153">[設定 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。</span><span class="sxs-lookup"><span data-stu-id="cba55-153">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="cba55-154">若要設定每個[設定的 Office 365 2 雙步驟驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用電話或文字訊息的全域系統管理員帳戶的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="cba55-154">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="cba55-155">如果您使用 Office 365 混合式身分識別模型較大型組織，您會有更多的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="cba55-155">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="cba55-156">如果您已經就緒更強的次要驗證方法有安全性基礎結構，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cba55-156">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="cba55-157">[設定 MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)。</span><span class="sxs-lookup"><span data-stu-id="cba55-157">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="cba55-158">若要設定每個[設定 2 雙步驟驗證 Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用全域系統管理員帳戶適當的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="cba55-158">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="cba55-159">如果想要更強的驗證方法的安全性基礎結構不是在位置及運作的 Office 365 MFA，我們強烈建議您在使用 MFA 設定專用的全域系統管理員帳戶使用電話或文字訊息作為過渡期的安全性考量，傳送給智慧型手機的全域管理員帳戶的驗證碼。</span><span class="sxs-lookup"><span data-stu-id="cba55-159">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="cba55-160">不要讓您專用的全域系統管理員帳戶沒有 MFA 所提供的額外保護。</span><span class="sxs-lookup"><span data-stu-id="cba55-160">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="cba55-161">如需更多資訊，請參閱 [Office 365 部署的多重要素驗證方案](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)。</span><span class="sxs-lookup"><span data-stu-id="cba55-161">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span></span>
  
<span data-ttu-id="cba55-162">若要連線至 Office 365 服務具有 MFA 和 PowerShell，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="cba55-162">To connect to Office 365 services with MFA and PowerShell, see these articles:</span></span>

- [<span data-ttu-id="cba55-163">Office 365 PowerShell 的使用者帳戶、 群組和授權</span><span class="sxs-lookup"><span data-stu-id="cba55-163">Office 365 PowerShell for user accounts, groups, and licenses</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [<span data-ttu-id="cba55-164">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="cba55-164">Exchange Online</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [<span data-ttu-id="cba55-165">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cba55-165">SharePoint Online</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [<span data-ttu-id="cba55-166">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="cba55-166">Skype for Business Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="cba55-167">對於企業組織的額外保護</span><span class="sxs-lookup"><span data-stu-id="cba55-167">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="cba55-168">步驟 1 和 2 中，使用這些額外的方法，以確保您的全域系統管理員帳戶，並使用它執行的設定之後，會盡可能的安全。</span><span class="sxs-lookup"><span data-stu-id="cba55-168">After steps 1 and 2, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation"></a><span data-ttu-id="cba55-169">特殊權限的存取工作站</span><span class="sxs-lookup"><span data-stu-id="cba55-169">Privileged access workstation</span></span>

<span data-ttu-id="cba55-170">若要確保高權工作的執行會儘可能安全，使用的特殊權限的存取工作站 （爪）。</span><span class="sxs-lookup"><span data-stu-id="cba55-170">To ensure that the execution of highly privileged tasks is as secure as possible, use a privileged access workstation (PAW).</span></span> <span data-ttu-id="cba55-171">不是爪只適用於機密組態工作，例如需要全域系統管理員帳戶的 Office 365 設定專用的電腦。</span><span class="sxs-lookup"><span data-stu-id="cba55-171">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="cba55-172">這部電腦不是每日的網際網路瀏覽或電子郵件，因為它更妥善地保護從網際網路攻擊與潛在威脅。</span><span class="sxs-lookup"><span data-stu-id="cba55-172">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="cba55-173">如需如何設定爪指示，請參閱[https://aka.ms/cyberpaw](https://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="cba55-173">For instructions on how to set up a PAW, see [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management"></a><span data-ttu-id="cba55-174">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="cba55-174">Azure AD Privileged Identity Management</span></span>

<span data-ttu-id="cba55-175">而不是您要永久地指派全域系統管理員角色的全域系統管理員帳戶，您可以使用 Azure AD Privileged Identity Management (PIM) 時，它會啟用全域系統管理員角色的隨選、 剛時間指派所需。</span><span class="sxs-lookup"><span data-stu-id="cba55-175">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD Privileged Identity Management (PIM) to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="cba55-176">而不是您要永久的系統管理員的全域系統管理員帳戶，他們會成為合格的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="cba55-176">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="cba55-177">需要有人之後，才不在作用中的全域系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="cba55-177">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="cba55-178">然後，您完成新增至全域系統管理員帳戶的全域系統管理員角色，在預定時間的啟用程序。</span><span class="sxs-lookup"><span data-stu-id="cba55-178">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="cba55-179">當到期時間時，PIM 會移除全域系統管理員帳戶的全域系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="cba55-179">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="cba55-180">使用 PIM，此程序會大幅降低您的全域系統管理員帳戶容易受到攻擊和惡意使用者所使用的時間量。</span><span class="sxs-lookup"><span data-stu-id="cba55-180">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="cba55-181">如需詳細資訊，請參閱[Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。</span><span class="sxs-lookup"><span data-stu-id="cba55-181">For more information, see [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="cba55-182">PIM 是隨附於 Azure AD Premium P2，隨附於 Microsoft 365 企業版 E5 或 Enterprise Mobility + Security (EMS) E5，或者您可以購買個別授權您的全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="cba55-182">PIM is available with Azure AD Premium P2, which is included with Microsoft 365 Enterprise E5 or Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="cba55-183">Office 365 記錄的安全性資訊和事件管理 (SIEM) 軟體</span><span class="sxs-lookup"><span data-stu-id="cba55-183">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="cba55-184">在伺服器上執行的 SIEM 軟體執行即時分析安全性提醒及建立的應用程式和網路硬體的事件。</span><span class="sxs-lookup"><span data-stu-id="cba55-184">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="cba55-185">若要允許 SIEM 伺服器加入 Office 365 安全性提醒及事件在其分析和報告功能，將 Azure AD 整合到您 SEIM。</span><span class="sxs-lookup"><span data-stu-id="cba55-185">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate Azure AD into you SEIM.</span></span> <span data-ttu-id="cba55-186">請參閱[Azure 記錄整合的簡介](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)。</span><span class="sxs-lookup"><span data-stu-id="cba55-186">See [Introduction to Azure Log Integration](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="cba55-187">下一步</span><span class="sxs-lookup"><span data-stu-id="cba55-187">Next step</span></span>

<span data-ttu-id="cba55-188">如果您要設定 Office 365 訂用帳戶的身分識別，請參閱：</span><span class="sxs-lookup"><span data-stu-id="cba55-188">If you're setting up identity for your Office 365 subscription, see:</span></span>

- <span data-ttu-id="cba55-189">[僅限雲端身分識別](cloud-only-identities.md)如果您正在使用的僅限雲端身分識別</span><span class="sxs-lookup"><span data-stu-id="cba55-189">[Cloud-only identities](cloud-only-identities.md) if you're using cloud-only identity</span></span>
- <span data-ttu-id="cba55-190">[準備目錄同步處理](prepare-for-directory-synchronization.md)如果您使用混合式身分識別</span><span class="sxs-lookup"><span data-stu-id="cba55-190">[Prepare for directory synchronization](prepare-for-directory-synchronization.md) if you're using hybrid identity</span></span>

  
## <a name="see-also"></a><span data-ttu-id="cba55-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cba55-191">See also</span></span>

<span data-ttu-id="cba55-192">[Office 365 安全性藍圖](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="cba55-192">[Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span>
