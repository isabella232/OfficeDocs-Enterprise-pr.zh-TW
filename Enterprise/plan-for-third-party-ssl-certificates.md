---
title: Office 365 的協力廠商 SSL 憑證計劃
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要： 說明 Exchange 內部部署和混合部署、 使用 AD FS 的 SSO 所需 SSL 憑證的 Exchange 線上服務，以及 Exchange Web 服務。
ms.openlocfilehash: 3c22daa2315e36c45b5b5dd6271842168c90726d
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491409"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365 的協力廠商 SSL 憑證計劃

 **摘要：** 說明 Exchange 內部部署和混合部署、 使用 AD FS 的 SSO 所需 SSL 憑證的 Exchange 線上服務，以及 Exchange Web 服務。 
  
若要加密您的用戶端與 Office 365 環境之間的通訊，必須基礎結構伺服器上安裝協力廠商安全通訊端層 (SSL) 憑證。

||
|:-----|
| 本文是[網路規劃和效能調整的 Office 365](https://aka.ms/tune)的一部分。|
   
憑證所需的下列 Office 365 元件：
  
- Exchange 內部部署
    
- 單一登入 (SSO) （針對 Active Directory Federation Services (AD FS) 同盟伺服器和 AD FS 同盟伺服器 proxy）
    
- Exchange Online 服務，例如自動探索、 Outlook Anywhere 及 Exchange Web 服務
    
- Exchange 混合伺服器
    
## <a name="certificates-for-exchange-on-premises"></a>Exchange 內部部署的憑證

如需如何使用數位憑證來讓內部部署 Exchange 組織和 Exchange Online 之間的通訊安全，請參閱 TechNet 文章[了解憑證需求](https://go.microsoft.com/fwlink/p/?LinkID=243657)的概觀。
  
## <a name="certificates-for-single-sign-on"></a>單一登入的憑證

若要為使用者提供的簡化單一登入經驗，安全穩固下, 表所示的憑證所需要的同盟伺服器或同盟伺服器 proxy。 下表著重於 Active Directory Federation Services (AD FS)，我們也有使用[協力廠商身分識別提供者](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的詳細資訊。
  
||||
|:-----|:-----|:-----|
|**憑證類型** <br/> |**描述** <br/> |**您需要知道部署之前** <br/> |
|**SSL 憑證 （也稱為伺服器驗證憑證）** <br/> |這是一個標準 SSL 憑證，用來保護同盟伺服器、 用戶端與同盟伺服器 proxy 電腦之間的通訊安全。  <br/> |AD FS 需要 SSL 憑證。 根據預設，AD FS，請針對預設網站在網際網路資訊服務 (IIS) 設定 SSL 憑證。  <br/> 這個 SSL 憑證的主體名稱用於判斷每個您所部署的 AD FS 執行個體的同盟服務 (FS) 名稱。 選擇任何新的憑證授權單位 (CA) 的主體名稱，請考慮-已發行的憑證適合代表貴公司或組織到 Office 365 的名稱。 此名稱必須是網際網路路由傳送。  <br/>**警告：** AD FS 要求這個 SSL 憑證必須具備任何無點 （簡短名稱） 的主體名稱。          <br/> **建議：** 因為此憑證必須受到信任的 AD FS 用戶端，我們建議您使用由公用 （協力廠商） CA 或屬於公開受信任的根; CA 所發出的 SSL 憑證例如，VeriSign 或 Thawte。  <br/> |
|**權杖簽署憑證** <br/> |這是標準的 X.509 憑證，用來安全地簽署同盟伺服器問題以及 Office 365 所接受並驗證的所有 token。  <br/> |權杖簽署憑證必須包含私密金鑰的鏈結到 FS 中的受信任的根。 根據預設，AD FS 會建立自我簽署的憑證。 不過，根據組織的需求，您可以變更此憑證 CA 發行的憑證來使用 AD FS 管理] 嵌入式管理單元中。  <br/>**警告：** 權杖簽署憑證是重要的 FS 穩定性。 如果憑證已變更，則必須變更的通知 Office 365。 如果沒有提供通知，使用者無法登入其 Office 365 服務方案。<br/>**建議：** 我們建議您使用自我簽署的權杖簽署憑證所產生的 AD FS。 如此一來，它會管理此憑證為您預設。 例如，當此憑證即將到期，AD FS 會產生新的自我簽署的憑證。  <br/> |
   
同盟伺服器 proxy 需要下表所述的憑證。
  
||||
|:-----|:-----|:-----|
|**憑證類型** <br/> |**描述** <br/> |**您需要知道部署之前** <br/> |
|SSL 憑證  <br/> |這是一個標準 SSL 憑證，用於保護同盟伺服器、 同盟伺服器 proxy 與網際網路用戶端電腦之間的通訊。  <br/> |這個 SSL 憑證必須是繫結至 IIS 中的預設網站，才能成功執行 [AD FS 同盟伺服器 Proxy 組態精靈。  <br/> 此憑證必須已在公司網路中同盟伺服器設定 SSL 憑證的主體名稱相同。  <br/> **建議：** 我們建議您使用此同盟伺服器 proxy 所連線之同盟伺服器設定的相同伺服器驗證憑證。  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>自動探索、 Outlook 無所不在 」 及 Active Directory 同步處理的憑證

您向外 Exchange 2013、 Exchange 2010、 Exchange 2007 和 Exchange 2003 用戶端存取伺服器 （凱） 需要第三方 SSL 憑證的自動探索、 Outlook Anywhere 和 Active Directory 同步處理服務的安全連線。 您可能已在內部部署環境中安裝此憑證。
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange 混合伺服器的憑證

對外 Exchange 混合式或多部伺服器需要第三方 SSL 憑證與 Exchange Online 服務的安全連線。 您必須從您的第三方 SSL 提供者取得此憑證。
  
## <a name="office-365-certificate-chains"></a>Office 365 的憑證鏈結

本文說明您可能需要在您的基礎結構上安裝的憑證。 如需有關在我們的 Office 365 伺服器上已安裝的憑證的詳細資訊，請參閱 < <b0>Office 365 的憑證鏈結</b0>。
  

