---
title: 易於存取的圖表-Microsoft SharePoint 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: 本文是圖表的名為 Microsoft SharePoint 2013 Platform Options 易於存取的文字版本。
ms.openlocfilehash: 4a0b068ffb8abbe11c2286f3daa70c5f62295425
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068599"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>易於存取的圖表-Microsoft SharePoint 2013 平台選項

**摘要：** 本文是圖表的名為 Microsoft SharePoint 2013 Platform Options 易於存取的文字版本。
  
何種商務決策者 (Bdm) 和結構設計師需要了解 Office 365、 Microsoft Azure 和內部部署。 
  
此海報有兩個區段： 
  
- 比較的四個不同的部署的 SharePoint 2013： 在 Office 365 中，Office 365 的混合式 SharePoint 2013、 Azure 及 SharePoint 2013 的內部部署在內部部署 SharePoint。 
    
- 若要將移至 Azure 的三個一般工作負載的描述。 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>四個不同的部署的 SharePoint 2013 平台的比較

比較提供下列方面相關每個部署選項的相關資訊： 
  
- 不同的部署功能的概觀 
    
- 什麼每一種部署最適合 
    
- 授權需求 
    
- 若要實作所需的架構工作 
    
- IT 專業人員的實作的責任 
    
### <a name="overview"></a>概觀

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

取得效率，並最佳化的成本與 Office 365 多租用戶計劃。 
  
隨附圖表顯示 SharePoint Online 與 Azure Active Directory 承租人，以同步處理帳戶名稱和內部部署 Active Directory 環境與 Azure Active Directory 租用戶之間的密碼。 
  
描述的功能： 
  
- 軟體即服務 (SaaS)。 
    
- 豐富的功能集永遠是最新狀態。 
    
- 包含 （可以使用與其他應用程式），為 Azure Active Directory 租用戶。 
    
- Directory 整合包括同步處理帳戶名稱和內部部署 Active Directory 環境與 Azure Active Directory 租用戶之間的密碼。 
    
- 如果單一登入 (SSO) 是需求，可以實作 Active Directory Federation Services (AD FS)。 
    
- 透過加密和驗證存取 （連接埠 443） 經由網際網路的用戶端通訊。 
    
- 資料移轉僅限於功能可透過網際網路上傳。 
    
- 自訂： 應用程式的 Office、 SharePoint 和 SharePoint Designer 2013。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

SharePoint 2013 的內部部署與合併 Office 365 的優點。 
  
隨附圖表顯示使用 SharePoint Online 的 Office 365 連線到內部部署 SharePoint Server 2013 伺服器陣列使用 Business Connectivity Services (BCS)。 
  
選擇何種整合的下列功能： 
  
SharePoint Search 
  
- 使用者可以看見來自兩個環境的搜尋結果。 
    
- 外部網路使用者可以從遠端登入內部部署 Active Directory 帳戶，並使用所有可用的混合式功能。 
    
BCS
  
從 SharePoint Online： 使用者可以執行讀取與寫入作業。 BCS 服務連線至內部部署 SharePoint Server 2013 伺服器陣列。 BCS 服務在內部部署伺服器陣列代理人上設定內部部署 OData 服務端點的連線。 
  
Duet Enterprise Online 
  
從 SharePoint Online 中，使用者可以執行讀取與寫入作業對內部 SAP 系統。 
  
#### <a name="azure"></a>Azure

利用雲端時維護的功能與平台的完全控制權。 
  
隨附圖顯示 Azure，其中包含兩個雲端服務、 SharePoint 2013 伺服器陣列，以及 Windows Server Active Directory 與 DNS 透過網際網路連線的使用者，或是連線至內部部署 Active Directory 透過 VPN 通道。 
  
功能包括： 
  
-  Azure 是提供裝載 SharePoint 2013 伺服器陣列所需的基礎結構和應用程式服務平台。
    
- 基礎結構服務。 
    
- SQL Server 和 SharePoint 的最佳原生雲端平台。 
    
- 幾乎會立即與未承諾是運算資源。 
    
