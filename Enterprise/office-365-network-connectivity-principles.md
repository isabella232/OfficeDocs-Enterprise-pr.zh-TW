---
title: Microsoft 365 網路連線原則
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: 在您開始為 Office 365 網路連線規劃網路之前，務必了解安全管理 Office 365 流量以及可能獲取最佳效能的連線原則。 本文將會協助您了解關於安全最佳化 Office 365 網路連線的最新指引。
ms.openlocfilehash: 83743bfcb7a2bd3ba137947b7eb65d159d039b25
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230289"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Microsoft 365 網路連線原則

*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*

在您開始規劃 Microsoft 365 網路連線的網路之前，請務必瞭解連線原則，以安全地管理 Microsoft 365 流量，並取得最佳的效能。 本文將協助您瞭解安全優化 Microsoft 365 網路連線的最新指導方針。
  
傳統企業網路的主要設計目的，是為使用者提供應用程式和資料 (裝載於公司運作的資料中心) 的存取權，同時具有強式周邊網路安全性。 傳統模型假設使用者是從公司網路周邊網路內部存取應用程式和資料，透過分公司的 WAN 連結，或是透過 VPN 連線遠端存取。
  
採用 Microsoft 365 之類的 SaaS 應用程式，會在周邊網路之外移動一些服務和資料的組合。 若沒有最佳化，使用者與 SaaS 應用程式之間的流量會受限於封包檢查、網路 hairpin、與遠距端點的不當連線和其他因素所引入的延遲。 您可以瞭解及實施重要的優化指導方針，以確保最佳的 Microsoft 365 效能和可靠性。
  
在本文中，您將了解：
  
