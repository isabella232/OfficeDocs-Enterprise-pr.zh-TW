---
title: 新增或移除地理位置系統管理員
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: 了解如何在 Office 365 多地理位置中新增或移除地理位置系統管理員。
ms.openlocfilehash: 767dcf5284e93b9a2e908d4ec837f034b29cb6db
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068469"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="df755-103">在 Office 365 多地理位置中新增或移除地理位置系統管理員</span><span class="sxs-lookup"><span data-stu-id="df755-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="df755-104">您可以為租用戶中的每個地理位置設定個別的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="df755-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="df755-105">這些系統管理員將能存取專為其地理位置設定的 Sharepoint 和 OneDrive 設定。</span><span class="sxs-lookup"><span data-stu-id="df755-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="df755-106">某些服務 - 例如詞彙儲存庫- 可從中心位置進行管理並會複製到衛星位置。</span><span class="sxs-lookup"><span data-stu-id="df755-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="df755-107">中央位置的地理位置系統管理員可以存取這些服務，而衛星位置的地理位置系統管理員則無法存取。</span><span class="sxs-lookup"><span data-stu-id="df755-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="df755-108">全域系統管理員和 SharePoint Online 系統管理員可以繼續存取中心位置和所有衛星位置的設定。</span><span class="sxs-lookup"><span data-stu-id="df755-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="df755-109">設定地理位置系統管理員</span><span class="sxs-lookup"><span data-stu-id="df755-109">Configuring geo administrators</span></span>

<span data-ttu-id="df755-110">設定地理位置系統管理員需要 SharePoint Online PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="df755-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="df755-111">使用 [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) 連線到您想新增地理位置系統管理員之地理位置的系統管理中心。(例如，Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="df755-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="df755-112">若要檢視某位置的現有地理位置系統管理員，請執行 `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="df755-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="df755-113">將使用者新增為地理位置系統管理員</span><span class="sxs-lookup"><span data-stu-id="df755-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="df755-114">若要將使用者新增為地理位置系統管理員，請執行 `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="df755-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="df755-115">若要在某位置將使用者的地理位置系統管理員身份移除，請執行 `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="df755-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="df755-116">將群組新增為地理位置系統管理員</span><span class="sxs-lookup"><span data-stu-id="df755-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="df755-117">您可以新增安全性群組或擁有郵件功能的安全性群組作為地理位置系統管理員。(不支援通訊群組與 Office 365 群組。)</span><span class="sxs-lookup"><span data-stu-id="df755-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="df755-118">若要新增群組為地理位置系統管理員，請執行 `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="df755-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="df755-119">若要移除群組的地理位置系統管理員身份，請執行 `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="df755-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="df755-120">請注意，並非所有安全性群組都有群組別名。</span><span class="sxs-lookup"><span data-stu-id="df755-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="df755-121">如果您要新增的安全性群組並沒有別名，請執行 [Get-MsolGroup](https://docs.microsoft.com/zh-TW/powershell/module/msonline/get-msolgroup) 擷取群組清單、找出安全性群組 ObjectID，然後再執行：</span><span class="sxs-lookup"><span data-stu-id="df755-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="df755-122">若要使用 ObjectID 移除群組，請執行 `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="df755-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="df755-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df755-123">See Also</span></span>

[<span data-ttu-id="df755-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="df755-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="df755-125">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="df755-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="df755-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="df755-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

<span data-ttu-id="df755-127">
  [為安全性群組設定別名 (MailNickName)](https://docs.microsoft.com/zh-TW/powershell/module/azuread/set-azureadgroup)</span><span class="sxs-lookup"><span data-stu-id="df755-127">[Set an alias (MailNickName) for a security group](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)</span></span>