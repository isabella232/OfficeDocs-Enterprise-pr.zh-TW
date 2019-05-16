---
title: 如何設定 Exchange Server 內部部署以使用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: 混合式新式驗證 (HMA)，是一種方法的身分識別管理，提供更安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合式部署。
ms.openlocfilehash: 98a47f9527b3922767bfd8240790d7cfdeb14936
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068039"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="d786f-103">如何設定 Exchange Server 內部部署以使用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="d786f-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="d786f-104">混合式新式驗證 (HMA)，是一種方法的身分識別管理，提供更安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合式部署。</span><span class="sxs-lookup"><span data-stu-id="d786f-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="d786f-105">參考 FYI</span><span class="sxs-lookup"><span data-stu-id="d786f-105">FYI</span></span>

<span data-ttu-id="d786f-106">開始之前，我呼叫：</span><span class="sxs-lookup"><span data-stu-id="d786f-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="d786f-107">混合式新式驗證\>HMA</span><span class="sxs-lookup"><span data-stu-id="d786f-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="d786f-108">Exchange 內部部署\>NM-EXCH-UM-1ST</span><span class="sxs-lookup"><span data-stu-id="d786f-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="d786f-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="d786f-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="d786f-110">此外，*本文如果中的圖形具有找出具有 ' 變為 out' 或暗灰色所示的項目不包含在 HMA 特有設定這表示物件*。</span><span class="sxs-lookup"><span data-stu-id="d786f-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="d786f-111">啟用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="d786f-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="d786f-112">表示開啟 HMA:</span><span class="sxs-lookup"><span data-stu-id="d786f-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="d786f-113">要確定您符合必要條件之前。</span><span class="sxs-lookup"><span data-stu-id="d786f-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="d786f-114">自許多**必要條件**是很常見的兩個 Skype for Business 和 Exchange[混合式新式驗證概觀及必要條件使用它與內部部署 Skype for Business 和 Exchange 伺服器](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d786f-114">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="d786f-115">開始之前任何本文中的步驟，請執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="d786f-115">Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="d786f-116">新增內部 web 服務 Url 為服務主要名稱 (Spn) 在 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="d786f-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="d786f-117">確保所有虛擬目錄啟用 HMA</span><span class="sxs-lookup"><span data-stu-id="d786f-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="d786f-118">檢查 EvoSTS 驗證伺服器物件</span><span class="sxs-lookup"><span data-stu-id="d786f-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="d786f-119">啟用 HMA EXCH.中</span><span class="sxs-lookup"><span data-stu-id="d786f-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="d786f-120">**附註**您的 Office 版本是否支援 MA？</span><span class="sxs-lookup"><span data-stu-id="d786f-120">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="d786f-121">請參閱 < <b0>Office 2013 和 Office 2016 用戶端應用程式的方式新式驗證運作</b0>。</span><span class="sxs-lookup"><span data-stu-id="d786f-121">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="d786f-122">請確定您符合所有預先-需求</span><span class="sxs-lookup"><span data-stu-id="d786f-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="d786f-123">由於許多必要條件是很常見的兩個 Skype for Business 和 Exchange，檢閱[混合式新式驗證概觀及使用它與內部部署 Skype for Business 和 Exchange 伺服器的必要條件](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d786f-123">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="d786f-124">執行此*之前*開始任何本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="d786f-124">Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="d786f-125">新增內部 Azure AD 中為 Spn web 服務 Url</span><span class="sxs-lookup"><span data-stu-id="d786f-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="d786f-126">執行命令，指派內部 web 服務 Url 為 Azure AD Spn。</span><span class="sxs-lookup"><span data-stu-id="d786f-126">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="d786f-127">用戶端電腦和裝置會使用 Spn 期間驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="d786f-127">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="d786f-128">（這包括內部和外部命名空間） 的 AAD 中必須註冊可能用來從內部連線到 Azure Active Directory (AAD) 的所有 Url。</span><span class="sxs-lookup"><span data-stu-id="d786f-128">All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="d786f-129">首先，收集您需要新增的 AAD 中的所有 Url。</span><span class="sxs-lookup"><span data-stu-id="d786f-129">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="d786f-130">執行這些命令在內部部署：</span><span class="sxs-lookup"><span data-stu-id="d786f-130">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="d786f-131">確定用戶端可能連線至列為 HTTPS 服務主要名稱的 AAD 中的 Url。</span><span class="sxs-lookup"><span data-stu-id="d786f-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="d786f-132">首先，連線至 AAD[這些](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)指示。</span><span class="sxs-lookup"><span data-stu-id="d786f-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="d786f-133">**附註**您要使用此頁面的 [Connect-msolservice 選項無法使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="d786f-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="d786f-134">針對您的 Exchange 相關的 Url，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d786f-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="d786f-135">此命令，它應該包括 https:// *autodiscover.yourdomain.com*和 https:// *mail.yourdomain.com* URL，但是大部分所組成的開頭的 Spn 的輸出採取的附註 （和更新版本的比對的螢幕擷取畫面）00000002-0000-0ff1-ce00-000000000000 /。</span><span class="sxs-lookup"><span data-stu-id="d786f-135">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="d786f-136">如果有從您的內部所遺失的 https:// Url 我們將需要這些特定記錄新增到此清單。</span><span class="sxs-lookup"><span data-stu-id="d786f-136">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="d786f-137">如果您沒有看到您內部和外部 MAPI/HTTP、 EWS、 ActiveSync、 OAB 和自動探索記錄此清單中的，您必須新增其使用下列命令 (範例 Url 是 '`mail.corp.contoso.com`'和'`owa.contoso.com`'，但是您必須**取代以您自己的範例 Url** ):</span><span class="sxs-lookup"><span data-stu-id="d786f-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="d786f-138">確認您新的記錄已新增步驟 2 中取得 MsolServicePrincipal 命令執行，並將輸出中尋找。</span><span class="sxs-lookup"><span data-stu-id="d786f-138">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="d786f-139">比較清單 / 將螢幕擷取畫面從之前的 Spn （您可能也螢幕擷取畫面新清單以供記錄） 新的清單。</span><span class="sxs-lookup"><span data-stu-id="d786f-139">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="d786f-140">如果您已成功，您會看到兩個新的 Url 清單中。</span><span class="sxs-lookup"><span data-stu-id="d786f-140">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="d786f-141">將由我們的範例，此清單的 Spn 將現在包含特定 Url`https://mail.corp.contoso.com`和`https://owa.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="d786f-141">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="d786f-142">確認虛擬目錄設定正確</span><span class="sxs-lookup"><span data-stu-id="d786f-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="d786f-143">現在請確認中正確地啟用 OAuth 上所有虛擬目錄 Outlook Exchange 可能會使用藉由執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d786f-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="d786f-144">核取輸出至請確定**OAuth**啟用每個這些 VDirs 它看起來像這樣 （，若要查看的重點是 'OAuth'）;</span><span class="sxs-lookup"><span data-stu-id="d786f-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="d786f-145">如果 OAuth 遺漏來自任何伺服器和四個虛擬目錄的任何您需要新增使用相關的命令，再繼續執行它。</span><span class="sxs-lookup"><span data-stu-id="d786f-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="d786f-146">確認 EvoSTS 驗證伺服器物件是展示</span><span class="sxs-lookup"><span data-stu-id="d786f-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="d786f-147">會傳回內部部署 Exchange 管理命令介面，此最後一個命令。</span><span class="sxs-lookup"><span data-stu-id="d786f-147">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="d786f-148">現在您可以驗證內部有項目，evoSTS 驗證提供者：</span><span class="sxs-lookup"><span data-stu-id="d786f-148">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="d786f-149">您的輸出應該會顯示名稱 EvoSts AuthServer 和 [啟用] 狀態應為 True。</span><span class="sxs-lookup"><span data-stu-id="d786f-149">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="d786f-150">如果您沒有看到此，您應該下載並執行混合組態精靈的最新版本。</span><span class="sxs-lookup"><span data-stu-id="d786f-150">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="d786f-151">**重要**如果您正在執行 Exchange 2010 環境中，不會建立 EvoSTS 驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="d786f-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="d786f-152">啟用 HMA</span><span class="sxs-lookup"><span data-stu-id="d786f-152">Enable HMA</span></span>

