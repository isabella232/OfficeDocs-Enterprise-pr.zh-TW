---
title: 如何設定商務用 Skype 內部部署以使用混合式新式驗證 (英文)
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: 經過驗證是一種方法提供較安全的使用者驗證與授權、 供商務 server 內部部署和 Exchange server 內部部署，以及商務混合的分隔網域 Skype Skype 的身分識別管理。
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540279"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>如何設定商務用 Skype 內部部署以使用混合式新式驗證 (英文)

經過驗證是一種方法提供較安全的使用者驗證與授權、 供商務 server 內部部署和 Exchange server 內部部署，以及商務混合的分隔網域 Skype Skype 的身分識別管理。
  
 **重要**您要了解更多有關現代驗證 (MA) 與您可能希望使用公司或組織中嗎吗？檢查[此文件](hybrid-modern-auth-overview.md)的概觀。如果您需要知道什麼 Skype for Business 拓撲支援 MA，此處所記載的 ！ 
  
 **我們開始之前**，請使用呼叫： 
  
- 現代驗證\>MA
    
- 混合式現代驗證\>HMA
    
- Exchange 內部部署\>NM-EXCH-UM-1ST
    
- Exchange Online \> EXO
    
- 企業內部的 Skype \> SFB
    
- 和 Skype 的線上商務\>SFBO
    
此外，* 如果本文中的圖形具有物件 ' 變為 out' 或 '變暗'，表示灰色**不**包含在 MA 特有設定中所示的元素。 * 
  
## <a name="read-the-summary"></a>閱讀摘要

此摘要 boils 程序將可能否則取得遺失執行期間並良好的整體檢查清單可保留所程序中的追蹤記錄的步驟。
  
1. 首先，請確定您符合所有必要軟體。
    
1. 自許多**必要條件**都通用的兩個 Skype 的業務與 Exchange，[請參閱概觀 （英文） 之前需求檢查清單](hybrid-modern-auth-overview.md)。執行此作業此*之前*開始執行任何本文中的步驟。 
    
2. 收集您需要在檔案或 OneNote HMA 特定資訊。
    
3. 開啟 ON 經過驗證的 EXO （如果它尚未開啟）。
    
4. 開啟 ON 經過驗證的 SFBO （如果它尚未開啟）。
    
5. 開啟 Exchange 內部部署的混合式經過驗證。
    
6. 開啟商務內部部署混合式的 Skype 經過驗證。
    
請注意下列步驟開啟 MA SFB、 SFBO、 NM-EXCH-UM-1ST 及 EXO-亦即可以參與 HMA 設定 SFB 和 SFBO （包括 NM-EXCH-UM-1ST/EXO 相依關係） 的所有產品。換句話說，如果您的使用者皆位於 / 已在混合式 （EXO + SFBO、 EXO + SFB、 NM-EXCH-UM-1ST + SFBO，或 NM-EXCH-UM-1ST + SFB） 的任何部分中建立信箱，您完成的產品會看起來如下：
  
