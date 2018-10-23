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
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="ec777-105">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="ec777-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="ec777-p102">大部分企業組織若有多個辦公室位置和連接的 WAN 的需要需要有的 Office 365 網路連線設定。您可以藉由傳送的所有受信任直接透過防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理最佳化您的網路。這可減少延遲並減少周邊容量需求。用來識別 Office 365 網路流量會提供 Office 365 使用者獲得最佳效能的第一個步驟。如需 Office 365 網路連線的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)</span><span class="sxs-lookup"><span data-stu-id="ec777-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need to have configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and reduces your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your Office 365 users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="ec777-111">Microsoft 建議您存取 Office 365 網路端點和使用[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)進行的變更</span><span class="sxs-lookup"><span data-stu-id="ec777-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Services](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="ec777-p103">不論您管理的方式環 Office 365 網路流量，Office 365 需要網際網路連線能力。[其他不包含在 Office 365 IP 位址及 URL Web 服務的端點](additional-office365-ip-addresses-and-urls.md)上所列的連線需要裝載的其他網路端點</span><span class="sxs-lookup"><span data-stu-id="ec777-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="ec777-p104">如何使用 Office 365 網路端點將取決於您企業組織的網路架構。本文概述與 Office 365 IP 位址及 Url 可以整合企業網路架構的幾種方法。選擇 [建立信任關係要求的網路最簡單的方法是使用 SDWAN 裝置的支援自動化的 Office 365 設定每一層的辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="ec777-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span> 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="ec777-117">環 Office 365 網路流量的本機分支輸出的 SDWAN</span><span class="sxs-lookup"><span data-stu-id="ec777-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="ec777-p105">在每個分公司位置，您可以提供 Office 365 最佳化] 類別中，或最佳化 SDWAN 裝置設定路由的 IP 位址並允許類別，直接與 Microsoft 的網路。包括內部部署資料中心流量、 一般網際網路網站流量和 Office 365 預設類別流量其他網路流量傳送到另一個位置有更明顯的周邊網路的位置。</span><span class="sxs-lookup"><span data-stu-id="ec777-p105">At each branch office location, you can provide an SDWAN device which is configured to route IP Addresses for Office 365 Optimize category, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, generic internet web sites traffic, and Office 365 Default category traffic is sent to another location where you have a more substantial network perimeter.</span></span> 

<span data-ttu-id="ec777-p106">Microsoft SDWAN 提供者以啟用自動的設定運作。您可以閱讀關於[Office 365 網路協力廠商程式](office-365-networking-partner-program.md)進一步</span><span class="sxs-lookup"><span data-stu-id="ec777-p106">Microsoft is working with SDWAN providers to enable automated configuration. You can read further about the [Office 365 Networking Partner Program](office-365-networking-partner-program.md)</span></span>

<span data-ttu-id="ec777-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-122"></span></span>
## <a name="use-of-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="ec777-123">環 Office 365 流量的直接路由 PAC 檔案使用的</span><span class="sxs-lookup"><span data-stu-id="ec777-123">Use of a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="ec777-p107">用於管理 Office 365 與相關聯，但沒有提供 IP 位址的網路要求 PAC 或 WPAD 檔案。透過 proxy 或周邊裝置傳送的一般網路要求可能會形成額外的延遲。時自動換行 SSL 和檢查會帶來最大稅，例如 proxy 驗證和信譽查閱其他服務可能會造成不良的使用者經驗。此外，這些周邊網路裝置需要足夠的容量來處理所有網路連線要求。我們建議略過您直接的 Office 365 網路要求的 proxy 或檢查基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ec777-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While SSL Break and Inspect incurs the largest tax, other services such as proxy authentication and reputation lookup can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="ec777-129">[PowerShell 圖庫 Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)是最新的網路端點讀取 web 服務並建立範例 PAC 檔案的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ec777-129">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the web services and creates a sample PAC file.</span></span> 

<span data-ttu-id="ec777-p108">一旦您下載此指令碼，您可以使用它來產生 PAC 檔案。您也可以修改指令碼，讓它與您現有的 PAC 檔案管理整合。</span><span class="sxs-lookup"><span data-stu-id="ec777-p108">Once you download this script, you can use it to generate a PAC file. You can also modify the script so that it integrates with your existing PAC file management.</span></span> 

