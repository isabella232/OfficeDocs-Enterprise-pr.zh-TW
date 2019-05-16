---
title: Office 365 的工作階段逾時
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
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
ms.collection:
- M365-security-compliance
description: 工作階段逾時可用來平衡 securtiy 與 [輕鬆存取 Office 365 用戶端應用程式中。
ms.openlocfilehash: d43bc123de982f3ebf55f05f48e53debe7df036b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070849"
---
# <a name="session-timeouts-for-office-365"></a><span data-ttu-id="c03d4-103">Office 365 的工作階段逾時</span><span class="sxs-lookup"><span data-stu-id="c03d4-103">Session timeouts for Office 365</span></span>

<span data-ttu-id="c03d4-104">工作階段存留時間是很重要的部分的 Office 365 驗證，而且是以平衡安全性和次數系統會提示使用者輸入其認證的重要元件。</span><span class="sxs-lookup"><span data-stu-id="c03d4-104">Session lifetimes are an important part of authentication for Office 365 and are an important component in balancing security and the number of times users are prompted for their credentials.</span></span>
  
## <a name="session-times-for-office-365-services"></a><span data-ttu-id="c03d4-105">Office 365 服務的工作階段時間</span><span class="sxs-lookup"><span data-stu-id="c03d4-105">Session times for Office 365 services</span></span>

<span data-ttu-id="c03d4-106">當使用者在任何 Office 365 web 應用程式或行動應用程式進行驗證時，建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="c03d4-106">When users authenticate in any of the Office 365 web apps or mobile apps, a session is established.</span></span> <span data-ttu-id="c03d4-107">工作階段期間，使用者不需要重新驗證。</span><span class="sxs-lookup"><span data-stu-id="c03d4-107">For the duration of the session, users won't need to re-authenticate.</span></span> <span data-ttu-id="c03d4-108">當使用者不在作用中，當使用者關閉瀏覽器或] 索引標籤，或其驗證權杖到期時已重設其密碼其他原因時，可以過期工作階段。</span><span class="sxs-lookup"><span data-stu-id="c03d4-108">Sessions can expire when users are inactive, when they close the browser or tab, or when their authentication token expires for other reasons such as when their password has been reset.</span></span> <span data-ttu-id="c03d4-109">Office 365 服務有對應的每個服務一般使用不同的工作階段逾時。</span><span class="sxs-lookup"><span data-stu-id="c03d4-109">The Office 365 services have different session timeouts to correspond with the typical use of each service.</span></span>
  
<span data-ttu-id="c03d4-110">下表列出 Office 365 服務的工作階段存留時間：</span><span class="sxs-lookup"><span data-stu-id="c03d4-110">The following table lists the session lifetimes for Office 365 services:</span></span>
  
|<span data-ttu-id="c03d4-111">**Office 365 服務**</span><span class="sxs-lookup"><span data-stu-id="c03d4-111">**Office 365 service**</span></span>|<span data-ttu-id="c03d4-112">**工作階段逾時**</span><span class="sxs-lookup"><span data-stu-id="c03d4-112">**Session timeout**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c03d4-113">Office 365 系統管理中心</span><span class="sxs-lookup"><span data-stu-id="c03d4-113">Office 365 Admin center</span></span>  <br/> |<span data-ttu-id="c03d4-114">會要求您提供的認證，在系統管理中心來每隔 8 小時。</span><span class="sxs-lookup"><span data-stu-id="c03d4-114">You are asked to provide credentials for the admin center every 8 hours.</span></span>  <br/> |
|<span data-ttu-id="c03d4-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c03d4-115">SharePoint Online</span></span>  <br/> |<span data-ttu-id="c03d4-116">5 天的閒置時間長達使用者選擇 [**保持我登入**。</span><span class="sxs-lookup"><span data-stu-id="c03d4-116">5 days of inactivity as long as the users chooses **Keep me signed in**.</span></span> <span data-ttu-id="c03d4-117">如果使用者存取 SharePoint Online 一次之後從舊的登入已傳遞 24 個小時以上，逾時值是重設為 5 天。</span><span class="sxs-lookup"><span data-stu-id="c03d4-117">If the user accesses SharePoint Online again after 24 or more hours have passed from the previous sign-in, the timeout value is reset to 5 days.</span></span>  <br/> |
|<span data-ttu-id="c03d4-118">Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="c03d4-118">Outlook Web App</span></span>  <br/> |<span data-ttu-id="c03d4-119">6 小時。</span><span class="sxs-lookup"><span data-stu-id="c03d4-119">6 hours.</span></span>  <br/> <span data-ttu-id="c03d4-120">您可以使用_ActivityBasedAuthenticationTimeoutInterval_參數， [Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378)指令程式中變更此值。</span><span class="sxs-lookup"><span data-stu-id="c03d4-120">You can change this value by using the  _ActivityBasedAuthenticationTimeoutInterval_ parameter in the [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) cmdlet.</span></span>  <br/> |
|<span data-ttu-id="c03d4-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c03d4-121">Azure Active Directory</span></span>  <br/> <span data-ttu-id="c03d4-122">（搭配 Office 2013 Windows 用戶端啟用新式驗證）</span><span class="sxs-lookup"><span data-stu-id="c03d4-122">(Used by Office 2013 Windows clients with modern authentication enabled)</span></span>  <br/> | <span data-ttu-id="c03d4-123">新式驗證會使用存取權杖並重新整理權杖來授與使用者存取使用 Azure Active Directory 的 Office 365 資源。</span><span class="sxs-lookup"><span data-stu-id="c03d4-123">Modern authentication uses access tokens and refresh tokens to grant user access to Office 365 resources using Azure Active Directory.</span></span> <span data-ttu-id="c03d4-124">存取權杖是 JSON Web 權杖驗證成功後所提供且有效 （1 小時）。</span><span class="sxs-lookup"><span data-stu-id="c03d4-124">An access token is a JSON Web Token provided after a successful authentication and is valid for 1 hour.</span></span> <span data-ttu-id="c03d4-125">也提供較長的生命週期與重新整理權杖。</span><span class="sxs-lookup"><span data-stu-id="c03d4-125">A refresh token with a longer lifetime is also provided.</span></span> <span data-ttu-id="c03d4-126">當存取權杖到期時，Office 用戶端會使用有效的重新整理權杖來取得新的存取權杖。</span><span class="sxs-lookup"><span data-stu-id="c03d4-126">When access tokens expire, Office clients use a valid refresh token to obtain a new access token.</span></span> <span data-ttu-id="c03d4-127">此 exchange 會成功，如果使用者的初始驗證仍然有效。</span><span class="sxs-lookup"><span data-stu-id="c03d4-127">This exchange succeeds if the user's initial authentication is still valid.</span></span>  <br/>  <span data-ttu-id="c03d4-128">重新整理權杖有效 90 天，且隨著連續使用，它們可以有效直到撤銷。</span><span class="sxs-lookup"><span data-stu-id="c03d4-128">Refresh tokens are valid for 90 days, and with continuous use, they can be valid until revoked.</span></span>  <br/>  <span data-ttu-id="c03d4-129">重新整理權杖可以失效由數個事件如下：</span><span class="sxs-lookup"><span data-stu-id="c03d4-129">Refresh tokens can be invalidated by several events such as :</span></span>  <br/>  <span data-ttu-id="c03d4-130">重新整理權杖已發出後，已變更使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="c03d4-130">User's password has changed since the refresh token was issued.</span></span>  <br/>  <span data-ttu-id="c03d4-131">系統管理員可以套用至使用者嘗試存取的資源限制存取條件式存取原則。</span><span class="sxs-lookup"><span data-stu-id="c03d4-131">An administrator can apply conditional access policies which restrict access to the resource the user is trying to access.</span></span>  <br/> |
|<span data-ttu-id="c03d4-132">針對 Android、 iOS 和 Windows 10 的 SharePoint 和 OneDrive 行動應用程式</span><span class="sxs-lookup"><span data-stu-id="c03d4-132">SharePoint and OneDrive mobile apps for Android, iOS, and Windows 10</span></span>  <br/> |<span data-ttu-id="c03d4-133">預設存取權杖的存留期為 1 小時。</span><span class="sxs-lookup"><span data-stu-id="c03d4-133">The default lifetime for the access token is 1 hour.</span></span> <span data-ttu-id="c03d4-134">預設最大非使用中的時間重新整理權杖是 90 天。</span><span class="sxs-lookup"><span data-stu-id="c03d4-134">The default max inactive time of the refresh token is 90 days.</span></span>  <br/> [<span data-ttu-id="c03d4-135">深入了解權杖，以及如何設定權杖存留期</span><span class="sxs-lookup"><span data-stu-id="c03d4-135">Learn more about tokens and how to configure token lifetimes</span></span>](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> <span data-ttu-id="c03d4-136">若要撤銷重新整理權杖，您可以重設使用者的 Office 365 密碼</span><span class="sxs-lookup"><span data-stu-id="c03d4-136">To revoke the refresh token, you can reset the user's Office 365 password</span></span>  <br/> |
|<span data-ttu-id="c03d4-137">Yammer 與 Office 365 登入</span><span class="sxs-lookup"><span data-stu-id="c03d4-137">Yammer with Office 365 Sign-In</span></span>  <br/> |<span data-ttu-id="c03d4-138">在瀏覽器的存留期。</span><span class="sxs-lookup"><span data-stu-id="c03d4-138">Lifetime of the browser.</span></span> <span data-ttu-id="c03d4-139">如果使用者關閉瀏覽器，並在新的瀏覽器中存取 Yammer，則 Yammer 重新將驗證它們與 Office 365。</span><span class="sxs-lookup"><span data-stu-id="c03d4-139">If users close the browser and access Yammer in a new browser, Yammer will re-authenticate them with Office 365.</span></span> <span data-ttu-id="c03d4-140">如果使用者使用協力廠商瀏覽器該快取 cookie，他們可能不需要重新驗證當他們重新開啟瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="c03d4-140">If users use third-party browsers that cache cookies, they may not need to re-authenticate when they reopen the browser.</span></span>  <br/> <span data-ttu-id="c03d4-141">> [!NOTE]> 這是僅適用於使用 Office 365 登入 Yammer 網路。</span><span class="sxs-lookup"><span data-stu-id="c03d4-141">> [!NOTE]> This is valid only for networks using Office 365 Sign-In for Yammer.</span></span>           |
   

