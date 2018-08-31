---
title: IdFix 已排除和支援的物件和屬性
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出已排除和支援 IdFix 工具的屬性。
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540078"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="427c3-103">IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="427c3-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="427c3-p101">IdFix 維護兩組規則；多租用戶和 專用的/ITAR。這兩個規則集目前會在其搜尋中排除相同的物件、屬性和屬性值。這可能會在未來的版本中變更。</span><span class="sxs-lookup"><span data-stu-id="427c3-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="427c3-107">IdFix 所使用的多租用戶和 專用的 錯誤排除項目</span><span class="sxs-lookup"><span data-stu-id="427c3-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="427c3-p102">本節列出物件、 屬性和 IdFix 應從其的目錄搜尋中排除的值。星號 (\*) 可以為其他任何字元取代為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="427c3-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="427c3-110">在 IdFix 搜尋期間排除的物件、屬性和值</span><span class="sxs-lookup"><span data-stu-id="427c3-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="427c3-111">**排除**</span><span class="sxs-lookup"><span data-stu-id="427c3-111">**Exclusion**</span></span>|<span data-ttu-id="427c3-112">**範例**</span><span class="sxs-lookup"><span data-stu-id="427c3-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="427c3-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="427c3-113">Admini\*</span></span> |<span data-ttu-id="427c3-114">系統管理員</span><span class="sxs-lookup"><span data-stu-id="427c3-114">Administrator</span></span> |
|<span data-ttu-id="427c3-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="427c3-115">CAS_{\*</span></span>  |<span data-ttu-id="427c3-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="427c3-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="427c3-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="427c3-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="427c3-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="427c3-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="427c3-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="427c3-119">FederatedEmail\*</span></span> |<span data-ttu-id="427c3-p103">FederatedEmail。*GUID*</span><span class="sxs-lookup"><span data-stu-id="427c3-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="427c3-122">來賓\*</span><span class="sxs-lookup"><span data-stu-id="427c3-122">Guest\*</span></span> ||
|<span data-ttu-id="427c3-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="427c3-123">HTTPConnector\*</span></span>  |<span data-ttu-id="427c3-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="427c3-124">HTTPConnector</span></span> |
|<span data-ttu-id="427c3-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="427c3-125">krbtgt\*</span></span> |<span data-ttu-id="427c3-126">ms DS-KrbTgt 連結</span><span class="sxs-lookup"><span data-stu-id="427c3-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="427c3-127">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="427c3-127">iusr_\*</span></span> |<span data-ttu-id="427c3-128">iusr_ *machinename 資料*</span><span class="sxs-lookup"><span data-stu-id="427c3-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="427c3-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="427c3-129">iwam\*</span></span>  |<span data-ttu-id="427c3-130">IWAM_ *machinename 資料*</span><span class="sxs-lookup"><span data-stu-id="427c3-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="427c3-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="427c3-131">msol\*</span></span> |<span data-ttu-id="427c3-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="427c3-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="427c3-133">support_\*</span><span class="sxs-lookup"><span data-stu-id="427c3-133">support_\*</span></span> ||
|<span data-ttu-id="427c3-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="427c3-134">SystemMailbox\*</span></span> |<span data-ttu-id="427c3-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="427c3-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="427c3-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="427c3-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="427c3-137">distinguishedName 包含"\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="427c3-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="427c3-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="427c3-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="427c3-139">物件包含 IsCriticalSystemObject 屬性</span><span class="sxs-lookup"><span data-stu-id="427c3-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="427c3-140">請參閱[isCriticalSystemObject 屬性](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="427c3-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="427c3-141">IdFix 所檢查的多租用戶和 專用的 物件和屬性</span><span class="sxs-lookup"><span data-stu-id="427c3-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="427c3-142">會檢查有錯誤 IdFix 所屬性"目錄物件和屬性準備 」 在[進行同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)] 區段中所述。</span><span class="sxs-lookup"><span data-stu-id="427c3-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

