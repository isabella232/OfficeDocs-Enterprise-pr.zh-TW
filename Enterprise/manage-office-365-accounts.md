---
title: 用來管理 Office 365 帳戶的工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '了解哪些工具，以用來管理 Office 365 使用者，及如何您可以使用取決於如何管理使用者身分識別。 '
ms.openlocfilehash: 0fa515d89afa3abe4b0fe936b297156b20890b0f
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085362"
---
# <a name="tools-to-manage-office-365-accounts"></a><span data-ttu-id="6cc0e-103">用來管理 Office 365 帳戶的工具</span><span class="sxs-lookup"><span data-stu-id="6cc0e-103">Tools to manage Office 365 accounts</span></span>

<span data-ttu-id="6cc0e-p101">您可以根據您的設定數個不同的方式管理 Office 365 使用者。您可以管理 Azure Active Directory 系統入口網站或 Office 365 系統管理中心，Windows PowerShell 您的內部部署目錄中的使用者。一旦您購買 Office 365、 系統管理中心及 Windows PowerShell 可用來管理帳戶。管理雲端身分時您組織中的每個人的 Office 365 會有不同的使用者識別碼和密碼。如果您想要整合與您的內部部署基礎結構與使用者帳戶與 Office 365 同步處理，您可以使用 Azure 作用中的目錄連線至提供之身分識別的同步處理 （選擇性） 提供密碼同步處理或完整單一登入功能。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p101">You can manage Office 365 users in several different ways, depending on your configuration. You can manage users in the Office 365 admin center, Windows PowerShell, your on-premises directory, or in Azure Active Directory admin portal . As soon as you purchase Office 365, the admin center and Windows PowerShell can be used to manage accounts. When managing cloud identities every person in your organization has a separate user ID and password for Office 365. If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Office 365, you can use Azure Active Directory Connect to provide synchronization of identities and optionally provide password synchronization, or full single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="6cc0e-109">何處及如何管理您的使用者帳戶的計劃</span><span class="sxs-lookup"><span data-stu-id="6cc0e-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="6cc0e-p102">何處及如何可以管理您的使用者帳戶，取決於您想要用於您的 Office 365 的身分識別模型。兩個的整體模型是雲端驗證和同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p102">Where and how you can manage your user accounts depends on the identity model you want to use for your Office 365. The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="6cc0e-112">雲端驗證</span><span class="sxs-lookup"><span data-stu-id="6cc0e-112">Cloud authentication</span></span>

