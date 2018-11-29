---
title: Microsoft 雲端連線的共同項目
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 摘要： 了解一般的網路基礎結構元素，以及如何準備您的網路。
ms.openlocfilehash: e00ad8820ef37c818c270323cf2aa036bb86a804
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872214"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Microsoft 雲端連線的共同項目

 **摘要：** 了解一般的網路基礎結構元素，以及如何準備您的網路。
  
將您的網路與 Microsoft 雲端整合，提供各種服務的最佳存取途徑。
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>若要準備您的網路 Microsoft 雲端服務的步驟
<a name="steps"> </a>

為您的內部網路：
  
1. 分析您的用戶端電腦和最佳化網路硬體、 軟體驅動程式、 通訊協定設定及網際網路瀏覽器。
    
2. 分析您的內部網路流量延遲和最佳路由傳送至網際網路 edge 裝置。
    
3. 分析的容量和效能網際網路 edge 裝置並最佳化的較高的層級的流量。
    
網際網路連線：
  
1. 分析您的網際網路 edge 裝置 （例如外部防火牆） 與您所連接之 Microsoft 雲端服務將區域位置之間的延遲。
    
2. 分析的容量和您目前的網際網路連線的使用情況並視新增容量。或者，新增 [ExpressRoute 連線]。
    
## <a name="microsoft-cloud-connectivity-options"></a>Microsoft 雲端連線選項
<a name="steps"> </a>

使用您現有的網際網路管道或 Office 365、 Azure、 和 Dynamics 365 ExpressRoute 連線。
  
**圖 1： Microsoft cloud 連線選項**

![圖 1：Microsoft Cloud 連線能力選項](media/Network-Poster/CommonElements.png)

  
圖 1 顯示如何在內部網路可以連線至 Microsoft cloud 方案使用其現有的網際網路管道或 ExpressRoute。網際網路管道代表 DMZ，且可有下列元件：
  
- **內部防火牆：** 信任的網路與未受信任的其中一個之間門檻。執行流量篩選 （根據規則） 和監控。
    
- **外部工作量：** 網站或其他工作負載供外部使用者在網際網路上。
    
- **Proxy 伺服器：** 服務要求代表內部網路使用者的 web 內容。反向 proxy，允許來路不明的輸入的要求。
    
- **外部防火牆：** 允許輸出流量及指定的輸入的流量。可執行位址轉譯、 封包檢查、 SSL 會自動換行及檢查，或是資料外洩防護。
    
- **WAN 連線的 ISP:** ISP 具有網際網路連線能力與路由的對等電信業者式連線。
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>範圍的所有 Microsoft 雲端服務一般網路區域
<a name="steps"> </a>

您需要時要考慮這些方面的網路採用任何 Microsoft 雲端服務。
  
- **內部網路效能：** 如果您的內部網路，包括用戶端電腦無法進行最佳化，會降低效能網際網路架構的資源。
    
- **Edge 裝置：** 在您的網路邊緣的裝置輸出點且可包含網路位址轉譯器 (Nat)、 proxy 伺服器 （包括反向 proxy）、 防火牆、 入侵偵測裝置或組合。
    
- **網際網路連線：** 您的 WAN 連線至您的 ISP 和網際網路應該有足夠的容量來處理尖峰負載。您也可以使用 ExpressRoute 連線。
    
- **網際網路 DNS：** A、 AAAA、 CNAME、 MX、 PTR 及其他記錄以找出 Microsoft cloud 或雲端服務。例如，您可能需要 CNAME 記錄為您的應用程式架設在 Azure PaaS。
    

## <a name="next-step"></a>下一步

[Microsoft 雲端連線 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>另請參閱

<a name="steps"> </a>

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)


