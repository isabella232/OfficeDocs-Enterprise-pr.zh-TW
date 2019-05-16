---
title: Office 365 與內部部署環境整合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何將 Office 365 與您現有的目錄服務整合。
ms.openlocfilehash: 1fa044a0a9db0d8422239cf301fea21a2c3d47e9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069739"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="2af15-103">Office 365 與內部部署環境整合</span><span class="sxs-lookup"><span data-stu-id="2af15-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="2af15-104">您可以將整合 Office 365 與您現有的目錄服務和內部部署安裝的 Exchange Server、 Skype Server 2015，或 SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="2af15-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="2af15-105">當您在整合與目錄服務時，您可以同步處理及管理使用者帳戶的兩個環境。</span><span class="sxs-lookup"><span data-stu-id="2af15-105">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="2af15-106">您也可以新增密碼雜湊同步處理或單一登入 (SSO)，使用者還是可以登入兩個環境使用其內部部署認證。</span><span class="sxs-lookup"><span data-stu-id="2af15-106">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="2af15-107">當您在整合的內部部署伺服器產品時，您會建立混合式環境。</span><span class="sxs-lookup"><span data-stu-id="2af15-107">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="2af15-108">混合式環境可協助您將使用者或資訊移轉至 Office 365，或您可以繼續有一些使用者或某些資訊在內部和部分定域機組中。</span><span class="sxs-lookup"><span data-stu-id="2af15-108">A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="2af15-109">如需有關混合式環境的詳細資訊，請參閱[Office 365 的混合式雲端解決方案概觀](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)。</span><span class="sxs-lookup"><span data-stu-id="2af15-109">For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="2af15-110">您也可以使用 Azure AD 建議的自訂的設定指導方針：</span><span class="sxs-lookup"><span data-stu-id="2af15-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="2af15-111">Azure AD Connect 顧問</span><span class="sxs-lookup"><span data-stu-id="2af15-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="2af15-112">AD FS 部署建議程式</span><span class="sxs-lookup"><span data-stu-id="2af15-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="2af15-113">Azure RMS 部署精靈</span><span class="sxs-lookup"><span data-stu-id="2af15-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="2af15-114">Azure AD Premium 安裝指引</span><span class="sxs-lookup"><span data-stu-id="2af15-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="2af15-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="2af15-115">Before you begin</span></span>
<span data-ttu-id="2af15-116">整合 Office 365 和內部部署環境之前，您也需要參加[網路規劃](network-planning-and-performance.md)和效能調整的 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2af15-116">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span> <span data-ttu-id="2af15-117">您也會想要了解 Office 365 中可用的[身分識別模型](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="2af15-117">You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="2af15-118">請參閱[位置來管理 Office 365 使用者帳戶](manage-office-365-accounts.md)的工具來管理 Office 365 使用者帳戶，您可以使用的清單。</span><span class="sxs-lookup"><span data-stu-id="2af15-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="2af15-119">Office 365 與目錄服務整合</span><span class="sxs-lookup"><span data-stu-id="2af15-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="2af15-120">如果您有現有的使用者帳戶在內部部署目錄中，您不想重新建立所有 Office 365 和簡介差異或錯誤環境之間的風險中這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="2af15-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="2af15-121">目錄同步處理可協助您鏡像這些帳戶之間線上和內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="2af15-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="2af15-122">目錄同步處理，您的使用者不需要針對每個環境中，新的資訊，請記得，您不必建立或兩次更新帳戶。</span><span class="sxs-lookup"><span data-stu-id="2af15-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="2af15-123">您想要[準備您的內部部署目錄](prepare-for-directory-synchronization.md)進行目錄同步處理，您可以執行這項操作以手動方式或使用[IdFix 工具](install-and-run-idfix.md)（IdFix 工具只能與 Active Directory）。</span><span class="sxs-lookup"><span data-stu-id="2af15-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![若要保留在內部部署和線上的使用者帳戶資訊同步處理使用目錄同步處理](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="2af15-125">如果您希望使用者能夠使用其內部部署認證登入 Office 365，您也可以設定 SSO。</span><span class="sxs-lookup"><span data-stu-id="2af15-125">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="2af15-126">SSO，與 Office 365 設定為信任的使用者驗證的內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="2af15-126">With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![搭配單一登入，相同的帳戶是可在內部部署與線上環境](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="2af15-128">不同的使用者帳戶管理技術為您的使用者，提供不同的體驗，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="2af15-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="2af15-129">**包含或不含密碼雜湊同步處理或通過驗證的目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="2af15-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="2af15-130">使用者登入他們的內部部署環境與其使用者帳戶 （網域 \ 使用者名稱）。</span><span class="sxs-lookup"><span data-stu-id="2af15-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="2af15-131">當他們移至 Office 365 時，他們必須登入一次使用其公司或學校帳戶 (user@domain.com)。</span><span class="sxs-lookup"><span data-stu-id="2af15-131">When they go to Office 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="2af15-132">兩個環境中的相同使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2af15-132">The user name is the same in both environments.</span></span> <span data-ttu-id="2af15-133">當您新增密碼雜湊同步處理或通過驗證時，使用者有兩個環境中，相同的密碼，但會有提供這些認證，登入 Office 365 時。</span><span class="sxs-lookup"><span data-stu-id="2af15-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365.</span></span> <span data-ttu-id="2af15-134">目錄同步處理與密碼雜湊同步處理時最常使用的目錄同步處理案例。</span><span class="sxs-lookup"><span data-stu-id="2af15-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="2af15-135">若要設定目錄同步處理，使用 Azure Active Directory Connect。</span><span class="sxs-lookup"><span data-stu-id="2af15-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="2af15-136">如需相關指示，請閱讀[設定 Office 365 的目錄同步處理](set-up-directory-synchronization.md)，並[使用 Azure AD Connect 搭配快速設定](https://go.microsoft.com/fwlink/p/?LinkId=698537)。</span><span class="sxs-lookup"><span data-stu-id="2af15-136">For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="2af15-137">深入了解[準備透過目錄同步處理至 Office 365 使用者佈建](prepare-for-directory-synchronization.md)並[整合您內部部署識別與 Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101)。</span><span class="sxs-lookup"><span data-stu-id="2af15-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="2af15-138">**目錄同步處理與 SSO**</span><span class="sxs-lookup"><span data-stu-id="2af15-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="2af15-139">使用者登入他們的內部部署環境與其使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2af15-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="2af15-140">當他們移至 Office 365 時，他們可以登入自動執行，或他們登入他們使用其內部部署環境 （網域 \ 使用者名稱） 的相同認證。</span><span class="sxs-lookup"><span data-stu-id="2af15-140">When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="2af15-141">若要設定 SSO 您也會使用 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="2af15-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="2af15-142">如需相關指示，請閱讀[使用 Azure AD Connect 搭配自訂設定](https://go.microsoft.com/fwlink/p/?LinkID=698430)。</span><span class="sxs-lookup"><span data-stu-id="2af15-142">For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="2af15-143">深入了解[應用程式的存取和單一登入與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="2af15-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="2af15-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="2af15-144">Azure AD Connect</span></span>
<span data-ttu-id="2af15-145">Azure AD Connect 會取代舊版的身分識別整合工具，例如 DirSync 和 Azure AD 同步處理。如需詳細資訊，請參閱[整合內部部署身分識別與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969)。</span><span class="sxs-lookup"><span data-stu-id="2af15-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="2af15-146">如果您想要從 Azure Active Directory 同步處理到 Azure AD Connect 更新，請參閱 <<c0>的升級指示。</span><span class="sxs-lookup"><span data-stu-id="2af15-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> <span data-ttu-id="2af15-147">請參閱針對[Office 365 目錄同步處理 (DirSync) 在 Microsoft Azure 中](https://go.microsoft.com/fwlink/?LinkId=517887)建置解決方案架構。</span><span class="sxs-lookup"><span data-stu-id="2af15-147">See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>