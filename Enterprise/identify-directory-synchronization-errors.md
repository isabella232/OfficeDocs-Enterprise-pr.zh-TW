---
title: 檢視 Office 365 中的目錄同步處理錯誤
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: 了解如何在 Microsoft 365 系統管理中心中檢視目錄同步處理錯誤。
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067519"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>檢視 Office 365 中的目錄同步處理錯誤

您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中檢視目錄同步處理錯誤。 僅限的使用者物件錯誤會顯示。 若要使用 PowerShell 檢視錯誤，請參閱 < <b0>DirSyncProvisioningErrors 識別物件</b0>。

之後檢視，請參閱[修正 Office 365 的目錄同步處理的問題](fix-problems-with-directory-synchronization.md)修正任何已識別的問題。
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>在系統管理中心中檢視目錄同步處理錯誤

若要在系統管理中心中檢視的任何錯誤：
  
1. 以公司或學校帳戶登入 Office 365。 
    
2. 移至[關於系統管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)。
    
3. 在 [**首頁**] 頁面上，您會看到 [**目錄同步狀態**] 磚。 
    
    ![在系統管理中心預覽中並排顯示 DirSync 狀態](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. 在該磚，選擇 [移至 [**目錄同步作業狀態**] 頁面上的**目錄同步狀態**。 
    
    在頁面底部中，您可以查看是否有 DirSync 錯誤。
    
    ![在 [目錄同步作業狀態] 頁面上您可以查看是否有 DirSync 物件時發生錯誤](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    選擇 [移至目錄同步處理錯誤的詳細檢視**我們發現 DirSync 物件時發生錯誤**。 
    
    > [!NOTE]
    > 如果您在 [**目錄同步狀態**] 磚上選擇 [**我們發現 DirSync 物件時發生錯誤**，您也可以移至**DirSync 錯誤**頁面。 
  
![DirSync 錯誤頁面](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. 在**DirSync 錯誤**頁面上，選擇任何列顯示如何修正問題的秘訣與錯誤的相關資訊的詳細資料] 窗格的錯誤。 
