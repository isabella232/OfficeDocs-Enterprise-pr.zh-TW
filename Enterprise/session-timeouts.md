---
title: Office 365 的工作階段逾時
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
description: 工作階段逾時可用來平衡 securtiy 與 Office 365 用戶端應用程式中存取的簡易性。
ms.openlocfilehash: dda13f280149c969354ae1f0eac336f1d8ed23e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540053"
---
# <a name="session-timeouts-for-office-365"></a><span data-ttu-id="6cae8-103">Office 365 的工作階段逾時</span><span class="sxs-lookup"><span data-stu-id="6cae8-103">Session timeouts for Office 365</span></span>

<span data-ttu-id="6cae8-104">工作階段存留時間是重要的 Office 365 的驗證和中平衡安全性和次數會提示使用者認證的重要元件。</span><span class="sxs-lookup"><span data-stu-id="6cae8-104">Session lifetimes are an important part of authentication for Office 365 and are an important component in balancing security and the number of times users are prompted for their credentials.</span></span>
  
## <a name="session-times-for-office-365-services"></a><span data-ttu-id="6cae8-105">Office 365 服務的工作階段時間</span><span class="sxs-lookup"><span data-stu-id="6cae8-105">Session times for Office 365 services</span></span>

<span data-ttu-id="6cae8-p101">當使用者在任何 Office 365 web 應用程式或行動應用程式進行驗證時，建立工作階段。工作階段期間，使用者不需要重新驗證。當使用者非使用中或其驗證權杖到期的其他原因有許多例如時已重設其密碼時也關閉瀏覽器或] 索引標籤可以過期工作階段。Office 365 服務必須與對應的每個服務的一般使用不同的工作階段逾時。</span><span class="sxs-lookup"><span data-stu-id="6cae8-p101">When users authenticate in any of the Office 365 web apps or mobile apps, a session is established. For the duration of the session, users won't need to re-authenticate. Sessions can expire when users are inactive, when they close the browser or tab, or when their authentication token expires for other reasons such as when their password has been reset. The Office 365 services have different session timeouts to correspond with the typical use of each service.</span></span>
  
<span data-ttu-id="6cae8-110">下表列出 Office 365 服務的工作階段存留時間：</span><span class="sxs-lookup"><span data-stu-id="6cae8-110">The following table lists the session lifetimes for Office 365 services:</span></span>
  
