---
title: "高可用性同盟的驗證 Office 365 的階段 5 設定同盟驗證"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: "摘要： 設定您的 Office 365 的高可用性同盟驗證的 Azure AD Connect in Microsoft Azure。"
ms.openlocfilehash: 92e579c325d2cfa18e404d15d6add56fc225eedd
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a>高可用性同盟驗證階段 5： 設定 Office 365 同盟的驗證

 **摘要：**設定您的 Office 365 的高可用性同盟驗證的 Azure AD Connect in Microsoft Azure。
 
此部署高可用性同盟的驗證 Office 365 Azure 基礎結構服務中的最後階段中，在您取得並安裝的公用憑證授權單位所發出的憑證、 驗證您的設定，然後安裝並執行 Azure ADDirSync 伺服器上的連線。Azure AD 連線設定您的 Office 365 訂閱和您的 Active Directory Federation Services (AD FS) 和同盟驗證的 web 應用程式 proxy 伺服器。
  
請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。
  
## <a name="get-a-public-certificate-and-copy-it-to-the-dirsync-server"></a>取得公用憑證並將它複製到 DirSync 伺服器

從具有下列內容的公用憑證授權單位取得數位憑證：
  
- 適用於建立 SSL 連線的 X.509 憑證。
    
- 主體替代名稱 (SAN) 擴充屬性設定為同盟服務 FQDN (範例： fs.contoso.com)。
    
- 憑證必須具備私密金鑰和 PFX 格式儲存。
    
此外，您的組織電腦和裝置必須信任會發出數位憑證的公用憑證授權單位。從安裝在您的電腦和裝置上的受信任的根憑證授權單位存放區中的公用憑證授權單位的根憑證藉由建立此信任。通常執行 Microsoft Windows 的電腦必須安裝從常用的憑證授權單位的憑證這些類型的一組。如果尚未安裝從您的公用憑證授權單位的根憑證，則必須將此部署至電腦與您組織的裝置。
  
如需同盟驗證的憑證需求的詳細資訊，請參閱[federation 安裝與設定的必要條件](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)。
  
當您收到憑證時，請將它複製到 c： 磁碟機的 DirSync 伺服器上的資料夾。例如 SSL.pfx 的檔案名稱和儲存在 c:\\DirSync 伺服器上的 [憑證] 資料夾。
  
## <a name="verify-your-configuration"></a>確認您的設定

