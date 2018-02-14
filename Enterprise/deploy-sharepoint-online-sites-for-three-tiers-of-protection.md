---
title: "部署三層的保護的 SharePoint Online 的網站"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "摘要： 建立及設定的不同層級的資訊保護的 SharePoint Online 小組網站。"
ms.openlocfilehash: f015ce8d7c91d02ce5dc0a7791ba22a53bc2933f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="56fcc-103">部署三層的保護的 SharePoint Online 的網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="56fcc-104">**摘要：**建立及設定的不同層級的資訊保護的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="56fcc-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="56fcc-p101">使用本文中的步驟來設計及部署比較基準 」、 機密、 和高度機密 SharePoint Online 小組網站。如需保護這些三層的詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="56fcc-107">[比較基準 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="56fcc-p102">[比較基準保護包含這兩個公用及私人小組網站。可以探索和組織中的任何人存取公用小組網站。私用網站可以只探索和存取小組網站相關聯的 Office 365 群組的成員。這兩個小組網站這類允許成員與其他人] 共用網站。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="56fcc-112">公用</span><span class="sxs-lookup"><span data-stu-id="56fcc-112">Public</span></span>

<span data-ttu-id="56fcc-113">若要建立基準 SharePoint Online 小組網站與公用存取和權限，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="56fcc-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="56fcc-p103">Office 365 入口網站也可用於管理 SharePoint Online 小組網站 （SharePoint Online 系統管理員） 帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="56fcc-116">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="56fcc-117">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="56fcc-118">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="56fcc-119">在**站台名稱**] 中，輸入公用小組網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fcc-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="56fcc-120">在**小組網站描述**] 中，輸入網站的用途說明。</span><span class="sxs-lookup"><span data-stu-id="56fcc-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="56fcc-121">**隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="56fcc-122">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="56fcc-123">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="56fcc-123">Here is your resulting configuration.</span></span>
  
