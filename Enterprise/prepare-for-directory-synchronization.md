---
title: 準備透過 Office 365 的目錄同步佈建使用者
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何準備將使用者佈建到 Office 365 使用目錄同步處理及使用此方法的長期效益。
ms.openlocfilehash: 0b2fe552911797337541bd25f0efcb81eab303bf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071029"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="569c9-103">準備透過 Office 365 的目錄同步佈建使用者</span><span class="sxs-lookup"><span data-stu-id="569c9-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="569c9-104">佈建使用目錄同步處理的使用者需要更多的規劃和準備比只管理您的公司或學校帳戶，直接在 Office 365 中。</span><span class="sxs-lookup"><span data-stu-id="569c9-104">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365.</span></span> <span data-ttu-id="569c9-105">額外的規劃和準備工作，才能確保您的內部部署 Active Directory 同步至 Azure Active Directory 正確處理。</span><span class="sxs-lookup"><span data-stu-id="569c9-105">The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory.</span></span> <span data-ttu-id="569c9-106">已新增至您的組織好處包括：</span><span class="sxs-lookup"><span data-stu-id="569c9-106">The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="569c9-107">減少您組織中的系統管理程式</span><span class="sxs-lookup"><span data-stu-id="569c9-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="569c9-108">（選用） 啟用單一登入案例</span><span class="sxs-lookup"><span data-stu-id="569c9-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="569c9-109">自動化 Office 365 中的帳戶變更</span><span class="sxs-lookup"><span data-stu-id="569c9-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="569c9-110">如需詳細的使用目錄同步處理優點的相關資訊，請參閱[目錄同步處理藍圖]( https://go.microsoft.com/fwlink/p/?LinkId=525398)，以及[了解 Office 365 身分識別與 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="569c9-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="569c9-111">若要判斷哪些案例是最適合您的組織，請檢閱[目錄整合工具比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)。</span><span class="sxs-lookup"><span data-stu-id="569c9-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="569c9-112">目錄清理工作</span><span class="sxs-lookup"><span data-stu-id="569c9-112">Directory cleanup tasks</span></span>

