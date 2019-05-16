---
title: 易於存取的圖表-Microsoft Exchange 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: 本文是圖表的名為 Microsoft Exchange 2013 平台選項，這是圖表的可在技術圖表易於存取的文字版本。
ms.openlocfilehash: ddf215544b811257e6d43f212784a3a1e5aac7b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068589"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>易於存取的圖表-Microsoft Exchange 2013 平台選項

**摘要：** 本文是圖表的名為 Microsoft Exchange 2013 平台選項，這是圖表的可在[技術圖表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)易於存取的文字版本。
  
此海報描述商務決策者 (Bdm) 和結構設計師需要了解 Exchange Online 和 Exchange Server 部署，項目，並包括： 
  
- Exchange 2013 的四個可用的平台選項的比較： Exchange Online (Office 365)、 Exchange 混合式時，Exchange 伺服器上部署、 和 Provider-Hosted Exchange。 
    
- Exchange 2013 中的三個新的或更新功能的描述。 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>四個不同的部署的 Exchange 2013 平台的比較

比較提供下列項目的每個部署選項的相關資訊： 
  
- 不同的部署功能的概觀 
    
- 實作每個部署選項的優點 
    
- 授權需求 
    
- 必要的架構工作 
    
- IT 專業人員負責實作每個部署選項 
    
### <a name="overview"></a>概觀

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

您取得效率，並減少成本，以及 Office 365。
  
隨附圖表顯示 Exchange Online 與 Azure Active Directory 租用戶的帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境與 Azure Active Directory 租用戶之間會同步處理。 Active Directory Federation Services (AD FS) 是必要的單一登入。 
  
描述的特性與功能：
  
- 伺服器和伺服器軟體的作業是由 Microsoft 處理。
    
- 豐富型功能集的 Exchange Server 2013 作為雲端式服務。
    
- 保持最新的最新功能。
    
- Exchange Online Protection (EOP) 會包含反-垃圾郵件/反惡意程式碼保護。
    
- 高達 99.9%的內建高可用性服務層級協議 (SLA)。
    
- 目錄同步作業包括內部部署 Active Directory 網域服務 (AD DS) 與 Azure Active Directory 租用戶之間的密碼。 Active Directory Federation Services (AD FS) 是必要的單一登入。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

您可以利用 Office 365 的優點，同時維持 Exchange Server 內部部署。
  
隨附圖表顯示 Office 365 與 Exchange Online 其中部分使用者為隸屬於內部部署，以及某些使用者位於線上。 它也會顯示 Azure Active Directory 承租人以帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境與 Azure Active Directory 租用戶之間會同步處理。
  
描述的特性與功能：
  
- 部分使用者位於的內部和部分使用者位於線上，且使用者共用相同的電子郵件地址空間。
    
- 運用現有的 Exchange 伺服器基礎結構。
    
- 經過一段時間，在您的排程上，從 Exchange 內部部署移轉至 Exchange Online。
    
- 與其他 Office 365 應用程式，包括 Lync Online 和 SharePoint Online 整合。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

您可以設計及管理自己的 Exchange Server 2013 基礎結構。
  
隨附圖顯示內部部署 Active Directory 網域服務 (AD DS) 環境使用者所在位置，位於的內部部署 Exchange 伺服器基礎結構。
  
描述的特性與功能：
  
- 最大程度的控制項及自訂設定。
    
- 沒有項目相依於維護工作階段親和性負載平衡層級。
    
- 簡單高可用性和站台恢復使用資料庫可用性群組 (Dag)。
    
- 受管理的可用性，可協助您維護良好的使用者經驗。
    
- 利用現有的硬體和儲存體基礎結構。
    
#### <a name="provider-hosted-exchange"></a>提供者裝載的 Exchange

您可以將您的 Exchange 伺服器工作負載至 Exchange Server 解決方案提供者。
  
隨附圖是運作並提供者所維護的 Exchange Server 環境。
  
描述的特性與功能：
  
- 伺服器和伺服器軟體的作業會處理您的提供者。
    
