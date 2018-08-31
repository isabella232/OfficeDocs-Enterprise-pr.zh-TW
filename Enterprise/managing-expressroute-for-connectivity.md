---
title: 管理 ExpressRoute for Office 365 連線
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365 ExpressRoute 提供而不需要到網際網路的輸出至所有流量到達許多 Office 365 服務的替代路由路徑。雖然仍需要網際網路連線至 Office 365 時，Microsoft 通告 BGP 透過您的網路特定路由會讓直接 ExpressRoute 基礎的電路慣用除非有您網路中的其他設定。要設定來管理此路由包含三個一般區域首碼篩選、 安全性及規範。
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539988"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a><span data-ttu-id="5dbe6-105">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="5dbe6-105">Managing ExpressRoute for Office 365 connectivity</span></span>

<span data-ttu-id="5dbe6-p102">Office 365 ExpressRoute 提供而不需要到網際網路的輸出至所有流量到達許多 Office 365 服務的替代路由路徑。雖然仍需要網際網路連線至 Office 365 時，Microsoft 通告 BGP 透過您的網路特定路由會讓直接 ExpressRoute 基礎的電路慣用除非有您網路中的其他設定。要設定來管理此路由包含三個一般區域首碼篩選、 安全性及規範。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p102">ExpressRoute for Office 365 offers an alternative routing path to reach many Office 365 services without needing all traffic to egress to the internet. Although the internet connection to Office 365 is still needed, the specific routes that Microsoft advertises through BGP to your network make the direct ExpressRoute circuit preferred unless there are other configurations in your network. The three common areas you may want to configure to manage this routing include prefix filtering, security, and compliance.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5dbe6-p103">Microsoft 變更 Microsoft Peering 路由網域檢閱的 Azure ExpressRoute 的方式。啟動 2017 年 7 月 31 所有 Azure ExpressRoute 客戶可以都啟用 Microsoft Peering Azure 系統管理主控台從直接或透過 PowerShell。啟用 Microsoft Peering 之後, 任何客戶可以建立路由篩選器以接收 BGP 路由廣告 Dynamics 365 客戶參與應用程式 （前身為 CRM Online）。他們可以建立路由篩選 for Office 365 之前需要 Azure ExpressRoute for Office 365 的客戶必須從 Microsoft 取得檢閱。請連絡您的 Microsoft 帳戶小組來了解如何要求啟用 Office 365 ExpressRoute 檢閱。未經授權嘗試建立 Office 365 路由篩選的訂閱將收到[錯誤訊息](https://support.microsoft.com/kb/3181709)</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p103">Microsoft changed how the Microsoft Peering routing domain is reviewed for Azure ExpressRoute. Starting July 31st, 2017, all Azure ExpressRoute customers can enable Microsoft Peering directly from the Azure Administrative console or via PowerShell. After enabling Microsoft Peering, any customer can create route filters to receive BGP route advertisements for Dynamics 365 Customer Engagement applications (Formerly known as CRM Online). Customers needing Azure ExpressRoute for Office 365 must obtain review from Microsoft before they can create route filters for Office 365. Please contact your Microsoft Account team to learn about how to request a review for enabling Office 365 ExpressRoute. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709)</span></span>
  
## <a name="prefix-filtering"></a><span data-ttu-id="5dbe6-115">字首篩選</span><span class="sxs-lookup"><span data-stu-id="5dbe6-115">Prefix filtering</span></span>

<span data-ttu-id="5dbe6-p104">Microsoft 建議客戶接受所有 BGP 路由如 microsoft 通告、 所提供之路由、 經歷嚴密的檢閱和驗證的程序移除無法新增至任何好處。ExpressRoute 原本就會提供與篩選在客戶端沒有輸入路由的 IP 前置詞擁有權、 完整性和規模-例如建議的控制項。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p104">Microsoft recommends that customers accept all BGP routes as advertised from Microsoft, the routes provided undergo a rigorous review and validation process removing any benefits to added scrutiny. ExpressRoute natively offers the recommended controls such as IP prefix ownership, integrity, and scale - with no inbound route filtering on the customer side.</span></span>
  
<span data-ttu-id="5dbe6-p105">如果您需要的路由擁有權的其他驗證跨 ExpressRoute 公用對等，您可以檢查針對所有 IPv4 和 IPv6 IP 前置字元的清單，表示[Microsoft 的公用 IP 範圍](https://www.microsoft.com/download/details.aspx?id=53602)的公告所的路由。這些範圍涵蓋的完整 Microsoft 位址空間，並提供可靠的一組篩選依據的範圍，也提供其他保護擔心非 Microsoft 擁有路由到遺漏的客戶常，變更其環境。事件沒有變更，則會由上個月第 1 和] 頁面上的 [**詳細資料**] 區段的版本號碼會變更每次更新檔案。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p105">If you require additional validation of route ownership across ExpressRoute public peering, you can check the advertised routes against the list of all IPv4 and IPv6 IP prefixes that represent [Microsoft's public IP ranges](https://www.microsoft.com/download/details.aspx?id=53602). These ranges cover the full Microsoft address space and change infrequently, providing a reliable set of ranges to filter against that also provides additional protection to customers who are concerned about non-Microsoft owned routes leaking into their environment. In the event there is a change, it will be made on the 1st of the month and the version number in the **details** section of the page will change every time the file is updated.</span></span>
  
<span data-ttu-id="5dbe6-p106">有許多避免產生前置詞篩選清單的[Office 365 Url 和 IP 位址範圍](https://aka.ms/o365endpoints)使用的原因。包括下列：</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p106">There are a number of reasons to avoid the use of the [Office 365 URLs and IP address ranges](https://aka.ms/o365endpoints) for generating prefix filter lists. Including the following:</span></span>
  
- <span data-ttu-id="5dbe6-123">Office 365 IP 前置詞、 經歷許多常用為基礎的變更。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-123">The Office 365 IP prefixes undergo lots of changes on a frequent basis.</span></span>

- <span data-ttu-id="5dbe6-124">Office 365 Url 和 IP 位址範圍的設計用來管理防火牆允許清單與 Proxy 基礎結構、 未傳送。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-124">The Office 365 URLs and IP address ranges are designed for managing firewall allow lists and Proxy infrastructure, not routing.</span></span>

- <span data-ttu-id="5dbe6-125">Office 365 Url 和 IP 位址範圍涵蓋其他 Microsoft 服務可能會涵蓋 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-125">The Office 365 URLs and IP address ranges do not cover other Microsoft services that may be in scope for your ExpressRoute connections.</span></span>

<span data-ttu-id="5dbe6-126">| |</span><span class="sxs-lookup"><span data-stu-id="5dbe6-126"></span></span>
|<span data-ttu-id="5dbe6-127">**選項**</span><span class="sxs-lookup"><span data-stu-id="5dbe6-127">**Option**</span></span>|<span data-ttu-id="5dbe6-128">**複雜性**</span><span class="sxs-lookup"><span data-stu-id="5dbe6-128">**Complexity**</span></span>|<span data-ttu-id="5dbe6-129">**變更控制項**</span><span class="sxs-lookup"><span data-stu-id="5dbe6-129">**Change Control**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="5dbe6-130">接受所有的 Microsoft 路由</span><span class="sxs-lookup"><span data-stu-id="5dbe6-130">Accept all Microsoft routes</span></span>  <br/> |<span data-ttu-id="5dbe6-131">**低：** 客戶會依賴 Microsoft 控制項以確保正確且擁有的所有路由。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-131">**Low:** Customer relies upon Microsoft controls to ensure all routes are properly owned.</span></span>  <br/> |<span data-ttu-id="5dbe6-132">無</span><span class="sxs-lookup"><span data-stu-id="5dbe6-132">None</span></span>  <br/> |
|<span data-ttu-id="5dbe6-133">篩選 Microsoft 擁有 supernets</span><span class="sxs-lookup"><span data-stu-id="5dbe6-133">Filter Microsoft owned supernets</span></span>  <br/> |<span data-ttu-id="5dbe6-134">**中型：** 客戶實作允許擁有路由的 Microsoft 摘要的前置詞篩選清單。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-134">**Medium:** Customer implements summarized prefix filter lists to allow only Microsoft owned routes.</span></span>  <br/> |<span data-ttu-id="5dbe6-135">客戶必須確定非經常性更新便會反映在路由篩選器。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-135">Customers must ensure the infrequent updates are reflected in route filters.</span></span>  <br/> |
|<span data-ttu-id="5dbe6-136">篩選 Office 365 IP 範圍</span><span class="sxs-lookup"><span data-stu-id="5dbe6-136">Filter Office 365 IP ranges</span></span>  <br/> [!CAUTION] <span data-ttu-id="5dbe6-137">不建議使用</span><span class="sxs-lookup"><span data-stu-id="5dbe6-137">Not-Recommended</span></span>
|<span data-ttu-id="5dbe6-138">**高：** 客戶篩選根據已定義的 Office 365 IP 前置詞的路由。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-138">**High:** Customer filters routes based on defined Office 365 IP prefixes.</span></span>  <br/> |<span data-ttu-id="5dbe6-139">客戶必須實作完善變更管理程序的每月的更新。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-139">Customers must implement a robust change management process for the monthly updates.</span></span>  <br/> [!CAUTION]<span data-ttu-id="5dbe6-p107">此解決方案需要持續進行的重大變更。尚未實行的時間可能會導致服務中斷的變更。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p107"> This solution requires significant on-going changes. Changes not implemented in time will likely result in a service outage.</span></span>   |

<span data-ttu-id="5dbe6-p108">連線至 Office 365 使用 Azure ExpressRoute 根據 BGP 廣告的特定代表的網路之部署 Office 365 端點的 IP 子網路。Office 365 與 Office 365 所組成的服務號碼的全域性質，因為客戶通常有管理它們接受其網路廣告需要。如果您擔心與通告到您的環境的前置字元的數字， [BGP 社群](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)功能可讓您篩選到特定的一段 Office 365 服務廣告。此功能目前處於預覽。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p108">Connecting to Office 365 using Azure ExpressRoute is based on BGP advertisements of specific IP subnets that represent networks where Office 365 endpoints are deployed. Due to the global nature of Office 365 and the number of services that make up Office 365, customers often have a need to manage the advertisements they accept on their network. If you're concerned with number of prefixes advertised into your environment, the [BGP community](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) feature allows you to filter the advertisements to a specific set of Office 365 services. This feature is now in preview.</span></span>
  
<span data-ttu-id="5dbe6-p109">不論您管理來自 Microsoft BGP 路由廣告方式，您將不會獲得任何特殊公開給 Office 365 服務相較於透過網際網路基礎的電路表達連線至 Office 365。Microsoft 維護同一個安全性、 規範、 及效能層級的客戶用來連線到 Office 365 的電路型別無關。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p109">Regardless of how you manage the BGP route advertisements coming from Microsoft, you won't gain any special exposure to Office 365 services when compared to connecting to Office 365 over an internet circuit alone. Microsoft maintains the same security, compliance, and performance levels regardless of the type of circuit a customer uses to connect to Office 365.</span></span>
  
### <a name="security"></a><span data-ttu-id="5dbe6-148">安全性</span><span class="sxs-lookup"><span data-stu-id="5dbe6-148">Security</span></span>

<span data-ttu-id="5dbe6-p110">Microsoft 建議您維護自己網路和安全性周邊控制項連線移到與 ExpressRoute 公用和 Microsoft 對等，其中包含與 Office 365 服務的連線。安全性控管應網路要求之旅行社輸出從您的網路到 Microsoft 的網路，以及從 Microsoft 的網路輸入您的網路位置。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p110">Microsoft recommends that you maintain your own network and security perimeter controls for connections going to and from ExpressRoute public and Microsoft peering, which includes connections to and from Office 365 services. Security controls should be in place for network requests that travel outbound from your network to Microsoft's network as well as inbound from Microsoft's network to your network.</span></span>
  
#### <a name="outbound-from-customer-to-microsoft"></a><span data-ttu-id="5dbe6-151">從客戶輸出到 Microsoft</span><span class="sxs-lookup"><span data-stu-id="5dbe6-151">Outbound from Customer to Microsoft</span></span>
  
<span data-ttu-id="5dbe6-p111">當電腦連線到 Office 365 時，可連至相同的一組不論是否透過網際網路或 ExpressRoute 電路進行連線的端點。無論所使用的電路，Microsoft 建議您將 Office 365 服務，視為多信任比一般網際網路目的地的電話。輸出安全性控管您應著重於的連接埠和通訊協定以減少衝擊並持續維護最小化。使用[Office 365 端點](https://aka.ms/o365endpoints)參考文章中所需的連接埠資訊。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p111">When computers connect to Office 365, they connect to the same set of endpoints regardless of whether the connection is made over an internet or ExpressRoute circuit. Regardless of the circuit being used, Microsoft recommends that you treat Office 365 services as more trusted than generic internet destinations. Your outbound security controls should focus on the ports and protocols to reduce exposure and minimize ongoing maintenance. The required port information is available in the [Office 365 endpoints](https://aka.ms/o365endpoints) reference article.</span></span>
  
<span data-ttu-id="5dbe6-p112">已新增的控制項，您可以使用 FQDN 層級的 proxy 基礎結構內篩選限制或檢查目的地的網際網路或 Office 365 的部分或所有網路要求。隨著發行功能和 Office 365 方案仍有發展空間維護的 Fqdn 清單需要更完善的變更管理與追蹤的變更到已發佈的[Office 365 端點](https://aka.ms/o365endpoints)。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p112">For added controls, you can use FQDN level filtering within your proxy infrastructure to restrict or inspect some or all network requests destined for the internet or Office 365. Maintaining the list of FQDNs as features are released and the Office 365 offerings evolve requires more robust change management and tracking of changes to the published [Office 365 endpoints](https://aka.ms/o365endpoints).</span></span>
  
> [!CAUTION]
> <span data-ttu-id="5dbe6-158">Microsoft 建議您不要察覺依賴 IP 前置詞來管理輸出至 Office 365 的安全性。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-158">Microsoft recommends you don't rely solely on IP prefixes to manage outbound security to Office 365.</span></span>

|<span data-ttu-id="5dbe6-159">**選項**</span><span class="sxs-lookup"><span data-stu-id="5dbe6-159">**Option**</span></span>|<span data-ttu-id="5dbe6-160">**複雜性**</span><span class="sxs-lookup"><span data-stu-id="5dbe6-160">**Complexity**</span></span>|<span data-ttu-id="5dbe6-161">**變更控制項**</span><span class="sxs-lookup"><span data-stu-id="5dbe6-161">**Change Control**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="5dbe6-162">無限制</span><span class="sxs-lookup"><span data-stu-id="5dbe6-162">No restrictions</span></span>  <br/> |<span data-ttu-id="5dbe6-163">**低：** 客戶允許無限制的輸出存取給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-163">**Low:** Customer allows unrestricted outbound access to Microsoft.</span></span>  <br/> |<span data-ttu-id="5dbe6-164">無</span><span class="sxs-lookup"><span data-stu-id="5dbe6-164">None</span></span>  <br/> |
|<span data-ttu-id="5dbe6-165">連接埠限制</span><span class="sxs-lookup"><span data-stu-id="5dbe6-165">Port restrictions</span></span>  <br/> |<span data-ttu-id="5dbe6-166">**低：** 客戶限制輸出存取 Microsoft 所預期的連接埠。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-166">**Low:** Customer restricts outbound access to Microsoft by the expected ports.</span></span>  <br/> |<span data-ttu-id="5dbe6-167">非經常性。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-167">Infrequent.</span></span>  <br/> |
|<span data-ttu-id="5dbe6-168">FQDN 限制</span><span class="sxs-lookup"><span data-stu-id="5dbe6-168">FQDN restrictions</span></span>  <br/> |<span data-ttu-id="5dbe6-169">**高：** 客戶輸出存取限制的已發佈的 fqdn 均為基礎的 Office 365。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-169">**High:** Customer restricts outbound access to Office 365 based on the published FQDNs.</span></span>  <br/> |<span data-ttu-id="5dbe6-170">每月的變更。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-170">Monthly changes.</span></span>  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a><span data-ttu-id="5dbe6-171">輸入 microsoft 客戶</span><span class="sxs-lookup"><span data-stu-id="5dbe6-171">Inbound from Microsoft to Customer</span></span>
  
<span data-ttu-id="5dbe6-172">有數個選用的案例需要 Microsoft 啟動您的網路連線。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-172">There are several optional scenarios that require Microsoft to initiate connections to your network.</span></span>
  
- <span data-ttu-id="5dbe6-173">在 [密碼驗證登入期間 ADFS。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-173">ADFS during password validation for sign-in.</span></span>

- <span data-ttu-id="5dbe6-174">[Exchange Server 混合式部署](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-174">[Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).</span></span>

- <span data-ttu-id="5dbe6-175">將郵件從 Exchange Online 租用戶至內部部署主機。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-175">Mail from an Exchange Online tenant to an on-premises host.</span></span>

- <span data-ttu-id="5dbe6-176">SharePoint Online 郵件將傳送至內部部署主機的 [從 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-176">SharePoint Online Mail send from SharePoint Online to an on-premises host.</span></span>

- <span data-ttu-id="5dbe6-177">[ [SharePoint 同盟混合式搜尋](https://technet.microsoft.com/library/dn197174.aspx)]。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-177">[SharePoint federated hybrid search](https://technet.microsoft.com/library/dn197174.aspx).</span></span>

- <span data-ttu-id="5dbe6-178">[SharePoint 混合式 BCS](https://technet.microsoft.com/library/dn197239.aspx )。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-178">[SharePoint hybrid BCS](https://technet.microsoft.com/library/dn197239.aspx ).</span></span>

- <span data-ttu-id="5dbe6-179">[用於商業的混合式 Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx)和/或[Skype 商務同盟](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-179">[Skype for Business hybrid](https://technet.microsoft.com/en-us/library/jj205403.aspx) and/or [Skype for Business federation](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).</span></span>

- <span data-ttu-id="5dbe6-180">[Skype Business Cloud 連接器](https://technet.microsoft.com/library/mt605227.aspx )。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-180">[Skype for Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).</span></span>

<span data-ttu-id="5dbe6-p113">Microsoft 建議您接受這些連線透過網際網路電路而不是以降低複雜度您 ExpressRoute 電路。如果您的規範或效能需求支配哪些必須透過 ExpressRoute 電路接受這些輸入的連線，，建議使用防火牆或反向 proxy 的範圍公認的連線。您可以使用[Office 365 端點](https://aka.ms/o365endpoints)來了解右 Fqdn 和 IP 前置詞。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p113">Microsoft recommends that you accept these connections over your internet circuit instead of your ExpressRoute circuit to reduce complexity. If your compliance or performance needs dictate these inbound connections must be accepted over an ExpressRoute circuit, using a firewall or reverse proxy to scope the accepted connections is recommended. You can use the [Office 365 endpoints](https://aka.ms/o365endpoints) to figure out the right FQDNs and IP prefixes.</span></span>
  
### <a name="compliance"></a><span data-ttu-id="5dbe6-184">法規符合性</span><span class="sxs-lookup"><span data-stu-id="5dbe6-184">Compliance</span></span>

<span data-ttu-id="5dbe6-p114">我們不依賴您用於任何我們規範控制項的路由路徑。不論是否連線到 Office 365 服務透過 ExpressRoute 或網際網路電路，我們規範控制項將不會變更。您應該檢閱的不同規範和找出符合您的組織需求的最佳選擇 Office 365 的安全性憑證層級。</span><span class="sxs-lookup"><span data-stu-id="5dbe6-p114">We don't rely on the routing path you use for any of our compliance controls. Regardless of whether you connect to Office 365 services over an ExpressRoute or internet circuit, our compliance controls won't change. You should review the different compliance and security certification levels for Office 365 to figure out the best choice for meeting your organization's needs.</span></span>
  
<span data-ttu-id="5dbe6-188">以下是您可以使用回來的簡短連結：[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="5dbe6-188">Here's a short link you can use to come back: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="5dbe6-189">相關主題</span><span class="sxs-lookup"><span data-stu-id="5dbe6-189">Related Topics</span></span>

[<span data-ttu-id="5dbe6-190">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="5dbe6-190">Content delivery networks</span></span>](content-delivery-networks.md)
  
[<span data-ttu-id="5dbe6-191">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="5dbe6-191">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="5dbe6-192">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="5dbe6-192">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="5dbe6-193">Azure ExpressRoute for Office 365 訓練</span><span class="sxs-lookup"><span data-stu-id="5dbe6-193">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer)
