---
title: "設定群組及使用者政治 campaign 開發/測試環境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "摘要： 建立 Office 365 和 Enterprise 行動性 + 安全性 （EMS） 試用版訂閱使用者和群組政治 campaign 開發/測試環境。"
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="aee1a-103">設定群組及使用者政治 campaign 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="aee1a-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="aee1a-104">**摘要：**使用使用者和群組政治 campaign 開發/測試環境中建立 Office 365 和 Enterprise 行動性 + 安全性 （EMS） 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="aee1a-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="aee1a-105">若要建立包含簡化的使用者帳戶和群組[政治活動、 非營利機構，與其他靈活組織的 Microsoft 安全性指引](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解決方案的開發人員/測試環境中使用本文中的指示。</span><span class="sxs-lookup"><span data-stu-id="aee1a-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="aee1a-106">階段 1：建立 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="aee1a-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="aee1a-107">在此階段中，您可以取得 Office 365 E5 和 Enterprise 行動性 + 代表政治 campaign 虛構組織的安全性 (EMS) E5 試用版的訂閱。</span><span class="sxs-lookup"><span data-stu-id="aee1a-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="aee1a-108">首先，請遵循**階段 2**的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="aee1a-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="aee1a-109">接下來，註冊 EMS E5 試用訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="aee1a-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="aee1a-p101">必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="aee1a-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="aee1a-112">按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="aee1a-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="aee1a-113">在**Office 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**帳務 > 購買服務**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="aee1a-p102">在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="aee1a-116">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="aee1a-117">在 [**順序回條**] 頁面上按一下 [**繼續**]。</span><span class="sxs-lookup"><span data-stu-id="aee1a-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="aee1a-118">接下來，可讓您的全域管理員帳戶 EMS E5 授權。</span><span class="sxs-lookup"><span data-stu-id="aee1a-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="aee1a-119">在**Office 365 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**使用者 > 作用中使用者**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="aee1a-120">按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="aee1a-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="aee1a-121">在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="aee1a-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="aee1a-122">階段 2： 建立及設定您的 Azure Active Directory (AD) 群組</span><span class="sxs-lookup"><span data-stu-id="aee1a-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="aee1a-123">在此階段中，您建立及設定您的行銷活動的 Azure AD 群組。</span><span class="sxs-lookup"><span data-stu-id="aee1a-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="aee1a-124">首先，建立一組群組的一般政治行銷活動的 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="aee1a-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="aee1a-125">在瀏覽器中個別] 索引標籤上移至[https://portal.azure.com](https://portal.azure.com)Azure 入口網站。必要時，登入的全域管理員帳戶認證的 Office 365 E5 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="aee1a-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="aee1a-126">在 Azure 入口網站中，按一下 [ **Azure Active Directory > 使用者和群組 > 的所有群組**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="aee1a-127">不要在此清單中每個群組名稱的下列步驟：</span><span class="sxs-lookup"><span data-stu-id="aee1a-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="aee1a-128">資深和策略的人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="aee1a-129">IT 人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-129">IT staff</span></span>
    
  - <span data-ttu-id="aee1a-130">分析的人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-130">Analytics staff</span></span>
    
  - <span data-ttu-id="aee1a-131">一般核心人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-131">Regular core staff</span></span>
    
  - <span data-ttu-id="aee1a-132">作業人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-132">Operations staff</span></span>
    
  - <span data-ttu-id="aee1a-133">欄位的人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-133">Field staff</span></span>
    
1. <span data-ttu-id="aee1a-134">在**所有群組**blade 中，按一下 [ **+ 新群組**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="aee1a-135">在 [**名稱**輸入從清單中的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="aee1a-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="aee1a-136">在 [**成員資格**選取**動態的使用者**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="aee1a-137">按一下 [**是]**以**啟用 Office**功能。</span><span class="sxs-lookup"><span data-stu-id="aee1a-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="aee1a-138">按一下 [**新增動態查詢**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="aee1a-139">在**將使用者新增其中**、 選取**部門**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="aee1a-140">在下一步] 欄位中，選取 [**等於**]。</span><span class="sxs-lookup"><span data-stu-id="aee1a-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="aee1a-141">在 [下一步] 欄位中輸入從清單中的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="aee1a-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="aee1a-142">按一下 [**新增查詢**，並再按一下 [**建立**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="aee1a-143">按一下 [**使用者和群組-所有群組**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="aee1a-144">接下來，設定群組使成員會自動指派 Office 365 E5 以及 EMS E5 授權。</span><span class="sxs-lookup"><span data-stu-id="aee1a-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="aee1a-145">在 Azure 入口網站中，按一下 [ **Azure Active Directory > 授權 > 所有產品**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="aee1a-146">在清單中，選取 [**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**、] 和 [ **+ 指派**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="aee1a-147">在**指派授權給**blade，按一下 [**使用者與群組**]。</span><span class="sxs-lookup"><span data-stu-id="aee1a-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="aee1a-148">在群組清單中，選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="aee1a-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="aee1a-149">分析的人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-149">Analytics staff</span></span>
    
  - <span data-ttu-id="aee1a-150">欄位的人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-150">Field staff</span></span>
    
  - <span data-ttu-id="aee1a-151">IT 人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-151">IT staff</span></span>
    
  - <span data-ttu-id="aee1a-152">作業人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-152">Operations staff</span></span>
    
  - <span data-ttu-id="aee1a-153">一般核心人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-153">Regular core staff</span></span>
    
  - <span data-ttu-id="aee1a-154">資深和策略的人員</span><span class="sxs-lookup"><span data-stu-id="aee1a-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="aee1a-155">按一下 [**選取**] 和 [**指派**。</span><span class="sxs-lookup"><span data-stu-id="aee1a-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="aee1a-156">關閉瀏覽器中的 Azure 入口網站] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="aee1a-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="aee1a-157">階段 3： 新增您的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="aee1a-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="aee1a-158">在此階段中，您將範例中的使用者帳戶新增政治的活動。</span><span class="sxs-lookup"><span data-stu-id="aee1a-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="aee1a-159">首先，您[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="aee1a-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="aee1a-160">下一步] 您填入您的組織名稱、 您位置及常見的密碼，並再從 PowerShell 命令提示字元處或整合式指令碼環境 (ISE) 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="aee1a-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="aee1a-p103">自動化及簡化開發人員/測試環境是密碼的設定的使用一般。這是不建議使用實際執行訂閱。當您使用每個這些新的使用者帳戶登入，系統會提示您變更密碼。</span><span class="sxs-lookup"><span data-stu-id="aee1a-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="aee1a-164">使用下列步驟以確認動態群組成員資格與群組型授權均運作正常。</span><span class="sxs-lookup"><span data-stu-id="aee1a-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="aee1a-165">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="aee1a-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="aee1a-166">從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中按一下 [**使用者**]。</span><span class="sxs-lookup"><span data-stu-id="aee1a-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="aee1a-167">在使用者清單中，按一下 [**應徵者**]。</span><span class="sxs-lookup"><span data-stu-id="aee1a-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="aee1a-168">在列出**應徵者**的使用者帳戶內容窗格中，確認：</span><span class="sxs-lookup"><span data-stu-id="aee1a-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="aee1a-169">它是**資深和策略性人員**（中**群組的成員資格**） 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="aee1a-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="aee1a-170">已被指派**企業行動性 + 安全性 E5**和**Office 365 企業版 E5** （中的授權**產品授權**）。</span><span class="sxs-lookup"><span data-stu-id="aee1a-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="aee1a-171">關閉 [**應徵者**使用者帳戶] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="aee1a-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="aee1a-172">以供未來參照的記錄值</span><span class="sxs-lookup"><span data-stu-id="aee1a-172">Record values for future reference</span></span>

<span data-ttu-id="aee1a-173">記錄使用 Office 365 與 EMS 此開發/測試環境的試用版訂閱這些值：</span><span class="sxs-lookup"><span data-stu-id="aee1a-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="aee1a-174">您的試用版訂閱的組織名稱： ___</span><span class="sxs-lookup"><span data-stu-id="aee1a-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="aee1a-175">例如，contoso.onmicrosoft.com 試用訂閱網域名稱、 組織名稱為"contoso"。</span><span class="sxs-lookup"><span data-stu-id="aee1a-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="aee1a-176">Office 365 全域管理員名稱： ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="aee1a-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="aee1a-177">此帳戶的密碼和其他使用者帳戶的常見初始密碼記錄在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="aee1a-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="aee1a-178">下一步</span><span class="sxs-lookup"><span data-stu-id="aee1a-178">Next step</span></span>

<span data-ttu-id="aee1a-179">建置[在政治 campaign 開發/測試環境中的建立小組網站](create-team-sites-in-a-political-campaign-dev-test-environment.md)與此開發/測試環境中的 SharePoint Online 小組網站的四種不同類型。</span><span class="sxs-lookup"><span data-stu-id="aee1a-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aee1a-180">See Also</span><span class="sxs-lookup"><span data-stu-id="aee1a-180">See Also</span></span>

[<span data-ttu-id="aee1a-181">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="aee1a-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="aee1a-182">政治 campaign 開發/測試環境中建立小組網站</span><span class="sxs-lookup"><span data-stu-id="aee1a-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="aee1a-183">雲端採用測試實驗室指南 (Tlg)</span><span class="sxs-lookup"><span data-stu-id="aee1a-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="aee1a-184">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="aee1a-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




