---
title: 如何設定商務用 Skype 內部部署以使用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: 新式驗證，是一種方法提供了更安全的使用者驗證和授權、 skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合可用的身分識別管理。
ms.openlocfilehash: a9fb93d0269628c0c1d4cd374e3bca36482f7eee
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490315"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="67640-103">如何設定商務用 Skype 內部部署以使用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="67640-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="67640-104">新式驗證，是一種方法提供了更安全的使用者驗證和授權、 skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合可用的身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="67640-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="67640-105">**重要**您可能會想要深入了解新式驗證 (MA)，您可能偏好使用公司或組織中？</span><span class="sxs-lookup"><span data-stu-id="67640-105">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="67640-106">檢查[此文件](hybrid-modern-auth-overview.md)的概觀。</span><span class="sxs-lookup"><span data-stu-id="67640-106">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="67640-107">如果您需要知道哪些 Skype for Business 拓撲支援 MA，以下記載 ！</span><span class="sxs-lookup"><span data-stu-id="67640-107">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="67640-108">**開始前**，我呼叫：</span><span class="sxs-lookup"><span data-stu-id="67640-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="67640-109">新式驗證\>MA</span><span class="sxs-lookup"><span data-stu-id="67640-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="67640-110">混合式新式驗證\>HMA</span><span class="sxs-lookup"><span data-stu-id="67640-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="67640-111">Exchange 內部部署\>NM-EXCH-UM-1ST</span><span class="sxs-lookup"><span data-stu-id="67640-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="67640-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="67640-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="67640-113">Skype for Business 內部\>SFB</span><span class="sxs-lookup"><span data-stu-id="67640-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="67640-114">與 Skype for Business Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="67640-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="67640-115">此外，\* 如果本文中的圖形都有一個物件具有 ' 變為 out' 或 '變暗'，表示所示灰色**不**包含在 MA 特有設定的項目。</span><span class="sxs-lookup"><span data-stu-id="67640-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="67640-116">閱讀有關摘要</span><span class="sxs-lookup"><span data-stu-id="67640-116">Read the summary</span></span>

