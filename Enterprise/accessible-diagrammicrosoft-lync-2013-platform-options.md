---
title: 存取圖表-Microsoft Lync 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在技術圖表可存取的文字版本。
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504086"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>存取圖表-Microsoft Lync 2013 平台選項

**摘要：** 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在[技術圖表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)可存取的文字版本。
  
此海報說明 business decision makers (Bdm) 和架構師需要知道什麼有關 Lync Online (Office 365) 和 Lync Server 部署並包括：
  
- 四個不同的部署選項的比較： Lync Online (Office 365)、 Lync Online/伺服器混合 Lync Server 和 Provider-Hosted Lync Server。 
    
- 部署 Lync 2013 的兩個範例案例。
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>四個不同的部署的 Lync 2013 平台的比較

比較提供下列區域中的每個部署] 選項的相關資訊： 
  
- 不同的部署功能的概觀
    
- 實作每個部署選項的優點
    
- 授權需求
    
- 必要的架構工作
    
- IT 專業人員責任實作每個部署選項
    
### <a name="overview"></a>概觀

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

您的入侵效率和最佳化的 Office 365 multitenant 計劃的成本。
  
隨附圖 Lync Online 搭配 Azure Active Directory 承租人，以同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間。 
  
功能和功用描述：
  
- 軟體即服務 (SaaS)。
    
- 豐富型功能永遠是最新的設定。
    
- 包括可與其他應用程式的線上帳戶的 Azure Active Directory 租用戶。 
    
- 目錄整合包括同步處理帳戶名稱和密碼的內部部署 Active Directory 網域服務 (AD DS) 環境及 Azure Active Directory 租用戶之間。
    
- 如果單一登入 (SSO) 是需求，就必須實作 Active Directory Federation Services (AD FS)。 
    
- 透過網際網路的用戶端通訊會加密及驗證。
    
- 舊版的電話設備公用交換電話網路 (PSTN)、 連線是可透過協力廠商提供者。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

您可以結合 Office 365 的優點與 Lync 2013 的內部部署。
  
隨附的圖表顯示 Office 365 with Lync Online 其中某些使用者所隸屬於內部部署和某些使用者的主伺服器皆線上。也會顯示內部部署 Edge Server。
  
功能和功用描述：
  
- 某些使用者位於內部部署與某些使用者的主伺服器皆線上，但使用者都共用同一個 SIP 網域 （例如 contoso.com)。
    
- 利用您現有的 Lync Server 2013 基礎結構，包括 PSTN 連線。
    
- 新增新的 Lync Online 使用者輕鬆時不需要 PSTN。
    
- ＜ migrate from Lync 內部 Lync online 一段時間，在您的排程。
    
- 與其他 Office 365 應用程式，包括 Exchange Online 和 SharePoint Online 的整合。
    
#### <a name="lync-server"></a>Lync Server

在本部署中，擁有每個項目。隨附的圖顯示內部部署 Active Directory 網域服務 (AD DS) 環境如果使用者是所隸屬於內部部署 Lync Server 基礎結構。
  
功能和功用描述：
  
- 容量規劃及調整大小。
    
- 伺服器擷取及安裝程式。
    
- 部署。
    
- 向外延展、 修補及作業。
    
- 備份資料。
    
- 維護容錯移轉及災害復原。
    
- 將您的 Lync Server 2013 基礎結構連線至 PSTN。
    
- 與現有的電話設備，例如專用交換機 (Pbx) 整合。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控 Lync Server

在本部署中，您的提供者擁有每個項目。隨附的圖表顯示包含其伺服器和設備連線至內部部署環境的提供者的網路。
  
功能和功用描述：
  
- 容量規劃及調整大小。
    
- 伺服器擷取及安裝程式。
    
- 部署。
    
- 向外延展、 修補及作業。
    
- 備份資料。
    
- 維護容錯移轉及災害復原。
    
- 與現有的電話設備，例如專用交換機 (Pbx) 整合。
    
- 此外，可以提供者：
    
  - 在您內部部署 （實線） 的連線與他們自己網路安裝其伺服器和設備。
    
  - 在您內部部署 （虛線） 安裝其伺服器。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>實作每個部署選項的優點

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 在內部伺服器或伺服器軟體的任何作業負擔。
    
- Lync Server 2013 以雲端架構服務通訊功能。
    
- Lync 顯示狀態、 立即訊息、 音訊和視訊呼叫豐富的線上會議和廣泛的 web 會議功能。
    
- 依地理位置分散的組織或與主要行動裝置的員工使用。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

- 使用 Lync Online 的遠端使用者與業務合作夥伴與整合。
    
- 促進 Lync 內部將移轉至 Lync Online。
    
- 不使用 branch office appliance 支援遠端站台。
    
- 簡化的新增的新營業併 Lync 支援。
    
#### <a name="lync-server"></a>Lync Server

- 私人雲端解決方案。
    
- 高度自訂的解決方案。
    
- 與協力廠商的項目都取決於硬體及軟體的元件不支援的 Lync Online 的舊版方案。
    
- 隱私權導致無法同步處理的 AD DS 帳戶與 Office 365 的限制。
    
- 想要控制整個平台和解決方案的組織。
    
- 與 Lync Enterprise Voice PBX 替換。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控 Lync Server

- 需要 Lync Server 功能，但想要將其部署及維護的組織。
    
- 提供者為基礎的方案。
    
- 高度自訂的解決方案。
    
- 與協力廠商的項目都取決於硬體及軟體的元件不支援的 Lync Online 的舊版方案。
    
