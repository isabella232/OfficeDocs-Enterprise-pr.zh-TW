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
# <a name="managing-office-365-endpoints"></a>管理 Office 365 端點

## <a name="office-365-network-connectivity"></a>Office 365 網路連線

 連線至 Office 365 包含高數量，受信任的網路要求他們正在進行透過接近使用者低延遲輸出時最適合執行。某些 Office 365 的連線可以獲益最佳化連線。 
  
1. 確定防火牆允許清單允許連線到 Office 365 端點。
    
2. 若要允許透過網際網路連線到萬用字元及解除發佈目的地的電話使用 proxy 基礎結構。
    
3. 維護最佳的周邊網路組態。
    
4. [確定您要取得最佳的連線](https://aka.ms/o365perfprinciples)。
    
5. 請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。 
    
![透過防火牆及 proxy 連線至 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>更新的輸出防火牆允許清單

您可以藉由傳送的所有受信任直接透過防火牆的 Office 365 網路要求、 略過所有其他的封包層級檢查或處理最佳化您的網路。這可減少從延遲的效能低落並減少周邊容量需求。選擇 [建立信任關係要求的網路最簡單的方法是使用上述**Proxy** ] 索引標籤上的我們預先建置的 PAC 檔案。 
  
如果您防火牆封鎖輸出流量會想要確保所有 IP 和 Fqdn 列為此[XML 檔案](https://go.microsoft.com/fwlink/?LinkId=533185)中**所需**的 [允許] 清單上。辨識所有服務都需要使用一些 3rd 廠商服務。我們不提供的憑證提供者、 內容傳遞網路、 DNS 提供者，例如這些 3rd 廠商服務的 IP 位址等等。完整 Office 365 功能，您必須能夠抵達所有要求的 Office 365 不論多少資訊我們發佈目的地的目的地。 
  
許多目的地沒有發佈 IP 位址或列為 「 無特定的完整的網域名稱萬用字元網域，請使用這項功能您必須能夠解析這些網路要求，以目前的 IP 位址要求以及傳送透過網際網路的網路要求。
  
使用防火牆會剖析代替您撥打電話之 XML 檔案，更新規則會自動根據服務或功能想要路由傳送直接透過防火牆自動化您的程序。您也可以使用[Azure 範圍](https://azurerange.azurewebsites.net/)工具已由社群建立且會為您的 XML 剖析 Cisco XE 路由或 ACL 清單組態、 純文字或 CSV 匯出選項。 
  
讓您可以變更訂閱透過[RSS 根據變更記錄](https://go.microsoft.com/fwlink/p/?linkid=236301)我們使用我們[參考 （英文） 網站](urls-and-ip-address-ranges.md)上的網路目的地的較長的說明。 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>設定 PAC 檔輸出路徑

用於管理 Office 365 與相關聯，但沒有提供 IP 位址的網路要求 PAC 或 WPAD 檔案。透過 proxy 或周邊裝置傳送的一般網路要求可能會形成額外的延遲。雖然 proxy 驗證會帶來最大稅，其他服務，例如信譽查閱和嘗試檢查封包可能會造成不良的使用者經驗。此外，這些周邊網路裝置需要足夠的容量來處理所有網路要求。我們建議略過您直接的 Office 365 網路要求的 proxy 或檢查基礎結構。
  
使用下列其中一個我們 PAC 檔案的起始位置為決定何種網路流量會傳送至 proxy 和其就會傳送給防火牆。如果您是 PAC 或 WPAD 檔案，從一個適用的 Office 365 顧問閱讀此文章[部署 PAC 檔案](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/)的相關的新功能。想要檢閱這些開始進行並編輯以符合您的環境。 
  
 **更新 7/10/2018 PAC 檔案**。 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1-PAC 檔案： 隔開需要網際網路從已知的 Office 365 FQDN 的 Fqdn。

第一個範例是透過網際網路僅管理端點我們建議方法的示範。略過 Office 365 目的地 IP 位址其中發佈而將剩餘的網路要求傳送至 proxy 的 proxy。
  
程式碼片段：
  
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

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2-PAC 檔案： 透過網際網路和 ExpressRoute 連線到 Office 365
<a name="bkmk_inet-aer"> </a>

第二個範例是方法的我們建議有 ExpressRoute 和網際網路電路時管理連線的示範。傳送 ExpressRoute 通告 ExpressRoute 電路的目的地及網際網路只通告 proxy 的目的地。
  
程式碼片段：
  
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

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3-PAC 檔案： 分別表示管理所有 Office 365 目的地
<a name="bkmk_inet-direct"> </a>

第三個範例會示範如何將傳送至單一目的地與 Office 365 相關聯的所有網路要求。這通常用來略過的 Office 365 網路要求的所有檢查並提供您所有已發佈端點的格式是在清單中要用於您的自訂 PAC 格式。
  
程式碼片段：
  
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

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>使用自訂指令碼或手動建立自己的 PAC 檔案
<a name="pacfiles_manual"> </a>

以下是一些社群的更多工具如果您已建立您想要共用離開的某個項目中的註解的附註。無的社群工具本文中所參照的正式支援或 microsoft 維護，而且您的方便這裡提供。
  
- 這是最早社群產生工具來協助管理程序的 Office 365 社群成員的內建的工具。以下是[下載](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)的連結。
    
- 概念證明具有可匯出的防火牆規則： [Microsoft Cloud IP API](https://mscloudips.azurewebsites.net/)。
    
- [從 IT Praktyk: RSS 轉換](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7)和[XML 轉換](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)。
    
- 從 Peter Abele：[下載](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)。
    
- 使用網路分析來判斷其網路要求應該略過 proxy 基礎結構。若要略過客戶 proxy 所使用的最常見 Fqdn 如下所示因網路流量傳送和接收來自這些端點數量。
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  
  ```

- 確定直接傳送到您的防火牆的所有網路要求都有相對應項目在防火牆允許允許透過要求的清單。
    
## <a name="perimeter-network-integration"></a>周邊網路整合
<a name="BKMK_Perimeter"> </a>

您知道 Microsoft 的 WAN 是其中一個世界中的最大或骨幹吗？
  
它會是 true，這個大規模的網路是何謂 Office 365 並在您的世界不論 where 工作我們其他雲端服務。我們網路組成高頻寬、 低延遲、 容錯移轉能力連結與千分位私下擁有的深色光纖和資料中心及 edge 節點，所有以方便使用我們 cloud services 之間的多個 Tb 連線路由哩的分數。
  
使用類似的網路中，您想貴組織的裝置盡連線到我們的網路。超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好並不那麼良好對等手掌核我們的網路。 
  
您可以手動或自動設定以最佳方式處理 Office 365 應用程式網路要求，視您的設備網路上的裝置。您需要對以最佳方式處理 Office 365 的網路流量進行哪些設定變更取決於您的環境。Office 365 網路要求可能獲益允許下列的網路設定：
  
- 透過較不重要的網路流量的優先順序。
    
- 路由傳送至本機的輸出透過慢速 WAN 避免 backhauling 時利用 Microsoft 網路上可用的低延遲的連結。[以下是很好的討論區](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/)的客戶投入為基礎。 
    
- 使用本機輸出附近的 DNS 以確保離開本機輸出網路要求到達最接近的 Microsoft 對等的位置。
    
- 從深入的封包檢查或符合規模的延遲需求處理其他密集的網路封包排除。
    
摩登的網路裝置包括一般、 不受信任的網際網路流量不同管理網路要求受信任應用程式，例如 Office 365 的功能。SD WAN 解決方案之新入門、 使用的網路，例如點時間可用性、 延遲或效能的各種連線路徑中的變更狀態認知也可用執行流量及路徑的選取範圍的這類區別之間的使用者與雲端。
  
請參閱規劃您的網路設定的其他指導[網路和 Office 365 規劃移轉](network-and-migration-planning.md)、[效能疑難排解 Office 365 的規劃](performance-troubleshooting-plan.md)和[部署 Office 365 規劃檢查清單](deployment-planning-checklist.md)。 
  
### <a name="to-implement-this-scenario"></a>若要實作此案例：

如果他們可以使用 Office 365 URL 和 IP 定義從 xml 轉換成便利負荷本機 （使用者）、 低網路輸出的 Office 365 流量、 管理其優先順序相對於其他應用程式及調整] 核取您的網路解決方案或服務提供者Office 365 連線到 Microsoft network 根據變更網路狀況的網路路徑。某些解決方案下載及自動化 Office 365 URL 和 IP XMLs 定義其堆疊中。
  
永遠確定已實作的解決方案具有必要程度恢復] 中的 Office 365 流量的網路路徑的適當地理備援當他們成為發佈至 Office 365 Url 和 Ip 變更所能容納。
  
## <a name="web-service"></a>Web 服務
<a name="webservice"> </a>

為了協助您更妥善地識別及區分不同 Office 365 網路流量，新的 web 服務會發佈 Office 365 端點，讓您評估、 設定及保持最新變更更容易。這個新的 web 服務 （現在存在於 preview) 最後將會取代中[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)的文章，以及該資料的 RSS 和 XML 版本的端點清單。分階段進行上 2018 年 10 月 2、 預計端點資料這些格式。 
  
為客戶或網路周邊裝置廠商，您可以建置對新的 rest web 服務的 Office 365 IP 位址和 FQDN 項目。
  
- Office 365 Url 和 IP 位址範圍的最新版本，使用[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
    
- 在 Office 365 Url 和 IP 位址範圍] 頁面上的防火牆及 proxy 伺服器上的資料、 使用[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
    
- 若要取得最新變更，請使用[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)。
    
為客戶，您可以使用此 web 服務： 
  
- 更新您的 PowerShell 指令碼取得 Office 365 端點資料並修改您的網路裝置任何格式設定。
    
- 使用此資訊來更新 PAC 檔案部署至用戶端電腦。
    
為網路周邊裝置廠商，您可以使用此 web 服務： 
  
- 建立和測試裝置的軟體下載自動設定的清單。 
    
- 檢查目前的版本。
    
- 取得目前的變更。
    
下列各節說明此 web 服務、 可能會變更一段時間直到服務通常可用的預覽。 
  
在 web 服務的資料是最新及我們不打算變更進一步的 web 服務 Url 或傳回此 web 服務的一般可用性發行前的資料結構描述。
  
如需其他資訊，請參閱：
  
- [在 Office 365 Tech 社群論壇中宣告部落格文章](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
    
- [如需使用 web 服務的問題的 office 365 Tech 社群論壇](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
    
### <a name="common-parameters"></a>一般參數

這些參數彼此一般跨所有 web 服務方法：
  
- **格式 = CSV |JSON** -查詢字串參數。根據預設，傳回的資料格式為 JSON。包含此選用參數，以傳回的資料以逗點分隔值 (CSV) 格式。 
    
- **ClientRequestId** -查詢字串參數。您的用戶端工作階段關聯產生必要的 GUID。您應該產生每個用戶端電腦可呼叫 web service 的 GUID。請勿使用因為它們可能會被封鎖的 web 服務未來在下列範例所示的 Guid。GUID 格式為 xxxxxxxx-是-是-是-xxxxxxxxxxxx，其中 x 代表十六進位數字。若要產生的 GUID，使用 [[新增 Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell 命令。 
    
### <a name="version-web-method"></a>版本 web 方法

Microsoft 更新的 Office 365 IP 位址和 FQDN 項目的結尾的每個月及有時會登出週期操作或支援需求。每個已發佈的執行個體的資料會指派版本號碼。版本 web 方法可讓您針對每個 Office 365 服務執行個體的最新版本會輪詢有無。我們建議您在每日、 或最、 每小時檢查版本。
  
有一個版本 web 方法的參數：
  
- **AllVersions = true** -查詢字串參數。根據預設，傳回的版本是最新。包含此選用參數，以要求所有發佈的版本。 
    
- **執行個體**-Route 參數。此選用參數會指定要傳回之版本的執行個體。如果省略，則會傳回所有執行個體。有效的執行個體： 全球性、 中國、 德國、 USGovDoD、 USGovGCCHigh 
    
版本 web 方法的結果可能是單一記錄的陣列。每筆記錄中的元素包括：
  
- 執行個體-Office 365 服務執行個體的簡短名稱。
    
- 最新-指定執行個體的端點之最新版本。
    
- 版本-指定執行個體的所有先前版本的清單。此元素是只包含如果 AllVersions 參數，則為 true。
   
#### <a name="examples"></a>範例：
  
範例 1 要求 URI: ** <span>https:</span>//endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
此 URI 會傳回最新版的每個 Office 365 服務執行個體。範例結果：
  
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
> 在這些 Uri ClientRequestID 參數的 GUID 是僅限範例。若要嘗試 web 服務 Uri 取出、 產生自己的 GUID。以下範例所示的 Guid 可能會遭到封鎖 web 服務所未來。 
  
範例 2 要求 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
此 URI 會傳回指定的 Office 365 服務執行個體的最新版本。範例結果：
  
```
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

範例 3 要求 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
此 URI CSV 格式顯示輸出。範例結果：
  
```
instance,latest
Worldwide,2018063000
```

範例 4 要求 URI: ** <span>https:</span>//endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
此 URI 會顯示已發佈的 Office 365 全世界的服務執行個體的所有先前版本。範例結果：
  
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

### <a name="endpoints-web-method"></a>端點 web 方法

端點 web 方法會傳回所有記錄的 IP 位址範圍及構成 Office 365 服務的 Url。端點 web 方法的參數為：
  
- **ServiceAreas** -查詢字串參數。服務區域以逗號分隔清單。有效的項目是一般、 Exchange、 SharePoint、 Skype。因為常見的服務] 區域中項目的所有其他服務區域的先決條件、 web 服務將會一律包含它們。如果您未包含此參數，會傳回所有服務區域。 
    
- **TenantName** -查詢字串參數。您的 Office 365 租用戶名稱。Web 服務會提供的名稱並且將它插入的租用戶名稱包含 Url 的組件中。如果您沒有提供的租用戶名稱、 Url 的這些組件已萬用字元 (\*)。 
    
- **NoIPv6** -查詢字串參數。將此設為 true 是表示排除 IPv6 位址從輸出，例如，如果您未在您的網路中使用 IPv6。 
    
- **執行個體**-Route 參數。這個必要的參數會指定要傳回之端點的執行個體。有效的執行個體： 全球性、 中國、 德國、 USGovDoD、 USGovGCCHigh。 
    
端點 web 方法的結果是含有代表端點設每一筆記錄的記錄的陣列。針對每個記錄項目包括：
  
- 識別碼-端點不變的識別碼號碼設定。
    
- serviceArea-這是一部分的 [服務] 區域： 一般、 Exchange、 SharePoint、 或 Skype。
    
- url-端點的 Url 設定。DNS 記錄的 JSON 陣列。省略如果空白。
    
- tcpPorts-端點的 TCP 連接埠設定。連接埠的所有項目全都設為逗點分隔的連接埠] 或 [連接埠範圍以虛線字元 （-） 分隔清單。連接埠適用於所有 IP 位址及所有 Url，因為端點該類別的設定。省略如果空白。
    
- udpPorts-UDP 連接埠的 IP 位址在此端點集合中的範圍。省略如果空白。
    
- ip-這個設定如下所列的 TCP 或 UDP 連接埠相關聯的端點相關聯的 IP 位址範圍。省略如果空白。
    
- 類別-端點的 [連線] 類別設定。有效值為最佳化、 允許、 及預設值。所需。
    
- expressRoute-True 或 False 時，此端點集傳閱透過 ExpressRoute。
    
- 必要-True 如果此端點集需要具備才支援的 Office 365 的連線。若為 false，則省略。
    
- 備忘稿-選用端點此文字會說明若 IP 位址會遺失的 Office 365 功能或 Url 中此端點集無法存取網路層級。省略如果空白。
    
#### <a name="examples"></a>範例：
  
範例 1 要求 URI: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
此 URI 會取得所有工作量的 Office 365 全世界執行個體的所有端點。顯示輸出摘錄的範例結果：
  
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

其他端點設定並不包含在此範例中。
  
範例 2 要求 URI: ** <span>https:</span>//endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId = b10c5ed1-bad1-445f-b386-b919946339a7**
  
此範例會針對 Exchange Online 與相依性只取得端點之 Office 365 全世界的執行個體。
  
例如 2 的輸出是類似於範例 1 除了結果將不會包含端點的 SharePoint Online 或 Skype 商務 online。
  
### <a name="changes-web-method"></a>變更 web 方法

變更 web 方法會傳回最新版更新已發佈。這通常是 IP 位址範圍及 Url 的上個月的變更。
  
> [!NOTE]
> 會在預覽正確及應僅可用於開發和測試從 API 的變更資料。 
  
變更 web 方法的參數是：
  
- **版本**-所需的 URL route 參數。您目前已實作，而且您想要查看該版以來的變更項目的版本。格式為 YYYYMMDDNN。 
    
變更 web 方法的結果是代表特定版本的端點中變更的每筆記錄與記錄的陣列。針對每個記錄項目包括：
  
- id-不變的變更記錄的識別碼。
    
- endpointSetId-端點的識別碼設為已變更的記錄。所需。
    
- 處理-這可以是的變更、 新增或移除並說明變更沒有端點組記錄。
    
- 版本-設定中已採用變更的已發佈端點的版本。版本號碼是的 YYYYMMDDNN，其中 NN 是遞增有自然數字格式的多個版本才能發佈單一的日期。
    
- 前一層子結構細部先前的端點上變更元素的值設定。這不會包含新加入的端點設定。包含 tcpPorts、 udpPorts、 ExpressRoute、 類別、 所需、 備忘稿。
    
- 目前-子結構細部更新 endpoinset 上變更項目的值。包含 tcpPorts、 udpPorts、 ExpressRoute、 類別、 所需、 備忘稿。
    
- 新增-細部項目新增至端點 sub 結構設定集合。如果不有任何新增，省略。
    
  - effectiveDate-定義資料時新增的項目將會是 live 服務中。
    
  - ip-要新增至 ip 陣列項目。
    
  - url-項目加入至 url 的陣列。
    
- 移除-子結構細部從端點集合中移除的項目。如果不有任何移除，省略。
    
  - ip-要移除 ip 陣列中的項目。
    
  - 從 url 陣列中移除的 url 項。
    
 **範例：**
  
範例 1 要求 URI: ** <span>https:</span>//endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
這會要求所有舊版的 Office 365 全世界的服務執行個體變更。範例結果：
  
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

範例 2 要求 URI: ** <span>https:</span>//endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7**
  
這會要求變更後的指定版本的 Office 365 全世界的執行個體。在此例中指定的版本是最新。範例結果：
  
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

### <a name="example-powershell-script"></a>範例 PowerShell 指令碼

以下是您可以執行以查看是否有的動作所需的更新資料的 PowerShell 指令碼。此指令碼會檢查 Office 365 全世界的執行個體端點的版本號碼。變更時，它會下載端點和篩選的"Allow"和"最佳化"類別端點。它也使用跨多個通話的唯一 ClientRequestId 並儲存在暫存檔案中找到最新版本。您應該要檢查版本更新的呼叫此指令碼一次一小時。
  
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

### <a name="example-python-script"></a>範例 Python 指令碼

以下是 Python 指令碼、 測試與 Python 3.6.3 上 Windows 10，您可執行以查看是否有您需要更新的資料所採取的動作。此指令碼會檢查 Office 365 全世界的執行個體端點的版本號碼。變更時，它會下載端點和篩選的"Allow"和"最佳化"類別端點。它也使用跨多個通話的唯一 ClientRequestId 並儲存在暫存檔案中找到最新版本。您應該要檢查版本更新的呼叫此指令碼一次一小時。
  
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

### <a name="web-service-interface-versioning"></a>Web 服務介面版本設定

會更新以參數或這些 web 服務方法的結果可能需要未來。發佈這些 web 服務的一般可用版本之後，Microsoft 會使合理致力於提供之 web 服務的材料更新換頁通知。當 Microsoft 相信更新需要變更用戶端中使用 web 服務時、 Microsoft 會保持至少十二 （12） 月之後版本的新版本可用的 web 服務的舊版本 （回一個版本）。不要升級的時間期間的客戶可能無法存取 web 服務和它的方法。客戶必須確定 web 服務用戶端繼續運作不會發生錯誤如果至 web 服務介面簽章會進行下列變更：
  
- 將新的選用參數新增至現有的 web 方法都不會有以舊版用戶端所提供且不會影響結果的較舊的用戶端收到。
    
- 將新的具名的屬性的其中一個回應其餘項目或其他欄新增以回應 CSV。
    
- 新增新的 web 方法不由較舊的用戶端呼叫的新名稱。
    
## <a name="faq"></a>常見問題集

常見問題集管理員連線的相關問題：
  
### <a name="how-do-i-submit-a-question"></a>如何提交問題？

按一下以指出本文若已有幫助下方的連結並送出任何其他問題。我們監視意見反應及使用最常見問題集更新的問題。
  
### <a name="when-is-the-xml-file-updated"></a>更新之 XML 檔案的時機

當新端點即已宣佈時、 有通常是 30 + 天緩衝區它們有效與網路要求開始移至其之前。此緩衝區是以確保客戶和合作夥伴有機會來更新其系統。FQDN 和 IP 首碼新增和移除當做宣告，這表示新的 FQDN 將 XML 檔案中使用前 30 天內同時處理 XML 檔案中。因為我們停止傳送到我們要移除前公告其移除，當我們會移除之端點的 XML，同時當做宣告的端點的網路要求就會已經未使用。
  
### <a name="how-can-i-be-notified-of-changes"></a>可以使用要接收通知的方式變更的？
<a name="bkmk_changes"> </a>

Office 365 端點發佈結尾處的每個月 30 天的通知。有時會變更就會發生一次以上一個月或更短的通知期間使用。當加入端點時，列出的[RSS 摘要](https://go.microsoft.com/fwlink/p/?linkid=236301)的有效日期是要在其後網路要求將會傳送到端點的日期。如果您是新 rss，以下是如何[訂閱透過 Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416)或您可以[有 RSS 摘要更新傳送給您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。
  
### <a name="how-do-i-read-the-rss-change-log"></a>如何讀取 RSS 變更記錄檔
<a name="bkmk_changes"> </a>

訂閱 rss 摘要之後，您可以剖析資訊自行或以指令碼。下表說明格式的 rss 摘要 o 讓更容易。
  
|**區段**|**第 1 部分**|**第 2 部分**|**第 3 部分**|**第 4 部分**|**第 5**|**第 6**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**描述** <br/> |數目  <br/> |之後，您可以預期傳送給端點的網路要求的日期。  <br/> |基本的功能或服務所需之端點的詳細描述。  <br/> |您可以連線到此端點除了網際網路 ExpressRoute 電路上吗？  <br/> |**Yes** -您可以連線到此端點上的網際網路和 ExpressRoute。  <br/> [**否**]-您只可以連線至網際網路上這個端點。  <br/> |目的地正在新增或移除的 FQDN 或 IP 範圍。  <br/> |
|**範例** <br/> |1 /  <br/> |[有效 xx/xx/xxx。  <br/> |必要：\<描述\>。  <br/> |ExpressRoute：  <br/> |\<是/否\>。  <br/> |\<FQDN/IP\>]，  <br/> |
   
注意，每個項目有一組通用的分隔字元其他的一些事項：
  
- **/**-之後計數 
    
- **[** -指出項目計數 
    
- **.**-使用傳來的項目每個不同區段 
    
- **]、** -表示單一項目結尾 
    
- **].**-若要指出結尾的所有項目 
    
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何判斷我租用戶的位置？

 最適合使用我們的[資料中心對應](https://o365datacentermap.azurewebsites.net/)來判定**租用戶位置**。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Am I 對等適當地向 Microsoft 吗？

 在[具有 Microsoft 對等](https://www.microsoft.com/peering)的更詳細地說明**Peering 位置**。
  
超過 2500 ISP 對等相關聯全域和 70 點的目前狀態、 易於從您的網路是我們應該相當順暢。無法傷害花費數分鐘確定您的 ISP 對等關係最最佳[以下是一些範例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好並不那麼良好對等手掌核我們的網路。 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>如何判斷哪些 IP 位址來接受透過 ExpressRoute？

 [Microsoft 的 IP 範圍](https://www.microsoft.com/download/details.aspx?id=53602)及特定的 Office 365 [BGP 社群 （英文）](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)會定義**接受 ExpressRoute 路由**。
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>如何判斷我需要哪些端點？

我們定期新增新的功能與服務至 Office 365 套件中，展開連線橫向。如果您正在訂閱 E3 或 E5 SKU，要考量的端點清單簡易的方式是您需要所有這些套件以取得完整的功能。如果您未訂閱至這些 Sku 其中一項不同的是最少的端點數目。
  
請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)取得 Office 365 端點類別的詳細資訊並了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。 
  
在下列影像中，您可以看到 FQDN 資料表的 Office Online] 區段中的部分範例。資料列會依據功能及連線的差異。前兩列表示上標示之端點的設定依賴 Office Online 中的 Office 365 驗證及身分識別和入口網站所需與共用章節。這是一般內以這些共用服務所依賴的 Office 365 服務。第三列會指出用戶端電腦必須能夠抵達\*。 使用 Office Online 和第四列的 officeapps.live.com 表示電腦也必須能夠抵達\*。 若要使用 Office Online cdn.office.net。
  
雖然兩者第三列及四才能使用 Office Online，他們已經已分隔表示目的地是不同：
  
1. \*。 officeapps.live.com 並非 CDN、 此命名空間的這表示要求會直接移至 Microsoft 資料中心。
    
2. \*。 officeapps.live.com 是使用 Microsoft Peering ExpressRoute 電路上存取。
    
3. Office Online 相關聯的 IP 位址和\*。 officeapps.live.com 可以找到遵循此連結。
    
4. \*。 cdn.office.net 代表 CDN 主控的 Akamai、 此命名空間的這表示要求會前往 Akamai 資料中心。
    
5. \*。 cdn.office.net 不是在 ExpressRoute 電路可存取。
    
6. Office Online 相關聯的 IP 位址和\*。 cdn.office.net 不提供。
    
![端點] 頁面的螢幕擷取畫面](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>不是在 [發佈] 清單上查看 IP 位址的網路要求，我需要提供存取備份吗？
<a name="bkmk_MissingIP"> </a>

我們只會提供您應直接路由傳送至網際網路或 ExpressRoute 上的 Office 365 伺服器的 IP 位址。這不是所有您會看見網路要求的 IP 位址的完整清單。您會看見網路要求，以查看 Microsoft 及協力廠商擁有、 已解除發佈、 IP 位址。這些 IP 位址為動態產生或受管理的這些變更時防止及時通知的方式。如果您的防火牆不允許存取這些網路要求的 fqdn 均為基礎，可用於 PAC 或 WPAD 檔案管理要求。
  
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

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>什麼是 Office 365 端點的三種類型？
<a name="bkmk_akamai"> </a>

- 您連線至擷取如 DNS 查詢及 CDN 內容擷取的基本網際網路服務的協力廠商服務。您也連線至協力廠商服務如合併 YouTube 影片 OneNote 筆記本中的整合功能。
    
- 您連線至次要服務主控與執行 microsoft 如 edge 節點可讓您的網路要求的最接近的網際網路位置的 Microsoft 通用網路輸入到您的電腦。為金星上第三個最大網路，這可改善連線經驗。您也連線至 Microsoft Azure 服務，例如 Azure 媒體服務所用的各種 Office 365 服務。
    
- 您連線至主要 Office 365 服務，例如 Exchange Online 信箱伺服器或 Skype 商務線上唯一與專屬資料所在的伺服器。您可以連線至主要的 Office 365 服務 FQDN 或 IP 位址並使用網際網路或 ExpressRoute 電路。您只可以連線到第三方與網際網路電路上使用 Fqdn 的次要服務。
    
下圖顯示這些服務區域之間的差異。此圖表中左下角的客戶在內部網路具有多個網路裝置來協助管理網路連線。這種方式的設定都通用的企業客戶。如果您的網路只有用戶端電腦與網際網路，也支援，之間的防火牆，而且會想要確保您的防火牆可以允許清單規則中支援 Fqdn 和萬用字元。
  
請閱讀[Office 365 網路連線原則](office-365-network-connectivity-principles.md)取得 Office 365 端點類別的詳細資訊並了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。 
  
![使用 Office 365 時顯示三種不同類型的網路端點](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>我無法或不想要使用任何協力廠商的服務
<a name="bkmk_thirdparty"> </a>

Office 365 是一組透過網際網路內建函數的服務、 可靠性與可用性的承諾根據所提供的許多標準網際網路服務。例如，如 DNS、 CRL、 及 Cdn 標準網際網路服務必須使用 Office 365 就如同他們必須使用最現代網際網路服務連至連至。
  
除了這些基本的網際網路服務、 有協力廠商所使用服務的僅限整合功能。例如，使用中的 Microsoft 小組 Giphy.com 可讓客戶順暢地包含 Gif 小組中。同樣地，YouTube 和 Flickr 是用來將視訊及圖像順暢地整合至 Office 用戶端從網際網路的協力廠商服務。雖然這些所需的整合，它們被標示為選用這表示核心功能的服務會繼續運作如果端點不是可存取 Office 365 端點文章中。
  
如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>我無法或不想要使用任何次要服務
<a name="bkmk_secondary"> </a>

次要服務是 Microsoft Office 365 控制項內不屬於。這些是之類的邊緣網路、 Azure 媒體服務及 Azure 內容傳遞網路。這些所有需要使用 Office 365，且必須是連至。
  
如果您正在嘗試使用 Office 365 及尋找協力廠商服務都可以存取您將想要[確定透過 proxy 和防火牆允許所有標示為必要或選用本文中的 Fqdn](urls-and-ip-address-ranges.md)。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何封鎖存取 Microsoft 的用戶服務？
<a name="bkmk_consumer"> </a>

限制存取我們取用者服務應在您自己的風險、 封鎖取用者服務僅可靠方法是以限制存取*login.live.com* FQDN。這個 FQDN 可供廣泛的服務包括非消費者服務，例如 MSDN、 TechNet、 和其他人。限制存取至此 fqdn 可能會導致需要也包含這些服務相關聯的網路要求規則的例外狀況。 
  
請記住封鎖存取 Microsoft 取用者服務來說不會阻止您網路上的某個人的能力 exfiltrate 使用 Office 365 租用戶或其他服務的資訊。
  
## <a name="related-topics"></a>相關主題

[Microsoft Azure 資料中心 IP 範圍](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公用 IP 空間](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的網路基礎結構需求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI 和 ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md)
  
[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)
  
[Office 365 網路連線原則](office-365-network-connectivity-principles.md)
  

