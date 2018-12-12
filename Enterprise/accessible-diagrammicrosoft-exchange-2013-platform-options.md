---
title: 存取圖表-Microsoft Exchange 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: 本文是圖表的名為 Microsoft Exchange 2013 平台選項，這是圖表的可在技術圖表可存取的文字版本。
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503126"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>存取圖表-Microsoft Exchange 2013 平台選項

**摘要：** 本文是圖表的名為 Microsoft Exchange 2013 平台選項，這是圖表的可在[技術圖表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)可存取的文字版本。
  
此海報說明 business decision makers (Bdm) 和架構師需要知道什麼有關 Exchange Online 與 Exchange Server 部署並包括： 
  
- Exchange 2013 的四個可用的平台選項的比較： Exchange Online (Office 365)、 Exchange 混合式 Exchange 伺服器上部署、 和 Provider-Hosted Exchange。 
    
- Exchange 2013 中的三種全新或更新功能的說明。 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>四個不同的部署的 Exchange 2013 平台的比較

比較提供下列區域中的每個部署] 選項的相關資訊： 
  
- 不同的部署功能的概觀 
    
- 實作每個部署選項的優點 
    
- 授權需求 
    
- 必要的架構工作 
    
- IT 專業人員責任實作每個部署選項 
    
### <a name="overview"></a>概觀

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

您的入侵效率並降低與 Office 365 的成本。
  
使用 Azure Active Directory 承租人以同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間隨附的圖表顯示 Exchange Online。Active Directory Federation Services (AD FS) 是必要的單一登入。 
  
功能和功用描述：
  
- 伺服器和伺服器軟體的作業是由 Microsoft 處理。
    
- 豐富型功能集的 Exchange Server 2013 以雲端架構服務。
    
- 永遠保持其最新的最新的功能。
    
- Exchange Online Protection (EOP) 是包含反-垃圾郵件/反惡意程式碼保護。
    
- 內建的高可用性與達 99.9%服務層級協議 (SLA)。
    
- 目錄同步作業包括內部部署 Active Directory 網域服務 (AD DS) 與 Azure Active Directory 租用戶之間的密碼。Active Directory Federation Services (AD FS) 是必要的單一登入。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

維護 Exchange Server 內部部署時，您可以運用 Office 365 的優點。
  
隨附的圖表顯示 Office 365 與 Exchange Online 其中某些使用者隸屬於內部部署，且某些使用者的主伺服器皆線上。它也會顯示 Azure Active Directory 承租人以同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間。
  
功能和功用描述：
  
- 某些使用者隸屬於內部部署和某些使用者的主伺服器皆線上，且使用者共用相同的電子郵件地址空間。
    
- 如何運用現有的 Exchange Server 基礎結構。
    
- 一段時間，在您的排程上，從 Exchange 內部部署移轉至 Exchange Online。
    
- 與其他 Office 365 應用程式，包括 Lync Online 和 SharePoint Online 的整合。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

您可以設計及管理自己的 Exchange Server 2013 基礎結構。
  
隨附的圖顯示內部部署 Active Directory 網域服務 (AD DS) 環境如果使用者是所隸屬於內部部署 Exchange Server 基礎結構。
  
功能和功用描述：
  
- 最大程度控制項及自訂設定的詳細資訊。
    
- 在維護工作階段親和性的負載平衡層在沒有相依性。
    
- 簡單高可用性和站台恢復使用資料庫可用性群組 (DAGs)。
    
- 受管理的可用性，可協助您更好的使用者經驗。
    
- 運用現有的硬體和存放區基礎結構。
    
#### <a name="provider-hosted-exchange"></a>提供者主控 Exchange

您可以將您的 Exchange Server 工作負載的 Exchange Server 解決方案提供者。
  
隨附圖 21vianet 且由供應商維護 Exchange Server 環境。
  
功能和功用描述：
  
- 伺服器和伺服器軟體的作業會處理您的提供者。
    
- 規劃、 大小、 縮放比例、 及維護 Exchange Server 基礎結構的委派給您的提供者。
    
- 服務維護會處理您的提供者。
    
- Exchange 功能集僅限於提供者所部署的軟體版本。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>實作每個部署選項的優點

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

此部署選項最適合的：
  
- 尋找以減少作業成本的內部部署組織的 Exchange 部署。
    
- 規劃利用其他 Office 365 方案，例如 SharePoint Online 與 Lync Online 的組織。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

此部署選項最適合的：
  
- 協助從 Exchange 內部部署移轉至 Exchange Online。
    
- 不含演變在分公司的基礎結構支援遠端站台。
    
- 與子公司需要資料至位於內部部署的跨國企業。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

此部署選項最適合的：
  
- 高度自訂的解決方案。
    
- 與協力廠商的項目都取決於硬體及軟體的元件不支援的 Exchange Online 的舊版方案。
    
- 組織主旨至需要至位於內部部署資料的資料控管規定。
    
- 想要保留控制整個平台和解決方案的組織。
    
#### <a name="provider-hosted-exchange"></a>提供者主控 Exchange

此部署選項最適合的：
  
- 需要 Exchange Server 功能，但想要將其部署及維護外包的組織。
    
- 需要個人化的支援選項的組織。
    
- 自訂的解決方案，以與提供者所提供的自訂應用程式整合。
    
- 與協力廠商的項目都取決於硬體及軟體的元件不支援的 Exchange Online 的舊版方案。
    
### <a name="license-requirements"></a>授權需求

下表詳細說明每個部署選項的授權需求。
  
