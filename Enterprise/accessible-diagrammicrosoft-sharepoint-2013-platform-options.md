---
title: "存取圖表-Microsoft SharePoint 2013 平台選項"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "本文是圖表的名為 Microsoft SharePoint 2013 Platform Options 可存取的文字版本。"
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>存取圖表-Microsoft SharePoint 2013 平台選項

**摘要：**本文是圖表的名為 Microsoft SharePoint 2013 Platform Options 可存取的文字版本。
  
了解 Office 365、 Microsoft Azure 和內部部署需要何種商務決策者 (Bdm) 與架構師。 
  
此海報有兩個章節： 
  
- 比較 SharePoint 2013 的四個不同的部署： 在 Office 365、 SharePoint 2013、 Azure、 和內部部署 SharePoint 2013 的內部部署與 Office 365 的混合式 SharePoint。 
    
- 若要將移至 Azure 三個一般工作負載的描述。 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>四個不同的部署的 SharePoint 2013 平台的比較

比較提供下列項目相關的每個部署選項的相關資訊： 
  
- 不同的部署功能的概觀 
    
- 內容部署的每一種最適合 
    
- 授權需求 
    
- 若要實作所需的架構工作 
    
- IT 專業人員實作的責任 
    
### <a name="overview"></a>概觀

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

取得效率和最佳化的 Office 365 multitenant 計劃的成本。 
  
隨附圖 SharePoint Online 搭配 Azure Active Directory 承租人，以同步處理帳戶名稱和密碼的內部部署 Active Directory 環境及 Azure Active Directory 租用戶之間。 
  
功能描述： 
  
- 軟體即服務 (SaaS)。 
    
- 豐富的功能集永遠是最新的。 
    
- 包含 Azure Active Directory 租用戶 （可搭配其他應用程式）。 
    
- 目錄整合包括同步處理帳戶名稱和密碼的內部部署 Active Directory 環境及 Azure Active Directory 租用戶之間。 
    
- 如果單一登入 (SSO) 是需求，可實作 Active Directory Federation Services (AD FS)。 
    
- 加密及經過驗證的存取 （連接埠 443） 透過網際網路用戶端通訊。 
    
- 資料移轉僅限於功能可透過網際網路上傳。 
    
- Office、 SharePoint、 及 SharePoint Designer 2013 的自訂項目： 應用程式。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

結合 Office 365 的優點與內部部署 SharePoint 2013。 
  
隨附的圖表顯示與 SharePoint Online 的 Office 365 使用 Business Connectivity Services (BCS) 連線至內部部署 SharePoint Server 2013 伺服器陣列。 
  
選擇何種整合的下列功能： 
  
SharePoint Search 
  
- 使用者會看見來自這兩個環境的搜尋結果。 
    
- 外部網路使用者可以從遠端登入內部部署 Active Directory 帳戶和使用所有可用的混合式功能。 
    
BCS
  
從 SharePoint Online： 使用者可以執行讀取與寫入作業。BCS 服務連線至內部部署 SharePoint Server 2013 伺服器陣列。在內部部署伺服器陣列經紀人上設定的 BCS 服務的連線到內部部署 OData 服務端點。 
  
Duet Enterprise Online 
  
從 SharePoint Online，使用者可以執行讀取與寫入作業對內部部署的 SAP 系統。 
  
#### <a name="azure"></a>Azure

運用雲端同時又不完全控制的平台和功能。 
  
隨附圖 Azure，其中包含兩個雲端服務、 SharePoint 2013 伺服器陣列，以及 Windows Server Active Directory 與 DNS 透過網際網路連線至使用者或連線至內部部署 Active Directory 透過 VPN 通道。 
  
功能包括： 
  
-  Azure 是提供架設在 SharePoint 2013 伺服器陣列所需的基礎結構和應用程式服務平台。
    
- 基礎結構服務。 
    
- SQL Server 與 SharePoint 的最佳原生雲端平台。 
    
