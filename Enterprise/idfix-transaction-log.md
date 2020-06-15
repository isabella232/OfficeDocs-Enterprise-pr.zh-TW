---
title: Microsoft 365 IdFix 交易記錄檔
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 提供範例，並說明 Microsoft 365 IdFix 交易記錄檔的命名慣例和預設記錄層級。
ms.openlocfilehash: a2b887907dd1ad622a9d237cf7200aa6db8a2a8e
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711553"
---
# <a name="microsoft-365-idfix-transaction-log"></a>Microsoft 365 IdFix 交易記錄檔

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

提供範例，並說明 Microsoft 365 IdFix 交易記錄檔的命名慣例和預設記錄層級。
  
## <a name="idfix-transaction-log-location"></a>IdFix 交易記錄位置

當您在 IdFix 中按一下 [套用]**並將變更**套用至 Active Directory 樹系時，Microsoft 365 IdFix 工具會建立新的交易記錄檔。 交易記錄會儲存在您安裝 IdFix 所在的相同資料夾中。 根據預設，此資料夾為 C:\Deployment Tools\IDFix。 交易記錄檔名稱使用日期和時間戳記格式，例如，Verbose 6-1-2018 6-17-22 PM 表示在 6:17:22 2018 的晚上6月1日產生的檔案。 詳細指出記錄等級。 
  
## <a name="idfix-transaction-log-logging-level"></a>IdFix 交易記錄檔記錄層級

交易記錄檔名稱中的 [文字詳細資訊] 表示檔中的記錄層級。 詳細表示記錄中所捕獲的資訊數目上限。 這是預設的記錄等級。 此時，您無法變更記錄等級。
  
## <a name="idfix-transaction-log-format"></a>IdFix 事務歷史記錄格式

IdFix 會將每個**更新**動作的結果寫入交易記錄檔，如下列範例所示：
  
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