- 專注於應用程式，而不是資料中心和基礎結構。 
    
- 運用低成本的開發和測試環境。 
    
- SharePoint 解決方案可以從網際網路存取或只能從公司環境透過站台對站 VPN 通道存取。 
    
- 自訂項目並不侷限於。 
    
#### <a name="on-premises"></a>內部部署

您擁有的所有項目。 
  
隨附的圖表會顯示與網頁伺服器、 應用程式伺服器與所有資料庫及搜尋專用應用程式伺服器的 Active Directory 進行通訊的內部部署環境。 
  
功能包括： 
  
- 容量計劃及調整大小。 
    
- 伺服器擷取和設定。 
    
- 部署。 
    
- 向外延展、 修補和作業。 
    
- 備份資料。 
    
- 維護的災害復原環境。 
    
- 自訂項目並不侷限於。 
    
### <a name="deployment-type-is-best-for---"></a>部署類型是適合使用。 . .

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 保護外部共用與共同作業。 （唯一功能 ！） 
    
- 內部網路 — 小組網站、 「 我的網站和內部共同作業。 
    
- 文件儲存與雲端中的版本設定。 
    
- 基本的公用對向網站。 
    
使用 Office 365 專用訂閱計劃的其他功能： 
  
- Microsoft 資料中心設備專用於您的組織並不會與任何其他組織共用。 
    
- 每個客戶環境所在的實體分開的網路中。 
    
- 跨 IPSec 安全 VPN 或客戶擁有私人連線的用戶端通訊。 雙因素驗證是選擇性的。 
    
- ITAR 支援方案。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

- 使用 Office 365 的外部共用和協同作業而不是設定外部網路環境。 
    
- 將 「 我的網站 (商務用 OneDrive) 移至雲端，方便使用者可以從遠端存取他們的檔案。 
    
- Office 365 中開始新的小組網站。 
    
- 整合 Office 365 網站與內部部署 BCS SharePoint 環境。 
    
#### <a name="azure"></a>Azure

- SharePoint 的網際網路網站 — 公用對向網站。 善用客戶帳戶和驗證的 Azure AD。 
    
- 開發人員、 測試及執行環境 — 快速地佈建和 deprovision 整個環境。 
    
- 混合式應用程式，跨資料中心部署與雲端的應用程式。 
    
- 嚴重損壞修復環境 — 快速地從嚴重損壞復原。 支付僅供使用。 
    
- 需要深入的報告或稽核的伺服器陣列。 
    
- Web analytics。 
    
- 靜態 （資料進行加密 SQL 資料庫） 的資料加密。 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>靜態 （資料進行加密 SQL 資料庫） 的資料加密

- 國內伺服器陣列 （當資料才能位於管轄）。 
    
- 複雜的 BI 解決方案，都必須位於關閉 BI 資料。 
    
- 私人雲端解決方案。 
    
- 高度自訂的解決方案。 
    
- 具有協力廠商元件，取決於硬體和軟體不支援在 Azure 基礎結構服務上的舊版解決方案。 
    
- 防止與 Azure Active Directory （如 Office 365 的需求） 的 Active Directory 帳戶同步處理的隱私性限制。 
    
- 偏好控制整個平台和解決方案的組織。 
    
### <a name="license-requirements"></a>授權需求

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

訂閱模型。 不需要額外的授權。 
  
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

- Office 365-訂閱模型。 不需要額外的授權。 
    
- 內部 — 所有的內部部署授權套用。 
    
#### <a name="azure"></a>Azure

-  Azure 訂用帳戶 （包括伺服器作業系統）
    
- SQL Server 
    
- SharePoint 2013 伺服器授權 
    
- SharePoint 2013 用戶端存取授權 
    
#### <a name="on-premises"></a>內部部署

- 伺服器作業系統 
    
- SQL Server 
    
- SharePoint 2013 伺服器授權 
    
- SharePoint 2013 用戶端存取授權 
    
