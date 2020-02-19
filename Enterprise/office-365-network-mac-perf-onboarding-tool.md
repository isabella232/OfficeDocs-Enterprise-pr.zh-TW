---
title: Office 365 網路上架工具 M365 系統管理中心 （預覽）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 網路上架工具 M365 系統管理中心 （預覽）
ms.openlocfilehash: 7ead201d78c1a6ce971c6ff09d4be9c0d2c76be6
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106283"
---
# <a name="office-365-network-onboarding-tool-in-the-m365-admin-center-preview"></a><span data-ttu-id="0a7b8-103">Office 365 網路上架工具 M365 系統管理中心 （預覽）</span><span class="sxs-lookup"><span data-stu-id="0a7b8-103">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>

<span data-ttu-id="0a7b8-104">Office 365 網路上架工具位於<https://connectivity.office.com>。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-104">The Office 365 network onboarding tool is located at <https://connectivity.office.com>.</span></span> <span data-ttu-id="0a7b8-105">它是附加的工具，以網路深入解析和網路分數資訊，可在 Microsoft 365 系統管理中心在**健康情況下 |網路效能**功能表。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-105">It is an adjunct tool to the network insights and network score information available in the Microsoft 365 Admin Center under the **Health | Network Performance** menu.</span></span>

<span data-ttu-id="0a7b8-106">網路深入了解 Microsoft 365 系統管理中心根據您的 Office 365 租用戶的產品內測量值。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-106">The network insights in the Microsoft 365 Admin Center are based on in-product measurements for your Office 365 tenant.</span></span> <span data-ttu-id="0a7b8-107">相較之下，Office 365 網路上架工具的網路觀點，會在本機上工具中執行。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-107">In comparison, the network insights from the Office 365 network onboarding tool are run locally in the tool.</span></span> <span data-ttu-id="0a7b8-108">測試，可在產品完成限制及執行測試使用者的本機更多資料可收集產生更深入的見解。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-108">Testing that can be done in-product is limited and by running tests local to the user more data can be gathered resulting in deeper insights.</span></span> <span data-ttu-id="0a7b8-109">然後請考慮網路深入了解 Microsoft 365 系統管理中心中的會顯示已運用在特定的辦公室位置上的 Office 365 的網路問題。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-109">Consider then that the network insights in the Microsoft 365 Admin Center will show that there is a networking problem for use of Office 365 at a specific office location.</span></span> <span data-ttu-id="0a7b8-110">Office 365 網路上架工具可協助識別建議的網路效能改進動作而導致該問題的根本原因。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-110">The Office 365 network onboarding tool can help to identify the root cause of that problem leading to a recommended network performance improvement action.</span></span>

<span data-ttu-id="0a7b8-111">我們建議，這些一起使用可評估為 Microsoft 365 系統管理中心中每個辦公室位置的網路品質狀態，並測試部署之後，可以找到更多細節根據 Office 365 網路上架工具。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-111">We recommend that these be used together where networking quality status can be assessed for each office location in the Microsoft 365 Admin Center and more specifics can be found after deployment of testing based on the Office 365 network onboarding tool.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0a7b8-112">網路效能建議、 深入了解 Microsoft 365 系統管理中心中的評估目前處於預覽狀態，並只適用於具有已註冊功能預覽計畫的 Office 365 租用戶。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-112">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="the-advanced-tests-client-application"></a><span data-ttu-id="0a7b8-113">進階的測試用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="0a7b8-113">The advanced tests client application</span></span>

<span data-ttu-id="0a7b8-114">有兩個組件至 Office 365 網路上架工具。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-114">There are two parts to the Office 365 network onboarding tool.</span></span> <span data-ttu-id="0a7b8-115">沒有網站<https://connectivity.office.com>，而且沒有可下載的 Windows 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-115">There is the web site <https://connectivity.office.com> and there is a downloadable Windows client application.</span></span> <span data-ttu-id="0a7b8-116">可下載的用戶端執行進階的網路連線測試，且大多數的測試需要此選項，即可執行。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-116">The downloadable client runs advanced network connectivity tests and most of the tests require this to be run.</span></span>

<span data-ttu-id="0a7b8-117">您可以從網站中，執行進階用戶端測試，它會填入結果回 [web] 頁面上，因為它會執行。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-117">You can run the advanced client test from the web site, and it will populate results back into the web page as it runs.</span></span>

![O365 網路上架工具測試結果範例](Media/m365-mac-perf/m365-mac-perf-onboarding-tool-tests.png)

## <a name="user-office-location"></a><span data-ttu-id="0a7b8-119">使用者的辦公室位置</span><span class="sxs-lookup"><span data-stu-id="0a7b8-119">User office location</span></span>

