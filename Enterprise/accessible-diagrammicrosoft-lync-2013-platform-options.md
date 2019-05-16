---
title: 易於存取的圖表-Microsoft Lync 2013 平台選項
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在技術圖表易於存取的文字版本。
ms.openlocfilehash: 4993ad90307973589da6dc5081d8c2875b44ce66
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068609"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>易於存取的圖表-Microsoft Lync 2013 平台選項

**摘要：** 本文是圖表的名為 Microsoft Lync 2013 平台選項，這是圖表的可在[技術圖表](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)易於存取的文字版本。
  
此海報說明 business decision makers (Bdm) 和架構設計人員需要瞭解哪些有關 Lync Online (Office 365) 和 Lync Server 部署，並包括：
  
- 四個不同的部署選項的比較： Lync Online (Office 365)、 Lync Online/伺服器混合式、 Lync Server 和 Provider-Hosted Lync Server。 
    
- 部署 Lync 2013 的兩個範例案例。
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>四個不同的部署的 Lync 2013 平台的比較

比較提供下列項目的每個部署選項的相關資訊： 
  
- 不同的部署功能的概觀
    
- 實作每個部署選項的優點
    
- 授權需求
    
- 必要的架構工作
    
- IT 專業人員負責實作每個部署選項
    
### <a name="overview"></a>概觀

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

您取得效率，並最佳化的成本與 Office 365 多租用戶計劃。
  
隨附圖表顯示 Lync Online 與 Azure Active Directory 承租人，以同步處理帳戶名稱和內部部署 Active Directory 網域服務 (AD DS) 環境與 Azure Active Directory 租用戶之間的密碼。 
  
描述的特性與功能：
  
- 軟體即服務 (SaaS)。
    
- 豐富型功能永遠是最新的設定。
    
- 包含可搭配其他應用程式的線上帳戶 Azure Active Directory 租用戶。 
    
- Directory 整合包括同步處理帳戶名稱和內部部署 Active Directory 網域服務 (AD DS) 環境與 Azure Active Directory 租用戶之間的密碼。
    
- 如果單一登入 (SSO) 是需求，必須實作 Active Directory Federation Services (AD FS)。 
    
- 在網際網路上的用戶端通訊是加密與驗證。
    
- 舊版的電話設備公用交換電話網路 (PSTN)，連線是可透過協力廠商提供者。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

您可以合併 Office 365 的優點與 Lync 2013 的內部部署。
  
隨附圖表顯示 Office 365 with Lync Online 其中部分使用者為隸屬於內部部署，有些使用者位於線上。 也會顯示內部部署 Edge Server。
  
描述的特性與功能：
  
- 某些使用者位於內部部署和部分使用者位於線上使用，但使用者共用相同的 SIP 網域 （例如 contoso.com)。
    
- 利用您現有的 Lync Server 2013 基礎結構，包括 PSTN 連線。
    
- 新增新的 Lync Online 使用者輕鬆地時不需要 PSTN。
    
- 經過一段時間，在您的排程上，從 Lync 內部部署移轉至 Lync Online。
    
- 與其他 Office 365 應用程式，包括 Exchange Online 和 SharePoint Online 整合。
    
#### <a name="lync-server"></a>Lync Server

在此部署中，您所擁有的所有項目。 隨附的圖表會顯示使用者對位於的內部的所在的內部部署 Active Directory 網域服務 (AD DS) 環境與 Lync Server 基礎結構。
  
描述的特性與功能：
  
- 容量計劃及調整大小。
    
- 伺服器擷取和設定。
    
- 部署。
    
- 向外延展、 修補和作業。
    
- 備份資料。
    
- 維護容錯移轉及災害復原。
    
- 將您的 Lync Server 2013 基礎結構連線至 PSTN。
    
- 與現有的電話設備，例如專用交換機 (Pbx) 整合。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控的 Lync 伺服器

在此部署中，您的提供者會擁有的所有項目。 隨附圖表顯示包含其伺服器和設備連線到內部部署環境的提供者的網路。
  
