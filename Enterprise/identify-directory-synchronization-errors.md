---
title: 檢視 Office 365 中目錄同步處理錯誤
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: 了解如何在 Office 365 系統管理中心檢視目錄同步作業錯誤。
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327335"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="345ec-103">檢視 Office 365 中目錄同步處理錯誤</span><span class="sxs-lookup"><span data-stu-id="345ec-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="345ec-p101">您可以在 Office 365 系統管理中心檢視目錄同步作業錯誤。僅限使用者物件錯誤會顯示。若要使用 PowerShell 檢視錯誤，請參閱 ＜[身分識別 DirSyncProvisioningErrors 物件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。</span><span class="sxs-lookup"><span data-stu-id="345ec-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="345ec-107">之後檢視，請參閱[修復 Office 365 的目錄同步處理問題的](fix-problems-with-directory-synchronization.md)修正任何已識別的問題。</span><span class="sxs-lookup"><span data-stu-id="345ec-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="345ec-108">檢視系統管理中心中的目錄同步處理錯誤</span><span class="sxs-lookup"><span data-stu-id="345ec-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="345ec-109">在管理中心中檢視的任何錯誤：</span><span class="sxs-lookup"><span data-stu-id="345ec-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="345ec-110">以公司或學校帳戶登入 Office 365。</span><span class="sxs-lookup"><span data-stu-id="345ec-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="345ec-111">瀏覽至[相關的 Office 365 系統管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)。</span><span class="sxs-lookup"><span data-stu-id="345ec-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="345ec-112">在 [**首頁**] 頁面上您會看到**DirSync 狀態**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="345ec-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![DirSync 狀態磚 admin center preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="345ec-114">磚上選擇 [移至 [**目錄同步處理狀態**] 頁面上的**DirSync 狀態**]。</span><span class="sxs-lookup"><span data-stu-id="345ec-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="345ec-115">在頁面底部可以查看是否有 DirSync 錯誤。</span><span class="sxs-lookup"><span data-stu-id="345ec-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![在 [目錄同步處理狀態] 頁面上您可以查看是否有 DirSync 物件時發生錯誤](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="345ec-117">選擇 [移至目錄同步處理錯誤的詳細檢視**我們找到 DirSync 物件時發生錯誤**。</span><span class="sxs-lookup"><span data-stu-id="345ec-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="345ec-118">如果您選擇**我們找到 DirSync 物件錯誤** **DirSync 狀態**磚上也可以移至**DirSync 錯誤**頁面。</span><span class="sxs-lookup"><span data-stu-id="345ec-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![DirSync 錯誤頁面](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="345ec-120">**DirSync 錯誤**] 索引標籤上選擇 [顯示詳細資料窗格的錯誤與如何修正此問題的秘訣資訊所列之任何的錯誤]。</span><span class="sxs-lookup"><span data-stu-id="345ec-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
