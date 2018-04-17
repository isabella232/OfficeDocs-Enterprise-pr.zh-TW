---
title: OneDrive 和 Office 365 中的 SharePoint Online 中的多個地理位置功能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 展開您的 Office 365 平台服務來使用 OneDrive 和 SharePoint Online 中的多個地理位置功能的多個地理區域。
ms.openlocfilehash: 2c5de533aaaace68e51b747cd62a53b9572bcaec
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="88068-103">OneDrive 和 Office 365 中的 SharePoint Online 中的多個地理位置功能</span><span class="sxs-lookup"><span data-stu-id="88068-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="88068-p101">OneDrive 和 SharePoint Online 中的多個地理位置功能，您的組織可以依序展開 [其 Office 365 平台服務多個地理區域 （英文） 和/或國家/地區內您現有的租用戶。此功能目前處於預覽。到達給 Microsoft 帳戶小組才能註冊多 National 公司 OneDrive 多重地理 preview。</span><span class="sxs-lookup"><span data-stu-id="88068-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="88068-107">使用 OneDrive 多-地理位置，您可以佈建靜態資料儲存在您已選擇要符合資料 residency 需求的地理位置和同時解除鎖定您通用 roll 超出現代產能體驗到您的人力。</span><span class="sxs-lookup"><span data-stu-id="88068-107">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="88068-108">以下是多重地理位置功能何助益組織：</span><span class="sxs-lookup"><span data-stu-id="88068-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="88068-109">操作與一部通用連接組織與單一 Office 365 租用戶跨越多個地理位置。</span><span class="sxs-lookup"><span data-stu-id="88068-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="88068-110">建立和主控的資料集在-rest 內指定的地理位置符合資料 residency 需求。</span><span class="sxs-lookup"><span data-stu-id="88068-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="88068-111">對您衛星使用者賦能集中管理位置使用者中慣用相同現代產能經驗。</span><span class="sxs-lookup"><span data-stu-id="88068-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="88068-112">可讓您存取其內容會保持不變時為其角色的變更，移動所有地理位置之間的使用者。</span><span class="sxs-lookup"><span data-stu-id="88068-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="88068-113">依此修改您每個地理位置的共用原則和每個站台的資料外洩防護原則。</span><span class="sxs-lookup"><span data-stu-id="88068-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="88068-114">指定 eDiscovery 管理員每個地理位置，然後允許管理量身訂作地理位置的情況。</span><span class="sxs-lookup"><span data-stu-id="88068-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="88068-115">額外的地理位置的選擇唯一 URL 命名空間 (例如 ContosoEUR.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="88068-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="88068-116">將您內部區域的資料合併到您的 Office 365 多重地理位置租用戶。</span><span class="sxs-lookup"><span data-stu-id="88068-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="88068-p102">在多個地理位置設定中，您的 Office 365 租用戶包含一個集中的位置 （也稱為預設位置） 和一或多個衛星地理位置。多個地理位置的重要概念是該單一租用會跨越一個多個地理位置。在多個地理位置租用戶中對應的 Azure Active Directory (AAD) 地理位置、 群組及使用者資訊的相關資訊。因為您的租用戶資訊是以集中與同步至每個地理位置、 共用及初始化的任何人從您公司的體驗包含全域傳達方式。</span><span class="sxs-lookup"><span data-stu-id="88068-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="88068-121">範例多重地理位置租用戶組態</span><span class="sxs-lookup"><span data-stu-id="88068-121">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="88068-122">藉由使用多個地理位置租用戶，Contoso，與 「 北美地區 」 的集中位置可以依序展開 [附屬地理位置在歐洲、 和澳洲下單一組織雨傘 Contoso.com。時使用他們偏好的資料中的位置北美地區的使用者必須在美國其 OneDrive 使用其偏好的資料的位置設為歐洲使用者將能夠在歐洲其 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="88068-122">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![World 顯示 Contoso 的地理位置及其他可用的地理位置的分佈圖](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="88068-124">取得多個地理位置功能中三個簡單的步驟</span><span class="sxs-lookup"><span data-stu-id="88068-124">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="88068-125">設定多個地理位置很簡單：</span><span class="sxs-lookup"><span data-stu-id="88068-125">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="88068-p103">若要新增_多個地理位置功能的 Office 365_服務計劃帳戶小組與搭配使用。它們可引導您要新增所需的授權數。</span><span class="sxs-lookup"><span data-stu-id="88068-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="88068-128">新增衛星位置。</span><span class="sxs-lookup"><span data-stu-id="88068-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="88068-129">設定您的使用者帳戶的適當位置。</span><span class="sxs-lookup"><span data-stu-id="88068-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="88068-130">多個地理位置狀態與可用性</span><span class="sxs-lookup"><span data-stu-id="88068-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="88068-131">OneDrive 多重地理位置是目前提供這些區域 （英文） 和國家/地區：</span><span class="sxs-lookup"><span data-stu-id="88068-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="88068-132">亞太地區</span><span class="sxs-lookup"><span data-stu-id="88068-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="88068-133">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="88068-133">Australia</span></span>
    
- <span data-ttu-id="88068-134">加拿大</span><span class="sxs-lookup"><span data-stu-id="88068-134">Canada</span></span>
    
- <span data-ttu-id="88068-135">歐盟 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="88068-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="88068-136">日本</span><span class="sxs-lookup"><span data-stu-id="88068-136">Japan</span></span>
    
- <span data-ttu-id="88068-137">英國</span><span class="sxs-lookup"><span data-stu-id="88068-137">United Kingdom</span></span>
    
- <span data-ttu-id="88068-138">美國 （北美洲）</span><span class="sxs-lookup"><span data-stu-id="88068-138">United States (North America)</span></span>
    
- <span data-ttu-id="88068-139">韓國</span><span class="sxs-lookup"><span data-stu-id="88068-139">Korea</span></span>
      
<span data-ttu-id="88068-140">即將推出的地理位置：</span><span class="sxs-lookup"><span data-stu-id="88068-140">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="88068-141">法國</span><span class="sxs-lookup"><span data-stu-id="88068-141">France</span></span>
- <span data-ttu-id="88068-142">印度</span><span class="sxs-lookup"><span data-stu-id="88068-142">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="88068-143">快速入門</span><span class="sxs-lookup"><span data-stu-id="88068-143">Getting started</span></span>

<span data-ttu-id="88068-p104">若要開始使用 OneDrive for Business 多-地理位置，第一個步驟是[規劃您 OneDrive for Business 的多個地理環境](plan-for-multi-geo.md)。下一步]、[了解如何管理多個地理位置環境](administering-a-multi-geo-environment.md)及[如何讓使用者會遇到的多個地理位置環境](multi-geo-user-experience.md)。當您準備好設定 OneDrive for Business 多-地理位置，[設定您的租用戶的多個地理位置](multi-geo-tenant-configuration.md)，然後[移至其新的地理位置的任何現有 OneDrive 網站](move-onedrive-between-geo-locations.md)及[設定搜尋](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="88068-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
