---
title: 關閉 Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
description: 了解如何使用 PowerShell 來關閉 for Office 365 的目錄同步處理
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085072"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="cc871-103">關閉 Office 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="cc871-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="cc871-p101">您可以使用 PowerShell 關閉目錄同步處理。不過，不建議您關閉目錄同步處理所疑難排解步驟。如果您需要使用目錄同步處理的疑難排解協助，請參閱[Office 365 的目錄同步作業正在修復問題](fix-problems-with-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="cc871-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="cc871-107">[連絡人支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)的商務產品視。</span><span class="sxs-lookup"><span data-stu-id="cc871-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="cc871-108">關閉目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="cc871-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="cc871-109">若要關閉目錄同步作業：</span><span class="sxs-lookup"><span data-stu-id="cc871-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="cc871-p102">首先，安裝必要的軟體並連線至您的 Office 365 訂閱。兩者的指示，請參閱[連線至 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938)。</span><span class="sxs-lookup"><span data-stu-id="cc871-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="cc871-112">使用[Set-msoldirsyncenabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)來停用目錄同步作業：</span><span class="sxs-lookup"><span data-stu-id="cc871-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```