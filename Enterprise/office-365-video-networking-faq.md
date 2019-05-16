---
title: 網路常見問題集的 office 365 影片
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 影片存放庫與資料流的服務，讓儲存及資料流組織內的影片簡單。 有很棒的資訊有關 Office 365 影片;此網路的常見問題集被設計來回答周圍頻寬規劃、 加密，以及服務如何運用內容傳遞網路 (Cdn) 最常見的問題。
ms.openlocfilehash: 93f55e0c1e4d065e02a9cc41e5aaaab89b459a0d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069469"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>網路常見問題集的 office 365 影片

Office 365 影片存放庫與資料流的服務，讓儲存及資料流組織內的影片簡單。 有很棒的[Office 365 影片的相關資訊](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50);此網路的常見問題集被設計來回答周圍頻寬規劃、 加密，以及服務如何運用[內容傳遞網路](content-delivery-networks.md)(Cdn) 最常見的問題。
  
如果您不已有充分了解上傳程序的影片時，會發生什麼事，或播放，看看這段影片我們放在一起[上, 傳至 Office 365 影片的視訊檔案會發生什麼事](https://www.youtube.com/watch?v=HXSZ0jYBKlM)。
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Office 365 影片頻寬需求是甚麼？

有許多[支援的視訊格式](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)可上傳至 Office 365。 每個視訊檔案然後編碼為標準格式與數個不同的視訊品質播放。 Office 365 影片中會使用調適型選取最佳的視訊播放品質的可用網路頻寬和大小的視訊播放程式為基礎的資料流的位元速率。 若要這麼做，請在播放程式最初要求最低播放品質。 服務便可開始在影片播放程式來傳送 2 秒視訊的區段。 播放程式就可以要求較高或較低播放品質根據每一條線段會傳遞速度。
  
調適型的位元速率資料流這麼做是所有在幕後時視訊播放中斷或緩衝處理的最小。 視訊播放時，視訊播放程式可讓手動覆寫自動播放品質]，以選取特定的視訊播放品質檢視器]。
  
以下是每個播放視訊品質的網路需求概述快速資料表。 播放視訊時需要的人的最低頻寬為 802 Kbps。
  
|||
|:-----|:-----|
|**播放品質** <br/> |**網路速度** <br/> |
|288 p  <br/> |802 kbps  <br/> |
|360 p  <br/> |1.2 Mbps  <br/> |
|576 p  <br/> |2.5 Mbps  <br/> |
|720 p  <br/> |3.8 Mbps  <br/> |

([回到頁首](office-365-video-networking-faq.md))
  
## <a name="how-do-content-delivery-networks-cdns-help-video-playback"></a>內容傳遞網路 (Cdn) 如何協助視訊播放？

如果從相同的組織內的相同的地理位置的數名人員資料流相同的影片，Cdn 就會儲存一份這些影片中的位置接近該地理區域。 與視訊儲存，或快取的最接近的位置，每位人員會串流傳送給他們而不是位置進一步最接近的位置的視訊離開。 Office 365 影片會使用 Azure 媒體服務來管理項目快取中的 Azure Cdn，以及如何長時間。 Azure 媒體服務可以使用任何[Azure CDN 位置](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)來快取視訊片段及幾天的資訊清單。 如果您組織中的人員會繼續觀賞快取的視訊留在快取中。 如果數天，影片的影片最後也將任何一個存取放置捨棄從快取。 下次有人嘗試觀看影片它會再次重申快取的最接近的 CDN 位置。
  
每一位使用者嘗試觀看影片內容時是鄰近的 CDN 優點從視訊正在接近，並在大多數情況下小於躍點，立即在快取。 這樣可以改善視訊播放速度;不過，它不會變更來播放影片的網路需求。
  
> [!NOTE]
> 有某些情況下，例如正在到達，已達三天前，移除影片可能其中我們容量限制。
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>可以快取到本機的速度播放影片嗎？

是。 Office 365 不會使您無法將影片或其他 Office 365 內容移入進行快速存取您的區域網路使用本機 CDN 或快取的 proxy。 有幾種方式可以實作您網路上的本機快取解決方案，最常用的方法是使用快取本機內容的 proxy 解決方案。 一旦視訊片段和資訊清單的 proxy 或私人 CDN 已快取，未來要求透過 proxy 或私人 CDN 路由傳送這些檔案是提取從本機快取，並不取自網際網路位置。 類似解決方案的規劃期間，請考慮網路頻寬、 容量及視訊播放並行數目。
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>如何影片加密和保護？

Office 365 影片知道會保護您的資料，安全無虞且私用的重要程度。 [Microsoft 信任中心](https://products.office.com/business/office-365-trust-center-welcome)說明我們致力於內容的安全性與隱私權。 播放視訊時，速度是很重要的良好的體驗。不過，我們不危害安全性或隱私權相信速度。 以下是我們如何配合速度、 安全性及隱私權。
  
當您或貴組織中的人員將上傳新的視訊時，視訊是轉碼，使用 AES 128 加密，加密並儲存在 Azure 媒體服務。 這表示在傳輸及靜態加密影片。
  
當您的組織中的人員嘗試觀看之新視訊時，他們會遵循下列步驟：
  
1. 要求 SharePoint Online 是否他們有權檢視視訊。

2. SharePoint Online 會使用檔案的權限來決定是否人員可以觀看影片。

3. 如果他們正在允許，SharePoint Online 擷取權杖從 Azure 將授與視訊播放程式。

4. 視訊播放程式接著會使用語彙基元，從 Azure 要求解密金鑰。

5. 在手解密金鑰，視訊播放程式是能夠傳送視訊資料流。

![O365 視訊播放](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>Office 365 影片播放需求是甚麼？

Office 365 影片支援的作業系統和網頁瀏覽器是[Office 365 系統需求](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)中的 SharePoint Online 需求相同。 視哪些作業系統和網頁瀏覽器設定，您必須將會決定在影片播放程式的特定需求。 以下是在[影片播放需求](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)的詳細資訊。
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>無法取得 Office 365 影片運作，其中應該開始？

疑難排解 Office 365 影片的連線，包括疑難排解您的網路、 您 ISP(s)，與您的 Office 365 的設定。 若要啟動的第一個位置是在服務健康狀況儀表板。 這會告知您的 Office 365 影片有問題，或不。 如果一切就很好，以下是一些額外的資源，可以協助您。
  
- 請確定您可以連線至[Office 365 影片所需的網路端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)。

- 檢查網路連線使用我們的[Office 365 網路疑難排解指南](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。

- 請參閱我們的[使用在慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)。

- [尋找有關 Office 365 影片設定的說明](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)。

([回到頁首](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365 影片資源

以下是一些其他資源以協助您成功部署及使用 Office 365 影片：
  
[尋找有關 Office 365 影片設定的說明](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)
  
[符合 Office 365 影片](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[建立及管理 Office 365 影片中的通道](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[管理您的 Office 365 影片入口網站](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[在 Office 365 影片中運作的視訊格式](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([回到頁首](office-365-video-networking-faq.md))
  
您可以使用下列短連結返回這裡：[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
