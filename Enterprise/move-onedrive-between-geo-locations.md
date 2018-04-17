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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="64c8a-103">將 OneDrive 網站移至不同地理位置</span><span class="sxs-lookup"><span data-stu-id="64c8a-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="64c8a-p101">使用 OneDrive 地理位置移動，您可以將使用者的 OneDrive 移到不同地理位置。SharePoint Online 系統管理員或 Office 365 全域管理員在執行 OneDrive 地理位置移動作業。在您開始地理位置移動 OneDrive 之前，請務必通知的使用者要移動之 OneDrive 及建議也移動期間關閉所有檔案。（如果使用者有後再使用 Office 用戶端移動期間開啟文件移動的完成文件必須儲存到新的位置。）如果想要移動可排程的未來的時間。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="64c8a-p102">OneDrive 服務使用 Azure Blob 儲存空間來儲存內容。儲存 blob 相關聯的使用者 OneDrive 要移從來源至目的地地理位置的目的地 OneDrive 所要對使用者提供 40 天內。一旦目的地 OneDrive 有將會還原至使用者的 OneDrive 存取。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="64c8a-p103">期間 OneDrive 地理位置移動 （約 2-6 小時） 的使用者 OneDrive 設為唯讀屬性。使用者仍然可以存取其透過 OneDrive sync 用戶端或其 OneDrive 網站 SharePoint Online 中的檔案。OneDrive 地理位置移動完成後，使用者將自動連線至的目的地地理位置其 OneDrive 時的 Office 365 應用程式啟動器瀏覽至 OneDrive。Sync 用戶端會自動開始次從新的位置。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="64c8a-115">本文中的程序需要[Microsoft SharePoint Online PowerShell 模組](https://www.microsoft.com/en-us/download/details.aspx?id=35588)。</span><span class="sxs-lookup"><span data-stu-id="64c8a-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="64c8a-116">移動 OneDrive 站台</span><span class="sxs-lookup"><span data-stu-id="64c8a-116">Moving a OneDrive site</span></span>

<span data-ttu-id="64c8a-p104">若要執行 OneDrive 地理位置移動，承租人管理員必須先將使用者的慣用資料位置 (PDL) 為適當的地理位置。PDL 設定之後，等待至少 24 小時的值開始 OneDrive 地理位置移動前先同步處理所有地理位置之間的 PDL 更新。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="64c8a-119">當使用地理位置移動指令程式時，請連接至 SPO 服務使用者的目前 OneDrive 地理位置，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="64c8a-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="64c8a-120">例如： 若要移動的使用者 'Matt@contosoenergy.onmicrosoft.com' OneDrive，連線至 EUR SharePoint 系統管理中心使用者 OneDrive 就 EUR 地理位置中：</span><span class="sxs-lookup"><span data-stu-id="64c8a-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="64c8a-121">驗證環境</span><span class="sxs-lookup"><span data-stu-id="64c8a-121">Validating the environment</span></span>

<span data-ttu-id="64c8a-122">在您開始之前 OneDrive 地理位置移動，我們建議您驗證的環境。</span><span class="sxs-lookup"><span data-stu-id="64c8a-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="64c8a-123">若要確保所有地理位置相容，執行：</span><span class="sxs-lookup"><span data-stu-id="64c8a-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="64c8a-p105">如果 OneDrive 處於合法持有下或者它包含子網站，它不能移動。您可以使用-ValidationOnly 參數開始 SPOUserAndContentMove 指令程式驗證如果 OneDrive 能夠移動：</span><span class="sxs-lookup"><span data-stu-id="64c8a-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="64c8a-p106">如此可傳回成功如果 OneDrive 已準備好要移或失敗時的合法持有或一般防止移動的子網站。一旦您驗證 OneDrive 已準備好移動時，您可以啟動移動。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="64c8a-128">啟動 OneDrive 地理位置移動</span><span class="sxs-lookup"><span data-stu-id="64c8a-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="64c8a-129">若要啟動移動，請執行：</span><span class="sxs-lookup"><span data-stu-id="64c8a-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="64c8a-130">使用下列參數：</span><span class="sxs-lookup"><span data-stu-id="64c8a-130">Using these parameters:</span></span>

