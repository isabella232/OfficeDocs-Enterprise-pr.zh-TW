---
title: Azure 與 Microsoft 365 的整合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: 您的 Microsoft 365 訂閱包含 Azure AD 的訂閱。 如果您想要使用您的內部部署環境進行密碼同步處理或單一登入，請整合 Microsoft 365 與 Azure AD。
ms.openlocfilehash: d6ef9d05d66709d360c625fd3b47ad142bdde7a0
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842055"
---
# <a name="azure-integration-with-microsoft-365"></a><span data-ttu-id="16a01-104">Azure 與 Microsoft 365 的整合</span><span class="sxs-lookup"><span data-stu-id="16a01-104">Azure integration with Microsoft 365</span></span>

<span data-ttu-id="16a01-105">*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="16a01-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="16a01-106">Microsoft 365 使用 Azure Active Directory （Azure AD）來管理幕後的使用者身分識別。</span><span class="sxs-lookup"><span data-stu-id="16a01-106">Microsoft 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="16a01-107">您的 Microsoft 365 訂閱包含 Azure AD 的免費訂閱，如果您想要同步處理密碼或設定與您的內部部署環境的單一登入，則可以整合 Microsoft 365 與 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="16a01-107">Your Microsoft 365 subscription includes a free subscription to Azure AD so that you can integrate Microsoft 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="16a01-108">您也可以購買高級功能，以更好地管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="16a01-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="16a01-109">Azure 也提供其他功能（如管理整合型應用程式），您可以用來擴充和自訂您的 Microsoft 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="16a01-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Microsoft 365 subscriptions.</span></span>
  
<span data-ttu-id="16a01-110">您可以使用 Azure AD 部署顧問進行引導安裝和設定體驗（您必須登入 Microsoft 365）：</span><span class="sxs-lookup"><span data-stu-id="16a01-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Microsoft 365):</span></span>

 - [<span data-ttu-id="16a01-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="16a01-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="16a01-112">AD FS 部署顧問</span><span class="sxs-lookup"><span data-stu-id="16a01-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="16a01-113">Azure AD 安裝指南</span><span class="sxs-lookup"><span data-stu-id="16a01-113">Azure AD setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a><span data-ttu-id="16a01-114">Azure AD 版本和 Microsoft 365 身分識別管理</span><span class="sxs-lookup"><span data-stu-id="16a01-114">Azure AD editions and Microsoft 365 identity management</span></span>

<span data-ttu-id="16a01-115">如果您已付費訂閱 Microsoft 365，您也可以免費訂閱 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="16a01-115">If you have a paid subscription to Microsoft 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="16a01-116">您可以使用 Azure AD 建立及管理使用者和群群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="16a01-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="16a01-117">若要啟動此訂閱，您必須完成一次性註冊。</span><span class="sxs-lookup"><span data-stu-id="16a01-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="16a01-118">此後，您可以從您的 Microsoft 365 系統管理中心存取 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="16a01-118">Afterward, you can access Azure AD from your Microsoft 365 admin center.</span></span> 

<span data-ttu-id="16a01-119">如需相關指示，請參閱[使用免費 AZURE AD 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="16a01-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="16a01-120">依照指示，將您訂閱隨附的免費 Azure AD 訂閱註冊至 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="16a01-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Microsoft 365.</span></span> <span data-ttu-id="16a01-121">請勿直接前往 azure.microsoft.com 進行註冊，否則您將會使用 Microsoft Azure 的試用版或付費訂閱，以與 Microsoft 365 的免費訂閱分開。</span><span class="sxs-lookup"><span data-stu-id="16a01-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Microsoft 365.</span></span> 
  
<span data-ttu-id="16a01-122">使用免費訂閱，您可以同步處理內部部署目錄、設定單一登入，並與許多軟體（例如 Salesforce、DropBox 及其他許多軟體）同步處理。</span><span class="sxs-lookup"><span data-stu-id="16a01-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="16a01-123">如果您想要增強的 Active Directory 網域服務（AD DS）功能、雙向同步處理及其他管理功能，您可以將免費訂閱升級為付費的特優訂閱。</span><span class="sxs-lookup"><span data-stu-id="16a01-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="16a01-124">如需詳細資訊，請參閱[Azure Active Directory 版本](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="16a01-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="16a01-125">如需 Microsoft 365 和 Azure AD 的詳細資訊，請參閱[瞭解 microsoft 365 身分識別和 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="16a01-125">For more information about Microsoft 365 and Azure AD, see [Understanding Microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a><span data-ttu-id="16a01-126">擴充 Microsoft 365 租使用者的功能</span><span class="sxs-lookup"><span data-stu-id="16a01-126">Extend the capabilities of your Microsoft 365 tenant</span></span>

|<span data-ttu-id="16a01-127">**功能**</span><span class="sxs-lookup"><span data-stu-id="16a01-127">**Feature**</span></span>|<span data-ttu-id="16a01-128">**描述**</span><span class="sxs-lookup"><span data-stu-id="16a01-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="16a01-129">整合式應用程式</span><span class="sxs-lookup"><span data-stu-id="16a01-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="16a01-130">您可以將個別應用程式的存取權授與您的 Microsoft 365 資料，例如郵件、行事曆、連絡人、使用者、群組、檔案及資料夾。</span><span class="sxs-lookup"><span data-stu-id="16a01-130">You can grant individual apps access to your Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="16a01-131">您也可以在全域系統管理員層級授權這些應用程式，並在 Azure AD 中註冊應用程式，以將其提供給整個公司。</span><span class="sxs-lookup"><span data-stu-id="16a01-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="16a01-132">如需詳細資訊，請參閱[Microsoft 365 系統管理員的整合式應用程式和 AZURE AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。</span><span class="sxs-lookup"><span data-stu-id="16a01-132">For details see [Integrated Apps and Azure AD for Microsoft 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="16a01-133">另請參閱[單一登入至應用程式](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="16a01-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="16a01-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="16a01-134">PowerApps</span></span>  <br/> | <span data-ttu-id="16a01-135">Power app 是可連接到現有資料來源（如 SharePoint 清單）和其他資料應用程式的行動裝置應用程式。</span><span class="sxs-lookup"><span data-stu-id="16a01-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="16a01-136">如需詳細資訊，請參閱在 SharePoint Online 和[PowerApps 頁面](https://powerapps.microsoft.com/)[中建立清單的 PowerApp](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) 。</span><span class="sxs-lookup"><span data-stu-id="16a01-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="16a01-137">若要深入瞭解，請參閱 Microsoft 365 系統管理員和[AZURE ad 應用程式庫及單一登入](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[的整合式應用程式和 azure ad](integrated-apps-and-azure-ads.md) 。</span><span class="sxs-lookup"><span data-stu-id="16a01-137">Learn more at [Integrated Apps and Azure AD for Microsoft 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="16a01-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16a01-138">See also</span></span>

[<span data-ttu-id="16a01-139">Microsoft 365 企業版概觀</span><span class="sxs-lookup"><span data-stu-id="16a01-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
