---
title: 將 SharePoint 網站內容限制在地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何將多地理位置環境中的 SharePoint 網站限制在特定的地理位置。
ms.openlocfilehash: b8716eb0ad2d9292a0d52638f827dcc7665d027a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845014"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>將 SharePoint 網站內容限制在地理位置

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
