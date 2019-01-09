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
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何設定 Office 365 與您在內部部署 Active Directory 之間的目錄同步處理。
ms.openlocfilehash: 95f138a0a11f14a1036d7d48983f4c88bc965fd0
ms.sourcegitcommit: 0fdb6e470342a98ba164db627fe3dd02cfe8aa0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "27768822"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>設定 Office 365 的目錄同步處理
Office 365 管理使用者使用雲端使用者身分識別管理 Azure Active Directory 服務。您也可以使用 Azure AD 整合您的內部部署 Active Directory 來使用 Office 365 同步處理內部部署環境。一旦您設定同步處理您可以決定有內部部署目錄或 Azure AD 內進行其使用者驗證。
  
## <a name="office-365-directory-synchronization"></a>Office 365 目錄同步處理
您可以使用同步處理的身分識別或內部部署組織與 Office 365 之間的同盟身分識別。與同步處理的身分識別管理您的使用者內部部署，並當他們使用相同的密碼在雲端為內部部署的 Azure AD 驗證。這是最常見的目錄同步處理案例。通過驗證] 或 [同盟身分識別可讓您管理您的使用者內部部署和他們通過驗證的內部部署目錄。同盟身分識別需要進行其他設定並可讓您只有一次登入的使用者。如需詳細資訊，請閱讀[了解 Office 365 身分識別與 Azure Active Directory](about-office-365-identity.md)。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>要從 Windows Azure Active Directory 同步處理 (DirSync) 升級至 Azure [Active Directory 連線吗？
如果您在使用 DirSync，想要升級的[升級指示](https://go.microsoft.com/fwlink/p/?LinkId=733240)向透過[azure.com](https://azure.com) 。
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD 的先決條件連線
您要取得與 Office 365 訂閱免費訂閱 Azure AD。當您設定目錄同步作業時，您將會安裝 Azure [Active Directory 連線在其中一部內部伺服器。
  
Office 365 的您必須：
  
- 確認您的內部部署網域 （程序將會帶領您完成此）。
- 已[指派管理員角色在 Office 365 企業版](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)Office 365 租用戶的權限和內部部署 Active Directory。 
    
安裝 Azure AD 連接內部部署伺服器您將需要下列軟體：
  
|**伺服器 OS**|**其他軟體**|
|:-----|:-----|
|**Windows Server 2012 R2** | 預設會安裝 PowerShell、 不不需要任何動作。  <br/> 互打 4.5.1 並提供更新版本的 Windows Update 透過。請確定您已安裝最新的更新在控制台中的 Windows server。 |
|**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012** | -使用 Windows Management Framework 4.0 中 PowerShell 的最新版本。在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜尋它。<br/> -.Net 4.5.1 及更新的版本是位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |
|**Windows Server 2008** | -使用 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)的 PowerShell 最新支援的版本。  <br/> -.Net 4.5.1 及更新的版本是位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |
   
> [!NOTE]
> 如果您使用 Azure Active Directory DirSync，您可以對 Azure Active Directory 同步處理從內部部署 Active Directory 的通訊群組成員數目上限為 15000。Azure AD 連線，該號碼為 50000。 
  
更多謹慎檢閱硬體、 軟體、 帳戶和權限需求、 SSL 憑證需求，以及 Azure AD 連接中的物件限制讀取[Azure 作用中的目錄連線的先決條件](https://go.microsoft.com/fwlink/p/?LinkId=716896)。
  
您也可以檢閱 Azure AD 連接[版本版本歷程記錄](https://go.microsoft.com/fwlink/p/?LinkId=733238)項目包含以及固定在每個版本中。 

## <a name="to-set-up-directory-synchronization"></a>若要設定目錄同步作業
1. 登入 Office 365 系統管理中心並且選擇 [**使用者** \> **作用中使用者**在左導覽列中。 
2. 在 Office 365 系統管理中心，在**作用中使用者**] 頁面上，選擇 [* * 更 * * \> **目錄同步處理**。
    
    ![在 [更多] 功能表中選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. 在 [ **Active Directory 準備工作**] 頁面上選取 [開始**下載 Microsoft Azure Active Directory 連線工具**連結。如需 Azure [Active Directory 連線安裝程序的詳細資訊，請參閱[Azure AD Connect 及 Azure AD 連線狀況安裝藍圖](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。
    
## <a name="assign-licences-to-synchronized-users"></a>將授權指派給同步處理的使用者
您已同步處理至 Office 365 使用者之後，會在建立時，但您必須將授權指派給他們，以便他們可以使用 Office 365 的功能，例如郵件。指示，請參閱[指派給 Office 365 中的商務使用者的授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。
    
## <a name="finish-setting-up-domains"></a>完成的網域設定
請遵循[的 Office 365 管理 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成設定您的網域中的步驟。