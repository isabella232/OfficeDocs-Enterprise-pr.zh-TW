---
title: "Contoso Corporation 的身分識別"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: "摘要： 了解如何利用 IDaaS Contoso，並提供地理位置分散變得多餘的和驗證其使用者。"
ms.openlocfilehash: d9aee05d36061433398cd8ce913a03bce65cc103
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="identity-for-the-contoso-corporation"></a>Contoso Corporation 的身分識別

 **摘要：**了解如何利用 IDaaS Contoso，並提供地理位置分散變得多餘的和驗證其使用者。
  
Microsoft 會提供跨其雲端方案以服務 (IDaaS) 的身分識別。若要採用雲端 （含） 的基礎結構，Contoso 的 IDaaS 解決方案必須並用其內部身分識別提供者並包括使用其現有的受信任、 協力廠商身分識別提供者同盟的驗證。
  
## <a name="contosos-windows-server-ad-forest"></a>Contoso 的 Windows Server AD 樹系

Contoso 會使用單一 Windows Server Active Directory (AD) 樹系與另一個適用於每個區域的全球的七個網域 contoso.com。Headquarters、 區域 hub 辦公室和衛星辦公室包含本機驗證和授權的網域控制站。
  
**圖 1： Contoso 的樹系及網域組成的全球**

![Contoso 的 Windows Server AD 樹系和世界各地的網域](images/Contoso_Poster/Contoso_WW_ID.png)
  
圖 1 顯示與區域不同組件的全球包含區域的集線器網域 Contoso 樹系。
  
Contoso 想要使用的帳戶和群組 contoso.com 樹系中的驗證與授權其雲端應用程式及工作負載。
  
## <a name="contosos-federated-authentication-infrastructure"></a>Contoso 的同盟的驗證基礎結構

Contoso 可讓：
  
- 客戶使用其 Microsoft、 Facebook、 或 Google Mail 的帳戶登入其公用網站。
    
- 廠商與協力廠商使用其 LinkedIn、 Salesforce、 或 Google Mail 的帳戶登入網路之協力廠商。
    
**圖 2： Contoso 的驗證支援的同盟的客戶與合作夥伴**

![Contoso 現有的基礎結構，用以支援客戶和合作夥伴同盟驗證](images/Contoso_Poster/Federated_ID.png)
  
圖 2 顯示包含公用網站、 外部網路是合作夥伴與 AD FS 伺服器的一組 Contoso DMZ。DMZ 被連線至網際網路包含客戶和合作夥伴與網際網路服務。
  
客戶認證以存取公用網站及合作夥伴外部存取的協力廠商認證進行驗證 DMZ 中的 active Directory Federation Services (AD FS) 伺服器。
  
當 Contoso 轉換至 Azure Web 應用程式與合作夥伴外部 Dynamics 365 至其公用網站時，他們想要繼續使用其客戶和合作夥伴這些協力廠商身分識別提供者。這會藉由設定 Contoso Azure AD 租用戶與這些協力廠商身分識別提供者之間的同盟。
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a>Contoso 的 Windows Server AD 樹系目錄同步處理

Contoso 已部署在其 Paris 資料中心伺服器的叢集上 「 Azure AD 連線工具。Azure AD 連線同步處理與共用的 Contoso 的 Office 365、 EMS、 Dynamics 365 和 Azure 訂閱 Azure AD 租用 contoso.com Windows Server AD 樹系的變更。如需訂閱、 授權、 使用者帳戶及租用戶的詳細資訊，請參閱[訂閱、 授權及使用者帳戶為 Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)。
  
**圖 3： Contoso 的目錄同步處理基礎結構**

![Contoso 的目錄同步處理基礎結構](images/Contoso_Poster/DirSync.png)
  
圖 3 是執行使用 Azure AD 租用戶同步處理 Contoso Windows Server AD 樹系的 Azure AD 連線的伺服器叢集。
  
