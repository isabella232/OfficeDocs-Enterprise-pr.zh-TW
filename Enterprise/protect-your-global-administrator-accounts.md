---
title: 保護您的 Office 365 全域系統管理員帳戶
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
description: 保護全域系統管理員存取您的 Office 365 訂用帳戶包含下列三個步驟。
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573917"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="708a0-103">保護您的 Office 365 全域系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="708a0-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="708a0-104">**摘要：** 保護您的 Office 365 訂閱不根據洩露的全域系統管理員帳戶的攻擊。</span><span class="sxs-lookup"><span data-stu-id="708a0-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="708a0-105">Office 365 訂閱，包括資訊蒐集和網路釣魚攻擊的安全性破壞通常即可危害 Office 365 全域系統管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="708a0-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="708a0-106">在雲端中的安全性是您與 Microsoft 之間的合作關係：</span><span class="sxs-lookup"><span data-stu-id="708a0-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="708a0-107">Microsoft 雲端服務會信任] 與 [安全性 foundation 上建置。</span><span class="sxs-lookup"><span data-stu-id="708a0-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="708a0-108">Microsoft 提供安全性控制和功能，協助您保護您的資料和應用程式。</span><span class="sxs-lookup"><span data-stu-id="708a0-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="708a0-109">您擁有您的資料和身分識別和保護它們，您的內部部署資源的安全性和您控制的雲端元件的安全性的責任。</span><span class="sxs-lookup"><span data-stu-id="708a0-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="708a0-110">Microsoft 提供功能來協助保護您的組織，但它們有效只有當您使用它們。</span><span class="sxs-lookup"><span data-stu-id="708a0-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="708a0-111">如果您不使用它們，您可能容易受到攻擊。</span><span class="sxs-lookup"><span data-stu-id="708a0-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="708a0-112">若要保護您的全域系統管理員帳戶，Microsoft 是以下詳細指示，以協助您：</span><span class="sxs-lookup"><span data-stu-id="708a0-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="708a0-113">建立專用的 Office 365 全域系統管理員帳戶，並使用它們只在需要時。</span><span class="sxs-lookup"><span data-stu-id="708a0-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="708a0-114">設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證。</span><span class="sxs-lookup"><span data-stu-id="708a0-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="708a0-115">啟用及設定 Office 365 雲端 App 安全性來監視可疑的全域系統管理員帳戶活動。</span><span class="sxs-lookup"><span data-stu-id="708a0-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="708a0-116">雖然本文著重於全域系統管理員帳戶，您也應該考慮是否其他帳戶具有廣泛的權限來存取您的訂閱，例如 eDiscovery 系統管理員或安全性或規範中的資料系統管理員帳戶，都必須保護相同的方式。</span><span class="sxs-lookup"><span data-stu-id="708a0-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="708a0-117">步驟 1。</span><span class="sxs-lookup"><span data-stu-id="708a0-117">Step 1.</span></span> <span data-ttu-id="708a0-118">建立專用的 Office 365 全域系統管理員帳戶和使用它們只在需要時</span><span class="sxs-lookup"><span data-stu-id="708a0-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="708a0-119">有相對很少的管理工作，例如將角色指派給需要全域系統管理員權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="708a0-120">因此，而不是使用已指派全域系統管理員角色的日常使用者帳戶，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="708a0-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="708a0-121">判斷已指派全域系統管理員角色的使用者帳戶的集合。</span><span class="sxs-lookup"><span data-stu-id="708a0-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="708a0-122">您可以使用此命令在 Microsoft Azure Active Directory 模組的 Windows PowerShell 命令提示字元來這麼做：</span><span class="sxs-lookup"><span data-stu-id="708a0-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="708a0-123">登入 Office 365 訂閱已被指派全域系統管理員角色的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="708a0-124">建立至少一個與最多五個最多的專用全域系統管理員使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="708a0-125">**使用強式密碼，至少有 12 個字元。**</span><span class="sxs-lookup"><span data-stu-id="708a0-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="708a0-126">如需詳細資訊，請參閱[建立強式密碼](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)。</span><span class="sxs-lookup"><span data-stu-id="708a0-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="708a0-127">將新帳戶的密碼儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="708a0-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="708a0-128">將全域系統管理員角色指派給每個新增專用的全域系統管理員使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="708a0-129">登出 Office 365。</span><span class="sxs-lookup"><span data-stu-id="708a0-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="708a0-130">使用下列其中一個新的專用全域系統管理員使用者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="708a0-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="708a0-131">針對每個現有使用者帳戶具有已被指派全域系統管理員角色從步驟 1:</span><span class="sxs-lookup"><span data-stu-id="708a0-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="708a0-132">移除全域系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="708a0-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="708a0-133">適用於該使用者的工作的功能和責任的帳戶指派系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="708a0-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="708a0-134">如需有關 Office 365 中的各種系統管理員角色的詳細資訊，請參閱 <<c0>關於 Office 365 系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="708a0-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="708a0-135">登出 Office 365。</span><span class="sxs-lookup"><span data-stu-id="708a0-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="708a0-136">應該結果：</span><span class="sxs-lookup"><span data-stu-id="708a0-136">The result should be:</span></span>
  
