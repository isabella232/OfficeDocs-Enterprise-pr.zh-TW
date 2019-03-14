---
title: 如何新式驗證運作的 Office 2013 和 Office 2016 用戶端應用程式
ms.author: tracyp
author: MSFTTracyP
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
ms.collection:
- M365-security-compliance
description: 了解 Office 365 新式驗證運作方式的 Office 2013 和 2016年用戶端應用程式。
ms.openlocfilehash: 0e7b1a91a13fdd1ea5bb5fd3b42fcda60c704d6f
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372910"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>如何新式驗證運作的 Office 2013 和 Office 2016 用戶端應用程式

請閱讀本篇文章以了解如何在 Office 2013 和 Office 2016 用戶端應用程式使用新式驗證功能為基礎的驗證設定 Office 365 租用戶上的 Exchange Online、 SharePoint Online，與 Skype for Business Online。
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>新式驗證 Office 365 服務的可用性

Office 365 服務，則新式驗證的預設狀態：
  
- **Exchange Online 的預設開啟。** 請參閱[啟用或停用新式驗證在 Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662)將它關閉或開啟。 
    
- **SharePoint Online 的預設開啟。** 
    
- **Skype 商務 Online 的預設開啟。** 請參閱 <<c0>啟用 Skype 商務 Online 進行新式驗證來關閉或開啟。
    
## <a name="sign-in-behavior-of-office-client-apps"></a>登入的 Office 用戶端應用程式的行為

Office 2013 用戶端應用程式預設支援舊版的驗證。 舊版表示它們支援可以是 Microsoft Online 登入小幫手] 或 [基本驗證。 為了讓這些用戶端使用新式驗證功能，用戶端具有 Windows 會有設定的登錄機碼。 如需相關指示，請參閱 < <b0>Windows 裝置上的 Office 2013 啟用新式驗證</b0>。
  
閱讀[如何使用新式驗證 (ADAL) 與商務用 Skype](https://go.microsoft.com/fwlink/p/?LinkId=785431)若要了解使用商務用 Skype 的運作方式。 
  
Office 2016 用戶端支援新式驗證，根據預設，並採取任何動作所需的用戶端使用這些新的流量。 不過，使用傳統驗證需要明確的巨集指令。
  
按一下下列連結，請參閱 < Office 2013 和 Office 2016 用戶端驗證與根據已開啟新式驗證的 Office 365 服務的運作方式。
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [商務用 Skype Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

下表說明 Office 2013 或 Office 2016 用戶端應用程式的驗證行為時包含或不含新式驗證連線至 Exchange Online。
  
|Office 用戶端應用程式版本 * * *|登錄機碼存在？ * * *|上的新式驗證？ * * *|新式驗證的驗證行為開啟租用戶 （預設值） * * *|新式驗證的驗證行為關閉租用戶 * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用基本驗證。 未啟用租用戶時，伺服器就會拒絕新式驗證。  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用基本驗證。 未啟用租用戶時，伺服器就會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用基本驗證。 未啟用租用戶時，伺服器就會拒絕新式驗證。  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用基本驗證。 未啟用租用戶時，伺服器就會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |基本驗證  <br/> |基本驗證  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |基本驗證  <br/> |基本驗證  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用基本驗證。 未啟用租用戶時，伺服器就會拒絕新式驗證。  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用基本驗證。 未啟用租用戶時，伺服器就會拒絕新式驗證。  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

下表說明 Office 2013 或 Office 2016 用戶端應用程式的驗證行為時包含或不含新式驗證連線至 SharePoint Online。
  
|Office 用戶端應用程式版本 * * *|登錄機碼存在？ * * *|上的新式驗證？ * * *|新式驗證的驗證行為開啟租用戶 （預設值） * * *|新式驗證的驗證行為關閉租用戶 * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |僅限新式驗證。  <br/> |連線失敗。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |僅限新式驗證。  <br/> |連線失敗。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |Microsoft 線上登入小幫手僅。  <br/> |Microsoft 線上登入小幫手僅。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |Microsoft 線上登入小幫手僅。  <br/> |Microsoft 線上登入小幫手僅。  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |僅限新式驗證。  <br/> |連線失敗。  <br/> |
   
### <a name="skype-for-business-online"></a>商務用 Skype Online
<a name="BK_SFBO"> </a>

下表說明適用於 Office 2013 或 Office 2016 用戶端應用程式的驗證行為，連線至 Skype for Business Online 包含或不含新式驗證。
  
|Office 用戶端應用程式版本 * * *|登錄機碼存在？ * * *|上的新式驗證？ * * *|新式驗證的驗證行為開啟租用戶 * * *|新式驗證的驗證行為關閉租用戶 （預設值） * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |否，或 EnableADAL = 1  <br/> |是  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用 Microsoft Online 登入小幫手。 未啟用 Skype for Business Online 租用戶時，伺服器就會拒絕新式驗證。  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用 Microsoft Online 登入小幫手。 未啟用 Skype for Business Online 租用戶時，伺服器就會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用 Microsoft Online 登入小幫手。 未啟用 Skype for Business Online 租用戶時，伺服器就會拒絕新式驗證。  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用 Microsoft Online 登入小幫手。 未啟用 Skype for Business Online 租用戶時，伺服器就會拒絕新式驗證。  <br/> |
|Office 2016  <br/> |是，EnableADAL = 0  <br/> |否  <br/> |Microsoft 線上登入小幫手僅。  <br/> |Microsoft 線上登入小幫手僅。  <br/> |
|Office 2013  <br/> |否  <br/> |否  <br/> |Microsoft 線上登入小幫手僅。  <br/> |Microsoft 線上登入小幫手僅。  <br/> |
|Office 2013  <br/> |是，EnableADAL = 1  <br/> |是  <br/> |會先嘗試新式驗證。 如果伺服器拒絕的新式驗證連線，則會使用 Microsoft Online 登入小幫手。 未啟用 Skype for Business Online 租用戶時，伺服器就會拒絕新式驗證。  <br/> |Microsoft 線上登入小幫手僅。  <br/> |
   
## <a name="see-also"></a>另請參閱

[Windows 裝置上啟用 Office 2013 的新式驗證](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[ Plan for Office 365 部署的多重要素驗證 （適用於 Office 365 系統管理員）](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[使用 （適用於使用者） 的 2 雙步驟驗證登入 Office 365](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)