Contoso 已設定的同盟的驗證，Contoso 的工作者提供單一登入。當使用者已經登入 contoso.com Windows Server AD 樹系存取 Microsoft SaaS 或 PaaS 雲端資源時，他們便不會提示密碼。
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a>Contoso 驗證流量的地理位置分布

若要更妥善地支援其行動電話和遠端工作團隊，Contoso 已部署在其區域辦公室驗證伺服器的設定。此基礎結構負載分散每個，並使用一般的 Azure AD 租用戶的 Microsoft cloud 方案存取的使用者認證進行驗證時提供備援和更高的效能。
  
若要將驗證要求的負載，Contoso 已設定 Azure 流量管理員具有設定檔使用路由方法，這是指地域最接近的一組驗證伺服器驗證的用戶端的效能。 
  
**圖 4： 地區分公司的驗證流量的地理位置分布**

![地區辦公室 Contoso 驗證流量的地理分配](images/Contoso_Poster/Auth_GeoDist.png)
  
圖 4 顯示區域辦公室的用戶端電腦、 Azure 流量管理員和驗證伺服器層級。每個區域的 office 會使用 web proxy 伺服器和 AD FS 伺服器來驗證使用者認證與 Windows Server AD 網域控制站。
  
驗證程序範例：
  
1. 用戶端電腦起始通訊網頁與 Office 365 租用中的歐洲 （例如 sharepoint.contoso.com)。
    
2. Office 365 後將要求傳送至傳送證明驗證。要求包含連絡人進行驗證的 URL。
    
3. 用戶端電腦嘗試在 URL 中的 DNS 名稱解析為 IP 位址。
    
4. Azure 流量管理員收到的 DNS 查詢和用戶端電腦與用戶端電腦最接近地區性 office 中的 web 應用程式 proxy 伺服器的 IP 位址的回應。
    
5.  用戶端電腦將驗證要求傳送至轉寄至 AD FS 伺服器要求的 web 應用程式 proxy 伺服器。
    
6. AD FS 伺服器要求用戶端電腦的使用者認證。
    
7. 用戶端電腦而不提示使用者傳送使用者認證。
    
8. AD FS 伺服器會驗證與區域 office 中的 Windows Server AD 網域控制站的認證，並傳回用戶端電腦的安全性權杖。
    
9. 用戶端電腦將安全性權杖傳送至 Office 365。
    
10. 在驗證成功之後 Office 365 的安全性權杖快取及傳送要求用戶端電腦的步驟 1 中的網頁。
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a>在 Azure IaaS headquarters 驗證基礎結構的備援

若要提供包含 15000 工作者 Paris headquarters 遠端和行動工作者備援，Contoso 已部署應用程式 proxy 與 AD FS 伺服器中的 Azure IaaS 第二組。
  
**圖 5： Azure IaaS 變得多餘的驗證基礎結構**

![巴黎總部 Azure IaaS 中的備援驗證基礎結構](images/Contoso_Poster/Paris_Auth_Redun.png)
  
圖 5 顯示 web proxy 伺服器和 AD FS 伺服器中 DMZ 以及跨部署 Azure 中的每個其他設定虛擬網路。
  
Headquarters DMZ 中主要的驗證伺服器變成無法使用，IT 人員切換至部署在 Azure IaaS 備援組 」。後續的驗證要求從 Paris office 電腦會使用組中 Azure IaaS 直到更正可用性問題。
  
切換和回、 交換器 Contoso 更新要用於 web 應用程式 proxy 的一組不同的 IP 位址的 Paris 區域的 Azure 流量管理員設定檔：
  
- DMZ 驗證伺服器可用、 DMZ 中使用之伺服器的 IP 位址。
    
- 當 DMZ 驗證伺服器無法使用，在 Azure IaaS 中使用之伺服器的 IP 位址。
    
## <a name="see-also"></a>請參閱

[Microsoft Cloud 中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[Microsoft Cloud Identity for Enterprise Architects](http://aka.ms/cloudarchidentity)
  
[Office 365 的身分識別與裝置保護](http://aka.ms/o365protect_device)
  
[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)