- 幾乎立即使用沒有承諾可用運算資源。 
    
- 整個計畫重心在應用程式，而不是資料中心及基礎結構上。 
    
- 便宜的開發及測試環境。 
    
- SharePoint 解決方案可以從網際網路存取或無法存取僅從網站 VPN 通道透過公司環境。 
    
- 自訂項目並未限制。 
    
#### <a name="on-premises"></a>在內部部署

您擁有每個項目。 
  
隨附的圖表顯示網頁伺服器、 應用程式伺服器及 Active Directory 通訊的所有資料庫和搜尋的專用應用程式伺服器的內部部署環境。 
  
功能包括： 
  
- 容量規劃及調整大小。 
    
- 伺服器擷取及安裝程式。 
    
- 部署。 
    
- 向外延展、 修補及作業。 
    
- 備份資料。 
    
- 維護嚴重損壞修復環境。 
    
- 自訂項目並未限制。 
    
### <a name="deployment-type-is-best-for---"></a>部署類型適合...]

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 保護外部共用和協同合作。（唯一功能 ！） 
    
- 內部網路 — 小組網站、 「 我的網站及內部共同作業。 
    
- 文件儲存區與雲端中的版本設定。 
    
- 基本公開網站。 
    
使用 Office 365 專用訂閱計劃的其他功能： 
  
- 專屬於您的組織且不與任何其他組織共用 Microsoft 資料中心設備。 
    
- 每個客戶環境所在的實體分開的網路中。 
    
- 跨 IPSec 安全 VPN 或客戶擁有私人連線的用戶端通訊。雙因素驗證是選擇性的。 
    
- ITAR 支援計劃。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

- 使用 Office 365 外部的共用和協同作業而不是設定外部網路環境。 
    
- 將 「 我的網站 (OneDrive for Business) 移至雲端，讓使用者從遠端存取其檔案更容易。 
    
- Office 365 中開始新的小組網站。 
    
- 整合 Office 365 網站的內部部署 BCS SharePoint 環境。 
    
#### <a name="azure"></a>Azure

- 網際網路網站的 SharePoint — 公用對向網站。善用 Azure AD 的客戶帳戶及驗證。 
    
- 開發人員、 測試及執行環境 — 迅速佈建和 deprovision 整個環境。 
    
- 混合式應用程式-跨您的資料中心及雲端的應用程式。 
    
- 嚴重損壞修復環境 — 快速地從災害復原。工資僅供使用。 
    
- 需要深入的報表或稽核的伺服器陣列。 
    
- Web analytics。 
    
- 資料加密 （加密 SQL 資料庫的資料） 的靜態。 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>資料加密 （加密 SQL 資料庫的資料） 的靜態

- 國內伺服器陣列 （當資料才可位於管轄）。 
    
- 複雜的 BI 解決方案必須位於關閉 BI 資料。 
    
- 私人雲端解決方案。 
    
- 高度自訂的解決方案。 
    
- 協力廠商的元件取決於硬體和軟體不支援在 Azure 基礎結構服務上的舊版方案。 
    
- 隱私權導致無法同步處理的 Active Directory 帳戶的 Azure Active Directory （Office 365 的需求） 的限制。 
    
- 偏好控制整個平台和解決方案的組織。 
    
### <a name="license-requirements"></a>授權需求

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

訂閱模型。無需額外的授權。 
  
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

- Office 365-訂閱模型。無需額外的授權。 
    
- 內部 — 所有的內部部署授權套用。 
    
#### <a name="azure"></a>Azure

-  Azure 訂閱 （包括伺服器作業系統）
    
- SQL Server 
    
- SharePoint 2013 伺服器授權 
    
- SharePoint 2013 用戶端存取授權 
    
#### <a name="on-premises"></a>在內部部署

- 伺服器作業系統 
    
- SQL Server 
    
- SharePoint 2013 伺服器授權 
    
- SharePoint 2013 用戶端存取授權 
    
