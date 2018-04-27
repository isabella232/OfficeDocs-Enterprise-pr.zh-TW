---
title: 在開發/測試環境中保護 SharePoint Online 網站
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
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 摘要： 建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站的開發人員/測試環境中。
ms.openlocfilehash: 8c02f1416cb00150e68dcc27dc7afb41bf82ed21
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="0f0e1-103">在開發/測試環境中保護 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="0f0e1-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="0f0e1-104">**摘要：**開發/測試環境中建立公用、 私人、 機密、 和高度機密的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="0f0e1-105">本文提供逐步指示以建立包含四種不同類型的[安全 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)解決方案的 SharePoint Online 小組網站的開發人員/測試環境。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="0f0e1-107">您可以先使用此開發/測試環境，來試驗資訊保護行為，並針對特定需求微調設定，然後再將 SharePoint Online 小組網站部署在生產環境中。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="0f0e1-108">階段 1：建立開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="0f0e1-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="0f0e1-109">在這個階段中，您會為虛構組織取得 Office 365 與 Enterprise Mobility + Security 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="0f0e1-110">首先，請遵循 [Office 365 開發/測試環境](office-365-dev-test-environment.md)的**階段 2** 中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="0f0e1-111">接下來，註冊 EMS 試用訂閱並將其新增至您的 Office 365 試用版訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="0f0e1-p101">必要時，登入 Office 365 入口網站與您的試用版訂閱的全域管理員帳戶的認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-114">按一下 [管理] 磚。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0f0e1-115">在瀏覽器的 [Office 系統管理中心] 索引標籤上，按一下左導覽中的 [計費] > [購買服務]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0f0e1-p102">在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0f0e1-118">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0f0e1-119">在 [訂單收據] 頁面上，按一下 [繼續]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="0f0e1-120">接下來，啟用全域管理員帳戶的 Enterprise Mobility + Security E5 授權。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="0f0e1-121">在瀏覽器的 [Office 365 系統管理中心] 索引標籤上，按一下左導覽中的 [使用者] > [作用中使用者]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="0f0e1-122">按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="0f0e1-123">在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]** 及 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="0f0e1-124">階段 2：建立和設定 Azure Active Directory (AD) 群組和使用者</span><span class="sxs-lookup"><span data-stu-id="0f0e1-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="0f0e1-125">在這個階段中，您會為虛構組織建立和設定 Azure AD 群組和使用者。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="0f0e1-126">首先，利用 Azure 入口網站建立一組典型組織的群組。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="0f0e1-127">在瀏覽器中，建立不同的索引標籤並前往 Azure 入口網站[https://portal.azure.com](https://portal.azure.com)。必要時，登入的全域管理員帳戶認證的 Office 365 E5 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="0f0e1-128">在 Azure 入口網站中，按一下 [Azure Active Directory] > [使用者和群組] > [所有群組]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="0f0e1-129">在 [所有群組] 刀鋒視窗中，按一下 [+ 新增群組]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="0f0e1-130">在 [群組] 刀鋒視窗中：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="0f0e1-131">在 [**名稱**類型**C 套件**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="0f0e1-132">在 [成員資格] 中選取 [已指派]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="0f0e1-133">對 [啟用 Office 功能] 按一下 [是]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="0f0e1-134">按一下 [建立]，然後關閉 [群組] 刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="0f0e1-135">重複步驟 3-5，逐一設定下列群組名稱：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="0f0e1-136">IT 人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-136">IT staff</span></span>
    
  - <span data-ttu-id="0f0e1-137">研究人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-137">Research staff</span></span>
    
  - <span data-ttu-id="0f0e1-138">一般人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-138">Regular staff</span></span>
    
  - <span data-ttu-id="0f0e1-139">行銷人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-139">Marketing staff</span></span>
    
  - <span data-ttu-id="0f0e1-140">銷售人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-140">Sales staff</span></span>
    
7. <span data-ttu-id="0f0e1-141">請將瀏覽器中的 [Azure 入口網站] 索引標籤保持開啟。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="0f0e1-142">接下來，設定自動授權，讓您群組的成員會自動指派授權 Office 365 和 EMS 訂閱。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="0f0e1-143">在 Azure 入口網站中，按一下 [Azure Active Directory] > [授權] > [所有產品]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="0f0e1-144">在清單中，選取 [**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**、] 和 [**指派**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="0f0e1-145">在 [指派授權] 刀鋒視窗中，按一下 [使用者和群組]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="0f0e1-146">在群組清單中，選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="0f0e1-147">高層主管</span><span class="sxs-lookup"><span data-stu-id="0f0e1-147">C-Suite</span></span>
    
  - <span data-ttu-id="0f0e1-148">IT 人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-148">IT staff</span></span>
    
  - <span data-ttu-id="0f0e1-149">研究人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-149">Research staff</span></span>
    
  - <span data-ttu-id="0f0e1-150">一般人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-150">Regular staff</span></span>
    
  - <span data-ttu-id="0f0e1-151">行銷人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-151">Marketing staff</span></span>
    
  - <span data-ttu-id="0f0e1-152">銷售人員</span><span class="sxs-lookup"><span data-stu-id="0f0e1-152">Sales staff</span></span>
    
5. <span data-ttu-id="0f0e1-153">按一下 [**選取**] 和 [**指派**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="0f0e1-154">關閉瀏覽器的 Azure 入口網站索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="0f0e1-155">接著，[與 Azure Active Directory V2 PowerShell 模組連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="0f0e1-156">填入您的組織名稱、 您位置及常見的密碼，然後從 PowerShell 命令提示字元處或建立使用者帳戶並將它們新增至其群組的整合式指令碼環境 (ISE) 執行這些命令：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
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
> <span data-ttu-id="0f0e1-p103">這裡會使用常見密碼，以便在開發/測試環境中能自動化並輕鬆進行設定。 這不建議用於實際執行的訂閱。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="0f0e1-159">使用下列步驟以確認群組型授權正常運作正常。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="0f0e1-160">從瀏覽器的 [Microsoft Office 的首頁] 索引標籤中，按一下 [管理] 磚。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="0f0e1-161">從瀏覽器的新 [Office 系統管理中心] 索引標籤中，按一下 [使用者]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="0f0e1-162">在使用者清單中，按一下 [CEO]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="0f0e1-163">在列出**CEO**使用者帳戶內容窗格中，確認它已被指派 （在**產品授權**）**企業行動性 + 安全性 E5**和**Office 365 企業版 E5**授權。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="0f0e1-164">階段 3：建立 Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="0f0e1-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="0f0e1-165">在這個階段中，您會為 SharePoint Online 小組網站的文件資料夾，建立不同安全性層級的標籤。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="0f0e1-p104">必要時，使用專用的網際網路瀏覽器並登入 Office 365 入口網站與您的 Office 365 E5 試用版訂閱的全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-168">從 [Microsoft Office 的首頁] 索引標籤中，按一下 [管理] 磚。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0f0e1-169">從 [新**Office 系統管理中心**] 索引標籤的瀏覽器中，按一下 [**系統中心 > 安全性&amp;規範**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="0f0e1-170">從新**首頁-安全性&amp;規範**] 索引標籤的瀏覽器中，按一下 [**分類 > 標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="0f0e1-171">從 [首頁] > [標籤] 窗格中，按一下 [建立標籤]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="0f0e1-172">在**您標籤名稱**] 窗格中，輸入**內部公用**，然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="0f0e1-173">在 [**標籤設定**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-174">在**檢閱您的設定**] 窗格中，按一下 [**建立此標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="0f0e1-175">重複步驟 5-8，逐一設定下列其他標籤：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="0f0e1-176">Private</span><span class="sxs-lookup"><span data-stu-id="0f0e1-176">Private</span></span>
    
  - <span data-ttu-id="0f0e1-177">敏感性</span><span class="sxs-lookup"><span data-stu-id="0f0e1-177">Sensitive</span></span>
    
  - <span data-ttu-id="0f0e1-178">高度機密</span><span class="sxs-lookup"><span data-stu-id="0f0e1-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="0f0e1-179">從**首頁 > 標籤**] 窗格中，按一下 [**發佈標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="0f0e1-180">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**選擇標籤發佈**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="0f0e1-181">在 [**選擇標籤**] 窗格中，按一下 [**新增**] 並選取所有的四個標籤。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="0f0e1-182">按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="0f0e1-183">在 [**選擇要發佈的標籤**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="0f0e1-184">在 [**選擇位置**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="0f0e1-185">在**您的原則名稱**] 窗格中，輸入**範例組織**在 [**名稱**] 然後再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="0f0e1-186">在**檢閱您的設定**] 窗格中，按一下 [**發佈標籤**] 及 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="0f0e1-187">階段 4：建立 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="0f0e1-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="0f0e1-188">在這個階段中，您會為範例組織建立和設定四種類型的 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="0f0e1-189">整個組織的小組網站</span><span class="sxs-lookup"><span data-stu-id="0f0e1-189">Organization wide team site</span></span>

<span data-ttu-id="0f0e1-190">若要建立公用的基準 SharePoint Online 小組網站，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="0f0e1-p105">如果需要，請使用本機電腦上的瀏覽器，並使用全域管理員帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-193">在磚清單中，按一下 [SharePoint]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="0f0e1-194">在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="0f0e1-195">在 [建立網站] 頁面上，按一下 [小組網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="0f0e1-196">在 [網站名稱] 中，鍵入「整個組織」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="0f0e1-197">在 [小組網站描述] 中，鍵入「整個組織的 SharePoint 網站」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="0f0e1-198">**隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-199">在 [您想要新增誰?] 窗格中，按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="0f0e1-200">接下來，設定組織整體小組網站內部公用標籤的 [文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="0f0e1-201">在瀏覽器的**組織整體首頁**] 索引標籤中按一下 [**文件**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="0f0e1-202">按一下設定圖示，然後按一下 [文件庫設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="0f0e1-203">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="0f0e1-204">在**套用設定的標籤**、 選取 [**內部公用**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="0f0e1-205">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-205">Here is your resulting configuration.</span></span>
  
![用於整個組織之公用 SharePoint Online 小組網站的基準層級保護。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="0f0e1-207">專案 1 小組網站</span><span class="sxs-lookup"><span data-stu-id="0f0e1-207">Project 1 team site</span></span>

<span data-ttu-id="0f0e1-208">若要為組織內部的專案建立私用的基準 SharePoint Online 小組網站，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="0f0e1-p106">如果需要，請使用本機電腦上的瀏覽器，並使用全域管理員帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-211">在磚清單中，按一下 [SharePoint]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="0f0e1-212">在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="0f0e1-213">在 [建立網站] 頁面上，按一下 [小組網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="0f0e1-214">在 [網站名稱] 中，鍵入「專案 1」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="0f0e1-215">在**小組網站描述] 中，**輸入**SharePoint 網站的專案 1**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="0f0e1-216">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-217">在 [您想要新增誰?] 窗格中，按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="0f0e1-218">接下來，為「專案 1」小組網站的文件資料夾設定「私用」標籤。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="0f0e1-219">在瀏覽器的 [Project 1-Home (專案 1 - 首頁)] 索引標籤中，按一下 [文件]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="0f0e1-220">按一下設定圖示，然後按一下 [文件庫設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="0f0e1-221">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="0f0e1-222">在**套用設定的標籤**、 選取 [**私人**] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="0f0e1-223">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-223">Here is your resulting configuration.</span></span>
  
![用於 Project1 私人 SharePoint Online 小組網站的基準層級保護。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="0f0e1-225">行銷活動小組網站</span><span class="sxs-lookup"><span data-stu-id="0f0e1-225">Marketing campaigns team site</span></span>

<span data-ttu-id="0f0e1-226">若要為行銷活動資源，建立敏感性層級的隔離 SharePoint Online 小組網站，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="0f0e1-p107">本機電腦上使用瀏覽器，登入 Office 365 入口網站使用全域管理員帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-229">在磚清單中，按一下 [SharePoint]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="0f0e1-230">在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="0f0e1-231">在 [建立網站] 頁面上，按一下 [小組網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="0f0e1-232">在 [小組網站名稱] 中，鍵入「行銷活動」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="0f0e1-233">在 [小組網站描述] 中，鍵入「行銷活動的 SharePoint 網站 (敏感性)」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="0f0e1-234">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-235">在 [您想要新增誰?] 窗格中，按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="0f0e1-236">在瀏覽器中的 [工具] 列中新的**行銷活動**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="0f0e1-237">在 [網站權限] 窗格中，按一下 [進階權限設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="0f0e1-238">在瀏覽器的新 [權限] 索引標籤中，按一下 [存取要求設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="0f0e1-239">在 [**存取要求設定**] 對話方塊中，清除**允許成員] 共用網站和個別的檔案及資料夾**並**邀請其他人的網站成員群組允許成員**] 核取方塊中，輸入**ITAdmin1 @**\<您組織名稱 >**。 onmicrosoft.com**中**傳送所有要求存取**]，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="0f0e1-240">按一下清單中的 [Marketing campaigns Members (行銷活動成員)]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="0f0e1-241">在 [人員與群組] 頁面上，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="0f0e1-242">在 [**共用**] 對話方塊中，輸入**行銷人員**、 選取它，，然後按一下 [**共用**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="0f0e1-243">重複步驟 14 與 15 **Researcher1**使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="0f0e1-244">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="0f0e1-245">按一下 [**行銷活動擁有者**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="0f0e1-246">在 [人員與群組] 頁面上，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="0f0e1-247">在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="0f0e1-248">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="0f0e1-249">關閉瀏覽器中的 [**人員與群組**] 索引標籤、 [瀏覽器中的 [**行銷活動首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="0f0e1-250">以下是設定權限的結果：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="0f0e1-251">**行銷活動成員**SharePoint 群組包含只**行銷活動**群組 （其中包含全域管理員使用者帳戶）、**行銷人員**群組 （其中包含 [Marketing1 及 Marketing2 使用者帳戶） 及**Researcher1**的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="0f0e1-252">「行銷活動 - 擁有者」的 SharePoint 群組僅包含「IT 人員」群組 (其中僅包含 ITAdmin1 和 ITAdmin2 使用者帳戶)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="0f0e1-253">「行銷活動 - 訪客」的 SharePoint 群組未包含任何群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="0f0e1-254">成員無法修改網站層級的權限 (這只能由「行銷活動 - 擁有者」群組成員來執行)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="0f0e1-255">其他使用者帳戶無法存取之網站或其資源，但可以要求網站，會將電子郵件傳送至 ITAdmin1 使用者帳戶信箱的存取權。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="0f0e1-256">接下來，為「行銷活動」小組網站的文件資料夾設定「敏感性」標籤。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="0f0e1-257">在瀏覽器的 [Marketing campaigns-Home (行銷活動 - 首頁)] 索引標籤中，按一下 [文件]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="0f0e1-258">按一下設定圖示，然後按一下 [文件庫設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="0f0e1-259">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="0f0e1-260">在**套用設定的標籤**、 選取**機密**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="0f0e1-261">接下來，設定資料外洩防護 (DLP) 原則；當使用者在組織外部共用具「敏感性」標籤之 SharePoint Online 小組網站 (包含「行銷活動」網站) 上的文件時，即會通知使用者。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="0f0e1-262">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="0f0e1-263">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="0f0e1-264">在 [資料外洩防護] 窗格中，按一下 [+ 建立原則]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="0f0e1-265">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="0f0e1-266">在**您的原則名稱**] 窗格中，輸入**機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="0f0e1-267">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="0f0e1-268">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-269">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="0f0e1-270">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="0f0e1-271">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**機密**標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="0f0e1-272">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="0f0e1-273">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="0f0e1-274">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="0f0e1-275">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="0f0e1-276">在文字方塊中，鍵入或貼上下列內容：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="0f0e1-p108">若要與組織外部的使用者共用，請下載檔案，然後將它開啟。 依序按一下 [檔案]、[保護文件] 和 [以密碼加密]，然後指定強式密碼。 以個別電子郵件或其他通訊方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="0f0e1-280">按一下 [ **OK** ]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="0f0e1-281">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，清除**封鎖來自共用、 人員及限制共用內容的存取權**] 核取方塊，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="0f0e1-282">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下 **[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="0f0e1-283">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="0f0e1-284">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-284">Here is your resulting configuration.</span></span>
  
![用於行銷活動隔離之 SharePoint Online 小組網站的敏感性層級保護。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="0f0e1-286">公司策略小組網站</span><span class="sxs-lookup"><span data-stu-id="0f0e1-286">Company strategy team site</span></span>

<span data-ttu-id="0f0e1-287">若要為組織執行長的公司策略資源，建立高度機密層級的隔離 SharePoint Online 小組網站，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="0f0e1-p109">如果需要，請使用本機電腦上的瀏覽器，並使用全域管理員帳戶登入 Office 365 入口網站。 如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-290">在磚清單中，按一下 [SharePoint]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="0f0e1-291">在瀏覽器的新 [SharePoint] 索引標籤上，按一下 [+ 建立網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="0f0e1-292">在 [建立網站] 頁面上，按一下 [小組網站]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="0f0e1-293">在 [小組網站名稱] 中，鍵入「公司策略」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="0f0e1-294">在 [小組網站描述] 中，鍵入「公司策略的 SharePoint 網站 (高度機密)」。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="0f0e1-295">**隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-296">在 [您想要新增誰?] 窗格中，按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="0f0e1-297">在瀏覽器中的 [工具] 列中新的**公司策略**] 索引標籤上按一下 [設定] 圖示，和 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="0f0e1-298">在 [網站權限] 窗格中，按一下 [進階權限設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="0f0e1-299">在瀏覽器的新 [權限] 索引標籤中，按一下 [存取要求設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="0f0e1-300">**存取要求設定**] 對話方塊中，清除 [**允許成員] 共用網站和個別的檔案及資料夾**並**允許邀請其他人網站成員 」 群組的成員**（使已取消選取所有的三個核取方塊），然後按一下 [ **確定**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="0f0e1-301">清單中的 [**公司策略成員**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="0f0e1-302">在 [人員與群組] 頁面上，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="0f0e1-303">在 [**共用**] 對話方塊中，輸入**C 套件**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="0f0e1-304">按一下 [**公司策略擁有者**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="0f0e1-305">在 [人員與群組] 頁面上，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="0f0e1-306">在 [**共用**] 對話方塊中，輸入**IT 人員**、 選取它，，然後按一下 [**共用**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="0f0e1-307">按一下瀏覽器上的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="0f0e1-308">關閉瀏覽器上的 [**人員與群組**] 索引標籤按一下 [瀏覽器上的 [**公司策略首頁**] 索引標籤，然後關閉 [**網站權限**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="0f0e1-309">以下是設定權限的結果：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="0f0e1-310">「公司策略 - 成員」的 SharePoint 群組僅包含「高層主管」群組 (其中僅包含 CEO、CFO 和 CIO 使用者帳戶) 和「公司策略」群組 (其中僅包含全域管理員使用者帳戶)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="0f0e1-311">**公司策略擁有者**SharePoint 群組包含只**IT 人員**群組 （其中包含只 ITAdmin1 與 ITAdmin2 使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="0f0e1-312">「公司策略 - 訪客」的 SharePoint 群組未包含任何群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="0f0e1-313">成員無法修改網站層級的權限 (這只能由「公司策略 - 擁有者」群組成員來執行)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="0f0e1-p110">其他使用者帳戶無法存取網站或其資源，或要求存取網站。 網站的額外權限必須由全域管理員或「公司策略 - 擁有者」群組成員來執行。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="0f0e1-316">接下來，為「公司策略」小組網站的文件資料夾設定「高度機密」標籤。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="0f0e1-317">在瀏覽器的 [Company strategy-Home (公司策略 - 首頁)] 索引標籤中，按一下 [文件]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="0f0e1-318">按一下設定圖示，然後按一下 [文件庫設定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="0f0e1-319">在 [**權限與管理**] 按一下 [**套用此文件庫中的項目標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="0f0e1-320">在**套用設定的標籤**、 選取**高度機密**、] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="0f0e1-321">接下來，設定 DLP 原則；當使用者在組織外部共用具「高度機密」標籤之 SharePoint Online 小組網站 (包含「公司策略」網站) 上的文件時，即會封鎖使用者。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="0f0e1-p111">必要時，您的本機電腦上使用瀏覽器並登入 Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-324">從您的瀏覽器的 [ **Microsoft Office Home** ] 索引標籤按一下 [**安全性&amp;規範**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="0f0e1-325">在新**安全性&amp;規範**在瀏覽器] 索引標籤中按一下 [**資料遺失防護 > 原則**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="0f0e1-326">在 [資料外洩防護] 窗格中，按一下 [+ 建立原則]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="0f0e1-327">在**開始使用範本建立自訂原則或**] 窗格中，按一下**自訂**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="0f0e1-328">在**您的原則名稱**] 窗格中，輸入**高度機密標籤 SharePoint Online 小組網站**在 [**名稱**]，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="0f0e1-329">中**選擇位置**] 窗格中，按一下 [**讓我選擇特定位置**] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0f0e1-330">在清單中的位置，停用的**Exchange 電子郵件**和**OneDrive 帳戶**的位置，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="0f0e1-331">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="0f0e1-332">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**新增**] 的下拉式方塊中，和 [**標籤**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="0f0e1-333">[**標籤**] 窗格中按一下 [ **+ 新增**、 選取**高度機密**的標籤、 按一下 [**新增**] 和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="0f0e1-334">在 [**選擇要保護的內容類型**] 窗格中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="0f0e1-335">在**自訂您想要保護敏感資訊類型**] 窗格中，按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="0f0e1-336">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，按一下 [**自訂提示] 及 [電子郵件**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="0f0e1-337">在**自訂原則提示及電子郵件通知**] 窗格中，按一下 [**自訂原則提示文字**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="0f0e1-338">在文字方塊中，鍵入或貼上下列內容：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="0f0e1-p112">若要與組織外部的使用者共用，請下載檔案，然後將它開啟。 依序按一下 [檔案]、[保護文件] 和 [以密碼加密]，然後指定強式密碼。 以個別電子郵件或其他通訊方式傳送密碼。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="0f0e1-342">按一下 [ **OK** ]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="0f0e1-343">在**您想要如果我們偵測敏感資訊吗？** ] 窗格中，選取**需要覆寫業務上理由**，然後再按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="0f0e1-344">在**您要開啟 [先取出的原則或測試事項？** ] 窗格中，按一下 **[是]，開啟立即**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="0f0e1-345">在**檢閱您的設定**] 窗格中，按一下 [**建立**] 和 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="0f0e1-346">接下來，遵循[使用 Office 365 系統管理中心啟用 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="0f0e1-347">接著，遵循下列步驟，為 Azure 資訊保護設定新的限域原則與子標籤，以提供保護及權限：</span><span class="sxs-lookup"><span data-stu-id="0f0e1-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="0f0e1-p113">Office 365 入口網站與有安全性管理員或公司管理員角色的帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0f0e1-350">在瀏覽器中的個別] 索引標籤移至 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="0f0e1-351">如果這是您要設定 Azure 資訊保護第一次，請參閱這些[指示](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="0f0e1-352">在 [清單] 窗格中，按一下 [**更多的服務**、 輸入**資訊**，和 [ **Azure 資訊保護**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="0f0e1-353">**Azure 資訊保護**blade、 上，按一下 [**範圍設定的原則 > + 新增原則**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="0f0e1-354">輸入**CompanyStrategy** [**原則名稱**] 及 [**標籤公司策略小組網站中的文件**中**描述**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="0f0e1-355">按一下 [選取取得此原則的使用者或群組] > [使用者/群組]，然後選取 [高階主管]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="0f0e1-356">按一下 [選取] > [確定]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="0f0e1-357">針對 [高度機密] 標籤，按一下省略符號 (...)，然後再按一下 [新增子標籤]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="0f0e1-358">在 [名稱] 中鍵入子標籤的名稱，並在 [描述] 中鍵入標籤的描述。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="0f0e1-359">在 [為包含此標籤的文件與電子郵件設定權限] 中，按一下 [保護]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="0f0e1-360">在 [保護] 區段中，按一下 [Azure (雲端金鑰)]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="0f0e1-361">在 [保護] 刀鋒視窗中，按一下 [保護設定] 下的 [+ 新增權限]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="0f0e1-362">在 [新增權限] 刀鋒視窗中，按一下 [指定使用者與群組] 下的 [+ 瀏覽目錄]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="0f0e1-363">在**AAD 使用者與群組**] 窗格中，選取**C 套件**，然後再按一下 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="0f0e1-364">在**預設選擇權限**] 下方清除**列印**、**複製及擷取內容**以及**轉寄**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="0f0e1-365">按兩次 [**確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="0f0e1-366">在 [子標籤] 刀鋒視窗中，按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="0f0e1-367">關閉新的限域原則刀鋒視窗。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="0f0e1-368">在**Azure 資訊保護-範圍的原則**blade 中，按一下 [**發佈**] 及 [ **[是]**。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="0f0e1-369">若要保護與 Azure 資訊保護及這個新的標籤文件，您必須在測試電腦上的 [[安裝 Azure 資訊保護用戶端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 從 Office 365 入口網站安裝 Office 並再登入從 Microsoft Word 中**帳戶C 套件**您試用版訂閱的群組。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="0f0e1-370">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-370">Here is your resulting configuration.</span></span>
  
![用於公司策略隔離之 SharePoint Online 小組網站的高度機密層級保護。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="0f0e1-372">您現在準備好建立這四個網站中的文件，以及使用您試用訂用帳戶中的不同使用者帳戶來測試與其的存取。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="0f0e1-373">以下是所有四種 SharePoint Online 小組網站的整體設定。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![安全的 SharePoint Online 開發/測試環境中的所有四個小組網站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="0f0e1-375">下一步</span><span class="sxs-lookup"><span data-stu-id="0f0e1-375">Next step</span></span>

<span data-ttu-id="0f0e1-376">當您準備好進行安全的 SharePoint Online 網站的生產環境部署時，請參閱[保護 SharePoint Online 網站與檔案](secure-sharepoint-online-sites-and-files.md)，以取得詳細資訊及逐步部署文章的連結。</span><span class="sxs-lookup"><span data-stu-id="0f0e1-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0f0e1-377">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f0e1-377">See Also</span></span>

[<span data-ttu-id="0f0e1-378">保護 SharePoint Online 網站與檔案</span><span class="sxs-lookup"><span data-stu-id="0f0e1-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="0f0e1-379">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="0f0e1-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="0f0e1-380">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="0f0e1-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="0f0e1-381">適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南</span><span class="sxs-lookup"><span data-stu-id="0f0e1-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




