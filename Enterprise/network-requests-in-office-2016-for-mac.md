---
title: Mac 版 Office 中的網路要求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office for Mac 的應用程式提供原生應用程式體驗 macOS 平台上。 每個應用程式被專為各種案例，包括沒有網路存取可用時的狀態。 當機器連線至網路時，應用程式自動連線至一系列的 web 服務來提供增強的功能。 本白皮書說明哪個端點和 Url 應用程式嘗試聯繫，以及所提供的服務。 疑難排解網路組態問題，以及設定網路 proxy 伺服器原則時，這項資訊非常有用。 指定與 Office 365 URL 和地址範圍文章旨在本文中的詳細資料。
ms.openlocfilehash: 09795ab15ba4a387dc53afea60c2d048d6ca9022
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844544"
---
# <a name="network-requests-in-office-for-mac"></a>Mac 版 Office 中的網路要求

Office for Mac 的應用程式提供原生應用程式體驗 macOS 平台上。 每個應用程式被專為各種案例，包括沒有網路存取可用時的狀態。 當機器連線至網路時，應用程式自動連線至一系列的 web 服務來提供增強的功能。 下列資訊說明哪個端點和 Url 應用程式嘗試聯繫，以及所提供的服務。 疑難排解網路組態問題並設定原則的網路 proxy 伺服器時，這項資訊非常有用。 本文中的詳細資料主要補充[Office 365 URL 與位址範圍文章](urls-and-ip-address-ranges.md)，其中包含執行 Microsoft Windows 的電腦的端點。 除非另有說明，本文資訊也適用於 Mac 版 Office 2019 和 Office 2016 for Mac，也就是可作為一次性購買從零售商店或透過大量授權合約。 

  
大部分是本文的資料表細部網路 Url、 類型及描述服務或該端點所提供的功能。 每個 Office 應用程式可能會不同其服務和端點的使用量。 下列應用程式定義表所示：
  
- 寫入： Word
- P: PowerPoint
- X: Excel
- O: outlook
- N OneNote
   
URL 類型定義如下：
  
- ST： 靜態-URL 是硬式編碼至用戶端應用程式。
    
- SS： 半靜態-URL 編碼為網頁或重新導向程式的一部分。
    
- CS: Config Service-URL 會傳回為 Office 設定服務的一部分。

    
## <a name="office-for-mac-default-configuration"></a>Office for Mac 預設組態

 **安裝和更新**
  
下列的網路端點可用來從 Microsoft 內容傳遞網路 (CDN) 下載 Office for Mac 的安裝程式。
  
|**URL**|**類型**|**描述**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Office 365 入口網站安裝此前導連結服務以最新安裝套件。  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |內容傳遞網路上的安裝套件的位置。  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |內容傳遞網路上的安裝套件的位置。  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Microsoft AutoUpdate 的管理控制端點  <br/> |
   
 **第一個應用程式啟動**
  
下列的網路端點，則會連絡在第一次啟動 Office 應用程式。 這些端點的使用者，提供增強的 Office 功能和 Url，則會連絡不論授權類型 （包括大量授權安裝）。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' 組態-允許功能光線向上鍵和試驗。  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' 的網路組態測試  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' 的網路組態測試  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 設定服務的主機服務端點的清單。  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 規則遙測下載-通知用戶端何種資料及上傳到遙測服務事件。  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote 遙測服務  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 遙測上傳報告-「 Heartbeart 」 及錯誤事件發生在用戶端上傳至遙測服務。  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office 範本 Service-為使用者提供線上文件範本。  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office 範本下載-PNG 範本映像的儲存空間。  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office 相關應用程式儲存區設定。  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office 文件整合服務目錄 （服務和端點的清單） 與首頁領域探索。  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |資源的首頁領域探索 v2 （15.40 和更新版本）  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate 資訊清單-檢查，請參閱是否有更新可用  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft 的 Ajax JavaScript 程式庫  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 應用程式的 Office 設定和資源。  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |適用於 Office 的組態和資源的 Bing 地圖應用程式。  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |人員圖形應用程式的 Office 設定和資源。  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |什麼是用於 OneNote 的新內容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |用於 OneNote 的新內容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |什麼是用於 OneNote 的新圖像。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |在 [應用程式支援服務。  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |電子郵件帳戶偵測服務。  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook 自動探索  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Office 365 服務的 outlook 端點。  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Outlook 增益集的圖示。  <br/> |
   
