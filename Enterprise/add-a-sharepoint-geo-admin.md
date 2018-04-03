---
title: 新增或移除的地理位置管理員
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何在新增或移除的地理位置管理員 OneDrive for Business 多-地理位置。
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="ac344-103">新增或移除的地理位置管理員的 onedrive for Busniess 多-地理位置</span><span class="sxs-lookup"><span data-stu-id="ac344-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="ac344-p101">您可以設定不同的系統管理員必須在您的租用戶中每個地理位置。這些系統管理員必須 SharePoint Online 和 OneDrive 設定所特有及其地理位置的存取權。</span><span class="sxs-lookup"><span data-stu-id="ac344-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="ac344-p102">某些服務-例如之字詞儲存區-是從集中管理位置管理並複寫至衛星位置。集中管理位置地理系統管理員具有存取這些，而衛星位置的地理位置 admins 不。</span><span class="sxs-lookup"><span data-stu-id="ac344-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="ac344-108">全域管理員與 SharePoint Online 管理員繼續所有地理位置中有權限設定。</span><span class="sxs-lookup"><span data-stu-id="ac344-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="ac344-109">設定地理管理員</span><span class="sxs-lookup"><span data-stu-id="ac344-109">Configuring geo administrators</span></span>

<span data-ttu-id="ac344-110">設定地理 admins 需要 SharePoint Online PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="ac344-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="ac344-111">使用[Connect-sposervice](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)連線至系統管理中心的地理位置您要新增地理位置管理]。（例如 Connect-sposervicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="ac344-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="ac344-112">若要將使用者新增為地理位置管理、 執行`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="ac344-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="ac344-113">若要檢視現有地理 admins 的位置，請執行`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="ac344-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="ac344-114">若要移除使用者以地理位置的系統管理員位置、 執行`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="ac344-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="ac344-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac344-115">See Also</span></span>

[<span data-ttu-id="ac344-116">新增 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="ac344-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="ac344-117">取得 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="ac344-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="ac344-118">移除 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="ac344-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)