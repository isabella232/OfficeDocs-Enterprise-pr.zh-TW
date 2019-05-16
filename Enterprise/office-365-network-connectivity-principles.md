---
title: Office 365 網路連線原則
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: 在您開始規劃您的 Office 365 網路連線的網路之前，請務必了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。 本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。
ms.openlocfilehash: 2d8b629d291be44da3d3360e676e7a01d9cd5a35
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069819"
---
# <a name="office-365-network-connectivity-principles"></a>Office 365 網路連線原則

在您開始規劃您的 Office 365 網路連線的網路之前，請務必了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。 本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。
  
傳統企業網路主要被設計來提供使用者存取應用程式和使用強式周邊安全性裝載在 21vianet 運作的公司資料中心中的資料。 傳統模型假設，使用者會存取應用程式和資料從內部公司網路外圍透過 WAN 連結從分公司，或從遠端透過 VPN 連線。 
  
SaaS 應用程式，如 Office 365 採用移動一些組合的服務和周邊網路外部的資料。 最佳化，而使用者與 SaaS 應用程式之間的流量受限於引入的封包檢查、 網路 hairpin 以取得、 不慎連線遠距端點及其他因素的延遲。 您可以確保 Office 365 的最佳效能和可靠性藉由瞭解和實作關鍵最佳化指導方針。
  
在本文中，您將了解：
  
