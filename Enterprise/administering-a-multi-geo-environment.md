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
# <a name="administering-a-multi-geo-environment"></a>管理多個地理位置環境

以下是認識 OneDrive 及 SharePoint 服務在多個地理位置環境中的運作方式。

#### <a name="onedrive-administrator-experience"></a>OneDrive 管理員體驗

[OneDrive 系統管理中心](https://admin.onedrive.com)有哪些功能地理位置對應您可以在其中檢視並管理您的地理位置的左方導覽中的**地理位置**] 索引標籤。使用此頁面來新增或刪除您的租用戶的地理位置。

#### <a name="taxonomy"></a>分類

我們支援整合的[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)為企業受管理的中繼資料所有地理位置之間有受託管在您的公司的集中位置中的主圖形。我們建議您從集中管理位置管理通用的分類並只將特定位置的字詞新增至衛星地理位置的分類。通用分類字詞會同步處理至衛星地理位置。

#### <a name="sharing"></a>共用

系統管理員可以設定和管理共用原則的每個其位置。在每個地理位置中的 OneDrive 網站會受限於只能對應地理特定共用設定。例如，您可以讓[外部共用](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)您的集中位置，但並非針對您衛星位置，反之亦然。針對 OneDrive 多-地理位置，必須為這些不同步整個承租人管理您在每個地理位置的共用設定。

若要管理共用造訪[OneDrive 系統管理中心共用設定](https://admin.onedrive.com/?v=SharingSettings)] 頁面。外部共用預設會使用每個衛星位置中的任何人啟用。

#### <a name="user-profile-application"></a>使用者設定檔應用程式

每個地理位置中有[使用者設定檔應用程式](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。每位使用者的設定檔資訊被架設在其地理位置且可供該地理位置的管理員。

如果您有自訂設定檔屬性，則建議您地理位置都使用相同的設定檔結構描述及填入您的自訂設定檔屬性在所有地理位置中或在需要時。

#### <a name="bcs-secure-store-apps"></a>BCS、 安全認證儲存應用程式

BCS、 Secure Store 和應用程式所有具有不同地理位置執行個體，因此 SharePoint Online 系統管理員應該管理和設定這些服務從他們想它們存在每個地理位置執行個體。

#### <a name="security-and-compliance-admin-center"></a>安全性及規範系統管理中心

有多個地理位置租用戶的一個中央規範中心： [Office 365 的安全性與規範中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>資訊保護 (IP) 資料外洩防護 (DLP) 原則

您可以設定 IP DLP 原則 OneDrive for Business 的安全性和規範中心，視整個承租人或適用於使用者範圍設定的原則。例如： 如果您想要在衛星位置中選取 OneDrive 使用者原則，請選取這個選項可將原則套用至特定 OneDrive 並輸入使用者的 OneDrive url。請參閱[Overview of 資料外洩防護原則](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)建立 DLP 原則的一般指引。

DLP 原則會自動同步處理根據其適用性至每個地理位置。

實作地理位置中的所有使用者的資訊保護和資料遺失防護原則不是在 UI 中可用的選項，而是必須選取適用 OneDrive 帳戶原則或全域原則套用至所有 OneDrive 帳戶。

#### <a name="ediscovery"></a>eDiscovery 

根據預設，eDiscovery 管理員或多個地理位置租用戶的系統管理員將能夠進行 eDiscovery 只能在該租用戶的集中位置。若要支援進行 eDiscovery 衛星位置的能力，稱為"Region"的新規範安全性篩選參數是可透過 PowerShell。

Office 365 全域管理員必須指派 eDiscovery 管理員權限] 允許其他人來執行 eDiscovery 和指派"Region"參數中指定區域進行 eDiscovery 衛星為其適用規範安全性篩選位置，否則不 eDiscovery 可實現衛星位置。

EDiscovery 管理員或系統管理員角色的特定地理位置的設定時，eDiscovery 管理員或系統管理員將只能夠執行根據 SharePoint 網站和 OneDrive 網站位在該地理位置的 eDiscovery 搜尋動作。如果 eDiscovery 管理員或系統管理員嘗試搜尋 SharePoint 或 OneDrive 網站外的指定區域，將會不傳回任何結果。此外，當區域 eDiscovery 管理員或系統管理員會觸發匯出、 資料匯出至該區域的 Azure 執行個體。這可幫助組織掌握規範中不允許匯出控制框線之間的內容。

> [!NOTE]
> 如果時所需的 eDiscovery 來搜尋跨多個 SharePoint 區域的管理員，另一個使用者帳戶必須要建立 ediscovery 管理員指定 OneDrive 或 SharePoint 網站的所在位置的其他區域。

<table>
<thead>
<tr class="header">
<th align="left"><strong>多個地理位置支援地理位置</strong></th>
<th align="left"><strong>在此 Azure Blob 資料位置將 eDiscovery for SharePoint 匯出資料...]</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>名稱</strong></td>
<td align="left">US 資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">歐洲資料中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">南東或東亞洲資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>可以</strong></td>
<td align="left">US 資料中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>澳洲</strong></td>
<td align="left">南東或東亞洲資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>韓文</strong></td>
<td align="left">用戶預設資料位置</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">歐洲資料中心</td>
</tr>
<tr class="even">
<td align="left"><strong>日文</strong></td>
<td align="left">南東或東亞洲資料中心</td>
</tr>
</tbody>
</table>

若要設定規範安全性篩選區域：

1.  開啟 Windows PowerShell

2.  Enter 鍵  
    $s = 新增 PSSession ConfigurationName Microsoft.Exchange-來指定 ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -認證 $cred-基本驗證 AllowRedirection-SessionOption (新增 PSSessionOption SkipCACheck-SkipCNCheck-SkipRevocationCheck)

    $ = Import-pssession $s AllowClobber  

3.  **新 ComplianceSecurityFilter****-動作**所有**-FilterName** EnterTheNameYouWantToAssign **-地區**EnterTheRegionParameter **-使用者**EnterTheUserPrincipalName

    例如：**新 ComplianceSecurityFilter-動作**所有**-FilterName** NAMEDISCOVERYMANAGERS **-地區**名稱**位使用者**adwood@contosodemosx.onmicrosoft.com

請參閱[新增 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)額外的參數和語法

#### <a name="audit-log-search"></a>稽核記錄檔搜尋

整合[稽核記錄](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)您的所有地理位置是可從 Office 365 都稽核記錄搜尋頁面。您可以看到所有稽核記錄項目從不同 geos、 例如在一個 org 檢視會顯示名稱為 EUR 地理使用者活動，然後適用於現有的篩選器以查看特定的使用者活動。
