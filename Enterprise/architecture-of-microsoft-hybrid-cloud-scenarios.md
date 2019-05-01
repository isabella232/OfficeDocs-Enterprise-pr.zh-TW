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
description: 摘要： 了解 Microsoft 的混合式雲端供應項目的的架構。
ms.openlocfilehash: f5493c0f008b22af412ee95ccb8b7581eee71476
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490262"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft 混合式雲端案例的架構

 **摘要：** 了解 Microsoft 的混合式雲端供應項目的的架構。
  
用於規劃及實作 Microsoft 雲端服務與平台的混合式雲端案例的架構的方法。
  
**圖 1: Microsoft 混合式雲端堆疊**

![Microsoft 混合式雲端堆疊](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
圖 1 顯示 Microsoft 混合式雲端堆疊和其圖層，其中包含內部部署、 網路、 身分識別、 應用程式與案例中和雲端服務 （Microsoft SaaS、 Azure PaaS 和 Azure PaaS） 的類別。
  
應用程式和案例圖層有此模型中的其他文章會詳細說明的特定混合式雲端案例。 身分識別、 網路和內部部署層可以是常見的雲端服務 （SaaS、 PaaS 或 PaaS） 的類別。
  
- 內部部署
    
    混合式案例的內部部署基礎結構可以包含伺服器用於 SharePoint、 Exchange、 Skype for Business 和商務應用程式。 它也可以包含的資料存放區 （資料庫、 清單、 檔案）。 ExpressRoute 連線，而必須透過反向 proxy 或讓伺服器或資料，可在您 DMZ 上存取或外部網路允許存取內部部署資料存放區。
    
- 網路
    
    有兩種選擇進行 Microsoft 雲端平台及服務的連線： 您的現有 Internet 管道和 ExpressRoute。 如果可預測的效能非常重要，請使用 ExpressRoute 連線。 您可以使用一個 ExpressRoute 連線直接連線至 Microsoft SaaS 服務 （Office 365 和 Dynamics 365）、 Azure PaaS 服務和 Azure IaaS 服務。
    
- 身分識別
    
    雲端身分識別基礎結構，有兩種方式可移，根據 Microsoft 雲端平台。 為 SaaS、 Azure PaaS，與 Azure AD 整合您的內部部署身分識別基礎結構或您內部部署身分識別基礎結構或協力廠商身分識別提供者同盟。 在 Azure 中執行的 vm，您可以擴充到您的 Vm 的所在位置的虛擬網路 (Vnet) 的 Active Directory 網域服務 (AD DS)，例如您內部部署身分識別基礎結構。
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>三個階段雲端採用程序的混合式雲端案例

許多企業，包括 Microsoft 的則會使用採用雲端的三個階段方法。 混合式雲端案例可以每個階段中扮演重要角色。
  
1. Saas 移動生產力工作負載
    
    目前或必須保持內部部署的生產力工作負載，混合式案例允許他們與與其雲端對應項目進行整合。
    
2. 開發新的和新式的應用程式，在 Azure PaaS 中
    
    Azure PaaS 混合應用程式可以安全地利用內部部署伺服器或儲存資源。
    
3. 移至 Azure IaaS 的現有應用程式
    
    增益 shift 和在雲端建立案例中，執行於 Azure Vm 的伺服器型應用程式會提供簡單佈建和縮放比例。
    
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

