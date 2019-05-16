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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出已排除和 IdFix 工具所支援的屬性。
ms.openlocfilehash: bf88fea3592860a89d69717177593b6553318ee4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067269"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="24620-103">IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="24620-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="24620-104">有兩組 IdFix; 所維護的規則多租用戶和專用 /ITAR。</span><span class="sxs-lookup"><span data-stu-id="24620-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="24620-105">在這個階段中，兩個規則設定相同的物件、 屬性和屬性值從搜尋中排除其。</span><span class="sxs-lookup"><span data-stu-id="24620-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="24620-106">這可能會變更在未來版本。</span><span class="sxs-lookup"><span data-stu-id="24620-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="24620-107">多重租用戶和專用的 IdFix 所使用的錯誤排除項目</span><span class="sxs-lookup"><span data-stu-id="24620-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="24620-108">此章節將列出物件、 屬性和 IdFix 排除其搜尋目錄的值。</span><span class="sxs-lookup"><span data-stu-id="24620-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="24620-109">星號 (\*) 可以針對其他字元取代為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="24620-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="24620-110">物件、 屬性和 IdFix 搜尋期間排除的值</span><span class="sxs-lookup"><span data-stu-id="24620-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="24620-111">**排除項目**</span><span class="sxs-lookup"><span data-stu-id="24620-111">**Exclusion**</span></span>|<span data-ttu-id="24620-112">**範例**</span><span class="sxs-lookup"><span data-stu-id="24620-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="24620-113">系統管理員\*</span><span class="sxs-lookup"><span data-stu-id="24620-113">Admini\*</span></span> |<span data-ttu-id="24620-114">系統管理員</span><span class="sxs-lookup"><span data-stu-id="24620-114">Administrator</span></span> |
|<span data-ttu-id="24620-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="24620-115">CAS_{\*</span></span>  |<span data-ttu-id="24620-116">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="24620-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="24620-117">Discoverysearchmailbox 為開頭\*</span><span class="sxs-lookup"><span data-stu-id="24620-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="24620-118">Discoverysearchmailbox 為開頭</span><span class="sxs-lookup"><span data-stu-id="24620-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="24620-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="24620-119">FederatedEmail\*</span></span> |<span data-ttu-id="24620-120">FederatedEmail。</span><span class="sxs-lookup"><span data-stu-id="24620-120">FederatedEmail.</span></span> <span data-ttu-id="24620-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="24620-121">*GUID*</span></span> |
|<span data-ttu-id="24620-122">來賓\*</span><span class="sxs-lookup"><span data-stu-id="24620-122">Guest\*</span></span> ||
|<span data-ttu-id="24620-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="24620-123">HTTPConnector\*</span></span>  |<span data-ttu-id="24620-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="24620-124">HTTPConnector</span></span> |
|<span data-ttu-id="24620-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="24620-125">krbtgt\*</span></span> |<span data-ttu-id="24620-126">ms DS-KrbTgt 連結</span><span class="sxs-lookup"><span data-stu-id="24620-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="24620-127">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="24620-127">iusr_\*</span></span> |<span data-ttu-id="24620-128">iusr_ *machinename 資料*</span><span class="sxs-lookup"><span data-stu-id="24620-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="24620-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="24620-129">iwam\*</span></span>  |<span data-ttu-id="24620-130">IWAM_ *machinename 資料*</span><span class="sxs-lookup"><span data-stu-id="24620-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="24620-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="24620-131">msol\*</span></span> |<span data-ttu-id="24620-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="24620-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="24620-133">support_\*</span><span class="sxs-lookup"><span data-stu-id="24620-133">support_\*</span></span> ||
|<span data-ttu-id="24620-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="24620-134">SystemMailbox\*</span></span> |<span data-ttu-id="24620-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="24620-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="24620-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="24620-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="24620-137">distinguishedName 包含 「 \0ACNF: 」</span><span class="sxs-lookup"><span data-stu-id="24620-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="24620-138">「 \0ACNF: *GUID* 」</span><span class="sxs-lookup"><span data-stu-id="24620-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="24620-139">物件包含 IsCriticalSystemObject 屬性</span><span class="sxs-lookup"><span data-stu-id="24620-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="24620-140">請參閱 <<c0>屬性 isCriticalSystemObject。</span><span class="sxs-lookup"><span data-stu-id="24620-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="24620-141">多重租用戶和專用的物件和 IdFix 所檢查的屬性</span><span class="sxs-lookup"><span data-stu-id="24620-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="24620-142">在部分 」 目錄物件和屬性準備 」 中[進行同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)會描述 IdFix 所檢查有錯誤的屬性。</span><span class="sxs-lookup"><span data-stu-id="24620-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

