---
title: 商務用 OneDrive 多地理位置租用戶設定
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 了解如何設定商務用 OneDrive 多地理位置。
ms.openlocfilehash: f521470b024817bbe53bbf3cbb1dd81e2a4a6754
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200702"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="d9303-103">商務用 OneDrive 多地理位置租用戶設定</span><span class="sxs-lookup"><span data-stu-id="d9303-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="d9303-p101">在您為商務用 OneDrive 多地理位置設定租用戶之前，請務必先閱讀[規劃商務用 OneDrive 多地理位置](plan-for-multi-geo.md)。若要按照本文所述步驟，您需要一份要啟用為衛星位置的地理位置，以及要為那些位置佈建的測試使用者清單。</span><span class="sxs-lookup"><span data-stu-id="d9303-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="d9303-106">將 Office 365 方案中的多地理位置功能新增到您的租用戶</span><span class="sxs-lookup"><span data-stu-id="d9303-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="d9303-p102">若要使用商務用 OneDrive 多地理位置，您需要 _Office 365 的多地理位置功能_方案。與帳戶團隊合作，將此方案新增到租用戶。您的帳戶團隊會向您引薦適當的授權專家，並設定您的租用戶。</span><span class="sxs-lookup"><span data-stu-id="d9303-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="d9303-p103">請注意，_Office 365 的多地理位置功能_方案是使用者層級的服務方案。您需要有要在衛星位置中裝載之每個使用者的授權。隨著您在衛星位置中新增使用者，您可以逐漸新增更多授權。</span><span class="sxs-lookup"><span data-stu-id="d9303-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="d9303-113">在租用戶佈建 _Office 365 的多地理位置功能_方案後，[OneDrive 系統管理中心](https://admin.onedrive.com)的 [地理位置]\*\*\*\* 索引標籤即變成可用。</span><span class="sxs-lookup"><span data-stu-id="d9303-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="d9303-114">將衛星位置新增至您的租用戶</span><span class="sxs-lookup"><span data-stu-id="d9303-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="d9303-p104">您必須針對要使用商務用 OneDrive 的每個地理位置新增衛星位置。下表顯示可用的地理位置：</span><span class="sxs-lookup"><span data-stu-id="d9303-p104">You must add a satellite location for each geo location where you want to use OneDrive for Business. Available geo locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d9303-117"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="d9303-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="d9303-118"><strong>代碼</strong></span><span class="sxs-lookup"><span data-stu-id="d9303-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d9303-119">亞太地區</span><span class="sxs-lookup"><span data-stu-id="d9303-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="d9303-120">APC</span><span class="sxs-lookup"><span data-stu-id="d9303-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9303-121">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="d9303-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="d9303-122">AUS</span><span class="sxs-lookup"><span data-stu-id="d9303-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9303-123">加拿大</span><span class="sxs-lookup"><span data-stu-id="d9303-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="d9303-124">CAN</span><span class="sxs-lookup"><span data-stu-id="d9303-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9303-125">歐洲/中東/非洲</span><span class="sxs-lookup"><span data-stu-id="d9303-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="d9303-126">EUR</span><span class="sxs-lookup"><span data-stu-id="d9303-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9303-127">法國</span><span class="sxs-lookup"><span data-stu-id="d9303-127">France</span></span></td>
<td align="left"><span data-ttu-id="d9303-128">FRA</span><span class="sxs-lookup"><span data-stu-id="d9303-128">FRA</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9303-129">印度</span><span class="sxs-lookup"><span data-stu-id="d9303-129">India</span></span></td>
<td align="left"><span data-ttu-id="d9303-130">IND</span><span class="sxs-lookup"><span data-stu-id="d9303-130">IND</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d9303-131">日本</span><span class="sxs-lookup"><span data-stu-id="d9303-131">Japan</span></span></td>
<td align="left"><span data-ttu-id="d9303-132">JPN</span><span class="sxs-lookup"><span data-stu-id="d9303-132">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d9303-133">韓國</span><span class="sxs-lookup"><span data-stu-id="d9303-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="d9303-134">KOR</span><span class="sxs-lookup"><span data-stu-id="d9303-134">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d9303-135">北美洲</span><span class="sxs-lookup"><span data-stu-id="d9303-135">North America</span></span></td>
<td align="left"><span data-ttu-id="d9303-136">NAM</span><span class="sxs-lookup"><span data-stu-id="d9303-136">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d9303-137">英國</span><span class="sxs-lookup"><span data-stu-id="d9303-137">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="d9303-138">GBR</span><span class="sxs-lookup"><span data-stu-id="d9303-138">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d9303-139">新增衛星位置</span><span class="sxs-lookup"><span data-stu-id="d9303-139">To add a satellite location</span></span>

1. <span data-ttu-id="d9303-140">開啟 [OneDrive 系統管理中心](https://admin.onedrive.com)。</span><span class="sxs-lookup"><span data-stu-id="d9303-140">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="d9303-141">瀏覽至 [地理位置]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d9303-141">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="d9303-142">按一下 [新增位置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9303-142">Click **Add location**.</span></span>

4. <span data-ttu-id="d9303-143">選取您要新增的位置，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9303-143">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="d9303-144">輸入您要搭配地理位置使用的網域，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9303-144">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="d9303-145">按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9303-145">Click **Close**.</span></span>

<span data-ttu-id="d9303-p105">佈建可能需要幾小時，最多 72 小時，視租用戶大小而定。衛星位置的佈建完成後，您將會收到電子郵件確認。當新的地理位置在 OneDrive 系統管理中心的 [**地理位置**] 索引標籤上以藍色顯示在地圖上，您就可以繼續將使用者慣用的資料位置設定到該地理位置。</span><span class="sxs-lookup"><span data-stu-id="d9303-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d9303-p106">您的新衛星位置將會以預設設定進行設定。這可讓您依當地合規性需求來設定該衛星位置。</span><span class="sxs-lookup"><span data-stu-id="d9303-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="d9303-151">設定使用者的慣用資料位置</span><span class="sxs-lookup"><span data-stu-id="d9303-151">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="d9303-p107">一旦啟用所需的衛星位置，您就可以更新使用者帳戶以使用適當的慣用資料位置。建議您為每個使用者設定慣用的資料位置，即使該使用者會停留在中央位置。</span><span class="sxs-lookup"><span data-stu-id="d9303-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!TIP]
> <span data-ttu-id="d9303-154">建議您從測試使用者或一小群使用者開始驗證，再向整個組織推出多地理位置。</span><span class="sxs-lookup"><span data-stu-id="d9303-154">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="d9303-p108">AAD 中有兩種類型的使用者物件：雲端專用使用者及同步處理的使用者。請針對使用者類型遵從適當的指示。</span><span class="sxs-lookup"><span data-stu-id="d9303-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="d9303-157">使用 AD Connect 同步處理使用者的慣用資料位置</span><span class="sxs-lookup"><span data-stu-id="d9303-157">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="d9303-p109">如果貴公司的使用者已從內部部署 Active Directory 系統同步處理到 Azure Active Directory，其 PreferredDataLocation 必須在 AD 中填入，並同步處理到 AAD。請依照 [Azure Active Directory Connect 同步處理：設定 Office 365 資源的慣用資料位置](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)中的程序，設定從內部部署 Active Directory 將慣用的資料位置同步處理到 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="d9303-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="d9303-160">建議您將設定使用者的慣用資料位置納入標準使用者建立工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="d9303-160">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9303-p110">對於未佈建 OneDrive 的新使用者，在使用者的 PDL 同步處理到 Azure Active Directory 後，請等候至少 24 小時讓變更傳播，使用者才能登入商務用 OneDrive。(在使用者登入以佈建商務用 OneDrive 之前設定慣用資料位置，如此可確保使用者的新 OneDrive 會佈建在正確位置。)</span><span class="sxs-lookup"><span data-stu-id="d9303-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="d9303-163">為雲端專用使用者設定慣用的資料位置為雲端專用使用者設定慣用的資料位置</span><span class="sxs-lookup"><span data-stu-id="d9303-163">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="d9303-164">如果貴公司的使用者不是從內部部署 Active Directory 系統同步處理到 Azure Active Directory，這表示使用者是在 Office 365 或 Azure Active Directory 中建立，則必須使用 Azure Active Directory PowerShell 設定 PDL。</span><span class="sxs-lookup"><span data-stu-id="d9303-164">If your company’s users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="d9303-p111">本節的程序需要[適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果您已安裝 Azure Active Directory PowerShell，請確認您已更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="d9303-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="d9303-167">開啟適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="d9303-167">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="d9303-168">執行 `Connect-MsolService` 並輸入租用戶的全域系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="d9303-168">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="d9303-p112">使用 [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) Cmdlet 為每個使用者設定慣用資料位置。例如：</span><span class="sxs-lookup"><span data-stu-id="d9303-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="d9303-p113">您可以檢查以確認慣用的資料位置已使用 Get-MsolUser Cmdlet 正確更新。例如：</span><span class="sxs-lookup"><span data-stu-id="d9303-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="d9303-173">建議您將設定使用者的慣用資料位置納入標準使用者建立工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="d9303-173">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9303-p114">對於未佈建 OneDrive 的新使用者，在使用者的 PDL 設定好後，請等候至少 24 小時讓變更傳播，使用者才能登入 OneDrive。(在使用者登入以佈建商務用 OneDrive 之前設定慣用資料位置，如此可確保使用者的新 OneDrive 會佈建在正確位置。)</span><span class="sxs-lookup"><span data-stu-id="d9303-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="d9303-176">OneDrive 佈建及 PDL 的影響</span><span class="sxs-lookup"><span data-stu-id="d9303-176">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="d9303-p115">如果使用者已在租用戶中建立 OneDrive 網站，設定其 PDL 不會自動移動其現有的 OneDrive。若要移動使用者的 OneDrive，請參閱[商務用 OneDrive 異地移動](move-onedrive-between-geo-locations.md)，請按照「在地理位置之間移動 OneDrive」中的指示。</span><span class="sxs-lookup"><span data-stu-id="d9303-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="d9303-179">如果使用者在租用戶中沒有 OneDrive 網站，OneDrive 會根據其 PDL 值進行佈建，並假設使用者的 PDL 符合公司的其中一個衛星位置。</span><span class="sxs-lookup"><span data-stu-id="d9303-179">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="d9303-180">設定多地理位置搜尋</span><span class="sxs-lookup"><span data-stu-id="d9303-180">Configuring Multi-Geo search</span></span>

<span data-ttu-id="d9303-181">多地理位置租用戶具有彙總搜尋功能，可讓搜尋查詢從租用戶中的任何位置傳回結果。</span><span class="sxs-lookup"><span data-stu-id="d9303-181">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="d9303-182">根據預設，從這些進入點搜尋會傳回彙總的結果，即使每個搜尋索引都位於其相關的地理位置內：</span><span class="sxs-lookup"><span data-stu-id="d9303-182">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="d9303-183">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="d9303-183">OneDrive for business</span></span>

- <span data-ttu-id="d9303-184">Delve</span><span class="sxs-lookup"><span data-stu-id="d9303-184">Delve</span></span>

- <span data-ttu-id="d9303-185">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="d9303-185">SharePoint Home</span></span>

- <span data-ttu-id="d9303-186">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="d9303-186">Search Center</span></span>

<span data-ttu-id="d9303-187">此外，多地理位置搜尋功能可針對使用 SharePoint 搜尋 API 的自訂搜尋應用程式進行設定。</span><span class="sxs-lookup"><span data-stu-id="d9303-187">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="d9303-188">請檢閱[為商務用 OneDrive 多地理位置設定搜尋](configure-search-for-multi-geo.md)以取得相關指示，包括任何限制與差異。</span><span class="sxs-lookup"><span data-stu-id="d9303-188">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="d9303-189">驗證商務用 OneDrive 多地理位置設定</span><span class="sxs-lookup"><span data-stu-id="d9303-189">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="d9303-p116">以下是一些基本使用案例，在向公司廣泛推出商務用 OneDrive 多地理位置之前，您可能會想將其納入驗證規劃。完成這些測試以及與貴公司相關的任何其他使用案例後，您可以選擇繼續在初始試驗群組中新增使用者。</span><span class="sxs-lookup"><span data-stu-id="d9303-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="d9303-192">**商務用 OneDrive**</span><span class="sxs-lookup"><span data-stu-id="d9303-192">**OneDrive for Business**</span></span>

<span data-ttu-id="d9303-p117">從 Office 365 應用程式啟動器選取 OneDrive，並確認系統自動根據使用者的 PDL 將您導向至使用者的適當地理位置。商務用 OneDrive 現在應於該位置開始佈建。佈建後，請嘗試上傳和下載一些文件。</span><span class="sxs-lookup"><span data-stu-id="d9303-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="d9303-196">**OneDrive 行動應用程式**</span><span class="sxs-lookup"><span data-stu-id="d9303-196">**OneDrive Mobile App**</span></span>

<span data-ttu-id="d9303-p118">以測試帳戶認證登入 OneDrive 行動應用程式。確認您可以看到您的商務用 OneDrive 檔案，並可從行動裝置與檔案互動。</span><span class="sxs-lookup"><span data-stu-id="d9303-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="d9303-199">**OneDrive 同步處理用戶端**</span><span class="sxs-lookup"><span data-stu-id="d9303-199">**OneDrive sync client**</span></span>

<span data-ttu-id="d9303-p119">確認 OneDrive 同步處理用戶端會在登入時自動偵測商務用 OneDrive 的地理位置。如果您要下載同步處理用戶端，請按一下 OneDrive 文件庫中的 [**同步處理**]。</span><span class="sxs-lookup"><span data-stu-id="d9303-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="d9303-202">**Office 應用程式**</span><span class="sxs-lookup"><span data-stu-id="d9303-202">**Office applications**</span></span>

<span data-ttu-id="d9303-p120">請確認您可以從 Office 應用程式 (如 Word) 登入，以存取商務用 OneDrive。開啟 Office 應用程式並選取 [OneDrive – <TenantName>]。Office 會偵測您的 OneDrive 位置，並顯示您可以開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="d9303-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="d9303-206">**共用**</span><span class="sxs-lookup"><span data-stu-id="d9303-206">**Sharing**</span></span>

<span data-ttu-id="d9303-p121">嘗試共用 OneDrive 檔案。確認人員選擇器顯示您的所有 SharePoint 線上使用者，無論其地理位置為何。</span><span class="sxs-lookup"><span data-stu-id="d9303-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
