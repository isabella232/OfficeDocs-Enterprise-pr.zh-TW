---
title: 為 Office 365 設定目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162476"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>為 Office 365 設定目錄同步處理

Office 365 會使用 Azure Active Directory (Azure AD) 租用戶來儲存和管理身分識別驗證及存取雲端式資源的權限。 

如果您有內部部署 Active Directory 網域服務 (AD DS)，您可以使用 Office 365 訂閱下 Azure AD 租用戶同步處理您的 AD DS 使用者帳戶、 群組和連絡人。 這是 Office 365 的混合式身分識別。 以下是及其元件。

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect 在內部部署伺服器上執行，並將 AD DS 與 Azure AD 租用戶同步處理。 目錄同步處理，以及您也可以指定這些驗證選項：

- 密碼雜湊同步處理 (PHS)

  Azure AD 會執行本身的驗證。

- 傳遞驗證 (PTA)

  Azure AD 具有 AD DS 執行驗證。

- 同盟的驗證

  Azure AD 會重新導向的用戶端電腦要求驗證連絡另一個身分識別提供者。

如需詳細資訊，請參閱[混合式身分識別](plan-for-directory-synchronization.md)。
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1.檢閱 Azure AD Connect 的必要條件

您要取得免費的 Office 365 訂閱的 Azure AD 訂閱。 當您設定目錄同步處理時，您將在其中一部內部部署伺服器上安裝 Azure AD Connect。
  
Office 365，您必須以：
  
- 確認您的內部部署網域。 Azure AD Connect 精靈會引導您完成這。
- 取得的使用者名稱和您的 Office 365 租用戶及 AD DS 的系統管理員帳戶的密碼。

內部部署伺服器上安裝 Azure AD Connect，您將需要：
  
|**伺服器作業系統**|**其他軟體**|
|:-----|:-----|
|Windows Server 2012 R2 和更新版本 | -預設會安裝 PowerShell，不不需要任何動作。  <br> 額淨 4.5.1 和更新版本提供透過 Windows Update。 請確定您已安裝最新的更新至控制台] 中的 Windows Server。 |
|Windows Server 2008 R2 Service Pack 1 (SP1) * * 或 Windows Server 2012 | -在 Windows Management Framework 4.0 中使用 PowerShell 的最新版本。 在[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上進行搜尋。  <br> -.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |
|Windows Server 2008 | -在 Windows Management Framework 3.0，位於[Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)中使用 PowerShell 的最新支援的版本。  <br> -.Net 4.5.1 和更新版本的版本是位於[Microsoft 下載中心找到](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |

請參閱 < <b0>Azure Active Directory Connect 的必要條件</b0>for 硬體、 軟體、 帳戶及權限需求、 SSL 憑證需求及物件限制的詳細資料的 Azure AD Connect。
  
您也可以檢閱 Azure AD Connect[版本版本歷程記錄](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)項目包含以及固定中每個版本。

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2.安裝 Azure AD Connect 及設定目錄同步作業

開始之前，請確定您具有：

- 使用者名稱和密碼的 Office 365 全域系統管理員
- 使用者名稱和密碼的 AD DS 網域系統管理員
- 哪一種驗證方法 （PHS、 PTA，同盟）
- 您是否要使用[Azure AD 無縫單一登入 (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

請遵循下列步驟：

1. 登入[Microsoft 365 系統管理中心](https://admin.microsoft.com)(https://admin.microsoft.com) ，然後選擇 [**使用者**\>左側導覽窗格上的**作用中的使用者**。
2. 在系統管理中心中，在**作用中使用者**] 頁面上，選擇 [**更多** \> **目錄同步處理**。

    ![在 [更多] 功能表中，選擇 [目錄同步處理](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. 在 [ **Active Directory 準備工作**] 頁面上，選取 [**下載 Microsoft Azure Active Directory Connect 工具**連結若要開始。 
4. 遵循 [ [Azure AD Connect 與 Azure AD Connect Health 安裝藍圖](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)中的步驟。

## <a name="3-finish-setting-up-domains"></a>3.完成網域設定

請遵循[Office 365 管理您的 DNS 記錄時建立 DNS 記錄](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)，以完成您的網域設定] 中的步驟。

## <a name="next-step"></a>下一步

[指派授權給使用者帳戶](assign-licenses-to-user-accounts.md)。
