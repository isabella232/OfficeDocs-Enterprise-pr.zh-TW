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
ms.openlocfilehash: 0396174719adc7794a1d6bb4b1f950bfe4603996
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540060"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="2b6ca-104">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="2b6ca-104">Managing Office 365 endpoints</span></span>

## <a name="office-365-network-connectivity"></a><span data-ttu-id="2b6ca-105">Office 365 網路連線</span><span class="sxs-lookup"><span data-stu-id="2b6ca-105">Office 365 network connectivity</span></span>

 <span data-ttu-id="2b6ca-p102">連線至 Office 365 包含高數量，受信任的網路要求他們正在進行透過接近使用者低延遲輸出時最適合執行。某些 Office 365 的連線可以獲益最佳化連線。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p102">Connections to Office 365 consist of high volume, trusted network requests that perform best when they're made over a low-latency egress that is near the user. Some Office 365 connections can benefit from optimizing the connection.</span></span> 
  
1. <span data-ttu-id="2b6ca-108">確定防火牆允許清單允許連線到 Office 365 端點。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-108">Ensure your firewall allow lists allow for connectivity to Office 365 endpoints.</span></span>
    
2. <span data-ttu-id="2b6ca-109">若要允許透過網際網路連線到萬用字元及解除發佈目的地的電話使用 proxy 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-109">Use your proxy infrastructure to allow Internet connectivity to wildcard and unpublished destinations.</span></span>
    
3. <span data-ttu-id="2b6ca-110">維護最佳的周邊網路組態。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-110">Maintain an optimal perimeter network configuration.</span></span>
    