<span data-ttu-id="0a7b8-120">使用者網頁瀏覽器中偵測到使用者的辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-120">The user office location is detected from the users web browser.</span></span> <span data-ttu-id="0a7b8-121">它用來識別特定的組件的企業周邊網路的網路距離。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-121">It is used to identify network distances to specific parts of the enterprise network perimeter.</span></span>

<span data-ttu-id="0a7b8-122">[地圖] 檢視會顯示使用者的辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-122">The user office location is shown on the map view.</span></span>

## <a name="distance-to-the-network-egress-location"></a><span data-ttu-id="0a7b8-123">距離的網路輸出位置</span><span class="sxs-lookup"><span data-stu-id="0a7b8-123">Distance to the network egress location</span></span>

<span data-ttu-id="0a7b8-124">我們找出伺服器端的網路輸出 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-124">We identify the network egress IP Address on the server side.</span></span> <span data-ttu-id="0a7b8-125">位置資料庫用來查閱網路輸出的概略位置，並判斷該位置到的位置之間的距離。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-125">Location databases are used to look up the approximate location for the network egress and determine the distance from that location to the office location.</span></span> <span data-ttu-id="0a7b8-126">如果超過 500 英哩 （800 公里） 之間的距離，這會顯示為網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-126">This is shown as a network insight if the distance is greater than 500 miles (800 kilometers).</span></span>

<span data-ttu-id="0a7b8-127">網路輸出位置是 [地圖] 檢視會顯示，而連線至指出內部企業 WAN 網路 backhaul 使用者辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-127">The network egress location is shown on the map view and connected to the user office location indicating the network backhaul inside of the enterprise WAN.</span></span>

<span data-ttu-id="0a7b8-128">從網路輸出 IP 位址進行查閱的位置可能不正確，這會從這項測試會導致為 false 的結果。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-128">The location looked up from the network egress IP Address may not be accurate and this would lead to a false result from this test.</span></span> <span data-ttu-id="0a7b8-129">若要驗證如果發生此錯誤針對特定的 IP 位址您可以使用可公開存取的網路的 IP 位址位置的網站。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-129">To validate if this error is occurring for a specific IP Address you can use publicly accessible network IP Address location web sites.</span></span>

<span data-ttu-id="0a7b8-130">Office 365 網路連線，建議您實作從使用者的辦公室位置的本機和直接的網路輸出至網際網路。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-130">Implementing local and direct network egress from user office locations to the Internet is recommended for Office 365 network connectivity.</span></span> <span data-ttu-id="0a7b8-131">本機和直接輸出的改善，是解決這個網路深入解析的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-131">Improvements to local and direct egress are the best way to address this network insight.</span></span>

## <a name="exchange-online-service-front-door"></a><span data-ttu-id="0a7b8-132">Exchange Online 服務的前哨</span><span class="sxs-lookup"><span data-stu-id="0a7b8-132">Exchange Online service front door</span></span>

<span data-ttu-id="0a7b8-133">在 Outlook 執行此動作，以及我們測量網路給它的 TCP 延遲從使用者的辦公室位置的相同方式來識別正在使用 Exchange Online 服務的前哨。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-133">The in-use Exchange Online service front door is identified in the same way that Outlook does this and we measure the network TCP latency from the user office location to it.</span></span> <span data-ttu-id="0a7b8-134">這些記錄會同時顯示與正在使用 Exchange Online 服務的前哨相較於清單中的目前位置的建議最佳服務前方門。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-134">These are both shown and the in-use Exchange Online service front door is compared to the list of recommended optimal service front doors for the current location.</span></span> <span data-ttu-id="0a7b8-135">如果未最佳化 Exchange Online 服務的前哨正在使用中，這會顯示為網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-135">This is shown as a network insight if a non-optimal Exchange Online service front door is in use.</span></span>

<span data-ttu-id="0a7b8-136">使用非最佳 Exchange Online 服務的前哨可能被因網路 backhaul 公司網路輸出之前在此情況下建議本機和直接的網路輸出。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-136">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="0a7b8-137">它也可能被造成所使用的遠端 DNS 遞迴解析程式伺服器在此情況下建議對齊 DNS 遞迴解析程式伺服器具有網路輸出。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-137">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="0a7b8-138">我們在 Exchange Online 服務前哨 TCP 延遲計算潛在的改進。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-138">We calculate a potential improvement in TCP latency to the Exchange Online service front door.</span></span> <span data-ttu-id="0a7b8-139">這是透過查看已測試的使用者辦公室位置網路延遲與減去室網路延遲從目前的位置 Exchange Online 服務的前哨。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-139">This is done by looking at the tested user office location network latency and subtracting the network latency from the current location to the closets Exchange Online service front door.</span></span> <span data-ttu-id="0a7b8-140">差異代表改進的潛在機會。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-140">The difference represents the potential opportunity for improvement.</span></span>

