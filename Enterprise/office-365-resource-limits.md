---
title: Office 365 資源限制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 摘要： 資源的相關資訊的 Office 365 內的各種應用程式限制。
ms.openlocfilehash: ece25deece5a0f2eec7ab0295a2af68f47e1c50c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067307"
---
# <a name="resource-limits"></a><span data-ttu-id="1f480-103">資源限制</span><span class="sxs-lookup"><span data-stu-id="1f480-103">Resource Limits</span></span>

<span data-ttu-id="1f480-104">使用配額 （限制） 與節流設定，會強制執行資源限制。</span><span class="sxs-lookup"><span data-stu-id="1f480-104">Resource limits are enforced using quotas (limits) and throttling.</span></span> <span data-ttu-id="1f480-105">Azure Active Directory 和個別的 Office 365 服務使用兩者。</span><span class="sxs-lookup"><span data-stu-id="1f480-105">Azure Active Directory and the individual Office 365 services use both.</span></span> <span data-ttu-id="1f480-106">限制都是特定的服務，並變更經過一段時間，也會加入新功能。</span><span class="sxs-lookup"><span data-stu-id="1f480-106">Limits are service-specific and change over time as new capabilities are added.</span></span> <span data-ttu-id="1f480-107">如需各種服務的目前限制的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1f480-107">For details on the current limits for the various services, see the following topics:</span></span>
- [<span data-ttu-id="1f480-108">Azure Active Directory 服務限制及限制</span><span class="sxs-lookup"><span data-stu-id="1f480-108">Azure Active Directory service limits and restrictions</span></span>](https://msdn.microsoft.com/en-us/library/azure/dn764971.aspx)
- [<span data-ttu-id="1f480-109">Exchange Online 限制</span><span class="sxs-lookup"><span data-stu-id="1f480-109">Exchange Online Limits</span></span>](https://technet.microsoft.com/en-us/library/exchange-online-limits.aspx)
- [<span data-ttu-id="1f480-110">Exchange Online Protection 限制</span><span class="sxs-lookup"><span data-stu-id="1f480-110">Exchange Online Protection Limits</span></span>](https://technet.microsoft.com/en-us/library/exchange-online-protection-limits.aspx)
- [<span data-ttu-id="1f480-111">SharePoint Online 的軟體界限及限制</span><span class="sxs-lookup"><span data-stu-id="1f480-111">SharePoint Online software boundaries and limits</span></span>](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [<span data-ttu-id="1f480-112">Skype 商務限制</span><span class="sxs-lookup"><span data-stu-id="1f480-112">Skype for Business Limits</span></span>](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx)
- [<span data-ttu-id="1f480-113">Yammer REST API 和流量限制</span><span class="sxs-lookup"><span data-stu-id="1f480-113">Yammer REST API and Rate Limits</span></span>](https://developer.yammer.com/docs/rest-api-rate-limits)
- [<span data-ttu-id="1f480-114">在 Sway 中的檔案大小限制</span><span class="sxs-lookup"><span data-stu-id="1f480-114">File Size Limits in Sway</span></span>](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

<span data-ttu-id="1f480-115">除了這些限制，幾個節流機制可用整個 Azure Active Directory 和 Office 365。</span><span class="sxs-lookup"><span data-stu-id="1f480-115">In addition to these limits, several throttling mechanisms are used throughout Azure Active Directory and Office 365.</span></span> <span data-ttu-id="1f480-116">在服務中的節流會特別重要，，假設在 Microsoft 資料中心的網路資源已針對廣泛使用之服務的客戶的進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="1f480-116">Throttling within the service is especially important, given that network resources in Microsoft's datacenters are optimized for the broad set of customers that use the services.</span></span> <span data-ttu-id="1f480-117">節流機制包括：</span><span class="sxs-lookup"><span data-stu-id="1f480-117">Throttling mechanisms include:</span></span>
- <span data-ttu-id="1f480-118">Azure Active Directory 和 Office 365 功能使用者層級節流，其中的交易或 （由指令碼或程式碼） 可以執行由單一使用者的並行通話數目限制。</span><span class="sxs-lookup"><span data-stu-id="1f480-118">Azure Active Directory and Office 365 feature user-level throttling, which limit the number of transactions or concurrent calls (by script or code) that can be performed by a single user.</span></span>
- <span data-ttu-id="1f480-119">此為預設節流原則的 PowerShell 被指派給在租用戶建立每個租用戶。</span><span class="sxs-lookup"><span data-stu-id="1f480-119">A default PowerShell throttling policy is assigned to each tenant at tenant creation.</span></span> <span data-ttu-id="1f480-120">這些設定會影響其他項目，例如單一系統管理員所能開啟的同時 PowerShell 工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="1f480-120">These settings affect other items, such as the maximum number of simultaneous PowerShell sessions that can be opened by a single administrator.</span></span>
- <span data-ttu-id="1f480-121">每個 Exchange Online 客戶已針對 EWS 用戶端作業，調整預設 Exchange Web 服務 (EWS) 原則和節流設定，套用至所有 Outlook 用戶端。</span><span class="sxs-lookup"><span data-stu-id="1f480-121">Each Exchange Online customer has a default Exchange Web Services (EWS) policy that is tuned for EWS client operations, and throttling that applies to all Outlook clients.</span></span>
