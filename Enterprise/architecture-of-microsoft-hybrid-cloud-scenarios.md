---
title: Microsoft 混合式雲端案例的架構
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 摘要： 了解 Microsoft 的混合式雲端方案的架構。
ms.openlocfilehash: 74fc046d1f60b29338e7f12184dec018538ba9da
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123390"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft 混合式雲端案例的架構

 **摘要：** 了解 Microsoft 的混合式雲端方案的架構。
  
若要規劃並實作搭配 Microsoft 雲端服務與平台的混合式雲端案例使用架構的方法。
  
**圖 1： Microsoft 混合雲端堆疊**

![Microsoft 混合式雲端堆疊](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
圖 1 顯示 Microsoft 混合雲端堆疊和其階層，其中包含內部部署、 網路、 身分識別、 應用程式和案例，以及雲端服務 （Microsoft SaaS、 Azure PaaS 和 Azure PaaS） 的類別。
  
應用程式與案例層此模型中的其他文章中有詳細說明特定混合雲端案例。身分識別、 網路和內部部署圖層] 可以是公用雲端服務 （SaaS、 PaaS 或 PaaS） 的類別。
  
- 內部部署
    
    混合式案例的內部部署基礎結構可以包含伺服器的 SharePoint、 Exchange、 Skype for Business 和營運系統應用程式。它也可以包含資料儲存區 （資料庫、 清單、 檔案）。不含 ExpressRoute 連線的存取權的內部部署資料存放區必須允許透過反向 proxy 或以存取在您 DMZ 或外部網路伺服器或資料。
    
- 工作列最右邊的網路
    
    有兩個選擇 Microsoft cloud 平台及服務的連線： 您的現有 Internet 管道和 ExpressRoute。如果可預測的效能，請務必使用 ExpressRoute 連線。您可以使用一個 ExpressRoute 連線至直接連接到 Microsoft saas 和服務 （Office 365 和 Dynamics 365）、 Azure PaaS 服務及 Azure IaaS 服務。
    
- 身分識別
    
    雲端身分識別基礎結構，有兩種方式可以移，根據 Microsoft cloud 平台。SaaS 和 Azure PaaS、 整合與 Azure AD 的內部部署身分識別基礎結構或與您的內部識別基礎結構或協力廠商身分識別提供者結盟。針對執行 Azure 中的 Vm，您可以擴充到您的 Vm 所在虛擬網路 (VNets) 的 Windows Server AD，例如您的內部身分識別基礎結構。
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>三階段雲端採用程序的混合式雲端案例

許多企業，包括 Microsoft 的、 使用採用雲端的三階段方法。混合式雲端案例可以在每個階段中扮演的角色。
  
1. 將產能工作量移至 saas 和
    
    產能工作量目前或必須保持在最內部部署的混合式案例允許他們與與其雲端對應項目進行整合。
    
2. 開發新的和現代 Azure PaaS 中的應用程式
    
    Azure PaaS 混合式應用程式可以安全地運用內部伺服器或儲存資源。
    
3. 移動 Azure IaaS 現有的應用程式
    
    增益 shift 並在雲端建立案例的伺服器端 Azure Vm 上執行的應用程式提供簡單佈建與縮放比例。
    
## <a name="see-also"></a>請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

