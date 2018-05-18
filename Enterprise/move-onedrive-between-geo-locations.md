---
title: 將 OneDrive 網站移至不同的地理位置
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
description: 了解如何將 OneDrive 網站移至不同的地理位置。
ms.openlocfilehash: 6bac98cc0707f977b7b585e8ae0a570f4b9662ee
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>將 OneDrive 網站移至不同的地理位置 

使用 OneDrive 異地移動時，您可以將使用者的 OneDrive 移到不同的地理位置。OneDrive 異地移動是由 SharePoint Online 系統管理員或 Office 365 全域系統管理員所執行。在啟動 OneDrive 異地移動前，請務必告知使用者 OneDrive 即將移動，並建議使用者在移動期間關閉所有檔案。(如果在移動期間使用者使用 Office 用戶端開啟文件，則在移動完成後，文件必須儲存到新位置。) 如有需要，移動可排程至日後的時間。

OneDrive 服務使用 Azure Blob 儲存體來儲存內容。與使用者 OneDrive 相關聯的儲存體 blob 會在使用者能夠使用目的地 OneDrive 的 40 天內，從來源移動到目的地理位置。在目的地 OneDrive 可以使用後，將會還原使用者 OneDrive 的存取。

在 OneDrive 異地移動期間 (大約 2-6 小時)，使用者的 OneDrive 會設為唯讀狀態。使用者仍可以透過 OneDrive 同步處理用戶端或 SharePoint Online 中的 OneDrive 網站存取檔案。在完成 OneDrive 異地移動後，若使用者瀏覽至 Office 365 應用程式啟動器中的 OneDrive，將會自動連線到位於目的地理位置的 OneDrive。同步處理用戶端將自動開始新位置的同步處理。

