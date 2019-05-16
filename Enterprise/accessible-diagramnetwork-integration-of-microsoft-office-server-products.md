---
title: 易於存取的圖表-網路整合的 Microsoft Office 伺服器產品
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: 本文是圖表的名為網路整合的 Microsoft Office Server 產品易於存取的文字版本。
ms.openlocfilehash: d63b3b581a03840676393657d6ed641e11046ef9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068559"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>易於存取的圖表-網路整合的 Microsoft Office 伺服器產品

**摘要：** 本文是圖表的名為網路整合的 Microsoft Office Server 產品易於存取的文字版本。
  
此海報提供網路環境，其中包含 Lync Server 2013、 SharePoint 2013 和 Exchange Server 2013 一般圖例。 它也會說明下列都是通用這些產品的網路元素： 遠端和內部存取、 驗證、 用戶端流量，以及路由流量通過共用的裝置。 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Lync、 Exchange、 SharePoint Server 和 Office Web Apps 的高層級概念

### <a name="about-the-design"></a>關於設計

#### <a name="streamlined-network-design"></a>簡化的網路規劃

這種拓撲說明 SharePoint 2013、 Exchange Server 2013 和 Lync Server 2013 的內部網路部署。 它也會顯示使用 Microsoft 雲端式服務，Exchange Online Protection，提供來自網際網路的內送簡易郵件傳送通訊協定 (SMTP) 流量的垃圾郵件和惡意程式碼保護。 
  
此網路設計被精簡到最小的一段的網路功能。 設計不會考慮帳戶額外安全性或基礎結構功能，有些組織可能需要。 
  
此圖中： 
  
- 提供說明輸入和輸出流量通過閘道路由器和負載平衡的用戶端工作階段的流量 （外部及內部） 至適當的 SharePoint、 Exchange 和 Lync 伺服器層範例網路拓撲。 
    
- 顯示使用選用的遠端存取伺服器，例如協力廠商 VPN 閘道或 DirectAccess 伺服器，以提供漫遊或遠端員工的安全通訊。 
    
- 詳細說明 SharePoint、 Exchange 和 Lync 流量從用戶端至每個平台伺服器層。 
    
- 會識別根據用戶端 （例如合作夥伴或員工），以及使用的驗證方法的遠端或內部存取連線的類型。 
    
- 細分 SharePoint、 Exchange 和 Lync 平台所需的伺服器角色，用來識別前端、 應用程式、 資料庫及其他層級。 
    
架構以下用於 SharePoint、 Lync 和 Exchange 不會建議實作這些平台的慣用的方法。 這只是提供範例為根據唯一的網路需求及安全性考量拓撲而有所不同。 
  
#### <a name="gateway-router"></a>閘道路由器

此拓撲中，閘道路由器位於網路邊緣，並將所有內送和外寄流量的路由傳送到及傳送自內部網路。 或者，也有可能閘道路由器，以及負載平衡器所示，例如多層的防火牆之間的差距其他元件。 這種拓撲代表只是一種方式來部署您的網路出許多。 在此組態中，以允許非常特定傳入和傳出 IP 式傳輸的路由器介面上的存取控制清單 (Acl) 設定的閘道。 Acl、 進階的檢查或網路位址轉譯 (NAT) 也可以在其他裝置，例如防火牆，整個網路上執行。 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>負載平衡器和反向 proxy 裝置

您可以使用硬體或軟體負載平衡解決方案來將區段包括 SharePoint 前端網頁伺服器和 Exchange Client Access Server （凱） 流量重新導向。 在某些情況下最好是因為它可以更妥善地執行要求，例如 cookie 或標頭中使用資訊第 7 層硬體型負載平衡器用於持續性需求。 不過，因素，像是成本及增加的使用率，並從這類解決方案的工作負載可能不適合您的特定需求。 請考慮下列重點為跨 SharePoint、 Exchange 和 Lync 的負載平衡： 
  
- SharePoint-針對 SharePoint 2013，您不需要啟用親和性的前端網頁伺服器。 一般而言，這會用於建立自黏工作階段，以及避免多個驗證來自用戶端要求每一部前端網頁伺服器。 在 SharePoint 2013 中新的分散式快取服務儲存及 SharePoint 伺服器陣列的網頁伺服器間分散登入權杖。 
    
