---
title: "Contoso Corporation 的網路"
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
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "摘要： 了解的定義和 Microsoft 混合雲端的元素。"
ms.openlocfilehash: 1f023364c4b2e9c64af954ec9ba63a6197ebc01a
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="networking-for-the-contoso-corporation"></a>Contoso Corporation 的網路

 **摘要：**了解的定義和 Microsoft 混合雲端的元素。
  
若要採用雲端 （含） 的基礎結構，Contoso 的網路工程師實現網路流量傳送到雲端架構服務針對這趟旅行方式基本 shift 鍵。而不是只最佳化的內部伺服器和資料中心流量，等於廣告必須付費來最佳化網際網路邊緣和網際網路之間的流量。
  
## <a name="contosos-networking-infrastructure"></a>Contoso 的網路基礎結構

Contoso 具有圖 1 所示的網路基礎結構。
  
**圖 1： Contoso 的 WAN 基礎結構**

![Contoso 的 WAN 基礎結構，連結了總部、區域中樞和分公司辦公室](images/Contoso_Poster/Contoso_WW_Net.png)
  
圖 1 顯示 Contoso 的辦公室跨全球的環境的地區設定與兩者之間衛星 office WAN 連結。
  
其他網路元素如下所示：
  
- 在內部網路
    
    WAN 連結連線 Paris headquarters 地區辦公室和區域來衛星辦公室支點和中樞組態中的辦公室。內每個 office、 路由器會傳遞至主機或子網路，使用私人 IP 位址空間的無線存取點的流量。
    
- 網際網路連線能力
    
    每個 office 有其專屬的網際網路連線能力透過 proxy 伺服器。這通常會實作為 WAN 連結到本機的 ISP 的 proxy 伺服器] 也提供公用 IP 位址。
    
- 網際網路平台服務
    
    Contoso 擁有 contoso.com 公用網域名稱。Contoso 公用網站以進行排序產品是一組 Paris 校園的網際網路連線的資料中心中的伺服器。Contoso 使用 / 24 在網際網路上的公用 IP 位址範圍。
    
## <a name="contosos-app-infrastructure"></a>Contoso 的應用程式基礎結構

Contoso 具有架構台下列其應用程式及伺服器基礎結構：
  
**圖 2： Contoso 的基礎結構的內部應用程式**

![Contoso 的內部應用程式基礎結構](images/Contoso_Poster/App_Infra.png)
  
- 衛星辦公室使用快取的本機伺服器以儲存常存取文件與內部網路網站。
    
- 區域性集線器使用衛星台和區域的應用程式伺服器的區域。這些伺服器與伺服器中的 Paris headquarters 同步處理。
    
- Paris 校園有包含整個組織提供服務的集中式應用程式伺服器的資料中心。
    
衛星或地區的集線器辦公室的使用者，可以所衛星和地區 hub office server 服務 60%的員工所需的資源。額外 40%的資源要求必須傳送透過 WAN 連結至 Paris 校園。
  
## <a name="contosos-network-analysis"></a>Contoso 的網路分析

以下是分析的需要網路上以容納 Microsoft cloud 方案的不同類別的變更 Contoso 的結果：
  
|**Saas 和雲端方案： Office 365、 EMS 及 Dynamics 365**|**Azure PaaS： 行動應用程式**|**Azure IaaS： 伺服器為基礎的工作負載**|
|:-----|:-----|:-----|
|Saas 和服務使用者所擁有的成功採用取決於高可用性和效能低落連線至網際網路，或直接 Microsoft 雲端服務。  <br/> 行動使用者及其目前的網際網路存取假設其值為足夠。  <br/> Contoso 公司內部網路上的使用者，每個 office 必須分析和最佳化到網際網路的輸送量和到 Microsoft 的歐洲資料中心主控 Office 365、 EMS 及 Dynamics 365 租用戶的來回時間。  <br/> |若要更佳的支援行動工作者、 舊版的應用程式以及某些檔案共用網站已成為已修訂及部署為 「 Azure PaaS 應用程式。以獲得最佳效能，Contoso 計劃部署在全世界來自多個 Azure 資料中心的新應用程式。Azure 流量管理員傳送給用戶端應用程式要求是否它們是來自行動裝置的使用者或 office 中的電腦到最接近的 Azure 資料中心主控應用程式。  <br/>  IT 部門將需要將 PaaS 應用程式的效能和流量通訊群組加入至其網路狀況監視解決方案。 <br/> |若要移動 Paris 校園資料中心一些舊版和封存伺服器並根據需要為季端處理新增伺服器，Contoso 計劃使用 Azure 基礎結構服務中執行的虛擬機器。  <br/> Azure 虛擬網路，到內含這些伺服器必須設計的不重疊地址空格、 路由、 和整合式 DNS。  <br/> IT 部門必須包含這些新的伺服器網路管理和監控系統。  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>ExpressRoute Contoso 的使用

