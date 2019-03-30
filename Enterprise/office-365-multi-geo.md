---
title: Office 365 多地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 使用 Office 365 多地理位置，將 Office 365 的存在狀態拓展至多個地理區域。
ms.openlocfilehash: e216f61806ea5d648519ac7217acf7dbaddd1419
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933968"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="5bc37-103">Office 365 多地理位置</span><span class="sxs-lookup"><span data-stu-id="5bc37-103">Video: Introducing Office 365 Multi-Geo</span></span>

<span data-ttu-id="5bc37-104">使用 Office 365 多地理位置，您的組織可以將 Office 365 存在狀態擴展到現有租用戶中的多個地理區域和/或國家/地區。</span><span class="sxs-lookup"><span data-stu-id="5bc37-104">With Multi-Geo capabilities in OneDrive Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span> <span data-ttu-id="5bc37-105">聯繫您的 Microsoft 客戶小組，以註冊跨國公司的 Office 365 多地理位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Office 365 Multi-Geo.</span></span>
  
<span data-ttu-id="5bc37-106">您可以使用 Office 365 多地理位置，來佈建待用資料並將資料儲存在您所選擇之符合資料常駐要求的地理位置，和同時將現代化生產力體驗逐步拓展至您的員工。</span><span class="sxs-lookup"><span data-stu-id="5bc37-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="5bc37-107">影片：介紹 Office 365 的多地理位置</span><span class="sxs-lookup"><span data-stu-id="5bc37-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="5bc37-108">在多地理位置環境中，Office 365 租用戶包含一個中央位置(最初佈建 Office 365 訂閱的位置) 和一個或多個衛星位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="5bc37-109">在多地理位置租用戶中，地理位置、群組和使用者資訊的相關資訊掌握在 Azure Active Directory (AAD) 中。</span><span class="sxs-lookup"><span data-stu-id="5bc37-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="5bc37-110">由於您的租用戶資訊會集中管理並同步到每個地理位置，若要共用及體驗，公司的每一位員工都必須擁有全域概念。</span><span class="sxs-lookup"><span data-stu-id="5bc37-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![SharePoint 系統管理中心內多地理位置地圖的螢幕擷取畫面](media/multi-geo-world-map.png)

<span data-ttu-id="5bc37-112">請注意，Office 365 多地理位置主要不是為效能最佳化優化而設計，其主要設計目的在滿足資料落地要求。</span><span class="sxs-lookup"><span data-stu-id="5bc37-112">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see Network planning and performance tuning for Office 365 or contact your support group.</span></span> <span data-ttu-id="5bc37-113">如需 Office 365 的效能最佳化的詳細資訊，請參閱 [ Office 365 的網路規劃與效能調整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)或連絡客戶支援小組。</span><span class="sxs-lookup"><span data-stu-id="5bc37-113">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="5bc37-114">詞彙</span><span class="sxs-lookup"><span data-stu-id="5bc37-114">Terminology</span></span>

<span data-ttu-id="5bc37-115">以下是用於說明 Office 365 多地理位置的重要詞彙：</span><span class="sxs-lookup"><span data-stu-id="5bc37-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="5bc37-116">**中央位置** - 佈建租用戶的原始地理位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="5bc37-117">**地理位置管理員** - 系統管理員，可以管理一或多個指定的衛星位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="5bc37-118">**地理位置代碼** - 表示特定地理位置的三個字母代碼。</span><span class="sxs-lookup"><span data-stu-id="5bc37-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="5bc37-119">**地理位置** – 用於在多地理位置租用戶中主控資料的地理位置，包括 Exchange 信箱以及 OneDrive 和 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="5bc37-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="5bc37-120">**慣用的資料位置 (PDL)** - 由系統管理員設定的使用者屬性，表示應佈建使用者 Exchange 信箱和 OneDrive 的地理位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="5bc37-121">PDL 還可決定要在哪裡佈建使用者建立的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="5bc37-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="5bc37-122">**衛星位置** – 在多地理位置租用戶中啟用地理感知 Office 365工作量 (SharePoint、OneDrive和 Exchange) 的地理位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="5bc37-123">**租用戶** – 組織在 Office 365 中的呈現方式，通常會有與其相關聯的一個或多個網域 (例如 contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="5bc37-123">Tenant – An organization's representation in the Office 365 cloud which typically has one or more domains associated with it (for example, .</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="5bc37-124">Office 365 多地理位置可用性</span><span class="sxs-lookup"><span data-stu-id="5bc37-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="5bc37-125">目前在這些地區與國家中提供 Office 365 多地理位置：</span><span class="sxs-lookup"><span data-stu-id="5bc37-125">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="5bc37-126">快速入門</span><span class="sxs-lookup"><span data-stu-id="5bc37-126">Getting started</span></span>

<span data-ttu-id="5bc37-127">按照這些步驟來開始使用多地理位置：</span><span class="sxs-lookup"><span data-stu-id="5bc37-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="5bc37-p105">與您的帳戶小組合作以新增 _Office 365 中的多地理位置功能_服務方案。他們會引導您新增所需的授權數目。</span><span class="sxs-lookup"><span data-stu-id="5bc37-p105">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>

   <span data-ttu-id="5bc37-130">開始使用 Office 365 多地理位置之前，Microsoft 必須先設定您的 Exchange Online 租用戶，以支援多地理位置。</span><span class="sxs-lookup"><span data-stu-id="5bc37-130">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="5bc37-131">當您訂購 *Office 365 中的多地理位置功能*服務方案，並於租用戶中顯示授權之後，將觸發此一次性設定程序。</span><span class="sxs-lookup"><span data-stu-id="5bc37-131">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="5bc37-132">套用多地理位置授權之後，您會在 [Office 365 訊息中心](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093)收到通知，然後就可以開始進行設定並使用 Office 365 多地理位置功能。</span><span class="sxs-lookup"><span data-stu-id="5bc37-132">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="5bc37-133">閱讀[規劃多地理位置環境](plan-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="5bc37-133">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="5bc37-134">深入了解[管理多地理位置環境](administering-a-multi-geo-environment.md)與[使用者會遇到的環境](multi-geo-user-experience.md)。</span><span class="sxs-lookup"><span data-stu-id="5bc37-134">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="5bc37-135">當您準備好設定 Office 365 多地理位置，請[設定租用戶以支援多地理位置](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="5bc37-135">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="5bc37-136">[設定搜尋](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="5bc37-136">[Set up people search](configure-search-for-multi-geo.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="5bc37-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bc37-137">See also</span></span>

[<span data-ttu-id="5bc37-138">Aka.ms/GoMultiGeo </span><span class="sxs-lookup"><span data-stu-id="5bc37-138">Aka.ms/GoMultiGeo </span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="5bc37-139">OneDrive 和 SharePoint Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="5bc37-139">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365.md)

[<span data-ttu-id="5bc37-140">Exchange Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="5bc37-140">NoteFor information on Multi-Geo Capabilities, see Multi-Geo Capabilities in Exchange Online.</span></span>](multi-geo-capabilities-in-exchange-online.md)