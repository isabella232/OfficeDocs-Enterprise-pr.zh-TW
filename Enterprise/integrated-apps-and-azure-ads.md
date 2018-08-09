---
title: 整合式應用程式及 Office 365 系統管理員的 Azure AD
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: 了解如何 O365 整合應用程式已註冊和管理 Azure AD 的項目
ms.openlocfilehash: 666bfca5c2621d25f13dff7c5753c5ef47591b68
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "22213108"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>整合式應用程式及 Office 365 系統管理員的 Azure AD

有多個管理超過剛[開啟整合式應用程式開啟或關閉](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114)的整合式應用程式。與 Office 365 REST Api 推出，使用者可以授與應用程式存取其 Office 365 資料，例如郵件、 行事曆、 連絡人、 使用者、 群組、 檔案及資料夾。根據預設，使用者必須個別授與權限給每個應用程式，但這不會擴充以及如果您想要授權一次在全域管理員層級的應用程式與導透過 app 啟動器整個組織。為達成此目的，您必須在 Azure AD 中登錄應用程式。有一些所需您可以在 Azure AD 登錄應用程式和一些背景資訊時應該知道可幫助您管理 Office 365 組織中的應用程式之前可採取的步驟。本文指引您閱讀這些資源。
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Office 365 系統管理員的 azure AD 資源

您必須執行下列兩個程序之前您可以使用 Azure AD 管理您的 Office 365 應用程式。
  
|**必要條件**|**註解**|
|:-----|:-----|
|[註冊免費的 Azure Active Directory 訂閱](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |每個付費的訂閱至 Office 365 隨附 Azure Active directory 的免費訂閱。您可以使用 Azure AD 來管理您的應用程式也可以建立和管理使用者與群組帳戶。若要啟動此訂閱及存取 Azure 管理入口網站，您必須完成一次性註冊程序。之後，您可以從 Office 365 系統管理中心移至 Azure AD。  <br/> |
|[開啟或關閉忘記整合式應用程式](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |您必須針對您要允許存取其 Office 365 資訊的協力廠商應用程式的使用者與您在 Azure AD 中登錄應用程式開啟整合式應用程式。例如，當某人使用協力廠商應用程式，該應用程式可能會要求權限以存取其行事曆及編輯 OneDrive for Business 資料夾中的檔案。  <br/> |
   
管理 Office 365 應用程式需要您已在 Azure AD 的應用程式的知識。這些文章可協助提供您需要的背景。
  
|**背景文章**|**註解**|
|:-----|:-----|
|[符合 Office 365 應用程式啟動器](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |如果您是應用程式啟動器的新功能，您可能會想要知道功能以及如何使用它。應用程式啟動器專門設計來協助您從任何位置跳至您的應用程式在 Office 365 中。  <br/> |
|[新增、 更新及移除應用程式](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |本主題顯示如何新增、 更新或移除 Azure Active Directory 中的應用程式。您將了解可以整合搭配 Azure AD 的應用程式的不同類型，以及如何設定您的應用程式以存取其他例如網頁 api （英文），以及更多的資源。  <br/> |
|[有出現在 Office 365 應用程式啟動器您應用程式](https://go.microsoft.com/fwlink/?LinkId=617138)。  <br/> |應用程式中的啟動器便於尋找和存取其應用程式的使用者的 Office 365。本文說明您身為開發人員可以取得您的應用程式會出現在使用者的應用程式 launchers 並提供使用 Office 365 認證的單一登入 (SSO) 體驗的方式。  <br/> |
|[Office 365 Api 平台概觀 （英文)](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Office 365 api （英文） 可讓您提供存取您的客戶 Office 365 資料，包括最關心的事項 — 其郵件、 行事曆、 連絡人、 使用者及群組、 檔案及資料夾。本文說明 Office 365 應用程式] Azure AD 間的關聯中有一個很好的圖表和應用程式存取資料。  <br/> |
|[整合 Azure Active Directory 中的應用程式](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | 了解整合 Azure Active Directory，以及如何註冊您的應用程式、 了解概念的已登錄的應用程式，並了解如何將品牌的多個準則租用戶應用程式的應用程式。  <br/> |
|[Azure Active Directory 整合教學課程](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |這些教學課程的目標是以告訴您如何設定 Azure AD SSO 的協力廠商 saas 和應用程式。  <br/> |
|[Azure AD 驗證案例](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD 簡化適用於開發人員的驗證服務的身分識別提供支援 OAuth 2.0 和 OpenID 連線，等的業界標準通訊協定，以及開啟來源文件庫可協助您快速開始撰寫程式碼的不同平台。本文件協助您了解各種案例 Azure AD 支援，教您如何開始。  <br/> |
|[應用程式的存取](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure AD 讓許多今天的常用軟體做為服務 (SaaS) 應用程式 ； 的簡易整合它可提供身分識別與存取管理] 和它將傳遞的使用者存取面板其中他們可以探索有哪些應用程式存取和其中他們可以使用 SSO 來存取其應用程式。本文提供可讓您深入了解 Azure AD 的應用程式存取增強功能與它們拉長您可以如何相關資源的連結。  <br/> |
|[新增或移除在 Office 365 應用程式啟動器上的並排顯示](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |您可以取得快速存取每天使用新增或移除在 Office 365 應用程式啟動器應用程式的應用程式。  <br/> |
   