ExpressRoute 是從所在位置到您的網路連線至 Microsoft cloud 網路 Microsoft 對等位置專用 WAN 連線。ExpressRoute 連線提供可預測的效能與達 99.9%執行時間 SLA。.
  
使用 ExpressRoute 連線，您會連線到 Microsoft cloud 網路和同一個大陸中的所有 Microsoft 資料中心位置。雲端對等位置與目的地 Microsoft 資料中心之間的流量遷 Microsoft cloud 網路
  
**圖 3： Microsoft cloud 網路組成的全球**

![全球 Microsoft 雲端網路](images/Contoso_Poster/MS_WW_Cloud.png)
  
圖 3 是生活的各區域互連的 Microsoft cloud 網路。
  
使用 ExpressRoute Premium 您可以達到任何大陸從任何大陸上任何 Microsoft 對等位置上的任何 Microsoft 資料中心。透過 Microsoft 雲端網路執行是 continents 之間的流量。
  
請依據目前和未來 Microsoft cloud 方案流量分析，Contoso 已執行網路評估及實作具有私人和公用對等的 Azure 資源存取任何-任何 （MPLS 型） ExpressRoute 連線從 Microsoft 對等位置歐洲 Paris headquarters 的關係。
  
此連線將提供 Contoso 的 IT 部門：
  
- 一致的效能分散式 Azure PaaS 應用程式的權限管理
    
    所有 Contoso 的應用程式開發人員和核心基礎結構 IT 管理員位於 Paris 校園。散佈至不同的 Azure 資料中心全球各地 Azure PaaS 應用程式] 與 Contoso 需要從來管理應用程式和其儲存資源，其中包含的文件 TB Paris 校園一致的效能。
    
- Azure IaaS 中伺服器的權限管理一致的效能
    
    Contoso 的資料中心系統管理員在 Paris 校園且其伺服器設為部署在 Azure 中副檔名為 Paris 資料中心。Contoso 必須一致的效能與這些新的伺服器存取舊版的應用程式及封存儲存區和結束一季處理。
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>雲端網路整備的 Contoso 的路徑

Contoso 以備妥 Microsoft cloud 其網路使用下列步驟：
  
1. 最佳化員工電腦的網際網路存取
    
    個別電腦則檢查以確認已安裝最新的 TCP/IP 堆疊、 瀏覽器、 NIC 驅動程式及安全性和作業系統的更新。
    
2. 分析每個 office 中的網際網路連線使用率，並增加視
    
    將目前的網際網路使用量分析每個 office 和 WAN 連結頻寬會增加如果操作 70%或以上使用率。
    
3. 分析 DMZ 系統每個 office 以達最佳效能
    
    防火牆、 Ids、 及其他系統中的網際網路路徑會分析獲得最佳效能。Proxy 伺服器會更新或升級所需。
    
4. 新增 Paris 校園 ExpressRoute
    
    提供一致資源的存取權 Azure Azure PaaS 和 IaaS 工作負載的權限管理。
    
5. 建立及測試 Azure PaaS 應用程式為 Azure 流量管理員設定檔
    
    測試散佈網際網路流量區域位置中獲取經驗會使用效能的路由方法為 Azure 流量管理員設定檔。
    
6. 為 Azure VNets 保留私人位址空間
    
    根據預計的簡短和長期伺服器在 Azure IaaS 的數字，保留私人位址空間 Azure VNets 和其子網路。
    
## <a name="see-also"></a>請參閱

[Microsoft Cloud 中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