## <a name="comparison-of-performance-of-customers-in-the-area"></a><span data-ttu-id="0a7b8-141">效能的區域中的客戶的比較</span><span class="sxs-lookup"><span data-stu-id="0a7b8-141">Comparison of performance of customers in the area</span></span>

<span data-ttu-id="0a7b8-142">網路 TCP 延遲，Exchange Online 服務前哨之使用者辦公室位置是相較於其他 Office 365 的客戶在相同的地鐵區域。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-142">The network TCP latency of the user office location to the Exchange Online service front door is compared to other Office 365 customers in the same metro area.</span></span> <span data-ttu-id="0a7b8-143">網路深入了解會顯示 10%或以上的客戶相同地鐵區域中有更好的效能。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-143">A network insight is shown if 10% or more of customers in the same metro area have better performance.</span></span>

<span data-ttu-id="0a7b8-144">此網路深入了解就會產生根據縣/市中的所有使用者都擁有存取權的同一個電訊基礎結構，以及相同鄰近的網際網路電路和 Microsoft 的網路。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-144">This network insight is generated on the basis that all users in a city have access to the same telecommunications infrastructure and the same proximity to Internet circuits and Microsoft's network.</span></span>

## <a name="in-use-default-gateway"></a><span data-ttu-id="0a7b8-145">在 [使用預設閘道</span><span class="sxs-lookup"><span data-stu-id="0a7b8-145">In use default gateway</span></span>

