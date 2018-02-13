---
title: "安全的開發人員/測試環境中的 SharePoint Online 網站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "摘要： 建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站的開發人員/測試環境中。"
ms.openlocfilehash: a0448cdbce570db748f8fcae784fd6f1beefc218
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="a565f-103">安全的開發人員/測試環境中的 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="a565f-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="a565f-104">**摘要：**開發/測試環境中建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="a565f-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="a565f-105">本文提供逐步指示以建立包含四種不同類型的[安全 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)解決方案的 SharePoint Online 小組網站的開發人員/測試環境。</span><span class="sxs-lookup"><span data-stu-id="a565f-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="a565f-107">開發/測試環境用於實驗的資訊保護行為和微調您的特定需求才能部署在生產環境中的 SharePoint Online 小組網站的設定。</span><span class="sxs-lookup"><span data-stu-id="a565f-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="a565f-108">階段 1： 建立您的開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="a565f-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="a565f-109">在此階段中，您可以取得試用版訂閱的 Office 365 和 Enterprise 行動性 + 安全性為虛構的組織。</span><span class="sxs-lookup"><span data-stu-id="a565f-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="a565f-110">首先，請遵循**階段 2**的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a565f-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a565f-111">接下來，註冊 EMS 試用訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="a565f-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="a565f-p101">必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-114">按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="a565f-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="a565f-115">在**Office 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**帳務 > 購買服務**。</span><span class="sxs-lookup"><span data-stu-id="a565f-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="a565f-p102">在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="a565f-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="a565f-118">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="a565f-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="a565f-119">在 [**順序回條**] 頁面上按一下 [**繼續**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="a565f-120">接下來，可讓企業行動性 + 全域管理員帳戶的安全性 E5 授權。</span><span class="sxs-lookup"><span data-stu-id="a565f-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="a565f-121">在**Office 365 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**使用者 > 作用中使用者**。</span><span class="sxs-lookup"><span data-stu-id="a565f-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="a565f-122">按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="a565f-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="a565f-123">在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="a565f-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="a565f-124">階段 2： 建立及設定您的 Azure Active Directory (AD) 群組及使用者</span><span class="sxs-lookup"><span data-stu-id="a565f-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="a565f-125">在此階段中，您可以建立及設定 Azure AD 群組及使用者虛構組織的。</span><span class="sxs-lookup"><span data-stu-id="a565f-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="a565f-126">首先，建立一組群組的典型組織的 Azure 入口網站。</span><span class="sxs-lookup"><span data-stu-id="a565f-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="a565f-127">在瀏覽器中，建立不同的索引標籤並前往[https://portal.azure.com](https://portal.azure.com)Azure 入口網站。必要時，登入的全域管理員帳戶認證的 Office 365 E5 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="a565f-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="a565f-128">在 Azure 入口網站中，按一下 [ **Azure Active Directory > 使用者和群組 > 的所有群組**。</span><span class="sxs-lookup"><span data-stu-id="a565f-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="a565f-129">在**所有群組**blade 中，按一下 [ **+ 新群組**。</span><span class="sxs-lookup"><span data-stu-id="a565f-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="a565f-130">在**群組**blade 中：</span><span class="sxs-lookup"><span data-stu-id="a565f-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="a565f-131">在 [**名稱**類型**C 套件**。</span><span class="sxs-lookup"><span data-stu-id="a565f-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="a565f-132">選取**指派**中的**成員資格**。</span><span class="sxs-lookup"><span data-stu-id="a565f-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="a565f-133">按一下 [**是]**以**啟用 Office**功能。</span><span class="sxs-lookup"><span data-stu-id="a565f-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="a565f-134">按一下 [**建立**]，然後關閉 [**群組**blade。</span><span class="sxs-lookup"><span data-stu-id="a565f-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="a565f-135">針對下列群組的名稱重複步驟 3-5：</span><span class="sxs-lookup"><span data-stu-id="a565f-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="a565f-136">IT 人員</span><span class="sxs-lookup"><span data-stu-id="a565f-136">IT staff</span></span>
    
  - <span data-ttu-id="a565f-137">[參考資料的人員</span><span class="sxs-lookup"><span data-stu-id="a565f-137">Research staff</span></span>
    
  - <span data-ttu-id="a565f-138">一般的人員</span><span class="sxs-lookup"><span data-stu-id="a565f-138">Regular staff</span></span>
    
  - <span data-ttu-id="a565f-139">行銷人員</span><span class="sxs-lookup"><span data-stu-id="a565f-139">Marketing staff</span></span>
    
  - <span data-ttu-id="a565f-140">銷售人員</span><span class="sxs-lookup"><span data-stu-id="a565f-140">Sales staff</span></span>
    
7. <span data-ttu-id="a565f-141">在瀏覽器開啟保留 Azure 的入口網站] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a565f-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="a565f-142">接下來，設定自動授權，讓您群組的成員會自動指派授權 Office 365 和 EMS 訂閱。</span><span class="sxs-lookup"><span data-stu-id="a565f-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="a565f-143">在 Azure 入口網站中，按一下 [ **Azure Active Directory > 授權 > 所有產品**。</span><span class="sxs-lookup"><span data-stu-id="a565f-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="a565f-144">在清單中，選取 [**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**、] 和 [**指派**。</span><span class="sxs-lookup"><span data-stu-id="a565f-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="a565f-145">在**指派授權給**blade，按一下 [**使用者與群組**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="a565f-146">在群組清單中，選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="a565f-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="a565f-147">C 套件</span><span class="sxs-lookup"><span data-stu-id="a565f-147">C-Suite</span></span>
    
  - <span data-ttu-id="a565f-148">IT 人員</span><span class="sxs-lookup"><span data-stu-id="a565f-148">IT staff</span></span>
    
  - <span data-ttu-id="a565f-149">[參考資料的人員</span><span class="sxs-lookup"><span data-stu-id="a565f-149">Research staff</span></span>
    
  - <span data-ttu-id="a565f-150">一般的人員</span><span class="sxs-lookup"><span data-stu-id="a565f-150">Regular staff</span></span>
    
  - <span data-ttu-id="a565f-151">行銷人員</span><span class="sxs-lookup"><span data-stu-id="a565f-151">Marketing staff</span></span>
    
  - <span data-ttu-id="a565f-152">銷售人員</span><span class="sxs-lookup"><span data-stu-id="a565f-152">Sales staff</span></span>
    
5. <span data-ttu-id="a565f-153">按一下 [**選取**] 和 [**指派**。</span><span class="sxs-lookup"><span data-stu-id="a565f-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="a565f-154">關閉瀏覽器中的 Azure 入口網站] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a565f-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="a565f-155">接著，您[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="a565f-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="a565f-156">填入您的組織名稱、 您位置及常見的密碼，然後從 PowerShell 命令提示字元處或建立使用者帳戶並將它們新增至其群組的整合式指令碼環境 (ISE) 執行這些命令：</span><span class="sxs-lookup"><span data-stu-id="a565f-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="a565f-p103">自動化及簡化開發人員/測試環境是密碼的設定的使用一般。這是不建議使用實際執行訂閱。</span><span class="sxs-lookup"><span data-stu-id="a565f-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="a565f-159">使用下列步驟以確認群組型授權正常運作正常。</span><span class="sxs-lookup"><span data-stu-id="a565f-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="a565f-160">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="a565f-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="a565f-161">從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中按一下 [**使用者**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="a565f-162">在使用者清單中，按一下 [**執行長**。</span><span class="sxs-lookup"><span data-stu-id="a565f-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="a565f-163">在列出**CEO**使用者帳戶內容窗格中，確認它已被指派 （在**產品授權**）**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**授權。</span><span class="sxs-lookup"><span data-stu-id="a565f-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="a565f-164">階段 3： 建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="a565f-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="a565f-165">在此階段中，您可以建立不同的層級的 SharePoint Online 小組網站的文件資料夾的安全性的標籤。</span><span class="sxs-lookup"><span data-stu-id="a565f-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="a565f-p104">必要時，使用專用的網際網路瀏覽器並登入 Office 365 入口網站與您的 Office 365 E5 試用版訂閱的全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-168">從**Microsoft Office Home** ] 索引標籤上，按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="a565f-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="a565f-169">從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中，按一下 [**系統中心 > 安全性&amp;規範**。</span><span class="sxs-lookup"><span data-stu-id="a565f-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="a565f-170">從新**首頁-安全性&amp;規範**] 索引標籤的瀏覽器中，按一下 [**分類 > 標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="a565f-171">從**首頁 > 標籤**] 窗格中，按一下 [**建立] 標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="a565f-172">在**您標籤名稱**] 窗格中，輸入**內部公用**，然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="a565f-173">在 [**標籤設定**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-174">在**檢閱您的設定**] 窗格中，按一下 [**建立此標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="a565f-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="a565f-175">針對這些額外的標籤重複步驟 5-8：</span><span class="sxs-lookup"><span data-stu-id="a565f-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="a565f-176">私人</span><span class="sxs-lookup"><span data-stu-id="a565f-176">Private</span></span>
    
  - <span data-ttu-id="a565f-177">機密</span><span class="sxs-lookup"><span data-stu-id="a565f-177">Sensitive</span></span>
    
  - <span data-ttu-id="a565f-178">高度機密</span><span class="sxs-lookup"><span data-stu-id="a565f-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="a565f-179">從**首頁 > 標籤**] 窗格中，按一下 [**發佈標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="a565f-180">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**選擇標籤發佈**。</span><span class="sxs-lookup"><span data-stu-id="a565f-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="a565f-181">在 [**選擇標籤**] 窗格中，按一下 [**新增**] 並選取所有的四個標籤。</span><span class="sxs-lookup"><span data-stu-id="a565f-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="a565f-182">按一下 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="a565f-183">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="a565f-184">在 [**選擇位置**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="a565f-185">在**您的原則名稱**] 窗格中，輸入**範例組織**在 [**名稱**] 然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="a565f-186">在**檢閱您的設定**] 窗格中，按一下 [**發佈標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="a565f-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="a565f-187">階段 4： 建立 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="a565f-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="a565f-188">在此階段中，您可以建立及設定 SharePoint Online 小組網站的四種類型的範例組織。</span><span class="sxs-lookup"><span data-stu-id="a565f-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="a565f-189">組織整體小組網站</span><span class="sxs-lookup"><span data-stu-id="a565f-189">Organization wide team site</span></span>

<span data-ttu-id="a565f-190">若要建立基準公用 SharePoint Online 小組網站，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a565f-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="a565f-p105">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-193">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="a565f-194">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="a565f-195">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="a565f-196">在**站台名稱**] 中輸入**整個組織**。</span><span class="sxs-lookup"><span data-stu-id="a565f-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="a565f-197">在**小組網站描述**] 中，輸入**SharePoint 網站的整個組織**。</span><span class="sxs-lookup"><span data-stu-id="a565f-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="a565f-198">**隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-199">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="a565f-200">接下來，設定組織整體小組網站內部公用標籤的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a565f-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="a565f-201">在瀏覽器的**組織整體首頁**] 索引標籤中按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="a565f-202">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="a565f-203">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="a565f-204">在**套用設定的標籤**、 選取 [**內部公用**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="a565f-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="a565f-205">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a565f-205">Here is your resulting configuration.</span></span>
  
![用於整個組織之公用 SharePoint Online 小組網站的基準層級保護。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="a565f-207">專案 1 小組網站</span><span class="sxs-lookup"><span data-stu-id="a565f-207">Project 1 team site</span></span>

<span data-ttu-id="a565f-208">若要建立基準私人 SharePoint Online 小組網站組織內的專案，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a565f-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="a565f-p106">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-211">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="a565f-212">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="a565f-213">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="a565f-214">在**站台名稱**] 中輸入**專案 1**。</span><span class="sxs-lookup"><span data-stu-id="a565f-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="a565f-215">在**小組網站描述] 中，**輸入**SharePoint 網站的專案 1**。</span><span class="sxs-lookup"><span data-stu-id="a565f-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="a565f-216">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-217">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="a565f-218">接下來，設定專案 1 小組網站私人標籤的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a565f-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="a565f-219">**專案 1 首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="a565f-220">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="a565f-221">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="a565f-222">在**套用設定的標籤**、 選取 [**私人**] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="a565f-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="a565f-223">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a565f-223">Here is your resulting configuration.</span></span>
  
![用於 Project1 私人 SharePoint Online 小組網站的基準層級保護。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="a565f-225">行銷活動小組網站</span><span class="sxs-lookup"><span data-stu-id="a565f-225">Marketing campaigns team site</span></span>

<span data-ttu-id="a565f-226">若要建立機密層級隔離的 SharePoint Online 小組網站行銷活動全方位的資源，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a565f-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="a565f-p107">本機電腦上使用瀏覽器，登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-229">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="a565f-230">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="a565f-231">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="a565f-232">在**小組網站名稱**] 中輸入**行銷活動**。</span><span class="sxs-lookup"><span data-stu-id="a565f-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="a565f-233">在**小組網站描述**] 中，輸入**SharePoint 網站的行銷活動全方位資源 （機密）**。</span><span class="sxs-lookup"><span data-stu-id="a565f-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="a565f-234">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-235">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="a565f-236">在瀏覽器中的 [工具] 列中新的**行銷活動**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="a565f-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="a565f-237">在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。</span><span class="sxs-lookup"><span data-stu-id="a565f-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="a565f-238">在 [新**的權限**] 索引標籤在瀏覽器中按一下 [**存取要求的設定**。</span><span class="sxs-lookup"><span data-stu-id="a565f-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="a565f-239">在 [**存取要求設定**] 對話方塊中，清除**允許成員] 共用網站和個別的檔案及資料夾**並**邀請其他人的網站成員群組允許成員**] 核取方塊中，輸入**ITAdmin1 @**\<您組織名稱 >**。 onmicrosoft.com**中**傳送所有要求存取**]，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="a565f-240">按一下清單中的**行銷活動成員**。</span><span class="sxs-lookup"><span data-stu-id="a565f-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="a565f-241">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="a565f-242">在 [**共用**] 對話方塊中，輸入**行銷人員**、 選取它，，然後按一下 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="a565f-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="a565f-243">重複步驟 14 與 15 **Researcher1**使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a565f-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="a565f-244">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a565f-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="a565f-245">按一下 [**行銷活動擁有者**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="a565f-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="a565f-246">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="a565f-247">在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="a565f-248">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a565f-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="a565f-249">關閉瀏覽器中的 [**人員與群組**] 索引標籤、 [瀏覽器中的 [**行銷活動首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="a565f-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="a565f-250">設定權限的結果如下︰</span><span class="sxs-lookup"><span data-stu-id="a565f-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="a565f-251">**行銷活動成員**SharePoint 群組包含只**行銷活動**群組 （其中包含全域管理員使用者帳戶）、**行銷人員**群組 （其中包含 [Marketing1 及 Marketing2 使用者帳戶） 及**Researcher1**的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a565f-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="a565f-252">**行銷活動擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="a565f-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="a565f-253">**行銷活動訪客**SharePoint 群組沒有包含群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a565f-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="a565f-254">成員無法修改站台層級權限 （這可以只來完成**行銷活動擁有人**群組的成員）。</span><span class="sxs-lookup"><span data-stu-id="a565f-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="a565f-255">其他使用者帳戶無法存取之網站或其資源，但可以要求網站，會將電子郵件傳送至 ITAdmin1 使用者帳戶信箱的存取權。</span><span class="sxs-lookup"><span data-stu-id="a565f-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="a565f-256">接下來，設定行銷活動小組網站機密標籤的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a565f-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="a565f-257">**行銷活動首頁**] 索引標籤中的瀏覽器中，按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="a565f-258">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="a565f-259">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="a565f-260">在**套用設定的標籤**、 選取**機密**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="a565f-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="a565f-261">下一步] 設定時階級機密標籤，其中包含組織外的行銷活動網站與 SharePoint Online 小組網站上的文件會通知使用者資料外洩防護 (DLP) 原則。</span><span class="sxs-lookup"><span data-stu-id="a565f-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="a565f-262">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="a565f-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="a565f-263">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="a565f-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="a565f-264">在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。</span><span class="sxs-lookup"><span data-stu-id="a565f-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="a565f-265">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="a565f-266">在**您的原則名稱**] 窗格中，輸入**機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="a565f-267">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="a565f-268">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-269">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="a565f-270">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="a565f-271">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**機密**標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="a565f-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="a565f-272">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="a565f-273">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="a565f-274">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="a565f-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="a565f-275">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="a565f-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="a565f-276">[文字] 方塊中輸入或貼上下列：</span><span class="sxs-lookup"><span data-stu-id="a565f-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="a565f-p108">與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="a565f-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="a565f-280">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="a565f-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="a565f-281">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，清除**封鎖來自共用、 人員及限制共用內容的存取權**] 核取方塊，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="a565f-282">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="a565f-283">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="a565f-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="a565f-284">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a565f-284">Here is your resulting configuration.</span></span>
  
![用於行銷活動隔離之 SharePoint Online 小組網站的敏感性層級保護。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="a565f-286">公司策略小組網站</span><span class="sxs-lookup"><span data-stu-id="a565f-286">Company strategy team site</span></span>

<span data-ttu-id="a565f-287">若要建立隔離的 SharePoint Online 小組網站的組織的首席高階主管的策略性公司資源之高度機密層級，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a565f-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="a565f-p109">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-290">在 [並排顯示] 清單中按一下 [ **SharePoint**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="a565f-291">在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="a565f-292">在 [**建立網站**] 頁面上，按一下 [**小組網站**。</span><span class="sxs-lookup"><span data-stu-id="a565f-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="a565f-293">在**小組網站名稱**] 中輸入**公司策略**。</span><span class="sxs-lookup"><span data-stu-id="a565f-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="a565f-294">在**小組網站描述**] 中，輸入**SharePoint 網站的公司策略 （高度機密）**。</span><span class="sxs-lookup"><span data-stu-id="a565f-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="a565f-295">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-296">在**您要新增誰？** ] 窗格中，按一下 [**完成]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="a565f-297">在瀏覽器中的 [工具] 列中新的**公司策略**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="a565f-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="a565f-298">在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。</span><span class="sxs-lookup"><span data-stu-id="a565f-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="a565f-299">在 [新**的權限**] 索引標籤在瀏覽器中按一下 [**存取要求的設定**。</span><span class="sxs-lookup"><span data-stu-id="a565f-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="a565f-300">**存取要求設定**] 對話方塊中，清除 [**允許成員] 共用網站和個別的檔案及資料夾**並**允許邀請其他人網站成員 」 群組的成員**（使已取消選取所有的三個核取方塊），然後按一下 [ **確定**。</span><span class="sxs-lookup"><span data-stu-id="a565f-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="a565f-301">清單中的 [**公司策略成員**。</span><span class="sxs-lookup"><span data-stu-id="a565f-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="a565f-302">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="a565f-303">在 [**共用**] 對話方塊中，輸入**C 套件**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="a565f-304">按一下 [**公司策略擁有者**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="a565f-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="a565f-305">在 [**人員與群組**] 頁面上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="a565f-306">在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="a565f-307">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a565f-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="a565f-308">關閉瀏覽器上的 [**人員與群組**] 索引標籤按一下 [瀏覽器上的 [**公司策略首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="a565f-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="a565f-309">設定權限的結果如下︰</span><span class="sxs-lookup"><span data-stu-id="a565f-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="a565f-310">**公司策略成員**SharePoint 群組包含只**C 套件**群組 （其中包含只 CEO、 CFO、 及 CIO 使用者帳戶） 和**公司策略**群組 （其中包含只有一個全域管理員使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="a565f-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="a565f-311">**公司策略擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="a565f-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="a565f-312">**公司策略訪客**SharePoint 群組沒有包含群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a565f-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="a565f-313">成員無法修改站台層級權限 （這可以只來完成**公司策略擁有人**群組的成員）。</span><span class="sxs-lookup"><span data-stu-id="a565f-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="a565f-p110">其他使用者帳戶無法存取之網站或其資源的更新或要求網站的存取權。全域管理員或**公司策略擁有者**群組的成員必須完成網站的其他權限。</span><span class="sxs-lookup"><span data-stu-id="a565f-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="a565f-316">接下來，設定高度機密標籤公司策略小組網站的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a565f-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="a565f-317">在瀏覽器的**公司策略首頁**] 索引標籤中按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="a565f-318">按一下 [設定] 圖示，並再按一下 [**文件庫設定**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="a565f-319">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="a565f-320">在**套用設定的標籤**、 選取**高度機密**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="a565f-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="a565f-321">接下來，設定 DLP 原則，封鎖使用者時階級具有高度機密標籤，其中包含組織外的公司策略網站 SharePoint Online 小組網站上的文件。</span><span class="sxs-lookup"><span data-stu-id="a565f-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="a565f-p111">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-324">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="a565f-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="a565f-325">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="a565f-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="a565f-326">在 [**資料外洩防護**] 窗格中，按一下 [ **+ 建立原則**。</span><span class="sxs-lookup"><span data-stu-id="a565f-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="a565f-327">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="a565f-328">在**您的原則名稱**] 窗格中，輸入**高度機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="a565f-329">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a565f-330">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="a565f-331">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="a565f-332">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="a565f-333">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**高度機密**的標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="a565f-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="a565f-334">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="a565f-335">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="a565f-336">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="a565f-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="a565f-337">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="a565f-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="a565f-338">[文字] 方塊中輸入或貼上下列：</span><span class="sxs-lookup"><span data-stu-id="a565f-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="a565f-p112">與組織外部使用者共用，下載檔案，然後開啟它。按一下 [檔案]，然後保護文件，並使用密碼，然後加密，然後指定強式密碼。以不同的電子郵件或其他通訊的方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="a565f-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="a565f-342">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="a565f-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="a565f-343">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，選取**需要覆寫業務上理由**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="a565f-344">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下**[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a565f-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="a565f-345">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="a565f-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="a565f-346">接下來，遵循[與 Office 365 系統管理中心啟動 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a565f-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="a565f-347">接下來，設定 Azure 資訊保護與新範圍的原則和子標籤保護和權限的下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a565f-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="a565f-p113">Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="a565f-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="a565f-350">在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="a565f-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="a565f-351">如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="a565f-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="a565f-352">在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。</span><span class="sxs-lookup"><span data-stu-id="a565f-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="a565f-353">**Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。</span><span class="sxs-lookup"><span data-stu-id="a565f-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="a565f-354">輸入**CompanyStrategy** [**原則名稱**] 及 [**標籤公司策略小組網站中的文件**中**描述**。</span><span class="sxs-lookup"><span data-stu-id="a565f-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="a565f-355">按一下 [**選取哪些使用者或群組取得此原則 > 使用者/群組**，然後選取 [ **C 套件**。</span><span class="sxs-lookup"><span data-stu-id="a565f-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="a565f-356">按一下 [**選取 > [確定]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="a565f-357">**高度機密**標籤中，按一下省略符號 （...）] 和 [**新增子標籤**。</span><span class="sxs-lookup"><span data-stu-id="a565f-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="a565f-358">輸入**名稱**與**描述**標籤的描述的子標籤名稱。</span><span class="sxs-lookup"><span data-stu-id="a565f-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="a565f-359">在**設定文件及包含此標籤的電子郵件的權限**，請按一下 [**保護**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="a565f-360">在 [**保護**] 區段中，按一下 [ **Azure （雲端索引鍵）**。</span><span class="sxs-lookup"><span data-stu-id="a565f-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="a565f-361">在**保護**blade，**保護設定**] 下按一下 [ **+ 新增權限**。</span><span class="sxs-lookup"><span data-stu-id="a565f-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="a565f-362">在**新增權限**blade 中，**指定使用者與群組**] 下按一下 [ **+ 瀏覽目錄]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="a565f-363">在**AAD 使用者與群組**] 窗格中，選取**C 套件**，然後再按一下 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="a565f-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="a565f-364">在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a565f-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="a565f-365">按兩次 [**確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a565f-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="a565f-366">在**子標籤**blade 中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="a565f-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="a565f-367">關閉新範圍的原則 blade。</span><span class="sxs-lookup"><span data-stu-id="a565f-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="a565f-368">在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**] 及 [ **[是]**。</span><span class="sxs-lookup"><span data-stu-id="a565f-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="a565f-369">若要保護與 Azure 資訊保護及這個新的標籤文件，您必須在測試電腦上的 [[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 從 Office 365 入口網站安裝 Office 並再登入從 Microsoft Word 中**帳戶C 套件**您試用版訂閱的群組。</span><span class="sxs-lookup"><span data-stu-id="a565f-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="a565f-370">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a565f-370">Here is your resulting configuration.</span></span>
  
![用於公司策略隔離之 SharePoint Online 小組網站的高度機密層級保護。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="a565f-372">您現在可以開始建立下列四個網站中的文件並測試您的試用版訂閱具有不同的使用者帳戶給他們的存取權。</span><span class="sxs-lookup"><span data-stu-id="a565f-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="a565f-373">以下是所有的四個 SharePoint Online 小組網站的整體設定。</span><span class="sxs-lookup"><span data-stu-id="a565f-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="a565f-375">下一步</span><span class="sxs-lookup"><span data-stu-id="a565f-375">Next step</span></span>

<span data-ttu-id="a565f-376">當您準備好實際執行部署的安全的 SharePoint Online 網站時，請參閱[安全 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)的詳細的資訊以及逐步說明的部署文章的連結。</span><span class="sxs-lookup"><span data-stu-id="a565f-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a565f-377">請參閱</span><span class="sxs-lookup"><span data-stu-id="a565f-377">See Also</span></span>

[<span data-ttu-id="a565f-378">安全的 SharePoint Online 網站及檔案</span><span class="sxs-lookup"><span data-stu-id="a565f-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="a565f-379">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="a565f-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="a565f-380">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="a565f-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="a565f-381">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="a565f-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