|**部署選項**|**授權需求**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |訂閱模型  <br/> |
|Exchange 混合式  <br/> | Office 365-訂閱模型 <br/>  內部-所有內部部署授權套用 （檢閱授權交換伺服器內部部署） <br/>  混合伺服器授權 * <br/> |
|Exchange Server 內部部署  <br/> | 伺服器作業系統 <br/>  Exchange 2013 伺服器授權 <br/>  Exchange 2013 用戶端存取授權 <br/> |
|提供者主控 Exchange  <br/> |成本根據與提供者協議  <br/> |
   
### <a name="architecture-tasks"></a>架構工作

本節列出每個部署選項的架構工作。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 規劃及設計目錄同步作業。
    
- 確定網路容量和透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結的連線。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

除了 Office 365 與內部部署環境的架構工作：
  
- 決定是否要提供單一登入經驗。
    
- 決定是否要透過內部部署組織或 Exchange Online Protection 的輸入的網際網路郵件路由傳送。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

- 設計 Exchange 拓撲。
    
- 規劃伺服器硬體的容量。
    
- 設計郵件路由拓撲。
    
- 設計負載平衡的用戶端存取伺服器。
    
- 規劃高可用性使用資料庫可用性群組。
    
#### <a name="provider-hosted-exchange"></a>提供者主控 Exchange

確定網路容量和可用性透過防火牆、 proxy 伺服器、 閘道，且跨 WAN 連結可至提供者。
  
### <a name="it-pro-responsibilities"></a>IT 專業人員的責任

本節列出每個部署選項以 IT 專業人員的責任。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 實作目錄同步處理計劃。
    
- 規劃及實作內部和外部 DNS 記錄和路由。
    
- 設定 proxy 伺服器或防火牆的 Office 365 IP 位址及 URL 需求。
    
- 管理使用者帳戶和 Exchange Online 的設定。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

除了 Office 365 與內部部署環境的 IT 專業人員的責任：
  
- 設定單一登入的 Active Directory Federation Services (AD FS) 上，（若有需要）。
    
- 設定 Exchange 2013 伺服器與 Office 365 之間的安全通訊的 Exchange 憑證。
    
- 設定 DNS 記錄的所需的內送網際網路郵件路徑。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

- 設定 Exchange 服務所需的憑證。
    
- 佈建伺服器。
    
- 實作 Exchange 郵件路由拓撲。
    
- 實作資料庫可用性群組。
    
- 更新及維護 Exchange 伺服器。
    
- 根據使用率、 新增或移除伺服器所需。
    
#### <a name="provider-hosted-exchange"></a>提供者主控 Exchange

提供者的責任包括：
  
- 系統及服務維護。
    
- 功能部署。
    
- 資料保護和嚴重損壞修復。
    
在組織中的 IT 人員責任包括建立和管理使用者帳戶。
  
#### <a name="more-information"></a>詳細資訊

若要深入了解 Exchange Online (Office 365)，請參閱下列各項：
  
- [Exchange Online 服務說明](https://aka.ms/EXOSD)
    
- [TechNet 上的 Exchange Online 文件庫](https://aka.ms/EXOTN)
    
- [Exchange Online 的入口網站](https://aka.ms/EXO)
    
若要深入了解 Exchange 的混合，請參閱下列各項：
  
- [Exchange 2013 混合部署](https://aka.ms/ExchangeHybrid)。您應該注意的混合伺服器授權為只需要在下列情況： Exchange 2010 組織與 Exchange 2013 混合式伺服器和 Exchange 2007 組織與 Exchange 2013 或 Exchange 2010 混合伺服器。
    
- [Office 365 登入](https://aka.ms/HybridKey)
    
若要深入了解 Exchange Server 內部部署，請參閱下列各項：
  
- [TechNet 上的 Exchange Server 2013 文件庫](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013 入口網站](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013 架構](https://aka.ms/Ex2013SP1ArchPoster)
    
若要深入了解 Provider-Hosted Exchange，請參閱下列各項：
  
[Exchange Server 2013 主控與多重租用解決方案和指引](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Exchange 2013 中的三種全新或更新功能的說明

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) 提供任何部署的反垃圾郵件和反惡意程式碼的保護提供一層的部署跨資料中心的通用網路的保護功能。這有助於您簡化的訊息環境的管理。EOP 隨附於 Exchange Online 訂閱，但您也可以運用它混合式和內部部署。
  
隨附的圖表說明 Exchange Online、 Exchange 混合部署和部署的 Exchange 內部部署中通用網路包含 EOP 圖層。
  
### <a name="exchange-server-deployment-assistant"></a>Exchange Server 部署助理

Exchange Server 部署助理是 web 式工具，詢問您目前的環境的幾個問題，然後再產生自訂逐步檢查清單可協助您部署 Exchange Server 不同類型的案例。是否從舊版 Exchange 至 Exchange 2013 的升級、 移轉至 Exchange Online 或規劃混合式基礎結構 Exchange Server 部署助理會建立自訂的部署檢查表您的案例。
  
隨附的螢幕擷取畫面顯示使用 Exchange Server 部署助理建立範例檢查清單。
  
### <a name="integration-with-lync-and-sharepoint"></a>與 Lync 和 SharePoint 整合

Exchange Server 2013 包含整合 Lync Server 2013 與 SharePoint Server 2013 的許多功能。在一起，這些產品提供一組豐富型功能並提升整個組織共同作業。 
  
隨附的圖表顯示伺服器對伺服器驗證海報並包含海報的連結。 
  
- 封存、 保留和 eDiscovery
    
- 網站信箱
    
- 整合聯絡資料儲存
    
- 高解析度的使用者相片
    
- Outlook 和 Outlook Web App 中的 Lync 顯示狀態
    
- 伺服器對伺服器驗證
    
- 語音信箱
    
- 會議錄製
    
- Exchange 工作同步處理
    
隨附的圖表顯示 Exchange Server 2013 SP1 架構海報 （英文） 並包含海報的連結。
  

