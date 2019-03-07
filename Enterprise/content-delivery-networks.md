---
title: 內容傳遞網路
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/5/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: 使用此資訊來瞭解內容傳遞網路 (Cdn) 與 Office 365 如何使用它們。 Cdn 協助保護使用者的 Office 365 快速且可靠。 使用 Cdn，雲端服務，例如 Office 365 快速下載圖示] 等的一般內容至使用者的瀏覽器當他們使用透過 web 用戶端的服務。
ms.openlocfilehash: c38b4c1fae2a40ff702c4d2222ed534e11fa2fc3
ms.sourcegitcommit: 19f0deee26b6cf2eef316c742054572bb9d98b84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "30458333"
---
# <a name="content-delivery-networks"></a>內容傳遞網路

使用此資訊來瞭解內容傳遞網路 (Cdn) 與 Office 365 如何使用它們。 Cdn 協助保護使用者的 Office 365 快速且可靠。 使用 Cdn，雲端服務，例如 Office 365 快速下載圖示] 等的一般內容至使用者的瀏覽器當他們使用透過 web 用戶端的服務。
  
 **Head 回到**[網路規劃和效能調整的 Office 365](https://aka.ms/tune)。
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>如何應該設定我的網路以便 Cdn 運作起來最順暢與 Office 365？

如果您計劃[對 Office 365 的網路連線](network-connectivity.md)，很有幫助 Cdn 的運作方式。 務必了解您不能使用 IP 位址篩選 Cdn 的連線。 我們會提供 Office 365，例如 Exchange Online 中的服務的 Ip 的最佳投入比清單。 深入了解[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)我們建議。
  
## <a name="how-do-cdns-make-services-work-faster"></a>Cdn 如何讓服務運作得更快？

超過再次下載常見之類的圖示，可能會耗費可更妥善地用於下載重要的個人內容，例如電子郵件或文件的網路頻寬。 因為 Office 365 使用架構，包括 Cdn、 圖示、 指令碼，以及其他一般內容可從伺服器更接近下載至用戶端電腦，更快速地進行下載。 這表示您個人的內容，安全地儲存在 Office 365 資料中心的快速存取。
  
## <a name="what-exactly-is-a-cdn"></a>什麼 CDN 究竟是？

大部分的企業雲端服務會使用 Cdn。 Office 365 等雲端服務有數百萬份客戶一次下載混合專屬的內容 （例如電子郵件） 和一般內容 （例如圖示）。 它會將所有人使用的圖示，例如影像最接近使用者的電腦，盡可能更有效率。 尚未，它不是實際的每個雲端服務，以建立儲存此一般內容，在每個都會] 區域中，或即使是在世界各地的每個主要網際網路 hub 讓這些 Cdn 的一些共用的 CDN 資料中心。
  
Cdn 可以是私人或公開。 擁有私人 Cdn 且 21vianet 運作的單一的公司，而只有該公司的應用程式與服務可以使用它。 租用使用狀況，多家公司的公司會執行公用 Cdn。 根據您所在地，可能是最有效率的 Office 365 為您下載泛型影像，從 Office 365 擁有 CDN 和執行、 公用 CDN 或兩者的組合。 無論使用何種類型的 CDN，以擷取資料的步驟都相同。
  
1. 您的用戶端要求的資料從 Office 365。

2. Office 365 直接對您的用戶端中傳回的資料，或是會引導您以 CDN 的用戶端。

3. 如果在 CDN 已快取資料，您的用戶端會直接從最接近的 CDN 位置下載資料至您在網際網路上的用戶端中。

4. 如果資料不在 CDN 快取，CDN 節點要求從 Office 365 的資料，然後快取的資料為一段時間之後您的用戶端下載資料。

Cdn 取出的檔案和影像從最接近的 Office 365 資料中心，並接著，您的用戶端的檔案和影像會從提取最接近的 CDN。 當使用者正在存取雲端服務，例如閱讀 Outlook Web App 中的電子郵件使用者的瀏覽器會嘗試從 Office 365 資料中心中擷取的檔案和影像。 而不是花時間與頻寬傳遞檔案，Office 365 會在瀏覽器重新導向至 CDN。 CDN 找出最接近的資料中心到使用者的瀏覽器，並使用重新導向，從該處下載一般的影像。 使用此 CDN 重新導向快速，且它會儲存使用者大量下載時間。
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>是否有利用 Cdn 的所有 Fqdn 的清單？

