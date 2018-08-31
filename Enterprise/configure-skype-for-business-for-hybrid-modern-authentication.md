---
title: 如何設定商務用 Skype 內部部署以使用混合式新式驗證 (英文)
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
description: 經過驗證是一種方法提供較安全的使用者驗證與授權、 供商務 server 內部部署和 Exchange server 內部部署，以及商務混合的分隔網域 Skype Skype 的身分識別管理。
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540279"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="458a7-103">如何設定商務用 Skype 內部部署以使用混合式新式驗證 (英文)</span><span class="sxs-lookup"><span data-stu-id="458a7-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="458a7-104">經過驗證是一種方法提供較安全的使用者驗證與授權、 供商務 server 內部部署和 Exchange server 內部部署，以及商務混合的分隔網域 Skype Skype 的身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="458a7-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="458a7-p101">**重要**您要了解更多有關現代驗證 (MA) 與您可能希望使用公司或組織中嗎吗？檢查[此文件](hybrid-modern-auth-overview.md)的概觀。如果您需要知道什麼 Skype for Business 拓撲支援 MA，此處所記載的 ！</span><span class="sxs-lookup"><span data-stu-id="458a7-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="458a7-108">**我們開始之前**，請使用呼叫：</span><span class="sxs-lookup"><span data-stu-id="458a7-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="458a7-109">現代驗證\>MA</span><span class="sxs-lookup"><span data-stu-id="458a7-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="458a7-110">混合式現代驗證\>HMA</span><span class="sxs-lookup"><span data-stu-id="458a7-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="458a7-111">Exchange 內部部署\>NM-EXCH-UM-1ST</span><span class="sxs-lookup"><span data-stu-id="458a7-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="458a7-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="458a7-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="458a7-113">企業內部的 Skype \> SFB</span><span class="sxs-lookup"><span data-stu-id="458a7-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="458a7-114">和 Skype 的線上商務\>SFBO</span><span class="sxs-lookup"><span data-stu-id="458a7-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="458a7-115">此外，\* 如果本文中的圖形具有物件 ' 變為 out' 或 '變暗'，表示灰色**不**包含在 MA 特有設定中所示的元素。</span><span class="sxs-lookup"><span data-stu-id="458a7-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="458a7-116">閱讀摘要</span><span class="sxs-lookup"><span data-stu-id="458a7-116">Read the summary</span></span>