<span data-ttu-id="d786f-153">在 Exchange 管理命令介面，內部部署中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d786f-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="d786f-154">確認</span><span class="sxs-lookup"><span data-stu-id="d786f-154">Verify</span></span>

<span data-ttu-id="d786f-155">一旦您啟用 HMA，用戶端下次登入時會使用新的驗證流程。</span><span class="sxs-lookup"><span data-stu-id="d786f-155">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="d786f-156">請注意，只開啟 HMA 就不會觸發重新驗證任何用戶端。</span><span class="sxs-lookup"><span data-stu-id="d786f-156">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="d786f-157">用戶端重新驗證為基礎的存留期的驗證權杖及/或他們所擁有的憑證。</span><span class="sxs-lookup"><span data-stu-id="d786f-157">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="d786f-158">您也應按住 CTRL 鍵，同時以滑鼠右鍵按一下 [Outlook 用戶端 （也在 Windows 通知紙匣）] 圖示，然後按一下 [' 連線狀態 '。</span><span class="sxs-lookup"><span data-stu-id="d786f-158">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="d786f-159">尋找針對 'Authn' 類型的用戶端的 SMTP 位址 ' 承載\*'，用來表示用於 OAuth 承載 token。</span><span class="sxs-lookup"><span data-stu-id="d786f-159">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="d786f-160">**附註**需要使用 HMA 設定商務用 Skype？</span><span class="sxs-lookup"><span data-stu-id="d786f-160">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="d786f-161">您將需要兩篇文章： 一個列出[支援的拓撲](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)，而另一個示範[如何進行設定](configure-skype-for-business-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="d786f-161">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="d786f-162">相關主題</span><span class="sxs-lookup"><span data-stu-id="d786f-162">Related topics</span></span>

[<span data-ttu-id="d786f-163">混合式新式驗證概觀及使用商務和 Exchange 伺服器內部部署用 Skype 的必要條件</span><span class="sxs-lookup"><span data-stu-id="d786f-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

