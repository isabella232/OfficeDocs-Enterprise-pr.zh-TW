---
title: 設計 Microsoft Azure PaaS 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 摘要： 了解如何最佳化您的網路存取 Microsoft Azure PaaS。
ms.openlocfilehash: 49096276a0e8356a11e52bc8765cc796eec32510
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872234"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>設計 Microsoft Azure PaaS 的網路

 **摘要：** 了解如何最佳化您的網路存取 Microsoft Azure PaaS。
  
若要針對 Azure PaaS 應用程式最佳化網路，必須具備充足的網際網路頻寬，且可能需要跨多個站台或應用程式分散網路流量。
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>規劃步驟裝載在 Azure 中的組織 PaaS 應用程式

1. 經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。
    
2. 最佳化您的網際網路頻寬使用中[設計的 Microsoft saas 和網路](designing-networking-for-microsoft-saas.md)的**步驟來準備您的網路 Microsoft saas 和服務的**一節的步驟 2 到 4。
    
3. 決定您是否需要 Azure ExpressRoute 連線。
    
4. 針對 web 式工作量，決定您是否需要 Azure Application Gateway。
    
5. 針對散佈至不同的資料中心中的不同端點流量，決定您是否需要 Azure 流量管理員。
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>組織 PaaS 應用程式的網際網路頻寬

架設在 Azure PaaS 的組織應用程式的內部網路的使用者需要的網際網路頻寬。有兩個選項：
  
- **選項 1:** 使用您現有的管道、 最佳化處理尖峰負載的容量與網際網路流量。請參閱[設計的 Microsoft saas 和網路](designing-networking-for-microsoft-saas.md)網際網路 edge、 用戶端使用狀況和 IT 作業考量。
    
- **選項 2：** 高頻寬或低延遲需求使用 Azure ExpressRoute 連線。
    
**圖 1： 連接 Azure PaaS 服務的連線選項**

![圖 1：Azure PaaS 服務的連線選項](media/Network-Poster/PaaS1.png)
  
圖 1 顯示透過網際網路管道或 ExpressRoute Azure PaaS 服務連線至內部部署網路。
  
## <a name="azure-application-gateway"></a>Azure Application Gateway

應用程式層級路由和負載平衡的服務，可讓您建立可擴充及高度可用的 web 前端 Azure 中的 web 應用程式、 雲端服務與虛擬機器。 
  
**圖 2： Azure Application Gateway**

![圖 2：Azure 應用程式閘道服務](media/Network-Poster/PaaS2.png)
  
圖 2 顯示 Azure Application Gateway 以及使用者要求來自網際網路的方式可以轉接至 Azure 的 web 應用程式、 雲端服務或虛擬機器。
  
Application Gateway 目前支援階層 7 應用程式傳遞下列：
  
- HTTP 負載平衡
    
- Cookie 為主的工作階段親和性
    
- SSL 卸載
    
如需詳細資訊，請參閱[Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)。
  
## <a name="azure-traffic-manager"></a>Azure 流量管理員

散佈至不同的端點，可以包含 cloud services 或 Azure 的 web 應用程式位於不同的資料中心] 或 [外部端點的流量。
  
流量管理員會使用下列的路由方法：
  
- **容錯移轉：** 端點的相同或不同的 Azure 資料中心，且您想要使用的所有流量的主要端點，但提供備份主要索引器或備份端點已無法使用。
    
- **循環配置資源：** 您想要在相同的資料中心的端點一組或跨越不同的資料中心散佈負載。
    
- **效能：** 必須在不同地理位置端點和您要要求用戶端使用方面的最低的延遲 」 最接近"的端點。
    
以下是三個地理位置分散的 web 應用程式的範例。
  
**圖 3：Azure 流量管理員**

![圖 3：Azure 流量管理員](media/Network-Poster/PaaS3.png)
  
圖 3 是基本程序將要求路由傳送至美國、 歐洲和亞洲中的三個不同的 Azure web 應用程式使用流量管理員。在範例：
  
1. 網站 URL 取得導向至 Azure 流量管理員] 中，這會傳回區域的 web 應用程式的名稱、 使用者 DNS 查詢根據效能的路由方法。
    
2. 使用者會具有歐洲地區的 web 應用程式的流量。
    
如需詳細資訊，請參閱[流量管理員](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。

## <a name="next-step"></a>下一步

[設計 Microsoft Azure IaaS 的網路](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

