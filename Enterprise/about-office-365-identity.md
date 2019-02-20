---
title: 了解 Office 365 身分識別和 Azure Active Directory
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
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理使用者身分識別。
ms.openlocfilehash: 0b0dd133979a5f94f7f8322c532c61fd24719359
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085422"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>了解 Office 365 身分識別和 Azure Active Directory

Office 365 管理使用者使用的雲端使用者身分識別與驗證服務 Azure Active Directory (Azure AD)。選擇的身分識別管理設定內部部署組織與 Office 365 之間是其中一個雲端基礎結構的基礎早期決策。因為變更此設定稍後可能很難，所以請謹慎考慮選項以判斷什麼最適用於您組織的需求。您可以選擇設定及管理使用者帳戶 ； 在 Office 365 中的兩個主要的驗證模型**雲端驗證**和**同盟的驗證**。
  
很重要謹慎考慮其中一種驗證及身分識別的模型以用來取得及執行。思考時間、 現有複雜度和成本實作及維護每個驗證及身分識別選項。這些因素之差異的每一個組織;與您應了解您想要使用您的部署的重要概念的身分識別選項可協助您選擇的驗證及身分識別模型。
  
## <a name="cloud-authentication"></a>雲端驗證

這取決於如果您有或沒有現有 Active Directory 環境內部部署，您有數個選項來管理 Office 365 使用者的驗證及身分識別服務。
  
### <a name="cloud-only"></a>僅雲端

僅限雲端模型，管理 [Office 365 中的您使用者帳戶僅]。無內部伺服器所需;它是所有在雲端中由處理 Azure AD。建立及管理 Office 365 系統管理中心中的使用者或使用 Windows PowerShell [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)和身分識別與驗證處理完全在雲端中的 Azure AD。僅限雲端模型通常是不錯的選擇是否： 
  
- 您有任何其他內部部署使用者目錄。
    
- 您有非常複雜內部部署目錄並只想要避免整合其工作。
    
- 您已在現有的內部部署目錄，但您想要執行的試用版或 Office 365 試驗。稍後，您可以比對內部使用者的雲端使用者當您準備好連線到您的內部部署目錄。
    
若要開始使用雲端身分識別，請參閱 ＜[設定 Office 365 企業版](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>使用順暢單一登入的密碼雜湊同步處理

若要啟用內部部署目錄物件在 Azure AD 驗證最簡單的方法。使用密碼雜湊同步處理 (PHS)，與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。使用者密碼雜湊已同步處理從內部部署 Active Directory 至 Azure AD，讓使用者有相同的密碼內部部署與雲端中。密碼已變更或重設為內部，新的密碼雜湊就進行同步處理至 Azure AD 使您的使用者可以雲端資源和內部部署資源一律使用相同的密碼。密碼永遠不會傳送到 Azure AD 或儲存在 Azure AD 以純文字。Azure AD，例如身分識別保護部分 premium 功能需要的 PHS 不論其選取驗證方法。以順暢單一登入，使用者會自動登入時位於其公司裝置並連線至公司網路的 Azure AD。
  
深入了解[選擇密碼雜湊同步處理](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)及[順暢單一登入](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)。
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>通過驗證與順暢單一登入

提供使用一或多個內部部署伺服器上執行的軟體代理程式驗證的使用者直接與您在內部部署 Active Directory 的 Azure AD 驗證服務的簡單密碼驗證。與通過驗證 (PTA) 與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。可讓使用者登入內部部署和 Office 365 資源和使用其內部部署帳戶及密碼的應用程式。此設定會對您的內部部署 Active Directory 直接使用者密碼驗證而不傳送給 Office 365 的密碼雜湊。會指出與安全性需求來立即強制執行內部部署使用者帳戶的公司、 密碼原則和登入時間可使用此驗證方法。以順暢單一登入，使用者會自動登入時位於其公司裝置並連線至公司網路的 Azure AD。
  
深入了解[選擇通過驗證](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)和[順暢單一登入](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)。
  
## <a name="federated-authentication-options"></a>同盟的驗證選項

如果您有現有 Active Directory 環境內部部署，您可以透過使用同盟的驗證來管理 Office 365 中使用者的驗證及身分識別服務與您的目錄整合 Office 365。
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>同盟身分識別與 Active Directory Federation Services (AD FS)

主要針對具有較複雜的驗證需求的大型企業組織、 內部部署與 Office 365 同步處理目錄物件和使用者帳戶是受管理的內部。使用 AD FS 使用者有相同的密碼內部部署與雲端中並不需要登入一次使用 Office 365。此同盟的驗證模型可提供額外的驗證需求，例如智慧卡型驗證或協力廠商多重要素驗證時，為通常是必要的組織已驗證需求。原本就不支援 Azure AD。
  
深入了解[選擇 with AD FS 同盟身分識別](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。
  
### <a name="third-party-authentication-and-identity-providers"></a>協力廠商驗證及身分識別提供者

在內部部署目錄物件可能會同步至 Office 365 與雲端資源存取主要受管理的協力廠商身分識別提供者 (IdP)。如果貴組織使用的同盟協力廠商解決方案，您可以設定登入該解決方案的 Office 365 同盟協力廠商解決方案是相容於 Azure AD。
  
深入了解[Azure AD 同盟相容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)。
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>使用 Office 365 設定身分識別與驗證

將您的內部部署目錄整合與 Office 365 和 Azure AD 簡化了[Azure AD 連線](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。Azure AD 連線是最適合您的目錄連線] 及 [是 Microsoft 的組織中的建議來同步處理至雲端使用者。
  
您也可以使用 Azure AD 顧問： [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)、 [AD FS 部署顧問](https://aka.ms/adfsguidance)，以及[Azure AD Premium 安裝指南](https://aka.ms/aadpguidance)。
  
## <a name="video-training"></a>影片訓練課程

如需詳細資訊，請參閱視訊課程[Office 365： 管理身分識別使用 Azure AD 連接](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)、 LinkedIn 學習由致力提供給您。
