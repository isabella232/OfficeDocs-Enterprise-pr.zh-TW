---
title: 設定 Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何設定 Office 365 與您在內部部署 Active Directory 之間的目錄同步處理。
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539961"
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
  
3. 在 * * 為目錄同步處理適合您嗎？* *] 頁面上的兩個的第一個選擇的**1-10**和**11 50**結果在"根據組織的大小，建議您建立及管理在雲端中的使用者。使用目錄同步處理會使您的安裝程式更複雜。移至作用中使用者加入您的使用者 」。 
    
    - 您還是可以，不過，繼續設定目錄同步處理選擇**以下繼續**在頁面底部。 
    
    - 如果您選取兩個的選擇後者**51-250** **大於或等於 251**、 同步處理設定將會建議目錄同步處理。選擇 [**下一步**繼續執行。 
    
    ![選擇 [下一步] 繼續進行目錄同步處理設定](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. 在**同步處理您的本機目錄與雲端**中讀取資訊，及如果您想的詳細資訊，請選擇了解更多連結會移到：[佈建使用者可透過目錄同步處理至 Office 365 的準備](prepare-for-directory-synchronization.md)，然後選擇 [下一步****. 
    
5. 在**我們檢查您的目錄**] 頁面上檢閱自動檢查您的目錄的需求。如果符合需求，選擇 [**下一步** \> **開始掃描**。如果您不能符合要求您仍然可以繼續選擇 [**繼續] 以手動方式**。
    
    ![選擇 [下一步] 或手動在繼續我們檢查您的目錄] 頁面上](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. 如果您選取要掃描您的目錄，選擇 [**開始掃描****評估目錄同步處理設定**] 頁面上。 
    
    遵循下載並執行掃描的指示。
    
7. 掃描完成後，回到 [安裝精靈] 並選擇 [**下一步**查看掃描結果。 
    
8. 依指示在**驗證擁有權的網域**] 頁面上確認您的網域。如需詳細指示，請參閱[Office 365 管理 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)。
    
    > [!IMPORTANT]
    > 新增 TXT 記錄，以確認您擁有網域之後，不前往 [網域] 精靈中新增使用者的下一個步驟。目錄同步作業會將使用者新增為您。 
  
    傳回**Office 365 設定**] 頁面上，選擇 [**重新整理**
    
    ![確認您的網域之後，請選擇 [重新整理](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. 在**您的網域已準備就緒**] 頁面上選擇 [**下一步**]。
    
10. **清理您的環境**] 索引標籤上 （選用） 依照指示下載 IDFix 檢查您的 Active Directory。選擇 [**下一步**繼續執行。 
    
11. 在 * * 執行 Azure Active Directory 連線 * *] 頁面上，選擇 [**下載**] 以安裝 Azure AD 連線精靈]。 
    
    > [!NOTE]
    > 此時您就會在 Azure AD 連線精靈]。請務必保留您已上次在開啟在瀏覽器中，因此您可以將它的 Azure AD Connect 步驟已完成後返回 [目錄同步處理精靈] 頁面。 
  
    Azure AD 連線精靈已完成安裝後將會自動開啟它。您也可以從您的桌面預設安裝網站開啟它。請遵循精靈的指示進行根據您的案例：
    
  - 使用密碼雜湊同步處理的目錄同步作業，使用[Azure AD 連線明確的設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。
    
  - 針對多個樹系、 通過驗證、 同盟身分識別與 SSO 選項、 使用[自訂安裝的 Azure AD 連線](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
    
    **自訂** **Express 設定**] 頁面上選取要使用這些選項。 
    
12. Azure AD 連線精靈] 完成之後，回到 [ **Office 365 設定**精靈] 並依照上**進行確認同步處理作業如預期] 頁面上**的指示。選擇 [**下一步**繼續執行。 
    
13. 閱讀指示 * * 啟動使用者 * *] 頁面上，然後選擇 [**下一步**。
    
14. **您是所有的安裝程式**] 頁面上選擇 [**完成**]。 
    
## <a name="assign-licences-to-synchronized-users"></a>將授權指派給同步處理的使用者
您已同步處理至 Office 365 使用者之後，會在建立時，但您必須將授權指派給他們，以便他們可以使用 Office 365 的功能，例如郵件。指示，請參閱[指派給 Office 365 中的商務使用者的授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。
    
## <a name="finish-setting-up-domains"></a>完成的網域設定
請遵循[的 Office 365 管理 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成設定您的網域中的步驟。