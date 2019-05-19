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
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162476"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="01c7a-103">為 Office 365 設定目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="01c7a-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="01c7a-104">Office 365 會使用 Azure Active Directory (Azure AD) 租用戶來儲存和管理身分識別驗證及存取雲端式資源的權限。</span><span class="sxs-lookup"><span data-stu-id="01c7a-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="01c7a-105">如果您有內部部署 Active Directory 網域服務 (AD DS)，您可以使用 Office 365 訂閱下 Azure AD 租用戶同步處理您的 AD DS 使用者帳戶、 群組和連絡人。</span><span class="sxs-lookup"><span data-stu-id="01c7a-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="01c7a-106">這是 Office 365 的混合式身分識別。</span><span class="sxs-lookup"><span data-stu-id="01c7a-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="01c7a-107">以下是及其元件。</span><span class="sxs-lookup"><span data-stu-id="01c7a-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="01c7a-108">Azure AD Connect 在內部部署伺服器上執行，並將 AD DS 與 Azure AD 租用戶同步處理。</span><span class="sxs-lookup"><span data-stu-id="01c7a-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="01c7a-109">目錄同步處理，以及您也可以指定這些驗證選項：</span><span class="sxs-lookup"><span data-stu-id="01c7a-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="01c7a-110">密碼雜湊同步處理 (PHS)</span><span class="sxs-lookup"><span data-stu-id="01c7a-110">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="01c7a-111">Azure AD 會執行本身的驗證。</span><span class="sxs-lookup"><span data-stu-id="01c7a-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="01c7a-112">傳遞驗證 (PTA)</span><span class="sxs-lookup"><span data-stu-id="01c7a-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="01c7a-113">Azure AD 具有 AD DS 執行驗證。</span><span class="sxs-lookup"><span data-stu-id="01c7a-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="01c7a-114">同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="01c7a-114">Federated authentication</span></span>

  <span data-ttu-id="01c7a-115">Azure AD 會重新導向的用戶端電腦要求驗證連絡另一個身分識別提供者。</span><span class="sxs-lookup"><span data-stu-id="01c7a-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="01c7a-116">如需詳細資訊，請參閱[混合式身分識別](plan-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="01c7a-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="01c7a-117">1.檢閱 Azure AD Connect 的必要條件</span><span class="sxs-lookup"><span data-stu-id="01c7a-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="01c7a-118">您要取得免費的 Office 365 訂閱的 Azure AD 訂閱。</span><span class="sxs-lookup"><span data-stu-id="01c7a-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="01c7a-119">當您設定目錄同步處理時，您將在其中一部內部部署伺服器上安裝 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="01c7a-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="01c7a-120">Office 365，您必須以：</span><span class="sxs-lookup"><span data-stu-id="01c7a-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="01c7a-121">確認您的內部部署網域。</span><span class="sxs-lookup"><span data-stu-id="01c7a-121">Verify your on-premises domain.</span></span> <span data-ttu-id="01c7a-122">Azure AD Connect 精靈會引導您完成這。</span><span class="sxs-lookup"><span data-stu-id="01c7a-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="01c7a-123">取得的使用者名稱和您的 Office 365 租用戶及 AD DS 的系統管理員帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="01c7a-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="01c7a-124">內部部署伺服器上安裝 Azure AD Connect，您將需要：</span><span class="sxs-lookup"><span data-stu-id="01c7a-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="01c7a-125">**伺服器作業系統**</span><span class="sxs-lookup"><span data-stu-id="01c7a-125">**Server OS**</span></span>|<span data-ttu-id="01c7a-126">**其他軟體**</span><span class="sxs-lookup"><span data-stu-id="01c7a-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="01c7a-127">Windows Server 2012 R2 和更新版本</span><span class="sxs-lookup"><span data-stu-id="01c7a-127">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="01c7a-128">-預設會安裝 PowerShell，不不需要任何動作。</span><span class="sxs-lookup"><span data-stu-id="01c7a-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="01c7a-129">額淨 4.5.1 和更新版本提供透過 Windows Update。</span><span class="sxs-lookup"><span data-stu-id="01c7a-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="01c7a-130">請確定您已安裝最新的更新至控制台] 中的 Windows Server。</span><span class="sxs-lookup"><span data-stu-id="01c7a-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="01c7a-131">Windows Server 2008 R2 Service Pack 1 (SP1) \* \* 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="01c7a-131">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="01c7a-132">-在 Windows Management Framework 4.0 中使用 PowerShell 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="01c7a-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="01c7a-133">在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="01c7a-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="01c7a-134">-.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="01c7a-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="01c7a-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="01c7a-135">Windows Server 2008</span></span> | <span data-ttu-id="01c7a-136">-在 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)中使用 PowerShell 的最新支援的版本。</span><span class="sxs-lookup"><span data-stu-id="01c7a-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="01c7a-137">-.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="01c7a-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="01c7a-138">請參閱 < <b0>Azure Active Directory Connect 的必要條件</b0>for 硬體、 軟體、 帳戶及權限需求、 SSL 憑證需求及物件限制的詳細資料的 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="01c7a-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="01c7a-139">您也可以檢閱 Azure AD Connect[版本版本歷程記錄](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)項目包含以及固定中每個版本。</span><span class="sxs-lookup"><span data-stu-id="01c7a-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="01c7a-140">2.安裝 Azure AD Connect 及設定目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="01c7a-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="01c7a-141">開始之前，請確定您具有：</span><span class="sxs-lookup"><span data-stu-id="01c7a-141">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="01c7a-142">使用者名稱和密碼的 Office 365 全域系統管理員</span><span class="sxs-lookup"><span data-stu-id="01c7a-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="01c7a-143">使用者名稱和密碼的 AD DS 網域系統管理員</span><span class="sxs-lookup"><span data-stu-id="01c7a-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="01c7a-144">哪一種驗證方法 （PHS、 PTA，同盟）</span><span class="sxs-lookup"><span data-stu-id="01c7a-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="01c7a-145">您是否要使用[Azure AD 無縫單一登入 (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="01c7a-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="01c7a-146">請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="01c7a-146">Follow these steps:</span></span>

