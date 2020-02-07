---
title: 如何設定商務用 Skype 內部部署以使用混合式新式驗證
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 新式驗證，是一種方法提供了更安全的使用者驗證和授權、 skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合可用的身分識別管理。
ms.openlocfilehash: de5063da9eed03e2cd455b79b3a2d1c2f671ad1e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840720"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>如何設定商務用 Skype 內部部署以使用混合式新式驗證

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

新式驗證，是一種方法提供了更安全的使用者驗證和授權、 skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合可用的身分識別管理。
  
 **重要**您可能會想要深入了解新式驗證 (MA)，您可能偏好使用公司或組織中？ 檢查[此文件](hybrid-modern-auth-overview.md)的概觀。 如果您需要知道哪些 Skype for Business 拓撲支援 MA，以下記載 ！
  
 **開始前**，我呼叫：
  
- 新式驗證\>MA

- 混合式新式驗證\>HMA

- Exchange 內部部署\>NM-EXCH-UM-1ST

- Exchange Online \> EXO

- Skype for Business 內部\>SFB

- 與 Skype for Business Online \> SFBO

此外，本文中的圖形是否會呈現灰色延展或變暗物件，表示中灰色**不是**顯示的項目包含在特定 MA 的組態。
  
## <a name="read-the-summary"></a>閱讀有關摘要

此摘要會分解成步驟可能否則會遺失在執行期間，以及良好的整體的檢查清單，以保留您所在之程序中的追蹤記錄的程序。
  
1. 首先，請確定您符合所有必要條件。

1. 自許多**必要條件**是很常見的兩個 Skype for Business 和 Exchange，[請參閱您預先需求的檢查清單概觀文章](hybrid-modern-auth-overview.md)。 執行此*之前*開始任何本文中的步驟。

1. 收集您需要在檔案或 OneNote HMA 特有資訊。

1. 開啟 ON 新式驗證 EXO （如果它尚未開啟）。

1. 開啟 ON 新式驗證 SFBO （如果它尚未開啟）。

1. 開啟 Exchange 內部部署的混合式新式驗證。

1. 開啟商務內部 skype 的混合式新式驗證。

下列步驟開啟 MA SFB、 SFBO、 NM-EXCH-UM-1ST，及 EXO-亦即可以參與 HMA 設定 SFB 和 SFBO （包括 NM-EXCH-UM-1ST/EXO 上的相依性） 的所有產品。 也就是說，如果您的使用者皆位於 / 已在混合式 （EXO + SFBO、 EXO + SFB、 NM-EXCH-UM-1ST + SFBO，或 NM-EXCH-UM-1ST + SFB） 的任何部分中建立信箱，您已完成的產品看起來像這樣：
  
