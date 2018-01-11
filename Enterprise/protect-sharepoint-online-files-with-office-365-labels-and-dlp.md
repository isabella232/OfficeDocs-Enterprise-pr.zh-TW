---
title: "保護 SharePoint Online 與 Office 365 標籤和 DLP 檔案"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: "摘要： 適用於具有不同的層級的資訊保護的 SharePoint Online 小組網站的 Office 365 標籤和資料外洩防護 (DLP) 原則。"
ms.openlocfilehash: dd4f71d8fae458d6d20f7a5b35b46e14a72853f1
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="6fb31-103">保護 SharePoint Online 與 Office 365 標籤和 DLP 檔案</span><span class="sxs-lookup"><span data-stu-id="6fb31-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="6fb31-104">**摘要：**適用於具有不同的層級的資訊保護的 SharePoint Online 小組網站的 Office 365 標籤和資料外洩防護 (DLP) 原則。</span><span class="sxs-lookup"><span data-stu-id="6fb31-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="6fb31-p101">使用本文中的步驟來設計及部署 Office 365 標籤和 [比較基準、 機密、 和高度機密 SharePoint Online 小組網站的 DLP 原則。如需保護這些三層的詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6fb31-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="6fb31-107">SharePoint Online 網站的 office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fb31-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="6fb31-108">若要建立的三個階段，然後指派 Office 365 標籤至 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="6fb31-108">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="6fb31-109">階段 1： 判斷 Office 365 標籤名稱</span><span class="sxs-lookup"><span data-stu-id="6fb31-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="6fb31-p102">在此階段中，可決定您的 Office 365 標籤的四個層級的資訊保護套用至 SharePoint Online 小組網站的名稱。下表列出每個層級的建議的名稱。</span><span class="sxs-lookup"><span data-stu-id="6fb31-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="6fb31-112">**SharePoint Online 小組網站保護層級**</span><span class="sxs-lookup"><span data-stu-id="6fb31-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="6fb31-113">**標籤名稱**</span><span class="sxs-lookup"><span data-stu-id="6fb31-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6fb31-114">[比較基準公用</span><span class="sxs-lookup"><span data-stu-id="6fb31-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="6fb31-115">內部公用</span><span class="sxs-lookup"><span data-stu-id="6fb31-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="6fb31-116">[比較基準私人</span><span class="sxs-lookup"><span data-stu-id="6fb31-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="6fb31-117">私人</span><span class="sxs-lookup"><span data-stu-id="6fb31-117">Private</span></span>  <br/> |
|<span data-ttu-id="6fb31-118">機密</span><span class="sxs-lookup"><span data-stu-id="6fb31-118">Sensitive</span></span>  <br/> |<span data-ttu-id="6fb31-119">機密</span><span class="sxs-lookup"><span data-stu-id="6fb31-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="6fb31-120">高度機密</span><span class="sxs-lookup"><span data-stu-id="6fb31-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="6fb31-121">高度機密</span><span class="sxs-lookup"><span data-stu-id="6fb31-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="6fb31-122">階段 2： 建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fb31-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="6fb31-123">在此階段中，您可以建立，然後發佈的不同層級的資訊保護您決定的標籤。</span><span class="sxs-lookup"><span data-stu-id="6fb31-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="6fb31-124">若要建立之標籤，您可以使用 Office 365 系統管理中心或 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6fb31-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="6fb31-125">使用 Office 365 系統管理中心建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fb31-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="6fb31-p103">Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="6fb31-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6fb31-128">從**Microsoft Office Home** ] 索引標籤上，按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="6fb31-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="6fb31-129">從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中，按一下 [**系統中心 > 安全性&amp;規範**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-129">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="6fb31-130">從新**首頁-安全性&amp;規範**] 索引標籤的瀏覽器中，按一下 [**分類 > 標籤**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-130">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="6fb31-131">從**首頁 > 標籤**] 窗格中，按一下 [**建立] 標籤**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="6fb31-132">在**您的標籤名稱**] 窗格中，輸入標籤的名稱並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6fb31-133">在 [**標籤設定**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="6fb31-134">在**檢閱您的設定**] 窗格中，按一下 [**建立此標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-134">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="6fb31-135">重複步驟 5-8 額外的標籤。</span><span class="sxs-lookup"><span data-stu-id="6fb31-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="6fb31-136">使用 PowerShell 建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fb31-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="6fb31-137">[連線至 Office 365 安全性&amp;規範中心使用遠端 PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)並指定有安全性管理員或公司管理員角色的帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="6fb31-137">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="6fb31-138">填寫的標籤名稱清單，並再 PowerShell 命令提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="6fb31-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="6fb31-139">接下來，請使用下列步驟發佈新的 Office 365 標籤。</span><span class="sxs-lookup"><span data-stu-id="6fb31-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="6fb31-140">從**首頁 > 標籤**窗格安全性&amp;規範中心，按一下 [**發佈標籤**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="6fb31-141">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**選擇標籤發佈**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="6fb31-142">在 [**選擇標籤**] 窗格中，按一下 [**新增**] 並選取所有的四個標籤。</span><span class="sxs-lookup"><span data-stu-id="6fb31-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="6fb31-143">按一下 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="6fb31-144">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="6fb31-145">在 [**選擇位置**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="6fb31-146">在**您的原則名稱**] 窗格中，在 [**名稱**] 中輸入您的集之標籤的名稱然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6fb31-147">在**檢閱您的設定**] 窗格中，按一下 [**發佈標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="6fb31-148">階段 3： 將 Office 365 標籤套用至 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="6fb31-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="6fb31-149">使用下列步驟將 Office 365 標籤套用至您的 SharePoint Online 小組網站的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6fb31-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="6fb31-150">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [ **SharePoint** ] 磚。</span><span class="sxs-lookup"><span data-stu-id="6fb31-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="6fb31-151">新**SharePoint** ] 索引標籤上瀏覽器中，按一下 [需要指派 Office 365 標籤的網站]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="6fb31-152">在 [新增 SharePoint 網站] 索引標籤的瀏覽器中按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="6fb31-153">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="6fb31-154">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="6fb31-155">在**套用設定的標籤**、 選取適當的標籤] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-155">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="6fb31-156">關閉 SharePoint Online 網站] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fb31-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="6fb31-157">重複步驟 3-8 指派給其他的 SharePoint Online 網站的 Office 365 標籤。</span><span class="sxs-lookup"><span data-stu-id="6fb31-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="6fb31-158">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="6fb31-158">Here is your resulting configuration.</span></span>
  
![用於四種類型 SharePoint Online 小組網站的 Office 365 標籤。](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="6fb31-160">SharePoint Online 網站的 DLP 原則</span><span class="sxs-lookup"><span data-stu-id="6fb31-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="6fb31-161">使用下列步驟來設定 DLP 原則階級組織外部的 SharePoint Online 機密小組網站上的文件時通知使用者。</span><span class="sxs-lookup"><span data-stu-id="6fb31-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="6fb31-162">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="6fb31-162">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="6fb31-163">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-163">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="6fb31-164">在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6fb31-165">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="6fb31-166">在**您的原則名稱**] 窗格中，輸入機密層級的 DLP 原則的名稱在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-166">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6fb31-167">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6fb31-168">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6fb31-169">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6fb31-170">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6fb31-171">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**機密**標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="6fb31-172">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6fb31-173">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6fb31-174">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6fb31-175">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6fb31-176">[文字] 方塊中輸入或貼上下列：</span><span class="sxs-lookup"><span data-stu-id="6fb31-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6fb31-p104">與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="6fb31-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="6fb31-180">或者，輸入或貼上的指示使用者如何共用您組織外部檔案自己原則提示。</span><span class="sxs-lookup"><span data-stu-id="6fb31-180">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="6fb31-181">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="6fb31-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="6fb31-182">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，清除**封鎖來自共用、 人員及限制共用內容的存取權**] 核取方塊，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="6fb31-183">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6fb31-184">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-184">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="6fb31-185">以下是您所產生的設定以便機密的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="6fb31-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![使用敏感性 Office 365 標籤之隔離 SharePoint Online 小組網站的 DLP 原則。](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="6fb31-187">接下來，使用下列步驟來設定 DLP 原則，封鎖使用者階級組織外部的 SharePoint Online 高度機密小組網站上的文件時。</span><span class="sxs-lookup"><span data-stu-id="6fb31-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="6fb31-188">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="6fb31-188">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="6fb31-189">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-189">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="6fb31-190">在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6fb31-191">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="6fb31-192">在**您的原則名稱**] 窗格中，輸入極高機密層級的 DLP 原則的名稱在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6fb31-193">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6fb31-194">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6fb31-195">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6fb31-196">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6fb31-197">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**高度機密**的標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="6fb31-198">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6fb31-199">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="6fb31-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6fb31-200">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6fb31-201">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6fb31-202">[文字] 方塊中輸入或貼上下列：</span><span class="sxs-lookup"><span data-stu-id="6fb31-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6fb31-p105">與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="6fb31-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="6fb31-206">或者，輸入或貼上的指示使用者如何共用您組織外部檔案自己原則提示。</span><span class="sxs-lookup"><span data-stu-id="6fb31-206">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="6fb31-207">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="6fb31-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="6fb31-208">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，選取**需要覆寫業務上理由**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="6fb31-209">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6fb31-210">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="6fb31-210">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="6fb31-211">以下是您所產生的設定以便高機密性 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="6fb31-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![使用高度機密 Office 365 標籤之隔離 SharePoint Online 小組網站的 DLP 原則。](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="6fb31-213">下一步</span><span class="sxs-lookup"><span data-stu-id="6fb31-213">Next step</span></span>

[<span data-ttu-id="6fb31-214">保護與 Azure 資訊保護的 SharePoint Online 檔案</span><span class="sxs-lookup"><span data-stu-id="6fb31-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="6fb31-215">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fb31-215">See Also</span></span>

[<span data-ttu-id="6fb31-216">安全的 SharePoint Online 網站及檔案</span><span class="sxs-lookup"><span data-stu-id="6fb31-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6fb31-217">安全的開發人員/測試環境中的 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="6fb31-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="6fb31-218">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="6fb31-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="6fb31-219">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="6fb31-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


