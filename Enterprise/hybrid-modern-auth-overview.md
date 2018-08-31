---
title: 經過驗證的混合式概觀及使用內部部署 Skype 中的商務與 Exchange 伺服器的先決條件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: 現代驗證是一種方法提供較安全的使用者驗證和授權的身分識別管理。使用混合式部署的 Skype Business server 內部部署與 Exchange server 內部部署，以及商務混合的分隔網域 Skype。本文章的連結與相關文件需安裝程式/停用經過驗證的必要條件以及部分相關的用戶端 （例如 Outlook 和 Skype 用戶端） 資訊。
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240588"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>經過驗證的混合式概觀及使用內部部署 Skype 中的商務與 Exchange 伺服器的先決條件

現代驗證是一種方法提供較安全的使用者驗證和授權的身分識別管理。使用 Office 365 的 Skype 的混合式部署 Business server 內部部署和 Exchange server 內部部署，以及、 商務混合的分隔網域 Skype。本文章的連結與相關文件需安裝程式/停用經過驗證的必要條件以及部分相關的用戶端 （例如 Outlook 和 Skype 用戶端） 資訊。 
  
- [什麼是經過驗證？](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [有什麼變更時使用經過驗證？](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [檢查您的內部部署環境的現代驗證狀態](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [您符合經過驗證的必要條件嗎？](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [我需要知道開始前還有什麼？](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [現代驗證 Url 清單](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>什麼是經過驗證？
<a name="BKMK_WhatisModAuth"> </a>

當談論 （例如膝上型電腦或您的電話） 的用戶端與伺服器之間的通訊，Microsoft 會使用片語 '現代驗證 」。
  
現代驗證是雨傘字詞的驗證和授權方法以及依賴存取原則可能熟悉的一些安全性量值的組合。包含：
  
- **驗證方法**： 多重要素驗證 ；用戶端憑證型驗證 ；與 Active Directory 驗證文件庫 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。
    
- **授權方法**： Microsoft 的實作 Open Authorization (OAuth)。 
    
- **設定格式化的條件存取原則**： 行動應用程式管理 」 (MAM) 和 Azure Active Directory 設定格式化的條件存取。 
    
管理使用經過驗證的使用者身分識別提供系統管理員使用它可保護資源並提供更安全的身分識別管理這兩個內部部署 （Exchange 和 Skype for Business） 方法時，Exchange 混合式許多不同的工具和 Skype 商務混合/分割網域案例。
  
請注意與 Exchange 密切合作 Skype for Business，因為使用者會看到的商務用戶端登入行為 Skype 將會受到 Exchange 摩登的驗證狀態。這也會套用如果您有商務分隔網域混合式的 Skype。此外，Skype 支援使用經過驗證的商務混合式的類型通常稱為 「 分割網域 」 （在分隔網域中具有商務 online Skype 和 Skype 的業務上-prem 和使用者皆位於兩個位置）。
  
 **重要**您知道 2017 年 8 月、 年所有新 Office 365 租用戶的線上包括 Skype for Business 和 Exchange online 會有預設啟用的現代驗證嗎？既承租人不會有變更其預設 MA 的狀態，但所有新的租用戶自動支援擴充的功能集的識別您看到以上所列。若要線上檢查 for Business Skype MA 狀態，您可以使用 Skype 商務 powershell online 以全域管理員認證。執行 'Get-csoauthconfiguration' 檢查-ClientADALAuthOverride 的輸出。若啟用-ClientADALAuthOverride 則' ' 摩登的驗證是上。 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>有什麼變更時使用經過驗證？
<a name="BKMK_WhatChanges"> </a>

使用時經過驗證的內部 Skype 商務或 Exchange server，您還是*驗證*使用者內部部署，但的*授權*由來資源 （例如檔或電子郵件） 變更其存取。這是為何，但是現代驗證需用戶端和伺服器通訊時 evoSTS (Security Token Service 使用 Azure AD) 中設定 MA 結果所採取的步驟是要設為 [驗證伺服器 Skype 的業務與 Exchange server 的內部。 
  
EvoSTS 變更可讓您在內部伺服器的授權您的用戶端充分運用 OAuth （token 發行） 和也可讓您在內部使用安全性方法一般在雲端 （例如多重要素驗證）。此外，evoSTS 問題允許使用者而不提供其密碼的要求一部分要求資源的存取權的 token。不論隸屬使用者 (online 或內部部署)，與位置裝載所需的資源，不論 EvoSTS 會成為的授權使用者與用戶端設定現代驗證之後核心。
  
以下是範例我的意義。如果 Skype 商務用戶端的需求來存取取得代表使用者的行事曆資訊的 Exchange server，它會使用 Active Directory 驗證文件庫 (ADAL) 若要這樣做。ADAL 的程式碼庫設計您的目錄中可供用戶端應用程式使用 OAuth 安全性權杖進行安全的資源。若要確認宣告並交換權杖 （而非密碼）、 授與使用者存取資源的 OAuth 與 ADAL works。過去在類似這一個-知道如何驗證使用者宣告及問題所需的權杖伺服器--在交易中的授權單位可能已 Security Token Service 內部或甚至是 Active Directory Federation Services。不過，現代驗證可集中與 Azure Active Directory (Azure AD)，雲端中的授權單位。
  
這也表示，即使您的 Exchange server 和 Skype 的商務環境可能完全內部部署、 授權伺服器會成為 online 和內部部署環境必須建立及維護您的 Office 的連線能力在雲端 （與您的訂閱使用作為其目錄的 Azure Active Directory 執行個體） 的 365 訂閱。
  
項目不會變更？無論您是在分隔網域混合式或使用 Skype 的業務與 Exchange server 內部部署中，所有使用者必須先進行都驗證*的內部*。在經過驗證的混合式實作、 Lyncdiscovery 和自動探索指向內部伺服器。 
  
 **重要**如果您需要知道特定 Skype 商務拓撲支援 MA，這是[記載以下右邊](https://technet.microsoft.com/en-us/library/mt803262.aspx)。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>檢查您的內部部署環境的現代驗證狀態
<a name="BKMK_CheckStatus"> </a>

因為現代驗證變更服務運用 OAuth/S2S 時所使用的授權伺服器，您需要知道經過驗證的業務與 Exchange 環境您 Skype 是否是開啟或關閉。您可以在 PowerShell 中執行 Get-csoauthconfiguration 命令來檢查商務伺服器，在內部部署，Exchange 或 Skype 上的狀態。如果此命令會傳回空的 'OAuthServers' 屬性、 現代驗證已停用。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>您符合經過驗證的必要條件嗎？

確認，然後再繼續檢查您的清單關閉這些項目：
  
- **針對 Business 特定 Skype**
    
  - 所有伺服器都必須 SFB Server 2015 CU5 或更新版本
    
  - **例外狀況**-生存能力 Branch Appliance (SBA) 可位於目前的版本 （根據 Lync 2013） 
    
  - SIP 網域會新增為 Office 365 中的同盟網域
    
  - 所有 SFB 前端都必須連線至網際網路，Office 365 驗證 Url (TCP 443) 和熟知憑證根 Crl (TCP 80) 撥出的列 1 及 2 的[Office 365 Url 和 IP 的 'Office 365 驗證及身分識別 」 一節中列出處理範圍](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E)。
    
 **附註**如果您 Skype 商務前端伺服器用於網際網路存取 proxy 伺服器，必須輸入 proxy 伺服器 IP 和連接埠號碼用在 [設定] 區段中的每個前端的 web.config 檔案中。 
  
- 針對 Business Server 2015\Web Components\Web ticket\int\web.config c:\program files\Skype
    
- 針對 Business Server 2015\Web Components\Web ticket\ext\web.config c:\program files\Skype
    
- \</system.identityModel.services\>
    
     \<system.net\> 
    
     \<defaultProxy\> 
    
     \<proxy 
    
     proxyaddress ="http://192.168.100.60:8080" 
    
     bypassonlocal ="true" 
    
     /\> 
    
     \</defaultProxy\> 
    
     \</system.net\> 
    
    \</configuration\>
    
 **重要**請務必以訂閱 RSS 摘要的[Office 365 Url 和 IP 位址範圍](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)保持最新的 Url 所需的最新的清單。 
  
- **特定的 Exchange Server**
    
  - 您使用 [Exchange server 2013 CU19 和，或 Exchange server 2016 CU8 及向上。
    
  - 在環境中的沒有 Exchange server 2010。
    
  - 未設定 SSL 卸載。支援 SSL 終止並重新加密。
    
  - 事件中您的環境使用 proxy 伺服器基礎結構，以允許伺服器進行連線到網際網路，請確定所有 Exchange 伺服器都已[InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)屬性中所定義的 proxy 伺服器。
    
- **Exchange 用戶端和通訊協定需求**
  
  - 下列用戶端支援現代驗證：

  |**用戶端**|**主要的通訊協定**|**附註**|
  |:-----|:-----|:-----|
  |Outlook 2013 與 Outlook 2016  <br/> |MAPI over HTTP  <br/> |MAPI over HTTP 必須啟用 Exchange 內才能並用摩登的驗證與這些用戶端 （通常被啟用或新安裝 Exchange 2013 Service Pack 1 和上方則為 True） ；如需詳細資訊請參閱 ＜ [Office 2013 與 Office 2016 用戶端應用程式如何經過驗證的運作](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)。  <br/> 確定您正在執行 Outlook; 最小必要的建置請參閱[的 Outlook 會使用 Windows Installer (MSI) 版本的最新更新](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)。  <br/> |
  |Outlook 2016 for Mac  <br/> |Exchange Web 服務  <br/> |  <br/> |
  |Outlook for iOS 和 Android  <br/> |  <br/> |如需詳細資訊，請參閱[使用 hybrid 現代 Authentication with Outlook iOS 及 android （英文）](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。  <br/> |
  |Exchange ActiveSync 用戶端 （例如 iOS11 郵件）  <br/> |Exchange ActiveSync  <br/> |支援經過驗證的 Exchange ActiveSync 用戶端，則必須重新設定檔建立以從基本驗證切換至經過驗證。  <br/> |

- **一般的先決條件**
    
  - 如果您使用 ADFS，您應該會有 Windows 2012 R2 ADFS 3.0 及以上的同盟
    
  - 您的身分識別設定是否有任何支援 AAD 連線的類型 (例如密碼雜湊同步處理、 通過驗證內部部署 Office 365 所支援的 STS，et cetera。)
    
  - 您必須 AAD 連線設定且運作的使用者複寫及同步處理。
    
  - 確認該混合使用內部部署和 Office 365 之間：
    
  - Exchange 混合式的正式支援陳述式會指出您必須具備目前 CU 或目前 CU-1。
    
  - 請確定這兩個內部部署測試使用者，如混合測試使用者隸屬於 Office 365 登入 Skype 商務桌面用戶端 （如果您想要使用經過驗證與 Skype） 及 Microsoft Outlook （如果您想要讓使用經過驗證Exchange)。
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>我需要知道開始前還有什麼？
<a name="BKMK_Whatelse"> </a>

1. 內部部署伺服器的所有案例都包含經過驗證的內部設定 （事實上，如 Skype for Business 有支援的清單） 使負責驗證和授權的伺服器位於 Microsoft Cloud （AAD 的 security token service、 呼叫 'evoSTS')，並更新 Azure Active Directory (AAD)，相關的 Url 或內部部署安裝的其中一個 Skype 商務或 Exchange 所使用的命名空間。因此，在內部伺服器會採用 Microsoft Cloud 相依性。利用此動作無法被視為設定 '混合式驗證 」。
    
2. 本文章的連結取出給其他人可協助您選擇支援現代驗證拓撲 （僅適用於企業版 Skype 的必要），與使用方法文章該大綱的設定步驟，或 Exchange 內部可停用現代驗證步驟與 Skype 企業內部。最愛在瀏覽器如果您將需要在您的伺服器環境中使用經過驗證的常用基底些此頁面。
    
## <a name="list-of-modern-authentication-urls"></a>現代驗證 Url 清單
<a name="BKMK_URLListforMA"> </a>

- [如何設定 Exchange Server 內部使用經過驗證](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Skype 現代驗證支援的商務拓撲](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [如何設定為使用經過驗證的企業內部 Skype](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [從商務用 Skype 與 Exchange 移除或停用混合式新式驗證](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

