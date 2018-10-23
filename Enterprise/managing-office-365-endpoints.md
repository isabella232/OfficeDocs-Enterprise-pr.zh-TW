---
title: 管理 Office 365 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 某些企業網路一般網際網路位置限制存取或包含明顯 backhaul 或處理的網路流量。若要確定在像是這些可以存取 Office 365、 網路和 proxy 的系統管理員需要管理清單的 Fqdn、 Url 和 IP 位址的網路上的電腦組成的 Office 365 端點清單。要新增至直接路由、 proxy 旁路及 （或） 的防火牆規則及 PAC 檔案以確保能夠連絡 Office 365 網路要求這些需求。
ms.openlocfilehash: a240e3deea512dacd70b377b3d47a7b6f49a235c
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697969"
---
# <a name="managing-office-365-endpoints"></a>管理 Office 365 端點

大部分企業組織若有多個辦公室位置和連接的 WAN 的需要需要有的 Office 365 網路連線設定。您可以藉由傳送的所有受信任直接透過防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理最佳化您的網路。這可減少延遲並減少周邊容量需求。用來識別 Office 365 網路流量會提供 Office 365 使用者獲得最佳效能的第一個步驟。如需 Office 365 網路連線的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)

Microsoft 建議您存取 Office 365 網路端點和使用[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)進行的變更

不論您管理的方式環 Office 365 網路流量，Office 365 需要網際網路連線能力。[其他不包含在 Office 365 IP 位址及 URL Web 服務的端點](additional-office365-ip-addresses-and-urls.md)上所列的連線需要裝載的其他網路端點

如何使用 Office 365 網路端點將取決於您企業組織的網路架構。本文概述與 Office 365 IP 位址及 Url 可以整合企業網路架構的幾種方法。選擇 [建立信任關係要求的網路最簡單的方法是使用 SDWAN 裝置的支援自動化的 Office 365 設定每一層的辦公室位置。 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>環 Office 365 網路流量的本機分支輸出的 SDWAN

在每個分公司位置，您可以提供 Office 365 最佳化] 類別中，或最佳化 SDWAN 裝置設定路由的 IP 位址並允許類別，直接與 Microsoft 的網路。包括內部部署資料中心流量、 一般網際網路網站流量和 Office 365 預設類別流量其他網路流量傳送到另一個位置有更明顯的周邊網路的位置。 

Microsoft SDWAN 提供者以啟用自動的設定運作。您可以閱讀關於[Office 365 網路協力廠商程式](office-365-networking-partner-program.md)進一步

<a name="pacfiles"> </a>
## <a name="use-of-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>環 Office 365 流量的直接路由 PAC 檔案使用的

用於管理 Office 365 與相關聯，但沒有提供 IP 位址的網路要求 PAC 或 WPAD 檔案。透過 proxy 或周邊裝置傳送的一般網路要求可能會形成額外的延遲。時自動換行 SSL 和檢查會帶來最大稅，例如 proxy 驗證和信譽查閱其他服務可能會造成不良的使用者經驗。此外，這些周邊網路裝置需要足夠的容量來處理所有網路連線要求。我們建議略過您直接的 Office 365 網路要求的 proxy 或檢查基礎結構。
  
[PowerShell 圖庫 Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)是最新的網路端點讀取 web 服務並建立範例 PAC 檔案的 PowerShell 指令碼。 

一旦您下載此指令碼，您可以使用它來產生 PAC 檔案。您也可以修改指令碼，讓它與您現有的 PAC 檔案管理整合。 

![透過防火牆及 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)圖 1-簡單的企業周邊網路

PAC 檔案部署至圖 1 點 (1) 的電腦。當使用環 Office 365 網路流量的直接輸出 PAC 檔案，您也需要允許網路周邊防火牆後方這些 Url 的 IP 位址的連線。做法是擷取 PAC 檔案中所指定同一個 Office 365 端點類別的 IP 位址和這些地址為基礎建立防火牆 Acl。防火牆顯示為圖 1 點 (3)。 

