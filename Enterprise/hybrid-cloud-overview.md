---
title: 混合雲端概觀
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 摘要： 了解的 Microsoft hybrid cloud 元素與定義。
ms.openlocfilehash: f44251c0a0da79475c1cc391dd409db6b2faba0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067442"
---
# <a name="hybrid-cloud-overview"></a>混合雲端概觀

 **摘要：** 了解的 Microsoft hybrid cloud 元素與定義。
  
混合式雲端使用 compute 或存放裝置資源上您的內部網路和雲端中。 您可以使用混合式雲端將您的業務和其 IT 需求遷移至雲端，或與您現有的整合雲端平台及服務的路徑內部部署基礎結構以整體 IT 策略的一部分。
  
## <a name="microsoft-hybrid-cloud"></a>Microsoft 混合雲端

Microsoft 混合雲端是一組與內部部署元件，例如合併的 Microsoft 雲端平台的商務案例： 
  
- 在內部部署 SharePoint 伺服器陣列和 Office 365 中 SharePoint online，請從內容取得搜尋結果。
    
- 行動裝置的應用程式，在查詢內部部署資料存放區的 Azure 中執行。
    
- 企業內部網路 IT Azure 虛擬機器上執行的工作負載。
    
**圖 1： 元件的 Microsoft hybrid cloud**

![Microsoft 混合式雲端的元件](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
圖 1 顯示跨網際網路或 ExpressRoute 連線的 Microsoft hybrid cloud，從內部網路，到 Office 365、 Azure 平台即服務 (PaaS)，以及 Azure 基礎結構即服務 (IaaS) 服務提供一組的元件。
  
因為 Microsoft 最完整雲端解決方案 marketplace — 包括軟體作為服務 (SaaS)、 PaaS 和 IaaS-您可以：
  
- 當您移轉工作負載和雲端應用程式，請利用現有的內部部署投資。
    
- 併入混合式雲端案例長期 IT 計劃，例如，當法規或原則不允許將工作負載或特定的資料移至雲端。
    
- 建立包含多個 Microsoft 雲端服務與平台的其他的混合式案例。
    
Microsoft 雲端服務與混合式雲端案例會與平台而有所不同。
  
- SaaS
    
    Microsoft SaaS 服務包含 Office 365、 Microsoft Intune 和 Microsoft Dynamics 365。 使用 Microsoft SaaS 混合式雲端案例結合這些服務與內部部署服務或應用程式。 例如，Exchange Online 在 Office 365 中執行可整合與商務用 Skype 內部部署的商務版 2019年。
    
- Azure PaaS
    
    Microsoft Azure PaaS 服務可讓您建立雲端式應用程式。 混合式雲端案例 Azure PaaS 服務與內部部署資源或應用程式合併 Azure PaaS 應用程式。 例如，Azure PaaS 應用程式可以安全地查詢顯示行動應用程式的使用者所需的資訊在內部資料存放區。
    
- Azure IaaS
    
    Azure IaaS 服務可讓您建置及執行伺服器為基礎的 IT 工作負載，在雲端中，而不是在您內部部署資料中心。 混合式雲端案例 Azure IaaS 服務通常包含 IT 工作負載的虛擬機器上執行無障礙連線至您的內部部署網路。 您的內部部署使用者將不會注意到的差異。
    
## <a name="elements-of-hybrid-cloud"></a>混合式雲端的元素

您必須考慮下列項目時規劃及實作混合式雲端案例與 Microsoft 雲端平台及服務。
  
- 網路功能
    
    混合式雲端案例的網路功能包含連線至 Microsoft 雲端平台及服務與足夠的頻寬要在尖峰負載下的效能低落。 如需詳細資訊，請參閱[Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md)。
    
- 身分識別
    
    SaaS 和 Azure PaaS 混合案例的身分識別可以包含 Azure AD 作為一般的身分識別提供者，可以同步處理您的內部 Active Directory 網域服務 (AD DS)，或與 AD DS 或其他身分識別提供者同盟。 您也可以 Azure IaaS 來擴充您的內部部署身分識別基礎結構。 如需詳細資訊，請參閱 < <b0>Microsoft Cloud Identity for Enterprise Architects</b0>。
    
- 安全性
    
    混合式雲端案例的安全性包括保護和管理適用於您設定身分識別、 資料保護、 系統管理特殊權限管理、 威脅知悉的變更，並實作的控管和安全性原則。 如需詳細資訊，請參閱 < <b0>Microsoft Cloud Security for Enterprise Architects</b0>。
    
- 管理
    
    混合式雲端案例的管理包括維護設定、 資料、 帳戶、 原則和權限，以及監視案例和其效能的項目進行中的健康狀況的能力。 您也可以使用相同的工具集，例如 Systems Management Server，來管理虛擬機器在 Azure IaaS 中。
    
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

