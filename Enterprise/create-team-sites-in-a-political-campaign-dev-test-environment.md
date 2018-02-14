---
title: "政治 campaign 開發/測試環境中建立小組網站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "摘要： 政治 campaign 開發/測試環境中建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站。"
ms.openlocfilehash: 3a2e507d17a558452fe0c2f0a062098e7c9c6407
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="61f0b-103">政治 campaign 開發/測試環境中建立小組網站</span><span class="sxs-lookup"><span data-stu-id="61f0b-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="61f0b-104">**摘要：**政治 campaign 開發/測試環境中建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="61f0b-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="61f0b-p101">使用本文中的指示來建立[政治活動、 非營利機構，以及其他靈活組織的 Microsoft 安全性指導](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)包含四個不同類型的 SharePoint Online 小組網站的開發人員/測試環境解決方案。詳細說明這些網站上主題 10、 **SharePoint 及 OneDrive for Business**的標題。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="61f0b-107">階段 1： 建立政治 campaign 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="61f0b-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="61f0b-108">首先，請遵循[Configure 群組及使用者政治 campaign 開發/測試環境](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)中的指示以建立您的訂閱、 使用者及群組。</span><span class="sxs-lookup"><span data-stu-id="61f0b-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="61f0b-109">階段 2： 建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="61f0b-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="61f0b-110">在此階段中，您可以建立不同的層級的 SharePoint Online 小組網站的文件資料夾的安全性的標籤。</span><span class="sxs-lookup"><span data-stu-id="61f0b-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="61f0b-p102">必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="61f0b-113">從**Microsoft Office Home** ] 索引標籤上，按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="61f0b-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="61f0b-114">從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中，按一下 [**系統中心 > 安全性&amp;規範**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="61f0b-115">從新**首頁-安全性&amp;規範**] 索引標籤的瀏覽器中，按一下 [**分類 > 標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="61f0b-116">從**首頁 > 標籤**] 窗格中，按一下 [**建立] 標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="61f0b-117">在**名稱您標籤**] 窗格中，輸入**內部]**，然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="61f0b-118">在 [**標籤設定**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-119">在**檢閱您的設定**] 窗格中，按一下 [**建立此標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="61f0b-120">針對這些額外的標籤重複步驟 5-8：</span><span class="sxs-lookup"><span data-stu-id="61f0b-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="61f0b-121">私人</span><span class="sxs-lookup"><span data-stu-id="61f0b-121">Private</span></span>
    
  - <span data-ttu-id="61f0b-122">機密</span><span class="sxs-lookup"><span data-stu-id="61f0b-122">Sensitive</span></span>
    
  - <span data-ttu-id="61f0b-123">高度機密</span><span class="sxs-lookup"><span data-stu-id="61f0b-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="61f0b-124">從**首頁 > 標籤**] 窗格中，按一下 [**發佈標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="61f0b-125">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**選擇標籤發佈**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="61f0b-126">在 [**選擇標籤**] 窗格中，按一下 [**新增**] 並選取所有的四個標籤。</span><span class="sxs-lookup"><span data-stu-id="61f0b-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="61f0b-127">按一下 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="61f0b-128">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="61f0b-129">在 [**選擇位置**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="61f0b-130">在**您的原則名稱**] 窗格中，輸入**行銷活動**在 [**名稱**] 然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="61f0b-131">在**檢閱您的設定**] 窗格中，按一下 [**發佈標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="61f0b-132">階段 3： 建立 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="61f0b-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="61f0b-133">在此階段中，您可以建立及設定 SharePoint Online 小組網站的對應至 SharePoint Online 小組網站的四種類型您政治行銷活動。</span><span class="sxs-lookup"><span data-stu-id="61f0b-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="61f0b-134">行銷活動寬的小組網站</span><span class="sxs-lookup"><span data-stu-id="61f0b-134">Campaign wide team site</span></span>

<span data-ttu-id="61f0b-135">若要建立基準公用 SharePoint Online 小組網站，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="61f0b-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="61f0b-136">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 使用全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="61f0b-137">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="61f0b-138">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="61f0b-139">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="61f0b-140">在**站台名稱**] 中輸入**Campaign 寬**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="61f0b-141">在**小組網站描述**] 中，輸入**SharePoint 網站的整個行銷活動**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="61f0b-142">**隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-143">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="61f0b-144">接下來，設定內部標籤 Campaign 寬的小組網站的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="61f0b-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="61f0b-145">**戰役整個首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="61f0b-146">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="61f0b-147">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="61f0b-148">在**套用設定的標籤**、 選取 [**內部]**，和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="61f0b-149">行銷活動專案 1 的小組網站</span><span class="sxs-lookup"><span data-stu-id="61f0b-149">Campaign project 1 team site</span></span>

<span data-ttu-id="61f0b-150">若要建立基準私人 SharePoint Online 小組網站內行銷活動的專案，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="61f0b-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="61f0b-151">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 使用全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="61f0b-152">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="61f0b-153">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="61f0b-154">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="61f0b-155">在**站台名稱**] 中輸入**Campaign 專案 1**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="61f0b-156">在**小組網站描述] 中，**輸入**SharePoint 網站的行銷活動專案 1**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="61f0b-157">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-158">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="61f0b-159">下一步] 設定私人標籤 Campaign 專案 1 的小組網站的文件] 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="61f0b-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="61f0b-160">**戰役專案 1 首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="61f0b-161">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="61f0b-162">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="61f0b-163">在**套用設定的標籤**、 選取 [**私人**] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="61f0b-164">行銷活動行銷小組網站</span><span class="sxs-lookup"><span data-stu-id="61f0b-164">Campaign marketing team site</span></span>