### <a name="architecture-tasks"></a>架構工作

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 規劃與設計目錄整合。兩個選項。任一選項可在內部部署或 Azure 中部署： 密碼同步處理 （需要 64 位元伺服器）。SSO （需要 AD FS 和多部伺服器）。 
    
- 確定網路容量和可用性透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結。 
    
- 取得 Office 365 服務方案提供企業級的安全性的第三方 SSL 憑證。 
    
- 規劃的租用戶名稱及設計的網站集合架構與管理。 
    
- 規劃自訂項目、 解決方案、 和 SharePoint Online 應用程式。 
    
- 決定您是否要連線至 Office 365 使用網際網路通訊協定第 6 (IPv6)。這不是一般。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

除了 Office 365 與內部部署環境的工作： 
  
- 決定您想要與選擇的混合式拓撲多少功能整合。請參閱此模型海報： 我應該使用哪個混合式拓撲？ 
    
- 如有需要，決定要使用的 proxy 伺服器的裝置。 
    
#### <a name="azure"></a>Azure

設計 Azure 網路環境： 
  
- Azure，包括子網路內的虛擬網路。 
    
- 網域環境並與內部伺服器整合。 
    
- IP 位址和 DNS。 
    
- 親和性群組和儲存的帳戶。 
    
設計 Azure 中的 SharePoint 環境： 
  
- SharePoint 伺服器陣列拓撲和邏輯架構。 
    
-  Azure 可用性設定及更新網域。
    
- 虛擬機器大小。 
    
- 負載平衡的端點。 
    
- 供大眾存取，如果這是試試的外部端點。 
    
- 嚴重損壞修復環境。 
    
#### <a name="on-premises"></a>在內部部署

設計現有內部部署環境中的 SharePoint 環境： 
  
- SharePoint 伺服器陣列拓撲和邏輯架構。 
    
- 伺服器硬體。 
    
- 虛擬環境，如果使用。 
    
- 負載平衡。 
    
- 與 AD DS 與 DNS 的整合。 
    
- 嚴重損壞修復環境。 
    
### <a name="it-pro-responsibilities"></a>IT 專業人員的責任

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 確定使用者工作站符合 Office 365 用戶端的必要條件。 
    
- 實作目錄整合計劃。 
    
- 規劃及實作內部和外部 DNS 記錄和路由。 
    
- 設定 proxy 或防火牆的 Office 365 IP 位址及 URL 需求。 
    
- 建立及權限指派給網站集合。 
    
- SharePoint Online 的實作自訂項目、 解決方案、 與應用程式。 
    
- 監視網路可用性並找出可能瓶頸。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

除了 Office 365 與內部部署環境的工作： 
  
- 視需要設定 proxy 伺服器裝置。 
    
- 設定混合式身分識別管理基礎結構： SSO 與兩個環境之間的伺服器對伺服器驗證。 
    
- 設定所選擇的功能的整合： 搜尋、 BCS、 Duet Enterprise Online。 
    
#### <a name="azure"></a>Azure

部署及管理 Azure 與 SharePoint 環境： 
  
- 實作和管理 Azure 網路環境。 
    
- 部署 SharePoint 的環境。 
    
- 更新 SharePoint 伺服器陣列的伺服器。 
    
- 新增或關閉虛擬機器時所需根據伺服器陣列使用情況。 
    
- 增加或減少所需的虛擬機器大小。 
    
- 備份 SharePoint 的環境。 
    
- 實作嚴重損壞修復環境及通訊協定。 
    
#### <a name="on-premises"></a>在內部部署

部署及管理 SharePoint 內部部署環境： 
  
- 佈建伺服器。 
    
- 部署 SharePoint 的環境。 
    
- 更新 SharePoint 伺服器陣列的伺服器。 
    
- 新增或移除伺服器陣列中伺服器所需根據伺服器陣列使用情況。 
    
- 備份 SharePoint 的環境。 
    
