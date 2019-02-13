---
title: Office 365 協力廠商的 SSL 憑證的計劃
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要：說明 Exchange 內部和混合部署、使用 AD FS 的 SSO、Exchange Online 服務及 Exchange Web 服務所需的 SSL 憑證。
ms.openlocfilehash: 1746cf5059ba83e225e4a2d55c8eebc082366362
ms.sourcegitcommit: bdd0083dc9dc62994de29421a1f4056ebe27f15f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "29952469"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365 協力廠商的 SSL 憑證的計劃

 **摘要：** 說明 Exchange 內部和混合部署、 使用 AD FS 的 SSO 所需的 SSL 憑證 Exchange Online 服務及 Exchange Web 服務。 
  
若要將用戶端與 Office 365 環境之間的通訊加密，必須基礎結構伺服器上安裝協力廠商安全通訊端層 (SSL) 憑證。

||
|:-----|
| 本文是[網路規劃和 Office 365 的效能調整](https://aka.ms/tune)的一部分。|
   
下列 Office 365 元件需要憑證：
  
- Exchange 內部部署
    
- 單一登入 (SSO) (針對 Active Directory Federation Services (AD FS) 同盟伺服器和 AD FS 同盟伺服器 Proxy)
    
- Exchange Online 服務，例如自動探索、 「 Outlook 無所不在 」，以及 Exchange Web 服務
    
- Exchange 混合伺服器
    
## <a name="certificates-for-exchange-on-premises"></a>Exchange 內部部署的憑證

如需如何使用數位憑證保護內部部署 Exchange 組織與 Exchange Online 之間的通訊安全，請參閱 TechNet 文章[了解憑證需求](https://go.microsoft.com/fwlink/p/?LinkID=243657)的概觀。
  
## <a name="certificates-for-single-sign-on"></a>單一登入的憑證

簡化單一登入經驗，包含完善的安全性提供您的使用者，在同盟伺服器或同盟伺服器 proxy 需要下表所示憑證。下表重點在於 Active Directory Federation Services (AD FS)，我們也可以使用[協力廠商身分識別提供者](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的詳細資訊。
  
||||
|:-----|:-----|:-----|
|**憑證類型** <br/> |**描述** <br/> |**開始部署之前您必須了解的資訊** <br/> |
|**SSL 憑證 (也稱為伺服器驗證憑證)** <br/> |這是一個標準 SSL 憑證，用來保護同盟伺服器、用戶端及同盟伺服器 Proxy 電腦之間的通訊安全。  <br/> |AD FS 需要 SSL 憑證。根據預設，AD FS 會使用預設網站在網際網路資訊服務 (IIS) 設定 SSL 憑證。<br/> 這個 SSL 憑證的主體名稱用於判斷每個您所部署的 AD FS 執行個體的同盟服務 (FS) 名稱。請考慮選擇任何新的憑證授權單位 (CA) 的主體名稱-發出憑證適合代表公司或組織至 Office 365 的名稱。此名稱必須是網際網路可路由。<br/>**小心：** AD FS 會要求這個 SSL 憑證沒有無點 （簡短名稱） 的主體名稱。          <br/> **建議：** 因為此憑證必須由用戶端的 AD FS 信任，建議您依照公用 （第三方） CA 或公開受信任的根; 從屬於 CA 所發出的 SSL 憑證例如，VeriSign 或 Thawte。  <br/> |
|**權杖簽署憑證** <br/> |這是標準的 X.509 憑證，用來安全地簽署同盟伺服器問題以及 Office 365 所接受並驗證的所有 token。  <br/> |權杖簽署憑證必須包含鏈結到受信任的根 FS 中的私密金鑰。根據預設，AD FS 會建立自我簽署的憑證。不過，根據組織的需求，您可以變更此憑證 CA 發行的憑證來使用 AD FS 管理] 嵌入式管理單元。<br/>**小心：** 權杖簽署憑證是重要的 FS 穩定性。如果變更憑證，Office 365 必須通知的變更。如果未提供通知使用者無法登入其 Office 365 服務方案。<br/>**建議：** 我們建議您使用自我簽署的權杖簽署憑證產生的 AD FS。如此一來，它會管理此憑證您預設。例如，此憑證即將到期時，AD FS 將會產生新的自我簽署的憑證。<br/> |
   
同盟伺服器 Proxy 需要下表中所述的憑證。
  
||||
|:-----|:-----|:-----|
|**憑證類型** <br/> |**描述** <br/> |**開始部署之前您必須了解的資訊** <br/> |
|SSL 憑證  <br/> |這是一個標準 SSL 憑證，用來保護同盟伺服器、同盟伺服器 Proxy 及網際網路用戶端電腦之間的通訊安全。  <br/> |這個 SSL 憑證必須繫結至 IIS 中的預設網站才可成功執行 [AD FS 同盟伺服器 Proxy 設定精靈]。  <br/> 這個憑證的主體名稱必須與公司網路中同盟伺服器上設定之 SSL 憑證的主體名稱相同。  <br/> **建議：** 建議您使用此同盟伺服器 Proxy 所連線之同盟伺服器上設定的同一個伺服器驗證憑證。  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>自動探索 」、 「 Outlook 無所不在 」 及 「 Active Directory 同步處理的憑證

向外 Exchange 2013、 Exchange 2010、 Exchange 2007 與 Exchange 2003 用戶端存取伺服器 （類別） 需要第三方 SSL 憑證的自動探索、 Outlook 無所不在，與 Active Directory 同步處理服務的安全連線。您可能已安裝在您的內部部署環境中此憑證。
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>適用於 Exchange 混合式伺服器的憑證

向外 Exchange 混合伺服器需要安全連線與 Exchange Online 服務的第三方 SSL 憑證。您需要從您的第三方 SSL 提供者取得此憑證。
  
## <a name="office-365-certificate-chains"></a>Office 365 憑證鏈結

本文說明您可能需要在您的基礎結構上安裝的憑證。如需有關我們 Office 365 的伺服器上已安裝的憑證的詳細資訊，請參閱[Office 365 憑證鏈結](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)。
  

