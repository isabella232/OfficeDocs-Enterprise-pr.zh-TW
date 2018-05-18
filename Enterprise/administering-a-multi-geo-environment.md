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
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>管理多地理位置環境

查看 OneDrive 和 SharePoint 服務在多地理位置環境中的運作方式。

#### <a name="onedrive-administrator-experience"></a>OneDrive 系統管理員體驗

[OneDrive 系統管理中心](https://admin.onedrive.com)在左側瀏覽中 (含有地理位置地圖) 具有 [地理位置]**** 索引標籤，您可以在其中檢視及管理您的地理位置。請使用此頁面來新增或刪除您的租用戶地理位置。

#### <a name="taxonomy"></a>分類

我們支援整合[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)，以用於跨地理位置中的企業管理中繼資料，內含在貴公司之中央位置中主控的主機。我們建議您從中央位置管理全域分類，並只將特定位置的詞彙新增至衛星地理位置。通用的分類詞彙會同步處理至衛星地理位置。

#### <a name="sharing"></a>共用

系統管理員可以為每個位置設定並管理共用的原則。每個地理位置中的 OneDrive 網站會接受僅與特定地理位置相對應的共用設定。(例如，您可以允許[外部共用](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)中央位置，但無法外部共用衛星位置 (反之亦然)。) 請注意，共用的設定不允許設定地理位置間的共用限制。

針對 OneDrive 多地理位置，您必須管理每個地理位置的共用設定，因為系統不會在租用戶間同步處理這些設定。若要管理共用，請造訪 [OneDrive 系統管理中心的共用設定] [](https://admin.onedrive.com/?v=SharingSettings)頁面。依預設，每個衛星位置中的任何人都能啟用外部共用。

#### <a name="user-profile-application"></a>使用者設定檔應用程式

在每個地理位置中有[使用者設定檔應用程式](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。系統會在每位使用者的地理位置主控其設定檔資訊，且該設定檔資料可供該地理位置的系統管理員使用。

如果您有自訂的設定檔屬性，則建議您使用跨地理位置的相同設定檔結構描述，然後在所有的地理位置或所需的位置填入自訂設定檔屬性。如需有關如何以程式設計方式填入使用者設定檔資料的指導方針，請參閱[大量使用者設定檔更新 API](https://docs.microsoft.com/zh-TW/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)

#### <a name="bcs-secure-store-apps"></a>BCS、Secure Store、應用程式

BCS、Secure Store 及應用程式都有個別的地理位置執行個體，因此 Sharepoint Online 系統管理員應從他們希望這些服務出現的每個地理執行個體中管理及設定這些服務。

#### <a name="security-and-compliance-admin-center"></a>安全性與合規性管理中心

有一個適用於多地理位置租用戶的中央合規性中心：[Office 365 安全性與合規性中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>資訊保護 (IP) 的資料外洩防護 (DLP) 原則

您可以在安全性與合規性中心中為商務用 OneDrive 設定您的 IP DLP 原則，將所需的原則範圍設為整個租用戶或適用的使用者。例如：如果您想要為衛星位置中的 OneDrive 使用者選取原則，選取以將原則套用至特定 OneDrive，然後輸入使用者的 OneDrive 的 Url。請參閱[資料外洩防護原則概觀](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)，以了解建立 DLP 原則的一般指導方針。

系統會根據 DLP 原則對每個地理位置的適用性來自動同步處理這些原則。

對某個地理位置中的所有使用者執行資訊保護和資料外洩防護原則，不是 UI 中的可用選項，您反而必須選取該原則適用的 OneDrive 帳戶，或將該原則全域套用至所有 OneDrive 帳戶。

#### <a name="ediscovery"></a>eDiscovery 

依預設，電子文件探索管理員或多地理位置租用戶的系統管理員僅能在該租用戶的中央位置中進行 eDiscovery。若要支援對衛星位置進行 eDiscovery 的能力，則可透過 PowerShell 取得名為「地區」的新合規性安全性篩選參數。

Office 365 全域系統管理員必須指派電子文件探索管理員權限，以允許其他人執行 eDiscovery，並在其適用的合規性安全性篩選中指派「地區」參數，以將進行 eDiscovery 的區域指定為衛星位置，否則將不會為該衛星位置執行任何 eDiscovery。

當為特定地理位置設定電子文件探索管理員或系統管理員角色時，電子文件探索管理員或系統管理員只能對位於該地理位置中的 SharePoint 網站和 OneDrive 網站執行 eDiscovery 搜尋動作。如果電子文件探索管理員或系統管理員嘗試搜尋指定範圍外的 SharePoint 或 OneDrive 網站，則不會傳回任何結果。此外，當某地區的電子文件探索管理員或系統管理員區域觸發匯出時，系統會將資料匯出至該區域的 Azure 執行個體。這可透過禁止匯出控制框線外的內容來協助組織保持合規。

> [!NOTE]
> 如果此對跨多個 SharePoint 區域的電子文件探索管理員是必要的，將必須為指定 OneDrive 或 SharePoint 網站所在位置之替代區域的電子文件探索管理員建立另一個使用者帳戶。

<table>
<thead>
<tr class="header">
<th align="left"><strong>多地理位置支援的地理位置</strong></th>
<th align="left"><strong>SharePoint 匯出資料的 eDiscovery 將會位於 Azure Blob 資料位置中…</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>北美洲</strong></td>
<td align="left">美國資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>歐洲</strong></td>
<td align="left">歐洲資料中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">東南亞或東亞資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>加拿大</strong></td>
<td align="left">美國資料中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>澳洲</strong></td>
<td align="left">東南亞或東亞資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>韓國</strong></td>
<td align="left">租用戶的預設資料位置</td>
</tr>
<tr class="odd">
<td align="left"><strong>英國</strong></td>
<td align="left">歐洲資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>日本</strong></td>
<td align="left">東南亞或東亞資料中心</td>
</tr>
</tbody>
</table>

若要為某地區設定合規性安全性篩選：

1.  開啟 [Windows PowerShell]。

2.  Enter 鍵  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

請參閱 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 一文以了解額外的參數和語法

#### <a name="audit-log-search"></a>稽核記錄檔搜尋

適用於所有地理位置的整合式[稽核記錄](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)可從 Office 365 稽核記錄搜尋頁面中取得。您可以看到跨地區的所有稽核記錄項目，例如，北美洲與歐洲地理使用者的活動會在一個組織視圖中顯示，然後您可以套用現有的篩選，以查看特定使用者的活動。
