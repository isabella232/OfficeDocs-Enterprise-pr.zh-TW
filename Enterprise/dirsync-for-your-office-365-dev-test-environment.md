---
title: "Office 365 開發人員/測試環境的 DirSync"
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
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "摘要： 設定目錄同步處理 Office 365 開發人員/測試環境。"
ms.openlocfilehash: 8a656ea742af642a8b4dc3e096764f0e8cbde074
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a><span data-ttu-id="cab69-103">Office 365 開發人員/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="cab69-103">DirSync for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="cab69-104">**摘要：**設定 Office 365 開發人員/測試環境的目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="cab69-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="cab69-p101">許多組織使用 Azure AD 連線和目錄同步處理 (DirSync) 同步處理至 Office 365 中的帳戶一組其內部部署 Windows Server Active Directory (AD) 樹系中的帳戶的設定。本文說明如何新增 DirSync 搭配密碼同步處理至 Office 365 開發人員/測試環境中，則產生下列設定。</span><span class="sxs-lookup"><span data-stu-id="cab69-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![具有 DirSync 的 Office 365 開發/測試環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="cab69-108">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="cab69-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="cab69-109">Office 365 E5 試用版訂閱，這會從建立時的 30 天到期。</span><span class="sxs-lookup"><span data-stu-id="cab69-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="cab69-p102">簡化的組織內部網路連線至網際網路上的 Azure 虛擬網路 （DC1、 APP1 和 CLIENT1） 子網路的三個虛擬機器所組成。同步處理至 Office 365 的 Windows Server AD 網域在 APP1 上，執行 azure AD 連線。</span><span class="sxs-lookup"><span data-stu-id="cab69-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="cab69-112">有兩個階段來設定此開發/測試環境：</span><span class="sxs-lookup"><span data-stu-id="cab69-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="cab69-113">建立 Office 365 開發人員/測試環境 （DC1、 APP1 和 CLIENT1 虛擬機器的 Office 365 E5 試用版訂閱與 Azure 虛擬網路中）。</span><span class="sxs-lookup"><span data-stu-id="cab69-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
    
2. <span data-ttu-id="cab69-114">安裝及設定 Azure AD 連接在 APP1 上。</span><span class="sxs-lookup"><span data-stu-id="cab69-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="cab69-115">按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。</span><span class="sxs-lookup"><span data-stu-id="cab69-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="cab69-116">階段 1： 建立 Office 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="cab69-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="cab69-p103">階段 1、 2 及 3 的[Office 365 開發人員/test environment](office-365-dev-test-environment.md) ＞ 一文中遵循的指示。以下是所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="cab69-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Office 365 開發/測試環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="cab69-120">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="cab69-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="cab69-121">Office 365 E5 列印試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="cab69-121">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="cab69-122">簡化的組織內部網路連線至網際網路，DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路所組成。</span><span class="sxs-lookup"><span data-stu-id="cab69-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="cab69-123">在 APP1 上的階段 2： 安裝 Azure AD 連線</span><span class="sxs-lookup"><span data-stu-id="cab69-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="cab69-p104">之後安裝及設定，Azure AD 連線會使用您的 Office 365 試用版訂閱中的帳戶的一組同步處理的公司 Windows Server AD 網域中的帳戶。下列程序步驟您透過在 APP1 上安裝 Azure AD 連線與驗證其運作。</span><span class="sxs-lookup"><span data-stu-id="cab69-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="cab69-126">安裝及設定 Azure AD 連接在 APP1 上</span><span class="sxs-lookup"><span data-stu-id="cab69-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="cab69-127">從[Azure 入口網站](https://portal.azure.com)連線到與公司 APP1\\User1 帳戶。</span><span class="sxs-lookup"><span data-stu-id="cab69-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="cab69-128">從 APP1 開啟系統管理員層級 Windows PowerShell 命令提示字元處，並再執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="cab69-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="cab69-129">從 [任務] 列中，按一下 [ **Internet Explorer** ，並移至[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="cab69-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="cab69-130">在 [Microsoft Azure Active Directory 連線] 頁面上，按一下 [**下載**] 及 [**執行**。</span><span class="sxs-lookup"><span data-stu-id="cab69-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="cab69-131">在 [**歡迎使用 Azure AD 連線**] 頁面上按一下 [**我同意**] 並再按一下 [**繼續]**。</span><span class="sxs-lookup"><span data-stu-id="cab69-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="cab69-132">在 [**明確設定**] 頁面上按一下 [**使用 express 設定**]。</span><span class="sxs-lookup"><span data-stu-id="cab69-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="cab69-133">在 [**連接到 Azure AD** ] 頁面全域管理員帳戶名稱在 [**使用者名稱、**類型及其中輸入密碼**密碼**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="cab69-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="cab69-134">在 [**連接至 AD DS** ] 頁面上輸入**CORP\\User1**的**使用者名稱，**其和中輸入密碼**密碼**，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="cab69-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="cab69-135">在**Azure AD 登入設定**] 頁面上，按一下 [**繼續沒有任何已驗證的網域**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="cab69-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="cab69-136">在 [**準備好設定**] 頁面上按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="cab69-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="cab69-137">在 [**設定完成**] 頁面上按一下 [**結束**]。</span><span class="sxs-lookup"><span data-stu-id="cab69-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="cab69-138">在 Internet Explorer 中，移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="cab69-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="cab69-139">從主要的入口網站] 頁面上，按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="cab69-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="cab69-140">在左導覽列中，按一下 [**使用者 > 作用中使用者**。</span><span class="sxs-lookup"><span data-stu-id="cab69-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="cab69-p105">記下名為**User1**的帳戶。此帳戶是來自公司 Windows Server AD 網域並且 DirSync 具有正常運作的概念。</span><span class="sxs-lookup"><span data-stu-id="cab69-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="cab69-p106">按一下 [ **User1**帳戶。產品授權的按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="cab69-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="cab69-p107">在**產品授權**，選取您的國家/地區] 和 [**關**控制項的**Office 365 企業版 E5** （將它切換到**上**）。按一下頁面底部的 [**儲存**並再按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="cab69-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="cab69-147">這是所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="cab69-147">This is the resulting configuration.</span></span>
  
![具有 DirSync 的 Office 365 開發/測試環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="cab69-149">此組態組成為：</span><span class="sxs-lookup"><span data-stu-id="cab69-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="cab69-150">Office 365 E5 列印試用訂閱。</span><span class="sxs-lookup"><span data-stu-id="cab69-150">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="cab69-p108">簡化的組織內部網路連線至網際網路，DC1、 APP1 和 CLIENT1 虛擬機器上的 Azure 虛擬網路子網路所組成。同步處理至 Office 365 的公司 Windows Server AD 網域每 30 分鐘在 APP1 上，執行 azure AD 連線。</span><span class="sxs-lookup"><span data-stu-id="cab69-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="cab69-153">下一個步驟</span><span class="sxs-lookup"><span data-stu-id="cab69-153">Next Step</span></span>

<span data-ttu-id="cab69-154">當您準備好您的組織部署 DirSync 時，請參閱[部署 Office 365 中目錄同步處理 (DirSync) Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="cab69-154">When you are ready to deploy DirSync for your organization, see [Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cab69-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="cab69-155">See Also</span></span>

[<span data-ttu-id="cab69-156">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="cab69-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="cab69-157">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="cab69-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="cab69-158">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="cab69-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="cab69-159">Office 365 開發人員/測試環境的雲端應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="cab69-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="cab69-160">Office 365 開發人員/測試環境的進階威脅保護</span><span class="sxs-lookup"><span data-stu-id="cab69-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="cab69-161">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="cab69-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




