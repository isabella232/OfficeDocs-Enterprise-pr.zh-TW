---
title: 將內容限制在地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何將多地理位置環境中的 SharePoint 網站限制在特定的地理位置。
ms.openlocfilehash: 59301a591e5465bdcda4aa84a18880961c0b615b
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933963"
---
# <a name="restrict-content-to-a-geo-location"></a>將內容限制在地理位置

在某些情況下，您可以選擇強制將網站及其檔案內容保留在建立網站的地理位置，方法是防止網站移動或防止在另一個地理位置快取網站的檔案內容。

您使用 [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet 搭配 **RestrictedToGeo** 參數來進行。 此參數預設值為 NULL，但您可以將它變更為下列其中一項：

|Restriction|描述|
|:----------|:----------|
|NoRestriction|可將網站移至另一個地理位置。|
|BlockMoveOnly|無法將網站移到另一個地理位置，但可以在其他地理位置快取網站內容。|
|BlockFull|無法將網站移到另一個地理位置，也不可以在其他地理位置快取完整檔案內容。 仍可以在其他地理位置快取檔案的標題 (取自內容)、檔案名稱和檔案的其他內容。<br>在設定為 BlockFull 之前儲存在網站中的內容可能會繼續在其他地理位置快取。|

使用下列語法：

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

例如：

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