描述的特性與功能：
  
- 容量計劃及調整大小。
    
- 伺服器擷取和設定。
    
- 部署。
    
- 向外延展、 修補和作業。
    
- 備份資料。
    
- 維護容錯移轉及災害復原。
    
- 與現有的電話設備，例如專用交換機 (Pbx) 整合。
    
- 此外，提供者可以：
    
  - 與您的內部部署 （實線） 連線自己網路中安裝其伺服器和設備。
    
  - 在您內部部署 （虛線） 上安裝其伺服器。
    
### <a name="benefits-of-implementing-each-deployment-option"></a>實作每個部署選項的優點

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- 內部部署伺服器或伺服器軟體的任何作業負擔。
    
- Lync Server 2013 作為雲端式服務的通訊功能。
    
- Lync 顯示狀態、 立即訊息、 音訊和視訊通話、 豐富的線上會議，以及多樣的 web 會議功能。
    
- 與地理位置分散的組織或主要行動員工使用。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

- 使用 Lync Online 的遠端使用者和與商務合作夥伴的整合。
    
- 促進從 Lync 內部部署移轉至 Lync Online。
    
- 而不需使用 branch office appliance 支援遠端站台。
    
- 新增新的商務收購的 Lync 支援容易。
    
#### <a name="lync-server"></a>Lync Server

- 私人雲端解決方案。
    
- 高度自訂的解決方案。
    
- 具有協力廠商元件，取決於硬體和軟體所 Lync Online 不支援的舊版解決方案。
    
- 防止同步處理的 AD DS 帳戶與 Office 365 的隱私權限制。
    
- 想要控制整個平台和解決方案的組織。
    
- 與 Lync 企業語音 PBX 取代。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控的 Lync 伺服器

- 想要讓 Lync Server 功能，但想要將其部署及維護的組織。
    
- 提供者為基礎的解決方案。
    
- 高度自訂的解決方案。
    
- 具有協力廠商元件，取決於硬體和軟體所 Lync Online 不支援的舊版解決方案。
    
- 與 Lync 企業語音 PBX 取代。
    
### <a name="license-requirements"></a>授權需求

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

訂閱模型。
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

- Office 365-訂閱模型。 不需要額外的授權。 
    
- 內部 — 所有的內部部署授權套用。 
    
#### <a name="lync-server"></a>Lync Server

- 伺服器作業系統
    
- SQL Server
    
- Lync 2013 Server 授權
    
- Lync 2013 用戶端存取授權
    
#### <a name="provider-hosted-lync-server"></a>提供者主控的 Lync 伺服器

成本根據您的 Lync 解決方案提供者合約。
  
### <a name="architecture-tasks"></a>架構工作

此章節將列出每個部署選項的架構工作。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- < Plan and design 目錄同步處理。
    
- 請確定網路容量和透過防火牆、 proxy 伺服器、 閘道，以及跨 WAN 連結的可用性。
    
- 取得第三方 SSL 憑證，以提供 Office 365 服務方案的企業安全性。
    
- 決定是否您想要連線到 Office 365 與網際網路通訊協定第 6 版 (IPv6)。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

除了 Office 365 與內部部署環境的工作：
  
- 決定您想要使用多少功能整合內部部署和線上版本的 Exchange Server 和 SharePoint。
    
- 如有需要，判斷哪一個 proxy 伺服器裝置將用於從 Office 365 的要求。
    
#### <a name="lync-server"></a>Lync Server

設計現有內部部署環境中的 Lync 環境：
  
- 管理中心的 Lync 拓撲和分公司。
    
- 伺服器硬體，包括虛擬化。
    
- Active Directory 網域服務 (AD DS) 與整合和 DNS。
    
- 負載平衡的 Lync 伺服器集區。
    
- 容錯移轉及災害復原。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控的 Lync 伺服器

- 針對雲端型安裝，決定服務提供者的網路連線。
    
- 內部部署安裝，判斷您網路上的提供者的 Lync 伺服器的位置。
    
