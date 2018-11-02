---
title: 規劃商務用 OneDrive 多地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 了解商務用 OneDrive 多地理位置、多地理位置的運作方式，以及哪些地理位置可供資料儲存區使用。
ms.openlocfilehash: d40f84ea3636b4eca2711a48bd9d70c73a242cfd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849859"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="f4412-103">規劃商務用 OneDrive 多地理位置</span><span class="sxs-lookup"><span data-stu-id="f4412-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="f4412-104">本指南是為多國公司 (MNC) 的系統管理員而設計，這些管理員會根據公司的目前位置將 SharePoint Online 租用戶擴充為其他地理位置，以符合資料常駐要求。</span><span class="sxs-lookup"><span data-stu-id="f4412-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="f4412-p101">在 OneDrive 多地理位置設定中，Office 365 租用戶包含中央位置，以及一或多個衛星地理位置。這是跨多個地理位置的單一租用戶。在 Azure Active Directory (AAD) 中會使用 OneDrive 多地理位置控制租用戶的資訊 (包括地理位置)。</span><span class="sxs-lookup"><span data-stu-id="f4412-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="f4412-108">以下是一些重要的多地理位置詞彙，可協助您了解設定的基本概念：</span><span class="sxs-lookup"><span data-stu-id="f4412-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="f4412-109">**租用戶** – 組織在 Office 365 雲端中的呈現方式，通常會有與其相關聯的一個或多個網域 (例如 http://contoso.sharepoint.com))。</span><span class="sxs-lookup"><span data-stu-id="f4412-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="f4412-110">**地理位置** – 可用來裝載 Office 365 租用戶中資料的地理位置。</span><span class="sxs-lookup"><span data-stu-id="f4412-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="f4412-p102">**衛星位置** – 您已設定為裝載 Office 365 租用戶中資料的地理位置。多地理位置租用戶橫跨多個地理位置 (例如，北美洲和歐洲)。</span><span class="sxs-lookup"><span data-stu-id="f4412-p102">**Satellite locations** – The geo locations that you have configured to host data in your Office 365 tenant. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="f4412-p103">**慣用的資料位置 (PDL)** - 個別使用者 OneDrive 資料儲存所在的地理位置。系統管理員可以將此設定為任何已允許的資料位置 (已針對該租用戶而設定)。請注意，若您為已擁有 OneDrive 網站的使用者變更 PDL，其 OneDrive 資料將不會自動移至新地理位置。如需詳細資訊，請參閱[將 OneDrive 文件庫移到不同地理位置](move-onedrive-between-geo-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="f4412-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="f4412-117">啟用多地理位置需要四個關鍵步驟：</span><span class="sxs-lookup"><span data-stu-id="f4412-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="f4412-118">與您的帳戶團隊合作來新增 _Office 365 中的多地理位置功能_服務方案。</span><span class="sxs-lookup"><span data-stu-id="f4412-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="f4412-119">選擇您想要的衛星位置，並將其新增至您的租用戶。</span><span class="sxs-lookup"><span data-stu-id="f4412-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="f4412-p104">將使用者慣用的資料位置設定為想要的衛星位置。當系統為使用者佈建新的 OneDrive 網站時，會將該網站佈建至 PDL。</span><span class="sxs-lookup"><span data-stu-id="f4412-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="f4412-122">視需要將使用者現有 OneDrive 網站從中央位置移轉至其慣用的資料位置。</span><span class="sxs-lookup"><span data-stu-id="f4412-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="f4412-123">請參閱[設定商務用 OneDrive 多地理位置](multi-geo-tenant-configuration.md)，以了解這些每個步驟的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f4412-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4412-p105">請注意，Office 365 多地理位置不是針對效能最佳化案例而設計的，它是為符合資料常駐需求而設計的。如需 Office 365 效能最佳化的相關資訊，請參閱[ Office 365 的網路規劃與效能調整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或聯絡客戶支援小組。</span><span class="sxs-lookup"><span data-stu-id="f4412-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="f4412-p106">您可以將任何下列位置設定為衛星位置，您可在其中裝載 OneDrive 檔案。當您規劃多地理位置時，請建立您想要新增至 Office 365 租用戶之位置的清單。如有需要，我們建議從一或兩個衛星位置開始，並逐步擴展到多個地理位置。</span><span class="sxs-lookup"><span data-stu-id="f4412-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f4412-129"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="f4412-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="f4412-130"><strong>代碼</strong></span><span class="sxs-lookup"><span data-stu-id="f4412-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f4412-131">亞太地區</span><span class="sxs-lookup"><span data-stu-id="f4412-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="f4412-132">APC</span><span class="sxs-lookup"><span data-stu-id="f4412-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4412-133">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="f4412-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="f4412-134">AUS</span><span class="sxs-lookup"><span data-stu-id="f4412-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4412-135">加拿大</span><span class="sxs-lookup"><span data-stu-id="f4412-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="f4412-136">CAN</span><span class="sxs-lookup"><span data-stu-id="f4412-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4412-137">歐洲/中東/非洲</span><span class="sxs-lookup"><span data-stu-id="f4412-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="f4412-138">EUR</span><span class="sxs-lookup"><span data-stu-id="f4412-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4412-139">法國</span><span class="sxs-lookup"><span data-stu-id="f4412-139">France</span></span></td>
<td align="left"><span data-ttu-id="f4412-140">FRA</span><span class="sxs-lookup"><span data-stu-id="f4412-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4412-141">日本</span><span class="sxs-lookup"><span data-stu-id="f4412-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="f4412-142">JPN</span><span class="sxs-lookup"><span data-stu-id="f4412-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4412-143">韓國</span><span class="sxs-lookup"><span data-stu-id="f4412-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="f4412-144">KOR</span><span class="sxs-lookup"><span data-stu-id="f4412-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4412-145">北美洲</span><span class="sxs-lookup"><span data-stu-id="f4412-145">North America</span></span></td>
<td align="left"><span data-ttu-id="f4412-146">NAM</span><span class="sxs-lookup"><span data-stu-id="f4412-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4412-147">英國</span><span class="sxs-lookup"><span data-stu-id="f4412-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="f4412-148">GBR</span><span class="sxs-lookup"><span data-stu-id="f4412-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f4412-149">即將推出的地理位置：</span><span class="sxs-lookup"><span data-stu-id="f4412-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="f4412-150">印度</span><span class="sxs-lookup"><span data-stu-id="f4412-150">India</span></span>

<span data-ttu-id="f4412-p107">設定多地理位置時，請考慮在移轉到 Office 365 時合併內部部署基礎結構的可能性。比方說，如果您在新加坡和馬來西亞有內部部署伺服器陣列，然後您可以將他們合併至 APC 衛星位置中，提供的資料常駐要求可讓您執行此動作。</span><span class="sxs-lookup"><span data-stu-id="f4412-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="f4412-153">最佳做法</span><span class="sxs-lookup"><span data-stu-id="f4412-153">Best practices</span></span>

<span data-ttu-id="f4412-p108">我們建議您在 Office 365 建立測試使用者以進行一些初步的測試。我們會使用此使用者逐步進行一些測試和驗證步驟，再繼續將生產環境的使用者裝載到 OneDrive 的多地理位置。</span><span class="sxs-lookup"><span data-stu-id="f4412-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="f4412-p109">當您使用測試使用者完成測試時，請選取試驗群組 (可能是來自您的 IT 部門)，他們會是第一個在新地理位置中使用 OneDrive 的人員。針對此第一個群組，選取尚未擁有 OneDrive 的使用者。我們建議您在此初始群組中不要包含超過 5 個人員，接著再透過批次推行方法逐步擴展人員數量。</span><span class="sxs-lookup"><span data-stu-id="f4412-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="f4412-p110">每個使用者都應該有*慣用資料位置* (PDL) 設定，以便 Office 365 可以判斷應該在哪一個地理位置佈建其 OneDrive。使用者的慣用資料位置必須符合其中一個所選的衛星位置或您的中央位置。PDL 欄位為非必要時，我們建議為所有使用者設定一個 PDL。系統將在中央位置中佈建不具 PDL 的使用者工作負載。</span><span class="sxs-lookup"><span data-stu-id="f4412-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="f4412-p111">建立使用者清單，並包含使用者主體名稱 (UPN) 與適當慣用資料位置的位置代碼。包含測試使用者與您起始的試驗群組來開始進行。您將需要該組態程序的此清單。</span><span class="sxs-lookup"><span data-stu-id="f4412-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="f4412-p112">如果您的使用者從內部部署 Active Directory 系統同步處理至 Azure Active Directory，則您必須使用 Azure Active Directory Connect 為已同步處理的使用者設定慣用資料位置。您無法直接使用 Azure AD PowerShell 來為已同步處理的使用者設定慣用資料位置。[Azure Active Directory Connect 同步：設定 Office 365 資源的慣用資料位置](https://docs.microsoft.com/zh-TW/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)中已涵蓋在 AD 中設定 PDL 並同步處理的步驟。</span><span class="sxs-lookup"><span data-stu-id="f4412-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/zh-TW/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="f4412-p113">多地理位置租用戶的管理可能與非多地理位置租用戶不同，因為許多 SharePoint 和 OneDrive 設定與服務具有多地理位置意識。我們建議您檢閱[管理多地理位置環境](administering-a-multi-geo-environment.md)，再繼續進行您的組態。</span><span class="sxs-lookup"><span data-stu-id="f4412-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="f4412-171">閱讀[多地理位置環境中的使用者體驗](multi-geo-user-experience.md)，以了解多地理環境中的使用者體驗之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f4412-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="f4412-172">若要開始設定商務用 OneDrive 多地理位置，請參閱[設定商務用 OneDrive 多地理位置](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="f4412-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="f4412-173">當您完成設定時，請視需要記得[移轉使用者的 OneDrive 文件庫](move-onedrive-between-geo-locations.md)，以讓使用者可從自己的慣用資料位置來工作。</span><span class="sxs-lookup"><span data-stu-id="f4412-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
