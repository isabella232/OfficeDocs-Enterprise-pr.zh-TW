---
title: 管理 Office 365 帳戶的工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
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
description: '了解哪些工具用來管理您的 Office 365 使用者，以及如何您可以使用取決於您要如何管理使用者身分識別。 '
ms.openlocfilehash: a9bd7cd75902d2b3b3ff17572849fb1a46053eb5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067189"
---
# <a name="tools-to-manage-office-365-accounts"></a>管理 Office 365 帳戶的工具

您可以根據您的設定，以數種不同的方式，管理 Office 365 使用者。 您可以管理[Microsoft 365 系統管理中心](https://admin.microsoft.com)，Windows PowerShell，您的內部部署目錄，或 Azure Active Directory 系統管理入口網站中的使用者。 只要您購買 Office 365 系統管理中心和 Windows PowerShell 可以用來管理帳戶。 當管理雲端身分識別組織中的每個人的 Office 365 會有個別的使用者識別碼和密碼。 如果您想要整合您的內部部署基礎結構，並具有使用者帳戶與 Office 365 同步處理，您可以使用 Azure Active Directory Connect 提供的身分識別同步處理及選擇性地提供密碼同步處理，或完整單一登入功能。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>位置及方式將管理您的使用者帳戶的計劃

位置及方式，您就可以管理您的使用者帳戶，取決於您想要用於您的 Office 365 的身分識別模型。 兩個的整體模型是雲端驗證和同盟的驗證。
  
### <a name="cloud-authentication"></a>雲端驗證

- [雲端驗證](about-office-365-identity.md#cloud-authentication)-建立及管理使用者在系統管理中心中，您也可以使用 Windows PowerShell 或 Azure Active Directory，來管理您的使用者。 
    
- [密碼雜湊同步處理與無縫單一登入](about-office-365-identity.md)-啟用內部部署目錄物件的 [驗證]，在 Azure AD 中的最簡單方式。 使用密碼雜湊同步處理 (PHS)，您可以與 Office 365 同步處理您的內部部署 Active Directory 使用者帳戶物件及管理您內部使用者。 
    
- [無縫單一登入與通過驗證](about-office-365-identity.md)-提供使用一或多個內部部署伺服器上執行的軟體代理程式來驗證直接與使用者的 Azure AD 驗證服務的簡單密碼驗證您內部部署 Active Directory。 
    
### <a name="federated-authentication"></a>同盟的驗證

- [同盟驗證選項](about-office-365-identity.md#federated-authentication-options)-主要使用於具有較複雜的驗證需求，大型企業組織內部部署與 Office 365 同步處理目錄物件和使用者帳戶為受管理的內部部署。 
    
- [協力廠商驗證與身分識別提供者](about-office-365-identity.md)的內部部署目錄物件可能會同步至 Office 365 部署及雲端資源存取主要是由協力廠商身分識別提供者 (Isp) 所管理。 
    
## <a name="managing-accounts"></a>管理帳戶

當決定組織將建立和管理帳戶的方式，請考慮下列各項：
  
- 目錄同步處理軟體必須安裝在連線 Office 365 和您的內部部署目錄之間的身分識別在內部部署環境中的伺服器上。
    
- 任何目錄同步處理] 選項，包括 SSO 選項，需要您在內部 directory 屬性符合標準。 [準備透過目錄同步處理至 Office 365 佈建使用者](prepare-for-directory-synchronization.md)說明哪些屬性用於您的目錄，且需要何種清除 （如果有的話） 的細節。 如需如何使用 IdFix 來自動化目錄清理的指示，請參閱[安裝和執行 Office 365 IdFix 工具](install-and-run-idfix.md)。 
    
- 規劃您要如何建立 Office 365 帳戶。
    
    下表列出不同的帳戶管理工具。
    
|**選項**|**附註**|
|:-----|:-----|
|系統管理中心  <br/> |[將使用者新增個別或大量至 Office 365-系統管理說明](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  提供要新增或變更使用者帳戶的簡單 web 介面。  <br/>  無法用來變更使用者，如果已啟用目錄同步處理 （可以設定位置和授權指派）。  <br/>  無法與 SSO 選項搭配使用。  <br/> |
|Windows PowerShell  <br/> |[使用 Windows PowerShell 管理 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  可讓您將使用者在大量使用者，使用 Windows PowerShell 指令碼。  <br/>  可用來將位置和授權指派給帳戶，不論建立帳戶的方式。  <br/> |
|大量匯入  <br/> |[同時將多位使用者新增至 Office 365 - 系統管理說明](add-several-users-at-the-same-time.md) <br/>  可讓您匯入 CSV 檔案，以將使用者群組新增至 Office 365。  <br/>  無法與 SSO 選項搭配使用。  <br/> |
|Azure Active Directory  <br/> |您可以取得免費版本的 Azure Active Directory 與 Office 365 訂閱。 您可以執行像是自助密碼重設雲端使用者，以及自訂的登入及存取面板頁面使用免費版的功能。 若要取得增強的功能，您可以升級的基本的版本，或 premium edition。 支援的功能清單，請參閱[Azure Active Directory 的版本](https://go.microsoft.com/fwlink/p/?LinkId=698465)。  <br/> |
|目錄同步處理  <br/> |[整合內部部署身分識別與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  目錄同步處理或不需要密碼同步處理，使用[Azure AD Connect 搭配快速設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。  <br/>  針對多個樹系與 SSO 選項，使用[自訂安裝的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。  <br/>  提供必要時啟用 SSO 的基礎結構。  <br/>  所需的許多混合式案例：  <br/>  分段移轉  <br/>  混合式 Exchange  <br/>  同步處理安全性群組和擁有郵件功能的群組，從您的內部部署目錄。  <br/> |
   
- 不論如何您想要將使用者帳戶新增至 Office 365，您需要管理數個帳戶功能，例如指派授權，指定的位置，依此類推。 這些功能可以管理長期從系統管理中心，或者您也可以[建立使用 Office 365 PowerShell 的使用者帳戶](https://go.microsoft.com/fwlink/p/?LinkId=717083)。
    
    如果您選擇新增和管理您透過 admin 中心的所有使用者，您將指定的位置，並在同一時間建立 Office 365 帳戶指派授權。 因此，不多規劃是必要的。
    
    > [!IMPORTANT]
    > 在 Office 365 中建立帳戶，沒有指派授權 （給 SharePoint Online 中，例如) 表示的帳戶擁有者可以檢視 Office 365 入口網站，但無法存取任何您公司的訂閱內的服務。 指派位置和授權之後，帳戶會複寫到您指派服務的服務。 使用者可以登入其帳戶，並使用您指派給他們的服務。 
  
## <a name="next-steps"></a>後續步驟

[Office 365 與內部部署環境整合](office-365-integration.md)
  
## <a name="see-also"></a>另請參閱

[管理 Office 365 中的使用者帳戶](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