<span data-ttu-id="61f0b-165">若要建立機密層級隔離的 SharePoint Online 小組網站的資源行銷活動全方位，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="61f0b-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="61f0b-166">本機電腦上使用瀏覽器，登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 使用全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="61f0b-167">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="61f0b-168">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="61f0b-169">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="61f0b-170">在**小組網站名稱**] 中輸入**行銷活動全方位**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="61f0b-171">在**小組網站描述**] 中，輸入**SharePoint 網站 （機密） 行銷活動全方位的**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="61f0b-172">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-173">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="61f0b-174">在瀏覽器中的 [工具] 列中新的**行銷活動全方位**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="61f0b-175">在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="61f0b-176">在 [新**的權限**] 索引標籤在瀏覽器中按一下 [**存取要求的設定**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="61f0b-177">在 [**存取要求設定**] 對話方塊中，清除**允許成員] 共用網站和個別的檔案及資料夾**並**邀請其他人的網站成員群組允許成員**] 核取方塊中，輸入**ITAdmin1 @** <your organization name> **。onmicrosoft.com**中**傳送所有要求存取**]，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="61f0b-178">清單中的 [**成員行銷活動全方位**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="61f0b-179">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="61f0b-180">在 [**共用**] 對話方塊中，輸入**資深和策略性人員**、 選取它，，然後按一下 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="61f0b-181">重複步驟 14 與 15**分析員工**群組和**Regular1**使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="61f0b-182">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="61f0b-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="61f0b-183">清單中的 [**擁有者行銷活動全方位**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="61f0b-184">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="61f0b-185">在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="61f0b-186">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="61f0b-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="61f0b-187">關閉瀏覽器中的 [**人員與群組**] 索引標籤、 按一下 [瀏覽器上的 [ **Campaign 行銷首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="61f0b-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="61f0b-188">設定權限的結果如下︰</span><span class="sxs-lookup"><span data-stu-id="61f0b-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="61f0b-189">**行銷活動行銷部門成員**SharePoint 群組包含只**資深和策略性人員**群組 （其中包含候選項目、 ChiefOfStaff，以及 Strategic1 使用者帳戶）、**行銷活動全方位**群組 (其中包含全域管理員使用者帳戶），而**分析員工**群組 （其中包含 DataScientist1 使用者帳戶），及**Regular1**的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="61f0b-190">**行銷活動行銷擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="61f0b-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="61f0b-191">**行銷活動行銷訪客**SharePoint 群組沒有包含群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="61f0b-192">成員無法修改站台層級權限 （這可以只來完成**Campaign 行銷擁有人**群組的成員）。</span><span class="sxs-lookup"><span data-stu-id="61f0b-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="61f0b-193">其他使用者帳戶無法存取之網站或其資源，但可以要求網站，會將電子郵件傳送至 ITAdmin1 使用者帳戶信箱的存取權。</span><span class="sxs-lookup"><span data-stu-id="61f0b-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="61f0b-194">接下來，設定行銷活動行銷團隊網站機密標籤的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="61f0b-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="61f0b-195">在瀏覽器的**行銷活動行銷首頁**] 索引標籤中按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="61f0b-196">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="61f0b-197">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="61f0b-198">在**套用設定的標籤**、 選取**機密**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="61f0b-p103">下一步] 設定時階級與組織外的機密標籤上的 SharePoint Online 小組網站的文件會通知使用者資料外洩防護 (DLP) 原則。此 DLP 原則將會套用至 Campaign 行銷網站中的資源。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="61f0b-201">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="61f0b-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="61f0b-202">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="61f0b-203">在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="61f0b-204">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="61f0b-205">在**您的原則名稱**] 窗格中，輸入**機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="61f0b-206">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="61f0b-207">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-208">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="61f0b-209">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="61f0b-210">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**機密**標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="61f0b-211">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="61f0b-212">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="61f0b-213">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="61f0b-214">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="61f0b-215">[文字] 方塊中輸入或貼上下列：</span><span class="sxs-lookup"><span data-stu-id="61f0b-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="61f0b-p104">與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="61f0b-219">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="61f0b-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="61f0b-220">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，清除**封鎖來自共用、 人員及限制共用內容的存取權**] 核取方塊，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="61f0b-221">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="61f0b-222">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="61f0b-223">行銷活動策略小組網站</span><span class="sxs-lookup"><span data-stu-id="61f0b-223">Campaign strategy team site</span></span>

<span data-ttu-id="61f0b-224">行銷活動策略資源之高度機密層級建立隔離的 SharePoint Online 小組網站，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="61f0b-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="61f0b-225">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 使用全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="61f0b-226">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="61f0b-227">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="61f0b-228">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="61f0b-229">在**小組網站名稱**] 中輸入**Campaign 策略**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="61f0b-230">在**小組網站描述**] 中，輸入**SharePoint 網站的行銷活動策略 （高度機密）**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="61f0b-231">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-232">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="61f0b-233">在瀏覽器中的 [工具] 列中新的**行銷活動策略**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="61f0b-234">在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="61f0b-235">在 [新**的權限**] 索引標籤在瀏覽器中按一下 [**存取要求的設定**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="61f0b-236">**存取要求設定**] 對話方塊中，清除 [**允許成員] 共用網站和個別的檔案及資料夾**並**允許邀請其他人網站成員 」 群組的成員**（使已取消選取所有的三個核取方塊），然後按一下 [ **確定**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="61f0b-237">清單中的 [ **Campaign 策略成員**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="61f0b-238">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="61f0b-239">在 [**共用**] 對話方塊中，輸入**資深和策略性人員**、 選取它，，然後按一下 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="61f0b-240">按一下 [ **Campaign 策略擁有者**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="61f0b-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="61f0b-241">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="61f0b-242">在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="61f0b-243">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="61f0b-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="61f0b-244">關閉瀏覽器中的 [**人員與群組**] 索引標籤、 [瀏覽器中的 [**戰役策略首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="61f0b-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="61f0b-245">設定權限的結果如下︰</span><span class="sxs-lookup"><span data-stu-id="61f0b-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="61f0b-246">**行銷活動策略成員**SharePoint 群組包含只**資深和策略性人員**群組 （其中包含只候選項目、 ChiefOfStaff，以及 Strategic1 使用者帳戶） 和**Campaign 策略**群組 （其中包含僅限全域管理員使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="61f0b-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="61f0b-247">**行銷活動策略擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="61f0b-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="61f0b-248">**行銷活動策略訪客**SharePoint 群組沒有包含群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="61f0b-249">成員無法修改站台層級權限 （這可以只來完成**Campaign 策略擁有人**群組的成員）。</span><span class="sxs-lookup"><span data-stu-id="61f0b-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="61f0b-p105">其他使用者帳戶無法存取之網站或其資源的更新或要求網站的存取權。全域管理員或**Campaign 策略擁有者**群組的成員必須完成網站的其他權限。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="61f0b-252">接下來，設定高度機密標籤 Campaign 策略小組網站的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="61f0b-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="61f0b-253">**戰役策略首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="61f0b-254">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="61f0b-255">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="61f0b-256">在**套用設定的標籤**、 選取**高度機密**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="61f0b-p106">接下來，設定 DLP 原則，封鎖使用者時階級與組織外的高度機密標籤上的 SharePoint Online 小組網站的文件。此 DLP 原則將會套用至 Campaign 策略網站中的資源。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="61f0b-259">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 與有安全性管理員或公司管理員角色的帳戶。</span><span class="sxs-lookup"><span data-stu-id="61f0b-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="61f0b-260">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="61f0b-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="61f0b-261">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="61f0b-262">在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="61f0b-263">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="61f0b-264">在**您的原則名稱**] 窗格中，輸入**高度機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="61f0b-265">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="61f0b-266">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="61f0b-267">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="61f0b-268">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="61f0b-269">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**高度機密**的標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="61f0b-270">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="61f0b-271">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="61f0b-272">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="61f0b-273">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="61f0b-274">[文字] 方塊中輸入或貼上下列：</span><span class="sxs-lookup"><span data-stu-id="61f0b-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="61f0b-p107">與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="61f0b-278">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="61f0b-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="61f0b-279">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，選取**需要覆寫業務上理由**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="61f0b-280">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="61f0b-281">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="61f0b-282">使用中[與 Office 365 系統管理中心啟動 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)的指示。</span><span class="sxs-lookup"><span data-stu-id="61f0b-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="61f0b-283">接下來，設定 Azure 資訊保護與新範圍的原則和子標籤保護和權限的下列步驟：</span><span class="sxs-lookup"><span data-stu-id="61f0b-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="61f0b-p108">Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="61f0b-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="61f0b-286">在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="61f0b-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="61f0b-287">如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="61f0b-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="61f0b-288">在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="61f0b-289">**Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="61f0b-290">輸入**CampaignStrategy** [**原則名稱**] 及 [**標籤 Campaign 策略小組網站中的文件**中**描述**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="61f0b-291">按一下 [**選取哪些使用者或群組取得此原則 > 使用者/群組**，然後選取**資深和策略的人員**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="61f0b-292">按一下 [**選取 > [確定]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="61f0b-293">**高度機密**標籤中，按一下省略符號 （...）] 和 [**新增子標籤**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="61f0b-294">輸入**名稱**與**描述**標籤的描述的子標籤名稱。</span><span class="sxs-lookup"><span data-stu-id="61f0b-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="61f0b-295">在**設定文件及包含此標籤的電子郵件的權限**，請按一下 [**保護**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="61f0b-296">在 [**保護**] 區段中，按一下 [ **Azure （雲端索引鍵）**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="61f0b-297">在**保護**blade，**保護設定**] 下按一下 [ **+ 新增權限**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="61f0b-298">在**新增權限**blade 中，**指定使用者與群組**] 下按一下 [ **+ 瀏覽目錄]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="61f0b-299">在**AAD 使用者與群組**] 窗格中，選取**資深和策略的人員**，然後再按一下 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="61f0b-300">在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="61f0b-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="61f0b-301">按兩次 [**確定]** 。</span><span class="sxs-lookup"><span data-stu-id="61f0b-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="61f0b-302">在**子標籤**blade 中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="61f0b-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="61f0b-303">關閉新範圍的原則 blade。</span><span class="sxs-lookup"><span data-stu-id="61f0b-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="61f0b-304">在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**] 及 [ **[是]**。</span><span class="sxs-lookup"><span data-stu-id="61f0b-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="61f0b-305">您現在可以開始建立下列四個網站中的文件並在您的試用版訂閱中測試其具有不同的使用者帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="61f0b-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="61f0b-306">若要保護與 Azure 資訊保護及這個新的標籤文件，您必須在測試電腦上的 [[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 從 Office 365 入口網站安裝 Office 並再登入從 Microsoft Word 中**帳戶資深和策略性人員**您試用版訂閱的群組。</span><span class="sxs-lookup"><span data-stu-id="61f0b-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="61f0b-307">請參閱</span><span class="sxs-lookup"><span data-stu-id="61f0b-307">See Also</span></span>

[<span data-ttu-id="61f0b-308">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="61f0b-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="61f0b-309">設定群組及使用者政治 campaign 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="61f0b-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="61f0b-310">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="61f0b-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="61f0b-311">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="61f0b-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




