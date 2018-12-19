---
title: 準備透過 Office 365 的目錄同步佈建使用者
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 說明如何準備使用目錄同步作業及使用此方法的長期效益佈建到 Office 365 的使用者。
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371117"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="cdd77-103">準備透過 Office 365 的目錄同步佈建使用者</span><span class="sxs-lookup"><span data-stu-id="cdd77-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="cdd77-p101">佈建使用目錄同步處理的使用者需要更多的規劃和準備比只管理 Office 365 中直接您工作或學校帳戶。其他的規劃和準備工作所需以確保您的內部部署 Active Directory 同步至 Azure Active Directory 正確處理。若您的組織要新增的好處包括：</span><span class="sxs-lookup"><span data-stu-id="cdd77-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="cdd77-107">減少您組織中的系統管理程式</span><span class="sxs-lookup"><span data-stu-id="cdd77-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="cdd77-108">（選用） 啟用單一登入案例</span><span class="sxs-lookup"><span data-stu-id="cdd77-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="cdd77-109">自動化 Office 365 中的帳戶變更</span><span class="sxs-lookup"><span data-stu-id="cdd77-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="cdd77-110">如需使用目錄同步處理的優點的相關資訊，請參閱[目錄同步處理藍圖]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[了解 Office 365 身分識別和 Azure Active Directory。](about-office-365-identity.md)</span><span class="sxs-lookup"><span data-stu-id="cdd77-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="cdd77-111">若要決定哪些案例是最適合您的組織，請檢閱[目錄整合工具比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="cdd77-112">目錄清理工作</span><span class="sxs-lookup"><span data-stu-id="cdd77-112">Directory cleanup tasks</span></span>

