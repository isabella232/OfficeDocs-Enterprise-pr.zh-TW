---
title: 使用 ExpressRoute for Office 365 進行網路規劃
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
audience: ITPro
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
description: 適用於 Office 365 可提供第 3 層之間的連線能力您的網路與 Microsoft 資料中心。 迴路使用框線閘道通訊協定 (BGP) 路由廣告的 Office 365 的前端伺服器。 從您的內部部署裝置的觀點來看，當他們需要選取正確的 TCP/IP 路徑至 Office 365 Azure ExpressRoute 會視為網際網路的替代方案。
ms.openlocfilehash: 459850a29e87650f1aecfc6a6977cd6e5b77ae07
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069699"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>使用 ExpressRoute for Office 365 進行網路規劃

適用於 Office 365 可提供第 3 層之間的連線能力您的網路與 Microsoft 資料中心。 迴路使用框線閘道通訊協定 (BGP) 路由廣告的 Office 365 的前端伺服器。 從您的內部部署裝置的觀點來看，當他們需要選取正確的 TCP/IP 路徑至 Office 365 Azure ExpressRoute 會視為網際網路的替代方案。
  
Azure ExpressRoute 會新增至一組特定的支援的功能和服務所提供的 Microsoft 資料中心內的 Office 365 伺服器直接的路徑。 Azure ExpressRoute 不會取代與 Microsoft 資料中心部署或基本的網際網路服務，例如網域名稱解析的網際網路連線。 Azure ExpressRoute 和網際網路電路應該安全和備援。
  
下表會醒目提示內容中的 Office 365 的 Azure ExpressRoute 連線與網際網路之間的一些差異。