- 實作嚴重損壞修復環境及通訊協定。 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>若要將移至 Azure 三個一般工作負載

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 加上在 Azure 中的目錄元件

部署在 Azure 中的 Office 365 目錄整合元件速度是因為它可部署虛擬機器隨選。 
  
#### <a name="directory-synchronization-server-only"></a>僅限目錄同步處理伺服器

而不是部署在內部部署環境中的 64 位元目錄同步處理伺服器，請改用佈建在 Azure 虛擬機器。 
  
隨附圖 SharePoint Online 搭配 Azure Active Directory 承租人，以同步處理帳戶名稱和密碼的內部部署 Active Directory 環境及 Azure Active Directory 租用戶之間。 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>目錄同步作業加上 AD FS

此選項可讓您不透過新增至您的內部部署基礎結構的硬體支援 Office 365 同盟身分識別 (SSO)。如果內部部署 Active Directory 環境無法使用也提供恢復能力。 
  
- 位在 Azure 中的目錄整合元件。 
    
- AD FS 發佈至網際網路 Azure 中的 AD FS proxy 透過。 
    
- 用戶端驗證流量的連接的任何位置的使用者會處理的 AD FS 伺服器和部署在 Azure 的 proxy。 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>公開網際網路網站和客戶驗證 Azure AD

善用可輕鬆地適應需求藉由在 Azure 中放入網際網路網站的能力。使用 Azure AD 儲存客戶帳戶。 
  
#### <a name="azure-advantages-for-internet-sites"></a>Azure 網際網路網站的優點

- 僅限工資來調整伺服器陣列使用情況為基礎的虛擬機器數目所需的資源。 
    
- 新增深報告與 web 分析。 
    
- 整個計畫重心在開發更好的網站而不是建置基礎結構。 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD 提供雲端服務的身分識別管理和存取控制功能。功能包括目錄資料與一組核心身分識別服務，包括使用者登入程序、 驗證服務及 AD FS 的雲端存放區。輕鬆地將與您的內部部署 Active Directory 部署整合且完全支援協力廠商身分識別提供者的身分識別服務隨附 Azure AD。 
  
隨附圖區域及重要的網際網路網站的驗證的設定。此圖顯示 Azure Active Directory 承租人，以使用兩個區域包含在 Azure 的 SharePoint 伺服器陣列： 
  
- 與其互動匿名與驗證的訪客和客戶網路外部的網際網路區域 
    
- 包含用於編目和透過 VPN 通道會與內部部署 Active Directory 部署互動的 Windows 驗證的 NTLM 預設區域。 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>內部部署伺服器陣列以及 Azure 中的災害復原

選擇符合您的業務需求的災害復原選項。Azure 提供快速入門嚴重損壞修復的公司的性質選項及進階高恢復能力需求的企業版的選項。 
  
#### <a name="cold-standby"></a>冷待命

- 在伺服器陣列完全建置基礎，但已停止虛擬機器。（錢只有當他們正在執行 ！） 
    
- 維護環境包含啟動虛擬機器從時間來-階段、 修補、 更新及驗證環境。 
    
- 開始在發生災害時完整的環境。 
    
#### <a name="warm-standby"></a>暖待命

- 這包括已佈建及執行的小型伺服器陣列。 
    
- 伺服器陣列的容錯移轉的情況下才能立即到使用者。 
    
- 向外延展伺服器陣列快速完整的使用者提供服務。 
    
#### <a name="hot-standby"></a>熱待命

完全調整大小的伺服器陣列已佈建及執行處於待命狀態。 
  
隨附圖互動 Azure 上的 SharePoint 災害復原環境的內部部署伺服器陣列。在內部資料庫使用 SQL Server 記錄傳送透過 VPN 通道來存取 SharePoint 嚴重損壞修復環境，其中包含兩個包含 SharePoint 資料庫、 兩部 Web 前端伺服器，以及兩個 SharePoint 的 SQL 資料庫伺服器應用程式伺服器。 
  