- <span data-ttu-id="708a0-137">訂閱中擁有的全域系統管理員角色的唯一的使用者帳戶是一組新的專用全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="708a0-138">確認這搭配下列 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="708a0-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="708a0-139">管理您訂閱的所有其他日常使用者帳戶擁有指派的系統管理員角色，這些角色會與他們的工作職責相關聯。</span><span class="sxs-lookup"><span data-stu-id="708a0-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="708a0-140">從 + 這一點時間，您使用登入專用的全域系統管理員帳戶僅適用於需要全域系統管理員權限的工作。</span><span class="sxs-lookup"><span data-stu-id="708a0-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="708a0-141">所有其他 Office 365 系統管理工作必須執行其他系統管理角色指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="708a0-142">是的這需要額外的步驟，為您的日常使用者帳戶登出並使用專用的全域系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="708a0-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="708a0-143">但這只需要完成的有時會針對全域系統管理員的作業。</span><span class="sxs-lookup"><span data-stu-id="708a0-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="708a0-144">請考慮的全域系統管理員帳戶外洩，需要更多的步驟之後，可用來復原您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="708a0-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="708a0-145">步驟 2。</span><span class="sxs-lookup"><span data-stu-id="708a0-145">Step 2.</span></span> <span data-ttu-id="708a0-146">設定專用的 Office 365 全域系統管理員帳戶的多重要素驗證，並使用最強的次要驗證</span><span class="sxs-lookup"><span data-stu-id="708a0-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="708a0-147">您的全域系統管理員帳戶的多重要素驗證 (MFA) 需要以外的帳戶名稱和密碼的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="708a0-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="708a0-148">Office 365 支援下列驗證方法：</span><span class="sxs-lookup"><span data-stu-id="708a0-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="708a0-149">電話</span><span class="sxs-lookup"><span data-stu-id="708a0-149">A phone call</span></span>
    
- <span data-ttu-id="708a0-150">隨機產生的密碼</span><span class="sxs-lookup"><span data-stu-id="708a0-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="708a0-151">智慧卡 (虛擬或實體)</span><span class="sxs-lookup"><span data-stu-id="708a0-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="708a0-152">生物特徵辨識裝置</span><span class="sxs-lookup"><span data-stu-id="708a0-152">A biometric device</span></span>
    
