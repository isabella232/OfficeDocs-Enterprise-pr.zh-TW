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
# <a name="view-directory-synchronization-errors-in-office-365"></a>檢視 Office 365 中目錄同步處理錯誤

您可以在 Office 365 系統管理中心檢視目錄同步作業錯誤。僅限使用者物件錯誤會顯示。若要使用 PowerShell 檢視錯誤，請參閱 ＜[身分識別 DirSyncProvisioningErrors 物件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。

之後檢視，請參閱[修復 Office 365 的目錄同步處理問題的](fix-problems-with-directory-synchronization.md)修正任何已識別的問題。
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>檢視系統管理中心中的目錄同步處理錯誤

在管理中心中檢視的任何錯誤：
  
1. 以公司或學校帳戶登入 Office 365。 
    
2. 瀏覽至[相關的 Office 365 系統管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)。
    
3. 在 [**首頁**] 頁面上您會看到**DirSync 狀態**並排顯示。 
    
    ![DirSync 狀態磚 admin center preview](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. 磚上選擇 [移至 [**目錄同步處理狀態**] 頁面上的**DirSync 狀態**]。 
    
    在頁面底部可以查看是否有 DirSync 錯誤。
    
    ![在 [目錄同步處理狀態] 頁面上您可以查看是否有 DirSync 物件時發生錯誤](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    選擇 [移至目錄同步處理錯誤的詳細檢視**我們找到 DirSync 物件時發生錯誤**。 
    
    > [!NOTE]
    > 如果您選擇**我們找到 DirSync 物件錯誤** **DirSync 狀態**磚上也可以移至**DirSync 錯誤**頁面。 
  
![DirSync 錯誤頁面](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. **DirSync 錯誤**] 索引標籤上選擇 [顯示詳細資料窗格的錯誤與如何修正此問題的秘訣資訊所列之任何的錯誤]。 
