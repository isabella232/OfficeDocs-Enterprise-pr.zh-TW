---
title: 管理 Office 365 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 有些企業網路一般網際網路位置限制存取，或包含大量 backhaul 或處理的網路流量。 若要確保像這些可以存取 Office 365、 網路和 proxy 的系統管理員需要管理的 Fqdn，Url、 清單及 IP 位址的網路上的電腦構成的 Office 365 端點清單。 若要新增至直接路由傳送，proxy 略過及/或防火牆規則以確保能夠連線到 Office 365 的網路要求的 PAC 檔案這些需求。
ms.openlocfilehash: 99445e6feac84a6091888422039e8ba655d246c9
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072485"
---
# <a name="managing-office-365-endpoints"></a>管理 Office 365 端點

大多數的企業組織具有多個辦公室的位置和連線 WAN 需要需要設定的 Office 365 網路連線。 您可以藉由傳送所有受信任直接透過您的防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理，以最佳化您的網路。 這可減少延遲與周邊容量需求。 識別 Office 365 的網路流量是提供最佳的效能，為您的使用者的第一個步驟。 如需有關 Office 365 網路連線的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)。

Microsoft 建議您存取 Office 365 網路端點和變更他們使用[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。

不論您如何管理很重要的 Office 365 網路流量，Office 365 會需要網際網路連線。 其中連線是需要其他網路端點會列於[Office 365 IP 位址和 URL Web 服務中未包含的其他端點](additional-office365-ip-addresses-and-urls.md)。

如何使用 Office 365 網路端點將取決於您企業組織的網路架構。 本文概述與 Office 365 IP 位址和 Url 可以整合企業網路架構的幾種方式。 選擇 [信任的網路要求的最簡單方式是使用 SDWAN 裝置支援自動化的 Office 365 設定在每個辦公室位置。

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>針對本機分支輸出很重要的 Office 365 網路流量的 SDWAN

在每個分公司位置，您可以提供設定為 Office 365 最佳化類別端點或最佳化的流量路由傳送，並允許類別，直接向 Microsoft 網路 SDWAN 裝置。 其他網路流量，包括內部部署資料中心流量、 一般網際網路網站流量，以及 Office 365 預設類別端點流量傳送至您能更顯著的網路周邊的另一個位置。

Microsoft 會使用 SDWAN 提供者來啟用自動的設定。 如需詳細資訊，請參閱[Office 365 網路合作夥伴計劃](office-365-networking-partner-program.md)。

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>使用 PAC 檔案進行的重要的 Office 365 流量直接路由傳送

使用 PAC 或 WPAD 檔案來管理 Office 365 與相關聯，但沒有 IP 位址的網路要求。 透過 proxy 或周邊裝置傳送的一般網路要求增加延遲。 雖然 SSL 中斷，並檢查建立的最大延遲，其他服務例如 proxy 驗證和信譽查閱會導致效能不佳，以及不正確的使用者體驗。 此外，這些周邊網路裝置需要容量足以處理所有的網路連線要求。 我們建議您略過 proxy 或檢查裝置的 Office 365 網路的直接要求。
  
[PowerShell 圖庫 Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)是 PowerShell 指令碼會讀取來自 Office 365 IP 位址和 URL Web 服務的最新的網路端點，並建立範例 PAC 檔案。 您可以修改指令碼，使其與您現有的 PAC 檔案管理整合。

![透過防火牆或 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**圖 1-簡單的企業周邊網路**

PAC 檔案部署到在圖 1 點 1 的網頁瀏覽器中。 使用時的 PAC 檔案直接輸出很重要的 Office 365 網路流量，您也需要在您的網路周邊防火牆允許這些 Url 後面的 IP 位址的連線。 這是所擷取的 PAC 檔案中指定同一個 Office 365 端點類別的 IP 位址及建立防火牆的 Acl，根據這些地址。 圖 1 中的資料點 3 皆防火牆。

分開如果您選擇不要只直接針對最佳化類別端點，您傳送給 proxy 伺服器的類別端點將需要略過繼續處理的 proxy 伺服器中所列的任何必要允許進行路由傳送。 例如，SSL 符號並檢查及 Proxy 驗證與不相容的最佳化和允許類別端點。 圖 1 中的資料點 2 proxy 伺服器。

常見的設定為允許而無需處理來自拜訪人次 proxy 伺服器的 Office 365 網路流量的目的地 IP 位址使用 proxy 伺服器的所有輸出流量。 使用 SSL，然後檢查問題的相關資訊，請參閱[使用協力廠商的網路裝置或在 Office 365 流量的解決方案](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)。

有兩種類型的 Get-PacFile 指令碼會產生的 PAC 檔案。

|**類型**|**描述**|
|:-----|:-----|
|**1** <br/> |將最佳化端點流量直接和其他所有項目傳送至 proxy 伺服器。 <br/> |
|**2** <br/> |將直接最佳化和允許端點流量和其他所有項目傳送至 proxy 伺服器。 此類型也可以用來傳送所有支援 ExpressRoute ExpressRoute 的網路區段的 Office 365 流量和其他 proxy 伺服器的每個項目。 <br/> |

以下是呼叫的 PowerShell 指令碼的簡單範例：

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

有一些您可以傳遞至指令碼的參數：

|**參數**|**描述**|
|:-----|:-----|
|**ClientRequestId** <br/> |這是必要的會傳遞至代表在用戶端電腦進行呼叫 web 服務的 GUID。 <br/> |
|**Instance** <br/> |預設值為全球網站 Office 365 服務執行個體。 也會傳遞至 web 服務。 <br/> |
|**TenantName** <br/> |您的 Office 365 租用戶名稱。 傳遞至 web 服務，並做為某些 Office 365 url 可取代的參數。 <br/> |
|**類型** <br/> |您想要產生 proxy PAC 檔案的類型。 <br/> |

以下是呼叫與其他參數的 PowerShell 指令碼的另一個範例：

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxy 伺服器略過 Office 365 的網路流量的處理

其中的 PAC 檔案不會用於直接輸出的流量，您仍然想要設定您的 proxy 伺服器，以略過您周邊網路上的處理。 在[Office 365 網路合作夥伴計劃](office-365-networking-partner-program.md)中所述，某些 proxy 伺服器廠商已啟用自動的的設定。

如果您執行此動作以手動方式將需要取得 [最佳化和允許來自 Office 365 IP 位址和 URL Web 服務的端點分類資料並設定您的 proxy 伺服器，以略過處理這些。 請務必避免 SSL 會自動換行和檢查及 Proxy 驗證針對最佳化和允許類別端點。
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Office 365 IP 位址和 Url 的變更管理

除了選取適當的設定您周邊網路，則務必您採用 Office 365 端點變更管理程序。 這些端點定期變更，如果您不是管理所做的變更，您可以結束與封鎖的使用者或與效能不佳後新增的 IP 位址或 URL 新增。

靠近每個月的最後一天通常被發佈至 Office 365 IP 位址和 Url 的變更。 有時變更將會發佈之外，因為作業排程、 支援或安全性需求。

變更發行時，需要您採取行動，因為已新增的 IP 位址或 URL，您應該會接收來自我們將發佈變更，直到該端點上的 Office 365 服務時的 30 天通知。 雖然我們目標此通知期間，可能永遠無法可能因為作業、 支援、 或安全性需求。 不需要維護的連線，例如即時運算] 動作的變更移除 IP 位址或 Url，或更低的重大變更，不包括事先通知。 不論提供哪些通知，則我們會列出每次變更的預期的服務 active 日期。

### <a name="change-notification-using-the-web-service"></a>使用 Web 服務的變更通知

若要取得的變更通知，您可以使用 Office 365 IP 位址和 URL Web 服務。 我們建議您先呼叫 **/version** web 方法一次一小時來檢查您用來連線到 Office 365 端點的版本。 如果此版本有所變更時，您必須使用中的版本進行比較，然後您應該從 **/endpoints** web 方法取得最新的端點資料並選擇性地從 **/changes** web 方法取得差異。 您不需要呼叫 **/endpoints**或 **/changes** web 方法如果尚未有您發現版本的任何變更。

如需詳細資訊，請參閱[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。

### <a name="change-notification-using-rss-feeds"></a>使用 RSS 摘要的變更通知

Office 365 IP 位址和 URL Web 服務提供您可以在 Outlook 中訂閱 RSS 摘要。 有 RSS Url 上每個 Office 365 服務執行個體特有頁面 IP 位址和 Url 的連結。 如需詳細資訊，請參閱[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>變更通知及核准檢閱使用 Microsoft Flow

我們理解，您仍可能需要手動處理來自每個月的網路端點變更。 若要建立流量，通知您透過電子郵件，並選擇性地執行變更核准程序，Office 365 網路端點有變更時，您可以使用 Microsoft Flow。 檢閱完成之後，您可以自動電子郵件所做的變更防火牆和 proxy 伺服器管理小組的流程。

如需 Microsoft Flow 範例和範本的資訊，請參閱[使用 Microsoft Flow 接收電子郵件到 Office 365 IP 位址和 Url 的變更](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)。
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 網路端點常見問題集

Office 365 連線的相關的常見問題集的系統管理員問題：
  
### <a name="how-do-i-submit-a-question"></a>如何提交問題？

按一下連結，以指出文章是否已有幫助底部並送出任何其他的問題。 我們監視意見反應，並使用最常見問題集更新的問題。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何判斷我的租用戶的位置？

 **租用戶的位置**是最佳決定使用我們的[資料中心對應](https://aka.ms/datamaps)。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>'M 我對等適當地與 Microsoft 嗎？

 在[與 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。
  
與超過 2500 ISP 對等關係全域和 70 點的目前狀態，我們取得從您的網路應該一致。 無法傷害花幾分鐘的時間，並確定您的 ISP 對等關係是最最佳的作法[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)的良好且不會所以良好對等手有其專屬到我們的網路。
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>我不是在 [發佈] 清單上看到的 IP 位址的網路要求，我需要提供給他們的存取權？
<a name="bkmk_MissingIP"> </a>

我們只會提供您應該將直接路由至 Office 365 伺服器的 IP 位址。 這不是所有您會看到的網路要求的 IP 位址的完整清單。 您會看到 Microsoft 和協力廠商擁有、 發佈、 IP 位址的網路要求。 這些 IP 位址會以動態方式產生或受管理的方式，可防止及時通知他們變更時。 如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。
  
請參閱 < IP 相關聯 Office 365 上您想要的詳細資訊嗎？
  
1. 請檢查是否 IP 位址會包含在較大的發佈範圍使用[CIDR [小算盤]](https://www.ipaddressguide.com/cidr)。
2. 請參閱協力廠商是否擁有 IP 與[whois 查詢](https://dnsquery.org/)。 如果是 Microsoft 所擁有，可能是內部的協力廠商。
3. 檢查憑證，在瀏覽器中連線至 IP 位址使用*HTTPS://\<IP_ADDRESS\> * ，檢查憑證，以了解哪些網域相關聯的 IP 位址上列出的網域。 如果它是 Microsoft 所擁有的 IP 位址，而且不在清單上的 Office 365 IP 位址，很可能的 IP 位址是與 Microsoft CDN 例如*MSOCDN.NET*或不含已發佈的 IP 資訊的另一個 Microsoft 網域相關聯。 如果您發現在憑證上的網域是其中一個我們宣告清單的 IP 位址，請讓我們知道。

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>某些 Office 365 Url 指向筆 CNAME 記錄，而不是在 「 DNS A 記錄。 我有的 CNAME 記錄？

用戶端電腦都必須包含一或多個 IP Address(s) 連線到雲端服務的 DNS A 或 AAAA 記錄。 Office 365 中包含一些 Url 顯示筆 CNAME 記錄，而不是 A 或 AAAA 記錄。 這些 CNAME 記錄是介且可能會有數個鏈結中。 它們永遠最終會將 IP 位址來解析的 A 或 AAAA 記錄。 例如，請考慮以下一系列的 DNS 記錄，其最終會解析為 IP 位址_IP_1_:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

這些 CNAME 重新導向是 DNS 的一般組件，而且是透明的用戶端電腦和透明 proxy 伺服器。 它們可用於負載平衡、 內容傳遞網路、 高可用性和服務意外事件緩和措施。 Microsoft 不會發佈的中間的 CNAME 記錄、 他們受限於任何時候，變更，您應該不需要將它們設定為允許在您的 proxy 伺服器。

Proxy 伺服器會驗證這在上述範例中是 serviceA.office.com 初始 URL，而此 URL 可能會包含在 Office 365 發佈。 Proxy 伺服器要求的 IP 位址至該 URL 的 DNS 解析，也會收到備份 IP_1。 它不會驗證中繼 cname 重新導向。

硬式編碼設定或間接的 Office 365 Fqdn 為基礎的核准清單不建議使用，不受支援的 Microsoft，和已知會造成客戶連線問題。 封鎖 CNAME 重新導向，或，否則不正確的 DNS 解決方案解決 Office 365 DNS 項目，就可以解決透過 DNS 條件轉寄 （範圍限定為直接使用 Office 365 Fqdn） 與 DNS 遞迴啟用。 許多協力廠商周邊網路產品原生整合建議他們使用[Office 365 IP 位址和 URL Web 服務](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)的設定中的 Office 365 端點核准清單。

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>為什麼看名稱，例如 nsatc.net 或 akadns.net Microsoft 網域名稱？
<a name="bkmk_akamai"> </a>

Office 365 和其他 Microsoft 服務使用幾個協力廠商服務，例如 Akamai 和 MarkMonitor 改善您的 Office 365 使用經驗。 保留給予您的最佳經驗，我們可能會變更這些服務在未來。 協力廠商網域可能裝載內容，例如 CDN，或他們可能會主控服務，例如地理位置的流量管理服務。 目前所使用的服務包括：
  
當您看到所提出的要求時，將在使用[MarkMonitor](https://www.markmonitor.com/) * \*。 nsatc.net* 。 這項服務提供網域名稱保護和監控，以防範惡意的行為。
  
當您看到要求時，將在使用[ExactTarget](https://www.marketingcloud.com/) * \*。 exacttarget.com* 。 這項服務會提供電子郵件連結管理和監視對抗惡意的行為。
  
[Akamai](https://www.akamai.com/)正在使用中，當您看到包含下列其中一個下列 Fqdn 的要求。 這項服務提供地理 DNS 和內容傳遞網路服務。
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>我必須要有可能的最小連線的 Office 365
<a name="bkmk_thirdparty"> </a>

此為 Office 365 內建函式，在網際網路上的服務套件，可靠性與可用性 promise 取決於許多標準的網際網路服務不會出現。 例如，DNS、 CRL，等 Cdn 的標準網際網路服務必須能夠使用 Office 365，就像它們必須能夠使用大部分現代的網際網路服務。

Office 365 套件細分主要服務區域。 這些可以選擇性地啟用的連線，且沒有這是所有相依性，而且一定要有的一般區域。

|**服務區域**|**描述**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online 和 Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online 和商務用 OneDrive <br/> |
|**商務用 Skype Online 及 Microsoft Teams** <br/> |Skype for Business 和 Microsoft Teams <br/> |
|**通用** <br/> |Office 365 專業增強版、 瀏覽器中，Azure AD 中的 Office 和其他常見的網路端點 <br/> |

除了基本的網際網路服務，還有只用來整合功能的協力廠商服務。 雖然整合需要這些項目，它們被標示為選用這表示服務的核心功能將會繼續運作如果端點無法存取 Office 365 端點文件中。 任何網路端點，如此才會有 required 屬性設定為 true。 這是選用的任何網路端點會有必要的屬性設定為 false 並備忘稿屬性將詳細說明如果封鎖的連線，您應該會遺失的功能。
  
如果您嘗試使用 Office 365，並會尋找第三方服務無法存取您會想要[確保標示為必要或選用本文中的所有 Fqdn 則都允許通過 proxy 和防火牆](urls-and-ip-address-ranges.md)。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何封鎖對 Microsoft 的消費者服務存取權？
<a name="bkmk_consumer"> </a>

限制存取我們的消費者服務應自行承擔風險。 限制存取權*login.live.com* FQDN 為封鎖消費者服務僅可靠的方法。 廣泛的服務，包括非消費者服務，例如 MSDN、 TechNet，與其他人使用此 FQDN。 此 FQDN 也由 Microsoft 支援服務的安全檔案 Exchange 程式，需要傳輸檔案，以利 Microsoft 產品的疑難排解。  限制存取此 FQDN，可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。
  
請記住封鎖存取單獨的 Microsoft 消費者服務不會防止您網路上的使用者功能使用 Office 365 租用戶或其他服務的 exfiltrate 資訊。
  
## <a name="related-topics"></a>相關主題

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[Microsoft Azure Datacenter IP 範圍](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公用 IP 空間](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的網路基礎結構需求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute 與 Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[Office 365 網路連線原則](office-365-network-connectivity-principles.md)