- 規劃、 大小、 縮放比例，以及 Exchange 伺服器基礎結構的維護被委派給您的提供者。
    
- 服務維護是由您的提供者處理。
    
- Exchange 功能集僅限於部署您的提供者的軟體版本。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>實作每個部署選項的優點

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

此部署選項最適合的：
  
- 組織可以減少作業成本，內部部署 Exchange 部署。
    
- 若要利用其他 Office 365 方案，例如 SharePoint Online 和 Lync Online 計劃的組織。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

此部署選項最適合的：
  
- 促進從 Exchange 內部部署移轉至 Exchange Online。
    
- 不含投資分公司的基礎結構支援遠端站台。
    
- 與需要資料至位於內部部署的分公司的跨國企業。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

此部署選項最適合的：
  
- 高度自訂的解決方案。
    
- 具有協力廠商元件，取決於硬體和軟體不支援的 Exchange Online 的舊版解決方案。
    
- 組織遭到需要至位於內部部署資料的資料控管法規。
    
- 想要保留整個平台與解決方案的控制的組織。
    
#### <a name="provider-hosted-exchange"></a>提供者裝載的 Exchange

此部署選項最適合的：
  
- 需要 Exchange 伺服器功能，但想要將其部署及維護的組織。
    
- 需要個人化的支援選項的組織。
    
- 自訂的解決方案，提供者所提供的自訂應用程式整合。
    
- 具有協力廠商元件，取決於硬體和軟體不支援的 Exchange Online 的舊版解決方案。
    
### <a name="license-requirements"></a>授權需求

下表詳述每個部署選項的授權需求。
  
|**部署選項**|**授權需求**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |訂閱模型  <br/> |
|Exchange 混合式  <br/> | Office 365-訂閱模型 <br/>  內部部署的所有內部部署授權套用 （檢閱授權交換伺服器內部部署） <br/>  混合式伺服器授權 * <br/> |
|Exchange Server 內部部署  <br/> | 伺服器作業系統 <br/>  Exchange 2013 伺服器授權 <br/>  Exchange 2013 用戶端存取授權 <br/> |
|提供者裝載的 Exchange  <br/> |成本根據提供者合約  <br/> |
   
### <a name="architecture-tasks"></a>架構工作

此章節將列出每個部署選項的架構工作。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 規劃及設計的目錄同步處理。
    
- 請確定網路容量和透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結的連線。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

除了 Office 365 與內部部署環境的架構工作：
  
- 決定是否要提供單一登入經驗。
    
- 決定是否要路由傳送內送的網際網路郵件透過內部部署組織或 Exchange Online Protection。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

- 設計 Exchange 拓撲。
    
- 規劃伺服器硬體容量。
    
- 設計郵件路由拓撲。
    
- 設計負載平衡的 Client Access server。
    
- 規劃高可用性使用資料庫可用性群組。
    
#### <a name="provider-hosted-exchange"></a>提供者裝載的 Exchange

確保網路容量和透過防火牆、 proxy 伺服器、 閘道、 可用性及跨 WAN 連結可用於您的提供者。
  
### <a name="it-pro-responsibilities"></a>IT 專業人員的責任

此章節將列出每個部署選項的 IT 專業人員的責任。
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- 實作目錄同步處理計劃。
    
- 規劃及實作內部和外部 DNS 記錄和路由。
    
- 設定 proxy 伺服器或防火牆的 Office 365 IP 位址和 URL 需求。
    
- 管理使用者帳戶與 Exchange Online 設定。
    
#### <a name="exchange-hybrid"></a>Exchange 混合式

除了 Office 365 與內部部署環境的 IT 專業人員的職責：
  
- （如有需要），請在設定單一登入的 Active Directory Federation Services (AD FS)。
    
- 設定 Exchange 憑證的 Exchange 2013 伺服器與 Office 365 之間的安全通訊。
    
- 設定 DNS 記錄所需的內送網際網路郵件路徑。
    
#### <a name="exchange-server-on-premises"></a>Exchange Server 內部部署

- 設定必要的憑證，如 Exchange 服務。
    
