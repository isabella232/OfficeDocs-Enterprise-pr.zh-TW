---
title: 準備目錄同步處理至 Office 365
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
ms.openlocfilehash: 2361f4484f00d61fda90fed407bf3c287bbc2bc1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162466"
---
# <a name="prepare-for-directory-synchronization-to-office-365"></a><span data-ttu-id="8c6ba-103">準備目錄同步處理至 Office 365</span><span class="sxs-lookup"><span data-stu-id="8c6ba-103">Prepare for directory synchronization to Office 365</span></span>

<span data-ttu-id="8c6ba-104">混合式身分識別與目錄同步處理優點組織包括：</span><span class="sxs-lookup"><span data-stu-id="8c6ba-104">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="8c6ba-105">減少您組織中的系統管理程式</span><span class="sxs-lookup"><span data-stu-id="8c6ba-105">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="8c6ba-106">（選用） 啟用單一登入案例</span><span class="sxs-lookup"><span data-stu-id="8c6ba-106">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="8c6ba-107">自動化 Office 365 中的帳戶變更</span><span class="sxs-lookup"><span data-stu-id="8c6ba-107">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="8c6ba-108">如需詳細的使用目錄同步處理優點的相關資訊，請參閱[目錄同步處理藍圖]( https://go.microsoft.com/fwlink/p/?LinkId=525398)及[Office 365 的混合式身分識別](plan-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-108">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Office 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="8c6ba-109">不過，目錄同步處理需要規劃和準備，以確保您 Active Directory 網域服務 (AD DS) 同步處理至 Office 365 訂閱的 Azure Active Directory (Azure AD) 租用戶最少要有的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-109">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="8c6ba-110">請遵循下列步驟，為了獲得最佳結果順序。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-110">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="8c6ba-111">1.目錄清理工作</span><span class="sxs-lookup"><span data-stu-id="8c6ba-111">1. Directory cleanup tasks</span></span>

<span data-ttu-id="8c6ba-112">將 AD DS 同步處理到 Azure AD 租用戶之前，您需要清除您的 AD DS。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-112">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c6ba-113">如果您不執行 AD DS 清除，再進行同步處理，可以有重大的負面影響，在部署程序。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-113">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="8c6ba-114">它可能需要數天，或甚至週，透過目錄同步處理，用來識別錯誤，以及重新同步處理的週期。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-114">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="8c6ba-115">在 AD DS 中，完成下列清理工作每個使用者帳戶，將被指派 Office 365 授權：</span><span class="sxs-lookup"><span data-stu-id="8c6ba-115">In your AD DS, complete the following clean-up tasks for each user account that will be assigned an Office 365 license:</span></span>
  
1. <span data-ttu-id="8c6ba-116">請確定之**proxyAddresses**屬性中有效且唯一的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-116">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="8c6ba-117">**ProxyAddresses**屬性中移除任何重複的值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-117">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="8c6ba-118">如果可能的話，請確定使用者的**使用者**物件中的**userPrincipalName**屬性有效且唯一值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-118">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="8c6ba-119">為了最佳的同步處理體驗，請確定 AD DS UPN 符合 Azure AD UPN。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-119">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="8c6ba-120">如果使用者沒有**userPrincipalName**屬性的值，**使用者**物件必須包含有效且唯一的**sAMAccountName**屬性值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-120">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="8c6ba-121">**UserPrincipalName**屬性中移除任何重複的值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-121">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="8c6ba-122">為了充分利用全域通訊清單 (GAL)，請確定下列屬性中的 AD DS 使用者帳戶的資訊正確：</span><span class="sxs-lookup"><span data-stu-id="8c6ba-122">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="8c6ba-123">givenName</span><span class="sxs-lookup"><span data-stu-id="8c6ba-123">givenName</span></span>
  - <span data-ttu-id="8c6ba-124">姓氏</span><span class="sxs-lookup"><span data-stu-id="8c6ba-124">surname</span></span>
  - <span data-ttu-id="8c6ba-125">displayName</span><span class="sxs-lookup"><span data-stu-id="8c6ba-125">displayName</span></span>
  - <span data-ttu-id="8c6ba-126">職稱</span><span class="sxs-lookup"><span data-stu-id="8c6ba-126">Job Title</span></span>
  - <span data-ttu-id="8c6ba-127">部門</span><span class="sxs-lookup"><span data-stu-id="8c6ba-127">Department</span></span>
  - <span data-ttu-id="8c6ba-128">辦公室</span><span class="sxs-lookup"><span data-stu-id="8c6ba-128">Office</span></span>
  - <span data-ttu-id="8c6ba-129">辦公室電話</span><span class="sxs-lookup"><span data-stu-id="8c6ba-129">Office Phone</span></span>
  - <span data-ttu-id="8c6ba-130">行動電話</span><span class="sxs-lookup"><span data-stu-id="8c6ba-130">Mobile Phone</span></span>
  - <span data-ttu-id="8c6ba-131">傳真號碼</span><span class="sxs-lookup"><span data-stu-id="8c6ba-131">Fax Number</span></span>
  - <span data-ttu-id="8c6ba-132">街道地址</span><span class="sxs-lookup"><span data-stu-id="8c6ba-132">Street Address</span></span>
  - <span data-ttu-id="8c6ba-133">城市</span><span class="sxs-lookup"><span data-stu-id="8c6ba-133">City</span></span>
  - <span data-ttu-id="8c6ba-134">州/省</span><span class="sxs-lookup"><span data-stu-id="8c6ba-134">State or Province</span></span>
  - <span data-ttu-id="8c6ba-135">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="8c6ba-135">Zip or Postal Code</span></span>
  - <span data-ttu-id="8c6ba-136">國家或地區</span><span class="sxs-lookup"><span data-stu-id="8c6ba-136">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="8c6ba-137">2.目錄物件和屬性準備</span><span class="sxs-lookup"><span data-stu-id="8c6ba-137">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="8c6ba-138">成功執行目錄同步處理 AD DS 與 Office 365 之間需要適當準備您的 AD DS 屬性。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-138">Successful directory synchronization between your AD DS and Office 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="8c6ba-139">例如，您需要確保特定字元不使用同步處理與 Office 365 環境特定屬性。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-139">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="8c6ba-140">未預期的字元，不會造成目錄同步處理失敗，但可能會傳回一則警告。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-140">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="8c6ba-141">無效的字元將會造成目錄同步作業失敗。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-141">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="8c6ba-142">目錄同步處理時，也會失敗如果某些 AD DS 使用者具有一或多個重複屬性。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-142">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="8c6ba-143">每位使用者必須具有唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-143">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="8c6ba-144">您需要準備的屬性都會列在這裡：</span><span class="sxs-lookup"><span data-stu-id="8c6ba-144">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="8c6ba-145">**displayName**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-145">**displayName**</span></span>
    
  - <span data-ttu-id="8c6ba-146">如果此屬性存在於使用者物件中，將會同步處理與 Office 365。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-146">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="8c6ba-147">如果此屬性存在於使用者物件，必須是它的值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-147">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="8c6ba-148">亦即屬性必須不是空白。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-148">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="8c6ba-149">字元數上限： 256</span><span class="sxs-lookup"><span data-stu-id="8c6ba-149">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="8c6ba-150">**givenName**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-150">**givenName**</span></span>
    
  - <span data-ttu-id="8c6ba-151">如果此屬性存在於使用者物件中，會與 Office 365 同步處理，但 Office 365 不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-151">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="8c6ba-152">字元數上限： 64</span><span class="sxs-lookup"><span data-stu-id="8c6ba-152">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="8c6ba-153">**mail**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-153">**mail**</span></span>
    
  - <span data-ttu-id="8c6ba-154">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-154">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="8c6ba-155">如果沒有重複的值，會同步處理具有值的第一個使用者。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-155">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="8c6ba-156">後續的使用者不會出現在 Office 365。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-156">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="8c6ba-157">您必須修改 Office 365 中的其中一個值，或修改這兩個 AD DS 中兩個使用者在 Office 365 中顯示的順序中的值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-157">You must modify either the value in Office 365 or modify both of the values in AD DS in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="8c6ba-158">**mailNickname**（Exchange 別名）</span><span class="sxs-lookup"><span data-stu-id="8c6ba-158">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="8c6ba-159">屬性值不能以句點 （.） 開頭。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-159">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="8c6ba-160">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-160">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="8c6ba-161">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-161">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="8c6ba-162">多重值屬性</span><span class="sxs-lookup"><span data-stu-id="8c6ba-162">Multiple-value attribute</span></span>
  - <span data-ttu-id="8c6ba-163">每個值的字元數上限： 256</span><span class="sxs-lookup"><span data-stu-id="8c6ba-163">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="8c6ba-164">屬性值不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-164">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="8c6ba-165">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-165">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="8c6ba-166">無效字元： \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="8c6ba-166">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="8c6ba-167">請注意，無效的字元會套用至下列類型的分隔符號字元和 「: 」，使得允許 SMTP:User@contso.com，但是 SMTP:user:M@contoso.com 不支援。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-167">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="8c6ba-168">所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-168">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="8c6ba-169">如果重複或不想要的地址存在，請參閱[在 Exchange 中移除重複而不想要的 proxy 位址](https://go.microsoft.com/fwlink/?LinkId=293860)的說明主題。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-169">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="8c6ba-170">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-170">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="8c6ba-171">字元數上限： 20</span><span class="sxs-lookup"><span data-stu-id="8c6ba-171">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="8c6ba-172">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-172">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="8c6ba-173">無效字元: [\"|，/: \< \> + =;？</span><span class="sxs-lookup"><span data-stu-id="8c6ba-173">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="8c6ba-174">\* ]</span><span class="sxs-lookup"><span data-stu-id="8c6ba-174"></span></span>
  - <span data-ttu-id="8c6ba-175">如果使用者具有**sAMAccountName**屬性無效但**userPrincipalName**屬性有效，Office 365 中建立使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-175">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="8c6ba-176">如果**sAMAccountName**和**userPrincipalName**均為無效，則必須更新 AD DS **userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-176">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="8c6ba-177">**sn**（姓氏）</span><span class="sxs-lookup"><span data-stu-id="8c6ba-177">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="8c6ba-178">如果此屬性存在於使用者物件中，會與 Office 365 同步處理，但 Office 365 不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-178">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="8c6ba-179">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-179">**targetAddress**</span></span>
    
    <span data-ttu-id="8c6ba-180">此為必填入使用者的**targetAddress**屬性 (例如，SMTP:tom@contoso.com) 必須出現在 Office 365 GAL。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-180">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="8c6ba-181">在第三方訊息移轉案例中，這會需要 Office 365 架構延伸模組的 AD DS。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-181">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the AD DS.</span></span> <span data-ttu-id="8c6ba-182">Office 365 架構延伸模組也會新增其他有用的屬性，以管理填入使用目錄同步作業工具，從 AD DS 的 Office 365 物件。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-182">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="8c6ba-183">例如，將會新增**msExchHideFromAddressLists**屬性，來管理隱藏的信箱或通訊群組。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-183">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="8c6ba-184">字元數上限： 256</span><span class="sxs-lookup"><span data-stu-id="8c6ba-184">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="8c6ba-185">屬性值不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-185">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="8c6ba-186">屬性值必須是唯一在目錄內。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-186">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="8c6ba-187">無效字元: \ \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="8c6ba-187">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="8c6ba-188">所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-188">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="8c6ba-189">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="8c6ba-189">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="8c6ba-190">**UserPrincipalName**屬性必須是網際網路樣式登入格式的使用者名稱，後面接著 at (@) 和網域名稱： 例如，user@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-190">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="8c6ba-191">所有 Simple Mail Transport Protocol (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="8c6ba-192">**UserPrincipalName**屬性的字元數目上限是 113。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-192">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="8c6ba-193">為特定的字元數之前和之後，允許 at (@)、，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ba-193">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="8c6ba-194">是前面的使用者名稱的字元數上限 at (@): 64</span><span class="sxs-lookup"><span data-stu-id="8c6ba-194">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="8c6ba-195">最大數目的網域名稱字元 at (@): 48</span><span class="sxs-lookup"><span data-stu-id="8c6ba-195">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="8c6ba-196">無效字元: \ % &amp; \* + / =？</span><span class="sxs-lookup"><span data-stu-id="8c6ba-196">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="8c6ba-197">{ } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="8c6ba-197"></span></span>
  - <span data-ttu-id="8c6ba-198">母音也是無效的字元。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-198">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="8c6ba-199">@ 字元所需要的是每個**userPrincipalName**值。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-199">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="8c6ba-200">@ 字元不能是每個**userPrincipalName**值的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-200">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="8c6ba-201">使用者名稱無法當做尾以英文句點 （.）、 連字號 (&amp;)、 空格，或依 at (@)。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-201">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="8c6ba-202">使用者名稱不得包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-202">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="8c6ba-203">必須使用可路由的網域。例如，無法使用 local 或 internal 的網域。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-203">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="8c6ba-204">Unicode 字元會轉換為底線字元。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-204">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="8c6ba-205">**userPrincipalName**不能包含任何重複的值在目錄中。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-205">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="8c6ba-206">請參閱[使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)使用 IdFIx 工具來識別屬性的 AD DS 中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-206">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="2-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="8c6ba-207">2.準備 userPrincipalName 屬性</span><span class="sxs-lookup"><span data-stu-id="8c6ba-207">2. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="8c6ba-208">Active Directory 被為了讓您的組織藉由使用 [ **sAMAccountName** ] 或 [ **userPrincipalName**登入您的目錄中的使用者。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-208">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="8c6ba-209">同樣地，使用者可以使用他們的公司使用者主體名稱 (UPN) 登入 Office 365 或學校帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-209">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="8c6ba-210">目錄同步處理會嘗試在 Azure Active Directory 中建立新的使用者使用位於 AD SD.相同 UPN</span><span class="sxs-lookup"><span data-stu-id="8c6ba-210">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD SD.</span></span> <span data-ttu-id="8c6ba-211">UPN 的格式類似的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-211">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="8c6ba-212">在 Office 365 UPN 是用來產生的電子郵件地址的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-212">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="8c6ba-213">很容易在**proxyAddresses**設定為不同的值取得**userPrincipalName** （AD DS 中和 Azure AD） 和主要電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-213">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="8c6ba-214">當其設定為不同的值時，可以是系統管理員和使用者的混淆。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-214">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="8c6ba-215">最好對齊這些屬性，以減少混淆。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-215">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="8c6ba-216">若要符合需求的單一登入與 Active Directory Federation Services (AD FS) 2.0 中，您需要確保在 Azure Active Directory 與 AD DS Upn 相符，而且所使用的有效的網域命名空間。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-216">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="8c6ba-217">4.將替代的 UPN 尾碼新增至 AD DS</span><span class="sxs-lookup"><span data-stu-id="8c6ba-217">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="8c6ba-218">您可能需要新增至使用者的公司認證關聯的 Office 365 環境替代的 UPN 尾碼。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-218">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="8c6ba-219">UPN 尾碼是 @ 字元右側的 UPN 部分。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-219">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="8c6ba-220">用於單一登入的 UPN 可包含字母、數字、句號、虛線和底線，但不得包含其他字元類型。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-220">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="8c6ba-221">如需有關如何將替代的 UPN 尾碼新增至 Active Directory 的詳細資訊，請參閱 <<c0>為目錄同步作業做好準備。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-221">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-office-365-upn"></a><span data-ttu-id="8c6ba-222">5.符合 AD DS UPN 與 Office 365 UPN</span><span class="sxs-lookup"><span data-stu-id="8c6ba-222">5. Match the AD DS UPN with the Office 365 UPN</span></span>

<span data-ttu-id="8c6ba-223">如果您已經設定目錄同步處理，Office 365 使用者的 UPN 可能不符合您的 AD DS 中定義的使用者的 AD DS UPN。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-223">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="8c6ba-224">若使用者在網域經過驗證之前即獲得指派授權，就可能發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-224">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="8c6ba-225">若要修正此問題，請使用[PowerShell 修正 upn 重複的問題](https://go.microsoft.com/fwlink/p/?LinkId=396730)來更新使用者的 UPN，以確保 Office 365 UPN 相符的公司的使用者名稱和網域。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-225">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="8c6ba-226">如果您要更新的 AD DS 中的 UPN，可能會想要同步處理與 Azure Active Directory 身分識別，您需要在 Office 365 中移除使用者的授權之前在 AD DS 中進行的變更。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-226">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="8c6ba-227">也請參閱[How to 準備目錄同步處理的非可路由網域 （例如.local 網域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-227">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="8c6ba-228">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8c6ba-228">Next steps</span></span>

<span data-ttu-id="8c6ba-229">請參閱[使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)以協助您修正前目錄同步處理 AD DS 的屬性中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-229">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="8c6ba-230">如果您已更正 IdFix 工具用來識別的所有屬性錯誤，並已完成步驟 1 到 5 上述，請參閱 <<c0>設定目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="8c6ba-230">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
