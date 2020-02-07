---
title: Microsoft Azure SharePoint 2013 架構
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 摘要： SharePoint 2013 解決方案可以裝載於 Microsoft Azure 虛擬機器。 了解何種類型的解決方案是很好的調整，以及如何設定 Microsoft Azure，以其中一個主機。
ms.openlocfilehash: ff5837030384a7f10dc36bb9c436394a19521254
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844904"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Microsoft Azure SharePoint 2013 架構

 **摘要：** SharePoint 2013 解決方案可裝載在 Microsoft Azure 虛擬機器。 了解何種類型的解決方案是很好的調整，以及如何設定 Microsoft Azure，以其中一個主機。
  
Azure 是主控 SharePoint Server 2013 解決方案的良好環境。 在大多數情況下，我們建議您 Office 365，但裝載於 Azure 中 SharePoint Server 伺服器陣列可以是很好的選擇，針對特定解決方案。 本文說明如何設計的 SharePoint 解決方案，因此它們是不錯符合在 Azure 的平台。 下列兩個特定解決方案做為範例：
  
- [Microsoft Azure 中的 SharePoint Server 2013 災害復原](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Azure 基礎結構服務的建議的 SharePoint 解決方案

Azure 基礎結構服務是令人讚嘆裝載 SharePoint 解決方案的選項。 某些解決方案會比其他較適合此平台。 下表顯示建議的解決方案。
  
|**解決方案**|**Azure 為何建議此解決方案**|
|:-----|:-----|
|開發和測試環境  <br/> |很容易建立及管理這些環境。  <br/> |
|內部部署 SharePoint 伺服器陣列至 Azure 的災害復原  <br/> |**託管次要資料中心**使用 Azure，而非投資位於不同地區的次要資料中心內。 <br/> **成本較低的災害復原環境**維護及支付比內部損毀修復環境較少的資源。 資源數目取決於您選擇在災害復原環境： 冷待命、 暖待命或熱待命。 <br/> **更多彈性的平台**發生災害時，輕鬆地延展復原 SharePoint 伺服器陣列以符合負載需求。 當您不再需要資源中比例調整。 <br/> 請參閱[Microsoft Azure 中 SharePoint Server 2013 災害復原](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)。  <br/> |
|使用功能並不適用於 Office 365 的縮放比例的網際網路對向網站  <br/> |**業務**專注於建立絕佳的網站，而不是建置基礎結構。 <br/> **利用 Azure 中的彈性**來新增新的伺服器、 調整大小需求的伺服器陣列，並僅支付您需要的資源。 動態機器配置不受支援 （自動調整大小）。 <br/> **使用 Azure Active Directory (AD)** 善用客戶帳戶的 Azure AD。 <br/> **新增 SharePoint 功能不適用於 Office 365**新增深報告及 web analytics。 <br/> 請參閱[Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)。  <br/> |
|若要支援 Office 365 或內部部署環境的應用程式伺服器陣列  <br/> |**建立、 測試和主機應用程式**以支援這兩個內部部署和雲端環境的 Azure 中。 <br/> 而不是購買新的硬體，內部部署環境的 Azure 中的**主機此角色**。 <br/> |
   
內部網路共同作業解決方案和工作負載，請考慮下列選項：
  
- 決定 Office 365 是否符合您的業務需求，或是可以是方案的一部分。 Office 365 提供永遠是最新的豐富的功能集。
    
- 如果 Office 365 不符合所有您的業務需求，請考慮 SharePoint 2013 內部部署從 Microsoft 諮詢服務 (MCS) 的標準實作。 標準架構可供您支援超過一份自訂的速度較快，成本較低，且更容易解決方案。 
    
- 如果標準的實作不符合您的業務需求，請考慮為自訂的內部部署解決方案。
    
- 如果使用雲端平台是很重要的商務需求，請考慮裝載在 Azure 基礎結構服務中的 SharePoint 2013 的標準或自訂實作。 SharePoint 解決方案會比其他非原生 Microsoft 公用雲端平台支援在 Azure 中更加容易。
    
## <a name="before-you-design-the-azure-environment"></a>您在設計 Azure 環境之前

儘管本文使用範例 SharePoint 拓撲，您可以使用這些設計概念與任何 SharePoint 伺服器陣列拓撲。 設計 Azure 環境之前，請使用下列的拓撲、 架構、 容量及效能指引來設計 SharePoint 伺服器陣列：
  
- [適用於 SharePoint 2013 IT 專業人員的架構設計](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [規劃效能和 SharePoint Server 2013 中的容量管理](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>判定 Active Directory 網域類型

每個 SharePoint 伺服器陣列依賴 Active Directory 以伺服器陣列安裝程式提供的管理帳戶。 在這個階段中，有兩個選項可在 Azure 中的 SharePoint 解決方案。 下表說明這些。
  
|**選項**|**描述**|
|:-----|:-----|
|專用的網域  <br/> |您可以將以支援您的 SharePoint 伺服器陣列的 Azure 部署專用和隔離的 Active Directory 網域。 這是很好的選擇的公用對向網際網路網站。  <br/> |
|擴充跨單位連線到內部部署網域  <br/> |當您擴充跨單位連線到內部部署網域時，使用者會存取透過您的內部網路 SharePoint 伺服器陣列，好像它是裝載於內部。 您可以利用您的內部部署 Active Directory 和 DNS 實作。  <br/> 需要建立容錯移轉至從內部部署伺服器陣列的 Azure 中的災害復原環境的跨單位連線。  <br/> |
   
本文包含延伸透過跨單位連線內部部署網域設計的概念。 如果您的解決方案使用專用的網域，您不需要跨單位連線。
  
## <a name="design-the-virtual-network"></a>設計虛擬網路

首先，您必須包含您要放置虛擬機器的子網路的 azure 虛擬網路。 虛擬網路需要私人 IP 位址空間，您指派至子網路的部分。
  
如果您透過跨單位連線 （所需的災害復原環境），將您的內部部署網路延伸到 Azure，您必須選擇尚未在您組織的網路，其中可以包含其他地方使用私人位址空間您的內部部署環境和其他 Azure 虛擬網路。 
  
**圖 1： 內部部署環境與 Azure 虛擬網路**

![為 SharePoint 解決方案設計的 Microsoft Azure 虛擬網路。 Azure 閘道的一個子網路。 虛擬機器的一個子網路。](media/OPrrasconWA-AZarch.png)
  
在此圖表中：
  
- 在 Azure 虛擬網路是圖解-並存至內部部署環境。 在兩個環境已透過跨單位連線，這可以是站台對站 VPN 連線或是 ExpressRoute 尚未連接。
    
- 此時，虛擬網路只包含子網路與任何其他架構的項目。 一個子網路會裝載 Azure 閘道和其他子網路裝載 SharePoint 伺服器陣列，額外一個用於 Active Directory 和 DNS 的層級。
    
## <a name="add-cross-premises-connectivity"></a>新增交叉部署連線能力

部署下一步是建立跨單位連線 （如果這適用於您的解決方案）。 對於跨單位連線，Azure 閘道位於不同的閘道子網路，您必須建立並指派位址空間。 
  
當您規劃的跨單位連線時，您定義，並建立 Azure 閘道和內部部署閘道器裝置的連線。
  
**圖 2： 使用 Azure 閘道和內部部署閘道器裝置來提供內部部署環境與 Azure 之間的站台對站台連線**

![內部部署環境已透過跨單位連線連接至 Azure 虛擬網路，其可以是網站對網站 VPN 連線或是 ExpressRoute](media/AZarch-VPNgtwyconnct.png)
  
在此圖表中：
  
- 將新增至上圖，內部部署環境是透過連接至 Azure 虛擬網路的跨單位連線，可以是站台對站 VPN 連線或是 ExpressRoute。
    
- Azure 閘道為閘道子網路上。
    
- 內部部署環境中包含閘道裝置，例如路由器或 VPN 伺服器。
    
如需規劃和建立跨單位部署虛擬網路的詳細資訊，請參閱[連線到 Microsoft Azure 虛擬網路的內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>新增 Active Directory 網域服務 (AD DS) 和 DNS

對於在 Azure 中的災害復原，您部署 Windows Server AD 和混合式案例，其中是 Windows Server AD 中的 DNS 這兩個內部部署與 Azure 虛擬機器上。
  
**圖 3： 混合式 Active Directory 網域組態**

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](media/AZarch-HyADdomainConfig.png)
  
此圖為基礎的前一個圖表新增至 Windows Server AD 的兩部虛擬機器和 DNS 子網路。 這些虛擬機器是複本網域控制站和 DNS 伺服器。 它們是副檔名為內部部署 Windows Server AD 環境。 
  
下表提供這些虛擬機器，在 Azure 中的設定建議。 供您自己的環境中使用這些做為起點 — 提供充足的儲存您的 Azure 環境不會與您的內部部署環境通訊的地方專用網域。
  
|**Item**|**設定**|
|:-----|:-----|
|在 Azure 中的虛擬機器大小  <br/> |在標準層中的 A1 或 A2 大小  <br/> |
|作業系統  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory 角色  <br/> |AD DS 網域控制站指定為通用類別目錄伺服器。 此設定可透過跨單位連線減少輸出流量。  <br/> 在多網域率較高的變更 （這並不常見） 環境中，設定網域控制站上未提供給同步處理與 Azure，以減少複寫流量中的通用類別目錄伺服器的內部部署。  <br/> |
|DNS 角色  <br/> |安裝及設定的網域控制站上的 DNS 伺服器服務。  <br/> |
|資料磁碟  <br/> |將 Active Directory 資料庫、 記錄檔及 SYSVOL 放在其他的 Azure 資料磁碟上。 不放置這些作業系統的磁碟或 Azure 所提供的暫存磁碟上。  <br/> |
|IP 位址  <br/> |使用靜態 IP 位址，並設定已設定網域控制站之後，將這些位址指派給虛擬網路中的虛擬機器的虛擬網路。  <br/> |
   
> [!IMPORTANT]
> 部署在 Azure 中的 Active Directory 之前，請閱讀[部署 Windows Server Active Directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。 這些協助您判斷解決方案需要不同的架構或不同的組態設定。 
  
## <a name="add-the-sharepoint-farm"></a>新增 SharePoint 伺服器陣列

在適當的子網路上的層級中放置在 SharePoint 伺服器陣列的虛擬機器。
  
**圖 4： 位置的 SharePoint 虛擬機器**

![資料庫伺服器和 SharePoint 伺服器角色加入 SharePoint 伺服器陣列子網路內的 Azure 虛擬網路](media/AZarch-SPVMsinCloudSer.png)
  
此圖為基礎的前一個圖表在其各自的層級中加入 SharePoint 伺服器陣列伺服器角色。
  
- 兩部執行 SQL Server 資料庫虛擬機器建立的資料庫層。
    
- 下列各層的每個執行 SharePoint Server 2013 的兩部虛擬機器： 前端伺服器、 分散式快取伺服器及後端伺服器。
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>設計並微調可用性設定組 」 和 「 容錯網域的伺服器角色

容錯網域是硬體的一種執行哪些角色執行個體中。 在相同的容錯網域內的虛擬機器可以由 Azure 基礎結構更新在同一時間。 或者，可以在同一時間中失敗，因為它們會共用相同的機架。 若要避免相同的容錯網域上具有兩部虛擬機器的風險，您可以設定您的虛擬機器的可用性設定組，這可確保每部虛擬機器位於不同的容錯網域為。 如果三部虛擬機器設定為一個可用性設定組，可確保 Azure 不超過兩個虛擬機器都位於相同的容錯網域。
  
當您設計的 SharePoint 伺服器陣列的 Azure 架構時，設定相同的伺服器角色是一個可用性設定組的一部分。 這可確保您的虛擬機器會散佈於多個容錯網域。
  
**圖 5： 使用 Azure 可用性設定組以提供高可用性 SharePoint 伺服器陣列層級**

![Azure 基礎結構中針對 SharePoint 2013 解決方案的可用性設定組設定](media/AZenv-WinAzureAvailSetsHA.png)
  
此圖呼叫出 Azure 基礎結構內的可用性設定組的設定。 下列角色的每個共用個別的可用性設定組：
  
- Active Directory 和 DNS
    
- Database
    
- 後端
    
- 發佈快取
    
- 前端
    
在 SharePoint 伺服器陣列可能需要為正常調整 Azure 的平台] 中。 若要確保所有元件的高可用性，請確定該伺服器角色的所有設定都相同。
  
以下是範例會顯示標準的網際網路網站架構符合特定容量和效能目標。 本範例精選，下列的架構模型： [SharePoint Server 2013 的網際網路網站搜尋架構](https://go.microsoft.com/fwlink/p/?LinkId=261519)。
  
**圖 6： 規劃在三層式伺服器陣列中的容量和效能目標的範例**

![標準 SharePoint 2013 Internet Sites 架構具有符合特定容量和效能目標的元件配置](media/AZarch-CapPerfexmpArch.png)
  
在此圖表中：
  
- 在三層式伺服器陣列都以表示： 網頁伺服器、 應用程式伺服器與資料庫伺服器。
    
- 三個網頁伺服器進行完全相同設定了多個元件。
    
- 兩部資料庫伺服器的設定都相同。
    
- 三個應用程式伺服器，未設定相同。 這些伺服器角色需要在 Azure 中的可用性微調設定。
    
讓我們看接近應用程式伺服器層級。
  
**圖 7： 應用程式伺服器層之前微調**

![調整為 Microsoft Azure 可用性設定組之前的 SharePoint Server 2013 應用程式伺服器層範例](media/AZarch-AppServtierBefore.png)
  
在此圖表中：
  
- 三部伺服器都包含在應用程式層。
    
- 第一部伺服器包含四個元件。
    
- 第二個伺服器包含三個元件。
    
- 第三個伺服器包含兩個元件。
    
您決定伺服器陣列的效能與容量目標的元件數目。 Azure 能否這種架構，我們將所有的三部伺服器上複寫的四個元件。 這會增加以外的功能所需的效能與容量的元件數目。 缺點是這種設計可確保當這些三部虛擬機器會指派給一個可用性設定組 Azure 的平台] 中的所有四個元件的高可用性。
  
**圖 8： 應用程式伺服器層後微調**

![調整為 Microsoft Azure 可用性設定組之後的 SharePoint Server 2013 應用程式伺服器層範例](media/AZarch-AppServtierAfter.png)
  
這個圖表顯示所有三個應用程式伺服器都設定具有相同的四個元件。
  
當我們將可用性設定組新增至 SharePoint 伺服器陣列層級時，實作已完成。
  
**圖 9： 完成的 SharePoint 伺服器陣列在 Azure 基礎結構服務中**

![Azure Infrastructure Services 中的 SharePoint 2013 伺服器陣列以及虛擬網路、跨單位連線能力、子網路、VM 以及可用性設定組的範例 ](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
此圖顯示實作在 Azure 基礎結構服務中，以提供容錯網域中每一層的伺服器的可用性設定組與 SharePoint 伺服器陣列。
  
## <a name="see-also"></a>另請參閱

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Microsoft Azure 中的 SharePoint Server 2013 災害復原](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