- Exchange 位在 Exchange 2013 中，CAS 角色被設計來使用第 4 層負載平衡，分散於傳輸層的要求。 這會大幅降低負載平衡器使用率和工作負載。 
    
- Lync-Lync 集區的工作階段初始通訊協定 (SIP) 流量，建議使用網域名稱系統 (DNS) 負載平衡。 硬體負載平衡 (HLB) 有 Lync Web (HTTPS) 流量。 
    
### <a name="remote-access-options"></a>遠端存取選項

有幾個選項可以發佈內部網路資源的網際網路上的合作夥伴或遠端或漫遊員工提供安全的遠端存取。 這類範例包括反向 proxy、 DirectAccess，與協力廠商 VPN 閘道。 本節稍後討論的遠端存取解決方案是可以用於 SharePoint、 Lync 和 Exchange 或在內部部署中的這些伺服器的任何組合。 不過，某些遠端選項可能無法使用特定的解決方案。 
  
反向 Proxy-反向 proxy 支援流量加密，例如安全通訊端層 (SSL)，並與其您可以發佈內部網路應用程式和 web 資源，以驗證使用者與網際網路上的合作夥伴。 例如，Microsoft Forefront Unified Access Gateway (UAG)。 許多硬體負載平衡器也支援反向 proxy 功能。 不過，有仍然有效使用根據您的需求和需求，例如流量隔離、 安全性分隔和效能最佳化獨立方案的案例。 
  
反向 proxy 的優勢及考量： 
  
- 提供已驗證和安全存取協力廠商或使用者存取內部網路資源 （使用在用戶端和反向 proxy 伺服器之間的 SSL (TCP 443)）。 
    
- Exchange，使用例如 Forefront UAG 的反向 proxy 的好處是預先驗證存取 Exchange 用戶端存取伺服器之前。 使用的遠端存取使用者發佈應用程式，例如 Outlook Web Access (OWA) 可以使用驗證的基本、 NTLM 或 Kerberos 方法之前到達內部網路。 
    
- Exchange 和 SharePoint，像是 Forefront UAG 的解決方案可以終止 SSL 連線，並減少網路資源伺服器的負載時提供的憑證管理的單一資料點。 
    
- Lync，網站 (HTTPS) 流量會通過反向 proxy (TCP 443) 的用戶端通訊。 反向 proxy proxy HTTPS 連線至 Lync Web 服務、 Exchange CAS 和 Office Web Apps。 Lync Server 2013 不支援 UAG。 
    
DirectAccess-依賴網際網路通訊協定安全性 (IPsec) 進行驗證和加密 DirectAccess 用戶端與伺服器之間的流量的遠端存取的技術。 DirectAccess 提供不必初始連線漫遊及遠端員工同時存取網際網路和內部網路資源。 
  
DirectAccess 要考慮的事項： 
  
- DirectAccess 使用 IPsec 保護流量 （通訊協定 50 51 和 UDP 500） DirectAccess 用戶端與伺服器之間。 
    
- Windows Server 2012 的 DirectAccess 和 Windows 8 不需要公開金鑰基礎結構 (PKI) 部署的伺服器和用戶端驗證。 
    
- 我們建議您不要使用 Lync Server 2013 中的 DirectAccess，因為 IPsec 加密和解密相關聯的音訊和視訊延遲問題。 
    
    VPN 閘道-一般 VPN 閘道提供遠端存取連線中的遠端存取用戶端電腦以邏輯方式投射通道及使用者起始連線到內部網路。 您可以使用整合 Windows Server 2012 或幾個協力廠商解決方案中的遠端存取提供安全的存取內部網路的漫遊或遠端員工。 Lync 不建議 VPN。 遠端 Lync 流量應該使用 Edge Server，並將 split 通道。 
    
### <a name="domain-name-system-dns-considerations"></a>網域名稱系統 (DNS) 考量

您需要規劃的一組 DNS 記錄，可讓網際網路和內部網路 DNS 名稱解析為適當的 IP 位址的使用者。 
  