4. <span data-ttu-id="2b6ca-111">[確定您要取得最佳的連線](https://aka.ms/o365perfprinciples)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-111">[Ensure you're getting the best connectivity](https://aka.ms/o365perfprinciples).</span></span>
    
5. <span data-ttu-id="2b6ca-112">請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-112">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
    
![透過防火牆及 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a><span data-ttu-id="2b6ca-114">更新的輸出防火牆允許清單</span><span class="sxs-lookup"><span data-stu-id="2b6ca-114">Update your firewall's outbound allow lists</span></span>

<span data-ttu-id="2b6ca-p103">您可以藉由傳送的所有受信任直接透過防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理最佳化您的網路。這可減少從延遲的效能低落並減少周邊容量需求。選擇 [建立信任關係要求的網路最簡單的方法是使用上述**Proxy** ] 索引標籤上的我們預先建置的 PAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p103">You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces slow performance from latency and reduces your perimeter capacity requirements. The easiest way to choose which network requests to trust is to use our pre-built PAC files on the **Proxies** tab above.</span></span> 
  
<span data-ttu-id="2b6ca-p104">如果您防火牆封鎖輸出流量會想要確保所有 IP 和 Fqdn 列為此[XML 檔案](https://go.microsoft.com/fwlink/?LinkId=533185)中**所需**的 [允許] 清單上。辨識所有服務都需要使用一些 3rd 廠商服務。我們不提供的憑證提供者、 內容傳遞網路、 DNS 提供者，例如這些 3rd 廠商服務的 IP 位址等等。完整 Office 365 功能，您必須能夠抵達所有要求的 Office 365 不論多少資訊我們發佈目的地的目的地。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p104">If your firewall blocks outbound traffic, you'll want to ensure all of the IP and FQDNs listed as **Required** in this [XML file](https://go.microsoft.com/fwlink/?LinkId=533185) are on the allow list. Recognize all services require the use of some 3rd party services. We don't provide IP addresses for these 3rd party services such as certificate providers, Content Delivery Networks, DNS providers, and so on. For full Office 365 functionality, you must be able to reach all destinations requested by Office 365 regardless of how much information we publish about the destination.</span></span> 
  
<span data-ttu-id="2b6ca-122">許多目的地沒有發佈 IP 位址或列為 「 無特定的完整的網域名稱萬用字元網域，請使用這項功能您必須能夠解析這些網路要求，以目前的 IP 位址要求以及傳送透過網際網路的網路要求。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-122">Many destinations do not have an IP address published or are listed as a wildcard domain with no specific fully qualified domain name, to use this functionality you must be able to resolve these network requests to the current IP address being requested and send the network request over the Internet.</span></span>
  
<span data-ttu-id="2b6ca-p105">使用防火牆會剖析代替您撥打電話之 XML 檔案，更新規則會自動根據服務或功能想要路由傳送直接透過防火牆自動化您的程序。您也可以使用[Azure 範圍](https://azurerange.azurewebsites.net/)工具已由社群建立且會為您的 XML 剖析 Cisco XE 路由或 ACL 清單組態、 純文字或 CSV 匯出選項。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p105">Automate your process by using a firewall that parses the XML file on your behalf and updates your rules automatically based on the services or features you plan to route directly through your firewall. You can also use the [Azure Range](https://azurerange.azurewebsites.net/) tool that has been built by the community and parses the XML for you with export options for Cisco XE Route or ACL list configuration, plain text, or CSV.</span></span> 
  
<span data-ttu-id="2b6ca-125">讓您可以變更訂閱透過[RSS 根據變更記錄](https://go.microsoft.com/fwlink/p/?linkid=236301)我們使用我們[參考 （英文） 網站](urls-and-ip-address-ranges.md)上的網路目的地的較長的說明。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-125">A longer explanation of the network destinations is available on our [reference site](urls-and-ip-address-ranges.md) as well through our [RSS based change log](https://go.microsoft.com/fwlink/p/?linkid=236301) so you can subscribe to changes.</span></span> 
  
<span data-ttu-id="2b6ca-126"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-126"></span></span>
## <a name="configure-outbound-paths-with-pac-files"></a><span data-ttu-id="2b6ca-127">設定 PAC 檔輸出路徑</span><span class="sxs-lookup"><span data-stu-id="2b6ca-127">Configure outbound paths with PAC files</span></span>

<span data-ttu-id="2b6ca-p106">用於管理 Office 365 與相關聯，但沒有提供 IP 位址的網路要求 PAC 或 WPAD 檔案。透過 proxy 或周邊裝置傳送的一般網路要求可能會形成額外的延遲。雖然 proxy 驗證會帶來最大稅，其他服務，例如信譽查閱和嘗試檢查封包可能會造成不良的使用者經驗。此外，這些周邊網路裝置需要足夠的容量來處理所有網路要求。我們建議略過您直接的 Office 365 網路要求的 proxy 或檢查基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p106">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While proxy authentication incurs the largest tax, other services such as reputation lookup and attempts to inspect packets can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="2b6ca-p107">使用下列其中一個我們 PAC 檔案的起始位置為決定何種網路流量會傳送至 proxy 和其就會傳送給防火牆。如果您是 PAC 或 WPAD 檔案，從一個適用的 Office 365 顧問閱讀此文章[部署 PAC 檔案](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/)的相關的新功能。想要檢閱這些開始進行並編輯以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p107">Use one of our PAC files as a starting place to determine what network traffic will be sent to a proxy and which will be sent to a firewall. If you're new to PAC or WPAD files, read this post about [deploying PAC files](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/) from one of our Office 365 consultants. You'll want to review these as a starting place and edit to suit your environment.</span></span> 
  
 <span data-ttu-id="2b6ca-136">**更新 7/10/2018 PAC 檔案**。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-136">**PAC files updated 7/10/2018**.</span></span> 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a><span data-ttu-id="2b6ca-137">#1-PAC 檔案： 隔開需要網際網路從已知的 Office 365 FQDN 的 Fqdn。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-137">#1 - PAC file: Separates required Internet FQDNs from known Office 365 FQDN.</span></span>

<span data-ttu-id="2b6ca-p108">第一個範例是透過網際網路僅管理端點我們建議方法的示範。略過 Office 365 目的地 IP 位址其中發佈而將剩餘的網路要求傳送至 proxy 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p108">The first example is a demonstration of our recommended approach to managing endpoints over the Internet only. Bypasses the proxy for Office 365 destinations where the IP address is published and sends remaining network requests to the proxy.</span></span>
  
<span data-ttu-id="2b6ca-140">程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-140">Code snippet:</span></span>
  
```
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a><span data-ttu-id="2b6ca-141">#2-PAC 檔案： 透過網際網路和 ExpressRoute 連線到 Office 365</span><span class="sxs-lookup"><span data-stu-id="2b6ca-141">#2 - PAC file: Connect to Office 365 over the Internet and ExpressRoute</span></span>
<span data-ttu-id="2b6ca-142"><a name="bkmk_inet-aer"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-142"></span></span>

<span data-ttu-id="2b6ca-p109">第二個範例是方法的我們建議有 ExpressRoute 和網際網路電路時管理連線的示範。傳送 ExpressRoute 通告 ExpressRoute 電路的目的地及網際網路只通告 proxy 的目的地。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p109">The second example is a demonstration of our recommended approach to managing connections when ExpressRoute and Internet circuits are available. Sends ExpressRoute advertised destinations to the ExpressRoute circuit and Internet only advertised destinations to the proxy.</span></span>
  
<span data-ttu-id="2b6ca-145">程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-145">Code snippet:</span></span>
  
```
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a><span data-ttu-id="2b6ca-146">#3-PAC 檔案： 分別表示管理所有 Office 365 目的地</span><span class="sxs-lookup"><span data-stu-id="2b6ca-146">#3 - PAC file: Manage all Office 365 destinations collectively</span></span>
<span data-ttu-id="2b6ca-147"><a name="bkmk_inet-direct"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-147"></span></span>

<span data-ttu-id="2b6ca-p110">第三個範例會示範如何將傳送至單一目的地與 Office 365 相關聯的所有網路要求。這通常用來略過的 Office 365 網路要求的所有檢查並提供您所有已發佈端點的格式是在清單中要用於您的自訂 PAC 格式。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p110">The third example demonstrates sending all network requests associated with Office 365 to a single destination. This is commonly used to bypass all inspection of Office 365 network requests and offers you a format where all published endpoints are in list in the PAC format to use for your customization.</span></span>
  
<span data-ttu-id="2b6ca-150">程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-150">Code snippet:</span></span>
  
```
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a><span data-ttu-id="2b6ca-151">使用自訂指令碼或手動建立自己的 PAC 檔案</span><span class="sxs-lookup"><span data-stu-id="2b6ca-151">Use custom scripts or manually create your own PAC files</span></span>
<span data-ttu-id="2b6ca-152"><a name="pacfiles_manual"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-152"></span></span>

<span data-ttu-id="2b6ca-p111">以下是一些社群的更多工具如果您已建立您想要共用離開的某個項目中的註解的附註。無的社群工具本文中所參照的正式支援或 microsoft 維護，而且您的方便這裡提供。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p111">Here's a few more tools from the community, if you've built something you'd like to share leave a note in the comments. None of the community tools referenced in this article are officially supported or maintained by Microsoft and are provided here for your convenience.</span></span>
  
- <span data-ttu-id="2b6ca-p112">這是最早社群產生工具來協助管理程序的 Office 365 社群成員的內建的工具。以下是[下載](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)的連結。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p112">This is the oldest community generated tool to help manage the process, a tool built by a member of the Office 365 community. Here is link to [download](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7).</span></span>
    
- <span data-ttu-id="2b6ca-157">概念證明具有可匯出的防火牆規則： [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-157">Proof of Concept with exportable firewall rules: [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/).</span></span>
    
- <span data-ttu-id="2b6ca-158">[從 IT Praktyk: RSS 轉換](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7)和[XML 轉換](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-158">From IT Praktyk: [RSS conversion](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7) and [XML conversion](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896).</span></span>
    
- <span data-ttu-id="2b6ca-159">從 Peter Abele：[下載](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-159">From Peter Abele: [Download](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3).</span></span>
    
- <span data-ttu-id="2b6ca-p113">使用網路分析來判斷其網路要求應該略過 proxy 基礎結構。若要略過客戶 proxy 所使用的最常見 Fqdn 如下所示因網路流量傳送和接收來自這些端點數量。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p113">Use your network analysis to determine which network requests should bypass your proxy infrastructure. The most common FQDNs used to bypass customer proxies include the following due to the volume of network traffic sent and received from these endpoints.</span></span>
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- <span data-ttu-id="2b6ca-162">確定直接傳送到您的防火牆的所有網路要求都有相對應項目在防火牆允許允許透過要求的清單。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-162">Ensure any network requests being sent to your firewall directly have a corresponding entry in the firewall allow list to allow the request to go through.</span></span>
    
## <a name="perimeter-network-integration"></a><span data-ttu-id="2b6ca-163">周邊網路整合</span><span class="sxs-lookup"><span data-stu-id="2b6ca-163">Perimeter network integration</span></span>
<span data-ttu-id="2b6ca-164"><a name="BKMK_Perimeter"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-164"></span></span>

<span data-ttu-id="2b6ca-165">您知道 Microsoft 的 WAN 是其中一個世界中的最大或骨幹吗？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-165">Did you know Microsoft's WAN is one of the largest backbones in the world?</span></span>
  
<span data-ttu-id="2b6ca-p114">它會是 true，這個大規模的網路是何謂 Office 365 並在您的世界不論 where 工作我們其他雲端服務。我們網路組成高頻寬、 低延遲、 容錯移轉能力連結與千分位私下擁有的深色光纖和資料中心及 edge 節點，所有以方便使用我們 cloud services 之間的多個 Tb 連線路由哩的分數。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p114">It's true, this massive network is what makes Office 365 and our other cloud services work regardless of where in the world you are. Our network consists of high bandwidth, low latency, fail-over capable links with thousands of route miles of privately owned dark fiber, and multi-Terabit connections between datacenters and edge nodes, all to make it easier to use our cloud services.</span></span>
  
<span data-ttu-id="2b6ca-p115">使用類似的網路中，您想貴組織的裝置盡連線到我們的網路。超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好並不那麼良好對等手掌核我們的網路。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p115">With a network like this, you want your organization's devices to connect to our network as soon as possible. With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
<span data-ttu-id="2b6ca-p116">您可以手動或自動設定以最佳方式處理 Office 365 應用程式網路要求，視您的設備網路上的裝置。您需要對以最佳方式處理 Office 365 的網路流量進行哪些設定變更取決於您的環境。Office 365 網路要求可能獲益允許下列的網路設定：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p116">You can manually or automatically configure the devices on your network to optimally handle Office 365 application network requests, depending on your equipment. What configuration changes you need to make to optimally handle Office 365 network traffic will depend on your environment. Office 365 network requests may benefit from network configurations that allow the following:</span></span>
  
- <span data-ttu-id="2b6ca-174">透過較不重要的網路流量的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-174">Priority over less critical network traffic.</span></span>
    
- <span data-ttu-id="2b6ca-p117">路由傳送至本機的輸出透過慢速 WAN 避免 backhauling 時利用 Microsoft 網路上可用的低延遲的連結。[以下是很好的討論區](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/)的客戶投入為基礎。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p117">Routing to a local egress to avoid backhauling over a slow WAN link while taking advantage of the low latency available on the Microsoft network. [Here's a good discussion](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/) based on customer engagements.</span></span> 
    
- <span data-ttu-id="2b6ca-177">使用本機輸出附近的 DNS 以確保離開本機輸出網路要求到達最接近的 Microsoft 對等的位置。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-177">Using DNS near a local egress to ensure the network request that leaves the local egress arrives at the nearest Microsoft peering location.</span></span>
    
- <span data-ttu-id="2b6ca-178">從深入的封包檢查或符合規模的延遲需求處理其他密集的網路封包排除。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-178">Exclusion from deep packet inspection or other intensive network packet processing to meet latency requirements at scale.</span></span>
    
<span data-ttu-id="2b6ca-p118">摩登的網路裝置包括一般、 不受信任的網際網路流量不同管理網路要求受信任應用程式，例如 Office 365 的功能。SD WAN 解決方案之新入門、 使用的網路，例如點時間可用性、 延遲或效能的各種連線路徑中的變更狀態認知也可用執行流量及路徑的選取範圍的這類區別之間的使用者與雲端。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p118">Modern network devices include capabilities to manage network requests for trusted applications such as Office 365 differently than generic, untrusted Internet traffic. With the emerging landscape of SD-WAN solutions, such differentiation of traffic and path selection can also be performed with awareness of the changing state of the network, such as point in time availability, latency or performance of various connectivity paths between the user and the cloud.</span></span>
  
<span data-ttu-id="2b6ca-181">請參閱規劃您的網路設定的其他指導[網路和 Office 365 規劃移轉](network-and-migration-planning.md)、[效能疑難排解 Office 365 的規劃](performance-troubleshooting-plan.md)和[部署 Office 365 規劃檢查清單](deployment-planning-checklist.md)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-181">See [Network and migration planning for Office 365](network-and-migration-planning.md), [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), and [Deployment planning checklist for Office 365](deployment-planning-checklist.md) for additional guidance on planning your network configuration.</span></span> 
  
### <a name="to-implement-this-scenario"></a><span data-ttu-id="2b6ca-182">若要實作此案例：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-182">To implement this scenario:</span></span>

<span data-ttu-id="2b6ca-p119">如果他們可以使用 Office 365 URL 和 IP 定義從 xml 轉換成便利負荷本機 （使用者）、 低網路輸出的 Office 365 流量、 管理其優先順序相對於其他應用程式及調整] 核取您的網路解決方案或服務提供者Office 365 連線到 Microsoft network 根據變更網路狀況的網路路徑。某些解決方案下載及自動化 Office 365 URL 和 IP XMLs 定義其堆疊中。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p119">Check with your network solution or service provider if they can use Office 365 URL and IP definitions from XML to facilitate local (to the user), low overhead network egress for Office 365 traffic, manage its priority relative to other applications and adjust the network path for Office 365 connections into Microsoft network depending on changing network conditions. Some solutions download and automate Office 365 URL and IP XMLs definition in their stacks.</span></span>
  
<span data-ttu-id="2b6ca-185">永遠確定已實作的解決方案具有必要程度恢復] 中的 Office 365 流量的網路路徑的適當地理備援當他們成為發佈至 Office 365 Url 和 Ip 變更所能容納。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-185">Always ensure that the implemented solution has necessary degree of resiliency, appropriate geo-redundancy of the network path for Office 365 traffic and accommodates changes to Office 365 URLs and IPs as they become published.</span></span>
  
## <a name="web-service"></a><span data-ttu-id="2b6ca-186">Web 服務</span><span class="sxs-lookup"><span data-stu-id="2b6ca-186">Web service</span></span>
<span data-ttu-id="2b6ca-187"><a name="webservice"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-187"></span></span>

<span data-ttu-id="2b6ca-p120">為了協助您更妥善地識別及區分不同 Office 365 網路流量，新的 web 服務會發佈 Office 365 端點，讓您評估、 設定及保持最新變更更容易。這個新的 web 服務 （現在存在於 preview) 最後將會取代中[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)的文章，以及該資料的 RSS 和 XML 版本的端點清單。分階段進行上 2018 年 10 月 2、 預計端點資料這些格式。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p120">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service (now in preview), will eventually replace the lists of endpoints in the [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) article, along with the RSS and XML versions of that data. These format of endpoint data are planned to be phased out on October 2, 2018.</span></span> 
  
<span data-ttu-id="2b6ca-191">為客戶或網路周邊裝置廠商，您可以建置對新的 rest web 服務的 Office 365 IP 位址和 FQDN 項目。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-191">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries.</span></span>
  
- <span data-ttu-id="2b6ca-192">Office 365 Url 和 IP 位址範圍的最新版本，使用[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-192">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="2b6ca-193">在 Office 365 Url 和 IP 位址範圍] 頁面上的防火牆及 proxy 伺服器上的資料、 使用[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-193">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
- <span data-ttu-id="2b6ca-194">若要取得最新變更，請使用[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-194">To get the latest changes, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
    
<span data-ttu-id="2b6ca-195">為客戶，您可以使用此 web 服務：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-195">As a customer, you can use this web service to:</span></span> 
  
- <span data-ttu-id="2b6ca-196">更新您的 PowerShell 指令碼取得 Office 365 端點資料並修改您的網路裝置任何格式設定。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-196">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
    
- <span data-ttu-id="2b6ca-197">使用此資訊來更新 PAC 檔案部署至用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-197">Use this information to update PAC files deployed to client computers.</span></span>
    
<span data-ttu-id="2b6ca-198">為網路周邊裝置廠商，您可以使用此 web 服務：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-198">As a network perimeter device vendor, you can use this web service to:</span></span> 
  
- <span data-ttu-id="2b6ca-199">建立和測試裝置的軟體下載自動設定的清單。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-199">Create and test device software to download the list for automated configuration.</span></span> 
    
- <span data-ttu-id="2b6ca-200">檢查目前的版本。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-200">Check for the current version.</span></span>
    
- <span data-ttu-id="2b6ca-201">取得目前的變更。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-201">Get the current changes.</span></span>
    
<span data-ttu-id="2b6ca-202">下列各節說明此 web 服務、 可能會變更一段時間直到服務通常可用的預覽。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-202">The following sections describe the preview of this web service, which might change over time until the service is generally available.</span></span> 
  
<span data-ttu-id="2b6ca-203">在 web 服務的資料是最新及我們不打算變更進一步的 web 服務 Url 或傳回此 web 服務的一般可用性發行前的資料結構描述。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-203">The data on the web service is up to date and we are not planning to make further changes to the web service URLs or returned data schema before the general availability release of this web service.</span></span>
  
<span data-ttu-id="2b6ca-204">如需其他資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-204">For additional information, see:</span></span>
  
- [<span data-ttu-id="2b6ca-205">在 Office 365 Tech 社群論壇中宣告部落格文章</span><span class="sxs-lookup"><span data-stu-id="2b6ca-205">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [<span data-ttu-id="2b6ca-206">如需使用 web 服務的問題的 office 365 Tech 社群論壇</span><span class="sxs-lookup"><span data-stu-id="2b6ca-206">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a><span data-ttu-id="2b6ca-207">一般參數</span><span class="sxs-lookup"><span data-stu-id="2b6ca-207">Common parameters</span></span>

<span data-ttu-id="2b6ca-208">這些參數彼此一般跨所有 web 服務方法：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-208">These parameters are common across all the web service methods:</span></span>
  
- <span data-ttu-id="2b6ca-p121">**格式 = CSV |JSON** -查詢字串參數。根據預設，傳回的資料格式為 JSON。包含此選用參數，以傳回的資料以逗點分隔值 (CSV) 格式。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p121">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span> 
    
- <span data-ttu-id="2b6ca-p122">**ClientRequestId** -查詢字串參數。您的用戶端工作階段關聯產生必要的 GUID。您應該產生每個用戶端電腦可呼叫 web service 的 GUID。請勿使用因為它們可能會被封鎖的 web 服務未來在下列範例所示的 Guid。GUID 格式為 xxxxxxxx-是-是-是-xxxxxxxxxxxx，其中 x 代表十六進位數字。若要產生的 GUID，使用 [[新增 Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p122">**ClientRequestId** - Query string parameter. A required GUID that you generate for client session association. You should generate a GUID for each client machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span> 
    
### <a name="version-web-method"></a><span data-ttu-id="2b6ca-218">版本 web 方法</span><span class="sxs-lookup"><span data-stu-id="2b6ca-218">Version web method</span></span>

<span data-ttu-id="2b6ca-p123">Microsoft 更新的 Office 365 IP 位址和 FQDN 項目的結尾的每個月及有時會登出週期操作或支援需求。每個已發佈的執行個體的資料會指派版本號碼。版本 web 方法可讓您針對每個 Office 365 服務執行個體的最新版本會輪詢有無。我們建議您在每日、 或最、 每小時檢查版本。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p123">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly.</span></span>
  
<span data-ttu-id="2b6ca-223">有一個版本 web 方法的參數：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-223">There is one parameter for the version web method:</span></span>
  
- <span data-ttu-id="2b6ca-p124">**AllVersions = true** -查詢字串參數。根據預設，傳回的版本是最新。包含此選用參數，以要求所有發佈的版本。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p124">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span> 
    
- <span data-ttu-id="2b6ca-p125">**執行個體**-Route 參數。此選用參數會指定要傳回之版本的執行個體。如果省略，則會傳回所有執行個體。有效的執行個體： 全球性、 中國、 德國、 USGovDoD、 USGovGCCHigh</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p125">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh</span></span> 
    
<span data-ttu-id="2b6ca-p126">版本 web 方法的結果可能是單一記錄的陣列。每筆記錄中的元素包括：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p126">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>
  
- <span data-ttu-id="2b6ca-233">執行個體-Office 365 服務執行個體的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-233">instance - The short name of the Office 365 service instance.</span></span>
    
- <span data-ttu-id="2b6ca-234">最新-指定執行個體的端點之最新版本。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-234">latest - The latest version for endpoints of the specified instance.</span></span>
    
- <span data-ttu-id="2b6ca-p127">版本-指定執行個體的所有先前版本的清單。此元素是只包含如果 AllVersions 參數，則為 true。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p127">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>
   
#### <a name="examples"></a><span data-ttu-id="2b6ca-237">範例：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-237">Examples:</span></span>
  
<span data-ttu-id="2b6ca-238">範例 1 要求 URI: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-238">Example 1 request URI: **<span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p128">此 URI 會傳回最新版的每個 Office 365 服務執行個體。範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p128">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>
  
```
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
> <span data-ttu-id="2b6ca-p129">在這些 Uri ClientRequestID 參數的 GUID 是僅限範例。若要嘗試 web 服務 Uri 取出、 產生自己的 GUID。以下範例所示的 Guid 可能會遭到封鎖 web 服務所未來。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p129">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span> 
  
<span data-ttu-id="2b6ca-244">範例 2 要求 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-244">Example 2 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p130">此 URI 會傳回指定的 Office 365 服務執行個體的最新版本。範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p130">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="2b6ca-247">範例 3 要求 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-247">Example 3 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p131">此 URI CSV 格式顯示輸出。範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p131">This URI shows output in CSV format. Example result:</span></span>
  
```
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="2b6ca-250">範例 4 要求 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-250">Example 4 request URI: **<span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p132">此 URI 會顯示已發佈的 Office 365 全世界的服務執行個體的所有先前版本。範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p132">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>
  
```
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

### <a name="endpoints-web-method"></a><span data-ttu-id="2b6ca-253">端點 web 方法</span><span class="sxs-lookup"><span data-stu-id="2b6ca-253">Endpoints web method</span></span>

<span data-ttu-id="2b6ca-p133">端點 web 方法會傳回所有記錄的 IP 位址範圍及構成 Office 365 服務的 Url。端點 web 方法的參數為：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p133">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. Parameters for the endpoints web method are:</span></span>
  
- <span data-ttu-id="2b6ca-p134">**ServiceAreas** -查詢字串參數。服務區域以逗號分隔清單。有效的項目是一般、 Exchange、 SharePoint、 Skype。因為常見的服務] 區域中項目的所有其他服務區域的先決條件、 web 服務將會一律包含它們。如果您未包含此參數，會傳回所有服務區域。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p134">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span> 
    
- <span data-ttu-id="2b6ca-p135">**TenantName** -查詢字串參數。您的 Office 365 租用戶名稱。Web 服務會提供的名稱並且將它插入的租用戶名稱包含 Url 的組件中。如果您沒有提供的租用戶名稱、 Url 的這些組件已萬用字元 (\*)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p135">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span> 
    
- <span data-ttu-id="2b6ca-p136">**NoIPv6** -查詢字串參數。將此設為 true 是表示排除 IPv6 位址從輸出，例如，如果您未在您的網路中使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p136">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span> 
    
- <span data-ttu-id="2b6ca-p137">**執行個體**-Route 參數。這個必要的參數會指定要傳回之端點的執行個體。有效的執行個體： 全球性、 中國、 德國、 USGovDoD、 USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p137">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span> 
    
<span data-ttu-id="2b6ca-p138">端點 web 方法的結果是含有代表端點設每一筆記錄的記錄的陣列。針對每個記錄項目包括：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p138">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>
  
- <span data-ttu-id="2b6ca-272">識別碼-端點不變的識別碼號碼設定。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-272">id - The immutable id number of the endpoint set.</span></span>
    
- <span data-ttu-id="2b6ca-273">serviceArea-這是一部分的 [服務] 區域： 一般、 Exchange、 SharePoint、 或 Skype。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-273">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
    
- <span data-ttu-id="2b6ca-p139">url-端點的 Url 設定。DNS 記錄的 JSON 陣列。省略如果空白。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p139">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
    
- <span data-ttu-id="2b6ca-p140">tcpPorts-端點的 TCP 連接埠設定。連接埠的所有項目全都設為逗點分隔的連接埠] 或 [連接埠範圍以虛線字元 （-） 分隔清單。連接埠適用於所有 IP 位址及所有 Url，因為端點該類別的設定。省略如果空白。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p140">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
    
- <span data-ttu-id="2b6ca-p141">udpPorts-UDP 連接埠的 IP 位址在此端點集合中的範圍。省略如果空白。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p141">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
    
- <span data-ttu-id="2b6ca-p142">ip-這個設定如下所列的 TCP 或 UDP 連接埠相關聯的端點相關聯的 IP 位址範圍。省略如果空白。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p142">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. Omitted if blank.</span></span>
    
- <span data-ttu-id="2b6ca-p143">類別-端點的 [連線] 類別設定。有效值為最佳化、 允許、 及預設值。所需。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p143">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. Required.</span></span>
    
- <span data-ttu-id="2b6ca-288">expressRoute-True 或 False 時，此端點集傳閱透過 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-288">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
    
- <span data-ttu-id="2b6ca-p144">必要-True 如果此端點集需要具備才支援的 Office 365 的連線。若為 false，則省略。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p144">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. Omitted if false.</span></span>
    
- <span data-ttu-id="2b6ca-p145">備忘稿-選用端點此文字會說明若 IP 位址會遺失的 Office 365 功能或 Url 中此端點集無法存取網路層級。省略如果空白。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p145">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>
    
#### <a name="examples"></a><span data-ttu-id="2b6ca-293">範例：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-293">Examples:</span></span>
  
<span data-ttu-id="2b6ca-294">範例 1 要求 URI: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-294">Example 1 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p146">此 URI 會取得所有工作量的 Office 365 全世界執行個體的所有端點。顯示輸出摘錄的範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p146">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>
  
```
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

<span data-ttu-id="2b6ca-297">其他端點設定並不包含在此範例中。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-297">Additional endpoint sets are not included in this example.</span></span>
  
<span data-ttu-id="2b6ca-298">範例 2 要求 URI: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-298">Example 2 request URI: **<span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-299">此範例會針對 Exchange Online 與相依性只取得端點之 Office 365 全世界的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-299">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>
  
<span data-ttu-id="2b6ca-300">例如 2 的輸出是類似於範例 1 除了結果將不會包含端點的 SharePoint Online 或 Skype 商務 online。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-300">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>
  
### <a name="changes-web-method"></a><span data-ttu-id="2b6ca-301">變更 web 方法</span><span class="sxs-lookup"><span data-stu-id="2b6ca-301">Changes web method</span></span>

<span data-ttu-id="2b6ca-p147">變更 web 方法會傳回最新版更新已發佈。這通常是 IP 位址範圍及 Url 的上個月的變更。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p147">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2b6ca-304">會在預覽正確及應僅可用於開發和測試從 API 的變更資料。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-304">Data from the changes API is accurate in the preview and should be used for development and testing only.</span></span> 
  
<span data-ttu-id="2b6ca-305">變更 web 方法的參數是：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-305">The parameter for the changes web method is:</span></span>
  
- <span data-ttu-id="2b6ca-p148">**版本**-所需的 URL route 參數。您目前已實作，而且您想要查看該版以來的變更項目的版本。格式為 YYYYMMDDNN。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p148">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is YYYYMMDDNN.</span></span> 
    
<span data-ttu-id="2b6ca-p149">變更 web 方法的結果是代表特定版本的端點中變更的每筆記錄與記錄的陣列。針對每個記錄項目包括：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p149">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>
  
- <span data-ttu-id="2b6ca-311">id-不變的變更記錄的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-311">id - The immutable id of the change record.</span></span>
    
- <span data-ttu-id="2b6ca-p150">endpointSetId-端點的識別碼設為已變更的記錄。所需。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p150">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
    
- <span data-ttu-id="2b6ca-314">處理-這可以是的變更、 新增或移除並說明變更沒有端點組記錄。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-314">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record.</span></span>
    
- <span data-ttu-id="2b6ca-p151">版本-設定中已採用變更的已發佈端點的版本。版本號碼是的 YYYYMMDDNN，其中 NN 是遞增有自然數字格式的多個版本才能發佈單一的日期。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p151">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format YYYYMMDDNN, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
    
- <span data-ttu-id="2b6ca-p152">前一層子結構細部先前的端點上變更元素的值設定。這不會包含新加入的端點設定。包含 tcpPorts、 udpPorts、 ExpressRoute、 類別、 所需、 備忘稿。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p152">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="2b6ca-p153">目前-子結構細部更新 endpoinset 上變更項目的值。包含 tcpPorts、 udpPorts、 ExpressRoute、 類別、 所需、 備忘稿。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p153">current - A substructure detailing updated values of changes elements on the endpoinset. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
    
- <span data-ttu-id="2b6ca-p154">新增-細部項目新增至端點 sub 結構設定集合。如果不有任何新增，省略。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p154">add - A sub structure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
    
  - <span data-ttu-id="2b6ca-324">effectiveDate-定義資料時新增的項目將會是 live 服務中。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-324">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
    
  - <span data-ttu-id="2b6ca-325">ip-要新增至 ip 陣列項目。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-325">ips - Items to be added to the ips array.</span></span>
    
  - <span data-ttu-id="2b6ca-326">url-項目加入至 url 的陣列。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-326">urls- Items to be added to the urls array.</span></span>
    
- <span data-ttu-id="2b6ca-p155">移除-子結構細部從端點集合中移除的項目。如果不有任何移除，省略。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p155">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
    
  - <span data-ttu-id="2b6ca-329">ip-要移除 ip 陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-329">ips - Items to be removed from the ips array.</span></span>
    
  - <span data-ttu-id="2b6ca-330">從 url 陣列中移除的 url 項。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-330">urls- Items to be removed from the urls array.</span></span>
    
 <span data-ttu-id="2b6ca-331">**範例：**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-331">**Examples:**</span></span>
  
<span data-ttu-id="2b6ca-332">範例 1 要求 URI: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-332">Example 1 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p156">這會要求所有舊版的 Office 365 全世界的服務執行個體變更。範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p156">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>
  
```
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

<span data-ttu-id="2b6ca-335">範例 2 要求 URI: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-335">Example 2 request URI: **<span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**</span></span>
  
<span data-ttu-id="2b6ca-p157">這會要求變更後的指定版本的 Office 365 全世界的執行個體。在此例中指定的版本是最新。範例結果：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p157">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>
  
```
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

### <a name="example-powershell-script"></a><span data-ttu-id="2b6ca-339">範例 PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="2b6ca-339">Example PowerShell Script</span></span>

<span data-ttu-id="2b6ca-p158">以下是您可以執行以查看是否有的動作所需的更新資料的 PowerShell 指令碼。此指令碼會檢查 Office 365 全世界的執行個體端點的版本號碼。變更時，它會下載端點和篩選的"Allow"和"最佳化"類別端點。它也使用跨多個通話的唯一 ClientRequestId 並儲存在暫存檔案中找到最新版本。您應該要檢查版本更新的呼叫此指令碼一次一小時。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p158">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
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

### <a name="example-python-script"></a><span data-ttu-id="2b6ca-345">範例 Python 指令碼</span><span class="sxs-lookup"><span data-stu-id="2b6ca-345">Example Python Script</span></span>

<span data-ttu-id="2b6ca-p159">以下是 Python 指令碼、 測試與 Python 3.6.3 上 Windows 10，您可執行以查看是否有您需要更新的資料所採取的動作。此指令碼會檢查 Office 365 全世界的執行個體端點的版本號碼。變更時，它會下載端點和篩選的"Allow"和"最佳化"類別端點。它也使用跨多個通話的唯一 ClientRequestId 並儲存在暫存檔案中找到最新版本。您應該要檢查版本更新的呼叫此指令碼一次一小時。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p159">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the "Allow" and "Optimize" category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>
  
```
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

### <a name="web-service-interface-versioning"></a><span data-ttu-id="2b6ca-351">Web 服務介面版本設定</span><span class="sxs-lookup"><span data-stu-id="2b6ca-351">Web Service interface versioning</span></span>

<span data-ttu-id="2b6ca-p160">會更新以參數或這些 web 服務方法的結果可能需要未來。發佈這些 web 服務的一般可用版本之後，Microsoft 會使合理致力於提供之 web 服務的材料更新換頁通知。當 Microsoft 相信更新需要變更用戶端中使用 web 服務時、 Microsoft 會保持至少十二 （12） 月之後版本的新版本可用的 web 服務的舊版本 （回一個版本）。不要升級的時間期間的客戶可能無法存取 web 服務和它的方法。客戶必須確定 web 服務用戶端繼續運作不會發生錯誤如果至 web 服務介面簽章會進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p160">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>
  
- <span data-ttu-id="2b6ca-357">將新的選用參數新增至現有的 web 方法都不會有以舊版用戶端所提供且不會影響結果的較舊的用戶端收到。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-357">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
    
- <span data-ttu-id="2b6ca-358">將新的具名的屬性的其中一個回應其餘項目或其他欄新增以回應 CSV。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-358">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
    
- <span data-ttu-id="2b6ca-359">新增新的 web 方法不由較舊的用戶端呼叫的新名稱。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-359">Adding a new web method with a new name that is not called by the older clients.</span></span>
    
## <a name="faq"></a><span data-ttu-id="2b6ca-360">常見問題集</span><span class="sxs-lookup"><span data-stu-id="2b6ca-360">FAQ</span></span>

<span data-ttu-id="2b6ca-361">常見問題集管理員連線的相關問題：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-361">Frequently-asked administrator questions about connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="2b6ca-362">如何提交問題？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-362">How do I submit a question?</span></span>

<span data-ttu-id="2b6ca-p161">按一下以指出本文若已有幫助下方的連結並送出任何其他問題。我們監視意見反應及使用最常見問題集更新的問題。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p161">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="when-is-the-xml-file-updated"></a><span data-ttu-id="2b6ca-365">更新之 XML 檔案的時機</span><span class="sxs-lookup"><span data-stu-id="2b6ca-365">When is the XML file updated?</span></span>

<span data-ttu-id="2b6ca-p162">當新端點即已宣佈時、 有通常是 30 + 天緩衝區它們有效與網路要求開始移至其之前。此緩衝區是以確保客戶和合作夥伴有機會來更新其系統。FQDN 和 IP 首碼新增和移除當做宣告，這表示新的 FQDN 將 XML 檔案中使用前 30 天內同時處理 XML 檔案中。因為我們停止傳送到我們要移除前公告其移除，當我們會移除之端點的 XML，同時當做宣告的端點的網路要求就會已經未使用。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p162">When new endpoints are announced, there is usually a 30+ day buffer before they are effective and network requests begin going to them. This buffer is to ensure customers and partners have an opportunity to update their systems. FQDN and IP prefix additions and removals are processed in the XML file at the same time as the announcement, meaning a new FQDN will be in the XML file 30 days before use. Since we stop sending network requests to endpoints we're removing prior to announcing their removal, when we remove the endpoint from the XML at the same time as the announcement it is already unused.</span></span>
  
### <a name="how-can-i-be-notified-of-changes"></a><span data-ttu-id="2b6ca-370">可以使用要接收通知的方式變更的？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-370">How can I be notified of changes?</span></span>
<span data-ttu-id="2b6ca-371"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-371"></span></span>

<span data-ttu-id="2b6ca-p163">Office 365 端點發佈結尾處的每個月 30 天的通知。有時會變更就會發生一次以上一個月或更短的通知期間使用。當加入端點時，列出的[RSS 摘要](https://go.microsoft.com/fwlink/p/?linkid=236301)的有效日期是要在其後網路要求將會傳送到端點的日期。如果您是新 rss，以下是如何[訂閱透過 Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416)或您可以[有 RSS 摘要更新傳送給您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p163">Office 365 endpoints are published at the end of each month with 30 days notice. Occasionally changes will occur more than once a month or with shorter notice periods. When an endpoint is added, the effective date listed in the [RSS feed](https://go.microsoft.com/fwlink/p/?linkid=236301) is the date after which network requests will be sent to the endpoint. If you're new to RSS, here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).</span></span>
  
### <a name="how-do-i-read-the-rss-change-log"></a><span data-ttu-id="2b6ca-376">如何讀取 RSS 變更記錄檔</span><span class="sxs-lookup"><span data-stu-id="2b6ca-376">How do I read the RSS change log?</span></span>
<span data-ttu-id="2b6ca-377"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-377"></span></span>

<span data-ttu-id="2b6ca-p164">訂閱 rss 摘要之後，您可以剖析資訊自行或以指令碼。下表說明格式的 rss 摘要 o 讓更容易。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p164">After you subscribe to the RSS feed, you can parse the information yourself or with a script. The following table describes the format of the RSS feed o make it easier.</span></span>
  
|<span data-ttu-id="2b6ca-380">**區段**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-380">**Section**</span></span>|<span data-ttu-id="2b6ca-381">**第 1 部分**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-381">**Part 1**</span></span>|<span data-ttu-id="2b6ca-382">**第 2 部分**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-382">**Part 2**</span></span>|<span data-ttu-id="2b6ca-383">**第 3 部分**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-383">**Part 3**</span></span>|<span data-ttu-id="2b6ca-384">**第 4 部分**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-384">**Part 4**</span></span>|<span data-ttu-id="2b6ca-385">**第 5**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-385">**Part 5**</span></span>|<span data-ttu-id="2b6ca-386">**第 6**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-386">**Part 6**</span></span>|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="2b6ca-387">**描述**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-387">**Description**</span></span> <br/> |<span data-ttu-id="2b6ca-388">數目</span><span class="sxs-lookup"><span data-stu-id="2b6ca-388">Count</span></span>  <br/> |<span data-ttu-id="2b6ca-389">之後，您可以預期傳送給端點的網路要求的日期。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-389">Date after which you can expect network requests to be sent to the endpoint.</span></span>  <br/> |<span data-ttu-id="2b6ca-390">基本的功能或服務所需之端點的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-390">Basic description of the feature or service that requires the endpoint.</span></span>  <br/> |<span data-ttu-id="2b6ca-391">您可以連線到此端點除了網際網路 ExpressRoute 電路上吗？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-391">Can you connect to this endpoint on an ExpressRoute Circuit in addition to the internet?</span></span>  <br/> |<span data-ttu-id="2b6ca-392">**Yes** -您可以連線到此端點上的網際網路和 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-392">**Yes** - you can connect to this endpoint on both the internet and ExpressRoute.</span></span>  <br/> <span data-ttu-id="2b6ca-393">[**否**]-您只可以連線至網際網路上這個端點。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-393">**No** - you can only connect to this endpoint on the internet.</span></span>  <br/> |<span data-ttu-id="2b6ca-394">目的地正在新增或移除的 FQDN 或 IP 範圍。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-394">The destination FQDN or IP range being added or removed.</span></span>  <br/> |
|<span data-ttu-id="2b6ca-395">**範例**</span><span class="sxs-lookup"><span data-stu-id="2b6ca-395">**Example**</span></span> <br/> |<span data-ttu-id="2b6ca-396">1 /</span><span class="sxs-lookup"><span data-stu-id="2b6ca-396">1/</span></span>  <br/> |<span data-ttu-id="2b6ca-397">[有效 xx/xx/xxx。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-397">[Effective xx/xx/xxx.</span></span>  <br/> |<span data-ttu-id="2b6ca-398">必要：\<描述\>。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-398">Required: \<description\>.</span></span>  <br/> |<span data-ttu-id="2b6ca-399">ExpressRoute：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-399">ExpressRoute:</span></span>  <br/> |<span data-ttu-id="2b6ca-400">\<是/否\>。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-400">\<Yes/No\>.</span></span>  <br/> |<span data-ttu-id="2b6ca-401">\<FQDN/IP\>]，</span><span class="sxs-lookup"><span data-stu-id="2b6ca-401">\<FQDN/IP\>],</span></span>  <br/> |
   
<span data-ttu-id="2b6ca-402">注意，每個項目有一組通用的分隔字元其他的一些事項：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-402">A couple other things to note, every entry has a common set of delimiters:</span></span>
  
- <span data-ttu-id="2b6ca-403">**/**-之後計數</span><span class="sxs-lookup"><span data-stu-id="2b6ca-403">**/** - after the count</span></span> 
    
- <span data-ttu-id="2b6ca-404">**[** -指出項目計數</span><span class="sxs-lookup"><span data-stu-id="2b6ca-404">**[** - to indicate the entry for the count</span></span> 
    
- <span data-ttu-id="2b6ca-p165">**.**-使用傳來的項目每個不同區段</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p165">**.** - used in between each distinct section of the entry</span></span> 
    
- <span data-ttu-id="2b6ca-407">**]、** -表示單一項目結尾</span><span class="sxs-lookup"><span data-stu-id="2b6ca-407">**],** - to indicate the end of a single entry</span></span> 
    
- <span data-ttu-id="2b6ca-p166">**].**-若要指出結尾的所有項目</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p166">**].** - To indicate the end of all the entries</span></span> 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="2b6ca-410">如何判斷我租用戶的位置？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-410">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="2b6ca-411">最適合使用我們的[資料中心對應](https://o365datacentermap.azurewebsites.net/)來判定**租用戶位置**。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-411">**Tenant location** is best determined using our [datacenter map](https://o365datacentermap.azurewebsites.net/).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="2b6ca-412">Am I 對等適當地向 Microsoft 吗？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-412">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="2b6ca-413">在[具有 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-413">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="2b6ca-p167">超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好並不那麼良好對等手掌核我們的網路。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p167">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a><span data-ttu-id="2b6ca-416">如何判斷哪些 IP 位址來接受透過 ExpressRoute？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-416">How do I determine which IP addresses to accept over ExpressRoute?</span></span>

 <span data-ttu-id="2b6ca-417">[Microsoft 的 IP 範圍](https://www.microsoft.com/download/details.aspx?id=53602)及特定的 Office 365 [BGP 社群 （英文）](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)會定義**接受 ExpressRoute 路由**。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-417">**Accepted ExpressRoute routes** are defined by [Microsoft's IP ranges](https://www.microsoft.com/download/details.aspx?id=53602) and the specific Office 365 [BGP communities](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099).</span></span>
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a><span data-ttu-id="2b6ca-418">如何判斷我需要哪些端點？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-418">How do I determine which endpoints I need?</span></span>

<span data-ttu-id="2b6ca-p168">我們定期新增新的功能與服務至 Office 365 套件中，展開連線橫向。如果您正在訂閱 E3 或 E5 SKU，要考量的端點清單簡易的方式是您需要所有這些套件以取得完整的功能。如果您未訂閱至這些 Sku 其中一項不同的是最少的端點數目。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p168">We regularly add new features and services to the Office 365 suite, expanding the connectivity landscape. If you're subscribed to the E3 or E5 SKU, the simple way to think about the list of endpoints is that you need all of them to get full functionality for the suite. If you aren't subscribed to either of these SKUs the difference is minimal in terms of the number of endpoints.</span></span>
  
<span data-ttu-id="2b6ca-422">請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)取得 Office 365 端點類別的詳細資訊並了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-422">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
<span data-ttu-id="2b6ca-p169">在下列影像中，您可以看到 FQDN 資料表的 Office Online] 區段中的部分範例。資料列會依據功能及連線的差異。前兩列表示上標示之端點的設定依賴 Office Online 中的 Office 365 驗證及身分識別和入口網站所需與共用章節。這是一般內以這些共用服務所依賴的 Office 365 服務。第三列會指出用戶端電腦必須能夠抵達\*。 使用 Office Online 和第四列的 officeapps.live.com 表示電腦也必須能夠抵達\*。 若要使用 Office Online cdn.office.net。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p169">In the image below, you can see an example from a portion of the FQDN table in the Office Online section. The rows are organized by feature and differences in connectivity. The first two rows indicate Office Online relies on the endpoints marked Required in the Office 365 Authentication and Identity and portal and shared sections. This is typical for a service within Office 365 to rely on these shared services. The third row indicates client computers must be able to reach \*.officeapps.live.com to use Office Online and the fourth row indicates computers must also be able to reach \*.cdn.office.net to use Office Online.</span></span>
  
<span data-ttu-id="2b6ca-428">雖然兩者第三列及四才能使用 Office Online，他們已經已分隔表示目的地是不同：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-428">Even though both row three and four are required to use Office Online, they've been separated to indicate the destination is different:</span></span>
  
1. <span data-ttu-id="2b6ca-429">\*。 officeapps.live.com 並非 CDN、 此命名空間的這表示要求會直接移至 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-429">\*.officeapps.live.com does not represent a CDN, meaning requests to this namespace will go directly to a Microsoft datacenter.</span></span>
    
2. <span data-ttu-id="2b6ca-430">\*。 officeapps.live.com 是使用 Microsoft Peering ExpressRoute 電路上存取。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-430">\*.officeapps.live.com is accessible on ExpressRoute circuits using Microsoft Peering.</span></span>
    
3. <span data-ttu-id="2b6ca-431">Office Online 相關聯的 IP 位址和\*。 officeapps.live.com 可以找到遵循此連結。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-431">The IP addresses associated with Office Online and \*.officeapps.live.com can be found by following this link.</span></span>
    
4. <span data-ttu-id="2b6ca-432">\*。 cdn.office.net 代表 CDN 主控的 Akamai、 此命名空間的這表示要求會前往 Akamai 資料中心。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-432">\*.cdn.office.net represents a CDN hosted by Akamai, meaning requests to this namespace will go to an Akamai datacenter.</span></span>
    
5. <span data-ttu-id="2b6ca-433">\*。 cdn.office.net 不是在 ExpressRoute 電路可存取。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-433">\*.cdn.office.net is not accessible on ExpressRoute circuits.</span></span>
    
6. <span data-ttu-id="2b6ca-434">Office Online 相關聯的 IP 位址和\*。 cdn.office.net 不提供。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-434">The IP addresses associated with Office Online and \*.cdn.office.net are not available.</span></span>
    
![端點] 頁面的螢幕擷取畫面](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="2b6ca-436">不是在 [發佈] 清單上查看 IP 位址的網路要求，我需要提供存取備份吗？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-436">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="2b6ca-437"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-437"></span></span>

<span data-ttu-id="2b6ca-p170">我們只會提供您應直接路由傳送至網際網路或 ExpressRoute 上的 Office 365 伺服器的 IP 位址。這不是所有您會看見網路要求的 IP 位址的完整清單。您會看見網路要求，以查看 Microsoft 及協力廠商擁有、 已解除發佈、 IP 位址。這些 IP 位址為動態產生或受管理的這些變更時防止及時通知的方式。如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p170">We only provide IP addresses for the Office 365 servers you should route directly to over the Internet or ExpressRoute. This isn't a comprehensive list of all IP addresses you'll see network requests for. You'll see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="2b6ca-443">請參閱 IP 相關聯想的詳細資訊的 Office 365 吗？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-443">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="2b6ca-444">檢查是否使用[CIDR 計算器](http://jodies.de/ipcalc)較大發佈範圍中包含的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-444">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
    
2. <span data-ttu-id="2b6ca-p171">請參閱協力廠商是否擁有 IP 與[whois 查詢](https://dnsquery.org/)。如果是擁有 Microsoft，則可能內部的協力廠商。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p171">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
    
3. <span data-ttu-id="2b6ca-p172">檢查憑證、 在瀏覽器中連線至 IP 位址使用*HTTPS://\<IP_ADDRESS\> * ，檢查要了解哪些網域相關聯的 IP 位址的憑證上所列的網域。如果它是 Microsoft 擁有 IP 位址和不在清單上的 Office 365 IP 位址，它是可能的 IP 位址是與 Microsoft CDN 如*MSOCDN.NET*或另一個 Microsoft 網域不含已發佈的 IP 資訊相關聯。如果您不要發現憑證上的網域是一個其中我們宣告清單的 IP 位址，請讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p172">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span> 
    
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="2b6ca-450">為什麼要查看名稱 nsatc.net 或 akadns.net Microsoft 網域名稱？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-450">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="2b6ca-451"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-451"></span></span>

<span data-ttu-id="2b6ca-p173">Office 365 與其他 Microsoft 服務使用數個協力廠商服務，例如 Akamai 和 MarkMonitor 以提升您的 Office 365 功能。若要保留給予您最佳的經驗，我們可能會變更這些服務未來。在這麼做，我們通常會發佈 CNAME 記錄以指向協力廠商擁有的網域、 record 或 IP 位址。協力廠商網域可能會主控內容，例如 CDN 或時可能會主控的服務，例如地理流量管理服務。當您看到這些協力廠商提供的連線時，它們的格式重新導向或轉介，無法從用戶端初始要求。某些客戶必須以確保這種形式的轉介和重新導向允許將傳遞沒有明確地將新增可能會使用長潛在 Fqdn 第三方服務清單。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p173">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="2b6ca-p174">服務清單，可能隨時變更。一些目前所使用的服務包括：</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p174">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="2b6ca-p175">[MarkMonitor](https://www.markmonitor.com/)使用中看見要求包含*\*。 nsatc.net* 。此服務會提供網域名稱保護和監控以防止遭到惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p175">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span> 
  
<span data-ttu-id="2b6ca-p176">[ExactTarget](https://www.marketingcloud.com/)使用中看見要求送至*\*。 exacttarget.com* 。此服務會提供電子郵件連結管理和監控對惡意的行為。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p176">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span> 
  
<span data-ttu-id="2b6ca-p177">當您看到包含其中一個下列 Fqdn 的要求時[Akamai](https://www.akamai.com/)未使用。此服務會提供地理 DNS 和內容傳遞網路服務。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p177">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span> 
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a><span data-ttu-id="2b6ca-466">什麼是 Office 365 端點的三種類型？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-466">What are the three types of Office 365 endpoints?</span></span>
<span data-ttu-id="2b6ca-467"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-467"></span></span>

- <span data-ttu-id="2b6ca-p178">您連線至擷取如 DNS 查詢及 CDN 內容擷取的基本網際網路服務的協力廠商服務。您也連線至協力廠商服務如合併 YouTube 影片 OneNote 筆記本中的整合功能。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p178">You connect to third-party services to retrieve basic internet services such as DNS lookups and CDN content retrieval. You also connect to third-party services for integrations such as incorporating YouTube videos in your OneNote notebooks.</span></span>
    
- <span data-ttu-id="2b6ca-p179">您連線至次要服務主控與執行 microsoft 如 edge 節點可讓您的網路要求的最接近的網際網路位置的 Microsoft 通用網路輸入到您的電腦。為金星上第三個最大網路，這可改善連線經驗。您也連線至 Microsoft Azure 服務，例如 Azure 媒體服務所用的各種 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p179">You connect to secondary services hosted and run by Microsoft such as edge nodes that enable your network request to enter Microsoft's global network at the closest internet location to your computer. As the third largest network on the planet, this improves your connectivity experience. You also connect to Microsoft Azure services such as Azure Media Services which are used by a variety of Office 365 services.</span></span>
    
- <span data-ttu-id="2b6ca-p180">您連線至主要 Office 365 服務，例如 Exchange Online 信箱伺服器或 Skype 商務線上唯一與專屬資料所在的伺服器。您可以連線至主要的 Office 365 服務 FQDN 或 IP 位址並使用網際網路或 ExpressRoute 電路。您只可以連線到第三方與網際網路電路上使用 Fqdn 的次要服務。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p180">You connect to primary Office 365 services such as the Exchange Online mailbox server or the Skype for Business Online server where your unique and proprietary data lives. You can connect to the primary Office 365 services by FQDN or IP address and use internet or ExpressRoute circuits. You can only connect to the third party and secondary services using FQDNs on an internet circuit.</span></span>
    
<span data-ttu-id="2b6ca-p181">下圖顯示這些服務區域之間的差異。此圖表中左下角的客戶在內部網路具有多個網路裝置來協助管理網路連線。這種方式的設定都通用的企業客戶。如果您的網路只有用戶端電腦與網際網路，也支援，之間的防火牆，而且會想要確保您的防火牆可以允許清單規則中支援 Fqdn 和萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p181">The following diagram shows the differences between these service areas. In this diagram, the customer on-premises network in the lower left has multiple network devices to assist in managing network connectivity. Configurations like this one are common for enterprise customers. If your network only has a firewall between your client computers and the internet, that's supported as well, and you'll want to ensure your firewall can support FQDNs and wildcards in the allow list rules.</span></span>
  
<span data-ttu-id="2b6ca-480">請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)取得 Office 365 端點類別的詳細資訊並了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-480">Read [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md) to get more information on Office 365 endpoint categories, and to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> 
  
![使用 Office 365 時顯示三種不同類型的網路端點](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a><span data-ttu-id="2b6ca-482">我無法或不想要使用任何協力廠商的服務</span><span class="sxs-lookup"><span data-stu-id="2b6ca-482">I can't or don't want to use any third-party service</span></span>
<span data-ttu-id="2b6ca-483"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-483"></span></span>

<span data-ttu-id="2b6ca-p182">Office 365 是一組透過網際網路內建函數的服務、 可靠性與可用性的承諾根據所提供的許多標準網際網路服務。例如，如 DNS、 CRL、 及 Cdn 標準網際網路服務必須使用 Office 365 就如同他們必須使用最現代網際網路服務連至連至。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p182">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>
  
<span data-ttu-id="2b6ca-p183">除了這些基本的網際網路服務、 有協力廠商所使用服務的僅限整合功能。例如，使用中的 Microsoft 小組 Giphy.com 可讓客戶順暢地包含 Gif 小組中。同樣地，YouTube 和 Flickr 是用來將視訊及圖像順暢地整合至 Office 用戶端從網際網路的協力廠商服務。雖然這些所需的整合，它們被標示為選用這表示核心功能的服務會繼續運作如果端點不是可存取 Office 365 端點文章中。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p183">In addition to these basic internet services, there are third-party services that are only used to integrate functionality. For example, using Giphy.com within Microsoft Teams allows customers to seamlessly include Gifs within Teams. Similarly, YouTube and Flickr are third-party services that are used to seamlessly integrate video and images into Office clients from the internet. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible.</span></span>
  
<span data-ttu-id="2b6ca-490">如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-490">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a><span data-ttu-id="2b6ca-491">我無法或不想要使用任何次要服務</span><span class="sxs-lookup"><span data-stu-id="2b6ca-491">I can't or don't want to use any secondary services</span></span>
<span data-ttu-id="2b6ca-492"><a name="bkmk_secondary"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-492"></span></span>

<span data-ttu-id="2b6ca-p184">次要服務是 Microsoft Office 365 控制項內不屬於。這些是之類的邊緣網路、 Azure 媒體服務及 Azure 內容傳遞網路。這些所有需要使用 Office 365，且必須是連至。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p184">Secondary services are Microsoft services that don't fall within Office 365 control. These are things like the edge network, Azure Media Services, and Azure Content Delivery Networks. These are all required to use Office 365 and must be reachable.</span></span>
  
<span data-ttu-id="2b6ca-496">如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-496">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="2b6ca-497">如何封鎖存取 Microsoft 的用戶服務？</span><span class="sxs-lookup"><span data-stu-id="2b6ca-497">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="2b6ca-498"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="2b6ca-498"></span></span>

<span data-ttu-id="2b6ca-p185">限制存取我們取用者服務應在您自己的風險、 封鎖取用者服務僅可靠方法是以限制存取*login.live.com* FQDN。這個 FQDN 可供廣泛的服務包括非消費者服務，例如 MSDN、 TechNet、 和其他人。限制存取至此 fqdn 可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-p185">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span> 
  
<span data-ttu-id="2b6ca-502">請記住封鎖存取 Microsoft 取用者服務來說不會阻止您網路上的某個人的能力 exfiltrate 使用 Office 365 租用戶或其他服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b6ca-502">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="2b6ca-503">相關主題</span><span class="sxs-lookup"><span data-stu-id="2b6ca-503">Related Topics</span></span>

[<span data-ttu-id="2b6ca-504">Microsoft Azure 資料中心 IP 範圍</span><span class="sxs-lookup"><span data-stu-id="2b6ca-504">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="2b6ca-505">Microsoft 公用 IP 空間</span><span class="sxs-lookup"><span data-stu-id="2b6ca-505">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="2b6ca-506">Microsoft Intune 的網路基礎結構需求</span><span class="sxs-lookup"><span data-stu-id="2b6ca-506">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="2b6ca-507">Power BI 和 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2b6ca-507">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="2b6ca-508">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="2b6ca-508">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="2b6ca-509">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="2b6ca-509">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="2b6ca-510">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="2b6ca-510">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
  

