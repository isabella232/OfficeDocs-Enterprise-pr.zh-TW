---
title: Office 2013 和 Office 2016 用戶端應用程式的新式驗證運作方式
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: 瞭解 Office 365 新式驗證在 Office 2013 和2016用戶端應用程式中的運作方式不同。
ms.openlocfilehash: 25646c014fc9ff11926c0091209a3419fad811d6
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203622"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Office 2013 和 Office 2016 用戶端應用程式的新式驗證運作方式

請閱讀本文以瞭解 Office 2013 和 Office 2016 用戶端應用程式如何根據 Office 365 租使用者在 Exchange Online、SharePoint Online 和商務用 Skype Online 上的驗證設定, 使用新式驗證功能。

> [!NOTE]
> 舊版用戶端應用程式 (例如 Office 2010 和 Office for Mac 2011) 不支援新式驗證, 而且只能搭配基本驗證使用。

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Office 365 服務的新式驗證可用性

對於 Office 365 服務, 新式驗證的預設狀態為:
  
- 依**** 預設開啟 [Exchange Online]。 請參閱[啟用或停用 Exchange Online 中的新式驗證](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662), 以將其關閉或開啟。 
    
- 預設**** 會開啟 SharePoint Online。 
    
- 依**** 預設開啟商務用 Skype Online。 請參閱[Enable 商務用 Skype Online for 新式驗證](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx), 將其關閉或開啟。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Office 用戶端應用程式的登入行為

根據預設, Office 2013 用戶端應用程式支援舊版驗證。 舊版是指它們支援 Microsoft Online 登入小幫手或基本驗證。 為了讓這些用戶端使用新式驗證功能, Windows 用戶端已設定登錄機碼。 如需相關指示, 請參閱[在 Windows 裝置上啟用 Office 2013 的新式驗證](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)。
  
閱讀[如何使用新式驗證 (ADAL) 與商務用 skype](https://go.microsoft.com/fwlink/p/?LinkId=785431)來瞭解其如何與商務用 skype 搭配運作。 
  
Office 2016 用戶端預設支援新式驗證, 且用戶端不需要採取任何動作, 即可使用這些新流程。 不過, 若要使用舊版驗證, 則需要明確的動作。
  
按一下下列連結, 以查看 Office 2013 和 Office 2016 用戶端驗證如何與 Office 365 服務搭配使用, 這取決於是否已開啟新式驗證。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [商務用 Skype Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

下表說明 Office 2013 或 Office 2016 用戶端應用程式在連線至 Exchange Online (含或不含新式驗證) 時的驗證行為。
  
|Office 用戶端應用程式版本 * * * *|登錄機碼存在？ * * * *|上的新式驗證？ * * * *|已針對租使用者開啟的新式驗證的驗證行為 (預設值) * * * *|針對承租人的新式驗證關閉驗證行為 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否, 或 EnableADAL = 1  <br/> |是  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用基本驗證。 當租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用基本驗證。 當租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用基本驗證。 當租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用基本驗證。 當租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 0  <br/> |否  <br/> |基本驗證  <br/> |基本驗證  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |基本驗證  <br/> |基本驗證  <br/> |
|Office 2013  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用基本驗證。 當租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用基本驗證。 當租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

下表說明 Office 2013 或 Office 2016 用戶端應用程式在連線至 SharePoint Online (含或不含新式驗證) 時的驗證行為。
  
|Office 用戶端應用程式版本 * * * *|登錄機碼存在？ * * * *|上的新式驗證？ * * * *|已針對租使用者開啟的新式驗證的驗證行為 (預設值) * * * *|針對承租人的新式驗證關閉驗證行為 * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否, 或 EnableADAL = 1  <br/> |是  <br/> |僅限新式驗證。  <br/> |連線失敗。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |僅限新式驗證。  <br/> |連線失敗。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 0  <br/> |否  <br/> |僅限 Microsoft Online 登入助理。  <br/> |僅限 Microsoft Online 登入助理。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |僅限 Microsoft Online 登入助理。  <br/> |僅限 Microsoft Online 登入助理。  <br/> |
|Office 2013  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |僅限新式驗證。  <br/> |連線失敗。  <br/> |
   
### <a name="skype-for-business-online"></a>商務用 Skype Online
<a name="BK_SFBO"> </a>

下表說明 Office 2013 或 Office 2016 用戶端應用程式在連線至具有或不含新式驗證的商務用 Skype Online 時的驗證行為。
  
|Office 用戶端應用程式版本 * * * *|登錄機碼存在？ * * * *|上的新式驗證？ * * * *|針對租使用者開啟的新式驗證的驗證行為 * * * *|租使用者的新式驗證的驗證行為 (預設值) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否, 或 EnableADAL = 1  <br/> |是  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用 Microsoft Online 登入助理。 當商務用 Skype Online 租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用 Microsoft Online 登入助理。 當商務用 Skype Online 租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用 Microsoft Online 登入助理。 當商務用 Skype Online 租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用 Microsoft Online 登入助理。 當商務用 Skype Online 租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是, EnableADAL = 0  <br/> |否  <br/> |僅限 Microsoft Online 登入助理。  <br/> |僅限 Microsoft Online 登入助理。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |僅限 Microsoft Online 登入助理。  <br/> |僅限 Microsoft Online 登入助理。  <br/> |
|Office 2013  <br/> |是, EnableADAL = 1  <br/> |是  <br/> |先嘗試新式驗證。 如果伺服器拒絕新式驗證連線, 則會使用 Microsoft Online 登入助理。 當商務用 Skype Online 租使用者未啟用時, 伺服器會拒絕新式驗證。  <br/> |僅限 Microsoft Online 登入助理。  <br/> |
   
## <a name="see-also"></a>另請參閱

[在 Windows 裝置上啟用 Office 2013 的新式驗證](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[規劃 Office 365 部署的多重要素驗證 (適用于 Office 365 系統管理員)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[使用雙步驟驗證登入 Office 365 (適用于使用者)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)