- 為網際網路型合作夥伴和漫遊或遠端員工，註冊網際網路 DNS 伺服器的 DNS 記錄提供一組公用 IP 位址對應至閘道路由器，Lync Edge Server，一組虛擬 IP 位址 (Vip) 的解析度負載平衡器，並視 DirectAccess 或 VPN 閘道。 
    
- 對於內部網路為基礎的使用者，註冊內部網路 DNS 伺服器的 DNS 記錄提供的虛擬 IP 位址 (Vip) 的解析度負載平衡器上 SharePoint、 Lync 和 Exchange 資源的存取權。 
    
- DirectAccess 用戶端會使用內部網路 DNS 伺服器名稱對應至內部網路 DNS 命名空間和網際網路 DNS 伺服器的名稱，則否。 為了簡化 DirectAccess 的作業，請考慮使用內部網路和網際網路型的名稱會使用不同的 DNS 命名空間的分割 DNS 實作。 例如，使用網際網路命名空間和命名空間的內部網路 corp.contoso.com contoso.com。 
    
- Exchange 會使用分割 DNS 模型 IP 解析度的主機上可公開路由傳送流量從公司網路上的不同位置。 在最低限度下，您需要有的 OWA、 自動探索、 ActiveSync Url 的 DNS 記錄，用戶端流量和輸入郵件的 MX 記錄。 
    
- 如果您使用 Exchange Online Protection (EOP)，您的 MX 記錄會指向該服務，而不是您的 Exchange 伺服器陣列。 
    
- Exchange，則必須證明擁有權 TXT 記錄您在公用 DNS，以及同盟組織識別碼來設定同盟共用。 
    
- 遠端存取 VPN 用戶端可以設定成使用僅限內部網路 DNS 伺服器，當 VPN 連線的遠端存取為作用中。 
    
### <a name="diagram-description"></a>圖表描述

此圖提供說明輸入和輸出流量通過閘道路由器和負載平衡的用戶端工作階段的流量 （外部及內部） 至適當的 SharePoint、 Exchange 和 Lync 伺服器層範例網路拓撲。 此圖說明可分成兩個部分： 
  
- 元件圖所示的描述 
    
- 描述如何流量進入元件至 SharePoint、 Exchange、 Lync 與 Office Web Apps server 層級。 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>元件圖所示的描述

#### <a name="user-types"></a>使用者類型

有四種不同類型的使用者、 外的網路和雲端服務的三個，一個內部，其中包括： 
  
- 合作夥伴公司 （企業對企業）-外部 
    
- 個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部 
    
- 漫遊及遠端員工外部 
    
- 內部員工 
    
#### <a name="cloud-based-email-traffic"></a>雲端式電子郵件流量

沒有 SMTP 型電子郵件流量，網際網路郵件主機或 Exchange Online Protection 的基於雲端的元件。 
  
#### <a name="authentication-for-external-access"></a>外部存取認證

沒有一組特定的 Lync、 SharePoint 和 Exchange 的每個使用者類型的驗證程序。 在本文件稍後詳細說明他們。 
  
#### <a name="gateway-router-with-acls"></a>Acl 的閘道路由器

閘道路由器位於網路邊緣，並將所有內送和外寄流量的路由傳送到及傳送自內部網路。 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Lync 和 SharePoint 的遠端存取伺服器

此拓撲包含 Lync Edge server，以及 SharePoint VPN 閘道或 DirectAccess 伺服器。 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>負載平衡器和反向 proxy 裝置

您可以使用硬體或軟體負載平衡解決方案來將區段包括 SharePoint 前端網頁伺服器和 Exchange Client Access Server （凱） 流量重新導向。 這種拓撲在負載平衡器中顯示 Lync VIP、 SharePoint VIP 和 Exchange VIP 元件。 
  
#### <a name="servers"></a>伺服器

有四部伺服器： Lync、 SharePoint、 Exchange 和 Office Web Apps Server。 每一部伺服器可以有三種層級： 前端、 用戶端存取層、 應用程式層與資料庫/儲存層。
  
#### <a name="front-end-client-access-tier"></a>前端、 用戶端存取層

這一層具有四個的所有伺服器上的元件： 
  
- Lync 集區 （前端）。 此圖顯示兩個 Lync 資料庫。 
    
- SharePoint 前端和分散式快取。 此圖顯示三個 SharePoint 資料庫。 
    
