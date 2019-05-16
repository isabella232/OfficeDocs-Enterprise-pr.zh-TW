---
title: Office 365 與內部部署環境整合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何將 Office 365 與您現有的目錄服務整合。
ms.openlocfilehash: 1fa044a0a9db0d8422239cf301fea21a2c3d47e9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069739"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Office 365 與內部部署環境整合

您可以將整合 Office 365 與您現有的目錄服務和內部部署安裝的 Exchange Server、 Skype Server 2015，或 SharePoint Server 2013。
  
 - 當您在整合與目錄服務時，您可以同步處理及管理使用者帳戶的兩個環境。 您也可以新增密碼雜湊同步處理或單一登入 (SSO)，使用者還是可以登入兩個環境使用其內部部署認證。
 - 當您在整合的內部部署伺服器產品時，您會建立混合式環境。 混合式環境可協助您將使用者或資訊移轉至 Office 365，或您可以繼續有一些使用者或某些資訊在內部和部分定域機組中。 如需有關混合式環境的詳細資訊，請參閱[Office 365 的混合式雲端解決方案概觀](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)。

您也可以使用 Azure AD 建議的自訂的設定指導方針：
- [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)
- [AD FS 部署建議程式](https://aka.ms/adfsguidance)
- [Azure RMS 部署精靈](https://aka.ms/azuremsguidance)
- [Azure AD Premium 安裝指引](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>開始之前
整合 Office 365 和內部部署環境之前，您也需要參加[網路規劃](network-planning-and-performance.md)和效能調整的 Office 365。 您也會想要了解 Office 365 中可用的[身分識別模型](about-office-365-identity.md)。 

請參閱[位置來管理 Office 365 使用者帳戶](manage-office-365-accounts.md)的工具來管理 Office 365 使用者帳戶，您可以使用的清單。 
  
## <a name="integrate-office-365-with-directory-services"></a>Office 365 與目錄服務整合
如果您有現有的使用者帳戶在內部部署目錄中，您不想重新建立所有 Office 365 和簡介差異或錯誤環境之間的風險中這些帳戶。 目錄同步處理可協助您鏡像這些帳戶之間線上和內部部署環境。 目錄同步處理，您的使用者不需要針對每個環境中，新的資訊，請記得，您不必建立或兩次更新帳戶。 您想要[準備您的內部部署目錄](prepare-for-directory-synchronization.md)進行目錄同步處理，您可以執行這項操作以手動方式或使用[IdFix 工具](install-and-run-idfix.md)（IdFix 工具只能與 Active Directory）。 
  
![若要保留在內部部署和線上的使用者帳戶資訊同步處理使用目錄同步處理](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
如果您希望使用者能夠使用其內部部署認證登入 Office 365，您也可以設定 SSO。 SSO，與 Office 365 設定為信任的使用者驗證的內部部署環境。
  
![搭配單一登入，相同的帳戶是可在內部部署與線上環境](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
不同的使用者帳戶管理技術為您的使用者，提供不同的體驗，如下表所示。
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**包含或不含密碼雜湊同步處理或通過驗證的目錄同步處理**
使用者登入他們的內部部署環境與其使用者帳戶 （網域 \ 使用者名稱）。 當他們移至 Office 365 時，他們必須登入一次使用其公司或學校帳戶 (user@domain.com)。 兩個環境中的相同使用者名稱。 當您新增密碼雜湊同步處理或通過驗證時，使用者有兩個環境中，相同的密碼，但會有提供這些認證，登入 Office 365 時。 目錄同步處理與密碼雜湊同步處理時最常使用的目錄同步處理案例。

若要設定目錄同步處理，使用 Azure Active Directory Connect。 如需相關指示，請閱讀[設定 Office 365 的目錄同步處理](set-up-directory-synchronization.md)，並[使用 Azure AD Connect 搭配快速設定](https://go.microsoft.com/fwlink/p/?LinkId=698537)。

深入了解[準備透過目錄同步處理至 Office 365 使用者佈建](prepare-for-directory-synchronization.md)並[整合您內部部署識別與 Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101)。

### <a name="directory-synchronization-with-sso"></a>**目錄同步處理與 SSO**
使用者登入他們的內部部署環境與其使用者帳戶。 當他們移至 Office 365 時，他們可以登入自動執行，或他們登入他們使用其內部部署環境 （網域 \ 使用者名稱） 的相同認證。

若要設定 SSO 您也會使用 Azure AD Connect。 如需相關指示，請閱讀[使用 Azure AD Connect 搭配自訂設定](https://go.microsoft.com/fwlink/p/?LinkID=698430)。

深入了解[應用程式的存取和單一登入與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604)。

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD Connect 會取代舊版的身分識別整合工具，例如 DirSync 和 Azure AD 同步處理。如需詳細資訊，請參閱[整合內部部署身分識別與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969)。 如果您想要從 Azure Active Directory 同步處理到 Azure AD Connect 更新，請參閱 <<c0>的升級指示。 請參閱針對[Office 365 目錄同步處理 (DirSync) 在 Microsoft Azure 中](https://go.microsoft.com/fwlink/?LinkId=517887)建置解決方案架構。