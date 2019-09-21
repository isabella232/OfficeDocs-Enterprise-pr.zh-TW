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
description: 摘要： 各種監視和稽核存取控制 Office 365 內提供摘要。
ms.openlocfilehash: 00f0032afa85905ed5b1e0c4e016ea218207fc34
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067276"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a><span data-ttu-id="b8a13-103">監視和稽核的 Office 365 中的存取控制</span><span class="sxs-lookup"><span data-stu-id="b8a13-103">Monitoring and Auditing Access Controls in Office 365</span></span>

<span data-ttu-id="b8a13-104">Microsoft 會執行廣泛的監視與稽核所有委派、 權限，與 Office 365 內發生的作業。</span><span class="sxs-lookup"><span data-stu-id="b8a13-104">Microsoft performs extensive monitoring and auditing of all delegation, privileges, and operations that occur within Office 365.</span></span> <span data-ttu-id="b8a13-105">Office 365 的存取控制為基礎的最低權限和採用資料的存取控制和稽核原則自動化程序：</span><span class="sxs-lookup"><span data-stu-id="b8a13-105">Office 365 access control is an automated process built on the principle of least privilege and incorporate data access controls and audits:</span></span>

- <span data-ttu-id="b8a13-106">所有允許的存取是唯一的使用者可進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b8a13-106">All permitted access is traceable to a unique user.</span></span> <span data-ttu-id="b8a13-107">系統管理員是負責其處理的客戶內容。</span><span class="sxs-lookup"><span data-stu-id="b8a13-107">Administrators are accountable for their handling of customer content.</span></span>
- <span data-ttu-id="b8a13-108">存取控制項要求、 核准及管理作業記錄檔擷取進行分析的安全性和惡意的事件。</span><span class="sxs-lookup"><span data-stu-id="b8a13-108">Access control requests, approvals, and administrative operations logs are captured for analysis of security and malicious events.</span></span>
- <span data-ttu-id="b8a13-109">存取層級中檢閱接近即時根據的安全性群組成員資格，以確保只有使用者已獲授權業務理由，且符合資格需求有系統的存取。</span><span class="sxs-lookup"><span data-stu-id="b8a13-109">Access levels are reviewed in near real-time based on security group membership to ensure that only users who have authorized business justifications and meet the eligibility requirements have access to the systems.</span></span>
- <span data-ttu-id="b8a13-110">Office 365、 其存取控制和支援服務，包括 Azure Active Directory 和實體資料中心，定期[ISO/IEC 27001](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27001)、 [ISO/IEC 27018](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27018)、 [SOC](https://www.microsoft.com/en-us/TrustCenter/Compliance/SOC)、[規範的獨立第三方稽核FedRAMP](https://www.microsoft.com/en-us/TrustCenter/Compliance/FedRAMP)，與其他[標準](https://www.microsoft.com/en-us/TrustCenter/Compliance?service=Office#Icons)。</span><span class="sxs-lookup"><span data-stu-id="b8a13-110">Office 365, its access controls, and supporting services, including Azure Active Directory and physical datacenters, are regularly audited by independent third-parties for compliance with [ISO/IEC 27001](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/en-us/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/en-us/TrustCenter/Compliance/FedRAMP), and other [standards](https://www.microsoft.com/en-us/TrustCenter/Compliance?service=Office#Icons).</span></span>
- <span data-ttu-id="b8a13-111">Office 365 工程師必須採取每年的安全性訓練、 檢閱提高權限的存取最佳的程序，並確認 Microsoft 的安全性和隱私權原則，以維護服務的權利。</span><span class="sxs-lookup"><span data-stu-id="b8a13-111">Office 365 engineers must take yearly security training, review elevated access best procedures, and acknowledge Microsoft's security and privacy policies to maintain entitlements to the service.</span></span>

<span data-ttu-id="b8a13-112">偵測到可疑的活動時，例如在短時間內多個失敗的登入的自動化通知觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8a13-112">Automated alerts trigger when suspicious activity is detected, such as multiple failed logins within a short period.</span></span> <span data-ttu-id="b8a13-113">Office 365 安全性回應小組使用機器學習和大的資料分析，請先檢閱及分析活動、 尋找不規則存取模式，以及主動回應異常和非法活動。</span><span class="sxs-lookup"><span data-stu-id="b8a13-113">The Office 365 Security Response team uses machine learning and big data analysis to review and analyze activity, look for irregular access patterns, and proactively respond to anomalous and illicit activities.</span></span> <span data-ttu-id="b8a13-114">Microsoft 也會採用滲透測試人員專用的小組，並凝聚中定期紅色小組及藍色小組練習，來尋找安全性和存取控制服務中的問題。</span><span class="sxs-lookup"><span data-stu-id="b8a13-114">Microsoft also employs a dedicated team of penetration testers and engages in periodic Red Team and Blue Team exercises to find security and access control issues in the service.</span></span> <span data-ttu-id="b8a13-115">客戶可以使用稽核報告和管理活動 API 提供 Office 365 所驗證訪問控制系統的有效性。</span><span class="sxs-lookup"><span data-stu-id="b8a13-115">Customers can verify the effectiveness of access control systems by using audit reports and the management activity API provided by Office 365.</span></span>

<span data-ttu-id="b8a13-116">如需詳細資訊，請參閱[Office 365 管理活動 API 參考資料](https://msdn.microsoft.com/en-us/library/office/mt227394.aspx)及[稽核與 Office 365 中的報告](office-365-auditing-and-reporting-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a13-116">For more information, see [Office 365 Management Activity API reference](https://msdn.microsoft.com/en-us/library/office/mt227394.aspx) and [Auditing and Reporting in Office 365](office-365-auditing-and-reporting-overview.md).</span></span>
