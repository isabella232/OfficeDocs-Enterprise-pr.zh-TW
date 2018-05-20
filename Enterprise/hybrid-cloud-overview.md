---
title: 混合式雲端概觀
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: 摘要： 了解的定義和 Microsoft 混合雲端的元素。
ms.openlocfilehash: 6d23f4f759e882ed925bd8bcb4c21ee365b231a0
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
---
# <a name="hybrid-cloud-overview"></a>混合式雲端概觀

 **摘要：** 了解的定義和 Microsoft 混合雲端的元素。
  
在內部網路上與雲端中混合式雲端會使用 compute 或儲存資源。您可以使用混合式雲端為路徑將您的業務與其 IT 需要移轉至雲端或整合雲端平台及服務與您現有的內部部署基礎結構整體 IT 策略的一部分。
  
## <a name="microsoft-hybrid-cloud"></a>Microsoft 混合雲端

Microsoft 混合雲端是一組與內部部署的元件，例如合併的 Microsoft cloud 平台的商務案例： 
  
- 在內部部署 SharePoint 伺服器陣列與 SharePoint Online 在 Office 365 中，請從內容取得搜尋結果。
    
- 執行查詢內部部署資料儲存區的 Azure 中的行動裝置應用程式。
    
- 內部網路 IT 在 Azure 虛擬機器上執行的工作負載。
    
**圖 1： 元件，Microsoft 混合雲端**

![Microsoft 混合式雲端的元件](images/Hybrid_Poster/MS_Hybrid_Cloud.png)
  
圖 1 顯示跨網際網路或 ExpressRoute 連線 Microsoft 混合雲端，從 Office 365 服務 (PaaS) Azure 平台和 Azure 基礎架構以服務 (IaaS) 服務的內部網路的元件。
  
因為 Microsoft 服務商場中具有最完整的雲端解決方案 — 服務 (SaaS)、 PaaS、 和 IaaS 包括軟體-您可以：
  
- 當您移轉工作量和應用程式至雲端運用現有的內部部署投資。
    
- 併入混合雲端案例長期 IT 計劃，例如，當規定或原則不要允許將特定資料或將工作量移至雲端。
    
- 建立包含多個 Microsoft 雲端服務和平台的其他混合式案例。
    
與 Microsoft 雲端服務的混合式雲端案例會平台而有所不同。
  
- Saas 和
    
    Microsoft saas 和服務包括 Office 365、 Microsoft Intune 和 Microsoft Dynamics 365。使用 Microsoft saas 和混合式雲端案例結合這些服務與內部部署服務或應用程式。例如，Exchange Online 在 Office 365 中執行與整合的內部部署的 Business 2015 Skype。
    
- Azure PaaS
    
    Microsoft Azure PaaS 服務可讓您建立雲端應用程式。使用 Azure PaaS services 混合式雲端案例結合 Azure PaaS 應用程式與內部部署資源或應用程式。例如 Azure PaaS 應用程式可以安全地查詢的內部部署資料儲存區的行動裝置應用程式的使用者顯示所需的資訊。
    
- Azure IaaS
    
    Azure IaaS 服務可讓您建立及雲端中，而不是在您內部部署資料中心內執行伺服器型 IT 工作量。使用 Azure IaaS services 混合式雲端案例通常包含 IT 工作量的虛擬機器上執行透明連線至您的內部網路。您的內部部署使用者並不會通知差異。
    
## <a name="elements-of-hybrid-cloud"></a>混合式雲端的元素

您必須考量下列元素時規劃和實作混合雲端案例與 Microsoft 雲端平台及服務。
  
- 網路功能
    
    網路混合式雲端案例包括 Microsoft cloud 平台及服務並設為 [尖峰負載下的效能低落足夠頻寬的連線。如需詳細資訊，請參閱[Microsoft 雲端網路的企業架構師](microsoft-cloud-networking-for-enterprise-architects.md)。
    
- 身分識別
    
    SaaS 和 Azure PaaS 混合式案例的身分識別可以包含為一般的身分識別提供者，其可與您的內部部署 Windows Server AD、 同步處理或 Windows Server AD 或其他身分識別提供者與同盟的 Azure AD。您也可以擴充您的內部識別基礎結構以 Azure IaaS。如需詳細資訊，請參閱[Microsoft 雲端身分識別的企業架構師](microsoft-cloud-it-architecture-resources.md#identity)。
    
- 安全性
    
    混合式雲端案例的安全性包括保護以及管理您的身分識別、 資料保護、 系統管理的最低權限管理、 威脅傳達及實作的控管和安全性原則。如需詳細資訊，請參閱[Microsoft 雲端 Security for Enterprise 架構師](https://technet.microsoft.com/library/dn919927.aspx#security)。
    
- 管理
    
    混合式雲端案例的管理包括維護設定、 資料、 帳戶、 原則與權限，以及要監視的案例和與其效能元素的進行中狀況的功能。您也可以使用相同的工具集，例如 Systems Management Server、 管理 Azure IaaS 中的虛擬機器。
    
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)
 


