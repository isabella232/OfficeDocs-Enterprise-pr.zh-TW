---
title: 調整 Exchange Online 效能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 本文包含一般的秘訣與告訴您如何增進效能的 Exchange Online 的其他資源的連結。
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540295"
---
# <a name="tune-exchange-online-performance"></a>調整 Exchange Online 效能

本文包含一般的秘訣與告訴您如何增進效能的 Exchange Online 的其他資源的連結。本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)專案的一部分。
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>若要提升 Exchange Online 效能考量事項

若要提升移轉速度及降低組織的頻寬限制的 Exchange Online，請考慮下列各項：
  
- **縮小信箱大小。** 較小的信箱能提升移轉速度。 
    
- **在 Exchange 混合部署中使用信箱移動功能。** 在 Exchange 混合部署中，離線郵件 (.OST 檔案形式) 不需要在移轉至 Exchange Online 時重新下載。如此能大幅降低下載頻寬需求。 
    
- **將信箱移動時間排程在網際網路流量較低且內部部署 Exchange 使用量較低的期間來進行。** 排程移動時，會提交移轉要求給信箱複寫 Proxy 且可能不會立即發生。 
    
- **Outlook web 上使用精簡 popouts。** 精簡 popouts 提供較小型、 較少需要大量記憶體版本的 Microsoft Edge 或 Internet Explorer 中特定電子郵件訊息所呈現某些元件的伺服器上。如需詳細資訊，請參閱[使用精簡 popouts 減少記憶體使用閱讀郵件時](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。
    
如需 Exchange 移轉效能的詳細資訊，請參閱[Office 365 遷移效能和最佳作法](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。
  