-   <span data-ttu-id="64c8a-131">_UserPrincipalName_ – 其 OneDrive 要移動之使用者的 UPN。</span><span class="sxs-lookup"><span data-stu-id="64c8a-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="64c8a-p107">_DestinationDataLocation_ – 地理位置 OneDrive 需要要移動的位置。這應該是以使用者的偏好的資料位置相同。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="64c8a-134">建議您執行`Get-SPOGeoMoveStateCompatibility`與`ValidationOnly`之前初始化 OneDrive 地理位置移動。</span><span class="sxs-lookup"><span data-stu-id="64c8a-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="64c8a-135">例如，將 EUR OneDrive matt@contosoenergy.onmicrosoft.com 移至澳洲，請執行：</span><span class="sxs-lookup"><span data-stu-id="64c8a-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="64c8a-136">若要排程稍後地理位置移動，使用下列參數中的程序：</span><span class="sxs-lookup"><span data-stu-id="64c8a-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="64c8a-p108">_PreferredMoveBeginDate_ – 可能移動會開始在此指定的時間。必須指定時間的國際標準時間 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="64c8a-p109">_PreferredMoveEndDate_ – 可能移動會完成此指定的時間、 最佳投入比為基礎。必須指定時間的國際標準時間 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="64c8a-141">取消 OneDrive 地理位置移動</span><span class="sxs-lookup"><span data-stu-id="64c8a-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="64c8a-142">您可以停止地理位置移動使用者的 OneDrive 提供移動不正在進行中或使用此指令程式來完成：</span><span class="sxs-lookup"><span data-stu-id="64c8a-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="64c8a-143">_UserPrincipalName_所在之 OneDrive 移動您想要停止之使用者的 UPN。</span><span class="sxs-lookup"><span data-stu-id="64c8a-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="64c8a-144">判斷目前的狀態</span><span class="sxs-lookup"><span data-stu-id="64c8a-144">Determining current status</span></span>

<span data-ttu-id="64c8a-145">您可以檢查地理位置移入或登出您使用 Get SPOUserAndContentMoveState 指令程式來連線至地理 OneDrive 的狀態。</span><span class="sxs-lookup"><span data-stu-id="64c8a-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="64c8a-146">下表說明移動狀態。</span><span class="sxs-lookup"><span data-stu-id="64c8a-146">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="64c8a-147"><strong>狀態</strong></span><span class="sxs-lookup"><span data-stu-id="64c8a-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="64c8a-148"><strong>描述</strong></span><span class="sxs-lookup"><span data-stu-id="64c8a-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="64c8a-149">為 NotStarted</span><span class="sxs-lookup"><span data-stu-id="64c8a-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="64c8a-150">移動尚未啟動。</span><span class="sxs-lookup"><span data-stu-id="64c8a-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="64c8a-151">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="64c8a-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="64c8a-152">移動正在進行中其中一個下列狀態： 驗證 (1/4) 備份 (2/4)，還原 (3/4) 清理 (4/4)。</span><span class="sxs-lookup"><span data-stu-id="64c8a-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="64c8a-153">成功</span><span class="sxs-lookup"><span data-stu-id="64c8a-153">Success</span></span></td>
<td align="left"><span data-ttu-id="64c8a-154">已成功完成移動。</span><span class="sxs-lookup"><span data-stu-id="64c8a-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="64c8a-155">失敗</span><span class="sxs-lookup"><span data-stu-id="64c8a-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="64c8a-156">移動失敗。</span><span class="sxs-lookup"><span data-stu-id="64c8a-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="64c8a-157">若要尋找之特定使用者的移動的狀態，請使用 UserPrincipalName 參數：</span><span class="sxs-lookup"><span data-stu-id="64c8a-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="64c8a-158">若要尋找狀態的所有移入或登出您連線至的地理位置，請使用 MoveState 參數使用下列值之一： 為 NotStarted、 InProgress、 成功、 失敗、 所有。</span><span class="sxs-lookup"><span data-stu-id="64c8a-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="64c8a-159">您也可以新增`-Verbose`參數的更多詳細資訊說明移動狀態。</span><span class="sxs-lookup"><span data-stu-id="64c8a-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="64c8a-160">使用者經驗</span><span class="sxs-lookup"><span data-stu-id="64c8a-160">User Experience</span></span>

