---
title: 在慢速網路上使用 Office 365 的最佳作法
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
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
description: 如果您的網際網路連線永遠是 fast 且永遠不向下，不是很好吗？或許會跳那天。但同時，有要怎麼做才能解決 balky 網路和仍屬可以完成您日常工作的實用事項。
ms.openlocfilehash: 2287de562672f5ceb1ab32949168e8dfdeb31585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933140"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a><span data-ttu-id="3d05b-105">在慢速網路上使用 Office 365 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-105">Best practices for using Office 365 on a slow network</span></span>

<span data-ttu-id="3d05b-p102">如果您的網際網路連線永遠是 fast 且永遠不向下，不是很好吗？或許會跳那天。但同時，有要怎麼做才能解決 balky 網路和仍屬可以完成您日常工作的實用事項。雖然 Office 365 雲端架構服務，也提供許多方法可讓內容離線使用以及順暢地保留變更同步處理。此外，有時候很多有效使用內容離線只是因為應用程式執行更快的使用者介面會更快的回應。這是點： Office 365 可讓您運用這兩者的最佳。以下是如何利用這些。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p102">Wouldn't it be nice if your Internet connection was always fast and never down? Perhaps that day will come. But in the meantime, there are practical things you can do to work around a balky network and still get your day-to-day work done. Although Office 365 is a cloud-based service, it also provides many ways to work with your content offline and to smoothly keep your changes synchronized. Besides, it's sometimes more efficient to work with content offline just because applications run faster and the user interface is more responsive. The point is this: Office 365 gives you the best of both worlds. Here's how to take advantage of that.</span></span> 
  
