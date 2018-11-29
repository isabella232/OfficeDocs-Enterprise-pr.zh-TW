---
title: 設計 Microsoft SaaS 的網路
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
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 摘要： 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872264"
---
# <a name="designing-networking-for-microsoft-saas"></a>設計 Microsoft SaaS 的網路

 **摘要：** 了解如何最佳化您的網路存取 Microsoft saas 和服務，包括 Office 365 和 Microsoft Intune Dynamics 365。
  
最佳化您的網路 Microsoft saas 和服務要求的內部的設定資料庫和路由傳送到 Microsoft saas 和服務的流量的不同類別的邊緣裝置。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>準備您的網路 Microsoft saas 和服務的步驟

請遵循這些步驟以最佳化您的網路 Microsoft saas 和服務：
  
1. 經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。
    
2. 將網際網路連線新增至每個您辦公室。
    
3. 請確認所有網際網路連線的 Isp 本機的 IP 位址搭配使用的 DNS 伺服器。
    
4. 檢查網路 hairpins、 雲端式安全性服務等的中介目的地，並盡可能避免它們。
    
5. 設定您的 edge 裝置略過最佳化的處理，讓 Microsoft saas 和流量的類別。

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>最佳化給 Microsoft 的 saas 和服務的流量    

有三個類別的 Microsoft saas 和流量：

- 最佳化

  所需的每一個 Microsoft saas 和服務，以及代表超過 75%的 Microsoft saas 和頻寬、 連線和大量的資料連線。

- 允許

  所需的連線至特定 Microsoft saas 和服務和功能 （英文） 但不是以受到網路效能和外出最佳化類別中的延遲。

- 預設

  代表 Microsoft saas 和服務並不需要任何最佳化的相依性。您可以將類似標準網際網路流量的預設類別流量。


**圖 1： 適用於建議設定的所有分公司的 Microsoft saas 和流量**

![圖 1： 適用於建議設定的所有分公司的 Microsoft saas 和流量](media/Network-Poster/SaaS1.png)

圖 1 顯示的所有分公司，包括分公司和地區或中央 api，在其中的建議的設定：

- **預設**類別與一般網際網路的流量路由傳送至具有 proxy 伺服器和其他 edge 裝置提供保護對網際網路型安全性風險的辦公室。
- **最佳化**] 和 [**允許**類別流量遞給直接 Microsoft 網路前端包含連線的使用者，略過 proxy 伺服器和其他 edge 裝置 office，最靠近的邊緣。

在分公司的軟體定義廣域網路 (SD WAN) 的網路裝置分隔流量使： 

- **預設**類別與一般透過 WAN 骨幹網際網路的流量會移到中央或地區的辦公室。 
- **最佳化**] 和 [**允許**類別流量前往 ISP 提供本機網際網路連線。
  
如需詳細資訊，請參閱：
  
- [網路連線原則](https://aka.ms/expressrouteoffice365)

- [Office 365 的網路和移轉規劃](https://aka.ms/tune)
    
## <a name="next-step"></a>下一步

[設計 Microsoft Azure PaaS 的網路](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

