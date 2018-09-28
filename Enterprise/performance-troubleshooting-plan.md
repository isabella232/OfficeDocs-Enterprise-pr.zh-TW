---
title: Office 365 的效能疑難排解規劃
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 4/26/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
description: 您需要知道要找出並修正 lags、 擱置，與 SharePoint Online、 OneDrive for Business、 Exchange Online 或 Skype 商務 online 與您的用戶端電腦之間的效能低落所採取的步驟嗎？連絡支援之前，這篇文章可協助您疑難排解 Office 365 的效能問題及即使修正的一些常見的問題。
ms.openlocfilehash: 0e588d35ff6caaa0796092bb2f964bced15f4e47
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975181"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a><span data-ttu-id="6e588-104">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="6e588-104">Performance troubleshooting plan for Office 365</span></span>

<span data-ttu-id="6e588-p102">您需要知道要找出並修正 lags、 擱置，與 SharePoint Online、 OneDrive for Business、 Exchange Online 或 Skype 商務 online 與您的用戶端電腦之間的效能低落所採取的步驟嗎？連絡支援之前，這篇文章可協助您疑難排解 Office 365 的效能問題及即使修正的一些常見的問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-p102">Do you need to know the steps to take to identify and fix lags, hangs, and slow performance between SharePoint Online, OneDrive for Business, Exchange Online, or Skype for Business Online, and your client computer? Before you call support, this article can help you troubleshoot Office 365 performance issues and even fix some of the most common issues.</span></span>
  
<span data-ttu-id="6e588-p103">本文是實際範例動作計劃可用來擷取效能問題的相關的寶貴資料原狀新鮮事。本文也會包含一些前幾名問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-p103">This article is actually a sample action plan that you can use to capture valuable data about your performance issue as it's happening. Some top issues are also included in this article.</span></span>
    
<span data-ttu-id="6e588-109">如果您是新的網路效能並想要讓監控用戶端機器與 Office 365 之間的效能的長期計劃，請查看[Office 365 效能調整及疑難排解-管理員及 IT 專業人員](performance-tuning-using-baselines-and-history.md)。</span><span class="sxs-lookup"><span data-stu-id="6e588-109">If you're new to network performance and want to make a long term plan to monitor performance between your client machines and Office 365, take a look at [Office 365 performance tuning and troubleshooting - Admin and IT Pro](performance-tuning-using-baselines-and-history.md).</span></span>
  
## <a name="sample-performance-troubleshooting-action-plan"></a><span data-ttu-id="6e588-110">範例效能疑難排解動作計劃</span><span class="sxs-lookup"><span data-stu-id="6e588-110">Sample performance troubleshooting action plan</span></span>

<span data-ttu-id="6e588-p104">此巨集指令計劃包含兩個部分 ；準備階段，並記錄時期。如果您正，有效能問題，您需要執行資料收集您可以啟動立即使用此計劃。</span><span class="sxs-lookup"><span data-stu-id="6e588-p104">This action plan contains two parts; a preparation phase, and a logging phase. If you have a performance problem right now, and you need to do data collection, you can start using this plan right away.</span></span>
  
 <span data-ttu-id="6e588-113">**準備用戶端電腦**</span><span class="sxs-lookup"><span data-stu-id="6e588-113">**Prepare the client computer**</span></span>
  
- <span data-ttu-id="6e588-p105">尋找可重現效能問題的用戶端電腦。這部電腦將用於疑難排解期間。</span><span class="sxs-lookup"><span data-stu-id="6e588-p105">Find a client computer that can reproduce the performance problem. This computer will be used during the course of troubleshooting.</span></span>
    
- <span data-ttu-id="6e588-116">記下會導致效能問題，才能讓您準備好要測試時所發生的步驟。</span><span class="sxs-lookup"><span data-stu-id="6e588-116">Write down the steps that cause the performance problem to happen so you're ready when it comes time to test.</span></span>
    
- <span data-ttu-id="6e588-117">收集和記錄資訊的工具安裝：</span><span class="sxs-lookup"><span data-stu-id="6e588-117">Install tools for gathering and recording information:</span></span>
    
  - <span data-ttu-id="6e588-118">安裝[Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) （或使用相等的網路追蹤工具）。</span><span class="sxs-lookup"><span data-stu-id="6e588-118">Install [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) (or use an equivalent network tracing tool).</span></span> 
    
  - <span data-ttu-id="6e588-119">安裝可用的基本版本的[HTTPWatch](https://www.httpwatch.com/download/) （或使用相等的網路追蹤工具）。</span><span class="sxs-lookup"><span data-stu-id="6e588-119">Install the free Basic Edition of [HTTPWatch](https://www.httpwatch.com/download/) (or use an equivalent network Tracing tool).</span></span> 
    
  - <span data-ttu-id="6e588-120">使用螢幕錄製或執行以保留記錄的測試期間所採取的步驟而言具有 Windows Vista 和更新版本、 步驟錄製器 (PSR.exe)。</span><span class="sxs-lookup"><span data-stu-id="6e588-120">Use a screen recorder or run the Steps Recorder (PSR.exe) that comes with Windows Vista and later, in order to keep a record of the steps you take during testing.</span></span>
    
 <span data-ttu-id="6e588-121">**記錄檔的效能問題**</span><span class="sxs-lookup"><span data-stu-id="6e588-121">**Log the performance issue**</span></span>
  
- <span data-ttu-id="6e588-122">關閉所有無關的網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6e588-122">Close all extraneous Internet browsers.</span></span>
    
- <span data-ttu-id="6e588-123">啟動步驟錄製器或另一個畫面中錄製。</span><span class="sxs-lookup"><span data-stu-id="6e588-123">Start the Steps Recorder, or another screen recorder.</span></span>
    
- <span data-ttu-id="6e588-124">啟動 Netmon 擷取 （或網路追蹤工具）。</span><span class="sxs-lookup"><span data-stu-id="6e588-124">Start your Netmon capture (or network tracing tool).</span></span>
    
- <span data-ttu-id="6e588-125">輸入 ipconfig /flushdns 來清除您在用戶端電腦從命令列上的 DNS 快取。</span><span class="sxs-lookup"><span data-stu-id="6e588-125">Clear your DNS cache on the client computer from the command line by typing ipconfig /flushdns.</span></span>
    
- <span data-ttu-id="6e588-126">啟動新的瀏覽器工作階段並開啟 HTTPWatch。</span><span class="sxs-lookup"><span data-stu-id="6e588-126">Start a new browser session and turn on HTTPWatch.</span></span>
    
- <span data-ttu-id="6e588-127">選用： 如果您要測試 Exchange Online、 Exchange 用戶端效能 Analyzer 工具從執行 Office 365 系統管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6e588-127">Optional: If you are testing Exchange Online, run the Exchange Client Performance Analyzer tool from the Office 365 admin console.</span></span>
    
- <span data-ttu-id="6e588-128">重現會導致效能問題的確切步驟。</span><span class="sxs-lookup"><span data-stu-id="6e588-128">Reproduce the exact steps that cause the performance issue.</span></span>
    
- <span data-ttu-id="6e588-129">停止在 Netmon 或其他工具追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-129">Stop your Netmon or other tool's trace.</span></span>
    
- <span data-ttu-id="6e588-130">在命令列上執行追蹤路由傳送至您的 Office 365 訂閱輸入下列命令後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="6e588-130">At the command line, run a trace route to your Office 365 subscription by typing the following command and then pressing ENTER:</span></span>
    
    `tracert \< *subscriptionname*  \>.onmicrosoft.com` 
    
- <span data-ttu-id="6e588-p106">停止步驟錄製並儲存的視訊。請務必包含的日期和時間擷取及是否示範良好或不正確的效能。</span><span class="sxs-lookup"><span data-stu-id="6e588-p106">Stop the Steps Recorder and save the video. Be sure to include the date and time of the capture and whether it demonstrates good or bad performance.</span></span>
    
- <span data-ttu-id="6e588-p107">儲存追蹤檔案。同樣地，請務必包含的日期和時間擷取及是否示範良好或不正確的效能。</span><span class="sxs-lookup"><span data-stu-id="6e588-p107">Save the trace files. Again, be sure to include the date and time of the capture and whether it demonstrates good or bad performance.</span></span>
    
<span data-ttu-id="6e588-p108">如果您不熟悉執行本文中提及的工具，請不要擔心因為我們接下來提供這些步驟。如果您已經習慣來執行此類網路擷取，您可以略過[如何收集基準線](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)，其中會說明篩選以及讀取記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6e588-p108">If you're not familiar with running the tools mentioned in this article, don't worry because we provide those steps next. If you're accustomed to doing this kind of network capturing, you can skip to [How to collect baselines](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), which describes filtering and reading the logs.</span></span> 
  
## <a name="flush-the-dns-cache-first"></a><span data-ttu-id="6e588-137">先清除 DNS 快取</span><span class="sxs-lookup"><span data-stu-id="6e588-137">Flush the DNS Cache first</span></span>

<span data-ttu-id="6e588-p109">為何？來取出的 DNS 快取清除中您正在測試開頭乾淨的版面。清除快取，您正在重新設定 DNS 解決程式內容的最新的項目。請記得 flush 不會移除主機檔案項目。如果您是廣泛使用主機檔案項目，您應該將這些項目複製至另一個目錄中的檔案，然後清空主機檔案。</span><span class="sxs-lookup"><span data-stu-id="6e588-p109">Why? By flushing out the DNS cache you're starting your tests with a clean slate. By clearing the cache, you're resetting the DNS resolver contents to the most up-to-date entries. Remember that a flush does not remove HOSTs file entries. If you use HOST file entries extensively, you should copy those entries out to a file in another directory and then empty the HOST file.</span></span>
  
 <span data-ttu-id="6e588-143">**清除 DNS 解決程式快取**</span><span class="sxs-lookup"><span data-stu-id="6e588-143">**Flush your DNS resolver cache**</span></span>
  
1. <span data-ttu-id="6e588-144">開啟命令提示字元 (**開始**任一\>**執行** \> **cmd**或**Windows 鍵** \> **cmd**)。</span><span class="sxs-lookup"><span data-stu-id="6e588-144">Open the command prompt, (either **Start** \> **Run** \> **cmd** or **Windows key** \> **cmd**).</span></span>
    
2. <span data-ttu-id="6e588-145">輸入下列命令並按 ENTER：`ipconfig /flushdns`</span><span class="sxs-lookup"><span data-stu-id="6e588-145">Type the following command and press ENTER: `ipconfig /flushdns`</span></span>
    
## <a name="netmon"></a><span data-ttu-id="6e588-146">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-146">Netmon</span></span>

<span data-ttu-id="6e588-p110">Microsoft 的網路監視工具 ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) 分析封包的傳遞在網路上的電腦之間的流量。藉由使用 Netmon 追蹤與 Office 365 您可以擷取、 檢視、 流量和閱讀封包標頭、 識別而且裝置、 檢查重要設定網路硬體上的，尋找捨棄封包，並遵循流量傳送之間上您公司的電腦網路與 Office 365。因為已加密的流量實際本文，亦即其 （透過 SSL/TLS 的連接埠 443 上旅行您無法讀取所傳送的檔案。而是您要取得之路徑的封包取得可協助您追蹤問題行為篩選的追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p110">Microsoft's Network Monitoring tool ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analyzes packets, that is traffic, that passes between computers on networks. By using Netmon to trace traffic with Office 365 you can capture, view, and read packet headers, identify intervening devices, check important settings on network hardware, look for dropped packets, and follow the flow of traffic between computers on your corporate network and Office 365. Because the actual body of the traffic is encrypted, that is, it(travels on port 443 via SSL/TLS, you can't read the files being sent. Instead, you get an unfiltered trace of the path that the packet takes which can help you track down the problem behavior.</span></span>
  
<span data-ttu-id="6e588-p111">請確定您不要在此時間套用篩選器。而完成的步驟執行，並示範之前停止追蹤和儲存的問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-p111">Be sure you don't apply a filter at this time. Instead, run through the steps and demonstrate the problem before stopping the trace and saving.</span></span>
  
<span data-ttu-id="6e588-153">安裝 Netmon 3.4 之後，請開啟工具並執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6e588-153">After you install Netmon 3.4, open the tool and take these steps:</span></span>
  
 <span data-ttu-id="6e588-154">**取得 Netmon 追蹤並重現問題**</span><span class="sxs-lookup"><span data-stu-id="6e588-154">**Take a Netmon trace and reproduce the issue**</span></span>
  
