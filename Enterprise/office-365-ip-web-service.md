---
title: Office 365 IP 位址和 URL Web 服務
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: 為了協助您更能識別及區分 Office 365 網路流量，新的 Web 服務會發佈 Office 365 端點，讓您更容易評估、設定及掌握變更。這個新的 Web 服務會取代目前使用中的 XML 可下載檔案。
ms.openlocfilehash: 1765a35e961d6aa3da42c36e5a04333e57ae010b
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697979"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="9b602-104">**Office 365 IP 位址和 URL Web 服務**</span><span class="sxs-lookup"><span data-stu-id="9b602-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="9b602-p102">為了協助您更能識別及區分 Office 365 網路流量，新的 Web 服務會發佈 Office 365 端點，讓您更容易評估、設定及掌握變更。這個新的 Web 服務會取代目前使用中的 XML 可下載檔案。XML 格式計劃於 2018 年 10 月 2 日淘汰。</span><span class="sxs-lookup"><span data-stu-id="9b602-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="9b602-p103">身為客戶或網路周邊裝置廠商，您可以根據新的 REST 型 Web 服務，針對 Office 365 IP 位址和 FQDN 項目進行建置。您可以直接在網頁瀏覽器中使用這些 URL 來存取資料。</span><span class="sxs-lookup"><span data-stu-id="9b602-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="9b602-110">如需最新版本的 Office 365 URL 與 IP 位址範圍，請使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="9b602-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="9b602-111">如需在 Office 365 URL 與防火牆和 Proxy 伺服器的 IP 位址範圍頁面上的資料，請使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="9b602-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="9b602-112">若要在 Web 服務第一次可用時，取得從 2018 年 7 月底以來的所有最新變更，請使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="9b602-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="9b602-113">身為客戶，您可以使用這個 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="9b602-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="9b602-114">更新 PowerShell 指令碼，以取得 Office 365 端點資料以及為您的網路裝置修改任何格式。</span><span class="sxs-lookup"><span data-stu-id="9b602-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="9b602-115">使用這項資訊來更新部署到用戶端電腦的 PAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="9b602-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="9b602-116">身為網路周邊裝置廠商，您可以使用這個 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="9b602-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="9b602-117">建立及測試裝置軟體，以下載自動設定的清單。</span><span class="sxs-lookup"><span data-stu-id="9b602-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="9b602-118">檢查目前的版本。</span><span class="sxs-lookup"><span data-stu-id="9b602-118">Check for the current version.</span></span>
- <span data-ttu-id="9b602-119">取得目前的變更。</span><span class="sxs-lookup"><span data-stu-id="9b602-119">Get the current changes.</span></span>

<span data-ttu-id="9b602-120">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="9b602-120">For additional information, see:</span></span>

- <span data-ttu-id="9b602-121">[Office 365 技術社群論壇中的宣告部落格文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638) (英文)</span><span class="sxs-lookup"><span data-stu-id="9b602-121">[Announcement blog post in the Office 365 Tech Community Forum](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)</span></span>
- <span data-ttu-id="9b602-122">[Office 365 技術社群論壇中關於使用 Web 服務的問題](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) (英文)</span><span class="sxs-lookup"><span data-stu-id="9b602-122">[Office 365 Tech Community Forum for questions about use of the web services](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)</span></span>

## <a name="common-parameters"></a><span data-ttu-id="9b602-123">**共用參數**</span><span class="sxs-lookup"><span data-stu-id="9b602-123">**Common parameters**</span></span>

<span data-ttu-id="9b602-124">這些參數在所有 Web 服務方法之間共用：</span><span class="sxs-lookup"><span data-stu-id="9b602-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="9b602-p104">**format=CSV | JSON** - 查詢字串參數。根據預設，傳回的資料格式是 JSON。包含此選擇性參數，以逗點分隔值 (CSV) 格式傳回資料。</span><span class="sxs-lookup"><span data-stu-id="9b602-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="9b602-p105">**ClientRequestId** - 查詢字串參數。您針對用戶端關聯產生的必要 GUID。您應該為呼叫 Web 服務的每部機器產生 GUID。請勿使用以下範例顯示的 GUID，因為它們未來可能會遭到 Web 服務封鎖。GUID 格式是 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示十六進位數字。若要產生 GUID，請使用 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="9b602-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="9b602-134">**版本 Web 方法**</span><span class="sxs-lookup"><span data-stu-id="9b602-134">**Version web method**</span></span>

