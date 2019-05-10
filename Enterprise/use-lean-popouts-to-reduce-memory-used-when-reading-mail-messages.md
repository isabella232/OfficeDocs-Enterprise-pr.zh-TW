---
title: 若要降低讀取郵件時使用的記憶體使用精簡的快顯
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: 本文包含改進網頁型 Outlook 中的郵件下載效能的資訊。
ms.openlocfilehash: 55cbdec3dc994f3301afaf1bf0a261de446d522a
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655777"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>若要降低讀取郵件時使用的記憶體使用精簡的快顯

本文包含改進網頁型 Outlook 中的郵件下載效能的資訊。 本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)專案的一部分。
   
身為 Office 365 全域管理員，您可以設定 outlook 網頁版傳送*精簡的快顯*，較小，較不需要大量記憶體的版本的 Microsoft Edge 或 Internet Explorer 中某些電子郵件訊息。 當精簡的快顯已為網頁型 Outlook 時，伺服器端轉譯元件會載入的最佳化效能。 
  
> [!NOTE]
> 截至年 3 月 2018年精簡的快顯目前目前不適用於指定使用的權限限制，例如資訊版權管理 (IRM) 的郵件。 
  
這些功能將會繼續在主視窗中工作，但不提供精簡的快顯：
  
- Outlook 增益集
    
- Skype 商務的目前狀態
    
 **若要設定的所有使用者在 Office 365 組織的精簡快顯**
  
1. [連線至 Exchange Online 使用遠端 PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。
    
2. 執行[Set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)指令程式搭配 LeanPopoutEnabled 參數如下所示： 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  例如，若要啟用您的組織中的所有使用者的精簡快顯：
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  若要停用您組織中的所有使用者的精簡快顯：
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


