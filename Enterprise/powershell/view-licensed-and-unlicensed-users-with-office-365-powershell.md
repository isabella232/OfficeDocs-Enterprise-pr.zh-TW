---
title: 使用 Office 365 PowerShell 檢視經授權與未經授權的使用者
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。
ms.openlocfilehash: 9bef0994d516de9c06da64969f090135aad4fa46
ms.sourcegitcommit: 16a060c0732c6234bb2ebc037786a7c4872fe686
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "38308578"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="649d0-103">使用 Office 365 PowerShell 檢視經授權與未經授權的使用者</span><span class="sxs-lookup"><span data-stu-id="649d0-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="649d0-104">**摘要：** 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="649d0-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="649d0-p101">在您的 Office 365 組織中的使用者帳戶，可能具有從組織的可用授權方案指派給他們的部分授權、全部授權或完全沒有授權。您可以使用 Office 365 PowerShell 快速尋找組織中的經授權和未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="649d0-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="649d0-107">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="649d0-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="649d0-108">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="649d0-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="649d0-109">若要檢視的所有使用者帳戶清單未指派授權計劃 （未授權的使用者） 的任何您組織中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="649d0-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="649d0-110">若要檢視的所有使用者帳戶清單中您的組織已指派任何授權計劃 （授權的使用者），執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="649d0-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```
>[!Note]
><span data-ttu-id="649d0-111">若要列出所有在您的訂閱中的使用者，請使用`Get-AzureAdUser -All $true`命令。</span><span class="sxs-lookup"><span data-stu-id="649d0-111">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="649d0-112">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="649d0-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="649d0-113">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="649d0-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="649d0-114">若要檢視您組織中所有使用者帳戶及其授權狀態的清單，在 Office 365 PowerShell 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="649d0-114">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

<span data-ttu-id="649d0-115">若要檢視您組織中所有未經授權使用者帳戶的清單，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="649d0-115">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="649d0-116">若要檢視您組織中所有經授權使用者帳戶的清單，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="649d0-116">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="649d0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="649d0-117">See also</span></span>

[<span data-ttu-id="649d0-118">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="649d0-118">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="649d0-119">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="649d0-119">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="649d0-120">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="649d0-120">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
