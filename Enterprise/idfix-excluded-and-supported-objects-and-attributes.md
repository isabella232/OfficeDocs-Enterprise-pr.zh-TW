---
title: IdFix 已排除和支援的物件和屬性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出已排除和 IdFix 工具所支援的屬性。
ms.openlocfilehash: bf88fea3592860a89d69717177593b6553318ee4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067269"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 已排除和支援的物件和屬性
有兩組 IdFix; 所維護的規則多租用戶和專用 /ITAR。 在這個階段中，兩個規則設定相同的物件、 屬性和屬性值從搜尋中排除其。 這可能會變更在未來版本。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>多重租用戶和專用的 IdFix 所使用的錯誤排除項目
此章節將列出物件、 屬性和 IdFix 排除其搜尋目錄的值。 星號 (\*) 可以針對其他字元取代為萬用字元。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>物件、 屬性和 IdFix 搜尋期間排除的值

|**排除項目**|**範例**|
|:-----|:-----|
|系統管理員\* |系統管理員 |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|Discoverysearchmailbox 為開頭\*  |Discoverysearchmailbox 為開頭  |
|FederatedEmail\* |FederatedEmail。 *GUID* |
|來賓\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms DS-KrbTgt 連結 |
|iusr_\* |iusr_ *machinename 資料* |
|iwam\*  |IWAM_ *machinename 資料* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName 包含 「 \0ACNF: 」|「 \0ACNF: *GUID* 」 |
|物件包含 IsCriticalSystemObject 屬性 |請參閱 <<c0>屬性 isCriticalSystemObject。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>多重租用戶和專用的物件和 IdFix 所檢查的屬性
在部分 」 目錄物件和屬性準備 」 中[進行同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)會描述 IdFix 所檢查有錯誤的屬性。
  