- Exchange CAS。 此圖顯示兩個 Exchange 資料庫。 
    
- Office Web Apps Server。 此圖顯示兩個 Office Web 應用程式資料庫。 
    
#### <a name="application-tier"></a>應用程式層

這一層只能在 SharePoint 伺服器上有元件： 
  
- 搜尋查詢、 索引 （系統）。 此圖顯示三個 SharePoint 資料庫。 
    
- 批次處理程序。 此圖顯示三個 SharePoint 資料庫。 
    
#### <a name="databasestorage-tier"></a>資料庫/儲存層

這一層 Lync、 SharePoint 和 Exchange 伺服器上有元件： 
  
- Lync 資料庫 （後端）。 此圖顯示三個 Lync 資料庫。 
    
- SharePoint 資料庫。 此圖顯示三個 SharePoint 資料庫。 
    
- Exchange 信箱伺服器。 此圖顯示兩個 Exchange 信箱伺服器。 
    
如需安裝在每個 SharePoint 伺服器角色上元件的詳細資訊，請參閱 < <b0>SharePoint 2013 的簡化拓撲</b0>。 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>如何流量進入元件至不同的伺服器層級的描述

本章節說明使用者要求瀏覽的網路拓撲的方式。 
  
#### <a name="authentication-and-routing-for-external-access"></a>驗證和外部存取的路由

有三種不同的網路和雲端服務，其中包含外的用戶端： 
  
- 合作夥伴公司 （企業對企業）-外部 
    
- 個別合作夥伴 （SharePoint 和匿名 (Lync)）-外部 
    
- 漫遊及遠端員工外部 
    
