---
title: Office 365 監視和稽核的存取控制
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
description: 摘要： 各種監視和稽核存取控制 Office 365 內提供摘要。
ms.openlocfilehash: 300d5efa2b448e8e5219eb88f3d736eeba66f2d6
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41842602"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a>監視和稽核的 Office 365 中的存取控制

Microsoft 會執行廣泛的監視與稽核所有委派、 權限，與 Office 365 內發生的作業。 Office 365 的存取控制為基礎的最低權限和採用資料的存取控制和稽核原則自動化程序：

- 所有允許的存取是唯一的使用者可進行追蹤。 系統管理員是負責其處理的客戶內容。
- 存取控制項要求、 核准及管理作業記錄檔擷取進行分析的安全性和惡意的事件。
- 存取層級中檢閱接近即時根據的安全性群組成員資格，以確保只有使用者已獲授權業務理由，且符合資格需求有系統的存取。
- Office 365、 其存取控制和支援服務，包括 Azure Active Directory 和實體資料中心，定期稽核由獨立第三方的[ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001)、 [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018)、 [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC)、 [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)及其他[標準](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)的合規性。
- Office 365 工程師必須採取每年的安全性訓練、 檢閱提高權限的存取最佳的程序，並確認 Microsoft 的安全性和隱私權原則，以維護服務的權利。

偵測到可疑的活動時，例如在短時間內多個失敗的登入的自動化通知觸發程序。 Office 365 安全性回應小組使用機器學習和大的資料分析，請先檢閱及分析活動、 尋找不規則存取模式，以及主動回應異常和非法活動。 Microsoft 也會採用滲透測試人員專用的小組，並凝聚中定期紅色小組及藍色小組練習，來尋找安全性和存取控制服務中的問題。 客戶可以使用稽核報告和管理活動 API 提供 Office 365 所驗證訪問控制系統的有效性。

如需詳細資訊，請參閱[Office 365 管理活動 API 參考資料](https://msdn.microsoft.com/library/office/mt227394.aspx)及[稽核與 Office 365 中的報告](office-365-auditing-and-reporting-overview.md)。
