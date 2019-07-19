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
description: 工作階段逾時可用來平衡安全性和 [輕鬆存取 Office 365 用戶端應用程式中。
ms.openlocfilehash: 6c37f53086a840a05e879682c95d6a4f25463707
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782013"
---
# <a name="session-timeouts-for-office-365"></a>Office 365 的工作階段逾時

工作階段存留時間是很重要的部分的 Office 365 驗證，而且是以平衡安全性和次數系統會提示使用者輸入其認證的重要元件。
  
## <a name="session-times-for-office-365-services"></a>Office 365 服務的工作階段時間

當使用者在任何 Office 365 web 應用程式或行動應用程式進行驗證時，建立工作階段。 工作階段期間，使用者不需要重新驗證。 當使用者不在作用中，當使用者關閉瀏覽器或] 索引標籤，或其驗證權杖到期時已重設其密碼其他原因時，可以過期工作階段。 Office 365 服務有對應的每個服務一般使用不同的工作階段逾時。
  
下表列出 Office 365 服務的工作階段存留時間：
  
|**Office 365 服務**|**工作階段逾時**|
|:-----|:-----|
|Microsoft 365 系統管理中心  <br/> |會要求您提供的認證，在系統管理中心來每隔 8 小時。  <br/> |
|SharePoint Online  <br/> |5 天的閒置時間長達使用者選擇 [**保持我登入**。 如果使用者存取 SharePoint Online 一次之後從舊的登入已傳遞 24 個小時以上，逾時值是重設為 5 天。  <br/> |
|Outlook Web App  <br/> |6 小時。  <br/> 您可以使用_ActivityBasedAuthenticationTimeoutInterval_參數， [Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378)指令程式中變更此值。  <br/> |
|Azure Active Directory  <br/> （搭配 Office 2013 Windows 用戶端啟用新式驗證）  <br/> | 新式驗證會使用存取權杖並重新整理權杖來授與使用者存取使用 Azure Active Directory 的 Office 365 資源。 存取權杖是 JSON Web 權杖驗證成功後所提供且有效 （1 小時）。 也提供較長的生命週期與重新整理權杖。 當存取權杖到期時，Office 用戶端會使用有效的重新整理權杖來取得新的存取權杖。 此 exchange 會成功，如果使用者的初始驗證仍然有效。  <br/>  重新整理權杖有效 90 天，且隨著連續使用，它們可以有效直到撤銷。  <br/>  重新整理權杖可以失效由數個事件如下：  <br/>  重新整理權杖已發出後，已變更使用者的密碼。  <br/>  系統管理員可以套用至使用者嘗試存取的資源限制存取條件式存取原則。  <br/> |
|針對 Android、 iOS 和 Windows 10 的 SharePoint 和 OneDrive 行動應用程式  <br/> |預設存取權杖的存留期為 1 小時。 預設最大非使用中的時間重新整理權杖是 90 天。  <br/> [深入了解權杖，以及如何設定權杖存留期](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 若要撤銷重新整理權杖，您可以重設使用者的 Office 365 密碼  <br/> |
|Yammer 與 Office 365 登入  <br/> |在瀏覽器的存留期。 如果使用者關閉瀏覽器，並在新的瀏覽器中存取 Yammer，則 Yammer 重新將驗證它們與 Office 365。 如果使用者使用協力廠商瀏覽器該快取 cookie，他們可能不需要重新驗證當他們重新開啟瀏覽器。  <br/> > [!NOTE]> 這是僅適用於使用 Office 365 登入 Yammer 網路。           |
   