### <a name="architecture-tasks"></a>架構工作

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- < Plan and design 目錄整合。 兩個選項。 內部部署或在 Azure 中部署任一選項： 密碼同步處理 （需要一個 64 位元伺服器）。 SSO （需要 AD FS 和多部伺服器）。 
    
- 請確定網路容量和透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結的可用性。 
    
- 取得第三方 SSL 憑證，以提供 Office 365 服務方案的企業安全性。 
    
- 規劃租用戶名稱，以及設計的網站集合架構與控管。 
    
- 規劃自訂、 解決方案，而且適用於 SharePoint Online 應用程式。 
    
- 決定是否要使用網際網路通訊協定第 6 (IPv6) 連線至 Office 365。 這並不常見。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

除了 Office 365 與內部部署環境的工作： 
  
- 決定您想要然後選擇 [混合式拓撲多少功能整合。 請參閱此模型海報： 我應該使用哪個混合式拓撲？ 
    
- 如有需要，決定要使用哪一個 proxy 伺服器裝置。 
    
#### <a name="azure"></a>Azure

設計 Azure 的網路環境： 
  
- 在 Azure，包括子網路的虛擬網路。 
    
- 網域環境和與內部伺服器整合。 
    
- IP 位址和 DNS。 
    
- 親和性群組和儲存體帳戶。 
    
設計 Azure 中的 SharePoint 環境： 
  
- SharePoint 伺服器陣列拓撲和邏輯架構。 
    
-  Azure 可用性設定組和更新的網域。
    
- 虛擬機器大小。 
    
- 負載平衡的端點。 
    
- 供大眾存取，如果這是建議的外部端點。 
    
- 嚴重損壞修復環境。 
    
#### <a name="on-premises"></a>內部部署

設計現有內部部署環境中的 SharePoint 環境： 
  
- SharePoint 伺服器陣列拓撲和邏輯架構。 
    
- 伺服器硬體。 
    
- 虛擬環境，如果使用。 
    
- 負載平衡。 
    
- AD DS 與 DNS 的整合。 
    
- 嚴重損壞修復環境。 
    
### <a name="it-pro-responsibilities"></a>IT 專業人員的責任

#### <a name="sharepoint-2013-in-office-365"></a>Office 365 中的 SharePoint 2013

- 確保使用者工作站符合 Office 365 用戶端必要條件。 
    
- 實作目錄整合計劃。 
    
- 規劃及實作內部和外部 DNS 記錄和路由。 
    
- 設定 proxy 或防火牆的 Office 365 IP 位址和 URL 需求。 
    
- 建立並指派權限給網站集合。 
    
- SharePoint Online 的實作自訂項目、 解決方案和應用程式。 
    
- 監控網路可用性，並找出可能的瓶頸。 
    
#### <a name="hybrid-with-office-365"></a>與 Office 365 的混合式

除了 Office 365 與內部部署環境的工作： 
  
- 如有必要，請設定 proxy 伺服器的裝置。 
    
- 設定混合式身分識別管理基礎結構： SSO 和兩個環境之間的伺服器對伺服器驗證。 
    
- 設定所選擇的功能的整合： 搜尋，BCS、 Duet Enterprise Online。 
    
#### <a name="azure"></a>Azure

部署及管理 Azure 和 SharePoint 環境： 
  
- 實作和管理 Azure 網路環境。 
    
- 部署 SharePoint 環境。 
    
- 更新 SharePoint 伺服器陣列的伺服器。 
    
- 新增或關閉虛擬機器視根據伺服器陣列使用率。 
    
- 增加或減少虛擬機器的大小，視需要。 
    
- 備份 SharePoint 環境。 
    
- 實作災害復原環境和通訊協定。 
    
#### <a name="on-premises"></a>內部部署

部署及管理 SharePoint 的內部部署環境： 
  
- 佈建伺服器。 
    
- 部署 SharePoint 環境。 
    
- 更新 SharePoint 伺服器陣列的伺服器。 
    
- 新增或移除伺服器陣列的伺服器需要根據伺服器陣列使用率。 
    
- 備份 SharePoint 環境。 
    
- 實作災害復原環境和通訊協定。 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>若要將移至 Azure 的三個一般工作負載

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 加上在 Azure 中的目錄元件

部署 Office 365 目錄整合元件，在 Azure 中的更快速地是因為它可以部署虛擬機器上的需求。 
  
#### <a name="directory-synchronization-server-only"></a>僅限目錄同步處理伺服器

而不是部署在內部部署環境中的 64 位元目錄同步處理伺服器，請改為佈建在 Azure 中的虛擬機器。 
  
隨附圖表顯示 SharePoint Online 與 Azure Active Directory 承租人，以同步處理帳戶名稱和內部部署 Active Directory 環境與 Azure Active Directory 租用戶之間的密碼。 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>目錄同步作業加上 AD FS

此選項可讓您支援 Office 365 同盟身分識別 (SSO)，不會新增至您的內部部署基礎結構的硬體。 它也提供恢復能力，如果內部部署 Active Directory 環境無法使用。 
  
- 目錄整合元件會存放在 Azure 中。 
    
- AD FS 是透過 Azure 中的 AD FS proxy 的網際網路發佈。 
    
- 從任何位置連線的使用者的用戶端驗證流量是由 AD FS 伺服器與在 Azure 部署的 proxy 處理。 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>公用對向網際網路網站和客戶驗證的 Azure AD

善用能夠輕鬆地藉由將您的網際網路網站在 Azure 中將其調整為需求。 使用 Azure AD 以儲存客戶帳戶。 
  
#### <a name="azure-advantages-for-internet-sites"></a>Azure 的網際網路網站的優點

- 僅支付您需要的縮放比例的伺服器陣列使用率為基礎的虛擬機器數量的資源。 
    
- 新增深報告及 web analytics。 
    
- 專注於開發絕佳的網站，而不是建置基礎結構。 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD 提供雲端服務的身分識別管理及存取控制功能。 功能包括目錄資料和一組核心的身分識別服務，包括使用者登入程序、 驗證服務，並使用 AD FS 的雲端式存放區。 包含與 Azure AD 識別服務輕鬆地整合您的內部部署 Active Directory 部署，並完全支援協力廠商身分識別提供者。 
  
隨附圖表顯示區域及是很重要的網際網路對向網站的驗證的設定。 此圖顯示 Azure Active Directory 租用戶，其中包含使用兩個區域上 Azure 的 SharePoint 伺服器陣列： 
  
- 互動匿名與驗證訪客和客戶網路外部的網際網路區域 
    
- 包含 NTLM 編目] 和 [Windows 驗證透過 VPN 通道與您的內部部署 Active Directory 部署互動的預設區域。 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>內部部署伺服器陣列以及 Azure 中的災害復原

選擇符合您的業務需求的災害復原選項。 Azure 提供快速入門嚴重損壞修復的公司的入門選項及進階高的恢復能力需求的企業版的選項。 
  
#### <a name="cold-standby"></a>冷待命

- 完全建置在伺服器陣列，但會停止虛擬機器。 （您付費只有當他們正在執行 ！） 
    
- 維護環境包含從時間來-時期，修補程式、 更新及驗證環境開始虛擬機器。 
    
- 啟動完整的環境發生嚴重損壞。 
    
#### <a name="warm-standby"></a>暖待命

- 這包括已佈建並執行的小型伺服器陣列。 
    
- 在伺服器陣列發生容錯移轉時，可以立即做使用者。 
    
- 擴充伺服器陣列快速完整的使用者提供服務。 
    
#### <a name="hot-standby"></a>熱待命

完全調整大小的伺服器陣列已佈建並執行處於待命狀態。 
  
隨附圖顯示在內部部署伺服器陣列上 Azure 的 SharePoint 災害復原環境與互動。 內部部署資料庫使用 SQL Server 記錄傳送透過 VPN 通道來存取 SharePoint 嚴重損壞修復環境，其中包括兩個包含 SharePoint 資料庫、 兩部 Web 前端伺服器，以及兩個 SharePoint 的 SQL 資料庫伺服器應用程式伺服器。 
  