- [Office 365 架構](office-365-network-connectivity-principles.md#BKMK_Architecture)時套用至 [客戶連線至雲端
- 更新的[Office 365 連線能力原則](office-365-network-connectivity-principles.md#BKMK_Principles)和最佳化網路流量，以及使用者體驗的策略
- [Office 365 端點 web 服務](office-365-network-connectivity-principles.md#BKMK_WebSvc)，可讓網路系統管理員可以使用結構化用於網路最佳化端點的清單
- [新的 Office 365 端點類別](office-365-network-connectivity-principles.md#BKMK_Categories)和最佳化的指導方針
- [比較具有端點安全性的網路周邊安全性](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- 針對 Office 365 流量的[累加最佳化](office-365-network-connectivity-principles.md#BKMK_IncOpt)選項

## <a name="office-365-architecture"></a>Office 365 架構
<a name="BKMK_Architecture"> </a>

Office 365 是提供一套多樣化的微型服務和應用程式，例如 Exchange Online、 SharePoint Online、 Skype for Business Online、 Microsoft 透過生產力和共同作業案例分散式的軟體為-服務 (SaaS) 雲端Microsoft teams、 Exchange Online Protection、 Office Online 及許多其他人。 雖然特定的 Office 365 應用程式可能會有其獨特的功能，套用至客戶網路和連線至雲端時，它們會共用一些重要的主體、 目標及架構模式。 這些主體和架構模式進行連線都是一般的許多其他 SaaS 定域機組並同時正在截然不同的平台為-服務和基礎結構以-服務的 cloud，例如 Microsoft 的典型的部署模型Azure。
  
下列其中一個 Office 365 （也就是通常會接或誤解網路規劃者） 的最大顯著性架構功能是它是真正的全球化之分散式的服務，在內容中的使用者如何連接到它。 目標 Office 365 租用戶的位置務必了解的客戶資料在雲端中的儲存位置，但 Office 365 的使用者經驗不涉及直接連線至包含資料的磁碟。 Office 365 （包括效能、 可靠性和其他重要的品質特性） 的使用者經驗牽涉到透過向外延展數百個 Microsoft 地點跨全球高度分散的服務前方門連線。 在大部分的情況下，最佳使用者經驗，允許使用者要求路由傳送至最接近的 Office 365 服務進入點，客戶網路，而不是透過輸出中的點的中央位置或地區連線到 Office 365 來達成。
  
對於大多數的客戶，Office 365 使用者分散許多不同的位置。 若要達到最佳結果，此文件中所概述的原則應該要搜尋在從延展 （未擴充） 的觀點，將重點放在最佳化連線至最接近 Microsoft 全球網路中的目前狀態點，而非地理Office 365 租用戶的位置。 基本上，這表示即使 Office 365 租用戶資料可能會儲存在特定的地理位置，該租用戶的 Office 365 體驗維持分散式和中可以存在非常關閉 （網路） 鄰近的租用戶都有每個使用者位置.
  
## <a name="office-365-connectivity-principles"></a>Office 365 連線能力原則
<a name="BKMK_Principles"> </a>

Microsoft 建議下列原則以達到最佳的 Office 365 連線能力與效能。 使用這些 Office 365 連線能力原則來管理您的流量，並連線至 Office 365 時取得最佳的效能。
  
網路設計中的主要目標應該是延遲降至最低，藉由減少的來回行程時間 (RTT) 從您的網路成 Microsoft 全球網路，具有低延遲連接所有 Microsoft 資料中心的 Microsoft 的公用網路骨幹部署及雲端擴張世界各地的應用程式的進入點。 您可以深入了解在[如何 Microsoft 建置其快速且可靠的全球網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 全球網路。
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>識別並區分 Office 365 流量

![找出 Office 365 流量](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
識別 Office 365 的網路流量是能夠從一般網際網路的網路流量區分該流量的第一個步驟。 Office 365 連線能力您可最佳化所實作的方法，例如網路路由最佳化、 防火牆規則、 瀏覽器 proxy 設定] 和 [略過某些端點的網路檢查裝置的組合。
  
先前的 Office 365 最佳化指導方針分成兩個類別，**必要**和**選用**的 Office 365 端點。 為端點已新增至支援新的 Office 365 服務和功能，我們已經重新組織，Office 365 端點分為三種類別：**最佳化**、**允許**和**預設值**。 針對每個類別的指導方針適用於類別中，進行最佳化容易了解和實作中的所有端點。 
  
如需 Office 365 端點類別和最佳化方法的詳細資訊，請參閱 <<c0>新的 Office 365 端點類別] 區段。
  
Microsoft 現在發佈為 web 服務的所有 Office 365 端點，並提供如何使用此資料的最佳的指引。 如需有關如何擷取並搭配 Office 365 端點的詳細資訊，請參閱[Office 365 Url 和 IP 位址範圍](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)。
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>在當地輸出網路連線

![在當地輸出網路連線](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
本機 DNS 和網際網路的輸出是進入的非常重要的減少連線延遲，以確保使用者的連線數目會對最接近的 Office 365 服務點。 在複雜的網路拓撲中，請務必在一起實作本機 DNS 和本機網際網路輸出。 如需 Office 365 如何路由的用戶端連線到最接近的進入點的詳細資訊，請參閱[用戶端連線](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)。
  
之前的雲端服務，例如 Office 365 推出，使用者做為設計因素網路架構中的網際網路連線能力是相當簡單。 當網際網路服務與網站分散各地時，公司輸出點與任何指定的目的端點之間的延遲是距離的主要的函式地理位置。
  
在傳統網路架構中，所有輸出網際網路連線周遊公司網路時，以及從中央位置的輸出。 為 Microsoft 的雲端供應項目有變種，分散式的網際網路對向網路架構已成為重要支援區分延遲的雲端服務。 Microsoft 全球網路用意是要配合使用分散式服務 Front Door 基礎結構，將雲端服務的傳入連線路由傳送至最接近的進入點的全域的進入點的動態 fabric 延遲需求。 這被要減少 「 上次哩 」 的長度的 Microsoft 雲端客戶來有效地縮短客戶與雲端之間的路由。
  
企業 Wan 通常被為了進行輸出到網際網路時，通常是透過一或多個 proxy 伺服器之前檢查中央公司總部 backhaul 網路流量。 下圖說明這類網路拓撲。
  
![傳統企業網路模型](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
因為 Office 365 會執行在 Microsoft 全球網路，包含在世界各地的前端伺服器，通常會接近使用者的位置的前端伺服器。 藉由提供本機網際網路輸出，並藉由設定內部 DNS 伺服器，以提供 Office 365 端點的本機名稱解析，目的地是 Office 365 的網路流量可以連線到 Office 365 前端伺服器盡可能給使用者。 下圖顯示可讓使用者從主要的 office、 分公司和遠端位置連線到最接近的 Office 365 進入點會遵循最短的路由的網路拓撲範例。
  
![具有區域輸出點的 WAN 網路模型](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
縮短的網路路徑至 Office 365 進入點，以這種方式可改善連線的效能和使用者體驗在 Office 365 中，可以同時協助減少未來的變更網路架構對 Office 365 效能的影響和可靠性。
  
此外，DNS 要求可能導致延遲，如果回應的 DNS 伺服器距或忙線中。 您可以延遲降至最低名稱解析佈建本機 DNS 伺服器，在分公司位置中的，確定它們會適當地設定為快取的 DNS 記錄。
  
雖然區域的輸出可適用於 Office 365，是最佳的 connectivity 模型一律會提供使用者的位置，不論是否將公司網路或遠端位置，例如 home、 飯店、 咖啡廳上的網路輸出和機場。 下圖中表示此本機直接輸出模型。
  
![本機輸出網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
使用者必須採用 Office 365 企業版能夠充分運用 Microsoft 全球網路分散式服務 Front Door 架構來確保使用者連線到 Office 365 到最接近的 Microsoft 全球網路項目採取的最短可能路由點。 本機輸出網路架構會藉由使用 Office 365 流量進行路由傳送透過最接近的輸出，不論使用者的位置。
  
本機輸出架構透過傳統模型具有下列優點：
  
- 提供 Office 365 的最佳效能最佳化路由長度。 使用者連線所以動態方式路由傳送至最接近的 Office 365 進入點的分散式服務 Front Door 基礎結構。
- 藉由使用本機輸出，可減少在公司網路基礎結構上的負載。
- 利用用戶端端點安全性與雲端安全性功能來保護上兩個端點的連線。

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>避免網路 hairpin

![避免 hairpin](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
為一般的經驗法則，使用者和最接近的 Office 365 端點之間的最短，最直接路由會提供最佳的效能。 WAN 或 VPN 流量繫結的特定目的地第一次導入至另一個中間的位置 （例如安全性堆疊，雲端存取代理人，雲端式 web 閘道的），情況網路髮夾延遲和潛在的重新導向至簡介遠距端點。 網路 hairpin 以取得也會造成路由/對等的效率或不是很理想的 （遠端） DNS 查閱。
  
若要確保，Office 365 連線能力不會受限於網路 hairpin 以取得甚至是在本機的輸出的情況下，請檢查是否可用於提供使用者位置的網際網路輸出已與 Microsoft 全球網路中的直接對等關係的 ISP 關閉至該位置的近似值。 您可能也想要設定輸出路由傳送至直接傳送受信任的 Office 365 流量，而不是 proxy 處理或透過協力廠商雲端或雲端式網路安全性廠商通道，處理您的網際網路的流量。 本機 DNS 名稱解析的 Office 365 端點有助於確保，除了直接路由傳送，最接近的 Office 365 進入點時使用的是使用者的連線數目。
  
如果您使用雲端為基礎的網路或您的 Office 365 流量的安全性服務，請確定 「 髮夾 」 效果會評估及瞭解其對 Office 365 效能的影響。 這可以透過檢查的數目和位置的分公司和 Microsoft 全球網路對等點，網路對等關係的品質數目的關係透過其轉送流量服務提供者位置完成您的 ISP 和 Microsoft 服務提供者基礎結構中回載的效能影響與服務提供者。
  
因為大量的 Office 365 進入點與使用者對於鄰近的分配位置中，路由至任何協力廠商的網路或安全性提供者的 Office 365 流量可以有負面的影響 Office 365 連線的提供者網路不為達到最佳的 Office 365 對等設定。
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>評估略過 proxy，流量檢查裝置及重複安全性技術

![略過 proxy 流量檢查裝置，重複安全性技術](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
企業客戶應該檢閱其網路安全性和特別針對 Office 365 的風險減少方法繫結流量及使用 Office 365 安全性功能來降低其侵入依賴、 效能影響，以及昂貴的網路安全性Office 365 的網路流量的技術。
  
大部分的企業網路強制使用像是 proxy、 SSL 檢查、 封包檢查和資料遺失防護系統的技術的網際網路流量的網路安全性。 這些技術提供重要的風險降低一般網際網路要求，但是可以大幅降低效能、 延展性及套用至 Office 365 端點時的使用者體驗的品質。
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 端點 web 服務

Office 365 系統管理員可以使用指令碼或耗用來自 Office 365 端點的端點的結構化的清單的 REST 呼叫 web 服務及更新的周邊防火牆設定和其他網路裝置。 這可確保繫結的 Office 365 的流量會識別、 適當處理和受管理以不同方式從繫結的一般和通常未知的網際網路網站的網路流量。 如需有關如何使用 Office 365 端點 web 服務，請參閱[Office 365 Url 和 IP 位址範圍](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)的文章。
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC （Proxy 自動組態） 指令碼
<a name="BKMK_WebSvc"> </a>

Office 365 系統管理員可以建立可以傳遞至使用者的電腦，透過 WPAD 或 GPO 的 PAC （Proxy 自動組態） 指令碼。 PAC 指令碼可用來略過 proxy WAN 或 VPN 使用者從 Office 365 要求可讓 Office 365 流量使用直接網際網路連線，而不是周遊公司網路。
  
#### <a name="office-365-security-features"></a>Office 365 安全性功能
<a name="BKMK_WebSvc"> </a>

Microsoft 是資料中心安全性、 作業的安全性和 Office 365 伺服器與它們所代表的網路端點周圍的風險降低相關透明的。 Office 365 內建安全性功能可供降低網路的安全性風險，如資料遺失防護、 防毒、 多重要素驗證、 客戶鎖定] 方塊、 進階威脅防護，Office 365 威脅情報、 Office 365 安全分數、 Exchange Online Protection 和網路 DDOS 安全性。
  
如需有關 Microsoft 資料中心和全球網路安全性的詳細資訊，請參閱[Microsoft 信任中心](https://www.microsoft.com/en-us/trustcenter/security)。
  
## <a name="new-office-365-endpoint-categories"></a>新的 Office 365 端點類別
<a name="BKMK_Categories"> </a>

Office 365 端點代表具有不同的網路位址和子網路。 端點的 Url，可能 IP 位址或 IP 範圍，而且某些端點會列出使用特定的 TCP/UDP 連接埠。 Url 可以是*account.office.net* ，像是 FQDN 或相對 URL like * \*。.office365.com*。
  
> [!NOTE]
> Office 365 租用戶資料的位置不直接相關的 Office 365 端點網路內的位置。 基於這個理由，客戶應查看 Office 365 為分散式和全域服務，而且應該不會嘗試為封鎖地理準則為基礎的 Office 365 端點的網路連線。
  
在管理 Office 365 流量我們先前指引，端點已分成兩個類別，**必要**和**選用**。 許多客戶面臨挑戰權衡的 Office 365 Url 和 IP 位址的完整清單相同網路最佳化的應用程式和每個類別中的端點所需重要性根據不同的最佳化的服務]。 
  
在新模型中，端點被分為三種類別，**最佳化**、**允許**和**預設值**，在哪裡可以實現的最佳的效能改進功能，並傳回焦點網路最佳化努力提供優先順序為基礎的樞紐分析投資。 端點會合併上述類別為基礎的案例的網路品質、 磁碟區及效能信封並簡化實作有效的使用者體驗的敏感度。 建議的最佳化可套用至指定的類別中的所有端點的相同方式。
  
- **最佳化**端點所需的每個 Office 365 服務的連線，並代表超過 75%的 Office 365 的頻寬、 連線和資料量。 這些端點表示最敏感的網路效能、 延遲及可用性的 Office 365 案例。 在 Microsoft 資料中心主控的所有端點。 此類別中的端點變更速率預期會遠低於其他兩個類別的端點。 此類別包含 Url 和一組定義的 IP 子網路專用於核心 Office 365 工作負載，例如 Exchange Online、 SharePoint Online、 Skype for Business Online 及 Microsoft Teams 的機碼 （控制項會 ~ 10) 非常小組。

    定義良好的要徑端點緊縮的清單應該協助您規劃及實作更快且更容易這些目的地的高價值網路最佳化。

    *最佳化*端點的範例包括*https://outlook.office365.com*， *https://\<租用戶\>。 sharepoint.com*和*https://\<租用戶\>-my.sharepoint.com* 。

    最佳化的方法如下：

  - 略過或 whitelist*最佳化*端點上的網路裝置與執行流量攔截、 SSL 解密、 深層封包檢查及內容篩選的服務。
  - 略過內部部署 proxy 裝置和常用於一般網際網路瀏覽的雲端式 proxy 服務。
  - 優先順序為完全信任的網路基礎結構和周邊系統這些端點的評估。
  - 設定優先順序減少或消除 WAN 回載，並且最使用者/分支位置盡可能接近利直接分散式架構的網際網路輸出，這些端點。
  - 藉由實作分割通道利直接連線的 VPN 使用者這些雲端端點。
  - 請確定 IP 位址的 DNS 名稱解析傳回符合這些端點的路由輸出路徑。
  - 優先順序 SD WAN 整合直接、 最小延遲路由到最接近網際網路對等點 Microsoft 全球網路這些端點。

- **允許**端點所需的連線至特定的 Office 365 服務與功能，但不是對網路效能和延遲不如*最佳化*類別中敏感。 從頻寬及連線計數的觀點來看這些端點的整體網路使用量也會大幅較小的。 這些端點專用於 Office 365，並裝載於 Microsoft 資料中心。 它們代表廣泛的 Office 365 微型服務，以及其相依性 （控制項會 ~ 100 Url) 及預期變更以較高的速率，比*最佳化*類別中。 定義專用的 IP 子網路與此類別中的並非所有端點相關都聯。

    *允許*端點的網路最佳化可改善 Office 365 的使用者經驗，但有些客戶可能會選擇範圍這些最佳化可取得更多窄到最小變更他們的網路。

    *允許*端點的範例包括*https://\*。 protection.outlook.com*和*https://accounts.accesscontrol.windows.net*。

    最佳化的方法如下：

  - 略過或 whitelist*允許*端點上的網路裝置與執行流量攔截、 SSL 解密、 深層封包檢查及內容篩選的服務。
  - 優先順序為完全信任的網路基礎結構和周邊系統這些端點的評估。
  - 設定優先順序減少或消除 WAN 回載，並且最使用者/分支位置盡可能接近利直接分散式架構的網際網路輸出，這些端點。
  - 請確定 IP 位址的 DNS 名稱解析傳回符合這些端點的路由輸出路徑。
  - 優先順序 SD WAN 整合直接、 最小延遲路由到最接近網際網路對等點 Microsoft 全球網路這些端點。

- **預設**端點表示 Office 365 服務和相依性，不需要任何最佳化，並且可以被視為由客戶網路一般網際網路繫結的流量。 請注意此類別中的有些端點可能不裝載於 Microsoft 資料中心。 範例包括*https://odc.officeapps.live.com*和*https://appexsin.stb.s-msn.com*。

如需 Office 365 網路最佳化技巧的詳細資訊，請參閱[管理 Office 365 端點](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview)。
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>比較具有端點安全性的網路周邊安全性
<a name="BKMK_SecurityComparison"> </a>

傳統的網路安全性的目標是來強化公司網路周邊抵禦入侵和惡意攻擊。 為組織採用 Office 365，有些網路服務和資料是部分或完全移轉至雲端。 當沒有任何基礎網路架構變更，此程序需要新興因素納入考量的網路安全性重新評估：
  
- 為雲端服務會採用，網路服務和資料分散在內部部署資料中心與雲端之間而且不再足夠合用周邊安全性。
- 遠端使用者連線至內部部署資料中心中並不受控制的位置，例如家庭、 旅館或咖啡館從雲端中的公司資源。
- 特殊用途的安全性功能逐漸內建於雲端服務和可以有潛在補充或取代現有的安全性系統。

Microsoft 提供整體範圍的 Office 365 安全性功能，並提供採用安全性最佳作法，可協助您確保資料和網路安全性的 Office 365 的規範指引。 建議的最佳作法如下：
  
- **使用多重要素驗證 (MFA)** MFA 會藉由要求使用者確認電話、 文字訊息或其智慧型手機上的應用程式通知正確輸入其密碼之後，將額外的保護層級新增至強式密碼策略。

- **使用 Office 365 雲端 App 安全性**設定追蹤異常的活動，並對它的原則。 設定與 Office 365 雲端 App 安全性的提醒，以系統管理員可以檢閱不尋常或高風險使用者活動，例如下載大量的資料，多失敗的登入嘗試或連線來自未知或危險的 IP 位址。

- **設定資料外洩防護 (DLP)** DLP 可讓您識別敏感資料，並建立原則，以協助防止使用者意外或故意共用資料。 DLP 的運作方式，讓您的使用者可以符合規範，而不中斷其工作流程包括 Exchange Online、 SharePoint Online 和 OneDrive 的 Office 365。

- **使用客戶加密箱**身為 Office 365 系統管理員，您可以使用 Customer Lockbox 控制 Microsoft 支援工程師如何協助工作階段期間存取您的資料。 在工程師需要存取您的資料來排解及修正問題的情況下，Customer Lockbox 可讓您核准或拒絕存取要求。

- **使用 Office 365 安全分數**安全分數是種安全性分析工具，建議您能夠如何進一步降低風險。 安全分數會查看您的 Office 365 設定和活動，並比較它們，由 Microsoft 所建立的基線。 您會看到如何對齊您使用最佳安全性作法為基礎的分數。

增強的安全性的全面性方法應該包含下列考量：
  
- 移動強調周邊安全性向藉由套用 [雲端式的端點安全性及 Office 用戶端的安全性功能。
  - 安全性周邊網路壓縮到資料中心
  - 啟用使用者裝置 office 內或在遠端位置的對等信任
  - 專注於保護資料的位置及使用者位置
  - 受管理的使用者機器具有高信任具有端點安全性
- 所有的資訊安全性管理，而不只可以在周邊網路上的焦點
  - 重新定義 WAN，並允許信任的流量可以略過安全性裝置並分隔受管理的裝置來賓 Wi-fi 網路來建置周邊網路的安全性。
  - 降低網路的安全性需求的公司 WAN edge
  - 減少某些網路周邊安全性裝置例如防火牆仍然為必需，但是載入
  - 確保 Office 365 流量的本機輸出
- 改善解決逐漸[累加最佳化](office-365-network-connectivity-principles.md#BKMK_IncOpt)一節所述。 某些最佳化技巧還可提供更佳的成本效益比率，根據您的網路架構，您應該選擇做為您的組織最有意義的最佳化。

如需有關 Office 365 安全性與合規性的詳細資訊，請參閱 <<c0>的安全性與 Office 365 的合規性概觀的文章。
  
## <a name="incremental-optimization"></a>累加最佳化
<a name="BKMK_IncOpt"> </a>

我們表示的 SaaS 的理想的網路連線能力模型，稍早在本文章中，但針對在過去複雜網路架構，許多大型組織，就不會實際直接進行所有的這些變更。 在這個部分，我們討論可以協助改善 Office 365 的效能與可靠性的增量變更的數目。
  
您將會使用，以最佳化 Office 365 流量的方法將視您的網路拓撲以及您實作的網路裝置而異。 有許多位置與複雜的網路安全性作法的大型企業將需要開發策略，其中包含大部分或所有而較小的組織可能只會在[Office 365 連線能力原則](office-365-network-connectivity-principles.md#BKMK_Principles)] 區段中所列的原則需要考慮下列一或兩個。
  
您可以方法最佳化，累加程序，不斷地套用每一種方法。 下表列出使用者的最大數目對延遲和可靠性其影響的順序金鑰最佳化方法。
  
|**最佳化方法**|**描述**|**影響**|
|:-----|:-----|:-----|
|本機 DNS 解析無法與網際網路輸出  <br/> |佈建中每個位置的本機 DNS 伺服器，並確定該 Office 365 連線通往網際網路盡可能到使用者的位置。  <br/> | 延遲降至最低  <br/>  改善可靠連線到最接近的 Office 365 進入點  <br/> |
|新增地區輸出點  <br/> |如果您的公司網路有多個位置，但只有一個出口點，新增地區輸出點，以讓使用者連線到最接近的 Office 365 進入點。  <br/> | 延遲降至最低  <br/>  改善可靠連線到最接近的 Office 365 進入點  <br/> |
|略過 proxy 並檢查裝置  <br/> |使用 Office 365 要求直接傳送到輸出點為單位的 PAC 檔案設定瀏覽器。  <br/> 設定 edge 路由器和防火牆以允許 Office 365 流量，而不檢查。  <br/> | 延遲降至最低  <br/>  減少網路裝置上的負載  <br/> |
|啟用直接連線的 VPN 使用者  <br/> |VPN 使用者啟用 Office 365 連線，直接從使用者的網路，而不是透過 VPN 通道藉由實作分割通道。  <br/> | 延遲降至最低  <br/>  改善可靠連線到最接近的 Office 365 進入點  <br/> |
|從傳統 WAN 移轉至 SD WAN  <br/> |SD Wan （軟體定義各種區域網路） 簡化 WAN 管理，並使用來取代傳統的 WAN 路由器虛擬設備，類似於使用虛擬機器 (Vm) 的計算資源的虛擬化改善效能。  <br/> | 改善效能和 WAN 的流量可管理性  <br/>  減少網路裝置上的負載  <br/> |
