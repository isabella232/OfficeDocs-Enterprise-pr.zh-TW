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
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>在 Microsoft 365 中查看目錄同步處理錯誤

您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)中查看目錄同步處理錯誤。 只會顯示使用者物件錯誤。 若要使用 PowerShell 來查看錯誤，請參閱使用[DirSyncProvisioningErrors 識別物件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。

查看之後，請參閱[修正 Microsoft 365 目錄同步處理的問題](fix-problems-with-directory-synchronization.md)，修正任何已識別的問題。
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>在系統管理中心中查看目錄同步處理錯誤

若要在系統管理中心中查看任何錯誤：
  
1. 請使用工作或學校帳戶登入 Microsoft 365。 
    
2. 請移至[相關](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)的系統管理中心。
    
3. 在**首頁**上，您會看到**DirSync 狀態**磚。 
    
    ![系統管理中心預覽中的 DirSync 狀態磚](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. 在磚上，選擇 [ **DirSync 狀態**]，以移至 [**目錄同步處理狀態**] 頁面。 
    
    在頁面底部，您可以查看是否有 DirSync 錯誤。
    
    ![在 [目錄同步處理狀態] 頁面上，您可以查看是否有 DirSync 物件錯誤](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    選擇 [**我們發現 DirSync 物件錯誤**]，以移至詳細的目錄同步處理錯誤的觀點。 
    
    > [!NOTE]
    > 您也可以移至 [ **DirSync 錯誤**] 頁面（如果選擇我們在**DirSync 狀態**磚上**找到 DirSync 物件錯誤**）。 
  
![DirSync 錯誤] 頁面](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. 在 [ **DirSync 錯誤**] 頁面上，選擇所列的任何錯誤，以顯示詳細資料窗格，顯示錯誤的相關資訊，以及如何修正問題的秘訣。 
