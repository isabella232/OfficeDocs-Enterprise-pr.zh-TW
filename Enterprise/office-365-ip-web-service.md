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
# <a name="office-365-ip-address-and-url-web-service"></a>**Office 365 IP 位址和 URL Web 服務**

為了協助您更能識別及區分 Office 365 網路流量，新的 Web 服務會發佈 Office 365 端點，讓您更容易評估、設定及掌握變更。這個新的 Web 服務會取代目前使用中的 XML 可下載檔案。XML 格式計劃於 2018 年 10 月 2 日淘汰。

身為客戶或網路周邊裝置廠商，您可以根據新的 REST 型 Web 服務，針對 Office 365 IP 位址和 FQDN 項目進行建置。您可以直接在網頁瀏覽器中使用這些 URL 來存取資料。

- 如需最新版本的 Office 365 URL 與 IP 位址範圍，請使用 [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
- 如需在 Office 365 URL 與防火牆和 Proxy 伺服器的 IP 位址範圍頁面上的資料，請使用 [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
- 若要在 Web 服務第一次可用時，取得從 2018 年 7 月底以來的所有最新變更，請使用 [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。

身為客戶，您可以使用這個 Web 服務：

- 更新 PowerShell 指令碼，以取得 Office 365 端點資料以及為您的網路裝置修改任何格式。
- 使用這項資訊來更新部署到用戶端電腦的 PAC 檔案。

身為網路周邊裝置廠商，您可以使用這個 Web 服務：

- 建立及測試裝置軟體，以下載自動設定的清單。
- 檢查目前的版本。
- 取得目前的變更。

如需詳細資訊，請參閱：

- [Office 365 技術社群論壇中的宣告部落格文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638) (英文)
- [Office 365 技術社群論壇中關於使用 Web 服務的問題](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) (英文)

## <a name="common-parameters"></a>**共用參數**

這些參數在所有 Web 服務方法之間共用：

- **format=CSV | JSON** - 查詢字串參數。根據預設，傳回的資料格式是 JSON。包含此選擇性參數，以逗點分隔值 (CSV) 格式傳回資料。
- **ClientRequestId** - 查詢字串參數。您針對用戶端關聯產生的必要 GUID。您應該為呼叫 Web 服務的每部機器產生 GUID。請勿使用以下範例顯示的 GUID，因為它們未來可能會遭到 Web 服務封鎖。GUID 格式是 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_，其中 x 表示十六進位數字。若要產生 GUID，請使用 [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。

## <a name="version-web-method"></a>**版本 Web 方法**

Microsoft 會在每個月底更新 Office 365 IP 位址和 FQDN 項目，有時候會在這個定期期間以外針對作業或支援需求進行更新。每個已發佈執行個體的資料會獲得指派版本號碼。版本 Web 方法可讓您輪詢每個 Office 365 服務執行個體的最新版本。我們建議您每天檢查版本，或者最多每小時檢查。新版本預期會在每個月初發行。有時候因為支援事件、安全性或其他作業需求，在每個月當中也會有新版本。

版本 Web 方法有一個參數：

- **AllVersions=true** - 查詢字串參數。根據預設，傳回的版本是最新版本。包含此選擇性參數，以要求所有已發佈的版本。
- **Format=JSON** | **CSV** | **RSS** – 除了 JSON 和 CSV 格式之外，版本 Web 方法也支援 RSS。您可以搭配 allVersions=true 參數使用這個格式來要求 RSS 摘要，此摘要可以與 Outlook 或其他 RSS 讀取器搭配使用。
- **Instance** - 路由參數。這個選擇性參數會指定要傳回其版本的執行個體。如果省略，則會傳回所有執行個體。有效的執行個體為：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。

版本 Web 方法的結果可能是單一記錄或記錄陣列。每個記錄的元素是：

- instance - Office 365 服務執行個體的簡短名稱。
- latest - 指定執行個體端點的最新版本。
- versions - 指定執行個體所有舊版的清單。這個元素只有在 AllVersions 參數為 true 時才會納入。

您可以使用 Microsoft Flow 取得 IP 位址和 URL 變更的電子郵件通知。請參閱[使用 Microsoft Flow 接收有關 Office 365 IP 位址和 URL 變更的電子郵件](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651) (英文)。

### <a name="examples"></a>**範例：**

範例 1 要求 URI：[https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

這個 URI 會傳回每個 Office 365 服務執行個體的最新版本。範例結果：

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
> 這些 URI 中 ClientRequestID 參數的 GUID 只是範例。若要試用 Web 服務 URI，請產生您自己的 GUID。這些範例中所顯示的 GUID 未來可能會遭到 Web 服務封鎖。

範例 2 要求 URI：[https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

這個 URI 會傳回指定 Office 365 服務執行個體的最新版本。範例結果：

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

範例 3 要求 URI：[https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 會以 CSV 格式顯示輸出。範例結果：

```csv
instance,latest
Worldwide,2018063000
```

範例 4 要求 URI：[https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 會顯示已針對 Office 365 全球服務執行個體發佈的所有舊版。範例結果：

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

範例 5 RSS 摘要 URI：[https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

此 URI 會顯示已發佈版本的 RSS 摘要，其中包含每個版本的變更清單連結。範例結果：

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

## <a name="endpoints-web-method"></a>**端點 Web 方法**

端點 Web 方法會傳回組成 Office 365 服務之 IP 位址範圍和 URL 的所有記錄。雖然應該針對網路裝置組態使用端點 Web 方法的最新資料，因為會提供事先通知作為額外項目，所以資料在發佈之後可以快取最多 30 天。端點 Web 方法的參數為：

- **ServiceAreas** - 查詢字串參數。服務區域的以逗點分隔清單。有效項目為 Common、Exchange、SharePoint、Skype。因為通用服務區域項目是其他所有服務區域的必要條件，Web 服務一律會包含它們。如果您未包含此參數，則會傳回所有服務區域。
- **TenantName** - 查詢字串參數。您的 Office 365 租用戶名稱。Web 服務會採用您提供的名稱並且插入包含租用戶名稱的 URL 當中。如果您未提供租用戶名稱，則 URL 的這些部分會是萬用字元 (\*)。
- **NoIPv6** - 查詢字串參數。將這個參數設為 true 以從輸出排除 IPv6 位址，例如，如果您未在網路中使用 IPv6。
- **Instance** - 路由參數。這個必要參數會指定要傳回端點的執行個體。有效的執行個體為：Worldwide、China、Germany、USGovDoD、USGovGCCHigh。

端點 Web 方法的結果是記錄的陣列，每個記錄代表端點集。每個記錄的元素為：

- id - 端點集的固定識別碼。
- serviceArea - 屬於以下項目的服務區域：Common、Exchange、SharePoint 或 Skype。
- urls - 端點集的 URL。DNS 記錄的 JSON 陣列。如果空白則省略。
- tcpPorts - 端點集的 TCP 連接埠。所有連接埠元素會格式化為以逗點分隔的連接埠清單，或以破折號字元 (-) 分隔的連接埠範圍。該端點中套用至所有 IP 位址和所有 URL 的連接部會針對該分類進行設定。如果空白則省略。
- udpPorts - 此端點集中 IP 位址範圍的 UDP 連接埠。如果空白則省略。
- ips - 與此端點集相關聯的 IP 位址範圍會設定為與列出的 TCP 或 UDP 連接埠相關聯。IP 位址範圍的 JSON 陣列。如果空白則省略。
- 類別 - 端點集的連線類別。有效值為「最佳化」、「允許」和「預設」。若使用端點資料來搜尋 IP 位址或 URL 的類別，您的查詢可能會傳回多個類別。有幾個原因會讓這種情況發生。若發生這種情況，請遵循最高優先順序類別的建議。例如，若端點出現「最佳化」和「允許」，請依「最佳化」的需求來處理。此為必要動作。 
- expressRoute - 此端點集是否透過 ExpressRoute 路由傳送，True 或 False。
- required - 如果需要此端點集才能支援 Office 365 連線，則為 True。如果此端點集為選擇性的，則為 False。
- notes - 針對選擇性的端點，文字說明無法在網路層存取此端點集中的 IP 位址或 URL 時，會遺失的 Office 365 功能。如果空白則省略。

### <a name="examples"></a>範例：

範例 1 要求 URI：[https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

此 URI 會取得所有工作負載之 Office 365 全球執行個體的所有端點。範例結果顯示輸出的摘要：

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

此範例中未包含額外的端點集。

範例 2 要求 URI：[https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

這個範例只會取得 Exchange Online 和相依性之 Office 365 全球執行個體的端點。

範例 2 的輸出類似於範例 1，不同之處在於結果不會包含 SharePoint Online 或商務用 Skype Online 的端點。

## <a name="changes-web-method"></a>變更 Web 方法

變更 Web 方法會傳回已發佈的最新更新。通常是上個月對於 IP 位址範圍和 URL 的變更。要處理的最重要變更是在無法將 IP 位址新增至防火牆存取控制清單，或無法將 URL 新增至 Proxy 伺服器略過清單之後，新增的新 URL 或 IP 位址會導致該網路裝置後的 Office 365 使用者中斷。儘管_新增_作業是作業需求，但是它會在此類中斷發生之前，新增 30 天通知。

變更 Web 方法的參數為：

- **Version** - 必要 URL 路由參數。您目前實作的版本，以及您想要在該版本之後查看的變更。格式為 _YYYYMMDDNN_。

變更 Web 方法的結果是記錄的陣列，每個記錄代表特定版本端點中的變更。每個記錄的元素為：

- id - 變更記錄的固定識別碼。
- endpointSetId - 已變更的端點集記錄識別碼。必要。
- disposition - 可以是變更、新增或移除，並且說明對端點集記錄進行什麼變更。必要。
- version - 在其中引入變更的已發佈端點集版本。版本號碼的格式為 _YYYYMMDDNN_，其中 NN 是當一天中有多個版本需要發佈時，遞增的自然數。
- previous - 子結構，詳細說明端點集上已變更元素的先前值。新增的端點集不會包含這個項目。包含 tcpPorts、udpPorts、ExpressRoute、category、required、notes。
- current - 子結構，詳細說明端點集上變更元素的更新值。包含 tcpPorts、udpPorts、ExpressRoute、category、required、notes。
- add - 子結構，詳細說明要新增至端點集集合的項目。如果沒有新增項目則省略。
  - effectiveDate - 定義新增項目在服務中生效的日期。
  - ips - 要新增至 ips 陣列的項目。
  - urls - 要新增至 urls 陣列的項目。
- remove - 子結構，詳細說明要從端點集移除的項目。如果沒有移除項目則省略。
  - ips - 要從 ips 陣列移除的項目。
  - urls - 要從 urls 陣列移除的項目。

### <a name="examples"></a>**範例：**

範例 1 要求 URI：[https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

這會要求對 Office 365 全球服務執行個體所做的所有先前變更。範例結果：

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

範例 2 要求 URI：[https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

這會要求從 Office 365 全球執行個體指定版本之後的變更。在此案例中，指定版本是最新版本。範例結果：

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

## <a name="example-powershell-script"></a>**範例 PowerShell 指令碼**

以下是 PowerShell 指令碼，您可以執行以查看是否需要針對更新的資料採取動作。此指令碼會檢查 Office 365 全球執行個體端點的版本號碼。有變更時，它會針對 &quot;允許&quot; 和 &quot;最佳化&quot; 分類端點，下載端點和篩選條件。它也會在多個呼叫之間使用唯一的 ClientRequestId，並且儲存在暫存檔案中找到的最新版本。您應該一小時呼叫此指令碼一次，以檢查版本更新。

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

## <a name="example-python-script"></a>**範例 Python 指令碼**

以下是 Python 指令碼 (在 Windows 10 上以 Python 3.6.3 進行測試)，您可以執行以查看是否需要針對更新的資料採取動作。此指令碼會檢查 Office 365 全球執行個體端點的版本號碼。有變更時，它會針對 _允許_ 和 _最佳化_ 分類端點，下載端點和篩選條件。它也會在多個呼叫之間使用唯一的 ClientRequestId，並且儲存在暫存檔案中找到的最新版本。您應該一小時呼叫此指令碼一次，以檢查版本更新。

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

## <a name="web-service-interface-versioning"></a>**Web 服務介面版本設定**

未來可能需要對於這些 Web 服務方法的參數或結果更新。在這些 Web 服務的正式運作版本發行之後，Microsoft 會致力於提供 Web 服務材料更新的事先通知。當 Microsoft 認為需要對使用 Web 服務的用戶端進行更新時，Microsoft 會讓舊版 (上一個版本) Web 服務在新版本發行之後，仍然保持至少十二 (12) 個月可用。在這段期間未升級的客戶可能無法存取 Web 服務及其方法。如果對 Web 服務介面簽章進行下列變更，客戶必須確保 Web 服務的用戶端持續運作且沒有錯誤：

- 將新的選擇性參數新增至現有 Web 方法，該方法不一定要由舊的用戶端提供，且不會影響舊用戶端接收的結果。
- 將其中一個回應 REST 項目中的具名屬性或額外資料行新增至回應 CSV。
- 新增具有新名稱 (不是舊用戶端使用的名稱) 的新 Web 方法。

## <a name="related-topics"></a>相關主題
  
[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) (英文)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)

[Office 365 網路連線原則](office-365-network-connectivity-principles.md)

[Office 365 網路與效能調整](network-planning-and-performance.md)

[對 Office 365 的網路連線](network-connectivity.md)
  
[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)
  
[針對商務用 Skype Online 最佳化您的網路](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43) (英文)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)
  
[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)
