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
description: 摘要： 了解如何最佳化您的網路存取 Microsoft 的 SaaS 服務，包括 Office 365、 Microsoft Intune 和 Dynamics 365。
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487292"
---
# <a name="designing-networking-for-microsoft-saas"></a>設計 Microsoft SaaS 的網路

 **摘要：** 了解如何最佳化您的網路存取 Microsoft 的 SaaS 服務，包括 Office 365、 Microsoft Intune 和 Dynamics 365。
  
針對 Microsoft SaaS 服務將您的網路最佳化時，必須將內部和邊緣裝置設定為將不同類別的流量路由傳送至 Microsoft SaaS 服務。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>步驟來準備用於 Microsoft SaaS 服務的網路

請遵循下列步驟來最佳化您的網路以 Microsoft SaaS 服務：
  
1. 經過[Microsoft 雲端連線能力的共同元素](common-elements-of-microsoft-cloud-connectivity.md)中的**步驟來準備您的 Microsoft 雲端服務的網路**區段。
    
2. 新增至每個您的分公司的網際網路連線。
    
3. 請確定所有的網際網路連線的 Isp，使用具有本機 IP 位址的 DNS 伺服器。
    
4. 檢查您的網路 hairpin 以取得，基於雲端的安全性服務，例如中介目的地，並且盡可能刪除它們。
    
5. 設定您的邊緣裝置能夠略過處理針對最佳化和允許類別的 Microsoft SaaS 流量。

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Microsoft 的 SaaS 服務最佳化流量    

有三種類別的 Microsoft SaaS 流量：

- 最佳化

  所需的連線至每個 Microsoft SaaS 服務與代表超過 75%的 Microsoft SaaS 頻寬、 連線及資料量。

- 允許

  所需的連線至特定 Microsoft SaaS 服務和功能但不是對網路效能和延遲不如最佳化類別中敏感。

- 預設

  代表 Microsoft SaaS 服務並不需要任何最佳化的相依性。 您可以將視為像是一般網際網路流量的預設類別流量。


**圖 1： 建議的針對 Microsoft SaaS 流量的所有辦公室的組態**

![圖 1： 建議的針對 Microsoft SaaS 流量的所有辦公室的組態](media/Network-Poster/SaaS1.png)

圖 1 顯示所有辦公室，包括分公司和地區或管理中心的在其中建議的組態的設定：

- **預設**類別和一般網際網路流量路由傳送至有 proxy 伺服器和其他邊緣裝置提供保護針對網際網路型安全性風險的辦公室。
- **最佳化**和**允許**類別流量會轉送直接向 Microsoft 網路前端包含連線的使用者，略過 proxy 伺服器和其他邊緣裝置在辦公室，最靠近的邊緣。

軟體定義的廣域網路 (SD WAN) 的網路裝置分公司中分隔流量以便： 

- **預設**類別和一般網際網路流量前往透過 WAN 骨幹中央或地區辦公室。 
- **最佳化**和**允許**類別流量前往 ISP 提供當地網際網路連線。
  
如需詳細資訊，請參閱：
  
- [網路連線原則](https://aka.ms/expressrouteoffice365)

- [Office 365 的網路和移轉規劃](https://aka.ms/tune)
    
## <a name="next-step"></a>下一步

[設計 Microsoft Azure PaaS 的網路](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>另請參閱

[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