<span data-ttu-id="cdd77-113">開始同步處理目錄之前，您需要清理目錄。</span><span class="sxs-lookup"><span data-stu-id="cdd77-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="cdd77-114">請檢閱[屬性由 Azure AD 連接的 Azure Active directory 同步處理](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="cdd77-p102">如果您不執行目錄清理同步處理之前，可以是嚴重的負面影響的部署程序。它可能需要數天，或偶數週，透過目錄同步處理，用來識別錯誤及重新同步處理的週期。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="cdd77-117">在內部部署目錄中，完成下列清理工作：</span><span class="sxs-lookup"><span data-stu-id="cdd77-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="cdd77-118">請確保每位將被指派 Office 365 服務方案的使用者在 **proxyAddresses** 屬性中都具有一個有效且唯一的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="cdd77-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="cdd77-119">移除 **proxyAddresses** 屬性中的任何重複值。</span><span class="sxs-lookup"><span data-stu-id="cdd77-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="cdd77-p103">請儘可能確定將被指派 Office 365 服務方案的每個使用者在使用者的**使用者**物件中具有**userPrincipalName**屬性有效且唯一值。最佳的同步處理體驗，請確定內部部署 Active Directory UPN 符合雲端 UPN。如果使用者不具有**userPrincipalName**屬性的值，**使用者**物件必須包含有效且唯一的**sAMAccountName**屬性值。**UserPrincipalName**屬性中移除任何重複值。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="cdd77-124">為了充分利用全域通訊清單 (GAL)，請確定下列屬性中的資訊正確：</span><span class="sxs-lookup"><span data-stu-id="cdd77-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="cdd77-125">givenName </span><span class="sxs-lookup"><span data-stu-id="cdd77-125">givenName</span></span>
  - <span data-ttu-id="cdd77-126">surname</span><span class="sxs-lookup"><span data-stu-id="cdd77-126">surname</span></span>
  - <span data-ttu-id="cdd77-127">displayName</span><span class="sxs-lookup"><span data-stu-id="cdd77-127">displayName</span></span>
  - <span data-ttu-id="cdd77-128">職稱</span><span class="sxs-lookup"><span data-stu-id="cdd77-128">Job Title</span></span>
  - <span data-ttu-id="cdd77-129">部門</span><span class="sxs-lookup"><span data-stu-id="cdd77-129">Department</span></span>
  - <span data-ttu-id="cdd77-130">辦公室</span><span class="sxs-lookup"><span data-stu-id="cdd77-130">Office</span></span>
  - <span data-ttu-id="cdd77-131">辦公室電話</span><span class="sxs-lookup"><span data-stu-id="cdd77-131">Office Phone</span></span>
  - <span data-ttu-id="cdd77-132">行動電話</span><span class="sxs-lookup"><span data-stu-id="cdd77-132">Mobile Phone</span></span>
  - <span data-ttu-id="cdd77-133">傳真號碼</span><span class="sxs-lookup"><span data-stu-id="cdd77-133">Fax Number</span></span>
  - <span data-ttu-id="cdd77-134">路/街</span><span class="sxs-lookup"><span data-stu-id="cdd77-134">Street Address</span></span>
  - <span data-ttu-id="cdd77-135">市或鎮</span><span class="sxs-lookup"><span data-stu-id="cdd77-135">City</span></span>
  - <span data-ttu-id="cdd77-136">州或省</span><span class="sxs-lookup"><span data-stu-id="cdd77-136">State or Province</span></span>
  - <span data-ttu-id="cdd77-137">郵遞區號</span><span class="sxs-lookup"><span data-stu-id="cdd77-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="cdd77-138">國家或地區</span><span class="sxs-lookup"><span data-stu-id="cdd77-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="cdd77-139">目錄物件和屬性準備</span><span class="sxs-lookup"><span data-stu-id="cdd77-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="cdd77-p104">您的內部部署目錄和 Office 365 之間順利目錄同步處理需要已適當地準備您的內部部署目錄屬性。例如，您需要確定特定字元不用於特定會與 Office 365 環境進行同步處理的屬性。未預期的字元不會造成目錄同步處理失敗，但是可能會傳回一則警告訊息。無效字元將會造成目錄同步作業失敗。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="cdd77-p105">如果您的部分 Active Directory 使用者有一或多個重複屬性也會失敗目錄同步處理。每位使用者必須具有唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="cdd77-146">以下列出您需要準備屬性：</span><span class="sxs-lookup"><span data-stu-id="cdd77-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="cdd77-147">**附註：** 您也可以使用[IdFix 工具](install-and-run-idfix.md)以更方便此程序。</span><span class="sxs-lookup"><span data-stu-id="cdd77-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="cdd77-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="cdd77-148">**displayName**</span></span>
    
  - <span data-ttu-id="cdd77-149">如果此屬性存在於使用者物件中，則會與 Office 365 同步處理。</span><span class="sxs-lookup"><span data-stu-id="cdd77-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="cdd77-p106">如果此屬性存在於使用者物件中，該屬性必須有值。也就是說，屬性不能空白。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="cdd77-152">字元數上限：256</span><span class="sxs-lookup"><span data-stu-id="cdd77-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="cdd77-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="cdd77-153">**givenName**</span></span>
    
  - <span data-ttu-id="cdd77-154">如果屬性存在於使用者物件中，該屬性會與 Office 365 同步處理，但 Office 365 不需要或不會使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="cdd77-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="cdd77-155">字元數上限：64</span><span class="sxs-lookup"><span data-stu-id="cdd77-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="cdd77-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="cdd77-156">**mail**</span></span>
    
  - <span data-ttu-id="cdd77-157">屬性值在目錄內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cdd77-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="cdd77-p107">如果有重複值，此值的第一個使用者會同步處理。後續的使用者將不會出現在 Office 365 中。您必須修改 Office 365 中的其中一個值或修改兩個兩個使用者會出現在 Office 365 中的順序中的內部部署目錄中的值。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="cdd77-161">**mailNickname** (Exchange 別名)</span><span class="sxs-lookup"><span data-stu-id="cdd77-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="cdd77-162">屬性值不能以句點 （.） 開頭。</span><span class="sxs-lookup"><span data-stu-id="cdd77-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="cdd77-163">屬性值在目錄內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cdd77-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="cdd77-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="cdd77-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="cdd77-165">多重值屬性</span><span class="sxs-lookup"><span data-stu-id="cdd77-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="cdd77-166">每個值的字元數上限：256</span><span class="sxs-lookup"><span data-stu-id="cdd77-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="cdd77-167">屬性值不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="cdd77-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="cdd77-168">屬性值在目錄內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cdd77-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="cdd77-169">無效字元： \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="cdd77-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="cdd77-170">附註的無效字元套用到下列類型的分隔字元的字元與":"，因而可以看允許 SMTP:User@contso.com，但不是 SMTP:user:M@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="cdd77-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="cdd77-p108">所有的簡易郵件傳輸通訊協定 (SMTP) 位址均應遵循電子郵件傳訊標準。如果存在重複或不想要的地址，請參閱[Exchange 中移除重複並不需要 proxy 位址](https://go.microsoft.com/fwlink/?LinkId=293860)的說明主題。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="cdd77-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="cdd77-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="cdd77-174">字元數上限：20</span><span class="sxs-lookup"><span data-stu-id="cdd77-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="cdd77-175">屬性值在目錄內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cdd77-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="cdd77-p109">無效字元： [\"|，/: \< \> + =;？\* ]</span><span class="sxs-lookup"><span data-stu-id="cdd77-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="cdd77-178">如果使用者的 **sAMAccountName** 屬性無效，但 **userPrincipalName** 屬性有效，則會在 Office 365 中建立使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cdd77-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="cdd77-179">若**sAMAccountName**及**userPrincipalName**均為無效，則必須更新內部部署 Active Directory **userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="cdd77-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="cdd77-180">**sn** (姓氏)</span><span class="sxs-lookup"><span data-stu-id="cdd77-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="cdd77-181">如果屬性存在於使用者物件中，該屬性會與 Office 365 同步處理，但 Office 365 不需要或不會使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="cdd77-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="cdd77-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="cdd77-182">**targetAddress**</span></span>
    
    <span data-ttu-id="cdd77-p110">有必要便會填入使用者的**targetAddress**屬性 (例如 SMTP:tom@contoso.com) 必須出現在 Office 365 GAL。在第三方訊息移轉案例中這會需要擴充 Office 365 架構內部部署目錄。擴充 Office 365 架構也會新增其他有用的屬性來管理 Office 365 填入使用目錄同步作業工具從內部部署目錄的物件。例如，且無法新增**msExchHideFromAddressLists**屬性來管理隱藏的信箱或通訊群組。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="cdd77-187">字元數上限：256</span><span class="sxs-lookup"><span data-stu-id="cdd77-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="cdd77-188">屬性值不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="cdd77-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="cdd77-189">屬性值在目錄內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cdd77-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="cdd77-190">無效字元： \ \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="cdd77-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="cdd77-191">所有 Simple Mail Transport Protocol (SMTP) 位址都要符合電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="cdd77-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="cdd77-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="cdd77-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="cdd77-p111">**UserPrincipalName**屬性必須是網際網路樣式登入格式的使用者名稱後面其中 at 符號 (@) 和網域名稱： 例如 user@contoso.com。所有的簡易郵件傳輸通訊協定 (SMTP) 位址均應遵循電子郵件傳訊標準。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="cdd77-p112">**userPrincipalName** 屬性的字元數上限為 113。@ 符號前後允許的特定字元數如下：</span><span class="sxs-lookup"><span data-stu-id="cdd77-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="cdd77-197">@ 符號之前的使用者名稱字元數上限：64</span><span class="sxs-lookup"><span data-stu-id="cdd77-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="cdd77-198">@ 符號之後的網域名稱字元數上限：48</span><span class="sxs-lookup"><span data-stu-id="cdd77-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="cdd77-p113">無效字元： \ % &amp; \* + / =？{ } |\< \> ( ) ;: , [ ] "</span><span class="sxs-lookup"><span data-stu-id="cdd77-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="cdd77-201">母音也是無效的字元。</span><span class="sxs-lookup"><span data-stu-id="cdd77-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="cdd77-202">字元必須要有 @ 每個**userPrincipalName**值。</span><span class="sxs-lookup"><span data-stu-id="cdd77-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="cdd77-203">每個 **userPrincipalName** 值皆不可以 @ 字元做為第一個字元。</span><span class="sxs-lookup"><span data-stu-id="cdd77-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="cdd77-204">使用者名稱結尾不得句點 （.）、 & 符號 (&amp;)、 空格，或參閱註冊 (@)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="cdd77-205">使用者名稱不得包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="cdd77-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="cdd77-206">必須使用可路由的網域 ；例如，不能使用 local 或 internal 的網域。</span><span class="sxs-lookup"><span data-stu-id="cdd77-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="cdd77-207">Unicode 字元會轉換為底線字元。</span><span class="sxs-lookup"><span data-stu-id="cdd77-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="cdd77-208">**userPrincipalName** 不可包含任何在目錄中會重複的值。</span><span class="sxs-lookup"><span data-stu-id="cdd77-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="cdd77-209">準備 userPrincipalName 屬性</span><span class="sxs-lookup"><span data-stu-id="cdd77-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="cdd77-p114">Active Directory 的設計允許您的組織可以使用 [ **sAMAccountName** ] 或 [ **userPrincipalName**登入您的目錄中的使用者。同樣地，使用者可以使用其工作的使用者主體名稱 (UPN) 登入 Office 365 或學校帳戶。使用您的內部部署目錄中的相同 UPN Azure Active Directory 中建立新的使用者嘗試目錄同步處理。UPN 格式類似電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="cdd77-p115">在 Office 365 UPN 是用來產生電子郵件地址的預設屬性。很容易取得**userPrincipalName** (內部和 Azure Active Directory 中) 及**proxyAddresses**設為不同的值的主要電子郵件地址。當已設為不同的值時，可以是系統管理員和使用者混淆。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="cdd77-p116">最好對齊以減少混淆這些屬性。若要符合需求的單一登入與 Active Directory Federation Services (AD FS) 2.0、 您需要確定 Azure Active Directory 與您在內部部署 Active Directory Upn 相符，並使用有效的網域命名空間。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="cdd77-219">將替代的 UPN 尾碼新增至 AD DS</span><span class="sxs-lookup"><span data-stu-id="cdd77-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="cdd77-p117">您可能需要新增至使用者的公司認證關聯的 Office 365 環境替代的 UPN 尾碼。UPN 尾碼屬於右邊的 UPN @ 字元。單一登入所用的 Upn 可以包含字母、 數字、 期間、 虛線、 和底線，但沒有其他類型的字元。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="cdd77-223">如需有關如何將替代的 UPN 尾碼新增至 Active Directory 的詳細資訊，請參閱[為目錄同步作業的準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="cdd77-224">使內部部署 UPN 與 Office 365 UPN</span><span class="sxs-lookup"><span data-stu-id="cdd77-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="cdd77-p118">如果您已設定目錄同步處理，Office 365 使用者的 UPN 可能不符合您的內部部署目錄服務中定義的使用者的內部部署 UPN。當使用者已指派授權已驗證網域之前可以發生此情況。若要修正此問題，使用[PowerShell 修正重複 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)更新以確保 Office 365 UPN 相符的公司的使用者名稱與網域使用者的 UPN。如果您要更新的內部部署目錄服務中的 UPN 並想要同步處理與 Azure Active Directory 身分識別，您需要在 Office 365 中移除使用者的授權之前先進行變更內部。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="cdd77-229">另請參閱[如何準備非-路由傳送的網域 （例如.local 網域） 進行目錄同步作業](prepare-a-non-routable-domain-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="cdd77-230">目錄整合工具</span><span class="sxs-lookup"><span data-stu-id="cdd77-230">Directory integration tools</span></span>

<span data-ttu-id="cdd77-p119">目錄物件 （使用者、 群組及連絡人） 從內部部署 Active Directory 環境至 Office 365 目錄基礎結構、 Azure Active Directory 同步處理的目錄同步處理。請參閱[目錄整合工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)的可用的工具和功能的清單。[Microsoft Azure Active Directory 連線](https://go.microsoft.com/fwlink/p/?LinkID=510956)是建議的工具。如需 Azure 作用中的目錄連線的詳細資訊，請參閱[Azure Active Directory 與您的內部身分識別的整合](https://go.microsoft.com/fwlink/p/?LinkId=527969)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="cdd77-p120">當使用者帳戶與 Office 365 目錄第一次同步處理時，則會標示為為未啟動。他們無法傳送或接收電子郵件，以及它們不取用訂閱授權。當您準備好要指派給特定使用者的 Office 365 訂閱時，您必須選取並啟動其[指派給 Office 365 中的商務使用者的授權](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="cdd77-p121">您也可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)指派授權。請參閱自動化解決方案[如何使用 PowerShell 自動將授權指派給您的 Office 365 使用者](https://go.microsoft.com/fwlink/p?LinkID=329805)。</span><span class="sxs-lookup"><span data-stu-id="cdd77-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>