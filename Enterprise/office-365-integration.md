---
title: 與內部部署環境的 office 365 整合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: 了解如何將與您現有的目錄服務整合 Office 365。
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540090"
---
# <a name="office-365-integration-with-on-premises-environments"></a>與內部部署環境的 office 365 整合

您可以針對 Business Server 2015、 或 SharePoint Server 2013 使用您現有的目錄服務與內部部署安裝的 Exchange Server、 Skype 整合 Office 365。
  
 - 當您與目錄服務整合時，您可以同步處理及管理這兩個環境的使用者帳戶。您也可以新增密碼雜湊同步處理或單一登入 (SSO) 讓使用者可以登入內部部署認證與這兩個環境。
 - 當您與內部部署伺服器產品整合時，您會建立在混合式環境。混合式環境可以協助使用者或資訊移轉至 Office 365 或您可以繼續有一些使用者或某些資訊在內部以及部分雲端中。如需混合式環境的詳細資訊，請參閱[Office 365 的混合式雲端解決方案概觀](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)。

您也可以使用 Azure AD 顧問的自訂的安裝指引：
- [Azure AD Connect 顧問](https://aka.ms/aadconnectpwsync)
- [AD FS 部署顧問](https://aka.ms/adfsguidance)
- [Azure RMS 部署精靈](https://aka.ms/azuremsguidance)
- [Azure AD Premium 安裝指引](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>開始之前
您整合 Office 365 與內部部署環境之前，您也需要參加與[網路規劃和 Office 365 的效能調整](network-planning-and-performance.md)。您也會想要了解 Office 365 中可用的[身分識別模型](about-office-365-identity.md)。 

請參閱[位置來管理 Office 365 使用者帳戶](manage-office-365-accounts.md)的工具可用來管理 Office 365 使用者帳戶的清單。 
  
## <a name="integrate-office-365-with-directory-services"></a>與目錄服務整合 Office 365
如果您有現有的使用者帳戶的內部部署目錄中，您不想重新建立所有這些帳戶在 Office 365 和簡介 （英文） 複寫差異處或錯誤環境之間的風險。目錄同步處理可協助您鏡像那些帳戶之間在線上和內部部署環境。使用目錄同步處理您的使用者不需要為每個環境、 新的資訊，請記得與您不需要建立或更新帳戶兩次。您將需要目錄同步作業[準備您的內部部署目錄](prepare-for-directory-synchronization.md)，您可以執行這項作業以手動方式或使用[IdFix 工具](install-and-run-idfix.md)（IdFix 工具僅可透過 Active Directory）。 
  
![使用目錄同步處理可保留在內部部署和線上的使用者帳戶資訊進行同步處理](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
如果您想要能夠使用其內部部署認證登入 Office 365 的使用者，您也可以設定 SSO。使用 SSO，Office 365 已設定為信任的使用者驗證的內部部署環境。
  
![搭配單一登入，相同的帳戶是可在內部部署與線上環境](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
不同的使用者帳戶管理技巧 （英文） 提供的不同經驗供使用者，使用下表所示。
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**使用或不密碼雜湊同步處理或通過驗證目錄同步處理**
使用者登入其內部部署環境中使用其使用者帳戶 (domain\username)。當他們移至 Office 365 時，他們必須再次登入其工作或學校的帳戶 (user@domain.com)。這兩個環境中的相同使用者名稱。新增密碼雜湊同步處理] 或 [通過驗證之後，使用者有相同的密碼這兩個環境中，但必須登入 Office 365 時一次提供所需的認證。使用密碼雜湊同步處理的目錄同步作業是最常用的目錄同步處理案例。

若要設定目錄同步作業，使用 Azure Active Directory 連線。指示，請閱讀[Office 365 的目錄同步作業設定](set-up-directory-synchronization.md)及[使用 Azure AD Connect 明確設定](https://go.microsoft.com/fwlink/p/?LinkId=698537)。

深入了解[準備透過目錄同步處理至 Office 365 的使用者佈建](prepare-for-directory-synchronization.md)和[整合內部會識別與 Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101)。

### <a name="directory-synchronization-with-sso"></a>**與 SSO 的目錄同步處理**
使用者登入其內部部署環境中使用其使用者帳戶。當他們移至 Office 365 時，他們也登入自動，或登入他們使用其內部部署環境 (domain\username) 的相同認證。

若要設定 SSO 也使用 Azure AD 連線。指示，請閱讀[使用自訂設定使用 Azure AD 連線]](https://go.microsoft.com/fwlink/p/?LinkID=698430)。

深入了解[應用程式存取與單一登入與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604)。

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD 連線會取代為舊版的身分識別的整合工具，例如 DirSync 以及 Azure AD 同步處理。如需詳細資訊，請參閱[您的內部部署身分識別與 Azure Active Directory 的整合](https://go.microsoft.com/fwlink/p/?LinkId=527969)。如果您想要更新的 Azure Active Directory 同步處理 Azure AD 連線，請參閱[的升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。請參閱[Office 365 目錄同步處理 (DirSync) Microsoft Azure 中](https://go.microsoft.com/fwlink/?LinkId=517887)的內建的解決方案架構。