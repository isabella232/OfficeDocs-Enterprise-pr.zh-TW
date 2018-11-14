---
title: Office for Mac 中的網路要求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office for Mac 應用程式提供 macOS 平台上的原生 app 經驗。每個應用程式的設計在各種案例，包括狀態時沒有網路存取權是可用的工作。當電腦連線至網路時，應用程式自動連線至一系列的 web 服務來提供增強的功能。此白皮書說明的端點和連絡，嘗試應用程式的 Url 及提供的服務。此資訊在疑難排解網路組態問題和設定網路 proxy 伺服器的原則時很有用。指定與 Office 365 URL 和地址範圍文章旨在本文中的詳細資料。
ms.openlocfilehash: 929b93433f5d990952b540a1b28fe2ac74edfb5d
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219893"
---
# <a name="network-requests-in-office-for-mac"></a>Office for Mac 中的網路要求

Office for Mac 應用程式提供 macOS 平台上的原生 app 經驗。每個應用程式的設計在各種案例，包括狀態時沒有網路存取權是可用的工作。當電腦連線至網路時，應用程式自動連線至一系列的 web 服務來提供增強的功能。下列資訊說明的端點和連絡，嘗試應用程式的 Url 及提供的服務。此資訊在疑難排解網路組態問題和網路 proxy 伺服器的設定原則時很有用。本文中的詳細資料都是要輔助[Office 365 URL 和地址範圍文章](urls-and-ip-address-ranges.md)，其中包含執行 Microsoft Windows 的電腦的端點。除非另有說明，本文中的資訊也適用於 Office 2019 for Mac 和 Office 2016 for Mac，可用以一次性購買零售商店或透過大量授權合約。 

  
充分運用本文是資料表細部網路 Url、 類型及描述服務或該端點所提供的功能。每個 Office 應用程式可能會不同服務和端點使用方式。下列應用程式定義表所示：
  
- W: Word
- P： PowerPoint
- X: Excel
- O outlook
- N OneNote
   
URL 類型定義如下：
  
- ST： 靜態-URL 是硬式編碼到用戶端應用程式。
    
- SS： 分號靜態-URL 編碼為網頁或重新導向程式的一部分。
    
- CS： Config Service-URL 會傳回 Office 設定服務的一部分。

    
## <a name="office-for-mac-default-configuration"></a>Office for Mac 預設設定

 **安裝和更新**
  
若要下載 Office for Mac 安裝程式從 Microsoft 內容傳遞網路 (CDN) 可用下列網路端點。
  
|**URL**|**類型**|**描述**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |智慧標籤  <br/> |Office 365 入口網站安裝至最新安裝套件的前導連結服務。  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |內容傳遞網路上的安裝套件的位置。  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |內容傳遞網路上的安裝套件的位置。  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |智慧標籤  <br/> |Microsoft AutoUpdate 管理控制端點  <br/> |
   
 **第一個應用程式啟動**
  
