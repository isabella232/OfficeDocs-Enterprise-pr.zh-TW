---
title: 為 Office 365 設定目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何設定 Office 365 和您在內部部署 Active Directory 之間的目錄同步處理。
ms.openlocfilehash: d5c09b006c4e4b9ca9fbe3b0d673435a8ea6637e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070869"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="68846-103">為 Office 365 設定目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="68846-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="68846-104">Office 365 使用雲端型使用者身分識別管理服務 Azure Active Directory 來管理使用者。</span><span class="sxs-lookup"><span data-stu-id="68846-104">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users.</span></span> <span data-ttu-id="68846-105">您也可以與 Office 365 同步內部部署環境，與 Azure AD 整合您的內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="68846-105">You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365.</span></span> <span data-ttu-id="68846-106">一旦您設定同步處理您可以決定有您的內部部署目錄或 Azure AD 內進行其使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="68846-106">Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="68846-107">Office 365 目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="68846-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="68846-108">您可以使用同步處理的身分識別或在內部部署組織與 Office 365 之間的同盟身分識別。</span><span class="sxs-lookup"><span data-stu-id="68846-108">You can either use synchronized identity or federated identity between your on-premises organization and Office 365.</span></span> <span data-ttu-id="68846-109">同步處理的身分識別，管理您內部使用者，以及當他們使用相同的密碼定域機組中為內部部署的 Azure AD 驗證。</span><span class="sxs-lookup"><span data-stu-id="68846-109">With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises.</span></span> <span data-ttu-id="68846-110">這是最常見的目錄同步處理案例。</span><span class="sxs-lookup"><span data-stu-id="68846-110">This is the most common directory synchronization scenario.</span></span> <span data-ttu-id="68846-111">通過驗證] 或 [同盟身分識別，可讓您管理您內部使用者，就會成為驗證您的內部部署目錄。</span><span class="sxs-lookup"><span data-stu-id="68846-111">Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory.</span></span> <span data-ttu-id="68846-112">同盟身分識別需要其他設定，並可讓您只有一次登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="68846-112">Federated identity requires additional configuration and enables your users to only sign in once.</span></span> <span data-ttu-id="68846-113">如需詳細資訊，請閱讀[了解 Office 365 身分識別與 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="68846-113">For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="68846-114">要從 Windows Azure Active Directory 同步處理 (DirSync) 升級至 Azure Active Directory Connect 嗎？</span><span class="sxs-lookup"><span data-stu-id="68846-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="68846-115">如果您目前使用目錄同步，並且想要升級，請前往透過[azure.com](https://azure.com) [升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="68846-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="68846-116">必要條件的 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="68846-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="68846-117">您要取得免費的訂閱 Azure AD 與您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="68846-117">You get a free subscription to Azure AD with your Office 365 subscription.</span></span> <span data-ttu-id="68846-118">當您設定目錄同步處理時，您將安裝 Azure Active Directory Connect 在其中一部內部部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="68846-118">When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="68846-119">針對 Office 365 您將需要：</span><span class="sxs-lookup"><span data-stu-id="68846-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="68846-120">確認您的內部網域 （程序將引導您進行此）。</span><span class="sxs-lookup"><span data-stu-id="68846-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="68846-121">已[指派系統管理員角色在商務用 Office 365 中的](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)您的 Office 365 租用戶的權限和內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="68846-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="68846-122">您的內部部署伺服器安裝 Azure AD Connect，您將需要下列軟體：</span><span class="sxs-lookup"><span data-stu-id="68846-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="68846-123">**伺服器作業系統**</span><span class="sxs-lookup"><span data-stu-id="68846-123">**Server OS**</span></span>|<span data-ttu-id="68846-124">**其他軟體**</span><span class="sxs-lookup"><span data-stu-id="68846-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="68846-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="68846-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="68846-126">-預設會安裝 PowerShell，不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="68846-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="68846-127">額淨 4.5.1 和更新版本提供透過 Windows Update。</span><span class="sxs-lookup"><span data-stu-id="68846-127">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="68846-128">請確定您已安裝最新的更新至控制台] 中的 Windows Server。</span><span class="sxs-lookup"><span data-stu-id="68846-128">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="68846-129">**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="68846-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="68846-130">-在 Windows Management Framework 4.0 中使用 PowerShell 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="68846-130">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="68846-131">在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="68846-131">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="68846-132">-.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="68846-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="68846-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="68846-133">**Windows Server 2008**</span></span> | <span data-ttu-id="68846-134">-在 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)中使用 PowerShell 的最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="68846-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="68846-135">-.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="68846-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="68846-136">如果您使用 Azure Active Directory DirSync，您可以對 Azure Active Directory 同步處理從內部部署 Active Directory 的通訊群組成員的數目上限為 15000。</span><span class="sxs-lookup"><span data-stu-id="68846-136">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000.</span></span> <span data-ttu-id="68846-137">針對 Azure AD Connect，該數量為 50000。</span><span class="sxs-lookup"><span data-stu-id="68846-137">For Azure AD Connect, that number is 50,000.</span></span>
  
<span data-ttu-id="68846-138">若要更仔細檢閱 Azure AD Connect 硬體、 軟體、 帳戶及權限需求、 SSL 憑證需求及物件限制，請閱讀[Azure Active Directory Connect 的必要條件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="68846-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).</span></span>
  
<span data-ttu-id="68846-139">您也可以檢閱 Azure AD Connect[版本版本歷程記錄](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)項目包含以及固定中每個版本。</span><span class="sxs-lookup"><span data-stu-id="68846-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="68846-140">若要設定目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="68846-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="68846-141">登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)，選擇 [**使用者**\>左側導覽窗格上的**作用中的使用者**。</span><span class="sxs-lookup"><span data-stu-id="68846-141">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="68846-142">在系統管理中心中，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="68846-142">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![在 [更多] 功能表中，選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="68846-144">在 [ **Active Directory 準備工作**] 頁面上，選取 [**下載 Microsoft Azure Active Directory Connect 工具**連結若要開始。</span><span class="sxs-lookup"><span data-stu-id="68846-144">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> <span data-ttu-id="68846-145">如需 Azure Active Directory Connect 安裝程序的詳細資訊，請參閱[Azure AD Connect 與 Azure AD Connect Health 安裝藍圖](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="68846-145">For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="68846-146">將授權指派給同步處理的使用者</span><span class="sxs-lookup"><span data-stu-id="68846-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="68846-147">您已同步至 Office 365 使用者之後，他們所建立，但您需要指派授權給他們，讓他們可以使用 Office 365 功能，例如郵件。</span><span class="sxs-lookup"><span data-stu-id="68846-147">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail.</span></span> <span data-ttu-id="68846-148">如需相關指示，請參閱 <<c0>指派給商務用 Office 365 中的使用者授權。</span><span class="sxs-lookup"><span data-stu-id="68846-148">For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="68846-149">完成設定網域</span><span class="sxs-lookup"><span data-stu-id="68846-149">Finish setting up domains</span></span>

<span data-ttu-id="68846-150">請遵循[Office 365 管理您的 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)，以完成您的網域設定] 中的步驟。</span><span class="sxs-lookup"><span data-stu-id="68846-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>