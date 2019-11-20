---
title: Azure 與 Office 365 的整合
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
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 訂閱包含到 Azure AD 訂閱。 如果您想與您的內部部署環境的密碼同步處理或單一登入，Office 365 與 Azure AD 中整合。
ms.openlocfilehash: 44231420ee92c37f14874d6fb0f9e926d8d4369d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745786"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="eaac9-104">Azure 與 Office 365 的整合</span><span class="sxs-lookup"><span data-stu-id="eaac9-104">Azure integration with Office 365</span></span>

<span data-ttu-id="eaac9-105">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="eaac9-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="eaac9-106">Office 365 管理使用者身分識別，幕後使用 Azure Active Directory (Azure AD)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-106">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="eaac9-107">Office 365 訂閱包含免費的 Azure AD 訂閱，因此如果您想要同步處理密碼，或設定單一登入與您的內部部署環境，您可以與 Azure AD 整合 Office 365。</span><span class="sxs-lookup"><span data-stu-id="eaac9-107">Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="eaac9-108">您也可以購買進階的功能，可以更妥善地管理您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="eaac9-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="eaac9-109">Azure 也提供其他功能，例如管理整合式應用程式，您可以用來擴充並自訂您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="eaac9-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="eaac9-110">您可以使用 （您必須登入到 Office 365） 的引導式安裝與設定體驗的 Azure AD 部署建議：</span><span class="sxs-lookup"><span data-stu-id="eaac9-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Office 365):</span></span>

 - [<span data-ttu-id="eaac9-111">Azure AD Connect 顧問</span><span class="sxs-lookup"><span data-stu-id="eaac9-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="eaac9-112">AD FS 部署建議程式</span><span class="sxs-lookup"><span data-stu-id="eaac9-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="eaac9-113">Azure AD Premium 安裝指南</span><span class="sxs-lookup"><span data-stu-id="eaac9-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="eaac9-114">Azure AD 版本和 Office 365 身分識別管理</span><span class="sxs-lookup"><span data-stu-id="eaac9-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="eaac9-115">如果您有 Office 365 的付費的訂閱，您也必須免費的 Azure AD 訂閱。</span><span class="sxs-lookup"><span data-stu-id="eaac9-115">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="eaac9-116">您可以使用 Azure AD 來建立及管理使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="eaac9-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="eaac9-117">若要啟用此訂閱，您必須完成一次性的註冊。</span><span class="sxs-lookup"><span data-stu-id="eaac9-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="eaac9-118">之後，您可以從您的 Office 365 系統管理入口網站存取 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="eaac9-118">Afterward, you can access Azure AD from your Office 365 admin portal.</span></span> 

<span data-ttu-id="eaac9-119">如需相關指示，請參閱[使用您免費 Azure AD 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="eaac9-120">Office 365 訂閱隨附的註冊免費的 Azure AD 訂閱，請遵循指示。</span><span class="sxs-lookup"><span data-stu-id="eaac9-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Office 365.</span></span> <span data-ttu-id="eaac9-121">不要直接前往 azure.microsoft.com 登入，或您最後會有與您的 Office 365 的免費一台不同的 Microsoft Azure 試用版或付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="eaac9-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="eaac9-122">免費的訂閱，您可以與內部部署目錄同步處理，設定 [單一登入功能，與許多軟體與服務應用程式，例如 Salesforce、 投寄箱和其他更多選項進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="eaac9-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="eaac9-123">如果您想增強的 Active Directory 網域服務 (AD DS) 功能、 雙向同步，以及其他管理功能，您可以升級免費的訂閱付費進階版訂閱。</span><span class="sxs-lookup"><span data-stu-id="eaac9-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="eaac9-124">如需詳細資訊，請參閱[Azure Active Directory 的版本](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="eaac9-125">如需有關 Office 365 和 Azure AD 的詳細資訊，請參閱[了解 Office 365 身分識別與 Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="eaac9-126">擴充您的 Office 365 租用戶的功能</span><span class="sxs-lookup"><span data-stu-id="eaac9-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="eaac9-127">**功能**</span><span class="sxs-lookup"><span data-stu-id="eaac9-127">**Feature**</span></span>|<span data-ttu-id="eaac9-128">**描述**</span><span class="sxs-lookup"><span data-stu-id="eaac9-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="eaac9-129">整合式應用程式</span><span class="sxs-lookup"><span data-stu-id="eaac9-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="eaac9-130">您可以個別應用程式存取授與您的 Office 365 資料，例如郵件、 行事曆、 連絡人、 使用者、 群組、 檔案及資料夾。</span><span class="sxs-lookup"><span data-stu-id="eaac9-130">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="eaac9-131">您也可以授權全域系統管理員層級這些應用程式，並讓他們可供整個公司使用 Azure AD 中登錄應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaac9-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="eaac9-132">如需詳細資訊，請參閱[整合式應用程式和 Office 365 系統管理員的 Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-132">For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="eaac9-133">也請參閱[單一登入應用程式](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="eaac9-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="eaac9-134">PowerApps</span></span>  <br/> | <span data-ttu-id="eaac9-135">電源應用程式是可以連線至您現有的資料來源像 SharePoint 清單的行動裝置具有焦點的應用程式及其他資料應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaac9-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="eaac9-136">如需詳細資訊，請參閱[建立 PowerApp SharePoint Online 中的清單](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps] 頁面](https://powerapps.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="eaac9-137">深入[整合式應用程式和 Office 365 系統管理員的 Azure AD](integrated-apps-and-azure-ads.md)和[Azure AD 應用程式庫和單一登入](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="eaac9-137">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="eaac9-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaac9-138">See also</span></span>

[<span data-ttu-id="eaac9-139">Microsoft 365 企業版概觀</span><span class="sxs-lookup"><span data-stu-id="eaac9-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