<span data-ttu-id="67640-117">此摘要 boils 程序為可能否則會遺失在執行期間，以及良好的整體檢查清單來追蹤您所在之程序中的步驟。</span><span class="sxs-lookup"><span data-stu-id="67640-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="67640-118">首先，請確定您符合所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="67640-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="67640-119">自許多**必要條件**是很常見的兩個 Skype for Business 和 Exchange，[請參閱您預先需求的檢查清單概觀文章](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67640-119">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="67640-120">執行此*之前*開始任何本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="67640-120">Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="67640-121">收集您需要在檔案或 OneNote HMA 特有資訊。</span><span class="sxs-lookup"><span data-stu-id="67640-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="67640-122">開啟 ON 新式驗證 EXO （如果它尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="67640-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="67640-123">開啟 ON 新式驗證 SFBO （如果它尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="67640-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="67640-124">開啟 Exchange 內部部署的混合式新式驗證。</span><span class="sxs-lookup"><span data-stu-id="67640-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="67640-125">開啟商務內部 skype 的混合式新式驗證。</span><span class="sxs-lookup"><span data-stu-id="67640-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="67640-126">請注意下列步驟開啟 MA SFB、 SFBO、 NM-EXCH-UM-1ST，及 EXO-亦即可以參與 HMA 設定 SFB 和 SFBO （包括 NM-EXCH-UM-1ST/EXO 上的相依性） 的所有產品。</span><span class="sxs-lookup"><span data-stu-id="67640-126">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="67640-127">也就是說，如果您的使用者皆位於 / 已在混合式 （EXO + SFBO、 EXO + SFB、 NM-EXCH-UM-1ST + SFBO，或 NM-EXCH-UM-1ST + SFB） 的任何部分中建立信箱，您已完成的產品看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="67640-127">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![商務 HMA 拓撲混合 6 商務用 Skype 具備 MA 中所有四個可能的位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="67640-129">您可以看到有四個不同的位置，來開啟 MA ！</span><span class="sxs-lookup"><span data-stu-id="67640-129">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="67640-130">為最佳使用者經驗，我們建議您開啟 MA 總共四個這些位置中。</span><span class="sxs-lookup"><span data-stu-id="67640-130">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="67640-131">如果您不能在所有這些位置開啟 MA，請調整步驟，讓您開啟 MA 只能在所需的環境的位置。</span><span class="sxs-lookup"><span data-stu-id="67640-131">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="67640-132">請參閱支援的拓撲[與 MA 的商務用 Skype 的支援主題](https://technet.microsoft.com/en-us/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67640-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="67640-133">**重要**請仔細檢查您開始之前已符合所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="67640-133">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="67640-134">您會發現該資訊[以下](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67640-134">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="67640-135">收集您需要的所有 HMA 特有資訊</span><span class="sxs-lookup"><span data-stu-id="67640-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="67640-136">您已重複檢查，之後您已符合[先決條件](hybrid-modern-auth-overview.md)以使用新式驗證 （請參閱上述的附註），您應該建立檔案來包含您需要設定 HMA 往前的步驟中的資訊。</span><span class="sxs-lookup"><span data-stu-id="67640-136">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="67640-137">使用本文中的範例：</span><span class="sxs-lookup"><span data-stu-id="67640-137">Examples used in this article:</span></span> 
  
- <span data-ttu-id="67640-138">**SIP/SMTP 網域**</span><span class="sxs-lookup"><span data-stu-id="67640-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="67640-139">例如</span><span class="sxs-lookup"><span data-stu-id="67640-139">Ex.</span></span> <span data-ttu-id="67640-140">contoso.com （同盟與 Office 365）</span><span class="sxs-lookup"><span data-stu-id="67640-140">contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="67640-141">**租用戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="67640-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="67640-142">GUID，代表您的 Office 365 租用戶 （位於 contoso.onmicrosoft.com 的登入）。</span><span class="sxs-lookup"><span data-stu-id="67640-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="67640-143">**SFB 2015 CU5 Web 服務 Url**</span><span class="sxs-lookup"><span data-stu-id="67640-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="67640-144">您將需要內部和外部 web 服務 URL 的所有部署的 SfB 2015 集區。</span><span class="sxs-lookup"><span data-stu-id="67640-144">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="67640-145">若要取得這些，請執行下列從 Skype for Business 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="67640-145">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="67640-146">例如</span><span class="sxs-lookup"><span data-stu-id="67640-146">Ex.</span></span> <span data-ttu-id="67640-147">內部：https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="67640-147">Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="67640-148">例如</span><span class="sxs-lookup"><span data-stu-id="67640-148">Ex.</span></span> <span data-ttu-id="67640-149">外部：https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="67640-149">External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="67640-150">如果您使用 Standard Edition server，內部 URL 將會空白。</span><span class="sxs-lookup"><span data-stu-id="67640-150">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="67640-151">在此情況下，使用內部 URL 的集區 fqdn。</span><span class="sxs-lookup"><span data-stu-id="67640-151">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="67640-152">開啟 [EXO 的新式驗證</span><span class="sxs-lookup"><span data-stu-id="67640-152">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="67640-153">請遵循以下指示： [Exchange Online： 如何啟用新式驗證在租用戶。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="67640-153">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="67640-154">開啟 SFBO 的新式驗證</span><span class="sxs-lookup"><span data-stu-id="67640-154">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="67640-155">請遵循以下指示： [Skype for Business Online： 啟用新式驗證在租用戶](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67640-155">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="67640-156">開啟 Exchange 內部部署的混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="67640-156">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="67640-157">請遵循以下指示：[如何設定 Exchange Server 內部部署以使用混合式新式驗證](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="67640-157">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="67640-158">開啟商務內部部署的 skype 的混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="67640-158">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="67640-159">新增內部 Azure AD 中為 Spn web 服務 Url</span><span class="sxs-lookup"><span data-stu-id="67640-159">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="67640-160">現在您需要執行命令，以作為服務主體中 SFBO 新增 （收集更早版本） 的 Url。</span><span class="sxs-lookup"><span data-stu-id="67640-160">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="67640-161">**附註**服務主要名稱 (Spn) 識別 web 服務，以及其關聯 （例如帳戶名稱或群組） 的安全性主體，讓該服務可對授權的使用者代理。</span><span class="sxs-lookup"><span data-stu-id="67640-161">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="67640-162">伺服器進行驗證的用戶端進行使用的資訊的中所含的 Spn。</span><span class="sxs-lookup"><span data-stu-id="67640-162">Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="67640-163">首先，連線至 AAD[這些](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0)指示。</span><span class="sxs-lookup"><span data-stu-id="67640-163">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>
    
2. <span data-ttu-id="67640-164">執行此命令中，內部部署，若要取得之 SFB web 服務 Url 的清單。</span><span class="sxs-lookup"><span data-stu-id="67640-164">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="67640-165">請注意，AppPrincipalId 開頭`00000004`。</span><span class="sxs-lookup"><span data-stu-id="67640-165">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="67640-166">這會對應到 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="67640-166">This corresponds to Skype for Business Online.</span></span>
    
   <span data-ttu-id="67640-167">此命令，它會包括 SE 和 WS URL，但是大部分所組成的開頭的 Spn 的輸出採取的附註 （和更新版本的比對的螢幕擷取畫面） `00000004-0000-0ff1-ce00-000000000000/`。</span><span class="sxs-lookup"><span data-stu-id="67640-167">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>
    
```
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```
    
3. <span data-ttu-id="67640-168">如果內部**或**外部遺漏了從內部 SFB Url (例如https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我們需要將這些特定記錄新增至這份清單。</span><span class="sxs-lookup"><span data-stu-id="67640-168">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="67640-169">請務必*範例 Url* ] 下方，取代實際 Url 中新增命令 ！</span><span class="sxs-lookup"><span data-stu-id="67640-169">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
  
```  
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="67640-170">確認您新的記錄已新增步驟 2 中取得 MsolServicePrincipal 命令執行，並將輸出中尋找。</span><span class="sxs-lookup"><span data-stu-id="67640-170">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="67640-171">比較清單 / 將螢幕擷取畫面從之前的 Spn （您可能也螢幕擷取畫面新清單以供記錄） 新的清單。</span><span class="sxs-lookup"><span data-stu-id="67640-171">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="67640-172">如果您已成功，您會看到兩個新的 Url 清單中。</span><span class="sxs-lookup"><span data-stu-id="67640-172">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="67640-173">將由我們的範例，此清單的 Spn 將現在包含特定 Urlhttps://lyncweb01.contoso.com和https://lyncwebext01.contoso.com/。</span><span class="sxs-lookup"><span data-stu-id="67640-173">Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="67640-174">建立 EvoSTS 驗證伺服器物件</span><span class="sxs-lookup"><span data-stu-id="67640-174">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="67640-175">下列中執行命令 Skype for Business 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="67640-175">Run the following command in the Skype for Business Management Shell.</span></span>
  
```
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="67640-176">啟用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="67640-176">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="67640-177">這是實際開啟 MA 的步驟。</span><span class="sxs-lookup"><span data-stu-id="67640-177">This is the step that actually turns MA on.</span></span> <span data-ttu-id="67640-178">所有先前的步驟可以執行事先，而不需要變更用戶端驗證流程。</span><span class="sxs-lookup"><span data-stu-id="67640-178">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="67640-179">當您準備好要變更的驗證流程時，執行此命令中 Skype for Business 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="67640-179">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
```
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```
    
## <a name="verify"></a><span data-ttu-id="67640-180">確認</span><span class="sxs-lookup"><span data-stu-id="67640-180">Verify</span></span>

<span data-ttu-id="67640-181">一旦您啟用 HMA，用戶端下次登入時會使用新的驗證流程。</span><span class="sxs-lookup"><span data-stu-id="67640-181">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="67640-182">請注意，只開啟 HMA 就不會觸發重新驗證任何用戶端。</span><span class="sxs-lookup"><span data-stu-id="67640-182">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="67640-183">用戶端重新驗證為基礎的存留期的驗證權杖及/或他們所擁有的憑證。</span><span class="sxs-lookup"><span data-stu-id="67640-183">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="67640-184">若要測試 HMA 正常之後您已啟用它，登出測試 SFB Windows 用戶端，請務必按一下 [刪除我的認證]。</span><span class="sxs-lookup"><span data-stu-id="67640-184">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="67640-185">再次登入。</span><span class="sxs-lookup"><span data-stu-id="67640-185">Sign in again.</span></span> <span data-ttu-id="67640-186">用戶端現在應該使用新式驗證流程和您的登入現在包含 '工作或學校' 的**Office 365**提示看右之前用戶端連絡伺服器，而且您登入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="67640-186">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="67640-187">您應該也檢查組態資訊 skype 商務用戶端 'OAuth 授權單位 」。</span><span class="sxs-lookup"><span data-stu-id="67640-187">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="67640-188">用戶端電腦上執行這項操作，請按住 CTRL 鍵在同一時間以滑鼠右鍵按一下 Skype for Business 圖示 Windows 通知紙匣。</span><span class="sxs-lookup"><span data-stu-id="67640-188">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="67640-189">在出現的功能表中，按一下 [設定資訊。</span><span class="sxs-lookup"><span data-stu-id="67640-189">Click Configuration Information in the menu that appears.</span></span> <span data-ttu-id="67640-190">在桌面上會出現 ['Skype for Business 組態資訊'] 視窗中，尋找下列：</span><span class="sxs-lookup"><span data-stu-id="67640-190">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![商務用戶端使用新式驗證用 Skype 的組態資訊會顯示 Lync 和 EWS OAUTH 授權 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="67640-192">您也應按住 CTRL 鍵，同時以滑鼠右鍵按一下 [Outlook 用戶端 （也在 Windows 通知紙匣）] 圖示，然後按一下 [' 連線狀態 '。</span><span class="sxs-lookup"><span data-stu-id="67640-192">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="67640-193">用戶端的 SMTP 位址是否與 Authn 類型尋找 ' 承載\*'，用來表示用於 OAuth 承載 token。</span><span class="sxs-lookup"><span data-stu-id="67640-193">Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="67640-194">相關文章</span><span class="sxs-lookup"><span data-stu-id="67640-194">Related articles</span></span>

<span data-ttu-id="67640-195">[新式驗證概觀連結](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="67640-195">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="67640-196">您需要了解如何使用您 skype 的新式驗證 (ADAL) 的商務用戶端嗎？</span><span class="sxs-lookup"><span data-stu-id="67640-196">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="67640-197">我們是否已取得最新產品步驟[以下](https://technet.microsoft.com/en-us/library/mt710548.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67640-197">We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="67640-198">是否要閱讀這些步驟，以讓其顯示 Exchange Server 的內部部署、 執行沒有 SFB？</span><span class="sxs-lookup"><span data-stu-id="67640-198">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB?</span></span> <span data-ttu-id="67640-199">在這裡可執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="67640-199">Those steps are available here.</span></span>
  