|<span data-ttu-id="6cae8-111">**Office 365 服務**</span><span class="sxs-lookup"><span data-stu-id="6cae8-111">**Office 365 service**</span></span>|<span data-ttu-id="6cae8-112">**工作階段逾時**</span><span class="sxs-lookup"><span data-stu-id="6cae8-112">**Session timeout**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6cae8-113">Office 365 系統管理中心</span><span class="sxs-lookup"><span data-stu-id="6cae8-113">Office 365 Admin center</span></span>  <br/> |<span data-ttu-id="6cae8-114">系統會要求您提供認證管理中心的每個 8 小時。</span><span class="sxs-lookup"><span data-stu-id="6cae8-114">You are asked to provide credentials for the admin center every 8 hours.</span></span>  <br/> |
|<span data-ttu-id="6cae8-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6cae8-115">SharePoint Online</span></span>  <br/> |<span data-ttu-id="6cae8-p102">5 天的閒置時間只要使用者選擇 [**保持我登入**。如果使用者存取 SharePoint Online 再次 24 個小時以上已經過從舊的登入之後，逾時值會重設為 5 天。</span><span class="sxs-lookup"><span data-stu-id="6cae8-p102">5 days of inactivity as long as the users chooses **Keep me signed in**. If the user accesses SharePoint Online again after 24 or more hours have passed from the previous sign-in, the timeout value is reset to 5 days.  </span></span><br/> |
|<span data-ttu-id="6cae8-118">Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="6cae8-118">Outlook Web App</span></span>  <br/> |<span data-ttu-id="6cae8-119">6 小時。</span><span class="sxs-lookup"><span data-stu-id="6cae8-119">6 hours.</span></span>  <br/> <span data-ttu-id="6cae8-120">您可以使用_ActivityBasedAuthenticationTimeoutInterval_參數[Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378)指令程式中變更此值。</span><span class="sxs-lookup"><span data-stu-id="6cae8-120">You can change this value by using the  _ActivityBasedAuthenticationTimeoutInterval_ parameter in the [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet.</span></span>  <br/> |
|<span data-ttu-id="6cae8-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6cae8-121">Azure Active Directory</span></span>  <br/> <span data-ttu-id="6cae8-122">（搭配 Office 2013 Windows 用戶端啟用的現代驗證）</span><span class="sxs-lookup"><span data-stu-id="6cae8-122">(Used by Office 2013 Windows clients with modern authentication enabled)</span></span>  <br/> | <span data-ttu-id="6cae8-p103">經過驗證會使用 Office 365 資源使用 Azure Active Directory 的使用者存取權授與存取權杖和重新整理權杖。存取權杖 JSON Web Token 驗證成功後所提供且 1 小時時才有效。具有較長的存留期的重新整理語彙基元也提供。當存取權杖到期時，Office 用戶端會使用有效的重新整理權杖以取得新的存取權杖。此 exchange 成功如果使用者的初始驗證仍然有效。</span><span class="sxs-lookup"><span data-stu-id="6cae8-p103">Modern authentication uses access tokens and refresh tokens to grant user access to Office 365 resources using Azure Active Directory. An access token is a JSON Web Token provided after a successful authentication and is valid for 1 hour. A refresh token with a longer lifetime is also provided. When access tokens expire, Office clients use a valid refresh token to obtain a new access token. This exchange succeeds if the user's initial authentication is still valid.</span></span>  <br/>  <span data-ttu-id="6cae8-128">重新整理權杖有效期為 90 天，並且使用連續使用他們可以有效直到撤銷。</span><span class="sxs-lookup"><span data-stu-id="6cae8-128">Refresh tokens are valid for 90 days, and with continuous use, they can be valid until revoked.</span></span>  <br/>  <span data-ttu-id="6cae8-129">重新整理權杖可以要變成無效數個事件所例如：</span><span class="sxs-lookup"><span data-stu-id="6cae8-129">Refresh tokens can be invalidated by several events such as :</span></span>  <br/>  <span data-ttu-id="6cae8-130">使用者的密碼已變更之後發行的重新整理 token。</span><span class="sxs-lookup"><span data-stu-id="6cae8-130">User's password has changed since the refresh token was issued.</span></span>  <br/>  <span data-ttu-id="6cae8-131">系統管理員可以套用設定格式化的條件存取原則以限制存取權的使用者嘗試存取的資源。</span><span class="sxs-lookup"><span data-stu-id="6cae8-131">An administrator can apply conditional access policies which restrict access to the resource the user is trying to access.</span></span>  <br/> |
|<span data-ttu-id="6cae8-132">Android （英文）、 iOS，以及 Windows 10 的 SharePoint 和 OneDrive 行動應用程式</span><span class="sxs-lookup"><span data-stu-id="6cae8-132">SharePoint and OneDrive mobile apps for Android, iOS, and Windows 10</span></span>  <br/> |<span data-ttu-id="6cae8-p104">存取權杖的預設存留期更改為 1 小時。預設最大的重新整理 token 不在作用中時間為 90 天。</span><span class="sxs-lookup"><span data-stu-id="6cae8-p104">The default lifetime for the access token is 1 hour. The default max inactive time of the refresh token is 90 days.  </span></span><br/> [<span data-ttu-id="6cae8-135">深入了解權杖以及如何設定權杖存留期</span><span class="sxs-lookup"><span data-stu-id="6cae8-135">Learn more about tokens and how to configure token lifetimes</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> <span data-ttu-id="6cae8-136">若要撤銷重新整理 token，您可以重設使用者的 Office 365 密碼</span><span class="sxs-lookup"><span data-stu-id="6cae8-136">To revoke the refresh token, you can reset the user's Office 365 password</span></span>  <br/> |
|<span data-ttu-id="6cae8-137">Yammer 與 Office 365 登入</span><span class="sxs-lookup"><span data-stu-id="6cae8-137">Yammer with Office 365 Sign-In</span></span>  <br/> |<span data-ttu-id="6cae8-p105">存留期瀏覽器。如果使用者關閉瀏覽器及在新的瀏覽器中存取 Yammer] Yammer 會重新驗證它們與 Office 365。如果使用者是使用第三方瀏覽器的快取 cookie，他們可能不需要重新時進行驗證時重新開啟瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6cae8-p105">Lifetime of the browser. If users close the browser and access Yammer in a new browser, Yammer will re-authenticate them with Office 365. If users use third-party browsers that cache cookies, they may not need to re-authenticate when they reopen the browser.  </span></span><br/> <span data-ttu-id="6cae8-141">> [!NOTE]> 這是僅適用於使用 Office 365 登入 Yammer 網路。</span><span class="sxs-lookup"><span data-stu-id="6cae8-141">> [!NOTE]> This is valid only for networks using Office 365 Sign-In for Yammer.</span></span>           |
   

