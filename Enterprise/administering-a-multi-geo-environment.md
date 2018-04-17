---
title: 管理多個地理位置環境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何管理多個地理位置環境中的 SharePoint 和 OneDrive 服務。
ms.openlocfilehash: 5d423fedc25b6e58ee84a51b01eb3858e6f198bb
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="cd053-103">管理多個地理位置環境</span><span class="sxs-lookup"><span data-stu-id="cd053-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="cd053-104">以下是認識 OneDrive 及 SharePoint 服務在多個地理位置環境中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="cd053-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="cd053-105">OneDrive 管理員體驗</span><span class="sxs-lookup"><span data-stu-id="cd053-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="cd053-p101">[OneDrive 系統管理中心](https://admin.onedrive.com)有哪些功能地理位置對應您可以在其中檢視並管理您的地理位置的左方導覽中的**地理位置**] 索引標籤。使用此頁面來新增或刪除您的租用戶的地理位置。</span><span class="sxs-lookup"><span data-stu-id="cd053-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="cd053-108">分類</span><span class="sxs-lookup"><span data-stu-id="cd053-108">Taxonomy</span></span>

<span data-ttu-id="cd053-p102">我們支援整合的[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)為企業受管理的中繼資料所有地理位置之間有受託管在您的公司的集中位置中的主圖形。我們建議您從集中管理位置管理通用的分類並只將特定位置的字詞新增至衛星地理位置的分類。通用分類字詞會同步處理至衛星地理位置。</span><span class="sxs-lookup"><span data-stu-id="cd053-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="cd053-112">共用</span><span class="sxs-lookup"><span data-stu-id="cd053-112">Sharing</span></span>

<span data-ttu-id="cd053-p103">系統管理員可以設定和管理共用原則的每個其位置。在每個地理位置中的 OneDrive 網站會受限於只能對應地理特定共用設定。例如，您可以讓[外部共用](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)您的集中位置，但並非針對您衛星位置，反之亦然。針對 OneDrive 多-地理位置，必須為這些不同步整個承租人管理您在每個地理位置的共用設定。</span><span class="sxs-lookup"><span data-stu-id="cd053-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="cd053-p104">若要管理共用造訪[OneDrive 系統管理中心共用設定](https://admin.onedrive.com/?v=SharingSettings)] 頁面。外部共用預設會使用每個衛星位置中的任何人啟用。</span><span class="sxs-lookup"><span data-stu-id="cd053-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="cd053-119">使用者設定檔應用程式</span><span class="sxs-lookup"><span data-stu-id="cd053-119">User Profile Application</span></span>