本文所述的程序需要 [Microsoft SharePoint Online PowerShell 模組](https://www.microsoft.com/en-us/download/details.aspx?id=35588)。

## <a name="moving-a-onedrive-site"></a>移動 OneDrive 網站

若要執行 OneDrive 異地移動，租用戶系統管理員必須先將使用者的慣用資料位置 (PDL) 設定至適當的地理位置。設定好 PDL 後，請等候至少 24 小時，讓 PDL 更新可在地理位置之間同步處理，才能開始 OneDrive 異地移動。

使用異地移動 Cmdlet 時，請使用下列語法連線到使用者目前 OneDrive 地理位置的 SPO 服務：

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

例如：若要移動使用者 ‘Matt@contosoenergy.onmicrosoft.com’ 的 OneDrive，因使用者的 OneDrive 位於 EUR 地理位置，請連線到 EUR SharePoint 管理中心：

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>驗證環境

在您開始 OneDrive 異地移動之前，我們建議您先驗證環境。

若要確保所有地理位置相容，請執行：

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

如果 OneDrive 處於法務保存狀態或包含子網站，則無法移動。您可以使用 Start-SPOUserAndContentMove Cmdlet 以及 -ValidationOnly 參數驗證 OneDrive 是否可以移動：

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

如果 OneDrive 已準備好要移動會傳回成功，如果有防止移動的法務保存狀態或子網站，則會傳回失敗。在您已驗證 OneDrive 移動準備就緒之後，就可以開始移動。

## <a name="start-a-onedrive-geo-move"></a>啟動 OneDrive 異地移動

若要啟動移動，請執行：  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

使用下列參數：

-   _UserPrincipalName_ – OneDrive 即將移動的使用者 UPN。

-   _DestinationDataLocation_ – OneDrive 要移動到的地理位置。這應與使用者慣用資料位置相同。

> [!NOTE]
> 在起始 OneDrive 異地移動前，建議您執行 `Get-SPOGeoMoveStateCompatibility` 與 `ValidationOnly`。

比方說，若要將 matt@contosoenergy.onmicrosoft.com 的 OneDrive 從 EUR 移動到 AUS，請執行：

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

若要排程稍後進行異地移動，請使用下列參數的其中一個：

-   _PreferredMoveBeginDate_ – 移動會在指定的時間開始。必須以國際標準時間 (UTC) 來指定時間。

-   _PreferredMoveEndDate_ – 移動會以最佳方式在指定的時間前完成。必須以國際標準時間 (UTC) 來指定時間。 

## <a name="cancel-a-onedrive-geo-move"></a>取消 OneDrive 異地移動 

只要移動非正在進行或已完成，您即可使用 Cmdlet 停止使用者 OneDrive 的異地移動：

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

其中 _UserPrincipalName_ 是您要停止的 OneDrive 移動之使用者 UPN。

## <a name="determining-current-status"></a>判斷目前狀態

您可以使用 Get-SPOUserAndContentMoveState Cmdlet 查看 OneDrive 異地移動的狀態是位於或已移出您連線的地理位置。

下表說明移動狀態。

<table>
<thead>
<tr class="header">
<th align="left"><strong>狀態</strong></th>
<th align="left"><strong>描述</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">移動尚未啟動。</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">移動正在進行中，可能是下列其中一種狀態：驗證 (1/4)、備份 (2/4)、還原 (3/4)、清除 (4/4)。</td>
</tr>
<tr class="odd">
<td align="left">成功</td>
<td align="left">已成功完成移動。</td>
</tr>
<tr class="even">
<td align="left">失敗</td>
<td align="left">移動失敗。</td>
</tr>
</tbody>
</table>

若要尋找特定使用者的移動狀態，請使用 UserPrincipalName 參數：

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

若要找出位於或已移出您連線地理位置的所有移動之狀態，請使用 MoveState 參數搭配下列值的其中一個：NotStarted、InProgress、成功、失敗、全部。

`Get-SPOUserAndContentMoveState -MoveState <value>`

您也可以新增 `-Verbose` 參數，以取得移動狀態更詳細的說明。

## <a name="user-experience"></a>使用者體驗

如果 OneDrive 移到不同的地理位置，OneDrive 使用者應注意是否有服務中斷。除了在移動期間會發生簡短的唯讀狀態，在移動完成後，現有的連結和權限會如預期般繼續運作。

### <a name="onedrive-for-business"></a>商務用 OneDrive

移動正在進行時，使用者的 OneDrive 會設為唯讀狀態。完成移動後，若使用者瀏覽至 Office 365 應用程式啟動器或網頁瀏覽器中的 OneDrive，使用者會導向至新地理位置中的 OneDrive。

### <a name="permissions-on-onedrive-content"></a>OneDrive 內容的權限

具有 OneDrive 內容權限的使用者將在移動期間和移動完成後繼續擁有內容的存取權。

### <a name="onedrive-sync-client"></a>OneDrive 同步處理用戶端 

OneDrive 異地移動完成後，OneDrive 同步處理用戶端會自動偵測並順暢地傳輸同步處理至 OneDrive 的新位置。使用者不必重新登入或採取任何其他動作。

如果使用者在進行 OneDrive 異地移動時更新檔案，同步處理用戶端會告知使用者，進行異地移動時上傳的檔案會擱置。

### <a name="sharing-links"></a>共用連結 

在 OneDrive 異地移動完成後，移動的檔案之現有共用連結將會自動重新導向至新的地理位置。

### <a name="onenote-experience"></a>OneNote 體驗 

OneDrive 異地移動完成後，OneNote win32 用戶端和 UWP (通用) 應用程式會自動偵測並順暢地將筆記本同步處理到 OneDrive 的新位置。使用者不必重新登入或採取任何其他動作。使用者唯一可見的指標是，若 OneDrive 異地移動正在進行時，筆記本同步處理會失敗。此體驗適用於下列 OneNote 用戶端版本：

-   OneNote win32 – 版本 16.0.8326.2096 (及更新版本)

-   OneNote UWP – 版本 16.0.8431.1006 (及更新版本)

-   OneNote 行動應用程式 – 版本 16.0.8431.1011 (及更新版本)

### <a name="teams-app"></a>Teams 應用程式

OneDrive 異地移動完成後，使用者可以在 Teams 應用程式上存取其 OneDrive 檔案。此外，在異地移動之前從 OneDrive 透過 Teams 交談共用的檔案，在移動完成後將會繼續運作。

### <a name="onedrive-for-business-mobile-app-ios"></a>商務用 OneDrive 行動應用程式 (iOS) 

在 OneDrive 異地移動完成後，使用者必須在 iOS 行動應用程式上登出並重新登入，以同步處理到 OneDrive 的新位置。

### <a name="existing-followed-groups-and-sites"></a>現有的已追蹤群組和網站

已追蹤的網站和群組會針對業務顯示在使用者的 OneDrive 中，無論其地理位置。裝載於其他地理位置的網站和群組會在不同的索引標籤中開啟。