Fqdn，以及它們如何運用一段時間的 Cdn 變更的清單，請參閱我們已發佈的[Office 365 端點] 頁面上](https://go.microsoft.com/fwlink/p/?LinkID=293744)以取得最新利用 Cdn 的最新 Fqdn。
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>是否有 Office 365 使用的所有 Cdn 的清單？

使用 Office 365 Cdn 永遠都會受到變更，並在許多情況下，有多個 CDN 合作夥伴設定事件中其中一個已無法使用。 主要是使用中的 Cdn:

+ [Office 365 （特別是適用於 SharePoint Online 內容）](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

這些 CDN 解決方案有全球提升到全球多個角落的服務] 的範圍。 儲存於該處的內容包含一般 Office 365 指令碼、 檔案和影像。 例如，當您登入至 portal.office.com，影像會提取從最接近 CDN 以加快頁面載入時間。 其他範例包括 Office 365 專業增強版上以加速下載最新版的 Office 所花費的時間量 CDN 儲存安裝位元。

另外還有一些 Cdn 例如視訊檔案儲存為 Office 365 影片的專屬內容。 一旦您上傳影片，檔案會加密，，然後儲存在與 Azure 媒體服務及其加密格式。 當 Office 365 的視訊播放程式會擷取影片它是第一次快取至最接近的 CDN 之前正在下載以加速下載視訊所花費的時間量。

如需如何使用 Office 365 CDN 的詳細資訊，請參閱 <<c0>使用 SharePoint Online 的 Office 365 內容傳遞網路。

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>可以在我的區域網路使用我自己 CDN 及快取的內容？

我們不斷正在尋找新的方法來支援我們的客戶的需求，目前瀏覽使用快取 proxy 解決方案和其他在內部部署 CDN 解決方案。
  
## <a name="is-my-data-safe"></a>為我的資料安全嗎？

我們小心謹慎以確保我們保護執行您的業務資料。 客戶特定資料儲存在 Cdn 傳輸中和 rest、 加密，並受保護的資料不會儲存在 CDN 相同的檔案層級權限。

CDN 提供者可能會有不同於所述的 Office 365 信任中心的承諾的隱私權和法規遵循標準。 透過 CDN 服務快取的資料可能不符合到 Microsoft 資料處理合約 (DPT)，且可能會在 Office 365 信任中心合規性界限之外。

深入資訊的隱私權和資料保護 Office 365 CDN 提供者的詳細資訊，請造訪下列各項：  

+ 深入了解在[Office 365 信任中心](https://go.microsoft.com/fwlink/p/?LinkId=397383)的 Office 365 的隱私權和資料保護
+ 深入了解 Azure 的隱私權和資料保護在[Azure 的 [信任中心](https://azure.microsoft.com/en-us/overview/trusted-cloud/)
+ 深入了解 Akamai 的隱私權和資料保護在[Akamai 隱私權信任中心](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>如何保護我的網路，具有所有這些 3rd 廠商服務？

利用廣泛的協力廠商服務可讓 Office 365 擴充和符合可用性需求，以及使用 Office 365 時強化使用者體驗。 Office 365 採用 3rd 廠商服務包含兩個憑證撤銷清單;例如 crl.microsoft.com 或 sa.symcb.com 和 Cdn;例如 r3.res.outlook.com。 每個 CDN FQDN Office 365 使用 Office 365 自訂 FQDN，如果您正在傳送到 Office 365 要求的 FQDN 您可以確保我們控制 FQDN 和基礎內容在該位置。
  
客戶，還是要隔離目的地要求目的地為 3rd 廠商，從 Microsoft 或 Office 365 資料中心的要求我們已在[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)上寫設定下列項目的指引。
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>我使用 Azure ExpressRoute for Office 365，不會變更事項嗎？

[Azure ExpressRoute for Office 365](azure-expressroute.md)提供從公用的網際網路專用的連線隔離的 Office 365 基礎結構。 這表示用戶端仍將需要透過非 ExpressRoute 連線以連線到 Cdn 和其他 Microsoft 基礎結構，不明確包含清單中的 ExpressRoute 所支援的服務連線。 如需如何路由傳送特定的流量，例如要求目的地 Cdn 的詳細資訊，請參閱[管理 Office 365 網路流量](routing-with-expressroute.md)。
  
您可以使用下列短連結返回這裡：[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>另請參閱

[Office 365 端點常見問題集](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) (機器翻譯)
