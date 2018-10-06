---
title: 新式驗證對於 Office 2013 和 Office 2016 用戶端應用程式的運作方式
ms.author: sirkkuw
author: Sirkkuw
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
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
description: 了解 Office 365 經過驗證的運作方式不同的 Office 2013 和 2016年用戶端應用程式。
ms.openlocfilehash: 78df8c12ab008922592516cf1d3cda10c594e552
ms.sourcegitcommit: 7a12a46019970fcd45a6461f4f4cbcd1f76c9b4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "25436081"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>新式驗證對於 Office 2013 和 Office 2016 用戶端應用程式的運作方式

請閱讀本文以了解如何在 Office 2013 與 Office 2016 用戶端應用程式使用經過驗證功能為基礎的驗證設定在 Office 365 租用戶上的 Exchange Online、 SharePoint Online 和 Skype 商務線上。
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>經過驗證的 Office 365 服務的可用性

Office 365 服務、 經過驗證的預設狀態是：
  
- **Exchange Online 的預設開啟。** 請參閱[啟用或停用現代驗證在 Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)關閉或開啟。 
    
- **SharePoint Online 的預設開啟。** 
    
- **For Skype Business Online 的預設開啟。** 請參閱[啟用 Skype 商務 Online 經過驗證的](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)以關閉或開啟。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>登入的 Office 用戶端應用程式的行為

Office 2013 用戶端應用程式預設支援舊版 authentication。舊版表示他們支援可以是 Microsoft Online 登入小幫手] 或 [基本驗證。為了讓這些用戶端使用經過驗證功能，用戶端具有 Windows 已設定的登錄機碼。指示，請參閱[Windows 裝置上的 Office 2013 啟用經過驗證](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910)。
  
閱讀[如何使用經過驗證 (ADAL) 與 Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=785431) ，深入了解與 Skype for Business 的運作方式。 
  
Office 2016 用戶端支援現代驗證根據預設，而且採取任何動作所需的用戶端使用這些新的流量。不過，明確巨集指令會需要以使用舊版的驗證。
  
按一下下列連結，從而查看 Office 2013 與 Office 2016 用戶端驗證與 Office 365 服務根據已開啟經過驗證的運作方式。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- 
  [商務用 Skype Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

下表說明 Office 2013 或 Office 2016 用戶端應用程式的驗證行為時使用或不經過驗證連線至 Exchange Online。
  
|Office 用戶端應用程式版本 * * *|登錄機碼存在？ * * *|在經過驗證？ * * *|使用經過驗證的驗證行為開啟租戶 （預設值） * * *|使用經過驗證的驗證行為已關閉的租用戶 * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，會使用基本驗證。伺服器拒絕現代驗證時未啟用租用戶。  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，會使用基本驗證。伺服器拒絕現代驗證時未啟用租用戶。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，會使用基本驗證。伺服器拒絕現代驗證時未啟用租用戶。  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，會使用基本驗證。伺服器拒絕現代驗證時未啟用租用戶。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |基本驗證  <br/> |基本驗證  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |基本驗證  <br/> |基本驗證  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，會使用基本驗證。伺服器拒絕現代驗證時未啟用租用戶。  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，會使用基本驗證。伺服器拒絕現代驗證時未啟用租用戶。  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

下表說明 Office 2013 或 Office 2016 用戶端應用程式的驗證行為時使用或不經過驗證連接至 SharePoint Online。
  
|Office 用戶端應用程式版本 * * *|登錄機碼存在？ * * *|在經過驗證？ * * *|使用經過驗證的驗證行為開啟租戶 （預設值） * * *|使用經過驗證的驗證行為已關閉的租用戶 * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |僅限經過驗證。  <br/> |無法連線。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |僅限經過驗證。  <br/> |無法連線。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |Microsoft Online 登入小幫手僅。  <br/> |Microsoft Online 登入小幫手僅。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |Microsoft Online 登入小幫手僅。  <br/> |Microsoft Online 登入小幫手僅。  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |僅限經過驗證。  <br/> |無法連線。  <br/> |
   
### <a name="skype-for-business-online"></a>商務用 Skype Online
<a name="BK_SFBO"> </a>

下表說明 Office 2013 或 Office 2016 用戶端應用程式的驗證行為時可連至 Skype 商務 online 使用或不經過驗證。
  
|Office 用戶端應用程式版本 * * *|登錄機碼存在？ * * *|在經過驗證？ * * *|使用經過驗證的驗證行為開啟租用戶 * * *|使用經過驗證的驗證行為關閉租戶 （預設值） * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，就會使用 Microsoft Online 登入小幫手。伺服器拒絕現代驗證時未啟用 Skype 之商務 Online 租用戶。  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，就會使用 Microsoft Online 登入小幫手。伺服器拒絕現代驗證時未啟用 Skype 之商務 Online 租用戶。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，就會使用 Microsoft Online 登入小幫手。伺服器拒絕現代驗證時未啟用 Skype 之商務 Online 租用戶。  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，就會使用 Microsoft Online 登入小幫手。伺服器拒絕現代驗證時未啟用 Skype 之商務 Online 租用戶。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |Microsoft Online 登入小幫手僅。  <br/> |Microsoft Online 登入小幫手僅。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |Microsoft Online 登入小幫手僅。  <br/> |Microsoft Online 登入小幫手僅。  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試經過驗證。如果伺服器拒絕摩登的驗證連線，就會使用 Microsoft Online 登入小幫手。伺服器拒絕現代驗證時未啟用 Skype 之商務 Online 租用戶。  <br/> |Microsoft Online 登入小幫手僅。  <br/> |
   
## <a name="see-also"></a>另請參閱

[啟用 Windows 裝置上的 Office 2013 的現代驗證](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[規劃 Office 365 部署的多重要素驗證 （適用於 Office 365 系統管理員）](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[以 （適用於使用者） 的步驟 2 驗證登入 Office 365](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)