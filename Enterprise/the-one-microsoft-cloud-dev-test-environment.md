---
title: One Microsoft Cloud 開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 摘要：使用這項測試實驗室指南來建立開發/測試環境，其中包含所有的 Microsoft 雲端供應項目。
ms.openlocfilehash: 51899ceb0cceef0248f6dc10cb21f5353e774cea
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897146"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="f2d4e-103">One Microsoft Cloud 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="f2d4e-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="f2d4e-104">**摘要：** 使用這項測試實驗室指南來建立開發/測試環境，其中包含所有的 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="f2d4e-p101">依照本文所述的指示，您可以在 Microsoft Azure 基礎結構服務中建立模擬的內部網路，然後再新增 Microsoft Office 365、Microsoft Enterprise Mobility + Security (EMS)，與 Microsoft Dynamics 365 訂閱。結果是經簡化的組織在單一開發/測試環境中一次使用所有 Microsoft 雲端供應項目。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![具有 Azure、Office 365、EMS 及 Dynamics 365 之 One Microsoft Cloud 開發/測試環境的階段 3 ](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="f2d4e-108">您可以使用所產生的組態來：</span><span class="sxs-lookup"><span data-stu-id="f2d4e-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="f2d4e-109">體驗在 Microsoft 雲端供應項目間的整合 (例如 Azure Active Directory (AD) 所提供的常見身分識別基礎結構)。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="f2d4e-110">評估包含多個 Microsoft Cloud 供應項目的端對端案例。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="f2d4e-111">建立示範、概念證明或使用多個 Microsoft Cloud 供應項目的開發/測試組態。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="f2d4e-112">建置適用於專業開發的 Microsoft Cloud 技能。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="f2d4e-113">階段 1：建立模擬的內部網路，並新增 Office 365</span><span class="sxs-lookup"><span data-stu-id="f2d4e-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="f2d4e-114">遵循在 [ Office 365 開發/測試環境中的 DirSync ](dirsync-for-your-office-365-dev-test-environment.md) 中的指示。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f2d4e-115">圖 1 顯示您產生的組態，其中包括 Office 365 與在 Azure 基礎結構服務中執行模擬內部網路與來自內部部署 Windows Server Active Directory (AD) 樹系中的目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="f2d4e-116">**圖 1：含 Office 365 之 Azure 中的模擬內部網路**</span><span class="sxs-lookup"><span data-stu-id="f2d4e-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![具有 DirSync 的 Office 365 開發/測試環境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="f2d4e-p102">Azure 試用版是 30 天。Office 365 企業版 E5 試用訂閱是 30 天，此可以輕鬆地延長額外 30 天的時間。針對永久開發/測試環境，建立新付費 Azure 訂閱並建立新付費的 Office 365 企業版 E5 訂閱，內含少量的授權。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="f2d4e-121">階段 2：新增 EMS</span><span class="sxs-lookup"><span data-stu-id="f2d4e-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="f2d4e-122">在這個階段中，您可以註冊 EMS 試用訂閱，並將它新增至與 Office 365 試用訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="f2d4e-123">使用電腦上的瀏覽器或是從 CLIENT1，以全域系統管理員帳戶的認證，登入位於 [https://portal.office.com](https://portal.office.com) 的 Office 365 入口網站。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="f2d4e-124">按一下 [管理]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f2d4e-125">在瀏覽器的 [Office 系統管理中心]\*\*\*\* 索引標籤上，按一下左導覽中的 [計費] > [購買服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="f2d4e-p103">在 [購買服務]\*\*\*\* 頁面上，尋找 **Enterprise Mobility + Security E5** 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="f2d4e-128">在 [確認訂單]\*\*\*\* 頁面上，按一下 [立即試用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="f2d4e-129">在 [訂單收據]\*\*\*\* 頁面上，按一下 [繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f2d4e-p104">Enterprise Mobility + Security E5 試用訂閱為 90 天。針對永久開發/測試環境，建立具有少數授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="f2d4e-132">接下來，啟用適用於所有使用者帳戶的 Enterprise Mobility + Security E5 授權。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="f2d4e-133">在瀏覽器的 [Office 365 系統管理中心]\*\*\*\* 索引標籤上，按一下左導覽中的 [使用者] > [作用中使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="f2d4e-134">按一下您的全域系統管理員帳戶，然後按一下 [產品授權]\*\*\*\* 的 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="f2d4e-135">在 [產品授權]\*\*\*\* 窗格中，將 **Enterprise Mobility + Security E5** 的產品授權設為 [開啟]\*\*，按一下 [儲存]，然後按兩次 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="f2d4e-136">針對您的所有其他帳戶 (User1、User 2、User 3、User 4 及 User 5) 執行步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="f2d4e-137">開發/測試環境現在擁有：</span><span class="sxs-lookup"><span data-stu-id="f2d4e-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="f2d4e-138">在 Azure 基礎結構服務中執行的模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="f2d4e-139">Office 365 E5 Enterprise 和 EMS 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="f2d4e-140">您的所有使用者帳戶都會啟用以使用 Office 365 E5 Enterprise 和 EMS。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="f2d4e-141">圖 2 顯示產生的組態，其中會新增 EMS。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="f2d4e-142">**圖 2：含 Office 365 和 EMS 之 Azure 中的模擬內部網路**</span><span class="sxs-lookup"><span data-stu-id="f2d4e-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![具有 Azure、Office 365 及 EMS 之 One Microsoft Cloud 開發/測試環境的階段 2 ](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="f2d4e-144">階段 3：新增 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f2d4e-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="f2d4e-145">在這個階段中，您可以註冊 Dynamics 365 試用訂閱，並將它新增至與 Office 365 與 EMS 試用訂閱的相同組織。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="f2d4e-146">使用電腦上的瀏覽器或是從 CLIENT1，以全域系統管理員帳戶的認證，登入位於 [https://portal.office.com](https://portal.office.com) 的 Office 365 入口網站。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="f2d4e-147">按一下 [管理]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f2d4e-148">在 [Office 系統管理中心]\*\*\*\* 索引標籤上，按一下左導覽中的 [計費] > [購買服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="f2d4e-p105">在 [購買服務]\*\*\*\* 頁面上，尋找 [Dynamics 365 方案 1 企業版]\*\*\*\* 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="f2d4e-151">在 [確認訂單]\*\*\*\* 頁面上，按一下 [立即試用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="f2d4e-152">在 [訂單收據]\*\*\*\* 頁面上，按一下 [繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f2d4e-p106">Dynamics 365 方案 1 企業版試用訂閱是 30 天。您可以輕鬆地將試用訂閱延長額外 30 天的時間。針對永久開發/測試環境，建立內含少量授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="f2d4e-156">使用這些步驟，將 Dynamics 365 授權指派給全域系統管理員、使用者 2 和使用者 3 帳戶，並將他們設為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="f2d4e-157">在 [Office 系統管理中心]\*\*\*\* 索引標籤上，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="f2d4e-158">在作用中使用者清單中，按一下全域系統管理員帳戶，然後按一下 [產品授權]\*\*\*\* 的 [編輯] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="f2d4e-159">在 [產品授權] \*\*\*\* 窗格中，將 [Dynamics 365 方案 1 企業版]\*\*\*\* 的產品授權設為 [開啟]\*\*\*\*，按一下 [儲存]\*\*\*\*，然後按兩次 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="f2d4e-160">對使用者 2 和使用者 3 帳戶執行步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="f2d4e-161">關閉 [Office 系統管理中心]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="f2d4e-162">使用這些步驟，將使用者 2 和使用者 3 帳戶設定為 Dynamics 365 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="f2d4e-163">在瀏覽器的 [Office 系統管理中心]\*\*\*\* 索引標籤上，依序按一下 [系統管理中心]\*\*\*\*、[Dynamics 365]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="f2d4e-164">您可能需要等待 Dynamics 365 完成佈建，Dynamics 365 才會顯示在功能表中。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="f2d4e-165">在 [Dynamics 365] 索引標籤上，按一下 [這些所有]\*\*\*\*，然後按一下 [完成安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="f2d4e-166">請等候安裝完成。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="f2d4e-p107">安裝完成後，就會根據屬於試用訂閱的範例資料來顯示銷售活動儀表板。請花幾分鐘觀看**歡迎使用試用版**影片。觀看完畢請關閉影片視窗。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="f2d4e-170">在頂端的工具列上，按一下 [銷售]\*\*\*\* 旁的向下箭號，按一下 [設定]\*\*\*\*，然後按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="f2d4e-171">在 [安全性]\*\*\*\* 頁面，按一下 [使用者] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="f2d4e-172">在使用者清單中，按一下 [使用者 2]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="f2d4e-173">在工具列中，按一下 [管理角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="f2d4e-174">在 [管理角色]\*\*\*\*，按一下 [系統管理員]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="f2d4e-175">在頂部的工具列上按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="f2d4e-176">對使用者 3 帳戶重複步驟 5 到 8。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="f2d4e-177">關閉 [使用者：User3]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f2d4e-178">Office 365 全域系統管理員帳戶已自動指派 Dynamics 365 系統管理員角色。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="f2d4e-179">開發/測試環境現在擁有：</span><span class="sxs-lookup"><span data-stu-id="f2d4e-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="f2d4e-180">在 Azure 基礎結構服務中執行的模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="f2d4e-181">Office 365 E5 Enterprise、EMS 和 Dynamics 365 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="f2d4e-182">您的所有使用者帳戶都會啟用以使用 Office 365 E5 Enterprise 和 EMS。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="f2d4e-183">您的全域企業系統管理員、使用者 2 和使用者 3 帳戶已啟用，可使用 Dynamics 365 且為 Dynamics 365 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="f2d4e-184">圖 3 顯示產生的組態。</span><span class="sxs-lookup"><span data-stu-id="f2d4e-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="f2d4e-185">**圖 3：含 Office 365、EMS 和 Dynamics 365 之 Azure 中的模擬內部網路**</span><span class="sxs-lookup"><span data-stu-id="f2d4e-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![具有 Azure、Office 365、EMS 及 Dynamics 365 之 One Microsoft Cloud 開發/測試環境的階段 3 ](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="f2d4e-187">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f2d4e-187">Next steps</span></span>

<span data-ttu-id="f2d4e-p108">您現在可以使用 One Microsoft Cloud 開發/測試環境來進行實驗。以下是一些引導經驗的構想：</span><span class="sxs-lookup"><span data-stu-id="f2d4e-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="f2d4e-190">在適用於 Office 365 應用程式的 EMS 中設定行動應用程式管理 (MAM) 原則</span><span class="sxs-lookup"><span data-stu-id="f2d4e-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="f2d4e-191">在含 Dynamics 365 連絡人的 Office 365 整合中示範 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f2d4e-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="f2d4e-192">在 Azure 基礎結構服務建立模擬的跨部署網路來主控以伺服器為基礎的工作負載</span><span class="sxs-lookup"><span data-stu-id="f2d4e-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="f2d4e-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2d4e-193">See Also</span></span>

[<span data-ttu-id="f2d4e-194">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="f2d4e-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f2d4e-195">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="f2d4e-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="f2d4e-196">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="f2d4e-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="f2d4e-197">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="f2d4e-197">Security solutions</span></span>](security-solutions.md)