1. <span data-ttu-id="01c7a-147">登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)(https://admin.microsoft.com) ，然後選擇 [**使用者**\>左側導覽窗格上的**作用中的使用者**。</span><span class="sxs-lookup"><span data-stu-id="01c7a-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="01c7a-148">在系統管理中心中，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。</span><span class="sxs-lookup"><span data-stu-id="01c7a-148">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![在 [更多] 功能表中，選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="01c7a-150">在 [ **Active Directory 準備工作**] 頁面上，選取 [**下載 Microsoft Azure Active Directory Connect 工具**連結若要開始。</span><span class="sxs-lookup"><span data-stu-id="01c7a-150">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="01c7a-151">遵循 [ [Azure AD Connect 與 Azure AD Connect Health 安裝藍圖](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)中的步驟。</span><span class="sxs-lookup"><span data-stu-id="01c7a-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="01c7a-152">3.完成網域設定</span><span class="sxs-lookup"><span data-stu-id="01c7a-152">3. Finish setting up domains</span></span>

<span data-ttu-id="01c7a-153">請遵循[Office 365 管理您的 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)，以完成您的網域設定] 中的步驟。</span><span class="sxs-lookup"><span data-stu-id="01c7a-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="01c7a-154">下一步</span><span class="sxs-lookup"><span data-stu-id="01c7a-154">Next step</span></span>

<span data-ttu-id="01c7a-155">[指派授權給使用者帳戶](assign-licenses-to-user-accounts.md)。</span><span class="sxs-lookup"><span data-stu-id="01c7a-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md).</span></span>
