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
description: Office 365 訂閱包含到 Azure AD 訂閱。 如果您想與您的內部部署環境的密碼同步處理或單一登入，Office 365 與 Azure AD 中整合。
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490139"
---
# <a name="azure-integration-with-office-365"></a>Azure 與 Office 365 的整合

Office 365 管理使用者身分識別，幕後使用 Azure Active Directory (Azure AD)。 Office 365 訂閱包含免費的 Azure AD 訂閱，因此如果您想要同步處理密碼，或設定單一登入與您的內部部署環境，您可以與 Azure AD 整合 Office 365。 您也可以購買進階的功能，可以更妥善地管理您的帳戶。
  
Azure 也提供其他功能，例如管理整合式應用程式，您可以用來擴充並自訂您的 Office 365 訂閱。
  
您可以使用 Azure AD 部署建議的引導式的安裝及設定經驗：
 - [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)
 - [AD FS 部署建議程式](https://aka.ms/adfsguidance)
 - [Azure RMS 部署精靈](https://aka.ms/azuremsguidance)
 - [Azure AD Premium 安裝指南](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD 版本和 Office 365 身分識別管理

如果您有 Office 365 的付費的訂閱，您也必須免費的 Azure AD 訂閱。 您可以使用 Azure AD 來建立及管理使用者和群組帳戶。 若要啟用此訂閱，您必須完成一次性的註冊。 之後，您可以從您的 Office 365 系統管理入口網站存取 Azure AD。 如需相關指示，請參閱[註冊您的免費 Azure AD 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=617127)。 
  
> [!TIP]
> Office 365 訂閱隨附的註冊免費的 Azure AD 訂閱，請遵循上述指示。 不要直接前往 azure.microsoft.com 登入，或您最後會有與您的 Office 365 的免費一台不同的 Microsoft Azure 試用版或付費訂閱。 
  
免費的訂閱，您可以與內部部署目錄同步處理，設定 [單一登入功能，與許多軟體與服務應用程式，例如 Salesforce、 投寄箱和其他更多選項進行同步處理。
  
如果您想增強的 AD DS 功能、 雙向同步，以及其他管理功能，您可以升級免費的訂閱付費進階版訂閱。 如需詳細資訊，請參閱[Azure Active Directory 的版本](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)。
  
如需有關 Office 365 和 Azure AD 的詳細資訊，請參閱[了解 Office 365 身分識別與 Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)。
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>擴充您的 Office 365 租用戶的功能

|**功能**|**描述**|
|:-----|:-----|
|整合式應用程式  <br/> |您可以個別應用程式存取授與您的 Office 365 資料，例如郵件、 行事曆、 連絡人、 使用者、 群組、 檔案及資料夾。 您也可以授權全域系統管理員層級這些應用程式，並讓他們可供整個公司使用 Azure AD 中登錄應用程式。 如需詳細資訊，請參閱[整合式應用程式和 Office 365 系統管理員的 Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。  <br/> 另請參閱[Azure AD 應用程式庫和單一登入](https://go.microsoft.com/fwlink/p/?LinkId=698604)。  <br/> |
|PowerApps  <br/> | 電源應用程式是可以連線至您現有的資料來源像 SharePoint 清單的行動裝置具有焦點的應用程式及其他資料應用程式。 如需詳細資訊，請參閱[建立 PowerApp SharePoint Online 中的清單](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps] 頁面](https://powerapps.microsoft.com/)。  <br/> |
   
有關 Microsoft Cloud 和 Office 365 的其他資源，請參閱下列資源：
  
- [Microsoft Cloud Identity for Enterprise Architects](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [在 Microsoft Azure 中部署 Office 365 目錄同步作業 (DirSync)](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

深入[整合式應用程式和 Office 365 系統管理員的 Azure AD](integrated-apps-and-azure-ads.md)和[Azure AD 應用程式庫和單一登入](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。

### <a name="power-apps"></a>電源應用程式
電源應用程式是可以連線至您現有的資料來源像 SharePoint 清單的行動裝置具有焦點的應用程式及其他資料應用程式。 如需詳細資訊，請參閱[建立 PowerApp SharePoint Online 中的清單](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps] 頁面](https://powerapps.microsoft.com/)。