<span data-ttu-id="569c9-113">在您開始同步處理目錄之前，您需要清理目錄。</span><span class="sxs-lookup"><span data-stu-id="569c9-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="569c9-114">檢閱也[屬性同步處理到 Azure AD Connect 的 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)。</span><span class="sxs-lookup"><span data-stu-id="569c9-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="569c9-115">如果您不執行目錄清理，再進行同步處理，可以有重大的負面影響，在部署程序。</span><span class="sxs-lookup"><span data-stu-id="569c9-115">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="569c9-116">它可能需要數天，或甚至週，透過目錄同步處理，用來識別錯誤，以及重新同步處理的週期。</span><span class="sxs-lookup"><span data-stu-id="569c9-116">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="569c9-117">在內部部署目錄中，完成下列清理工作：</span><span class="sxs-lookup"><span data-stu-id="569c9-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="569c9-118">確定每個將被指派 Office 365 服務方案的使用者之**proxyAddresses**屬性中具有有效且唯一的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="569c9-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="569c9-119">**ProxyAddresses**屬性中移除任何重複的值。</span><span class="sxs-lookup"><span data-stu-id="569c9-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="569c9-120">如果可能，請確定將被指派 Office 365 服務方案的每個使用者在使用者的**使用者**物件中具有**userPrincipalName**屬性有效且唯一值。</span><span class="sxs-lookup"><span data-stu-id="569c9-120">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="569c9-121">為了最佳的同步處理體驗，請確定內部部署 Active Directory UPN 符合雲端 UPN。</span><span class="sxs-lookup"><span data-stu-id="569c9-121">For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN.</span></span> <span data-ttu-id="569c9-122">如果使用者沒有**userPrincipalName**屬性的值，**使用者**物件必須包含有效且唯一的**sAMAccountName**屬性值。</span><span class="sxs-lookup"><span data-stu-id="569c9-122">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="569c9-123">**UserPrincipalName**屬性中移除任何重複的值。</span><span class="sxs-lookup"><span data-stu-id="569c9-123">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="569c9-124">為了充分利用全域通訊清單 (GAL)，請務必下列屬性中的資訊正確：</span><span class="sxs-lookup"><span data-stu-id="569c9-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="569c9-125">givenName</span><span class="sxs-lookup"><span data-stu-id="569c9-125">givenName</span></span>
  - <span data-ttu-id="569c9-126">姓氏</span><span class="sxs-lookup"><span data-stu-id="569c9-126">surname</span></span>
  - <span data-ttu-id="569c9-127">displayName</span><span class="sxs-lookup"><span data-stu-id="569c9-127">displayName</span></span>
  - <span data-ttu-id="569c9-128">職稱</span><span class="sxs-lookup"><span data-stu-id="569c9-128">Job Title</span></span>
  - <span data-ttu-id="569c9-129">部門</span><span class="sxs-lookup"><span data-stu-id="569c9-129">Department</span></span>
  - <span data-ttu-id="569c9-130">辦公室</span><span class="sxs-lookup"><span data-stu-id="569c9-130">Office</span></span>
  - <span data-ttu-id="569c9-131">辦公室電話</span><span class="sxs-lookup"><span data-stu-id="569c9-131">Office Phone</span></span>
  - <span data-ttu-id="569c9-132">行動電話</span><span class="sxs-lookup"><span data-stu-id="569c9-132">Mobile Phone</span></span>
  - <span data-ttu-id="569c9-133">傳真號碼</span><span class="sxs-lookup"><span data-stu-id="569c9-133">Fax Number</span></span>
  - <span data-ttu-id="569c9-134">街道地址</span><span class="sxs-lookup"><span data-stu-id="569c9-134">Street Address</span></span>
  - <span data-ttu-id="569c9-135">城市</span><span class="sxs-lookup"><span data-stu-id="569c9-135">City</span></span>
  - <span data-ttu-id="569c9-136">州/省</span><span class="sxs-lookup"><span data-stu-id="569c9-136">State or Province</span></span>
  - <span data-ttu-id="569c9-137">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="569c9-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="569c9-138">國家或地區</span><span class="sxs-lookup"><span data-stu-id="569c9-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="569c9-139">目錄物件和屬性準備</span><span class="sxs-lookup"><span data-stu-id="569c9-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="569c9-140">成功執行目錄同步處理內部部署目錄和 Office 365 之間需要適當準備您的內部部署目錄屬性。</span><span class="sxs-lookup"><span data-stu-id="569c9-140">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared.</span></span> <span data-ttu-id="569c9-141">例如，您需要確保特定字元不使用同步處理與 Office 365 環境特定屬性。</span><span class="sxs-lookup"><span data-stu-id="569c9-141">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="569c9-142">未預期的字元，不會造成目錄同步處理失敗，但可能會傳回一則警告。</span><span class="sxs-lookup"><span data-stu-id="569c9-142">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="569c9-143">無效的字元將會造成目錄同步作業失敗。</span><span class="sxs-lookup"><span data-stu-id="569c9-143">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="569c9-144">目錄同步處理時，也會失敗如果某些 Active Directory 使用者具有一或多個重複屬性。</span><span class="sxs-lookup"><span data-stu-id="569c9-144">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes.</span></span> <span data-ttu-id="569c9-145">每位使用者必須具有唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="569c9-145">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="569c9-146">您需要準備的屬性都會列在這裡：</span><span class="sxs-lookup"><span data-stu-id="569c9-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="569c9-147">**附註：** 您也可以使用[IdFix 工具](install-and-run-idfix.md)進行此程序的生活更輕鬆。</span><span class="sxs-lookup"><span data-stu-id="569c9-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="569c9-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="569c9-148">**displayName**</span></span>
    
  - <span data-ttu-id="569c9-149">如果此屬性存在於使用者物件中，將會同步處理與 Office 365。</span><span class="sxs-lookup"><span data-stu-id="569c9-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="569c9-150">如果此屬性存在於使用者物件，必須是它的值。</span><span class="sxs-lookup"><span data-stu-id="569c9-150">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="569c9-151">亦即屬性必須不是空白。</span><span class="sxs-lookup"><span data-stu-id="569c9-151">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="569c9-152">字元數上限： 256</span><span class="sxs-lookup"><span data-stu-id="569c9-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="569c9-153">**givenName**</span><span class="sxs-lookup"><span data-stu-id="569c9-153">**givenName**</span></span>
    
  - <span data-ttu-id="569c9-154">如果此屬性存在於使用者物件中，會與 Office 365 同步處理，但 Office 365 不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="569c9-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="569c9-155">字元數上限： 64</span><span class="sxs-lookup"><span data-stu-id="569c9-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="569c9-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="569c9-156">**mail**</span></span>
    
  - <span data-ttu-id="569c9-157">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="569c9-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="569c9-158">如果沒有重複的值，會同步處理具有值的第一個使用者。</span><span class="sxs-lookup"><span data-stu-id="569c9-158">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="569c9-159">後續的使用者不會出現在 Office 365。</span><span class="sxs-lookup"><span data-stu-id="569c9-159">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="569c9-160">您必須修改 Office 365 中的其中一個值，或修改這兩個為了讓這兩個使用者出現在 Office 365 中的內部部署目錄中的值。</span><span class="sxs-lookup"><span data-stu-id="569c9-160">You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="569c9-161">**mailNickname**（Exchange 別名）</span><span class="sxs-lookup"><span data-stu-id="569c9-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="569c9-162">屬性值不能以句點 （.） 開頭。</span><span class="sxs-lookup"><span data-stu-id="569c9-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="569c9-163">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="569c9-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="569c9-164">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="569c9-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="569c9-165">多重值屬性</span><span class="sxs-lookup"><span data-stu-id="569c9-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="569c9-166">每個值的字元數上限： 256</span><span class="sxs-lookup"><span data-stu-id="569c9-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="569c9-167">屬性值不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="569c9-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="569c9-168">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="569c9-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="569c9-169">無效字元： \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="569c9-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="569c9-170">請注意，無效的字元會套用至下列類型的分隔符號字元和 「: 」，使得允許 SMTP:User@contso.com，但是 SMTP:user:M@contoso.com 不支援。</span><span class="sxs-lookup"><span data-stu-id="569c9-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="569c9-171">所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="569c9-171">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="569c9-172">如果重複或不想要的地址存在，請參閱[在 Exchange 中移除重複而不想要的 proxy 位址](https://go.microsoft.com/fwlink/?LinkId=293860)的說明主題。</span><span class="sxs-lookup"><span data-stu-id="569c9-172">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="569c9-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="569c9-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="569c9-174">字元數上限： 20</span><span class="sxs-lookup"><span data-stu-id="569c9-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="569c9-175">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="569c9-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="569c9-176">無效字元: [\"|，/: \< \> + =;？</span><span class="sxs-lookup"><span data-stu-id="569c9-176">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="569c9-177">\* ]</span><span class="sxs-lookup"><span data-stu-id="569c9-177"></span></span>
  - <span data-ttu-id="569c9-178">如果使用者具有**sAMAccountName**屬性無效但**userPrincipalName**屬性有效，Office 365 中建立使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="569c9-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="569c9-179">如果**sAMAccountName**和**userPrincipalName**均為無效，則必須更新內部部署 Active Directory **userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="569c9-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="569c9-180">**sn**（姓氏）</span><span class="sxs-lookup"><span data-stu-id="569c9-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="569c9-181">如果此屬性存在於使用者物件中，會與 Office 365 同步處理，但 Office 365 不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="569c9-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="569c9-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="569c9-182">**targetAddress**</span></span>
    
    <span data-ttu-id="569c9-183">此為必填入使用者的**targetAddress**屬性 (例如，SMTP:tom@contoso.com) 必須出現在 Office 365 GAL。</span><span class="sxs-lookup"><span data-stu-id="569c9-183">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="569c9-184">在第三方訊息移轉案例中，這會需要 Office 365 架構延伸模組的內部部署目錄。</span><span class="sxs-lookup"><span data-stu-id="569c9-184">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory.</span></span> <span data-ttu-id="569c9-185">Office 365 架構延伸模組也會新增其他有用的屬性，以管理填入使用從內部部署目錄的目錄同步處理工具的 Office 365 物件。</span><span class="sxs-lookup"><span data-stu-id="569c9-185">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory.</span></span> <span data-ttu-id="569c9-186">例如，將會新增**msExchHideFromAddressLists**屬性，來管理隱藏的信箱或通訊群組。</span><span class="sxs-lookup"><span data-stu-id="569c9-186">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="569c9-187">字元數上限： 256</span><span class="sxs-lookup"><span data-stu-id="569c9-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="569c9-188">屬性值不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="569c9-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="569c9-189">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="569c9-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="569c9-190">無效字元: \ \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="569c9-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="569c9-191">所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="569c9-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="569c9-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="569c9-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="569c9-193">**UserPrincipalName**屬性必須是網際網路樣式登入格式的使用者名稱，後面接著 at (@) 和網域名稱： 例如，user@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="569c9-193">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="569c9-194">所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="569c9-194">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="569c9-195">**UserPrincipalName**屬性的字元數目上限是 113。</span><span class="sxs-lookup"><span data-stu-id="569c9-195">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="569c9-196">為特定的字元數之前和之後，允許 at (@)、，如下所示：</span><span class="sxs-lookup"><span data-stu-id="569c9-196">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="569c9-197">是前面的使用者名稱的字元數上限 at (@): 64</span><span class="sxs-lookup"><span data-stu-id="569c9-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="569c9-198">最大數目的網域名稱字元 at (@): 48</span><span class="sxs-lookup"><span data-stu-id="569c9-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="569c9-199">無效字元: \ % &amp; \* + / =？</span><span class="sxs-lookup"><span data-stu-id="569c9-199">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="569c9-200">{ } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="569c9-200"></span></span>
  - <span data-ttu-id="569c9-201">母音也是無效的字元。</span><span class="sxs-lookup"><span data-stu-id="569c9-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="569c9-202">@ 字元所需要的是每個**userPrincipalName**值。</span><span class="sxs-lookup"><span data-stu-id="569c9-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="569c9-203">@ 字元不能是每個**userPrincipalName**值的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="569c9-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="569c9-204">使用者名稱無法當做尾以英文句點 （.）、 連字號 (&amp;)、 空格，或依 at (@)。</span><span class="sxs-lookup"><span data-stu-id="569c9-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="569c9-205">使用者名稱不得包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="569c9-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="569c9-206">必須使用可路由的網域。例如，無法使用 local 或 internal 的網域。</span><span class="sxs-lookup"><span data-stu-id="569c9-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="569c9-207">Unicode 字元會轉換為底線字元。</span><span class="sxs-lookup"><span data-stu-id="569c9-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="569c9-208">**userPrincipalName**不能包含任何重複的值在目錄中。</span><span class="sxs-lookup"><span data-stu-id="569c9-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="569c9-209">準備 userPrincipalName 屬性</span><span class="sxs-lookup"><span data-stu-id="569c9-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="569c9-210">Active Directory 被為了讓您的組織藉由使用 [ **sAMAccountName** ] 或 [ **userPrincipalName**登入您的目錄中的使用者。</span><span class="sxs-lookup"><span data-stu-id="569c9-210">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="569c9-211">同樣地，使用者可以使用他們的公司使用者主體名稱 (UPN) 登入 Office 365 或學校帳戶。</span><span class="sxs-lookup"><span data-stu-id="569c9-211">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="569c9-212">目錄同步處理會嘗試在 Azure Active Directory 中建立新的使用者使用您的內部部署目錄中的相同 UPN。</span><span class="sxs-lookup"><span data-stu-id="569c9-212">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory.</span></span> <span data-ttu-id="569c9-213">UPN 的格式類似的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="569c9-213">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="569c9-214">在 Office 365 UPN 是用來產生的電子郵件地址的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="569c9-214">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="569c9-215">很容易取得**userPrincipalName** (內部部署與 Azure Active Directory 中) 及**proxyAddresses**設定為不同的值中的主要電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="569c9-215">It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="569c9-216">當其設定為不同的值時，可以是系統管理員和使用者的混淆。</span><span class="sxs-lookup"><span data-stu-id="569c9-216">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="569c9-217">最好對齊這些屬性，以減少混淆。</span><span class="sxs-lookup"><span data-stu-id="569c9-217">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="569c9-218">若要符合需求的單一登入與 Active Directory Federation Services (AD FS) 2.0 中，您必須確定在 Azure Active Directory 和您在內部部署 Active Directory Upn 相符，而且所使用的有效的網域命名空間。</span><span class="sxs-lookup"><span data-stu-id="569c9-218">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="569c9-219">將替代的 UPN 尾碼新增至 AD DS</span><span class="sxs-lookup"><span data-stu-id="569c9-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="569c9-220">您可能需要新增至使用者的公司認證關聯的 Office 365 環境替代的 UPN 尾碼。</span><span class="sxs-lookup"><span data-stu-id="569c9-220">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="569c9-221">UPN 尾碼是 @ 字元右側的 UPN 部分。</span><span class="sxs-lookup"><span data-stu-id="569c9-221">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="569c9-222">用於單一登入的 UPN 可包含字母、數字、句號、虛線和底線，但不得包含其他字元類型。</span><span class="sxs-lookup"><span data-stu-id="569c9-222">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="569c9-223">如需有關如何將替代的 UPN 尾碼新增至 Active Directory 的詳細資訊，請參閱 <<c0>為目錄同步作業做好準備。</span><span class="sxs-lookup"><span data-stu-id="569c9-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="569c9-224">比對內部部署 UPN 與 Office 365 UPN</span><span class="sxs-lookup"><span data-stu-id="569c9-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="569c9-225">如果您已經設定目錄同步處理，Office 365 使用者的 UPN 可能不符合您在內部部署目錄服務中所定義的使用者的內部部署 UPN。</span><span class="sxs-lookup"><span data-stu-id="569c9-225">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service.</span></span> <span data-ttu-id="569c9-226">若使用者在網域經過驗證之前即獲得指派授權，就可能發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="569c9-226">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="569c9-227">若要修正此問題，請使用[PowerShell 修正 upn 重複的問題](https://go.microsoft.com/fwlink/p/?LinkId=396730)來更新使用者的 UPN，以確保 Office 365 UPN 相符的公司的使用者名稱和網域。</span><span class="sxs-lookup"><span data-stu-id="569c9-227">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="569c9-228">如果您要更新的內部部署目錄服務中的 UPN，可能會想要同步處理與 Azure Active Directory 身分識別，您需要變更內部部署之前，請先在 Office 365 中移除使用者的授權。</span><span class="sxs-lookup"><span data-stu-id="569c9-228">If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="569c9-229">另請參閱[如何準備目錄同步處理的非可路由網域 （例如.local 網域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="569c9-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="569c9-230">目錄整合工具</span><span class="sxs-lookup"><span data-stu-id="569c9-230">Directory integration tools</span></span>

<span data-ttu-id="569c9-231">目錄同步處理的目錄物件 （使用者、 群組和連絡人） 從內部部署 Active Directory 環境到 Office 365 目錄基礎結構，Azure Active Directory 同步處理。</span><span class="sxs-lookup"><span data-stu-id="569c9-231">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory.</span></span> <span data-ttu-id="569c9-232">如需可用的工具和功能的清單，請參閱[目錄整合工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。</span><span class="sxs-lookup"><span data-stu-id="569c9-232">See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality.</span></span> <span data-ttu-id="569c9-233">建議的工具是[Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956)。</span><span class="sxs-lookup"><span data-stu-id="569c9-233">The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956).</span></span> <span data-ttu-id="569c9-234">如需 Azure Active Directory Connect 的詳細資訊，請參閱 <<c0>整合內部部署身分識別與 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="569c9-234">For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="569c9-235">當使用者帳戶會與 Office 365 目錄同步處理，第一次時，它們會標示為未啟動。</span><span class="sxs-lookup"><span data-stu-id="569c9-235">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated.</span></span> <span data-ttu-id="569c9-236">無法傳送或接收電子郵件，以及它們不會耗用訂閱授權。</span><span class="sxs-lookup"><span data-stu-id="569c9-236">They cannot send or receive email, and they don't consume subscription licenses.</span></span> <span data-ttu-id="569c9-237">當您準備好要指派給特定使用者的 Office 365 訂閱時，您必須選取並啟動它們[指派給商務用 Office 365 中的使用者授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="569c9-237">When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="569c9-238">您也可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)指派授權。</span><span class="sxs-lookup"><span data-stu-id="569c9-238">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses.</span></span> <span data-ttu-id="569c9-239">自動化解決方案，請參閱[如何使用 PowerShell 來自動將授權指派給您的 Office 365 使用者](https://go.microsoft.com/fwlink/p?LinkID=329805)。</span><span class="sxs-lookup"><span data-stu-id="569c9-239">See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>