<span data-ttu-id="9b602-p106">Microsoft 會在每個月底更新 Office 365 IP 位址和 FQDN 項目，有時候會在這個定期期間以外針對作業或支援需求進行更新。每個已發佈執行個體的資料會獲得指派版本號碼。版本 Web 方法可讓您輪詢每個 Office 365 服務執行個體的最新版本。我們建議您每天檢查版本，或者最多每小時檢查。新版本預期會在每個月初發行。有時候因為支援事件、安全性或其他作業需求，在每個月當中也會有新版本。</span><span class="sxs-lookup"><span data-stu-id="9b602-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="9b602-141">版本 Web 方法有一個參數：</span><span class="sxs-lookup"><span data-stu-id="9b602-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="9b602-p107">**AllVersions=true** - 查詢字串參數。根據預設，傳回的版本是最新版本。包含此選擇性參數，以要求所有已發佈的版本。</span><span class="sxs-lookup"><span data-stu-id="9b602-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="9b602-p108">**Format=JSON** | **CSV** | **RSS** – 除了 JSON 和 CSV 格式之外，版本 Web 方法也支援 RSS。您可以搭配 allVersions=true 參數使用這個格式來要求 RSS 摘要，此摘要可以與 Outlook 或其他 RSS 讀取器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9b602-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="9b602-p109">**Instance** - 路由參數。這個選擇性參數會指定要傳回其版本的執行個體。如果省略，則會傳回所有執行個體。有效的執行個體為：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="9b602-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="9b602-p110">版本 Web 方法的結果可能是單一記錄或記錄陣列。每個記錄的元素是：</span><span class="sxs-lookup"><span data-stu-id="9b602-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="9b602-153">instance - Office 365 服務執行個體的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="9b602-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="9b602-154">latest - 指定執行個體端點的最新版本。</span><span class="sxs-lookup"><span data-stu-id="9b602-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="9b602-p111">versions - 指定執行個體所有舊版的清單。這個元素只有在 AllVersions 參數為 true 時才會納入。</span><span class="sxs-lookup"><span data-stu-id="9b602-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="9b602-p112">您可以使用 Microsoft Flow 取得 IP 位址和 URL 變更的電子郵件通知。請參閱[使用 Microsoft Flow 接收有關 Office 365 IP 位址和 URL 變更的電子郵件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651) (英文)。</span><span class="sxs-lookup"><span data-stu-id="9b602-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="9b602-159">**範例：**</span><span class="sxs-lookup"><span data-stu-id="9b602-159">**Examples:**</span></span>

