---
title: 設定 Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何設定 Office 365 與您在內部部署 Active Directory 之間的目錄同步處理。
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555439"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="1d767-103">設定 Office 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="1d767-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="1d767-p101">Office 365 管理使用者使用雲端使用者身分識別管理 Azure Active Directory 服務。您也可以使用 Azure AD 整合您的內部部署 Active Directory 來使用 Office 365 同步處理內部部署環境。一旦您設定同步處理您可以決定有內部部署目錄或 Azure AD 內進行其使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="1d767-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="1d767-107">Office 365 目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="1d767-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="1d767-p102">您可以使用同步處理的身分識別或內部部署組織與 Office 365 之間的同盟身分識別。與同步處理的身分識別管理您的使用者內部部署，並當他們使用相同的密碼在雲端為內部部署的 Azure AD 驗證。這是最常見的目錄同步處理案例。通過驗證] 或 [同盟身分識別可讓您管理您的使用者內部部署和他們通過驗證的內部部署目錄。同盟身分識別需要進行其他設定並可讓您只有一次登入的使用者。如需詳細資訊，請閱讀[了解 Office 365 身分識別與 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="1d767-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="1d767-114">要從 Windows Azure Active Directory 同步處理 (DirSync) 升級至 Azure [Active Directory 連線吗？</span><span class="sxs-lookup"><span data-stu-id="1d767-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="1d767-115">如果您在使用 DirSync，想要升級的[升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)向透過[azure.com](https://azure.com) 。</span><span class="sxs-lookup"><span data-stu-id="1d767-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="1d767-116">Azure AD 的先決條件連線</span><span class="sxs-lookup"><span data-stu-id="1d767-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="1d767-p103">您要取得與 Office 365 訂閱免費訂閱 Azure AD。當您設定目錄同步作業時，您將會安裝 Azure [Active Directory 連線在其中一部內部伺服器。</span><span class="sxs-lookup"><span data-stu-id="1d767-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="1d767-119">Office 365 的您必須：</span><span class="sxs-lookup"><span data-stu-id="1d767-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="1d767-120">確認您的內部部署網域 （程序將會帶領您完成此）。</span><span class="sxs-lookup"><span data-stu-id="1d767-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="1d767-121">已[指派管理員角色在 Office 365 企業版](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)Office 365 租用戶的權限和內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="1d767-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="1d767-122">安裝 Azure AD 連接內部部署伺服器您將需要下列軟體：</span><span class="sxs-lookup"><span data-stu-id="1d767-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="1d767-123">**伺服器 OS**</span><span class="sxs-lookup"><span data-stu-id="1d767-123">**Server OS**</span></span>|<span data-ttu-id="1d767-124">**其他軟體**</span><span class="sxs-lookup"><span data-stu-id="1d767-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1d767-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="1d767-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="1d767-126">預設會安裝 PowerShell、 不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="1d767-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="1d767-p104">互打 4.5.1 並提供更新版本的 Windows Update 透過。請確定您已安裝最新的更新在控制台中的 Windows server。</span><span class="sxs-lookup"><span data-stu-id="1d767-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="1d767-129">**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="1d767-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="1d767-p105">-使用 Windows Management Framework 4.0 中 PowerShell 的最新版本。在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜尋它。</span><span class="sxs-lookup"><span data-stu-id="1d767-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="1d767-132">-.Net 4.5.1 及更新的版本是位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="1d767-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="1d767-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="1d767-133">**Windows Server 2008**</span></span> | <span data-ttu-id="1d767-134">-使用 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)的 PowerShell 最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="1d767-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="1d767-135">-.Net 4.5.1 及更新的版本是位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="1d767-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="1d767-p106">如果您使用 Azure Active Directory DirSync，您可以對 Azure Active Directory 同步處理從內部部署 Active Directory 的通訊群組成員數目上限為 15000。Azure AD 連線，該號碼為 50000。</span><span class="sxs-lookup"><span data-stu-id="1d767-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="1d767-138">更多謹慎檢閱硬體、 軟體、 帳戶和權限需求、 SSL 憑證需求，以及 Azure AD 連接中的物件限制讀取[Azure 作用中的目錄連線的先決條件](https://go.microsoft.com/fwlink/p/?LinkId=716896)。</span><span class="sxs-lookup"><span data-stu-id="1d767-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="1d767-139">您也可以檢閱 Azure AD 連接[版本版本歷程記錄](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)項目包含以及固定在每個版本中。</span><span class="sxs-lookup"><span data-stu-id="1d767-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="1d767-140">若要設定目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="1d767-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="1d767-141">登入 Office 365 系統管理中心並且選擇 [**使用者** \> **作用中使用者**在左導覽列中。</span><span class="sxs-lookup"><span data-stu-id="1d767-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="1d767-142">在 Office 365 系統管理中心，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="1d767-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![在 [更多] 功能表中選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="1d767-p107">在 [ **Active Directory 準備工作**] 頁面上選取 [開始**下載 Microsoft Azure Active Directory 連線工具**連結。如需 Azure [Active Directory 連線安裝程序的詳細資訊，請參閱[Azure AD Connect 及 Azure AD 連線狀況安裝藍圖](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="1d767-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="1d767-146">將授權指派給同步處理的使用者</span><span class="sxs-lookup"><span data-stu-id="1d767-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="1d767-p108">您已同步處理至 Office 365 使用者之後，會在建立時，但您必須將授權指派給他們，以便他們可以使用 Office 365 的功能，例如郵件。指示，請參閱[指派給 Office 365 中的商務使用者的授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="1d767-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="1d767-149">完成的網域設定</span><span class="sxs-lookup"><span data-stu-id="1d767-149">Finish setting up domains</span></span>

<span data-ttu-id="1d767-150">請遵循[的 Office 365 管理 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成設定您的網域中的步驟。</span><span class="sxs-lookup"><span data-stu-id="1d767-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>