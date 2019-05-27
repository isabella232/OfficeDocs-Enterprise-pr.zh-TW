---
title: 混合式新式驗證概觀及使用商務和 Exchange 伺服器內部部署用 Skype 的必要條件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: 新式驗證是一種方法提供更安全的使用者驗證及授權的身分識別管理。 使用混合式部署的 Skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合。 此文章連結至相關的文件有關先決條件，安裝程式/停用新式驗證，和某些相關的用戶端 （例如。 Outlook 與 Skype 用戶端） 的資訊。
ms.openlocfilehash: 0448dfdc46598a6aa4df0108214ff0a4cf290382
ms.sourcegitcommit: 54c07ffcfe0da286b1780fdc03ba2f2fd0dbc86d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2019
ms.locfileid: "34404215"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>混合式新式驗證概觀及使用商務和 Exchange 伺服器內部部署用 Skype 的必要條件

新式驗證是一種方法提供更安全的使用者驗證及授權的身分識別管理。 使用 Office 365 混合式部署的 Skype for Business server 內部部署和 Exchange server 內部部署，以及，分割網域 Skype for Business 混合。 此文章連結至相關的文件有關先決條件，安裝程式/停用新式驗證，和某些相關的用戶端 （例如。 Outlook 與 Skype 用戶端） 的資訊。 
  
