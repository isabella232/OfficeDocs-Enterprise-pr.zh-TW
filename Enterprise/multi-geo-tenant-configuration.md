---
title: OneDrive for Business 多重地理租用戶組態
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何設定 OneDrive for Business 多-地理位置。
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="e12a8-103">OneDrive for Business 多重地理租用戶組態</span><span class="sxs-lookup"><span data-stu-id="e12a8-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="e12a8-p101">設定您的租用戶 onedrive for Business 多-地理位置之前，請確定您已閱讀[規劃 OneDrive for Business 多-地理位置](plan-for-multi-geo.md)。若要遵循本文中的步驟，您將需要您想要啟用的位置和測試使用者想要佈建那些位置的清單。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="e12a8-106">Office 365 計劃中的多個地理位置功能新增至您的租用戶</span><span class="sxs-lookup"><span data-stu-id="e12a8-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="e12a8-p102">若要使用 OneDrive for Business 多-地理位置，您需要_多個地理位置功能的 Office 365_計劃。若要將此計劃新增至您的租用戶帳戶小組與搭配使用。帳戶小組會與適當的授權專家連線並取得設定您的租用戶。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="e12a8-p103">請注意_Office 365 的多重地理位置功能_規劃使用者層級的服務計劃。您要主控衛星位置中每個使用者需要授權。您可以新增更多授權一段時間當您將使用者新增衛星位置中。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="e12a8-113">一旦_Office 365 的多重地理位置功能_計劃已佈建租用戶、**地理位置**] 索引標籤會變成可用[OneDrive 系統管理中心](https://admin.onedrive.com)。</span><span class="sxs-lookup"><span data-stu-id="e12a8-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="e12a8-114">設為您的租用戶的允許資料位置 (ADL)</span><span class="sxs-lookup"><span data-stu-id="e12a8-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="e12a8-p104">您必須將允許資料位置 SharePoint 的每個地理位置您想要用來使用 OneDrive for Business。下表顯示可用的地理位置：</span><span class="sxs-lookup"><span data-stu-id="e12a8-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e12a8-117"><strong>位置</strong></span><span class="sxs-lookup"><span data-stu-id="e12a8-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="e12a8-118"><strong>程式碼</strong></span><span class="sxs-lookup"><span data-stu-id="e12a8-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e12a8-119">北美</span><span class="sxs-lookup"><span data-stu-id="e12a8-119">North America</span></span></td>
<td align="left"><span data-ttu-id="e12a8-120">名稱</span><span class="sxs-lookup"><span data-stu-id="e12a8-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e12a8-121">歐洲 / 東部正 / 非洲</span><span class="sxs-lookup"><span data-stu-id="e12a8-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="e12a8-122">EUR</span><span class="sxs-lookup"><span data-stu-id="e12a8-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e12a8-123">亞太地區</span><span class="sxs-lookup"><span data-stu-id="e12a8-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="e12a8-124">APC</span><span class="sxs-lookup"><span data-stu-id="e12a8-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e12a8-125">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="e12a8-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="e12a8-126">澳洲</span><span class="sxs-lookup"><span data-stu-id="e12a8-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e12a8-127">日本</span><span class="sxs-lookup"><span data-stu-id="e12a8-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="e12a8-128">日文</span><span class="sxs-lookup"><span data-stu-id="e12a8-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e12a8-129">加拿大</span><span class="sxs-lookup"><span data-stu-id="e12a8-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="e12a8-130">可以</span><span class="sxs-lookup"><span data-stu-id="e12a8-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e12a8-131">英國</span><span class="sxs-lookup"><span data-stu-id="e12a8-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="e12a8-132">GBR</span><span class="sxs-lookup"><span data-stu-id="e12a8-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e12a8-133">韓國</span><span class="sxs-lookup"><span data-stu-id="e12a8-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="e12a8-134">韓文</span><span class="sxs-lookup"><span data-stu-id="e12a8-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="e12a8-135">若要新增衛星地理位置</span><span class="sxs-lookup"><span data-stu-id="e12a8-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="e12a8-136">開啟[OneDrive 系統管理中心](https://admin.onedrive.com)。</span><span class="sxs-lookup"><span data-stu-id="e12a8-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="e12a8-137">瀏覽至 [**地理位置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e12a8-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="e12a8-138">按一下 [**新增位置**。</span><span class="sxs-lookup"><span data-stu-id="e12a8-138">Click **Add location**.</span></span>

4. <span data-ttu-id="e12a8-139">選取您想要新增的位置，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="e12a8-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="e12a8-140">輸入您想要的地理位置，搭配使用的網域，然後按一下 [**新增**。</span><span class="sxs-lookup"><span data-stu-id="e12a8-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="e12a8-141">按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="e12a8-141">Click **Close**.</span></span>

<span data-ttu-id="e12a8-p105">佈建可能需要幾個小時從到 72 個小時，視您的租用戶的大小而定。衛星位置的佈建完成之後，您會收到電子郵件確認。當新的地理位置會出現在地圖上 OneDrive 系統管理中心的 [**地理位置**] 索引標籤上的藍色時，您可以繼續設定使用者的偏好的資料位置為該地理位置。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="e12a8-p106">新的衛星地理位置會設定為預設值。這可讓您設定最適合您的本機規範需求的地理位置。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="e12a8-147">設定使用者的偏好的資料位置</span><span class="sxs-lookup"><span data-stu-id="e12a8-147">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="e12a8-p107">一旦您啟用所需的資料位置，您可以更新您的使用者帳戶來使用適當的資料位置。我們建議您設定喜好的資料位置的每位使用者，即使該使用者停留在預設資料位置。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="e12a8-150">建議您驗證測試使用者或小群使用者開始之前您更廣泛的組織啟用多個地理位置功能。</span><span class="sxs-lookup"><span data-stu-id="e12a8-150">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="e12a8-p108">AAD 中有兩種類型的使用者物件： 雲端只有使用者和同步處理的使用者。請遵循適當的指示您類型的使用者。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="e12a8-153">同步處理使用者的慣用資料位置使用 AD 連線</span><span class="sxs-lookup"><span data-stu-id="e12a8-153">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="e12a8-p109">如果您的公司使用者從同步處理內部部署 Active Directory (AD) 系統以 Azure Active Directory (AAD)，必須已在 AD 中填入及同步處理至 AAD 其 PreferredDataLocation。請依照下列程序中的[Azure AD 連線同步處理： 變更預設的設定](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)設定喜好從資料位置同步處理內部部署 AD 以 AAD。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="e12a8-156">我們建議您將包括使用者的慣用資料位置設定為標準使用者建立工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="e12a8-156">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e12a8-p110">含有佈建沒有 OneDrive 的新使用者，等待至少 24 小時之後使用者 PDL 同步處理至 AAD 的變更傳播使用者登入到 OneDrive for Business 之前。（設定偏好的資料使用者登入到佈建其 OneDrive for Business 之前的位置可確保使用者的新 OneDrive 會在正確的位置來佈建。）</span><span class="sxs-lookup"><span data-stu-id="e12a8-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="e12a8-159">雲端的唯一使用者設定慣用資料位置</span><span class="sxs-lookup"><span data-stu-id="e12a8-159">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="e12a8-160">如果您的公司使用者不同步從內部部署 Active Directory (AD) 系統以 Azure Active Directory (AAD)，這表示他們所建立的 Office 365 或 AAD，然後 PDL 必須設定使用 AAD PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e12a8-160">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="e12a8-p111">本節中的程序需要[Microsoft Azure Active Directory Module for Windows PowerShell 模組](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果您已安裝的 AAD PowerShell，請確定您更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="e12a8-163">開啟 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="e12a8-163">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="e12a8-164">執行`Connect-MsolService`並輸入您的租用戶的全域系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="e12a8-164">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="e12a8-p112">使用[Set-msoluser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet 可設定每個使用者的偏好的資料位置。例如：</span><span class="sxs-lookup"><span data-stu-id="e12a8-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="e12a8-p113">您可以檢查以確認已使用 Get-msoluser cmdlet 正確更新慣用的資料的位置。例如：</span><span class="sxs-lookup"><span data-stu-id="e12a8-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="e12a8-169">我們建議您將包括使用者的慣用資料位置設定為標準使用者建立工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="e12a8-169">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e12a8-p114">含有佈建沒有 OneDrive 的新使用者，等待至少 24 小時之後的變更傳播之前使用者登入到 SharePoint OneDrive 設定使用者的 PDL。（設定偏好的資料使用者登入到佈建其 OneDrive for Business 之前的位置可確保使用者的新 OneDrive 會在正確的位置來佈建。）</span><span class="sxs-lookup"><span data-stu-id="e12a8-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="e12a8-172">OneDrive 佈建和 PDL 的影響</span><span class="sxs-lookup"><span data-stu-id="e12a8-172">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="e12a8-p115">如果使用者已有 OneDrive 站台的租用戶中建立、 設定其 PDL 不會自動將其現有 OneDrive。若要移動使用者的 OneDrive，請參閱[OneDrive for Business 地理位置移動](move-onedrive-between-geo-locations.md)請遵循地理位置之間的 [移動 OneDrive 中的指示。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="e12a8-175">如果使用者不具有 OneDrive 站台內的租用戶、 OneDrive 在佈建為根據其 PDL 值，假設使用者 PDL 符合其中一個公司的允許的資料位置 (ADLs)。</span><span class="sxs-lookup"><span data-stu-id="e12a8-175">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="e12a8-176">設定多個地理位置搜尋</span><span class="sxs-lookup"><span data-stu-id="e12a8-176">Configuring Multi-Geo search</span></span>

<span data-ttu-id="e12a8-177">您的多個地理位置租用戶會有彙總的搜尋功能讓搜尋查詢結果傳回從任何地方租用戶內。</span><span class="sxs-lookup"><span data-stu-id="e12a8-177">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="e12a8-178">根據預設，從下列進入點的搜尋會傳回彙總結果，即使其相關的地理位置中的每個搜尋索引所在：</span><span class="sxs-lookup"><span data-stu-id="e12a8-178">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="e12a8-179">OneDrive for business</span><span class="sxs-lookup"><span data-stu-id="e12a8-179">OneDrive for business</span></span>

- <span data-ttu-id="e12a8-180">Delve</span><span class="sxs-lookup"><span data-stu-id="e12a8-180">Delve</span></span>

- <span data-ttu-id="e12a8-181">SharePoint 首頁</span><span class="sxs-lookup"><span data-stu-id="e12a8-181">SharePoint Home</span></span>

- <span data-ttu-id="e12a8-182">搜尋中心</span><span class="sxs-lookup"><span data-stu-id="e12a8-182">Search Center</span></span>

<span data-ttu-id="e12a8-183">此外，可以設定多個地理位置的搜尋功能的自訂搜尋應用程式所使用的 SharePoint 搜尋 API。</span><span class="sxs-lookup"><span data-stu-id="e12a8-183">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="e12a8-184">請檢閱[設定搜尋 onedrive for Business 多-地理位置](configure-search-for-multi-geo.md)的指示包含任何限制和差異。</span><span class="sxs-lookup"><span data-stu-id="e12a8-184">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="e12a8-185">驗證 OneDrive for Business 多重地理位置設定</span><span class="sxs-lookup"><span data-stu-id="e12a8-185">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="e12a8-p116">以下是一些您可能會想要包含在您的驗證計劃之前廣泛推出 OneDrive for Business 多-地理位置為您的公司的基本使用情況。一旦您完成這些測試及相關貴公司任何其他的使用情況下，您可以選擇移至初始試驗群組中新增的使用者。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="e12a8-188">**OneDrive for Business**</span><span class="sxs-lookup"><span data-stu-id="e12a8-188">**OneDrive for Business**</span></span>

<span data-ttu-id="e12a8-p117">從 Office 365 應用程式啟動器選取 OneDrive 並確認您自動導向至適當使用者根據使用者的 PDL 的地理位置-位置。OneDrive for Business 現在應該開始佈建在該位置。一次已佈建的嘗試上傳及下載部分文件。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="e12a8-192">**OneDrive 行動應用程式**</span><span class="sxs-lookup"><span data-stu-id="e12a8-192">**OneDrive Mobile App**</span></span>

<span data-ttu-id="e12a8-p118">登入您的測試帳戶認證與您 OneDrive 行動裝置應用程式。確認您可以看到您 OneDrive for business 檔案可以從行動裝置的與其互動。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="e12a8-195">**OneDrive sync 用戶端**</span><span class="sxs-lookup"><span data-stu-id="e12a8-195">**OneDrive sync client**</span></span>

<span data-ttu-id="e12a8-p119">確認 OneDrive sync 用戶端會自動偵測將 OneDrive for Business 地理位置時登入。如果您需要下載 sync 用戶端，您可以按一下 [**同步處理**OneDrive 程式庫中。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="e12a8-198">**Office 應用程式**</span><span class="sxs-lookup"><span data-stu-id="e12a8-198">**Office applications**</span></span>

<span data-ttu-id="e12a8-p120">確認您可以存取 OneDrive for Business 的 Office 應用程式，如 Word 登入。開啟 Office 應用程式與 select"OneDrive – <TenantName>"。Office 會偵測您 OneDrive 位置，並顯示您可以開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="e12a8-202">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="e12a8-202">**Sharing**</span></span>

<span data-ttu-id="e12a8-p121">嘗試以共用 OneDrive 檔案。確認人員選擇] 顯示您所有的 SharePoint online 使用者不論其地理位置。</span><span class="sxs-lookup"><span data-stu-id="e12a8-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