<span data-ttu-id="458a7-117">此摘要 boils 程序將可能否則取得遺失執行期間並良好的整體檢查清單可保留所程序中的追蹤記錄的步驟。</span><span class="sxs-lookup"><span data-stu-id="458a7-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="458a7-118">首先，請確定您符合所有必要軟體。</span><span class="sxs-lookup"><span data-stu-id="458a7-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="458a7-p102">自許多**必要條件**都通用的兩個 Skype 的業務與 Exchange，[請參閱概觀 （英文） 之前需求檢查清單](hybrid-modern-auth-overview.md)。執行此作業此*之前*開始執行任何本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="458a7-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="458a7-121">收集您需要在檔案或 OneNote HMA 特定資訊。</span><span class="sxs-lookup"><span data-stu-id="458a7-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="458a7-122">開啟 ON 經過驗證的 EXO （如果它尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="458a7-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="458a7-123">開啟 ON 經過驗證的 SFBO （如果它尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="458a7-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="458a7-124">開啟 Exchange 內部部署的混合式經過驗證。</span><span class="sxs-lookup"><span data-stu-id="458a7-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="458a7-125">開啟商務內部部署混合式的 Skype 經過驗證。</span><span class="sxs-lookup"><span data-stu-id="458a7-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="458a7-p103">請注意下列步驟開啟 MA SFB、 SFBO、 NM-EXCH-UM-1ST 及 EXO-亦即可以參與 HMA 設定 SFB 和 SFBO （包括 NM-EXCH-UM-1ST/EXO 相依關係） 的所有產品。換句話說，如果您的使用者皆位於 / 已在混合式 （EXO + SFBO、 EXO + SFB、 NM-EXCH-UM-1ST + SFBO，或 NM-EXCH-UM-1ST + SFB） 的任何部分中建立信箱，您完成的產品會看起來如下：</span><span class="sxs-lookup"><span data-stu-id="458a7-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![商務 HMA 拓撲的混合 6 Skype 具有 MA 中所有的四個可能位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="458a7-p104">您可以看到有四種不同的位置可開啟 MA ！最佳使用者經驗的建議您開啟 MA 中所有的四個位置。如果您不能在所有這些位置開啟 MA，使您開啟位置所需的環境中僅 MA 調整步驟。</span><span class="sxs-lookup"><span data-stu-id="458a7-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="458a7-132">請參閱支援的拓撲[支援 Skype for Business 與 MA 的主題](https://technet.microsoft.com/en-us/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="458a7-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="458a7-p105">**重要**請仔細檢查您是否已符合所有必要軟體之前。您會找到該資訊[此處](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="458a7-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="458a7-135">收集您需要的所有 HMA 專屬資訊</span><span class="sxs-lookup"><span data-stu-id="458a7-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="458a7-p106">您是否已重複的檢查之後您已符合[先決條件](hybrid-modern-auth-overview.md)使用經過驗證 （請參閱上面的附註），則應該建立檔案來包含您需要設定 HMA 在繼續進行步驟中的資訊。使用本文中的範例：</span><span class="sxs-lookup"><span data-stu-id="458a7-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="458a7-138">**SIP/SMTP 網域**</span><span class="sxs-lookup"><span data-stu-id="458a7-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="458a7-p107">例如 contoso.com （聯盟與 Office 365）</span><span class="sxs-lookup"><span data-stu-id="458a7-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="458a7-141">**租用戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="458a7-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="458a7-142">代表您的 Office 365 租用戶 （位於 contoso.onmicrosoft.com 登入） 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="458a7-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="458a7-143">**SFB 2015 CU5 Web 服務 Url**</span><span class="sxs-lookup"><span data-stu-id="458a7-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="458a7-p108">您必須內部和外部 web 服務 URL 的部署的所有 SfB 2015 集區。若要取得這些，執行下列從 Skype 商務管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="458a7-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="458a7-146">Get-csservice-WebServer |Select-object PoolFqdn、 InternalFqdn、 ExternalFqdn |FL</span><span class="sxs-lookup"><span data-stu-id="458a7-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="458a7-p109">例如內部：https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="458a7-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="458a7-p110">例如外部：https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="458a7-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="458a7-p111">如果您使用 Standard Edition server，將會是空白的內部 URL。在此例中，使用內部 URL 的集區 fqdn。</span><span class="sxs-lookup"><span data-stu-id="458a7-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="458a7-153">開啟 [EXO 現代驗證</span><span class="sxs-lookup"><span data-stu-id="458a7-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="458a7-154">請遵循此處的指示： [Exchange Online： 如何啟用經過驗證的租用戶。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="458a7-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="458a7-155">開啟經過驗證的 SFBO</span><span class="sxs-lookup"><span data-stu-id="458a7-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="458a7-156">遵循此處的指示： [Skype 商務 online： 啟用經過驗證的租用戶](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="458a7-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="458a7-157">開啟混合經過驗證的 Exchange 內部部署</span><span class="sxs-lookup"><span data-stu-id="458a7-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="458a7-158">請遵循此處的指示：[如何設定 Exchange Server 內部使用混合式經過驗證](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="458a7-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="458a7-159">開啟商務內部 Skype 的交互式現代驗證</span><span class="sxs-lookup"><span data-stu-id="458a7-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="458a7-160">新增內部部署在 Azure AD 為 Spn web 服務 Url</span><span class="sxs-lookup"><span data-stu-id="458a7-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="458a7-161">現在您需要執行命令以新增為 SFBO 中的服務主體 （收集稍早） 的 Url。</span><span class="sxs-lookup"><span data-stu-id="458a7-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="458a7-p112">**附註**服務主要名稱 (Spn) 識別 web 服務和其關聯 （例如帳戶名稱或群組） 的安全性主體，讓此服務可處理的授權的使用者代理。驗證伺服器的用戶端利用的資訊的中所含的 Spn。</span><span class="sxs-lookup"><span data-stu-id="458a7-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="458a7-164">首先，連線至 AAD[這些指示](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)。</span><span class="sxs-lookup"><span data-stu-id="458a7-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="458a7-165">執行此命令中，內部，以取得 SFB web 服務 Url 的清單。</span><span class="sxs-lookup"><span data-stu-id="458a7-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="458a7-166">取得 MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 |選取 [-ExpandProperty ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="458a7-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="458a7-p113">請注意 AppPrincipalId 開頭 '00000004'。這會對應至 Skype 商務 online。</span><span class="sxs-lookup"><span data-stu-id="458a7-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="458a7-169">此命令將會包含 SE 和 WS URL，但多半組成 00000004-0000-0ff1-ce00-000000000000 的開頭的 Spn 的輸出採取的附註 （及更新版本比較的螢幕擷取畫面） /。</span><span class="sxs-lookup"><span data-stu-id="458a7-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="458a7-170">如果內部**或**外部從內部部署的 SFB Url 會遺失 (例如https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我們需要將這些特定的記錄新增至這份清單。</span><span class="sxs-lookup"><span data-stu-id="458a7-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="458a7-171">請務必下方的*範例 Url*取代實際 Url 中新增命令 ！</span><span class="sxs-lookup"><span data-stu-id="458a7-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="458a7-172">$x = get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="458a7-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="458a7-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="458a7-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="458a7-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="458a7-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="458a7-175">設定 MSOLServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000-ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="458a7-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="458a7-p114">確認新的記錄已新增再次執行步驟 2 的 Get MsolServicePrincipal 命令並尋找透過輸出。將清單進行比較 / 螢幕擷取畫面從之前至新的 Spn （您也可以螢幕擷取畫面新清單的記錄） 清單。如果您已成功，您會看到兩個新的 Url 清單中。不再由我們的範例的 Spn 清單將會立即包含特定 Urlhttps://lyncweb01.contoso.com和https://autodiscover.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="458a7-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="458a7-180">建立 EvoSTS 驗證伺服器物件</span><span class="sxs-lookup"><span data-stu-id="458a7-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="458a7-181">商務管理命令介面 Skype 執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="458a7-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="458a7-182">New-csoauthserver-Identity evoSTS-MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true-類型 AzureAD</span><span class="sxs-lookup"><span data-stu-id="458a7-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="458a7-183">啟用混合現代驗證</span><span class="sxs-lookup"><span data-stu-id="458a7-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="458a7-p115">這是實際開啟 MA 的步驟。所有先前的步驟可以隨時執行而不變更用戶端驗證流程。當您準備好要變更的驗證流程時，請執行此命令中 Skype 商務管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="458a7-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="458a7-187">Set-csoauthconfiguration-ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="458a7-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="458a7-188">[驗證]</span><span class="sxs-lookup"><span data-stu-id="458a7-188">Verify</span></span>

<span data-ttu-id="458a7-p116">一旦您啟用 HMA，用戶端的下一個登入將會使用新的驗證流程。請注意剛開啟 HMA 將不會觸發重新驗證的任何用戶端。用戶端重新驗證的驗證 token 及 （或） 憑證有存留期為基礎。</span><span class="sxs-lookup"><span data-stu-id="458a7-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="458a7-p117">若要測試您已啟用它之後的運作 HMA，登出測試 SFB Windows 用戶端和務必按一下 [刪除我的認證]。再次登入。用戶端現在應該使用經過驗證流程與您的登入現在包含 '工作或學校' 的**Office 365**提示呈現右之前用戶端連絡伺服器，並在記錄您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="458a7-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="458a7-p118">您應該也檢查組態資訊 Skype 商務用戶端的 OAuth 授權 」。用戶端電腦上執行這項作業，請按住 CTRL 鍵，同時您用滑鼠右鍵按一下 Skype 商務圖示中的 Windows 通知紙匣。在出現的功能表中按一下 [設定資訊。在桌上型電腦會出現 ['Skype 的商務組態資訊 」] 視窗中，尋找下列：</span><span class="sxs-lookup"><span data-stu-id="458a7-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![商務用戶端使用經過驗證的組態資訊之 Skype 顯示 Lync 和 EWS OAUTH 授權 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="458a7-p119">您也應該以滑鼠右鍵按一下圖示 Outlook 用戶端 （也是在 Windows 通知紙匣中） 的同時按住 CTRL 鍵並按一下 ' 連線狀態 」。針對根據驗證類型的用戶端的 SMTP 位址看起來 ' 承載\*'，這代表用於 OAuth 承載 token。</span><span class="sxs-lookup"><span data-stu-id="458a7-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="458a7-202">相關的文章</span><span class="sxs-lookup"><span data-stu-id="458a7-202">Related articles</span></span>

<span data-ttu-id="458a7-203">[現代驗證概觀連結](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="458a7-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="458a7-p120">您需要了解如何使用您 Skype 商務用戶端的現代驗證 (ADAL)？我們已 got 步驟[此處](https://technet.microsoft.com/en-us/library/mt710548.aspx)。</span><span class="sxs-lookup"><span data-stu-id="458a7-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="458a7-p121">是否要閱讀這些步驟，因為他們顯示的 Exchange Server 內部部署、 執行沒有 SFB 吗？這些步驟這裡可供使用。</span><span class="sxs-lookup"><span data-stu-id="458a7-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

