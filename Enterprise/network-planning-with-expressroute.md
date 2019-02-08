---
title: 使用 ExpressRoute for Office 365 進行網路規劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Office 365 ExpressRoute 提供第 3 層之間的連線網路和 Microsoft 資料中心。電路使用框線閘道通訊協定 (BGP) 路由廣告的 Office 365 前端伺服器。從您的內部部署裝置的觀點來看時所需選取正確的 TCP/IP 路徑至 Office 365, Azure ExpressRoute 看到另一個到網際網路。
ms.openlocfilehash: 7a2c9cb8ee562c0527416aa83184de90cd204476
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897226"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>使用 ExpressRoute for Office 365 進行網路規劃

Office 365 ExpressRoute 提供第 3 層之間的連線網路和 Microsoft 資料中心。電路使用框線閘道通訊協定 (BGP) 路由廣告的 Office 365 前端伺服器。從您的內部部署裝置的觀點來看時所需選取正確的 TCP/IP 路徑至 Office 365, Azure ExpressRoute 看到另一個到網際網路。
  
Azure ExpressRoute 會直接路徑新增到特定的一段支援的功能與 Microsoft 資料中心內的 Office 365 伺服器所提供的服務。Azure ExpressRoute 不會取代 Microsoft 資料中心或網域名稱解析等的基本網際網路服務的網際網路連線能力。Azure ExpressRoute 及網際網路電路應該是安全的和多餘。
  
下表重點在於說明網際網路與 Office 365 的 Azure ExpressRoute 連線內容中的一些差異。

