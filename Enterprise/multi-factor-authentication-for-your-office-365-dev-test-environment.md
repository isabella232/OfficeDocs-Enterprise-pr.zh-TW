---
title: 適用於您的 Office 365 開發/測試環境的多重要素驗證
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 摘要： 設定多重要素驗證使用文字訊息傳送給 Office 365 開發人員/測試環境中的智慧型手機。
ms.openlocfilehash: 6e2aefa9309e7e268c937055f7fe59600f8c87da
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897446"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="f1dd6-103">適用於您的 Office 365 開發/測試環境的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="f1dd6-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="f1dd6-104">**摘要：** 設定使用文字訊息傳送給 Office 365 開發人員/測試環境中的智慧型電話的多重要素驗證。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="f1dd6-p101">登入您的 Office 365 訂閱的安全性其他層級，您可以啟用 Azure 需要超過剛使用者名稱和密碼驗證帳戶的多重要素驗證。與 Office 365 的多重要素驗證的使用者所需確認電話、 輸入驗證碼傳送文字郵件內或智慧型電話上指定的應用程式密碼後正確地輸入其密碼。未滿足此第二個驗證因素之後才可以登入。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="f1dd6-108">本文說明如何啟用並測試文字郵件驗證特定的 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="f1dd6-109">有兩個階段來設定 Office 365 的開發人員/測試環境中的多重要素驗證：</span><span class="sxs-lookup"><span data-stu-id="f1dd6-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="f1dd6-110">建立 Office 365 開發/測試環境。
</span><span class="sxs-lookup"><span data-stu-id="f1dd6-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="f1dd6-111">啟用並測試使用者 2 帳戶的多重要素驗證。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="f1dd6-112">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="f1dd6-113">階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="f1dd6-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="f1dd6-114">如果您只想要測試多重要素驗證的最低需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f1dd6-115">如果您想要測試模擬企業中的多重要素驗證，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f1dd6-p102">測試多重要素驗證不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server AD 樹系目錄同步處理。它會提供這裡是做為選項可以測試多重要素驗證和代表的典型組織的環境中實驗。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="f1dd6-118">階段 2： 啟用並測試使用者 2 帳戶的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="f1dd6-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="f1dd6-119">啟用多重要素驗證使用者 2 帳戶進行這些步驟：</span><span class="sxs-lookup"><span data-stu-id="f1dd6-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="f1dd6-120">開啟瀏覽器中的個別執行個體，請移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com))，並再登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="f1dd6-121">從主要的入口網站頁面中，按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="f1dd6-122">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="f1dd6-123">在 [作用中使用者] 窗格中，按一下 [**更多 > 安裝 Azure 多重要素驗證**。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="f1dd6-124">在清單中，選取**使用者 2**帳戶。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="f1dd6-125">**使用者 2** ] 區段中的 [**快速步驟**，按一下 [**啟用**。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="f1dd6-126">**如何啟用多重要素驗證**] 對話方塊中，按一下 [**啟用多重要素驗證**]。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="f1dd6-127">在**更新成功**] 對話方塊中，按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="f1dd6-128">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [使用者帳戶中的圖示右上方，和 [**登出**。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="f1dd6-129">關閉瀏覽器執行個體。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-129">Close your browser instance.</span></span>
    
<span data-ttu-id="f1dd6-130">完成設定使用者 2 帳戶使用的文字訊息的驗證和測試這些步驟：</span><span class="sxs-lookup"><span data-stu-id="f1dd6-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="f1dd6-131">開啟瀏覽器中的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="f1dd6-132">移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 和登入的使用者 2 帳戶 (user2 @\<組織 name>.onmicrosoft.com) 和密碼。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="f1dd6-p103">登入之後, 會提示您設定的其他安全性驗證的帳戶。按一下 [**立即設定**]。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="f1dd6-135">在 [**其他安全性驗證**] 頁面上：</span><span class="sxs-lookup"><span data-stu-id="f1dd6-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="f1dd6-136">選取 [國家或地區。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="f1dd6-137">輸入要接收文字訊息智慧型手機電話號碼。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="f1dd6-138">在**方法**中，按一下 [**傳送我文字訊息的程式碼**。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="f1dd6-139">按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="f1dd6-140">輸入驗證碼從智慧型手機上接收的文字訊息，然後按一下**確認**。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="f1dd6-141">在**步驟 3： 保留現有的應用程式**頁面、 使用者 2 帳戶將顯示應用程式密碼記錄在安全的位置，然後再按一下 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="f1dd6-p104">如果這是第一次您登入的使用者 2 帳戶後，系統提示您變更密碼。按兩次，輸入原始密碼] 和 [新密碼] 和 [**更新密碼，登入**。安全的位置記錄的新密碼。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="f1dd6-145">您應請參閱 ＜ Office 365 入口網站使用者 2 在瀏覽器的 [ **Microsoft Office Home** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f1dd6-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="f1dd6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1dd6-146">See Also</span></span>

[<span data-ttu-id="f1dd6-147">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="f1dd6-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f1dd6-148">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="f1dd6-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="f1dd6-149">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="f1dd6-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="f1dd6-150">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="f1dd6-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="f1dd6-151">Office 365 部署多重要素驗證方案</span><span class="sxs-lookup"><span data-stu-id="f1dd6-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

