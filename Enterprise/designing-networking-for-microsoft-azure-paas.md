---
title: 設計 Microsoft Azure PaaS 的網路
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 摘要： 了解如何最佳化您存取 Microsoft Azure PaaS 的網路。
ms.openlocfilehash: fafc3de1c5f755e891da6c07ae8993fb869bc5e1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067819"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>設計 Microsoft Azure PaaS 的網路

 **摘要：** 了解如何最佳化您存取 Microsoft Azure PaaS 的網路。
  
若要針對 Azure PaaS 應用程式最佳化網路，必須具備充足的網際網路頻寬，且可能需要跨多個站台或應用程式分散網路流量。
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>規劃步驟裝載在 Azure 中的組織 PaaS 應用程式

1. 經過[Microsoft 雲端連線能力的共同元素](common-elements-of-microsoft-cloud-connectivity.md)中的**步驟來準備您的 Microsoft 雲端服務的網路**區段。
    
2. 最佳化網際網路頻寬使用步驟 2 到 4 的**步驟來準備您的網路以 Microsoft SaaS 服務**] 區段中，在[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)。
    
3. 決定您是否需要 Azure ExpressRoute 連線。
    
4. 適用於 web 型工作負載，決定您是否需要 Azure 應用程式閘道。
    
5. 針對分散在不同資料中心中的不同端點的流量，決定您是否需要 Azure 流量管理員。
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>組織 PaaS 應用程式的網際網路頻寬

裝載在 Azure PaaS 中的組織應用程式需要內部網路使用者的網際網路頻寬。 其中有兩個選項：
  
- **選項 1:** 使用您現有的管道，以具有足夠容量處理尖峰負載的網際網路流量最佳化。 網際網路邊緣、 用戶端流量及 IT 作業考量，請參閱[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)。
    
- **選項 2:** 高頻寬或低延遲需求，會使用 Azure ExpressRoute 連線。
    
**圖 1： 連接的 Azure PaaS 服務的連線選項**

![圖 1：Azure PaaS 服務的連線選項](media/Network-Poster/PaaS1.png)
  
圖 1 顯示透過網際網路管道或 ExpressRoute 連線到 Azure PaaS 服務的內部網路。
  
## <a name="azure-application-gateway"></a>Azure 應用程式閘道

應用程式層級路由和負載平衡服務，可讓您建置可延展及高可用 web 前端在 Azure 中的 web 應用程式、 雲端服務和虛擬機器。 
  
**圖 2: Azure 應用程式閘道**

![圖 2：Azure 應用程式閘道服務](media/Network-Poster/PaaS2.png)
  
圖 2 顯示 Azure 應用程式閘道和使用者從網際網路的要求路由至 Azure 的 web 應用程式、 雲端服務時或虛擬機器。
  
應用程式閘道目前支援層級 7 應用程式傳遞下列：
  
- HTTP 負載平衡
    
- Cookie 為主的工作階段親和性
    
- SSL 卸載
    
如需詳細資訊，請參閱 < <b0>Application Gateway</b0>。
  
## <a name="azure-traffic-manager"></a>Azure 流量管理員

分散到不同的端點，可以包含雲端服務或位於不同的資料中心] 或 [外部端點的 Azure 的 web 應用程式的流量。
  
流量管理員會使用下列的路由方法：
  
- **容錯移轉：** 端點是在相同或不同的 Azure 資料中心，而您想要使用的主要端點的所有流量，但提供備份，以防主要或備份端點會無法使用。
    
- **循環配置資源：** 您想要將負載分散給一群在相同資料中心的端點或跨越不同的資料中心。
    
- **效能：** 您必須在不同地理位置的端點，而且您想要求用戶端使用方面的最低延遲的 「 最接近的 「 端點。
    
以下是三個地理位置分散的 web 應用程式的範例。
  
**圖 3：Azure 流量管理員**

![圖 3：Azure 流量管理員](media/Network-Poster/PaaS3.png)
  
圖 3 顯示基本程序流量管理員用以在美國、 歐洲及亞洲的三個不同的 Azure web 應用程式要求路由傳送。 在範例中：
  
1. URL 取得導向至 Azure 流量管理員] 中，會傳回區域的 web 應用程式的名稱，網站使用者 DNS 查詢為基礎的效能路由方法。
    
2. 從使用者起始與歐洲地區的 web 應用程式的流量。
    
如需詳細資訊，請參閱[Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)。

## <a name="next-step"></a>下一步

[設計 Microsoft Azure IaaS 的網路](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

