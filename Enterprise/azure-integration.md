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
# <a name="azure-integration-with-office-365"></a>Azure 與 Office 365 的整合

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

Office 365 管理使用者身分識別，幕後使用 Azure Active Directory (Azure AD)。 Office 365 訂閱包含免費的 Azure AD 訂閱，因此如果您想要同步處理密碼，或設定單一登入與您的內部部署環境，您可以與 Azure AD 整合 Office 365。 您也可以購買進階的功能，可以更妥善地管理您的帳戶。
  
Azure 也提供其他功能，例如管理整合式應用程式，您可以用來擴充並自訂您的 Office 365 訂閱。
  
您可以使用 （您必須登入到 Office 365） 的引導式安裝與設定體驗的 Azure AD 部署建議：

 - [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)
 - [AD FS 部署建議程式](https://aka.ms/adfsguidance)
 - [Azure AD Premium 安裝指南](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD 版本和 Office 365 身分識別管理

如果您有 Office 365 的付費的訂閱，您也必須免費的 Azure AD 訂閱。 您可以使用 Azure AD 來建立及管理使用者和群組帳戶。 若要啟用此訂閱，您必須完成一次性的註冊。 之後，您可以從您的 Office 365 系統管理入口網站存取 Azure AD。 

如需相關指示，請參閱[使用您免費 Azure AD 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=617127)。 Office 365 訂閱隨附的註冊免費的 Azure AD 訂閱，請遵循指示。 不要直接前往 azure.microsoft.com 登入，或您最後會有與您的 Office 365 的免費一台不同的 Microsoft Azure 試用版或付費訂閱。 
  
免費的訂閱，您可以與內部部署目錄同步處理，設定 [單一登入功能，與許多軟體與服務應用程式，例如 Salesforce、 投寄箱和其他更多選項進行同步處理。
  
如果您想增強的 Active Directory 網域服務 (AD DS) 功能、 雙向同步，以及其他管理功能，您可以升級免費的訂閱付費進階版訂閱。 如需詳細資訊，請參閱[Azure Active Directory 的版本](https://azure.microsoft.com/pricing/details/active-directory/)。
  
如需有關 Office 365 和 Azure AD 的詳細資訊，請參閱[了解 Office 365 身分識別與 Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity)。
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>擴充您的 Office 365 租用戶的功能

|**功能**|**描述**|
|:-----|:-----|
|整合式應用程式  <br/> |您可以個別應用程式存取授與您的 Office 365 資料，例如郵件、 行事曆、 連絡人、 使用者、 群組、 檔案及資料夾。 您也可以授權全域系統管理員層級這些應用程式，並讓他們可供整個公司使用 Azure AD 中登錄應用程式。 如需詳細資訊，請參閱[整合式應用程式和 Office 365 系統管理員的 Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。  <br/> 也請參閱[單一登入應用程式](https://go.microsoft.com/fwlink/p/?LinkId=698604)。  <br/> |
|PowerApps  <br/> | 電源應用程式是可以連線至您現有的資料來源像 SharePoint 清單的行動裝置具有焦點的應用程式及其他資料應用程式。 如需詳細資訊，請參閱[建立 PowerApp SharePoint Online 中的清單](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps] 頁面](https://powerapps.microsoft.com/)。  <br/> |
   
深入[整合式應用程式和 Office 365 系統管理員的 Azure AD](integrated-apps-and-azure-ads.md)和[Azure AD 應用程式庫和單一登入](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。

## <a name="see-also"></a>另請參閱

[Microsoft 365 企業版概觀](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
