---
title: "Contoso 的 IT 基礎結構和需求"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "摘要： 了解 Contoso 的基本結構內部 IT 基礎結構和如何其商務需要可符合由 Microsoft cloud 方案。"
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a>Contoso 的 IT 基礎結構和需求

 **摘要：**了解 Contoso 的基本結構內部 IT 基礎結構和如何其商務需要可符合由 Microsoft cloud 方案。
  
Contoso 正從內部部署轉換、 至雲端 （含） 的一個納入雲端式個人產能工作量、 應用程式以及混合式案例的集中式的 IT 基礎結構。
  
## <a name="contosos-existing-it-infrastructure"></a>Contoso 現有的 IT 基礎結構

Contoso 使用多半集中式內部 IT 基礎結構與 Paris headquarters 中的應用程式資料中心。
  
**圖 1： Contoso 的現有 IT 基礎結構**

![Contoso 現有的 IT 基礎結構](images/Contoso_Poster/Existing_IT.png)
  
圖 1 顯示 headquarters office 應用程式資料中心、 DMZ 與網際網路。
  
在 [Contoso 的 DMZ 不同的伺服器集提供：
  
- 遠端存取 contoso 公司內部網路和網頁代理 Paris headquarters 的工作者。
    
- 架設 Contoso 公用網站中，從哪些客戶可以排序產品、 組件、 或供應。
    
- 架設 Contoso 合作夥伴外部合作夥伴的通訊與共同作業。
    
## <a name="contosos-business-needs"></a>Contoso 的業務需求

以下是會依照優先順序 Contoso 的業務需求：
  
1. 遵守區域法規需求
    
    若要防止罰並維持與本機政府良好的關係，請 Contoso 必須確定遵守資料儲存區與加密規定。
    
2. 改善廠商和協力廠商的管理
    
    合作夥伴外部已過時且最耗費成本來維護。Contoso 想要取代使用同盟的驗證的雲端架構解決方案。
    
3. 改善行動工作團隊的生產力、 裝置管理和存取
    
    Contoso 的僅限行動工作團隊會展開並需要裝置管理可確保財產保護及更有效率資源的存取權。
    
4. 減少遠端存取基礎結構
    
    移至雲端的遠端工作者常存取的資源，Contoso 將儲存 money 降低其遠端存取解決方案維護和支援成本。
    
5. 向內部部署資料中心下向內
    
    Contoso 資料中心都包含數百個部份只會執行影響 IT 人員從維護高的商務值工作負載的舊版或封存功能的伺服器。
    
6. 結束一季處理的向外延展運算和儲存資源
    
    結束一季財務會計和預測處理以及庫存管理需要短期增加伺服器及存放區。
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>對應 Contoso 的商務需要 Microsoft cloud 方案

根據 Microsoft cloud 方案，Contoso 的分析的 IT 部門會決定下列對應：
  
|**軟體即服務 (SaaS)**|**以服務 (Azure PaaS) 的平台**|**基礎架構以服務 (Azure IaaS)**|
|:-----|:-----|:-----|
|**Office 365：**在雲端中主要個人及群組的產能應用程式。 <br/> 業務需求： 1 3 5  <br/> |主控銷售和支援文件並使用雲端應用程式的資訊系統。  <br/> 業務需求： 3  <br/> |將封存與舊版系統移至雲端架構的伺服器。  <br/> 業務需求： 5  <br/> |
|**Dynamics 365:**使用雲端式客戶與廠商管理。移除網路 DMZ 中的協力廠商。<br/> 業務需求： 2  <br/> |行動應用程式的雲端式而不是 Paris 資料中心架構。  <br/> 業務需求： 3 4  <br/> |移轉使用率低的應用程式和不在內部部署資料中心的資料。  <br/> 業務需求： 5  <br/> |
|**Intune/EMS:**管理 iOS 及 Android 裝置。 <br/> 業務需求： 3  <br/> ||新增暫時伺服器和結束一季處理需求的儲存空間。  <br/> 商務需要： 6  <br/> |
   
## <a name="see-also"></a>See Also

[在 Microsoft Cloud Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)


