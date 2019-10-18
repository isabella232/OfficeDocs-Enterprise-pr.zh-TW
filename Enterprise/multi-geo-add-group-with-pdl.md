---
title: 使用特定 PDL 建立 Office 365 群組
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解如何使用指定的慣用資料位置在多地理位置環境中建立 Office 365 群組。
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069999"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="c0635-103">使用特定 PDL 建立 Office 365 群組</span><span class="sxs-lookup"><span data-stu-id="c0635-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="c0635-104">在位於多地理位置環境中的使用者建立 Office 365 群組時，群組慣用資料位置將自動設定為使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="c0635-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="c0635-105">如果需要建立具有特定 PDL 的群組，則可以使用 Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet 來建立。</span><span class="sxs-lookup"><span data-stu-id="c0635-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="c0635-106">如此一來，將在指定的 PDL 中佈建與該群組關聯的群組信箱和 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="c0635-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="c0635-107">您必須是全域系統管理員或 SharePoint Online 或 Exchange Online 系統管理員才能進行此操作。</span><span class="sxs-lookup"><span data-stu-id="c0635-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="c0635-108">若要使用您指定的 PDL 建立 Office 365 群組，請連線至 Exchange Online PowerShell，並傳遞參數 *-MailBoxRegion* 與地理位置代碼。</span><span class="sxs-lookup"><span data-stu-id="c0635-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="c0635-109">例如：</span><span class="sxs-lookup"><span data-stu-id="c0635-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![New-UnifiedGroup PowerShell cmdlet 以及語法的螢幕擷取畫面](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="c0635-111">請注意，SharePoint 群組網站佈建將依照需求。</span><span class="sxs-lookup"><span data-stu-id="c0635-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="c0635-112">在群組擁有者或成員首次嘗試存取網站時，會對該網站進行佈建。</span><span class="sxs-lookup"><span data-stu-id="c0635-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="c0635-113">地理位置代碼</span><span class="sxs-lookup"><span data-stu-id="c0635-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="c0635-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0635-114">See also</span></span>

[<span data-ttu-id="c0635-115">連線到 Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0635-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)