- [Microsoft 365 架構](office-365-network-connectivity-principles.md#BKMK_Architecture)，在套用至雲端的客戶連接時
- 更新[Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles)的連線原則及策略，以優化網路流量和使用者體驗
- [Office 365 端點 Web 服務](office-365-network-connectivity-principles.md#BKMK_WebSvc)，允許網路系統管理員在網路最佳化中使用端點的結構化清單
- [新的 Office 365 端點類別](office-365-network-connectivity-principles.md#BKMK_Categories)以及最佳化指引
- [比較網路周邊網路安全性與端點安全性](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Microsoft 365 流量的[增量優化](office-365-network-connectivity-principles.md#BKMK_IncOpt)選項
- [Microsoft 365 連線測試](https://aka.ms/netonboard)，用來測試基本連線至 Microsoft 365 的新工具

## <a name="microsoft-365-architecture"></a>Microsoft 365 架構
<a name="BKMK_Architecture"> </a>

Microsoft 365 是一種分散式軟體即服務（SaaS）雲端，可透過一組共同服務和應用程式（例如 Exchange Online、SharePoint 線上、商務用 Skype Online、Microsoft 團隊、Exchange Online Protection、Office in 瀏覽器）及其他許多應用程式提供生產力與共同作業案例。 雖然特定的 Microsoft 365 應用程式在套用至雲端的客戶網路和連線功能時，其獨特的功能，但都會共用一些重要的主體、目標和架構模式。 對於其他許多 SaaS 群而言，這些原則和架構模式是常見的，而且與平臺即服務和基礎結構即服務群的一般部署模型不同，例如 Microsoft Azure。
  
Microsoft 365 的其中一個最重要的結構功能（即網路架構師經常錯過或誤解）是一種真正的全域分散式服務，其內容是使用者連線的方式。 目標 Microsoft 365 租使用者的位置很重要，您必須瞭解客戶資料儲存在雲端的位置，但 Microsoft 365 的使用者體驗不會直接連線至包含資料的磁片。 使用 Microsoft 365 （包括效能、可靠性及其他重要品質特性）的使用者體驗，會包括透過高分散式服務前端門的連線功能，可跨全球數百個 Microsoft 位置擴充。 在大多數情況下，您可以透過讓客戶網路將使用者要求路由傳送至最接近的 Microsoft 365 服務進入點，而不是透過中央位置或地區的出局點來連線至 Microsoft 365，以取得最佳的使用者體驗。
  
對大多數客戶而言，Microsoft 365 使用者會分散在多個位置。 若要達到最佳的結果，應從向外延展（不是向上擴充）觀點來查看此檔中所述的原則，著重于優化連線到 Microsoft 全球網路的最接近狀態點，而不是 Microsoft 365 租使用者的地理位置。 實際上，這表示即使 Microsoft 365 租使用者資料可能會儲存在特定地理位置，但該租使用者的 Microsoft 365 體驗仍會保持發佈，而且可以出現在租使用者所擁有之每個使用者位置的接近（網路）。
  
## <a name="microsoft-365-connectivity-principles"></a>Microsoft 365 連線性原則
<a name="BKMK_Principles"> </a>

Microsoft 建議遵循下列原則，以取得最佳的 Microsoft 365 連線能力和效能。 使用下列 Microsoft 365 連線原則來管理您的流量，並在連接至 Microsoft 365 時取得最佳效能。
  
網路設計的主要目標應該是透過降低從您的網路到 Microsoft 全域網路、Microsoft 公用網路骨幹 (將所有低延遲 Microsoft 資料中心與遍佈全球的雲端應用程式進入點互連) 的來回行程時間 (RTT)，將延遲降至最低。 您可以在 [Microsoft 如何建置其快速且可靠的全域網路](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) 中，深入了解 Microsoft 全域網路。
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>識別並區別 Microsoft 365 流量

![識別 Microsoft 365 流量](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
識別 Microsoft 365 網路流量是可區別來自一般網際網路系結網路流量之流量的第一步。 您可以針對特定端點的各種方法（例如網路路由優化、防火牆規則、瀏覽器 proxy 設定和旁路網路檢查裝置）進行組合，以優化 Microsoft 365 連線能力。
  
舊版 Microsoft 365 優化指導會將 Microsoft 365 端點分割成兩個類別，**必要**和**選用**。 隨著已新增端點以支援新的 Microsoft 365 服務和功能，我們已將 Microsoft 365 端點重新組織成三個類別： [**優化**]、[**允許**] 和 [**預設**]。 每個類別的指導方針都適用於該類別的所有端點，讓最佳化更易於了解及實作。
  
如需 Microsoft 365 端點類別及優化方法的詳細資訊，請參閱「[新的 Office 365 端點類別](office-365-network-connectivity-principles.md#BKMK_Categories)」區段。
  
Microsoft 現在會將所有 Microsoft 365 端點發佈為 web 服務，並提供如何最佳使用此資料的指導方針。 如需如何提取及使用 Microsoft 365 端點的詳細資訊，請參閱[Office 365 URLs 及 IP 位址範圍](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)一文。
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>在當地輸出網路連線

![在當地輸出網路連線](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
本機 DNS 和網際網路出口對於減少連線延遲，並確保使用者連線進入 Microsoft 365 服務的最接近點非常重要。 在複雜的網路拓撲中。同時實作本機 DNS 和本機網際網路出口相當重要。 如需 Microsoft 365 如何將用戶端連線路由傳送至最近進入專案的詳細資訊，請參閱[Client Connectivity](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)一文。
  
在雲端服務（例如 Microsoft 365）的使用中，使用者網際網路連線成為網路架構中的設計要素，相對簡單。 當網際網路服務和網站散佈在全球各地時，公司出口點與任何指定目的地端點之間的延遲，成為地理距離很大的函數。
  
在傳統的網路架構中，所有輸出網際網路連線會周遊公司網路，然後從中央位置出口。 隨著 Microsoft 的雲端供應項目成熟，分散式網際網路對應網路架構對於支援延遲敏感雲端服務變得關鍵。 Microsoft 全域網路的設計目的是透過分散式服務 Front Door 基礎結構 (這是一個動態全域進入點網狀架構，將輸入雲端服務連線路由傳送到最接近的進入點) 來容納延遲需求。 目的在於藉由縮短客戶與雲端之間的路由，為 Microsoft 雲端客戶減少「最後一步」的長度。
  
企業 WAN 通常設計為將網路流量回傳到中央總公司，在出口到網際網路之前進行檢查，通常是透過一或多個 Proxy 伺服器。 下圖說明此類網路拓撲。
  
![傳統企業網路模型](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
因為 Microsoft 的365是在 Microsoft 全球網路上執行（包括世界各地的前端伺服器），所以通常會有前端伺服器接近使用者的位置。 透過提供本機 Internet 出局，並設定內部 DNS 伺服器來提供 Microsoft 365 端點的本機名稱解析，針對 Microsoft 365 的網路流量，可以盡可能接近使用者的 Microsoft 365 前端伺服器。 下圖顯示網路拓朴的範例，可讓使用者從主要 office、分支辦公室和遠端位置連線，以遵循最短的路徑至最接近的 Microsoft 365 進入點。
  
![具有區域出口點的 WAN 網路模型](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
以這種方式縮短 Microsoft 365 進入點的網路路徑，可提高連線效能和 Microsoft 365 中的使用者體驗，也可協助減少 Microsoft 365 效能與可靠性對網路架構的未來變更影響。
  
此外，如果回應 DNS 伺服器是遠距或忙碌中，則 DNS 要求會導致延遲。 您可以藉由在分公司位置佈建本機 DNS 伺服器，並且確定這些伺服器已設定為適當地快取 DNS 記錄，將名稱解析延遲降至最低。
  
雖然區域內出口可適用于 Microsoft 365，但最佳連線模型是永遠在使用者的位置提供網路出局，不論這是在公司網路或遠端位置（例如，住房、酒店、咖啡廳和機場）上。 下圖呈現這個本機直接出口模型。
  
![本機出口網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
已採用 Microsoft 365 的企業可以充分利用 Microsoft 全球網路的分散式服務前端架構，其方式是確保使用者與 Microsoft 365 的連線，以盡可能最短的路徑傳送至最接近的 Microsoft 全域網路進入點。 本機出局網路架構這樣做的方式是讓 Microsoft 365 流量能夠透過最近的出口路由傳送，不論使用者位置為何。
  
本機出口架構相較於傳統模型，具有以下優點：
  
- 優化路由長度，以提供最佳的 Microsoft 365 效能。 使用者連線會以分散式服務前端基礎結構的方式，動態路由傳送至最接近的 Microsoft 365 進入點。
- 藉由允許本機出口，降低公司網路基礎結構的負載。
- 藉由利用用戶端端點安全性和雲端安全性功能，保護兩個端點的連線。

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>避免網路 hairpin

![避免 hairpin](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
一般的經驗法則，使用者和最接近的 Microsoft 365 端點之間最短、最直接的路由可提供最佳效能。 在特定目的地的 WAN 或 VPN 流量第一次導向其他中間位置（例如，以雲端為基礎的 web 閘道的安全性堆疊、雲端存取代理程式）時，會發生網路髮夾，引入地理位置較遠的端點的延遲和潛在重新導向。 網路 hairpin 也可能由於路由/對等互連不足或次佳 (遠端) DNS 查閱所導致。
  
若要確保 Microsoft 365 連線不會受到網路 hairpin （即使是在本機出口情況下），請檢查用於為使用者位置提供網際網路出局的 ISP，與 Microsoft 全球網路的直接對等關係，是否與該位置密切接近。 您也可以將出局路由設定為直接傳送受信任的 Microsoft 365 流量，而不是透過處理網際網路系結流量的協力廠商雲端或雲端式網路安全性廠商進行 proxy 或通道傳送。 Microsoft 365 端點的本機 DNS 名稱解析可協助確保除了直接路由之外，使用者連線也會使用最接近的 Microsoft 365 進入點。
  
如果您使用雲端式網路或安全性服務做為 Microsoft 365 流量，請務必評估髮夾的結果，並瞭解其對 Microsoft 365 效能的影響。 可以藉由檢查服務提供者位置 (流量經由這些位置轉送) 的數量和位置，與您的分公司和 Microsoft 全域網路對等互連點的關係、服務提供者與您的 ISP 和 Microsoft 的網路對等互連關係品質，以及服務提供者基礎結構回傳的效能影響，來完成這項操作。
  
由於大量分散式位置具有 Microsoft 365 進入點，以及其對使用者的接近程度，因此，如果未設定提供者網路以取得最佳的 Microsoft 365 對等狀態，請將 Microsoft 365 流量路由傳送至任何協力廠商網路或安全性提供365者。
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>評估略過 proxy、流量檢查裝置和重複的安全性技術

![旁路 proxy、流量檢查裝置和重複的安全性技術](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
企業客戶應特別針對 Microsoft 365 系結流量檢查其網路安全性和降低風險方法，並使用 Microsoft 365 安全性功能來降低其對 Microsoft 365 網路流量的入侵、效能影響和昂貴網路安全性技術的依賴性。
  
大部分企業網路會針對使用如 Proxy、SSL 檢查、封包檢查及資料外洩防護系統等技術的網際網路流量，強制執行網路安全性。 這些技術為一般 Internet 要求提供重要的風險降低，但在套用至 Microsoft 365 端點時，可大幅降低效能、可擴充性和使用者體驗的品質。
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Office 365 端點 Web 服務

Microsoft 365 系統管理員可以使用腳本或 REST 通話，以使用 Office 365 端點 web 服務的已結構化清單，並更新周邊防火牆和其他網路裝置的設定。 這可確保針對 Microsoft 365 所系結的流量進行識別、適當地處理，並與系結及一般網際網路網站的網路流量系結，進行不同的管理。 如需如何使用 Office 365 端點 Web 服務的詳細資訊，請參閱 [Office 365 URL 和 IP 位址範圍](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US)一文。
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>PAC (Proxy 自動設定) 指令碼
<a name="BKMK_WebSvc"> </a>

Microsoft 365 系統管理員可以建立可透過 WPAD 或 GPO 傳遞給使用者電腦的 PAC （Proxy 自動設定）腳本。 您可以使用 PAC 腳本來略過 WAN 或 VPN 使用者的 Microsoft 365 要求 proxy，讓 Microsoft 365 流量能夠使用直接網際網路連線，而不是透過公司網路進行遍歷。
  
#### <a name="microsoft-365-security-features"></a>Microsoft 365 安全性功能
<a name="BKMK_WebSvc"> </a>

Microsoft 對資料中心的安全性、運作安全性和降低其所代表之網路端點的風險365降低透明。 Microsoft 365 內建的安全性功能可用於減少網路安全性風險，例如資料遺失防護、防病毒、Multi-Factor 驗證、客戶鎖定盒、高級威脅防護、Microsoft 365 威脅情報、Microsoft 365 安全分數、Exchange Online Protection 及網路 DDOS 安全性。
  
如需 Microsoft 資料中心和全域網路安全性的詳細資訊，請參閱 [Microsoft 信任中心](https://www.microsoft.com/trustcenter/security)。
  
## <a name="new-office-365-endpoint-categories"></a>新的 Office 365 端點類別
<a name="BKMK_Categories"> </a>

Office 365 端點代表不同的網路位址和子網路集合。 端點可能是 URL、IP 位址或 IP 範圍，部分端點與特定 TCP/UDP 連接埠一起列出。 URLs 可以是 FQDN （如*account.office.net*），或萬用字元 URL （如* \* office365.com*）。
  
> [!NOTE]
> 網路內 Office 365 端點的位置並不直接與 Microsoft 365 租使用者資料的位置相關。 基於此原因，客戶應以分散式和全域服務的身分查看 Microsoft 365，而不應嘗試根據地理位置的準則來封鎖 Office 365 端點的網路連線。
  
在先前管理 Microsoft 365 流量的指南中，端點已組織成兩個類別，**必要**和**選用**。 根據服務嚴重性的不同，每個類別中的端點所需的最佳化也不同，許多客戶在將相同網路最佳化應用到 Office 365 URL 和 IP 位址完整清單時面臨了挑戰。
  
在新的模型中，端點分為三個類別、[**優化**]、[**允許**] 及 [**預設**]，提供一個依重點放置網路優化工作的位置，以實現最佳效能的改善，並使投資傳回投資。 根據使用者對網路品質、數量和效能信封的有效使用者體驗敏感度和易於執行的程度，在上述類別中合併端點。 建議的最佳化可以相同方式套用到指定類別中的所有端點。
  
- 若要連線至每個 Office 365 服務，需要**優化**端點，並且代表超過75% 的 office 365 頻寬、連線和資料量。 這些端點代表最具機密網路效能、延遲和可用性的 Office 365 案例。 所有端點都裝載於 Microsoft 資料中心。 此類別中端點的變更率預期遠比其他兩個類別中的端點低。 此類別包含一組小（超過大約10個）的金鑰 URLs，以及一組定義的 IP 子網，專用於核心 Office 365 工作負載，例如 Exchange Online、SharePoint 線上、商務用 Skype Online 及 Microsoft 團隊。

    完善定義之重要端點的簡潔清單，可協助您更快速且更容易地規劃及實現這些目標的高價值網路優化。

    *優化*端點的範例包括 *https://outlook.office365.com* *HTTPs://、 \<tenant\> sharepoint.com*和*HTTPs:// \<tenant\> -my.sharepoint.com*。

    最佳化方法包括：

  - 繞*過*網路裝置上的端點，以及執行流量攔截、SSL 解密、深入封包檢查和內容篩選的服務。
  - 略過通常用於一般網際網路瀏覽的內部部署 Proxy 裝置和雲端型 Proxy 服務。
  - 優先評估您的網路基礎結構和周邊系統完全信任的這些端點。
  - 將 WAN backhauling 的減少優先順序和消除優先順序，並協助這些端點的直接分散式網際網路出口，盡可能接近使用者/分支位置。
  - 藉由實作分割通道，為 VPN 使用者促成與這些雲端端點的直接連線。
  - 確定 DNS 名稱解析所傳回的 IP 位址符合這些端點的路由出口路徑。
  - 優先處理這些端點的 SD-WAN 整合，以取得進入 Microsoft 全域網路最接近網際網路對等互連點的直接、最低延遲路由。

- **允許**端點連線至特定 Office 365 服務和功能，但不像是在 [*優化*] 類別中對網路效能和延遲的敏感性。 從頻寬和連線計數的觀點來看，這些端點的整體網路佔用也較小。 這些端點是專用於 Office 365，並且裝載於 Microsoft 資料中心。 它們代表廣泛的 Office 365 微服務及其相依性的集合 (順序為 ~100 URL)，並且預期變更率比 *「最佳化」* 類別中的端點高。 並非此類別中的所有端點都與已定義專用 IP 子網路相關聯。

    *「允許」* 端點的網路最佳化可以改善 Office 365 使用者體驗，但是部分使用者選擇將最佳化範圍更縮小，讓他們的網路變更降至最低。

    *「允許」* 端點的範例包括 *https://\*.protection.outlook.com* 和 *https://accounts.accesscontrol.windows.net*。

    最佳化方法包括：

  - 旁路：*允許*網路裝置上的端點，以及執行流量截取、SSL 解密、深入封包檢查和內容篩選的服務。
  - 優先評估您的網路基礎結構和周邊系統完全信任的這些端點。
  - 將 WAN backhauling 的減少優先順序和消除優先順序，並協助這些端點的直接分散式網際網路出口，盡可能接近使用者/分支位置。
  - 確定 DNS 名稱解析所傳回的 IP 位址符合這些端點的路由出口路徑。
  - 優先處理這些端點的 SD-WAN 整合，以取得進入 Microsoft 全域網路最接近網際網路對等互連點的直接、最低延遲路由。

- **「預設」** 端點表示不需要任何最佳化的 Office 365 服務和相依性，可以由客戶網路視為一般網際網路繫結流量。 此類別中的某些端點可能不是在 Microsoft 資料中心內主控。 範例包括 *https://odc.officeapps.live.com* 和 *https://appexsin.stb.s-msn.com*。

如需有關 Office 365 網路最佳化技術的詳細資訊，請參閱[管理 Office 365 端點](managing-office-365-endpoints.md) 一文。
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>比較網路周邊網路安全性與端點安全性
<a name="BKMK_SecurityComparison"> </a>

傳統網路安全性的目標是強化公司網路周邊網路，免於入侵和惡意攻擊。 組織採用 Microsoft 365 時，某些網路服務和資料會部分或完整地遷移至雲端。 針對網路架構的任何基礎變更，此程式需要重新評估採用下列考慮因素的網路安全性：
  
- 採用雲端服務之後，網路服務和資料會在內部部署資料中心與雲端之間散佈，周邊安全性本身已不足夠。
- 遠端使用者從內部部署資料中心和雲端中的公司資源，從無法控制的位置（例如住房、酒店和咖啡廳）連接到公司資源。
- 有目的建置的安全性功能大量內建到雲端服務，也許可以補充或取代現有的安全性系統。

Microsoft 提供一系列的 Microsoft 365 安全性功能，並提供使用安全性最佳作法的規範性指導方針，可協助您確保 Microsoft 365 的資料和網路安全性。 建議的最佳做法包括下列項目：
  
- **使用多重要素驗證 (MFA)** MFA 會藉由在使用者輸入密碼之後，要求使用者在其智慧型手機上確認電話來電、簡訊或應用程式通知，對強式密碼策略增加另外一層的保護。

- **使用 Microsoft Cloud App Security**設定原則以追蹤反常的活動，並對其進行作用。 使用 Microsoft Cloud App Security 設定警示，讓管理員可以檢閱不尋常或是有風險的使用者活動，例如下載大量的資料、多次失敗的登入嘗試或是來自未知或危險 IP 位址的連線。

- **設定資料外洩防護 (DLP)** DLP 可讓您識別敏感性資料，並且建立原則，協助防止使用者意外或故意共用資料。 DLP 可以跨 Microsoft 365 （包括 Exchange Online、線上 SharePoint 和 OneDrive）運作，讓使用者在不中斷其工作流程的情況下保持相容性。

- **使用客戶密碼箱**做為 Microsoft 365 系統管理員，您可以使用客戶密碼箱來控制 Microsoft 支援工程師如何在協助會話中存取您的資料。 在工程師需要存取您的資料來排解及修正問題的情況下，Customer Lockbox 可讓您核准或拒絕存取要求。

- **使用 Office 365 安全分數**一種安全分析工具，建議您可以做什麼以進一步降低風險。 安全分數會查看您的 Microsoft 365 設定和活動，並比較其與 Microsoft 所建立的基準。 您的得分將會以您與最佳安全性實作的相符程度為準。

用來增強安全性的整體方法應該包含下列考量：
  
- 藉由套用雲端型和 Office 用戶端安全性功能，將重點從周邊安全性切換到端點安全性。
  - 將安全性周邊縮小到資料中心
  - 針對公司內部或遠端位置的使用者裝置，啟用對等信任
  - 專注於保護資料位置和使用者位置
  - 受控使用者電腦具有端點安全性的更高信任
- 從整體管理所有資訊安全性，而不是單獨專注在周邊上
  - 重新定義 WAN 和建立周邊網路安全性，方法是允許受信任的流量略過安全性裝置，並將未受管理的裝置分割為來賓 Wi-Fi 網路
  - 減少公司 WAN edge 的網路安全性需求
  - 仍然需要某些網路周邊安全性裝置 (例如防火牆)，但是負載會減少
  - 確保 Microsoft 365 流量的本機出口
- 改進可以逐漸實施，如同[增量最佳化](office-365-network-connectivity-principles.md#BKMK_IncOpt)一節中所述。 某些最佳化技術可能會提供更佳的成本/效益比，取決於您的網路架構，您應該選擇對貴組織最有意義的最佳化。

如需 Microsoft 365 安全性和合規性的詳細資訊，請參閱[microsoft 365 安全性](https://docs.microsoft.com/microsoft-365/security)和[Microsoft 365 security](https://docs.microsoft.com/microsoft-365/compliance)一文。
  
## <a name="incremental-optimization"></a>增量最佳化
<a name="BKMK_IncOpt"> </a>

我們稍早在本文中呈現了 SaaS 的理想網路連線模型，但是對於具有歷史複雜網路架構的許多大型組織而言，直接做以上所有變更並不實際。 在本節中，我們將討論許多可協助改善 Microsoft 365 效能與可靠性的增量變更。
  
您將用來優化 Microsoft 365 流量的方法會因您的網路拓撲和您所實施的網路裝置而異。 具有許多位置和複雜網路安全性作法的大型企業，將需要開發一個策略，其中包含[Microsoft 365 connectivity 原則](office-365-network-connectivity-principles.md#BKMK_Principles)區段中所列的大部分或所有原則，而較小的組織可能只需要考慮一或兩個。
  
您可以透過增量程序來達到最佳化，接續地套用各個方法。 下表列出關鍵最佳化方法，編排方式是依照方法對於最大量使用者延遲和可靠性的影響。
  
|**最佳化方法**|**描述**|**影響**|
|:-----|:-----|:-----|
|本機 DNS 解析和網際網路出口  <br/> |在每個位置布建本機 DNS 伺服器，並確保 Microsoft 365 連線到網際網路盡可能接近使用者的位置。  <br/> | 將延遲降至最低  <br/>  提高最接近的 Microsoft 365 進入點的可靠連線能力  <br/> |
|新增區域出口點  <br/> |如果您的公司網路有多個地點，但只有一個出局點，請新增區域出局點，讓使用者能夠連線到最接近的 Microsoft 365 進入點。  <br/> | 將延遲降至最低  <br/>  提高最接近的 Microsoft 365 進入點的可靠連線能力  <br/> |
|略過 Proxy 和檢查裝置  <br/> |使用將 Microsoft 365 要求直接傳送給出局點的 PAC 檔案，設定瀏覽器。  <br/> 設定 edge 路由器和防火牆，以允許未檢查的 Microsoft 365 流量。  <br/> | 將延遲降至最低  <br/>  減少網路裝置上的負載  <br/> |
|針對 VPN 使用者啟用直接連線  <br/> |針對 VPN 使用者，啟用 Microsoft 365 連線以直接從使用者的網路連線，而不是透過透過 VPN 隧道執行分割隧道。  <br/> | 將延遲降至最低  <br/>  提高最接近的 Microsoft 365 進入點的可靠連線能力  <br/> |
|從傳統 WAN 遷移至 SD-WAN  <br/> |SD-WAN (軟體定義廣域網路) 藉由以虛擬設備來取代傳統 WAN 路由器，簡化 WAN 管理以及改進效能，類似於使用虛擬機器 (VM) 的計算資源虛擬化。  <br/> | 改善 WAN 流量的效能和管理性  <br/>  減少網路裝置上的負載  <br/> |

## <a name="related-topics"></a>相關主題

[Microsoft 365 網路連線能力一覽](office-365-networking-overview.md)

[管理 Office 365 端點](managing-office-365-endpoints.md)

[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md)

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[評估 Microsoft 365 網路連線能力](assessing-network-connectivity.md)

[Microsoft 365 的網路規劃和效能調整](network-planning-and-performance.md)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)

[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)

[內容傳遞網路](content-delivery-networks.md)

[Microsoft 365 連線測試](https://aka.ms/netonboard)

[Microsoft 如何建置其快速且可靠的全域網路](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 網路部落格](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
