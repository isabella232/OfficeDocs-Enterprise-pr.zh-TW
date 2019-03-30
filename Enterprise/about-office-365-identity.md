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
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理使用者身分識別。
ms.openlocfilehash: c9dff7e17e4c0dcceb7cdeab86c1acdd40e01205
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001556"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>了解 Office 365 身分識別和 Azure Active Directory

Office 365 來管理使用者使用的雲端型使用者身分識別與驗證服務 Azure Active Directory (Azure AD)。 選擇身分識別管理已在內部部署組織與 Office 365 之間是下列其中一個雲端基礎結構的基礎早期決策。 因為變更此設定稍後可能很難，謹慎考慮至判斷什麼最適合組織的需求的選項。 您可以選擇設定及管理使用者帳戶; Office 365 中的兩個主要的驗證模型**雲端驗證**和**同盟的驗證**。
  
很重要請謹慎考慮何種用來取得這些驗證與身分識別模型和執行。 思考時間、 現有複雜度和成本實作和維護每個驗證與身分識別選項。 這些因素是不同的每個組織;您應先了解您要部署的重要概念的身分識別選項，可協助您選擇的驗證與身分識別模型。
  
## <a name="cloud-authentication"></a>雲端驗證

這取決於如果您有或沒有現有 Active Directory 環境上部署，您有數個選項可以管理的 Office 365 使用者的驗證與身分識別服務。
  
### <a name="cloud-only"></a>僅雲端

使用僅限雲端模型，您可以管理 Office 365 中的您使用者帳戶僅。 沒有內部部署伺服器是必要的資訊;它是所有處理定域機組中的 Azure AD。 您建立及管理[Microsoft 365 系統管理中心](https://admin.microsoft.com)中的使用者或使用 Windows PowerShell [PowerShell cmdlet](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)與身分識別，並驗證處理完全定域機組中的 Azure AD。 僅限雲端模型通常是很好的選擇如果： 
  
- 您有任何其他內部部署使用者目錄。
    
- 您有非常複雜的內部部署目錄，而且只想要避免與其整合的工作。
    
- 您有現有的內部部署目錄，但您想要執行的試用版或 Office 365 的試驗。 更新版本中，您可以符合內部部署使用者的雲端使用者，當您準備好要連線至您的內部部署目錄。
    
若要開始使用雲端身分識別，請參閱[設定商務用 Office 365](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>使用無縫單一登入的密碼雜湊同步處理

若要啟用內部部署目錄物件的 [驗證]，在 Azure AD 中最簡單的方式。 使用密碼雜湊同步處理 (PHS)，您可以與 Office 365 同步處理您的內部部署 Active Directory 使用者帳戶物件及管理您內部使用者。 使用者密碼雜湊同步處理從內部部署 Active Directory 至 Azure AD 如此，使用者擁有相同的密碼與內部及雲端中。 當密碼已變更，或重設為內部時，新的密碼雜湊同步處理到 Azure AD，讓您的使用者一定可以使用相同的密碼雲端資源和內部部署資源。 密碼永遠不會傳送到 Azure AD 或儲存在 Azure AD 以純文字。 Azure AD，例如 Identity Protection 的部分進階功能需要的 PHS 不論其選取驗證方法。 使用無縫單一登入，使用者會自動登入到當他們位於其公司規範的裝置，並連線至公司網路的 Azure AD。
  
深入了解[選擇密碼雜湊同步處理](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)並[無縫單一登入](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)。
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>使用無縫單一登入的傳遞驗證

提供使用一或多個內部部署伺服器上執行的軟體代理程式來驗證直接與您在內部部署 Active Directory 使用者的 Azure AD 驗證服務的簡單密碼驗證。 使用傳遞驗證 (PTA)，您可以與 Office 365 同步內部部署 Active Directory 使用者帳戶物件及管理您內部使用者。 可讓您的使用者登入內部部署和 Office 365 資源並使用其內部部署帳戶和密碼的應用程式。 此組態不會傳送到 Office 365 的密碼雜湊驗證直接針對您在內部部署 Active Directory 的使用者密碼。 若要立即強制執行內部部署使用者帳戶的安全性需求與公司狀態，密碼原則和登入時間會使用這種驗證方法。 使用無縫單一登入，使用者會自動登入到當他們位於其公司規範的裝置，並連線至公司網路的 Azure AD。
  
深入了解[選擇通過驗證](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)並[無縫單一登入](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)。
  
## <a name="federated-authentication-options"></a>同盟的驗證選項

如果您有現有 Active Directory 環境上部署，您可以將 Office 365 整合與您的目錄，藉由使用同盟的驗證，以管理 Office 365 中的使用者驗證與身分識別服務。
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>與 Active Directory Federation Services (AD FS) 的同盟身分識別

主要使用於大型企業組織中具有較複雜的驗證需求，在內部部署與 Office 365 同步處理目錄物件和使用者帳戶為受管理的內部部署。 搭配 AD FS，使用者有相同的密碼與內部及雲端中並不需要再次登入才能使用 Office 365。 此同盟的驗證模型可提供其他驗證需求，例如智慧卡型驗證或協力廠商的多重要素驗證和時，通常需要組織有驗證需求不原生支援 Azure AD。
  
深入了解[選擇與 AD FS 的同盟身分識別](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)。
  
### <a name="third-party-authentication-and-identity-providers"></a>協力廠商驗證與身分識別提供者

內部部署目錄物件可能會同步至 Office 365 和雲端資源存取主要是由協力廠商身分識別提供者 (Isp)。 如果您的組織使用同盟協力廠商解決方案，您可以設定登入與該解決方案搭配運作的 Office 365 提供協力廠商同盟解決方案會與 Azure AD 相容。
  
深入了解[Azure AD 同盟相容性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)。
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>使用 Office 365 設定身分識別與驗證

Office 365 與 Azure AD 整合您的內部部署目錄已經過簡化的[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。 Azure AD Connect 是最好的方法連線您的目錄，Microsoft 建議的組織同步處理至雲端使用者。
  
您也可以使用 Azure AD 建議： [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)、 [AD FS 部署建議程式](https://aka.ms/adfsguidance)中，與[Azure AD Premium 設定指南](https://aka.ms/aadpguidance)。
  
## <a name="video-training"></a>影片訓練課程

如需詳細資訊，請參閱影片課程[Office 365： 管理身分識別使用 Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)，由 LinkedIn Learning 帶您。
