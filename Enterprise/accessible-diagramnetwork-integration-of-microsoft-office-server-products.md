---
title: 存取圖表-網路整合的 Microsoft Office 伺服器產品
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: 本文是圖表的名為網路整合的 Microsoft Office Server 產品可存取的文字版本。
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504426"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>存取圖表-網路整合的 Microsoft Office 伺服器產品

**摘要：** 本文是圖表的名為網路整合的 Microsoft Office Server 產品可存取的文字版本。
  
這張海報提供網路環境包含 Lync Server 2013、 SharePoint 2013 與 Exchange Server 2013 一般圖。它也會說明這些產品都通用的下列網路元素： 遠端及內部存取、 驗證、 用戶端流量及共用裝置透過路由流量。 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Lync、 Exchange、 SharePoint Server 及 Office Web Apps 的高層級概念

### <a name="about-the-design"></a>關於設計

#### <a name="streamlined-network-design"></a>簡化的網路設計

SharePoint 2013、 Exchange Server 2013 及 Lync Server 2013 的內部網路部署進行說明這種拓撲。它也會顯示使用 Microsoft 雲端式服務、 Exchange Online Protection，提供從網際網路輸入簡易郵件傳送通訊協定 (SMTP) 流量的垃圾郵件和惡意程式碼保護。 
  
此網路設計會簡化到最小的一段網路功能。設計不會將列入帳戶額外安全性或基礎結構功能的某些組織可能會需要。 
  
此圖中： 
  
- 提供說明透過閘道路由器和負載平衡的用戶端工作階段 （外部和內部） 至流量適當 SharePoint、 Exchange 及 Lync server 層的輸入和輸出流量範例網路拓撲。 
    
- 會顯示使用選用的遠端存取伺服器，例如協力廠商 VPN 閘道或 DirectAccess 伺服器，以提供漫遊或遠端員工的安全通訊。 
    
- 詳細說明 SharePoint、 Exchange 及 Lync 流量從用戶端至每個平台伺服器層。 
    
- 會識別根據用戶端 （例如協力廠商或員工） 和使用的驗證方法的遠端或內部存取連線的類型。 
    
- 細分的 SharePoint、 Exchange 及 Lync 的平台所需的伺服器角色，用來識別前端、 應用程式、 資料庫及其他層級。 
    
架構以下用於 SharePoint、 Lync 和 Exchange 不會建議的實作這些平台的慣用的方法。它只是提供一個範例為根據唯一的網路需求及安全性考量拓撲而有所不同。 
  
#### <a name="gateway-router"></a>閘道路由器

這種拓撲的閘道路由器置於桌網路邊緣和路由傳送所有內送和外寄流量到與內部網路。或者，也有可能閘道路由器和負載平衡器所示，例如多層的防火牆之間的差距其他元件。這種拓撲代表來部署您的網路移出許多的只是一種方式。在此設定，閘道設定以允許非常特定內送和外寄 IP 型流量路由器介面上的存取控制清單 (Acl)。也可在其他裝置，例如防火牆，整個網路上執行 Acl、 進階的檢查、 或網路位址轉譯 (NAT)。 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>負載平衡器和反向 proxy 裝置

硬體或軟體負載平衡解決方案可用於將區段包含 SharePoint 前端網頁伺服器和 Exchange Client Access Server （類別） 流量重新導向。在某些情況下它是用於第 7 層硬體為基礎的負載平衡器持續性需求可以更妥善地執行的要求，例如 cookie 或標頭中使用的資訊。不過，因素 like 成本並提升的使用情況和這類方案中的工作負載可能不是您的特定需求的取捨。請考慮下列點跨 SharePoint、 Exchange 及 Lync 的負載平衡： 
  
- 適用於 SharePoint 2013 的 SharePoint-您不需要啟用的前端網頁伺服器的相關性。一般而言，這就用於建立自黏工作階段與避免多個驗證要求用戶端至每部前端網頁伺服器。在 SharePoint 2013 中新的分散式快取服務儲存及分散登入 token 每個 SharePoint 伺服器陣列的網頁伺服器。 
    
