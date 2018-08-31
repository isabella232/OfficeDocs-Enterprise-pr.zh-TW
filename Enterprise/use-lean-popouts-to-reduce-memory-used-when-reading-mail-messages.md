---
title: 使用精簡 popouts 降低閱讀郵件時所使用的記憶體
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
description: 本文包含改進在網路上的 Outlook 中的郵件下載效能的資訊。
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540005"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>使用精簡 popouts 降低閱讀郵件時所使用的記憶體

本文包含改進在網路上的 Outlook 中的郵件下載效能的資訊。本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)專案的一部分。
   
身為 Office 365 全域管理員，您可以設定 Outlook web 上將傳遞*精簡 popouts* 、 較小、 更少需要大量記憶體版本的 Microsoft Edge 或 Internet Explorer 中特定電子郵件訊息。當精簡 popouts 設定在 web 上的 outlook 時，伺服器端呈現元件會載入的最佳化效能。 
  
> [!NOTE]
> 年 3 月 2018年精簡 popouts 目前不提供所指定 usage 權限限制，例如資訊版權管理 (IRM) 的郵件。 
  
這些功能將會繼續處理主視窗中但不提供精簡 popouts：
  
- Outlook 增益集
    
- Skype 商務平台服務
    
 **若要設定 Office 365 組織內的所有使用者的精簡 popouts**
  
1. [連線至 Exchange Online 使用遠端 PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。
    
2. 執行[Set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)指令程式搭配 LeanPopoutEnabled 參數如下所示： 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    例如，若要啟用貴組織中的所有使用者的精簡 popouts：
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    若要停用貴組織中的所有使用者的精簡 popouts：
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