![商務 HMA 拓撲的混合 6 Skype 具有 MA 中所有的四個可能位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
您可以看到有四種不同的位置可開啟 MA ！最佳使用者經驗的建議您開啟 MA 中所有的四個位置。如果您不能在所有這些位置開啟 MA，使您開啟位置所需的環境中僅 MA 調整步驟。
  
請參閱支援的拓撲[支援 Skype for Business 與 MA 的主題](https://technet.microsoft.com/en-us/library/mt803262.aspx)。 
  
 **重要**請仔細檢查您是否已符合所有必要軟體之前。您會找到該資訊[此處](hybrid-modern-auth-overview.md)。
  
## <a name="collect-all-hma-specific-info-youll-need"></a>收集您需要的所有 HMA 專屬資訊

您是否已重複的檢查之後您已符合[先決條件](hybrid-modern-auth-overview.md)使用經過驗證 （請參閱上面的附註），則應該建立檔案來包含您需要設定 HMA 在繼續進行步驟中的資訊。使用本文中的範例： 
  
- **SIP/SMTP 網域**
    
  - 例如 contoso.com （聯盟與 Office 365）
    
- **租用戶識別碼**
    
  - 代表您的 Office 365 租用戶 （位於 contoso.onmicrosoft.com 登入） 的 GUID。
    
- **SFB 2015 CU5 Web 服務 Url**
    
您必須內部和外部 web 服務 URL 的部署的所有 SfB 2015 集區。若要取得這些，執行下列從 Skype 商務管理命令介面：
  
Get-csservice-WebServer |Select-object PoolFqdn、 InternalFqdn、 ExternalFqdn |FL
  
- 例如內部：https://lyncwebint01.contoso.com
    
- 例如外部：https://lyncwebext01.contoso.com
    
如果您使用 Standard Edition server，將會是空白的內部 URL。在此例中，使用內部 URL 的集區 fqdn。
  
## <a name="turn-on-modern-authentication-for-exo"></a>開啟 [EXO 現代驗證

請遵循此處的指示： [Exchange Online： 如何啟用經過驗證的租用戶。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>開啟經過驗證的 SFBO

遵循此處的指示： [Skype 商務 online： 啟用經過驗證的租用戶](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>開啟混合經過驗證的 Exchange 內部部署

請遵循此處的指示：[如何設定 Exchange Server 內部使用混合式經過驗證](configure-exchange-server-for-hybrid-modern-authentication.md)。
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>開啟商務內部 Skype 的交互式現代驗證

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>新增內部部署在 Azure AD 為 Spn web 服務 Url

現在您需要執行命令以新增為 SFBO 中的服務主體 （收集稍早） 的 Url。
  
 **附註**服務主要名稱 (Spn) 識別 web 服務和其關聯 （例如帳戶名稱或群組） 的安全性主體，讓此服務可處理的授權的使用者代理。驗證伺服器的用戶端利用的資訊的中所含的 Spn。 
  
1. 首先，連線至 AAD[這些指示](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)。
    
2. 執行此命令中，內部，以取得 SFB web 服務 Url 的清單。
    
  - 取得 MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 |選取 [-ExpandProperty ServicePrincipalNames
    
    請注意 AppPrincipalId 開頭 '00000004'。這會對應至 Skype 商務 online。
    
    此命令將會包含 SE 和 WS URL，但多半組成 00000004-0000-0ff1-ce00-000000000000 的開頭的 Spn 的輸出採取的附註 （及更新版本比較的螢幕擷取畫面） /。
    
3. 如果內部**或**外部從內部部署的 SFB Url 會遺失 (例如https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我們需要將這些特定的記錄新增至這份清單。 
    
    請務必下方的*範例 Url*取代實際 Url 中新增命令 ！ 
    
  - $x = get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - 設定 MSOLServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000-ServicePrincipalNames $x.ServicePrincipalNames
    
4. 確認新的記錄已新增再次執行步驟 2 的 Get MsolServicePrincipal 命令並尋找透過輸出。將清單進行比較 / 螢幕擷取畫面從之前至新的 Spn （您也可以螢幕擷取畫面新清單的記錄） 清單。如果您已成功，您會看到兩個新的 Url 清單中。不再由我們的範例的 Spn 清單將會立即包含特定 Urlhttps://lyncweb01.contoso.com和https://autodiscover.contoso.com。
    
### <a name="create-the-evosts-auth-server-object"></a>建立 EvoSTS 驗證伺服器物件

商務管理命令介面 Skype 執行下列命令。
  
- New-csoauthserver-Identity evoSTS-MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true-類型 AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>啟用混合現代驗證

這是實際開啟 MA 的步驟。所有先前的步驟可以隨時執行而不變更用戶端驗證流程。當您準備好要變更的驗證流程時，請執行此命令中 Skype 商務管理命令介面。 
  
- Set-csoauthconfiguration-ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>[驗證]

一旦您啟用 HMA，用戶端的下一個登入將會使用新的驗證流程。請注意剛開啟 HMA 將不會觸發重新驗證的任何用戶端。用戶端重新驗證的驗證 token 及 （或） 憑證有存留期為基礎。
  
若要測試您已啟用它之後的運作 HMA，登出測試 SFB Windows 用戶端和務必按一下 [刪除我的認證]。再次登入。用戶端現在應該使用經過驗證流程與您的登入現在包含 '工作或學校' 的**Office 365**提示呈現右之前用戶端連絡伺服器，並在記錄您的帳戶。 
  
您應該也檢查組態資訊 Skype 商務用戶端的 OAuth 授權 」。用戶端電腦上執行這項作業，請按住 CTRL 鍵，同時您用滑鼠右鍵按一下 Skype 商務圖示中的 Windows 通知紙匣。在出現的功能表中按一下 [設定資訊。在桌上型電腦會出現 ['Skype 的商務組態資訊 」] 視窗中，尋找下列：
  
![商務用戶端使用經過驗證的組態資訊之 Skype 顯示 Lync 和 EWS OAUTH 授權 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
您也應該以滑鼠右鍵按一下圖示 Outlook 用戶端 （也是在 Windows 通知紙匣中） 的同時按住 CTRL 鍵並按一下 ' 連線狀態 」。針對根據驗證類型的用戶端的 SMTP 位址看起來 ' 承載\*'，這代表用於 OAuth 承載 token。
  
## <a name="related-articles"></a>相關的文章

[現代驗證概觀連結](hybrid-modern-auth-overview.md)。 
  
您需要了解如何使用您 Skype 商務用戶端的現代驗證 (ADAL)？我們已 got 步驟[此處](https://technet.microsoft.com/en-us/library/mt710548.aspx)。
  
是否要閱讀這些步驟，因為他們顯示的 Exchange Server 內部部署、 執行沒有 SFB 吗？這些步驟這裡可供使用。
  

