---
title: Office 365 IdFix 交易記錄檔
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 提供範例，並描述的命名慣例和預設記錄層級的 Office 365 IdFix 交易記錄檔。
ms.openlocfilehash: 0c6f2dd64cb406681c0a98099b2a42887ee79c25
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067259"
---
# <a name="office-365-idfix-transaction-log"></a>Office 365 IdFix 交易記錄檔

提供範例，並描述的命名慣例和預設記錄層級的 Office 365 IdFix 交易記錄檔。
  
## <a name="idfix-transaction-log-location"></a>IdFix 交易記錄檔的位置

Office 365 IdFix 工具在每次您按一下 [**套用**在 IdFix 中，將變更套用至 Active Directory 樹系時，都會建立新的交易記錄檔。 交易記錄檔會儲存在您安裝 IdFix 的相同資料夾中。 根據預設，這個資料夾是 C:\Deployment Tools\IDFix。 交易記錄檔名稱使用日期和時間戳記格式，例如 Verbose 6-1-2018年 6-17-22 PM 指示在 2018 年 6 月 1 日下午 6:17:22 產生的檔案。 Verbose 指出的記錄等級。 
  
## <a name="idfix-transaction-log-logging-level"></a>IdFix 交易記錄檔記錄層級

Verbose 在交易記錄檔名稱的字會指出記錄檔中的層的級。 Verbose 表示最高資訊量會擷取在記錄檔。 這是預設記錄等級。 在這個階段中，您無法變更的記錄等級。
  
## <a name="idfix-transaction-log-format"></a>IdFix 交易記錄格式

IdFix 會將每個 [ **UPDATE** ] 動作的結果寫入至交易記錄檔在下列範例所示：
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```