---
title: Office 365 的網路和移轉規劃
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 包含資訊的網路規劃和測試、 連結以及移轉至 Office 365。
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223055"
---
# <a name="network-and-migration-planning-for-office-365"></a>Office 365 的網路和移轉規劃

本文包含網路規劃和測試的相關資訊的連結並移轉至 Office 365。
  
在首次部署或移轉至 Office 365 前，您可使用這些主題的資訊來預估您需要的頻寬，然後測試並確認您有足夠頻寬可部署或移轉至 Office 365。

||
|:-----|
| 本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。|

|||
|:-----|:-----|
|![請參閱 Microsoft 雲端網路的企業架構師海報 （英文）](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|如需如何最佳化您的網路的 Office 365 與其他 Microsoft cloud 平台及服務的步驟，請參閱[Microsoft 雲端網路的企業架構師](https://aka.ms/cloudarchnetworking)海報。 |
   
## <a name="estimate-network-bandwidth-requirements"></a>預估網路頻寬需求
<a name="EstimateBandwidthRequirements"> </a>

使用 Office 365 可能會增加您組織的網際網路電路使用率。請務必判斷目前可用的頻寬量是否足以同時又至少 20%完整部署 Office 365 一旦處理估計的增加產能，處理忙碌的天數。
  
若要估算頻寬，請使用下列步驟：
  
1. 評估將會使用每個網際網路輸出的用戶端數目。可讓我們處理的連線盡量的多個 tb 網路。 
    
2. 決定哪些 Office 365 服務和功能可供用戶端使用。您可能會有不同的服務或使用設定檔的人員的群組。
    
3. 測量網路使用的用戶端試驗群組。確定試驗用戶端的不同的組織如不同地理位置中的人員設定檔的人。您可以跨檢查您對我們舊計算器的結果[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[Skype 的商務](https://go.microsoft.com/fwlink/p/?LinkId=321551)或我們執行我們自己網路的[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。 
    
4. 使用的度量單位從試驗群組推斷結果整個組織的需求和重新測試來驗證估算之前對您的網路進行任何變更。
    
## <a name="test-your-existing-network"></a>測試您現有的網路
<a name="calculators"> </a>

 **網路工具。** 測試及驗證您的網際網路頻寬來決定下載 （英文）、 上傳，並延遲條件約束。這些工具可協助您決定您的網路進行移轉以及在完整部署之後的功能。 
  
- [Microsoft 訊息 Analyzer](https://technet.microsoft.com/library/jj649776.aspx)： 訊息 Analyzer 是有效的網路問題的疑難排解工具。郵件 Analyzer 擷取、 顯示、 和分析通訊協定式訊息流量和系統訊息。郵件 Analyzer 也可讓您匯入、 總計、 和分析記錄檔和追蹤檔案的資料。
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 環境中測試連線。
    
- 使用[Microsoft 支援與 Office 365 的助理復原](https://diagnostics.office.com/#/Download?env=SOC)修正 Outlook 與 Office 365 的問題。 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

深入探討一點這些提升您的 Office 365 功能的詳細資訊的最佳作法。
  
1. 想要立即協助使用者開始吗？請參閱使用 Office 365，包括 SharePoint Online、 Exchange Online 與 Lync Online，當您的網路只是不是合作秘訣[使用在慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。本文及最佳化您的 Office 365 功能的連結出載入的 TechNet 和 Support.office.com 內容包含如何輕鬆自訂您的網頁及如何設定您的 Internet Explorer 設定獲得最佳的 Office 365 體驗的方式的資訊。 
    
2. 請閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)了解連線原則可安全地管理 Office 365 流量和快速獲得最佳效能。本文可協助您了解可安全地最佳化 Office 365 網路連線的最新的指引。 
    
3. 改善郵件移轉效能謹慎管理 Windows 更新的排程。您可以更新用戶端電腦的批次並確保所有用戶端電腦進行更新之前移轉至 Office 365 管理網路頻寬的使用。如需詳細資訊，請參閱[手動更新及設定桌上型電腦的 Office 365 的最新的更新](https://support.microsoft.com/gp/office-2013-365-update)。
    
4. 已被視為信任的網際網路服務，並允許略過量傳統篩選和掃描有些組織放到不受信任的網際網路服務網路流量的最佳執行 office 365 網路流量。這通常包含移除輸出處理如 proxy 使用者驗證及封包檢查、 以及確保本機輸出至適當的網路位址轉譯 (NAT) 與足夠的頻寬容量來處理增加網際網路網路要求。請參閱[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)的設定來處理做為信任的網際網路服務網路上的 Office 365 網路的其他指導。
    
1. 請確定[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。移至 Office 365 的其他流量會產生的輸出 proxy 連線增加時的安全流量增加 over TLS/SSL。
    
2. 如果您輸出 proxy 需要使用者驗證您可能會遇到慢速連線或遺失的功能。略過的 Office 365 網域驗證要求可能會降低此額外負荷。
    
3. 如果您有大量的共用行事曆和信箱，可能會看見從 Outlook 至 Exchange 的連線數目增加。例如，Outlook 用戶端可能會針對每個使用中的共用行事曆，開啟最多兩個額外連線。在此情況下，請確定向外的 Proxy 可以處理連線，或針對 Outlook 對 Office 365 的連線來略過 Proxy。
    
4. 決定的公用 IP 位址支援的裝置數目上限，以及如何跨多個 IP 位址的負載平衡。如需詳細資訊，請參閱[Office 365 的 NAT 支援](nat-support-with-office-365.md)。
    
5. 如果您正在檢查從電腦的輸出連線網路上，略過篩選至 Office 365 網域將可改善連線和效能。此外，略過輸出檢查通常會移除單一的網際網路輸出需要與可讓目的地的 Office 365 網路要求的本機網際網路輸出。
    
6. 某些客戶會尋找內部網路設定可能會影響效能。最大傳輸單位 (MTU) 大小，例如設定網路自動交涉或自動偵測和子最佳路由到網際網路常見的位置可尋找。
    
## <a name="network-planning-reference-for-office-365"></a>Office 365 的網路規劃參考
<a name="NetReference"> </a>

這些主題包含詳細的 Office 365 網路參考資訊。
  
- [管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [用戶端連線](client-connectivity.md)
    
- [內容傳遞網路](content-delivery-networks.md)
    
- [Office 365 的外部網域名稱系統記錄](external-domain-name-system-records.md)
    
- [Office 365 服務中的 IPv6 支援](ipv6-support.md)
    
- [Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)
    
- [Microsoft 虛擬學院： Office 365 績效管理](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Office 365 影片網路常見問題集 (FAQ)](office-365-video-networking-faq.md)
    
- [連線到 Office 365 服務的網路裝置的計劃](plan-for-network-devices.md)
    
- [Office 365 服務的部署建議](deployment-advisors-for-office-365.md)
    