- 佈建伺服器。
    
- 實作 Exchange 郵件路由拓撲。
    
- 實作資料庫可用性群組。
    
- 更新及維護的 Exchange 伺服器。
    
- 根據使用率，新增或移除伺服器，視需要。
    
#### <a name="provider-hosted-exchange"></a>提供者裝載的 Exchange

提供者的責任包括：
  
- 系統及服務維護。
    
- 功能發行。
    
- 資料保護和嚴重損壞修復。
    
在您的組織中的 IT 人員的職責包括建立及管理使用者帳戶。
  
#### <a name="more-information"></a>詳細資訊

若要深入了解 Exchange Online (Office 365)，請參閱下列各項：
  
- [Exchange Online 服務說明](https://aka.ms/EXOSD)
    
- [TechNet 上的 Exchange Online 文件庫](https://aka.ms/EXOTN)
    
- [Exchange Online 的入口網站](https://aka.ms/EXO)
    
若要深入了解 Exchange 混合式，請參閱下列各項：
  
- [Exchange 2013 混合式部署](https://aka.ms/ExchangeHybrid)。 您應該注意的混合式伺服器授權只有下列案例所需： Exchange 2013 混合式伺服器與 Exchange 2007 組織與 Exchange 2013 或 Exchange 2010 混合伺服器的 Exchange 2010 組織。
    
- [Office 365 登入](https://aka.ms/HybridKey)
    
若要深入了解關於 Exchange Server 內部部署的詳細資訊，請參閱下列：
  
- [TechNet 上的 Exchange Server 2013 文件庫](https://aka.ms/Ex2013TN)
    
- [Exchange Server 2013 入口網站](https://aka.ms/Exchange2013)
    
- [Exchange Server 2013 架構](https://aka.ms/Ex2013SP1ArchPoster)
    
若要深入了解 Provider-Hosted Exchange，請參閱下列各項：
  
[Exchange Server 2013 主控與多重租用解決方案和指引](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Exchange 2013 中的三個新的或更新功能的描述

### <a name="exchange-online-protection"></a>Exchange Online Protection

Exchange Online Protection (EOP) 提供任何部署的反垃圾郵件和反惡意程式碼的保護藉由提供一層的部署跨資料中心全球網路的保護功能。 這可協助您簡化您的郵件環境的管理。 EOP 隨附於 Exchange Online 訂閱，但您也可以利用它用於混合式和內部部署。
  
隨附的圖表顯示 Exchange Online、 Exchange 混合式部署和部署的 Exchange 內部部署中，包含 EOP 層全球網路。
  
### <a name="exchange-server-deployment-assistant"></a>Exchange Server 部署助理

Exchange Server 部署助理是 web 型的工具，詢問您一些問題有關您目前的環境，然後再產生自訂的逐步檢查清單，以協助您部署 Exchange 伺服器的不同類型的案例。 是否要從舊版的 Exchange 至 Exchange 2013 移轉，移轉至 Exchange Online，或規劃混合式基礎結構中，Exchange Server 部署助理會建立自訂的部署檢查清單，方便您的案例。
  
隨附的螢幕擷取畫面顯示已建立使用 Exchange Server 部署助理範例檢查清單。
  
### <a name="integration-with-lync-and-sharepoint"></a>與 Lync 和 SharePoint 整合

Exchange Server 2013 包含許多整合 Lync Server 2013 和 SharePoint Server 2013 的功能。 在一起，這些產品提供一組豐富型功能，並改善您的組織間的共同作業。 
  
隨附的圖表顯示伺服器對伺服器驗證海報，並包括海報的連結。 
  
- 封存、 保留和 eDiscovery
    
- 網站信箱
    
- 整合聯絡資料儲存
    
- 高解析度的使用者相片
    
- 在 Outlook 和 Outlook Web App 中呈現的 lycn
    
- 伺服器對伺服器驗證
    
- 語音信箱
    
- 會議錄製
    
- Exchange 工作同步處理
    
隨附的圖表顯示 Exchange Server 2013 SP1 架構海報，並包括海報的連結。
  