分開如果您選擇不要僅直接路由網路流量的最佳化類別端點傳送至 proxy 伺服器的類別端點必須列在 [proxy 伺服器略過進一步的處理任何必要允許的路由。例如，SSL 符號和檢查及 Proxy 驗證與不相容的最佳化和允許類別端點。Proxy 伺服器會顯示如圖 1 點 (2)。

允許從 proxy 伺服器的所有輸出流量如此拜訪人次 proxy 伺服器的 Office 365 網路流量的目的地 IP 位址，則不需要是通用設定。了解 SSL 會自動換行及[使用協力廠商網路裝置](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)或解決方案在 Office 365 流量的檢查的問題。

有兩種類型的 PAC Get PacFile 指令碼會產生的檔案。

|**類型**|**描述**|
|:-----|:-----|
|**1** <br/> |最佳化端點將流量傳送直接與所有人的 proxy 伺服器。 <br/> |
|**2** <br/> |傳送最佳化並允許直接與所有人的 proxy 伺服器的端點流量。也可以用來傳送至 ExpressRoute 網路區段與所有人的 proxy 伺服器的 Office 365 流量支援所有 ExpressRoute。 <br/> |

以下是呼叫 PowerShell 指令碼的簡單範例：

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

有一些您可以傳遞給指令碼的參數：

|**參數**|**描述**|
|:-----|:-----|
|**ClientRequestId** <br/> |這是必要的而會傳遞至代表進行通話的用戶端電腦的 web 服務的 GUID <br/> |
|**Instance** <br/> |全球網站的預設是 Office 365 服務執行個體。也傳遞給 web 服務 <br/> |
|**TenantName** <br/> |您的 Office 365 租用戶名稱。傳遞至 web 服務並做為可取代的參數中某些 Office 365 Url <br/> |
|**類型** <br/> |您想要產生 proxy PAC 檔案類型 <br/> |

以下是另一個範例呼叫 PowerShell 指令碼與其他參數：

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Proxy 伺服器旁路處理 Office 365 網路流量 

其中 PAC 檔案不會用於輸出流量導向，您仍要設定 proxy 伺服器就能節省您周邊網路上的處理。某些 proxy 伺服器廠商已啟用自動的的設定在[Office 365 網路協力廠商程式](office-365-networking-partner-program.md)中所述。如果您執行此動作手動必須取得 [最佳化並允許來自 Office 365 IP 位址及 URL Web 服務的端點類別端點資料並設定 proxy 伺服器略過這些處理。請務必避免 SSL 會自動換行及檢查和 Proxy 驗證的最佳化並允許類別端點。 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>變更管理 Office 365 的 IP 位址及 Url

選取適當設定您周邊網路，除了是重要您採用 Office 365 端點變更管理程序。這些端點定期變更且如果您不會管理所做的變更可以與封鎖的使用者結束或與效能低落之後新的 IP 位址] 或 [URL 加入。 

每個月最後一天附近通常被發佈 Url 和 Office 365 IP 位址的變更。有時變更將會發佈該排程因為作業、 支援、 或安全性需求以外的地方。

發佈變更需要將因為 IP 位址] 或 [URL 已新增採取動作時, 應預期得到的端點上有 live 的 Office 365 服務之前，我們發佈變更的時間 30 天的通知。雖然 Microsoft 目標是統此通知期間，其有時可能無法可能因為操作、 支援、 或安全性需求。移除的 IP 位址或 Url 或更少的重大變更，不包含預先通知不需要維護連線，例如立即動作的變更。不論提供何種通知，我們會列出每項變更的預期的服務 active 日期。

### <a name="change-notification-using-web-services"></a>使用 web 服務的變更通知

您可以使用 Office 365 IP 位址和 URL Web 服務，以取得變更通知。我們建議您先呼叫 /version web 方法一次一小時檢查您用來連線至 Office 365 之端點的版本。如果這個版本變更相較於您有使用中的版本，然後您應該從 /endpoints web 方法取得最新的端點資料並 （選擇性） 取得差異從 /changes web 方法。您不需要呼叫 /endpoints 或 /changes web 方法如果尚未存在您所找到之版本的任何變更。 

如需詳細資訊，請參閱[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)。

### <a name="change-notification-using-rss-feeds"></a>使用 RSS 摘要的變更通知

Office 365 IP 位址及 URL Web 服務提供 RSS 摘要您可以在 Outlook 中訂閱至。有在每個 IP 位址的 Office 365 服務執行個體特定頁面上的 RSS Url 及 Url 的連結。RSS 摘要進一步說明[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)。

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>變更通知及核准檢閱使用 Microsoft 流程

我們先了解您仍可能需要手動處理跳到每個月的網路端點變更。您可以使用 Microsoft 流程建立流程通知您的電子郵件及選擇性地變更核准程序會時執行 Office 365 網路端點已變更。檢閱完成之後，您可以自動電子郵件給防火牆及 proxy 伺服器管理小組變更的流程。 

了解 Microsoft 流程範例和範本在[使用 Microsoft 流程接收電子郵件和 Office 365 IP 位址的變更](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Office 365 網路端點常見問題集

Office 365 連線的相關的常見問題集管理員問題：
  
### <a name="how-do-i-submit-a-question"></a>如何提交問題？

按一下以指出本文若已有幫助下方的連結並送出任何其他問題。我們監視意見反應及使用最常見問題集更新的問題。
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何判斷我租用戶的位置？

 最適合使用我們的[資料中心對應](http://aka.ms/datamaps)來判定**租用戶位置**。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Am I 對等適當地向 Microsoft 吗？

 在[具有 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。
  
超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)的良好並不那麼良好對等手掌核我們的網路。 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>不是在 [發佈] 清單上查看 IP 位址的網路要求，我需要提供存取備份吗？
<a name="bkmk_MissingIP"> </a>

我們只會提供您應直接路由傳送至 Office 365 伺服器的 IP 位址。這不是所有您會看見網路要求的 IP 位址的完整清單。您會看到網路要求，以查看 Microsoft 及協力廠商擁有、 已解除發佈、 IP 位址。這些 IP 位址為動態產生或受管理的這些變更時防止及時通知的方式。如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。
  
請參閱 IP 相關聯想的詳細資訊的 Office 365 吗？
  
1. 檢查是否使用[CIDR 計算器](http://jodies.de/ipcalc)較大發佈範圍中包含的 IP 位址。
2. 請參閱協力廠商是否擁有 IP 與[whois 查詢](https://dnsquery.org/)。如果是擁有 Microsoft，則可能內部的協力廠商。
3. 檢查憑證、 在瀏覽器中連線至 IP 位址使用*HTTPS://\<IP_ADDRESS\> * ，檢查要了解哪些網域相關聯的 IP 位址的憑證上所列的網域。如果它是 Microsoft 擁有 IP 位址和不在清單上的 Office 365 IP 位址，它是可能的 IP 位址是與 Microsoft CDN 如*MSOCDN.NET*或另一個 Microsoft 網域不含已發佈的 IP 資訊相關聯。如果您不要發現憑證上的網域是一個其中我們宣告清單的 IP 位址，請讓我們知道。

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>為什麼要查看名稱 nsatc.net 或 akadns.net Microsoft 網域名稱？
<a name="bkmk_akamai"> </a>

Office 365 與其他 Microsoft 服務使用數個協力廠商服務，例如 Akamai 和 MarkMonitor 以提升您的 Office 365 功能。若要保留給予您最佳的經驗，我們可能會變更這些服務未來。在這麼做，我們通常會發佈 CNAME 記錄以指向協力廠商擁有的網域、 record 或 IP 位址。協力廠商網域可能會主控內容，例如 CDN 或時可能會主控的服務，例如地理流量管理服務。當您看到這些協力廠商提供的連線時，它們的格式重新導向或轉介，無法從用戶端初始要求。某些客戶必須以確保這種形式的轉介和重新導向允許將傳遞沒有明確地將新增可能會使用長潛在 Fqdn 第三方服務清單。
  
服務清單，可能隨時變更。一些目前所使用的服務包括：
  
[MarkMonitor](https://www.markmonitor.com/)使用中看見要求包含*\*。 nsatc.net* 。此服務會提供網域名稱保護和監控以防止遭到惡意的行為。
  
[ExactTarget](https://www.marketingcloud.com/)使用中看見要求送至*\*。 exacttarget.com* 。此服務會提供電子郵件連結管理和監控對惡意的行為。
  
當您看到包含其中一個下列 Fqdn 的要求時[Akamai](https://www.akamai.com/)未使用。此服務會提供地理 DNS 和內容傳遞網路服務。
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>我必須要有可能的基本連線 for Office 365
<a name="bkmk_thirdparty"> </a>

Office 365 是一組透過網際網路內建函數的服務、 可靠性與可用性的承諾根據所提供的許多標準網際網路服務。例如，如 DNS、 CRL、 及 Cdn 標準網際網路服務必須使用 Office 365 就如同他們必須使用最現代網際網路服務連至連至。

Office 365 套裝軟體細分主要服務區域。這些可以選擇性地啟用連線和所有相依性，一律需要在一般區域。

|**服務區域**|**描述**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online 與 Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online 和商務用 OneDrive <br/> |
|**Skype** <br/> |Skype 的業務與的 Microsoft 小組 <br/> |
|**一般** <br/> |Office 365 Pro Plus、 Office Online、 Azure AD 和其他一般網路端點 <br/> |

除了基本的網際網路服務有協力廠商所使用服務的僅限整合功能。雖然這些所需的整合，它們被標示為選用這表示核心功能的服務會繼續運作如果端點不是可存取 Office 365 端點文章中。這是必要的任何網路端點會有 required 屬性設定為 true。這是選用的任何網路端點會有必要的屬性設定為 false 並備忘稿屬性將會詳細說明應可預期如果封鎖連線缺少的功能。
  
如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何封鎖存取 Microsoft 的用戶服務？
<a name="bkmk_consumer"> </a>

限制存取我們取用者服務應在您自己的風險、 封鎖取用者服務僅可靠方法是以限制存取*login.live.com* FQDN。這個 FQDN 可供廣泛的服務包括非消費者服務，例如 MSDN、 TechNet、 和其他人。限制存取至此 fqdn 可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。
  
請記住封鎖存取 Microsoft 取用者服務來說不會阻止您網路上的某個人的能力 exfiltrate 使用 Office 365 租用戶或其他服務的資訊。
  
## <a name="related-topics"></a>相關主題

[Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)

[Microsoft Azure Datacenter IP 範圍](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公用 IP 空間](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的網路基礎結構需求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI 和 ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[Office 365 網路連線原則](office-365-network-connectivity-principles.md)