您現在應該準備好設定 Azure AD 連線] 及 [Office 365 同盟的驗證。若要確保您，以下是檢查清單：
  
- 您的組織部署公用網域新增至您的 Office 365 訂閱。
    
- 貴組織的 Office 365 使用者帳戶設定為您的組織部署公用網域名稱，且可以成功登入。
    
- 您已決定同盟服務 FQDN 型公用網域名稱。
    
- 在同盟服務 FQDN 指向公用 IP 位址的網際網路 Azure 的公用 DNS A 記錄負載平衡器的 web 應用程式 proxy 伺服器。
    
- 您同盟服務 FQDN 點的私人 IP 位址的內部 Azure 的負載平衡器的 AD FS 伺服器私人的 DNS A 記錄。
    
- 公用憑證授權單位 isssued 數位憑證合適與 SAN 設為同盟服務的 SSL 連線 FQDN 是 PFX 檔案儲存在 DirSync 伺服器。
    
- 公用憑證授權單位的根憑證安裝在信任的根憑證授權儲存在您的電腦和裝置。
    
以下是範例 Contoso 組織：
  
**高可用性的範例設定同盟 Azure 中的驗證基礎結構**

![Azure 中高可用性 Office 365 同盟驗證基礎結構的範例設定](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>執行設定同盟的驗證的 Azure AD 連線

「 Azure AD 連線工具設定 AD FS 伺服器、 web 應用程式 proxy 伺服器及 Office 365 同盟驗證進行這些步驟：
  
1. 使用具有本機系統管理員權限的網域帳戶建立 DirSync 伺服器的遠端桌面連線。
    
2. 從 DirSync 伺服器的桌面，開啟 Internet Explorer，並移至[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。
    
3. 在 [ **Microsoft Azure Active Directory 連線**] 頁面上，按一下 [**下載**] 及 [**執行**。
    
4. 在 [**歡迎使用 Azure AD 連線**] 頁面上按一下 [**我同意**] 和 [**繼續。**
    
5. 按一下 [ **Express 設定**] 頁面上的 [**自訂**]。
    
6. 按一下 [**安裝所需的元件**] 頁面的 [**安裝**]。
    
7. 在 [**使用者登入**] 頁面上按一下 [**與 AD FS 同盟**，然後按 [**下一步**。
    
8. 在 [**連接到 Azure AD** ] 頁面輸入名稱與您的 Office 365 訂閱的全域管理員帳戶的密碼並再按 [**下一步**。
    
9. 在**您的目錄連線**] 頁面上確認**樹系**中已選取您的內部部署 Windows Server AD 樹系、 輸入的名稱與網域管理員帳戶的密碼、 按一下 [**新增目錄**]，然後按 [**下一步**。
    
10. 在**Azure AD 登入設定**] 頁面上，按一下 [**下一步**]。
    
11. 按一下 [**網域及 OU 篩選**] 頁面的 [**下一步**]。
    
12. **唯一識別您的使用者**] 頁面上按一下 [**下一步**]。
    
13. 按一下 [**篩選使用者和裝置**] 索引標籤的 [**下一步**]。
    
14. 在 [**選用功能**] 頁面上按一下 [**下一步**]。
    
15. 按一下 [ **AD FS 伺服器陣列**] 頁面的 [**設定新的 AD FS 伺服器陣列**]。
    
16. 按一下 [**瀏覽**並指定的位置和來自公用憑證授權單位的 SSL 憑證的名稱。
    
17. 出現提示時，輸入憑證的密碼，並再按一下 [**確定]**。
    
18. 確認的**主體名稱**和**同盟服務名稱**設定為同盟服務 FQDN]，然後按 [**下一步**。
    
19. 在**AD FS 伺服器**] 頁面上輸入第一部 AD FS 伺服器的名稱 （表格 M-項目 4-虛擬機器名稱] 欄中），並再按一下 [**新增**]。
    
20. 輸入第二個 AD FS 伺服器的名稱 （表格 M-項目 5-虛擬機器名稱] 欄中）、 按一下 [**新增**]，並再按 [**下一步**。
    
21. 在 [ **Web 應用程式 Proxy 伺服器**] 頁面上輸入第一個 web 應用程式 proxy 伺服器的名稱 （表格 M-項目 6-虛擬機器名稱] 欄中），並再按一下 [**新增**]。
    
22. 輸入第二個 web 應用程式 proxy 伺服器的名稱 （表格 M-項目 7-虛擬機器名稱] 欄中）、 按一下 [**新增**]，並再按 [**下一步**。
    
23. 在 [**網域系統管理員認證**] 頁面上輸入使用者名稱和密碼的網域管理員帳戶，並再按 [**下一步**。
    
24. 在**AD FS 服務帳戶**] 頁面上輸入使用者名稱和密碼的企業系統管理員帳戶，並再按 [**下一步**。
    
25. 在**Azure AD 網域**] 頁面的 [**網域**] 中，選取您的組織 DNS 網域名稱，並再按 [**下一步**。
    
26. 在 [**準備好設定**] 頁面上按一下 [**安裝**]。
    
27. 按一下 [**安裝完成**] 頁面的 [**驗證**]。您應該在內部網路和網際網路看到兩個訊息，指出已順利驗證組態。
    
  - 內部網路訊息應列出您的 Azure 內部負載平衡器 AD FS 伺服器的私人 IP 位址。
    
  - 網際網路訊息應列出 web 應用程式 proxy 伺服器您 Azure 網際網路對向負載平衡器的公用 IP 位址。
    
28. 在 [**安裝完成**] 頁面上按一下 [**結束**]。
    
以下是與伺服器的版面配置區名稱的最後一個設定。
  
**階段 5： 高可用性的最後一個設定同盟 Azure 中的驗證基礎結構**

![Azure 中高可用性 Office 365 同盟驗證基礎結構的最後設定](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
您在 Azure 中的 Office 365 的高可用性同盟的驗證基礎架構即完成。
  
## <a name="see-also"></a>請參閱

[部署在 Azure 中的 Office 365 的高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 的同盟身分識別](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


