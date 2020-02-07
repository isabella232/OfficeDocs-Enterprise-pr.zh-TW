---
title: Office 365 Yammer 企業存取控制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 摘要： 簡短摘要有關 Yammer 企業存取控制在實際執行環境中。
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841790"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer 企業存取控制 

對 Yammer 實際執行環境的實體和邏輯存取只有一小群人 （基礎結構和作業）。 就像其他 Office 365 工程人員 Yammer 工程師會有零常設存取客戶資料。 類似於 Lockbox 核准型剛時間存取控制系統使用有限數量的核准者必須要求存取權。 核准者確認要求 （例如，它們可驗證要求是否合法根據需要、 業務案例、 時間、 等），然後核准或拒絕要求。 如果核准要求，JIT 存取會授與定義及有限的時間。 超過存取時間後，access 會自動到期。

就像其他 Office 365 服務，所有存取 Yammer 實際執行環境都使用多重要素驗證。 所有的存取權和命令歷程記錄是歸因於一位使用者，登入和定期檢閱 Yammer 安全性小組。

如需有關 Yammer 系統管理與管理的詳細資訊，請參閱[Yammer 系統管理說明](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US)。