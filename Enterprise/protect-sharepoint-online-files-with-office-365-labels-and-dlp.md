---
title: 使用 Office 365 標籤與 DLP 來保護 SharePoint Online 檔案
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 摘要：使用各種資訊保護層級，對 SharePoint Online 小組網站套用 Office 365 標籤和資料外洩防護 (DLP) 原則。
ms.openlocfilehash: 52617e43f5c1bcb2ab958e751734a2f948ceba37
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="6fbbb-103">使用 Office 365 標籤與 DLP 來保護 SharePoint Online 檔案</span><span class="sxs-lookup"><span data-stu-id="6fbbb-103">Protect SharePoint Online files with Office 365 labels and Data Loss Prevention</span></span>

 <span data-ttu-id="6fbbb-104">**摘要：** 使用各種資訊保護層級，對 SharePoint Online 小組網站套用 Office 365 標籤和資料外洩防護 (DLP) 原則。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="6fbbb-p101">您可以使用本文中的步驟，為基準、機密和高度機密 SharePoint Online 小組網站設計及部署 Office 365 標籤和資料外洩防護 (DLP) 原則。如需這三種保護層級的詳細資訊，請參閱[保護 SharePoint Online 網站與檔案](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-p101">Use the steps in this article to design and deploy Office 365 labels and Data Loss Prevention (DLP) policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="6fbbb-107">適用於 SharePoint Online 網站的 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fbbb-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="6fbbb-108">建立 Office 365 標籤並將其指派給 SharePoint Online 小組網站時的三個階段。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-108">You must complete the following three phases when creating and assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="6fbbb-109">階段 1：決定 Office 365 標籤名稱</span><span class="sxs-lookup"><span data-stu-id="6fbbb-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="6fbbb-p102">在此階段中，您會為套用至 SharePoint Online 小組網站的四種資訊保護層級，決定其 Office 365 標籤的名稱。 下表列出每種層級的建議名稱。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="6fbbb-112">**SharePoint Online 小組網站保護層級**</span><span class="sxs-lookup"><span data-stu-id="6fbbb-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="6fbbb-113">**標籤名稱**</span><span class="sxs-lookup"><span data-stu-id="6fbbb-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6fbbb-114">基準-公用</span><span class="sxs-lookup"><span data-stu-id="6fbbb-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="6fbbb-115">內部公用</span><span class="sxs-lookup"><span data-stu-id="6fbbb-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="6fbbb-116">基準-私人</span><span class="sxs-lookup"><span data-stu-id="6fbbb-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="6fbbb-117">Private</span><span class="sxs-lookup"><span data-stu-id="6fbbb-117">Private</span></span>  <br/> |
|<span data-ttu-id="6fbbb-118">敏感性</span><span class="sxs-lookup"><span data-stu-id="6fbbb-118">Sensitive</span></span>  <br/> |<span data-ttu-id="6fbbb-119">敏感性</span><span class="sxs-lookup"><span data-stu-id="6fbbb-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="6fbbb-120">高度機密</span><span class="sxs-lookup"><span data-stu-id="6fbbb-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="6fbbb-121">高度機密</span><span class="sxs-lookup"><span data-stu-id="6fbbb-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="6fbbb-122">階段 2：建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fbbb-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="6fbbb-123">在此階段中，您會為不同資訊保護層級建立所決定的標籤，然後將它發佈。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="6fbbb-124">若要建立標籤，您可以使用 Office 365 系統管理中心或 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="6fbbb-125">使用 Office 365 系統管理中心建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fbbb-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="6fbbb-p103">使用具有安全性系統管理員或公司系統管理員角色的帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6fbbb-128">從 [Microsoft Office 的首頁]**** 索引標籤中，按一下 [管理]**** 磚。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="6fbbb-129">從瀏覽器的新 [Office 系統管理中心]**** 索引標籤中，按一下 [系統管理中心] > [安全性 &amp; 合規性]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-129">From the new Office Admin center tab of your browser, click Admin centers > Security & Compliance.</span></span>
    
4. <span data-ttu-id="6fbbb-130">從瀏覽器的新 [首頁 - 安全性 &amp; 合規性]**** 索引標籤中，按一下 [分類] > [標籤]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-130">From the new Home – Security & Compliance tab of your browser, click Classifications > Labels.</span></span>
    
5. <span data-ttu-id="6fbbb-131">從 [首頁] > [標籤]**** 窗格中，按一下 [建立標籤]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="6fbbb-132">在 [命名您的標籤]**** 窗格中，鍵入標籤的名稱，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6fbbb-133">在 [標籤設定]**** 窗格中，按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="6fbbb-134">在 [檢閱您的設定]**** 窗格中，按一下 [建立此標籤]****，然後按一下 [關閉]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-134">In the **Review your settings pane**, click **Create**, and click **Close**.</span></span>
    
9. <span data-ttu-id="6fbbb-135">針對其他標籤重複步驟 5 至 8。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="6fbbb-136">使用 PowerShell 建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="6fbbb-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="6fbbb-137">[使用遠端 PowerShell 連線到 Office 365 安全 &amp;規範中心，](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)並指定具有安全性系統管理員或公司系統管理員角色之帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-137">Connect to the Office 365 Security & Compliance Center using remote PowerShell and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="6fbbb-138">填寫標籤名稱清單，然後在 PowerShell 命令提示字元中執行這些命令：</span><span class="sxs-lookup"><span data-stu-id="6fbbb-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="6fbbb-139">接下來，使用下列步驟來發佈新的 Office 365 標籤。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="6fbbb-140">從安全性 &amp; 合規性的 [首頁] > [標籤]**** 窗格中，按一下 [發佈標籤]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="6fbbb-141">在 [選擇要發佈的標籤]**** 窗格中，按一下 [選擇要發佈的標籤]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="6fbbb-142">在 [Choose labels]\(選擇標籤)**** 窗格中，按一下 [新增]**** 並選取所有四個標籤。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="6fbbb-143">按一下 [完成]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="6fbbb-144">在 [選擇要發佈的標籤]**** 窗格上，按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="6fbbb-145">在 [選擇位置]**** 窗格中，按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="6fbbb-146">在 [命名您的原則]**** 窗格的 [名稱]**** 中，鍵入標籤集的名稱，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and click **Next**.</span></span>
    
8. <span data-ttu-id="6fbbb-147">在 [檢閱您的設定]**** 窗格中，按一下 [發佈標籤]****，然後按一下 [關閉]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="6fbbb-148">階段 3：將 Office 365 標籤套用至 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="6fbbb-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="6fbbb-149">使用下列步驟，將 Office 365 標籤套用至 SharePoint Online 小組網站的文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="6fbbb-150">從 [Microsoft Office 的首頁]**** 瀏覽器索引標籤，按一下 [SharePoint]**** 磚。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="6fbbb-151">在新的 [SharePoint]**** 瀏覽器索引標籤中，按一下需要指派 Office 365 標籤的網站。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="6fbbb-152">在瀏覽器的新 [SharePoint 網站] 索引標籤中，按一下 [文件]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="6fbbb-153">按一下設定圖示，然後按一下 [文件庫設定]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="6fbbb-154">在 [權限與管理]**** 下，按一下 [Apply label to items in this library]\(將標籤套用至此文件庫中的項目)****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="6fbbb-155">在 [設定] - [套用標籤]**** 中，選取適當的標籤，然後按一下 [儲存]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-155">In **Settings-Apply Label**, select the appropriate label, and click **Save**.</span></span>
    
7. <span data-ttu-id="6fbbb-156">關閉 SharePoint Online 網站的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="6fbbb-157">重複步驟 3-8，將 Office 365 標籤指派給其他 SharePoint Online 網站。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="6fbbb-158">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-158">Here is your resulting configuration.</span></span>
  
![用於四種類型 SharePoint Online 小組網站的 Office 365 標籤。](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="6fbbb-160">適用於 SharePoint Online 網站的 DLP 原則</span><span class="sxs-lookup"><span data-stu-id="6fbbb-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="6fbbb-161">使用下列步驟來設定 DLP 原則，以在使用者共用組織外部 SharePoint Online 機密小組網站上的文件時通知使用者。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="6fbbb-162">從瀏覽器的 [Microsoft Office 的首頁]**** 索引標籤中，按一下 [安全性 &amp; 合規性]**** 磚。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-162">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="6fbbb-163">在瀏覽器的新 [安全性 &amp; 合規性]**** 索引標籤上，按一下 [資料外洩防護] > [原則]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-163">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="6fbbb-164">在 [資料外洩防護]**** 窗格中，按一下 [+ 建立原則]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6fbbb-165">在 [從範本開始或建立自訂原則]**** 窗格中，按一下 [自訂]****，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="6fbbb-166">在 [命名您的原則]**** 窗格的 [名稱]**** 中，鍵入機密層級 DLP 原則的名稱，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-166">In the Name your policy pane, type the name for the sensitive level DLP policy in Name, and click Next.</span></span>
    
6. <span data-ttu-id="6fbbb-167">在 [選擇位置]**** 窗格中，按一下 [讓我選擇特定位置]****，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6fbbb-168">在位置清單中，停用 [Exchange 電子郵件]**** 和 [OneDrive 帳戶]**** 位置，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts locations**, and click **Next**.</span></span>
    
8. <span data-ttu-id="6fbbb-169">在 [自訂您要保護的機密資訊類型]**** 窗格中，按一下 [編輯]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6fbbb-170">在 [選擇要保護的內容類型]**** 窗格中，從下拉式方塊按一下 [新增]****，然後按一下 [標籤]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6fbbb-171">在 [標籤]**** 窗格中，按一下 [+ 新增]**** 並選取 [敏感性]**** 標籤，然後依序按一下 [新增]**** 和 [完成]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="6fbbb-172">在 [選擇要保護的內容類型]**** 窗格中，按一下 [儲存]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6fbbb-173">在 [Customize the types of sensitive info you want to protect]\(自訂您要保護的機密資訊類型)**** 窗格中，按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6fbbb-174">在 [What do you want to do if we detect sensitive info?]\(如果偵測到機密資訊要如何處理?)**** 窗格中，按一下 [Customize the tip and email]\(自訂提示和電子郵件)****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6fbbb-175">在 [Customize policy tips and email notifications]\(自訂原則提示和電子郵件通知)**** 窗格中，按一下 [Customize the policy tip text]\(自訂原則提示文字)****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6fbbb-176">在文字方塊中，鍵入或貼上下列內容：</span><span class="sxs-lookup"><span data-stu-id="6fbbb-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6fbbb-p104">若要與組織外部的使用者共用，請下載檔案，然後將它開啟。 依序按一下 [檔案]、[保護文件] 和 [以密碼加密]，然後指定強式密碼。 以個別電子郵件或其他通訊方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="6fbbb-180">或者，鍵入或貼上您自己的原則提示，以指示使用者如何共用組織外部的檔案。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-180">Or type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="6fbbb-181">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="6fbbb-182">在 [如果偵測到機密資訊要如何處理?]**** 窗格中，清除 [禁止人員共用及限制共用內容的存取]**** 核取方塊，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and click **Next**.</span></span>
    
18. <span data-ttu-id="6fbbb-183">在 [要先開啟原則或測試內容嗎?]**** 窗格中，按一下 [是]**** 立即將它開啟，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6fbbb-184">在 [檢閱您的設定]**** 窗格中，按一下 [建立]****，然後按一下 [關閉]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-184">In the **Review your settings** pane, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="6fbbb-185">以下是敏感性 SharePoint Online 小組網站的設定結果。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![使用敏感性 Office 365 標籤之隔離 SharePoint Online 小組網站的 DLP 原則。](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="6fbbb-187">接下來，使用下列步驟來設定 DLP 原則，以在使用者共用組織外部 SharePoint Online 高度機密小組網站上的文件時封鎖使用者。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="6fbbb-188">從瀏覽器的 [Microsoft Office 的首頁]**** 索引標籤中，按一下 [安全性 &amp; 合規性]**** 磚。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-188">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="6fbbb-189">在瀏覽器的新 [安全性 &amp; 合規性]**** 索引標籤上，按一下 [資料外洩防護] > [原則]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-189">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="6fbbb-190">在 [資料外洩防護]**** 窗格中，按一下 [+ 建立原則]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="6fbbb-191">在 [從範本開始或建立自訂原則]**** 窗格中，按一下 [自訂]****，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="6fbbb-192">在 [命名您的原則]**** 窗格的 [名稱]**** 中，鍵入高度機密層級 DLP 原則的名稱，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and click **Next**.</span></span>
    
6. <span data-ttu-id="6fbbb-193">在 [選擇位置]**** 窗格中，按一下 [讓我選擇特定位置]****，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="6fbbb-194">在位置清單中，停用 [Exchange 電子郵件]**** 和 [OneDrive 帳戶]**** 位置，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts locations**, and click **Next**.</span></span>
    
8. <span data-ttu-id="6fbbb-195">在 [自訂您要保護的機密資訊類型]**** 窗格中，按一下 [編輯]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="6fbbb-196">在 [選擇要保護的內容類型]**** 窗格中，從下拉式方塊按一下 [新增]****，然後按一下 [標籤]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="6fbbb-197">在 [標籤]**** 窗格中，按一下 [+ 新增]****，並選取 [高度機密]**** 標籤，然後依序按一下 [新增]**** 和 [完成]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential label**, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="6fbbb-198">在 [選擇要保護的內容類型]**** 窗格中，按一下 [儲存]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="6fbbb-199">在 [Customize the types of sensitive info you want to protect]\(自訂您要保護的機密資訊類型)**** 窗格中，按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="6fbbb-200">在 [What do you want to do if we detect sensitive info?]\(如果偵測到機密資訊要如何處理?)**** 窗格中，按一下 [Customize the tip and email]\(自訂提示和電子郵件)****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="6fbbb-201">在 [Customize policy tips and email notifications]\(自訂原則提示和電子郵件通知)**** 窗格中，按一下 [Customize the policy tip text]\(自訂原則提示文字)****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="6fbbb-202">在文字方塊中，鍵入或貼上下列內容：</span><span class="sxs-lookup"><span data-stu-id="6fbbb-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="6fbbb-p105">若要與組織外部的使用者共用，請下載檔案，然後將它開啟。 依序按一下 [檔案]、[保護文件] 和 [以密碼加密]，然後指定強式密碼。 以個別電子郵件或其他通訊方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="6fbbb-206">或者，鍵入或貼上您自己的原則提示，以指示使用者如何共用組織外部的檔案。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-206">Or type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="6fbbb-207">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="6fbbb-208">在 [如果偵測到機密資訊要如何處理?]**** 窗格中，選取 [需要有業務上的正當理由才能覆寫]****，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="6fbbb-209">在 [要先開啟原則或測試內容嗎?]**** 窗格中，按一下 [是]**** 立即將它開啟，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="6fbbb-210">在 [檢閱您的設定]**** 窗格中，按一下 [建立]****，然後按一下 [關閉]****。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-210">In the **Review your settings** pane, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="6fbbb-211">以下是高度機密 SharePoint Online 小組網站的設定結果。</span><span class="sxs-lookup"><span data-stu-id="6fbbb-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![使用高度機密 Office 365 標籤之隔離 SharePoint Online 小組網站的 DLP 原則。](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="6fbbb-213">下一步</span><span class="sxs-lookup"><span data-stu-id="6fbbb-213">Next step</span></span>

[<span data-ttu-id="6fbbb-214">使用 Azure 資訊保護來保護 SharePoint Online 檔案</span><span class="sxs-lookup"><span data-stu-id="6fbbb-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="6fbbb-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fbbb-215">See Also</span></span>

[<span data-ttu-id="6fbbb-216">保護 SharePoint Online 網站與檔案</span><span class="sxs-lookup"><span data-stu-id="6fbbb-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6fbbb-217">在開發/測試環境中保護 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="6fbbb-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="6fbbb-218">適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南</span><span class="sxs-lookup"><span data-stu-id="6fbbb-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="6fbbb-219">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="6fbbb-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