<span data-ttu-id="708a0-153">如果您使用只能在雲端 （雲端身分識別模型） 中儲存的使用者帳戶的小型企業版，請使用下列步驟來設定 MFA 使用電話撥號或傳送到智慧電話的文字郵件驗證碼：</span><span class="sxs-lookup"><span data-stu-id="708a0-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="708a0-154">[啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="708a0-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="708a0-155">若要設定每個[設定的 Office 365 2 雙步驟驗證](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用電話或文字訊息的全域系統管理員帳戶的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="708a0-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="708a0-156">如果您使用 Office 365 混合式身分識別模型較大型組織，您會有更多的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="708a0-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="708a0-157">如果您已經就緒更強的次要驗證方法有安全性基礎結構，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="708a0-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="708a0-158">[啟用 MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。</span><span class="sxs-lookup"><span data-stu-id="708a0-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="708a0-159">若要設定每個[設定 2 雙步驟驗證 Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)專用全域系統管理員帳戶適當的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="708a0-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="708a0-160">如果想要更強的驗證方法的安全性基礎結構不是在位置及運作的 Office 365 MFA，我們強烈建議您在使用 MFA 設定專用的全域系統管理員帳戶使用電話或文字訊息作為過渡期的安全性考量，傳送給智慧型手機的全域管理員帳戶的驗證碼。</span><span class="sxs-lookup"><span data-stu-id="708a0-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="708a0-161">不要讓您專用的全域系統管理員帳戶沒有 MFA 所提供的額外保護。</span><span class="sxs-lookup"><span data-stu-id="708a0-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="708a0-162">如需更多資訊，請參閱 [Office 365 部署的多重要素驗證方案](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)。</span><span class="sxs-lookup"><span data-stu-id="708a0-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="708a0-163">若要連線至 Office 365 服務具有 MFA 和 PowerShell，請參閱[這篇文章](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="708a0-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="708a0-164">步驟 3。</span><span class="sxs-lookup"><span data-stu-id="708a0-164">Step 3.</span></span> <span data-ttu-id="708a0-165">監視可疑的全域系統管理員帳戶活動</span><span class="sxs-lookup"><span data-stu-id="708a0-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="708a0-166">Office 365 雲端 App 安全性可讓您建立原則，以通知您的訂閱中的可疑行為。</span><span class="sxs-lookup"><span data-stu-id="708a0-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="708a0-167">Cloud App Security 內建於 Office 365 E5，但也可做為個別的服務。</span><span class="sxs-lookup"><span data-stu-id="708a0-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="708a0-168">例如，如果您沒有 Office 365 E5，您可以購買個別的 Cloud App Security 授權的使用者帳戶的全域系統管理員、 安全性系統管理員和符合性系統管理員角色指派。</span><span class="sxs-lookup"><span data-stu-id="708a0-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="708a0-169">如果您有雲端 App 安全性中 Office 365 訂閱，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="708a0-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="708a0-170">登入 Microsoft 365 系統管理中心以指派安全性系統管理員或符合性系統管理員角色的帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="708a0-171">[開啟 Office 365 雲端 App 安全性](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)。</span><span class="sxs-lookup"><span data-stu-id="708a0-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="708a0-172">檢閱您的[Office 365 雲端 App 安全性中的異常偵測原則](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)以異常模式的特殊權限的系統管理活動的電子郵件通知您。</span><span class="sxs-lookup"><span data-stu-id="708a0-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="708a0-173">若要新增的安全性管理員角色的使用者帳戶，[連線至 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3)與專用的全域系統管理員帳戶的 MFA，填寫使用者主體名稱的使用者帳戶，並再執行這些命令：</span><span class="sxs-lookup"><span data-stu-id="708a0-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="708a0-174">若要將使用者帳戶新增至 「 合規性管理員 」 角色的使用者帳戶後，使用者主體名稱，填寫，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="708a0-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="708a0-175">對於企業組織的額外保護</span><span class="sxs-lookup"><span data-stu-id="708a0-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="708a0-176">步驟 1-3，使用這些額外的方法，以確保您的全域系統管理員帳戶，並使用它執行的設定之後，會盡可能的安全。</span><span class="sxs-lookup"><span data-stu-id="708a0-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="708a0-177">特殊權限的存取工作站 （爪）</span><span class="sxs-lookup"><span data-stu-id="708a0-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="708a0-178">若要確保高權工作的執行會儘可能安全，使用爪。</span><span class="sxs-lookup"><span data-stu-id="708a0-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="708a0-179">不是爪只適用於機密組態工作，例如需要全域系統管理員帳戶的 Office 365 設定專用的電腦。</span><span class="sxs-lookup"><span data-stu-id="708a0-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="708a0-180">這部電腦不是每日的網際網路瀏覽或電子郵件，因為它更妥善地保護從網際網路攻擊與潛在威脅。</span><span class="sxs-lookup"><span data-stu-id="708a0-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="708a0-181">如需如何設定爪指示，請參閱[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="708a0-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="708a0-182">Azure AD 有權限 Identity Management (PIM)</span><span class="sxs-lookup"><span data-stu-id="708a0-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="708a0-183">而不是您要永久地指派全域系統管理員角色的全域系統管理員帳戶，您可以使用 Azure AD PIM 必要時，啟用全域系統管理員角色的隨選、 剛時間工作分派。</span><span class="sxs-lookup"><span data-stu-id="708a0-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="708a0-184">而不是您要永久的系統管理員的全域系統管理員帳戶，他們會成為合格的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="708a0-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="708a0-185">需要有人之後，才不在作用中的全域系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="708a0-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="708a0-186">然後，您完成新增至全域系統管理員帳戶的全域系統管理員角色，在預定時間的啟用程序。</span><span class="sxs-lookup"><span data-stu-id="708a0-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="708a0-187">當到期時間時，PIM 會移除全域系統管理員帳戶的全域系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="708a0-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="708a0-188">使用 PIM，此程序會大幅降低您的全域系統管理員帳戶容易受到攻擊和惡意使用者所使用的時間量。</span><span class="sxs-lookup"><span data-stu-id="708a0-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="708a0-189">如需詳細資訊，請參閱[設定 Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)。</span><span class="sxs-lookup"><span data-stu-id="708a0-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="708a0-190">PIM 是隨附於 Azure Active Directory 進階版 P2，也就是隨附 Enterprise Mobility + Security (EMS) E5，或者您可以購買個別授權您的全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="708a0-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="708a0-191">Office 365 記錄的安全性資訊和事件管理 (SIEM) 軟體</span><span class="sxs-lookup"><span data-stu-id="708a0-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="708a0-192">在伺服器上執行的 SIEM 軟體執行即時分析安全性提醒及建立的應用程式和網路硬體的事件。</span><span class="sxs-lookup"><span data-stu-id="708a0-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="708a0-193">若要允許 SIEM 伺服器加入 Office 365 安全性提醒及事件在其分析和報告功能，整合這些 SIEM 系統中：</span><span class="sxs-lookup"><span data-stu-id="708a0-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="708a0-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="708a0-194">Azure AD</span></span>
    
    <span data-ttu-id="708a0-195">如需詳細資訊，請參閱 <<c0>整合項目記錄從 Azure 到 SIEM 系統資源。</span><span class="sxs-lookup"><span data-stu-id="708a0-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="708a0-196">Office 365 雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="708a0-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="708a0-197">如需詳細資訊，請參閱[整合 Office 365 雲端 App 安全性與 SIEM 伺服器](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)。</span><span class="sxs-lookup"><span data-stu-id="708a0-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="708a0-198">下一步</span><span class="sxs-lookup"><span data-stu-id="708a0-198">Next step</span></span>

<span data-ttu-id="708a0-199">請參閱[Office 365 的安全性最佳做法](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)。</span><span class="sxs-lookup"><span data-stu-id="708a0-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

