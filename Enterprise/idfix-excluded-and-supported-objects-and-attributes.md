---
title: IdFix 已排除和支援的物件和屬性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出 IdFix 工具排除並支援的屬性。
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711573"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="36506-103">IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="36506-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="36506-104">*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="36506-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="36506-105">IdFix 維護兩組規則;多承租人和專用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="36506-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="36506-106">此時，這兩個規則集會從其搜尋中排除相同的物件、屬性和屬性值。</span><span class="sxs-lookup"><span data-stu-id="36506-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="36506-107">在未來的版本中可能會有所變更。</span><span class="sxs-lookup"><span data-stu-id="36506-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="36506-108">IdFix 所使用的多租使用者和專用錯誤排除</span><span class="sxs-lookup"><span data-stu-id="36506-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="36506-109">本節列出 IdFix 從其目錄搜尋中排除的物件、屬性及值。</span><span class="sxs-lookup"><span data-stu-id="36506-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="36506-110">星號（ \* ）是可以取代其他字元的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="36506-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="36506-111">在 IdFix 搜尋期間排除的物件、屬性及值</span><span class="sxs-lookup"><span data-stu-id="36506-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="36506-112">**排除**</span><span class="sxs-lookup"><span data-stu-id="36506-112">**Exclusion**</span></span>|<span data-ttu-id="36506-113">**範例**</span><span class="sxs-lookup"><span data-stu-id="36506-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36506-114">Admini\*</span><span class="sxs-lookup"><span data-stu-id="36506-114">Admini\*</span></span> |<span data-ttu-id="36506-115">系統管理員</span><span class="sxs-lookup"><span data-stu-id="36506-115">Administrator</span></span> |
|<span data-ttu-id="36506-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="36506-116">CAS_{\*</span></span>  |<span data-ttu-id="36506-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="36506-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="36506-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="36506-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="36506-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="36506-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="36506-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="36506-120">FederatedEmail\*</span></span> |<span data-ttu-id="36506-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="36506-121">FederatedEmail.</span></span> <span data-ttu-id="36506-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="36506-122">*GUID*</span></span> |
|<span data-ttu-id="36506-123">客人\*</span><span class="sxs-lookup"><span data-stu-id="36506-123">Guest\*</span></span> ||
|<span data-ttu-id="36506-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="36506-124">HTTPConnector\*</span></span>  |<span data-ttu-id="36506-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="36506-125">HTTPConnector</span></span> |
|<span data-ttu-id="36506-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="36506-126">krbtgt\*</span></span> |<span data-ttu-id="36506-127">ms-DS-KrbTgt-連結</span><span class="sxs-lookup"><span data-stu-id="36506-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="36506-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="36506-128">iusr_\*</span></span> |<span data-ttu-id="36506-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="36506-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="36506-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="36506-130">iwam\*</span></span>  |<span data-ttu-id="36506-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="36506-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="36506-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="36506-132">msol\*</span></span> |<span data-ttu-id="36506-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="36506-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="36506-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="36506-134">support_\*</span></span> ||
|<span data-ttu-id="36506-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="36506-135">SystemMailbox\*</span></span> |<span data-ttu-id="36506-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="36506-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="36506-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="36506-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="36506-138">distinguishedName 包含 "\0ACNF："</span><span class="sxs-lookup"><span data-stu-id="36506-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="36506-139">"\0ACNF： *GUID* "</span><span class="sxs-lookup"><span data-stu-id="36506-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="36506-140">物件包含 IsCriticalSystemObject 屬性</span><span class="sxs-lookup"><span data-stu-id="36506-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="36506-141">請參閱[屬性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="36506-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="36506-142">由 IdFix 檢查的多承租人和專用物件及屬性</span><span class="sxs-lookup"><span data-stu-id="36506-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="36506-143">[使用 IdFix 工具，準備目錄365屬性](prepare-directory-attributes-for-synch-with-idfix.md)中的「目錄物件及屬性準備」一節中的「目錄物件及屬性準備」一節中所述的 IdFix 所檢查的錯誤屬性。</span><span class="sxs-lookup"><span data-stu-id="36506-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Microsoft 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