> [!NOTE]
> Office Configuration Service 作為自動探索服務的所有 Microsoft Office 用戶端，不只是 for mac。 回應中傳回的端點是以半靜態中變更為極少用，但仍可進行。 
  
 **登入**
  
下列的網路端點所連接時登入至雲端式儲存裝置。 根據您的帳戶類型，可能會連絡不同的服務。 例如：
  
- **MSA: Microsoft 帳戶**-通常用於家庭用戶與零售版的案例 
    
- **OrgID： 組織帳戶**-通常用於商業案例 
    
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows 授權服務  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office 365 登入服務 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 帳戶登入服務 (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft 帳戶登入服務協助程式 (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |品牌 (OrgID) 的 office 365 登入  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |文件和位置儲存定位器  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |大部分的最近使用 (MRU) 文件服務  <br/> |
   
> [!NOTE]
> 訂閱式和忮授權，登入兩者會啟動、 產品，並可讓您存取雲端資源，例如 OneDrive。 大量授權安裝，使用者仍提示登入 （預設），但是，只有當產品尚未啟動，所需的雲端資源的存取權。 
  
 **產品啟動**
  
下列的網路端點適用於 Office 365 訂閱和零售授權啟用。 具體而言，這不適用於大量授權安裝。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office 授權服務  <br/> |
   
 **什麼是新的內容**
  
下列的網路端點僅適用於 Office 365 訂用帳戶。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |什麼是新的 JSON 頁面內容。  <br/> |
   
 **研究工具**
  
下列的網路端點僅適用於 Office 365 訂用帳戶。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Researcher Web 服務  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Researcher 靜態內容  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Researcher 內容提供者  <br/> |
   
 **智慧查閱**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |深入了解 Web 服務  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery 程式庫  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |支援的 JavaScript 程式庫  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |深入了解內容提供者  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |深入了解內容提供者  <br/> |
   
 **PowerPoint 設計工具**
  
下列的網路端點僅適用於 Office 365 訂用帳戶。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint 設計工具 web 服務  <br/> |
   
 **PowerPoint 快速啟動工具**
  
下列的網路端點僅適用於 Office 365 訂用帳戶。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint 快速啟動工具 web 服務  <br/> |
   
 **傳送笑臉/皺眉頭**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |傳送笑臉服務  <br/> |
   
 **連絡客戶支援**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |連絡支援服務  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |在 [應用程式支援服務  <br/> |
   
 **另存為 PDF**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word 文件轉換服務 (PDF)  <br/> |
   
 **Office 應用程式 （也稱為增益集）**
  
Office 應用程式增益集受信任時，下列的網路端點會套用至 Office 365 訂閱和零售/大量授權啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office 應用程式儲存區設定  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 應用程式資源  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing 地圖應用程式資源  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |人員圖形應用程式資源  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office 重新導向服務  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office 的 JavaScript 程式庫  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |遙測及報告 Office 相關應用程式服務  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft 的 Ajax JavaScript 程式庫  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft 的 Ajax JavaScript 程式庫  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office 的 JavaScript 程式庫  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支援資源  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支援資源  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |支援資源  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript 程式庫  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |錯誤報告  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |字型的資源  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |遙測服務  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |遙測報告  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft 網上商店資產庫  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |維基百科頁面資源  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |維基百科媒體資源  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |維基百科沙箱圖文框  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |對應範本  <br/> |
   
 **安全連結**
  
下列的網路端點適用於所有 Office 應用程式的 Office 365 訂閱僅。
  
|**URL**|**類型**|**描述**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft 安全連結服務  <br/> |
   
 **當機報告**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用的所有 Office 應用程式。 當程序意外當機時，報表就會產生，並且傳送至 Watson 服務。
  
|**URL**|**類型**|**描述**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft 錯誤報告服務  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office 共同作業 Insights 服務  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>減少網路要求和流量的選項

Mac 版 Office 的預設組態提供最佳使用者經驗，包括類功能，並將機器保持最新狀態。 在某些情況下，您可能想要防止從連絡網路端點的應用程式。 本章節將討論這樣的選項。
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>停用雲端登入和 Office 增益集
  
大量授權客戶可能需要將文件儲存到雲端式存放裝置相關嚴格的原則。 下列每個應用程式喜好設定可以設定為停用 MSA/OrgID 登入，並存取 Office 增益集。
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

如果使用者嘗試存取登入函式，他們會看到錯誤的網路連線不存在。 因為這個喜好設定也會封鎖線上產品啟用，則應僅用於大量授權安裝。 具體而言，使用這個喜好設定將會導致 Office 應用程式存取下列端點：
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 在上述 ' 登入 」 一節中所列的所有端點。
    
- 上述 ' 智慧查閱 」 一節中所列的所有端點。
    
- 上述 ' 產品啟用 」 一節中所列的所有端點。
    
- 上述 ' Office 應用程式 （也稱為增益集） 」 一節中所列的所有端點。
    
若要重新建立使用者的完整功能，請將為 '2' 的喜好設定或移除它。
  
> [!NOTE]
> 這個喜好設定需要 Office for Mac 組建 15.25 [160726] 或更新版本。 
  
### <a name="telemetry"></a>遙測
  
Mac 版 office 會定期將遙測資訊傳送回給 Microsoft。 資料上傳至 '關係' 的端點。 遙測資料可協助評估健康狀況和每個 Office 應用程式的任何非預期的行為工程團隊。 有兩個類別的遙測：
  
- **活動訊號**包含版本及授權資訊。 此資料會在應用程式啟動時立即傳送。 
    
- **Usage**包含應用程式的使用方式的資訊和非嚴重錯誤。 此資料會傳送每 60 分鐘。 
    
Microsoft 會非常重視帶您的隱私權。 您可以了解 Microsoft 的資料收集原則在[https://privacy.microsoft.com](https://privacy.microsoft.com)。 若要防止傳送 '流量' 遙測的應用程式，可以調整**SendAllTelemetryEnabled**喜好設定。 喜好設定為每個應用程式，並可透過 macOS 設定設定檔，或以手動方式從 Terminal 設定： 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

活動訊號遙測一律傳送，且無法停用。
  
### <a name="crash-reporting"></a>當機報告
  
發生嚴重的應用程式錯誤時，應用程式會意外終止，並將當機報告的上傳到 'Watson' 服務。 當機報告包含呼叫堆疊，也就是應用程式已處理導致當機的步驟清單。 這些步驟協助找出失敗的確切函數工程團隊和原因。
  
在某些情況下，文件的內容會導致應用程式損毀。 如果應用程式識別文件為原因，它會詢問使用者是否可以也傳送文件，以及呼叫堆疊。 使用者可以做出明智的選擇這個問題。 IT 系統管理員可能會有關於傳輸的文件的嚴格需求，並讓使用者代表的決策，永遠不會傳送文件。 可以設定下列的喜好設定，以防止文件傳送，並隱藏使用者提示：
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> 如果**SendAllTelemetryEnabled**設為**FALSE**，所有損毀報告的已停用程序。 若要啟用損毀而不傳送流量遙測報告，您可以設定下列的喜好設定：```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>更新
  
Microsoft 發行 Office for Mac 更新固定時間間隔 （通常是一次一個月）。 我們強烈鼓勵使用者與 IT 系統管理員將機器保持在最新狀態以確保最新的安全性修正程式已安裝。 在 IT 系統管理員想要嚴密控制和管理機器更新的情況下，下列的喜好設定可以設定為防止從自動偵測並提供產品更新 AutoUpdate 程序：
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>封鎖防火牆/Proxy 要求
  
如果您的組織封鎖 url 要求透過防火牆或 proxy 伺服器是設定為 [不允許此文件中列出的 Url 或封鎖，請務必列出 40 X 回應 （例如 403 或 404）。 40 X 回應可讓 Office 應用程式，可依正常程序接受無法存取的資源，並將提供更快的使用者體驗，請比只需卸除的連線，進而導致用戶端重試。
  
如果您的 proxy 伺服器需要驗證，407 回應將會傳回給用戶端。 為最佳使用體驗，請確定您使用 Office for Mac 組建 15.27 或更新版本，因為這些包括使用 NTLM 和 Kerberos 伺服器特定的修正程式。
  
  
## <a name="see-also"></a>另請參閱

[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md)

