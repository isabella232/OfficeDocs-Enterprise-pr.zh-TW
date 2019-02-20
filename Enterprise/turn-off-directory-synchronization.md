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
# <a name="turn-off-directory-synchronization-for-office-365"></a>關閉 Office 365 的目錄同步處理
您可以使用 PowerShell 關閉目錄同步處理。不過，不建議您關閉目錄同步處理所疑難排解步驟。如果您需要使用目錄同步處理的疑難排解協助，請參閱[Office 365 的目錄同步作業正在修復問題](fix-problems-with-directory-synchronization.md)。 
  
[連絡人支援](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)的商務產品視。
  
## <a name="turn-off-directory-synchronization"></a>關閉目錄同步處理  
若要關閉目錄同步作業：
  
1. 首先，安裝必要的軟體並連線至您的 Office 365 訂閱。兩者的指示，請參閱[連線至 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938)。
    
2. 使用[Set-msoldirsyncenabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)來停用目錄同步作業： 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```