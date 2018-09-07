---
title: Office 365 和 Dynamics 365 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 摘要：您可以使用這個測試實驗室指南將 Dynamics 365 新增到您的 Office 365 開發/測試環境。
ms.openlocfilehash: 195e5ab4fd96d1f238c96d47cc7406a45e0e02b1
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915208"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="0d286-103">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0d286-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="0d286-104">**摘要：** 您可以使用這個測試實驗室指南將 Dynamics 365 新增到您的 Office 365 開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="0d286-104">**Summary:** Use this Test Lab Guide to add EMS to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0d286-105">使用這篇文章中的指示，您可以將 Dynamics 365 試用版訂閱新增到與 Office 365 開發/測試環境相同的組織，建立 Office 365 和 Dynamics 365 開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="0d286-105">With the instructions in this article, you add an EMS trial subscription to the same organization as  your Office 365 dev/test environment, creating an Office 365 and EMS dev/test environment.</span></span>

![Office 365 和 Dynamics 365 開發/測試環境](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="0d286-p101">您可以使用 Dynamics 365 試用訂閱來實作 Dynamics 365 的特色和功能。下列解決方案隨附於 Dynamics 365 方案 1 企業版試用：</span><span class="sxs-lookup"><span data-stu-id="0d286-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="0d286-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales)。透過自動化和數位智慧，協助銷售人員保持專注並提高工作效率，藉此提升銷售量。</span><span class="sxs-lookup"><span data-stu-id="0d286-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="0d286-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service)。讓代理商獲得提供完美服務所需的完整資訊和數位智慧，藉此贏得客戶忠誠度。</span><span class="sxs-lookup"><span data-stu-id="0d286-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="0d286-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service)。將排程最佳化、為員工提供所需工具，以及使用預測工具來增加獲利，藉此打造完美的服務專線。</span><span class="sxs-lookup"><span data-stu-id="0d286-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="0d286-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/zh-TW/dynamics365/project-service-automation)。為專案畫下成功的句點，並與高生產力的員工和智慧工具建立互利的關係。</span><span class="sxs-lookup"><span data-stu-id="0d286-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/zh-TW/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="0d286-117">您可以在 Dynamics 365 試用訂閱中探索上述一或多個項目。</span><span class="sxs-lookup"><span data-stu-id="0d286-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="0d286-119">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="0d286-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="0d286-120">階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0d286-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="0d286-121">如果您只想以具有最小需求的輕量型方式測試 Office 365 和 Dynamics 365，請遵循 [Office 365 開發/測試環境](office-365-dev-test-environment.md)的階段 2 和階段 3 中的指示。</span><span class="sxs-lookup"><span data-stu-id="0d286-121">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of Create an Office 365 Dev/Test Environment.</span></span>
  
<span data-ttu-id="0d286-122">如果您想要針對模擬的企業測試 Office 365 和 Dynamics 365，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0d286-122">If you want to test Office 365 and EMS for a simulated enterprise, follow the instructions in Add DirSync to Your Office 365 Dev/Test Environment.</span></span>

