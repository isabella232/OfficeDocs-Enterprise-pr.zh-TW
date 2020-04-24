---
title: 適用於 Office 365 開發人員/測試環境的雲端 App 安全性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 摘要：設定並示範 Office 365 開發/測試環境中的 Office 365 雲端 App 安全性。
ms.openlocfilehash: f76aaa5b13e409f08a4b96714e1f4bdfcc84ecac
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793716"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="0e12e-103">適用於 Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="0e12e-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="0e12e-104">**摘要：** 在您的 Office 365 開發/測試環境中設定並示範 Office 365 雲端 App 安全性。</span><span class="sxs-lookup"><span data-stu-id="0e12e-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0e12e-105">Office 365 Cloud App Security （先前稱為 Office 365 高級安全性管理）可讓您建立原則來監視並通知 Office 365 訂閱中的可疑活動，這樣您就能調查和採取可能的修正動作。</span><span class="sxs-lookup"><span data-stu-id="0e12e-105">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action.</span></span> <span data-ttu-id="0e12e-106">如需詳細資訊，請參閱[Office 365 中的 Cloud App Security 一覽](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="0e12e-106">For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="0e12e-107">透過本文中的指示，您可以啟用並測試您 Office 365 試用訂閱中的 Cloud App Security。</span><span class="sxs-lookup"><span data-stu-id="0e12e-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="0e12e-108">按一下[這裡](https://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="0e12e-108">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="0e12e-109">階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0e12e-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="0e12e-110">如果您只想以輕量的方式測試 Cloud App 安全性，請依照[Office 365 開發/測試環境](office-365-dev-test-environment.md)的階段2和3中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="0e12e-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="0e12e-111">如果您想要在模擬的企業中測試 Cloud App Security，請遵循[您的 Office 365 開發/測試環境 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0e12e-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0e12e-112">測試 Cloud App Security 不需要模擬企業開發/測試環境，其中包括連線到網際網路的模擬內部網路和 Active Directory 網域服務（AD DS）樹系的目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="0e12e-112">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="0e12e-113">這裡是以選項形式提供，可讓您測試 Cloud App 安全性，並在代表一般組織的環境中進行試驗。</span><span class="sxs-lookup"><span data-stu-id="0e12e-113">It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="0e12e-114">階段2：啟用 Cloud App Security 和建立原則之前</span><span class="sxs-lookup"><span data-stu-id="0e12e-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="0e12e-115">在此程式中，您會示範在啟用 Cloud App Security 之前，變更使用者角色並不會提供電子郵件通知給全域管理員。</span><span class="sxs-lookup"><span data-stu-id="0e12e-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="0e12e-116">測試 Office 365 的預設通知行為</span><span class="sxs-lookup"><span data-stu-id="0e12e-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="0e12e-117">移至 Microsoft 365 系統管理中心（[https://admin.microsoft.com](https://admin.microsoft.com)），並以全域系統管理員帳戶登入您的 Office 365 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="0e12e-117">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="0e12e-118">如果您使用輕量型 Office 365 開發/測試環境，請從本機電腦登入。</span><span class="sxs-lookup"><span data-stu-id="0e12e-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="0e12e-119">如果您使用模擬的 enterprise Office 365 開發/測試環境，請使用[Azure 入口網站](https://portal.azure.com)連線至 CLIENT1 虛擬機器，然後從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="0e12e-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="0e12e-120">從主要的入口網站頁面中，按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="0e12e-121">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="0e12e-122">	按一下 [使用者 4]\*\*\*\* 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0e12e-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="0e12e-123">在 [使用者 4]\*\*\*\* 頁面上按一下 [角色] \*\*\*\* 列的 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="0e12e-p103">在 [編輯使用者角色]\*\*\*\* 頁面上按一下 [全域管理員]\*\*\*\*，並在 [備用電子郵件地址]\*\*\*\* 中輸入 **user4@contoso.com**，然後按一下 [儲存]\*\*\*\*。按兩次 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="0e12e-126">	選取左上角的應用程式啟動器圖示 ，然後選擇 [郵件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="0e12e-127">等候 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="0e12e-127">Wait 30 minutes.</span></span> <span data-ttu-id="0e12e-128">請注意，[收件匣] 中沒有電子郵件訊息，通知您使用者4的角色為全域系統管理員所做的變更。</span><span class="sxs-lookup"><span data-stu-id="0e12e-128">Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="0e12e-129">階段3：啟用 Cloud App Security 和 create policy</span><span class="sxs-lookup"><span data-stu-id="0e12e-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="0e12e-130">在此程式中，您可以啟用 Cloud App Security，並建立新的原則，將電子郵件通知傳送給全域管理員帳戶，以瞭解使用者帳戶角色的變更。</span><span class="sxs-lookup"><span data-stu-id="0e12e-130">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles.</span></span> <span data-ttu-id="0e12e-131">此程序需要︰</span><span class="sxs-lookup"><span data-stu-id="0e12e-131">This procedure requires:</span></span>
  
- <span data-ttu-id="0e12e-132">Office 365 試用版訂閱的全域管理員帳戶名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="0e12e-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="0e12e-133">Office 365 試用版訂閱使用者 5 帳戶的名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="0e12e-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="0e12e-134">啟用和設定 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="0e12e-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="0e12e-135">移至 Microsoft 365 系統管理中心（[https://admin.microsoft.com](https://admin.microsoft.com)），並以全域系統管理員帳戶登入您的 Office 365 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="0e12e-135">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="0e12e-136">按一下 [管理]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="0e12e-136">Click the **Admin** tile.</span></span> <span data-ttu-id="0e12e-137">在 [ **Office 系統管理中心**] 索引標籤上，按一下 [系統**管理中心] > 安全性 & 相容性**。</span><span class="sxs-lookup"><span data-stu-id="0e12e-137">On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="0e12e-138">在左功能窗格中，按一下 [**警示 > 管理 [高級提醒**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="0e12e-139">在 [**管理高級提醒**] 頁面上，按一下 [**開啟 Office 365 雲端 app 安全性**]，然後按一下 [**移至 office 365 cloud app security**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="0e12e-140">在 [新增**儀表板**] 索引標籤上，按一下 [**控制 > 原則**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="0e12e-141">在 [**原則**] 頁面上，按一下 [**建立原則**]，然後按一下 [**活動原則**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="0e12e-142">在 [**原則名稱**] 中，輸入「**管理活動**」。</span><span class="sxs-lookup"><span data-stu-id="0e12e-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="0e12e-143">在 [原則嚴重性]\*\*\*\* 中按一下 [高]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="0e12e-144">在 [**類別**] 中，按一下 [**特權帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="0e12e-145">在 **[建立原則的篩選**] 的 [活動] 中，按一下 **[\*\*\*\*管理活動**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="0e12e-p107">在 [警示]\*\*\*\* 中按一下 [透過電子郵件傳送警示]\*\*\*\*。在 [收件者]\*\*\*\* 中輸入全域管理員帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="0e12e-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="0e12e-148">在頁面底部按一下 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="0e12e-149">階段4：顯示 Cloud App Security in action</span><span class="sxs-lookup"><span data-stu-id="0e12e-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="0e12e-150">在此程式中，您將示範 Cloud App Security 如何在使用者4讓使用者5成為密碼和使用者管理管理員時，如何建立提醒，以及如何將電子郵件通知傳送給全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="0e12e-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="0e12e-151">示範變更使用者帳戶角色時的電子郵件通知</span><span class="sxs-lookup"><span data-stu-id="0e12e-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="0e12e-152">按一下右上角的使用者圖示，然後按一下 [登出]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0e12e-153">請移至 [https://www.office.com](https://www.office.com)。</span><span class="sxs-lookup"><span data-stu-id="0e12e-153">Go to [https://www.office.com](https://www.office.com).</span></span>
    
3. <span data-ttu-id="0e12e-154">在 Office 365 登入頁面上按一下 [使用其他帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="0e12e-155">輸入使用者 4 的帳戶名稱與密碼，然後按一下 [登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="0e12e-156">如有需要，變更使用者 4 的帳戶密碼，然後按一下 [更新密碼並登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="0e12e-157">從 Office 365 入口網站頁面，按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="0e12e-158">如有需要，當系統提示您更新管理員連絡資訊時，請按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="0e12e-159">從主要的入口網站頁面中，按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="0e12e-160">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="0e12e-161">按一下 [使用者 5]\*\*\*\* 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0e12e-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="0e12e-162">在 [使用者 5]\*\*\*\* 頁面上按一下 [角色] \*\*\*\* 列的 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="0e12e-p108">在 [編輯使用者角色]\*\*\*\* 頁面上按一下 [自訂的系統管理員]\*\*\*\*，再按一下 [密碼管理員]\*\*\*\* 和 [使用者管理管理員]\*\*\*\*，在 [備用電子郵件地址]\*\*\*\* 中輸入 **user5@contoso.com**，然後按一下 [儲存]\*\*\*\*。按兩次 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="0e12e-165">按一下右上角的使用者圖示，然後按一下 [登出]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="0e12e-166">請移至 [https://www.office.com](https://www.office.com)。</span><span class="sxs-lookup"><span data-stu-id="0e12e-166">Go to [https://www.office.com](https://www.office.com).</span></span>
    
15. <span data-ttu-id="0e12e-167">在 [Office 365 登入]\*\*\*\* 頁面上按一下您的全域系統管理員帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="0e12e-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="0e12e-168">輸入密碼，然後按一下 [登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e12e-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="0e12e-169">在 [Office 365 入口網站] 頁面上，按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-169">From the Office 365 portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="0e12e-170">按一下 [**安全性&amp;與合規性**] 磚。</span><span class="sxs-lookup"><span data-stu-id="0e12e-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="0e12e-171">在左功能窗格中，按一下 [**警示 > 管理 [高級提醒**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="0e12e-172">在 [**管理高級提醒**] 頁面上，按一下 [**移至 Office 365 雲端 App 安全性**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="0e12e-173">在 [新增**儀表板**] 索引標籤上，請注意系統**管理活動**的兩個新警示。</span><span class="sxs-lookup"><span data-stu-id="0e12e-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="0e12e-174">在 [ **Microsoft Office 首頁**] 索引標籤上，按一下 [**郵件**]。</span><span class="sxs-lookup"><span data-stu-id="0e12e-174">From the **Microsoft Office Home** tab, click **Mail**.</span></span> <span data-ttu-id="0e12e-175">等待 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="0e12e-175">Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="0e12e-176">您應該會在 [收件匣] 中看到兩個新的電子郵件，具有標題**Microsoft AZURE AD Notification 服務**。</span><span class="sxs-lookup"><span data-stu-id="0e12e-176">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**.</span></span> <span data-ttu-id="0e12e-177">一封郵件指出使用者5帳戶已新增至**密碼系統管理員**角色，另一則訊息表示使用者5帳戶已新增至**使用者系統管理員**角色（相當於 Microsoft 365 系統管理中心中的使用者管理系統管理員角色）。</span><span class="sxs-lookup"><span data-stu-id="0e12e-177">One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Microsoft 365 admin center).</span></span>
    
<span data-ttu-id="0e12e-178">您現在可以使用此環境建立新的原則，並以 Office 365 雲端 App 安全性進一步實驗。</span><span class="sxs-lookup"><span data-stu-id="0e12e-178">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security.</span></span> <span data-ttu-id="0e12e-179">如需其他設定文章的連結，請參閱[取得 Office 365 Cloud App 安全性的準備](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)。</span><span class="sxs-lookup"><span data-stu-id="0e12e-179">See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0e12e-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e12e-180">See Also</span></span>

[<span data-ttu-id="0e12e-181">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="0e12e-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0e12e-182">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0e12e-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0e12e-183">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="0e12e-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

[<span data-ttu-id="0e12e-184">Office 365 中 Cloud App 安全性的概述</span><span class="sxs-lookup"><span data-stu-id="0e12e-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


