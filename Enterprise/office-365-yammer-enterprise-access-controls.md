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
description: 摘要： 簡短摘要有關 Yammer 企業存取控制在實際執行環境中。
ms.openlocfilehash: 19910ec0771b3034e7a290190ae7045ffc8651cf
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067302"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="03efb-103">Yammer 企業存取控制</span><span class="sxs-lookup"><span data-stu-id="03efb-103">Yammer Enterprise Access Controls</span></span> 

<span data-ttu-id="03efb-104">對 Yammer 實際執行環境的實體和邏輯存取只有一小群人 （基礎結構和作業）。</span><span class="sxs-lookup"><span data-stu-id="03efb-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="03efb-105">就像其他 Office 365 工程人員 Yammer 工程師會有零常設存取客戶資料。</span><span class="sxs-lookup"><span data-stu-id="03efb-105">As with other Office 365 engineers, Yammer engineers have zero standing access to Customer Data.</span></span> <span data-ttu-id="03efb-106">類似於 Lockbox 核准型剛時間存取控制系統使用有限數量的核准者必須要求存取權。</span><span class="sxs-lookup"><span data-stu-id="03efb-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="03efb-107">核准者確認要求 （例如，它們可驗證要求是否合法根據需要、 業務案例、 時間、 等），然後核准或拒絕要求。</span><span class="sxs-lookup"><span data-stu-id="03efb-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="03efb-108">如果核准要求，JIT 存取會授與定義及有限的時間。</span><span class="sxs-lookup"><span data-stu-id="03efb-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="03efb-109">超過存取時間後，access 會自動到期。</span><span class="sxs-lookup"><span data-stu-id="03efb-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="03efb-110">就像其他 Office 365 服務，所有存取 Yammer 實際執行環境都使用多重要素驗證。</span><span class="sxs-lookup"><span data-stu-id="03efb-110">As with other Office 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="03efb-111">所有的存取權和命令歷程記錄是歸因於一位使用者，登入和定期檢閱 Yammer 安全性小組。</span><span class="sxs-lookup"><span data-stu-id="03efb-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="03efb-112">如需有關 Yammer 系統管理與管理的詳細資訊，請參閱[Yammer 系統管理說明](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US)。</span><span class="sxs-lookup"><span data-stu-id="03efb-112">For more information about Yammer administration and management, see [Yammer Admin Help](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).</span></span>