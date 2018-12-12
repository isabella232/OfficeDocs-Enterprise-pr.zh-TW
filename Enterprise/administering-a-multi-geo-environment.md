---
title: 管理多地理位置環境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 深入了解在多地理位置環境中管理 SharePoint 和 OneDrive 服務。
ms.openlocfilehash: 09f8816fc0ba748ced5bd104710677829d893198
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200697"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="340cd-103">管理多地理位置環境</span><span class="sxs-lookup"><span data-stu-id="340cd-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="340cd-104">查看 OneDrive 和 SharePoint 服務在多地理位置環境中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="340cd-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="340cd-105">OneDrive 系統管理員體驗</span><span class="sxs-lookup"><span data-stu-id="340cd-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="340cd-p101">[OneDrive 系統管理中心](https://admin.onedrive.com)在左側瀏覽中 (含有地理位置地圖) 具有 [**地理位置**] 索引標籤，您可以在其中檢視及管理您的地理位置。請使用此頁面來新增或刪除您的租用戶地理位置。</span><span class="sxs-lookup"><span data-stu-id="340cd-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="340cd-108">分類</span><span class="sxs-lookup"><span data-stu-id="340cd-108">Taxonomy</span></span>

<span data-ttu-id="340cd-p102">我們支援整合[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)，以用於跨地理位置中的企業管理中繼資料，內含在貴公司之中央位置中主控的主機。我們建議您從中央位置管理全域分類，並只將特定位置的詞彙新增至衛星位置。通用的分類詞彙會同步處理至衛星位置。</span><span class="sxs-lookup"><span data-stu-id="340cd-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite location’s Taxonomy. Global taxonomy terms will synchronize to the satellite locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="340cd-112">共用</span><span class="sxs-lookup"><span data-stu-id="340cd-112">Sharing</span></span>

<span data-ttu-id="340cd-p103">系統管理員可以為每個位置設定並管理共用的原則。每個地理位置中的 OneDrive 網站會接受僅與特定地理位置相對應的共用設定。(例如，您可以允許[外部共用](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)中央位置，但無法外部共用衛星位置 (反之亦然)。) 請注意，共用的設定不允許設定地理位置間的共用限制。</span><span class="sxs-lookup"><span data-stu-id="340cd-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo locations.</span></span>

<span data-ttu-id="340cd-p104">針對 OneDrive 多地理位置，您必須管理每個地理位置的共用設定，因為系統不會在租用戶間同步處理這些設定。若要管理共用，請造訪 [OneDrive 系統管理中心的共用設定] [](https://admin.onedrive.com/?v=SharingSettings)頁面。依預設，每個衛星位置中的任何人都能啟用外部共用。</span><span class="sxs-lookup"><span data-stu-id="340cd-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="340cd-119">使用者設定檔應用程式</span><span class="sxs-lookup"><span data-stu-id="340cd-119">User Profile Application</span></span>

<span data-ttu-id="340cd-p105">在每個地理位置中有[使用者設定檔應用程式](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。系統會在每位使用者的地理位置主控其設定檔資訊，且該設定檔資料可供該地理位置的系統管理員使用。</span><span class="sxs-lookup"><span data-stu-id="340cd-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="340cd-p106">如果您有自訂的設定檔屬性，則建議您使用跨地理位置的相同設定檔結構描述，然後在所有的地理位置或所需的位置填入自訂設定檔屬性。如需有關如何以程式設計方式填入使用者設定檔資料的指導方針，請參閱[大量使用者設定檔更新 API](https://docs.microsoft.com/zh-TW/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span><span class="sxs-lookup"><span data-stu-id="340cd-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/zh-TW/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="340cd-124">BCS、Secure Store、應用程式</span><span class="sxs-lookup"><span data-stu-id="340cd-124">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="340cd-125">BCS、Secure Store 及應用程式在每個衛星位置中都有個別的執行個體，因此 Sharepoint Online 系統管理員應該從每個衛星位置中個別管理及設定這些服務。</span><span class="sxs-lookup"><span data-stu-id="340cd-125">BCS, Secure Store, and Apps all have separate instances in each satellite location, therefore the SharePoint Online administrator should manage and configure these services separately from each satellite location.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="340cd-126">安全性與合規性管理中心</span><span class="sxs-lookup"><span data-stu-id="340cd-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="340cd-127">有一個適用於多地理位置租用戶的中央合規性中心：[Office 365 安全性與合規性中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。</span><span class="sxs-lookup"><span data-stu-id="340cd-127">There is one central compliance center for a multi-geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="340cd-128">資訊保護 (IP) 的資料外洩防護 (DLP) 原則</span><span class="sxs-lookup"><span data-stu-id="340cd-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="340cd-p107">您可以在安全性與合規性中心中為商務用 OneDrive 設定您的 IP DLP 原則，將所需的原則範圍設為整個租用戶或適用的使用者。例如：如果您想要為衛星位置中的 OneDrive 使用者選取原則，選取以將原則套用至特定 OneDrive，然後輸入使用者的 OneDrive 的 Url。請參閱[資料外洩防護原則概觀](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)，以了解建立 DLP 原則的一般指導方針。</span><span class="sxs-lookup"><span data-stu-id="340cd-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="340cd-132">系統會根據 DLP 原則對每個地理位置的適用性來自動同步處理這些原則。</span><span class="sxs-lookup"><span data-stu-id="340cd-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="340cd-133">對某個地理位置中的所有使用者執行資訊保護和資料外洩防護原則，不是 UI 中的可用選項，您反而必須選取該原則適用的 OneDrive 帳戶，或將該原則全域套用至所有 OneDrive 帳戶。</span><span class="sxs-lookup"><span data-stu-id="340cd-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="340cd-134">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="340cd-134">eDiscovery</span></span> 

<span data-ttu-id="340cd-p108">依預設，電子文件探索管理員或多地理位置租用戶的系統管理員僅能在該租用戶的中央位置中進行 eDiscovery。若要支援對衛星位置進行 eDiscovery 的能力，則可透過 PowerShell 取得名為「地區」的新合規性安全性篩選參數。</span><span class="sxs-lookup"><span data-stu-id="340cd-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="340cd-137">Office 365 全域系統管理員必須指派電子文件探索管理員權限，以允許其他人執行 eDiscovery，並在其適用的合規性安全性篩選中指派「地區」參數，以將進行 eDiscovery 的區域指定為衛星位置，否則將不會為該衛星位置執行任何 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="340cd-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="340cd-p109">當為特定衛星位置設定電子文件探索管理員或系統管理員角色時，電子文件探索管理員或系統管理員只能對位於該衛星位置中的 SharePoint 網站和 OneDrive 網站執行 eDiscovery 搜尋動作。如果電子文件探索管理員或系統管理員嘗試搜尋指定的衛星位置外的 SharePoint 或 OneDrive 網站，則不會傳回任何結果。此外，當某衛星位置的電子文件探索管理員或系統管理員區域觸發匯出時，系統會將資料匯出至該區域的 Azure 執行個體。這可透過禁止匯出控制框線外的內容來協助組織保持合規。</span><span class="sxs-lookup"><span data-stu-id="340cd-p109">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="340cd-142">如果此對跨多個 SharePoint 衛星位置的電子文件探索管理員是必要的，將必須為指定 OneDrive 或 SharePoint 網站所在位置之替代衛星位置的電子文件探索管理員建立另一個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="340cd-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="340cd-143"><strong>多地理位置支援的地理位置</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="340cd-144"><strong>SharePoint 匯出資料的 eDiscovery 將會位於 Azure Blob 資料位置中…</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="340cd-145"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-145"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-146">東南亞或東亞資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-146">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="340cd-147"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-147"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-148">東南亞或東亞資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-148">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="340cd-149"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-149"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-150">美國資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-150">US datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="340cd-151"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-151"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-152">歐洲資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-152">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="340cd-153"><strong>FRA</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-153"><strong>FRA</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-154">歐洲資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-154">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="340cd-155"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-155"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-156">歐洲資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-156">Europe datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="340cd-157"><strong>IND</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-157"><strong>IND</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-158">東南亞或東亞資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-158">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="340cd-159"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-159"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-160">東南亞或東亞資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-160">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="340cd-161"><strong>JPN</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-161"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-162">東南亞或東亞資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-162">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="340cd-163"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="340cd-163"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="340cd-164">美國資料中心</span><span class="sxs-lookup"><span data-stu-id="340cd-164">US datacenters</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="340cd-165">若要為某地區設定合規性安全性篩選：</span><span class="sxs-lookup"><span data-stu-id="340cd-165">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="340cd-166">開啟 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="340cd-166">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="340cd-167">Enter 鍵</span><span class="sxs-lookup"><span data-stu-id="340cd-167">Enter</span></span>  
    <span data-ttu-id="340cd-168">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="340cd-168">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="340cd-169">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="340cd-169">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="340cd-170">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="340cd-170">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="340cd-171">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="340cd-171">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="340cd-172">請參閱 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 一文以了解額外的參數和語法</span><span class="sxs-lookup"><span data-stu-id="340cd-172">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="340cd-173">稽核記錄檔搜尋</span><span class="sxs-lookup"><span data-stu-id="340cd-173">Audit log search</span></span>

<span data-ttu-id="340cd-p110">適用於所有衛星位置的整合式[稽核記錄](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)可從 Office 365 稽核記錄搜尋頁面中取得。您可以看到跨地區的所有稽核記錄項目，例如，北美洲與歐洲地理使用者的活動會在一個組織視圖中顯示，然後您可以套用現有的篩選，以查看特定使用者的活動。</span><span class="sxs-lookup"><span data-stu-id="340cd-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your satellite locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
