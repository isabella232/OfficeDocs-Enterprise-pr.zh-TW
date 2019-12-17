---
title: 準備目錄同步處理的非路由傳送的網域
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: 了解要執行如果您有非 routale 網域，再進行同步處理與 Office 365 與內部部署使用者相關聯的動作。
ms.openlocfilehash: 013d29acdd3761793a93dab1eb8583324ba08591
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072415"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="0d855-103">準備目錄同步處理的非路由傳送的網域</span><span class="sxs-lookup"><span data-stu-id="0d855-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="0d855-104">當您同步處理您的內部部署目錄與 Office 365，您必須要有 Azure Active Directory 中的已驗證的網域。</span><span class="sxs-lookup"><span data-stu-id="0d855-104">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory.</span></span> <span data-ttu-id="0d855-105">僅限使用者主要名稱 (UPN) 相關聯的內部部署網域同步處理。</span><span class="sxs-lookup"><span data-stu-id="0d855-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="0d855-106">不過，任何 UPN 包含非路由傳送的網域，例如.local （例如 billa@contoso.local)，將會同步處理到。 onmicrosoft.com 網域 （例如 billa@contoso.onmicrosoft.com)。</span><span class="sxs-lookup"><span data-stu-id="0d855-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="0d855-107">如果您目前使用.local 網域，建議您變更他們才能正確地同步處理與您的 Office 365 網域使用驗證的網域 （例如 billa@contoso.com) 在 Active Directory 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0d855-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="0d855-108">如果僅有.local 內部網域？</span><span class="sxs-lookup"><span data-stu-id="0d855-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="0d855-109">您可以使用同步處理您的 Active Directory 至 Azure Active Directory 的最新工具是名為 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="0d855-109">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect.</span></span> <span data-ttu-id="0d855-110">如需詳細資訊，請參閱[將內部部署識別與 Azure Active Directory 整合](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。</span><span class="sxs-lookup"><span data-stu-id="0d855-110">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="0d855-111">Azure AD Connect 進行同步處理使用者的 UPN 與密碼，讓使用者可以登入相同的認證他們使用內部部署。</span><span class="sxs-lookup"><span data-stu-id="0d855-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="0d855-112">不過，Azure AD Connect 只會同步處理至 Office 365 所驗證的網域的使用者。</span><span class="sxs-lookup"><span data-stu-id="0d855-112">However, Azure AD Connect only synchronizes users to domains that are verified by Office 365.</span></span> <span data-ttu-id="0d855-113">這表示，網域也驗證 Azure Active directory 因為由 Azure Active Directory 管理 Office 365 身分識別。</span><span class="sxs-lookup"><span data-stu-id="0d855-113">This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory.</span></span> <span data-ttu-id="0d855-114">換句話說，網域必須是有效的網際網路網域 （例如，.com、.org、.net、.us 等等）。</span><span class="sxs-lookup"><span data-stu-id="0d855-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="0d855-115">如果您內部部署 Active Directory 只使用非路由傳送的網域 (例如.local)，這可能無法符合您有 Office 365 的已驗證的網域。</span><span class="sxs-lookup"><span data-stu-id="0d855-115">If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365.</span></span> <span data-ttu-id="0d855-116">若要修正此問題，您可以藉由變更您在您內部部署 Active Directory 中的主要網域，或藉由新增一或多個 UPN 尾碼。</span><span class="sxs-lookup"><span data-stu-id="0d855-116">You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="0d855-117">**變更主要網域**</span><span class="sxs-lookup"><span data-stu-id="0d855-117">**Change your primary domain**</span></span>