<span data-ttu-id="0a7b8-146">在 [使用預設閘道是路由器，測試用戶端已針對路由的 TCP/IP 網路連線設定。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-146">The in-use default gateway is the router that the test client has configured for routing TCP/IP network connections.</span></span>

<span data-ttu-id="0a7b8-147">這僅提供資訊，而且不會增加任何網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-147">This is provided for information only and does not contribute to any network insight.</span></span>

## <a name="in-use-dns-servers"></a><span data-ttu-id="0a7b8-148">使用 DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="0a7b8-148">In use DNS server(s)</span></span>

<span data-ttu-id="0a7b8-149">這會顯示在 [執行測試用戶端電腦上設定之 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-149">This shows the DNS server configured on the client machine that ran the tests.</span></span> <span data-ttu-id="0a7b8-150">不過，這並不常見，它可能是 DNS 遞迴解析程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-150">It might be a DNS Recursive Resolver server however this is uncommon.</span></span> <span data-ttu-id="0a7b8-151">很多可能會為 DNS 轉寄站伺服器的 DNS 結果會快取，並將轉寄至另一部 DNS 伺服器任何未快取的 DNS 要求。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-151">It is more likely to be a DNS forwarder server which caches DNS results and forwards any uncached DNS requests to another DNS server.</span></span>

<span data-ttu-id="0a7b8-152">這僅提供資訊，而且不會增加任何網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-152">This is provided for information only and does not contribute to any network insight.</span></span>

## <a name="identified-dns-recursive-resolver-server"></a><span data-ttu-id="0a7b8-153">已識別的 DNS 遞迴解析程式伺服器</span><span class="sxs-lookup"><span data-stu-id="0a7b8-153">Identified DNS Recursive Resolver server</span></span>

<span data-ttu-id="0a7b8-154">在使用 DNS 遞迴解析程式識別的特定的 DNS 要求，然後它會接收來自同一個要求的 IP 位址詢問 DNS 名稱伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-154">The in-use DNS Recursive Resolver is identified by making a specific DNS request and then asking the DNS Name Server for the IP Address that it received the same request from.</span></span> <span data-ttu-id="0a7b8-155">此 IP 位址是 DNS 遞迴解析程式，它會查閱以找出該位置的 IP 位址位置資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-155">This IP Address is the DNS Recursive Resolver and it will be looked up in IP Address location databases to find the location.</span></span> <span data-ttu-id="0a7b8-156">然後計算使用者的辦公室位置至 DNS 遞迴解析程式伺服器的位置之間的距離。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-156">The distance from the user office location to the DNS Recursive Resolver server location is then calculated.</span></span> <span data-ttu-id="0a7b8-157">如果超過 500 英哩 （800 公里） 之間的距離，這會顯示為網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-157">This is shown as a network insight if the distance is greater than 500 miles (800 kilometers).</span></span>

<span data-ttu-id="0a7b8-158">從網路輸出 IP 位址進行查閱的位置可能不正確，這會從這項測試會導致為 false 的結果。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-158">The location looked up from the network egress IP Address may not be accurate and this would lead to a false result from this test.</span></span> <span data-ttu-id="0a7b8-159">若要驗證如果發生此錯誤針對特定的 IP 位址您可以使用可公開存取的網路的 IP 位址位置的網站。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-159">To validate if this error is occurring for a specific IP Address you can use publicly accessible network IP Address location web sites.</span></span>

<span data-ttu-id="0a7b8-160">此網路深入了解特別是會影響 Exchange Online 服務前哨的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-160">This network insight will specifically impact the selection of the Exchange Online service front door.</span></span> <span data-ttu-id="0a7b8-161">若要解決此深入了解本機和直接的網路輸出應該必要條件，然後 DNS 遞迴解析程式應該位於接近該網路輸出。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-161">To address this insight local and direct network egress should be a pre-requisite and then DNS Recursive Resolver should be located close to that network egress.</span></span>

## <a name="dns-lookup-of-exchange-online-front-end-server-and-sharepoint-online-front-end-server"></a><span data-ttu-id="0a7b8-162">Exchange Online 的前端伺服器和 SharePoint Online 的前端伺服器的 DNS 查閱</span><span class="sxs-lookup"><span data-stu-id="0a7b8-162">DNS lookup of Exchange Online front end server and SharePoint Online front end server</span></span>

<span data-ttu-id="0a7b8-163">這些顯示服務的前哨適用於下列兩個 Office 365 工作負載的 DNS 記錄。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-163">These show the DNS record for the service front door for these two Office 365 workloads.</span></span> <span data-ttu-id="0a7b8-164">他們所提供的資訊只且沒有任何關聯的網路深入解析。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-164">They are provided for information only and there is no associated network insight.</span></span>

## <a name="proxy-server-identification"></a><span data-ttu-id="0a7b8-165">Proxy 伺服器識別碼</span><span class="sxs-lookup"><span data-stu-id="0a7b8-165">Proxy server identification</span></span>

<span data-ttu-id="0a7b8-166">我們找出在本機電腦上設定的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-166">We identify proxy server(s) configured on the local machine.</span></span> <span data-ttu-id="0a7b8-167">我們找出任何這些設定中的網路路徑的最佳化類別 Office 365 的網路流量。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-167">We identify if any of these are configured in the network path for optimize category Office 365 network traffic.</span></span> <span data-ttu-id="0a7b8-168">我們找出使用者的辦公室位置的 proxy 伺服器之間的距離。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-168">We identify the distance from the user office location to the proxy servers.</span></span> <span data-ttu-id="0a7b8-169">距離在 ICMP ping 中有不同的測試第一次，如果失敗我們測試與 TCP ping 最後如果失敗我們查閱 IP 位址位置資料庫中的 proxy 伺服器的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-169">The distance is tested first by ICMP ping and if that fails we test with TCP ping and finally if that fails we look up the proxy server IP Address in an IP Address location database.</span></span> <span data-ttu-id="0a7b8-170">我們顯示網路深入見解如果 proxy 伺服器會進一步超過 500 英哩 （800 公里） 開使用者辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-170">We show a network insight if the proxy server is further than 500 miles (800 kilometers) away from the user office location.</span></span>

## <a name="media-quality-checks"></a><span data-ttu-id="0a7b8-171">媒體品質檢查</span><span class="sxs-lookup"><span data-stu-id="0a7b8-171">Media quality checks</span></span>

<span data-ttu-id="0a7b8-172">這項測試安裝及執行 Skype for Business 網路評估工具，並解譯結果。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-172">This test installs and runs the Skype for Business network assessment tool and interprets the results.</span></span> <span data-ttu-id="0a7b8-173">此工具可以在找到[https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885)。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-173">The tool can be found at [https://www.microsoft.com/download/details.aspx?id=53885](https://www.microsoft.com/download/details.aspx?id=53885).</span></span>

<span data-ttu-id="0a7b8-174">因為由 Microsoft Teams 音訊和視訊通話及會議功能，這些是 UDP 通訊協定測試。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-174">These are UDP protocol tests as is used by Microsoft Teams audio and video call and conferencing functionality.</span></span> <span data-ttu-id="0a7b8-175">我們測試 UDP 封包遺失、 UDP 網路延遲、 UDP 抖動和 UDP 封包重新排列。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-175">We test for UDP packet loss, UDP network latency, UDP jitter, and UDP packet reorder.</span></span> <span data-ttu-id="0a7b8-176">網路深入了解會顯示任何安全性是否放在允許的範圍。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-176">A network insight is shown if any of these are over the allowable range.</span></span>

## <a name="tcp-connectivity-tests"></a><span data-ttu-id="0a7b8-177">TCP 連線測試</span><span class="sxs-lookup"><span data-stu-id="0a7b8-177">TCP Connectivity tests</span></span>

<span data-ttu-id="0a7b8-178">我們測試從使用者的辦公室位置的 HTTP 連線至所有必要的 Office 365 網路端點。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-178">We test for HTTP connectivity from the user office location to all of the required Office 365 network endpoints.</span></span> <span data-ttu-id="0a7b8-179">這些會在這裡發佈[https://aka.ms/o365ip](https://aka.ms/o365ip)。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-179">These are published at [https://aka.ms/o365ip](https://aka.ms/o365ip).</span></span> <span data-ttu-id="0a7b8-180">網路深入了解會顯示它無法連接至任何所需的網路端點。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-180">A network insight is shown for any required network endpoints which cannot be connected to.</span></span>

<span data-ttu-id="0a7b8-181">連線是被封鎖的 proxy 伺服器、 防火牆或另一個網路安全性裝置企業網路周邊網路上或在使用雲端 proxy 為。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-181">Connectivity ay be blocked by a proxy server, a firewall, or another network security device on the enterprise network perimeter or in use as a cloud proxy.</span></span>

## <a name="ssl-interception-tests"></a><span data-ttu-id="0a7b8-182">SSL 攔截測試</span><span class="sxs-lookup"><span data-stu-id="0a7b8-182">SSL interception tests</span></span>

<span data-ttu-id="0a7b8-183">我們測試每個必要的 Office 365 網路端點中最佳化或允許類別所定義在 SSL 憑證[https://aka.ms/o365ip](https://aka.ms/o365ip)。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-183">We test the SSL certificate at each required Office 365 network endpoint that is in the optimize or allow category as defined at [https://aka.ms/o365ip](https://aka.ms/o365ip).</span></span> <span data-ttu-id="0a7b8-184">如果任何測試找不到 Microsoft SSL 憑證，然後連線加密的網路必須有已遭到攔截介的網路裝置。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-184">If any tests do not find a Microsoft SSL certificate, then the encrypted network connected must have been intercepted by an intermediary network device.</span></span> <span data-ttu-id="0a7b8-185">網路深入了解會顯示任何攔截加密的網路端點。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-185">A network insight is shown on any intercepted encrypted network endpoints.</span></span>

<span data-ttu-id="0a7b8-186">SSL 憑證找到，不 Microsoft 所提供，我們示範測試並在使用 SSL 憑證擁有者的 FQDN。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-186">Where an SSL certificate is found that isn't provided by Microsoft, we show the FQDN for the test and the in-use SSL certificate owner.</span></span> <span data-ttu-id="0a7b8-187">此 SSL 憑證擁有者可能是 proxy 伺服器的廠商，或是可能很企業自我簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-187">This SSL certificate owner may be a proxy server vendor, or it may be an enterprise self-signed certificate.</span></span>

## <a name="network-path-diagnostics"></a><span data-ttu-id="0a7b8-188">網路路徑診斷</span><span class="sxs-lookup"><span data-stu-id="0a7b8-188">Network path diagnostics</span></span>

<span data-ttu-id="0a7b8-189">本節說明 Exchange Online 服務前哨、 SharePoint Online 服務的前哨，及 Microsoft Teams 服務前哨 ICMP traceroute 的結果。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-189">This section shows the results of an ICMP traceroute to the Exchange Online service front door, the SharePoint Online service front door, and the Microsoft Teams service front door.</span></span> <span data-ttu-id="0a7b8-190">它僅提供資訊，且沒有任何關聯的網路深入了解。</span><span class="sxs-lookup"><span data-stu-id="0a7b8-190">It is provided for information only and there is no associated network insight.</span></span>

## <a name="related-topics"></a><span data-ttu-id="0a7b8-191">相關主題</span><span class="sxs-lookup"><span data-stu-id="0a7b8-191">Related topics</span></span>

[<span data-ttu-id="0a7b8-192">在 Microsoft 365 系統管理中心 （預覽） 的網路效能建議</span><span class="sxs-lookup"><span data-stu-id="0a7b8-192">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="0a7b8-193">Office 365 網路效能觀點 （預覽）</span><span class="sxs-lookup"><span data-stu-id="0a7b8-193">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="0a7b8-194">Office 365 網路評估 （預覽）</span><span class="sxs-lookup"><span data-stu-id="0a7b8-194">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)
