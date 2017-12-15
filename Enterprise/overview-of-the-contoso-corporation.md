---
title: "Contoso Corporation 的概觀"
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
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: "摘要： 了解 Contoso Corporation 的業務以及其全世界的辦公室分層的結構。"
ms.openlocfilehash: 6243f6d6e5c08342cae7650d0b4e75de27ed3527
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="overview-of-the-contoso-corporation"></a>Contoso Corporation 的概觀

 **摘要：**了解 Contoso Corporation 的業務以及其全世界的辦公室分層的結構。
  
Contoso Corporation 是在 Paris、 法國 headquarters 通用的企業。它是 conglomerate 製造流程 」、 「 銷售 」 與 「 超過 100000 產品的支援組織。 
  
## <a name="the-contoso-corporation"></a>Contoso Corporation

Contoso 的全球組織有辦公室中的下列位置：
  
**圖 1： 全球各地的 Contoso 的辦公室**

![在世界各地的 Contoso 公司辦公室](images/Contoso_Poster/Contoso_WW_Org.png)

  
圖 1 顯示 headquarters office Paris 和區域的中樞與衛星辦公室中各種 continents。
  
Contoso 的全球各地辦公室遵循三層設計。
  
- Headquarters
    
    Contoso Corporation headquarters 是大型公司校園上數十個的系統管理、 工程和製造設施建築物搭配 Paris 的外圍地帶。所有 Contoso 的資料中心及它的網際網路平台服務被存放 Paris headquarters。
    
    Headquarters 有 15000 工作者。
    
- 區域性中樞
    
    區域性 hub 辦公室服務與 60%的銷售和支援人員世界的特定區域。每個區域的中樞已連接到 Paris headquarters 高頻寬 WAN 連結。 
    
    每個區域的中樞有 2000 工作者的平均。
    
- 衛星辦公室
    
    衛星辦公室包含 80%的銷售和支援人員並提供重要城市 （英文） 或子區域中的 Contoso 客戶實體和對現場目前狀態。每個衛星 office 已連接到高頻寬的 WAN 連結與區域中樞。
    
    每個衛星 office 具有 250 工作者的平均。
    
25%的 Contoso 的人力行動裝置，為較高的地區的中樞與衛星辦公室僅供行動工作者百分比。提供更佳的僅限行動工作者支援為 Contoso 的重要的業務目標。
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>元素的 Contoso 的實作 Microsoft 雲端

Contoso 的 IT 架構師規劃採用 Microsoft cloud 方案時識別下列項目。
  
- 網路功能
    
    網路包含連線至 Microsoft cloud 方案足夠的頻寬可在尖峰負載下的效能低落。某些連線會透過本機網際網路連線，以及一些跨 Contoso 的私人網路基礎結構。
    
    如需詳細資訊，請參閱[Microsoft 雲端網路的企業架構師](microsoft-cloud-networking-for-enterprise-architects.md)海報。
   
- 身分識別
    
    Contoso 其內部的身分識別提供者使用的 Windows Server AD 樹系，而且也同盟的客戶和合作夥伴的協力廠商提供者。Contoso 必須利用 Microsoft cloud 方案的帳戶的內部集。客戶與合作夥伴的雲端應用程式存取必須利用協力廠商身分識別提供者。
    
    如需詳細資訊，請參閱[Microsoft 雲端身分識別的企業架構師](microsoft-cloud-identity-for-enterprise-architects.md)海報 （英文）。
    
- 安全性
    
    雲端身分識別和資料安全性必須包含資料保護、 系統管理的最低權限管理、 威脅傳達及實作的資料管理和安全性原則。
    
    如需詳細資訊，請參閱[Microsoft 雲端 Security for Enterprise 架構師](http://aka.ms/cloudarchsecurity)海報 （英文）。
    
- 管理
    
    雲端應用程式及 saas 和工作負載管理需要維護設定、 資料、 帳戶、 原則與權限以及監視進行中的狀況與效能的功能。現有的伺服器管理工具將用來管理 Azure IaaS 中的虛擬機器。
    
## <a name="see-also"></a>See Also

[在 Microsoft Cloud Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)
 


