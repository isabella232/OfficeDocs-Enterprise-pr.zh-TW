---
title: 調整 Exchange Online 效能
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 本文包含一般的祕訣和告訴您如何增進效能的 Exchange Online 的其他資源的連結。
ms.openlocfilehash: 4ef0276345a3d7f1c9aeba016824f9cb06c475cb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841080"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="2ff18-103">調整 Exchange Online 效能</span><span class="sxs-lookup"><span data-stu-id="2ff18-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="2ff18-104">本文包含一般的祕訣和告訴您如何增進效能的 Exchange Online 中，特別是在移轉前方的其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="2ff18-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="2ff18-105">本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="2ff18-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="2ff18-106">若要改善 Exchange Online 效能的考量事項</span><span class="sxs-lookup"><span data-stu-id="2ff18-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="2ff18-107">若要改善移轉速度及降低組織的頻寬限制的 Exchange Online，請考慮下列各項：</span><span class="sxs-lookup"><span data-stu-id="2ff18-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="2ff18-108">**減少信箱大小。**</span><span class="sxs-lookup"><span data-stu-id="2ff18-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="2ff18-109">較小的信箱大小提升移轉速度。</span><span class="sxs-lookup"><span data-stu-id="2ff18-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="2ff18-110">**使用信箱移動與 Exchange 混合式部署的功能。**</span><span class="sxs-lookup"><span data-stu-id="2ff18-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="2ff18-111">Exchange 混合部署，離線郵件 （中的表單。OST 檔案） 不需要重新下載時移轉至 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="2ff18-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="2ff18-112">這會大幅降低您下載的頻寬需求。</span><span class="sxs-lookup"><span data-stu-id="2ff18-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="2ff18-113">**排程信箱移動到發生低的網際網路流量和低的內部部署 Exchange 使用的期間。**</span><span class="sxs-lookup"><span data-stu-id="2ff18-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="2ff18-114">在排程移動時, 移轉要求提交至信箱複寫 proxy，並可能不會立即生效。</span><span class="sxs-lookup"><span data-stu-id="2ff18-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="2ff18-115">**使用 Outlook 網頁精簡的快顯。**</span><span class="sxs-lookup"><span data-stu-id="2ff18-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="2ff18-116">精簡的快顯較小的大小，提供 Microsoft Edge 或 Internet Explorer 中某些電子郵件訊息所呈現的伺服器上的某些元件較少需要大量記憶體的版本。</span><span class="sxs-lookup"><span data-stu-id="2ff18-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="2ff18-117">如需詳細資訊，請參閱[讀取郵件時，使用以減少記憶體使用精簡快顯](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。</span><span class="sxs-lookup"><span data-stu-id="2ff18-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="2ff18-118">一般建議</span><span class="sxs-lookup"><span data-stu-id="2ff18-118">General advice</span></span>

- <span data-ttu-id="2ff18-119">請確定 outlook.office.com DNS 查閱進入您位置的邏輯的項目位置，MS 資料中心。</span><span class="sxs-lookup"><span data-stu-id="2ff18-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="2ff18-120">研究信箱快取，然後選擇適當的選項 （回覆。</span><span class="sxs-lookup"><span data-stu-id="2ff18-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="2ff18-121">快取週期、 共用的信箱快取、 et cetera）。</span><span class="sxs-lookup"><span data-stu-id="2ff18-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="2ff18-122">您無法傳送透過 VPN 連線 （中央機房） 之前的 Outlook 資料應放在網際網路上的保留。</span><span class="sxs-lookup"><span data-stu-id="2ff18-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="2ff18-123">請確定您的信箱資料遵守資料夾和項目、 金額上的限制。</span><span class="sxs-lookup"><span data-stu-id="2ff18-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="2ff18-124">如需 Exchange 移轉效能的詳細資訊，請參閱[Office 365 移轉效能和最佳作法](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。</span><span class="sxs-lookup"><span data-stu-id="2ff18-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

