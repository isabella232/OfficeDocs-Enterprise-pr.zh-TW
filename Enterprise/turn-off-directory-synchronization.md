---
title: 關閉 Microsoft 365 的目錄同步處理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
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
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: 瞭解如何使用 PowerShell 關閉 Microsoft 365 的目錄同步處理
ms.openlocfilehash: 935d7e26c7b99aba876500e6b9d428557aed5b9c
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906206"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="5c89b-103">關閉 Microsoft 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="5c89b-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="5c89b-104">您可以使用 PowerShell 關閉目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="5c89b-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="5c89b-105">不過，不建議您關閉目錄同步處理做為疑難排解步驟。</span><span class="sxs-lookup"><span data-stu-id="5c89b-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="5c89b-106">如果您需要協助進行目錄同步處理，請參閱[修正 Microsoft 365 文章的目錄同步處理問題](fix-problems-with-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="5c89b-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="5c89b-107">如有需要，[請聯絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)商務產品的支援人員。</span><span class="sxs-lookup"><span data-stu-id="5c89b-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="5c89b-108">關閉目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="5c89b-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="5c89b-109">若要關閉目錄同步處理：</span><span class="sxs-lookup"><span data-stu-id="5c89b-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="5c89b-110">首先，安裝必要的軟體，並聯機至您的 Microsoft 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="5c89b-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="5c89b-111">如需相關指示，請參閱[Connect The Microsoft Azure Active Directory Module For Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="5c89b-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="5c89b-112">使用[Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)停用目錄同步處理：</span><span class="sxs-lookup"><span data-stu-id="5c89b-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
