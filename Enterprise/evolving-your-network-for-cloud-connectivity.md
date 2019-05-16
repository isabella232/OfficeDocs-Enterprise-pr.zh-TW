---
title: 進化網路以善用雲端連線能力
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 摘要： 了解如何雲端採用需要網路基礎結構的投資的新方法。
ms.openlocfilehash: 47d24a4f545cfae8a6bd1c507a61f48b6d26cc7d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067629"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>進化網路以善用雲端連線能力

 **摘要：** 了解如何雲端採用需要網路基礎結構的投資的新方法。
  
雲端移轉改變了公司網路內外部的流量大小與本質。它也會影響降低安全性風險的方法。
  
- 在雲端之前
    
    大部分的網路基礎結構投資已所花費的確保可供使用、 可靠性和效能低落連線到內部部署資料中心。 對許多組織而言，網際網路連線能力來說並不重要的內部業務作業。 網路界限的主要防禦安全性弱點。
    
- 在雲端之後
    
    新的和已移轉的產能與執行在雲端的 IT 工作負載，基礎結構的投資移動從內部部署資料中心，以網際網路連線能力，也就是現在重要的內部企業營運。 同盟的連線會進入安全性策略，保護身分識別和資料通過的網路與 Microsoft 雲端服務的連線點。
    
網路基礎結構的投資的開頭的連線。 其他投資取決於雲端服務的類別。
  
- **軟體即服務 (SaaS)** Microsoft SaaS 服務包含 Office 365、 Microsoft Intune 和 Microsoft Dynamics 365。 成功的 SaaS 服務使用者採用取決於高可用性和效能低落連線至網際網路，或直接在 Microsoft 雲端服務。
    
    網路架構著重於可靠的備援連線與足夠的頻寬。 進行中的投資包含效能監視與調整。
    
- **Azure 的平台即服務 (PaaS)** 除了針對 Microsoft SaaS 服務投資，多站台或地理位置分散 PaaS 應用程式可能需要架構 Azure 流量管理員可將用戶端流量分散。 進行中的投資包括效能和流量通訊監視和容錯移轉測試。
    
- **Azure 基礎結構即服務 (IaaS)** Microsoft SaaS 和 PaaS 服務投資，除了在 IaaS 中執行的 IT 工作負載需要設計及設定 Azure 虛擬網路的裝載虛擬機器，它們，路由，IP 上執行的應用程式的安全連線解決，DNS 及負載平衡。 進行中的投資包括效能與安全性監視及疑難排解。

[Microsoft 365](https://www.microsoft.com/microsoft-365)是 Office 365、 企業管理 + 安全性 (EMS) 和 Windows 10 的組合。 Microsoft 365 結合多個 SaaS 和 Azure 服務的完整的智慧型解決方案，讓所有人發揮創意並安全地合作。
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>區域的網路成功定域機組中的投資

企業組織受益於採取有條理的方法，以最佳化網路輸送量，在您內部網路和網際網路。 您也可以受益於 ExpressRoute 連線。
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>最佳化您的邊緣網路的內部網路連線

多年來，許多組織有最佳化內部網路連線能力與內部部署資料中心中執行的應用程式的效能。 產能與執行 Microsoft cloud 中的 IT 工作負載，其他投資必須確定連線高可用性和邊緣網路與您的內部網路使用者之間的流量效能是最佳的作法。
  
### <a name="optimize-throughput-at-your-edge-network"></a>在邊緣網路輸送量最佳化

為多個至雲端您日常生產力流量移動，密切應該在您的邊緣網路，以確保其目前，提供高可用性，且沒有足夠的容量，以滿足尖峰負載檢查系統的集合。
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>若要在 Azure、 Office 365 和 Dynamics 365 高 SLA，使用 ExpressRoute

雖然您可以使用您目前的網際網路連線從您的邊緣網路，到及傳送自 Microsoft 雲端服務的流量必須與其他內部網路流量，移至 [網際網路共用管道。 此外，您對 Microsoft 雲端服務的流量受限於網際網路流量壅塞。
  
針對高 SLA 及最佳效能，使用 ExpressRoute，您的網路和 Azure、 Office 365、 Dynamics 365 或所有三個間的專用 WAN 連線。 
  
ExpressRoute 可以利用現有的專用連線的網路提供者。 透過 ExpressRoute 連線的資源會顯示好像他們位於您 WAN，即使的地理位置分散的組織。
  
如需詳細資訊，請參閱 <<c0>適用於 Microsoft 雲端連線能力。
  
## <a name="scope-of-network-investments"></a>網路投資的範圍

網路投資的範圍取決於雲端服務的類別。 跨 Microsoft 雲端投資會最大化網路團隊的投資。 例如，IaaS services 投資套用到所有投資區域。
  
|||||
|:-----|:-----|:-----|:-----|
|投資區域  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|架構師可靠的備援網際網路連線能力，具有足夠的頻寬  <br/> |適用於  <br/> |適用於  <br/> |適用於  <br/> |
|效能的監視與調整網際網路輸送量  <br/> |適用於  <br/> |適用於  <br/> |適用於  <br/> |
|網際網路連線及輸送量問題進行疑難排解  <br/> |適用於  <br/> |適用於  <br/> |適用於  <br/> |
|設計 Azure 流量管理員將流量負載平衡到不同的端點  <br/> ||適用於  <br/> |適用於  <br/> |
|Azure 虛擬網路的架構設計人員可靠的備援和效能低落連線  <br/> |||適用於  <br/> |
|設計 Azure 虛擬機器的安全連線  <br/> |||適用於  <br/> |
|設計和實作內部部署位置和虛擬網路之間的路由  <br/> |||適用於  <br/> |
|設計和實作內部和網際網路對向的 IT 工作負載的負載平衡  <br/> |||適用於  <br/> |
|針對虛擬機器連線及輸送量問題進行疑難排解  <br/> |||適用於  <br/> |
   
## <a name="next-step"></a>下一步

[Microsoft 雲端連線的常見的元素](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)



