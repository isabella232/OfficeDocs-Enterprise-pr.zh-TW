---
title: OneDrive 中和 Office 365 中 SharePoint Online 的多地理位置功能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 使用 OneDrive 和 Sharepoint 中的多地理位置功能，將 Office 365 的目前狀態拓展至多個地理區域。
ms.openlocfilehash: c6648dc8a0b225105e408fc082f6bb4d1a1b4930
ms.sourcegitcommit: 2f138e0733266ab4b179bbe882c734500118dde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "24012733"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="1352e-103">OneDrive 中和 Office 365 中 SharePoint Online 的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="1352e-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="1352e-p101">使用 OneDrive 和 Sharepoint Online 中的多地理位置功能，貴組織可以將 Office 365 目前狀態拓展至您現有租用戶中的多個地理區域及/或國家。連絡 Microsoft 帳戶小組以註冊商務用 OneDrive 多地理位置的多國家公司。</span><span class="sxs-lookup"><span data-stu-id="1352e-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="1352e-106">您可以使用 OneDrive 多地理位置，來佈建待用資料並將資料儲存在您所選擇之符合資料常駐要求的地理位置，和同時將現代化生產力體驗逐步拓展至您的員工。</span><span class="sxs-lookup"><span data-stu-id="1352e-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="1352e-107">以下是多地理位置功能為您組織帶來好處的方式：</span><span class="sxs-lookup"><span data-stu-id="1352e-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="1352e-108">以全域連接組織的形式運作，內含跨多個地理位置的單一 Office 365 租用戶。</span><span class="sxs-lookup"><span data-stu-id="1352e-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="1352e-109">在指定地理位置中建立及主控待用資料以符合資料常駐要求。</span><span class="sxs-lookup"><span data-stu-id="1352e-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="1352e-110">賦與衛星使用者中央位置使用者所享有的相同現代化生產力體驗。</span><span class="sxs-lookup"><span data-stu-id="1352e-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="1352e-111">可讓您的使用者隨著角色變更移到各個地理位置，同時對其內容的存取權則保持不變。</span><span class="sxs-lookup"><span data-stu-id="1352e-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="1352e-112">為每個地理位置打造共用原則和為每個網站打造資料外洩防護原則。</span><span class="sxs-lookup"><span data-stu-id="1352e-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="1352e-113">為每個地理位置指派電子文件探索管理員，並允許管理為您地理位置量身打造的案例。</span><span class="sxs-lookup"><span data-stu-id="1352e-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="1352e-114">選擇其他地理位置的唯一 URL 命名空間 (例如 ContosoEUR.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="1352e-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="1352e-115">將區域內部部署資料與 Office 365 多地理位置租用戶合併。</span><span class="sxs-lookup"><span data-stu-id="1352e-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="1352e-p102">在多地理位置組態中，Office 365 租用包含中央位置 (也就是預設位置) 以及一或多個衛星地理位置。多地理位置的重要概念是，單一租用戶會跨越多個地理位置。在多地理位置租用戶中，系統會在 Azure Active Directory (AAD) 中主控地理位置、群組和使用者資訊的相關資訊。因為您的租用戶資訊是集中管理且同步處理到每個地理位置，包含公司任何人的共用與體驗都會包含全域意識。</span><span class="sxs-lookup"><span data-stu-id="1352e-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="1352e-120">影片：介紹 Office 365 的多地理位置</span><span class="sxs-lookup"><span data-stu-id="1352e-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="1352e-121">在三個簡單的步驟中獲得多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="1352e-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="1352e-122">設定多地理位置很簡單：</span><span class="sxs-lookup"><span data-stu-id="1352e-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="1352e-p103">與您的帳戶小組合作以新增 _Office 365 中的多地理位置功能_服務方案。他們會引導您新增所需的授權數目。</span><span class="sxs-lookup"><span data-stu-id="1352e-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="1352e-125">新增衛星位置。</span><span class="sxs-lookup"><span data-stu-id="1352e-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="1352e-126">設定適當位置的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1352e-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="1352e-127">多地理位置狀態和可用性</span><span class="sxs-lookup"><span data-stu-id="1352e-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="1352e-128">目前在這些地區與國家中提供的 OneDrive 多地理位置：</span><span class="sxs-lookup"><span data-stu-id="1352e-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="1352e-129">亞太地區</span><span class="sxs-lookup"><span data-stu-id="1352e-129">Asia-Pacific</span></span>
    
- <span data-ttu-id="1352e-130">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="1352e-130">Australia</span></span>
    
- <span data-ttu-id="1352e-131">加拿大</span><span class="sxs-lookup"><span data-stu-id="1352e-131">Canada</span></span>
    
- <span data-ttu-id="1352e-132">歐盟 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="1352e-132">European Union (EMEA)</span></span>

- <span data-ttu-id="1352e-133">法國</span><span class="sxs-lookup"><span data-stu-id="1352e-133">France</span></span>
    
- <span data-ttu-id="1352e-134">日本</span><span class="sxs-lookup"><span data-stu-id="1352e-134">Japan</span></span>
    
- <span data-ttu-id="1352e-135">英國</span><span class="sxs-lookup"><span data-stu-id="1352e-135">United Kingdom</span></span>
    
- <span data-ttu-id="1352e-136">美國 (北美洲)</span><span class="sxs-lookup"><span data-stu-id="1352e-136">United States (North America)</span></span>
    
- <span data-ttu-id="1352e-137">韓國</span><span class="sxs-lookup"><span data-stu-id="1352e-137">Korea</span></span>
      
<span data-ttu-id="1352e-138">即將推出的地理位置：</span><span class="sxs-lookup"><span data-stu-id="1352e-138">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="1352e-139">印度</span><span class="sxs-lookup"><span data-stu-id="1352e-139">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="1352e-140">快速入門</span><span class="sxs-lookup"><span data-stu-id="1352e-140">Getting started</span></span>

<span data-ttu-id="1352e-p104">若要開始使用商務用 OneDrive 的多地理位置，第一個步驟是[規劃您的商務用 OneDrive 多地理位置環境](plan-for-multi-geo.md)。接下來，[了解管理多地理位置環境](administering-a-multi-geo-environment.md)與[使用者經歷多地理位置環境的方式](multi-geo-user-experience.md)。當您準備好設定商務用 OneDrive 多地理位置時，[設定多地理位置的租用戶](multi-geo-tenant-configuration.md)，然後[將任何現有的 OneDrive 網站移至其新地理位置](move-onedrive-between-geo-locations.md)和[設定搜尋](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="1352e-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
