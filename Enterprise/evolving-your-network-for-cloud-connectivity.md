---
title: 將您的網路提升為雲端連線網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 摘要： 了解如何雲端採用需要網路基礎結構投資的新方法。
ms.openlocfilehash: 16dbbafe46e903fa41163e12c1741a45b47c5f45
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915138"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>將您的網路提升為雲端連線網路

 **摘要：** 了解如何雲端採用需要網路基礎結構投資的新方法。
  
雲端移轉改變了公司網路內外部的流量大小與本質。它也會影響降低安全性風險的方法。
  
- 雲端之前
    
    大部分的網路基礎結構投資已所花費的確保可用、 可靠和效能低落連線到內部部署資料中心。許多組織的網際網路連線能力未內部商務作業的關鍵。網路界限已主要防禦安全性缺口。
    
- 在雲端之後
    
    新增及已移轉的產能與雲端中執行的 IT 工作量，基礎結構投資移動從內部部署至網際網路連線能力，現在有重大的內部企業營運資料中心。同盟的連線騰出安全性策略來保護身分識別和資料通過其網路與 Microsoft 雲端服務連線點。
    
網路基礎結構投資的開頭連線。其他投資取決於雲端服務的類別。
  
- **軟體即服務 (SaaS)** Microsoft saas 和服務包括 Office 365、 Microsoft Intune 和 Microsoft Dynamics 365。Saas 和服務使用者所擁有的成功採用取決於高可用性和效能低落連線至網際網路，或直接 Microsoft 雲端服務。
    
    網路架構著重於可靠而變得多餘連線和容許足夠的頻寬。進行中的投資包括效能監視與調整。
    
- **Azure 平台服務 (PaaS)** 除了 Microsoft saas 和服務的投資、 多個網站或地理位置分散 PaaS 應用程式可能會需要架構 Azure 流量管理員來散佈的用戶端流量。進行中的投資包括效能和流量通訊監控與容錯移轉測試。
    
- **Azure 基礎架構以服務 (IaaS)** Microsoft SaaS 和 PaaS 服務成本，除了 IaaS 中執行 IT 工作量需要設計及設定的 Azure 虛擬網路該主機虛擬機器、 它們、 路由、 IP 上執行應用程式的安全連線處理、 DNS、 和負載平衡。進行中的投資包括效能及安全性監視與疑難排解。
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>區域的網路投資在雲端中成功

企業組織而受益最佳化網路輸送量跨內部網路及網際網路進行條理方法。您可能也會受益從 ExpressRoute 連線。
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>最佳化您的邊緣網路的內部網路連線

多年來，許多組織已最佳化內部網路的連線能力與內部部署資料中心中執行的應用程式的效能。產能、 方法及執行 Microsoft 雲端中的 IT 工作量其他投資必須確保連線高可用性和邊緣網路與您的內部網路的使用者之間的流量效能是最佳選擇。
  
### <a name="optimize-throughput-at-your-edge-network"></a>最佳化在邊緣網路輸送量

為多個至雲端您日常產能流量移動，您應該密切在邊緣網路以確保它們是目前、 提供高可用性，並有足夠的容量以符合尖峰負載檢查的系統。
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>使用 Azure、 Office 365 及 Dynamics 365 高 SLA、 ExpressRoute

雖然您可以使用目前的網際網路連線的邊緣網路，到與 Microsoft 雲端服務的流量必須共用管道與其他移至網際網路的內部網路流量。此外，您以 Microsoft 雲端服務的流量受限於網際網路流量壅塞。
  
高 SLA 與最佳效能，請使用 ExpressRoute、 網路和 Azure、 Office 365、 Dynamics 365 或所有三個之間的專用 WAN 連線。 
  
ExpressRoute 可以運用您現有的網路提供者的專屬的連線。透過 ExpressRoute 連接的資源便會出現好像他們是在您的 WAN，甚至是針對地理位置分散的組織。
  
如需詳細資訊，請參閱[Microsoft 雲端連線 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。
  
## <a name="scope-of-network-investments"></a>網路投資的範圍

網路投資的範圍取決於雲端服務的類別。跨 Microsoft cloud 演變最大化網路團隊的投資。例如投資 IaaS services 套用至所有的投資區域。
  
|||||
|:-----|:-----|:-----|:-----|
|投資區域  <br/> |Saas 和  <br/> |PaaS  <br/> |IaaS  <br/> |
|以容許足夠的頻寬架構師可靠而變得多餘網際網路連線  <br/> |適用於  <br/> |適用於  <br/> |適用於  <br/> |
|監視與調整效能的網際網路輸送量  <br/> |適用於  <br/> |適用於  <br/> |適用於  <br/> |
|網際網路連線能力與輸送量問題進行疑難排解  <br/> |適用於  <br/> |適用於  <br/> |適用於  <br/> |
|設計以負載平衡流量到不同的端點 Azure 流量管理員  <br/> ||適用於  <br/> |適用於  <br/> |
|架構師可靠、 備援，與效能低落連線到 Azure 虛擬網路  <br/> |||適用於  <br/> |
|設計與 Azure 虛擬機器的安全連線  <br/> |||適用於  <br/> |
|設計和實作內部部署位置和虛擬網路間的路由  <br/> |||適用於  <br/> |
|包括工程師及實作的內部和網際網路對向 IT 工作量負載平衡  <br/> |||適用於  <br/> |
|虛擬機器連線及輸送量問題的疑難排解  <br/> |||適用於  <br/> |
   
## <a name="next-step"></a>下一步

[Microsoft 雲端連線的常見的元素](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)



