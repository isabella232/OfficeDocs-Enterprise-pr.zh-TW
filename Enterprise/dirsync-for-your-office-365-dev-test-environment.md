---
title: 適用於 Office 365 開發/測試環境的目錄同步作業
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 摘要：設定適用於 Office 365 開發/測試環境的目錄同步作業
ms.openlocfilehash: 0b51e3cb6c348c5c6f9bb1a6d818a18fb123e1b6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067759"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="515e1-103">適用於 Office 365 開發/測試環境的目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="515e1-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="515e1-104">**摘要：** 設定適用於 Office 365 開發/測試環境的目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="515e1-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="515e1-p101">許多組織使用 Azure AD Connect 和目錄同步作業，將其內部部署 Active Directory Domain Services (AD DS) 樹系中的帳戶集同步處理至 Office 365 中的帳戶集。本文說明如何使用密碼雜湊同步作業將目錄同步作業新增至 Office 365 開發/測試環境，進而產生下列組態。</span><span class="sxs-lookup"><span data-stu-id="515e1-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Active Directory Domain Services (AD DS) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![具有目錄同步作業的 Office 365 開發/測試環境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="515e1-108">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="515e1-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="515e1-109">Office 365 E5 試用訂閱，從您建立的 30 天後到期。</span><span class="sxs-lookup"><span data-stu-id="515e1-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="515e1-p102">簡化的組織內部網路與網際網路連線，由 Azure 虛擬網路的子網路上的三部虛擬機器 (DC1、APP1 及 CLIENT1) 組成。在 APP1 上執行的 Azure AD Connect 會將 AD DS 網域同步處理至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="515e1-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the AD DS domain to Office 365.</span></span>
    
<span data-ttu-id="515e1-112">設定此開發/測試環境有兩個主要階段︰</span><span class="sxs-lookup"><span data-stu-id="515e1-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="515e1-113">建立 Office 365 開發/測試環境 (Azure 虛擬網路中具有 Office 365 E5 試用訂閱的 DC1、APP1 及 CLIENT1 虛擬機器)。</span><span class="sxs-lookup"><span data-stu-id="515e1-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="515e1-114">在 APP1 上安裝及設定 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="515e1-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="515e1-115">按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="515e1-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="515e1-116">階段 1：建立 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="515e1-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="515e1-p103">遵循＜[Office 365 開發/測試環境](office-365-dev-test-environment.md)＞一文階段 1、2、3 中的指示。以下是所產生的組態。</span><span class="sxs-lookup"><span data-stu-id="515e1-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Office 365 開發/測試環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="515e1-120">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="515e1-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="515e1-121">Office 365 E5 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="515e1-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="515e1-122">簡化的組織內部網域與網際網路的連線，由 Azure 虛擬網路的子網路上的 DC1、APP1 及 CLIENT1 虛擬機器組成</span><span class="sxs-lookup"><span data-stu-id="515e1-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="515e1-123">階段 2：在 APP1 上安裝及設定 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="515e1-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="515e1-p104">安裝及設定完成後，Azure AD Connect 就會將 CORP AD DS 網域中的帳戶集與您的 Office 365 試用訂閱中的帳戶集同步處理。下列程序會逐步引導您在 APP1 上安裝 Azure AD Connect，並且確認它可以運作。</span><span class="sxs-lookup"><span data-stu-id="515e1-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP AD DS domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and checking that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="515e1-126">在 APP1 上安裝及設定 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="515e1-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="515e1-127">使用 CORP\\User1 帳戶，從 [Azure 入口網站](https://portal.azure.com)連線到 APP1。</span><span class="sxs-lookup"><span data-stu-id="515e1-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="515e1-128">從 APP1 開啟系統管理員層級 Windows PowerShell 命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="515e1-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="515e1-129">從工作列按一下 [Internet Explorer]\*\*\*\*，然後移至 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="515e1-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="515e1-130">在 [Microsoft Azure Active Directory Connect] 頁面上，按一下 [下載]\*\*\*\*，然後按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="515e1-131">在 [歡迎使用 Azure AD Connect]\*\*\*\* 頁面上，按一下 [我同意]\*\*\*\*，然後按一下 [繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="515e1-132">在 [快速設定]\*\*\*\* 頁面上，按一下 [使用快速設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="515e1-133">在 [連線到 Azure AD]\*\*\*\* 頁面上，在 [使用者名稱]\*\*\*\* 中輸入您的全域系統管理員帳戶名稱，在 [密碼]\*\*\*\* 中輸入其密碼，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="515e1-134">在 [連線到 AD DS]\*\*\*\* 頁面上，在 [使用者名稱]\*\*\*\* 中輸入「**CORP\\User1**」，在 [密碼]\*\*\*\* 中輸入其密碼，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="515e1-135">在 [Azure AD 登入設定]\*\*\*\* 頁面上，按一下 [在不具任何已驗證網域的情況下繼續執行]\*\*\*\*，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="515e1-136">在 [準備設定]\*\*\*\* 頁面上，按一下 [安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="515e1-137">在 [組態完成]\*\*\*\* 頁面上，按一下 [結束]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="515e1-138">在 Internet Explorer 中，移至 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))，然後使用您的全域系統管理員帳戶登入 Office 365 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="515e1-138">In Internet Explorer, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="515e1-139">從主要的入口網站頁面中，按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="515e1-140">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="515e1-p105">請注意名稱為 **User1** 的帳戶。此帳戶是來自 CORP AD DS 網域，且經過證明目錄同步作業可以運作。</span><span class="sxs-lookup"><span data-stu-id="515e1-p105">Note the account named **User1**. This account is from the CORP AD DS domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="515e1-p106">按一下 [User1]\*\*\*\* 帳戶。針對產品授權，按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="515e1-p107">在 [產品授權]\*\*\*\* 中，選取您的國家/地區，然後針對 **Office 365 企業版 E5** 按一下 [關閉]\*\*\*\* 控制項 (切換至 [開啟]\*\*\*\*)。按一下頁面底部的 [儲存]\*\*\*\*，然後按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e1-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="515e1-147">這是所產生的組態。</span><span class="sxs-lookup"><span data-stu-id="515e1-147">This is the resulting configuration.</span></span>
  
![具有目錄同步作業的 Office 365 開發/測試環境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="515e1-149">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="515e1-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="515e1-150">Office 365 E5 試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="515e1-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="515e1-p108">簡化的組織內部網路與網際網路連線，由 Azure 虛擬網路的子網路上的 DC1、APP1 及 CLIENT1 虛擬機器組成。在 APP1 上執行的 Azure AD Connect 會每隔 30 分鐘將 CORP AD DS 網域同步處理至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="515e1-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP AD DS domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="515e1-153">下一步</span><span class="sxs-lookup"><span data-stu-id="515e1-153">Next Step</span></span>

<span data-ttu-id="515e1-154">當您準備好要為您的組織部署目錄同步作業時，請參閱＜[在 Microsoft Azure 中部署 Office 365 目錄同步處理](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)＞。</span><span class="sxs-lookup"><span data-stu-id="515e1-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="515e1-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515e1-155">See Also</span></span>

[<span data-ttu-id="515e1-156">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="515e1-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="515e1-157">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="515e1-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)

[<span data-ttu-id="515e1-158">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="515e1-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)

[<span data-ttu-id="515e1-159">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="515e1-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="515e1-160">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="515e1-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="515e1-161">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="515e1-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




