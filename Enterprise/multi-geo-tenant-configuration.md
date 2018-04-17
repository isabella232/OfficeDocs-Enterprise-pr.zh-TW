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
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive for Business 多重地理租用戶組態

設定您的租用戶 onedrive for Business 多-地理位置之前，請確定您已閱讀[規劃 OneDrive for Business 多-地理位置](plan-for-multi-geo.md)。若要遵循本文中的步驟，您將需要您想要啟用的位置和測試使用者想要佈建那些位置的清單。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Office 365 計劃中的多個地理位置功能新增至您的租用戶

若要使用 OneDrive for Business 多-地理位置，您需要_多個地理位置功能的 Office 365_計劃。若要將此計劃新增至您的租用戶帳戶小組與搭配使用。帳戶小組會與適當的授權專家連線並取得設定您的租用戶。

請注意_Office 365 的多重地理位置功能_規劃使用者層級的服務計劃。您要主控衛星位置中每個使用者需要授權。您可以新增更多授權一段時間當您將使用者新增衛星位置中。

一旦_Office 365 的多重地理位置功能_計劃已佈建租用戶、**地理位置**] 索引標籤會變成可用[OneDrive 系統管理中心](https://admin.onedrive.com)。

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>設為您的租用戶的允許資料位置 (ADL)

您必須將允許資料位置 SharePoint 的每個地理位置您想要用來使用 OneDrive for Business。下表顯示可用的地理位置：

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>程式碼</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">北美</td>
<td align="left">名稱</td>
</tr>
<tr class="even">
<td align="left">歐洲 / 東部正 / 非洲</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">亞太地區</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">澳大利亞</td>
<td align="left">澳洲</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">日文</td>
</tr>
<tr class="even">
<td align="left">加拿大</td>
<td align="left">可以</td>
</tr>
<tr class="odd">
<td align="left">英國</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">韓國</td>
<td align="left">韓文</td>
</tr>
</tbody>
</table>

若要新增衛星地理位置

1. 開啟[OneDrive 系統管理中心](https://admin.onedrive.com)。

2. 瀏覽至 [**地理位置**] 索引標籤。

3. 按一下 [**新增位置**。

4. 選取您想要新增的位置，然後按一下 [**下一步**。

5. 輸入您想要的地理位置，搭配使用的網域，然後按一下 [**新增**。

6. 按一下 [關閉]。

佈建可能需要幾個小時從到 72 個小時，視您的租用戶的大小而定。衛星位置的佈建完成之後，您會收到電子郵件確認。當新的地理位置會出現在地圖上 OneDrive 系統管理中心的 [**地理位置**] 索引標籤上的藍色時，您可以繼續設定使用者的偏好的資料位置為該地理位置。 

> [!IMPORTANT]
> 新的衛星地理位置會設定為預設值。這可讓您設定最適合您的本機規範需求的地理位置。

## <a name="setting-users-preferred-data-location"></a>設定使用者的偏好的資料位置
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

一旦您啟用所需的資料位置，您可以更新您的使用者帳戶來使用適當的資料位置。我們建議您設定喜好的資料位置的每位使用者，即使該使用者停留在預設資料位置。

> [!TIP]
> 建議您驗證測試使用者或小群使用者開始之前您更廣泛的組織啟用多個地理位置功能。

AAD 中有兩種類型的使用者物件： 雲端只有使用者和同步處理的使用者。請遵循適當的指示您類型的使用者。

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>同步處理使用者的慣用資料位置使用 AD 連線 

如果您的公司使用者從同步處理內部部署 Active Directory (AD) 系統以 Azure Active Directory (AAD)，必須已在 AD 中填入及同步處理至 AAD 其 PreferredDataLocation。請依照下列程序中的[Azure AD 連線同步處理： 變更預設的設定](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)設定喜好從資料位置同步處理內部部署 AD 以 AAD。

我們建議您將包括使用者的慣用資料位置設定為標準使用者建立工作流程的一部分。

> [!IMPORTANT]
> 含有佈建沒有 OneDrive 的新使用者，等待至少 24 小時之後使用者 PDL 同步處理至 AAD 的變更傳播使用者登入到 OneDrive for Business 之前。（設定偏好的資料使用者登入到佈建其 OneDrive for Business 之前的位置可確保使用者的新 OneDrive 會在正確的位置來佈建。）

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>雲端的唯一使用者設定慣用資料位置 

如果您的公司使用者不同步從內部部署 Active Directory (AD) 系統以 Azure Active Directory (AAD)，這表示他們所建立的 Office 365 或 AAD，然後 PDL 必須設定使用 AAD PowerShell。

本節中的程序需要[Microsoft Azure Active Directory Module for Windows PowerShell 模組](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果您已安裝的 AAD PowerShell，請確定您更新為最新版本。

1.  開啟 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

2.  執行`Connect-MsolService`並輸入您的租用戶的全域系統管理員認證。

3.  使用[Set-msoluser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet 可設定每個使用者的偏好的資料位置。例如：

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    您可以檢查以確認已使用 Get-msoluser cmdlet 正確更新慣用的資料的位置。例如：

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

我們建議您將包括使用者的慣用資料位置設定為標準使用者建立工作流程的一部分。

> [!IMPORTANT]
> 含有佈建沒有 OneDrive 的新使用者，等待至少 24 小時之後的變更傳播之前使用者登入到 SharePoint OneDrive 設定使用者的 PDL。（設定偏好的資料使用者登入到佈建其 OneDrive for Business 之前的位置可確保使用者的新 OneDrive 會在正確的位置來佈建。）

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 佈建和 PDL 的影響

如果使用者已有 OneDrive 站台的租用戶中建立、 設定其 PDL 不會自動將其現有 OneDrive。若要移動使用者的 OneDrive，請參閱[OneDrive for Business 地理位置移動](move-onedrive-between-geo-locations.md)請遵循地理位置之間的 [移動 OneDrive 中的指示。

如果使用者不具有 OneDrive 站台內的租用戶、 OneDrive 在佈建為根據其 PDL 值，假設使用者 PDL 符合其中一個公司的允許的資料位置 (ADLs)。

## <a name="configuring-multi-geo-search"></a>設定多個地理位置搜尋

您的多個地理位置租用戶會有彙總的搜尋功能讓搜尋查詢結果傳回從任何地方租用戶內。

根據預設，從下列進入點的搜尋會傳回彙總結果，即使其相關的地理位置中的每個搜尋索引所在：

- OneDrive for business

- Delve

- SharePoint 首頁

- 搜尋中心

此外，可以設定多個地理位置的搜尋功能的自訂搜尋應用程式所使用的 SharePoint 搜尋 API。

請檢閱[設定搜尋 onedrive for Business 多-地理位置](configure-search-for-multi-geo.md)的指示包含任何限制和差異。

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>驗證 OneDrive for Business 多重地理位置設定

以下是一些您可能會想要包含在您的驗證計劃之前廣泛推出 OneDrive for Business 多-地理位置為您的公司的基本使用情況。一旦您完成這些測試及相關貴公司任何其他的使用情況下，您可以選擇移至初始試驗群組中新增的使用者。

**OneDrive for Business**

從 Office 365 應用程式啟動器選取 OneDrive 並確認您自動導向至適當使用者根據使用者的 PDL 的地理位置-位置。OneDrive for Business 現在應該開始佈建在該位置。一次已佈建的嘗試上傳及下載部分文件。

**OneDrive 行動應用程式**

登入您的測試帳戶認證與您 OneDrive 行動裝置應用程式。確認您可以看到您 OneDrive for business 檔案可以從行動裝置的與其互動。

**OneDrive sync 用戶端**

確認 OneDrive sync 用戶端會自動偵測將 OneDrive for Business 地理位置時登入。如果您需要下載 sync 用戶端，您可以按一下 [**同步處理**OneDrive 程式庫中。

**Office 應用程式**

確認您可以存取 OneDrive for Business 的 Office 應用程式，如 Word 登入。開啟 Office 應用程式與 select"OneDrive – <TenantName>"。Office 會偵測您 OneDrive 位置，並顯示您可以開啟的檔案。

**Sharing**

嘗試以共用 OneDrive 檔案。確認人員選擇] 顯示您所有的 SharePoint online 使用者不論其地理位置。
