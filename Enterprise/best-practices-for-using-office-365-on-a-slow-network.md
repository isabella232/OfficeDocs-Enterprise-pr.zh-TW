---
title: 在慢速網路上使用 Office 365 的最佳作法
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
description: 如果您的網際網路連線一律是快速而永遠不會向下，不是很好嗎？ 或許會變成那一天。 但是，同時，您能夠如何解決 balky 網路，還是完成您的日常工作的實際項目。
ms.openlocfilehash: 479947eb2e785ddfdf77fa2715007afd41d20763
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068239"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>在慢速網路上使用 Office 365 的最佳作法

如果您的網際網路連線一律是快速而永遠不會向下，不是很好嗎？ 或許會變成那一天。 但是，同時，您能夠如何解決 balky 網路，還是完成您的日常工作的實際項目。 雖然 Office 365 是一項雲端架構服務，它還提供許多方式能搭配您的內容離線並順暢地讓您同步處理的變更。 此外，有時候會更有效率的方法是使用離線內容，只是因為應用程式更快速地執行，並在使用者介面是回應速度更快。 這是點： Office 365 可讓您運用這兩者的最佳。 以下是如何利用該。 
  
> [!TIP]
> 想要查看您的網路連線是如何播放速度很慢 （或 fast）？ 請嘗試[OOKLA 速度測試](https://www.speedtest.net/)或[網路速度測試應用程式](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)。 
     
## <a name="why-is-my-network-so-slow"></a>為何我慢的網路？

雖然您不需要對網路效能本身的控制，很有幫助了解什麼在幕後程度。 網際網路助益複雜，但有一些概念，可協助您了解也是較好的情況。 遵循本文中的最佳作法可協助解決效能問題，並降低挫折感。
  
**主要因素可對網路效能的影響**

![網路效能因素](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **頻寬和延遲**網路效能的兩個最重要量值的頻寬和延遲： 
  
- 頻寬是輸送量的以位元 / 秒為單位的速度。 人質愈好。 頻寬就像是水災管道。 管道越大，您可以 「 透過 「 將它放的多個水。
    
- 延遲是它會想要從伺服器或服務前往您的裝置的內容，以毫秒為單位的時間。 更快速地愈好。 可以是數個因素包括低頻寬、 疏鬆的連線或傳輸時間所造成延遲。
    
 **常見的問題**除了頻寬和延遲，其他問題對網路效能的影響，通常是不可預期的。 網路效能可以根據一天或您的實體位置的時間波動。 網路可以堵塞當特定事件發生的特殊網際網路，例如天災或主要公用事件的使用。 大小和複雜性正在載入的頁面和數量及大小所傳輸的檔案會對效能有直接的關係。 暫時可能會降低 WiFi 連線： 例如，您輪詢千分位藉由要求所有人同時叫的大型會議會議。 
  
 **衛星網路考量**當地面網路不可行的情況下，例如後的國家/地區、 出航 ship 或遠端 「 科學記號區域，衛星網路特別有用。 這些網路自信地仰賴衛星位於 geosynchronous 軌道 22,000 英哩赤道上方。 不過，傳輸實際一起出差約 90,000 英哩，且因此衛星網路速度較慢的延遲 （500 毫秒或更多） 比地面網路 (20 到 50ms)。 下個條件的最佳，您可能不會注意到此延遲，但下載大型檔案、 資料流的視訊，及玩遊戲，您可能會。 另一個問題是哪一個大量的天氣，例如 thunderstorms 和 blizzards，可暫時中斷衛星傳輸中的 「 不論淡出 」。
  
## <a name="are-you-sure-its-the-network"></a>確定它是網路？

每當您遇到的效能問題，請先確定您的裝置不是問題的根本原因。 有兩件事您可以設定，可能導致較大的改善：
  
- 請確定您的裝置運作正常且在您的電腦上沒有任何惡意程式碼。
    
- 如果可能的話，請購買更多的記憶體。 新增記憶體是最簡單也通常最有效率的方式改善您的裝置上的效能。 使用大型檔案和影片時，它是特別有幫助。
    
如需詳細資訊，請參閱[Windows 效能及維護](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help)和[以改善在 Windows 10 中的電腦效能的秘訣](https://support.microsoft.com/en-za/help/4002019/windows-10-improve-pc-performance)。

## <a name="best-practices-for-using-your-browser"></a>使用您的瀏覽器的最佳作法

您的瀏覽器是您的閘道到 Office 365，以便它能造成影響的效能，尤其是載入所花的時間] 頁面上，以及您的圓形頻率成為 office 365 服務。 
  
 **在 [一般的瀏覽器**
  
以下是一些建議瀏覽器一般：
  
- 停用瀏覽器附加元件，可能會影響效能或實際上並不需要。
    
- 提高網際網路暫存檔的快取大小。
    
-  一旦您已登入您的公司或學校帳戶，讓瀏覽器視窗保持開啟一天之內。 您可以開啟其他索引標籤和 windows 而再次登入。 如果您需要登入至另一個帳戶，請使用私用瀏覽。 
    
- 每個頁面下載並開啟後，保持加以開啟使用定位點。 很容易標籤之間瀏覽並使用更新版中的一天。 只有當您需要在該頁面上的最新資料，請重新整理頁面。
    
- 如果的時間太長若要開啟 [] 頁面上，停止網頁下載 （按 esc 鍵），然後重新整理頁面 （按 F5）。 
    
-  請儘可能減少來回行程到 Office 365。 例如，而不是透過清單或文件庫的分頁，用於搜尋中的大型文件庫和篩選直接前往您想要的結果清單中尋找檔案。 或者，建立頁面載入時間降至最低的檢視。 如需詳細資訊，請參閱 <<c0>管理大型清單和 Office 365 中的文件庫。
    
- 視訊效能不佳時，您可能無法下載影片，並觀賞您的裝置上。 下載連結可能會提供，或您可能無法以滑鼠右鍵按一下 [視訊] 連結，然後選取 [**儲存成的目標**。 
    
 **瀏覽器特有**
  
以下是一些您特定的瀏覽器的建議：
  
- **Internet Explorer**升級至 Internet Explorer 版本 11 或更新版本的顯著的效能改進透過舊版。 如需詳細資訊，請參閱 < <b0>Internet Explorer 的疑難排解指南</b0>。
    
- **FireFox**如需詳細資訊，請參閱[Firefox 緩慢或停止運作](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging)。
    
- **safari**如需詳細資訊，請參閱[Apple-Safari](https://www.apple.com/safari/)。
    
- **chrome**如需詳細資訊，請參閱[Chrome 協助](https://support.google.com/chrome/?hl=en)。
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>使用 Outlook 和 Outlook Web App 的最佳作法

讀取、 寫入，和組織的電子郵件是 big 部分每個人的一天。 Outlook 和 Outlook Web App (OWA) 提供的離線支援。 智慧型手機上使用電子郵件應用程式是其他有用的替代方式。 使用最符合您需求的下列選項：
  
- 透過舊版升級至 Outlook 的顯著的效能改進的最新版本。 
    
-  Outlook Web App 可讓您建立離線訊息、 連絡人及行事曆事件時 OWA 下一步是上傳能夠連線到 Office 365。 如需有關設定，並在離線模式下使用 OWA 的詳細資訊，請參閱[使用 Outlook Web App 離線](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)。
    
- Outlook 可讓您在快取模式下，在其中它會自動連接儘運作。 您可以讓 Outlook 下載整個信箱時或只是它的一部分。 如需詳細資訊，請參閱[開啟快取 Exchange 模式](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c)，並[在 Outlook 中離線工作](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)。 
    
- Outlook 也提供離線模式。 若要使用此功能，您必須先設定快取模式，讓您的帳戶資訊會被複製到您的電腦。 在離線模式中，Outlook 會嘗試連線使用 「 代理傳送和接收的設定，或當您以手動方式將它設定為離線工作。 如需詳細資訊，請參閱[離線工作，以避免資料連線費用](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282)、[變更傳送和接收離線工作時的設定](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)，以及[從離線工作線上切換](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)。 
    
- 如果您有智慧型手機，您可以使用它來分類您的電子郵件和行事曆透過電話通信業者的網路。 
    
> [!NOTE]
> 以下是使用 Outlook 或 OWA 時機的一些指引。 如果磁碟空間不是此問題： 在裝置上的，Outlook 會有一套完整的功能，並可能最適合您。 如果沒有此問題： 在裝置上的磁碟空間，請考慮使用此功能的子集，但也適合在線上的情況下 OWA。 當然，您可以使用下列一項因為也一起運作。 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>使用商務用 OneDrive 的最佳做法

商務用 OneDrive 被為了從頭設定線上與離線工作與您的檔案。 一旦您設定它，自動且可靠地，就會發生的變更同步處理任何與每當您，讓它們。 如果網路速度很慢，您可以使用檔案的離線版本。
  
OneDrive for Business 同步處理應用程式隨附 SharePoint Online 和 Office 365 商務版訂閱，或者您也可以[下載](https://support.microsoft.com/kb/2903984)OneDrive for Business 同步處理應用程式的可用。 此應用程式也是較快，使用**在檔案總管中開啟**] 或 [**上傳**命令。 如需詳細資訊，請參閱[設定您的電腦同步處理您的 OneDrive for Office 365 中的業務檔案](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)。
  
以下是一些使用 OneDrive for Business 同步處理應用程式的其他指導方針：
  
- 如果您第一次同步處理大型文件庫，啟動期間關閉小時同步處理，例如，隔天。 
    
- 您可以使用[停止同步處理與 OneDrive for 商務應用程式的文件庫](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330)功能暫時停止 [同步處理的更新。 不過，對於短暫，例如幾個小時一次使用這項功能，以避免佇列大型數字的更新，以及如果數名人員使用相同的文件合併衝突的風險降至最低。 
  
## <a name="best-practices-for-using-onenote"></a>使用 OneNote 的最佳作法

每一個 SharePoint 小組網站有內建的 OneNote 筆記本，您可以輕鬆地建立您自己。 OneNote 會收集您需要以取得完成的工作每日的即時資訊的絕佳方式。 例如，許多 teams 作為 OneNote 集合點每週會議、 專案備忘稿、 構想、 計劃及狀態報表。 整齊即可將這項異質資訊組織使用頁面、 區段、 和索引標籤。
  
OneNote 的好處是，您可以存取內容從幾乎任何裝置是否桌上型電腦、 膝上型電腦、 平板電腦或智慧型手機。 與您不必擔心儲存，或因為 OneNote 會為您進行同步處理。 
  
如需詳細資訊，請參閱 < <b0>Microsoft OneNote</b0>。

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>使用 Skype for Business 和 Lync Online 的最佳作法

以下是基於商業或 Lync Online 使用 Skype，當您的網路速度很慢的一般方針：

- 使用立即訊息，每當您可以因為它在慢速網路上的運作方式。
    
- 請避免進行通話透過虛擬私人網路 (VPN) 或遠端存取服務 (RAS) 連線。
    
- 請確定您的音訊裝置已核准。 如需詳細資訊，請參閱[電話及裝置合格的 Microsoft Lync](https://docs.microsoft.com/skypeforbusiness/lync-cert/ip-phones)。
    
-  當使用 PowerPoint online 的簡報中，降低的大小和複雜性的投影片。 如需詳細資訊，請參閱 <<c0>的祕訣提升效能的簡報。
            
-  視訊的效能是非常密切對網路效能。 避免使用視訊，如果您的網路速度很慢。 

如需詳細資訊，請參閱[不佳的音訊或視訊品質 Lync Online 中的](https://support.microsoft.com/kb/2386655)，或者如何[在商務用 Skype 的連線問題進行疑難排解](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771)。
  
## <a name="best-practices-for-using-sharepoint-lists"></a>使用 SharePoint 清單的最佳作法

使用清單資料離線以 「 快轉 」、 分析或報告資料是在慢速網路的影響降至最低的絕佳方式。 您可以從讀取和寫入大部分列出 Microsoft Access 2019 與 Microsoft Access 2016 藉由連結給他們。 您也可以將清單匯出至 Excel 表格，以建立單向之間的資料連線的 Excel 表格和清單。 了解如何[使用離線資料表連結至 SharePoint 清單](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e)。
  
如需詳細資訊，請參閱中[管理大型清單和 Office 365 中的文件庫](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)的 「 深入了解管理大型清單 」 一節。
  
## <a name="best-practices-for-customizing-web-pages"></a>自訂網頁的最佳作法

當您自訂網頁時，您可能不小心頁面會導致效能不佳。 數個因素可以影響，例如] 頁面上，新增多少網頁組件，最初顯示多少個清單或文件庫項目，及字碼頁的方式的大小與複雜性。
  
如需詳細資訊，請參閱[調整 SharePoint Online 效能](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance)。
  
## <a name="best-practices-for-using-project-online"></a>使用 Project Online 的最佳作法

下列指導方針可協助改善網路效能。
  
- Project Online 和 SharePoint Online 需要同步處理，可能會很耗時。 如果您的專案小組之間有低周轉，停用來增進專案發佈 and Project Detail Pages 效能的專案網站同步處理。 限制的實際需要使用系統，並監視所有潛在的權限問題後的大型群組同步處理的資源群組的 Active Directory 同步處理。 
    
- 如果您的組織使用專案網站，以建立視需要而不是自動。 此加速的第一個發佈體驗，並避免建立不必要的網站和內容。
    
- 專案詳細資料頁面 (PDP) 可以觸發整個專案重新計算，並開始進行的工作流程動作，這兩種都可以是效能耗用資源的作業。 若要避免觸發兩個更新程序在此同時在相同的 PDP，避免更新行事曆欄位 （開始日期、 完成日期、 狀態日期，以及目前的日期） 和非排程欄位 （專案名稱、 描述及擁有者）。 
    
- 減少網頁組件及顯示在每個 PDP 的自訂欄位的數目。 建立專用的 PDP 唯一欄位需要更新以改善負載並節省時間。 
    
- 當您使用 OData 報告時，限制您查詢在執行階段使用伺服器端篩選的資料量。
    
如需詳細資訊，請參閱[調整 Project Online 的效能](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)。
  
## <a name="whats-the-best-way-to-report-problems"></a>報告問題的最佳方式為何？

Microsoft 不斷改善藉由監視網路，測量的頻寬的 Office 365 的整體效能和延遲，改善頁面載入時間，減少的磁碟 I/O，重新設計頁面以使用最少下載策略中，新增到資料中心的硬體和新增多個資料中心。 如需有關檢查您的目前狀態和報告問題的詳細資訊，請參閱 <<c0>如何檢查 Office 365 服務健康情況。
  
## <a name="see-also"></a>另請參閱

[Office 365 的網路規劃和效能調整](network-planning-and-performance.md)
  
[Office 365 網路連線原則](office-365-network-connectivity-principles.md)
  
[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)

