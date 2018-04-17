---
title: 將 OneDrive 網站移至不同地理位置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: 了解如何將 OneDrive 網站移至不同地理位置。
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>將 OneDrive 網站移至不同地理位置 

使用 OneDrive 地理位置移動，您可以將使用者的 OneDrive 移到不同地理位置。SharePoint Online 系統管理員或 Office 365 全域管理員在執行 OneDrive 地理位置移動作業。在您開始地理位置移動 OneDrive 之前，請務必通知的使用者要移動之 OneDrive 及建議也移動期間關閉所有檔案。（如果使用者有後再使用 Office 用戶端移動期間開啟文件移動的完成文件必須儲存到新的位置。）如果想要移動可排程的未來的時間。

OneDrive 服務使用 Azure Blob 儲存空間來儲存內容。儲存 blob 相關聯的使用者 OneDrive 要移從來源至目的地地理位置的目的地 OneDrive 所要對使用者提供 40 天內。一旦目的地 OneDrive 有將會還原至使用者的 OneDrive 存取。

期間 OneDrive 地理位置移動 （約 2-6 小時） 的使用者 OneDrive 設為唯讀屬性。使用者仍然可以存取其透過 OneDrive sync 用戶端或其 OneDrive 網站 SharePoint Online 中的檔案。OneDrive 地理位置移動完成後，使用者將自動連線至的目的地地理位置其 OneDrive 時的 Office 365 應用程式啟動器瀏覽至 OneDrive。Sync 用戶端會自動開始次從新的位置。

