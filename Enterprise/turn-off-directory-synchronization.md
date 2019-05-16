---
title: 關閉 Office 365 的目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: 了解如何使用 PowerShell 來關閉 Office 365 的目錄同步處理
ms.openlocfilehash: 83a01d827217db141016f622a2cb417f93f88e76
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070359"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="91ffb-103">關閉 Office 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="91ffb-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="91ffb-104">您可以使用 PowerShell 來關閉目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="91ffb-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="91ffb-105">不過，不建議您關閉目錄同步作業和疑難排解步驟。</span><span class="sxs-lookup"><span data-stu-id="91ffb-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="91ffb-106">如果您需要協助疑難排解目錄同步處理，請參閱[Office 365 的目錄同步處理的修正問題](fix-problems-with-directory-synchronization.md)> 一文。</span><span class="sxs-lookup"><span data-stu-id="91ffb-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="91ffb-107">[連絡支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)視商務版產品。</span><span class="sxs-lookup"><span data-stu-id="91ffb-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="91ffb-108">關閉目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="91ffb-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="91ffb-109">若要關閉目錄同步作業：</span><span class="sxs-lookup"><span data-stu-id="91ffb-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="91ffb-110">首先，安裝必要的軟體，並連線至您的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="91ffb-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="91ffb-111">兩者皆適用的指示，請參閱[連線至 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938)。</span><span class="sxs-lookup"><span data-stu-id="91ffb-111">For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="91ffb-112">使用[Set-msoldirsyncenabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)停用目錄同步作業：</span><span class="sxs-lookup"><span data-stu-id="91ffb-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```