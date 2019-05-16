---
title: Microsoft 雲端連線的共同項目
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
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 摘要： 了解常見的網路基礎結構元素，以及如何準備您的網路。
ms.openlocfilehash: f092e3fb0a2f009aa7c6bbb14229fe98b35700ea
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068109"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Microsoft 雲端連線的共同項目

 **摘要：** 了解常見的網路基礎結構元素，以及如何準備您的網路。
  
將您的網路與 Microsoft 雲端整合，提供各種服務的最佳存取途徑。
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>步驟來準備用於 Microsoft 雲端服務的網路
<a name="steps"> </a>

在內部網路：
  
1. 分析的用戶端電腦，並最佳化網路硬體、 軟體驅動程式、 通訊協定設定，以及網際網路瀏覽器。
    
2. 分析您的內部網路流量延遲與最佳路由傳送至網際網路邊緣裝置。
    
3. 分析網際網路邊緣裝置的效能與容量，並更高層級的流量最佳化。
    
針對您的網際網路連線：
  
1. 分析您的網際網路邊緣裝置 （例如外部防火牆） 與您所要連線的 Microsoft 雲端服務將區域位置之間的延遲。
    
2. 分析的容量與您目前的網際網路連線使用率，並新增容量，如有需要。 或者，新增的 ExpressRoute 連線。
    
## <a name="microsoft-cloud-connectivity-options"></a>Microsoft 雲端連線能力選項
<a name="steps"> </a>

使用您現有的網際網路管道或 ExpressRoute 連線到 Office 365、 Azure 和 Dynamics 365。
  
**圖 1: Microsoft 雲端連線能力的選項**

![圖 1：Microsoft Cloud 連線能力選項](media/Network-Poster/CommonElements.png)

  
圖 1 顯示如何在內部網路可以連線至 Microsoft 雲端供應項目使用其現有的網際網路管道或 ExpressRoute。 網際網路管道代表 DMZ 和可以有下列元件：
  
- **內部防火牆：** 信任的網路和不受信任的一間障礙。 執行流量篩選 （根據規則） 與監視。
    
- **外部的工作負載：** 網站或其他工作負載可供外部使用者在網際網路上。
    
- **Proxy 伺服器：** 服務代表內部網路使用者的網站內容的要求。 反向 proxy，允許來路不明的輸入的要求。
    
- **外部防火牆：** 允許的輸出流量及指定的輸入的流量。 可以執行位址轉譯、 封包檢查、 SSL 會自動換行和檢查或資料遺失防護。
    
- **WAN 連線的 ISP:** 電訊廠商型的 ISP，具有網際網路連線和路由的對等連線。
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>通用的所有 Microsoft 雲端服務的網路中的區域
<a name="steps"> </a>

您必須採用任何 Microsoft 雲端服務時，請考慮這些區域的網路。
  
- **內部網路效能：** 如果您的內部網路，包括用戶端電腦，無法進行最佳化，會降低效能，以網際網路為基礎的資源。
    
- **Edge 裝置：** 在您網路的邊緣裝置的出口點，而且可以包括網路位址轉譯 (Nat)、 （包括反向 proxy） 的 proxy 伺服器、 防火牆、 入侵偵測裝置或兩者。
    
- **網際網路連線：** 您的 WAN 連線到您的 ISP 和網際網路應有足夠的容量來處理尖峰負載。 您也可以使用 ExpressRoute 連線。
    
- **網際網路 DNS:** A、 AAAA、 CNAME、 MX、 PTR 和其他記錄來找出 Microsoft 雲端或您雲端中主控的服務。 例如，您可能需要的 CNAME 記錄您在 Azure PaaS 中裝載的應用程式。
    

## <a name="next-step"></a>下一步

[Microsoft 雲端連線 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>另請參閱

<a name="steps"> </a>

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)


