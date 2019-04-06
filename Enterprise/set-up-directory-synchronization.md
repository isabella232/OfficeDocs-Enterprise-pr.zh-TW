---
title: 設定 Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何設定 Office 365 和您在內部部署 Active Directory 之間的目錄同步處理。
ms.openlocfilehash: 6d635dbcacb5a1c6c6c9c202f2ece4fac35558a4
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001746"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>設定 Office 365 的目錄同步處理

Office 365 使用雲端型使用者身分識別管理服務 Azure Active Directory 來管理使用者。 您也可以與 Office 365 同步內部部署環境，與 Azure AD 整合您的內部部署 Active Directory。 一旦您設定同步處理您可以決定有您的內部部署目錄或 Azure AD 內進行其使用者驗證。
  
## <a name="office-365-directory-synchronization"></a>Office 365 目錄同步作業

您可以使用同步處理的身分識別或在內部部署組織與 Office 365 之間的同盟身分識別。 同步處理的身分識別，管理您內部使用者，以及當他們使用相同的密碼定域機組中為內部部署的 Azure AD 驗證。 這是最常見的目錄同步處理案例。 通過驗證] 或 [同盟身分識別，可讓您管理您內部使用者，就會成為驗證您的內部部署目錄。 同盟身分識別需要其他設定，並可讓您只有一次登入的使用者。 如需詳細資訊，請閱讀[了解 Office 365 身分識別與 Azure Active Directory](about-office-365-identity.md)。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>要從 Windows Azure Active Directory 同步處理 (DirSync) 升級至 Azure Active Directory Connect 嗎？

如果您目前使用目錄同步，並且想要升級，請前往透過[azure.com](https://azure.com) [升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="prerequisites-for-azure-ad-connect"></a>必要條件的 Azure AD Connect

您要取得免費的訂閱 Azure AD 與您的 Office 365 訂閱。 當您設定目錄同步處理時，您將安裝 Azure Active Directory Connect 在其中一部內部部署伺服器。
  
針對 Office 365 您將需要：
  
- 確認您的內部網域 （程序將引導您進行此）。
- 已[指派系統管理員角色在商務用 Office 365 中的](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)您的 Office 365 租用戶的權限和內部部署 Active Directory。

您的內部部署伺服器安裝 Azure AD Connect，您將需要下列軟體：
  
|**伺服器作業系統**|**其他軟體**|
|:-----|:-----|
|**Windows Server 2012 R2** | -預設會安裝 PowerShell，不不需要任何動作。  <br> 額淨 4.5.1 和更新版本提供透過 Windows Update。 請確定您已安裝最新的更新至控制台] 中的 Windows Server。 |
|**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012** | -在 Windows Management Framework 4.0 中使用 PowerShell 的最新版本。 在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上進行搜尋。  <br> -.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |
|**Windows Server 2008** | -在 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)中使用 PowerShell 的最新支援的版本。  <br> -.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |

> [!NOTE]
> 如果您使用 Azure Active Directory DirSync，您可以對 Azure Active Directory 同步處理從內部部署 Active Directory 的通訊群組成員的數目上限為 15000。 針對 Azure AD Connect，該數量為 50000。
  
若要更仔細檢閱 Azure AD Connect 硬體、 軟體、 帳戶及權限需求、 SSL 憑證需求及物件限制，請閱讀[Azure Active Directory Connect 的必要條件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)。
  
您也可以檢閱 Azure AD Connect[版本版本歷程記錄](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)項目包含以及固定中每個版本。

## <a name="to-set-up-directory-synchronization"></a>若要設定目錄同步處理

1. 登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)，選擇 [**使用者**\>左側導覽窗格上的**作用中的使用者**。
2. 在系統管理中心中，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。

    ![在 [更多] 功能表中，選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. 在 [ **Active Directory 準備工作**] 頁面上，選取 [**下載 Microsoft Azure Active Directory Connect 工具**連結若要開始。 如需 Azure Active Directory Connect 安裝程序的詳細資訊，請參閱[Azure AD Connect 與 Azure AD Connect Health 安裝藍圖](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。

## <a name="assign-licenses-to-synchronized-users"></a>將授權指派給同步處理的使用者

您已同步至 Office 365 使用者之後，他們所建立，但您需要指派授權給他們，讓他們可以使用 Office 365 功能，例如郵件。 如需相關指示，請參閱 <<c0>指派給商務用 Office 365 中的使用者授權。

## <a name="finish-setting-up-domains"></a>完成設定網域

請遵循[Office 365 管理您的 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)，以完成您的網域設定] 中的步驟。