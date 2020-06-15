---
title: 在 Microsoft 365 中查看目錄同步處理錯誤
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: 瞭解如何在 Microsoft 365 admin center 中查看目錄同步處理錯誤。
ms.openlocfilehash: d10abc29a08da4352d4c0779698e2062175008b4
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711643"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="a7513-103">在 Microsoft 365 中查看目錄同步處理錯誤</span><span class="sxs-lookup"><span data-stu-id="a7513-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="a7513-104">您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中查看目錄同步處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7513-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="a7513-105">只會顯示使用者物件錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7513-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="a7513-106">若要使用 PowerShell 來查看錯誤，請參閱使用[DirSyncProvisioningErrors 識別物件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。</span><span class="sxs-lookup"><span data-stu-id="a7513-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="a7513-107">查看之後，請參閱[修正 Microsoft 365 目錄同步處理的問題](fix-problems-with-directory-synchronization.md)，修正任何已識別的問題。</span><span class="sxs-lookup"><span data-stu-id="a7513-107">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="a7513-108">在系統管理中心中查看目錄同步處理錯誤</span><span class="sxs-lookup"><span data-stu-id="a7513-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="a7513-109">若要在系統管理中心中查看任何錯誤：</span><span class="sxs-lookup"><span data-stu-id="a7513-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="a7513-110">請使用工作或學校帳戶登入 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="a7513-110">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="a7513-111">請移至[相關](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)的系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="a7513-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="a7513-112">在**首頁**上，您會看到**DirSync 狀態**磚。</span><span class="sxs-lookup"><span data-stu-id="a7513-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![系統管理中心預覽中的 DirSync 狀態磚](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="a7513-114">在磚上，選擇 [ **DirSync 狀態**]，以移至 [**目錄同步處理狀態**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="a7513-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="a7513-115">在頁面底部，您可以查看是否有 DirSync 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7513-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![在 [目錄同步處理狀態] 頁面上，您可以查看是否有 DirSync 物件錯誤](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="a7513-117">選擇 [**我們發現 DirSync 物件錯誤**]，以移至詳細的目錄同步處理錯誤的觀點。</span><span class="sxs-lookup"><span data-stu-id="a7513-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="a7513-118">您也可以移至 [ **DirSync 錯誤**] 頁面（如果選擇我們在**DirSync 狀態**磚上**找到 DirSync 物件錯誤**）。</span><span class="sxs-lookup"><span data-stu-id="a7513-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![DirSync 錯誤] 頁面](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="a7513-120">在 [ **DirSync 錯誤**] 頁面上，選擇所列的任何錯誤，以顯示詳細資料窗格，顯示錯誤的相關資訊，以及如何修正問題的秘訣。</span><span class="sxs-lookup"><span data-stu-id="a7513-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
