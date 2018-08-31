---
title: 與內部部署環境的 office 365 整合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何將與您現有的目錄服務整合 Office 365。
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540090"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="d8f5d-103">與內部部署環境的 office 365 整合</span><span class="sxs-lookup"><span data-stu-id="d8f5d-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="d8f5d-104">您可以針對 Business Server 2015、 或 SharePoint Server 2013 使用您現有的目錄服務與內部部署安裝的 Exchange Server、 Skype 整合 Office 365。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="d8f5d-p101">當您與目錄服務整合時，您可以同步處理及管理這兩個環境的使用者帳戶。您也可以新增密碼雜湊同步處理或單一登入 (SSO) 讓使用者可以登入內部部署認證與這兩個環境。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p101">When you integrate with directory services, you can synchronize and manage user accounts for both environments. You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="d8f5d-p102">當您與內部部署伺服器產品整合時，您會建立在混合式環境。混合式環境可以協助使用者或資訊移轉至 Office 365 或您可以繼續有一些使用者或某些資訊在內部以及部分雲端中。如需混合式環境的詳細資訊，請參閱[Office 365 的混合式雲端解決方案概觀](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p102">When you integrate with on-premises server products, you create a hybrid environment. A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud. For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="d8f5d-110">您也可以使用 Azure AD 顧問的自訂的安裝指引：</span><span class="sxs-lookup"><span data-stu-id="d8f5d-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="d8f5d-111">Azure AD Connect 顧問</span><span class="sxs-lookup"><span data-stu-id="d8f5d-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="d8f5d-112">AD FS 部署顧問</span><span class="sxs-lookup"><span data-stu-id="d8f5d-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="d8f5d-113">Azure RMS 部署精靈</span><span class="sxs-lookup"><span data-stu-id="d8f5d-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="d8f5d-114">Azure AD Premium 安裝指引</span><span class="sxs-lookup"><span data-stu-id="d8f5d-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="d8f5d-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="d8f5d-115">Before you begin</span></span>
<span data-ttu-id="d8f5d-p103">您整合 Office 365 與內部部署環境之前，您也需要參加與[網路規劃和 Office 365 的效能調整](network-planning-and-performance.md)。您也會想要了解 Office 365 中可用的[身分識別模型](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p103">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md). You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="d8f5d-118">請參閱[位置來管理 Office 365 使用者帳戶](manage-office-365-accounts.md)的工具可用來管理 Office 365 使用者帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="d8f5d-119">與目錄服務整合 Office 365</span><span class="sxs-lookup"><span data-stu-id="d8f5d-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="d8f5d-p104">如果您有現有的使用者帳戶的內部部署目錄中，您不想重新建立所有這些帳戶在 Office 365 和簡介 （英文） 複寫差異處或錯誤環境之間的風險。目錄同步處理可協助您鏡像那些帳戶之間在線上和內部部署環境。使用目錄同步處理您的使用者不需要為每個環境、 新的資訊，請記得與您不需要建立或更新帳戶兩次。您將需要目錄同步作業[準備您的內部部署目錄](prepare-for-directory-synchronization.md)，您可以執行這項作業以手動方式或使用[IdFix 工具](install-and-run-idfix.md)（IdFix 工具僅可透過 Active Directory）。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p104">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments. Directory synchronization helps you mirror those accounts between your online and on-premises environments. With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice. You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![使用目錄同步處理可保留在內部部署和線上的使用者帳戶資訊進行同步處理](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="d8f5d-p105">如果您想要能夠使用其內部部署認證登入 Office 365 的使用者，您也可以設定 SSO。使用 SSO，Office 365 已設定為信任的使用者驗證的內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p105">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO. With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![搭配單一登入，相同的帳戶是可在內部部署與線上環境](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="d8f5d-128">不同的使用者帳戶管理技巧 （英文） 提供的不同經驗供使用者，使用下表所示。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="d8f5d-129">**使用或不密碼雜湊同步處理或通過驗證目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="d8f5d-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="d8f5d-p106">使用者登入其內部部署環境中使用其使用者帳戶 (domain\username)。當他們移至 Office 365 時，他們必須再次登入其工作或學校的帳戶 (user@domain.com)。這兩個環境中的相同使用者名稱。新增密碼雜湊同步處理] 或 [通過驗證之後，使用者有相同的密碼這兩個環境中，但必須登入 Office 365 時一次提供所需的認證。使用密碼雜湊同步處理的目錄同步作業是最常用的目錄同步處理案例。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p106">A user logs on to their on-premises environment with their user account (domain\username). When they go to Office 365, they must log on again with their work or school account (user@domain.com). The user name is the same in both environments. When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365. Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="d8f5d-p107">若要設定目錄同步作業，使用 Azure Active Directory 連線。指示，請閱讀[Office 365 的目錄同步作業設定](set-up-directory-synchronization.md)及[使用 Azure AD Connect 明確設定](https://go.microsoft.com/fwlink/p/?LinkId=698537)。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p107">To set up directory synchronization, use Azure Active Directory Connect. For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="d8f5d-137">深入了解[準備透過目錄同步處理至 Office 365 的使用者佈建](prepare-for-directory-synchronization.md)和[整合內部會識別與 Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101)。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="d8f5d-138">**與 SSO 的目錄同步處理**</span><span class="sxs-lookup"><span data-stu-id="d8f5d-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="d8f5d-p108">使用者登入其內部部署環境中使用其使用者帳戶。當他們移至 Office 365 時，他們也登入自動，或登入他們使用其內部部署環境 (domain\username) 的相同認證。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p108">A user logs on to their on-premises environment with their user account. When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="d8f5d-p109">若要設定 SSO 也使用 Azure AD 連線。指示，請閱讀[使用自訂設定使用 Azure AD 連線]](https://go.microsoft.com/fwlink/p/?LinkID=698430)。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p109">To set up SSO you also use Azure AD Connect. For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="d8f5d-143">深入了解[應用程式存取與單一登入與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="d8f5d-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="d8f5d-144">Azure AD Connect</span></span>
<span data-ttu-id="d8f5d-p110">Azure AD 連線會取代為舊版的身分識別的整合工具，例如 DirSync 以及 Azure AD 同步處理。如需詳細資訊，請參閱[您的內部部署身分識別與 Azure Active Directory 的整合](https://go.microsoft.com/fwlink/p/?LinkId=527969)。如果您想要更新的 Azure Active Directory 同步處理 Azure AD 連線，請參閱[的升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。請參閱[Office 365 目錄同步處理 (DirSync) Microsoft Azure 中](https://go.microsoft.com/fwlink/?LinkId=517887)的內建的解決方案架構。</span><span class="sxs-lookup"><span data-stu-id="d8f5d-p110">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240). See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>