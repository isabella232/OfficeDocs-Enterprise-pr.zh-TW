---
title: 設定 Office 365 多地理位置電子文件探索
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 了解如何在 Office 365 多地理位置設定電子文件探索。
ms.openlocfilehash: f9d8fe8b65f5772005bf7d6a7ea3735277077d3b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069959"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a>Office 365 多地理位置電子文件探索設定


依預設，電子文件探索管理員或多地理位置租用戶的系統管理員僅能在該租用戶的中央位置中進行 eDiscovery。若要支援對衛星位置進行 eDiscovery 的能力，則可透過 PowerShell 取得名為「地區」的新合規性安全性篩選參數。

Office 365 全域系統管理員必須指派電子文件探索管理員權限，以允許其他人執行 eDiscovery，並在其適用的合規性安全性篩選中指派「地區」參數，以將進行 eDiscovery 的區域指定為衛星位置，否則將不會為該衛星位置執行任何 eDiscovery。

當為特定衛星位置設定電子文件探索管理員或系統管理員角色時，電子文件探索管理員或系統管理員只能對位於該衛星位置中的 SharePoint 網站和 OneDrive 網站執行 eDiscovery 搜尋動作。如果電子文件探索管理員或系統管理員嘗試搜尋指定的衛星位置外的 SharePoint 或 OneDrive 網站，則不會傳回任何結果。此外，當某衛星位置的電子文件探索管理員或系統管理員區域觸發匯出時，系統會將資料匯出至該區域的 Azure 執行個體。這可透過禁止匯出控制框線外的內容來協助組織保持合規。

> [!NOTE]
> 如果此對跨多個 SharePoint 衛星位置的電子文件探索管理員是必要的，將必須為指定 OneDrive 或 SharePoint 網站所在位置之替代衛星位置的電子文件探索管理員建立另一個使用者帳戶。

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

若要為某地區設定合規性安全性篩選：

1.  開啟 [Windows PowerShell]。

2.  Enter 鍵  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

請參閱 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 一文以了解額外的參數和語法
