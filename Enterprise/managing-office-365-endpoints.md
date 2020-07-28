---
title: 管理 Office 365 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/24/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 有些商業網路會限制一般網際網路位置的存取，或包括大量 backhaul 或處理網路流量。 為了確保網路上的電腦可以存取 Office 365，網路及 proxy 系統管理員必須管理組成 Office 365 端點清單的 Fqdn、URLs 及 IP 位址清單。 這些都必須新增至 direct route、proxy 旁路和/或防火牆規則和 PAC 檔案，以確保網路要求能夠與 Office 365 取得聯繫。
ms.openlocfilehash: 335cfd3f27762c249cc9af88b169a9f0bb59bda7
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433554"
---
# <a name="managing-office-365-endpoints"></a>管理 Office 365 端點

大多數具有多個辦公室位置和連線 WAN 的企業組織，都需要 Office 365 網路連線的設定。 您可以直接透過防火牆傳送所有受信任的 Office 365 網路要求，以略過所有其他的資料包層級檢查或處理，以優化您的網路。 這可減少延遲和周邊容量需求。 識別 Office 365 網路流量是為使用者提供最佳效能的第一步。 如需有關 Office 365 網路連線的詳細資訊，請參閱[office 365 Network Connectivity 原則](office-365-network-connectivity-principles.md)。

Microsoft 建議您使用[office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)，存取 office 365 網路端點和對其所做的變更。

不論您如何管理重要的 Office 365 網路流量，Office 365 都需要網際網路連線能力。 其他需要連線的網路端點會列在[未包含在 Office 365 IP 位址和 URL Web 服務中的其他端點](additional-office365-ip-addresses-and-urls.md)。

Office 365 網路端點的使用方式將取決於您的企業組織網路架構。 本文概述商業網路架構可與 Office 365 IP 位址和 URLs 整合的幾種方式。 選擇信任哪些網路要求的最簡單方法，就是使用可在每個辦公室位置都支援自動 Office 365 設定的 SDWAN 裝置。

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN 重要 Office 365 網路流量的本機分支出口

在每個分支辦公室位置，您可以提供一個 SDWAN 裝置，將其設定為將 Office 365 的流量，[優化] 或 [優化並允許] 類別，直接傳送至 Microsoft 的網路。 其他網路流量包括內部部署資料中心流量、一般網際網路網站流量，以及到 Office 365 的流量預設類別端點會傳送到您具有較大網路周邊的另一個位置。

Microsoft 正在與 SDWAN 提供者合作以啟用自動設定。 如需詳細資訊，請參閱[Office 365 網路合作夥伴計畫](office-365-networking-partner-program.md)。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>使用 PAC 檔案，以直接路由傳送重要的 Office 365 流量

使用 PAC 或 WPAD 檔案來管理與 Office 365 相關聯但沒有 IP 位址的網路要求。 透過 proxy 或周邊裝置傳送的一般網路要求會增加延遲。 雖然 SSL 中斷及檢查會產生最大的延遲，但其他服務（如 proxy 驗證和信譽查閱）可能會導致效能不良，以及不良的使用者體驗。 此外，這些周邊網路裝置需要足夠的容量來處理所有的網路連線要求。 建議您略過您的 proxy 或檢查裝置，以進行直接的 Office 365 網路要求。
  