1. <span data-ttu-id="6e588-155">啟動 Netmon 3.4。</span><span class="sxs-lookup"><span data-stu-id="6e588-155">Launch Netmon 3.4.</span></span>
    
    <span data-ttu-id="6e588-p112">在 **[開始**] 頁面上有三個窗格：**最近擷取**、**選取 [網路**和**與 Microsoft Network Monitor 3.4 快速入門。請注意**。[選取 [網路] 面板中也會提供您可以擷取預設網路的清單。請務必張網路卡此處所選。</span><span class="sxs-lookup"><span data-stu-id="6e588-p112">There are three panes on the **Start** page: **Recent Captures**, **Select Networks**, and the **Getting Started with Microsoft Network Monitor 3.4. Notice**. The Select Networks panel will also give you a list of the default networks from which you can capture. Be sure that network cards are selected here.</span></span>
    
2. <span data-ttu-id="6e588-p113">按一下上方的 [**開始**] 頁面上的 [**新擷取**。這會新增新的索引標籤旁呼叫**擷取 1**的**開始**頁面索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p113">Click **New Capture** at the top of the **Start** page. This adds a new tab beside the **Start** page tab called **Capture 1**.</span></span>
    
    ![Nemon 的使用者介面與新擷取、 開始，並停止醒目提示] 按鈕。](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)
  
3. <span data-ttu-id="6e588-162">要採取簡單擷取、 按一下 [**開始**] 工具列上。</span><span class="sxs-lookup"><span data-stu-id="6e588-162">To take a simple capture, click **Start** on the toolbar.</span></span> 
    
4. <span data-ttu-id="6e588-163">重現呈現的效能問題的步驟。</span><span class="sxs-lookup"><span data-stu-id="6e588-163">Reproduce the steps that present a performance issue.</span></span>
    
5. <span data-ttu-id="6e588-p114">按一下 [**停止** \> **檔案** \> **另存為**。請記住授與的日期和時間的時區與提如果示範不正確或良好的效能。</span><span class="sxs-lookup"><span data-stu-id="6e588-p114">Click **Stop** \> **File** \> **Save As**. Remember to give the date and time with the time zone and to mention if it demonstrates bad or good performance.</span></span>
    
## <a name="httpwatch"></a><span data-ttu-id="6e588-166">HTTPWatch</span><span class="sxs-lookup"><span data-stu-id="6e588-166">HTTPWatch</span></span>

<span data-ttu-id="6e588-p115">[HTTPWatch](https://www.httpwatch.com/download/)有付費，以及可用的版本。免費的基本 Edition 涵蓋了這項測試所需的所有項目。HTTPWatch 監視器瀏覽器視窗中的網路流量及頁面載入時間。HTTPWatch 是要以圖形方式是指效能的 Internet Explorer 的外掛程式。分析可儲存及 HTTPWatch Studio 中檢視。</span><span class="sxs-lookup"><span data-stu-id="6e588-p115">[HTTPWatch](https://www.httpwatch.com/download/) comes in charged, and a free edition. The free Basic Edition covers everything you need for this test. HTTPWatch monitors network traffic and page load time right from your browser window. HTTPWatch is a plug-in to Internet Explorer that graphically describes performance. The analysis can be saved and viewed in HTTPWatch Studio.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="6e588-p116">如果您使用另一個瀏覽器，例如 Firefox、 Google Chrome 或您不能安裝 HTTPWatch Internet Explorer 中，開啟新的瀏覽器視窗，並鍵盤上按下 F12。您應該會看到底部的瀏覽器快顯 「 開發人員工具。如果您使用 Opera、 Web inspector 按 CTRL + SHIFT + I、 再按一下 [**網路**] 索引標籤及完成概述如下的測試。資訊會稍有不同，但仍會顯示載入時間 （毫秒）。> HTTPWatch 也是非常有用的 SharePoint Online 頁面載入時間的問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-p116">If you use another browser, such as Firefox, Google Chrome, or if you can't install HTTPWatch in Internet Explorer, open a new browser window and press F12 on your keyboard. You should see the Developer Tool pop-up at the bottom of your browser. If you use Opera, press CTRL+SHIFT+I for Web Inspector, then click the **Network** tab and complete the testing outlined below. The information will be slightly different, but load times will still be displayed in milliseconds. > HTTPWatch is also very useful for issues with SharePoint Online page load times.</span></span> 
  
 <span data-ttu-id="6e588-177">**執行 HTTPWatch 和重現問題**</span><span class="sxs-lookup"><span data-stu-id="6e588-177">**Run HTTPWatch and reproduce the issue**</span></span>
  
1. <span data-ttu-id="6e588-p117">HTTPWatch 是瀏覽器外掛程式，因此公開工具在瀏覽器中的每個版本的 Internet Explorer 稍微不同。一般而言，您可以下的命令列中找到 HTTPWatch Internet Explorer 瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="6e588-p117">HTTPWatch is a browser plug-in, so exposing the tool in the browser is slightly different for each version of Internet Explorer. Typically, you can find HTTPWatch under the Commands bar in the Internet Explorer browser. </span></span><br/><span data-ttu-id="6e588-p118">如果您沒有看到外掛程式 HTTPWatch 瀏覽器視窗中，檢查您的瀏覽器版本藉由按一下 [說明]\>有關，或者在更新版本的 Internet Explorer 中，按一下 [齒輪符號和有關 Internet Explorer。若要啟動的**命令**列、 Internet Explorer 中的功能表列上按一下滑鼠右鍵，按一下 [**命令列**。在過去，HTTPWatch 已產生關聯命令與瀏覽器列中，所以一次安裝，如果您立即未看見 （即使後重新開機） 檢查**工具**] 和圖示在工具列的圖示。請記住可自訂工具列和選項可新增到它們。</span><span class="sxs-lookup"><span data-stu-id="6e588-p118">If you don't see the HTTPWatch plug-in in your browser window, check the version of your browser by click Help \> About, or, in later versions of Internet Explorer, click the gear symbol and About Internet Explorer. To launch the **Commands** bar, right-click the menu bar in Internet Explorer and click **Commands bar**. In the past, HTTPWatch has been associated with both the Commands and the Explorer bars, so once you install, if you don't immediately see the icon (even after reboot) check **Tools**, and your toolbars for the icon. Remember that toolbars can be customized and options can be added to them.</span></span><br/>
    <span data-ttu-id="6e588-184">![Internet Explorer 命令工具列顯示 HTTPWatch 圖示。](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)</span><span class="sxs-lookup"><span data-stu-id="6e588-184">![Internet Explorer's Command toolbar with the HTTPWatch icon displayed.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)</span></span>
  
2. <span data-ttu-id="6e588-p119">啟動 HTTPWatch Internet Explorer 瀏覽器視窗中。它會顯示固定至該視窗底部瀏覽器。按一下 [**記錄**]。</span><span class="sxs-lookup"><span data-stu-id="6e588-p119">Launch HTTPWatch in an Internet Explorer browser window. It will appear docked to the browser at the bottom of that window. Click **Record**.</span></span>
    
3. <span data-ttu-id="6e588-p120">重現參與效能問題的的確切步驟。按一下 [HTTPWatch 中的 [**停止**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e588-p120">Reproduce the exact steps involved in the performance issue. Click the **Stop** button in HTTPWatch.</span></span> 
    
4. <span data-ttu-id="6e588-p121">**儲存**HTTPWatch 或**電子郵件來傳送**。請記得的檔案名稱，使其包含日期及時間的資訊和指示您的監看是否包含的示範良好或不正確的效能。</span><span class="sxs-lookup"><span data-stu-id="6e588-p121">**Save** the HTTPWatch or **Send by Email**. Remember to name the file so that it includes date and time information and an indication of whether your Watch contains a demonstration of good or bad performance.</span></span><br/><span data-ttu-id="6e588-192">![HTTPWatch，顯示 Office 365 首頁的頁面載入之 [網路] 索引標籤。](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</span><span class="sxs-lookup"><span data-stu-id="6e588-192">![HTTPWatch showing the Network tab for a page load of the Office 365 homepage.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</span></span><br/>
    <span data-ttu-id="6e588-p122">這個螢幕擷取畫面會從 HTTPWatch 專業版。您可以開啟採取基本版本的電腦上以專業版中的追蹤項目和那里讀取。額外的資訊可能可從透過該方法將追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="6e588-p122">This screen shot is from the Professional version of HTTPWatch. You can open traces taken in the Basic Version on a computer with a Professional version and read it there. Extra information may be available from the trace through that method.</span></span>
    
## <a name="problem-steps-recorder"></a><span data-ttu-id="6e588-196">問題步驟錄製</span><span class="sxs-lookup"><span data-stu-id="6e588-196">Problem Steps Recorder</span></span>

<span data-ttu-id="6e588-p123">步驟錄製或 PSR.exe，可讓您可記錄時所發生的問題。這是非常有用的工具和執行很簡單。</span><span class="sxs-lookup"><span data-stu-id="6e588-p123">Steps Recorder, or PSR.exe, allows you to record issues as they are occurring. It's a very useful tool and very simple to run.</span></span>
  
 <span data-ttu-id="6e588-199">**執行問題步驟錄製 (PSR.exe) 來記錄您的工作**</span><span class="sxs-lookup"><span data-stu-id="6e588-199">**Run Problem Steps Recorder (PSR.exe) to record your work**</span></span>
  
1. <span data-ttu-id="6e588-200">其中一個使用**啟動** \> **執行**\>輸入**PSR.exe** \> **[確定**] 或按一下 [ **Windows 鍵**\>輸入**PSR.exe** \> ，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="6e588-200">Either use **Start** \> **Run** \> type **PSR.exe** \> **OK**, or, click the **Windows Key** \> type **PSR.exe** \> and then press ENTER.</span></span> 
    
2. <span data-ttu-id="6e588-p124">小型 PSR.exe 視窗出現時，按一下 [**開始記錄**和重現重現效能問題的步驟。您可依需要，依序按一下 [**新增註解**新增註解。</span><span class="sxs-lookup"><span data-stu-id="6e588-p124">When the small PSR.exe window appears, click **Start Record** and reproduce the steps that reproduce the performance issue. You can add comments as needed, by clicking **Add Comments**.</span></span>
    
3. <span data-ttu-id="6e588-p125">當您完成步驟按一下 [**停止記錄**。如果頁面轉譯效能問題，等待轉譯之前停止錄製] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6e588-p125">Click **Stop Record** when you have completed the steps. If the performance issue is a page render, wait for the page to render before you stop the recording.</span></span> 
    
4. <span data-ttu-id="6e588-205">按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e588-205">Click **Save**.</span></span>
    
![步驟錄製或 PSR.exe 的螢幕擷取畫面。](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
<span data-ttu-id="6e588-p126">您的會記錄的日期和時間。這在 PSR Netmon 追蹤和 HTTPWatch 時間，及連結的精確度疑難排解協助。日期及時間 PSR 記錄中的可以顯示分鐘傳遞登入及瀏覽 URL 和部分的轉譯的系統管理網站，例如之間。</span><span class="sxs-lookup"><span data-stu-id="6e588-p126">The date and time is recorded for you. This links your PSR to your Netmon trace and HTTPWatch in time, and helps with precision troubleshooting. The date and time in the PSR record can show that a minute passed between the login and browsing of the URL and the partial render of the admin site, for example.</span></span>
  
## <a name="read-your-traces"></a><span data-ttu-id="6e588-210">讀取您追蹤項目</span><span class="sxs-lookup"><span data-stu-id="6e588-210">Read your traces</span></span>

<span data-ttu-id="6e588-p127">無法教導每個項目網路及疑難排解效能相關的某個人必須知道透過文章。取得在效能良好採用體驗，而您網路的運作方式與通常會執行的知識。但是很可能進位前幾名問題的清單並顯示如何工具可方便您才不致使最常見的問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-p127">It isn't possible to teach everything about network and performance troubleshooting that someone would need to know via an article. Getting good at performance takes experience, and knowledge of how your network works and usually performs. But it is possible to round up a list of top issues and show how tools can make it easier for you to eliminate the most common problems.</span></span>
  
<span data-ttu-id="6e588-p128">如果您想要挑選技能閱讀 Office 365 網站的網路追蹤，有超過定期建立的頁面載入追蹤及取得經驗閱讀這些沒有較佳老師。例如，當您有機會，載入 Office 365 服務，並追蹤程序。篩選的 DNS 流量追蹤或搜尋 FrameData 您瀏覽之服務的名稱。掃描 [取得服務載入時所發生的步驟粗略追蹤]。這可協助您了解哪些一般頁面負載的外觀和指疑難排解、 特別環繞效能比較好故障追蹤可以教您許多。</span><span class="sxs-lookup"><span data-stu-id="6e588-p128">If you want to pick up skills reading network traces for your Office 365 sites, there is no better teacher than creating traces of page loads regularly and gaining experience reading them. For example, when you have a chance, load an Office 365 service and trace the process. Filter the trace for DNS traffic, or search the FrameData for the name of the service you browsed. Scan the trace to get an idea of the steps that occur when the service loads. This will help you learn what normal page load should look like, and in the case of troubleshooting, particularly around performance, comparing good to bad traces can teach you a lot.</span></span>
  
<span data-ttu-id="6e588-p129">Netmon 使用 Microsoft Intellisense 中顯示的 [篩選] 欄位。Intellisense 或智慧型程式碼完成時，為該輪其中您在一段中輸入與下拉式選取] 方塊中顯示所有可用的選項。如果，例如您擔心 TCP 視窗調整，您可以找到您能夠在篩選器 (例如`.protocol.tcp.window < 100`) 此方法。</span><span class="sxs-lookup"><span data-stu-id="6e588-p129">Netmon uses Microsoft Intellisense in the Display filter field. Intellisense, or intelligent code completion, is that trick where you type in a period and all available options are displayed in a drop-down selection box. If, for example, you are worried about TCP window scaling, you can find your way to a filter (such as  `.protocol.tcp.window < 100`) by this means.</span></span>
  
![這個螢幕擷取畫面的 Netmon 顯示 [顯示篩選欄位] 使用 intellisense。](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
<span data-ttu-id="6e588-p130">Netmon 追蹤可以在其有許多的流量。如果您不具有讀取其經驗，很可能會是混亂開啟追蹤第一次。執行動作的第一個項重點是接收的訊號隔開中追蹤背景雜音。比照 Office 365 中，而您想要查看的流量。如果您是使用巡覽追蹤，您可能不需要此清單。</span><span class="sxs-lookup"><span data-stu-id="6e588-p130">Netmon traces can have a lot of traffic in them. If you aren't experienced with reading them, it's likely you will be overwhelmed opening the trace the first time. The first thing to do is separate the signal from the background noise in the trace. You tested against Office 365, and that's the traffic you want to see. If you are used to navigating through traces, you may not need this list.</span></span>
  
<span data-ttu-id="6e588-p131">透過 TLS，這表示本文的流量會加密和不在一般的 Netmon 追蹤可讀取一起出差用戶端與 Office 365 之間的流量。效能分析不需要知道封包中資訊的特定資訊。是，但非常興趣封包標頭及其中所包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="6e588-p131">Traffic between your client and Office 365 travels via TLS, which means that the body of the traffic will be encrypted and not readable in a generic Netmon trace. Your performance analysis doesn't need to know the specifics of the information in the packet. It is, however, very interested in packet headers and the information that they contain.</span></span>
  
 <span data-ttu-id="6e588-231">**若要取得良好的追蹤的秘訣**</span><span class="sxs-lookup"><span data-stu-id="6e588-231">**Tips to get a good trace**</span></span>
  
- <span data-ttu-id="6e588-p132">了解在用戶端電腦的 IPv4 或 IPv6 位址的值。您可以從命令提示字元處取得此輸入**IPConfig**命令後按 ENTER。了解這個位址會讓您告訴一覽是否將追蹤檔中的流量直接牽涉到您的用戶端電腦。如果沒有已知的 proxy，ping 它與要取得其 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6e588-p132">Know the value of the IPv4 or IPv6 address of your client computer. You can get this from the command prompt by typing **IPConfig** and then pressing ENTER. Knowing this address will let you tell at a glance whether the traffic in the trace directly involves your client computer. If there is a known proxy, ping it and get its IP address as well.</span></span> 
    
- <span data-ttu-id="6e588-p133">清除 DNS 解決程式快取並儘可能關閉所有瀏覽器除了您執行測試。如果您不能為達成此目的，例如，如果支援使用某些瀏覽器為基礎的工具來查看您的用戶端電腦桌面是準備篩選您追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p133">Flush your DNS resolver cache and, if possible, close all browsers except the one in which you are running your tests. If you are not able to do this, for instance, if support is using some browser-based tool to see your client computer's desktop, be prepared to filter your trace.</span></span>
    
- <span data-ttu-id="6e588-p134">在忙碌中的追蹤，找出您正在使用的 Office 365 服務。如果您已經永不或很少看到您之前的流量，這是來自其他網路雜訊分隔效能問題很有幫助步驟。有幾種執行這項作業。直接之前測試，您可以使用 ping 或 PsPing、 特定服務的 url (`ping outlook.office365.com`和/或`psping -4 microsoft-my.sharepoint.com:443`，如需範例)。您可以在也容易找到該 PsPing Netmon 追蹤 （由其處理程序名稱） 中的。會將會提供您啟動要尋找的位置。</span><span class="sxs-lookup"><span data-stu-id="6e588-p134">In a busy trace, locate the Office 365 service that you're using. If you've never or seldom seen your traffic before, this is a helpful step in separating the performance issue from other network noise. There are a few ways to do this. Directly before your test, you can use ping or, PsPing, to the URL of the specific service ( `ping outlook.office365.com` and/or  `psping -4 microsoft-my.sharepoint.com:443`, for examples) . You can also easily find that PsPing in a Netmon trace (by its process name). That will give you a place to start looking.</span></span>
    
    <span data-ttu-id="6e588-p135">如果您只使用 Netmon 追蹤問題的時間，這是外觀可以太。若要調整自行，使用類似的篩選器`ContainsBin(FrameData, ASCII, "office")`或`ContainsBin(FrameData, ASCII, "outlook")`。您可以記錄追蹤檔從您圖文框的號碼。您也可能會想要捲動到最右邊的框架摘要] 窗格，並尋找交談識別碼] 欄中的色彩。有數字表示有您也可記錄並在稍後隔離查看此特定交談 id。請記得套用任何其他篩選之前先移除此篩選器。</span><span class="sxs-lookup"><span data-stu-id="6e588-p135">If you're only using Netmon tracing at the time of the problem, that's okay too. To orient yourself, use a filter like  `ContainsBin(FrameData, ASCII, "office")` or  `ContainsBin(FrameData, ASCII, "outlook")`. You can record your frame number from the trace file. You may also want to scroll the Frame Summary pane all the way to the right and look for the Conversation ID column. There is a number indicated there for the ID of this specific conversation that you can also record and look at in isolation later. Remember to remove this filter before applying any other filtering.</span></span>
    
> [!TIP]
> <span data-ttu-id="6e588-p136">Netmon 有許多的實用的內建篩選器。嘗試上方**顯示**篩選窗格的 ["Load Filter"] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e588-p136">Netmon has a lot of helpful built-in filters. Try the "Load Filter" button at the top of the **Display** filter pane.</span></span> 
  
![在命令列上的用戶端電腦使用 PSPing 來尋找您 IP。](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![從用戶端透過 TCP 的篩選顯示在同一個 PSPing 命令 Netmon 追蹤。Flags.Syn = = 1。](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
<span data-ttu-id="6e588-p137">先熟悉您流量，並了解如何找出所需的資訊。例如，了解如何判斷哪些封包追蹤中的有您使用 （例如"Outlook") 的 Office 365 服務的第一個參照。</span><span class="sxs-lookup"><span data-stu-id="6e588-p137">Get familiar with your traffic, and learn to locate the information you need. For example, learn to determine which packet in the trace has the first reference to the Office 365 service you're using (like "Outlook").</span></span>
    
<span data-ttu-id="6e588-256">取得 Office 365 Outlook Online 做為範例流量一開始會類似：</span><span class="sxs-lookup"><span data-stu-id="6e588-256">Taking Office 365 Outlook Online as an example, the traffic begins something like this:</span></span>
  
- <span data-ttu-id="6e588-p138">標準的 DNS 查詢和相符 QueryIDs outlook.office365.com 的 DNS 回應。請務必注意針對此 turn-周圍，作為 where 世界的 Office 365 全域 DNS 的以及時間位移傳送之要求的名稱解析。在理想狀況下，為可能的而不是在全世界的半方式在本機。(這可能後面加上一些 DNS 流量 online 登入。)</span><span class="sxs-lookup"><span data-stu-id="6e588-p138">DNS Standard Query and DNS Response for outlook.office365.com with matching QueryIDs. It's important to note the Time Offset for this turn-around, as well as where in the world the Office 365 Global DNS sends the request for name resolution. Ideally, as locally as possible, rather than half-way across the world. (This may be followed by some DNS traffic the online login.)</span></span>
    
- <span data-ttu-id="6e588-261">HTTP 取得要求之狀態報表已永久移動 (301)</span><span class="sxs-lookup"><span data-stu-id="6e588-261">A HTTP GET Request whose status report Moved Permanently (301)</span></span>
    
- <span data-ttu-id="6e588-p139">包括 RWS 連線要求及 Connect 回覆 RWS 流量。（這是您進行連線的遠端 Winsock）。</span><span class="sxs-lookup"><span data-stu-id="6e588-p139">RWS Traffic including RWS Connect requests and Connect replies. (This is Remote Winsock making a connection for you.)</span></span>
    
- <span data-ttu-id="6e588-p140">TCP SYN 和 TCP SYN ACK 交談。許多的此交談中的設定會影響您的效能。</span><span class="sxs-lookup"><span data-stu-id="6e588-p140">A TCP SYN and TCP SYN/ACK conversation. A lot of the settings in this conversation impact your performance.</span></span>
    
- <span data-ttu-id="6e588-p141">再一系列的這是 TLS 信號交換與 TLS 憑證交談 TLS:TLS 流量進行。（請記住透過 SSL/TLS 加密資料）。</span><span class="sxs-lookup"><span data-stu-id="6e588-p141">Then a series of TLS:TLS traffic which is where the TLS handshake and TLS certificate conversations take place. (Remember the data is encrypted via SSL/TLS.)</span></span>
    
<span data-ttu-id="6e588-p142">所有組件的流量重要及連線，但小型的某些部分的追蹤包含資訊特別重要方面的疑難排解效能，因此我們會將焦點這些方面。此外，由於我們已完成 microsoft 編譯頂端十個清單常見問題疑難排解足夠 Office 365 效能，我們會將這些問題以及如何使用我們需要查明下一步] 工具在焦點。</span><span class="sxs-lookup"><span data-stu-id="6e588-p142">All parts of the traffic are important and connected, but small portions of the trace contain information particularly important in terms of performance troubleshooting, so we'll focus on those areas. Also, since we've done enough Office 365 performance troubleshooting at Microsoft to compile a Top Ten list of common problems, we'll focus on those issues and how to use the tools we have to root them out next.</span></span>
  
<span data-ttu-id="6e588-p143">若您尚未安裝所有好下列矩陣進行多項工具的使用。請儘可能。連結會提供給安裝點。清單會包含一般網路追蹤工具[Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865)和[Wireshark](https://www.wireshark.org/)，但使用您所感到，並在其中您正在習慣篩選網路流量任何追蹤工具。當您正在測試時，請記得：</span><span class="sxs-lookup"><span data-stu-id="6e588-p143">If you haven't installed them all ready, the matrix below makes use of several tools. Where possible. Links are provided to the installation points. The list includes common network tracing tools like [Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865) and [Wireshark](https://www.wireshark.org/), but use any tracing tool you are comfortable with, and in which you're accustomed to filtering network traffic. When you're testing, remember:</span></span>
  
-  <span data-ttu-id="6e588-p144">*關閉您的瀏覽器及測試執行只有一個瀏覽器*-這會減少擷取的整體流量。它會針對較少忙碌追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p144">*Close your browsers, and test with only one browser running*  - This will reduce the overall traffic you capture. It makes for a less busy trace.</span></span> 
    
-  <span data-ttu-id="6e588-277">*清除用戶端電腦上的您 DNS 解決程式快取*-這會提供您全新平板才會在擷取、 簡潔追蹤的啟動時。</span><span class="sxs-lookup"><span data-stu-id="6e588-277">*Flush your DNS resolver cache on the client computer*  - This will give you a clean slate when you start to take your capture, for a cleaner trace.</span></span> 
    
## <a name="some-top-issues"></a><span data-ttu-id="6e588-278">某些前幾名問題</span><span class="sxs-lookup"><span data-stu-id="6e588-278">Some Top Issues</span></span>

<span data-ttu-id="6e588-279">您可能會面臨的一些常見問題以及如何在您的網路追蹤中找到這些。</span><span class="sxs-lookup"><span data-stu-id="6e588-279">Some common issues you may face and how to find them in your Network trace.</span></span>

### <a name="tcp-windows-scaling"></a><span data-ttu-id="6e588-280">TCP Windows 縮放比例</span><span class="sxs-lookup"><span data-stu-id="6e588-280">TCP Windows Scaling</span></span>

<span data-ttu-id="6e588-p145">位於 SYN-SYN/通知舊版或過時硬體可能不充分運用 TCP windows 縮放比例。 不調整設定適當的 TCP windows、 TCP 標頭中的預設 16 位元緩衝區填滿以毫秒為單位。 流量無法繼續傳送直到用戶端收到指的已接收的原始資料，而造成延遲。</span><span class="sxs-lookup"><span data-stu-id="6e588-p145">Found in the SYN - SYN/ACK. Legacy or aging hardware may not take advantage of TCP windows scaling.  Without proper TCP windows scaling settings, the default 16-bit buffer in TCP headers fills in milliseconds.  Traffic cannot continue to send until the client receives an acknowledgment that the original data has been received, causing delays.</span></span>

#### <a name="tools"></a><span data-ttu-id="6e588-285">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-285">Tools:</span></span>

- <span data-ttu-id="6e588-286">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-286">Netmon</span></span>
- <span data-ttu-id="6e588-287">Wireshark</span><span class="sxs-lookup"><span data-stu-id="6e588-287">Wireshark</span></span> 

#### <a name="what-youre-looking-for"></a><span data-ttu-id="6e588-288">您要尋找的：</span><span class="sxs-lookup"><span data-stu-id="6e588-288">What you're looking for:</span></span>

<span data-ttu-id="6e588-p146">尋找 SYN-SYN/ACK 流量的網路追蹤。 在 Netmon，使用類似的篩選器`tcp.flags.syn == 1`。此篩選會在 Wireshark 相同。</span><span class="sxs-lookup"><span data-stu-id="6e588-p146">Look for the SYN - SYN/ACK traffic in your network trace.  In Netmon, use a filter like  `tcp.flags.syn == 1`. This filter is the same in Wireshark.</span></span>  

![篩選適用於這兩種工具的 Syn 封包 Netmon 或 Wireshark： TCP。Flags.Syn = = 1。](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)         
<span data-ttu-id="6e588-293">請注意針對每個 SYN 有相關的確認通知 (SYN/ACK) 的目的地連接埠 (DstPort) 中比對來源 （來源） 的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="6e588-293">Notice that for every SYN there is a source port (SrcPort) number that is matched in the destination port (DstPort) of the related Acknowledgment (SYN/ACK).</span></span> 

<span data-ttu-id="6e588-294">若要查看您的網路連線所使用的 Windows 調整值，依序展開 [先 SYN，然後按一下 [相關的 SYN/通知</span><span class="sxs-lookup"><span data-stu-id="6e588-294">To see the Windows Scaling value that is used by your network connection, expand first the SYN, and then the related SYN/ACK.</span></span>  

![圖形會顯示如何將符合 DstPort 的來源中的追蹤，以取得時間差異。](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a><span data-ttu-id="6e588-296">TCP 閒置時間設定</span><span class="sxs-lookup"><span data-stu-id="6e588-296">TCP Idle Time Settings</span></span>

<span data-ttu-id="6e588-p147">在過去，大部分的周邊網路中已暫時性的連線，這表示閒置連線通常會終止。可以由 proxy 和防火牆在大於 100 到 300 秒終止 TCP 的閒置工作階段。這是 Outlook Online 的問題因為它會建立並使用長期連線其是否為閒置或不。</span><span class="sxs-lookup"><span data-stu-id="6e588-p147">Historically, most perimeter networks are configured for transient connections, meaning idle connections are generally terminated. Idle TCP sessions can be terminated by proxies and firewalls at greater than 100 to 300 seconds. This is problematic for Outlook Online because it creates and uses long-term connections, whether they are idle or not.</span></span>  

<span data-ttu-id="6e588-p148">當連線會終止 proxy 或防火牆裝置，用戶端不是發生的事情，並嘗試使用 Outlook Online 表示可在用戶端電腦會嘗試，便會重複替換、 恢復從之前先進行一份新連線。您可能會在載入頁面上看到擱置中的產品、 提示或效能低落。</span><span class="sxs-lookup"><span data-stu-id="6e588-p148">When connections are terminated by proxy or firewall devices, the client is not informed, and an attempt to use Outlook Online will mean a client computer will try, repeatedly, to revive the connection before making a new one. You may see hangs in the product, prompts, or slow performance on page load.</span></span>

#### <a name="tools"></a><span data-ttu-id="6e588-302">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-302">Tools:</span></span>

- <span data-ttu-id="6e588-303">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-303">Netmon</span></span>
- <span data-ttu-id="6e588-304">Wireshark</span><span class="sxs-lookup"><span data-stu-id="6e588-304">Wireshark</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-305">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-305">What to look for:</span></span>

<span data-ttu-id="6e588-p149">在 Netmon，查看的來回行程時間位移] 欄位。來回行程是用戶端將要求傳送至伺服器並接收到回應後的間隔時間。檢查用戶端與輸出點之間 (例如用戶端-\> Proxy)，或 Office 365 用戶端 (用戶端-\> Office 365)。您可以看到此許多封包的類型。</span><span class="sxs-lookup"><span data-stu-id="6e588-p149">In Netmon, look at the Time Offset field for a round-trip. A round-trip is the time between client sending a request to the server and receiving a response back. Check between the Client and the egress point (ex. Client --\> Proxy), or the Client to Office 365 (Client --\> Office 365). You can see this in many types of packets.</span></span> 

<span data-ttu-id="6e588-311">例如，Netmon 中的篩選器可能看起來`.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`，或在 Wireshark、 `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`。</span><span class="sxs-lookup"><span data-stu-id="6e588-311">As an example, the filter in Netmon may look like  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, or, in Wireshark,  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.</span></span>  

> [!TIP]
> <span data-ttu-id="6e588-p150">不知道您追蹤中的 IP 位址是否屬於您的 DNS 伺服器吗？嘗試查閱在命令列。按一下 [**開始** \> **執行**\>與輸入**cmd**，或按**Windows 鍵**\>輸入**cmd**。在提示處輸入`nslookup <the IP address from the network trace>`。若要測試，請使用 nslookup 針對您自己的電腦 IP 位址。> 若 Microsoft 的 IP 範圍的清單，請參閱[Office 365 Url 和 IP 位址範圍](https://technet.microsoft.com/en-us/library/hh373144.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6e588-p150">Don't know if the IP address in your trace belongs to your DNS server? Try looking it up at the command line. Click **Start** \> **Run** \> and type **cmd**, or press **Windows Key** \> and type **cmd**. At the prompt, type  `nslookup <the IP address from the network trace>`. To test, use nslookup against your own computer's IP address. > To see a list of Microsoft's IP ranges, see [Office 365 URLs and IP address ranges](https://technet.microsoft.com/en-us/library/hh373144.aspx).</span></span> 

<span data-ttu-id="6e588-p151">問題時，預期長時間會位移看起來，在此例中 (Outlook Online)，特別是在 TLS:TLS 封包所顯示的應用程式資料傳送過程中 (例如 Netmon 您可以在尋找應用程式資料封包透過`.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`)。您應該會看到順利進程時間的不同工作階段。如果您看到長時間延遲重新整理您 Outlook Online 時，這可能是重設傳送高程度所造成。</span><span class="sxs-lookup"><span data-stu-id="6e588-p151">If there is a problem, expect long Time Offsets to appear, in this case (Outlook Online), particularly in TLS:TLS packets that show the passage of Application Data (for example, in Netmon you can find application data packets via  `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). You should see a smooth progression in the time across the session. If you see long delays when refreshing your Outlook Online, this could be caused by a high degree of resets being sent.</span></span> 

### <a name="latencyround-trip-time"></a><span data-ttu-id="6e588-321">延遲/循中斷時間</span><span class="sxs-lookup"><span data-stu-id="6e588-321">Latency/Round Trip Time</span></span> 

<span data-ttu-id="6e588-322">延遲就可以根據許多變數、 這類升級過時裝置、 將大量的使用者新增至網路與網路連接上的其他工作所耗用的整體頻寬的百分比的許多變更量值。</span><span class="sxs-lookup"><span data-stu-id="6e588-322">Latency is a measure that can change a lot depending on many variables, such upgrading aging devices, adding a large number of users to a network, and the percentage of overall bandwidth consumed by other tasks on a network connection.</span></span> 

<span data-ttu-id="6e588-323">有可從這個[網路規劃與 Office 365 的效能調整](network-planning-and-performance.md)] 頁面上的 Office 365 的頻寬計算器。</span><span class="sxs-lookup"><span data-stu-id="6e588-323">There are bandwidth calculators for Office 365 available from this [Network planning and performance tuning for Office 365](network-planning-and-performance.md) page.</span></span>  

<span data-ttu-id="6e588-p152">需要來測量的連線或您的 ISP 連線頻寬速度吗？嘗試這個網站 （或其類似的網站）： [Speedtest 官方網站](https://www.speedtest.net/)及[Pingtest](http://www.pingtest.net/)。</span><span class="sxs-lookup"><span data-stu-id="6e588-p152">Need to measure the speed of your connection, or your ISP connection's bandwidth? Try this site (or sites like it): [Speedtest Official Site](https://www.speedtest.net/), and [Pingtest](http://www.pingtest.net/).</span></span>

#### <a name="tools"></a><span data-ttu-id="6e588-326">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-326">Tools:</span></span>

- <span data-ttu-id="6e588-327">Ping</span><span class="sxs-lookup"><span data-stu-id="6e588-327">Ping</span></span>
- <span data-ttu-id="6e588-328">PsPing</span><span class="sxs-lookup"><span data-stu-id="6e588-328">PsPing</span></span>
- <span data-ttu-id="6e588-329">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-329">Netmon</span></span>
- <span data-ttu-id="6e588-330">Wireshark</span><span class="sxs-lookup"><span data-stu-id="6e588-330">Wireshark</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-331">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-331">What to look for:</span></span>

<span data-ttu-id="6e588-p153">若要追蹤中追蹤的延遲，將會受益擁有在 Office 365 中記錄的用戶端電腦 IP 位址和 DNS 伺服器的 IP 位址。這是基於更輕鬆地追蹤篩選。如果您透過 proxy 連線，您必須在用戶端電腦 IP 位址、 proxy/輸出 IP 位址] 中，與 Office 365 DNS IP 位址，以方便工時。</span><span class="sxs-lookup"><span data-stu-id="6e588-p153">To track latency in a trace, you will benefit from having recorded the client computer IP address and the IP address of the DNS server in Office 365. This is for the purpose of easier trace filtering. If you connect through a proxy, you will need your client computer IP address, the proxy/egress IP address, and the Office 365 DNS IP address, to make the work easier.</span></span>  

<span data-ttu-id="6e588-p154">Ping 要求傳送至 outlook.office365.com 會告訴您收到要求的資料中心名稱即使 ping*可能*無法連線至傳送商標連續 ICMP 封包。如果您使用 PsPing （下載免費工具），以及特定連接埠 (443) 和或許使用 IPv4 (-4) 將會收到平均 round 來回時間傳送封包。這可像在 Office 365 服務中，其他 Url 的運作這`psping -4 yourSite.sharepoint.com:443`。事實上，您可以指定取得較大的範例您 average try 類似如下的 ping 數： `psping -4 -n 20 yourSite-my.sharepoint.com:443`。</span><span class="sxs-lookup"><span data-stu-id="6e588-p154">A ping request sent to outlook.office365.com will tell you the name of the datacenter receiving the request, even if ping  *may*  not be able to connect to send the trademark consecutive ICMP packets. If you use PsPing (a free tool for download), and specific the port (443) and perhaps to use IPv4 (-4) you will get an average round-trip-time for packets sent. This will work this for other URLs in the Office 365 services, like  `psping -4 yourSite.sharepoint.com:443`. In fact, you can specify a number of pings to get a larger sample for your average, try something like:  `psping -4 -n 20 yourSite-my.sharepoint.com:443`.</span></span>  

> [!NOTE]
> <span data-ttu-id="6e588-p155">PsPing 不會傳送 ICMP 封包。它會偵測使用 TCP 封包透過特定連接埠，因此您可以使用任何一個您知道開啟。在 Office 365，它會使用 SSL/TLS，請嘗試附加連接埠： 至您 PsPing 443。</span><span class="sxs-lookup"><span data-stu-id="6e588-p155">PsPing doesn't send ICMP packets. It pings with TCP packets over a specific port, so you can use any one you know to be open. In Office 365, which uses SSL/TLS, try attaching port :443 to your PsPing.</span></span>

![螢幕擷取畫面顯示與 443 進行相同，但也報告 6.5ms年平均 RTT 解析 outlook.office365.com、 和 PSPing ping。](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)        

<span data-ttu-id="6e588-p156">如果您同時執行網路追蹤載入速度過慢執行的 Office 365] 頁面上，您應該篩選 Netmon 或 Wireshark 追蹤`DNS`。這是一個我們要尋找 Ip。</span><span class="sxs-lookup"><span data-stu-id="6e588-p156">If you loaded the slow performing Office 365 page while doing a network trace, you should filter a Netmon or Wireshark trace for  `DNS`. This is one of the IPs we're looking for.</span></span>  

<span data-ttu-id="6e588-p157">以下是篩選以取得 IP 位址 （並仔細 DNS 延遲） 您 Netmon 所採取的步驟。本範例會使用 outlook.office365.com，但也可以使用 SharePoint Online 的租用戶 (例如 hithere.sharepoint.com) 的 URL。</span><span class="sxs-lookup"><span data-stu-id="6e588-p157">Here are the steps to take to filter your Netmon to get the IP address (and take a look at DNS Latency). This example uses outlook.office365.com, but may also use the URL of a SharePoint Online tenant (hithere.sharepoint.com for example).</span></span>  

1. <span data-ttu-id="6e588-347">Ping URL`ping outlook.office365.com`和結果中的名稱和記錄的 DNS 伺服器來傳送 ping 要求的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6e588-347">Ping the URL `ping outlook.office365.com` and, in the results, record the name and IP address of the DNS server the ping request was sent to.</span></span> 
2. <span data-ttu-id="6e588-348">網路追蹤 [開啟] 頁面上，或執行巨集指令可讓您的效能問題，或如果您看到高延遲 ping 本身，在網路追蹤它。</span><span class="sxs-lookup"><span data-stu-id="6e588-348">Network trace opening the page, or doing the action that gives you the performance problem, or, if you see a high latency on the ping, itself, network trace it.</span></span> 
3. <span data-ttu-id="6e588-p158">Netmon 和篩選器中開啟追蹤的 DNS (此篩選器也運作中 Wireshark，但會區分大小寫`-- dns`)。由於您知道您 ping 從的 DNS 伺服器的名稱也可能會篩選類似的多個能快速以 Netmon:`DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`且哪一個看起來如下 Wireshark dns 中圖文框包含"namnorthwest"。</span><span class="sxs-lookup"><span data-stu-id="6e588-p158">Open the trace in Netmon and filter for DNS (this filter also works in Wireshark, but is sensitive to case `-- dns`). Since you know the name of the DNS server from your ping you may also filter more speedily in Netmon like this: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")` , which looks like this in Wireshark dns and frame contains "namnorthwest".</span></span><br/><span data-ttu-id="6e588-p159">開啟回應封包及在框架詳細資料視窗中的 Netmon，按一下 [DNS 展開如需詳細資訊。您會發現要求至 Office 365-中發生的 DNS 伺服器的 IP 位址的 DNS 資訊在您將需要此 IP 位址 （PsPing 工具） 的下一個步驟。移除篩選，請以滑鼠右鍵按一下 Netmon 的框架摘要中的 DNS 回應\>尋找交談\>DNS 以查看 DNS 查詢和回應-並排。</span><span class="sxs-lookup"><span data-stu-id="6e588-p159">Open the response packet and, in Frame Details window of Netmon, click DNS to expand for more information. In the DNS information you'll find the IP address of the DNS server the request went to in Office 365 -- you'll need this IP address for the next step (the PsPing tool). Remove the filter, right-click on the DNS Response in Netmon's Frame Summary \> Find Conversations \> DNS to see the DNS Query and Response side-by-side.</span></span> 
4. <span data-ttu-id="6e588-p160">在 Netmon，也請注意之間的 DNS 要求及回應時間位移] 欄。在下一步、 輕鬆安裝及使用[PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx)工具有非常實用同時 ICMP 通常會封鎖在防火牆，因為和 PsPing 精細追蹤延遲 （毫秒）。PsPing 完成 TCP 連線到位址及連接埠 （在我們 case 開啟連接埠 443）。</span><span class="sxs-lookup"><span data-stu-id="6e588-p160">In Netmon, also note the Time Offset  column between the DNS Request and Response. In the next step, the easy-to-install and use [PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) tool comes in very handy, both because ICMP is often blocked on Firewalls, and because PsPing elegantly tracks latency in milliseconds. PsPing completes a TCP connection to an address and port (in our case open port 443).</span></span> 
5. <span data-ttu-id="6e588-357">安裝 PsPing。</span><span class="sxs-lookup"><span data-stu-id="6e588-357">Install PsPing.</span></span> 
6. <span data-ttu-id="6e588-p161">開啟命令提示字元 (啟動\>執行\>輸入 cmd 或 Windows 鍵\>輸入 cmd) 並將目錄變更為 PsPing 執行 PsPing 命令的安裝所在的目錄。在 「 我的範例您可以看到我做 'Qfe' 資料夾上根目錄的 c。您可以執行相同的快速存取。</span><span class="sxs-lookup"><span data-stu-id="6e588-p161">Open a command prompt (Start \> Run \> type cmd, or Windows Key \> type cmd) and change directory to the directory where you installed PsPing to run the PsPing command. In my examples you can see I made a 'Perf' folder on the root of C. You can do the same for quick access.</span></span> 
7. <span data-ttu-id="6e588-360">輸入命令，讓您針對 Office 365 的 DNS 伺服器的 IP 位址 PsPing 進行從舊版的 Netmon 追蹤--若要新增的連接埠號碼，請記得。</span><span class="sxs-lookup"><span data-stu-id="6e588-360">Type the command so that you're making your PsPing against the IP address of the Office 365 DNS server from your earlier Netmon trace -- remember to add the port number.</span></span> <br/><span data-ttu-id="6e588-p162">換句話說， `psping -n 20 132.245.24.82:445`。這會提供您的 20 ping 取樣並時 PsPing 停駐點的平均延遲。</span><span class="sxs-lookup"><span data-stu-id="6e588-p162">In other words, `psping -n 20 132.245.24.82:445`. This will give you a sampling of 20 pings and average the latency when PsPing stops.</span></span> 

<span data-ttu-id="6e588-p163">如果您正在透過 proxy 伺服器移至 Office 365、 所有點不同的步驟。您將第一個 PsPing 至 proxy 伺服器，以取得平均延遲值以毫秒為單位 proxy/輸出後再回復，然後再其中一個執行 PsPing proxy 或取得遺失值 （有一個 Office 365 後再回復） 的直接網際網路連線的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6e588-p163">If you're going to Office 365 through a proxy server, the steps are a little different. You would first PsPing to your proxy server to get an average latency value in milliseconds to proxy/egress and back, and then either run PsPing on the proxy, or on a computer with a direct Internet connection to get the missing value (the one to Office 365 and back).</span></span>  

<span data-ttu-id="6e588-p164">如果您選擇從 proxy 執行 PsPing，需要兩個毫秒值： 對 proxy 伺服器或輸出點與 Office 365 的 proxy 伺服器的用戶端電腦。與完成 ！繼續錄製值。</span><span class="sxs-lookup"><span data-stu-id="6e588-p164">If you choose to run PsPing from the proxy, you'll have two millisecond values: Client computer to proxy server or egress point, and proxy server to Office 365. And you're done! Well, recording values, anyway.</span></span>  

<span data-ttu-id="6e588-p165">如果您有直接連線至網際網路的另一個用戶端電腦上執行 PsPing，也就是 proxy，而您也都有兩個毫秒值： 對 proxy 伺服器或輸出點與 Office 365 用戶端電腦的用戶端電腦。在此例中減去的用戶端電腦的值為 proxy 伺服器或輸出點至 Office 365 的用戶端電腦的值與您將必須 RTT 號碼從用戶端電腦的 proxy 伺服器或輸出點並從 proxy 伺服器或輸出指向 Office 365。</span><span class="sxs-lookup"><span data-stu-id="6e588-p165">If you run PsPing on another client computer that has a direct connection to the Internet, that is, without a proxy, you will have two millisecond values: Client computer to proxy server or egress point, and client computer to Office 365. In this case, subtract the value of client computer to proxy server or egress point from the value of client computer to Office 365, and you will have the RTT numbers from your client computer to the proxy server or egress point, and from proxy server or egress point to Office 365.</span></span> 

<span data-ttu-id="6e588-370">不過，如果您可以在受影響的位置直接連線或略過 proxy 找到的用戶端電腦，您可能會查看如果問題重現那里首先，選擇 [並測試之後，使用。</span><span class="sxs-lookup"><span data-stu-id="6e588-370">However, if you can find a client computer in the impacted location that is directly connected, or bypasses the proxy, you may choose to see if the issue reproduces there to begin with, and test using it, thereafter.</span></span> 

<span data-ttu-id="6e588-371">延遲視為 Netmon 追蹤，這些額外毫秒可以新增向上中, 如有足夠的任何指定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6e588-371">Latency, as seen in a Netmon trace, those extra milliseconds can add up, if there are enough of them in any given session.</span></span>  

![Netmon 中的一般延遲，並將 Netmon 預設時間差異欄位新增至框架摘要。](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> <span data-ttu-id="6e588-p166">您的 IP 位址可能不同於此處顯示，例如您 ping 可能會傳回類似詳細如下 157.56.0.0/16 或類似範圍 Ip。如需 Office 365 所使用的範圍的清單，請參閱[Office 365 Url 和 IP 位址範圍](https://technet.microsoft.com/en-us/library/hh373144.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6e588-p166">Your IP address may be different than the IPs shown here, for example, your ping may return something more like 157.56.0.0/16 or a similar range. For a list of ranges used by Office 365, check out [Office 365 URLs and IP address ranges](https://technet.microsoft.com/en-us/library/hh373144.aspx).</span></span> 

<span data-ttu-id="6e588-375">如果您想要搜尋的例如 132.245，記住展開 （這頂端有一個按鈕） 的所有節點。</span><span class="sxs-lookup"><span data-stu-id="6e588-375">Remember to expand all the nodes (there's a button at the top for this) if you want to search for, for example, 132.245.</span></span>

### <a name="proxy-authentication"></a><span data-ttu-id="6e588-376">Proxy 驗證</span><span class="sxs-lookup"><span data-stu-id="6e588-376">Proxy Authentication</span></span>

<span data-ttu-id="6e588-p167">這僅適用於您如果您經由 proxy 伺服器。如果不是，您可以略過這些步驟。正常運作時 proxy 驗證應進行毫秒一致。您不應該 （例如） 請參閱尖峰用量期間間歇性錯誤的效能。</span><span class="sxs-lookup"><span data-stu-id="6e588-p167">This only applies to you if you're going through a proxy server. If not, you can skip these steps. When working properly, proxy authentication should take place in milliseconds, consistently. You shouldn't see intermittent bad performance during peak usage periods (for example).</span></span>  

<span data-ttu-id="6e588-p168">只有在 Proxy 驗證位於的每當您進行新的 TCP 連線至 Office 365 以取得資訊，您需要通過幕後驗證程序。如此，例如從行事曆切換至 Outlook Online 中的郵件，當您將會進行驗證。與 SharePoint Online 中如果 」 頁面會顯示媒體或將資料從多個網站或位置，您會驗證轉譯資料時所需每個不同 TCP 連線。</span><span class="sxs-lookup"><span data-stu-id="6e588-p168">If Proxy authentication is on, each time you make a new TCP connection to Office 365 to get information, you need to pass through an authentication process behind the scenes. So, for example, when switching from Calendar to Mail in Outlook Online, you will authenticate. And in SharePoint Online, if a page displays media or data from multiple sites or locations, you will authenticate for each different TCP connection that is needed in order to render the data.</span></span>  

<span data-ttu-id="6e588-p169">在 Outlook Online 中，您可能會遇到每當您行事曆和您的信箱之間切換或 SharePoint Online 中的速度過慢的頁面載入的速度過慢的載入時間。不過，還有其他未列在這裡的徵狀。</span><span class="sxs-lookup"><span data-stu-id="6e588-p169">In Outlook Online, you may experience slow load times whenever you switch between Calendar and your mailbox, or slow page loads in SharePoint Online. However, there are other symptoms not listed here.</span></span> 

<span data-ttu-id="6e588-p170">Proxy 驗證是在輸出 proxy 伺服器上的設定。如果它與 Office 365 導致的效能問題，您必須請洽詢您的網路小組。</span><span class="sxs-lookup"><span data-stu-id="6e588-p170">Proxy authentication is a setting on your egress proxy server. If it is causing a performance issue with Office 365, you must consult your networking team.</span></span>  

#### <a name="tool"></a><span data-ttu-id="6e588-388">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-388">Tool:</span></span> 

- <span data-ttu-id="6e588-389">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-389">Netmon</span></span>
- <span data-ttu-id="6e588-390">Wireshark</span><span class="sxs-lookup"><span data-stu-id="6e588-390">Wireshark</span></span> 

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-391">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-391">What to look for:</span></span>

<span data-ttu-id="6e588-p171">Proxy 驗證發生於每當新的 TCP 工作階段必須旋轉完畢之後，通常為向伺服器要求的檔案或資訊或提供資訊。例如，您可能會看到 HTTP GET 或 HTTP POST 要求周圍的 proxy 驗證。如果您想要查看您所進行的要求驗證您追蹤中的框架、 將 ' NTLMSSP 摘要 」 資料行新增至 Netmon 及篩選的`.property.NTLMSSPSummary`。若要查看多久驗證正在進行，新增 [時間差異] 欄中。</span><span class="sxs-lookup"><span data-stu-id="6e588-p171">Proxy authentication takes place whenever a new TCP session must be spun up, commonly to request files or info from the server, or to supply info. For example, you may see proxy authentication around HTTP GET or HTTP POST requests. If you want to see the frames where you are authenticating requests in your trace, add the 'NTLMSSP Summary' column to Netmon and filter for  `.property.NTLMSSPSummary`. To see how long the authentication is taking, add the Time Delta column.</span></span> 

<span data-ttu-id="6e588-396">若要將欄新增至 Netmon：</span><span class="sxs-lookup"><span data-stu-id="6e588-396">To add a column to Netmon:</span></span> 
1. <span data-ttu-id="6e588-397">以滑鼠右鍵按一下例如描述資料行。</span><span class="sxs-lookup"><span data-stu-id="6e588-397">Right-click on a column such as Description.</span></span> 
2. <span data-ttu-id="6e588-398">按一下 [選擇資料行。</span><span class="sxs-lookup"><span data-stu-id="6e588-398">Click Choose Columns.</span></span> 
3. <span data-ttu-id="6e588-399">在清單中尋找 NTLMSSP 摘要和時間差異並按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="6e588-399">Locate NTLMSSP Summary and Time Delta in the list and click Add.</span></span> 
4. <span data-ttu-id="6e588-400">移動新欄到位置之前的前面或後面 [描述] 欄以便讀取並排顯示。</span><span class="sxs-lookup"><span data-stu-id="6e588-400">Move the new columns into place before or behind the Description column so you can read them side-by-side.</span></span>
5. <span data-ttu-id="6e588-401">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6e588-401">Click OK.</span></span> 

<span data-ttu-id="6e588-p172">即使您沒有加入資料行、 Netmon 篩選器會運作。但是您疑難排解會是您可以看到您正處於何種驗證階段的更加簡便。</span><span class="sxs-lookup"><span data-stu-id="6e588-p172">Even if you don't add the column, the Netmon filter will work. But your troubleshooting will be much easier if you can see what stage of authentication you're in.</span></span> 

<span data-ttu-id="6e588-p173">要尋找的執行個體的 Proxy 驗證務必研究所有的圖文框有 NTLM 挑戰，或的驗證訊息時出現。如有必要，以滑鼠右鍵按一下流量和尋找交談的特定片段\>TCP。請注意下列交談中的時間差異值。</span><span class="sxs-lookup"><span data-stu-id="6e588-p173">When looking for instances of Proxy Authentication, be sure to study all frames where there is an NTLM Challenge, or an Authenticate Message is present. If necessary, right-click the specific piece of traffic and Find Conversations \> TCP. Be aware of the Time Delta values in these Conversations.</span></span> 

![Netmon 追蹤顯示 proxy 驗證篩選依交談。](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)        

<span data-ttu-id="6e588-p174">四個秒延遲 proxy 驗證視為 Wireshark。**從舊的顯示圖文框的時間差異**欄進行透過圖文框詳細資料中的相同名稱的欄位上按一下滑鼠右鍵並選取 [做為資料行的 [新增。</span><span class="sxs-lookup"><span data-stu-id="6e588-p174">A four second delay in proxy authentication as seen in Wireshark. The **Time delta from previous displayed frame** column was made via right-clicking the field of the same name in the frame details and selecting Add as Column.  </span></span><br/> <span data-ttu-id="6e588-410">![在 Wireshark，'從舊的顯示圖文框的時間差異' 欄可以進行透過圖文框詳細資料中的相同名稱的欄位上按一下滑鼠右鍵並選取 [做為資料行的 [新增。](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)</span><span class="sxs-lookup"><span data-stu-id="6e588-410">![In Wireshark, the 'Time delta from previous displayed frame' column can be made via right-clicking the field of the same name in the frame details and selecting Add as Column.](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)</span></span>        

### <a name="dns-performance"></a><span data-ttu-id="6e588-411">DNS 效能</span><span class="sxs-lookup"><span data-stu-id="6e588-411">DNS Performance</span></span>

<span data-ttu-id="6e588-412">名稱解析 works 最佳以及最快速當它接近用戶端的國家/地區為可能的位置。</span><span class="sxs-lookup"><span data-stu-id="6e588-412">Name resolution works best and most quickly when it takes place as close to the client's country as possible.</span></span> 

<span data-ttu-id="6e588-p175">如果 DNS 名稱解析為進行 overseas，它可以新增頁面載入秒數。理想狀況下，名稱解析發生的情況下 100ms年中。如果不應進行進一步調查。</span><span class="sxs-lookup"><span data-stu-id="6e588-p175">If DNS name resolution is taking place overseas, it can add seconds to page loads. Ideally, name resolution happens in under 100ms. If not, you should do further investigation.</span></span> 

> [!TIP]
> <span data-ttu-id="6e588-p176">不確定如何在 Office 365 中的用戶端連線運作？仔細的用戶端連線參考文件[此處](https://technet.microsoft.com/en-us/library/dn741250.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6e588-p176">Not sure how Client Connectivity works in Office 365? Take a look at the Client Connectivity Reference document [here](https://technet.microsoft.com/en-us/library/dn741250.aspx).</span></span>           

#### <a name="tools"></a><span data-ttu-id="6e588-418">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-418">Tools:</span></span> 

- <span data-ttu-id="6e588-419">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-419">Netmon</span></span>
- <span data-ttu-id="6e588-420">Wireshark</span><span class="sxs-lookup"><span data-stu-id="6e588-420">Wireshark</span></span>
- <span data-ttu-id="6e588-421">PsPing</span><span class="sxs-lookup"><span data-stu-id="6e588-421">PsPing</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-422">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-422">What to look for:</span></span>
<span data-ttu-id="6e588-p177">分析 DNS 的效能是通常是另一個網路追蹤工作。不過，PsPing 十分有用的統治、 回或取出、 可能的原因。</span><span class="sxs-lookup"><span data-stu-id="6e588-p177">Analyzing DNS performance is typically another job for a network trace. However, PsPing is also helpful in ruling in, or out, a possible cause.</span></span> 

<span data-ttu-id="6e588-p178">DNS 流量根據 TCP 及 UDP 要求和回應清楚標示協助以符合其特定的回應特定要求的識別碼。您會看見 DNS 時，例如 SharePoint Online 使用的任何網路名稱或 URL 網頁上的流量。為規則的縮圖中，大部分的此流量 excepting 時傳送區域執行透過 UDP。</span><span class="sxs-lookup"><span data-stu-id="6e588-p178">DNS traffic is based on TCP and UDP requests and responses are clearly marked with an ID that will help to match a specific request with its specific response. You'll see DNS traffic when, for example, SharePoint Online uses a network name or URL on a web page. As a rule of thumb, most of this traffic, excepting when transferring Zones, runs over UDP.</span></span> 

<span data-ttu-id="6e588-p179">Netmon 和 Wireshark 中最基本篩選，將可讓您查看 DNS 流量只是`dns`。請務必在指定篩選條件時使用小寫。請記得重現問題用戶端電腦上的所顯示的之前清除 DNS 解析快取。例如，如果您有很慢 SharePoint Online 載入頁面的 [首頁] 頁面上，您應關閉所有瀏覽器、 開啟新的瀏覽器、 啟動追蹤、 清除 DNS 解決程式快取及瀏覽至您的 SharePoint Online 網站。一旦解析為整頁，您應該停止並儲存追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p179">In both Netmon and Wireshark, the most basic filter that will let you look at DNS traffic is simply  `dns`. Be sure to use lower case when specifying the filter. Remember to flush your DNS resolver cache before you begin to reproduce the issue on your client computer. For example, if you have a slow SharePoint Online page load for the Home page, you should close all browsers, open a new browser, start tracing, flush your DNS resolver cache, and browse to your SharePoint Online site. Once the entire page resolves, you should stop and save the trace.</span></span>

![在 Netmon 中，DNS 的基本篩選器是 DNS。](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

<span data-ttu-id="6e588-p180">您想要查看以下位移的時間。並將可能會有幫助將**時間差異**資料行新增至 Netmon 您可以藉由完成下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="6e588-p180">You want to look at the time offset here. And it may be helpful to add the **Time Delta** column to Netmon which you can do by completing these steps:</span></span> 
1. <span data-ttu-id="6e588-436">以滑鼠右鍵按一下例如描述資料行。</span><span class="sxs-lookup"><span data-stu-id="6e588-436">Right-click on a column such as Description.</span></span> 
2. <span data-ttu-id="6e588-437">按一下 [選擇資料行。</span><span class="sxs-lookup"><span data-stu-id="6e588-437">Click Choose Columns.</span></span> 
3. <span data-ttu-id="6e588-438">在清單中尋找時間差異並按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="6e588-438">Locate Time Delta in the list and click Add.</span></span> 
4. <span data-ttu-id="6e588-439">移動新欄到位置之前的前面或後面 [描述] 欄以便讀取並排顯示。</span><span class="sxs-lookup"><span data-stu-id="6e588-439">Move the new column into place before or behind the Description column so you can read them side-by-side.</span></span>
5. <span data-ttu-id="6e588-440">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6e588-440">Click OK.</span></span> 

<span data-ttu-id="6e588-p181">如果您發現感興趣的查詢，請考慮隔離以滑鼠右鍵按一下該圖文框的詳細資訊] 面板中，選擇 [**尋找交談**中的查詢\> **DNS**。請注意網路交談面板跳右 UDP 流量及其記錄檔中的特定對話。</span><span class="sxs-lookup"><span data-stu-id="6e588-p181">If you find a query of interest, consider isolating it by right-clicking that query in the frame details panel, choosing **Find Conversations** \> **DNS**. Notice that the Network Conversations panel jumps right to the specific conversation in its log of UDP traffic.</span></span> 

![Netmon 追蹤的 DNS，並使用篩選過的 Outlook Online 負載尋找交談則 DNS 縮減結果。](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)        

<span data-ttu-id="6e588-p182">Wireshark 您可以將一欄的 DNS 時間。取得您追蹤 （或開啟追蹤） 中 Wireshark 及 filter by `dns`，或更多好心`dns.time`。按一下 [在任何的 DNS 查詢和在 [顯示詳細資料] 面板中，展開`Domain Name System (response)`詳細資料。您會看到所有欄位的時間 (例如` [Time: 0.001111100 seconds] `。以滑鼠右鍵按一下此時間，並選取 [**套用] 做為資料行**。這會提供您的**時間**資料行您追蹤的速度較快排序。按一下 [在新的資料行來排序遞減值來查看 DNS 呼叫萬一最長的時間來解決。</span><span class="sxs-lookup"><span data-stu-id="6e588-p182">In Wireshark you can make a column for DNS time. Take your trace (or open a trace) in Wireshark and filter by  `dns`, or, more helpfully,  `dns.time`. Click on any DNS query, and, in the panel showing details, expand the  `Domain Name System (response)` details. You'll see a field for time (for example,  ` [Time: 0.001111100 seconds] `. Right-click this time and select **Apply as Column**. This will give you a **Time** column for quicker sorting of your trace. Click on the new column to sort by descending values to see which DNS call took the longest to resolve.</span></span> 

[<span data-ttu-id="6e588-451">在 Wireshark 中由 (小寫) dns.time 篩選的 SharePoint Online 瀏覽，時間起點為將詳細資料納入欄位和遞增排序起。</span><span class="sxs-lookup"><span data-stu-id="6e588-451">A browse of SharePoint Online filtered in Wireshark by (lowercase) dns.time, with the time from the details made into a column and sorted ascending.</span></span>](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

<span data-ttu-id="6e588-p183">如果您想要執行的 DNS 解析時間更多調查，嘗試針對使用 TCP 的 DNS 連接埠 PsPing (例如`psping <IP address of DNS server>:53`)。您仍看到的效能問題嗎吗？如果問題是特定的更多可能是特定的更廣泛的網路問題問題比又打執行解析度 DNS 應用程式。也值得再次提及，該 ping 以 outlook.office365.com 會告訴您其中 DNS 名稱解析為 Outlook Online 正在進行 (例如 namnorthwest.office365.com outlook)。</span><span class="sxs-lookup"><span data-stu-id="6e588-p183">If you would like to do more investigation of the DNS resolution time, try a PsPing against the DNS port used by TCP (for example,  `psping <IP address of DNS server>:53`) . Do you still see a performance issue? If you do, then the problem is more likely to be a broader network issue than an issue of specific the DNS application you're hitting to do resolution. It's also worth mentioning, again, that a ping to outlook.office365.com will tell you where DNS name resolution for Outlook Online is taking place (for example, outlook-namnorthwest.office365.com).  </span></span><br/> <span data-ttu-id="6e588-456">如果設為特定的 DNS 尋找問題，則可能需要連絡您的 IT 部門來查看 DNS 組態和 DNS 轉寄站進一步調查這個問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-456">If the issue looks to be DNS specific, it may be necessary to contact your IT department to look at DNS configurations and DNS Forwarders to further investigate this issue.</span></span> 

### <a name="proxy-scalability"></a><span data-ttu-id="6e588-457">Proxy 延展性</span><span class="sxs-lookup"><span data-stu-id="6e588-457">Proxy Scalability</span></span>

<span data-ttu-id="6e588-p184">像 Outlook Online 在 Office 365 服務授與用戶端多個長期連線。因此，每位使用者可能會使用多個需要較長的生命週期的連線。</span><span class="sxs-lookup"><span data-stu-id="6e588-p184">Services like Outlook Online in Office 365 grant clients multiple long-term connections. Therefore, each user may use more connections that require a longer life.</span></span>  

> [!TIP]
> <span data-ttu-id="6e588-p185">需要因為您即將許多使用者新增至 Office 365 的頻寬使用量計劃嗎？試用[Office 365 的網際網路頻寬使用量計劃](https://technet.microsoft.com/en-us/library/hh852542.aspx)。有可用頻寬計算器發生。</span><span class="sxs-lookup"><span data-stu-id="6e588-p185">Need to plan for bandwidth use because you're about to add a lot users to Office 365? Try [Plan for Internet bandwidth usage for Office 365](https://technet.microsoft.com/en-us/library/hh852542.aspx). There are bandwidth calculators available there.</span></span>

#### <a name="tool"></a><span data-ttu-id="6e588-463">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-463">Tool:</span></span>
 
<span data-ttu-id="6e588-464">數學</span><span class="sxs-lookup"><span data-stu-id="6e588-464">Math</span></span>  

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-465">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-465">What to look for:</span></span> 

<span data-ttu-id="6e588-p186">沒有網路追蹤或疑難排解工具專屬於這。而根據其授與限制及其他變數的頻寬計算。</span><span class="sxs-lookup"><span data-stu-id="6e588-p186">There is no network trace or troubleshooting tool specific to this. Instead, it's based upon bandwidth calculations given limitations and other variables.</span></span>  

### <a name="tcp-max-segment-size"></a><span data-ttu-id="6e588-468">TCP Max 區段大小</span><span class="sxs-lookup"><span data-stu-id="6e588-468">TCP Max Segment Size</span></span>

<span data-ttu-id="6e588-p187">位於 SYN-SYN/通知 執行這項檢查中已過以確定 TCP 封包設定為執行可能的資料數量上限任何效能網路追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p187">Found in the SYN - SYN/ACK.  Do this check in any performance network trace you've taken to ensure that TCP packets are configured to carry the maximum amount of data possible.</span></span> 

<span data-ttu-id="6e588-p188">目標是以查看 1460 位元組的資料傳輸的 MSS。如果您正在背後的 proxy 或使用 NAT，請一定要執行這項測試從用戶端 proxy/輸出/NAT 和 proxy/輸出/至 Office 365 的 NAT 獲得最佳結果 ！這些是不同的 TCP 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6e588-p188">The goal is to see a MSS of 1460 bytes for transmission of data. If you're behind a proxy, or you are using a NAT, remember to run this test from client to proxy/egress/NAT, and from proxy/egress/NAT to Office 365 for best results! These are different TCP sessions.</span></span>

#### <a name="tool"></a><span data-ttu-id="6e588-474">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-474">Tool:</span></span> 

<span data-ttu-id="6e588-475">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-475">Netmon</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-476">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-476">What to look for:</span></span>

<span data-ttu-id="6e588-p189">TCP Max 區段大小 (MSS) 是另一個參數的三種方式信號交換在您的網路追蹤，這表示您將 SYN-SYN/ACK 封包中找到所需的資料。MSS 是以查看其實很簡單。</span><span class="sxs-lookup"><span data-stu-id="6e588-p189">TCP Max Segment Size (MSS) is another parameter of the three-way handshake in your network trace, that means you'll find the data you need in the SYN - SYN/ACK packet. MSS is actually pretty simple to see.</span></span> 

<span data-ttu-id="6e588-479">開啟任何效能網路追蹤您部署及尋找你好奇、 連線或所示範的效能問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-479">Open any performance network trace you have and find the connection you're curious about, or that demonstrates the performance problem.</span></span> 

> [!NOTE]
> <span data-ttu-id="6e588-p190">如果您要查看追蹤並需要尋找與您交談相關的流量，篩選的用戶端 IP 或 proxy 伺服器或輸出點或兩個 IP。直接升級，您將需要 ping 正在測試的 Office 365 中的追蹤，與篩選器的 IP 位址由它的 URL。</span><span class="sxs-lookup"><span data-stu-id="6e588-p190">If you are looking at a trace and need to find the traffic relevant to your conversation, filter by the IP of the Client, or the IP of the proxy server or egress point, or both. Going directly, you will need to ping the URL that you're testing for the IP address of Office 365 in the trace, and filter by it.</span></span> 

<span data-ttu-id="6e588-p191">查看 second-hand 追蹤吗？嘗試使用篩選器的方式放置自己。執行 Netmon，根據 URL，例如搜尋`Containsbin(framedata, ascii, "sphybridExample")`，記下框架數。</span><span class="sxs-lookup"><span data-stu-id="6e588-p191">Looking at the trace second-hand? Try using filters to orient yourself. In Netmon, run a search based on the URL, such as  `Containsbin(framedata, ascii, "sphybridExample")`, take note of the frame number.</span></span> 

<span data-ttu-id="6e588-p192">在 Wireshark 使用類似如下`frame contains "sphybridExample"`。如果您注意到您已經找到遠端 Winsock (RWS) 流量 （它可能顯示為 [PSH、 ACK] 中 Wireshark），請記得 RWS 連線可以稍後再相關 SYN-SYN/認可呈現稍早所述。</span><span class="sxs-lookup"><span data-stu-id="6e588-p192">In Wireshark use something like  `frame contains "sphybridExample"`. If you notice that you've found Remote Winsock (RWS) traffic (it may appear as a [PSH, ACK] in Wireshark), remember that RWS connects can be seen shortly before relevant SYN - SYN/ACKs, as discussed earlier.</span></span> 

<span data-ttu-id="6e588-487">此時，記錄的圖文框號碼、 drop 篩選、 按一下 [網路交談] 視窗中查看最接近 SYN.Netmon 中的所有流量</span><span class="sxs-lookup"><span data-stu-id="6e588-487">At this point, you can record the frame number, drop the filter, click All Traffic in the Network Conversations window in Netmon to look at the nearest SYN.</span></span> 

<span data-ttu-id="6e588-488">重要的，如果您未收到任何追蹤時間的 IP 位址資訊，請尋找您的 URL 中追蹤 (的一部分`sphybridExample-my.sharepoint.com`、 例如)，將會提供您所篩選的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6e588-488">Importantly, if you didn't receive any of the IP address information at the time of the trace, finding your URL in the trace (part of `sphybridExample-my.sharepoint.com`, for example), will give you IP addresses to filter by.</span></span> 

<span data-ttu-id="6e588-p193">追蹤您感興趣看不到中找到的連線。您可以篩選的 IP 位址或選取特定的交談 Id 使用網路交談視窗中 Netmon 任一掃描追蹤，來執行這項作業。一旦您已經找到 SYN 封包，展開 [TCP （在 Netmon) 或傳輸控制通訊協定 （在 Wireshark) 台中之圖文框的詳細資訊。展開 [TCP 選項及 MaxSegementSize。尋找相關的接收圖文框並依序展開 [TCP 選項及 MaxSegmentSize。較小的兩個值會是最大的區段大小。在此圖片中，讓使用中稱為 [TCP 疑難排解 Netmon 的內建欄。</span><span class="sxs-lookup"><span data-stu-id="6e588-p193">Locate the connection in the trace that you're interested in seeing. You may do this by either scanning the trace, by filtering by IP addresses, or by selecting specific Conversation IDs using the Network Conversations window in Netmon. Once you've found the SYN packet, expand TCP (in Netmon), or Transmission Control Protocol (in Wireshark) in the Frame Details panel. Expand TCP Options and MaxSegementSize. Locate the related SYN-ACK frame and Expand TCP Options and MaxSegmentSize. The smaller of the two values will be your Maximum Segment Size. In this picture, I make use of the built-in Column in Netmon called TCP Troubleshoot.</span></span>  

![Netmon 使用內建欄篩選的網路追蹤。](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

<span data-ttu-id="6e588-p194">內建欄是頂端的**圖文框的詳細資訊**面板。（切換回至在標準模式，再按一下 [欄]，，然後選擇 [時區）。</span><span class="sxs-lookup"><span data-stu-id="6e588-p194">The built-in column is at the top of the **Frame Details** panel. (To switch back to your normal view, click Columns again, and then choose Time Zone.)</span></span> 

<span data-ttu-id="6e588-499">![在欄位下拉式清單中尋找 TCP 疑難排解選項 (在框架摘要的頂端)。](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)         </span><span class="sxs-lookup"><span data-stu-id="6e588-499">![Where to find the Columns drop down for the TCP Troubleshoot option (on top of the Frame Summary).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)         </span></span>  
<span data-ttu-id="6e588-p195">以下是篩選過的追蹤 Wireshark 中。有特定的 MSS 值的篩選器 ( `tcp.options.mss`)。下方的 Wireshark 等於圖文框的詳細資訊連結的框架 SYN SYN/ACK、 ACK 信號交換 （所以包圍 47 ACK、 46 SYN/ACK 連結、 連結 43 SYN） 以方便這種工作。</span><span class="sxs-lookup"><span data-stu-id="6e588-p195">Here's a filtered trace in Wireshark. There is a filter specific to the MSS value ( `tcp.options.mss`). The frames of a SYN, SYN/ACK, ACK handshake are linked at the bottom of the Wireshark equivalent to Frame Details (so frame 47 ACK, links to 46 SYN/ACK, links to 43 SYN) to make this kind of work easier.</span></span> 

![追蹤 Wireshark 中由 tcp.options.mss 的最大區段大小 (MSS) 的篩選。](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)         
<span data-ttu-id="6e588-504">如果您需要檢查選擇性指 （在此矩陣中的下一個主題），不會關閉您追蹤 ！</span><span class="sxs-lookup"><span data-stu-id="6e588-504">If you need to check Selective Acknowledgment (next topic in this matrix), don't close your trace!</span></span>

### <a name="selective-acknowledgment"></a><span data-ttu-id="6e588-505">選擇性指</span><span class="sxs-lookup"><span data-stu-id="6e588-505">Selective Acknowledgment</span></span>

<span data-ttu-id="6e588-p196">位於 SYN-SYN/通知必須報告為許可 SYN 和 SYN/通知選擇性指 (SACK) 中的允許更順暢地呈現資料時的封包重新傳輸或封包移遺失。裝置可以停用這項功能可能會導致效能問題。</span><span class="sxs-lookup"><span data-stu-id="6e588-p196">Found in the SYN - SYN/ACK. Must be reported as Permitted in both SYN and SYN/ACK. Selective Acknowledgment (SACK) allows for smoother retransmission of data when a packet or packets go missing. Devices can disable this feature, which can lead to performance problems.</span></span> 

<span data-ttu-id="6e588-p197">如果您正在背後的 proxy 或使用 NAT，請一定要執行這項測試從用戶端 proxy/輸出/NAT 和 proxy/輸出/至 Office 365 的 NAT 獲得最佳結果 ！這些是不同的 TCP 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6e588-p197">If you're behind a proxy, or you are using a NAT, remember to run this test from client to proxy/egress/NAT, and from proxy/egress/NAT to Office 365 for best results! These are different TCP sessions.</span></span>

#### <a name="tool"></a><span data-ttu-id="6e588-512">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-512">Tool:</span></span> 

<span data-ttu-id="6e588-513">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-513">Netmon</span></span> 

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-514">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-514">What to look for:</span></span>

<span data-ttu-id="6e588-p198">選擇性指 (SACK) 是另一個參數中的 SYN/接收信號交換。您可以篩選 SYN-SYN/ACK 許多方法可讓您追蹤。</span><span class="sxs-lookup"><span data-stu-id="6e588-p198">Selective Acknowledgment (SACK) is another parameter in the SYN-SYN/ACK handshake. You can filter your trace for SYN - SYN/ACK many ways.</span></span> 

<span data-ttu-id="6e588-p199">追蹤您感興趣看不到 [掃描追蹤篩選的 IP 位址或依序按一下 [使用網路交談視窗中 Netmon 交談 ID 之中找到連線。一旦您已經找到 SYN 封包，展開 [TCP 中 Netmon 或 Wireshark 圖文框詳細資料] 區段中的傳輸控制通訊協定。展開 [TCP 選項，然後 SACK。尋找相關的接收圖文框並依序展開 [TCP 選項和其 SACK] 欄位。讓特定 SACK 允許在 SYN 和 SYN/通知以下是 SACK 值視為 Netmon 和 Wireshark 中。</span><span class="sxs-lookup"><span data-stu-id="6e588-p199">Locate the connection in the trace that you're interested in seeing either by scanning the trace, filtering by IP addresses, or by clicking a Conversation ID using the Network Conversations window in Netmon. Once you've found the SYN packet, expand TCP in Netmon, or Transmission Control Protocol in Wireshark in the Frame Details section. Expand TCP Options and then SACK. Locate the related SYN-ACK frame and Expand TCP Options and its SACK field. Make certain SACK is permitted in both SYN and SYN/ACK. Here are SACK values as seen in both Netmon and Wireshark.</span></span>

![選擇性指 (SACK) 中 Netmon 結果的 tcp.flags.syn = = 1。](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)           <br/> ![Wireshark 中所示的 SACK 及篩選器 tcp.flags.syn == 1。](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)        

### <a name="dns-geolocation"></a><span data-ttu-id="6e588-525">DNS 地理位置</span><span class="sxs-lookup"><span data-stu-id="6e588-525">DNS Geolocation</span></span> 

<span data-ttu-id="6e588-526">其中世界的 Office 365 會嘗試解析 DNS 呼叫效果連線速度。</span><span class="sxs-lookup"><span data-stu-id="6e588-526">Where in the world Office 365 tries to resolve your DNS call effects your connection speed.</span></span> 

<span data-ttu-id="6e588-p200">Outlook Online 中第一個 DNS 查閱完成後，該 DNS 的位置會用以連線至最接近的資料中心。您會連線至 Outlook Online CAS 伺服器，將會使用骨幹網路連線至資料中心內 (dC) 儲存您的資料。這是更快。</span><span class="sxs-lookup"><span data-stu-id="6e588-p200">In Outlook Online, after the first DNS lookup is completed, the location of that DNS will be used to connect to your nearest datacenter. You will be connected to an Outlook Online CAS server, which will use the backbone network to connect to the datacenter (dC) where your data is stored. This is faster.</span></span>

<span data-ttu-id="6e588-530">當存取 SharePoint Online、 出國出差的使用者會將您導向到其作用中資料中心-屬於其位置根據其 SPO 租用戶 dC 的常用基底 (賣中 USA dC 如果使用者如果 USA 型)。</span><span class="sxs-lookup"><span data-stu-id="6e588-530">When accessing SharePoint Online, a user traveling abroad will be directed to their active datacenter -- that's the dC whose location is based on their SPO tenant's home-base (so, a dC in the USA if the user if USA-based).</span></span>  <br/>  <span data-ttu-id="6e588-p201">Lync online 會有作用中節點中多個 dC 一次。要求時傳送的 Lync online 執行個體中，Microsoft 的 DNS 會決定在全球要求來自哪個位置，並傳回 IP 位址從最接近地區性 dC 其中 Lync online 是使用中。</span><span class="sxs-lookup"><span data-stu-id="6e588-p201">Lync online has active nodes in more than one dC at a time. When requests are sent for Lync online instances, Microsoft's DNS will determine where in the world the request came from, and return IP addresses from the nearest regional dC where Lync online is active.</span></span> 

> [!TIP]
> <span data-ttu-id="6e588-p202">需要更了解用戶端如何連線至 Office 365？請查看下列[用戶端連線](https://technet.microsoft.com/en-us/library/dn741250.aspx)參考文章 （和其很有幫助圖形）。</span><span class="sxs-lookup"><span data-stu-id="6e588-p202">Need to know more about how clients connect to Office 365? Take a look at the [Client Connectivity](https://technet.microsoft.com/en-us/library/dn741250.aspx) reference article (and its helpful graphics).</span></span>           
#### <a name="tools"></a><span data-ttu-id="6e588-535">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-535">Tools:</span></span>

- <span data-ttu-id="6e588-536">Ping</span><span class="sxs-lookup"><span data-stu-id="6e588-536">Ping</span></span>
- <span data-ttu-id="6e588-537">PsPing</span><span class="sxs-lookup"><span data-stu-id="6e588-537">PsPing</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="6e588-538">要尋找的功能：</span><span class="sxs-lookup"><span data-stu-id="6e588-538">What to look for:</span></span>

<span data-ttu-id="6e588-p203">在大多數情況下結果中傳回的地區資料中心 (dC) 的 IP 位址的 Microsoft DNS 應該從用戶端的 DNS 伺服器的名稱解析 Microsoft 的 DNS 伺服器的要求。這代表您什麼？如果您 headquarters 班加羅爾 （印度），但在美國，當瀏覽器中的 Outlook Online 提出要求時所出差、 Microsoft 的 DNS 伺服器應該另一方面您的 IP 位址至美國-地區資料中心中的資料中心。視郵件是從 Outlook，該資料會透過 Microsoft 的快速骨幹網路旅行社之間的資料中心。</span><span class="sxs-lookup"><span data-stu-id="6e588-p203">Requests for name resolution from the client's DNS servers to Microsoft's DNS servers should in most cases result in Microsoft DNS returning the IP address of a regional datacenter (dC). What does this mean for you? If your headquarters are in Bangalore, India, but you are traveling in the United States, when your browser makes a request for Outlook Online, Microsoft's DNS servers should hand you IP addresses to datacenters in the United States -- a regional datacenter. If mail is needed from Outlook, that data will travel across Microsoft's quick backbone network between the datacenters.</span></span>

<span data-ttu-id="6e588-p204">名稱解析完成接近使用者位置盡位置時的 DNS 運作速度最快。如果您是在歐洲、 您要移至 [歐洲、 Microsoft DNS 與 （理想的情況下） 處理歐洲地區資料中心。從用戶端的 Europe 移至 DNS 和 America 中的資料中心的效能會較慢。</span><span class="sxs-lookup"><span data-stu-id="6e588-p204">DNS works fastest when name resolution is done as close to the user location as possible. If you're in Europe, you want to go to a Microsoft DNS in Europe, and (ideally) deal with a datacenter in Europe. Performance from a client in Europe going to DNS and a datacenter in America will be slower.</span></span>

<span data-ttu-id="6e588-p205">若要判斷出世界中您的 DNS 要求目前正在路由 outlook.office365.com 針對執行 Ping 工具。如果您是在歐洲，您應該會看到類似如下 outlook emeawest.office365.com 的回覆。在美洲預期類似如下 outlook namnorthwest.office365.com。</span><span class="sxs-lookup"><span data-stu-id="6e588-p205">Run the Ping tool against outlook.office365.com to determine where in the world your DNS request is being routed. If you are in Europe, you should see a reply from something like outlook-emeawest.office365.com. In the Americas, expect something like outlook-namnorthwest.office365.com.</span></span> 

<span data-ttu-id="6e588-p206">開啟命令提示字元中用戶端電腦上 (透過開始\>執行\>cmd 或 Windows 鍵\>輸入 cmd)。輸入 ping outlook.office365.com 並按 ENTER。請記住，如果您想要指定 ping IPv4 透過指定-4。您可能會失敗回覆跳 ICMP 封包，但您應該會看到的要求已路由傳送的 DNS 名稱。如果您想要查看此連線的延遲號碼 PsPing 嘗試 ping 所傳回之伺服器的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="6e588-p206">Open the command prompt on the client computer (via Start \> Run \> cmd or Windows key \> type cmd). Type ping outlook.office365.com and press ENTER. Remember, to specify -4 if you want to specify to ping via IPv4. You may fail to get a reply from the ICMP packets, but you should see the name of the DNS to which the request was routed. If you want to see the latency numbers for this connection try PsPing to the IP address of the server that is returned by ping.</span></span>  

![outlook.office365.com 的 Ping，顯示 outlook-namnorthwest 中的解析。](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)           
![PSPing ping 回到 outlook.office365.com 顯示平均 28 毫秒延遲的 IP 位址。](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)           
### <a name="office-365-application-troubleshooting"></a><span data-ttu-id="6e588-556">Office 365 的應用程式疑難排解</span><span class="sxs-lookup"><span data-stu-id="6e588-556">Office 365 Application Troubleshooting</span></span>

#### <a name="tools"></a><span data-ttu-id="6e588-557">工具：</span><span class="sxs-lookup"><span data-stu-id="6e588-557">Tools:</span></span> 

- <span data-ttu-id="6e588-558">Netmon</span><span class="sxs-lookup"><span data-stu-id="6e588-558">Netmon</span></span>
- <span data-ttu-id="6e588-559">HTTPWatch</span><span class="sxs-lookup"><span data-stu-id="6e588-559">HTTPWatch</span></span>
- <span data-ttu-id="6e588-560">在瀏覽器 F12 主控台</span><span class="sxs-lookup"><span data-stu-id="6e588-560">F12 Console in the browser</span></span>

<span data-ttu-id="6e588-p207">我們不涵蓋中特定應用程式疑難排解特定網路的本文中所使用的工具。可找到資源，但是您*可以*使用[此頁面上](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)。</span><span class="sxs-lookup"><span data-stu-id="6e588-p207">We don't cover tools used in application-specific troubleshooting in this network-specific article. But you'll find resources you  *can*  use [on this page](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).</span></span>
   
## <a name="related-topics"></a><span data-ttu-id="6e588-563">相關主題</span><span class="sxs-lookup"><span data-stu-id="6e588-563">Related Topics</span></span>

[<span data-ttu-id="6e588-564">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="6e588-564">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
<span data-ttu-id="6e588-565">[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)</span><span class="sxs-lookup"><span data-stu-id="6e588-565">[Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)</span></span>
  

