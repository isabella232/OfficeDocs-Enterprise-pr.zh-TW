---
title: 使用 Office 365 PowerShell 管理 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: 摘要：了解如何使用 Office 365 PowerShell 與 Office 365 使用者和授權、商務用 Skype Online、SharePoint Online、Exchange Online 和 Office 365 安全與規範中心。
ms.openlocfilehash: fbc10833d3ee1e7377e6ed68adb7d2299fce72fa
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004566"
---
# <a name="manage-office-365-with-office-365-powershell"></a><span data-ttu-id="b08f7-103">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="b08f7-103">Manage Office 365 with Office 365 PowerShell</span></span>

<span data-ttu-id="b08f7-104">*本文適用于 Office 365 和 Microsoft 365。*</span><span class="sxs-lookup"><span data-stu-id="b08f7-104">*This article applies to both Office 365 and Microsoft 365.*</span></span>

<span data-ttu-id="b08f7-105">Office 365 PowerShell 是一種強大的管理工具，可補充 Microsoft 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="b08f7-105">Office 365 PowerShell is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="b08f7-106">例如，您可以使用 Office 365 PowerShell 自動化更快速地管理多個使用者帳戶和授權，以及建立報告。</span><span class="sxs-lookup"><span data-stu-id="b08f7-106">For example, you can use Office 365 PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="b08f7-107">瞭解如何使用 Office 365 PowerShell 與 Office 365 使用者和授權、商務用 Skype Online、SharePoint 線上、Exchange Online 和 Office 365 Security & 合規性中心。</span><span class="sxs-lookup"><span data-stu-id="b08f7-107">Learn how to use Office 365 PowerShell with Office 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Office 365 Security & Compliance Center.</span></span>
  
<span data-ttu-id="b08f7-108">根據您的需求，選取主題：</span><span class="sxs-lookup"><span data-stu-id="b08f7-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="b08f7-109">開始使用</span><span class="sxs-lookup"><span data-stu-id="b08f7-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="b08f7-110">如果您不熟悉 Office 365 PowerShell，且想要安裝 Office 365 PowerShell 模組，並聯機至您的 Office 365 訂閱，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-110">Start here if you are not familiar with Office 365 PowerShell and want to install the Office 365 PowerShell modules and connect to your Office 365 subscription.</span></span>

- [<span data-ttu-id="b08f7-111">使用者帳戶、授權和群組</span><span class="sxs-lookup"><span data-stu-id="b08f7-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="b08f7-112">如果您已安裝 Office 365 PowerShell 模組，並想要深入瞭解如何使用自動化命令來管理使用者帳戶、授權和群組，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-112">Start here if you have installed the Office 365 PowerShell modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="b08f7-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b08f7-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="b08f7-114">如果您已安裝 Office 365 PowerShell 模組並且想要使用自動化命令來執行 SharePoint Online 的管理，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-114">Start here if you have installed the Office 365 PowerShell modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="b08f7-115">Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="b08f7-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="b08f7-116">如果您想要使用自動化命令來管理 Exchange Online，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="b08f7-117">電子郵件遷移至 Office 365</span><span class="sxs-lookup"><span data-stu-id="b08f7-117">Email migration to Office 365</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="b08f7-118">如果您已安裝 Office 365 PowerShell 模組並且想要從現有系統移轉您的電子郵件，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-118">Start here if you have installed the Office 365 PowerShell modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="b08f7-119">安全性與合規性中心</span><span class="sxs-lookup"><span data-stu-id="b08f7-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="b08f7-120">如果您想要使用自動化命令來管理安全與規範中心，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="b08f7-121">委派存取許可權（一起）合作夥伴</span><span class="sxs-lookup"><span data-stu-id="b08f7-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="b08f7-122">如果您想要使用 Syndication 和 Cloud Solution Provider (CSP) 合作夥伴來管理 Office 365 客戶租用戶，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Office 365 customer tenants.</span></span>

- [<span data-ttu-id="b08f7-123">商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="b08f7-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="b08f7-124">如果您已安裝 Office 365 PowerShell 模組並且想要執行商務用 Skype Online 的管理，請從這裡開始。</span><span class="sxs-lookup"><span data-stu-id="b08f7-124">Start here if you have installed the Office 365 PowerShell modules and want to perform management of Skype for Business Online.</span></span>