[PowerShell 圖庫 PacFile](https://www.powershellgallery.com/packages/Get-PacFile)是一種 PowerShell 腳本，可從 OFFICE 365 IP 位址和 URL Web 服務讀取最新的網路端點，並建立範例 PAC 檔案。 您可以修改腳本，使其與現有的 PAC 檔管理整合。

![透過防火牆和 proxy 連接至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**圖 1-簡單的商業網路周邊**

PAC 檔案會部署至網頁瀏覽器，其圖1的點1。 使用 PAC 檔案以直接出口重要的 Office 365 網路流量時，您也需要允許連線至位於網路周邊防火牆上的這些 URLs 的 IP 位址。 若要執行此動作，請從 PAC 檔案中所指定的相同 Office 365 端點類別提取 IP 位址，並根據這些位址建立防火牆 ACLs。 防火牆是圖1中的點3。

另外，如果您選擇只對優化類別端點執行直接路由，則您傳送至 proxy 伺服器的任何必要的允許類別端點都必須列在 proxy 伺服器中，以略過進一步的處理。 例如，SSL 中斷及檢查及 Proxy 驗證與 Optimize 和 Allow 類別端點不相容。 Proxy 伺服器是圖1中的點2。

通用設定可讓您不需要針對命中 proxy 伺服器的 Office 365 網路流量，處理來自 proxy 伺服器的所有輸出流量。 如需有關 SSL 中斷及檢查問題的詳細資訊，請參閱[在 Office 365 流量上使用協力廠商網路裝置或解決方案](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)。

PacFile 腳本會產生兩種類型的 PAC 檔案。

|**類型**|**描述**|
|:-----|:-----|
|**1** <br/> |傳送「直接將端點流量」及其他所有內容傳送至 proxy 伺服器。 <br/> |
|**第** <br/> |Send Optimize 和 Allow endpoint 流量 direct 和其他所有代理伺服器的流量。 這種類型也可以用來將 Office 365 流量的所有支援的 ExpressRoute 都傳送至 ExpressRoute 網路段，並將其他內容傳送至 proxy 伺服器。 <br/> |

以下是呼叫 PowerShell 腳本的簡單範例：

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

您可以傳遞至腳本的參數數目如下：

|**參數**|**描述**|
|:-----|:-----|
|**ClientRequestId** <br/> |這是必要的，也就是傳遞給 web 服務的 GUID，代表進行通話的用戶端電腦。 <br/> |
|**Instance** <br/> |預設為全球通用的 Office 365 服務實例。 也會傳遞到 web 服務。 <br/> |
|**TenantName** <br/> |您的 Office 365 租使用者名稱。 傳遞至 web 服務，並在某些 Office 365 URLs 中做為可取代的參數。 <br/> |
|**類型** <br/> |您要產生之 proxy PAC 檔案的類型。 <br/> |

以下是另一個以其他參數呼叫 PowerShell 腳本的範例：

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Office 365 網路流量的 Proxy 伺服器旁路處理

在直接輸出流量中不會使用 PAC 檔案，您仍然想要設定 proxy 伺服器，繞周邊網路進行處理。 部分 proxy 伺服器廠商已依照[Office 365 網路合作夥伴計畫](office-365-networking-partner-program.md)中所述，啟用此功能的自動設定。

如果您是手動執行這項操作，則需要從 Office 365 IP 位址和 URL Web 服務取得 [優化] 和 [允許] 端點類別資料，然後將 proxy 伺服器設定為略過處理。 請務必避免對 Optimize 和 Allow 類別端點進行 SSL 中斷及檢查及 Proxy 驗證。
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP 位址和 URLs 的變更管理

除了為您的網路周邊選擇適當的設定之外，您也必須採用 Office 365 端點的變更管理程式。 這些端點定期變更，而且如果您不管理變更，您可以在新增 IP 位址或 URL 之後，封鎖封鎖的使用者或效能不良。

Office 365 IP 位址和 URLs 的變更通常會在每個月的最後一天發佈近。 有時候，由於運作、支援或安全性需求，將會在該排程之外發佈變更。

當發佈需要您採取行動的變更時，因為已新增 IP 位址或 URL，因此在發佈變更之前，您應該會收到30天的通知，直到該端點上有 Office 365 服務為止。 雖然我們以這種通知週期為目標，但由於運作、支援或安全性需求可能並非總可能。 不需要立即採取動作來維護連線的變更（例如已移除的 IP 位址或 URLs 或較少的重大變更）不會包含提前通知。 不論提供什麼通知，我們都會列出每項變更的預期服務 active 日期。

### <a name="change-notification-using-the-web-service"></a>使用 Web 服務變更通知

您可以使用 Office 365 IP 位址和 URL Web 服務來取得變更通知。 建議您每小時呼叫一次 **/version** web 方法，檢查您用來連線至 Office 365 的端點版本。 如果此版本變更與您使用的版本相比較，則應該從 **/endpoints** web 方法取得最新的端點資料，並選擇性地從 **/changes** web 方法取得差異。 如果您找到的版本沒有任何變更，則不需要呼叫 **/endpoints**或 **/changes** web 方法。

如需詳細資訊，請參閱[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。

### <a name="change-notification-using-rss-feeds"></a>使用 RSS 摘要的變更通知

Office 365 IP 位址和 URL Web 服務提供您可以在 Outlook 中訂閱的 RSS 摘要。 在 [IP 位址] 和 [URLs] 的每個 Office 365 服務實例特有頁面上，都有 RSS URLs 的連結。 如需詳細資訊，請參閱[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>使用 Microsoft 流程變更通知和核准檢查

我們知道您可能仍然需要手動處理每月所進行的網路端點變更。 您可以使用 Microsoft 流程建立透過電子郵件通知您的流程，也可以在 Office 365 網路端點有變更時，執行變更的核准程式。 完成複查後，您就可以讓流程自動以電子郵件傳送防火牆和 proxy 伺服器管理小組所做的變更。

如需 Microsoft 流程範例與範本的相關資訊，請參閱[使用 Microsoft Flow 接收電子郵件以取得 Office 365 IP 位址和 URLs 的變更](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 網路端點常見問題

有關 Office 365 連線的常見系統管理員問題：
  
### <a name="how-do-i-submit-a-question"></a>如何提交問題？

按一下底部的連結，以指出該文章是否有説明，並提交其他任何問題。 我們會監控意見反應，並使用最常見的要求來更新這裡的問題。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何判斷我的承租人的位置？

 **租使用者位置**最適合使用我們的[資料中心地圖](https://aka.ms/datamaps)來決定。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>我是否與 Microsoft 有適當的對等專案？

 對**等位置**會在[與 Microsoft 的對](https://www.microsoft.com/peering)等內容中詳細說明。
  
透過70全球超過2500個 ISP 對等關係，從您的網路到我們的目前狀態，應順利進行。 在幾分鐘內，請確定您的 ISP 的對等關係是最好的方式，[以下是一些](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)好的範例，而且對我們的網路有很好的對等運作。
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>我在已發佈的清單上看到 [網路對 IP 位址的要求]，是否需要提供存取權？

我們只會提供您應直接路由傳送至的 Office 365 伺服器的 IP 位址。 這不是所有 IP 位址的完整清單，您會看到您的網路要求。 您會看到 Microsoft 和協力廠商擁有、未發佈的 IP 位址的網路要求。 這兩個 IP 位址會以動態方式產生或管理，以防止變更時及時看到通知。 如果您的防火牆無法根據這些網路要求的 Fqdn 允許存取，請使用 PAC 或 WPAD 檔案來管理要求。
  
如需詳細資訊，請參閱與 Office 365 相關聯的 IP。
  
1. 檢查使用 CIDR 計算機的較大發布範圍中是否包含 IP 位址，例如[IPv4](https://www.ipaddressguide.com/cidr)或[IPv6](https://www.ipaddressguide.com/ipv6-cidr)。 例如，40.96.0.0/13 會包含 IP 位址40.103.0.1，但40.96 不符合40.103。
2. 查看合作夥伴是否擁有[Whois 查詢](https://dnsquery.org/)的 IP。 如果是由 Microsoft 所擁有，它可能是內部合作夥伴。 許多夥伴網路端點會列為屬於_預設_類別，但不會發佈 IP 位址。
3. IP 位址可能不是 Office 365 或 dependency 的一部分。 Office 365 網路端點發佈不包含所有的 Microsoft 網路端點。
4. 檢查憑證，在瀏覽器使用*HTTPS:// \<IP_ADDRESS\> *連線至 IP 位址時，請檢查憑證上所列的網域，以瞭解哪些網域與 ip 位址相關聯。 如果是 Microsoft 所擁有的 IP 位址，而不是在 Office 365 IP 位址清單上，則此 IP 位址可能會與 Microsoft CDN 相關聯，例如*MSOCDN.NET*或其他未發佈 IP 資訊的 microsoft 網域。 如果您在憑證上找到的網域是我們宣告列出 IP 位址的一個，請告訴我們。

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>部分 Office 365 URLs 指向 CNAME 記錄，而不是 DNS 中的記錄。 如何處理 CNAME 記錄？

用戶端電腦需要 DNS A 或 AAAA 記錄，其中包含一個或多個連線至雲端服務的 IP 位址。 有些 URLs 包含在 Office 365 中，會顯示 CNAME 記錄，而不是 A 或 AAAA 記錄。 這些 CNAME 記錄是仲介的，而鏈中可能有數個。 它們永遠會最後解析為 IP 位址的 A 或 AAAA 記錄。 例如，請考慮下列 DNS 記錄系列，最後解析為 IP 位址_IP_1_：

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

這些 CNAME 重新導向是 DNS 的一般部分，對用戶端電腦透明，對 proxy 伺服器而言是透明的。 它們是用來進行負載平衡、內容傳遞網路、高可用性及服務事件減輕。 Microsoft 不會發佈中間 CNAME 記錄，它們可能會隨時變更，而且您不需要在 proxy 伺服器中以允許的方式加以設定。

Proxy 伺服器會驗證上述範例中的初始 URL 是否為 serviceA.office.com，且此 URL 會包含在 Office 365 發佈中。 Proxy 伺服器會要求將該 URL 的 DNS 解析為 IP 位址，並且會接收回 IP_1。 它不會驗證中間 CNAME 重新導向記錄。

Microsoft 不支援使用實編碼設定或 whitelisting，而是以間接的 Office 365 Fqdn 為基礎，而且知道會造成客戶連線問題。 在 CNAME 重新導向上封鎖的 DNS 解決方案，或是以錯誤方式解析 Office 365 DNS 專案的 DNS 解決方案，可透過 DNS 條件式轉移（範圍限定為直接使用的 Office 365 Fqdn）來透過已啟用 DNS 遞迴加以解決。 許多協力廠商網路周邊產品會以本機方式[，使用 office 365 IP 位址和 URL Web 服務](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)，將建議的 Office 365 端點 whitelisting 整合在其設定中。

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>為什麼我會在 Microsoft 功能變數名稱中看到名稱，例如 nsatc.net 或 akadns.net？

Office 365 和其他 Microsoft 服務使用數種協力廠商服務，例如 Akamai 和 MarkMonitor，以提升您的 Office 365 體驗。 為了讓您盡可能獲得最佳的體驗，我們可能會在將來變更這些服務。 協力廠商網域可以主控內容，例如 CDN，也可以主控服務，例如地理流量管理服務。 目前使用的某些服務包括：
  
當您看到包含* \* nsatc.net*的要求時， [MarkMonitor](https://www.markmonitor.com/)正在使用中。 此服務提供功能變數名稱保護和監視，以防範惡意行為。
  
當您看到* \* exacttarget.com*的要求時， [ExactTarget](https://www.marketingcloud.com/)正在使用中。 此服務提供電子郵件連結管理，並監控惡意行為。
  
當您看到包含下列其中一個 Fqdn 的要求時， [Akamai](https://www.akamai.com/)正在使用中。 這種服務提供地理位置 DNS 和內容傳遞網路服務。
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>我必須具備 Office 365 的最小連線能力

由於 Office 365 是一套可透過網際網路運作的服務，因此可靠性和可用性承諾是以許多標準網際網路服務為基礎。 例如，您必須能夠存取諸如 DNS、CRL 和 Cdn 等標準網際網路服務，才能使用 Office 365，就像他們必須能夠存取大多數現代的網際網路服務一樣。

Office 365 套件會分解為主要的服務區域。 您可以選擇性地為連線啟用這些功能，且有一個共同的範圍，都是共同性的，而且永遠都是必要的。

|**服務區域**|**描述**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online 和 Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online 和商務用 OneDrive <br/> |
|**商務用 Skype Online 及 Microsoft Teams** <br/> |商務用 Skype 和 Microsoft 團隊 <br/> |
|**通用** <br/> |Office 365 Pro Plus，Office in browser，Azure AD，及其他一般網路端點 <br/> |

除了基本的網際網路服務之外，還有協力廠商服務只是用來整合功能。 雖然這些是整合所需要的，但在 Office 365 端點文章中標示為選用，這表示當端點無法存取時，服務的核心功能仍可繼續運作。 任何必要的網路端點都必須將必要屬性設定為 true。 任何選用的網路端點，都必須將必要的屬性設定為 false，而且 [notes] 屬性將會詳細說明當連線封鎖時，應預期的遺失功能。
  
如果您嘗試使用 Office 365，而且找不到協力廠商服務可供存取，您會想要[確保所有標為必要的 fqdn 或此專案中的選用，都允許透過 proxy 和防火牆](urls-and-ip-address-ranges.md)。
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何阻擋存取 Microsoft 的消費者服務？

若限制存取我們的消費者服務，應您自行承擔。 封鎖消費者服務的唯一可靠方式是限制存取*Login.live.com* FQDN。 此 FQDN 是由廣泛的一組服務所使用，包括諸如 MSDN、TechNet 及其他服務等非消費者服務。 此 FQDN 也是由 Microsoft 支援的 Secure File Exchange 程式使用，而且您必須用來傳輸檔案，以協助 Microsoft 產品進行疑難排解。  限制存取此 FQDN 可能會導致必須針對與這些服務相關聯的網路要求，包含例外規則。
  
請記住，只需要封鎖 Microsoft 消費者服務的存取，便無法讓您的網路上的使用者能夠使用 Office 365 租使用者或其他服務來 exfiltrate 資訊。

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>我的防火牆需要 IP 位址，但無法處理 URLs。 如何設定 Office 365 的功能？

Office 365 不會提供所有必要網路端點的 IP 位址。 有些只會提供為 URLs，而且會分類為預設值。 在預設類別中 URLs 應該允許透過 proxy 伺服器的要求。 如果您沒有 proxy 伺服器，請查看您如何為 URLs 使用者在網頁瀏覽器的 [位址] 欄中輸入的 web 要求進行設定。使用者也不會提供 IP 位址。 不提供 IP 位址的 Office 365 預設類別 URLs 都應該以相同的方式來設定。

## <a name="related-topics"></a>相關主題

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[Microsoft Azure Datacenter IP 範圍](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公用 IP 空間](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的網路基礎結構需求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute 和 Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[Office 365 網路連線原則](office-365-network-connectivity-principles.md)