本文中的程序需要[Microsoft SharePoint Online PowerShell 模組](https://www.microsoft.com/en-us/download/details.aspx?id=35588)。

## <a name="moving-a-onedrive-site"></a>移動 OneDrive 站台

若要執行 OneDrive 地理位置移動，承租人管理員必須先將使用者的慣用資料位置 (PDL) 為適當的地理位置。PDL 設定之後，等待至少 24 小時的值開始 OneDrive 地理位置移動前先同步處理所有地理位置之間的 PDL 更新。

當使用地理位置移動指令程式時，請連接至 SPO 服務使用者的目前 OneDrive 地理位置，使用下列語法：

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

例如： 若要移動的使用者 'Matt@contosoenergy.onmicrosoft.com' OneDrive，連線至 EUR SharePoint 系統管理中心使用者 OneDrive 就 EUR 地理位置中：

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>驗證環境

在您開始之前 OneDrive 地理位置移動，我們建議您驗證的環境。

若要確保所有地理位置相容，執行：

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

如果 OneDrive 處於合法持有下或者它包含子網站，它不能移動。您可以使用-ValidationOnly 參數開始 SPOUserAndContentMove 指令程式驗證如果 OneDrive 能夠移動：

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

如此可傳回成功如果 OneDrive 已準備好要移或失敗時的合法持有或一般防止移動的子網站。一旦您驗證 OneDrive 已準備好移動時，您可以啟動移動。

## <a name="start-a-onedrive-geo-move"></a>啟動 OneDrive 地理位置移動

若要啟動移動，請執行：  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

使用下列參數：

-   _UserPrincipalName_ – 其 OneDrive 要移動之使用者的 UPN。

-   _DestinationDataLocation_ – 地理位置 OneDrive 需要要移動的位置。這應該是以使用者的偏好的資料位置相同。

> [!NOTE]
> 建議您執行`Get-SPOGeoMoveStateCompatibility`與`ValidationOnly`之前初始化 OneDrive 地理位置移動。

例如，將 EUR OneDrive matt@contosoenergy.onmicrosoft.com 移至澳洲，請執行：

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

若要排程稍後地理位置移動，使用下列參數中的程序：

-   _PreferredMoveBeginDate_ – 可能移動會開始在此指定的時間。必須指定時間的國際標準時間 (UTC)。

-   _PreferredMoveEndDate_ – 可能移動會完成此指定的時間、 最佳投入比為基礎。必須指定時間的國際標準時間 (UTC)。 

## <a name="cancel-a-onedrive-geo-move"></a>取消 OneDrive 地理位置移動 

您可以停止地理位置移動使用者的 OneDrive 提供移動不正在進行中或使用此指令程式來完成：

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

_UserPrincipalName_所在之 OneDrive 移動您想要停止之使用者的 UPN。

## <a name="determining-current-status"></a>判斷目前的狀態

您可以檢查地理位置移入或登出您使用 Get SPOUserAndContentMoveState 指令程式來連線至地理 OneDrive 的狀態。

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
<td align="left">為 NotStarted</td>
<td align="left">移動尚未啟動。</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">移動正在進行中其中一個下列狀態： 驗證 (1/4) 備份 (2/4)，還原 (3/4) 清理 (4/4)。</td>
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

若要尋找之特定使用者的移動的狀態，請使用 UserPrincipalName 參數：

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

若要尋找狀態的所有移入或登出您連線至的地理位置，請使用 MoveState 參數使用下列值之一： 為 NotStarted、 InProgress、 成功、 失敗、 所有。

`Get-SPOUserAndContentMoveState -MoveState <value>`

您也可以新增`-Verbose`參數的更多詳細資訊說明移動狀態。

## <a name="user-experience"></a>使用者經驗

如果其 OneDrive 移至不同地理位置，OneDrive 的使用者應注意到最少的中斷。除了之外的簡短唯讀狀態移動期間，現有的連結和權限會繼續移動完成之後如預期般運作。

### <a name="onedrive-for-business"></a>OneDrive for Business

雖然移動正在進行中使用者的 OneDrive 設為唯讀屬性。移動完成之後，將使用者導向至新的地理位置中其 OneDrive 時瀏覽至 OneDrive Office 365 應用程式啟動器或在網頁瀏覽器。

### <a name="permissions-on-onedrive-content"></a>OneDrive 內容的權限

使用 OneDrive 內容的權限的使用者會繼續移動期間及完成後具有內容的存取權。

### <a name="onedrive-sync-client"></a>OneDrive 同步處理用戶端 

OneDrive sync 用戶端將會自動偵測及順暢地將轉接 OneDrive 地理位置移動完成後同步至新的 OneDrive 位置。使用者不需要登入一次或採取任何其他動作。

如果使用者更新檔案時正在進行中的 OneDrive 地理位置移動、 sync 用戶端會通知他們檔案上傳待時移動技巧。

### <a name="sharing-links"></a>共用的連結 

在 OneDrive 地理位置時移動完成、 現有的共用的連結已移動檔案將會自動將重新導向至新的地理位置。

### <a name="onenote-experience"></a>OneNote 經驗 

OneNote win32 用戶端和 UWP （通用） 的應用程式將會自動偵測及順暢地在 OneDrive 地理位置移動完成後同步處理至新的 OneDrive 位置的筆記本。使用者不需要登入一次或採取任何其他動作。使用者只能看到標記為筆記本同步處理 OneDrive 地理位置移動正在進行中時，會失敗。此功能已提供下列 OneNote 用戶端版本：

-   OneNote win32 – 版本 16.0.8326.2096 （及更新版本）

-   OneNote UWP – 版本 16.0.8431.1006 （及更新版本）

-   OneNote Mobile 應用程式 – 版本 16.0.8431.1011 （及更新版本）

### <a name="teams-app"></a>小組應用程式

在 OneDrive 地理位置時移動完成、 使用者將能夠存取其 OneDrive 上的檔案小組 app 另外、 檔案共用的地理位置移動前其 OneDrive 小組聊天透過會繼續運作移動完成後。

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive for Business 行動應用程式 (iOS) 

在 OneDrive 地理位置時移動完成，使用者必須登出及登入一次 iOS 行動應用程式上將資料庫同步至新的 OneDrive 位置。

### <a name="existing-followed-groups-and-sites"></a>現有的後面群組和網站

已瀏覽過的站台及群組會顯示在使用者的 OneDrive for business 不論其地理位置。網站和裝載於另一個地理位置的群組將會開啟不同的索引標籤中。