<span data-ttu-id="64c8a-p110">如果其 OneDrive 移至不同地理位置，OneDrive 的使用者應注意到最少的中斷。除了之外的簡短唯讀狀態移動期間，現有的連結和權限會繼續移動完成之後如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="64c8a-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="64c8a-163">OneDrive for Business</span></span>

<span data-ttu-id="64c8a-p111">雖然移動正在進行中使用者的 OneDrive 設為唯讀屬性。移動完成之後，將使用者導向至新的地理位置中其 OneDrive 時瀏覽至 OneDrive Office 365 應用程式啟動器或在網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="64c8a-166">OneDrive 內容的權限</span><span class="sxs-lookup"><span data-stu-id="64c8a-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="64c8a-167">使用 OneDrive 內容的權限的使用者會繼續移動期間及完成後具有內容的存取權。</span><span class="sxs-lookup"><span data-stu-id="64c8a-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="64c8a-168">OneDrive 同步處理用戶端</span><span class="sxs-lookup"><span data-stu-id="64c8a-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="64c8a-p112">OneDrive sync 用戶端將會自動偵測及順暢地將轉接 OneDrive 地理位置移動完成後同步至新的 OneDrive 位置。使用者不需要登入一次或採取任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="64c8a-171">如果使用者更新檔案時正在進行中的 OneDrive 地理位置移動、 sync 用戶端會通知他們檔案上傳待時移動技巧。</span><span class="sxs-lookup"><span data-stu-id="64c8a-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="64c8a-172">共用的連結</span><span class="sxs-lookup"><span data-stu-id="64c8a-172">Sharing links</span></span> 

<span data-ttu-id="64c8a-173">在 OneDrive 地理位置時移動完成、 現有的共用的連結已移動檔案將會自動將重新導向至新的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64c8a-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="64c8a-174">OneNote 經驗</span><span class="sxs-lookup"><span data-stu-id="64c8a-174">OneNote Experience</span></span> 

<span data-ttu-id="64c8a-p113">OneNote win32 用戶端和 UWP （通用） 的應用程式將會自動偵測及順暢地在 OneDrive 地理位置移動完成後同步處理至新的 OneDrive 位置的筆記本。使用者不需要登入一次或採取任何其他動作。使用者只能看到標記為筆記本同步處理 OneDrive 地理位置移動正在進行中時，會失敗。此功能已提供下列 OneNote 用戶端版本：</span><span class="sxs-lookup"><span data-stu-id="64c8a-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="64c8a-179">OneNote win32 – 版本 16.0.8326.2096 （及更新版本）</span><span class="sxs-lookup"><span data-stu-id="64c8a-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="64c8a-180">OneNote UWP – 版本 16.0.8431.1006 （及更新版本）</span><span class="sxs-lookup"><span data-stu-id="64c8a-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="64c8a-181">OneNote Mobile 應用程式 – 版本 16.0.8431.1011 （及更新版本）</span><span class="sxs-lookup"><span data-stu-id="64c8a-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="64c8a-182">小組應用程式</span><span class="sxs-lookup"><span data-stu-id="64c8a-182">Teams app</span></span>

<span data-ttu-id="64c8a-p114">在 OneDrive 地理位置時移動完成、 使用者將能夠存取其 OneDrive 上的檔案小組 app 另外、 檔案共用的地理位置移動前其 OneDrive 小組聊天透過會繼續運作移動完成後。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="64c8a-185">OneDrive for Business 行動應用程式 (iOS)</span><span class="sxs-lookup"><span data-stu-id="64c8a-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="64c8a-186">在 OneDrive 地理位置時移動完成，使用者必須登出及登入一次 iOS 行動應用程式上將資料庫同步至新的 OneDrive 位置。</span><span class="sxs-lookup"><span data-stu-id="64c8a-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="64c8a-187">現有的後面群組和網站</span><span class="sxs-lookup"><span data-stu-id="64c8a-187">Existing followed groups and sites</span></span>

<span data-ttu-id="64c8a-p115">已瀏覽過的站台及群組會顯示在使用者的 OneDrive for business 不論其地理位置。網站和裝載於另一個地理位置的群組將會開啟不同的索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="64c8a-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
