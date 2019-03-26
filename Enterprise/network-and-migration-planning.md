---
title: 網路和移轉規劃 Office 365
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
description: 包含資訊的網路規劃與測試、 連結和移轉到 Office 365。
ms.openlocfilehash: 02576933a1be615e65b695a7dd72c19eed311c91
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574037"
---
# <a name="network-and-migration-planning-for-office-365"></a>網路和移轉規劃 Office 365

本文章包含有關網路規劃和測試資訊的連結和移轉到 Office 365。
  
在第一次部署或移轉至 Office 365 之前，您可以使用這些主題的資訊來評估您需要的頻寬，然後測試並確認您有足夠頻寬可部署或移轉至 Office 365。

||
|:-----|
| 本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。|

|||
|:-----|:-----|
|![請參閱 Microsoft Cloud Networking for Enterprise Architects 海報](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|如需 Office 365 和其他 Microsoft 雲端平台及服務最佳化您的網路的步驟，請參閱 < <b0>Microsoft Cloud Networking for Enterprise Architects</b0>海報。 |
   
## <a name="estimate-network-bandwidth-requirements"></a>預估網路頻寬需求
<a name="EstimateBandwidthRequirements"> </a>

使用 Office 365 可能會增加您的組織網際網路電路的使用率。 請務必判斷目前可用的頻寬量是否足以同時至少 20%完整部署 Office 365 之後處理預估的增加容量，以處理最忙碌的天數。
  
若要估計頻寬，請使用下列步驟：
  
1. 評估會使用每個網際網路輸出的用戶端數目。 讓我們處理最多的連線設定為可能的多 tb 網路。 
    
2. 判斷哪些 Office 365 服務和功能可供用戶端使用。 您可能需要一組不同的服務或使用設定檔的人。
    
3. 測量網路使用試驗群組的用戶端。 確認試驗用戶端都代表一個不同的組織，以及不同的地理位置中的人員設定檔。 您可以跨-檢查您對我們舊計算器的結果[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[商務用 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551)或我們執行自己的網路的[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。 
    
4. 使用的度量單位從試驗群組推斷整個組織的需求和重新測試來驗證您的網路進行任何變更之前的數量的估計值。
    
## <a name="test-your-existing-network"></a>測試您現有的網路
<a name="calculators"> </a>

 **網路工具。** 測試及驗證您的網際網路頻寬，以判斷下載、 上載及延遲的條件約束。 這些工具可協助您決定您的網路進行移轉，以及完整部署之後的功能。 
  
- [Microsoft 郵件分析器](https://technet.microsoft.com/library/jj649776.aspx)： 郵件分析器是有效的工具，如網路問題的疑難排解。 郵件分析器擷取、 會顯示，並分析通訊協定為基礎的郵件流量和系統訊息。 郵件分析器也可讓您匯入、 彙總，並分析記錄檔和追蹤檔案中的資料。
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 環境中測試連線。
    
- 使用[Microsoft 的支援及修復小幫手的 Office 365](https://diagnostics.office.com/#/Download?env=SOC)來修正 Outlook 與 Office 365 的問題。 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>網路規劃和改善的 Office 365 移轉效能的最佳做法
<a name="BestPractices"> </a>

深入探討稍微改善您的 Office 365 使用經驗的詳細資訊的這些最佳作法。
  
1. 要開始立即幫助您的使用者？ 使用 Office 365，包括 SharePoint Online、 Exchange Online 和 Lync Online 中，當您的網路只要不合作的秘訣，請參閱[使用慢速網路上的 Office 365 的最佳作法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。 本文會連結至 TechNet，Support.office.com 上的內容的負載最佳化您的 Office 365 使用經驗，並包含簡單的方法來自訂您的網頁以及如何設定 Internet Explorer 設定為最佳的 Office 365 經驗的詳細資訊。 
    
2. 閱讀[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)來了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則。 本文可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。 
    
3. 透過謹慎地管理 Windows 更新的排程來改善郵件移轉效能。 您可以更新批次中的用戶端電腦，並確定所有用戶端電腦會更新之前先移轉到 Office 365 來調整的網路頻寬使用。 如需詳細資訊，請參閱[手動更新及設定桌面的 Office 365 的最新的更新](https://support.microsoft.com/gp/office-2013-365-update)。
    
4. 當已被視為受信任的網際網路服務，並允許略過大部分的傳統篩選和掃描，有些組織置於不受信任的網際網路服務的網路流量可獲得最佳執行 office 365 的網路流量。 這通常包括移除輸出 proxy 使用者驗證及封包檢查，例如處理，以及確保本機通往網際網路頻寬容量足以處理增加與適當的網路位址轉譯 (NAT)網路要求。 如需設定您的網路以處理 Office 365 為您的網路上之信任的網際網路服務的其他指引，請參閱[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。
    
1. 請確定[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。 移至 Office 365 的其他流量會產生輸出 proxy 連線的增加以及增加的安全流量透過 TLS/SSL。
    
2. 如果您的輸出 proxy 需要使用者驗證您可能會遇到慢速連線或遺失的功能。 略過的 Office 365 網域驗證需求，可以降低此額外負荷。
    
3. 如果您有大量的共用行事曆及信箱，您可能會看到從 Outlook 連線至 Exchange 數目增加。 比方說，Outlook 用戶端可能開啟使用中每個共用行事曆達兩個額外的連線。 在此情況下，確定 [輸出 proxy 可以處理的連線，或略過的 proxy 連線至 outlook 的 Office 365]。
    
4. 決定公用 IP 位址支援的裝置數目上限，以及如何負載平衡跨多個 IP 位址。 如需詳細資訊，請參閱[使用 Office 365 的 NAT 支援](nat-support-with-office-365.md)。
    
5. 如果您在您網路上檢查從電腦的輸出連線，略過此篩選至 Office 365 網域會改善連線能力與效能。 此外，略過輸出檢查通常會移除單一的網際網路輸出的需求，並啟用的目的地是 Office 365 的網路要求的本機網際網路輸出。
    
6. 有些客戶尋找內部網路設定可能會影響效能。 設定最大傳輸單位 (MTU) 大小，例如網路自動交涉或自動偵測和子最佳路由傳送至網際網路是常見的位置可尋找。
    
## <a name="network-planning-reference-for-office-365"></a>Office 365 的網路規劃參考
<a name="NetReference"> </a>

這些主題包含詳細的 Office 365 網路參考資訊。
  
- [管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [用戶端連線](client-connectivity.md)
    
- [內容傳遞網路](content-delivery-networks.md)
    
- [Office 365 的外部網域名稱系統記錄](external-domain-name-system-records.md)
    
- [Office 365 服務中的 IPv6 支援](ipv6-support.md)
    
- [Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)
    
- [Office 365 影片網路常見問題集 (FAQ)](office-365-video-networking-faq.md)
    
- [網路裝置的連線至 Office 365 服務計劃](plan-for-network-devices.md)
    
- [Office 365 服務的部署建議](deployment-advisors-for-office-365.md)
    

