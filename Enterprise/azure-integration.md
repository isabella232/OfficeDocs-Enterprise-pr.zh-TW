---
title: Azure 與 Office 365 的整合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
description: 您的 Office 365 訂閱包括 Azure AD 訂閱。如果您想密碼同步或單一登入搭配內部部署環境，整合 Office 365 Azure AD。
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085472"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="ed037-104">Azure 與 Office 365 的整合</span><span class="sxs-lookup"><span data-stu-id="ed037-104">Azure integration with Office 365</span></span>

<span data-ttu-id="ed037-p102">Office 365 使用 Azure Active Directory (Azure AD) 來管理在幕後的使用者身分識別。您的 Office 365 訂閱包括 Azure AD 免費訂閱，讓您可以整合 Office 365 搭配 Azure AD，如果您想要同步處理密碼或設定單一登入搭配內部部署環境。您也可以購買更妥善地管理您的帳戶的進階的功能。</span><span class="sxs-lookup"><span data-stu-id="ed037-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="ed037-108">Azure 也提供其他功能，例如管理整合式應用程式，可用來擴充和自訂 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="ed037-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="ed037-109">您可以使用 Azure AD 部署顧問引導的安裝與設定體驗：</span><span class="sxs-lookup"><span data-stu-id="ed037-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="ed037-110">Azure AD Connect 顧問</span><span class="sxs-lookup"><span data-stu-id="ed037-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="ed037-111">AD FS 部署顧問</span><span class="sxs-lookup"><span data-stu-id="ed037-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="ed037-112">Azure RMS 部署精靈</span><span class="sxs-lookup"><span data-stu-id="ed037-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="ed037-113">Azure AD Premium 安裝指南</span><span class="sxs-lookup"><span data-stu-id="ed037-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="ed037-114">Azure AD 版本及 Office 365 身分識別管理</span><span class="sxs-lookup"><span data-stu-id="ed037-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="ed037-p103">如果您有付費的訂閱以 Office 365，您也可以免費訂閱 Azure AD。您可以使用 Azure AD 來建立及管理使用者與群組帳戶。若要啟動此訂閱您必須完成單次註冊。認知，您可以從 Office 365 系統管理入口網站存取 Azure AD。指示，請參閱[註冊您免費 Azure AD 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="ed037-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="ed037-p104">註冊免費的 Azure AD 訂閱至 Office 365 隨附您的訂閱所遵循上述的指示。沒有直接移至註冊的 azure.microsoft.com 或您將會結束與 Office 365 您免費一種不同的 Microsoft Azure 試用版或付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="ed037-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="ed037-122">您可以與內部部署目錄同步處理的免費訂閱，以設定單一登入，並同步處理具有許多軟體做為服務應用程式，例如 Salesforce、 投寄箱以及其他更多選項。</span><span class="sxs-lookup"><span data-stu-id="ed037-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="ed037-p105">如果您想增強的 AD DS 功能、 雙向同步處理及其他管理功能，您可以升級您免費的訂閱付費進階版訂閱。如需詳細資訊請參閱[Azure Active Directory 版本](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)。</span><span class="sxs-lookup"><span data-stu-id="ed037-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="ed037-125">如需 Office 365 和 Azure AD 的詳細資訊，請參閱[了解 Office 365 身分識別和 Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)。</span><span class="sxs-lookup"><span data-stu-id="ed037-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="ed037-126">擴充 Office 365 租用戶的功能</span><span class="sxs-lookup"><span data-stu-id="ed037-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="ed037-127">**功能**</span><span class="sxs-lookup"><span data-stu-id="ed037-127">**Feature**</span></span>|<span data-ttu-id="ed037-128">**描述**</span><span class="sxs-lookup"><span data-stu-id="ed037-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ed037-129">整合式應用程式</span><span class="sxs-lookup"><span data-stu-id="ed037-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="ed037-p106">您可以將個別的應用程式存取授與 Office 365 資料，例如郵件、 行事曆、 連絡人、 使用者、 群組、 檔案及資料夾。您也可以授權全域管理員層級這些應用程式並讓其可供整個公司使用在 Azure AD 中登錄應用程式。如需詳細資訊請參閱[整合式應用程式和 Office 365 系統管理員的 Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。</span><span class="sxs-lookup"><span data-stu-id="ed037-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="ed037-133">另請參閱[Azure AD 應用程式庫 （英文) 及單一登入](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="ed037-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="ed037-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="ed037-134">PowerApps</span></span>  <br/> | <span data-ttu-id="ed037-p107">電源應用程式是著重可以連線至現有的資料來源如 SharePoint 清單的行動裝置應用程式及其他資料應用程式。如需詳細資訊，請參閱[Create a PowerApp SharePoint Online 中的清單](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)及[PowerApps] 頁面](https://powerapps.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="ed037-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="ed037-137">如需 Microsoft Cloud 和 Office 365 其他資源，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="ed037-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="ed037-138">Microsoft Cloud Identity for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="ed037-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="ed037-139">在 Microsoft Azure 中部署 Office 365 目錄同步作業 (DirSync)</span><span class="sxs-lookup"><span data-stu-id="ed037-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="ed037-140">深入了解，[整合式應用程式及 Office 365 系統管理員的 Azure AD](integrated-apps-and-azure-ads.md)和[Azure AD 應用程式庫 （英文) 及單一登入](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="ed037-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="ed037-141">電源應用程式</span><span class="sxs-lookup"><span data-stu-id="ed037-141">Power Apps</span></span>
<span data-ttu-id="ed037-p108">電源應用程式是著重可以連線至現有的資料來源如 SharePoint 清單的行動裝置應用程式及其他資料應用程式。如需詳細資訊，請參閱[Create a PowerApp SharePoint Online 中的清單](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)及[PowerApps] 頁面](https://powerapps.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="ed037-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>