<span data-ttu-id="0d855-118">變更至您已在 Office 365，例如，contoso.com 中驗證網域的主要網域。</span><span class="sxs-lookup"><span data-stu-id="0d855-118">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com.</span></span> <span data-ttu-id="0d855-119">每個使用者都會具有網域 contoso.local 再將更新為 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="0d855-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="0d855-120">如需相關指示，請參閱[網域重新命名的運作方式](https://go.microsoft.com/fwlink/p/?LinkId=624174)。</span><span class="sxs-lookup"><span data-stu-id="0d855-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="0d855-121">這是非常複雜的過程中，不過，與下一節說明簡單的解決方案。</span><span class="sxs-lookup"><span data-stu-id="0d855-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="0d855-122">**新增的 UPN 尾碼和這些更新您的使用者**</span><span class="sxs-lookup"><span data-stu-id="0d855-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="0d855-123">您可以解決.local 問題您在 Office 365 中要比對 （或多個網域） 的 Active Directory 中註冊新的 UPN 尾碼驗證。</span><span class="sxs-lookup"><span data-stu-id="0d855-123">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365.</span></span> <span data-ttu-id="0d855-124">註冊新的尾碼之後，您會更新使用者以新的網域名稱，例如.local 取代，因此，使用者帳戶看起來像 billa@contoso.com Upn。</span><span class="sxs-lookup"><span data-stu-id="0d855-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="0d855-125">您已更新若要使用的已驗證的網域 Upn 之後，您已準備好將您的內部部署 Active Directory 與 Office 365 同步處理。</span><span class="sxs-lookup"><span data-stu-id="0d855-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="0d855-126">**步驟 1： 將新的 UPN 尾碼新增**</span><span class="sxs-lookup"><span data-stu-id="0d855-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="0d855-127">在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory 網域及信任**。</span><span class="sxs-lookup"><span data-stu-id="0d855-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="0d855-128">**或者，如果您不需要 Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="0d855-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="0d855-129">若要開啟 [**執行**] 對話方塊中，然後輸入 Domain.msc，在按下**Windows 鍵 + R** ，然後選擇 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="0d855-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![選擇 [Active Directory 網域及信任]。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="0d855-131">在 [ **Active Directory 網域及信任**] 視窗中，以滑鼠右鍵按一下 [ **Active Directory 網域及信任**，，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0d855-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![ActiveDirectory 網域及信任上按一下滑鼠右鍵，然後選擇 [屬性](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="0d855-133">在 [ **UPN 尾碼**] 索引標籤，在**替代的 UPN 尾碼**] 方塊中，輸入您新的 UPN 尾碼或尾碼，，然後選擇 [ **Add** \> **套用**。</span><span class="sxs-lookup"><span data-stu-id="0d855-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![新增新的 UPN 尾碼](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="0d855-135">當您完成新增尾碼，請選擇 [**確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0d855-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="0d855-136">**步驟 2： 變更現有使用者的 UPN 尾碼**</span><span class="sxs-lookup"><span data-stu-id="0d855-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="0d855-137">在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory Active Directory 使用者和電腦**。</span><span class="sxs-lookup"><span data-stu-id="0d855-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="0d855-138">**或者，如果您不需要 Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="0d855-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="0d855-139">以開啟 [**執行**] 對話方塊中，，然後輸入 [Dsa.msc，在按下**Windows 鍵 + R** ，然後按一下 [**確定]**</span><span class="sxs-lookup"><span data-stu-id="0d855-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="0d855-140">選取 [使用者]，按一下滑鼠右鍵，然後選擇 [**內容**。</span><span class="sxs-lookup"><span data-stu-id="0d855-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="0d855-141">在 [**帳戶**] 索引標籤中，在 [UPN 尾碼] 下拉式清單中，選擇新的 UPN 尾碼，，然後選擇 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="0d855-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![新增新使用者的 UPN 尾碼](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="0d855-143">完成下列步驟，將每一位使用者。</span><span class="sxs-lookup"><span data-stu-id="0d855-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="0d855-144">**您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼**</span><span class="sxs-lookup"><span data-stu-id="0d855-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="0d855-145">如果您有大量的使用者更新時，會比較容易使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0d855-145">If you have a lot of users to update, it is easier to use Windows PowerShell.</span></span> <span data-ttu-id="0d855-146">下列範例會使用的指令程式，[取得 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312)和[設定 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313)若要將所有 contoso.local 尾碼都變更為 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="0d855-146">The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="0d855-147">執行下列 Windows PowerShell 命令，以更新為 contoso.com 的所有 contoso.local 尾碼：</span><span class="sxs-lookup"><span data-stu-id="0d855-147">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

<span data-ttu-id="0d855-148">若要深入了解在 Active Directory 中使用 Windows PowerShell，請參閱[Active Directory Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=624314)。</span><span class="sxs-lookup"><span data-stu-id="0d855-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

