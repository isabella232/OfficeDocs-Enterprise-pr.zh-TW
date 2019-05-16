---
title: 適用於 Office 365 系統管理員的整合式應用程式和 Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: 了解如何 O365 整合式應用程式註冊和 Azure AD 中管理
ms.openlocfilehash: 01bd932ed12e040a0e6dae517d7b4fd360b5da80
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067249"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>適用於 Office 365 系統管理員的整合式應用程式和 Azure AD

沒有更多] 以管理比剛[開啟整合式應用程式開啟或關閉](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)整合式應用程式。 Office 365 REST Api 推出，使用者可以授與應用程式存取其 Office 365 資料，例如郵件、 行事曆、 連絡人、 使用者、 群組、 檔案及資料夾。 根據預設，使用者需要個別授與每個應用程式的權限，但這不會調整以及如果您要授權的應用程式一次在全域系統管理員層級和推行至整個組織透過應用程式啟動器。 若要這麼做，您必須在 Azure AD 中註冊應用程式。 有一些步驟，您需要採取之前您可以在 Azure AD 中註冊的應用程式和一些背景資訊，您應該了解可協助您管理 Office 365 組織中的應用程式。 本文為您指向這些資源。
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Office 365 系統管理員適用的 azure AD 資源

您必須執行下列兩個程序，您可以在 Azure AD 中管理您的 Office 365 應用程式之前。
  
|**必要條件**|**Comments**|
|:-----|:-----|
|[註冊免費的 Azure Active Directory 訂閱](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |每個 Office 365 的付費的訂閱隨附 Azure Active directory 的免費的訂閱。 您可以使用 Azure AD 來管理您的應用程式，來建立及管理使用者和群組帳戶。 若要啟用此訂閱並存取 Azure 管理入口網站，您必須完成一次性的註冊程序。 之後，您可以從 Office 365 系統管理中心移到 Azure AD。  <br/> |
|[開啟或關閉整合式應用程式](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |為您的使用者，以允許協力廠商應用程式，來存取其 Office 365 的資訊，以及您在 Azure AD 中註冊應用程式，您必須先開啟整合式應用程式。 例如，當有人使用協力廠商應用程式時，該應用程式可能會要求權限來存取其行事曆，以及編輯商務用 OneDrive 資料夾中的檔案。  <br/> |
   
管理 Office 365 應用程式需要您在 Azure AD 中的應用程式的知識。 這些文章可協助提供您需要的背景。
  
|**背景文章**|**Comments**|
|:-----|:-----|
|[符合 Office 365 app 啟動器](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |如果您是初次使用應用程式啟動器，您可能會想要知道它是什麼以及如何使用它。 應用程式啟動器設計來協助您從任何地方存取您的應用程式在 Office 365 中。  <br/> |
|[新增、 更新及移除應用程式](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |本主題會示範如何新增、 更新或移除 [Azure Active Directory 中的 [應用程式。 您將了解不同類型的應用程式，可以與 Azure AD 整合，以及如何設定您的應用程式，來存取其他資源，例如 web Api，等等。  <br/> |
|[有出現在 Office 365 app 啟動器應用程式](https://go.microsoft.com/fwlink/?LinkId=617138)。  <br/> |應用程式啟動器有助於使用者尋找和存取他們的應用程式的 Office 365 中。 本文將告訴您身為開發人員可以取得您的應用程式出現在一個使用者的應用程式啟動器，並提供使用 Office 365 認證的單一登入 (SSO) 體驗的方式。  <br/> |
|[Office 365 API 平台概觀](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Office 365 Api 可讓您提供存取客戶的 Office 365 資料，包括最關心的事項 — 其郵件、 行事曆、 連絡人、 使用者和群組、 檔案及資料夾。 本文說明在 Office 365 應用程式，Azure AD 之間的關聯性沒有良好的圖表和應用程式存取資料。  <br/> |
|[整合 Azure Active Directory 中的應用程式](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | 了解整合與 Azure Active Directory，以及如何註冊您的應用程式、 了解概念註冊的應用程式，取得並了解品牌的指導方針多租用戶的應用程式的應用程式。  <br/> |
|[Azure Active Directory 整合教學課程](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |這些教學課程的目標是要告訴您如何設定 Azure AD SSO 的協力廠商的 SaaS 應用程式。  <br/> |
|[Azure AD 的驗證案例](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD 做為服務，提供身分識別與支援的業界標準通訊協定，例如 OAuth 2.0 和 OpenID Connect，簡化適用於開發人員的驗證，以及開啟來源文件庫，可協助您迅速開始撰寫程式碼的不同平台。 本文件可協助您了解 Azure AD 支援並為您示範如何開始在各種案例。  <br/> |
|[應用程式的存取](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD 會啟用對多今天的常用軟體做為服務 (SaaS) 應用程式中; 的簡易整合它提供身分識別與存取管理]，它會傳遞使用者存取面板，他們可以探索他們有哪些應用程式的存取，而且他們可以使用 SSO 來存取他們的應用程式。 本文提供可讓您深入了解 Azure AD 的應用程式存取增強功能與如何可以參與給他們的相關資源的連結。  <br/> |
|[個人化您的 Office 365 經驗](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |您可以取得快速存取您每天使用藉由新增或移除 Office 365 app 啟動器中的應用程式的應用程式。  <br/> |
   