|**網路規劃之間的差異**|**網際網路網路連線**|**ExpressRoute 網路連線**|
|:-----|:-----|:-----|
| 存取所需的網際網路服務，包括;  <br/>  DNS 名稱解析  <br/>  憑證撤銷驗證  <br/>  內容傳遞網路  <br/> |是  <br/> |要求送至 Microsoft 擁有 DNS 和/或 CDN 基礎結構可以使用 ExpressRoute 網路。  <br/> |
| 存取 Office 365 服務，包括;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  商務用 Skype Online  <br/>  Office Online  <br/>  Office 365 入口網站及驗證  <br/> |是，所有應用程式和功能  <br/> |是，[特定應用程式與功能](https://aka.ms/o365endpoints) <br/> |
|內部部署在周邊的安全性。  <br/> |是  <br/> |可以  <br/> |
|規劃高可用性。  <br/> |容錯移轉至備用網際網路網路連線  <br/> |容錯移轉至備用 ExpressRoute 連線  <br/> |
|具有可預測的網路設定檔的直接連線。  <br/> |否  <br/> |是  <br/> |
|IPv6 連線能力。  <br/> |是  <br/> |可以  <br/> |

展開標題下方的多個網路規劃指引。我們也已記錄跤探討 10 組件[的 Office 365 訓練 Azure ExpressRoute](https://channel9.msdn.com/series/aer)數列。

## <a name="existing-azure-expressroute-customers"></a>現有的 Azure ExpressRoute 客戶

如果您使用現有的 Azure ExpressRoute 電路並想要新增此電路透過 Office 365 的連線，您應該查看電路、 輸出位置及大小以確保它們將符合需求的 Office 365 流量電路的數字。大部分客戶需要額外的頻寬，且許多需要額外的電路。
  
若要啟用透過現有的 Azure ExpressRoute 電路存取 Office 365，以確保在 Office 365 服務的 [[設定路由篩選](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)都可存取。
  
Azure ExpressRoute 訂閱為中心，這表示訂閱所繫結至客戶的客戶。為客戶，您可以有多個 Azure ExpressRoute 電路和可以存取這些電路許多 Microsoft 雲端資源。例如，您可以選擇存取 Azure 按兩個備援 Azure ExpressRoute 電路主控的虛擬機器、 Office 365 測試租用戶，與 Office 365 生產租用戶。
  
下表概述您可以選擇實作透過您電路的對等關係的兩種類型。

|**對等關係**|**Azure 私人**|**Microsoft**|
|:-----|:-----|:-----|
|**服務** <br/> |IaaS： Azure 虛擬機器  <br/> |PaaS： Azure 公用服務  <br/> Saas 和： Office 365  <br/> Saas 和： Dynamics 365  <br/> |
|連線初始 * * * <br/> |客戶-Microsoft  <br/> Microsoft 位客戶  <br/> |客戶-Microsoft  <br/> Microsoft 位客戶  <br/> |
|**QoS 支援** <br/> |沒有 QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup>QoS 支援商務 Skype 只會在此時間。
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>規劃 Azure ExpressRoute 頻寬

每個 Office 365 客戶如何 active 它們與每個 Office 365 應用程式及其他因素影響，例如使用內部部署或混合式設備及網路安全性設定的每個位置有唯一的頻寬需求的人員數目。
  
具有太少頻寬會導致擁塞、 重新資料及無法預測的延遲。有太多頻寬會導致不必要的成本。在現有的網路頻寬通常稱為電路可用發揮空間量就百分比。問題 10%發揮空間會壅塞的可能結果而通常有 80%發揮空間表示不必要的成本。一般發揮空間目標配置是 20%到 50%。
  
若要尋找正確的層級，最佳機制便是頻寬的測試您現有的網路使用率。這是要取得的使用狀況，則為 true 值量值且必須為每一個網路組態的唯一方式與應用程式會以唯一某些方式進行。當評估您會想要關閉都要總頻寬使用率、 延遲和 TCP 壅塞了解您的網路需求。
  
一次已包含所有網路應用程式皆包含在組織中的人員判斷實際流量的不同設定檔的小型群組與試驗 Office 365 估計的基準和使用兩個的度量值，以評估的數量您將需要針對每個辦公室位置的頻寬。如果有任何延遲或在測試中發現的 TCP 壅塞問題，您可能需要將輸出更接近移至使用 Office 365 的人員或移除掃描例如 SSL 解密/檢查密集的網路。
  
我們建議在建議的網路處理哪些類型的所有套用至 ExpressRoute 和網際網路電路。相同是指引的在我們的[效能調整網站](https://aka.ms/tune)上的其餘部分的則為 true。
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Office 365 案例將安全性控制套用至 Azure ExpressRoute

保護 Azure ExpressRoute 連線開頭為保護網際網路連線能力相同的原則。許多客戶會選擇部署網路和周邊網路的控制項沿著其內部網路連接到 Office 365 與其他 Microsoft 雲朵 ExpressRoute 路徑。這些控制項可能包括防火牆、 應用程式 proxy、 資料外洩防護、 入侵偵測、 入侵防護系統等等。在許多情況下客戶將控制項的不同層級套用到內部部署與流量起始 microsoft 客戶在內部網路流量從內部部署移至一般起始與要移至 Microsoft，從起始的流量網際網路目的地。
  
以下是一些範例整合安全性和部署您選擇[ExpressRoute connectivity 模型](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models)。

|**ExpressRoute 整合選項**|**網路安全性周邊模型**|
|:-----|:-----|
|共同位於雲端 exchange  <br/> |安裝新的或運用在其中建立 ExpressRoute 連線共置設備的現有安全性/周邊基礎結構。  <br/> 善用共置功能可以純粹路由/interconnect 的目的和後牽引連線至內部部署安全性/周邊基礎結構的共置設備。  <br/> |
|點對點乙太網路  <br/> |終止中現有的內部部署安全性/周邊基礎結構位置的點對點 ExpressRoute 連線。  <br/> 安裝新安全性/周邊基礎結構特定 ExpressRoute 路徑及終止的點對點連線。  <br/> |
|任何-任何 IPVPN  <br/> |運用現有的內部安全性/周邊基礎結構的輸出至 Office 365 連線用於 ExpressRoute IPVPN 的所有位置。  <br/> 髮夾用於 ExpressRoute for Office 365 內部特定位置 IPVPN 指定做為安全性/周邊網路。  <br/> |

某些服務提供者也提供與 Azure ExpressRoute 其整合解決方案一部分的受管理的安全性周邊功能。
  
時考慮拓撲位置的 ExpressRoute 用於 Office 365 連線的周邊網路/安全性選項，以下是其他考量
  
- 深度和類型網路/安全性控制項可能必須對效能與延展性的 Office 365 使用者經驗的影響。

- 輸出 (上-部署-\>Microsoft) 及輸入 (Microsoft-\>內部部署) [如果已啟用] 流程可能會有不同的需求。以下是可能不同於輸出到一般網際網路目的地的電話。

- 是否透過 Office 365 ExpressRoute 或透過網際網路路由傳送流量的連接埠/通訊協定及必要的 IP 子網路的 office 365 需求都是相同的。

- 客戶網路/安全性控制的拓樸位置決定最終端對端網路之間的使用者和 Office 365 服務及網路延遲和壅塞明顯提升。

- 客戶是建議設計其安全性/周邊拓撲，以使用 ExpressRoute 與 Office 365 符合的備援、 高可用性和嚴重損壞復原最佳作法。

以下是比較不同的 Azure ExpressRoute 連線選項與上面所討論的周邊安全性模型的 Woodgrove Bank 的範例。
  
### <a name="example-1-securing-azure-expressroute"></a>範例 1： 保護 Azure ExpressRoute
  
Woodgrove Bank 考慮實作 Azure ExpressRoute 及規劃[與 Office 365 ExpressRoute 路由](routing-with-expressroute.md)的最佳架構之後及使用上述準則瞭解頻寬需求之後，他們正在決定保護其周邊的最佳方法。
  
Woodgrove、 多重國家的組織具有多個 continents 中的位置的安全性必須跨所有周邊。Woodgrove 的最佳的連線選項是具有多個對等的位置來服務的每一個大陸其員工需求遍多點連線。每一個大陸包括大陸內的備援 Azure ExpressRoute 電路及安全性必須跨所有這些。
  
Woodgrove 的現有基礎結構可靠和可處理的其他工作，因此，Woodgrove Bank 是能夠使用基礎結構以其 Azure ExpressRoute 和網際網路周邊安全性。如果這未大小寫、 Woodgrove 可選擇購買額外的設備以輔助其現有的設備或處理不同類型的連線。
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>高可用性和容錯移轉與 Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

建議至少兩種 active 電路從 ExpressRoute 與每個輸出至 ExpressRoute 提供者佈建。這是最常見的地方我們看到失敗的客戶與您可以輕鬆地避免它佈建兩個主動/主動 ExpressRoute 電路。也建議至少兩個主動/主動網際網路電路因為許多 Office 365 服務都只能透過網際網路。
  
內部網路輸出點是許多其他裝置和扮演一個關鍵角色中人員如何察覺可用性的電路。這些中某些部分的連線案例並不涵蓋 ExpressRoute 或 Office 365 Sla，但他們播放端對端服務可用性重要角色為視為在組織中的人。
  
整個計畫重心在使用人員和操作 Office 365 中，如果失敗的任何一個元件會影響人員的體驗使用服務，尋找方式來限制受影響的人員的總百分比。如果方面複雜容錯移轉模式，請考慮的人員經驗的復原長的時間並尋找方面簡單且自動容錯移轉模式。
  
外部網路、 Office 365、 ExpressRoute 及 ExpressRoute 提供者所有具有不同程度的可用性。
  
### <a name="service-availability"></a>服務可用性
  
- Office 365 服務所涵蓋定義完善的[服務等級協定](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)，其中包含個別服務的執行時間與可用性計量。Office 365 可以維護這類高的服務可用性層級是個別元件以順暢地許多 Microsoft 資料中心，使用通用 Microsoft 網路之間的容錯移轉能力的原因之一。此容錯移轉從資料中心和網路延伸為多個網際網路的輸出點，並啟用順暢地使用服務的人員的觀點的容錯移轉。

- ExpressRoute 之間的 Microsoft 網路邊緣和 ExpressRoute 提供者或協力廠商基礎結構的個別專用電路[提供 99.9%可用性 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) 。在包含[兩個獨立連接](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)變得多餘的 Microsoft 設備及網路提供者設備中每個對等的位置之間的 ExpressRoute 電路層級套用這些服務層級。

### <a name="provider-availability"></a>提供者可用性
  
- Microsoft 的服務層級用以停止在 ExpressRoute 提供者或協力廠商。這也是您可以設定會影響您的可用性層級的選擇的第一個位置。您最應該評估架構、 可用性及恢復特性 ExpressRoute 提供者提供您周邊網路與提供者連線在每個 Microsoft 對等位置之間。密切注意的備援、 對等的設備、 電訊廠商提供 WAN 電路、 邏輯及實體層面與任何其他值新增服務，例如 NAT 服務或受管理的防火牆。

### <a name="designing-your-availability-plan"></a>設計可用性計劃
  
我們強烈建議您規劃及設計高可用性和彈性端對端連線案例到 Office 365。設計應該包含;
  
- 任何單一失敗，包括網際網路和 ExpressRoute 電路點。

- 最小化受影響的人數及的持續時間的影響最預期的失敗模式。

- 最佳化最預期的失敗模式中的簡單、 鎖死，且自動復原程序。

- 支援的網路流量和多餘的路徑，但明顯的效能下降不到功能完整的需求。

您連線的情況應該包含到 Office 365 的多個獨立和使用中的網路路徑的功能已最佳化網路拓撲。這將會獲得更妥善地端對端可用性比最佳化僅適用於個別裝置或設備層級的備援能力的拓撲。
  
> [!TIP]
> 如果您的使用者會分散於多個大陸或地理區域且每個這些位置連接到單一的 ExpressRoute 電路所在的內部單一位置設為備援 WAN 電路透過，您的使用者會遇到小於網路拓撲設計，其中包含連線至最接近的對等的不同區域的獨立 ExpressRoute 電路比可用的端對端服務位置。
  
建議至少兩種 ExpressRoute 電路與每個電路連接至不同的對等地理位置與佈建。您應該佈建此主動-主動一組人員將其中 for Office 365 服務使用 ExpressRoute 連線每個區域的電路。這可讓每個區域，將會影響如資料中心的主要位置或對等的位置在災害期間會保持連線。中其設定為主動/主動允許使用者流量分散於多個網路路徑。這可減少人員裝置或網路設備中斷期間受影響的範圍。
  
我們不建議使用網際網路使用單一的 ExpressRoute 電路備用。
  
### <a name="example-2-failover-and-high-availability"></a>範例 2： 容錯移轉與高可用性
  
Woodgrove Bank 多重地理設計上有路由傳送、 頻寬、 安全性、 檢閱及現在必須送交高可用性檢閱。Woodgrove 認定為涵蓋三種類別 ； 的高可用性的相關恢復能力、 可靠性及備援。
  
恢復能力允許 Woodgrove 快速復原失敗。可靠性允許 Woodgrove 來提供一致的結果系統內。備援允許 Woodgrove 的基礎結構的一或多個鏡像執行個體之間移動。
  
內每個 edge 設定] Woodgrove 具有多餘的防火牆、 Proxy 和識別碼。「 北美地區 」 Woodgrove 有在其 Dallas 資料中心內的一部 edge 設定並在其維吉尼亞州資料中心內的其他 edge 設定。在每個位置設為備援的設備提供該位置的彈性。
  
Woodgrove Bank 的網路組態是根據幾個主要原則而建置：
  
- 每個地理的地區內有多個 Azure ExpressRoute 電路。

- 每個區域內的電路可支援所有該區域內的網路流量。

- 路由會清楚偏好一或根據位置的可用性而定的其他路徑等等。

- Azure ExpressRoute 電路之間的容錯移轉會自動發生沒有其他設定] 或 [Woodgrove 所需要的動作。

- 網際網路電路之間的容錯移轉會自動發生沒有其他設定] 或 [Woodgrove 所需要的動作。

在此組態中，在實體和虛擬層級的備援與 Woodgrove Bank 能夠提供本機恢復能力、 區域恢復和全域恢復能力的可靠的方式。Woodgrove 選取這個設定之後評估單一 Azure ExpressRoute 電路個別地區為容錯移轉至網際網路的可能性。
  
如果 Woodgrove 無法擁有多個 Azure ExpressRoute 電路每個區域，則源自北美亞太地區在 Azure ExpressRoute 電路的流量路由會新增無法接受的層級延遲和所需的 DNS 轉寄站組態新增複雜性。
  
運用以備份設定網際網路不建議使用。這會中斷 Woodgrove 的可靠性當中，則產生使用連線不一致的體驗。此外，手動設定則需要考慮已設定 BGP 廣告容錯移轉、 NAT 組態、 DNS 組態及 proxy 設定。此新增容錯移轉複雜性增加時的復原時間並減少其能夠診斷與疑難排解的相關步驟。
  
是否仍有疑問如何規劃及實作流量管理或 Azure ExpressRoute？請閱讀我們[網路與效能指導](https://aka.ms/tune)或[Azure ExpressRoute 常見問題集](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)的其餘部分。
  
## <a name="working-with-azure-expressroute-providers"></a>使用 Azure ExpressRoute 提供者
<a name="BKMK_high-availability"> </a>

選擇您在頻寬、 延遲、 安全性及規劃高可用性為基礎的電路的位置。一旦您知道您想要放置的最佳位置電路[檢閱目前區域所提供者的清單](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。
  
使用您的提供者或提供者來選取最佳的連線選項、 多點或裝載的點對點。請記住，可以混合及只要頻寬和其他的備援元件支援您路由與高可用性的設計符合連線選項。
  
您可以使用下列短連結返回這裡：[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>相關主題
<a name="BKMK_high-availability"> </a>

[對 Office 365 的網路連線](network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[實作 ExpressRoute for Office 365](implementing-expressroute.md)
  
[在 ExpressRoute for Office 365 案例中使用 BGP 社群 (預覽)](bgp-communities-in-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)
  
[商務用 Skype Online 中的 ExpressRoute 與 QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d) (英文)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab) (英文)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)
