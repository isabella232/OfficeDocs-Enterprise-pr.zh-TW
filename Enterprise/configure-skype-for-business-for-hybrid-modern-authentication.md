---
title: 如何設定商務用 Skype 內部部署以使用混合式新式驗證
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 新式驗證，是一種方法提供了更安全的使用者驗證和授權、 skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合可用的身分識別管理。
ms.openlocfilehash: de5063da9eed03e2cd455b79b3a2d1c2f671ad1e
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840720"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="5a60a-103">如何設定商務用 Skype 內部部署以使用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="5a60a-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="5a60a-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="5a60a-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="5a60a-105">新式驗證，是一種方法提供了更安全的使用者驗證和授權、 skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合可用的身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="5a60a-105">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="5a60a-106">**重要**您可能會想要深入了解新式驗證 (MA)，您可能偏好使用公司或組織中？</span><span class="sxs-lookup"><span data-stu-id="5a60a-106">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="5a60a-107">檢查[此文件](hybrid-modern-auth-overview.md)的概觀。</span><span class="sxs-lookup"><span data-stu-id="5a60a-107">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="5a60a-108">如果您需要知道哪些 Skype for Business 拓撲支援 MA，以下記載 ！</span><span class="sxs-lookup"><span data-stu-id="5a60a-108">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span>
  
 <span data-ttu-id="5a60a-109">**開始前**，我呼叫：</span><span class="sxs-lookup"><span data-stu-id="5a60a-109">**Before we begin**, I call:</span></span>
  
- <span data-ttu-id="5a60a-110">新式驗證\>MA</span><span class="sxs-lookup"><span data-stu-id="5a60a-110">Modern Authentication \> MA</span></span>

- <span data-ttu-id="5a60a-111">混合式新式驗證\>HMA</span><span class="sxs-lookup"><span data-stu-id="5a60a-111">Hybrid Modern Authentication \> HMA</span></span>

- <span data-ttu-id="5a60a-112">Exchange 內部部署\>NM-EXCH-UM-1ST</span><span class="sxs-lookup"><span data-stu-id="5a60a-112">Exchange on-premises \> EXCH</span></span>

- <span data-ttu-id="5a60a-113">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="5a60a-113">Exchange Online \> EXO</span></span>

- <span data-ttu-id="5a60a-114">Skype for Business 內部\>SFB</span><span class="sxs-lookup"><span data-stu-id="5a60a-114">Skype for Business on-premises \> SFB</span></span>

- <span data-ttu-id="5a60a-115">與 Skype for Business Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="5a60a-115">and Skype for Business Online \> SFBO</span></span>

<span data-ttu-id="5a60a-116">此外，本文中的圖形是否會呈現灰色延展或變暗物件，表示中灰色**不是**顯示的項目包含在特定 MA 的組態。</span><span class="sxs-lookup"><span data-stu-id="5a60a-116">Also, if a graphic in this article has an object that's greyed-out or dimmed that means the element shown in gray **is not** included in MA-specific configuration.</span></span>
  
## <a name="read-the-summary"></a><span data-ttu-id="5a60a-117">閱讀有關摘要</span><span class="sxs-lookup"><span data-stu-id="5a60a-117">Read the summary</span></span>

<span data-ttu-id="5a60a-118">此摘要會分解成步驟可能否則會遺失在執行期間，以及良好的整體的檢查清單，以保留您所在之程序中的追蹤記錄的程序。</span><span class="sxs-lookup"><span data-stu-id="5a60a-118">This summary breaks down the process into steps that might otherwise get lost during the execution, and is good for an overall checklist to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="5a60a-119">首先，請確定您符合所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="5a60a-119">First, make sure you meet all the prerequisites.</span></span>

