---
title: 檢視 Office 365 中的目錄同步處理錯誤
ms.author: robmazz
author: robmazz
manager: laurawi
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: 了解如何在 Microsoft 365 系統管理中心中檢視目錄同步處理錯誤。
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491255"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="1a23b-103">檢視 Office 365 中的目錄同步處理錯誤</span><span class="sxs-lookup"><span data-stu-id="1a23b-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="1a23b-104">您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中檢視目錄同步處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a23b-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="1a23b-105">僅限的使用者物件錯誤會顯示。</span><span class="sxs-lookup"><span data-stu-id="1a23b-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="1a23b-106">若要使用 PowerShell 檢視錯誤，請參閱 < <b0>DirSyncProvisioningErrors 識別物件</b0>。</span><span class="sxs-lookup"><span data-stu-id="1a23b-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="1a23b-107">之後檢視，請參閱[修正 Office 365 的目錄同步處理的問題](fix-problems-with-directory-synchronization.md)修正任何已識別的問題。</span><span class="sxs-lookup"><span data-stu-id="1a23b-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="1a23b-108">在系統管理中心中檢視目錄同步處理錯誤</span><span class="sxs-lookup"><span data-stu-id="1a23b-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="1a23b-109">若要在系統管理中心中檢視的任何錯誤：</span><span class="sxs-lookup"><span data-stu-id="1a23b-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="1a23b-110">以公司或學校帳戶登入 Office 365。</span><span class="sxs-lookup"><span data-stu-id="1a23b-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="1a23b-111">移至[關於系統管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)。</span><span class="sxs-lookup"><span data-stu-id="1a23b-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="1a23b-112">在 [**首頁**] 頁面上，您會看到 [**目錄同步狀態**] 磚。</span><span class="sxs-lookup"><span data-stu-id="1a23b-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![在系統管理中心預覽中並排顯示 DirSync 狀態](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="1a23b-114">在該磚，選擇 [移至 [**目錄同步作業狀態**] 頁面上的**目錄同步狀態**。</span><span class="sxs-lookup"><span data-stu-id="1a23b-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="1a23b-115">在頁面底部中，您可以查看是否有 DirSync 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a23b-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![在 [目錄同步作業狀態] 頁面上您可以查看是否有 DirSync 物件時發生錯誤](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="1a23b-117">選擇 [移至目錄同步處理錯誤的詳細檢視**我們發現 DirSync 物件時發生錯誤**。</span><span class="sxs-lookup"><span data-stu-id="1a23b-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="1a23b-118">如果您在 [**目錄同步狀態**] 磚上選擇 [**我們發現 DirSync 物件時發生錯誤**，您也可以移至**DirSync 錯誤**頁面。</span><span class="sxs-lookup"><span data-stu-id="1a23b-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![DirSync 錯誤頁面](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="1a23b-120">在**DirSync 錯誤**頁面上，選擇任何列顯示如何修正問題的秘訣與錯誤的相關資訊的詳細資料] 窗格的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a23b-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
