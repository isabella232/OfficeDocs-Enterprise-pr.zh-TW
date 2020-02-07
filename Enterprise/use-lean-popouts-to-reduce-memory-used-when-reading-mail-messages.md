---
title: 若要降低讀取郵件時使用的記憶體使用精簡的快顯
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: 本文包含改進網頁型 Outlook 中的郵件下載效能的資訊。
ms.openlocfilehash: 49b570da9092ce4fc857757a7da72b2a81fd0090
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843904"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="f678f-103">若要降低讀取郵件時使用的記憶體使用精簡的快顯</span><span class="sxs-lookup"><span data-stu-id="f678f-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="f678f-104">本文包含改進網頁型 Outlook 中的郵件下載效能的資訊。</span><span class="sxs-lookup"><span data-stu-id="f678f-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="f678f-105">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="f678f-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
  
<span data-ttu-id="f678f-106">身為 Office 365 全域管理員，您可以設定 outlook 網頁版傳送_精簡的快顯_，較小，較不需要大量記憶體的版本的 Microsoft Edge 或 Internet Explorer 中某些電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="f678f-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver _lean popouts_, a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="f678f-107">當精簡的快顯已為網頁型 Outlook 時，伺服器端轉譯元件會載入的最佳化效能。</span><span class="sxs-lookup"><span data-stu-id="f678f-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f678f-108">截至年 3 月 2018年精簡的快顯訣不適用於指定使用的權限限制，例如資訊版權管理 (IRM) 的郵件。</span><span class="sxs-lookup"><span data-stu-id="f678f-108">As of March 2018, lean popouts are not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span>
  
<span data-ttu-id="f678f-109">這些功能將會繼續在主視窗中工作，但不提供精簡的快顯：</span><span class="sxs-lookup"><span data-stu-id="f678f-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="f678f-110">Outlook 增益集</span><span class="sxs-lookup"><span data-stu-id="f678f-110">Outlook add-ins</span></span>
  
- <span data-ttu-id="f678f-111">Skype 商務的目前狀態</span><span class="sxs-lookup"><span data-stu-id="f678f-111">Skype for Business presence</span></span>
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a><span data-ttu-id="f678f-112">若要設定的所有使用者在 Office 365 組織的精簡快顯</span><span class="sxs-lookup"><span data-stu-id="f678f-112">To configure lean popouts for all users within your Office 365 organization</span></span>
  
1. <span data-ttu-id="f678f-113">[連線至 Exchange Online 使用遠端 PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。</span><span class="sxs-lookup"><span data-stu-id="f678f-113">[Connect to Exchange Online Using Remote PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
  
2. <span data-ttu-id="f678f-114">執行[Set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx)指令程式搭配 LeanPopoutEnabled 參數如下所示：</span><span class="sxs-lookup"><span data-stu-id="f678f-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span>

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="f678f-115">例如，若要啟用您的組織中的所有使用者的精簡快顯：</span><span class="sxs-lookup"><span data-stu-id="f678f-115">For example, to enable lean popouts for all users in your organization:</span></span>
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="f678f-116">若要停用您組織中的所有使用者的精簡快顯：</span><span class="sxs-lookup"><span data-stu-id="f678f-116">To disable lean popouts for all users in your organization:</span></span>

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
