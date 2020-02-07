---
title: 調整 Exchange Online 效能
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 本文包含一般的祕訣和告訴您如何增進效能的 Exchange Online 的其他資源的連結。
ms.openlocfilehash: 4ef0276345a3d7f1c9aeba016824f9cb06c475cb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841080"
---
# <a name="tune-exchange-online-performance"></a>調整 Exchange Online 效能

本文包含一般的祕訣和告訴您如何增進效能的 Exchange Online 中，特別是在移轉前方的其他資源的連結。 本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)專案的一部分。
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>若要改善 Exchange Online 效能的考量事項

若要改善移轉速度及降低組織的頻寬限制的 Exchange Online，請考慮下列各項：
  
- **減少信箱大小。** 較小的信箱大小提升移轉速度。 
    
- **使用信箱移動與 Exchange 混合式部署的功能。** Exchange 混合部署，離線郵件 （中的表單。OST 檔案） 不需要重新下載時移轉至 Exchange Online。 這會大幅降低您下載的頻寬需求。 
    
- **排程信箱移動到發生低的網際網路流量和低的內部部署 Exchange 使用的期間。** 在排程移動時, 移轉要求提交至信箱複寫 proxy，並可能不會立即生效。 
    
- **使用 Outlook 網頁精簡的快顯。** 精簡的快顯較小的大小，提供 Microsoft Edge 或 Internet Explorer 中某些電子郵件訊息所呈現的伺服器上的某些元件較少需要大量記憶體的版本。 如需詳細資訊，請參閱[讀取郵件時，使用以減少記憶體使用精簡快顯](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。


## <a name="general-advice"></a>一般建議

- 請確定 outlook.office.com DNS 查閱進入您位置的邏輯的項目位置，MS 資料中心。

- 研究信箱快取，然後選擇適當的選項 （回覆。 快取週期、 共用的信箱快取、 et cetera）。

- 您無法傳送透過 VPN 連線 （中央機房） 之前的 Outlook 資料應放在網際網路上的保留。

- 請確定您的信箱資料遵守資料夾和項目、 金額上的限制。
    
如需 Exchange 移轉效能的詳細資訊，請參閱[Office 365 移轉效能和最佳作法](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。
  

