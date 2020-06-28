---
title: 管理 Microsoft 365 帳戶的工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: '瞭解用來管理 Microsoft 365 使用者的工具，以及您可以使用哪些工具，取決於您管理使用者身分識別的方式。 '
ms.openlocfilehash: c382006fe8cb46342548b7533148e760c103bf50
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906215"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a>管理 Microsoft 365 帳戶的工具

您可以根據您的設定，以數種不同的方式管理 Microsoft 365 使用者。 您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)、Windows PowerShell、您的內部部署目錄或 Azure Active directory 系統管理員入口網站中管理使用者。

一旦您購買 Microsoft 365，系統管理中心和 Windows PowerShell 便可用於管理帳戶。 管理雲端身分識別組織中的每一位人員，都有個別的使用者識別碼和密碼用於 Microsoft 365。 如果您想要與您的內部部署基礎結構整合，並將使用者帳戶與 Microsoft 365 同步，您可以使用 Azure Active Directory Connect 來提供身分識別的同步處理，並選擇性地提供密碼同步處理或完整單一登入功能。
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>規劃管理使用者帳戶的位置和方式

您可以管理使用者帳戶的位置和方式，取決於您要用於 Microsoft 365 訂閱的身分識別模型。 這兩個整體模型為雲端驗證及同盟驗證。
  
### <a name="cloud-authentication"></a>雲端驗證

- [Microsoft 365 Identity](about-office-365-identity.md) -建立及管理系統管理中心的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory 來管理使用者。
- [具有無縫單一登入的密碼雜湊同步處理](about-office-365-identity.md)-針對 Azure AD 中內部部署目錄物件啟用驗證的最簡單方式。 透過密碼雜湊同步處理（PHS），您可以將內部部署 Active Directory 使用者帳戶物件與 Microsoft 365 同步處理，並管理內部部署的使用者。 
- [透過無縫單一登入的傳遞驗證](about-office-365-identity.md)-利用一或多個內部部署伺服器上執行的軟體代理程式，為 Azure AD 驗證服務提供簡單的密碼驗證，以直接使用內部部署 Active Directory 驗證使用者。 

### <a name="federated-authentication"></a>同盟驗證

- [Microsoft 365 身分識別](about-office-365-identity.md)-主要針對具有更複雜驗證需求的大型企業組織，內部部署目錄物件會與 Microsoft 365 同步處理，而且使用者帳戶是在內部部署管理。 
- [協力廠商驗證和身分識別提供者](about-office-365-identity.md)-內部部署目錄物件可同步處理至 Microsoft 365，而雲端資源存取主要是由協力廠商身分識別提供者（IdP）來管理。 

## <a name="managing-accounts"></a>管理帳戶

決定組織建立及管理帳戶的方式時，請考慮下列各項：
  
- 您必須在內部部署環境中的伺服器上安裝目錄同步作業軟體，以連接 Microsoft 365 和內部部署目錄之間的身分識別。
- 任何目錄同步處理選項（包括 SSO 選項）都需要您的內部部署目錄屬性符合標準。 您的目錄中所使用的屬性和清理（如果有的話）的詳細資訊，說明如何在[目錄同步處理至 Microsoft 365 時提供使用者](prepare-for-directory-synchronization.md)。 請參閱[下載並執行 Microsoft 365 IdFix 工具](install-and-run-idfix.md)，以取得如何使用 IdFix 自動目錄清理的說明。 

## <a name="plan-how-you-are-going-to-create-microsoft-365-accounts"></a>規劃如何建立 Microsoft 365 帳戶

下表列出不同的帳戶管理工具：

|**選項**|**附註**|
|:-----|:-----|
|**系統管理中心** | - [個別或大量將使用者新增至 Microsoft 365-系統管理說明](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -提供簡單的 web 介面來新增及變更使用者帳戶。 <br> -如果啟用目錄同步處理，則無法用來變更使用者（可以設定位置和授權指派）。 <br> -無法與 SSO 選項搭配使用。 <br> |
|**Windows PowerShell** | - [使用 Windows PowerShell 管理 Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -可讓您使用 Windows PowerShell 腳本，在大量使用者中新增使用者。 <br> -可用於將位置和授權指派給帳戶，不論帳戶的建立方式為何。 <br> |
|**大量匯入** | - [同時將多個使用者新增至 Microsoft 365-系統管理說明](add-several-users-at-the-same-time.md) <br> -可讓您匯入 CSV 檔案，將使用者群組新增至 Microsoft 365。 <br> -無法與 SSO 選項搭配使用。 <br> |
|**Azure Active Directory** | -您可以使用 Microsoft 365 訂閱取得免費的 Azure Active Directory 版本。 -您可以執行雲端使用者的自助密碼重設功能，以及使用免費版本自訂登入和存取面板頁面等功能。 <br> -若要取得增強的功能，您可以升級至 basic edition 或 premium edition。 請參閱[Azure Active Directory edition](https://go.microsoft.com/fwlink/p/?LinkId=698465) ，以取得支援的功能清單。 <br> |
|**目錄同步處理** | - [整合您的內部部署身分識別與 Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -如果是使用或不使用密碼同步處理的目錄同步處理，請使用[AZURE AD Connect with express 設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。  <br>  -如果是多個樹系和 SSO 選項，請使用[AZURE AD Connect 的自訂安裝](https://go.microsoft.com/fwlink/p/?LinkId=698430)。 <br> -提供啟用 SSO 所需的基礎結構。 <br> -許多混合式案例都需要（分段遷移、混合式 Exchange） <br> -從您的內部部署目錄同步處理安全性和擁有郵件功能的群組。 <br> |

不論您要如何將使用者帳戶新增至 Microsoft 365，您需要管理多個帳戶功能，例如指派授權、指定位置等等。 您可以從系統管理中心管理這些功能，也可以[使用 Microsoft 365 PowerShell 來建立使用者帳戶](https://go.microsoft.com/fwlink/p/?LinkId=717083)。

如果您選擇透過系統管理中心新增及管理所有使用者，您會指定位置並指派授權，建立 Microsoft 365 帳戶時。 因此，不需要進行許多規劃。

> [!IMPORTANT]
> 在未指派授權的情況下建立 Microsoft 365 中的帳戶（例如，若要 SharePoint 線上），表示帳戶擁有者可以查看 Microsoft 365 系統管理中心，但無法存取公司訂閱內的任何服務。 在您指派位置和授權後，系統會將帳戶複製到您指派的服務或服務。 使用者可以登入其帳戶，並使用您指派給他們的服務。