![適用於公用 SharePoint Online 小組網站的基準層級保護。](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="56fcc-125">私人</span><span class="sxs-lookup"><span data-stu-id="56fcc-125">Private</span></span>

<span data-ttu-id="56fcc-126">若要建立基準 SharePoint Online 小組網站與私人 access 和權限，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="56fcc-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="56fcc-p104">Office 365 入口網站也可用於管理 SharePoint Online 小組網站 （SharePoint Online 系統管理員） 帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="56fcc-129">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="56fcc-130">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="56fcc-131">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="56fcc-132">在**站台名稱**] 中輸入私人小組網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fcc-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="56fcc-133">在**小組網站描述] 中，**輸入網站的用途說明。</span><span class="sxs-lookup"><span data-stu-id="56fcc-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="56fcc-134">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="56fcc-135">在**您要新增誰？** ] 窗格中，在**新增成員**中，輸入能夠存取這私人小組網站的使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fcc-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="56fcc-136">當您完成初始組成員新增至網站，按一下 [**完成時間**</span><span class="sxs-lookup"><span data-stu-id="56fcc-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="56fcc-137">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="56fcc-137">Here is your resulting configuration.</span></span>
  
![適用於私人 SharePoint Online 小組網站的基準層級保護。](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="56fcc-139">機密的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="56fcc-140">機密的 SharePoint Online 小組網站是隔離的小組網站] 表示權限所控制透過而不是在小組網站相關聯的 Office 365 群組的成員資格的 SharePoint 群組的成員資格。</span><span class="sxs-lookup"><span data-stu-id="56fcc-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="56fcc-141">若要建立的隔離的小組網站，有兩個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="56fcc-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="56fcc-142">步驟 1： 設計在隔離的網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="56fcc-143">若要設計隔離的小組網站，您需要決定：</span><span class="sxs-lookup"><span data-stu-id="56fcc-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="56fcc-144">您的 SharePoint 群組和權限層級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="56fcc-145">將您的 SharePoint 群組的成員存取群組的屬性集。</span><span class="sxs-lookup"><span data-stu-id="56fcc-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="56fcc-146">存取群組的建議的設定是一個網站成員，一個網站檢視者另一個網站管理員。</span><span class="sxs-lookup"><span data-stu-id="56fcc-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="56fcc-147">您是否要使用的巢狀存取群組內的群組。</span><span class="sxs-lookup"><span data-stu-id="56fcc-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="56fcc-148">例如，建議的群組結構和權限層級看起來如下：</span><span class="sxs-lookup"><span data-stu-id="56fcc-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="56fcc-149">**SharePoint 群組**</span><span class="sxs-lookup"><span data-stu-id="56fcc-149">**SharePoint group**</span></span>|<span data-ttu-id="56fcc-150">**權限層級**</span><span class="sxs-lookup"><span data-stu-id="56fcc-150">**Permission level**</span></span>|<span data-ttu-id="56fcc-151">**存取群組 （範例）**</span><span class="sxs-lookup"><span data-stu-id="56fcc-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="56fcc-152">[網站名稱]成員</span><span class="sxs-lookup"><span data-stu-id="56fcc-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="56fcc-153">編輯</span><span class="sxs-lookup"><span data-stu-id="56fcc-153">Edit</span></span>  <br/> |<span data-ttu-id="56fcc-154">[網站名稱]成員</span><span class="sxs-lookup"><span data-stu-id="56fcc-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="56fcc-155">[網站名稱]訪客</span><span class="sxs-lookup"><span data-stu-id="56fcc-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="56fcc-156">讀取</span><span class="sxs-lookup"><span data-stu-id="56fcc-156">Read</span></span>  <br/> |<span data-ttu-id="56fcc-157">[網站名稱]檢視程式</span><span class="sxs-lookup"><span data-stu-id="56fcc-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="56fcc-158">[網站名稱]擁有者</span><span class="sxs-lookup"><span data-stu-id="56fcc-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="56fcc-159">完全控制</span><span class="sxs-lookup"><span data-stu-id="56fcc-159">Full control</span></span>  <br/> |<span data-ttu-id="56fcc-160">[網站名稱]系統管理員</span><span class="sxs-lookup"><span data-stu-id="56fcc-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="56fcc-p105">小組網站的預設會建立 SharePoint 群組與權限層級。您需要確定您的存取群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="56fcc-163">如需設計程序的詳細資訊，請參閱 ＜ [Design 隔離的 SharePoint Online 小組網站](design-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="56fcc-164">步驟 2： 部署隔離的網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="56fcc-165">若要部署在隔離的網站，您必須先：</span><span class="sxs-lookup"><span data-stu-id="56fcc-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="56fcc-166">決定使用者帳戶和群組新增至每個存取群組。</span><span class="sxs-lookup"><span data-stu-id="56fcc-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="56fcc-167">建立存取群組並新增使用者和群組的成員。</span><span class="sxs-lookup"><span data-stu-id="56fcc-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="56fcc-168">如需詳細的步驟，請參閱 ＜**階段 1**的[部署隔離的 SharePoint Online 小組網站](deploy-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="56fcc-169">接下來，您可以建立的 SharePoint Online 小組網站進行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="56fcc-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="56fcc-p106">Office 365 入口網站也可用於管理 SharePoint Online 小組網站 （SharePoint Online 系統管理員） 帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="56fcc-172">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="56fcc-173">新**SharePoint**索引標籤中的瀏覽器中，按一下 [ **+ 建立網站**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="56fcc-174">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="56fcc-175">在**站台名稱**] 中輸入私人小組網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fcc-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="56fcc-176">在**小組網站描述**] 中，輸入的選用描述。</span><span class="sxs-lookup"><span data-stu-id="56fcc-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="56fcc-177">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="56fcc-178">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="56fcc-179">下一步] 從新的 SharePoint Online 小組網站，請使用下列步驟設定權限。</span><span class="sxs-lookup"><span data-stu-id="56fcc-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="56fcc-p107">決定使用者主體名稱 (UPN) 的 IT 管理員或其他負責回應及位址的網站的存取權要求的人員 （belindan@contoso.com 是 UPN 的範例）。寫入該的 UPN： ___。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="56fcc-182">在 [工具] 列中按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="56fcc-183">在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="56fcc-184">新**的權限**] 索引標籤上的瀏覽器中，按一下 [**存取要求設定**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="56fcc-185">在 [**存取要求設定**] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="56fcc-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="56fcc-186">清除 [**允許成員] 共用網站和個別的檔案及資料夾**和**允許邀請其他人網站成員 」 群組的成員**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="56fcc-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="56fcc-187">輸入您的 IT 管理員從步驟 1 的 UPN**傳送存取的所有要求**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="56fcc-188">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="56fcc-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="56fcc-189">在瀏覽器的 [**權限**] 索引標籤中，按一下 [清單中的**[網站名稱] 成員**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="56fcc-190">在 [**人員與群組**，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="56fcc-191">在 [**共用**] 對話方塊中，輸入您的網站成員存取群組此網站的名稱、 選取它，和 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="56fcc-192">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="56fcc-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="56fcc-193">按一下**[網站名稱] 擁有者**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="56fcc-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="56fcc-194">在 [**人員與群組**，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="56fcc-195">在 [**共用**] 對話方塊中，輸入此網站的網站管理員存取群組的名稱、 選取它，和 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="56fcc-196">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="56fcc-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="56fcc-197">按一下**[網站名稱] 訪客**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="56fcc-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="56fcc-198">在 [**人員與群組**，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="56fcc-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="56fcc-199">在 [**共用**] 對話方塊中，輸入此網站的網站檢視者存取群組的名稱、 選取它，和 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="56fcc-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="56fcc-200">關閉瀏覽器的 [**權限**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="56fcc-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="56fcc-201">這些權限設定的結果是：</span><span class="sxs-lookup"><span data-stu-id="56fcc-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="56fcc-202">**[網站名稱] 擁有者**SharePoint 群組包含網站管理員存取群組中的所有成員具有 [**完全控制**」 權限層級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="56fcc-203">**[網站名稱] 成員**SharePoint 群組包含網站成員存取群組中的所有成員具有**編輯**權限等級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="56fcc-204">**[網站名稱] 訪客**SharePoint 群組包含網站檢視者存取群組中的所有成員具有 「**讀取**」 權限等級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="56fcc-205">邀請其他成員的成員的功能已停用。</span><span class="sxs-lookup"><span data-stu-id="56fcc-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="56fcc-206">非成員要求存取的功能已啟用。</span><span class="sxs-lookup"><span data-stu-id="56fcc-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="56fcc-207">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="56fcc-207">Here is your resulting configuration.</span></span>
  
![適用於隔離 SharePoint Online 小組網站的敏感性層級保護。](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="56fcc-209">網站透過群組成員資格之一的存取群組的成員可以現在安全地進行共同作業網站的資源。</span><span class="sxs-lookup"><span data-stu-id="56fcc-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="56fcc-210">高度機密的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="56fcc-211">高度機密的 SharePoint Online 小組網站是隔離的小組網站] 表示權限所控制透過而不是在小組網站相關聯的 Office 365 群組的成員資格的 SharePoint 群組的成員資格。</span><span class="sxs-lookup"><span data-stu-id="56fcc-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="56fcc-212">若要建立高度機密資訊與共同作業的隔離的小組網站，有兩個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="56fcc-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="56fcc-213">步驟 1： 設計在隔離的網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="56fcc-214">若要設計隔離的小組網站，您需要決定：</span><span class="sxs-lookup"><span data-stu-id="56fcc-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="56fcc-215">您的 SharePoint 群組和權限層級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="56fcc-216">將您的 SharePoint 群組的成員存取群組的屬性集。</span><span class="sxs-lookup"><span data-stu-id="56fcc-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="56fcc-217">存取群組的建議的設定是一個網站成員，一個網站檢視者另一個網站管理員。</span><span class="sxs-lookup"><span data-stu-id="56fcc-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="56fcc-218">您是否要使用的巢狀存取群組內的群組。</span><span class="sxs-lookup"><span data-stu-id="56fcc-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="56fcc-219">例如，建議的群組結構和權限層級看起來如下：</span><span class="sxs-lookup"><span data-stu-id="56fcc-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="56fcc-220">**SharePoint 群組**</span><span class="sxs-lookup"><span data-stu-id="56fcc-220">**SharePoint group**</span></span>|<span data-ttu-id="56fcc-221">**權限層級**</span><span class="sxs-lookup"><span data-stu-id="56fcc-221">**Permission level**</span></span>|<span data-ttu-id="56fcc-222">**存取群組 （範例）**</span><span class="sxs-lookup"><span data-stu-id="56fcc-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="56fcc-223">[網站名稱]成員</span><span class="sxs-lookup"><span data-stu-id="56fcc-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="56fcc-224">編輯</span><span class="sxs-lookup"><span data-stu-id="56fcc-224">Edit</span></span>  <br/> |<span data-ttu-id="56fcc-225">[網站名稱]成員</span><span class="sxs-lookup"><span data-stu-id="56fcc-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="56fcc-226">[網站名稱]訪客</span><span class="sxs-lookup"><span data-stu-id="56fcc-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="56fcc-227">讀取</span><span class="sxs-lookup"><span data-stu-id="56fcc-227">Read</span></span>  <br/> |<span data-ttu-id="56fcc-228">[網站名稱]檢視程式</span><span class="sxs-lookup"><span data-stu-id="56fcc-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="56fcc-229">[網站名稱]擁有者</span><span class="sxs-lookup"><span data-stu-id="56fcc-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="56fcc-230">完全控制</span><span class="sxs-lookup"><span data-stu-id="56fcc-230">Full control</span></span>  <br/> |<span data-ttu-id="56fcc-231">[網站名稱]系統管理員</span><span class="sxs-lookup"><span data-stu-id="56fcc-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="56fcc-p108">小組網站的預設會建立 SharePoint 群組與權限層級。您需要確定您的存取群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fcc-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="56fcc-234">如需設計程序的詳細資訊，請參閱 ＜ [Design 隔離的 SharePoint Online 小組網站](design-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="56fcc-235">步驟 2： 部署隔離的網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="56fcc-236">若要部署在隔離的網站，您必須先：</span><span class="sxs-lookup"><span data-stu-id="56fcc-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="56fcc-237">決定每個存取群組的使用者與群組成員</span><span class="sxs-lookup"><span data-stu-id="56fcc-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="56fcc-238">建立存取群組並新增使用者和群組的成員</span><span class="sxs-lookup"><span data-stu-id="56fcc-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="56fcc-239">建立使用您的存取群組隔離的小組網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="56fcc-240">如需詳細的步驟，請參閱 ＜ [Deploy 隔離的 SharePoint Online 小組網站](deploy-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="56fcc-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="56fcc-241">權限設定的結果是：</span><span class="sxs-lookup"><span data-stu-id="56fcc-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="56fcc-242">**[網站名稱] 擁有者**SharePoint 群組包含網站管理員存取群組中的所有成員具有 [**完全控制**」 權限層級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="56fcc-243">**[網站名稱] 成員**SharePoint 群組包含網站成員存取群組中的所有成員具有**編輯**權限等級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="56fcc-244">**[網站名稱] 訪客**SharePoint 群組包含網站檢視者存取群組中的所有成員具有 「**讀取**」 權限等級。</span><span class="sxs-lookup"><span data-stu-id="56fcc-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="56fcc-245">邀請其他成員的成員的功能已停用。</span><span class="sxs-lookup"><span data-stu-id="56fcc-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="56fcc-246">非成員要求存取的功能已停用。</span><span class="sxs-lookup"><span data-stu-id="56fcc-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="56fcc-247">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="56fcc-247">Here is your resulting configuration.</span></span>
  
![適用於隔離 SharePoint Online 小組網站的高度機密層級保護。](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="56fcc-249">網站透過群組成員資格之一的存取群組的成員可以現在安全地進行共同作業網站的資源。</span><span class="sxs-lookup"><span data-stu-id="56fcc-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="56fcc-250">下一步</span><span class="sxs-lookup"><span data-stu-id="56fcc-250">Next step</span></span>

[<span data-ttu-id="56fcc-251">保護 SharePoint Online 與 Office 365 標籤和 DLP 檔案</span><span class="sxs-lookup"><span data-stu-id="56fcc-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="56fcc-252">請參閱</span><span class="sxs-lookup"><span data-stu-id="56fcc-252">See Also</span></span>

[<span data-ttu-id="56fcc-253">安全的 SharePoint Online 網站及檔案</span><span class="sxs-lookup"><span data-stu-id="56fcc-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="56fcc-254">安全的開發人員/測試環境中的 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="56fcc-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="56fcc-255">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="56fcc-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="56fcc-256">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="56fcc-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




