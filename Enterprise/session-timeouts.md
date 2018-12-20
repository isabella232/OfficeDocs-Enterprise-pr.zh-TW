---
title: Office 365 的工作階段逾時
ms.author: tracyp
author: MSFTTracyP
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
ms.openlocfilehash: 4ef50b876fd97e2de2449d324464b466243a6691
ms.sourcegitcommit: fd7a56f38ba2c2d2e7fcd6e165ec58b31be299d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "27378489"
---
# <a name="session-timeouts-for-office-365"></a>Office 365 的工作階段逾時

工作階段存留時間是重要的 Office 365 的驗證和中平衡安全性和次數會提示使用者認證的重要元件。
  
## <a name="session-times-for-office-365-services"></a>Office 365 服務的工作階段時間

當使用者在任何 Office 365 web 應用程式或行動應用程式進行驗證時，建立工作階段。工作階段期間，使用者不需要重新驗證。當使用者非使用中或其驗證權杖到期的其他原因有許多例如時已重設其密碼時也關閉瀏覽器或] 索引標籤可以過期工作階段。Office 365 服務必須與對應的每個服務的一般使用不同的工作階段逾時。
  
下表列出 Office 365 服務的工作階段存留時間：
  
|**Office 365 服務**|**工作階段逾時**|
|:-----|:-----|
|Office 365 系統管理中心  <br/> |系統會要求您提供認證管理中心的每個 8 小時。  <br/> |
|SharePoint Online  <br/> |5 天的閒置時間只要使用者選擇 [**保持我登入**。如果使用者存取 SharePoint Online 再次 24 個小時以上已經過從舊的登入之後，逾時值會重設為 5 天。<br/> |
|Outlook Web App  <br/> |6 小時。  <br/> 您可以使用_ActivityBasedAuthenticationTimeoutInterval_參數[Set-organizationconfig](https://go.microsoft.com/fwlink/p/?LinkId=615378)指令程式中變更此值。  <br/> |
|Azure Active Directory  <br/> （搭配 Office 2013 Windows 用戶端啟用的現代驗證）  <br/> | 經過驗證會使用 Office 365 資源使用 Azure Active Directory 的使用者存取權授與存取權杖和重新整理權杖。存取權杖 JSON Web Token 驗證成功後所提供且 1 小時時才有效。具有較長的存留期的重新整理語彙基元也提供。當存取權杖到期時，Office 用戶端會使用有效的重新整理權杖以取得新的存取權杖。此 exchange 成功如果使用者的初始驗證仍然有效。  <br/>  重新整理權杖有效期為 90 天，並且使用連續使用他們可以有效直到撤銷。  <br/>  重新整理權杖可以要變成無效數個事件所例如：  <br/>  使用者的密碼已變更之後發行的重新整理 token。  <br/>  系統管理員可以套用設定格式化的條件存取原則以限制存取權的使用者嘗試存取的資源。  <br/> |
|Android （英文）、 iOS，以及 Windows 10 的 SharePoint 和 OneDrive 行動應用程式  <br/> |存取權杖的預設存留期更改為 1 小時。預設最大的重新整理 token 不在作用中時間為 90 天。<br/> [深入了解權杖以及如何設定權杖存留期](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> 若要撤銷重新整理 token，您可以重設使用者的 Office 365 密碼  <br/> |
|Yammer 與 Office 365 登入  <br/> |存留期瀏覽器。如果使用者關閉瀏覽器及在新的瀏覽器中存取 Yammer] Yammer 會重新驗證它們與 Office 365。如果使用者是使用第三方瀏覽器的快取 cookie，他們可能不需要重新時進行驗證時重新開啟瀏覽器。<br/> > [!NOTE]> 這是僅適用於使用 Office 365 登入 Yammer 網路。           |
   