<span data-ttu-id="cd053-p105">每個地理位置中有[使用者設定檔應用程式](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。每位使用者的設定檔資訊被架設在其地理位置且可供該地理位置的管理員。</span><span class="sxs-lookup"><span data-stu-id="cd053-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="cd053-122">如果您有自訂設定檔屬性，則建議您地理位置都使用相同的設定檔結構描述及填入您的自訂設定檔屬性在所有地理位置中或在需要時。</span><span class="sxs-lookup"><span data-stu-id="cd053-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="cd053-123">BCS、 安全認證儲存應用程式</span><span class="sxs-lookup"><span data-stu-id="cd053-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="cd053-124">BCS、 Secure Store 和應用程式所有具有不同地理位置執行個體，因此 SharePoint Online 系統管理員應該管理和設定這些服務從他們想它們存在每個地理位置執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd053-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="cd053-125">安全性及規範系統管理中心</span><span class="sxs-lookup"><span data-stu-id="cd053-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="cd053-126">有多個地理位置租用戶的一個中央規範中心： [Office 365 的安全性與規範中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。</span><span class="sxs-lookup"><span data-stu-id="cd053-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="cd053-127">資訊保護 (IP) 資料外洩防護 (DLP) 原則</span><span class="sxs-lookup"><span data-stu-id="cd053-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="cd053-p106">您可以設定 IP DLP 原則 OneDrive for Business 的安全性和規範中心，視整個承租人或適用於使用者範圍設定的原則。例如： 如果您想要在衛星位置中選取 OneDrive 使用者原則，請選取這個選項可將原則套用至特定 OneDrive 並輸入使用者的 OneDrive url。請參閱[Overview of 資料外洩防護原則](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)建立 DLP 原則的一般指引。</span><span class="sxs-lookup"><span data-stu-id="cd053-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="cd053-131">DLP 原則會自動同步處理根據其適用性至每個地理位置。</span><span class="sxs-lookup"><span data-stu-id="cd053-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="cd053-132">實作地理位置中的所有使用者的資訊保護和資料遺失防護原則不是在 UI 中可用的選項，而是必須選取適用 OneDrive 帳戶原則或全域原則套用至所有 OneDrive 帳戶。</span><span class="sxs-lookup"><span data-stu-id="cd053-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="cd053-133">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="cd053-133">eDiscovery</span></span> 

<span data-ttu-id="cd053-p107">根據預設，eDiscovery 管理員或多個地理位置租用戶的系統管理員將能夠進行 eDiscovery 只能在該租用戶的集中位置。若要支援進行 eDiscovery 衛星位置的能力，稱為"Region"的新規範安全性篩選參數是可透過 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cd053-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="cd053-136">Office 365 全域管理員必須指派 eDiscovery 管理員權限] 允許其他人來執行 eDiscovery 和指派"Region"參數中指定區域進行 eDiscovery 衛星為其適用規範安全性篩選位置，否則不 eDiscovery 可實現衛星位置。</span><span class="sxs-lookup"><span data-stu-id="cd053-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="cd053-p108">EDiscovery 管理員或系統管理員角色的特定地理位置的設定時，eDiscovery 管理員或系統管理員將只能夠執行根據 SharePoint 網站和 OneDrive 網站位在該地理位置的 eDiscovery 搜尋動作。如果 eDiscovery 管理員或系統管理員嘗試搜尋 SharePoint 或 OneDrive 網站外的指定區域，將會不傳回任何結果。此外，當區域 eDiscovery 管理員或系統管理員會觸發匯出、 資料匯出至該區域的 Azure 執行個體。這可幫助組織掌握規範中不允許匯出控制框線之間的內容。</span><span class="sxs-lookup"><span data-stu-id="cd053-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="cd053-141">如果時所需的 eDiscovery 來搜尋跨多個 SharePoint 區域的管理員，另一個使用者帳戶必須要建立 ediscovery 管理員指定 OneDrive 或 SharePoint 網站的所在位置的其他區域。</span><span class="sxs-lookup"><span data-stu-id="cd053-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="cd053-142"><strong>多個地理位置支援地理位置</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="cd053-143"><strong>在此 Azure Blob 資料位置將 eDiscovery for SharePoint 匯出資料...]</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="cd053-144"><strong>名稱</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-145">US 資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cd053-146"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-147">歐洲資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cd053-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-149">南東或東亞洲資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cd053-150"><strong>可以</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-151">US 資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cd053-152"><strong>澳洲</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-153">南東或東亞洲資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cd053-154"><strong>韓文</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-155">用戶預設資料位置</span><span class="sxs-lookup"><span data-stu-id="cd053-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cd053-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-157">歐洲資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cd053-158"><strong>日文</strong></span><span class="sxs-lookup"><span data-stu-id="cd053-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="cd053-159">南東或東亞洲資料中心</span><span class="sxs-lookup"><span data-stu-id="cd053-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="cd053-160">若要設定規範安全性篩選區域：</span><span class="sxs-lookup"><span data-stu-id="cd053-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="cd053-161">開啟 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd053-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="cd053-162">Enter 鍵</span><span class="sxs-lookup"><span data-stu-id="cd053-162">Enter</span></span>  
    <span data-ttu-id="cd053-163">$s = 新增 PSSession ConfigurationName Microsoft.Exchange-來指定 ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -認證 $cred-基本驗證 AllowRedirection-SessionOption (新增 PSSessionOption SkipCACheck-SkipCNCheck-SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="cd053-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="cd053-164">$ = Import-pssession $s AllowClobber</span><span class="sxs-lookup"><span data-stu-id="cd053-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="cd053-165">**新 ComplianceSecurityFilter****-動作**所有**-FilterName** EnterTheNameYouWantToAssign **-地區**EnterTheRegionParameter **-使用者**EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="cd053-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="cd053-166">例如：**新 ComplianceSecurityFilter-動作**所有**-FilterName** NAMEDISCOVERYMANAGERS **-地區**名稱**位使用者**adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="cd053-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="cd053-167">請參閱[新增 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)額外的參數和語法</span><span class="sxs-lookup"><span data-stu-id="cd053-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="cd053-168">稽核記錄檔搜尋</span><span class="sxs-lookup"><span data-stu-id="cd053-168">Audit log search</span></span>

<span data-ttu-id="cd053-p109">整合[稽核記錄](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)您的所有地理位置是可從 Office 365 都稽核記錄搜尋頁面。您可以看到所有稽核記錄項目從不同 geos、 例如在一個 org 檢視會顯示名稱為 EUR 地理使用者活動，然後適用於現有的篩選器以查看特定的使用者活動。</span><span class="sxs-lookup"><span data-stu-id="cd053-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
