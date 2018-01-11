---
title: "註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "摘要： 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。"
ms.openlocfilehash: 71d04b0d2a59683ff09ad4256ed8fc82e89e876a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="4147b-103">註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="4147b-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="4147b-104">**摘要：**使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。</span><span class="sxs-lookup"><span data-stu-id="4147b-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="4147b-p101">Microsoft Enterprise 行動性套件 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="4147b-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="4147b-p102">如果您需要在裝置層級套用安全性作業，您必須在 Microsoft Intune 中註冊裝置。裝置註冊不只可協助您管理公司擁有的裝置，也可管理個人 (BYOD) 及共用的裝置 (視您組織的法規政策而定)。</span><span class="sxs-lookup"><span data-stu-id="4147b-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="4147b-109">遵循本文中提供的指示，您將能夠註冊並在 Microsoft 365 開發人員/測試環境中測試 iOS 及 Android 裝置的基本的行動裝置管理功能。</span><span class="sxs-lookup"><span data-stu-id="4147b-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="4147b-110">階段 1： 建立 Microsoft 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="4147b-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="4147b-111">遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4147b-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="4147b-112">階段 2：自訂 Microsoft Intune 公司入口網站應用程式</span><span class="sxs-lookup"><span data-stu-id="4147b-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="4147b-113">使用以下步驟自訂您虛構公司的 Microsoft Intune 公司入口網站：</span><span class="sxs-lookup"><span data-stu-id="4147b-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="4147b-114">在 [新增] 索引標籤上開啟 Microsoft Intune 管理主控台 ([https://manage.microsoft.com](https://manage.microsoft.com))。</span><span class="sxs-lookup"><span data-stu-id="4147b-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="4147b-115">在功能窗格] 中按一下 [**管理**和在 [**管理**] 窗格中 [**行動裝置管理**。</span><span class="sxs-lookup"><span data-stu-id="4147b-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="4147b-p103">在 [**工作**] 清單中選取 [**設定行動裝置管理授權**。請確定它設為**Microsoft Intune**。</span><span class="sxs-lookup"><span data-stu-id="4147b-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="4147b-118">在 [**管理**] 窗格中，按一下 [**公司入口網站**。</span><span class="sxs-lookup"><span data-stu-id="4147b-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="4147b-119">在**公司入口網站**] 窗格中，設定下列設定：</span><span class="sxs-lookup"><span data-stu-id="4147b-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="4147b-120">公司名稱：\<虛構公司名稱 ></span><span class="sxs-lookup"><span data-stu-id="4147b-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="4147b-121">IT 部門連絡人名稱： **User5**</span><span class="sxs-lookup"><span data-stu-id="4147b-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="4147b-122">IT 部門電話號碼： **555-1234**</span><span class="sxs-lookup"><span data-stu-id="4147b-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="4147b-123">IT 部門電子郵件地址： **User5 @**\<虛構的組織名稱 > **。 onmicrosoft.com** （User5 帳戶的電子郵件地址）</span><span class="sxs-lookup"><span data-stu-id="4147b-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="4147b-124">在**自訂**、 選取**佈景主題**色彩的**綠色**。</span><span class="sxs-lookup"><span data-stu-id="4147b-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="4147b-125">按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-125">Click **Save**.</span></span>
    
<span data-ttu-id="4147b-126">下一步，您將安裝 Microsoft Intune 公司入口網站應用程式並註冊 iOS 或 Android 裝置，然後從 Microsoft Intune 管理主控台測試基本管理功能。</span><span class="sxs-lookup"><span data-stu-id="4147b-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="4147b-127">階段 3 (僅適用於 iOS 裝置)：註冊並管理 iOS 裝置</span><span class="sxs-lookup"><span data-stu-id="4147b-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="4147b-128">若要註冊 iOS 裝置以透過 Intune 進行管理，您需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="4147b-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="4147b-129">Apple iPad 或 iPhone 等 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="4147b-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="4147b-130">IOS 裝置密碼的知識。</span><span class="sxs-lookup"><span data-stu-id="4147b-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="4147b-p104">Apple 識別碼 （帳戶名稱和密碼）。如果您已經沒有，前往[Apple 識別碼網站](https://appleid.apple.com/#!&amp;page=signin)並按一下 [**建立 Apple 識別碼**。建立 Apple 識別碼對應至您的 Office 365 訂閱的全域管理員帳戶。安全的位置記錄您的新 Apple ID 帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="4147b-p105">需要 Apple Push Notification Service (APNs) 的憑證，Intune 才能管理 iOS 和 Mac 裝置。一旦將憑證新增到 Intune，使用者就可以安裝 Microsoft Intune 公司入口網站應用程式來註冊他們的裝置，或管理員可以為公司擁有的 iOS 裝置設定管理作業。</span><span class="sxs-lookup"><span data-stu-id="4147b-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="4147b-p106">您將需要憑證簽署要求檔案來要求 Apple Push Certificates 入口網站的信任關係憑證。若要取得憑證簽署要求檔案：</span><span class="sxs-lookup"><span data-stu-id="4147b-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="4147b-139">在 Microsoft Intune 管理主控台中，按一下 [功能窗格中的**管理**。</span><span class="sxs-lookup"><span data-stu-id="4147b-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="4147b-140">在 [**管理**] 窗格中，開啟 [**行動裝置管理 > iOS 和 Mac OS X**，然後按一下 [**上傳 APNs 憑證**中**的工作**。</span><span class="sxs-lookup"><span data-stu-id="4147b-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="4147b-p107">在**APNs 憑證上傳**] 窗格中，按一下 [**下載 APNs 憑證要求**。儲存的憑證簽署要求 (.csr) 檔案在本機名稱**開發人員測試**。</span><span class="sxs-lookup"><span data-stu-id="4147b-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="4147b-143">若要取得 Apple Push Notification Service 憑證：</span><span class="sxs-lookup"><span data-stu-id="4147b-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="4147b-144">開啟 [新增] 索引標籤、 移至 [ [Apple 推入憑證入口網站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)，並使用 Apple 識別碼登入</span><span class="sxs-lookup"><span data-stu-id="4147b-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="4147b-145">在 [**開始**] 頁面上，按一下 [**建立憑證**。</span><span class="sxs-lookup"><span data-stu-id="4147b-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="4147b-146">在 [**使用**] 頁面上選取 [**我已閱讀並同意這些條款和條件**] 和 [**接受**。</span><span class="sxs-lookup"><span data-stu-id="4147b-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="4147b-p108">在 [**建立新的推入憑證**] 頁面上按一下 [**瀏覽**和選取在前一步驟中儲存的**開發人員 test.csr**檔案和 [**上傳**。出現提示時若要開啟 [json 檔案，請將它儲存到相同的開發人員 test.csr 檔案儲存所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4147b-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="4147b-149">開啟[Apple 推入憑證入口網站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)中的不同的索引標籤及**協力廠商伺服器的憑證**，按一下 [**下載**。</span><span class="sxs-lookup"><span data-stu-id="4147b-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="4147b-p109">出現提示時若要開啟 [.pem 檔案，請將其儲存至相同的開發人員 test.csr 檔案儲存所在的資料夾名稱**test.pem 開發人員**使用。這是 APNs 憑證。</span><span class="sxs-lookup"><span data-stu-id="4147b-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="4147b-152">若要將 APNs 憑證上傳到 Intune：</span><span class="sxs-lookup"><span data-stu-id="4147b-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="4147b-153">在 [Microsoft Intune 管理主控台] 索引標籤上**APNs 憑證上傳**] 頁面上按一下 [ **APNs 憑證上傳**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="4147b-154">按一下 [**瀏覽**並指定**開發 test.pem**檔案。</span><span class="sxs-lookup"><span data-stu-id="4147b-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="4147b-p110">按一下 [**開啟]**、 輸入 Apple ID 帳戶名稱，和 [**上傳**。您應該會看到**已準備好用於註冊**郵件**iOS 與 MaxOS X 行動裝置管理安裝**] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="4147b-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="4147b-157">安裝 APNs 憑證後，Intune 現在可以透過將原則推播至註冊的行動裝置來註冊並管理 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="4147b-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="4147b-158">若要下載 Microsoft Intune 公司入口網站應用程式並註冊 iOS 裝置︰</span><span class="sxs-lookup"><span data-stu-id="4147b-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="4147b-159">在您的 iOS 裝置中使用 Apple ID 登入。</span><span class="sxs-lookup"><span data-stu-id="4147b-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="4147b-160">開啟 [ **Apple 市集**應用程式]。</span><span class="sxs-lookup"><span data-stu-id="4147b-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="4147b-161">在 [搜尋] 方塊中輸入**intune**並點選 [ **Microsoft Intune 的公司入口網站**，則**取得**，然後**安裝**。</span><span class="sxs-lookup"><span data-stu-id="4147b-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="4147b-162">它會在安裝之後，點選 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="4147b-163">在 [ **Intune 的公司入口網站**] 畫面上使用登入您的 Office 365 全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="4147b-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="4147b-164">在**公司 Access 安裝**] 畫面上，點選 [**開始**，然後再點選 [**繼續]**兩次。</span><span class="sxs-lookup"><span data-stu-id="4147b-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="4147b-165">在**接下來是什麼？**螢幕、 點選**註冊**。</span><span class="sxs-lookup"><span data-stu-id="4147b-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="4147b-166">在**啟動裝置管理員吗？**螢幕、 點選 [**啟動**。</span><span class="sxs-lookup"><span data-stu-id="4147b-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="4147b-167">在 [**管理設定檔**] 畫面中，點選 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="4147b-168">在 [**輸入密碼**，輸入您 iOS 裝置密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="4147b-169">在**接下來是什麼**] 畫面中，點選 [**註冊**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="4147b-170">在**安裝設定檔**，點選 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="4147b-171">點選 [**警告**] 頁面的 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="4147b-172">在 [**遠端管理**，點選 [**信任**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="4147b-173">點選 [完成註冊程序的 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="4147b-174">當系統提示時**開啟"Comp Portal"中的此頁面？**，點選 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="4147b-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="4147b-175">在**公司 Access 安裝**] 畫面上，點選 [**開始**，然後再點選 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="4147b-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="4147b-176">在 Microsoft Intune 公司入口網站應用程式的主畫面中，您應該會看到︰</span><span class="sxs-lookup"><span data-stu-id="4147b-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="4147b-177">綠色的橫幅。</span><span class="sxs-lookup"><span data-stu-id="4147b-177">A green banner.</span></span>
    
  - <span data-ttu-id="4147b-178">您的虛擬公司名稱會在左上方。</span><span class="sxs-lookup"><span data-stu-id="4147b-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="4147b-179">您的 iOS 裝置名稱列在**「 我的裝置**。</span><span class="sxs-lookup"><span data-stu-id="4147b-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="4147b-180">在 [**服務台**] 區段中，按一下 [ **User5**與**555-1234年**與**連絡人電子郵件**] 按鈕的電話號碼的**連絡人名稱**。</span><span class="sxs-lookup"><span data-stu-id="4147b-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="4147b-p111">Microsoft Intune 提供遠端鎖定和密碼重設功能。如果有人遺失他們的裝置，您可以從遠端鎖定裝置。如果有人忘記他們的密碼，您可以從遠端移除密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="4147b-184">若要從遠端鎖定 iOS 裝置︰</span><span class="sxs-lookup"><span data-stu-id="4147b-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="4147b-185">從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中，按一下左方導覽中的 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="4147b-186">在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。</span><span class="sxs-lookup"><span data-stu-id="4147b-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="4147b-187">在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4147b-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="4147b-188">在裝置清單中，按一下您的 iOS 裝置。 </span><span class="sxs-lookup"><span data-stu-id="4147b-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="4147b-189">透過您的 iOS 裝置，確定裝置位於主畫面。 </span><span class="sxs-lookup"><span data-stu-id="4147b-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="4147b-p112">從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。觀看 iOS 裝置將它會切換至 [鎖定] 畫面。</span><span class="sxs-lookup"><span data-stu-id="4147b-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="4147b-192">若要移除密碼︰</span><span class="sxs-lookup"><span data-stu-id="4147b-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="4147b-193">從系統管理電腦中**的所有直接受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4147b-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="4147b-p113">在清單中，按一下 [iOS 裝置]。在工作列上，按一下 [**遠端工作 > 密碼重設**。靜待一分鐘。</span><span class="sxs-lookup"><span data-stu-id="4147b-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="4147b-p114">從您的 iOS 裝置解除鎖定其並注意到已不再密碼。若要變更密碼後，移至 [**設定**]，然後**密碼**。</span><span class="sxs-lookup"><span data-stu-id="4147b-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="4147b-199">階段 3 (僅適用於 Android 裝置)：註冊並管理 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="4147b-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="4147b-200">若要註冊 Android 裝置以透過 Intune 進行管理，您需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="4147b-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="4147b-201">Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="4147b-201">An Android device.</span></span>
    
- <span data-ttu-id="4147b-202">裝置密碼的知識。</span><span class="sxs-lookup"><span data-stu-id="4147b-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="4147b-203">若要下載 Intune 公司入口網站應用程式並註冊 Android 裝置︰</span><span class="sxs-lookup"><span data-stu-id="4147b-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="4147b-204">從您 Android 裝置移至**Google 播放存放區**中，然後再點選 [**開始**。</span><span class="sxs-lookup"><span data-stu-id="4147b-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="4147b-205">在 [搜尋] 方塊中輸入**intune**並再點選 [搜尋結果中的**intune 的公司入口網站**。</span><span class="sxs-lookup"><span data-stu-id="4147b-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="4147b-206">點選 [ **Intune 的公司入口網站**項目，然後點選 [**安裝**。</span><span class="sxs-lookup"><span data-stu-id="4147b-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="4147b-207">點選**的完整帳戶設定**] 畫面上的 [**繼續**，然後按一下 [**略過**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="4147b-p115">在**Intune 的公司入口網站**，點選 [**接受**]。應用程式安裝中。</span><span class="sxs-lookup"><span data-stu-id="4147b-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="4147b-210">點選 [**開啟**]，然後點選 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="4147b-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="4147b-211">在 [ **Intune 的公司入口網站**] 畫面上使用登入您的 Office 365 全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="4147b-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="4147b-212">在**公司 Access 安裝**] 畫面上，點選 [**開始**，然後**繼續**按兩次。</span><span class="sxs-lookup"><span data-stu-id="4147b-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="4147b-213">在**接下來是什麼？**螢幕、 點選**註冊**。</span><span class="sxs-lookup"><span data-stu-id="4147b-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="4147b-214">在**啟動裝置管理員吗？**螢幕、 點選**Activate。**</span><span class="sxs-lookup"><span data-stu-id="4147b-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="4147b-p116">在**具有隱私權原則**] 畫面上，選取 [**我確認**，然後點選 [**確認**。等候註冊程序來完成。</span><span class="sxs-lookup"><span data-stu-id="4147b-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="4147b-217">在**公司 Access 安裝**] 畫面上，點選 [**繼續**，然後再點選 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="4147b-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="4147b-218">在 Microsoft Intune 公司入口網站應用程式的主畫面中，您應該會在左上方看到綠色的橫幅和您在虛構公司的名稱。</span><span class="sxs-lookup"><span data-stu-id="4147b-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="4147b-p117">點選 [**我的裝置**。您應該會看到您 Android 裝置的名稱清單中。</span><span class="sxs-lookup"><span data-stu-id="4147b-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="4147b-p118">點選**連絡人 IT**。您應該會看到**555-1234年**、**連絡電子郵件**] 按鈕的電話號碼和 IT 連絡人的**User5**。</span><span class="sxs-lookup"><span data-stu-id="4147b-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="4147b-p119">Microsoft Intune 提供遠端鎖定和密碼重設功能。如果有人遺失他們的裝置，您可以從遠端鎖定裝置。如果有人忘記他們的密碼，您可以從遠端重設密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="4147b-226">若要從遠端鎖定 Android 裝置︰</span><span class="sxs-lookup"><span data-stu-id="4147b-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="4147b-227">從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中，按一下左方導覽中的 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="4147b-228">在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。</span><span class="sxs-lookup"><span data-stu-id="4147b-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="4147b-229">在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4147b-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="4147b-230">在裝置清單中，按一下您的 Android 裝置。 </span><span class="sxs-lookup"><span data-stu-id="4147b-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="4147b-231">透過您的 Android 裝置，確定裝置位於主畫面。 </span><span class="sxs-lookup"><span data-stu-id="4147b-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="4147b-p120">從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。出現提示時，按一下 [**是**]。</span><span class="sxs-lookup"><span data-stu-id="4147b-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="4147b-234">當 Android 裝置切換至鎖定畫面時，即可觀看您的 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="4147b-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="4147b-235">Android 裝置密碼重設時, Intune 系統管理入口網站，就會產生並設定強式密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="4147b-236">若要從遠端重設密碼︰</span><span class="sxs-lookup"><span data-stu-id="4147b-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="4147b-237">從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中的**所有直接的受管理的裝置**] 窗格中，按一下 [在 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="4147b-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="4147b-238">在工作列上，按一下 [**遠端工作 > 密碼重設**。</span><span class="sxs-lookup"><span data-stu-id="4147b-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="4147b-p121">在**遠端工作： 密碼重設**提示、 按一下 [**是]**。靜待一分鐘。</span><span class="sxs-lookup"><span data-stu-id="4147b-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="4147b-241">在**所有直接的受管理的裝置**] 窗格中，按一下 [**檢視屬性**。</span><span class="sxs-lookup"><span data-stu-id="4147b-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="4147b-242">在**密碼重設**，記下新的密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="4147b-243">在 Android 裝置的鎖定畫面上輸入新密碼。 </span><span class="sxs-lookup"><span data-stu-id="4147b-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="4147b-244">若要變更密碼後，移到**設定**、 點選**裝置**、 點選 [**鎖定] 畫面上**，輸入新的密碼再次、 點選 [**螢幕鎖定**及您所選擇的密碼。</span><span class="sxs-lookup"><span data-stu-id="4147b-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="4147b-245">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="4147b-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4147b-246">請參閱</span><span class="sxs-lookup"><span data-stu-id="4147b-246">See Also</span></span>

[<span data-ttu-id="4147b-247">Microsoft 365 Enterprise 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="4147b-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="4147b-248">Microsoft 365 Enterprise 開發人員/測試環境的 MAM 原則</span><span class="sxs-lookup"><span data-stu-id="4147b-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="4147b-249">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="4147b-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="4147b-250">Enterprise 行動性 + 安全性 （EMS）</span><span class="sxs-lookup"><span data-stu-id="4147b-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


