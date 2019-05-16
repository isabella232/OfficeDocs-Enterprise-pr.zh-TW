---
title: 若要降低讀取郵件時使用的記憶體使用精簡的快顯
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: 本文包含改進網頁型 Outlook 中的郵件下載效能的資訊。
ms.openlocfilehash: 344047363bd58850fcd08a7f8f2fd46de757668c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070559"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="f503f-103">若要降低讀取郵件時使用的記憶體使用精簡的快顯</span><span class="sxs-lookup"><span data-stu-id="f503f-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="f503f-104">本文包含改進網頁型 Outlook 中的郵件下載效能的資訊。</span><span class="sxs-lookup"><span data-stu-id="f503f-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="f503f-105">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="f503f-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="f503f-106">身為 Office 365 全域管理員，您可以設定 outlook 網頁版傳送*精簡的快顯*，較小，較不需要大量記憶體的版本的 Microsoft Edge 或 Internet Explorer 中某些電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="f503f-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="f503f-107">當精簡的快顯已為網頁型 Outlook 時，伺服器端轉譯元件會載入的最佳化效能。</span><span class="sxs-lookup"><span data-stu-id="f503f-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="f503f-108">截至年 3 月 2018年精簡的快顯目前目前不適用於指定使用的權限限制，例如資訊版權管理 (IRM) 的郵件。</span><span class="sxs-lookup"><span data-stu-id="f503f-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="f503f-109">這些功能將會繼續在主視窗中工作，但不提供精簡的快顯：</span><span class="sxs-lookup"><span data-stu-id="f503f-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="f503f-110">Outlook 增益集</span><span class="sxs-lookup"><span data-stu-id="f503f-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="f503f-111">Skype 商務的目前狀態</span><span class="sxs-lookup"><span data-stu-id="f503f-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="f503f-112">**若要設定的所有使用者在 Office 365 組織的精簡快顯**</span><span class="sxs-lookup"><span data-stu-id="f503f-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="f503f-113">[連線至 Exchange Online 使用遠端 PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。</span><span class="sxs-lookup"><span data-stu-id="f503f-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="f503f-114">執行[Set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)指令程式搭配 LeanPopoutEnabled 參數如下所示：</span><span class="sxs-lookup"><span data-stu-id="f503f-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="f503f-115">例如，若要啟用您的組織中的所有使用者的精簡快顯：</span><span class="sxs-lookup"><span data-stu-id="f503f-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="f503f-116">若要停用您組織中的所有使用者的精簡快顯：</span><span class="sxs-lookup"><span data-stu-id="f503f-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


