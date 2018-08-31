---
title: Office 365 影片網路常見問題集
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2016
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
ms.assetid: 2bed67a1-4052-49ff-a4ce-b7e6530eb98e
description: Office 365 影片存放庫及資料流服務幫助儲存與組織內的視訊資料流簡單。有許多的 Office 365 影片; 更好的資訊此網路的常見問題集的設計目的回答周圍頻寬規劃、 加密，以及如何服務使用內容傳遞網路 (Cdn) 的最常見的問題。
ms.openlocfilehash: bea9838277b5752e4c9905162c0e8525e8aded04
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539999"
---
# <a name="office-365-video-networking-frequently-asked-questions"></a>Office 365 影片網路常見問題集

Office 365 影片存放庫及資料流服務幫助儲存與組織內的視訊資料流簡單。有許多的更好的[Office 365 影片的相關資訊](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)；此網路的常見問題集的設計目的回答周圍頻寬規劃、 加密，以及如何服務使用[內容傳遞網路 (Cdn)](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)的最常見的問題。
  
如果您已經不充分的認知瞭解什麼程序的影片上傳時有或播放、 已看一下這段影片我們放在一起，[影片檔案上載至 Office 365 視訊會發生什麼事](https://www.youtube.com/watch?v=HXSZ0jYBKlM)。
  
## <a name="what-are-the-office-365-video-bandwidth-requirements"></a>Office 365 視訊頻寬需求為何？

有許多[支援的視訊格式](https://support.office.com/article/dd1af01c-fd8e-4640-b17b-93ee02b9b817)可上傳至 Office 365。每個視訊檔案然後是使用數種不同的視訊品質播放編碼標準格式。Office 365 影片使用調適型選取根據可用的網路頻寬和影片播放程式大小的最佳播放視訊品質資料流的位元速率。若要這樣做，player 最初要求的最低的播放品質。服務然後開始以影片播放程式傳送 2 秒視訊線段。Player 然後可以要求根據每個區段會傳送速度較高或較低播放品質。
  
調適型的位元速率串流所有執行此動作在背景中視訊播放中斷或緩衝處理最少量與項目時。視訊播放期間影片播放程式可讓手動覆寫自動播放品質]，選取特定的視訊播放品質檢視器。
  
以下是概要說明每個視訊播放品質的網路需求的快速表格。若要播放影片所需的人的最小頻寬是 802 Kbps。
  
|||
|:-----|:-----|
|**播放品質** <br/> |**網路速度** <br/> |
|288 p  <br/> |802 kbps  <br/> |
|360 p  <br/> |1.2 Mbps  <br/> |
|576 p  <br/> |2.5 Mbps  <br/> |
|720 p  <br/> |3.8 Mbps  <br/> |

([回到頁首](office-365-video-networking-faq.md))
  
## <a name="how-do-cdns-help-video-playback"></a>Cdn 如何協助視訊播放？

如果數個人員從相同的組織內之相同的地理位置的資料流相同的影片、 Cdn 會在該地理區域更接近位置儲存這些影片的複本。視訊儲存，或快取的最接近的位置，每位人員串流離開傳送給他們，而不是位置進一步最接近之位置的影片。Office 365 影片使用 Azure Media Services 管理什麼快取在 Azure Cdn，以及如何長。Azure 媒體服務可以使用任何[Azure CDN 位置](https://azure.microsoft.com/documentation/articles/cdn-pop-locations/)以快取視訊片段 （英文） 及在幾天後的資訊清單。如果您組織中的人員會繼續觀賞快取它們將留在快取。如果數天、 視訊影片最後會將任何一個存取卸除放置從快取。下一個每當使用者嘗試觀賞影片它是一次快取的最接近的 CDN 位置。
  
嘗試觀賞影片，內容時的所有人快取在從正在接近、 視訊及在大多數情況下小於離開旋入附近 CDN 好處。這可改善視訊播放速度;不過，它不會變更要播放影片的網路需求。
  
> [!NOTE]
> 有某些情況下，例如要達到，其中影片可能會移除前三天已達到我們容量限制。
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="can-i-cache-the-videos-locally-for-faster-playback"></a>可以快取在本機上的速度較快的播放影片吗？

[是]。Office 365 將不會防止您將視訊或其他 Office 365 內容移入速度較快的存取的區域網路使用本機 CDN 或快取的 proxy。有數種方式可以實作您網路上的本機快取解決方案、 最常見的方法是使用快取本機內容的 proxy 解決方案。一旦 proxy 或私人 CDN 具有 「 快取的視訊片段 （英文） 和資訊清單、 未來要求路由傳送經 proxy 或私人 CDN 那些檔案的取出的本機快取中，不提取從網際網路的位置。考慮網路頻寬、 容量及視訊播放並行處理期間類似解決方案的規劃。
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="how-videos-are-encrypted-and-secured"></a>如何影片加密和安全？

Office 365 影片知道會保護您的資料安全無虞且私人的重要程度。[Office 365 信任中心](https://products.office.com/business/office-365-trust-center-cloud-computing-security)說明我們承諾的隱私性及內容的安全性。使用視訊播放速度很重要良好體驗;不過，我們不危害安全性或隱私權交換以交換速度。以下是我們如何配合速度、 安全性及隱私權。
  
當您或某人在組織中上傳新的視訊時、 視訊是轉碼，AES 128 加密使用加密並儲存在 Azure 媒體服務。這表示影片來加密傳送過程中與其餘部分。
  
當某人在組織中嘗試觀賞新影片時，他們會遵循下列步驟：
  
1. 要求 SharePoint Online 當使用者有權限以檢視視訊。

2. SharePoint Online 使用來決定是否人員可觀賞影片檔案的權限。

3. 如果他們正在允許，SharePoint Online 權杖從擷取 Azure 來授與影片播放程式。

4. 影片播放程式再使用權杖從 Azure 要求解密金鑰。

5. 與在手解密機碼、 影片播放程式能夠傳送視訊資料流。

![O365 視訊播放](media/9d3c6e76-151d-48a3-a30e-ba8dd07db0b7.png)
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="what-are-the-requirements-to-playback-office-365-video"></a>什麼是 Office 365 視訊播放的硬體需求？

Office 365 視訊支援的作業系統和網頁瀏覽器在[Office 365 系統需求](https://support.office.com/article/Office-365-system-requirements-719254c0-2671-4648-9c84-c6a3d4f3be45)的 SharePoint Online 的需求相同。根據哪些作業系統和網頁瀏覽器設定您已決定影片播放程式的特定需求。以下是在[視訊播放需求](https://support.office.com/article/ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)的詳細資訊。
  
([回到頁首](office-365-video-networking-faq.md))
  
## <a name="i-cant-get-office-365-video-to-work-where-should-i-start"></a>無法取得 Office 365 影片運作，其中應開始？

疑難排解 Office 365 影片的連線需要疑難排解您的網路、 您 ISP(s) 與您的 Office 365 的設定。若要啟動的第一個位置是服務健康狀況儀表板。這會告訴您的 Office 365 影片或沒有問題發生問題。如果每個項目外觀更好，以下是一些可協助您的其他資源。
  
- 請確定您可以連線到[Office 365 視訊所需的網路端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)。

- 檢查您使用我們的[疑難排解指南的 Office 365 網路](https://support.office.com/article/Office-365-performance-tuning-and-troubleshooting-Admin-and-IT-Pro-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)的網路連線。

- 請參閱我們[使用在慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/Best-practices-for-using-Office-365-on-a-slow-network-fd16c8d2-4799-4c39-8fd7-045f06640166)。

- 尋找[有關 Office 365 視訊設定的說明](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)。

([回到頁首](office-365-video-networking-faq.md))
  
## <a name="office-365-video-resources"></a>Office 365 影片資源

評等主題並留下註解意見如果我們接聽您的問題或您仍要尋找答案。以下是一些其他資源以協助您順利部署及使用 Office 365 影片：
  
[尋找 Office 365 影片組態相關的說明](https://support.office.com/article/Find-help-about-Office-365-Video-b435f99a-f47e-4ebd-a946-f5c965844f50)。
  
[符合 Office 365 影片](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)
  
[建立及管理 Office 365 視訊] 中的通道](https://support.office.com/article/Create-and-manage-a-channel-in-Office-365-Video-1fede4cc-13c0-435a-b585-e7fbf1c83bb2)
  
[管理 Office 365 影片入口網站](https://support.office.com/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da)
  
[在 Office 365 影片中運作的視訊格式](https://support.office.com/article/Video-formats-that-work-in-Office-365-Video-dd1af01c-fd8e-4640-b17b-93ee02b9b817)
  
([回到頁首](office-365-video-networking-faq.md))
  
以下是您可以使用回來的簡短連結：[https://aka.ms/video365networkfaq](https://aka.ms/video365networkfaq)