> [!TIP]
> <span data-ttu-id="3d05b-p103">想要查看如何慢 （或 fast） 網路連線？請嘗試[OOKLA 速度測試](https://www.speedtest.net/)或[網路速度測試應用程式](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p103">Want to see how slow (or fast) your network connection is? Try the [ OOKLA Speed test ](https://www.speedtest.net/) or the [Network Speed Test App](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).</span></span> 
     
## <a name="why-is-my-network-so-slow"></a><span data-ttu-id="3d05b-115">為何我慢的網路？</span><span class="sxs-lookup"><span data-stu-id="3d05b-115">Why is my network so slow?</span></span>

<span data-ttu-id="3d05b-p104">雖然您不需要網路效能本身的控制權，有助於了解新將要幕後作業。網際網路是助益複雜，但有一些可協助您了解 「 brad 也是較好的概念。遵循本文中的最佳作法可以協助解決方法的效能問題，並減少挫折感。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p104">Although you don't have control over network performance itself, it helps to understand what's going on behind the scenes. The Internet is enormously complex, but there are a few concepts that can help you understand the situation much better. Following the best practices in this article can help workaround performance issues and reduce frustration.</span></span>
  
<span data-ttu-id="3d05b-119">**會影響網路效能的主要因素**</span><span class="sxs-lookup"><span data-stu-id="3d05b-119">**Major factors that affect network performance**</span></span>

![網路效能因素](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 <span data-ttu-id="3d05b-121">**頻寬和延遲**網路效能的兩個最重要測量的頻寬和延遲：</span><span class="sxs-lookup"><span data-stu-id="3d05b-121">**Bandwidth and latency** The two most important measures of network performance are bandwidth and latency:</span></span> 
  
- <span data-ttu-id="3d05b-p105">輸送量以每秒位元速率較頻寬。人質愈好。頻寬就像水管道。管道越大可以"放到"的多個水。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p105">Bandwidth is the rate of throughput measured in bits per second. Bigger is better. Bandwidth is like a water pipe. The larger the pipe, the more water that you can "put through" it.</span></span>
    
- <span data-ttu-id="3d05b-p106">延遲是的時間的內容以取得伺服器或服務從您的裝置並以毫秒為單位。更快愈好。延遲可以是數個因素包括低頻寬、 稀連線或傳輸時間所造成。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p106">Latency is the time it takes for content to get from a server or service to your device and is measured in milliseconds. Faster is better. Latency can be caused by a number of factors including low bandwidth, a sparse connection, or transmission time.</span></span>
    
 <span data-ttu-id="3d05b-p107">**一般問題**頻寬和延遲，除了其他問題影響網路效能及通常是不可預期。網路效能可以根據一天或實體位置的時間波動。網路可以堵塞當特定事件發生的突然增加網際網路，例如天然災害或主要公用事件使用。大小與複雜性載入頁面和數目與大小正在傳輸的檔案會對效能有直接的關係。WiFi 連線可能暫時會降低： 例如，您輪詢千分位所要求所有人同時叫的大型會議會議。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p107">**Common issues** Besides bandwidth and latency, other issues have an impact on network performance and are often unpredictable. Network performance can fluctuate based on the time of the day or your physical location. The network can become clogged when certain events occur that spike the use of the Internet, such as a natural disaster or a major public event. The size and complexity of the page being loaded and the number and size of files being transferred have a direct bearing on performance. A WiFi connection can temporarily degrade: for example, you poll a large conference meeting of thousands by requesting everyone to tweet at the same time.</span></span> 
  
 <span data-ttu-id="3d05b-p108">**衛星網路考量**當地面網路不可行，例如後的國家/地區、 遊 ship 或遠端工程區域，衛星網路特別有用。這些網路依賴衛星置於上方赤道 22,000 浬在 geosynchronous 範圍。但傳輸實際上一起出差約 90,000 浬與因此衛星網路具有較慢的延遲 （500 毫秒或更多） 比地面網路 (20 至 50ms)。底下的條件適合，您可能不會注意到此延遲，但下載大型檔案、 資料流影片及播放遊樂場，您可能會。另一個問題是在哪些粗天氣，例如 thunderstorms 和 blizzards，可暫時中斷衛星傳輸的"不論淡出"。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p108">**Considerations for a satellite network**A satellite network is useful when a terrestrial network is not feasible, such as the back country, a cruise ship, or a remote scientific area. These networks rely on satellites positioned in a geosynchronous orbit 22,000 miles above the equator. However, a transmission actually travels about 90,000 miles, and so a satellite network has a slower latency (500 ms or more) than a terrestrial network (20 to 50ms). Under the best of conditions, you may not notice this latency, but for downloading large files, streaming videos, and playing games, you probably will. Another issue is "rain fade" in which heavy weather, such as thunderstorms and blizzards, can temporarily interrupt satellite transmission.</span></span>
  
## <a name="are-you-sure-its-the-network"></a><span data-ttu-id="3d05b-139">您是否確定它是網路吗？</span><span class="sxs-lookup"><span data-stu-id="3d05b-139">Are you sure it's the network?</span></span>

<span data-ttu-id="3d05b-p109">每當發生效能問題時，首先請確定您的裝置不是根本原因的問題。有兩件事您可以執行動作，可能會讓 big 改進：</span><span class="sxs-lookup"><span data-stu-id="3d05b-p109">Whenever you experience performance problems, first make sure that your device is not the root cause of the problem. There are two things you can do that might make a big improvement:</span></span>
  
- <span data-ttu-id="3d05b-142">請確定您的裝置執行以及與您的電腦上有無惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d05b-142">Make sure your device is running well and there is no malware on your computer.</span></span>
    
- <span data-ttu-id="3d05b-p110">請儘可能購買更多的記憶體。新增記憶體是最簡單和通常最有效率的方式改善裝置上的效能。使用大型檔案及影片時相當特別有用。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p110">If possible, buy more memory. Adding memory is the simplest and often most effective way to improve performance on your device. It's especially helpful when working with large files and videos.</span></span>
    
<span data-ttu-id="3d05b-146">如需詳細資訊，請參閱[Windows 效能及維護](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help)和[修正的 Windows 系統效能問題](https://support.microsoft.com/mats/slow_windows_performance/)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-146">For more information, see [ Windows Performance and maintenance ](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) and [Fix Windows system performance problems](https://support.microsoft.com/mats/slow_windows_performance/).</span></span>
   
## <a name="best-practices-for-using-your-browser"></a><span data-ttu-id="3d05b-147">使用您的瀏覽器的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-147">Best practices for using your browser</span></span>

<span data-ttu-id="3d05b-148">在瀏覽器至 Office 365 閘道，讓它可對效能，特別是使用載入所花費的時間的影響頁面並頻率您圓角化成為至 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="3d05b-148">Your browser is your gateway to Office 365, so it can have an impact on performance, especially with the time it takes to load a page and how often you round trip to the Office 365 service.</span></span> 
  
 <span data-ttu-id="3d05b-149">**一般的瀏覽器**</span><span class="sxs-lookup"><span data-stu-id="3d05b-149">**Browsers in general**</span></span>
  
<span data-ttu-id="3d05b-150">以下是一般瀏覽器的一些建議：</span><span class="sxs-lookup"><span data-stu-id="3d05b-150">Here are some suggestions for browsers in general:</span></span>
  
- <span data-ttu-id="3d05b-151">停用瀏覽器附加元件，可能會影響效能或實際上並不需要。</span><span class="sxs-lookup"><span data-stu-id="3d05b-151">Disable browser add-ons that might impact performance or that you don't really need.</span></span>
    
- <span data-ttu-id="3d05b-152">增加快取大小的網際網路暫存檔。</span><span class="sxs-lookup"><span data-stu-id="3d05b-152">Increase the cache size for your temporary internet files.</span></span>
    
-  <span data-ttu-id="3d05b-p111">一旦您已登入您的工作或學校帳戶，讓瀏覽器視窗保持開啟在一天。您可以開啟其他索引標籤及 windows 而再次登入。如果您需要登入另一個帳戶，請使用私人瀏覽。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p111">Once you have signed into your work or school account, keep the browser window open throughout the day. You can open other tabs and windows without signing in again. If you need to sign in to another account, use Private Browsing.</span></span> 
    
- <span data-ttu-id="3d05b-p112">一旦每一頁為已下載的與開啟，保持其開啟使用定位點。很容易瀏覽] 索引標籤中與使用頁面稍後一天。只有當您需要在該頁面上的最新資料重新整理頁面。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p112">Once each page is downloaded and open, keep them open by using tabs. It's easy to navigate between tabs and use the page later on in the day. Refresh a page only if you need the latest data on that page.</span></span>
    
- <span data-ttu-id="3d05b-159">如果頁面時間太長開啟，停止頁面下載 （按 esc 鍵），並再重新整理頁面 （按 F5）。</span><span class="sxs-lookup"><span data-stu-id="3d05b-159">If a page is taking too long to open, stop the page download (press ESC) and then refresh the page (press F5).</span></span> 
    
-  <span data-ttu-id="3d05b-p113">請儘可能減少的來回至 Office 365。例如，而不是透過清單或文件庫的分頁、 使用搜尋大型文件庫中找出檔案和篩選要直接取得結果的清單中您想要。或者，建立最小化] 頁面載入時間的檢視。如需詳細資訊，請參閱[管理大型清單與 Office 365 中的文件庫](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p113">When possible, reduce round trips to Office 365. For example, rather than paging through lists or libraries, use search to locate files in a large library and filtering in a list to get directly to the results you want. Or, create views that minimize page load time. For more information, see [Manage large lists and libraries in Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).</span></span>
    
- <span data-ttu-id="3d05b-p114">如果視訊效能低落，您可能可以下載影片，並觀看裝置上。下載連結可能可以聯繫，或您可以以滑鼠右鍵按一下影片的連結，然後選取 [**另存成的目標**。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p114">If video performance is poor, you may be able to download the video and watch it on your device. A download link may be available, or you may be able to right click the video link, and select **Save Target as**.</span></span> 
    
 <span data-ttu-id="3d05b-166">**瀏覽器特有**</span><span class="sxs-lookup"><span data-stu-id="3d05b-166">**Browser-specific**</span></span>
  
<span data-ttu-id="3d05b-167">以下是一些您特定的瀏覽器的建議：</span><span class="sxs-lookup"><span data-stu-id="3d05b-167">Here are some suggestions for your specific browser:</span></span>
  
- <span data-ttu-id="3d05b-p115">**Internet Explorer**透過舊版升級至 Internet Explorer 版本 11 或更新版本明顯的效能改進。如需詳細資訊，請參閱 ＜ [Fix Internet Explorer 的問題](https://support.microsoft.com/mats/ie_performance_and_safety)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p115">**Internet Explorer** Upgrade to Internet Explorer Version 11 or later for substantial performance improvements over previous versions. For more information, see [ Fix Internet Explorer issues ](https://support.microsoft.com/mats/ie_performance_and_safety).</span></span>
    
- <span data-ttu-id="3d05b-170">**FireFox**如需詳細資訊，請參閱[Firefox 緩慢或會停止運作](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-170">**FireFox**For more information, see [Firefox is slow or stops working](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging).</span></span>
    
- <span data-ttu-id="3d05b-171">**safari**如需詳細資訊，請參閱[Apple-Safari](https://www.apple.com/safari/)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-171">**Safari** For more information, see [Apple - Safari](https://www.apple.com/safari/).</span></span>
    
- <span data-ttu-id="3d05b-172">**chrome**如需詳細資訊，請參閱[Chrome 協助](https://support.google.com/chrome/?hl=en)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-172">**Chrome** For more information, see [Chrome Help](https://support.google.com/chrome/?hl=en).</span></span>
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a><span data-ttu-id="3d05b-173">使用 Outlook 和 Outlook Web App 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-173">Best practices for using Outlook and Outlook Web App</span></span>

<span data-ttu-id="3d05b-p116">讀取、 寫入、 和組織的電子郵件屬於 big 所有人的一天。Outlook 和 Outlook Web App (OWA) 提供離線支援。使用智慧型手機上的電子郵件應用程式是其他有用的替代方式。使用最符合您需求的下列選項：</span><span class="sxs-lookup"><span data-stu-id="3d05b-p116">Reading, writing, and organizing email is a big part of everyone's day. Both Outlook and Outlook Web App (OWA) offer offline support. Using an email app on your smart phone is another useful alternative. Use the following options that best fit your needs:</span></span>
  
- <span data-ttu-id="3d05b-178">透過舊版升級至 Outlook 2013 SP1 或更新版本的明顯的效能改進。</span><span class="sxs-lookup"><span data-stu-id="3d05b-178">Upgrade to Outlook 2013 SP1 or later for substantial performance improvements over previous versions.</span></span> 
    
-  <span data-ttu-id="3d05b-p117">Outlook Web App 可讓您建立離線郵件、 連絡人和行事曆事件時 OWA 下一步是上傳能夠連線至 Office 365。如需設定及使用 OWA 以離線模式的詳細資訊，請參閱[使用 Outlook Web App 離線](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p117">Outlook Web App lets you create offline messages, contacts, and calendar events that are uploaded when OWA is next able to connect to Office 365. For more information about setting up and using OWA in offline mode, see [Using Outlook Web App offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).</span></span>
    
- <span data-ttu-id="3d05b-p118">Outlook 可讓您在快取模式下，在其中自動連線盡可能運作。您可以讓 Outlook 下載整個信箱或只是它的一部分。如需詳細資訊，請參閱[開啟快取 Exchange 模式](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c)，並[在 Outlook 中離線工作](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p118">Outlook lets you work in cached mode, in which it automatically connects whenever possible. You can have Outlook download your entire mailbox, or just a portion of it. For more information, see [Turn on Cached Exchange Mode](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) and [Work offline in Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).</span></span> 
    
- <span data-ttu-id="3d05b-p119">Outlook 也會提供離線模式。若要使用此項，您必須先將設定快取模式，讓您的帳戶資訊會複製到您的電腦。在離線模式中，Outlook 會嘗試連線使用傳送及接收設定]，或者當您以手動方式設定它在線上運作。如需詳細資訊，請參閱[離線工作以避免資料連線費用](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282)、[變更傳送及接收設定離線工作時](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)，及[從離線工作以線上切換](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p119">Outlook also offers an offline mode. To use this, you must first set up cached mode so that information from your account is copied down to your computer. In offline mode, Outlook will try to connect using the send and receive settings, or when you manually set it to work online. For more information, see [Work offline to avoid data connection charges](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [Change send and receive settings when you work offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a), and [Switch from working offline to online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).</span></span> 
    
- <span data-ttu-id="3d05b-188">如果您有智慧型手機，您可以使用它來分辨您的電子郵件和行事曆透過電話電信業者的網路。</span><span class="sxs-lookup"><span data-stu-id="3d05b-188">If you have a smart phone, you can use it to triage your email and calendar over your phone carrier's network.</span></span> 
    
> [!NOTE]
> <span data-ttu-id="3d05b-p120">以下是一些指導何時使用 Outlook 或 OWA。若磁碟空間不是在裝置上的問題，Outlook 會有完整的功能與可能最適合您。如果在裝置上發生問題的磁碟空間，請考慮使用 OWA 的子集的功能，但也適用於最適合在線上的情況下。當然，您可以使用其中一個因為以及共同作業。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p120">Here is some guidance on when to use Outlook or OWA. If disk space is not an issue on your device, Outlook has a full set of features and might work best for you. If disk space is an issue on your device, consider using OWA which has a subset of features, but also works best in an online situation. Of course, you can use either because they work well together.</span></span> 
  
## <a name="best-practices-for-using-onedrive-for-business"></a><span data-ttu-id="3d05b-193">使用 OneDrive for Business 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-193">Best practices for using OneDrive for Business</span></span>

<span data-ttu-id="3d05b-p121">OneDrive for Business 的設計為基礎而向上線上與離線工作與您的檔案。一旦您設定它，變更同步處理發生自動且可靠有及每當您幫助他們。如果網路速度很慢，您可以使用離線版的檔案。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p121">OneDrive for Business is designed from the ground up to work with your files online and offline. Once you set it up, synchronization of changes occurs automatically and reliably wherever and whenever you make them. If the network is slow, you can work with the offline version of the files.</span></span>
  
<span data-ttu-id="3d05b-p122">OneDrive for Business 同步處理應用程式皆可使用 Office 2013 （Professional Plus] 或 [Standard 版本） 或包含 Office 2013 應用程式的 Office 365 訂閱。如果您沒有 Office 2013，您可以[下載](https://support.microsoft.com/kb/2903984)OneDrive for Business sync app 免費。此應用程式也會比使用**在瀏覽器中開啟**] 或 [**上傳**命令快一點。如需詳細資訊，請參閱[設定電腦以將 OneDrive for Business 檔案在 Office 365 同步處理](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p122">The OneDrive for Business sync app is available with Office 2013 (Professional Plus, or Standard editions), or an Office 365 subscription that includes Office 2013 applications. If you don't have Office 2013, you can [download](https://support.microsoft.com/kb/2903984) the OneDrive for Business sync app for free. This app is also faster than using the **Open in Explorer** or **Upload** commands. For more information, see [Set up your computer to sync your OneDrive for Business files in Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).</span></span>
  
<span data-ttu-id="3d05b-201">以下是使用 OneDrive for Business sync app 一些其他指引：</span><span class="sxs-lookup"><span data-stu-id="3d05b-201">Here's some additional guidance for using the OneDrive for Business sync app:</span></span>
  
- <span data-ttu-id="3d05b-202">如果您第一次同步的大型文件庫，開始同步處理期間峰時間，例如隔天。</span><span class="sxs-lookup"><span data-stu-id="3d05b-202">If you're syncing a large library for the first time, start the sync during off hours, for example, overnight.</span></span> 
    
- <span data-ttu-id="3d05b-p123">您可以使用[停止同步與 OneDrive for Business 應用程式的文件庫](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330)功能暫時停止次更新。不過，以避免佇列大型簡短的期間，例如幾個小時一次使用此功能的更新和風險降至最低的合併衝突如果數個人員處理相同文件編號。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p123">You can use the [Stop syncing a library with the OneDrive for Business app](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) feature to temporarily stop syncing updates. However, use this feature for brief periods, such as a few hours at a time, to avoid queuing large numbers of updates, and to minimize the risk of merge conflicts if several people work on the same document.</span></span> 
  
## <a name="best-practices-for-using-onenote"></a><span data-ttu-id="3d05b-205">使用 OneNote 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-205">Best practices for using OneNote</span></span>

<span data-ttu-id="3d05b-p124">每個 SharePoint 小組網站具有內建的 OneNote 筆記本及您可以輕鬆地建立您自己。OneNote 是更好的方式來收集所需以完成工作每天的即時資訊。例如，許多小組使用 OneNote 作為集合點每週的會議、 專案備忘稿、 想法、 計劃及狀態報表。剛好即可將這項異質資訊組織使用頁面] 區段中，且索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p124">Every SharePoint team site has a built-in OneNote notebook and you can easily create your own. OneNote is a great way to collect timely information that you need every day to get tasks done. For example, many teams use OneNote as a collection point for weekly meetings, project notes, ideas, plans, and status reports. You can neatly organize this disparate information by using pages, sections, and tabs.</span></span>
  
<span data-ttu-id="3d05b-p125">但 OneNote 之美您可以存取內容從幾乎任何裝置是否透過桌上型電腦、 筆記型電腦、 平板電腦或智慧型手機。並沒有擔心在儲存或因為 OneNote 在於您同步處理。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p125">But the beauty of OneNote is that you can access the content from virtually any device, whether a desktop, a laptop, a tablet, or a smart phone. And you don't have to worry about saving or synchronizing because OneNote does it for you.</span></span> 
  
<span data-ttu-id="3d05b-212">如需詳細資訊，請參閱 ＜ [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-212">For more information, see [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/).</span></span>
  
## <a name="best-practices-for-using-lync-online"></a><span data-ttu-id="3d05b-213">使用 Lync Online 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-213">Best practices for using Lync Online</span></span>

<span data-ttu-id="3d05b-214">以下是您的網路速度過慢時使用 Lync Online 的一般指導方針：</span><span class="sxs-lookup"><span data-stu-id="3d05b-214">The following are general guidelines for using Lync Online when your network is slow:</span></span>
  
- <span data-ttu-id="3d05b-215">使用立即訊息每當您可以因為它也在慢速網路上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="3d05b-215">Use instant messaging whenever you can because it works well on a slow network.</span></span>
    
- <span data-ttu-id="3d05b-216">避免讓電話透過虛擬私人網路 (VPN) 或遠端存取服務 (RAS) 連線。</span><span class="sxs-lookup"><span data-stu-id="3d05b-216">Avoid making phone calls over a virtual private network (VPN) or remote access service (RAS) connections.</span></span>
    
- <span data-ttu-id="3d05b-p126">請確定您的音訊裝置為 「 已核准。如需詳細資訊，請參閱[合格電話和裝置的 Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p126">Make sure your audio device is approved. For more information, see [Phones and Devices Qualified for Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944).</span></span>
    
-  <span data-ttu-id="3d05b-p127">使用 PowerPoint online 簡報中時, 降低的大小與投影片的複雜性。如需詳細資訊，請參閱[改進您的簡報的效能秘訣](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p127">When using PowerPoint in an online presentation, reduce the size and complexity of the slides. For more information, see [Tips for improving the performance of your presentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).</span></span>
    
- <span data-ttu-id="3d05b-p128">盡可能共用監視器，而不是程式或桌面。如需詳細資訊，請參閱[共用桌面或 Lync 中的程式](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p128">Whenever possible, share a monitor, instead of a program or a desktop. For more information, see [Share your desktop or a program in Lync](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842).</span></span>
    
- <span data-ttu-id="3d05b-p129">而不是共用、 送出 PowerPoint 投影片隨時為會議要求附件讓出席者檢視使用者的用戶端裝置上的投影片。如需詳細資訊，請參閱 ＜ [Set up Lync 會議](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p129">Instead of sharing, send out the PowerPoint slides ahead of time as a meeting request attachment so attendees view the slides on their client device. For more information, see [Set up a Lync Meeting](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d).</span></span>
    
-  <span data-ttu-id="3d05b-p130">視訊的效能是非常密切的網路效能。避免使用視訊如果您的網路速度很慢。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p130">Video performance is very dependent on network performance. Avoid using video if your network is slow.</span></span> 
    
<span data-ttu-id="3d05b-227">如需詳細資訊，請參閱[不佳的音訊或視訊品質的 Lync Online](https://support.microsoft.com/kb/2386655)和[Lync 2013 的更新的速度過慢畫面](https://support.microsoft.com/kb/2958375)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-227">For more information, see [Poor audio or video quality in Lync Online](https://support.microsoft.com/kb/2386655) and [Slow screen update in Lync 2013](https://support.microsoft.com/kb/2958375).</span></span>
  
## <a name="best-practices-for-using-sharepoint-lists"></a><span data-ttu-id="3d05b-228">使用 SharePoint 清單的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-228">Best practices for using SharePoint lists</span></span>

<span data-ttu-id="3d05b-p131">透過使用清單資料離線"快轉"、 分析、 或報告資料是絕佳慢速網路的影響降到最低。您可以從讀取及寫入大部分列出 Microsoft Access 2013 的連結給他們。您也可以將清單匯出至 Excel 表格中，會建立 Excel 表格與清單之間的單向的資料連線。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p131">Working with list data offline to "scrub", analyze, or report data is a great way to minimize the impact of a slow network. You can read and write most lists from Microsoft Access 2013 by linking to them. You can also export a list to an Excel Table, which creates a one-way data connection between the Excel table and the list.</span></span>
  
<span data-ttu-id="3d05b-p132">此外，如果啟動 Access Services 功能，然後您可以使用許多詳細資料超過清單檢視臨界值，預設最多 50000 個項目。Access 2013 和 Excel 2013 自動處理小型的批次中的清單資料並再重新組合的資料，讓使用更多資料超過清單檢視臨界值，而不會有不良影響的服務效能的技術其他使用者。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p132">Furthermore, if the Access Services feature is activated, then you can work with considerably more data than the List View Threshold, up to 50,000 items by default. Both Access 2013 and Excel 2013 automatically process list data in small batches and then reassemble the data, a technique that enables working with substantially more data than the List View Threshold, and without adversely impacting the service performance of other users.</span></span> 
  
<span data-ttu-id="3d05b-234">如需詳細資訊，請參閱[管理大型清單與 Office 365 中的文件庫](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)中的 「 更多關於管理大型清單 」 一節。</span><span class="sxs-lookup"><span data-stu-id="3d05b-234">For more information, see the section "More about managing large lists" in [Manage large lists and libraries in Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).</span></span>
  
## <a name="best-practices-for-customizing-web-pages"></a><span data-ttu-id="3d05b-235">自訂網頁的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-235">Best practices for customizing web pages</span></span>

<span data-ttu-id="3d05b-p133">當您自訂網頁時，可能不經意會導致不佳的效能與頁。數個因素可以影響，例如複雜度及大小] 頁面上、 多少網頁組件會新增最初顯示多少個清單或文件庫項目，及程式碼] 頁面上的方式。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p133">When you customize a web page, you may inadvertently cause poor performance with the page. A number of factors can have an impact, such as the complexity and size of the page, how many web parts are added, how many list or library items are initially displayed, and the way you code the page.</span></span>
  
<span data-ttu-id="3d05b-238">如需詳細資訊，請參閱 ＜[調整 SharePoint Online 的效能](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-238">For more information, see [Tune SharePoint Online performance](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).</span></span>
  
## <a name="best-practices-for-using-project-online"></a><span data-ttu-id="3d05b-239">使用 Project Online 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="3d05b-239">Best practices for using Project Online</span></span>

<span data-ttu-id="3d05b-240">下列指導方針可協助增進網路效能。</span><span class="sxs-lookup"><span data-stu-id="3d05b-240">The following guidelines can help improve network performance.</span></span>
  
- <span data-ttu-id="3d05b-p134">Project Online 和 SharePoint Online 需要同步處理功能，可能會很耗時。如果您的專案小組低周轉，停用來增進發佈專案和專案詳細資料頁面效能的專案網站同步處理。限制的實際需要使用系統及監視大型群組的同步處理後的任何潛在的權限問題的資源群組的 Active Directory 同步處理。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p134">Project Online and SharePoint Online require synchronization, which can be time consuming. If your project teams have low turnover, disable Project Site Sync to improve the Project Publish and Project Detail Pages performance. Limit Active Directory sync to groups of resources that actually need to use the system, and monitor any potential permission issues after the synchronization of large groups.</span></span> 
    
- <span data-ttu-id="3d05b-p135">如果您的組織使用專案網站，建立這些隨選而不是自動。這會加速的第一個發佈經驗及可以避免建立不必要的網站及內容。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p135">If your organization uses project sites, create them on demand rather than automatically. This speeds up the first publishing experience and avoids creating unnecessary sites and content.</span></span>
    
- <span data-ttu-id="3d05b-p136">專案詳細資料頁面 (PDP) 可觸發整個專案重新計算並開始進行的工作流程動作、 兩者都可以是效能耗用資源的作業。若要避免觸發兩個更新程序，同時在相同的 PDP，避免更新行事曆 （開始日期、 完成日期、 狀態日期] 及 [欄位目前的日期） 和非排程欄位 （專案名稱、 描述與擁有者）。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p136">Project Detail Pages (PDP) can trigger a recalculation of the entire project and kick off workflow actions, both of which can be performance-intensive operations. To avoid triggering two update processes at the same time on the same PDP, avoid updating the calendar fields (Start date, Finish date, Status date, and Current date) and the non-scheduled fields (project name, description, and owner).</span></span> 
    
- <span data-ttu-id="3d05b-p137">減少網頁組件與顯示在每個 PDP 的自訂欄位的數目。建立專用的 PDP 使用唯一欄位需要更新以提升負載然後節省時間。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p137">Reduce the number of Web Parts and custom fields displayed on each PDP. Create a dedicated PDP with the only fields that require updating to improve load and save time.</span></span> 
    
- <span data-ttu-id="3d05b-250">當您使用 OData 進行報表功能時，限制查詢執行階段使用伺服器端篩選的資料的量。</span><span class="sxs-lookup"><span data-stu-id="3d05b-250">When you use OData for reporting, limit the amount of data you query at runtime by using server-side filtering.</span></span>
    
<span data-ttu-id="3d05b-251">如需詳細資訊，請參閱 ＜[調整 Project Online 的效能](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-251">For more information, see [Tune Project Online performance](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).</span></span>
  
## <a name="whats-the-best-way-to-report-problems"></a><span data-ttu-id="3d05b-252">什麼是報告問題的最佳方式？</span><span class="sxs-lookup"><span data-stu-id="3d05b-252">What's the best way to report problems?</span></span>

<span data-ttu-id="3d05b-p138">Microsoft 持續改善藉由監視網路測量的頻寬的 Office 365 的整體效能並改善頁面載入時間、 減少磁碟 I/O、 重新設計.net 的延遲頁面使用最少下載策略中，新增至資料中心的硬體和新增多個資料中心。如需檢查您的目前狀態和報告問題的詳細資訊，請參閱 ＜[檢視服務的狀態](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx)。</span><span class="sxs-lookup"><span data-stu-id="3d05b-p138">Microsoft continually improves the overall performance of Office 365 by monitoring the network, measuring bandwidth and latency, improving page load time, reducing disk I/O, redesigning pages to use Minimal Download Strategy, adding hardware to data centers and adding more data centers. For more information about checking your current status and reporting issues, see [View the status of your services](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3d05b-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d05b-255">See also</span></span>

[<span data-ttu-id="3d05b-256">Office 365 的網路規劃和效能調整</span><span class="sxs-lookup"><span data-stu-id="3d05b-256">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="3d05b-257">Microsoft 虛擬學院課程 （英文)-Office 365 績效管理</span><span class="sxs-lookup"><span data-stu-id="3d05b-257">Microsoft Virtual Academy course—Office 365 performance management</span></span>](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[<span data-ttu-id="3d05b-258">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="3d05b-258">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
<span data-ttu-id="3d05b-259">[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)</span><span class="sxs-lookup"><span data-stu-id="3d05b-259">[Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)</span></span>