<span data-ttu-id="9b602-160">範例 1 要求 URI：[https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-160">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p113">這個 URI 會傳回每個 Office 365 服務執行個體的最新版本。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> <span data-ttu-id="9b602-p114">這些 URI 中 ClientRequestID 參數的 GUID 只是範例。若要試用 Web 服務 URI，請產生您自己的 GUID。這些範例中所顯示的 GUID 未來可能會遭到 Web 服務封鎖。</span><span class="sxs-lookup"><span data-stu-id="9b602-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="9b602-166">範例 2 要求 URI：[https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-166">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p115">這個 URI 會傳回指定 Office 365 服務執行個體的最新版本。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="9b602-169">範例 3 要求 URI：[https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-169">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p116">此 URI 會以 CSV 格式顯示輸出。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="9b602-172">範例 4 要求 URI：[https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-172">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p117">此 URI 會顯示已針對 Office 365 全球服務執行個體發佈的所有舊版。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

<span data-ttu-id="9b602-175">範例 5 RSS 摘要 URI：[https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="9b602-175">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="9b602-p118">此 URI 會顯示已發佈版本的 RSS 摘要，其中包含每個版本的變更清單連結。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a><span data-ttu-id="9b602-178">**端點 Web 方法**</span><span class="sxs-lookup"><span data-stu-id="9b602-178">**Endpoints web method**</span></span>

<span data-ttu-id="9b602-p119">端點 Web 方法會傳回組成 Office 365 服務之 IP 位址範圍和 URL 的所有記錄。雖然應該針對網路裝置組態使用端點 Web 方法的最新資料，因為會提供事先通知作為額外項目，所以資料在發佈之後可以快取最多 30 天。端點 Web 方法的參數為：</span><span class="sxs-lookup"><span data-stu-id="9b602-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="9b602-p120">**ServiceAreas** - 查詢字串參數。服務區域的以逗點分隔清單。有效項目為 Common、Exchange、SharePoint、Skype。因為通用服務區域項目是其他所有服務區域的必要條件，Web 服務一律會包含它們。如果您未包含此參數，則會傳回所有服務區域。</span><span class="sxs-lookup"><span data-stu-id="9b602-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="9b602-p121">**TenantName** - 查詢字串參數。您的 Office 365 租用戶名稱。Web 服務會採用您提供的名稱並且插入包含租用戶名稱的 URL 當中。如果您未提供租用戶名稱，則 URL 的這些部分會是萬用字元 (\*)。</span><span class="sxs-lookup"><span data-stu-id="9b602-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="9b602-p122">**NoIPv6** - 查詢字串參數。將這個參數設為 true 以從輸出排除 IPv6 位址，例如，如果您未在網路中使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="9b602-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="9b602-p123">**Instance** - 路由參數。這個必要參數會指定要傳回端點的執行個體。有效的執行個體為：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="9b602-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="9b602-p124">端點 Web 方法的結果是記錄的陣列，每個記錄代表端點集。每個記錄的元素為：</span><span class="sxs-lookup"><span data-stu-id="9b602-p124">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="9b602-198">id - 端點集的固定識別碼。</span><span class="sxs-lookup"><span data-stu-id="9b602-198">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="9b602-199">serviceArea - 屬於以下項目的服務區域：Common、Exchange、SharePoint 或 Skype。</span><span class="sxs-lookup"><span data-stu-id="9b602-199">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="9b602-p125">urls - 端點集的 URL。DNS 記錄的 JSON 陣列。如果空白則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p125">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="9b602-p126">tcpPorts - 端點集的 TCP 連接埠。所有連接埠元素會格式化為以逗點分隔的連接埠清單，或以破折號字元 (-) 分隔的連接埠範圍。該端點中套用至所有 IP 位址和所有 URL 的連接部會針對該分類進行設定。如果空白則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p126">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="9b602-p127">udpPorts - 此端點集中 IP 位址範圍的 UDP 連接埠。如果空白則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p127">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="9b602-p128">ips - 與此端點集相關聯的 IP 位址範圍會設定為與列出的 TCP 或 UDP 連接埠相關聯。IP 位址範圍的 JSON 陣列。如果空白則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p128">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="9b602-p129">類別 - 端點集的連線類別。有效值為「最佳化」、「允許」和「預設」。若使用端點資料來搜尋 IP 位址或 URL 的類別，您的查詢可能會傳回多個類別。有幾個原因會讓這種情況發生。若發生這種情況，請遵循最高優先順序類別的建議。例如，若端點出現「最佳化」和「允許」，請依「最佳化」的需求來處理。此為必要動作。</span><span class="sxs-lookup"><span data-stu-id="9b602-p129">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span> 
- <span data-ttu-id="9b602-219">expressRoute - 此端點集是否透過 ExpressRoute 路由傳送，True 或 False。</span><span class="sxs-lookup"><span data-stu-id="9b602-219">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="9b602-p130">required - 如果需要此端點集才能支援 Office 365 連線，則為 True。如果此端點集為選擇性的，則為 False。</span><span class="sxs-lookup"><span data-stu-id="9b602-p130">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="9b602-p131">notes - 針對選擇性的端點，文字說明無法在網路層存取此端點集中的 IP 位址或 URL 時，會遺失的 Office 365 功能。如果空白則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p131">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="9b602-224">範例：</span><span class="sxs-lookup"><span data-stu-id="9b602-224">Examples:</span></span>

<span data-ttu-id="9b602-225">範例 1 要求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-225">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p132">此 URI 會取得所有工作負載之 Office 365 全球執行個體的所有端點。範例結果顯示輸出的摘要：</span><span class="sxs-lookup"><span data-stu-id="9b602-p132">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
...
```

<span data-ttu-id="9b602-228">此範例中未包含額外的端點集。</span><span class="sxs-lookup"><span data-stu-id="9b602-228">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="9b602-229">範例 2 要求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-229">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-230">這個範例只會取得 Exchange Online 和相依性之 Office 365 全球執行個體的端點。</span><span class="sxs-lookup"><span data-stu-id="9b602-230">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="9b602-231">範例 2 的輸出類似於範例 1，不同之處在於結果不會包含 SharePoint Online 或商務用 Skype Online 的端點。</span><span class="sxs-lookup"><span data-stu-id="9b602-231">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="9b602-232">變更 Web 方法</span><span class="sxs-lookup"><span data-stu-id="9b602-232">Changes web method</span></span>

<span data-ttu-id="9b602-p133">變更 Web 方法會傳回已發佈的最新更新。通常是上個月對於 IP 位址範圍和 URL 的變更。要處理的最重要變更是在無法將 IP 位址新增至防火牆存取控制清單，或無法將 URL 新增至 Proxy 伺服器略過清單之後，新增的新 URL 或 IP 位址會導致該網路裝置後的 Office 365 使用者中斷。儘管_新增_作業是作業需求，但是它會在此類中斷發生之前，新增 30 天通知。</span><span class="sxs-lookup"><span data-stu-id="9b602-p133">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="9b602-237">變更 Web 方法的參數為：</span><span class="sxs-lookup"><span data-stu-id="9b602-237">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="9b602-p134">**Version** - 必要 URL 路由參數。您目前實作的版本，以及您想要在該版本之後查看的變更。格式為 _YYYYMMDDNN_。</span><span class="sxs-lookup"><span data-stu-id="9b602-p134">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="9b602-p135">變更 Web 方法的結果是記錄的陣列，每個記錄代表特定版本端點中的變更。每個記錄的元素為：</span><span class="sxs-lookup"><span data-stu-id="9b602-p135">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="9b602-243">id - 變更記錄的固定識別碼。</span><span class="sxs-lookup"><span data-stu-id="9b602-243">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="9b602-p136">endpointSetId - 已變更的端點集記錄識別碼。必要。</span><span class="sxs-lookup"><span data-stu-id="9b602-p136">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="9b602-p137">disposition - 可以是變更、新增或移除，並且說明對端點集記錄進行什麼變更。必要。</span><span class="sxs-lookup"><span data-stu-id="9b602-p137">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="9b602-p138">version - 在其中引入變更的已發佈端點集版本。版本號碼的格式為 _YYYYMMDDNN_，其中 NN 是當一天中有多個版本需要發佈時，遞增的自然數。</span><span class="sxs-lookup"><span data-stu-id="9b602-p138">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="9b602-p139">previous - 子結構，詳細說明端點集上已變更元素的先前值。新增的端點集不會包含這個項目。包含 tcpPorts、udpPorts、ExpressRoute、category、required、notes。</span><span class="sxs-lookup"><span data-stu-id="9b602-p139">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="9b602-p140">current - 子結構，詳細說明端點集上變更元素的更新值。包含 tcpPorts、udpPorts、ExpressRoute、category、required、notes。</span><span class="sxs-lookup"><span data-stu-id="9b602-p140">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="9b602-p141">add - 子結構，詳細說明要新增至端點集集合的項目。如果沒有新增項目則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p141">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="9b602-257">effectiveDate - 定義新增項目在服務中生效的日期。</span><span class="sxs-lookup"><span data-stu-id="9b602-257">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="9b602-258">ips - 要新增至 ips 陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="9b602-258">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="9b602-259">urls - 要新增至 urls 陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="9b602-259">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="9b602-p142">remove - 子結構，詳細說明要從端點集移除的項目。如果沒有移除項目則省略。</span><span class="sxs-lookup"><span data-stu-id="9b602-p142">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="9b602-262">ips - 要從 ips 陣列移除的項目。</span><span class="sxs-lookup"><span data-stu-id="9b602-262">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="9b602-263">urls - 要從 urls 陣列移除的項目。</span><span class="sxs-lookup"><span data-stu-id="9b602-263">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="9b602-264">**範例：**</span><span class="sxs-lookup"><span data-stu-id="9b602-264">**Examples:**</span></span>

<span data-ttu-id="9b602-265">範例 1 要求 URI：[https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-265">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p143">這會要求對 Office 365 全球服務執行個體所做的所有先前變更。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p143">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
...
```

<span data-ttu-id="9b602-268">範例 2 要求 URI：[https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="9b602-268">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="9b602-p144">這會要求從 Office 365 全球執行個體指定版本之後的變更。在此案例中，指定版本是最新版本。範例結果：</span><span class="sxs-lookup"><span data-stu-id="9b602-p144">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a><span data-ttu-id="9b602-272">**範例 PowerShell 指令碼**</span><span class="sxs-lookup"><span data-stu-id="9b602-272">**Example PowerShell Script**</span></span>

<span data-ttu-id="9b602-p145">以下是 PowerShell 指令碼，您可以執行以查看是否需要針對更新的資料採取動作。此指令碼會檢查 Office 365 全球執行個體端點的版本號碼。有變更時，它會針對 &quot;允許&quot; 和 &quot;最佳化&quot; 分類端點，下載端點和篩選條件。它也會在多個呼叫之間使用唯一的 ClientRequestId，並且儲存在暫存檔案中找到的最新版本。您應該一小時呼叫此指令碼一次，以檢查版本更新。</span><span class="sxs-lookup"><span data-stu-id="9b602-p145">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a><span data-ttu-id="9b602-278">**範例 Python 指令碼**</span><span class="sxs-lookup"><span data-stu-id="9b602-278">**Example Python Script**</span></span>

<span data-ttu-id="9b602-p146">以下是 Python 指令碼 (在 Windows 10 上以 Python 3.6.3 進行測試)，您可以執行以查看是否需要針對更新的資料採取動作。此指令碼會檢查 Office 365 全球執行個體端點的版本號碼。有變更時，它會針對 _允許_ 和 _最佳化_ 分類端點，下載端點和篩選條件。它也會在多個呼叫之間使用唯一的 ClientRequestId，並且儲存在暫存檔案中找到的最新版本。您應該一小時呼叫此指令碼一次，以檢查版本更新。</span><span class="sxs-lookup"><span data-stu-id="9b602-p146">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a><span data-ttu-id="9b602-284">**Web 服務介面版本設定**</span><span class="sxs-lookup"><span data-stu-id="9b602-284">**Web Service interface versioning**</span></span>

<span data-ttu-id="9b602-p147">未來可能需要對於這些 Web 服務方法的參數或結果更新。在這些 Web 服務的正式運作版本發行之後，Microsoft 會致力於提供 Web 服務材料更新的事先通知。當 Microsoft 認為需要對使用 Web 服務的用戶端進行更新時，Microsoft 會讓舊版 (上一個版本) Web 服務在新版本發行之後，仍然保持至少十二 (12) 個月可用。在這段期間未升級的客戶可能無法存取 Web 服務及其方法。如果對 Web 服務介面簽章進行下列變更，客戶必須確保 Web 服務的用戶端持續運作且沒有錯誤：</span><span class="sxs-lookup"><span data-stu-id="9b602-p147">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="9b602-290">將新的選擇性參數新增至現有 Web 方法，該方法不一定要由舊的用戶端提供，且不會影響舊用戶端接收的結果。</span><span class="sxs-lookup"><span data-stu-id="9b602-290">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="9b602-291">將其中一個回應 REST 項目中的具名屬性或額外資料行新增至回應 CSV。</span><span class="sxs-lookup"><span data-stu-id="9b602-291">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="9b602-292">新增具有新名稱 (不是舊用戶端使用的名稱) 的新 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="9b602-292">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="9b602-293">相關主題</span><span class="sxs-lookup"><span data-stu-id="9b602-293">Related Topics</span></span>
  
<span data-ttu-id="9b602-294">[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)</span><span class="sxs-lookup"><span data-stu-id="9b602-294">[Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)</span></span>
  
<span data-ttu-id="9b602-295">[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)</span><span class="sxs-lookup"><span data-stu-id="9b602-295">[Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)</span></span>

[<span data-ttu-id="9b602-296">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="9b602-296">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="9b602-297">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="9b602-297">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="9b602-298">對 Office 365 的網路連線</span><span class="sxs-lookup"><span data-stu-id="9b602-298">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
<span data-ttu-id="9b602-299">[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)</span><span class="sxs-lookup"><span data-stu-id="9b602-299">[Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)</span></span>
  
<span data-ttu-id="9b602-300">[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)</span><span class="sxs-lookup"><span data-stu-id="9b602-300">[Optimizing your network for Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)</span></span>

[<span data-ttu-id="9b602-301">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="9b602-301">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="9b602-302">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="9b602-302">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
