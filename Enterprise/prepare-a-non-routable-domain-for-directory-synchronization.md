---
title: 非路由傳送的網域準備目錄同步作業
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: 了解新如果有非 routale 網域與 Office 365 同步處理之前與您的內部部署使用者相關聯。
ms.openlocfilehash: 150e670e58419cda0f8ba08a5fb1e375478a27b1
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085312"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="d1944-103">非路由傳送的網域準備目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="d1944-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="d1944-p101">當您與 Office 365 同步處理您的內部部署目錄必須有 Azure Active Directory 中的已驗證的網域。僅限使用者主體名稱 (UPN) 相關聯的內部部署網域進行同步處理。不過，包含非路由傳送的網域，例如.local （例如 billa@contoso.local)、 任何 UPN 會同步處理至。 onmicrosoft.com 網域 （例如 billa@contoso.onmicrosoft.com)。</span><span class="sxs-lookup"><span data-stu-id="d1944-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="d1944-107">如果您目前使用.local 網域在 Active Directory 中的使用者帳戶的建議變更他們能夠使用才能正確同步處理您的 Office 365 網域與已驗證的網域 （例如 billa@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="d1944-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="d1944-108">如果僅有.local 內部網域吗？</span><span class="sxs-lookup"><span data-stu-id="d1944-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="d1944-p102">您可以使用 Azure Active directory Active Directory 同步處理的最新工具名為 Azure AD 連線]。如需詳細資訊，請參閱[您的內部部署身分識別與 Azure Active Directory 的整合](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。</span><span class="sxs-lookup"><span data-stu-id="d1944-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="d1944-p103">Azure AD 連線同步處理使用者的 UPN 和密碼，讓使用者可以登入使用的相同認證他們使用內部部署。不過，Azure AD 連接僅同步處理至 Office 365 檢定的網域的使用者。這表示該網域也會通過 Azure Active Directory 因為 Azure Active Directory 管理 Office 365 身分識別。換句話說，網域必須為有效的網際網路網域 （例如.com、.org、.net、.us 等等）。如果您內部部署 Active Directory 僅使用非路由傳送的網域 (例如.local)，這可能是不能符合 Office 365 中有已驗證的網域。您可以透過變更主要在您內部部署 Active Directory 網域或新增一或多個 UPN 尾碼來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="d1944-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="d1944-117">**變更主要網域**</span><span class="sxs-lookup"><span data-stu-id="d1944-117">**Change your primary domain**</span></span>

<span data-ttu-id="d1944-p104">變更至您已在 Office 365，例如，contoso.com 中驗證網域的主要網域。每個使用者而言具有網域 contoso.local 然後更新為 contoso.com。指示，請參閱[網域重新命名的運作方式](https://go.microsoft.com/fwlink/p/?LinkId=624174)。這是非常相關的程序，但並更輕鬆地解決方案是若要[新增的 UPN 尾碼並更新其使用者](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register)下, 一節所示。</span><span class="sxs-lookup"><span data-stu-id="d1944-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="d1944-122">**新增的 UPN 尾碼並更新其使用者**</span><span class="sxs-lookup"><span data-stu-id="d1944-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="d1944-p105">您可以解決.local 問題您在 Office 365 中所要比對 （或多個網域） 的 Active Directory 中註冊新的 UPN 尾碼驗證。註冊新的後置詞後，您會更新使用者以.local 取代新網域名稱的範例會使起來 billa@contoso.com 的使用者帳戶的 Upn。</span><span class="sxs-lookup"><span data-stu-id="d1944-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="d1944-125">您已更新 Upn 来使用的已驗證的網域之後，您就可以與 Office 365 同步處理您的內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="d1944-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="d1944-126">**步驟 1： 將新的 UPN 尾碼新增**</span><span class="sxs-lookup"><span data-stu-id="d1944-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="d1944-127">在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory 網域及信任**。</span><span class="sxs-lookup"><span data-stu-id="d1944-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="d1944-128">**或者，您不需要 Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="d1944-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="d1944-129">若要開啟 [**執行**] 對話方塊，然後輸入 Domain.msc，在按**Windows 鍵 + R** ，然後選擇 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d1944-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![選擇 [Active Directory 網域及信任]。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="d1944-131">在 [ **Active Directory 網域及信任**] 視窗中，以滑鼠右鍵按一下 [ **Active Directory 網域及信任**、，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d1944-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![ActiveDirectory 網域及信任上按一下滑鼠右鍵並選擇屬性](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="d1944-133">在 [ **UPN 尾碼**] 索引標籤上 [**替用的 UPN 尾碼**] 方塊中輸入新的 UPN 尾碼或尾碼，然後按**新增** \> **套用**。</span><span class="sxs-lookup"><span data-stu-id="d1944-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![將新的 UPN 尾碼新增](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="d1944-135">選擇 **[確定]** 完成新增尾碼時。</span><span class="sxs-lookup"><span data-stu-id="d1944-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="d1944-136">**步驟 2： 變更現有使用者的 UPN 尾碼**</span><span class="sxs-lookup"><span data-stu-id="d1944-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="d1944-137">在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory 的 Active Directory 使用者及電腦**。</span><span class="sxs-lookup"><span data-stu-id="d1944-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="d1944-138">**或者，您不需要 Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="d1944-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="d1944-139">若要開啟 [**執行**] 對話方塊，然後輸入 [dsa.msc]，在按**Windows 鍵 + R** ，然後按一下 [**確定]**</span><span class="sxs-lookup"><span data-stu-id="d1944-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="d1944-140">選取 [使用者] 中，按一下滑鼠右鍵，然後選擇 [**內容**。</span><span class="sxs-lookup"><span data-stu-id="d1944-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="d1944-141">在**帳戶**] 索引標籤的 [UPN 尾碼下拉式清單中，選擇新的 UPN 尾碼，然後再選擇 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d1944-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![新增新使用者的 UPN 尾碼](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="d1944-143">完成這些步驟的每位使用者。</span><span class="sxs-lookup"><span data-stu-id="d1944-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="d1944-144">或者您可以大量更新 UPN 尾碼[您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh)。</span><span class="sxs-lookup"><span data-stu-id="d1944-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="d1944-145">**您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼**</span><span class="sxs-lookup"><span data-stu-id="d1944-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="d1944-p106">如果您有許多使用者更新的很容易使用 Windows PowerShell。下列範例會使用[Get ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312)與[組 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313)指令程式來變更為 contoso.com 的所有 contoso.local 尾碼。</span><span class="sxs-lookup"><span data-stu-id="d1944-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="d1944-148">執行下列 Windows PowerShell 命令來更新為 contoso.com 的所有 contoso.local 尾碼：</span><span class="sxs-lookup"><span data-stu-id="d1944-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="d1944-149">若要深入了解在 Active Directory 中使用 Windows PowerShell 查看[Active Directory Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=624314)。</span><span class="sxs-lookup"><span data-stu-id="d1944-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

