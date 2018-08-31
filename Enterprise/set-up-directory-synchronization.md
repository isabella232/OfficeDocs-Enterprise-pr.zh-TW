---
title: 設定 Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何設定 Office 365 與您在內部部署 Active Directory 之間的目錄同步處理。
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539961"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="62919-103">設定 Office 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="62919-103">Set up directory synchronization for Office 365</span></span>
<span data-ttu-id="62919-p101">Office 365 管理使用者使用雲端使用者身分識別管理 Azure Active Directory 服務。您也可以使用 Azure AD 整合您的內部部署 Active Directory 來使用 Office 365 同步處理內部部署環境。一旦您設定同步處理您可以決定有內部部署目錄或 Azure AD 內進行其使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="62919-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="62919-107">Office 365 目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="62919-107">Office 365 directory synchronization</span></span>
<span data-ttu-id="62919-p102">您可以使用同步處理的身分識別或內部部署組織與 Office 365 之間的同盟身分識別。與同步處理的身分識別管理您的使用者內部部署，並當他們使用相同的密碼在雲端為內部部署的 Azure AD 驗證。這是最常見的目錄同步處理案例。通過驗證] 或 [同盟身分識別可讓您管理您的使用者內部部署和他們通過驗證的內部部署目錄。同盟身分識別需要進行其他設定並可讓您只有一次登入的使用者。如需詳細資訊，請閱讀[了解 Office 365 身分識別與 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="62919-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="62919-114">要從 Windows Azure Active Directory 同步處理 (DirSync) 升級至 Azure [Active Directory 連線吗？</span><span class="sxs-lookup"><span data-stu-id="62919-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>
<span data-ttu-id="62919-115">如果您在使用 DirSync，想要升級的[升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)向透過[azure.com](https://azure.com) 。</span><span class="sxs-lookup"><span data-stu-id="62919-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="62919-116">Azure AD 的先決條件連線</span><span class="sxs-lookup"><span data-stu-id="62919-116">Prerequisites for Azure AD Connect</span></span>
<span data-ttu-id="62919-p103">您要取得與 Office 365 訂閱免費訂閱 Azure AD。當您設定目錄同步作業時，您將會安裝 Azure [Active Directory 連線在其中一部內部伺服器。</span><span class="sxs-lookup"><span data-stu-id="62919-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="62919-119">Office 365 的您必須：</span><span class="sxs-lookup"><span data-stu-id="62919-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="62919-120">確認您的內部部署網域 （程序將會帶領您完成此）。</span><span class="sxs-lookup"><span data-stu-id="62919-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="62919-121">已[指派管理員角色在 Office 365 企業版](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)Office 365 租用戶的權限和內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="62919-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span> 
    
<span data-ttu-id="62919-122">安裝 Azure AD 連接內部部署伺服器您將需要下列軟體：</span><span class="sxs-lookup"><span data-stu-id="62919-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="62919-123">**伺服器 OS**</span><span class="sxs-lookup"><span data-stu-id="62919-123">**Server OS**</span></span>|<span data-ttu-id="62919-124">**其他軟體**</span><span class="sxs-lookup"><span data-stu-id="62919-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62919-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="62919-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="62919-126">預設會安裝 PowerShell、 不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="62919-126">- PowerShell is installed by default, no action is required.</span></span>  <br/> <span data-ttu-id="62919-p104">互打 4.5.1 並提供更新版本的 Windows Update 透過。請確定您已安裝最新的更新在控制台中的 Windows server。</span><span class="sxs-lookup"><span data-stu-id="62919-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="62919-129">**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="62919-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="62919-p105">-使用 Windows Management Framework 4.0 中 PowerShell 的最新版本。在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜尋它。</span><span class="sxs-lookup"><span data-stu-id="62919-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br/> <span data-ttu-id="62919-132">-.Net 4.5.1 及更新的版本是位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="62919-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="62919-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="62919-133">**Windows Server 2008**</span></span> | <span data-ttu-id="62919-134">-使用 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)的 PowerShell 最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="62919-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br/> <span data-ttu-id="62919-135">-.Net 4.5.1 及更新的版本是位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="62919-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
   
> [!NOTE]
> <span data-ttu-id="62919-p106">如果您使用 Azure Active Directory DirSync，您可以對 Azure Active Directory 同步處理從內部部署 Active Directory 的通訊群組成員數目上限為 15000。Azure AD 連線，該號碼為 50000。</span><span class="sxs-lookup"><span data-stu-id="62919-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="62919-138">更多謹慎檢閱硬體、 軟體、 帳戶和權限需求、 SSL 憑證需求，以及 Azure AD 連接中的物件限制讀取[Azure 作用中的目錄連線的先決條件](https://go.microsoft.com/fwlink/p/?LinkId=716896)。</span><span class="sxs-lookup"><span data-stu-id="62919-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="62919-139">您也可以檢閱 Azure AD 連接[版本版本歷程記錄](https://go.microsoft.com/fwlink/p/?LinkId=733238)項目包含以及固定在每個版本中。</span><span class="sxs-lookup"><span data-stu-id="62919-139">You can also review the Azure AD Connect [version release history](https://go.microsoft.com/fwlink/p/?LinkId=733238) to see what is included and fixed in each release.</span></span> 

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="62919-140">若要設定目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="62919-140">To set up directory synchronization</span></span>
1. <span data-ttu-id="62919-141">登入 Office 365 系統管理中心並且選擇 [**使用者** \> **作用中使用者**在左導覽列中。</span><span class="sxs-lookup"><span data-stu-id="62919-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span> 
2. <span data-ttu-id="62919-142">在 Office 365 系統管理中心，在**作用中使用者**] 頁面上，選擇 [* * 更 * * \> **目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="62919-142">In the Office 365 admin center, on the **Active users** page, choose ** More ** \> **Directory synchronization**.</span></span>
    
    ![在 [更多] 功能表中選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="62919-p107">在 * * 為目錄同步處理適合您嗎？* *] 頁面上的兩個的第一個選擇的**1-10**和**11 50**結果在"根據組織的大小，建議您建立及管理在雲端中的使用者。使用目錄同步處理會使您的安裝程式更複雜。移至作用中使用者加入您的使用者 」。</span><span class="sxs-lookup"><span data-stu-id="62919-p107">On the ** Is directory sync right for you? ** page, the two first choices of **1-10**, and **11-50** result in "Based on the size of your organization, we recommend that you create and manage users in the cloud. Using directory synchronization will make your setup more complex. Go to Active users to add your users."</span></span> 
    
    - <span data-ttu-id="62919-148">您還是可以，不過，繼續設定目錄同步處理選擇**以下繼續**在頁面底部。</span><span class="sxs-lookup"><span data-stu-id="62919-148">You can still, however, continue setting up directory synchronization by choosing **Continue here** on the bottom of the page.</span></span> 
    
    - <span data-ttu-id="62919-p108">如果您選取兩個的選擇後者**51-250** **大於或等於 251**、 同步處理設定將會建議目錄同步處理。選擇 [**下一步**繼續執行。</span><span class="sxs-lookup"><span data-stu-id="62919-p108">If you select the two latter choices, **51-250** or **251 or greater**, the synchronization setup will recommend directory synchronization. Choose **Next** to continue.</span></span> 
    
    ![選擇 [下一步] 繼續進行目錄同步處理設定](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. <span data-ttu-id="62919-152">在**同步處理您的本機目錄與雲端**中讀取資訊，及如果您想的詳細資訊，請選擇了解更多連結會移到：[佈建使用者可透過目錄同步處理至 Office 365 的準備](prepare-for-directory-synchronization.md)，然後選擇 [下一步****.</span><span class="sxs-lookup"><span data-stu-id="62919-152">On the **Sync your local directory with the cloud**, read the information, and if you want more information, choose the learn more link that goes to: [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md), and then choose **Next**.</span></span> 
    
5. <span data-ttu-id="62919-p109">在**我們檢查您的目錄**] 頁面上檢閱自動檢查您的目錄的需求。如果符合需求，選擇 [**下一步** \> **開始掃描**。如果您不能符合要求您仍然可以繼續選擇 [**繼續] 以手動方式**。</span><span class="sxs-lookup"><span data-stu-id="62919-p109">On the **Let's check your directory** page, review the requirements for automatically checking your directory. If you meet the requirements, choose **Next** \> **Start scan**. If you can't meet the requirements you can still continue by choosing **continue manually**.</span></span>
    
    ![選擇 [下一步] 或手動在繼續我們檢查您的目錄] 頁面上](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. <span data-ttu-id="62919-157">如果您選取要掃描您的目錄，選擇 [**開始掃描****評估目錄同步處理設定**] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="62919-157">If you select to scan your directories, choose **Start scan** on the **Evaluating directory synchronization setup** page.</span></span> 
    
    <span data-ttu-id="62919-158">遵循下載並執行掃描的指示。</span><span class="sxs-lookup"><span data-stu-id="62919-158">Follow the instructions to download and run the scan.</span></span>
    
7. <span data-ttu-id="62919-159">掃描完成後，回到 [安裝精靈] 並選擇 [**下一步**查看掃描結果。</span><span class="sxs-lookup"><span data-stu-id="62919-159">Once the scan is complete, return to the setup wizard, and choose **Next** to see your scan results.</span></span> 
    
8. <span data-ttu-id="62919-p110">依指示在**驗證擁有權的網域**] 頁面上確認您的網域。如需詳細指示，請參閱[Office 365 管理 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)。</span><span class="sxs-lookup"><span data-stu-id="62919-p110">Verify your domains as instructed on the **Verify Ownership of your domains** page. For detailed instructions, see [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="62919-p111">新增 TXT 記錄，以確認您擁有網域之後，不前往 [網域] 精靈中新增使用者的下一個步驟。目錄同步作業會將使用者新增為您。</span><span class="sxs-lookup"><span data-stu-id="62919-p111">After you have added a TXT record to verify you own your domain, do not go to the next step of adding users in the domains wizard. The directory synchronization will add users for you.</span></span> 
  
    <span data-ttu-id="62919-164">傳回**Office 365 設定**] 頁面上，選擇 [**重新整理**</span><span class="sxs-lookup"><span data-stu-id="62919-164">Return to the **Office 365 Setup** page and choose **Refresh**</span></span>
    
    ![確認您的網域之後，請選擇 [重新整理](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. <span data-ttu-id="62919-166">在**您的網域已準備就緒**] 頁面上選擇 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="62919-166">On the **Your domains are ready** page, choose **Next**.</span></span>
    
10. <span data-ttu-id="62919-p112">**清理您的環境**] 索引標籤上 （選用） 依照指示下載 IDFix 檢查您的 Active Directory。選擇 [**下一步**繼續執行。</span><span class="sxs-lookup"><span data-stu-id="62919-p112">On the **Clean up your environment** page, optionally follow the instructions to download IDFix to check your Active Directory. Choose **Next** to continue.</span></span> 
    
11. <span data-ttu-id="62919-169">在 * * 執行 Azure Active Directory 連線 * *] 頁面上，選擇 [**下載**] 以安裝 Azure AD 連線精靈]。</span><span class="sxs-lookup"><span data-stu-id="62919-169">On the ** Run Azure Active Directory Connect ** page, choose **Download** to install Azure AD Connect wizard.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="62919-p113">此時您就會在 Azure AD 連線精靈]。請務必保留您已上次在開啟在瀏覽器中，因此您可以將它的 Azure AD Connect 步驟已完成後返回 [目錄同步處理精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62919-p113">At this point you will be in the Azure AD Connect wizard. Make sure you leave the directory synchronization wizard page you were last on open in your browser, so you can return to it after the Azure AD Connect steps are done.</span></span> 
  
    <span data-ttu-id="62919-p114">Azure AD 連線精靈已完成安裝後將會自動開啟它。您也可以從您的桌面預設安裝網站開啟它。請遵循精靈的指示進行根據您的案例：</span><span class="sxs-lookup"><span data-stu-id="62919-p114">After Azure AD Connect wizard has installed it will automatically open. You can also open it from your desktop, the default install site. Follow the wizard instructions depending on your scenario:</span></span>
    
  - <span data-ttu-id="62919-175">使用密碼雜湊同步處理的目錄同步作業，使用[Azure AD 連線明確的設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。</span><span class="sxs-lookup"><span data-stu-id="62919-175">For directory synchronization with password hash synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>
    
  - <span data-ttu-id="62919-176">針對多個樹系、 通過驗證、 同盟身分識別與 SSO 選項、 使用[自訂安裝的 Azure AD 連線](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="62919-176">For multiple forests, pass-through authentication, federated identity and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
    
    <span data-ttu-id="62919-177">**自訂** **Express 設定**] 頁面上選取要使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="62919-177">Select **Customize** on the **Express Settings** page to use these options.</span></span> 
    
12. <span data-ttu-id="62919-p115">Azure AD 連線精靈] 完成之後，回到 [ **Office 365 設定**精靈] 並依照上**進行確認同步處理作業如預期] 頁面上**的指示。選擇 [**下一步**繼續執行。</span><span class="sxs-lookup"><span data-stu-id="62919-p115">After the Azure AD Connect wizard is done, return to the **Office 365 Setup** wizard, and follow the instructions on the **Make sure sync worked as expected page**. Choose **Next** to continue.</span></span> 
    
13. <span data-ttu-id="62919-180">閱讀指示 * * 啟動使用者 * *] 頁面上，然後選擇 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="62919-180">Read the instructions on the ** Activate users ** page and then choose **Next**.</span></span>
    
14. <span data-ttu-id="62919-181">**您是所有的安裝程式**] 頁面上選擇 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="62919-181">Choose **Finish** on the **You're all setup** page.</span></span> 
    
## <a name="assign-licences-to-synchronized-users"></a><span data-ttu-id="62919-182">將授權指派給同步處理的使用者</span><span class="sxs-lookup"><span data-stu-id="62919-182">Assign licences to synchronized users</span></span>
<span data-ttu-id="62919-p116">您已同步處理至 Office 365 使用者之後，會在建立時，但您必須將授權指派給他們，以便他們可以使用 Office 365 的功能，例如郵件。指示，請參閱[指派給 Office 365 中的商務使用者的授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="62919-p116">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
    
## <a name="finish-setting-up-domains"></a><span data-ttu-id="62919-185">完成的網域設定</span><span class="sxs-lookup"><span data-stu-id="62919-185">Finish setting up domains</span></span>
<span data-ttu-id="62919-186">請遵循[的 Office 365 管理 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成設定您的網域中的步驟。</span><span class="sxs-lookup"><span data-stu-id="62919-186">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>