---
title: 規劃 OneDrive for Business 多重地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解 OneDrive 商務多重地理位置、 多個地理位置的運作方式，且何種地理位置可供資料存放區。
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="a00d3-103">規劃 OneDrive for Business 多重地理位置</span><span class="sxs-lookup"><span data-stu-id="a00d3-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="a00d3-104">本指南旨在協助系統管理員的人員，供其準備其展開至 「 公司的平台服務以滿足資料 residency 需求的其他地理位置的 SharePoint Online 租用戶的多重國民公司 (MNCs)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="a00d3-p101">在 OneDrive 多重地理位置設定中，您的 Office 365 租用戶包含一個集中的位置 （也稱為預設位置） 和一或多個衛星地理位置。這是跨多個地理位置之間的單一租用戶。在 OneDrive 多-地理位置，您的租用戶資訊，包括地理位置對應中 Azure Active Directory (AAD)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="a00d3-108">以下是一些重要的多個地理位置詞彙協助您了解設定的基本概念：</span><span class="sxs-lookup"><span data-stu-id="a00d3-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="a00d3-109">**租用戶**– Office 365 雲端通常具有與它相關聯的一或多個網域中的組織的表示法 (例如http://contoso.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="a00d3-p102">**地理位置**– 主控您的租用戶資料的地理位置。多個地理位置承租人跨越多個地理位置，例如 「 北美地區 」 和 「 歐洲。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="a00d3-112">**允許資料位置 (ADL)** – 的租用戶已設定主機 OneDrive 及 SharePoint 資料的地理位置。</span><span class="sxs-lookup"><span data-stu-id="a00d3-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="a00d3-p103">**慣用的資料位置 (PDL)** -儲存個別使用者的 OneDrive 資料的地理位置。這可以是任何允許資料位置已設定為承租人管理員設定。請注意是否您變更 PDL 已經有 OneDrive 站台的使用者，他們 OneDrive 資料為未移至新的地理位置自動。如需詳細資訊，請參閱[移到不同地理位置的 OneDrive 文件庫](move-onedrive-between-geo-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="a00d3-117">啟用多個地理位置需要四個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="a00d3-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="a00d3-118">若要新增_多個地理位置功能的 Office 365_服務計劃帳戶小組與搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a00d3-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="a00d3-119">選擇您想要的衛星地理位置並將其新增至您的租用戶。</span><span class="sxs-lookup"><span data-stu-id="a00d3-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="a00d3-p104">設定使用者的偏好的資料位置所需的衛星地理位置。當新 OneDrive 網站佈建的使用者時，它已佈建至其 PDL。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="a00d3-122">使用者的現有 OneDrive 將網站移轉從首頁位置到視其偏好的資料位置。</span><span class="sxs-lookup"><span data-stu-id="a00d3-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="a00d3-123">請參閱[設定 OneDrive for Business 多-地理位置](multi-geo-tenant-configuration.md)的每個這些步驟的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a00d3-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a00d3-p105">請注意針對效能最佳化案例旨在不到 Office 365 的多重地理位置功能，其設計用來符合資料 residency 需求。如需效能最佳化 Office 365 的詳細資訊，請參閱[網路規劃和 Office 365 的效能調整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)或連絡支援群組。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="a00d3-p106">您可以設定任何要裝載 OneDrive 檔案的採衛星地理位置的下列位置。當您規劃多個地理位置，進行您想要新增至 Office 365 租用戶的位置清單。我們建議具有一或兩個衛星位置開始逐漸擴充到多個地理位置，視。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a00d3-129"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="a00d3-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="a00d3-130"><strong>程式碼</strong></span><span class="sxs-lookup"><span data-stu-id="a00d3-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="a00d3-131">亞太地區</span><span class="sxs-lookup"><span data-stu-id="a00d3-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="a00d3-132">APC</span><span class="sxs-lookup"><span data-stu-id="a00d3-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a00d3-133">歐洲 / 東部正 / 非洲</span><span class="sxs-lookup"><span data-stu-id="a00d3-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="a00d3-134">EUR</span><span class="sxs-lookup"><span data-stu-id="a00d3-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a00d3-135">北美</span><span class="sxs-lookup"><span data-stu-id="a00d3-135">North America</span></span></td>
<td align="left"><span data-ttu-id="a00d3-136">名稱</span><span class="sxs-lookup"><span data-stu-id="a00d3-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a00d3-137">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="a00d3-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="a00d3-138">澳洲</span><span class="sxs-lookup"><span data-stu-id="a00d3-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a00d3-139">加拿大</span><span class="sxs-lookup"><span data-stu-id="a00d3-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="a00d3-140">可以</span><span class="sxs-lookup"><span data-stu-id="a00d3-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a00d3-141">日本</span><span class="sxs-lookup"><span data-stu-id="a00d3-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="a00d3-142">日文</span><span class="sxs-lookup"><span data-stu-id="a00d3-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="a00d3-143">韓國</span><span class="sxs-lookup"><span data-stu-id="a00d3-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="a00d3-144">韓文</span><span class="sxs-lookup"><span data-stu-id="a00d3-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="a00d3-145">英國</span><span class="sxs-lookup"><span data-stu-id="a00d3-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="a00d3-146">GBR</span><span class="sxs-lookup"><span data-stu-id="a00d3-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="a00d3-147">即將推出的地理位置：</span><span class="sxs-lookup"><span data-stu-id="a00d3-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="a00d3-148">法國</span><span class="sxs-lookup"><span data-stu-id="a00d3-148">France</span></span>
- <span data-ttu-id="a00d3-149">印度</span><span class="sxs-lookup"><span data-stu-id="a00d3-149">India</span></span>

<span data-ttu-id="a00d3-p107">當您設定多個地理位置時，請考慮將您的內部部署基礎結構時移轉至 Office 365 機會。例如，如果您有內部部署伺服器陣列中新加坡和馬來西亞，然後您可以合併它們到 APC 衛星位置提供資料 residency 需求允許您這麼。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="a00d3-152">最佳做法</span><span class="sxs-lookup"><span data-stu-id="a00d3-152">Best practices</span></span>

<span data-ttu-id="a00d3-p108">我們建議您執行一些初始測試的 Office 365 中建立測試使用者。我們將逐步解說一些測試及驗證步驟與此使用者才可繼續進行內建的實際執行使用者到 OneDrive 多重地理位置功能。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="a00d3-p109">一旦您已經完成測試的測試使用者，選取試驗群組 – 或許從您的 IT 部門 – 設為使用 OneDrive 在新的地理位置中之第一個。這個第一個群組中，選取尚未沒有 OneDrive 的使用者。我們建議使用不得超過五個此初始群組中的人員以及逐步展開 [追蹤批次導入方法。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="a00d3-p110">每位使用者應可在*慣用的資料位置*(PDL) 設定可讓判斷 Office 365 中佈建其 OneDrive 的地理位置。使用者的偏好的資料位置必須符合其中一個您所選擇的衛星位置或您集中的位置。雖然 PDL 欄位不是必要的但是建議 PDL 為所有使用者的設定。在集中管理位置上的多個地理位置邏輯架構中佈建 PDL 沒有使用者的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="a00d3-p111">建立您的使用者清單，並包括其使用者主要名稱 (UPN) 與適當的慣用的資料位置的位置程式碼。開始使用包括測試使用者與您的初始試驗群組。如需設定程序需要此清單。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="a00d3-p112">如果您的使用者會從同步處理內部部署 Active Directory (AD) 系統以 Azure Active Directory (AAD)，您必須使用 Azure [Active Directory 連線設定同步處理使用者的偏好的資料位置。您無法直接設定使用 Azure AD PowerShell 的同步處理使用者的偏好的資料位置。在 AD PDL 設定並將它同步處理步驟涵蓋在[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="a00d3-p113">從非多重地理承租人，請為許多 SharePoint 和 OneDrive 設定而異的多個地理位置租用戶管理及服務的多個地理注意。我們建議您檢閱[管理多個地理位置環境](administering-a-multi-geo-environment.md)您才可以繼續使用您的設定。</span><span class="sxs-lookup"><span data-stu-id="a00d3-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="a00d3-170">如需在多個地理位置環境中的一般使用者經驗的詳細資訊，請閱讀[multgeo 環境中的使用者體驗](multi-geo-user-experience.md)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="a00d3-171">若要開始設定 OneDrive for Business 多-地理位置，請參閱 ＜[設定 OneDrive for Business 多-地理位置](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="a00d3-172">視要取得您的使用者使用其偏好的資料位置從一旦您已經完成設定，請記得移轉[使用者的 OneDrive 文件庫](move-onedrive-between-geo-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="a00d3-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
