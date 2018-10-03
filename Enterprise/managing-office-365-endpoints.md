---
title: 管理 Office 365 端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
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
description: 某些網路的設計被用來限制存取網際網路，以確保這些可以存取 Office 365、 網路和 proxy 的系統管理員需要管理的 Fqdn，Url、 清單及 IP 位址的網路上的電腦組成的 Office 365 端點清單。這些需要在要新增至 proxy 或防火牆規則和 PAC 以確保網路要求的檔案都能夠連絡 Office 365。
ms.openlocfilehash: a1a658ff04bc7306cb953477798d3e32d894d695
ms.sourcegitcommit: 854653f927c9515024a1c9e0a86fd5f2fadb92f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "25359495"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="728f3-104">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="728f3-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="728f3-105">Office 365 網路連線</span><span class="sxs-lookup"><span data-stu-id="728f3-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="728f3-p102">連線至 Office 365 包含高數量，受信任的網路要求他們正在進行透過接近使用者低延遲輸出時最適合執行。某些 Office 365 的連線可以獲益最佳化連線。</span><span class="sxs-lookup"><span data-stu-id="728f3-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="728f3-108">確定防火牆允許清單允許連線到 Office 365 端點。</span><span class="sxs-lookup"><span data-stu-id="728f3-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="728f3-109">若要允許透過網際網路連線到萬用字元及解除發佈目的地的電話使用 proxy 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="728f3-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="728f3-110">維護最佳的周邊網路組態。</span><span class="sxs-lookup"><span data-stu-id="728f3-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="728f3-111">[確定您要取得最佳的連線](https://aka.ms/o365perfprinciples)。</span><span class="sxs-lookup"><span data-stu-id="728f3-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="728f3-112">請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="728f3-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![透過防火牆及 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="728f3-114">更新的輸出防火牆允許清單</span><span class="sxs-lookup"><span data-stu-id="728f3-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="728f3-p103">您可以藉由傳送的所有受信任直接透過防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理最佳化您的網路。這可減少從延遲的效能低落並減少周邊容量需求。選擇 [建立信任關係要求的網路最簡單的方法是使用我們[預先建置的 PAC 檔案](managing-office-365-endpoints.md#pacfiles)。</span><span class="sxs-lookup"><span data-stu-id="728f3-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our [pre-built PAC files](managing-office-365-endpoints.md#pacfiles).</span></span> 
  
<span data-ttu-id="728f3-p104">如果您防火牆封鎖輸出流量會想要確保所有 IP 和 Fqdn 列為此[XML 檔案](https://go.microsoft.com/fwlink/?LinkId=533185)中**所需**的 [允許] 清單上。辨識所有服務都需要使用一些 3rd 廠商服務。我們不提供的憑證提供者、 內容傳遞網路、 DNS 提供者，例如這些 3rd 廠商服務的 IP 位址等等。完整 Office 365 功能，您必須能夠抵達所有要求的 Office 365 不論多少資訊我們發佈目的地的目的地。</span><span class="sxs-lookup"><span data-stu-id="728f3-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="728f3-122">許多目的地沒有發佈 IP 位址或列為 「 無特定的完整的網域名稱萬用字元網域，請使用這項功能您必須能夠解析這些網路要求，以目前的 IP 位址要求以及傳送透過網際網路的網路要求。</span><span class="sxs-lookup"><span data-stu-id="728f3-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="728f3-p105">使用防火牆會剖析代替您撥打電話之 XML 檔案，更新規則會自動根據服務或功能想要路由傳送直接透過防火牆自動化您的程序。您也可以使用[Azure 範圍](https://azurerange.azurewebsites.net/)工具已由社群建立且會為您的 XML 剖析 Cisco XE 路由或 ACL 清單組態、 純文字或 CSV 匯出選項。</span><span class="sxs-lookup"><span data-stu-id="728f3-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="728f3-125">讓您可以變更訂閱透過[RSS 根據變更記錄](https://go.microsoft.com/fwlink/p/?linkid=236301)我們使用我們[參考 （英文） 網站](urls-and-ip-address-ranges.md)上的網路目的地的較長的說明。</span><span class="sxs-lookup"><span data-stu-id="728f3-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="728f3-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="728f3-127">設定 PAC 檔輸出路徑</span><span class="sxs-lookup"><span data-stu-id="728f3-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="728f3-p106">用於管理 Office 365 與相關聯，但沒有提供 IP 位址的網路要求 PAC 或 WPAD 檔案。透過 proxy 或周邊裝置傳送的一般網路要求可能會形成額外的延遲。雖然 proxy 驗證會帶來最大稅，其他服務，例如信譽查閱和嘗試檢查封包可能會造成不良的使用者經驗。此外，這些周邊網路裝置需要足夠的容量來處理所有網路要求。我們建議略過您直接的 Office 365 網路要求的 proxy 或檢查基礎結構。</span><span class="sxs-lookup"><span data-stu-id="728f3-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="728f3-p107">使用下列其中一個我們 PAC 檔案的起始位置為決定何種網路流量會傳送至 proxy 和其就會傳送給防火牆。如果您是 PAC 或 WPAD 檔案，從一個適用的 Office 365 顧問閱讀此文章[部署 PAC 檔案](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/)的相關的新功能。想要檢閱這些開始進行並編輯以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="728f3-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="728f3-136">**更新 7/10/2018 PAC 檔案**。</span><span class="sxs-lookup"><span data-stu-id="728f3-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="728f3-137">#1-PAC 檔案： 隔開需要網際網路從已知的 Office 365 FQDN 的 Fqdn。</span><span class="sxs-lookup"><span data-stu-id="728f3-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="728f3-p108">第一個範例是透過網際網路僅管理端點我們建議方法的示範。略過 Office 365 目的地 IP 位址其中發佈而將剩餘的網路要求傳送至 proxy 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="728f3-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="728f3-140">程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="728f3-140">Code snippet:</span></span>

```javascript
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))

    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))

    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="728f3-141">#2-PAC 檔案： 透過網際網路和 ExpressRoute 連線到 Office 365</span><span class="sxs-lookup"><span data-stu-id="728f3-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="728f3-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-142"></span></span>

<span data-ttu-id="728f3-p109">第二個範例是方法的我們建議有 ExpressRoute 和網際網路電路時管理連線的示範。傳送 ExpressRoute 通告 ExpressRoute 電路的目的地及網際網路只通告 proxy 的目的地。</span><span class="sxs-lookup"><span data-stu-id="728f3-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="728f3-145">程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="728f3-145">Code snippet:</span></span>

```javascript
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="728f3-146">#3-PAC 檔案： 分別表示管理所有 Office 365 目的地</span><span class="sxs-lookup"><span data-stu-id="728f3-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="728f3-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-147"></span></span>

<span data-ttu-id="728f3-p110">第三個範例會示範如何將傳送至單一目的地與 Office 365 相關聯的所有網路要求。這通常用來略過的 Office 365 網路要求的所有檢查並提供您所有已發佈端點的格式是在清單中要用於您的自訂 PAC 格式。</span><span class="sxs-lookup"><span data-stu-id="728f3-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="728f3-150">程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="728f3-150">Code snippet:</span></span>

```javascript
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="728f3-151">使用自訂指令碼或手動建立自己的 PAC 檔案</span><span class="sxs-lookup"><span data-stu-id="728f3-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="728f3-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-152"></span></span>

<span data-ttu-id="728f3-p111">以下是一些社群的更多工具如果您已建立您想要共用離開的某個項目中的註解的附註。無的社群工具本文中所參照的正式支援或 microsoft 維護，而且您的方便這裡提供。</span><span class="sxs-lookup"><span data-stu-id="728f3-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="728f3-p112">這是最早社群產生工具來協助管理程序的 Office 365 社群成員的內建的工具。以下是[下載](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)的連結。</span><span class="sxs-lookup"><span data-stu-id="728f3-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="728f3-157">概念證明具有可匯出的防火牆規則： [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/)。</span><span class="sxs-lookup"><span data-stu-id="728f3-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="728f3-158">[從 IT Praktyk: RSS 轉換](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7)和[XML 轉換](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)。</span><span class="sxs-lookup"><span data-stu-id="728f3-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="728f3-159">從 Peter Abele：[下載](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)。</span><span class="sxs-lookup"><span data-stu-id="728f3-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="728f3-p113">使用網路分析來判斷其網路要求應該略過 proxy 基礎結構。若要略過客戶 proxy 所使用的最常見 Fqdn 如下所示因網路流量傳送和接收來自這些端點數量。</span><span class="sxs-lookup"><span data-stu-id="728f3-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- <span data-ttu-id="728f3-162">確定直接傳送到您的防火牆的所有網路要求都有相對應項目在防火牆允許允許透過要求的清單。</span><span class="sxs-lookup"><span data-stu-id="728f3-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>

## <a name="perimeter-network-integration"></a><span data-ttu-id="728f3-163">周邊網路整合</span><span class="sxs-lookup"><span data-stu-id="728f3-163">Perimeter network integration</span></span>
<span data-ttu-id="728f3-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-164"></span></span>

<span data-ttu-id="728f3-165">您知道 Microsoft 的 WAN 是其中一個世界中的最大或骨幹吗？</span><span class="sxs-lookup"><span data-stu-id="728f3-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="728f3-p114">它會是 true，這個大規模的網路是何謂 Office 365 並在您的世界不論 where 工作我們其他雲端服務。我們網路組成高頻寬、 低延遲、 容錯移轉能力連結與千分位私下擁有的深色光纖和資料中心及 edge 節點，所有以方便使用我們 cloud services 之間的多個 Tb 連線路由哩的分數。</span><span class="sxs-lookup"><span data-stu-id="728f3-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="728f3-p115">使用類似的網路中，您想貴組織的裝置盡連線到我們的網路。超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好並不那麼良好對等手掌核我們的網路。</span><span class="sxs-lookup"><span data-stu-id="728f3-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="728f3-p116">您可以手動或自動設定以最佳方式處理 Office 365 應用程式網路要求，視您的設備網路上的裝置。您需要對以最佳方式處理 Office 365 的網路流量進行哪些設定變更取決於您的環境。Office 365 網路要求可能獲益允許下列的網路設定：</span><span class="sxs-lookup"><span data-stu-id="728f3-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="728f3-174">透過較不重要的網路流量的優先順序。</span><span class="sxs-lookup"><span data-stu-id="728f3-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="728f3-p117">路由傳送至本機的輸出透過慢速 WAN 避免 backhauling 時利用 Microsoft 網路上可用的低延遲的連結。[以下是很好的討論區](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/)的客戶投入為基礎。</span><span class="sxs-lookup"><span data-stu-id="728f3-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="728f3-177">使用本機輸出附近的 DNS 以確保離開本機輸出網路要求到達最接近的 Microsoft 對等的位置。</span><span class="sxs-lookup"><span data-stu-id="728f3-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="728f3-178">從深入的封包檢查或符合規模的延遲需求處理其他密集的網路封包排除。</span><span class="sxs-lookup"><span data-stu-id="728f3-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="728f3-p118">摩登的網路裝置包括一般、 不受信任的網際網路流量不同管理網路要求受信任應用程式，例如 Office 365 的功能。SD WAN 解決方案之新入門、 使用的網路，例如點時間可用性、 延遲或效能的各種連線路徑中的變更狀態認知也可用執行流量及路徑的選取範圍的這類區別之間的使用者與雲端。</span><span class="sxs-lookup"><span data-stu-id="728f3-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="728f3-181">請參閱規劃您的網路設定的其他指導[網路和 Office 365 規劃移轉](network-and-migration-planning.md)、[效能疑難排解 Office 365 的規劃](performance-troubleshooting-plan.md)和[部署 Office 365 規劃檢查清單](deployment-planning-checklist.md)。</span><span class="sxs-lookup"><span data-stu-id="728f3-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="728f3-182">若要實作此案例：</span><span class="sxs-lookup"><span data-stu-id="728f3-182">To implement this scenario:</span></span>

<span data-ttu-id="728f3-p119">如果他們可以使用 Office 365 URL 和 IP 定義從 xml 轉換成便利負荷本機 （使用者）、 低網路輸出的 Office 365 流量、 管理其優先順序相對於其他應用程式及調整] 核取您的網路解決方案或服務提供者Office 365 連線到 Microsoft network 根據變更網路狀況的網路路徑。某些解決方案下載及自動化 Office 365 URL 和 IP XMLs 定義其堆疊中。</span><span class="sxs-lookup"><span data-stu-id="728f3-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="728f3-185">永遠確定已實作的解決方案具有必要程度恢復] 中的 Office 365 流量的網路路徑的適當地理備援當他們成為發佈至 Office 365 Url 和 Ip 變更所能容納。</span><span class="sxs-lookup"><span data-stu-id="728f3-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>

## <a name="faq"></a><span data-ttu-id="728f3-186">常見問題集</span><span class="sxs-lookup"><span data-stu-id="728f3-186">FAQ</span></span>

<span data-ttu-id="728f3-187">常見問題集管理員連線的相關問題：</span><span class="sxs-lookup"><span data-stu-id="728f3-187">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="728f3-188">如何提交問題？</span><span class="sxs-lookup"><span data-stu-id="728f3-188">How do I submit a question?</span></span>

<span data-ttu-id="728f3-p120">按一下以指出本文若已有幫助下方的連結並送出任何其他問題。我們監視意見反應及使用最常見問題集更新的問題。</span><span class="sxs-lookup"><span data-stu-id="728f3-p120">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="728f3-191">更新之 XML 檔案的時機</span><span class="sxs-lookup"><span data-stu-id="728f3-191">When is the XML file updated?</span></span>

<span data-ttu-id="728f3-p121">當新端點即已宣佈時、 有通常是 30 + 天緩衝區它們有效與網路要求開始移至其之前。此緩衝區是以確保客戶和合作夥伴有機會來更新其系統。FQDN 和 IP 首碼新增和移除當做宣告，這表示新的 FQDN 將 XML 檔案中使用前 30 天內同時處理 XML 檔案中。因為我們停止傳送到我們要移除前公告其移除，當我們會移除之端點的 XML，同時當做宣告的端點的網路要求就會已經未使用。</span><span class="sxs-lookup"><span data-stu-id="728f3-p121">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="728f3-196">可以使用要接收通知的方式變更的？</span><span class="sxs-lookup"><span data-stu-id="728f3-196">How can I be notified of changes?</span></span>
<span data-ttu-id="728f3-197"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-197"></span></span>

<span data-ttu-id="728f3-p122">Office 365 端點發佈結尾處的每個月 30 天的通知。有時會變更就會發生一次以上一個月或更短的通知期間使用。當加入端點時，列出的[RSS 摘要](https://go.microsoft.com/fwlink/p/?linkid=236301)的有效日期是要在其後網路要求將會傳送到端點的日期。如果您是新 rss，以下是如何[訂閱透過 Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416)或您可以[有 RSS 摘要更新傳送給您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。</span><span class="sxs-lookup"><span data-stu-id="728f3-p122">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="728f3-202">如何讀取 RSS 變更記錄檔</span><span class="sxs-lookup"><span data-stu-id="728f3-202">How do I read the RSS change log?</span></span>
<span data-ttu-id="728f3-203"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-203"></span></span>

<span data-ttu-id="728f3-p123">訂閱 rss 摘要之後，您可以剖析資訊自行或以指令碼。下表說明格式的 rss 摘要 o 讓更容易。</span><span class="sxs-lookup"><span data-stu-id="728f3-p123">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="728f3-206">**區段**</span><span class="sxs-lookup"><span data-stu-id="728f3-206">**Section**</span></span>|<span data-ttu-id="728f3-207">**第 1 部分**</span><span class="sxs-lookup"><span data-stu-id="728f3-207">**Part 1**</span></span>|<span data-ttu-id="728f3-208">**第 2 部分**</span><span class="sxs-lookup"><span data-stu-id="728f3-208">**Part 2**</span></span>|<span data-ttu-id="728f3-209">**第 3 部分**</span><span class="sxs-lookup"><span data-stu-id="728f3-209">**Part 3**</span></span>|<span data-ttu-id="728f3-210">**第 4 部分**</span><span class="sxs-lookup"><span data-stu-id="728f3-210">**Part 4**</span></span>|<span data-ttu-id="728f3-211">**第 5**</span><span class="sxs-lookup"><span data-stu-id="728f3-211">**Part 5**</span></span>|<span data-ttu-id="728f3-212">**第 6**</span><span class="sxs-lookup"><span data-stu-id="728f3-212">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="728f3-213">**描述**</span><span class="sxs-lookup"><span data-stu-id="728f3-213">**Description**</span></span> <br/> |<span data-ttu-id="728f3-214">數目</span><span class="sxs-lookup"><span data-stu-id="728f3-214">Count</span></span>  <br/> |<span data-ttu-id="728f3-215">之後，您可以預期傳送給端點的網路要求的日期。</span><span class="sxs-lookup"><span data-stu-id="728f3-215">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="728f3-216">基本的功能或服務所需之端點的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="728f3-216">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="728f3-217">您可以連線到此端點除了網際網路 ExpressRoute 電路上吗？</span><span class="sxs-lookup"><span data-stu-id="728f3-217">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="728f3-218">**Yes** -您可以連線到此端點上的網際網路和 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="728f3-218">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="728f3-219">[**否**]-您只可以連線至網際網路上這個端點。</span><span class="sxs-lookup"><span data-stu-id="728f3-219">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="728f3-220">目的地正在新增或移除的 FQDN 或 IP 範圍。</span><span class="sxs-lookup"><span data-stu-id="728f3-220">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="728f3-221">**範例**</span><span class="sxs-lookup"><span data-stu-id="728f3-221">**Example**</span></span> <br/> |<span data-ttu-id="728f3-222">1 /</span><span class="sxs-lookup"><span data-stu-id="728f3-222">1/</span></span>  <br/> |<span data-ttu-id="728f3-223">[有效 xx/xx/xxx。</span><span class="sxs-lookup"><span data-stu-id="728f3-223">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="728f3-224">必要：\<描述\>。</span><span class="sxs-lookup"><span data-stu-id="728f3-224">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="728f3-225">ExpressRoute：</span><span class="sxs-lookup"><span data-stu-id="728f3-225">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="728f3-226">\<是/否\>。</span><span class="sxs-lookup"><span data-stu-id="728f3-226">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="728f3-227">\<FQDN/IP\>]，</span><span class="sxs-lookup"><span data-stu-id="728f3-227">\<FQDN/IP\>],</span></span>  <br/> |

<span data-ttu-id="728f3-228">注意，每個項目有一組通用的分隔字元其他的一些事項：</span><span class="sxs-lookup"><span data-stu-id="728f3-228">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="728f3-229">**/**-之後計數</span><span class="sxs-lookup"><span data-stu-id="728f3-229">**/** - after the count</span></span>
- <span data-ttu-id="728f3-230">**[** -指出項目計數</span><span class="sxs-lookup"><span data-stu-id="728f3-230">**[** - to indicate the entry for the count</span></span>
- <span data-ttu-id="728f3-p124">**.**-使用傳來的項目每個不同區段</span><span class="sxs-lookup"><span data-stu-id="728f3-p124">**.** - used in between each distinct section of the entry</span></span>
- <span data-ttu-id="728f3-233">**]、** -表示單一項目結尾</span><span class="sxs-lookup"><span data-stu-id="728f3-233">**],** - to indicate the end of a single entry</span></span>
- <span data-ttu-id="728f3-p125">**].**-若要指出結尾的所有項目</span><span class="sxs-lookup"><span data-stu-id="728f3-p125">**].** - To indicate the end of all the entries</span></span>

### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="728f3-236">如何判斷我租用戶的位置？</span><span class="sxs-lookup"><span data-stu-id="728f3-236">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="728f3-237">最適合使用我們的[資料中心對應](https://o365datacentermap.azurewebsites.net/)來判定**租用戶位置**。</span><span class="sxs-lookup"><span data-stu-id="728f3-237">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="728f3-238">Am I 對等適當地向 Microsoft 吗？</span><span class="sxs-lookup"><span data-stu-id="728f3-238">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="728f3-239">在[具有 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。</span><span class="sxs-lookup"><span data-stu-id="728f3-239">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="728f3-p126">超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好並不那麼良好對等手掌核我們的網路。</span><span class="sxs-lookup"><span data-stu-id="728f3-p126">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="728f3-242">如何判斷哪些 IP 位址來接受透過 ExpressRoute？</span><span class="sxs-lookup"><span data-stu-id="728f3-242">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="728f3-243">[Microsoft 的 IP 範圍](https://www.microsoft.com/download/details.aspx?id=53602)及特定的 Office 365 [BGP 社群 （英文）](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)會定義**接受 ExpressRoute 路由**。</span><span class="sxs-lookup"><span data-stu-id="728f3-243">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="728f3-244">如何判斷我需要哪些端點？</span><span class="sxs-lookup"><span data-stu-id="728f3-244">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="728f3-p127">我們定期新增新的功能與服務至 Office 365 套件中，展開連線橫向。如果您正在訂閱 E3 或 E5 SKU，要考量的端點清單簡易的方式是您需要所有這些套件以取得完整的功能。如果您未訂閱至這些 Sku 其中一項不同的是最少的端點數目。</span><span class="sxs-lookup"><span data-stu-id="728f3-p127">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="728f3-248">請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)取得 Office 365 端點類別的詳細資訊並了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="728f3-248">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="728f3-p128">在下列影像中，您可以看到 FQDN 資料表的 Office Online] 區段中的部分範例。資料列會依據功能及連線的差異。前兩列表示上標示之端點的設定依賴 Office Online 中的 Office 365 驗證及身分識別和入口網站所需與共用章節。這是一般內以這些共用服務所依賴的 Office 365 服務。第三列會指出用戶端電腦必須能夠抵達\*。 使用 Office Online 和第四列的 officeapps.live.com 表示電腦也必須能夠抵達\*。 若要使用 Office Online cdn.office.net。</span><span class="sxs-lookup"><span data-stu-id="728f3-p128">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="728f3-254">雖然兩者第三列及四才能使用 Office Online，他們已經已分隔表示目的地是不同：</span><span class="sxs-lookup"><span data-stu-id="728f3-254">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="728f3-255">\*。 officeapps.live.com 並非 CDN、 此命名空間的這表示要求會直接移至 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="728f3-255">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
2. <span data-ttu-id="728f3-256">\*。 officeapps.live.com 是使用 Microsoft Peering ExpressRoute 電路上存取。</span><span class="sxs-lookup"><span data-stu-id="728f3-256">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
3. <span data-ttu-id="728f3-257">Office Online 相關聯的 IP 位址和\*。 officeapps.live.com 可以找到遵循此連結。</span><span class="sxs-lookup"><span data-stu-id="728f3-257">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
4. <span data-ttu-id="728f3-258">\*。 cdn.office.net 代表 CDN 主控的 Akamai、 此命名空間的這表示要求會前往 Akamai 資料中心。</span><span class="sxs-lookup"><span data-stu-id="728f3-258">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
5. <span data-ttu-id="728f3-259">\*。 cdn.office.net 不是在 ExpressRoute 電路可存取。</span><span class="sxs-lookup"><span data-stu-id="728f3-259">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
6. <span data-ttu-id="728f3-260">Office Online 相關聯的 IP 位址和\*。 cdn.office.net 不提供。</span><span class="sxs-lookup"><span data-stu-id="728f3-260">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>

![端點] 頁面的螢幕擷取畫面](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="728f3-262">不是在 [發佈] 清單上查看 IP 位址的網路要求，我需要提供存取備份吗？</span><span class="sxs-lookup"><span data-stu-id="728f3-262">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="728f3-263"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-263"></span></span>

<span data-ttu-id="728f3-p129">我們只會提供您應直接路由傳送至網際網路或 ExpressRoute 上的 Office 365 伺服器的 IP 位址。這不是所有您會看見網路要求的 IP 位址的完整清單。您會看見網路要求，以查看 Microsoft 及協力廠商擁有、 已解除發佈、 IP 位址。這些 IP 位址為動態產生或受管理的這些變更時防止及時通知的方式。如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。</span><span class="sxs-lookup"><span data-stu-id="728f3-p129">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="728f3-269">請參閱 IP 相關聯想的詳細資訊的 Office 365 吗？</span><span class="sxs-lookup"><span data-stu-id="728f3-269">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="728f3-270">檢查是否使用[CIDR 計算器](http://jodies.de/ipcalc)較大發佈範圍中包含的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="728f3-270">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="728f3-p130">請參閱協力廠商是否擁有 IP 與[whois 查詢](https://dnsquery.org/)。如果是擁有 Microsoft，則可能內部的協力廠商。</span><span class="sxs-lookup"><span data-stu-id="728f3-p130">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="728f3-p131">檢查憑證、 在瀏覽器中連線至 IP 位址使用*HTTPS://\<IP_ADDRESS\> \* ，檢查要了解哪些網域相關聯的 IP 位址的憑證上所列的網域。如果它是 Microsoft 擁有 IP 位址和不在清單上的 Office 365 IP 位址，它是可能的 IP 位址是與 Microsoft CDN 如*MSOCDN.NET\*或另一個 Microsoft 網域不含已發佈的 IP 資訊相關聯。如果您不要發現憑證上的網域是一個其中我們宣告清單的 IP 位址，請讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="728f3-p131">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="728f3-276">為什麼要查看名稱 nsatc.net 或 akadns.net Microsoft 網域名稱？</span><span class="sxs-lookup"><span data-stu-id="728f3-276">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="728f3-277"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-277"></span></span>

<span data-ttu-id="728f3-p132">Office 365 與其他 Microsoft 服務使用數個協力廠商服務，例如 Akamai 和 MarkMonitor 以提升您的 Office 365 功能。若要保留給予您最佳的經驗，我們可能會變更這些服務未來。在這麼做，我們通常會發佈 CNAME 記錄以指向協力廠商擁有的網域、 record 或 IP 位址。協力廠商網域可能會主控內容，例如 CDN 或時可能會主控的服務，例如地理流量管理服務。當您看到這些協力廠商提供的連線時，它們的格式重新導向或轉介，無法從用戶端初始要求。某些客戶必須以確保這種形式的轉介和重新導向允許將傳遞沒有明確地將新增可能會使用長潛在 Fqdn 第三方服務清單。</span><span class="sxs-lookup"><span data-stu-id="728f3-p132">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="728f3-p133">服務清單，可能隨時變更。一些目前所使用的服務包括：</span><span class="sxs-lookup"><span data-stu-id="728f3-p133">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="728f3-p134">[MarkMonitor](https://www.markmonitor.com/)使用中看見要求包含*\*。 nsatc.net* 。此服務會提供網域名稱保護和監控以防止遭到惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="728f3-p134">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="728f3-p135">[ExactTarget](https://www.marketingcloud.com/)使用中看見要求送至*\*。 exacttarget.com* 。此服務會提供電子郵件連結管理和監控對惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="728f3-p135">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="728f3-p136">當您看到包含其中一個下列 Fqdn 的要求時[Akamai](https://www.akamai.com/)未使用。此服務會提供地理 DNS 和內容傳遞網路服務。</span><span class="sxs-lookup"><span data-stu-id="728f3-p136">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="728f3-292">什麼是 Office 365 端點的三種類型？</span><span class="sxs-lookup"><span data-stu-id="728f3-292">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="728f3-293"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-293"></span></span>

- <span data-ttu-id="728f3-p137">您連線至擷取如 DNS 查詢及 CDN 內容擷取的基本網際網路服務的協力廠商服務。您也連線至協力廠商服務如合併 YouTube 影片 OneNote 筆記本中的整合功能。</span><span class="sxs-lookup"><span data-stu-id="728f3-p137">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
- <span data-ttu-id="728f3-p138">您連線至次要服務主控與執行 microsoft 如 edge 節點可讓您的網路要求的最接近的網際網路位置的 Microsoft 通用網路輸入到您的電腦。為金星上第三個最大網路，這可改善連線經驗。您也連線至 Microsoft Azure 服務，例如 Azure 媒體服務所用的各種 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="728f3-p138">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
- <span data-ttu-id="728f3-p139">您連線至主要 Office 365 服務，例如 Exchange Online 信箱伺服器或 Skype 商務線上唯一與專屬資料所在的伺服器。您可以連線至主要的 Office 365 服務 FQDN 或 IP 位址並使用網際網路或 ExpressRoute 電路。您只可以連線到第三方與網際網路電路上使用 Fqdn 的次要服務。</span><span class="sxs-lookup"><span data-stu-id="728f3-p139">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>

<span data-ttu-id="728f3-p140">下圖顯示這些服務區域之間的差異。此圖表中左下角的客戶在內部網路具有多個網路裝置來協助管理網路連線。這種方式的設定都通用的企業客戶。如果您的網路只有用戶端電腦與網際網路，也支援，之間的防火牆，而且會想要確保您的防火牆可以允許清單規則中支援 Fqdn 和萬用字元。</span><span class="sxs-lookup"><span data-stu-id="728f3-p140">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="728f3-306">請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)取得 Office 365 端點類別的詳細資訊並了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="728f3-306">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![使用 Office 365 時顯示三種不同類型的網路端點](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="728f3-308">我無法或不想要使用任何協力廠商的服務</span><span class="sxs-lookup"><span data-stu-id="728f3-308">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="728f3-309"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-309"></span></span>

<span data-ttu-id="728f3-p141">Office 365 是一組透過網際網路內建函數的服務、 可靠性與可用性的承諾根據所提供的許多標準網際網路服務。例如，如 DNS、 CRL、 及 Cdn 標準網際網路服務必須使用 Office 365 就如同他們必須使用最現代網際網路服務連至連至。</span><span class="sxs-lookup"><span data-stu-id="728f3-p141">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="728f3-p142">除了這些基本的網際網路服務、 有協力廠商所使用服務的僅限整合功能。例如，使用中的 Microsoft 小組 Giphy.com 可讓客戶順暢地包含 Gif 小組中。同樣地，YouTube 和 Flickr 是用來將視訊及圖像順暢地整合至 Office 用戶端從網際網路的協力廠商服務。雖然這些所需的整合，它們被標示為選用這表示核心功能的服務會繼續運作如果端點不是可存取 Office 365 端點文章中。</span><span class="sxs-lookup"><span data-stu-id="728f3-p142">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="728f3-316">如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="728f3-316">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="728f3-317">我無法或不想要使用任何次要服務</span><span class="sxs-lookup"><span data-stu-id="728f3-317">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="728f3-318"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-318"></span></span>

<span data-ttu-id="728f3-p143">次要服務是 Microsoft Office 365 控制項內不屬於。這些是之類的邊緣網路、 Azure 媒體服務及 Azure 內容傳遞網路。這些所有需要使用 Office 365，且必須是連至。</span><span class="sxs-lookup"><span data-stu-id="728f3-p143">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="728f3-322">如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="728f3-322">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="728f3-323">如何封鎖存取 Microsoft 的用戶服務？</span><span class="sxs-lookup"><span data-stu-id="728f3-323">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="728f3-324"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="728f3-324"></span></span>

<span data-ttu-id="728f3-p144">限制存取我們取用者服務應在您自己的風險、 封鎖取用者服務僅可靠方法是以限制存取*login.live.com* FQDN。這個 FQDN 可供廣泛的服務包括非消費者服務，例如 MSDN、 TechNet、 和其他人。限制存取至此 fqdn 可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="728f3-p144">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="728f3-328">請記住封鎖存取 Microsoft 取用者服務來說不會阻止您網路上的某個人的能力 exfiltrate 使用 Office 365 租用戶或其他服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="728f3-328">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="728f3-329">相關主題</span><span class="sxs-lookup"><span data-stu-id="728f3-329">Related Topics</span></span>

[<span data-ttu-id="728f3-330">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="728f3-330">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="728f3-331">Microsoft Azure Datacenter IP 範圍</span><span class="sxs-lookup"><span data-stu-id="728f3-331">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="728f3-332">Microsoft 公用 IP 空間</span><span class="sxs-lookup"><span data-stu-id="728f3-332">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="728f3-333">Microsoft Intune 的網路基礎結構需求</span><span class="sxs-lookup"><span data-stu-id="728f3-333">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="728f3-334">Power BI 和 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="728f3-334">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
<span data-ttu-id="728f3-335">[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)</span><span class="sxs-lookup"><span data-stu-id="728f3-335">[Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md)</span></span>
  
[<span data-ttu-id="728f3-336">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="728f3-336">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="728f3-337">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="728f3-337">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)