<span data-ttu-id="ec777-p109">![透過防火牆及 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)圖 1-簡單的企業周邊網路</span><span class="sxs-lookup"><span data-stu-id="ec777-p109">![Connecting to Office 365 through firewalls and proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png) Figure 1 - Simple enterprise network perimeter</span></span>

<span data-ttu-id="ec777-p110">PAC 檔案部署至圖 1 點 (1) 的電腦。當使用環 Office 365 網路流量的直接輸出 PAC 檔案，您也需要允許網路周邊防火牆後方這些 Url 的 IP 位址的連線。做法是擷取 PAC 檔案中所指定同一個 Office 365 端點類別的 IP 位址和這些地址為基礎建立防火牆 Acl。防火牆顯示為圖 1 點 (3)。</span><span class="sxs-lookup"><span data-stu-id="ec777-p110">The PAC file is deployed to computers at point (1) in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is shown as point (3) in Figure 1.</span></span> 

<span data-ttu-id="ec777-p111">分開如果您選擇不要僅直接路由網路流量的最佳化類別端點傳送至 proxy 伺服器的類別端點必須列在 [proxy 伺服器略過進一步的處理任何必要允許的路由。例如，SSL 符號和檢查及 Proxy 驗證與不相容的最佳化和允許類別端點。Proxy 伺服器會顯示如圖 1 點 (2)。</span><span class="sxs-lookup"><span data-stu-id="ec777-p111">Separately if you choose to only do direct routing for the route network traffic for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is shown as point (2) in Figure 1.</span></span>

<span data-ttu-id="ec777-p112">允許從 proxy 伺服器的所有輸出流量如此拜訪人次 proxy 伺服器的 Office 365 網路流量的目的地 IP 位址，則不需要是通用設定。了解 SSL 會自動換行及[使用協力廠商網路裝置](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)或解決方案在 Office 365 流量的檢查的問題。</span><span class="sxs-lookup"><span data-stu-id="ec777-p112">The common configuration is to permit all outbound traffic from the proxy server such that destination IP addresses for Office 365 network traffic that hits the proxy server is not required. Read about issues with SSL Break and Inspect at [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="ec777-143">有兩種類型的 PAC Get PacFile 指令碼會產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="ec777-143">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="ec777-144">**類型**</span><span class="sxs-lookup"><span data-stu-id="ec777-144">**Type**</span></span>|<span data-ttu-id="ec777-145">**描述**</span><span class="sxs-lookup"><span data-stu-id="ec777-145">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ec777-146">**1**</span><span class="sxs-lookup"><span data-stu-id="ec777-146">**1**</span></span> <br/> |<span data-ttu-id="ec777-147">最佳化端點將流量傳送直接與所有人的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ec777-147">Send Optimize endpoint traffic direct and all else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="ec777-148">**2**</span><span class="sxs-lookup"><span data-stu-id="ec777-148">**2**</span></span> <br/> |<span data-ttu-id="ec777-p113">傳送最佳化並允許直接與所有人的 proxy 伺服器的端點流量。也可以用來傳送至 ExpressRoute 網路區段與所有人的 proxy 伺服器的 Office 365 流量支援所有 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="ec777-p113">Send Optimize and Allow endpoint traffic direct and all else to the proxy server. Can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and all else to the proxy server.</span></span> <br/> |

<span data-ttu-id="ec777-151">以下是呼叫 PowerShell 指令碼的簡單範例：</span><span class="sxs-lookup"><span data-stu-id="ec777-151">Here's a simple example of calling the PowerShell script:</span></span>

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="ec777-152">有一些您可以傳遞給指令碼的參數：</span><span class="sxs-lookup"><span data-stu-id="ec777-152">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="ec777-153">**參數**</span><span class="sxs-lookup"><span data-stu-id="ec777-153">**Parameter**</span></span>|<span data-ttu-id="ec777-154">**描述**</span><span class="sxs-lookup"><span data-stu-id="ec777-154">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ec777-155">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="ec777-155">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="ec777-156">這是必要的而會傳遞至代表進行通話的用戶端電腦的 web 服務的 GUID</span><span class="sxs-lookup"><span data-stu-id="ec777-156">This is required and is a GUID passed to the web service that represents the client machine making the call</span></span> <br/> |
|<span data-ttu-id="ec777-157">**Instance**</span><span class="sxs-lookup"><span data-stu-id="ec777-157">**Instance**</span></span> <br/> |<span data-ttu-id="ec777-p114">全球網站的預設是 Office 365 服務執行個體。也傳遞給 web 服務</span><span class="sxs-lookup"><span data-stu-id="ec777-p114">The Office 365 service instance which defaults to Worldwide. Also passed to the web service</span></span> <br/> |
|<span data-ttu-id="ec777-160">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="ec777-160">**TenantName**</span></span> <br/> |<span data-ttu-id="ec777-p115">您的 Office 365 租用戶名稱。傳遞至 web 服務並做為可取代的參數中某些 Office 365 Url</span><span class="sxs-lookup"><span data-stu-id="ec777-p115">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs</span></span> <br/> |
|<span data-ttu-id="ec777-163">**類型**</span><span class="sxs-lookup"><span data-stu-id="ec777-163">**Type**</span></span> <br/> |<span data-ttu-id="ec777-164">您想要產生 proxy PAC 檔案類型</span><span class="sxs-lookup"><span data-stu-id="ec777-164">The type of the proxy PAC file that you want to generate</span></span> <br/> |

<span data-ttu-id="ec777-165">以下是另一個範例呼叫 PowerShell 指令碼與其他參數：</span><span class="sxs-lookup"><span data-stu-id="ec777-165">Here's another example of calling the PowerShell script with additional parameters:</span></span>

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="ec777-166">Proxy 伺服器旁路處理 Office 365 網路流量</span><span class="sxs-lookup"><span data-stu-id="ec777-166">Proxy server bypass processing of Office 365 network traffic</span></span> 

<span data-ttu-id="ec777-p116">其中 PAC 檔案不會用於輸出流量導向，您仍要設定 proxy 伺服器就能節省您周邊網路上的處理。某些 proxy 伺服器廠商已啟用自動的的設定在[Office 365 網路協力廠商程式](office-365-networking-partner-program.md)中所述。如果您執行此動作手動必須取得 [最佳化並允許來自 Office 365 IP 位址及 URL Web 服務的端點類別端點資料並設定 proxy 伺服器略過這些處理。請務必避免 SSL 會自動換行及檢查和 Proxy 驗證的最佳化並允許類別端點。</span><span class="sxs-lookup"><span data-stu-id="ec777-p116">Where PAC files are not used for direct outbound traffic, you will still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). If you are doing this manually you will need to obtain the Optimize and Allow endpoint category endpoint data from the Office 365 IP Address and URL Web Services and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span> 
  
<span data-ttu-id="ec777-171"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-171"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="ec777-172">變更管理 Office 365 的 IP 位址及 Url</span><span class="sxs-lookup"><span data-stu-id="ec777-172">Change management for Office 365 IP Addresses and URLs</span></span>

<span data-ttu-id="ec777-p117">選取適當設定您周邊網路，除了是重要您採用 Office 365 端點變更管理程序。這些端點定期變更且如果您不會管理所做的變更可以與封鎖的使用者結束或與效能低落之後新的 IP 位址] 或 [URL 加入。</span><span class="sxs-lookup"><span data-stu-id="ec777-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span> 

<span data-ttu-id="ec777-p118">每個月最後一天附近通常被發佈 Url 和 Office 365 IP 位址的變更。有時變更將會發佈該排程因為作業、 支援、 或安全性需求以外的地方。</span><span class="sxs-lookup"><span data-stu-id="ec777-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="ec777-p119">發佈變更需要將因為 IP 位址] 或 [URL 已新增採取動作時, 應預期得到的端點上有 live 的 Office 365 服務之前，我們發佈變更的時間 30 天的通知。雖然 Microsoft 目標是統此通知期間，其有時可能無法可能因為操作、 支援、 或安全性需求。移除的 IP 位址或 Url 或更少的重大變更，不包含預先通知不需要維護連線，例如立即動作的變更。不論提供何種通知，我們會列出每項變更的預期的服務 active 日期。</span><span class="sxs-lookup"><span data-stu-id="ec777-p119">When a change is published that requires you to take action because an IP address or URL was added, you should expect to receive 30 days notice from the time we published the change until there is live Office 365 service on that endpoint. Although Microsoft aims for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP Addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we will list the expected service active date for each change.</span></span>

### <a name="change-notification-using-web-services"></a><span data-ttu-id="ec777-181">使用 web 服務的變更通知</span><span class="sxs-lookup"><span data-stu-id="ec777-181">Change notification using web services</span></span>

<span data-ttu-id="ec777-p120">您可以使用 Office 365 IP 位址和 URL Web 服務，以取得變更通知。我們建議您先呼叫 /version web 方法一次一小時檢查您用來連線至 Office 365 之端點的版本。如果這個版本變更相較於您有使用中的版本，然後您應該從 /endpoints web 方法取得最新的端點資料並 （選擇性） 取得差異從 /changes web 方法。您不需要呼叫 /endpoints 或 /changes web 方法如果尚未存在您所找到之版本的任何變更。</span><span class="sxs-lookup"><span data-stu-id="ec777-p120">You can use the Office 365 IP Address and URL Web Services to get change notification. We recommend you call the /version web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the /endpoints web method and optionally get the differences from the /changes web method. It is not necessary to call the /endpoints or /changes web methods if there has not been any change to the version you found.</span></span> 

<span data-ttu-id="ec777-186">如需詳細資訊，請參閱[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ec777-186">For more information, see [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="ec777-187">使用 RSS 摘要的變更通知</span><span class="sxs-lookup"><span data-stu-id="ec777-187">Change notification using RSS feeds</span></span>

<span data-ttu-id="ec777-p121">Office 365 IP 位址及 URL Web 服務提供 RSS 摘要您可以在 Outlook 中訂閱至。有在每個 IP 位址的 Office 365 服務執行個體特定頁面上的 RSS Url 及 Url 的連結。RSS 摘要進一步說明[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ec777-p121">The Office 365 IP Address and URL Web Services provide an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance specific pages for the IP addresses and URLs. The RSS feed is further described in the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="ec777-191">變更通知及核准檢閱使用 Microsoft 流程</span><span class="sxs-lookup"><span data-stu-id="ec777-191">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="ec777-p122">我們先了解您仍可能需要手動處理跳到每個月的網路端點變更。您可以使用 Microsoft 流程建立流程通知您的電子郵件及選擇性地變更核准程序會時執行 Office 365 網路端點已變更。檢閱完成之後，您可以自動電子郵件給防火牆及 proxy 伺服器管理小組變更的流程。</span><span class="sxs-lookup"><span data-stu-id="ec777-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span> 

<span data-ttu-id="ec777-195">了解 Microsoft 流程範例和範本在[使用 Microsoft 流程接收電子郵件和 Office 365 IP 位址的變更](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span><span class="sxs-lookup"><span data-stu-id="ec777-195">Read about the Microsoft Flow sample and template at [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="ec777-196"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-196"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="ec777-197">Office 365 網路端點常見問題集</span><span class="sxs-lookup"><span data-stu-id="ec777-197">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="ec777-198">Office 365 連線的相關的常見問題集管理員問題：</span><span class="sxs-lookup"><span data-stu-id="ec777-198">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="ec777-199">如何提交問題？</span><span class="sxs-lookup"><span data-stu-id="ec777-199">How do I submit a question?</span></span>

<span data-ttu-id="ec777-p123">按一下以指出本文若已有幫助下方的連結並送出任何其他問題。我們監視意見反應及使用最常見問題集更新的問題。</span><span class="sxs-lookup"><span data-stu-id="ec777-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="ec777-202">如何判斷我租用戶的位置？</span><span class="sxs-lookup"><span data-stu-id="ec777-202">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="ec777-203">最適合使用我們的[資料中心對應](http://aka.ms/datamaps)來判定**租用戶位置**。</span><span class="sxs-lookup"><span data-stu-id="ec777-203">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="ec777-204">Am I 對等適當地向 Microsoft 吗？</span><span class="sxs-lookup"><span data-stu-id="ec777-204">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="ec777-205">在[具有 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。</span><span class="sxs-lookup"><span data-stu-id="ec777-205">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="ec777-p124">超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)的良好並不那麼良好對等手掌核我們的網路。</span><span class="sxs-lookup"><span data-stu-id="ec777-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="ec777-208">不是在 [發佈] 清單上查看 IP 位址的網路要求，我需要提供存取備份吗？</span><span class="sxs-lookup"><span data-stu-id="ec777-208">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="ec777-209"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-209"></span></span>

<span data-ttu-id="ec777-p125">我們只會提供您應直接路由傳送至 Office 365 伺服器的 IP 位址。這不是所有您會看見網路要求的 IP 位址的完整清單。您會看到網路要求，以查看 Microsoft 及協力廠商擁有、 已解除發佈、 IP 位址。這些 IP 位址為動態產生或受管理的這些變更時防止及時通知的方式。如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。</span><span class="sxs-lookup"><span data-stu-id="ec777-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="ec777-215">請參閱 IP 相關聯想的詳細資訊的 Office 365 吗？</span><span class="sxs-lookup"><span data-stu-id="ec777-215">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="ec777-216">檢查是否使用[CIDR 計算器](http://jodies.de/ipcalc)較大發佈範圍中包含的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ec777-216">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="ec777-p126">請參閱協力廠商是否擁有 IP 與[whois 查詢](https://dnsquery.org/)。如果是擁有 Microsoft，則可能內部的協力廠商。</span><span class="sxs-lookup"><span data-stu-id="ec777-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="ec777-p127">檢查憑證、 在瀏覽器中連線至 IP 位址使用*HTTPS://\<IP_ADDRESS\> \* ，檢查要了解哪些網域相關聯的 IP 位址的憑證上所列的網域。如果它是 Microsoft 擁有 IP 位址和不在清單上的 Office 365 IP 位址，它是可能的 IP 位址是與 Microsoft CDN 如*MSOCDN.NET\*或另一個 Microsoft 網域不含已發佈的 IP 資訊相關聯。如果您不要發現憑證上的網域是一個其中我們宣告清單的 IP 位址，請讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="ec777-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="ec777-222">為什麼要查看名稱 nsatc.net 或 akadns.net Microsoft 網域名稱？</span><span class="sxs-lookup"><span data-stu-id="ec777-222">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="ec777-223"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-223"></span></span>

<span data-ttu-id="ec777-p128">Office 365 與其他 Microsoft 服務使用數個協力廠商服務，例如 Akamai 和 MarkMonitor 以提升您的 Office 365 功能。若要保留給予您最佳的經驗，我們可能會變更這些服務未來。在這麼做，我們通常會發佈 CNAME 記錄以指向協力廠商擁有的網域、 record 或 IP 位址。協力廠商網域可能會主控內容，例如 CDN 或時可能會主控的服務，例如地理流量管理服務。當您看到這些協力廠商提供的連線時，它們的格式重新導向或轉介，無法從用戶端初始要求。某些客戶必須以確保這種形式的轉介和重新導向允許將傳遞沒有明確地將新增可能會使用長潛在 Fqdn 第三方服務清單。</span><span class="sxs-lookup"><span data-stu-id="ec777-p128">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="ec777-p129">服務清單，可能隨時變更。一些目前所使用的服務包括：</span><span class="sxs-lookup"><span data-stu-id="ec777-p129">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="ec777-p130">[MarkMonitor](https://www.markmonitor.com/)使用中看見要求包含*\*。 nsatc.net* 。此服務會提供網域名稱保護和監控以防止遭到惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="ec777-p130">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="ec777-p131">[ExactTarget](https://www.marketingcloud.com/)使用中看見要求送至*\*。 exacttarget.com* 。此服務會提供電子郵件連結管理和監控對惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="ec777-p131">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="ec777-p132">當您看到包含其中一個下列 Fqdn 的要求時[Akamai](https://www.akamai.com/)未使用。此服務會提供地理 DNS 和內容傳遞網路服務。</span><span class="sxs-lookup"><span data-stu-id="ec777-p132">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="ec777-238">我必須要有可能的基本連線 for Office 365</span><span class="sxs-lookup"><span data-stu-id="ec777-238">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="ec777-239"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-239"></span></span>

<span data-ttu-id="ec777-p133">Office 365 是一組透過網際網路內建函數的服務、 可靠性與可用性的承諾根據所提供的許多標準網際網路服務。例如，如 DNS、 CRL、 及 Cdn 標準網際網路服務必須使用 Office 365 就如同他們必須使用最現代網際網路服務連至連至。</span><span class="sxs-lookup"><span data-stu-id="ec777-p133">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="ec777-p134">Office 365 套裝軟體細分主要服務區域。這些可以選擇性地啟用連線和所有相依性，一律需要在一般區域。</span><span class="sxs-lookup"><span data-stu-id="ec777-p134">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="ec777-244">**服務區域**</span><span class="sxs-lookup"><span data-stu-id="ec777-244">**Service Area**</span></span>|<span data-ttu-id="ec777-245">**描述**</span><span class="sxs-lookup"><span data-stu-id="ec777-245">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ec777-246">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="ec777-246">**Exchange**</span></span> <br/> |<span data-ttu-id="ec777-247">Exchange Online 與 Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="ec777-247">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="ec777-248">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="ec777-248">**SharePoint**</span></span> <br/> |<span data-ttu-id="ec777-249">SharePoint Online 和商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="ec777-249">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="ec777-250">**Skype**</span><span class="sxs-lookup"><span data-stu-id="ec777-250">**Skype**</span></span> <br/> |<span data-ttu-id="ec777-251">Skype 的業務與的 Microsoft 小組</span><span class="sxs-lookup"><span data-stu-id="ec777-251">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="ec777-252">**一般**</span><span class="sxs-lookup"><span data-stu-id="ec777-252">**Common**</span></span> <br/> |<span data-ttu-id="ec777-253">Office 365 Pro Plus、 Office Online、 Azure AD 和其他一般網路端點</span><span class="sxs-lookup"><span data-stu-id="ec777-253">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="ec777-p135">除了基本的網際網路服務有協力廠商所使用服務的僅限整合功能。雖然這些所需的整合，它們被標示為選用這表示核心功能的服務會繼續運作如果端點不是可存取 Office 365 端點文章中。這是必要的任何網路端點會有 required 屬性設定為 true。這是選用的任何網路端點會有必要的屬性設定為 false 並備忘稿屬性將會詳細說明應可預期如果封鎖連線缺少的功能。</span><span class="sxs-lookup"><span data-stu-id="ec777-p135">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="ec777-258">如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="ec777-258">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="ec777-259">如何封鎖存取 Microsoft 的用戶服務？</span><span class="sxs-lookup"><span data-stu-id="ec777-259">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="ec777-260"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="ec777-260"></span></span>

<span data-ttu-id="ec777-p136">限制存取我們取用者服務應在您自己的風險、 封鎖取用者服務僅可靠方法是以限制存取*login.live.com* FQDN。這個 FQDN 可供廣泛的服務包括非消費者服務，例如 MSDN、 TechNet、 和其他人。限制存取至此 fqdn 可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ec777-p136">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="ec777-264">請記住封鎖存取 Microsoft 取用者服務來說不會阻止您網路上的某個人的能力 exfiltrate 使用 Office 365 租用戶或其他服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="ec777-264">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="ec777-265">相關主題</span><span class="sxs-lookup"><span data-stu-id="ec777-265">Related Topics</span></span>

[<span data-ttu-id="ec777-266">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="ec777-266">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="ec777-267">Microsoft Azure Datacenter IP 範圍</span><span class="sxs-lookup"><span data-stu-id="ec777-267">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="ec777-268">Microsoft 公用 IP 空間</span><span class="sxs-lookup"><span data-stu-id="ec777-268">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="ec777-269">Microsoft Intune 的網路基礎結構需求</span><span class="sxs-lookup"><span data-stu-id="ec777-269">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="ec777-270">Power BI 和 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ec777-270">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
<span data-ttu-id="ec777-271">[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)</span><span class="sxs-lookup"><span data-stu-id="ec777-271">[Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md)</span></span>
  
[<span data-ttu-id="ec777-272">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="ec777-272">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="ec777-273">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="ec777-273">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
