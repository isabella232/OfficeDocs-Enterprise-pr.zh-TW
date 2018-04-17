---
title: 一個 Microsoft Cloud 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 摘要： 使用此測試實驗室指南建立包含所有的 Microsoft cloud 方案的開發人員/測試環境。
ms.openlocfilehash: c1d0e190e6d7e3871cf4289729b53cc0b4b5d04d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="ba54f-103">一個 Microsoft Cloud 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="ba54f-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="ba54f-104">**摘要：**若要建立包含所有的 Microsoft cloud 方案的開發人員/測試環境中使用此測試實驗室指南。</span><span class="sxs-lookup"><span data-stu-id="ba54f-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="ba54f-p101">使用本文中的指示，您可以在 Microsoft Azure 基礎結構服務中建立模擬內部網路然後再新增 [Microsoft Office 365、 Microsoft 企業行動性 + 安全性 (EMS) 及 Microsoft Dynamics 365 訂閱。結果是在單一的開發人員測試環境中同時使用所有 Microsoft cloud 方案簡化的組織。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![具有 Azure、Office 365、EMS 及 Dynamics 365 之 One Microsoft 雲端開發/測試環境的階段 3 ](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="ba54f-108">您可以使用要產生的設定：</span><span class="sxs-lookup"><span data-stu-id="ba54f-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="ba54f-109">跨 Microsoft cloud 方案，例如一般身分識別基礎結構所提供的 Azure Active Directory (AD) 體驗整合。</span><span class="sxs-lookup"><span data-stu-id="ba54f-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="ba54f-110">評估包含多個 Microsoft Cloud 方案的端對端案例。</span><span class="sxs-lookup"><span data-stu-id="ba54f-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="ba54f-111">建立示範 （英文）、 概念證明或使用多個 Microsoft Cloud 方案的開發人員/測試設定。</span><span class="sxs-lookup"><span data-stu-id="ba54f-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="ba54f-112">建置專業開發您 Microsoft Cloud 技能。</span><span class="sxs-lookup"><span data-stu-id="ba54f-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="ba54f-113">階段 1： 建立模擬內部網路及新增 Office 365</span><span class="sxs-lookup"><span data-stu-id="ba54f-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="ba54f-114">遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ba54f-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="ba54f-115">圖 1 顯示您所產生的組態，包括 Office 365 和 Azure 基礎結構服務和目錄同步處理中執行來自內部部署 Windows Server Active Directory (AD) 樹系模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="ba54f-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="ba54f-116">**圖 1： 模擬內部網路與 Office 365 搭配 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="ba54f-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![具有 DirSync 的 Office 365 開發/測試環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="ba54f-p102">Azure 試用版是 30 天。Office 365 企業版 E5 試用版訂閱是 30 天，可輕鬆地延伸的另一個 30 天。在永久的開發人員測試環境中建立新付費 Azure 訂閱和新的授權數目很少付費的 Office 365 企業版 E5 訂閱。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="ba54f-121">階段 2： 新增 EMS</span><span class="sxs-lookup"><span data-stu-id="ba54f-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="ba54f-122">在這個階段中，您可以註冊 EMS 試用訂閱，並將它新增至與 Office 365 試用訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="ba54f-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="ba54f-123">其中一個瀏覽器與您的桌上型電腦或從 CLIENT1，登入 Office 365 入口網站在[https://portal.office.com](https://portal.office.com)以全域管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="ba54f-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="ba54f-124">按一下 [管理] 磚。</span><span class="sxs-lookup"><span data-stu-id="ba54f-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="ba54f-125">在瀏覽器的 [Office 系統管理中心] 索引標籤上，按一下左導覽中的 [計費] > [購買服務]。</span><span class="sxs-lookup"><span data-stu-id="ba54f-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="ba54f-p103">在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="ba54f-128">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="ba54f-129">在 [訂單收據] 頁面上，按一下 [繼續]。</span><span class="sxs-lookup"><span data-stu-id="ba54f-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="ba54f-p104">Enterprise Mobility + Security E5 試用訂閱為 90 天。針對永久開發/測試環境，建立具有少數授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="ba54f-132">接下來，可讓企業行動性 + 安全性 E5 授權的所有使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ba54f-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="ba54f-133">在瀏覽器的 [Office 365 系統管理中心] 索引標籤上，按一下左導覽中的 [使用者] > [作用中使用者]。</span><span class="sxs-lookup"><span data-stu-id="ba54f-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="ba54f-134">按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="ba54f-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="ba54f-135">在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="ba54f-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="ba54f-136">所有其他帳戶 （User1、 使用者 2、 3 使用者、 使用者 4 和使用者 5），請執行步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="ba54f-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="ba54f-137">開發/測試環境現在有：</span><span class="sxs-lookup"><span data-stu-id="ba54f-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="ba54f-138">Azure 基礎結構服務中執行模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="ba54f-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="ba54f-139">Office 365 E5 Enterprise 和 EMS 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="ba54f-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="ba54f-140">您的所有使用者帳戶都會啟用以使用 Office 365 E5 Enterprise 和 EMS。</span><span class="sxs-lookup"><span data-stu-id="ba54f-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="ba54f-141">圖 2 顯示您所產生的設定，會新增 EMS。</span><span class="sxs-lookup"><span data-stu-id="ba54f-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="ba54f-142">**圖 2： 模擬內部網路與 Office 365 和 EMS Azure 中**</span><span class="sxs-lookup"><span data-stu-id="ba54f-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![具有 Azure、Office 365 及 EMS 之 One Microsoft 雲端開發/測試環境的階段 2 ](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="ba54f-144">階段 3： 新增 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="ba54f-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="ba54f-145">在此階段中，您註冊 Dynamics 365 試用版訂閱並將其新增至 Office 365 和 EMS 試用版訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="ba54f-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="ba54f-146">在 [您的桌上型電腦使用瀏覽器或從 CLIENT1，登入 Office 365 入口網站在[https://portal.office.com](https://portal.office.com)以全域管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="ba54f-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="ba54f-147">按一下 [管理] 磚。</span><span class="sxs-lookup"><span data-stu-id="ba54f-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="ba54f-148">在**Office 系統管理中心**] 索引標籤的 [在左導覽列中，按一下 [**帳務 > 購買服務**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="ba54f-p105">在 [**購買服務**] 頁面上尋找**Dynamics 365 計劃 1 Enterprise Edition**項目。滑鼠指標停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="ba54f-151">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="ba54f-152">在 [訂單收據] 頁面上，按一下 [繼續]。</span><span class="sxs-lookup"><span data-stu-id="ba54f-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="ba54f-p106">Dynamics 365 計劃 1 Enterprise Edition 試用訂閱是 30 天。您可以輕鬆地擴充另一個 30 天的軌跡訂閱。在永久的開發人員測試環境中建立新付費少量的授權與訂閱。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="ba54f-156">使用下列步驟將 Dynamics 365 授權指派給全域管理員、 使用者 2 及 3 使用者帳戶，並使其系統管理員。</span><span class="sxs-lookup"><span data-stu-id="ba54f-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="ba54f-157">在 [ **Office 系統管理中心**] 索引標籤上按一下 [**使用者 > 作用中使用者**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="ba54f-158">在作用中使用者清單中，按一下您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="ba54f-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="ba54f-159">在**產品授權**] 窗格中，開啟**Dynamics 365 計劃 1 Enterprise Edition** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="ba54f-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="ba54f-160">使用者 2 和 3 使用者帳戶執行步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="ba54f-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="ba54f-161">關閉**Office 系統管理中心**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ba54f-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="ba54f-162">使用下列步驟來設定使用者 2 和 3 使用者帳戶為 Dynamics 365 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="ba54f-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="ba54f-163">在瀏覽器中，在左導覽列中， **Office 系統管理中心**] 索引標籤上 [ **Admin 中心**，和 [ **Dynamics 365**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="ba54f-164">您可能需要等候 Dynamics 365 完成佈建之前 Dynamics 365 出現的功能表中。</span><span class="sxs-lookup"><span data-stu-id="ba54f-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="ba54f-165">在 [Dynamics 365] 索引標籤上按一下 [**全部都**、] 和 [**完成安裝。**</span><span class="sxs-lookup"><span data-stu-id="ba54f-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="ba54f-166">等候安裝程式完成。</span><span class="sxs-lookup"><span data-stu-id="ba54f-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="ba54f-p107">當安裝完成後時，它會顯示根據屬於軌跡訂閱資料範例銷售活動儀表板。需要一些時間來檢視**您的試用版歡迎使用**視訊。關閉 [視訊] 視窗時完成。</span><span class="sxs-lookup"><span data-stu-id="ba54f-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="ba54f-170">在頂端工具列上，按一下 [**銷售**] 旁的向下箭號、 按一下 [**設定**] 及 [**安全性**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="ba54f-171">按一下 [**安全性**] 索引標籤的 [**使用者**]。</span><span class="sxs-lookup"><span data-stu-id="ba54f-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="ba54f-172">在使用者清單中，按一下 [**使用者 2**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="ba54f-173">在 [工具] 列中，按一下 [**管理角色**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="ba54f-174">在**管理角色**、 按一下 [**系統管理員**，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="ba54f-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="ba54f-175">在上方的 [工具] 列中按一下 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="ba54f-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="ba54f-176">使用者 3 帳戶重複步驟 5-8。</span><span class="sxs-lookup"><span data-stu-id="ba54f-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="ba54f-177">關閉**使用者： User3** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ba54f-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="ba54f-178">您的 Office 365 全域管理員帳戶會自動指派 Dynamics 365 系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="ba54f-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="ba54f-179">開發/測試環境現在有：</span><span class="sxs-lookup"><span data-stu-id="ba54f-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="ba54f-180">Azure 基礎結構服務中執行模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="ba54f-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="ba54f-181">Office 365 E5 企業、 EMS 及 Dynamics 365 試用版訂閱共用相同的組織與相同的 Azure AD 租用戶與您的使用者帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="ba54f-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="ba54f-182">您的所有使用者帳戶都會啟用以使用 Office 365 E5 Enterprise 和 EMS。</span><span class="sxs-lookup"><span data-stu-id="ba54f-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="ba54f-183">您的全域企業系統管理員、 使用者 2 和 3 使用者帳戶能夠使用 Dynamics 365 且 Dynamics 365 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="ba54f-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="ba54f-184">圖 3 是您所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="ba54f-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="ba54f-185">**圖 3： 模擬內部網路與 Office 365、 EMS、 和 Dynamics 365 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="ba54f-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![具有 Azure、Office 365、EMS 及 Dynamics 365 之 One Microsoft 雲端開發/測試環境的階段 3 ](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="ba54f-187">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ba54f-187">Next steps</span></span>

<span data-ttu-id="ba54f-p108">您現在可以實驗一個 Microsoft Cloud 開發/測試環境。導引式體驗的某些概念如下：</span><span class="sxs-lookup"><span data-stu-id="ba54f-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="ba54f-190">在 EMS for Office 365 應用程式設定行動裝置應用程式管理 (MAM) 原則</span><span class="sxs-lookup"><span data-stu-id="ba54f-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="ba54f-191">在 Office 365 整合 Dynamics 365 連絡人示範 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ba54f-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="ba54f-192">在主控伺服器為基礎的工作負載的 Azure 基礎結構服務中建立模擬的跨內部網路</span><span class="sxs-lookup"><span data-stu-id="ba54f-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="ba54f-193">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba54f-193">See Also</span></span>

[<span data-ttu-id="ba54f-194">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="ba54f-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="ba54f-195">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="ba54f-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="ba54f-196">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="ba54f-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="ba54f-197">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="ba54f-197">Security solutions</span></span>](security-solutions.md)