- <span data-ttu-id="6cc0e-113">[雲端驗證](about-office-365-identity.md#cloud-authentication)-建立及管理 Office 365 系統管理中心中的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory，來管理您的使用者。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-113">[Cloud authentication](about-office-365-identity.md#cloud-authentication) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
    
- <span data-ttu-id="6cc0e-p103">[密碼雜湊同步處理順暢單一登入搭配](about-office-365-identity.md)-啟用在 Azure AD 驗證內部部署目錄物件的最簡單方式。使用密碼雜湊同步處理 (PHS)，與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="6cc0e-116">[順暢單一登入與通過驗證](about-office-365-identity.md)-提供的 Azure AD 驗證服務來驗證使用者直接與使用一或多個內部部署伺服器上執行的軟體代理程式簡單密碼驗證您內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="6cc0e-117">同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="6cc0e-117">Federated authentication</span></span>

- <span data-ttu-id="6cc0e-118">[同盟驗證選項](about-office-365-identity.md#federated-authentication-options)-主要針對具有較複雜的驗證需求的大型企業組織內部部署目錄物件與 Office 365 同步處理和使用者帳戶是受管理的內部。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-118">[Federated authentication options](about-office-365-identity.md#federated-authentication-options) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="6cc0e-119">[協力廠商驗證及身分識別提供者](about-office-365-identity.md)物件可能會同步至 Office 365 與雲端資源存取內部部署目錄是主要受管理的協力廠商身分識別提供者 (IdP)。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="6cc0e-120">管理帳戶</span><span class="sxs-lookup"><span data-stu-id="6cc0e-120">Managing Accounts</span></span>

<span data-ttu-id="6cc0e-121">當決定您的組織會建立和管理帳戶的方式，請考慮下列各項：</span><span class="sxs-lookup"><span data-stu-id="6cc0e-121">When deciding which way your organization will create and manage accounts, consider the following:</span></span>
  
- <span data-ttu-id="6cc0e-122">目錄同步處理軟體必須安裝在 Office 365 與您的內部部署目錄之間的身分識別連線在內部部署環境中的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-122">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Office 365 and your on-premises directory.</span></span>
    
- <span data-ttu-id="6cc0e-p104">任何目錄同步處理選項，包括 SSO 選項需要您內部部署目錄屬性符合標準。說明如何在您的目錄中使用哪些屬性和需要何種清理 （如果有的話） 所述[來佈建使用者透過目錄同步處理至 Office 365 的準備](prepare-for-directory-synchronization.md)。如需如何使用 IdFix 來自動化目錄清理指示，請參閱[安裝和執行 Office 365 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p104">Any directory synchronization option, including SSO options, requires your on-premises directory attributes meet standards. The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md). See [Install and run the Office 365 IdFix tool](install-and-run-idfix.md) for instruction on how to use IdFix to automate directory cleanup.</span></span> 
    
- <span data-ttu-id="6cc0e-126">規劃您要如何建立 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-126">Plan how you are going to create Office 365 accounts.</span></span>
    
    <span data-ttu-id="6cc0e-127">下表列出不同的帳戶管理工具。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="6cc0e-128">**選項**</span><span class="sxs-lookup"><span data-stu-id="6cc0e-128">**Option**</span></span>|<span data-ttu-id="6cc0e-129">**附註**</span><span class="sxs-lookup"><span data-stu-id="6cc0e-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6cc0e-130">Office 365 admin center</span><span class="sxs-lookup"><span data-stu-id="6cc0e-130">Office 365 admin center</span></span>  <br/> |[<span data-ttu-id="6cc0e-131">個別或大量將使用者新增至 Office 365 - 系統管理說明</span><span class="sxs-lookup"><span data-stu-id="6cc0e-131">Add users individually or in bulk to Office 365 - Admin Help</span></span>](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  <span data-ttu-id="6cc0e-132">提供新增及變更使用者帳戶的簡單 web 介面。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="6cc0e-133">無法用以啟用目錄同步作業時變更使用者 （可以設定位置和授權指派）。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="6cc0e-134">無法與 SSO 選項搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="6cc0e-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cc0e-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="6cc0e-136">使用 Windows PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="6cc0e-136">Manage Office 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="6cc0e-137">可讓您使用 Windows PowerShell 指令碼，將使用者加入在大量的使用者。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="6cc0e-138">可用來將位置和授權指派給不論如何建立帳戶的帳戶。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="6cc0e-139">大量匯入</span><span class="sxs-lookup"><span data-stu-id="6cc0e-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="6cc0e-140">同時將多位使用者新增至 Office 365 - 系統管理說明</span><span class="sxs-lookup"><span data-stu-id="6cc0e-140">Add several users at the same time to Office 365 - Admin Help</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="6cc0e-141">可讓您匯入 CSV 檔案新增至 Office 365 的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-141">Allows you to import a CSV file to add a group of users to Office 365.</span></span>  <br/>  <span data-ttu-id="6cc0e-142">無法與 SSO 選項搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="6cc0e-143">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6cc0e-143">Azure Active Directory</span></span>  <br/> |<span data-ttu-id="6cc0e-p105">您可以取得免費版本的 Azure Active Directory 與 Office 365 訂閱。您可以執行類似自助式密碼重設雲端使用者和自訂的登入及存取面板頁面所使用的是可用的版本的功能。若要取得增強的功能，您可以升級的基本的版本，或 premium edition。請參閱[Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)支援的功能的清單。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p105">You get a free edition of Azure Active Directory with your Office 365 subscription. You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition. To get enhanced functionality, you can upgrade to either the basic edition, or the premium edition. See [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.  </span></span><br/> |
|<span data-ttu-id="6cc0e-148">目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="6cc0e-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="6cc0e-149">整合內部身分識別與 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6cc0e-149">Integrating your on-premises identities with Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="6cc0e-150">為目錄同步作業使用或不密碼同步處理，使用[Azure AD 連線明確的設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="6cc0e-151">針對多個樹系與 SSO 選項、 使用[自訂安裝的 Azure AD 連線](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="6cc0e-152">提供已啟用 SSO 所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="6cc0e-153">許多混合式案例都需要：</span><span class="sxs-lookup"><span data-stu-id="6cc0e-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="6cc0e-154">分段移轉</span><span class="sxs-lookup"><span data-stu-id="6cc0e-154">Staged migration</span></span>  <br/>  <span data-ttu-id="6cc0e-155">混合式 Exchange</span><span class="sxs-lookup"><span data-stu-id="6cc0e-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="6cc0e-156">從您的內部部署目錄同步處理安全性群組和擁有郵件功能的群組。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-156">Synchronizes security and mail-enabled groups from your on-premises directory.</span></span>  <br/> |
   
- <span data-ttu-id="6cc0e-p106">不論如何您想要將使用者帳戶新增至 Office 365，您需要管理數個帳戶功能，例如指派授權，指定位置等等。這些功能可管理長期從 Office 365 系統管理中心或您也可以[使用 Office 365 PowerShell 建立使用者帳戶](https://go.microsoft.com/fwlink/p/?LinkId=717083)。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p106">Regardless of how you intend to add the user accounts to Office 365, you need to manage several account features, such as assigning licenses, specifying location, and so on. These features can be managed long-term from the Office 365 admin center or you can also [create user accounts with Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="6cc0e-p107">如果您選擇新增及管理您的所有使用者透過 Office 365 系統管理中心，您將指定的位置和指派授權，同時做為建立 Office 365 帳戶。因此，不太多規劃是必要的。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p107">If you choose to add and manage all your users through the Office 365 admin center, you will specify the location and assign licenses at the same time as creating the Office 365 account. As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="6cc0e-p108">建立 Office 365 中的帳戶沒有將授權指派 (to SharePoint Online，例如) 表示帳戶擁有人可以檢視 Office 365 入口網站但無法存取任何內公司的訂閱服務。您指派位置和授權之後，帳戶會複寫到服務或您所指定的服務。使用者可以登入其帳戶並使用您指派給他們的服務。</span><span class="sxs-lookup"><span data-stu-id="6cc0e-p108">Creating accounts in Office 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Office 365 portal but can't access any of the services within your company's subscription. After you assign a location and the license, the account is replicated to the service or services that you assigned. The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="6cc0e-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6cc0e-164">Next steps</span></span>

[<span data-ttu-id="6cc0e-165">整合 Office 365 與內部部署環境</span><span class="sxs-lookup"><span data-stu-id="6cc0e-165">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="6cc0e-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cc0e-166">See Also</span></span>

[<span data-ttu-id="6cc0e-167">管理 Office 365 中的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="6cc0e-167">Manage user accounts in Office 365</span></span>](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

