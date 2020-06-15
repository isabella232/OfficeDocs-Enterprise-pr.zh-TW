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
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出 IdFix 工具排除並支援的屬性。
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711573"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 已排除和支援的物件和屬性

*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*

IdFix 維護兩組規則;多承租人和專用/ITAR。 此時，這兩個規則集會從其搜尋中排除相同的物件、屬性和屬性值。 在未來的版本中可能會有所變更。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix 所使用的多租使用者和專用錯誤排除
本節列出 IdFix 從其目錄搜尋中排除的物件、屬性及值。 星號（ \* ）是可以取代其他字元的萬用字元。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>在 IdFix 搜尋期間排除的物件、屬性及值

|**排除**|**範例**|
|:-----|:-----|
|Admini\* |系統管理員 |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|客人\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-連結 |
|iusr_\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName 包含 "\0ACNF："|"\0ACNF： *GUID* " |
|物件包含 IsCriticalSystemObject 屬性 |請參閱[屬性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>由 IdFix 檢查的多承租人和專用物件及屬性
[使用 IdFix 工具，準備目錄365屬性](prepare-directory-attributes-for-synch-with-idfix.md)中的「目錄物件及屬性準備」一節中的「目錄物件及屬性準備」一節中所述的 IdFix 所檢查的錯誤屬性。
  

