---
title: 商務用 OneDrive 多地理位置租用戶設定
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 了解如何設定商務用 OneDrive 多地理位置。
ms.openlocfilehash: 1817eee1bb2ceefa0e2e167e327af417dd0c517d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915248"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>商務用 OneDrive 多地理位置租用戶設定

在您為商務用 OneDrive 多地理位置設定租用戶之前，請務必先閱讀[規劃商務用 OneDrive 多地理位置](plan-for-multi-geo.md)。若要按照本文所述步驟，您需要一份要啟用的位置，以及要為那些位置佈建的測試使用者清單。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>將 Office 365 方案中的多地理位置功能新增到您的租用戶

若要使用商務用 OneDrive 多地理位置，您需要 _Office 365 的多地理位置功能_方案。與帳戶團隊合作，將此方案新增到租用戶。您的帳戶團隊會向您引薦適當的授權專家，並設定您的租用戶。

請注意，_Office 365 的多地理位置功能_方案是使用者層級的服務方案。您需要有要在衛星位置中裝載之每個使用者的授權。隨著您在衛星位置中新增使用者，您可以逐漸新增更多授權。

在租用戶佈建 _Office 365 的多地理位置功能_方案後，[OneDrive 系統管理中心](https://admin.onedrive.com)的 [地理位置]**** 索引標籤即變成可用。

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>設定租用戶允許的資料位置 (ADL)

您必須針對要使用商務用 OneDrive 的每個地理位置設定 SharePoint 允許的資料位置。下表顯示可用的地理位置：

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>代碼</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">亞太地區</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">澳大利亞</td>
<td align="left">AUS</td>
</tr>
<tr class="even">
<td align="left">加拿大</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">歐洲/中東/非洲</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
<td align="left">法國</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">韓國</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">北美洲</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">英國</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

新增衛星地理位置

1. 開啟 [OneDrive 系統管理中心](https://admin.onedrive.com)。

2. 瀏覽至 [地理位置]**** 索引標籤。

3. 按一下 [新增位置]****。

4. 選取您要新增的位置，然後按一下 [下一步]****。

5. 輸入您要搭配地理位置使用的網域，然後按一下 [新增]****。

6. 按一下 [關閉]****。

佈建可能需要幾小時，最多 72 小時，視租用戶大小而定。衛星位置的佈建完成後，您將會收到電子郵件確認。當新的地理位置在 OneDrive 系統管理中心的**地理位置**索引標籤上以藍色顯示在地圖上，您就可以繼續將使用者慣用的資料位置設定到該地理位置。 

> [!IMPORTANT]
> 您的新衛星地理位置將會以預設設定進行設定。這可讓您依當地合規性需求來設定該地理位置。

## <a name="setting-users-preferred-data-location"></a>設定使用者的慣用資料位置
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

啟用所需的資料位置後，您可以更新使用者帳戶以使用適當的資料位置。建議您為每個使用者設定慣用的資料位置，即使該使用者會停留在預設的資料位置。

> [!TIP]
> 建議您從測試使用者或一小群使用者開始驗證，再向整個組織推出多地理位置功能。

AAD 中有兩種類型的使用者物件：雲端專用使用者及同步處理的使用者。請針對使用者類型遵從適當的指示。

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>使用 AD Connect 同步處理使用者的慣用資料位置 

如果貴公司的使用者已從內部部署 Active Directory (AD) 系統同步處理到 Azure Active Directory (AAD)，其 PreferredDataLocation 必須在 AD 中填入，並同步處理到 AAD。請依照 [Azure AD Connect 同步處理：變更預設設定](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)中的程序，設定從內部部署 AD 將慣用的資料位置同步處理到 AAD。

建議您將設定使用者的慣用資料位置納入標準使用者建立工作流程的一部分。

> [!IMPORTANT]
> 對於未佈建 OneDrive 的新使用者，在使用者的 PDL 同步處理到 AAD 後，請等候至少 24 小時讓變更傳播，使用者才能登入商務用 OneDrive。(在使用者登入以佈建商務用 OneDrive 之前設定慣用資料位置，如此可確保使用者的新 OneDrive 會佈建在正確位置。)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>為雲端專用使用者設定慣用的資料位置為雲端專用使用者設定慣用的資料位置 

如果貴公司的使用者不是從內部部署 Active Directory (AD) 系統同步處理到 Azure Active Directory (AAD)，這表示使用者是在 Office 365 或 AAD 中建立，則必須使用 AAD PowerShell 設定 PDL。

本節的程序需要[適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果您已安裝 AAD PowerShell，請確認您已更新到最新版本。

1.  開啟適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

2.  執行 `Connect-MsolService` 並輸入租用戶的全域系統管理員認證。

3.  使用 [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) Cmdlet 為每個使用者設定慣用資料位置。例如：

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    您可以檢查以確認慣用的資料位置已使用 Get-MsolUser Cmdlet 正確更新。例如：

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

建議您將設定使用者的慣用資料位置納入標準使用者建立工作流程的一部分。

> [!IMPORTANT]
> 對於未佈建 OneDrive 的新使用者，在使用者的 PDL 設定好後，請等候至少 24 小時讓變更傳播，使用者才能登入 SharePoint OneDrive。(在使用者登入以佈建商務用 OneDrive 之前設定慣用資料位置，如此可確保使用者的新 OneDrive 會佈建在正確位置。)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 佈建及 PDL 的影響

如果使用者已在租用戶中建立 OneDrive 網站，設定其 PDL 不會自動移動其現有的 OneDrive。若要移動使用者的 OneDrive，請參閱[商務用 OneDrive 異地移動](move-onedrive-between-geo-locations.md)，請按照「在地理位置之間移動 OneDrive」中的指示。

如果使用者在租用戶中沒有 OneDrive 網站，OneDrive 會根據其 PDL 值進行佈建，並假設使用者的 PDL 符合其中一個公司的允許資料位置 (ADL)。

## <a name="configuring-multi-geo-search"></a>設定多地理位置搜尋

多地理位置租用戶具有彙總搜尋功能，可讓搜尋查詢從租用戶中的任何位置傳回結果。

根據預設，從這些進入點搜尋會傳回彙總的結果，即使每個搜尋索引都位於其相關的地理位置內：

- 商務用 OneDrive

- Delve

- SharePoint 首頁

- 搜尋中心

此外，多地理位置搜尋功能可針對使用 SharePoint 搜尋 API 的自訂搜尋應用程式進行設定。

請檢閱[為商務用 OneDrive 多地理位置設定搜尋](configure-search-for-multi-geo.md)以取得相關指示，包括任何限制與差異。

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>驗證商務用 OneDrive 多地理位置設定

以下是一些基本使用案例，在向公司廣泛推出商務用 OneDrive 多地理位置之前，您可能會想將其納入驗證規劃。完成這些測試以及與貴公司相關的任何其他使用案例後，您可以選擇繼續在初始試驗群組中新增使用者。

**商務用 OneDrive**

從 Office 365 應用程式啟動器選取 OneDrive，並確認系統自動根據使用者的 PDL 將您導向至使用者的適當地理位置。商務用 OneDrive 現在應於該位置開始佈建。佈建後，請嘗試上傳和下載一些文件。

**OneDrive 行動應用程式**

以測試帳戶認證登入 OneDrive 行動應用程式。確認您可以看到您的商務用 OneDrive 檔案，並可從行動裝置與檔案互動。

**OneDrive 同步處理用戶端**

確認 OneDrive 同步處理用戶端會在登入時自動偵測商務用 OneDrive 的地理位置。如果您要下載同步處理用戶端，請按一下 OneDrive 文件庫中的 [同步處理]****。

**Office 應用程式**

請確認您可以從 Office 應用程式 (如 Word) 登入，以存取商務用 OneDrive。開啟 Office 應用程式並選取 [OneDrive – <TenantName>]。Office 會偵測您的 OneDrive 位置，並顯示您可以開啟的檔案。

**共用**

嘗試共用 OneDrive 檔案。確認人員選擇器顯示您的所有 SharePoint 線上使用者，無論其地理位置為何。
