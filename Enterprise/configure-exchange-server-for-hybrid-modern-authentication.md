---
title: 如何設定 Exchange Server 內部部署以使用混合式新式驗證
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 混合式現代驗證 (HMA)，是一種方法提供較安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合部署的身分識別管理。
ms.openlocfilehash: df5ea03b06ee1c101b03e19c7acb445c9543586b
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547155"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="205fa-103">如何設定 Exchange Server 內部部署以使用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="205fa-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="205fa-104">混合式現代驗證 (HMA)，是一種方法提供較安全的使用者驗證和授權，以及適用於 Exchange server 內部部署混合部署的身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="205fa-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="205fa-105">參考 FYI</span><span class="sxs-lookup"><span data-stu-id="205fa-105">FYI</span></span>

<span data-ttu-id="205fa-106">我們開始前，我呼叫：</span><span class="sxs-lookup"><span data-stu-id="205fa-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="205fa-107">混合式現代驗證\>HMA</span><span class="sxs-lookup"><span data-stu-id="205fa-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="205fa-108">Exchange 內部部署\>NM-EXCH-UM-1ST</span><span class="sxs-lookup"><span data-stu-id="205fa-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="205fa-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="205fa-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="205fa-110">此外，*本文如果中的圖形具有找出具有 ' 變為 out' 或暗灰色中顯示的項目未包含在 HMA 特有設定說的物件*。</span><span class="sxs-lookup"><span data-stu-id="205fa-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="205fa-111">啟用混合現代驗證</span><span class="sxs-lookup"><span data-stu-id="205fa-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="205fa-112">表示開啟 HMA：</span><span class="sxs-lookup"><span data-stu-id="205fa-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="205fa-113">要確定您符合必要條件是之前。</span><span class="sxs-lookup"><span data-stu-id="205fa-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="205fa-p101">自許多**必要條件**都通用的商務與 Exchange[混合式現代驗證概觀及使用它與先決條件內部 Skype 業務與 Exchange 伺服器的](hybrid-modern-auth-overview.md)兩個 Skype。這麼做之前任何本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="205fa-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="205fa-116">新增內部 web 服務 Url 為服務主要名稱 (Spn) 的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="205fa-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="205fa-117">確保所有虛擬目錄啟用 HMA</span><span class="sxs-lookup"><span data-stu-id="205fa-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="205fa-118">檢查 EvoSTS 驗證伺服器物件</span><span class="sxs-lookup"><span data-stu-id="205fa-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="205fa-119">啟用 HMA EXCH.中</span><span class="sxs-lookup"><span data-stu-id="205fa-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="205fa-p102">**附註**您的 Office 版本是否支援 MA 吗？請參閱 ＜ [Office 2013 與 Office 2016 用戶端應用程式如何經過驗證的運作](modern-auth-for-office-2013-and-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="205fa-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="205fa-122">請確定您符合所有之前-需求</span><span class="sxs-lookup"><span data-stu-id="205fa-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="205fa-p103">由於許多必要條件都通用的商務與 Exchange 的這兩個 Skype、 檢閱[混合現代驗證概觀及使用它與內部部署 Skype 業務與 Exchange 伺服器的先決條件](hybrid-modern-auth-overview.md)。執行此作業此*之前*開始執行任何本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="205fa-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="205fa-125">新增內部部署在 Azure AD 為 Spn web 服務 Url</span><span class="sxs-lookup"><span data-stu-id="205fa-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="205fa-p104">執行命令指派內部 web 服務 Url 為 Azure AD 的 Spn。 Spn 用戶端機器及裝置所使用的驗證和授權期間。可能會用來從內部連線至 Azure Active Directory (AAD) 的所有 Url 必須都登錄於 AAD （包括內部和外部的命名空間）。</span><span class="sxs-lookup"><span data-stu-id="205fa-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="205fa-p105">首先，收集您需要在 AAD 中新增的所有 Url。執行這些命令在內部部署：</span><span class="sxs-lookup"><span data-stu-id="205fa-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
<span data-ttu-id="205fa-131">確定用戶端可以連線至列為 AAD 中 HTTPS 服務主要名稱的 Url。</span><span class="sxs-lookup"><span data-stu-id="205fa-131">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="205fa-132">首先，連線至 AAD[這些指示](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="205fa-132">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

 <span data-ttu-id="205fa-133">**附註**您需要使用從此頁面 Connect-msolservice 選項，可以使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="205fa-133">**Note** You need to use the Connect-MsolService option from this page to be able to use the command below.</span></span> 
    
2. <span data-ttu-id="205fa-134">針對 Exchange 相關的 Url，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="205fa-134">For your Exchange related URLs, type the following command:</span></span>
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="205fa-p106">您應該包括 https:// *autodiscover.yourdomain.com*和 https:// *mail.yourdomain.com* URL，但多半包含開頭的 Spn 此命令的輸出採取的附註 （及更新版本比較的螢幕擷取畫面）00000002-0000-0ff1-ce00-000000000000 /。如果有從您的內部，遺漏的 https:// Url 我們必須將這些特定的記錄新增至這份清單。</span><span class="sxs-lookup"><span data-stu-id="205fa-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="205fa-137">如果您沒有看到您內部和外部 MAPI/HTTP、 EWS、 ActiveSync、 OAB 和自動探索記錄這份清單中的，您必須新增其使用下列命令 (範例 Url 是 '`mail.corp.contoso.com`'與'`owa.contoso.com`'，但您有**取代與您自己的範例 Url** ):</span><span class="sxs-lookup"><span data-stu-id="205fa-137">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="205fa-p107">確認新的記錄已新增再次執行步驟 2 的 Get MsolServicePrincipal 命令並尋找透過輸出。將清單進行比較 / 螢幕擷取畫面從之前至新的 Spn （您也可以螢幕擷取畫面新清單的記錄） 清單。如果您已成功，您會看到兩個新的 Url 清單中。不再由我們的範例的 Spn 清單將會立即包含特定 Url`https://mail.corp.contoso.com`和`https://owa.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="205fa-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="205fa-142">確認虛擬目錄已正確設定</span><span class="sxs-lookup"><span data-stu-id="205fa-142">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="205fa-143">現在確認中適當地啟用 OAuth 上所有虛擬目錄 Outlook 與 Exchange 可能會使用執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="205fa-143">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="205fa-144">在每個這些 VDirs 上啟用] 核取輸出至請確定**OAuth** 、 外觀類似如下 （及查看的重點是 'OAuth'）;</span><span class="sxs-lookup"><span data-stu-id="205fa-144">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 

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
  
<span data-ttu-id="205fa-145">如果 OAuth 遺漏來自任何伺服器和四個虛擬目錄的任何您需要新增使用相關命令再繼續執行它。</span><span class="sxs-lookup"><span data-stu-id="205fa-145">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="205fa-146">確認 EvoSTS 驗證伺服器物件存在</span><span class="sxs-lookup"><span data-stu-id="205fa-146">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="205fa-p108">會傳回此最後一個命令會在內部部署 Exchange 管理命令介面。現在您可以驗證您的內部具有項目 evoSTS 驗證提供者：</span><span class="sxs-lookup"><span data-stu-id="205fa-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="205fa-p109">您的輸出應顯示的名稱 EvoSts AuthServer 和 [啟用] 狀態應該是 True。如果您沒有看到此，您應該下載並執行 [混合組態精靈] 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="205fa-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="205fa-151">**重要**如果您正在執行 Exchange 2010 環境中，將不會建立 EvoSTS 驗證提供者。</span><span class="sxs-lookup"><span data-stu-id="205fa-151">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="205fa-152">啟用 HMA</span><span class="sxs-lookup"><span data-stu-id="205fa-152">Enable HMA</span></span>

<span data-ttu-id="205fa-153">在 Exchange 管理命令介面，在內部部署中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="205fa-153">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="205fa-154">[驗證]</span><span class="sxs-lookup"><span data-stu-id="205fa-154">Verify</span></span>

<span data-ttu-id="205fa-p110">一旦您啟用 HMA，用戶端的下一個登入將會使用新的驗證流程。請注意剛開啟 HMA 將不會觸發重新驗證的任何用戶端。用戶端重新驗證的驗證 token 及 （或） 憑證有存留期為基礎。</span><span class="sxs-lookup"><span data-stu-id="205fa-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="205fa-p111">您也應該以滑鼠右鍵按一下圖示 Outlook 用戶端 （也是在 Windows 通知紙匣中） 的同時按住 CTRL 鍵並按一下 ' 連線狀態 」。針對 「 驗證 」 類型的用戶端的 SMTP 位址看起來 ' 承載\*'，這代表用於 OAuth 承載 token。</span><span class="sxs-lookup"><span data-stu-id="205fa-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="205fa-p112">**附註**需要使用 HMA 設定適用於企業的 Skype 吗？您將需要兩篇文章： 一個列出[支援的拓撲](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)，另一個教您[如何進行的設定](configure-skype-for-business-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="205fa-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="205fa-162">相關主題</span><span class="sxs-lookup"><span data-stu-id="205fa-162">Related topics</span></span>

[<span data-ttu-id="205fa-163">經過驗證的混合式概觀及使用內部部署 Skype 中的商務與 Exchange 伺服器的先決條件</span><span class="sxs-lookup"><span data-stu-id="205fa-163">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