- 與 Lync Enterprise Voice PBX 替換。
    
### <a name="license-requirements"></a>授權需求

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

訂閱模型。
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

- Office 365-訂閱模型。無需額外的授權。 
    
- 內部 — 所有的內部部署授權套用。 
    
#### <a name="lync-server"></a>Lync Server

- 伺服器作業系統
    
- SQL Server
    
- Lync 2013 Server 授權
    
- Lync 2013 用戶端存取授權
    
#### <a name="provider-hosted-lync-server"></a>提供者主控 Lync Server

成本根據 Lync 解決方案提供者合約。
  
### <a name="architecture-tasks"></a>架構工作

本節列出每個部署選項的架構工作。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 規劃與設計目錄同步處理。
    
- 確定網路容量和可用性透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結。
    
- 取得 Office 365 服務方案提供企業級的安全性的第三方 SSL 憑證。
    
- 決定您是否要連線至 Office 365 與網際網路通訊協定第 6 版 (IPv6)。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

除了 Office 365 與內部部署環境的工作：
  
- 決定您想要使用多少功能整合在內部部署與線上版本的 Exchange Server 與 SharePoint。
    
- 如有需要，決定哪一個 proxy 伺服器裝置將用於 Office 365 的要求。
    
#### <a name="lync-server"></a>Lync Server

設計現有內部部署環境中的 Lync 環境：
  
- 管理中心的 Lync 拓撲和分公司。
    
- 伺服器硬體，包括虛擬化。
    
- Active Directory 網域服務 (AD DS) 與整合和 DNS。
    
- 負載平衡的 Lync server 集區。
    
- 容錯移轉及災害復原。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控 Lync Server

- 雲端型安裝，判斷服務提供者的網路連線。
    
- 內部部署安裝，判斷您的網路上的提供者的 Lync 伺服器的位置。
    
- 針對這兩種類型，決定 AD DS 與 PBX 設備的整合。
    
### <a name="it-pro-responsibilities"></a>IT 專業人員的責任

本節列出每個部署選項以 IT 專業人員的責任。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

部署及管理 Lync Online (Office 365)：
  
- 實作目錄同步處理計劃。
    
- 規劃及實作內部和外部 DNS 記錄和路由。
    
- 設定 proxy 或防火牆的 Office 365 IP 位址及 URL 需求。
    
- 管理使用者帳戶和 Lync Online 設定。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

除了 Office 365 與內部部署環境的工作：
  
- 視需要設定 proxy 伺服器裝置。
    
- 設定內部部署與線上版本的 Exchange Server 與 SharePoint 的功能整合。
    
#### <a name="lync-server"></a>Lync Server

部署及管理 Lync Server 的內部部署環境中：
  
- 佈建伺服器。
    
- 部署 Lync 拓撲。
    
- Lync 伺服器更新。
    
- 新增或移除拓撲伺服器所需根據使用率。
    
- 實作容錯移轉和嚴重損壞修復環境。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控 Lync Server

使用之提供者：
  
- 將 Lync Server 整合到您的網路。
    
- 將 Lync Server 整合與其他 Microsoft 產品或自訂解決方案。
    
- 提供者服務層次協議 (SLA) 具有嚴格監視該。
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>部署 Lync 2013 的兩個範例案例

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Microsoft Azure 中的目錄同步處理元件

部署在 Azure 中的 Office 365 目錄同步處理元件能夠部署虛擬機器隨選因為會較快。
  
隨附圖 Lync Online 搭配 Azure Active Directory 承租人，以同步處理帳戶名稱和密碼的內部部署 Active Directory 環境及 Azure Active Directory 租用戶之間。
  
 **僅限目錄同步處理伺服器**。而不是部署在內部部署環境中的 64 位元目錄同步處理伺服器，您可透過網際網路提供在 Azure 虛擬機器。
  
 **目錄同步作業 + AD FS**。此選項可讓您不透過新增至您的內部部署基礎結構的硬體支援 Office 365 同盟身分識別 (SSO)。如果內部部署 Active Directory 環境無法使用也提供恢復能力。此選項的功能包括：
  
- 以 Azure 虛擬機器執行目錄整合元件。
    
- AD FS 發佈至網際網路 Azure 虛擬機器時所執行的 AD FS proxy 透過。
    
- 用戶端驗證流量的連接的任何位置的使用者會處理的 AD FS 伺服器和部署為 「 Azure 虛擬機器的 proxy。
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>與 Exchange 和 SharePoint Office 365 中的 Lync 整合

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server 與 Exchange Online 和 SharePoint Online

隨附圖與 Exchange Online 和 SharePoint Online 的 Office 365 連線至內部部署 Lync Server 2013 伺服器陣列。
  
此部署的優點可讓您：
  
- 使用 Lync Server 2013 的完整的功能集。
    
- 利用您現有的內部電話設備，例如 Pbx。
    
- 使用 Exchange Online 電子郵件、 卸載內部電子郵件伺服器及儲存的負擔。
    
- 使用 SharePoint Online 進行共同作業、 卸載的維護負擔內部部署 SharePoint 伺服器。
    
- 使用 Lync、 Exchange 和 SharePoint 整合功能，包括整合通訊 (UM) Office 365 中。
    
#### <a name="exchange-server-with-lync-online"></a>使用 Lync Online 的 Exchange Server

隨附圖與 Lync Online 的 Office 365 連線至內部部署 Exchange 伺服器陣列。
  
此部署的優點可讓您：
  
- 運用現有的 Exchange 基礎結構。
    
- 使用 Lync Online 的目前狀態、 im 和會議功能。
    