- 對於這兩種類型，判斷 AD DS 與 PBX 設備的整合。
    
### <a name="it-pro-responsibilities"></a>IT 專業人員的責任

此章節將列出每個部署選項的 IT 專業人員的責任。
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

部署及管理 Lync Online (Office 365):
  
- 實作目錄同步處理計劃。
    
- 規劃及實作內部和外部 DNS 記錄和路由。
    
- 設定您的 proxy 或防火牆的 Office 365 IP 位址和 URL 需求。
    
- 管理使用者帳戶和 Lync Online 設定。
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/伺服器混合 （分割網域）

除了 Office 365 與內部部署環境的工作：
  
- 如有必要，請設定 proxy 伺服器的裝置。
    
- 內部部署與 Exchange Server 與 SharePoint online 的版本設定功能整合。
    
#### <a name="lync-server"></a>Lync Server

在部署和管理 Lync Server 內部部署環境：
  
- 佈建伺服器。
    
- 部署 Lync 拓撲。
    
- 更新 Lync server。
    
- 新增或移除拓撲伺服器需要根據使用率。
    
- 實作容錯移轉及災害復原環境。
    
#### <a name="provider-hosted-lync-server"></a>提供者主控的 Lync 伺服器

使用提供者：
  
- 將 Lync Server 整合到您的網路。
    
- 將 Lync Server 整合與其他 Microsoft 產品或自訂的解決方案。
    
- 提供者服務層次協議 (SLA) 與嚴格監視該。
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>部署 Lync 2013 的兩個範例案例

### <a name="directory-synchronization-components-in-microsoft-azure"></a>在 Microsoft Azure 中的目錄同步處理元件

部署 Office 365 目錄同步處理元件，在 Azure 中的更快速地是因為部署虛擬機器上隨選的能力。
  
隨附圖表顯示 Lync Online 與 Azure Active Directory 承租人，以同步處理帳戶名稱和內部部署 Active Directory 環境與 Azure Active Directory 租用戶之間的密碼。
  
 **僅限目錄同步處理伺服器**。 而不是部署在內部部署環境中的 64 位元目錄同步處理伺服器，您可以提供 Azure 中的虛擬機器在網際網路上。
  
 **目錄同步處理 + AD FS**。 此選項可讓您支援 Office 365 同盟身分識別 (SSO)，不會新增至您的內部部署基礎結構的硬體。 它也提供恢復能力，如果內部部署 Active Directory 環境無法使用。 此選項的功能包括：
  
- Azure 虛擬機器以執行目錄整合元件。
    
- AD FS 發佈至 Azure 虛擬機器以執行的 AD FS proxy 透過網際網路。
    
- 從任何位置連線的使用者的用戶端驗證流量是由 AD FS 伺服器與 Azure 虛擬機器與部署的 proxy 處理。
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Lync 整合 Exchange 與 Office 365 中的 SharePoint

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server 與 Exchange Online 和 SharePoint Online

隨附圖表顯示 Office 365 與 Exchange Online 和 SharePoint Online 連線到內部部署 Lync Server 2013 伺服器陣列。
  
此部署的優點可讓您：
  
- 使用 Lync Server 2013 的完整功能集。
    
- 利用您現有內部部署電話設備，例如 Pbx。
    
- 使用 Exchange Online 電子郵件，卸載內部電子郵件伺服器及儲存的負擔。
    
- 使用 SharePoint Online 進行共同作業，卸載的維護負擔內部部署 SharePoint 伺服器。
    
- 使用 Lync、 Exchange 和 SharePoint 整合功能，包括整合通訊 (UM) 在 Office 365 中。
    
#### <a name="exchange-server-with-lync-online"></a>Exchange Server 與 Lync Online

隨附的圖表會顯示與 Lync Online 的 Office 365 連線到內部部署 Exchange Server 伺服器陣列。
  
此部署的優點可讓您：
  
- 利用您現有的 Exchange 基礎結構。
    
- 使用 Lync Online 的目前狀態、 立即訊息和會議功能。
    