![商務 HMA 拓撲混合 6 商務用 Skype 具備 MA 中所有四個可能的位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
您可以看到有四個不同的位置，來開啟 MA ！ 為最佳使用者經驗，我們建議您開啟 MA 總共四個這些位置中。 如果您不能在所有這些位置開啟 MA，請調整步驟，讓您開啟 MA 只能在所需的環境的位置。
  
請參閱支援的拓撲[與 MA 的商務用 Skype 的支援主題](https://technet.microsoft.com/library/mt803262.aspx)。
  
 **重要**請仔細檢查您開始之前已符合所有必要條件。 您會發現該資訊[以下](hybrid-modern-auth-overview.md)。
  
## <a name="collect-all-hma-specific-info-youll-need"></a>收集您需要的所有 HMA 特有資訊

您已重複檢查，之後您已符合[先決條件](hybrid-modern-auth-overview.md)以使用新式驗證 （請參閱上述的附註），您應該建立檔案來包含您需要設定 HMA 往前的步驟中的資訊。 使用本文中的範例：
  
- **SIP/SMTP 網域**

  - 例如 contoso.com （同盟與 Office 365）

- **租用戶識別碼**

  - GUID，代表您的 Office 365 租用戶 （位於 contoso.onmicrosoft.com 的登入）。

- **SFB 2015 CU5 Web 服務 Url**

您將需要內部和外部 web 服務 URL 的所有部署的 SfB 2015 集區。 若要取得這些，請執行下列從 Skype for Business 管理命令介面：
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- 例如 內部：https://lyncwebint01.contoso.com

- 例如 外部：https://lyncwebext01.contoso.com

如果您使用 Standard Edition server，內部 URL 將會空白。 在此情況下，使用內部 URL 的集區 fqdn。
  
## <a name="turn-on-modern-authentication-for-exo"></a>開啟 [EXO 的新式驗證

請遵循以下指示： [Exchange Online： 如何啟用新式驗證在租用戶。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>開啟 SFBO 的新式驗證

請遵循以下指示： [Skype for Business Online： 啟用新式驗證在租用戶](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>開啟 Exchange 內部部署的混合式新式驗證

請遵循以下指示：[如何設定 Exchange Server 內部部署以使用混合式新式驗證](configure-exchange-server-for-hybrid-modern-authentication.md)。
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>開啟商務內部部署的 skype 的混合式新式驗證

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>新增內部 Azure AD 中為 Spn web 服務 Url

現在您需要執行命令，以作為服務主體中 SFBO 新增 （收集更早版本） 的 Url。
  
 **附註**服務主要名稱 (Spn) 識別 web 服務，以及其關聯 （例如帳戶名稱或群組） 的安全性主體，讓該服務可對授權的使用者代理。 伺服器進行驗證的用戶端進行使用的資訊的中所含的 Spn。
  
1. 首先，連線至 AAD[這些](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)指示。

2. 執行此命令中，內部部署，若要取得之 SFB web 服務 Url 的清單。

   請注意，AppPrincipalId 開頭`00000004`。 這會對應到 Skype for Business Online。

   此命令，它會包括 SE 和 WS URL，但是大部分所組成的開頭的 Spn 的輸出採取的附註 （和更新版本的比對的螢幕擷取畫面） `00000004-0000-0ff1-ce00-000000000000/`。

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. 如果內部**或**外部遺漏了從內部 SFB Url (例如https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我們需要將這些特定記錄新增至這份清單。

    請務必*範例 Url* ] 下方，取代實際 Url 中新增命令 ！
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. 確認您新的記錄已新增步驟 2 中**取得 MsolServicePrincipal**命令執行，並將輸出中尋找。 比較清單 / 將螢幕擷取畫面從之前的 Spn （您可能也螢幕擷取畫面新清單以供記錄） 新的清單。 如果您已成功，您會看到兩個新的 Url 清單中。 將由我們的範例，此清單的 Spn 將現在包含特定 Urlhttps://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com/。

### <a name="create-the-evosts-auth-server-object"></a>建立 EvoSTS 驗證伺服器物件

下列中執行命令 Skype for Business 管理命令介面。
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>啟用混合式新式驗證

這是實際開啟 MA 的步驟。 所有先前的步驟可以執行事先，而不需要變更用戶端驗證流程。 當您準備好要變更的驗證流程時，執行此命令中 Skype for Business 管理命令介面。

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>確認

一旦您啟用 HMA，用戶端下次登入時會使用新的驗證流程。 請注意，只開啟 HMA 就不會觸發重新驗證任何用戶端。 用戶端重新驗證為基礎的存留期的驗證權杖及/或他們所擁有的憑證。
  
若要測試 HMA 正常之後您已啟用它，登出測試 SFB Windows 用戶端，請務必按一下 [刪除我的認證]。 再次登入。 用戶端現在應該使用新式驗證流程和您的登入現在包含 '工作或學校' 的**Office 365**提示看右之前用戶端連絡伺服器，而且您登入的帳戶。
  
您應該也檢查組態資訊 skype 商務用戶端 'OAuth 授權單位 」。 用戶端電腦上執行這項操作，請按住 CTRL 鍵在同一時間以滑鼠右鍵按一下 Skype for Business 圖示 Windows 通知紙匣。 在出現的功能表中，按一下 [**設定資訊**。 在桌面上會出現 ['Skype for Business 組態資訊'] 視窗中，尋找下列：
  
![商務用戶端使用新式驗證用 Skype 的組態資訊會顯示 Lync 和 EWS OAUTH 授權 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
您也應按住 CTRL 鍵，同時以滑鼠右鍵按一下 [Outlook 用戶端 （也在 Windows 通知紙匣）] 圖示，然後按一下 [' 連線狀態 '。 用戶端的 SMTP 位址是否與 AuthN 類型尋找 ' 承載\*'，用來表示用於 OAuth 承載 token。
  
## <a name="related-articles"></a>相關文章

[新式驗證概觀連結](hybrid-modern-auth-overview.md)。
  
您需要了解如何使用您 skype 的新式驗證 (ADAL) 的商務用戶端嗎？ 我們是否已取得最新產品步驟[以下](https://technet.microsoft.com/library/mt710548.aspx)。