- [什麼是新式驗證？](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [有什麼變更時使用新式驗證嗎？](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [檢查您的內部部署環境的新式驗證狀態](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [您符合新式驗證必要條件嗎？](#do-you-meet-modern-authentication-prerequisites)
    
- [我需要知道開始前什麼？](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [新式驗證 Url 清單](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>什麼是新式驗證？
<a name="BKMK_WhatisModAuth"> </a>

當談論 （例如，您的膝上型電腦或手機） 的用戶端與伺服器之間的通訊，Microsoft 會使用片語 '新式驗證'。
  
新式驗證是組合的驗證和授權方法，以及某些依賴存取原則，您可能已經熟悉的安全性措施雨傘字詞。 其中包括：
  
- **驗證方法**： 多重要素驗證;用戶端憑證型驗證。
    
- **授權方法**： Open Authorization (OAuth) 的 Microsoft 實作。 
    
- **條件式存取原則**： 行動應用程式管理 (MAM) 和 Azure Active Directory 條件式存取。 
    
管理使用者身分識別與新式驗證可讓系統管理員使用談到保護資源，提供更安全的身分識別管理這兩個內部 （Exchange 和商務用 Skype） 方法時，請 Exchange 混合式許多不同的工具與 Skype for Business 混合/分割網域案例。
  
請注意，因為與 Exchange 密切商務用 Skype，登入行為 Skype，使用者會看到的商務用戶端將會受到 Exchange 的新式驗證狀態。 如果您有分割網域混合式商務用 Skype 時，這也會套用。 此外，支援使用新式驗證混合式商務用 Skype 的類型通常稱為 '分割網域' （分割網域中有商務用 Skype 和 Skype for Business 上內部部署和使用者皆位於這兩個位置）。
  
> [!IMPORTANT]
> 您知道的 2017 年 8 月起所有新的 Office 365 承租人，包括商務用 Skype online 和 Exchange online 將有預設啟用新式驗證嗎？ 既有的租用戶不需要變更其預設 MA 的狀態，但所有的新租用戶自動支援擴充一組身分識別功能看上面所列。 若要檢查 MA 狀態的商務用 Skype online，您可以使用 Skype 商務 online powershell，以全域系統管理員認證。 執行`Get-CsOAuthConfiguration`若要檢查的-ClientADALAuthOverride 輸出。 如果-ClientADALAuthOverride '允許' 您新式驗證是上。 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>有什麼變更時使用新式驗證嗎？
<a name="BKMK_WhatChanges"> </a>

當使用內部部署用 Skype 的新式驗證商務或 Exchange 伺服器，您仍*驗證*內部使用者，但*授權*的本文資源 （如檔案或電子郵件） 變更其存取。 這就是為什麼，但是新式驗證是關於用戶端和伺服器通訊期間 evoSTS (Security Token Service 使用 Azure AD) 中設定 MA 結果所採取的步驟正在 skype for Business 和 Exchange server 內部部署設定為驗證伺服器。 
  
EvoSTS 變更可讓您在內部伺服器，以利用授權您的用戶端，OAuth （token 發行），也可讓您在內部使用安全性方法一般在雲端 （例如多重要素驗證）。 此外，evoSTS 發出 token，可讓使用者不需為要求的一部分提供其密碼要求資源的存取權。 無論位於您的使用者 (online 或內部)，無論哪一個位置主控所需的資源，EvoSTS 會成為核心設定新式驗證之後，授權使用者和用戶端。
  
以下是範例我所代表的意義。 如果商務用 Skype 商務用戶端需要存取 Exchange 伺服器來取得代表使用者的行事曆資訊時，它會使用 Active Directory Authentication Library (ADAL) 若要這麼做。 ADAL 的程式碼庫旨在讓您的目錄中的安全的資源可供用戶端應用程式使用 OAuth 安全性權杖。 若要確認宣告並交換權杖 （而非密碼），以授與使用者資源的存取權的 oauth 的 ADAL 運作。 在過去，像這樣-知道如何驗證使用者宣告和發行的所需的權杖伺服器--在交易中的授權單位可能已經被 Security Token Service 內部或甚至是 Active Directory Federation Services。 不過，新式驗證可以集中與 Azure Active Directory (Azure AD)，在雲端中的授權單位。
  
這也表示，即使您的 Exchange 伺服器與 Skype for Business 環境可能完全內部部署、 授權伺服器將會在線上，且您的內部部署環境必須建立和維護您的 Office 的連線能力在雲端 （和作為其目錄會使用您的訂閱的 Azure Active Directory 執行個體） 的 365 訂用帳戶。
  
什麼不會變更？ 無論您是在分割網域混合式或使用 Skype for Business 和 Exchange server 內部部署中，所有使用者必須先都驗證*內部部署*。 在混合式實作中的新式驗證，Lyncdiscovery 和自動探索指向您的內部部署伺服器。 
  
> [!IMPORTANT]
> 如果您需要瞭解商務拓撲支援 MA 特定商務用 Skype，這是[記載在這裡](https://technet.microsoft.com/en-us/library/mt803262.aspx)。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>檢查您的內部部署環境的新式驗證狀態
<a name="BKMK_CheckStatus"> </a>

因為新式驗證變更服務利用 OAuth/S2S 時所使用的授權伺服器，您需要知道的新式驗證是否開啟或關閉您 skype for Business 和 Exchange 環境。 您可以藉由執行檢查針對商務伺服器，內部部署，在您的 Exchange 或 Skype 狀態`Get-CSOAuthConfiguration`在 PowerShell 命令。 如果該命令會傳回空的 'OAuthServers' 屬性，會停用的新式驗證。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>您符合新式驗證必要條件嗎？

確認，然後再繼續進行，請檢查清單關閉這些項目：
  
- **特定商務用 Skype**
    
  - 所有伺服器都必須 SFB Server 2015 CU5 或更新版本
    
  - **例外狀況**-生存能力 Branch Appliance (SBA) 便可位於目前版本 （根據 Lync 2013） 
    
  - SIP 網域會新增為 Office 365 中的同盟網域
    
  - 所有 SFB 前端都必須連線到網際網路，以 Office 365 驗證 Url (TCP 443) 輸出，而且熟知憑證根目錄 Crl (TCP 80) 會列出列 56 和 125 的[[Microsoft 365 一般及 Office Online] 區段中，Office 365 Url 和 IP位址範圍](urls-and-ip-address-ranges.md)。
  
- **商務用 Skype 內部部署混合式 Office 365 環境中**
  - 具有執行 Skype for Business Server 2019 的所有伺服器的商務 Server 2019 部署商務用 Skype。
  
  - 用 Skype Server 2015 部署與執行用 Skype Server 2015 的所有伺服器。
  
  - 最多兩個不同的伺服器版本，如下所示的部署：
  
     - Skype for Business Server 2015 與 Skype for Business Server 2019
     
  - 所有 Skype for Business 伺服器必須已安裝最新的 cummulative 更新，請參閱[Skype for Business Server 更新](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)若要尋找與管理所有可用的更新。
  - 沒有任何 Lync Server 2010 或 2013 混合式環境中。
    
 **附註**如果您 Skype for Business 前端伺服器使用的網際網路存取 proxy 伺服器，必須在 [設定] 區段中的每個前端的 web.config 檔案中輸入 proxy 伺服器 IP 和連接埠號碼使用。 
  
- 針對 Business Server 2015\Web Components\Web C:\Program Files\Skype ticket\int\web.config
    
- 針對 Business Server 2015\Web Components\Web C:\Program Files\Skype ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> 請務必訂閱 rss 摘要，讓[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)保持最新的最新清單的所需的 Url。 
  
- **特定的 Exchange 伺服器**
    
  - 您使用 [Exchange server 2013 CU19 和 up，或 Exchange server 2016 CU8 及設定。
    
  - 沒有任何 Exchange server 2010 環境中。
    
  - 未設定 SSL 卸載。 支援 SSL 終止並重新加密。
    
  - 事件中您的環境使用 proxy 伺服器基礎結構，以允許伺服器進行連線到網際網路，請務必在所有 Exchange 伺服器都有[InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx)屬性中所定義的 proxy 伺服器。
  
- **Exchange Server 內部部署混合式 Office 365 環境中**

  - 如果您使用 Exchange server 2013，至少一部伺服器必須已安裝 Mailbox 和 Client Access server role。 雖然可以在個別伺服器上安裝 Mailbox 和 Client Access role，我們強烈建議您安裝在每個伺服器，以提供額外的可靠性與效能改進這兩種角色。
  
  - 如果您使用 Exchange server 2016 或更新版本，至少一部伺服器必須已安裝 Mailbox server role。
  
  - 沒有任何 Exchange server 2007 或 2010 混合式環境中。
  
  - 所有 Exchange 伺服器必須已安裝最新的 cummulative 更新，請參閱[將 Exchange 升級至最新的累計更新](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)若要尋找與管理所有可用的更新。
    
- **Exchange 用戶端和通訊協定需求**
  
  - 下列用戶端支援新式驗證：

  |**用戶端**|**主要的通訊協定**|**附註**|
  |:-----|:-----|:-----|
  |Outlook 2013 與 Outlook 2016  <br/> |MAPI over HTTP  <br/> |必須在 Exchange 中啟用 MAPI over HTTP，才能使用這些用戶端 （通常是已啟用或則為 True 的新安裝的 Exchange 2013 Service Pack 1 和上方）; 利用新式驗證如需詳細資訊請參閱 < <b0>Office 2013 和 Office 2016 用戶端應用程式的方式新式驗證運作</b0>。  <br/> 確定您正在執行的 Outlook; 最小必要的建置請參閱 <<c0>使用 Windows Installer (MSI) 的 Outlook 版本的最新更新。  <br/> |
  |Mac 版 Outlook 2016  <br/> |Exchange Web 服務  <br/> |  <br/> |
  |Outlook for iOS 和 Android  <br/> |  <br/> |如需詳細資訊，請參閱[使用混合式新式驗證與 Outlook for iOS 和 Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。  <br/> |
  |Exchange ActiveSync 用戶端 (例如 iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |對於支援新式驗證的 Exchange ActiveSync 用戶端，必須重新建立設定檔，以便從基本驗證切換至新式驗證。  <br/> |

- **一般的必要條件**
    
  - 如果您使用 ADFS，您應該會有 Windows 2012 R2 ADFS 3.0 及以上進行同盟
    
  - 您的身分識別組態是否有任何支援 AAD 連線的類型 (例如密碼雜湊同步處理，通過驗證，內部部署 Office 365 所支援的 STS，et cetera。)
    
  - 您需要 AAD 連線設定，並進行使用者複寫及同步處理正常運作。
    
  - 您已經驗證該混合式設定使用您的內部部署和 Office 365 環境之間的傳統 Exchange 混合式拓撲模式。 Exchange 混合式的正式支援陳述式會指出您必須有目前的 CU 或目前的 CU-1。
    
    > [!Note]
    > 使用[混合式代理程式](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)不支援混合式新式驗證。
    
  - 請確定這兩個內部部署測試使用者，如混合式測試使用者位於 Office 365 登入商務桌面用戶端 （如果您想要使用 Skype 的新式驗證） 用 Skype 和 Microsoft Outlook （如果您想要讓使用啟用新式驗證Exchange)。
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>我需要知道開始前什麼？
<a name="BKMK_Whatelse"> </a>

1. 內部伺服器上的所有案例牽涉都到新式驗證內部部署的設定 （事實上，如商務用 Skype 沒有支援拓撲的清單），以便將負責驗證和授權的伺服器中的 Microsoft Cloud （AAD 的安全性權杖服務，稱為 'evoSTS'），並更新 Azure Active Directory (AAD)，相關的 Url 或使用任一 Skype 基於商業或 Exchange 內部部署安裝的命名空間。 因此，在內部伺服器採用 Microsoft Cloud 相依性。 執行此動作無法被視為設定 '混合式驗證'。
    
2. 此文章的連結出給其他人可協助您選擇支援的新式驗證拓撲 （僅適用於商務用 Skype 的必要） 和相關文件的大綱設定步驟，或步驟，即可停用新式驗證，如 Exchange 內部部署與商務用 Skype 內部部署。 最愛此頁面在瀏覽器，如果您將需要首頁基底的伺服器環境中使用新式驗證。
    
## <a name="list-of-modern-authentication-urls"></a>新式驗證 Url 清單
<a name="BKMK_URLListforMA"> </a>

- [如何設定 Exchange Server 內部部署以使用新式驗證](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [商務用 Skype 的新式驗證與支援的商務拓撲](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [如何設定商務用 Skype 內部部署以使用新式驗證](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [從商務用 Skype 與 Exchange 移除或停用混合式新式驗證](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

