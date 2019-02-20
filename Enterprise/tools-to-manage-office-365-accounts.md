---
title: 用來管理 Office 365 帳戶的工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '了解哪些工具，以用來管理 Office 365 使用者，及如何您可以使用取決於如何管理使用者身分識別。 '
ms.openlocfilehash: e13b6a998aa6de433d85ef3be60f08703eb914d4
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085382"
---
# <a name="tools-to-manage-office-365-accounts"></a>用來管理 Office 365 帳戶的工具

您可以根據您的設定數個不同的方式管理 Office 365 使用者。您可以管理 Azure Active Directory 系統入口網站或 Office 365 系統管理中心，Windows PowerShell 您的內部部署目錄中的使用者。 

一旦您購買 Office 365、 系統管理中心及 Windows PowerShell 可用來管理帳戶。管理雲端身分時您組織中的每個人的 Office 365 會有不同的使用者識別碼和密碼。如果您想要整合與您的內部部署基礎結構與使用者帳戶與 Office 365 同步處理，您可以使用 Azure 作用中的目錄連線至提供之身分識別的同步處理 （選擇性） 提供密碼同步處理或完整單一登入功能。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>何處及如何管理您的使用者帳戶的計劃

何處及如何可以管理您的使用者帳戶，取決於您想要用於您的 Office 365 的身分識別模型。兩個的整體模型是雲端驗證和同盟的驗證。
  
### <a name="cloud-authentication"></a>雲端驗證

- [Office 365 身分識別](about-office-365-identity.md)-建立及管理 Office 365 系統管理中心中的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory，來管理您的使用者。
- [密碼雜湊同步處理順暢單一登入搭配](about-office-365-identity.md)-啟用在 Azure AD 驗證內部部署目錄物件的最簡單方式。使用密碼雜湊同步處理 (PHS)，與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。 
- [順暢單一登入與通過驗證](about-office-365-identity.md)-提供的 Azure AD 驗證服務來驗證使用者直接與使用一或多個內部部署伺服器上執行的軟體代理程式簡單密碼驗證您內部部署 Active Directory。 
    
### <a name="federated-authentication"></a>同盟的驗證

- [Office 365 身分識別](about-office-365-identity.md)-主要針對具有較複雜的驗證需求的大型企業組織內部部署目錄物件與 Office 365 同步處理和使用者帳戶是受管理的內部。 
- [協力廠商驗證及身分識別提供者](about-office-365-identity.md)物件可能會同步至 Office 365 與雲端資源存取內部部署目錄是主要受管理的協力廠商身分識別提供者 (IdP)。 
    
## <a name="managing-accounts"></a>管理帳戶

當決定您的組織會建立和管理帳戶的方式，請考慮下列各項：
  
- 目錄同步處理軟體必須安裝在 Office 365 與您的內部部署目錄之間的身分識別連線在內部部署環境中的伺服器上。
- 任何目錄同步處理選項，包括 SSO 選項需要您內部部署目錄屬性符合標準。說明如何在您的目錄中使用哪些屬性和需要何種清理 （如果有的話） 所述[來佈建使用者透過目錄同步處理至 Office 365 的準備](prepare-for-directory-synchronization.md)。如需如何使用 IdFix 來自動化目錄清理指示，請參閱[安裝和執行 Office 365 IdFix 工具](install-and-run-idfix.md)。 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>規劃您要如何建立 Office 365 帳戶
下表列出不同的帳戶管理工具：
    
|**選項**|**附註**|
|:-----|:-----|
|**Office 365 admin center** | - [將使用者新增個別或大量至 Office 365-Admin 說明](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -提供新增及變更使用者帳戶的簡單 web 介面。 <br> -[無法用以啟用目錄同步作業時變更使用者 （可以設定位置和授權指派）。 <br> -[無法與 SSO 選項搭配使用。 <br> |
|**Windows PowerShell** | - [使用 Windows PowerShell 管理 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -可讓您將在大量使用者的使用者新增使用 Windows PowerShell 指令碼。 <br> -可用來將位置和授權指派給不論如何建立帳戶的帳戶。 <br> |
|**大量匯入** | - [將許多使用者同時新增至 Office 365-Admin 說明](add-several-users-at-the-same-time.md) <br> -可讓您匯入 CSV 檔案新增至 Office 365 的使用者群組。 <br> -[無法與 SSO 選項搭配使用。 <br> |
|**Azure Active Directory** | -您可以取得免費版本的 Azure Active Directory 與 Office 365 訂閱。-您可執行類似自助式密碼重設雲端使用者和自訂的登入及存取面板頁面所使用的是可用的版本的功能。<br> -若要取得增強的功能，您可以升級的基本的版本，或 premium edition。請參閱[Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)支援的功能的清單。<br> |
|**目錄同步處理** | - [整合內部身分識別與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -為目錄同步作業使用或不密碼同步處理，使用[Azure AD 連線明確的設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。  <br>  -針對多個樹系與 SSO 選項、 使用[自訂安裝的 Azure AD 連線](https://go.microsoft.com/fwlink/p/?LinkId=698430)。 <br> -提供不需要啟用 SSO 的基礎結構。 <br> -Required 許多混合式案例 （分段移轉，混合式 Exchange） <br> -同步處理安全性群組和擁有郵件功能的群組從您的內部部署目錄。 <br> |
   
不論如何您想要將使用者帳戶新增至 Office 365，您需要管理數個帳戶功能，例如指派授權，指定位置等等。這些功能可管理長期從 Office 365 系統管理中心或您也可以[使用 Office 365 PowerShell 建立使用者帳戶](https://go.microsoft.com/fwlink/p/?LinkId=717083)。
    
如果您選擇新增及管理您的所有使用者透過 Office 365 系統管理中心，您將指定的位置和指派授權，同時做為建立 Office 365 帳戶。因此，不太多規劃是必要的。
    
> [!IMPORTANT]
> 建立 Office 365 中的帳戶沒有將授權指派 (to SharePoint Online，例如) 表示帳戶擁有人可以檢視 Office 365 入口網站但無法存取任何內公司的訂閱服務。您指派位置和授權之後，帳戶會複寫到服務或您所指定的服務。使用者可以登入其帳戶並使用您指派給他們的服務。