|**網路規劃的差異**|**網際網路網路連線**|**ExpressRoute 的網路連線**|
|:-----|:-----|:-----|
| 必要的網際網路服務，包括; 存取權  <br/>  DNS 名稱解析  <br/>  憑證撤銷驗證  <br/>  內容傳遞網路  <br/> |是  <br/> |要求送至 Microsoft 擁有 DNS 及/或 CDN 基礎結構可能使用 ExpressRoute 的網路。  <br/> |
| 存取 Office 365 服務，包括;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  商務用 Skype Online  <br/>  Office Online  <br/>  Office 365 入口網站及驗證  <br/> |是，所有應用程式和功能  <br/> |是，[特定應用程式和功能](https://aka.ms/o365endpoints) <br/> |
|內部部署在周邊安全性。  <br/> |是  <br/> |是  <br/> |
|高可用性計劃。  <br/> |容錯移轉至備用網際網路網路連線  <br/> |容錯移轉至備用 ExpressRoute 連線  <br/> |
|與可預測的網路設定檔的直接連線。  <br/> |否  <br/> |是  <br/> |
|IPv6 連線能力。  <br/> |是  <br/> |是  <br/> |

展開之標題下方的更多的網路規劃指引。 我們也已記錄系列跤深 10 篇[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)。

## <a name="existing-azure-expressroute-customers"></a>現有的 Azure ExpressRoute 客戶

如果您使用現有的 Azure ExpressRoute 線路，而且可能會想要透過此電路新增 Office 365 連線能力，您應該查看電路、 輸出位置及大小以確保它們將符合您的 Office 365 流量的需求電路的數目。 大多數客戶需要額外的頻寬，且許多需要額外的迴路。
  
若要啟用透過現有的 Azure ExpressRoute 電路存取 Office 365，以確保 Office 365 服務的 [[設定路由篩選器，](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)來存取。
  
Azure ExpressRoute 訂閱是客戶中心，意義訂閱會繫結至客戶。 身為客戶，您可以有多個 Azure ExpressRoute 電路，而且可以透過這些電路存取多個 Microsoft 雲端資源。 例如，您可以選擇存取 Azure 主控的虛擬機器、 Office 365 測試租用戶和 Office 365 生產租用戶透過一組的備援 Azure ExpressRoute 電路。
  
下表概述您可以選擇實作以上透過您的電路的對等關係的兩種類型。

|**對等關係**|**Azure 的私用**|**Microsoft**|
|:-----|:-----|:-----|
|**服務** <br/> |IaaS: Azure 虛擬機器  <br/> |PaaS: Azure 的公用服務  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|連線初始 * * * <br/> |客戶-Microsoft  <br/> Microsoft 對客戶  <br/> |客戶-Microsoft  <br/> Microsoft 對客戶  <br/> |
|**QoS 支援** <br/> |沒有 QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup>QoS 支援這次只商務用 Skype。
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>規劃 Azure ExpressRoute 的頻寬

每個 Office 365 客戶有唯一的頻寬需求的人數根據每個位置，與每個 Office 365 應用程式及其他因素影響，例如使用內部部署或混合式設備和網路的安全性組態是如何使用中。
  
具有太少頻寬，會導致擁塞、 重新傳輸的資料，以及預期的延遲狀況。 有太多的頻寬，會導致不必要的成本。 在現有的網路，頻寬通常稱為方面電路可用發揮空間量的百分比。 有 10%發揮空間會可能會導致壅塞，通常需要 80%發揮空間表示不必要的成本。 一般發揮空間目標配置是 20%到 50%。
  
若要尋找的權限層級，最佳機制是頻寬的測試您現有的網路使用率。 這是唯一的方法來取得使用狀況，則為 true 測量及需要為每個網路組態，而應用程式皆位於唯一的一些方法。 當測量您會想要密切注意總頻寬使用率、 延遲及 TCP 壅塞若要了解您的網路需求。
  
一次預估的比較基準，其中包含所有網路應用程式，組成不同的設定檔，若要判斷實際使用情形，您組織中人員的一小群試驗 Office 365 也可以使用兩個測量來估計數量您將需要為每個辦公室位置的頻寬。 如果有任何延遲或您測試中發現的 TCP 壅塞問題，您可能需要將輸出更接近移至使用 Office 365 的人員或移除密集掃描例如 SSL 解密/檢查的網路。
  
我們建議在建議的網路處理何種類型的所有適用於 ExpressRoute 和網際網路電路。 相同是針對我們的[效能調整網站](https://aka.ms/tune)的指導方針的其餘部分，則為 true。
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>套用安全性控制，可 Azure ExpressRoute for Office 365 案例

保護 Azure ExpressRoute 連線的開頭為保護網際網路連線能力相同的原則。 許多客戶選擇部署網路和周邊網路的控制項，沿著其內部部署網路連線到 Office 365 和其他 Microsoft cloud 的 ExpressRoute 路徑。 這些控制項可能包括防火牆、 應用程式 proxy、 資料外洩防護、 入侵偵測、 入侵防護系統，依此類推。 在許多情況下的客戶，請套用到從內部部署與 Microsoft 移至 [客戶內部部署網路，從內部部署移至 [一般起始的流量與從起始的流量移至 Microsoft，起始的流量的不同層級的控制項網際網路目的地。
  
以下是您選擇要部署的[ExpressRoute 連接模型](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models)整合安全性的一些範例。

|**ExpressRoute 整合選項**|**網路安全性周邊模型**|
|:-----|:-----|
|共置在雲端 exchange  <br/> |安裝新的或運用在其中建立 ExpressRoute 連線共置設備中的現有安全/周邊基礎結構。  <br/> 利用單純的路由/interconnect 用途及從內部部署安全性/周邊基礎結構的共置設備後牽引連線共置設備。  <br/> |
|點對點乙太網路  <br/> |終止點對點 ExpressRoute 連線中現有的內部部署安全性/周邊基礎結構位置。  <br/> 安裝新特定的安全/周邊基礎結構的 ExpressRoute 路徑和終止的點對點連線。  <br/> |
|任何對多 IPVPN  <br/> |利用現有內部部署安全性/周邊基礎結構在所有的 IPVPN 使用 for ExpressRoute Office 365 連線到的輸出位置。  <br/> 髮夾用於 ExpressRoute for Office 365 到特定的內部部署位置 IPVPN 指定做為安全/周邊網路。  <br/> |

某些服務提供者也提供受管理的安全性周邊功能使用 Azure ExpressRoute 其整合解決方案的一部分。
  
考慮使用 for ExpressRoute Office 365 連線的周邊網路/安全性選項的拓撲位置，以下是其他考量
  
- 深度和類型網路/安全控制項可能會有影響的效能和延展性的 Office 365 使用者體驗。

- 輸出 (上-部署-\>Microsoft) 和輸入 (Microsoft-\>內部) [如果已啟用] 流程可能會有不同的需求。 以下是可能會不同一般網際網路目的地的輸出。

- 是否透過 ExpressRoute for Office 365 或透過網際網路路由傳送流量的連接埠/通訊協定和必要的 IP 子網路的 office 365 需求都是相同的。

- 拓樸的客戶網路/安全控制措施的位置會決定最終端對端網路之間的使用者和 Office 365 服務，而且可能會有顯著影響網路延遲與壅塞。

- 客戶所建議設計其安全性/周邊拓撲，以使用使用 ExpressRoute for Office 365 依據備援、 高可用性和災害復原的最佳做法。

以下是與上述周邊安全性模型會比較不同的 Azure ExpressRoute 連線選項的 Woodgrove Bank 的範例。
  
### <a name="example-1-securing-azure-expressroute"></a>範例 1： 保護 Azure ExpressRoute
  
Woodgrove Bank 考慮實作 Azure ExpressRoute 及之後規劃[路由使用 ExpressRoute for Office 365](routing-with-expressroute.md)的最佳架構，以及使用上述指南以了解頻寬需求之後，他們正在決定保護其周邊的最佳方法。
  
Woodgrove，具有多個 continents 中的位置的跨國組織的安全性必須跨越所有周邊。 Woodgrove 的最佳的連線選項是使用多個對等的位置來服務的每個大陸其員工需要遍多點連線。 每個大陸包含大陸備援 Azure ExpressRoute 電路和安全性必須跨越所有這些。
  
Woodgrove 的現有基礎結構是可靠，而且可以處理的其他工作，因此，Woodgrove Bank 是能夠使用基礎結構的 Azure ExpressRoute 和網際網路的外圍安全性。 如果這沒有這種情況，無法選擇 Woodgrove 購買其他設備來補充其現有的設備或處理不同類型的連線。
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>高可用性和容錯移轉進行 Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

我們建議您佈建至少兩個作用中的電路從每個輸出使用 ExpressRoute ExpressRoute 提供者。 這是最常見的地方我們的客戶會看到失敗，您可以輕鬆地避免其佈建一組的主動/主動 ExpressRoute 電路。 我們也建議至少兩個主動/主動網際網路電路，因為有許多 Office 365 服務，才可使用網際網路。
  
內部網路的輸出點是許多其他裝置和扮演重要角色人員如何更加可用性的電路。 這些部分的連線情況下不涵蓋的 ExpressRoute 或 Office 365 Sla，但他們端對端服務可用性中扮演重要角色為認知貴組織中的人員所。
  
專注於使用人員與運作 Office 365 中，如果失敗的任何一個元件會影響 peoples 的體驗使用服務，尋找限制受影響的人員的總百分比的方式。 方面複雜容錯移轉模式時，請考慮很長的時間，以復原 peoples 的經驗，並尋找方面簡單且自動容錯移轉模式。
  
外部網路、 Office 365、 ExpressRoute 和您的 ExpressRoute 提供者都有不同程度的可用性。
  
### <a name="service-availability"></a>服務可用性
  
- Office 365 服務所涵蓋定義完善[的服務等級協定](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)，其中包含個別服務的執行時間和可用性度量資訊。 Office 365 可以維護這類高的服務可用性層級，就是個別的元件，順暢地許多 Microsoft 資料中心，使用這個全球 Microsoft 網路之間的容錯移轉能力的原因之一。 此容錯移轉的資料中心與網路延伸至多個網際網路輸出點，並啟用順暢地從使用服務的人員的觀點來看容錯移轉。

- ExpressRoute Microsoft 網路邊緣和 ExpressRoute 提供者或協力廠商基礎結構之間的個別專用電路[提供高達 99.9%的可用性 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) 。 這些服務等級會套用在 ExpressRoute 電路層級，其中包含[兩個獨立於連接](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)之間的備援的 Microsoft 設備和網路提供者設備中每個對等的位置。

### <a name="provider-availability"></a>提供者可用性
  
- 在您的 ExpressRoute 供應商或協力廠商停止 Microsoft 的服務層級的排列方式。 這也是您可以設定選項，會影響您的可用性層級的第一個位置。 您周邊網路與您的提供者連線，在每個 Microsoft 對等位置之間，您應該仔細評估架構、 可用性和恢復特性 ExpressRoute 商提供。 請注意，備援、 對等的設備、 電訊廠商提供 WAN 迴路邏輯和實體層面，並任何其他值新增服務，例如 NAT 服務] 或 [受管理的防火牆。

### <a name="designing-your-availability-plan"></a>設計您的可用性計劃
  
我們強烈建議您規劃及設計高可用性和恢復到您的端對端連線情況下運作的 Office 365。 設計應該包含;
  
- 沒有的單一失敗點，包括網際網路和 ExpressRoute 電路。

- 最小化的受影響的人員數以及的持續時間的影響最預期的失敗模式。

- 最佳化的簡單、 可重複，且自動復原程序，從最預期的失敗模式。

- 支援的網路流量和備援的路徑，而大幅降低不透過功能完整的需求。

您的連線情況下應該包含 Office 365 的多個獨立和作用中的網路路徑的功能已最佳化網路拓撲。 這會產生更妥善地端對端可用性比最佳化僅適用於個別的裝置或設備層級的備援的拓撲。
  
> [!TIP]
> 如果您的使用者會分配到多個 continents 或地理區域和每個位置連線到單一的 ExpressRoute 線路所在的單一內部部署位置設為備援 WAN 迴路透過，您的使用者會遇到更少端對端服務可用性比包含不同的地區連線到最接近的對等的獨立 ExpressRoute 電路網路拓撲設計的位置。
  
我們建議您佈建至少兩個 ExpressRoute 電路每個電路連線至與不同的地理對等位置。 您應該佈建其中人員時，將 Office 365 服務使用 ExpressRoute 連線每個區域的電路此主動-主動配對。 這可讓每個區域來影響主要的位置，例如資料中心或對等的位置在災害期間會保持連線。 中其對應表設定為主動/主動可讓使用者流量分散於多個網路路徑。 這可減少裝置或網路設備中斷期間受影響的人員的範圍。
  
我們不建議使用單一的 ExpressRoute 線路與網際網路做為備份。
  
### <a name="example-2-failover-and-high-availability"></a>範例 2： 容錯移轉和高可用性
  
Woodgrove Bank 的多地理設計已經過檢閱路由傳送、 頻寬、 安全性、，和現在必須經過高可用性檢閱。 Woodgrove 認為為涵蓋三種類別; 的高可用性的相關恢復能力、 可靠性和備援。
  
恢復能力可讓 Woodgrove 快速地從失敗復原。 可靠性允許 Woodgrove 提供一致的結果，在系統中。 備援可讓 Woodgrove 的基礎結構的一或多個鏡像執行個體之間移動。
  
每個 edge 設定] 中 Woodgrove 具有備援防火牆、 Proxy 和識別碼。 北美地區 Woodgrove 有其 Dallas 資料中心內的一個 edge 設定和其維吉尼亞州資料中心裡的另一個 edge 組態。 在每個位置的備援設備提供恢復能力至該位置。
  
Woodgrove Bank 在網路組態是根據幾個關鍵而建置：
  
- 每個地理區域，內有多個 Azure ExpressRoute 電路。

- 每個區域內的電路可以支援所有該區域內的網路流量。

- 路由會清楚偏好使用一或其他路徑根據可用性、 位置，依此類推。

- Azure ExpressRoute 電路之間容錯移轉會自動發生而不需要額外設定或 Woodgrove 所需的動作。

- 網際網路電路之間容錯移轉會自動發生而不需要額外設定或 Woodgrove 所需的動作。

在此組態中，使用備援在實體和虛擬層級，Woodgrove Bank 是能夠提供本機恢復能力、 區域恢復能力和全域恢復可靠的方法。 Woodgrove 選定之後評估每個區域，以及可能容錯移轉至網際網路的單一 Azure ExpressRoute 線路此組態。
  
如果 Woodgrove 找不到每個地區有多個 Azure ExpressRoute 電路，源自北美在亞太地區 Azure ExpressRoute 線路的流量路由會新增無法接受的程度的延遲與所需的 DNS 轉寄站設定會增加複雜性。
  
利用做為備份設定網際網路不建議使用。 這會中斷 Woodgrove 的可靠性原則，導致不一致的體驗，使用的連線。 此外，手動設定可能需要考慮已設定 BGP 廣告的容錯移轉、 NAT 組態、 DNS 組態，及 proxy 組態。 這新增容錯移轉複雜性會增加復原時間，並減少其能夠診斷及疑難排解的相關步驟。
  
仍然有關於如何規劃及實作流量管理 」 或 「 Azure ExpressRoute 的問題嗎？ 閱讀其餘的[網路和效能的指導](https://aka.ms/tune)方針或[Azure ExpressRoute 常見問題集](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。
  
## <a name="working-with-azure-expressroute-providers"></a>使用 Azure ExpressRoute 提供者
<a name="BKMK_high-availability"> </a>

選擇您根據您的頻寬、 延遲、 安全性和高可用性計劃的電路的位置。 一旦您知道想要放置的最佳位置迴路[檢閱目前的地區的提供者清單](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。
  
與您的提供者或提供者來選取最佳的連線選項] 中，多點，或主控的點對點搭配使用。 請記住，您可以混合及比對的連線選項，只要頻寬和其他的備援元件支援您路由與高可用性的設計。
  
您可以使用下列短連結返回這裡：[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>相關主題
<a name="BKMK_high-availability"> </a>

[對 Office 365 的網路連線](network-connectivity.md)
  
[Azure ExpressRoute for Office 365](azure-expressroute.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)
  
[實作 ExpressRoute for Office 365](implementing-expressroute.md)
  
[使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）](bgp-communities-in-expressroute.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)
  
[ExpressRoute 與 QoS skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[使用 ExpressRoute 的通話流程](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)
  
[Office 365 網路與效能調整](network-planning-and-performance.md)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)
