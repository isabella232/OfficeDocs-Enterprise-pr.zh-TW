---
title: Office 365 開發人員/測試環境的雲端 App 安全性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 摘要： 設定及示範 Office 365 開發人員/測試環境中的 Office 365 雲端應用程式安全性。
ms.openlocfilehash: 089b9771d0600f8c74bc7b4c30ff2a4931c93ae6
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915758"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="1d6fe-103">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="1d6fe-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="1d6fe-104">**摘要：** 設定及示範 Office 365 開發人員/測試環境中的 Office 365 雲端應用程式安全性。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="1d6fe-p101">Office 365 雲端應用程式安全性] 先前稱為 「 Office 365 進階安全性管理，可讓您建立的監控和通知您在 Office 365 訂閱中可疑的活動，讓您可以調查並採取可能的原則修復動作。如需詳細資訊，請參閱[概觀 （英文) 的雲端應用程式 Office 365 的安全性](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="1d6fe-107">使用本文中的指示，您可以啟用並測試您的 Office 365 試用版訂閱中的雲端應用程式安全性。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="1d6fe-108">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="1d6fe-109">階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="1d6fe-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="1d6fe-110">如果您只想要測試雲端應用程式安全性的基本需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="1d6fe-111">如果您想要測試模擬企業中的雲端應用程式安全性，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1d6fe-p102">測試的雲端應用程式安全性不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項可以測試雲端應用程式安全性和代表的典型組織的環境中實驗。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="1d6fe-114">階段 2： 啟用雲端應用程式安全性及之前建立的原則</span><span class="sxs-lookup"><span data-stu-id="1d6fe-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="1d6fe-115">在此程序，您示範才能啟用雲端應用程式安全性、 變更使用者的角色提供沒有電子郵件通知給全域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="1d6fe-116">測試 Office 365 的預設通知行為</span><span class="sxs-lookup"><span data-stu-id="1d6fe-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="1d6fe-117">移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="1d6fe-118">如果您使用輕量型 Office 365 開發/測試環境，請從本機電腦登入。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="1d6fe-119">如果您使用模擬的企業版 Office 365 開發人員/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線到 CLIENT1 虛擬機器，並從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="1d6fe-120">從主要的入口網站頁面中，按一下 [管理]****。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="1d6fe-121">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]****。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="1d6fe-122">按一下 [**使用者 4**帳戶。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="1d6fe-123">**使用者 4** ] 索引標籤上按一下 [**角色**] 列中的 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="1d6fe-p103">在 [**編輯使用者角色**] 頁面上按一下 [**全域管理員**、**替代電子郵件地址**中，輸入**user4@contoso.com**和 [**儲存**。按一下 [**關閉**] 兩次。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="1d6fe-126">選取的應用程式啟動器圖示的左上角，選擇 [**郵件**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="1d6fe-p104">等待 30 分鐘。在通知您變更全域管理員身分的使用者 4 角色中的收件匣中有沒有電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="1d6fe-129">階段 3： 啟用雲端應用程式安全性及建立的原則</span><span class="sxs-lookup"><span data-stu-id="1d6fe-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="1d6fe-p105">在此程序，您可以啟用雲端應用程式安全性並建立新的原則傳送電子郵件通知給您的全域管理員帳戶的使用者帳戶角色中的變更。此程序需要：</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="1d6fe-132">Office 365 試用版訂閱的全域管理員帳戶名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="1d6fe-133">Office 365 試用版訂閱使用者 5 帳戶的名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="1d6fe-134">啟用及設定雲端應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="1d6fe-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="1d6fe-135">移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="1d6fe-p106">按一下 [**系統**] 磚。在 [ **Office 系統管理中心**] 索引標籤上按一下 [**系統中心 > 安全性與規範**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p106">Click the **Admin** tile. On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="1d6fe-138">在左側的導覽窗格中，按一下 [**提醒 > 管理進階提醒**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="1d6fe-139">**進階提醒的管理**] 頁面上按一下 [**開啟 Office 365 雲端應用程式安全性**] 和 [**移至 Office 365 雲端應用程式安全性**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="1d6fe-140">在 [新的**儀表板**] 索引標籤，按一下 [**控制項 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="1d6fe-141">在 [**原則**] 頁面上按一下 [**建立原則**] 和 [**活動原則**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="1d6fe-142">在 [**原則名稱**輸入**系統管理的活動**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="1d6fe-143">在**原則嚴重性**，按一下 [**高**]。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="1d6fe-144">在 [**類別**] 中，按一下 [**權限的帳戶**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="1d6fe-145">在**建立篩選器原則**中**符合下列所有的活動**，按一下 [**系統管理的活動**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="1d6fe-p107">在**警告**中，按一下 [**傳送做為電子郵件通知**。在 [**至**] 輸入您的全域管理員帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="1d6fe-148">在頁面的底端，按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="1d6fe-149">階段 4： 顯示雲端應用程式安全性的巨集指令</span><span class="sxs-lookup"><span data-stu-id="1d6fe-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="1d6fe-150">在此程序，您將示範如何雲端應用程式安全性建立提醒及時使用者 4 讓使用者 5 密碼] 和 [使用者管理管理員傳送給全域系統管理員帳戶的電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="1d6fe-151">示範變更使用者帳戶角色時的電子郵件通知</span><span class="sxs-lookup"><span data-stu-id="1d6fe-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="1d6fe-152">在右上角中按一下 [使用者] 圖示，和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="1d6fe-153">移至 [ [https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-153">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="1d6fe-154">在 Office 365 登入頁面中，按一下 [**使用另一個帳戶**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="1d6fe-155">輸入使用者 4 帳戶名稱和它的密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="1d6fe-156">如果需要變更使用者 4 帳戶密碼，然後再按一下 [**更新密碼，登入**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="1d6fe-157">在 Office 365 入口網站] 頁面上，按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="1d6fe-158">必要時，按一下 [**取消**當系統提示您輸入來更新您的系統管理連絡人資訊。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="1d6fe-159">從主要的入口網站頁面中，按一下 [管理]****。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="1d6fe-160">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]****。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="1d6fe-161">按一下 [**使用者 5**帳戶。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="1d6fe-162">**使用者 5** ] 索引標籤上按一下 [**角色**] 列中的 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="1d6fe-p108">在 [**編輯使用者角色**] 頁面上按一下 **[自訂管理員**、 [**密碼管理員**及**使用者管理管理員**、**替代電子郵件地址**中，輸入**user5@contoso.com**和 [**儲存**。按一下 [**關閉**] 兩次。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="1d6fe-165">按一下右上角中的 [使用者] 圖示] 和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="1d6fe-166">移至 [ [https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-166">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="1d6fe-167">在 [ **Office 365 登入**] 頁面上，按一下 [全域管理員帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="1d6fe-168">輸入密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="1d6fe-169">從主要的入口網站頁面中，按一下 [管理]****。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-169">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="1d6fe-170">按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="1d6fe-171">在左側的導覽窗格中，按一下 [**提醒 > 管理進階提醒**。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="1d6fe-172">按一下 [**管理進階提醒**] 頁面的 [**移至 Office 365 雲端應用程式安全性**]。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="1d6fe-173">在 [新的**儀表板**] 索引標籤，注意到**系統管理活動**的兩個新的提醒。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="1d6fe-p109">從**Microsoft Office Home** ] 索引標籤上，按一下 [**郵件**]。等候長達 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p109">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="1d6fe-p110">您應該會看到兩個新電子郵件訊息收件匣職稱**Microsoft Azure AD 通知服務**。一個訊息會指出使用者 5 帳戶已新增至**密碼管理員**角色與另一則訊息會指出使用者 5 帳戶已新增至**使用者系統管理員**角色 (等於中的使用者管理管理員角色Office 365 系統管理中心）。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p110">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="1d6fe-p111">您現在可以使用此環境中建立新的原則及進一步實驗 Office 365 雲端應用程式安全性。請參閱[備妥可供 Office 365 雲端應用程式安全性](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)的其他設定的文章連結。</span><span class="sxs-lookup"><span data-stu-id="1d6fe-p111">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1d6fe-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d6fe-180">See Also</span></span>

[<span data-ttu-id="1d6fe-181">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="1d6fe-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="1d6fe-182">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="1d6fe-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="1d6fe-183">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="1d6fe-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="1d6fe-184">Office 365 中的雲端應用程式安全性概觀</span><span class="sxs-lookup"><span data-stu-id="1d6fe-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