![Office 365 開發/測試環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="0d286-p106">這篇文章中的組態不需要模擬的企業開發/測試環境，其中包括模擬的內部網路 (連線到網際網路) 和 Windows Server AD 樹系中的目錄同步處理。它在這裡提供作為選項，讓您可以在代表典型組織的環境中試驗 Office 365 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="0d286-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="0d286-126">階段 2：新增 Dynamics 365 試用訂閱</span><span class="sxs-lookup"><span data-stu-id="0d286-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="0d286-127">在這個階段中，您可以註冊 Dynamics 365 試用訂閱，並將它新增到與 Office 365 試用訂閱的相同組織。</span><span class="sxs-lookup"><span data-stu-id="0d286-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="0d286-128">註冊 Dynamics 365 試用訂閱</span><span class="sxs-lookup"><span data-stu-id="0d286-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="0d286-129">使用電腦上的瀏覽器 (輕量型) 或是從 CLIENT1 (模擬企業)，以全域系統管理員帳戶的認證，登入位於 [https://portal.office.com](https://portal.office.com) 的 Office 365 入口網站。</span><span class="sxs-lookup"><span data-stu-id="0d286-129">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="0d286-130">按一下 [管理]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="0d286-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0d286-131">在 [Office 系統管理中心]\*\*\*\* 索引標籤上，按一下左導覽中的 [計費] > [購買服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-131">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0d286-p107">在 [購買服務]\*\*\*\* 頁面上，尋找 [Dynamics 365 方案 1 企業版]\*\*\*\* 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0d286-134">在 [確認訂單]\*\*\*\* 頁面上，按一下 [立即試用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0d286-135">在 [訂單收據]\*\*\*\* 頁面上，按一下 [繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-135">On the **Order receipt** page, click **Continue**.</span></span>

![Office 365 和 Dynamics 365 開發/測試環境](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="0d286-p108">Dynamics 365 方案 1 企業版試用訂閱是 30 天。您可以輕鬆地將試用訂閱延長額外 30 天的時間。針對永久開發/測試環境，建立內含少量授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="0d286-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="0d286-140">階段 3：指派 Dynamics 365 授權和系統管理員</span><span class="sxs-lookup"><span data-stu-id="0d286-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="0d286-141">在此階段中，您將 Dynamics 365 授權指派給全域系統管理員、使用者 2 和使用者 3 帳戶，並將他們設為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0d286-141">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="0d286-142">使用這些步驟來指派 Dynamics 365 授權。</span><span class="sxs-lookup"><span data-stu-id="0d286-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="0d286-143">在 [Office 系統管理中心]\*\*\*\* 索引標籤上，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-143">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="0d286-144">在作用中使用者清單中，按一下全域系統管理員帳戶，然後按一下 [產品授權]\*\*\*\* 的 [編輯] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="0d286-145">在 [產品授權] \*\*\*\* 窗格中，將 [Dynamics 365 方案 1 企業版]\*\*\*\* 的產品授權設為 [開啟]\*\*\*\*，按一下 [儲存]\*\*\*\*，然後按兩次 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="0d286-146">對使用者 2 和使用者 3 帳戶執行步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="0d286-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="0d286-147">關閉 [Office 系統管理中心]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d286-147">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="0d286-148">使用這些步驟，將使用者 2 和使用者 3 帳戶設定為 Dynamics 365 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0d286-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="0d286-149">從 [Microsoft Office 的首頁]\*\*\*\* 索引標籤中，按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-149">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="0d286-150">在 [Office 系統管理中心]\*\*\*\* 索引標籤上，依序按一下 [系統管理中心]\*\*\*\*、[Dynamics 365]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-150">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="0d286-151">您可能需要等待 Dynamics 365 完成佈建，Dynamics 365 才會顯示在功能表中。</span><span class="sxs-lookup"><span data-stu-id="0d286-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="0d286-152">在 [Dynamics 365] 索引標籤上，按一下 [這些所有]\*\*\*\*，然後按一下 [完成安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="0d286-153">請等候安裝完成。</span><span class="sxs-lookup"><span data-stu-id="0d286-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="0d286-p109">安裝完成後，就會顯示根據屬於試用訂閱之範例資料的銷售活動儀表板。花幾分鐘來檢視**歡迎使用試用版**影片。完成時關閉 [影片] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0d286-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="0d286-157">在頂端的工具列上，按一下 [銷售]\*\*\*\* 旁的向下箭號，按一下 [設定]\*\*\*\*，然後按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="0d286-158">在 [安全性]\*\*\*\* 頁面，按一下 [使用者] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="0d286-159">在使用者清單中，按一下 [使用者 2]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="0d286-160">在工具列中，按一下 [管理角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="0d286-161">在 [管理角色]\*\*\*\*，按一下 [系統管理員]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="0d286-162">在頂部的工具列上按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d286-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="0d286-163">對使用者 3 帳戶重複步驟 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="0d286-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="0d286-164">關閉 [使用者：User3]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d286-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="0d286-165">Office 365 全域系統管理員帳戶已自動指派 Dynamics 365 系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="0d286-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="0d286-166">Office 365 和 Dynamics 365 開發/測試環境現在有：</span><span class="sxs-lookup"><span data-stu-id="0d286-166">Your Office 365 and EMS dev/test environment now has:</span></span>
  
- <span data-ttu-id="0d286-167">Office 365 E5 企業版和 Dynamics 365 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="0d286-167">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="0d286-168">您的全域企業系統管理員、使用者 2 和使用者 3 帳戶已啟用，可使用 Office 365 E5 企業版和 Dynamics 365 且為 Dynamics 365 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0d286-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="0d286-169">下一步</span><span class="sxs-lookup"><span data-stu-id="0d286-169">Next step</span></span>

<span data-ttu-id="0d286-170">透過 [Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)，設定然後實作 Office 365 和 Dynamics 365 如何在 Exchange Online 信箱中共同運作。</span><span class="sxs-lookup"><span data-stu-id="0d286-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0d286-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d286-171">See Also</span></span>

[<span data-ttu-id="0d286-172">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="0d286-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0d286-173">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0d286-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="0d286-174">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0d286-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0d286-175">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="0d286-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="0d286-176">Dynamics 365 訂閱管理 (線上)</span><span class="sxs-lookup"><span data-stu-id="0d286-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="0d286-177">管理 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="0d286-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


