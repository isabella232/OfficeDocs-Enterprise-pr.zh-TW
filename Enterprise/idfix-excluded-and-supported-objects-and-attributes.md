---
title: IdFix 已排除和支援的物件和屬性
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出已排除和支援 IdFix 工具的屬性。
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540078"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 已排除和支援的物件和屬性
IdFix 維護兩組規則；多租用戶和 專用的/ITAR。這兩個規則集目前會在其搜尋中排除相同的物件、屬性和屬性值。這可能會在未來的版本中變更。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix 所使用的多租用戶和 專用的 錯誤排除項目
本節列出物件、 屬性和 IdFix 應從其的目錄搜尋中排除的值。星號 (\*) 可以為其他任何字元取代為萬用字元。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>在 IdFix 搜尋期間排除的物件、屬性和值

|**排除**|**範例**|
|:-----|:-----|
|Admini\* |系統管理員 |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail。*GUID* |
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
|distinguishedName 包含"\0ACNF:"|"\0ACNF: *GUID* " |
|物件包含 IsCriticalSystemObject 屬性 |請參閱[isCriticalSystemObject 屬性](https://go.microsoft.com/fwlink/p/?LinkId=401169)。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix 所檢查的多租用戶和 專用的 物件和屬性
會檢查有錯誤 IdFix 所屬性"目錄物件和屬性準備 」 在[進行同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)] 區段中所述。
  

