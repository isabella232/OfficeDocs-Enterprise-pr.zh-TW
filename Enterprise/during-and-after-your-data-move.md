---
title: 資料移動期間和之後
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: 資料移動是以使用者影響最小的後端作業。雖然 Microsoft 移動每個服務與相關的資料的租用戶至新的資料中心地理位置不不需要任何動作。資料傳輸和驗證發生事先以影響最小背景中的使用者。
ms.openlocfilehash: 6975a2ea4a1f2b2ebabe5f64b12ae58657180903
ms.sourcegitcommit: b745d570fd6691606d226f6232cfaafd2d875a2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "25361501"
---
# <a name="during-and-after-your-data-move"></a>資料移動期間和之後

資料移動是以使用者影響最小的後端作業。雖然 Microsoft 移動每個服務與相關的資料的租用戶至新的資料中心地理位置不不需要任何動作。資料傳輸和驗證發生事先以影響最小背景中的使用者。
  
> [!NOTE]
> 移動發生在不同時間的每個服務。因此，您會看到每個服務所述的精簡的功能在不同時間。 
  
每個 Exchange Online、 SharePoint Online 和 Skype for Business 的移動完成後，請觀看確認 Office 365 郵件中心。下表所示，可能很多達 24 個月內，註冊期間結束之後，才能完成所有要求的資料移動的所有客戶的特定地理位置。如果您看見任何問題與您的租用戶移動完成後，連絡[Office 365 支援](https://go.microsoft.com/fwlink/p/?LinkID=522459)以取得協助。 
  

|**客戶計費地址**|**完成所有移動**|
|:-----|:-----|
|澳洲、 紐西蘭、 斐濟群島  <br/> |2017 年 10 月 31 日  <br/> |
|日本  <br/> |2018 年 10 月 31 日  <br/> |
|印度  <br/> |2018 年 10 月 31 日  <br/> |
|加拿大  <br/> |2019 年 6 月 30 日  <br/> |
|South 韓國  <br/> |2018 年 10 月 31 日  <br/> |
|英國  <br/> |2019 年 9 月 15 日  <br/> |
|法國  <br/> |2020 年 9 月 15 日  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>包含與協力廠商音訊會議提供者的移動

- Skype for Business 的協力廠商音訊會議提供者的附加元件服務都無法使用的使用者隸屬於新的特定地理位置的資料中心。 
    
- 使用協力廠商音訊會議提供者服務的現有客戶應該不會要求將移至新的地理位置特有的資料中心。 
    
- 部署到新的特定地理位置的資料中心的新客戶必須要求的移動到地區資料中心使用協力廠商音訊會議提供者。 
    
## <a name="exchange-online"></a>Exchange Online

因為所花費時間的單一租用戶將每個使用者移至新的資料中心地理位置，某些使用者仍能在舊的資料中心地理位置移動期間時其他人都會採用新的資料中心地理位置。這表示涉及存取多個信箱的一些功能將無法完全運作之移動程序期間的可以最後一週。下列各節說明這些功能。
  
### <a name="mailbox-move"></a>信箱移動

當個別信箱移動 crosses 資料中心，geos 信箱內容會先前分段使現有的資料複製到目標地理位置而不會影響信箱。在轉換至目標地理位置的時間來源地理位置中的信箱已鎖定的幾分鐘。在該工作時，電子郵件用戶端無法暫時連線。任何其他變更複製到目標地理位置，並再信箱完成移至目標地理位置。沒有至 [郵件流程移動期間未中斷。
  
一些使用者可能需要重新啟動 Outlook 桌面之後的信箱移[知識庫文章 2591913](https://support.microsoft.com/kb/2591913)中所述。
  
### <a name="shared-mailbox"></a>共用信箱

擁有 「 共用信箱的 [完整存取] 權限的使用者不會影響移動期間。
  
### <a name="resource-mailbox"></a>資源信箱

需要來管理資源信箱設定透過 Outlook Web Access 中的 [選項] 頁面上的使用者可以繼續進行移動作業期間。
  
如果直接透過 Exchange cmdlet 管理資源信箱、 Set-mailboxregionalconfiguration 指令程式和 Set-mailboxcalendarconfiguration 不會用於如果執行的使用者和資源信箱位於不同 geos。
  
### <a name="calendar-delegation"></a>行事曆委派

空閒/忙碌和行事曆共用不受影響的租用戶移動期間。行事曆] 資料夾的信箱 B 的寫入權限的使用者仍可管理使用 Outlook 桌面信箱 B 的行事曆] 資料夾。不過，移動期間使用者 A 和 B 的信箱不在相同的地理位置，如果使用者 A 無法編輯 Outlook Web Access 中的信箱 B 的行事曆直到兩者會移至目標地理位置。
  
### <a name="open-shared-folder-in-outlook-web-access"></a>在 Outlook Web Access 中開啟 「 共用資料夾"

一些使用者從另一個信箱 （使用者具有讀取或寫入權限） 使用 「 共用資料夾 」 功能的 Outlook Web Access 中開啟共用的郵件資料夾。下表說明如何移至共用的資料夾運作期間信箱的存取。請注意使用共用信箱的完整權限的使用者可以開啟信箱移動作業期間使用 Outlook Web Access。 
  
|**組態**|**描述**|
|:-----|:-----|
|使用者具有另一個信箱的信箱資料夾權限  <br/> |可能會限制。  <br/> 如果使用者和信箱 B 未提供相同的地理位置租用戶移動期間，使用者 A 無法信箱 B 的資料夾中開啟 Outlook Web Access 如果使用者的僅限具有特定的資料夾信箱 b 權限  <br/> 若要新增的共用的資料夾，在左側的導覽] 面板中的使用者名稱上按一下滑鼠右鍵並選取 [**新增共用的資料夾**。  <br/> |
|另一個信箱的完整信箱權限的使用者  <br/> |完全支援。  <br/> 如果使用者的信箱 B 的 [完整存取] 權限，然後使用者 A 可以按一下在左的導覽] 面板中 Outlook Web Access] 即可開啟 [顯示信箱 b 的視窗中之共用的資料夾  <br/> > [!NOTE]> 使用者可開啟共用的信箱不含任何負面影響移動期間使用 Outlook Web Access。限制只適用於信箱的共用資料夾層級。           |
   
### <a name="public-folders"></a>公用資料夾

如果公用資料夾信箱暫時嘗試對其進行存取的使用者從不同的 datacenter 地理位置中，使用者便無法進行存取。 
  
### <a name="online-archives"></a>線上封存

進行中移動時，透過 Outlook Web Access 連線的使用者將無法連接至其線上封存信箱。支援存取封存信箱的使用者使用 Outlook 連線。
  
### <a name="ediscovery-amp-auditing"></a>eDiscovery&amp;稽核

EDiscovery 及稽核的 Office 365 安全性功能&amp;規範中心支援跨地理租用戶移動。不同 Exchange 系統管理中心 (EAC) 不支援已啟動查詢尚不移動之後承租人移動的使用者。如需關於安全性&amp;規範中心，請參閱[Office 365 安全性&amp;規範中心](https://go.microsoft.com/fwlink/p/?linkid=841313)。 
  
下表顯示您如何存取 eDiscovery 及透過 EAC 及安全性稽核&amp;規範中心。
  
||**Exchange 系統管理中心**|**安全性&amp;規範中心**|
|:-----|:-----|:-----|
|eDiscovery  <br/> | 移至 [ https://portal.office.com，然後按一下 [**系統管理**並排顯示。 <br/> 按一下 [**系統中心** \> **Exchange**。 <br/> 選取 [**相符性管理** \> **就地 eDiscovery&amp;保留**。 | 移至 [ https://portal.office.com，然後按一下 [系統管理並排顯示。 <br/> 按一下 [**系統中心** \> **安全性&amp;規範**。 <br/> 選取 [**搜尋&amp;調查** \> **eDiscovery**。|
|稽核  <br/> | 移至 [ https://portal.office.com，然後按一下 [**系統管理**並排顯示。 <br/> 按一下 [**系統中心** \> **Exchange**。選取 [**相符性管理** \> **稽核**。 | 移至 [ https://portal.office.com，然後按一下 [系統管理並排顯示。 <br/> 按一下 [**系統中心** \> **安全性&amp;規範**。 <br/> 選取 [**搜尋&amp;調查** \> **稽核記錄搜尋**。 |
   
### <a name="mailbox-migration"></a>信箱移轉

租用戶 geos 之間移動、 移轉批次可能會報告移轉批次中的一些使用者可能會遺留在來源地理位置中的錯誤。在此例中，移除現有的遷移批次移除基礎的同步處理要求。批次完全清除之後，建立的批次同樣地，這會開始同步處理的要求在建立目標地理位置。
  
## <a name="sharepoint-online"></a>SharePoint Online

移動 SharePoint Online、 時也會移動下列服務的資料：
  
- 商務用 OneDrive
    
- Microsoft Project Online
    
- Project for Office 365
    
- Office 365 影片服務
    
- Office Online
    
- Office 365 專業增強版
    
- Visio Pro for Office 365
    
我們已完成移動 SharePoint Online 資料之後，您可能會看到下列的效果的部分。
  
### <a name="office-365-video-services"></a>Office 365 影片服務

- 資料移動視訊取得超過您在 SharePoint Online 中的內容的其餘部分的移動。
    
- SharePoint Online 內容移動之後，會有時間圖文框時不能播放的影片。
    
- 我們要移除的交易式編碼將資料複製從上一個資料中心及針對轉碼再次中最新的資料中心。
    
### <a name="search"></a>搜尋

會移動 SharePoint Online 資料的過程中斷我們會將搜尋索引及搜尋設定移轉至新位置。我們已**完成**的 SharePoint Online 資料移動，直到我們繼續提供您的使用者從索引中的原始位置。在新的位置，搜尋會自動啟動後我們已完成移動 SharePoint Online 資料編目內容。從這點與我們這時候開始服務使用者從已移轉的索引。變更至您在移轉之後所發生的內容不包含在已移轉的索引中直到編目挑選它們。大部分客戶不發現結果較少新鮮右之後，我們已完成移動其 SharePoint Online 的資料，但有些客戶可能會遇到降低的新鮮度第 24 48 小時 
  
下列的搜尋功能會受影響：
  
- 搜尋結果與搜尋網頁組件： 結果未包含直到編目挑選它們遷移之後發生的變更。 
    
- 探索： 探索不含直到編目挑選它們遷移之後發生的變更。
    
- 常用性和搜尋報告網站： 新的位置中的 Excel 報表的計數僅包含已移轉的計數和計數 （英文） 從我們完成移動 SharePoint Online 資料之後已執行的流量報告。中期期間從任何計數遺失，且無法復原。這段期間通常是幾個天。某些客戶可能會遇到較短或長激增。
    
- 視訊的入口網站： 計數和視訊入口網站的統計資料而定的統計資料的 Excel 報表，因此檢視計數和視訊入口網站的統計資料的檢視丟失的多數 Excel 報表的相同時間週期。
    
- eDiscovery： 在移轉期間變更的項目不顯示之前所做的變更可以編目挑選。
    
- 資料遺失防護 (DLP)： 原則不會強制執行變更之前所做的變更可以編目挑選的項目。
    
## <a name="skype-for-business"></a>商務用 Skype

所有使用者將會都登出從商務用戶端軟體 Skype 在剪下移轉過程中。自動登入將重新連線使用者兩分鐘內。
  
|**整個移動期間可運作的功能**|**移動期間可能有限的功能**|
|:-----|:-----|
| 立即訊息和語音通話  <br/>  使用者可以新增連絡人、 新增連絡人群組、 將會議新增、 設定其位置和變更"今天有什麼新鮮事"。  <br/>  音訊會議提供者 (ACP) 設定會複製到目標資料中心地理位置。若出現在目標資料中心的 ACP 提供者，就會運作。否則，它不會。  <br/> | 承租人管理員 TRPS (租用戶遠端 PowerShell) 無法建立工作階段的系統管理員。  <br/>  承租人管理員 LAC 無法登入及變更使用者設定的系統管理員。  <br/> |
   
|**移動後**|
|:-----|
| 會議資料 （上傳的簡報中等等） 將不會移動並將需要重新上傳。  <br/>  較舊的 Lync 用戶端，例如 Lync 2010 用戶端和 Lync for Mac 2011 用戶端是已知快取服務而造成登入的問題的 DNS 資訊。清除的 DNS 快取可能需要如果使用者不是最新的 Skype for Business Windows 用戶端上。要求使用者在執行[疑難排解精靈]](https://support.microsoft.com/en-us/kb/2541980) ，然後遵循指示如何清除的用戶端快取。Lync for Mac 用戶端使用者應該遵循[這些指示](https://support.microsoft.com/en-us/kb/2629861)。<br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>資料的其他服務，包括 Yammer 與 Power BI

我們只將客戶資料移動的 Exchange Online、 SharePoint Online 和 Skype for Business。我們不會移動資料的其他服務。不會變更或給您的客戶或其他這些服務的使用者身分的影響。移動程序不會影響，以及其客戶資料的位置會維持不變。
  
## <a name="related-topics"></a>相關主題 
 
[如何要求資料移動](request-your-data-move.md)
    
[資料移動一般常見問題集](data-move-faq.md)
  
[Microsoft Dynamics CRM Online 的新資料中心 geos](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[依地區 azure 服務](https://azure.microsoft.com/en-us/regions/)

