---
title: 資料移動期間和之後
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: 資料移動是使用者的影響降至最低的後端作業。 Microsoft 會移每個服務和相關聯的資料租用戶至新的資料中心地理位置時，不不需要任何動作。 資料傳輸和驗證發生在背景事先與最不會影響使用者。
ms.openlocfilehash: 58c4b407062c5472e9c5908d34b084a2d192227d
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840370"
---
# <a name="during-and-after-your-data-move"></a>資料移動期間和之後

資料移動是使用者的影響降至最低的後端作業。 Microsoft 會移每個服務和相關聯的資料租用戶至新的資料中心地理位置時，不不需要任何動作。 資料傳輸和驗證發生在背景事先與最不會影響使用者。
  
> [!NOTE]
> 移動發生在不同時間的每項服務。 因此，您會看到每個服務所述的精簡的功能在不同的時間。 
  
每個 Exchange Online、 SharePoint Online 和商務用 Skype 移動完成後，請觀看確認 Office 365 訊息中心。 下表所示，可能會花費最多 24 個月的時間，註冊期間結束後，若要完成所有要求的資料移動特定的地理位置中的所有客戶。 如果您與您的租用戶中看到任何問題，移動完成後，請連絡[Office 365 支援人員](https://go.microsoft.com/fwlink/p/?LinkID=522459)，以取得協助。 
  

|**註冊國家/地區的客戶**|**完成的所有移動**|
|:-----|:-----|
|澳洲請紐西蘭斐濟群島  <br/> |2022 年 7 月 1 日  <br/> |
|日本  <br/> |2022 年 7 月 1 日  <br/> |
|印度  <br/> |2022 年 7 月 1 日  <br/> |
|加拿大  <br/> |2022 年 7 月 1 日  <br/> |
|南韓  <br/> |2022 年 7 月 1 日  <br/> |
|英國  <br/> |2022 年 7 月 1 日  <br/> |
|法國  <br/> |2022 年 7 月 1 日  <br/> |
|阿拉伯聯合大公國  <br/> |2022 年 7 月 1 日  <br/> |
|南非  <br/> |2022 年 7 月 1 日  <br/> |
|瑞士，列支敦斯登  <br/> |2022 年 7 月 1 日  <br/> |
|德國  <br/> |計劃  <br/> |

> [!NOTE]
> 在適用的 Office 365 國家/地區的客戶可能會選擇加入的 Microsoft Teams 聊天服務資料從移轉 2020 年 1 月 1，透過 2020 年 6 月 30，這也會訊號適用於任何其他合格的工作負載的移轉。  Exchange Online 和 SharePoint Online/OneDrive for Business 會移到原始的期限，雖然小組會針對所有客戶完成 2022 年 7 月 1，以完成，可以預期的客戶會選擇加入集以進行移轉前 2020年。 

## <a name="exchange-online"></a>Exchange Online

因為所花的時間將每個使用者移至新的資料中心地理位置，針對單一租用戶，部分使用者仍然可以在舊的資料中心地理位置中移動期間時其他人會在新的資料中心地理位置中。 這表示牽涉到存取多個信箱的某些功能可能不完全運作移動程序期間其可以最後一週。 下列各節將說明這些功能。
  
### <a name="open-shared-folder-in-outlook-web-access"></a>在 Outlook Web Access 中開啟 「 共用資料夾 」

部分使用者開啟的共用的郵件資料夾從另一個信箱 （使用者具有讀取或寫入權限） 在 Outlook Web Access 中使用 「 共用資料夾 」 功能。 下表說明如何移動期間信箱的共用的資料夾可存取。 請注意，使用共用信箱的完整權限的使用者可以開啟信箱移動期間使用 Outlook Web Access。 
  
|**設定**|**描述**|
|:-----|:-----|
|使用者具有另一個信箱的信箱資料夾權限  <br/> |潛在限制。  <br/> 使用者 A 如果使用者的僅有權限至信箱 b 中的特定資料夾，如果使用者和信箱 B 不是在相同的地理位置租用戶移動期間，無法開啟信箱 B 資料夾 in Outlook Web Access  <br/> 若要新增的共用的資料夾，以滑鼠右鍵按一下左的導覽] 面板中的使用者名稱，並選取 [**新增共用的資料夾**。  <br/> |
|具有完整信箱到另一個信箱的權限的使用者  <br/> |完全支援。  <br/> 如果使用者的信箱 B 的 「 完整存取 」 權限，然後使用者可以按一下 in Outlook Web Access，若要開啟 [顯示信箱 b 的視窗的左側的導覽] 面板中的共用的資料夾 使用者可以開啟共用的信箱不含任何負面影響移動期間使用 Outlook Web Access。 限制僅適用於資料夾層級共用信箱中。           |
  
## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online 移動時，也被移動下列服務的資料：
  
- 商務用 OneDrive
    
- Project Online
    
- Project for Office 365
    
- Office 365 影片服務
    
- 在 s 瀏覽器中的 office
    
- Office 365 專業增強版
    
- Visio Pro for Office 365
    
我們已完成移動您的 SharePoint Online 資料之後，您可能會看到下列的效果部分。
  
### <a name="office-365-video-services"></a>Office 365 影片服務

- 資料移動的視訊採取超過其他的 SharePoint Online 中內容移動。
    
- 之後的 SharePoint Online 內容都會移，會有時間範圍時不能夠播放影片。
    
- 我們正在移除交易式編碼將資料複製從舊的資料中心和轉碼到一次在新的資料中心。
    
### <a name="search"></a>搜尋

過程移動您的 SharePoint Online 資料，我們會將您的搜尋索引及搜尋設定移轉至新位置。 我們已**完成**的 SharePoint Online 資料移動，直到我們繼續提供您的使用者從原始位置中的索引。 在 [新的位置，搜尋會自動啟動編目內容之後我們已完成移動您的 SharePoint Online 資料。 從這點與以前的版本我們提供您的使用者從已移轉的索引。 變更您在移轉之後所發生的內容不包含在已移轉的索引中，直到編目挑選其。 大多數客戶不會注意到結果之後，我們已完成移動其 SharePoint Online 的資料，但有些客戶可能會遇到降低的新鮮度，第一個 24 到 48 小時內都小於最新的權限 
  
下列的搜尋功能會受到影響：
  
- 搜尋結果與搜尋網頁組件： 結果未包含在移轉之後發生，直到編目挑選它們的變更。 
    
- Delve: Delve 不包含在移轉之後發生，直到編目挑選它們的變更。
    
- 常用性和搜尋報告網站： 計數的新位置中的 Excel 報告只會包括已移轉的計數和已執行我們完成移動您的 SharePoint Online 資料後的使用情況報告中的計數。 任何過渡期的計數便會遺失而無法復原。 這段期間通常是幾個天。 有些客戶可能會遇到短或長損失。
    
- 視訊的入口網站： 計數和統計資料的影片入口網站取決於 Excel 報告，以便檢視計算的統計資料和影片入口網站的統計資料的檢視將會遺失與 Excel 報告之相同時間週期。
    
- eDiscovery： 直到編目挑選所做的變更不會顯示在移轉期間進行變更的項目。
    
- 資料外洩防護 (DLP): 未強制執行原則所做的變更可以編目挑選前發生變更的項目。

## <a name="microsoft-teams"></a>Microsoft Teams

在適用的 Office 365 國家/地區的客戶可能會選擇加入集截至 2020 年 1 月 1、 Microsoft Teams 聊天服務資料移轉。  

## <a name="skype-for-business"></a>商務用 Skype

所有使用者將會被登出從商務用戶端軟體商務用 Skype 在剪下移轉過程中。 自動登入將會重新連接使用者兩分鐘內。
  
|**整個移動期間使用的功能**|**移動部分期間可能有限的功能**|
|:-----|:-----|
| 立即訊息和語音通話  <br/>  使用者可以新增連絡人、 新增連絡人群組、 將會議新增、 設定它們的位置，並變更 「 今日新鮮事 」。  <br/>  音訊會議提供者 (ACP) 設定複製到目標資料中心地理位置。 如果 ACP 提供者存在於目標資料中心，它的運作方式。 否則，不會。  <br/> | 租用戶系統管理員 TRPS (租用戶遠端 PowerShell) 將無法建立工作階段的系統管理員。  <br/>  租用戶系統管理員 LAC 將無法使用系統管理員登入及變更使用者設定。  <br/> |
   
|**移動完成後**|
|:-----|
| 會議資料 （上傳的簡報等） 並不會移動，並將須重新上傳。  <br/>  較舊的 Lync 用戶端，例如 Lync 2010 用戶端和 Lync for Mac 2011 用戶端已知快取服務而造成登入問題的 DNS 資訊。 清除 DNS 快取可能需要如果使用者不是在最新的 Skype for Business Windows 用戶端上。 請參閱[在 Office 365 中的商務線上] DNS 組態問題進行疑難排解 Skype](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue)。 Lync for Mac 用戶端使用者應遵循[這些指示](https://support.microsoft.com/kb/2629861)。  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>商務用 Skype 移動所涉及之協力廠商音訊會議提供者
商務用 Skype 的協力廠商音訊會議提供者的附加元件服務都無法使用，如使用者位於新的地理特有的資料中心。  使用協力廠商音訊會議提供者服務的現有客戶應該不會要求移至新的地理特有的資料中心。  部署到新的地理特有的資料中心的新客戶必須要求移至使用協力廠商音訊會議提供者的地區資料中心。
  
## <a name="related-topics"></a>相關主題 
 
[如何要求資料移動](request-your-data-move.md)
    
[資料移動一般常見問題集](data-move-faq.md)
  
[Microsoft Dynamics CRM online 的新資料中心 geos](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[依地區的 azure 服務](https://azure.microsoft.com/regions/)

