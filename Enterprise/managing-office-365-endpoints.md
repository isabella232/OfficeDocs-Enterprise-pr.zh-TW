---
title: 管理 Office 365 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/21/2019
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
ms.openlocfilehash: 469c1fa91fc2695c4175a4eccea26a0ffc46c52a
ms.sourcegitcommit: bc565081b64d374d43b1bf3bb3d92edaaa24e4c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "30176743"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="62342-105">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="62342-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="62342-p102">大部分企業組織若有多個辦公室位置和連接的 WAN 的需要需要設定 Office 365 網路連線。您可以藉由傳送的所有受信任直接透過防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理最佳化您的網路。這可減少延遲與周邊容量需求。用來識別 Office 365 網路流量是提供給使用者的最佳效能的第一個步驟。如需 Office 365 網路連線的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)</span><span class="sxs-lookup"><span data-stu-id="62342-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="62342-111">Microsoft 建議您存取 Office 365 網路端點和使用[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)進行的變更</span><span class="sxs-lookup"><span data-stu-id="62342-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="62342-p103">不論您管理的方式環 Office 365 網路流量，Office 365 需要網際網路連線能力。[其他不包含在 Office 365 IP 位址及 URL Web 服務的端點](additional-office365-ip-addresses-and-urls.md)上所列的連線需要裝載的其他網路端點</span><span class="sxs-lookup"><span data-stu-id="62342-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="62342-p104">如何使用 Office 365 網路端點將取決於您企業組織的網路架構。本文概述與 Office 365 IP 位址及 Url 可以整合企業網路架構的幾種方法。選擇 [建立信任關係要求的網路最簡單的方法是使用 SDWAN 裝置的支援自動化的 Office 365 設定每一層的辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="62342-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span>

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="62342-117">環 Office 365 網路流量的本機分支輸出的 SDWAN</span><span class="sxs-lookup"><span data-stu-id="62342-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="62342-p105">您可以在每個分公司位置、 提供設定為 Office 365 最佳化類別的端點或最佳化的流量路由傳送並允許類別，直接與 Microsoft 的網路 SDWAN 裝置。包括內部部署資料中心流量、 一般網際網路網站流量和流量到 Office 365 預設類別端點其他網路流量傳送到另一個位置有更明顯的周邊網路的位置。</span><span class="sxs-lookup"><span data-stu-id="62342-p105">At each branch office location, you can provide an SDWAN device that is configured to route traffic for Office 365 Optimize category of endpoints, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, general Internet web sites traffic, and traffic to Office 365 Default category endpoints is sent to another location where you have a more substantial network perimeter.</span></span>

<span data-ttu-id="62342-p106">Microsoft SDWAN 提供者以啟用自動的設定運作。如需詳細資訊，請參閱[Office 365 網路協力廠商程式](office-365-networking-partner-program.md)。</span><span class="sxs-lookup"><span data-stu-id="62342-p106">Microsoft is working with SDWAN providers to enable automated configuration. For more information, see [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span>

<span data-ttu-id="62342-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-122"></span></span>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="62342-123">環 Office 365 流量的直接路由使用 PAC csv 檔案</span><span class="sxs-lookup"><span data-stu-id="62342-123">Use a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="62342-p107">用於管理 Office 365 與相關聯，但沒有 IP 位址的網路要求 PAC 或 WPAD 檔案。透過 proxy 或周邊裝置傳送的一般網路要求會增加延遲。雖然 SSL 會自動換行及檢查建立的最大的延遲，其他服務例如 proxy 驗證和信譽查閱會導致不佳的效能與不良的使用者經驗。此外，這些周邊網路裝置需要足夠的容量來處理所有網路連線要求。我們建議略過您 proxy 或檢查裝置的直接的 Office 365 網路要求。</span><span class="sxs-lookup"><span data-stu-id="62342-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address. Typical network requests that are sent through a proxy or perimeter device increase latency. While SSL Break and Inspect creates the largest latency, other services such as proxy authentication and reputation lookup can cause poor performance and a bad user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection devices for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="62342-p108">[PowerShell 圖庫 Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)會讀取來自 Office 365 IP 位址及 URL Web 服務的最新的網路端點，並建立範例 PAC 檔案的 PowerShell 指令碼。您可以修改指令碼，讓它與您現有的 PAC 檔案管理整合。</span><span class="sxs-lookup"><span data-stu-id="62342-p108">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL Web service and creates a sample PAC file. You can modify the script so that it integrates with your existing PAC file management.</span></span>

![透過防火牆及 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

<span data-ttu-id="62342-132">**圖 1-簡單的企業周邊網路**</span><span class="sxs-lookup"><span data-stu-id="62342-132">**Figure 1 - Simple enterprise network perimeter**</span></span>

<span data-ttu-id="62342-p109">PAC 檔案部署至網頁瀏覽器在圖 1 點 1。當使用環 Office 365 網路流量的直接輸出 PAC 檔案，您也需要允許網路周邊防火牆後方這些 Url 的 IP 位址的連線。做法是擷取 PAC 檔案中所指定同一個 Office 365 端點類別的 IP 位址和這些地址為基礎建立防火牆 Acl。防火牆是圖 1 3 點。</span><span class="sxs-lookup"><span data-stu-id="62342-p109">The PAC file is deployed to web browsers at point 1 in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is point 3 in Figure 1.</span></span>

<span data-ttu-id="62342-p110">分開如果您選擇不要僅直接最佳化類別端點傳送至 proxy 伺服器的類別端點必須列在 [proxy 伺服器略過進一步的處理任何必要允許的路由。例如，SSL 符號和檢查及 Proxy 驗證與不相容的最佳化和允許類別端點。圖 1 點 2 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="62342-p110">Separately if you choose to only do direct routing for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is point 2 in Figure 1.</span></span>

<span data-ttu-id="62342-p111">一般設定為允許不處理來自 Office 365 拜訪人次 proxy 伺服器的網路流量的目的地 IP 位址的 proxy 伺服器的所有輸出流量。SSL 會自動換行及檢查的問題的相關資訊，請參閱[使用協力廠商網路裝置或 Office 365 流量的解決方案](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)。</span><span class="sxs-lookup"><span data-stu-id="62342-p111">The common configuration is to permit without processing all outbound traffic from the proxy server for the destination IP addresses for Office 365 network traffic that hits the proxy server. For information about issues with SSL Break and Inspect, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="62342-142">有兩種類型的 PAC Get PacFile 指令碼會產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="62342-142">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="62342-143">**類型**</span><span class="sxs-lookup"><span data-stu-id="62342-143">**Type**</span></span>|<span data-ttu-id="62342-144">**說明**</span><span class="sxs-lookup"><span data-stu-id="62342-144">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62342-145">**1**</span><span class="sxs-lookup"><span data-stu-id="62342-145">**1**</span></span> <br/> |<span data-ttu-id="62342-146">將最佳化端點流量直接與其他人的每個項目傳送至 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="62342-146">Send Optimize endpoint traffic direct and everything else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="62342-147">**2**</span><span class="sxs-lookup"><span data-stu-id="62342-147">**2**</span></span> <br/> |<span data-ttu-id="62342-p112">Proxy 伺服器來傳送直接最佳化] 和 [允許端點流量和其他人的每個項目。此類型也可用來傳送所有支援 ExpressRoute ExpressRoute 網路區段到的 Office 365 流量和其他人的 proxy 伺服器的每個項目。</span><span class="sxs-lookup"><span data-stu-id="62342-p112">Send Optimize and Allow endpoint traffic direct and everything else to the proxy server. This type can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and everything else to the proxy server.</span></span> <br/> |

<span data-ttu-id="62342-150">以下是呼叫 PowerShell 指令碼的簡單範例：</span><span class="sxs-lookup"><span data-stu-id="62342-150">Here's a simple example of calling the PowerShell script:</span></span>

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="62342-151">有一些您可以傳遞給指令碼的參數：</span><span class="sxs-lookup"><span data-stu-id="62342-151">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="62342-152">**參數**</span><span class="sxs-lookup"><span data-stu-id="62342-152">**Parameter**</span></span>|<span data-ttu-id="62342-153">**描述**</span><span class="sxs-lookup"><span data-stu-id="62342-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62342-154">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="62342-154">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="62342-155">這是必要的和會傳遞至代表進行通話的用戶端電腦的 web 服務的 GUID。</span><span class="sxs-lookup"><span data-stu-id="62342-155">This is required and is a GUID passed to the web service that represents the client machine making the call.</span></span> <br/> |
|<span data-ttu-id="62342-156">**Instance**</span><span class="sxs-lookup"><span data-stu-id="62342-156">**Instance**</span></span> <br/> |<span data-ttu-id="62342-p113">全球網站的預設是 Office 365 服務執行個體。也傳遞給 web 服務。</span><span class="sxs-lookup"><span data-stu-id="62342-p113">The Office 365 service instance which defaults to Worldwide. Also passed to the web service.</span></span> <br/> |
|<span data-ttu-id="62342-159">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="62342-159">**TenantName**</span></span> <br/> |<span data-ttu-id="62342-p114">您的 Office 365 租用戶名稱。傳遞至 web 服務並做為在某些 Office 365 Url 可取代的參數。</span><span class="sxs-lookup"><span data-stu-id="62342-p114">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs.</span></span> <br/> |
|<span data-ttu-id="62342-162">**類型**</span><span class="sxs-lookup"><span data-stu-id="62342-162">**Type**</span></span> <br/> |<span data-ttu-id="62342-163">您想要產生的 proxy PAC 檔案類型。</span><span class="sxs-lookup"><span data-stu-id="62342-163">The type of the proxy PAC file that you want to generate.</span></span> <br/> |

<span data-ttu-id="62342-164">以下是另一個範例呼叫 PowerShell 指令碼與其他參數。</span><span class="sxs-lookup"><span data-stu-id="62342-164">Here's another example of calling the PowerShell script with additional parameters.</span></span>

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="62342-165">Proxy 伺服器旁路處理 Office 365 網路流量</span><span class="sxs-lookup"><span data-stu-id="62342-165">Proxy server bypass processing of Office 365 network traffic</span></span>

<span data-ttu-id="62342-p115">其中 PAC 檔案不會用於輸出流量導向，您仍想要設定 proxy 伺服器就能節省您周邊網路上的處理。某些 proxy 伺服器廠商已啟用自動的的設定在[Office 365 網路協力廠商程式](office-365-networking-partner-program.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="62342-p115">Where PAC files are not used for direct outbound traffic, you still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span>

<span data-ttu-id="62342-p116">如果您執行此動作手動您必須取得 [最佳化並允許來自 Office 365 IP 位址及 URL Web 服務的端點分類資料並設定 proxy 伺服器略過這些處理。請務必避免 SSL 會自動換行及檢查和 Proxy 驗證的最佳化並允許類別端點。</span><span class="sxs-lookup"><span data-stu-id="62342-p116">If you are doing this manually you will need to get the Optimize and Allow endpoint category data from the Office 365 IP Address and URL Web Service and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span>
  
<span data-ttu-id="62342-170"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-170"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="62342-171">變更管理 Office 365 IP 位址及 Url</span><span class="sxs-lookup"><span data-stu-id="62342-171">Change management for Office 365 IP addresses and URLs</span></span>

<span data-ttu-id="62342-p117">選取適當設定您周邊網路，除了是重要您採用 Office 365 端點變更管理程序。定期變更這些端點和如果您不是管理所做的變更，您可以結束與封鎖的使用者或與效能低落之後新的 IP 位址] 或 [URL 加入。</span><span class="sxs-lookup"><span data-stu-id="62342-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes, you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span>

<span data-ttu-id="62342-p118">每個月最後一天附近通常被發佈 Url 和 Office 365 IP 位址的變更。有時變更將會發佈該排程因為作業、 支援、 或安全性需求以外的地方。</span><span class="sxs-lookup"><span data-stu-id="62342-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="62342-p119">發佈變更需要將 act 因為 IP 位址] 或 [URL 已新增、 時應預期得到我們發佈變更直到該端點上的 Office 365 服務的時間的 30 天的通知。雖然我們瞄準此通知期間，其有時可能無法可能因為操作、 支援、 或安全性需求。移除的 IP 位址或 Url 或更少的重大變更，不包含預先通知不需要維護連線，例如立即動作的變更。不論提供何種通知，則我們會列出每項變更的預期的服務 active 日期。</span><span class="sxs-lookup"><span data-stu-id="62342-p119">When a change is published that requires you to act because an IP address or URL was added, you should expect to receive 30 days notice from the time we publish the change until there is an Office 365 service on that endpoint. Although we aim for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we list the expected service active date for each change.</span></span>

### <a name="change-notification-using-the-web-service"></a><span data-ttu-id="62342-180">使用 Web 服務的變更通知</span><span class="sxs-lookup"><span data-stu-id="62342-180">Change notification using the Web Service</span></span>

<span data-ttu-id="62342-p120">您可以使用 Office 365 IP 位址及 URL Web 服務來取得變更通知。我們建議您先呼叫 **/version** web 方法一次一小時檢查您用來連線至 Office 365 之端點的版本。如果這個版本變更相較於您有使用中的版本，然後您應該從 **/endpoints** web 方法取得最新的端點資料並 （選擇性） 從 **/changes** web 方法取得差異。您不需要呼叫 **/endpoints**或 **/changes** web 方法如果尚未存在您所找到之版本的任何變更。</span><span class="sxs-lookup"><span data-stu-id="62342-p120">You can use the Office 365 IP Address and URL Web Service to get change notification. We recommend you call the **/version** web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the **/endpoints** web method and optionally get the differences from the **/changes** web method. It is not necessary to call the **/endpoints** or **/changes** web methods if there has not been any change to the version you found.</span></span>

<span data-ttu-id="62342-185">如需詳細資訊，請參閱[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="62342-185">For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="62342-186">使用 RSS 摘要的變更通知</span><span class="sxs-lookup"><span data-stu-id="62342-186">Change notification using RSS feeds</span></span>

<span data-ttu-id="62342-p121">Office 365 IP 位址及 URL Web 服務會提供您可以在 Outlook 中訂閱 RSS 摘要。有在每個 IP 位址的 Office 365 服務執行個體特有頁面上的 RSS Url 及 Url 的連結。如需詳細資訊，請參閱[Office 365 IP 位址及 URL Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="62342-p121">The Office 365 IP Address and URL Web Service provides an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance-specific pages for the IP addresses and URLs. For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="62342-190">變更通知及核准檢閱使用 Microsoft 流程</span><span class="sxs-lookup"><span data-stu-id="62342-190">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="62342-p122">我們先了解您仍可能需要手動處理跳到每個月的網路端點變更。您可以使用 Microsoft 流程建立流程通知您的電子郵件及選擇性地變更核准程序會時執行 Office 365 網路端點已變更。檢閱完成之後，您可以自動電子郵件給防火牆及 proxy 伺服器管理小組變更的流程。</span><span class="sxs-lookup"><span data-stu-id="62342-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span>

<span data-ttu-id="62342-194">如需 Microsoft 流程範例和範本的資訊，請參閱[使用 Microsoft Flow 接收電子郵件和 Office 365 IP 位址的變更](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span><span class="sxs-lookup"><span data-stu-id="62342-194">For information about a Microsoft Flow sample and template, see [Use Microsoft Flow to receive an email for changes to Office 365 IP addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="62342-195"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-195"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="62342-196">Office 365 網路端點常見問題集</span><span class="sxs-lookup"><span data-stu-id="62342-196">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="62342-197">Office 365 連線的相關的常見問題集管理員問題：</span><span class="sxs-lookup"><span data-stu-id="62342-197">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="62342-198">如何提交問題？</span><span class="sxs-lookup"><span data-stu-id="62342-198">How do I submit a question?</span></span>

<span data-ttu-id="62342-p123">按一下以指出本文若已有幫助下方的連結並送出任何其他問題。我們監視意見反應及使用最常見問題集更新的問題。</span><span class="sxs-lookup"><span data-stu-id="62342-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="62342-201">如何判斷我租用戶的位置？</span><span class="sxs-lookup"><span data-stu-id="62342-201">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="62342-202">最適合使用我們的[資料中心對應](http://aka.ms/datamaps)來判定**租用戶位置**。</span><span class="sxs-lookup"><span data-stu-id="62342-202">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="62342-203">Am I 對等適當地向 Microsoft 吗？</span><span class="sxs-lookup"><span data-stu-id="62342-203">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="62342-204">在[具有 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。</span><span class="sxs-lookup"><span data-stu-id="62342-204">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="62342-p124">超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)的良好並不那麼良好對等手掌核我們的網路。</span><span class="sxs-lookup"><span data-stu-id="62342-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span>
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="62342-207">不是在 [發佈] 清單上查看 IP 位址的網路要求，我需要提供存取備份吗？</span><span class="sxs-lookup"><span data-stu-id="62342-207">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="62342-208"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-208"></span></span>

<span data-ttu-id="62342-p125">我們只會提供您應直接路由傳送至 Office 365 伺服器的 IP 位址。這不是所有您會看見網路要求的 IP 位址的完整清單。您會看到網路要求，以查看 Microsoft 及協力廠商擁有、 已解除發佈、 IP 位址。這些 IP 位址為動態產生或受管理的這些變更時防止及時通知的方式。如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。</span><span class="sxs-lookup"><span data-stu-id="62342-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="62342-214">請參閱 IP 相關聯想的詳細資訊的 Office 365 吗？</span><span class="sxs-lookup"><span data-stu-id="62342-214">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="62342-215">檢查是否使用[CIDR 計算器](http://jodies.de/ipcalc)較大發佈範圍中包含的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="62342-215">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="62342-p126">請參閱協力廠商是否擁有 IP 與[whois 查詢](https://dnsquery.org/)。如果是擁有 Microsoft，則可能內部的協力廠商。</span><span class="sxs-lookup"><span data-stu-id="62342-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="62342-p127">檢查憑證、 在瀏覽器中連線至 IP 位址使用*HTTPS://\<IP_ADDRESS\> \* ，檢查要了解哪些網域相關聯的 IP 位址的憑證上所列的網域。如果它是 Microsoft 擁有 IP 位址和不在清單上的 Office 365 IP 位址，它是可能的 IP 位址是與 Microsoft CDN 如*MSOCDN.NET\*或另一個 Microsoft 網域不含已發佈的 IP 資訊相關聯。如果您不要發現憑證上的網域是一個其中我們宣告清單的 IP 位址，請讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="62342-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

<span data-ttu-id="62342-221"><a name="bkmk_cname"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-221"></span></span>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a><span data-ttu-id="62342-p128">某些 Office 365 Url 指向 CNAME 記錄，而不是在 DNS A 記錄。我必須執行動作的 CNAME 記錄項目？</span><span class="sxs-lookup"><span data-stu-id="62342-p128">Some Office 365 URLs point to CNAME records instead of A records in the DNS. What do I have to do with the CNAME records?</span></span>

<span data-ttu-id="62342-p129">用戶端電腦都需要一個 DNS A 或 AAAA 記錄，其中包含一或多個 IP Address(s) 連線到雲端服務。Office 365 中包含一些 Url 顯示 CNAME 記錄，而不是 A 或 AAAA 記錄。中介這些 CNAME 記錄且可能會有數個鏈結中。他們一律最後會將 IP 位址來解析 A 或 AAAA 記錄。例如，請考慮以下一系列的 DNS 記錄的最終解析為 IP 位址_IP_1_：</span><span class="sxs-lookup"><span data-stu-id="62342-p129">Client computers need a DNS A or AAAA record that includes one or more IP Address(s) to connect to a cloud service. Some URLs included in Office 365 show CNAME records instead of A or AAAA records. These CNAME records are intermediary and there may be several in a chain. They will always eventually resolve to an A or AAAA record for an IP Address. For example, consider the following series of DNS records, which ultimately resolves to the IP address _IP_1_:</span></span>

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

<span data-ttu-id="62342-p130">這些 CNAME 重新導向是一般的 DNS 和部分是透明的用戶端電腦和透明 proxy 伺服器。使用負載平衡、 內容傳遞網路、 高可用性和服務附隨減輕。Microsoft 不會發佈的中介 CNAME 記錄、 他們可能隨時變更任何時候以及您應該不需要設定其所允許的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="62342-p130">These CNAME redirects are a normal part of the DNS and are transparent to the client computer and transparent to proxy servers. They are used for load balancing, content delivery networks, high availability, and service incident mitigation. Microsoft does not publish the intermediary CNAME records, they are subject to change at any time, and you should not need to configure them as allowed in your proxy server.</span></span>

<span data-ttu-id="62342-p131">Proxy 伺服器來驗證初始 URL 這在上述範例中是 serviceA.office.com 與此 URL 會是包含在 Office 365 發佈。Proxy 伺服器會要求 DNS 解析的 IP 位址的 URL，也會收到備份 IP_1。它未驗證的中介 CNAME 重新導向記錄。</span><span class="sxs-lookup"><span data-stu-id="62342-p131">A proxy server validates the initial URL which in the above example is serviceA.office.com and this URL would be included in Office 365 publishing. The proxy server requests DNS resolution of that URL to an IP Address and will receive back IP_1. It does not validate the intermediary CNAME redirection records.</span></span>

<span data-ttu-id="62342-p132">硬式編碼設定或間接的 Office 365 Fqdn 為基礎的家不建議使用，不支援 microsoft 與已知導致客戶的連線問題。封鎖 CNAME 重新導向或，否則不正確的 DNS 解決方案解決 Office 365 的 DNS 項目，即可啟用 DNS 遞迴與解決透過 DNS 設定格式化的條件轉寄 （範圍內直接使用 Office 365 Fqdn）。許多協力廠商周邊網路產品原本就整合建議的 Office 365 端點家中他們使用[Office 365 IP 位址及 URL Web 服務](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service)的設定。</span><span class="sxs-lookup"><span data-stu-id="62342-p132">Hard-coded configurations or whitelisting based on indirect Office 365 FQDNs is not recommended, not supported by Microsoft, and is known to cause customer connectivity issues. DNS solutions that block on CNAME redirection, or that otherwise incorrectly resolve Office 365 DNS entries, can be solved via DNS conditional forwarding (scoped to directly used Office 365 FQDNs) with DNS recursion enabled. Many third party network perimeter products natively integrate recommended Office 365 endpoint whitelisting in their configuration using the [Office 365 IP Address and URL Web service](https://docs.microsoft.com/en-us/office365/enterprise/office-365-ip-web-service).</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="62342-238">為什麼要查看名稱 nsatc.net 或 akadns.net Microsoft 網域名稱？</span><span class="sxs-lookup"><span data-stu-id="62342-238">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="62342-239"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-239"></span></span>

<span data-ttu-id="62342-p133">Office 365 與其他 Microsoft 服務使用數個協力廠商服務，例如 Akamai 和 MarkMonitor 以提升您的 Office 365 功能。若要保留給予您最佳的經驗，我們可能會變更這些服務未來。協力廠商網域可能會主控內容，例如 CDN 或時可能會主控的服務，例如地理流量管理服務。一些目前所使用的服務包括：</span><span class="sxs-lookup"><span data-stu-id="62342-p133">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="62342-p134">[MarkMonitor](https://www.markmonitor.com/)使用中看見要求包含*\*。 nsatc.net* 。此服務會提供網域名稱保護和監控以防止遭到惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="62342-p134">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="62342-p135">[ExactTarget](https://www.marketingcloud.com/)使用中看見要求送至*\*。 exacttarget.com* 。此服務會提供電子郵件連結管理和監控對惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="62342-p135">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="62342-p136">當您看到包含其中一個下列 Fqdn 的要求時[Akamai](https://www.akamai.com/)未使用。此服務會提供地理 DNS 和內容傳遞網路服務。</span><span class="sxs-lookup"><span data-stu-id="62342-p136">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="62342-250">我必須要有可能的基本連線 for Office 365</span><span class="sxs-lookup"><span data-stu-id="62342-250">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="62342-251"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-251"></span></span>

<span data-ttu-id="62342-p137">Office 365 是一組透過網際網路內建函數的服務、 可靠性與可用性的承諾根據所提供的許多標準網際網路服務。例如，如 DNS、 CRL、 及 Cdn 標準網際網路服務必須使用 Office 365 就如同他們必須使用最現代網際網路服務連至連至。</span><span class="sxs-lookup"><span data-stu-id="62342-p137">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="62342-p138">Office 365 套裝軟體細分主要服務區域。這些可以選擇性地啟用連線和所有相依性，一律需要在一般區域。</span><span class="sxs-lookup"><span data-stu-id="62342-p138">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="62342-256">**服務區域**</span><span class="sxs-lookup"><span data-stu-id="62342-256">**Service Area**</span></span>|<span data-ttu-id="62342-257">**描述**</span><span class="sxs-lookup"><span data-stu-id="62342-257">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="62342-258">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="62342-258">**Exchange**</span></span> <br/> |<span data-ttu-id="62342-259">Exchange Online 與 Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="62342-259">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="62342-260">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="62342-260">**SharePoint**</span></span> <br/> |<span data-ttu-id="62342-261">SharePoint Online 和商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="62342-261">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="62342-262">**商務用 Skype Online 及 Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="62342-262">**Skype for Business Online and Microsoft Teams**</span></span> <br/> |<span data-ttu-id="62342-263">Skype 的業務與的 Microsoft 小組</span><span class="sxs-lookup"><span data-stu-id="62342-263">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="62342-264">**一般**</span><span class="sxs-lookup"><span data-stu-id="62342-264">**Common**</span></span> <br/> |<span data-ttu-id="62342-265">Office 365 Pro Plus、 Office Online、 Azure AD 和其他一般網路端點</span><span class="sxs-lookup"><span data-stu-id="62342-265">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="62342-p139">除了基本的網際網路服務有協力廠商所使用服務的僅限整合功能。雖然這些所需的整合，它們被標示為選用這表示核心功能的服務會繼續運作如果端點不是可存取 Office 365 端點文章中。這是必要的任何網路端點會有 required 屬性設定為 true。這是選用的任何網路端點會有必要的屬性設定為 false 並備忘稿屬性將會詳細說明應可預期如果封鎖連線缺少的功能。</span><span class="sxs-lookup"><span data-stu-id="62342-p139">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="62342-270">如果您嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="62342-270">If you're trying to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="62342-271">如何封鎖存取 Microsoft 的用戶服務？</span><span class="sxs-lookup"><span data-stu-id="62342-271">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="62342-272"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="62342-272"></span></span>

<span data-ttu-id="62342-p140">限制存取我們取用者服務應在您自己的風險、 封鎖取用者服務僅可靠方法是以限制存取*login.live.com* FQDN。這個 FQDN 可供廣泛的服務包括非消費者服務，例如 MSDN、 TechNet、 和其他人。至此 FQDN 也由 Microsoft 支援安全檔案 Exchange 計劃並視需要傳輸來協助疑難排解 Microsoft 產品的檔案。 限制存取至此 fqdn 可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62342-p140">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. This FQDN is also used by Microsoft Support's Secure File Exchange program and is necessary to transfer files to facilitate troubleshooting for Microsoft products.  Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="62342-277">請記住封鎖存取 Microsoft 取用者服務來說不會阻止您網路上的某個人的能力 exfiltrate 使用 Office 365 租用戶或其他服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="62342-277">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="62342-278">相關主題</span><span class="sxs-lookup"><span data-stu-id="62342-278">Related Topics</span></span>

[<span data-ttu-id="62342-279">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="62342-279">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="62342-280">Microsoft Azure Datacenter IP 範圍</span><span class="sxs-lookup"><span data-stu-id="62342-280">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="62342-281">Microsoft 公用 IP 空間</span><span class="sxs-lookup"><span data-stu-id="62342-281">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="62342-282">Microsoft Intune 的網路基礎結構需求</span><span class="sxs-lookup"><span data-stu-id="62342-282">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="62342-283">ExpressRoute 和 Power BI</span><span class="sxs-lookup"><span data-stu-id="62342-283">ExpressRoute and Power BI</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="62342-284">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="62342-284">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="62342-285">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="62342-285">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="62342-286">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="62342-286">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