1. <span data-ttu-id="5a60a-120">自許多**必要條件**是很常見的兩個 Skype for Business 和 Exchange，[請參閱您預先需求的檢查清單概觀文章](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-120">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="5a60a-121">執行此*之前*開始任何本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="5a60a-121">Do this  *before*  you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="5a60a-122">收集您需要在檔案或 OneNote HMA 特有資訊。</span><span class="sxs-lookup"><span data-stu-id="5a60a-122">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>

1. <span data-ttu-id="5a60a-123">開啟 ON 新式驗證 EXO （如果它尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="5a60a-123">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>

1. <span data-ttu-id="5a60a-124">開啟 ON 新式驗證 SFBO （如果它尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="5a60a-124">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>

1. <span data-ttu-id="5a60a-125">開啟 Exchange 內部部署的混合式新式驗證。</span><span class="sxs-lookup"><span data-stu-id="5a60a-125">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>

1. <span data-ttu-id="5a60a-126">開啟商務內部 skype 的混合式新式驗證。</span><span class="sxs-lookup"><span data-stu-id="5a60a-126">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>

<span data-ttu-id="5a60a-127">下列步驟開啟 MA SFB、 SFBO、 NM-EXCH-UM-1ST，及 EXO-亦即可以參與 HMA 設定 SFB 和 SFBO （包括 NM-EXCH-UM-1ST/EXO 上的相依性） 的所有產品。</span><span class="sxs-lookup"><span data-stu-id="5a60a-127">These steps turn on MA for SFB, SFBO, EXCH, and EXO - that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="5a60a-128">也就是說，如果您的使用者皆位於 / 已在混合式 （EXO + SFBO、 EXO + SFB、 NM-EXCH-UM-1ST + SFBO，或 NM-EXCH-UM-1ST + SFB） 的任何部分中建立信箱，您已完成的產品看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="5a60a-128">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![商務 HMA 拓撲混合 6 商務用 Skype 具備 MA 中所有四個可能的位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="5a60a-130">您可以看到有四個不同的位置，來開啟 MA ！</span><span class="sxs-lookup"><span data-stu-id="5a60a-130">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="5a60a-131">為最佳使用者經驗，我們建議您開啟 MA 總共四個這些位置中。</span><span class="sxs-lookup"><span data-stu-id="5a60a-131">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="5a60a-132">如果您不能在所有這些位置開啟 MA，請調整步驟，讓您開啟 MA 只能在所需的環境的位置。</span><span class="sxs-lookup"><span data-stu-id="5a60a-132">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="5a60a-133">請參閱支援的拓撲[與 MA 的商務用 Skype 的支援主題](https://technet.microsoft.com/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-133">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span>
  
 <span data-ttu-id="5a60a-134">**重要**請仔細檢查您開始之前已符合所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="5a60a-134">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="5a60a-135">您會發現該資訊[以下](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-135">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="5a60a-136">收集您需要的所有 HMA 特有資訊</span><span class="sxs-lookup"><span data-stu-id="5a60a-136">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="5a60a-137">您已重複檢查，之後您已符合[先決條件](hybrid-modern-auth-overview.md)以使用新式驗證 （請參閱上述的附註），您應該建立檔案來包含您需要設定 HMA 往前的步驟中的資訊。</span><span class="sxs-lookup"><span data-stu-id="5a60a-137">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="5a60a-138">使用本文中的範例：</span><span class="sxs-lookup"><span data-stu-id="5a60a-138">Examples used in this article:</span></span>
  
- <span data-ttu-id="5a60a-139">**SIP/SMTP 網域**</span><span class="sxs-lookup"><span data-stu-id="5a60a-139">**SIP/SMTP domain**</span></span>

  - <span data-ttu-id="5a60a-140">例如</span><span class="sxs-lookup"><span data-stu-id="5a60a-140">Ex.</span></span> <span data-ttu-id="5a60a-141">contoso.com （同盟與 Office 365）</span><span class="sxs-lookup"><span data-stu-id="5a60a-141">contoso.com (is federated with Office 365)</span></span>

- <span data-ttu-id="5a60a-142">**租用戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="5a60a-142">**Tenant ID**</span></span>

  - <span data-ttu-id="5a60a-143">GUID，代表您的 Office 365 租用戶 （位於 contoso.onmicrosoft.com 的登入）。</span><span class="sxs-lookup"><span data-stu-id="5a60a-143">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>

- <span data-ttu-id="5a60a-144">**SFB 2015 CU5 Web 服務 Url**</span><span class="sxs-lookup"><span data-stu-id="5a60a-144">**SFB 2015 CU5 Web Service URLs**</span></span>

<span data-ttu-id="5a60a-145">您將需要內部和外部 web 服務 URL 的所有部署的 SfB 2015 集區。</span><span class="sxs-lookup"><span data-stu-id="5a60a-145">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="5a60a-146">若要取得這些，請執行下列從 Skype for Business 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="5a60a-146">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="5a60a-147">例如</span><span class="sxs-lookup"><span data-stu-id="5a60a-147">Ex.</span></span> <span data-ttu-id="5a60a-148">內部：https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5a60a-148">Internal: https://lyncwebint01.contoso.com</span></span>

- <span data-ttu-id="5a60a-149">例如</span><span class="sxs-lookup"><span data-stu-id="5a60a-149">Ex.</span></span> <span data-ttu-id="5a60a-150">外部：https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="5a60a-150">External: https://lyncwebext01.contoso.com</span></span>

<span data-ttu-id="5a60a-151">如果您使用 Standard Edition server，內部 URL 將會空白。</span><span class="sxs-lookup"><span data-stu-id="5a60a-151">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="5a60a-152">在此情況下，使用內部 URL 的集區 fqdn。</span><span class="sxs-lookup"><span data-stu-id="5a60a-152">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="5a60a-153">開啟 [EXO 的新式驗證</span><span class="sxs-lookup"><span data-stu-id="5a60a-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="5a60a-154">請遵循以下指示： [Exchange Online： 如何啟用新式驗證在租用戶。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="5a60a-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="5a60a-155">開啟 SFBO 的新式驗證</span><span class="sxs-lookup"><span data-stu-id="5a60a-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="5a60a-156">請遵循以下指示： [Skype for Business Online： 啟用新式驗證在租用戶](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="5a60a-157">開啟 Exchange 內部部署的混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="5a60a-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="5a60a-158">請遵循以下指示：[如何設定 Exchange Server 內部部署以使用混合式新式驗證](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="5a60a-159">開啟商務內部部署的 skype 的混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="5a60a-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="5a60a-160">新增內部 Azure AD 中為 Spn web 服務 Url</span><span class="sxs-lookup"><span data-stu-id="5a60a-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="5a60a-161">現在您需要執行命令，以作為服務主體中 SFBO 新增 （收集更早版本） 的 Url。</span><span class="sxs-lookup"><span data-stu-id="5a60a-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="5a60a-162">**附註**服務主要名稱 (Spn) 識別 web 服務，以及其關聯 （例如帳戶名稱或群組） 的安全性主體，讓該服務可對授權的使用者代理。</span><span class="sxs-lookup"><span data-stu-id="5a60a-162">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="5a60a-163">伺服器進行驗證的用戶端進行使用的資訊的中所含的 Spn。</span><span class="sxs-lookup"><span data-stu-id="5a60a-163">Clients authenticating to a server make use of information that's contained in SPNs.</span></span>
  
1. <span data-ttu-id="5a60a-164">首先，連線至 AAD[這些](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)指示。</span><span class="sxs-lookup"><span data-stu-id="5a60a-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>

2. <span data-ttu-id="5a60a-165">執行此命令中，內部部署，若要取得之 SFB web 服務 Url 的清單。</span><span class="sxs-lookup"><span data-stu-id="5a60a-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="5a60a-166">請注意，AppPrincipalId 開頭`00000004`。</span><span class="sxs-lookup"><span data-stu-id="5a60a-166">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="5a60a-167">這會對應到 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="5a60a-167">This corresponds to Skype for Business Online.</span></span>

   <span data-ttu-id="5a60a-168">此命令，它會包括 SE 和 WS URL，但是大部分所組成的開頭的 Spn 的輸出採取的附註 （和更新版本的比對的螢幕擷取畫面） `00000004-0000-0ff1-ce00-000000000000/`。</span><span class="sxs-lookup"><span data-stu-id="5a60a-168">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. <span data-ttu-id="5a60a-169">如果內部**或**外部遺漏了從內部 SFB Url (例如https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我們需要將這些特定記錄新增至這份清單。</span><span class="sxs-lookup"><span data-stu-id="5a60a-169">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span>

    <span data-ttu-id="5a60a-170">請務必*範例 Url* ] 下方，取代實際 Url 中新增命令 ！</span><span class="sxs-lookup"><span data-stu-id="5a60a-170">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span>
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="5a60a-171">確認您新的記錄已新增步驟 2 中**取得 MsolServicePrincipal**命令執行，並將輸出中尋找。</span><span class="sxs-lookup"><span data-stu-id="5a60a-171">Verify your new records were added by running the **Get-MsolServicePrincipal** command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="5a60a-172">比較清單 / 將螢幕擷取畫面從之前的 Spn （您可能也螢幕擷取畫面新清單以供記錄） 新的清單。</span><span class="sxs-lookup"><span data-stu-id="5a60a-172">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="5a60a-173">如果您已成功，您會看到兩個新的 Url 清單中。</span><span class="sxs-lookup"><span data-stu-id="5a60a-173">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="5a60a-174">將由我們的範例，此清單的 Spn 將現在包含特定 Urlhttps://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com/。</span><span class="sxs-lookup"><span data-stu-id="5a60a-174">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>

### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="5a60a-175">建立 EvoSTS 驗證伺服器物件</span><span class="sxs-lookup"><span data-stu-id="5a60a-175">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="5a60a-176">下列中執行命令 Skype for Business 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="5a60a-176">Run the following command in the Skype for Business Management Shell.</span></span>
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="5a60a-177">啟用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="5a60a-177">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="5a60a-178">這是實際開啟 MA 的步驟。</span><span class="sxs-lookup"><span data-stu-id="5a60a-178">This is the step that actually turns MA on.</span></span> <span data-ttu-id="5a60a-179">所有先前的步驟可以執行事先，而不需要變更用戶端驗證流程。</span><span class="sxs-lookup"><span data-stu-id="5a60a-179">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="5a60a-180">當您準備好要變更的驗證流程時，執行此命令中 Skype for Business 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="5a60a-180">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a><span data-ttu-id="5a60a-181">確認</span><span class="sxs-lookup"><span data-stu-id="5a60a-181">Verify</span></span>

<span data-ttu-id="5a60a-182">一旦您啟用 HMA，用戶端下次登入時會使用新的驗證流程。</span><span class="sxs-lookup"><span data-stu-id="5a60a-182">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="5a60a-183">請注意，只開啟 HMA 就不會觸發重新驗證任何用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a60a-183">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="5a60a-184">用戶端重新驗證為基礎的存留期的驗證權杖及/或他們所擁有的憑證。</span><span class="sxs-lookup"><span data-stu-id="5a60a-184">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="5a60a-185">若要測試 HMA 正常之後您已啟用它，登出測試 SFB Windows 用戶端，請務必按一下 [刪除我的認證]。</span><span class="sxs-lookup"><span data-stu-id="5a60a-185">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="5a60a-186">再次登入。</span><span class="sxs-lookup"><span data-stu-id="5a60a-186">Sign in again.</span></span> <span data-ttu-id="5a60a-187">用戶端現在應該使用新式驗證流程和您的登入現在包含 '工作或學校' 的**Office 365**提示看右之前用戶端連絡伺服器，而且您登入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5a60a-187">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span>
  
<span data-ttu-id="5a60a-188">您應該也檢查組態資訊 skype 商務用戶端 'OAuth 授權單位 」。</span><span class="sxs-lookup"><span data-stu-id="5a60a-188">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="5a60a-189">用戶端電腦上執行這項操作，請按住 CTRL 鍵在同一時間以滑鼠右鍵按一下 Skype for Business 圖示 Windows 通知紙匣。</span><span class="sxs-lookup"><span data-stu-id="5a60a-189">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="5a60a-190">在出現的功能表中，按一下 [**設定資訊**。</span><span class="sxs-lookup"><span data-stu-id="5a60a-190">Click **Configuration Information** in the menu that appears.</span></span> <span data-ttu-id="5a60a-191">在桌面上會出現 ['Skype for Business 組態資訊'] 視窗中，尋找下列：</span><span class="sxs-lookup"><span data-stu-id="5a60a-191">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![商務用戶端使用新式驗證用 Skype 的組態資訊會顯示 Lync 和 EWS OAUTH 授權 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="5a60a-193">您也應按住 CTRL 鍵，同時以滑鼠右鍵按一下 [Outlook 用戶端 （也在 Windows 通知紙匣）] 圖示，然後按一下 [' 連線狀態 '。</span><span class="sxs-lookup"><span data-stu-id="5a60a-193">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="5a60a-194">用戶端的 SMTP 位址是否與 AuthN 類型尋找 ' 承載\*'，用來表示用於 OAuth 承載 token。</span><span class="sxs-lookup"><span data-stu-id="5a60a-194">Look for the client's SMTP address against an AuthN type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="5a60a-195">相關文章</span><span class="sxs-lookup"><span data-stu-id="5a60a-195">Related articles</span></span>

<span data-ttu-id="5a60a-196">[新式驗證概觀連結](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-196">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md).</span></span>
  
<span data-ttu-id="5a60a-197">您需要了解如何使用您 skype 的新式驗證 (ADAL) 的商務用戶端嗎？</span><span class="sxs-lookup"><span data-stu-id="5a60a-197">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="5a60a-198">我們是否已取得最新產品步驟[以下](https://technet.microsoft.com/library/mt710548.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5a60a-198">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