下列網路端點會在第一次啟動 Office 應用程式的連線。這些端點提供增強的 Office 功能的使用者，並 Url 會連絡不論授權類型 （包括大量授權安裝）。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |'Flighting' 設定-允許功能光線向上鍵和試驗。  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |'Flighting' 的網路設定測試  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |'Flighting' 的網路設定測試  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Office Configuration Service-主要的服務端點清單。  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Office 規則遙測下載-會告知用戶端有關哪些資料及上傳到遙測服務的事件。  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote 遙測服務  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Office 遙測上傳報表-"Heartbeart"和錯誤所發生事件的用戶端上傳到遙測服務。  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Online 範本服務-提供使用者線上文件範本。  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office 範本下載-PNG 範本圖像儲存。  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office 應用程式儲存區設定。  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office 文件的整合服務目錄 （服務和端點的清單） 與首頁領域探索。  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |首頁領域探索 v2 （15.40 及更新版本） 的資源  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Microsoft AutoUpdate 資訊清單-若要查看是否有更新可用的檢查  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript 程式庫  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 應用程式的 Office 設定及資源。  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Office 設定及資源的 Bing 對應應用程式。  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |人員 Office 設定及資源的圖形應用的程式。  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |智慧標籤  <br/> |什麼是新增 OneNote 的內容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |智慧標籤  <br/> |新增 OneNote 的內容。  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |什麼是新的 OneNote 的圖像。  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |智慧標籤  <br/> |在 [應用程式支援服務。  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |智慧標籤  <br/> |電子郵件帳戶偵測服務。  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |智慧標籤  <br/> |Outlook 自動探索  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |智慧標籤  <br/> |Outlook 的 Office 365 服務的端點。  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |智慧標籤  <br/> |Outlook 增益集的圖示。  <br/> |
   
> [!NOTE]
> Office Configuration Service 作為自動探索服務的所有 Microsoft Office 用戶端，而不只是 for mac。傳回回應端點項目半靜態中的變更會很少用，但仍可能。 
  
 **登入**
  
下列的網路端點會連絡時登入雲端儲存。根據您的帳戶類型，可能會連絡不同服務。例如：
  
- **MSA： Microsoft 帳戶**-通常用於取用者與零售版的案例 
    
- **OrgID： 組織帳戶**-通常用於商業案例 
    
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Windows 驗證服務  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Office 365 登入服務 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |智慧標籤  <br/> |Microsoft 帳戶登入服務 (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft 帳戶登入服務協助程式 (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Office 365 登入品牌 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |文件和位置儲存定位器  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |大部分的最近使用過 (MRU) 文件服務  <br/> |
   
> [!NOTE]
> 訂閱型及忮授權的登入同時啟動、 產品並啟用例如 OneDrive 雲端資源的存取權。大量授權安裝，使用者仍系統提示登入 （預設），但這只是如已啟動產品所必要的雲端資源的存取權。 
  
 **啟用產品**
  
下列的網路端點適用於 Office 365 訂閱] 及 [零售授權啟用。尤其是這不適用於大量授權安裝。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office 授權服務  <br/> |
   
 **什麼是新的內容**
  
下列的網路端點僅適用於 Office 365 訂閱。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |什麼是新的 JSON] 頁面上的內容。  <br/> |
   
 **研究工具**
  
下列的網路端點僅適用於 Office 365 訂閱。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |研究者 Web 服務  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |研究者靜態內容  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |研究者內容提供者  <br/> |
   
 **智慧查閱**
  
下列的網路端點適用於零售/大量授權和 Office 365 訂閱啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |提供 Web 服務  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery 文件庫  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |支援的 JavaScript 程式庫  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |前瞻內容提供者  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |前瞻內容提供者  <br/> |
   
 **PowerPoint 設計工具**
  
下列的網路端點僅適用於 Office 365 訂閱。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint 設計工具 web 服務  <br/> |
   
 **PowerPoint 快速啟動工具**
  
下列的網路端點僅適用於 Office 365 訂閱。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint QuickStarter web 服務  <br/> |
   
 **傳送 Smile/皺眉頭**
  
下列的網路端點適用於零售/大量授權和 Office 365 訂閱啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |傳送 Smile 服務  <br/> |
   
 **連絡支援人員**
  
下列的網路端點適用於零售/大量授權和 Office 365 訂閱啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |連絡支援服務  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |在 [應用程式支援服務  <br/> |
   
 **另存為 PDF**
  
下列的網路端點適用於零售/大量授權和 Office 365 訂閱啟用。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word 文件轉換服務 (PDF)  <br/> |
   
 **Office 應用程式 （亦即增益集）**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用信任 Office 應用程式增益集時。
  
|**URL**|**應用程式**|**類型**|**描述**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office 應用程式儲存區設定  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 應用程式的資源  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing 對應應用程式資源  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |人員 Graph 應用程式資源  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office 重新導向服務  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript 文件庫  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |遙測與 Office 應用程式的報告服務  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax JavaScript 程式庫  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript 程式庫  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript 文件庫  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支援資源  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |支援資源  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |支援資源  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript 文件庫  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |錯誤報告  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |字型的資源  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |遙測服務  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |遙測報告  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft 存放區資產庫  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia] 頁面上的資源  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 媒體資源  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia 沙箱圖文框  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |對應範本  <br/> |
   
 **安全連結**
  
所有 Office 應用程式的 Office 365 訂閱僅適都用於下列網路端點。
  
|**URL**|**類型**|**描述**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft 安全連結服務  <br/> |
   
 **當機報告**
  
下列的網路端點適用於 Office 365 訂閱和零售/大量授權啟用的所有 Office 應用程式。當程序意外損毀時，報表會產生並傳送給 Watson 服務。
  
|**URL**|**類型**|**描述**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |智慧標籤  <br/> |Microsoft 錯誤報告服務  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |智慧標籤  <br/> |Office 共同作業觀點服務  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>減少網路要求和流量的選項

預設設定的 Office for Mac 提供最佳使用者經驗包括類功能和保持最新的電腦。在某些情況下，您可能會想要防止從連絡網路端點的應用程式。本章節將討論能力的選項。
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>停用雲端登入和 Office 增益集
  
大量授權客戶可能會有嚴格原則相關文件儲存至雲端式儲存裝置。停用 MSA/OrgID 登入，並存取至 Office 增益集可以設定下列每個應用程式喜好設定。
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

如果使用者嘗試存取的登入函數，就會看到錯誤的網路連線不存在。因為這個喜好設定也會封鎖線上產品啟用，則應僅用於大量授權安裝。尤其是使用此喜好設定會防止 Office 應用程式存取下列端點：
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- 上述 ' 登入 」 一節所列的所有端點。
    
- 上述 ' 智慧查閱 」 一節中所有的端點。
    
- 上述 ' 產品啟用 」 一節中所有的端點。
    
- 上述 ' Office 相關應用程式 （亦即增益集） 」 一節中所有的端點。
    
若要重新建立使用者的完整功能，其中一個設定為 '2' 的喜好設定或移除它。
  
> [!NOTE]
> 這個喜好設定需要 Office for Mac 組建 15.25 [160726] 或更新版本。 
  
### <a name="telemetry"></a>遙測
  
Office for Mac 會每隔將遙測資訊傳送回給 Microsoft。資料上傳至 '連結關係' 端點。將遙測資料可協助評估狀況和每個 Office 應用程式的任何非預期的行為工程小組。有兩種類別的遙測：
  
- **活動訊號**包含版本及授權資訊。在 [應用程式啟動時立即傳送此資料。 
    
- **Usage**包含有關如何使用應用程式的資訊和非嚴重錯誤。此資料會傳送每隔 60 分鐘。 
    
Microsoft 會非常嚴重引導您的隱私。您可以了解在 Microsoft 的資料收集原則[https://privacy.microsoft.com](https://privacy.microsoft.com)。若要防止傳送 '流量' 遙測應用程式，可以調整**SendAllTelemetryEnabled**喜好設定。喜好設定是個別應用程式，以及您可以將透過 macOS 設定設定檔，或手動從終端機： 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

活動訊號遙測一律傳送且無法加以停用。
  
### <a name="crash-reporting"></a>當機報告
  
嚴重的應用程式錯誤發生時，應用程式將會意外終止並將損毀報表上傳至 'Watson' 服務。損毀報告包含通話堆疊，這是清單中的應用程式已處理而導致損毀的步驟。下列步驟協助找出失敗的確切函數工程小組及為何。
  
在某些情況下，將文件的內容會導致損毀的應用程式。如果應用程式識別為原因的文件，它會詢問使用者是否有需要，可以為也將傳送文件以及呼叫堆疊。使用者可以將此問題做出正確的選擇。IT 管理員可能會有嚴格需求的相關文件的傳輸並代表使用者永遠不傳送文件的決策。若要防止文件所傳送和抑制向使用者提示您可以將下列喜好設定：
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> 如果**SendAllTelemetryEnabled**設為**FALSE**，所有損毀的報告已停用程序。若要啟用而不傳送流量遙測報告損毀，可以設定下列喜好設定：```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>更新
  
Microsoft 發行 Office for Mac 更新每隔 （通常是一次個月）。我們強烈鼓勵使用者和 it 專業人員適用保留機器最新以確保最新的安全性修正程式會安裝。在其中 IT 管理員要緊密控制及管理機器更新的情況下，下列喜好設定可以設定為防止從自動偵測並提供產品更新的 AutoUpdate 程序：
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>封鎖與防火牆/Proxy 要求
  
如果您的組織封鎖透過防火牆或 proxy 伺服器要求 url 務必設定為 [允許]，此文件中列出的 Url 或封鎖列出 40 X 回應 （例如 403 或 404）。40 X 回應將允許正常接受無法存取資源的 Office 應用程式，並可提供更快的使用者經驗，比只之間的連線，接著會導致重試的用戶端。
  
若 proxy 伺服器需要驗證，則會傳回 407 回應給用戶端。最佳的體驗，請確定您使用的 Office for Mac 組建 15.27 或更新版本，如它們包括使用 NTLM 和 Kerberos 伺服器特定的修正程式。
  
  
## <a name="see-also"></a>另請參閱

[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)