是個別說明的驗證及路由的程序的每個外部使用者類型。 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>合作夥伴公司 （企業對企業） (https://partnerweb.contoso.com)

- Lync： 與 Skype 和搭配 AOL 的公用 IM 連線能力 (PIC) 其他組織的同盟信任。 Lync 同盟流量通過閘道路由器至 Lync Edge Server、 Lync vip （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。 
    
- SharePoint 的安全： 信任的協力廠商身分識別提供者使用 SAML 驗證。 SharePoint 用戶端流量會通過閘道路由器，SharePoint vip （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint Server。 
    
- Exchange： 相互驗證 TLS 郵件流量，SAML 驗證的同盟共用。 Exchange 用戶端流量會通過閘道路由器，Exchange vip （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。 
    
- SMTP 流量會透過閘道路由器，以及透過 Exchange VIP （負載平衡器/反向 proxy 伺服器） 向 Exchange 伺服器。 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>個別合作夥伴 (SharePoint) 和匿名 (Lync) (https://partnerweb.contoso.com和https://meet.contoso.com)

- Lync： 匿名使用者只可以加入依員工的 Lync 會議。 Lync 同盟流量通過閘道路由器至 Lync Edge Server、 Lync vip （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。 
    
- SharePoint 的安全： 使用 SAML 驗證或表單型驗證的信任的合作夥伴身分識別提供者。 SharePoint 用戶端流量會通過閘道路由器，SharePoint vip （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint Server。 
    
- Exchange： 不適用。 
    
- Lync Web 流量會通過閘道路由器至 Lync Edge Server，Lync vip （負載平衡器/反向 proxy 伺服器），硬體負載平衡器，也就是必要的 HTTPS 流量，並再 Lync Server。 
    
#### <a name="roaming-and-remote-employees"></a>漫遊及遠端員工

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* Exchange URL 有下列虛擬目錄： 自動探索、 ecp，EWS、 Microsoft Server ActiveSync、 OAB，owa，PowerShell 
  
- Lync: TLS DSK] 或 [NTLM 驗證。 Lync 用戶端流量通過閘道路由器至 Lync Edge Server、 Lync vip （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。 
    
- SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。 SharePoint 用戶端流量會通過 VPN 閘道或 DirectAccess 伺服器至 SharePoint VIP （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint server。 
    
- Exchange： 透過 SSL (ActiveSync 自動探索)、 表單型驗證 (OWA) 的基本驗證。 Exchange 用戶端流量會通過閘道路由器，Exchange vip （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。 
    
- Lync 用戶端流量會通過閘道路由器 Lync vip （負載平衡器/反向 proxy 伺服器） 至硬體負載平衡器，也就是必要的 HTTPS 流量，然後再到 Lync Server。 
    
#### <a name="authentication-for-internal-access"></a>供內部存取的驗證

#### <a name="internal-employees"></a>內部員工

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync: Kerberos]、 [TLS DSK 或 [NTLM 驗證。 Lync 用戶端流量會移至 Lync VIP （負載平衡器/反向 proxy 伺服器），然後再到 Lync Server。 
    
- SharePoint: Active Directory 網域服務 (AD DS)、 表單型驗證或 SAML 驗證。 SharePoint 用戶端流量會移至 SharePoint VIP （負載平衡器/反向 proxy 伺服器），然後再到 SharePoint Server。 
    
- Exchange: AD DS 中，表單型驗證。 Exchange 用戶端流量會移至 Exchange VIP （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。 
    
- Lync 用戶端流量會移到 Lync VIP （負載平衡器/反向 proxy 伺服器） 至硬體負載平衡器，也就是必要的 HTTPS 流量，然後再到 Lync Server。 
    
#### <a name="cloud-based-email-traffic"></a>雲端式電子郵件流量

SMTP 型電子郵件流量的雲端架構元件是由網際網路郵件主機或 Exchange Online Protection 所組成。
  
這些元件會使用 SMTP 在網路上移動電子郵件流量。 流量會通過閘道路由器，Exchange vip （負載平衡器/反向 proxy 伺服器），然後再向 Exchange 伺服器。 
  
### <a name="network-traffic-legend"></a>網路流量圖例

[圖例] 方塊以圖形方式顯示不同類型的流量，如下所示的圖表中不同的彩色行上所述： 
  
- 綠色線條： Lync SIP 流量 
    
- 藍色線條： Lync Web 流量 
    
- 紫色線條： SharePoint 用戶端流量 
    
- 橘色線條： Exchange 用戶端流量 
    
- 灰色列： Exchange 內部部署與 Exchange Online Protection 之間的 Exchange 郵件伺服器流量。 
    
在 [圖例] 方塊中也說明不同類型的流量以及它們所使用的連接埠。 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Lync SIP 流量和 Lync web 流量

Lync Edge Server 會使用下列連接埠的外部使用者通訊： 
  
- IM 訊號流量 （SIP/簡單）： TCP 連接埠 443 （輸入流量開啟） 
    
- Web 會議流量 (PSOM): TCP 443 （輸入流量的 [開啟]） 
    
- A / V 流量 (SRTP): TCP 443、 UDP 3478 和 TCP 50000-59999 （選用） （開放輸入和輸出流量） 
    
Lync Edge Server 同盟的通訊使用下列連接埠： 
  
- TCP 連接埠 5061 (SIP)、 5269 (XMPP)，443 和 UDP 3478 (SRTP) （開放輸入和輸出流量） 
    
#### <a name="sharepoint-client-traffic"></a>SharePoint 用戶端流量

SharePoint 可以使用 TCP 連接埠 443 (SSL) 加密通訊用戶端與負載平衡器。 來自網際網路的外部存取，此連接埠必須開啟閘道路由器 （或外部防火牆） 上的輸入和輸出流量。 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Exchange 用戶端流量，且 Exchange 郵件伺服器流量

Exchange 會使用 TCP 連接埠 25 (SMTP) 伺服器對伺服器通訊。 連接埠 443 (HTTPS) 上會處理大部分的用戶端流量 （OWA、 ActiveSync、 自動探索、 Outlook 無所不在）。 如果您有 POP 或 IMAP 用戶端，連接埠 110 (POP3)，995 (加密 POP3)、 143 (IMAP4)，993 (加密 IMAP4)、 及 587 (SMTP) 也可用來支援這些用戶端。 
  
#### <a name="more-on-lync-network-traffic"></a>開啟 Lync 網路流量？

了解如何 Lync Server 可以協助您的組織提供立即訊息、 web 會議、 應用程式共用，以及語音通訊。 如需詳細資訊，請參閱 < <b0>Microsoft Lync Server 2013 通訊協定的工作負載海報</b0>。 
  
海報也包含 QR 碼，來存取這項資訊。 
  