- 在 Exchange 2013]、 [CAS 角色中的 Exchange 層的設計使用階層 4 負載平衡散佈傳輸層級的要求。這會大幅降低負載平衡器使用量及工作負載。 
    
- Lync-工作階段初始通訊協定 (SIP) 流量 Lync 集區的建議使用網域名稱系統 (DNS) 負載平衡。硬體負載平衡 (HLB) 是必要的 Lync Web (HTTPS) 流量。 
    
### <a name="remote-access-options"></a>遠端存取選項

有數個選項可以發佈內部網路資源的網際網路上的協力廠商或遠端或漫遊員工提供安全的遠端存取。這類包括反向 proxy、 DirectAccess 及第三方 VPN 閘道。本節稍後討論的遠端存取解決方案為可能性 SharePoint、 Lync 和 Exchange 或在內部部署中的這些伺服器的任何組合。不過，某些遠端選項可能無法運作的特定的解決方案。 
  
反向 Proxy-反向 proxy 支援流量加密，例如安全通訊端階層 (SSL)，並與其您可以發佈內部網路應用程式與 web 資源以驗證使用者與在網際網路上的協力廠商。例如，Microsoft Forefront Unified Access Gateway (UAG)。許多硬體負載平衡器也支援反向 proxy 功能。但有使用根據您的需求和需求，例如流量隔離、 安全性劃分和效能最佳化的獨立解決方案仍然有效案例。 
  
反向 proxy 的好處及考量： 
  
- 提供已驗證及安全存取的協力廠商或使用者存取內部網路資源 （使用用戶端和反向 proxy 伺服器之間的 SSL (TCP 443)）。 
    
- Exchange 使用例如 Forefront UAG 的反向 proxy 的好處為預先驗證之前存取 Exchange 用戶端存取伺服器。使用的遠端存取使用者在例如 Outlook Web Access (OWA) 驗證的基本、 [NTLM] 或 Kerberos 方法之前達到內部網路發佈應用程式。 
    
- Exchange 和 SharePoint、 like Forefront UAG 的解決方案可以終止 SSL 連線並減少同時提供的憑證管理的單一資料點的內部網路資源伺服器的負載。 
    
- For Lync Web (HTTPS) 流量會通過反向 proxy (TCP 443) 的用戶端通訊。反向 proxy proxy HTTPS Lync Web 服務、 Exchange CAS 和 Office Web Apps 的連線。Lync Server 2013 不支援 UAG。 
    
DirectAccess-依賴網際網路通訊協定安全性 (IPsec) 進行驗證和加密 DirectAccess 用戶端與伺服器之間的流量遠端存取技術。DirectAccess 提供不必起始連線漫遊和遠端員工同時存取網際網路及內部網路的資源。 
  
DirectAccess 要考慮的事項： 
  
- DirectAccess 使用受保護的 IPsec 流量 （50 和 51 及 UDP 500 通訊協定） DirectAccess 用戶端與伺服器之間。 
    
- Windows Server 2012 的 DirectAccess 及 Windows 8 不需要公開金鑰基礎結構 (PKI) 部署的伺服器與用戶端驗證。 
    
- 建議您針對 Lync Server 2013 搭配使用 DirectAccess 由於 IPsec 加密與解密相關聯的音訊和視訊延遲問題。 
    
    VPN 閘道-一般 VPN 閘道提供在其中的遠端存取用戶端電腦以邏輯方式投射到通道和使用者起始連線到內部網路的遠端存取連線。整合 Windows Server 2012 或數個協力廠商解決方案中的遠端存取可用來提供安全的存取內部網路的漫遊或遠端員工。Lync 不建議使用 VPN。遠端 Lync 流量應使用的 Edge Server，並將 split 通道。 
    
### <a name="domain-name-system-dns-considerations"></a>網域名稱系統 (DNS) 考量

您需要規劃的允許網際網路及內部網路使用者解析 DNS 名稱為適當的 IP 位址的 DNS 記錄集。 
  
- 網際網路為基礎的協力廠商和漫遊或遠端員工、 登錄與網際網路 DNS 伺服器的 DNS 記錄提供之公用 IP 位址對應至閘道路由器 Lync Edge Server 的虛擬 IP 位址 (Vip) 集的解決方法在負載平衡器和 DirectAccess 或 VPN 閘道所需。 
    
- 內部網路型使用者、 登錄與內部網路的 DNS 伺服器的 DNS 記錄提供解析之虛擬 IP 位址 (Vip) 集負載平衡器上存取 SharePoint、 Lync 和 Exchange 的資源。 
    
- DirectAccess 用戶端使用的內部網路的 DNS 伺服器的名稱對應的內部網路 DNS 命名空間和網際網路 DNS 伺服器的名稱未執行。為了簡化 DirectAccess 的作業，請考慮使用不同的 DNS 命名空間的內部網路和網際網路式名稱分割 DNS 實作使用。例如，使用 contoso.com 網際網路命名空間和 corp.contoso.com 內部網路命名空間。 
    
- Exchange 會使用分割 DNS 模型 IP 解析度主機上可公開路由流量與公司網路上的不同位置。在最低限度下，您需要有 OWA、 自動探索、 ActiveSync Url 的 DNS 記錄的用戶端流量和輸入郵件的 MX 記錄。 
    
- 如果您使用的 Exchange Online Protection (EOP)，您的 MX 記錄指向該服務，而不是您的 Exchange 伺服器陣列。 
    
- Exchange，則必須證明擁有權 TXT 記錄在公用 DNS 中，以及設定同盟組織識別碼同盟共用。 
    
- 遠端存取 VPN 用戶端可以設定為使用中的遠端存取 VPN 連線時使用的內部網路 DNS 伺服器。 
    
### <a name="diagram-description"></a>圖表描述

此圖提供範例網路拓撲說明透過閘道路由器和負載平衡的用戶端工作階段 （外部和內部） 至流量適當 SharePoint、 Exchange 及 Lync server 層的輸入和輸出流量。此圖說明可分為兩個部分： 
  
- 圖所示的元件的描述 
    
- 描述如何流量進入元件至 SharePoint、 Exchange、 Lync 及 Office Web Apps server 層。 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>圖所示的元件的描述

#### <a name="user-types"></a>使用者類型

有四種不同類型的使用者、 外部網路和雲端服務的三個與一部內部，其中包括： 
  
- 合作夥伴公司 (business-business)-外部 
    
- 個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部 
    
- 漫遊和遠端員工外部 
    
- 內部員工 
    
#### <a name="cloud-based-email-traffic"></a>雲端式電子郵件流量

有 SMTP 式電子郵件流量架設網際網路郵件或 Exchange Online Protection 的雲端式元件。 
  
#### <a name="authentication-for-external-access"></a>進行外部存取的驗證

有一組特定的 Lync、 SharePoint 及 Exchange 每個使用者所輸入的驗證程序。本文稍後的更詳細地說明它們。 
  
#### <a name="gateway-router-with-acls"></a>含 Acl 的閘道路由器

閘道路由器置於桌網路邊緣和路由傳送所有內送和外寄流量到與內部網路。 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Lync 和 SharePoint 的遠端存取伺服器

此拓撲包含 Lync Edge 伺服器與 SharePoint VPN 閘道或 DirectAccess 伺服器。 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>負載平衡器和反向 proxy 裝置

硬體或軟體負載平衡解決方案可用於將區段包含 SharePoint 前端網頁伺服器和 Exchange Client Access Server （類別） 流量重新導向。這種拓撲的負載平衡器中顯示 Lync VIP、 SharePoint VIP 和 Exchange VIP 元件。 
  
#### <a name="servers"></a>伺服器

有四部伺服器： Lync、 SharePoint、 Exchange 和 Office Web Apps Server。每一個伺服器可以有三層： 前端、 用戶端存取層、 應用程式層與資料庫/儲存層。
  
#### <a name="front-end-client-access-tier"></a>前端、 用戶端存取層

此層有四個的所有伺服器上的元件： 
  
- Lync 集區 （前端）。此圖顯示兩個 Lync 資料庫。 
    
- SharePoint 前端和分散式快取。此圖顯示三個 SharePoint 資料庫。 
    
- Exchange CAS。此圖顯示兩個 Exchange 資料庫。 
    
- Office Web Apps Server。此圖顯示兩個 Office Web 應用程式資料庫。 
    
#### <a name="application-tier"></a>應用程式層

此層 SharePoint 伺服器上只包含元件： 
  
- 搜尋查詢、 索引 （系統）。此圖顯示三個 SharePoint 資料庫。 
    
- 批次處理。此圖顯示三個 SharePoint 資料庫。 
    
#### <a name="databasestorage-tier"></a>資料庫/儲存層

此層 Lync、 SharePoint 及 Exchange 伺服器上有元件： 
  
- Lync 資料庫 （後端）。此圖顯示三個 Lync 資料庫。 
    
- SharePoint 資料庫。此圖顯示三個 SharePoint 資料庫。 
    
- Exchange 信箱伺服器。此圖顯示兩個的 Exchange 信箱伺服器。 
    
如需在每個 SharePoint 伺服器角色上安裝的元件的詳細資訊，請參閱 ＜ [SharePoint 2013 的簡化拓撲](https://aka.ms/Ma5cgk)。 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>說明的方式流量進入元件至不同的伺服器層

本節說明如何透過網路拓撲移動使用者要求。 
  
#### <a name="authentication-and-routing-for-external-access"></a>驗證與外部存取的路由

有三種不同的網路和雲端服務，其中包含外部的用戶端： 
  
- 合作夥伴公司 (business-business)-外部 
    
- 個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部 
    
- 漫遊和遠端員工外部 
    
驗證並針對每個外部使用者類型的傳閱程序說明個別。 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>合作夥伴公司 （商務對商務） (https://partnerweb.contoso.com)

- 與其他組織 Skype 和 aol 的公用 IM 連線 (PIC) Lync： 同盟信任。Lync 同盟流量會通過閘道路由器 Lync Edge server、 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。 
    
- SharePoint： 信任的協力廠商身分識別提供者使用 SAML 驗證。SharePoint 用戶端流量會通過閘道路由器，SharePoint VIP （負載平衡器/反向 proxy 伺服器）]、 [SharePoint 伺服器。 
    
- Exchange： 相互驗證 TLS 的郵件流量、 SAML 驗證同盟共用。Exchange 用戶端流量會通過閘道路由器 Exchange VIP （負載平衡器/反向 proxy 伺服器）]、 [Exchange 伺服器。 
    
- SMTP 流量會前往 Exchange server 透過閘道路由器和透過 Exchange VIP （負載平衡器/反向 proxy 伺服器）。 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>個別合作夥伴 (SharePoint) 和匿名 (Lync) （https://partnerweb.contoso.com 和 https://meet.contoso.com）

- Lync： 匿名使用者只可加入員工所召集的 Lync 會議。Lync 同盟流量會通過閘道路由器 Lync Edge server、 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。 
    
- SharePoint： 搭配 SAML 驗證或表單型驗證的信任的合作夥伴身分識別提供者。SharePoint 用戶端流量會通過閘道路由器，SharePoint VIP （負載平衡器/反向 proxy 伺服器）]、 [SharePoint 伺服器。 
    
- Exchange： 不適用。 
    
- Lync Web 流量會通過閘道路由器 Lync Edge server]，以 Lync VIP （負載平衡器/反向 proxy 伺服器），用於 HTTPS 流量所需的硬體負載平衡器]、 [Lync Server。 
    
#### <a name="roaming-and-remote-employees"></a>漫遊和遠端員工

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com * 
    
6. https://dial.contoso.com *
    
7. https://meet.contoso.com *
    
* Exchange URL 有下列的虛擬目錄： 自動探索、 ecp、 EWS、 Microsoft Server ActiveSync、 OAB、 owa、 PowerShell 
  
- Lync: TLS DSK] 或 [NTLM 驗證。Lync 用戶端流量會通過閘道路由器 Lync Edge server、 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。 
    
- SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。SharePoint 用戶端流量會通過 VPN 閘道或 DirectAccess 伺服器，SharePoint VIP （負載平衡器/反向 proxy 伺服器）]、 [SharePoint 伺服器。 
    
- Exchange： 透過 SSL (ActiveSync 自動探索)、 表單型驗證 (OWA) 的基本驗證。Exchange 用戶端流量會通過閘道路由器 Exchange VIP （負載平衡器/反向 proxy 伺服器）]、 [Exchange 伺服器。 
    
- Lync 用戶端流量會通過至 Lync VIP （負載平衡器/反向 proxy 伺服器），用於 HTTPS 流量所需的硬體負載平衡器]、 [Lync Server 的閘道路由器。 
    
#### <a name="authentication-for-internal-access"></a>內部存取權的驗證

#### <a name="internal-employees"></a>內部員工

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com * 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync: Kerberos]、 [TLS-DSK 或 [NTLM 驗證。Lync 用戶端流量會 Lync VIP （負載平衡器/反向 proxy 伺服器）]、 [Lync Server。 
    
- SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。SharePoint 用戶端流量會移至 SharePoint VIP （負載平衡器/反向 proxy 伺服器），然後至 SharePoint 伺服器。 
    
- Exchange： AD DS 中，表單型驗證。Exchange 用戶端流量會移至 Exchange VIP （負載平衡器/反向 proxy 伺服器），然後 Exchange 伺服器。 
    
- Lync 用戶端流量前往 Lync VIP （負載平衡器/反向 proxy 伺服器），用於 HTTPS 流量所需的硬體負載平衡器]、 [Lync Server。 
    
#### <a name="cloud-based-email-traffic"></a>雲端式電子郵件流量

SMTP 式電子郵件流量的雲端架構元件是由架設網際網路郵件或 Exchange Online Protection 所組成。
  
這些元件移動電子郵件流量網路使用 SMTP。流量會通過閘道路由器 Exchange VIP （負載平衡器/反向 proxy 伺服器）]、 [Exchange 伺服器。 
  
### <a name="network-traffic-legend"></a>網路流量圖例

[圖例] 方塊中以圖形顯示不同類型的流量，如下所示在不同的彩色線條圖所示： 
  
- 綠色線條： Lync SIP 流量 
    
- 藍色線條： Lync Web 流量 
    
- 紫色線條： SharePoint 用戶端流量 
    
- 橘色線條： Exchange 用戶端流量 
    
- 灰色列： 之間 Exchange 內部部署和 Exchange Online Protection Exchange 信箱伺服器的流量。 
    
[圖例] 方塊中也說明不同類型的流量，所使用的連接埠。 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Lync SIP 流量及 Lync web 流量

Lync Edge Server 會使用下列連接埠的外部使用者通訊： 
  
- IM 訊號流量 （SIP/簡易）： TCP 連接埠 443 （輸入流量開放） 
    
- Web 會議流量 (PSOM)： TCP 443 （輸入流量的 [開啟]） 
    
- A / V 流量 (SRTP)： TCP 443、 UDP 3478 和 TCP 50000-59999 （選用） （開放的輸入和輸出流量） 
    
Lync Edge Server 進行同盟通訊使用下列連接埠： 
  
- TCP 連接埠 5061 (SIP) 5269 (XMPP) 443 和 UDP 3478 (SRTP) （開放的輸入和輸出流量） 
    
#### <a name="sharepoint-client-traffic"></a>SharePoint 用戶端流量

SharePoint 可以用於用戶端與負載平衡器間加密通訊的 TCP 連接埠 443 (SSL)。從網際網路的外部存取，此連接埠必須開啟閘道路由器 （或外部防火牆） 上的輸入和輸出流量。 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Exchange 用戶端流量及 Exchange 信箱伺服器的流量

Exchange 會使用 TCP 連接埠 25 (SMTP) 伺服器對伺服器通訊。大部分的用戶端流量 （OWA、 ActiveSync、 自動探索、 「 Outlook 無所不在 」） 會處理透過連接埠 443 (HTTPS)。如果您有 POP 或 IMAP 用戶端，連接埠 110 (POP3)、 995 (加密 POP3)、 143 (IMAP4)、 993 (加密 IMAP4) 及 587 (SMTP) 也可用於支援這些用戶端。 
  
#### <a name="more-on-lync-network-traffic"></a>在 Lync 網路流量？

了解 Lync Server 能如何協助組織提供立即訊息、 web 會議、 應用程式共用和語音通訊。如需詳細資訊，請參閱[Microsoft Lync Server 2013 通訊協定工作量海報 （英文）](https://aka.ms/G5jzjo)。 
  
海報也包含說明 QR 程式碼來存取此資訊。 
  

