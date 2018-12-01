---
title: Azure IaaS 的混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 摘要： 了解混合式架構與案例的 Microsoft 的基礎結構以服務 (IaaS)-以 Azure 中的雲端方案。
ms.openlocfilehash: bb6611f51cc346273438e879d957597fe3299c58
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123240"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Azure IaaS 的混合式雲端案例

 **摘要：** 了解混合式架構與案例 Microsoft 的基礎結構以服務 (IaaS)-以 Azure 中的雲端方案。
  
擴充您的內部運算並將架設 IT 工作量中執行雲端身分識別基礎結構跨部署 Azure 虛擬網路 (VNets)。 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Azure IaaS 混合式案例的架構

圖 1 顯示在 Azure 中的 Microsoft IaaS 為基礎的混合式案例的架構。
  
**Azure 中的圖 1： Microsoft IaaS 為基礎的混合式案例**

![Azure 中的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
之架構的每個圖層：
  
- 應用程式與案例
    
    IT 工作負載通常是多層、 高度可用的應用程式所組成 Azure 虛擬機器 (Vm)。
    
- 身分識別
    
    將身分識別伺服器，例如 Windows Server AD 網域控制站，新增至 Azure VNets 中執行本機驗證伺服器的設定。
    
- 工作列最右邊的網路
    
    使用網站 VPN 連線透過網際網路或 ExpressRoute 連線至 Azure IaaS 私人對等。
    
- 內部部署
    
    包含已同步處理身分識別執行的伺服器在 Azure 中的身分識別伺服器。也可以包含在 Azure 中執行的 Vm 可以存取，例如儲存區與系統管理基礎結構的資源。
    
## <a name="dirsync-server-for-office-365"></a>Office 365 DirSync 伺服器

圖 2 所示在 Azure VNet，從執行您的目錄同步處理 (DirSync) 伺服器是擴充到雲端您運算與身分識別基礎結構的範例。
  
**圖 2： Azure IaaS 中的 Office 365 DirSync 伺服器**

![Azure IaaS 中 Office 365 DirSync 伺服器](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
圖 2] 中的內部網路主控 Windows Server AD 基礎結構、 proxy 伺服器和其邊緣路由器。路由器請連接至緣的網站 VPN 或 ExpressRoute 連線 Azure VNet Azure 閘道。內部 VNet DirSync 伺服器執行 Azure AD 連線。
  
Office 365 DirSync server 與 Office 365 訂閱 Azure AD 租用同步在 Windows Server AD 帳戶的清單。
  
DirSync Windows 型伺服器是執行 Azure AD 連線。更快的佈建或減少您組織中的內部部署伺服器的數目，部署您 DirSync server Azure IaaS 虛擬網路 (VNet) 中。
  
DirSync server 輪詢 Windows Server AD 的變更，然後將其同步與 Office 365 訂閱。
  
如需詳細資訊，請參閱[Microsoft Azure 中部署 Office 365 目錄同步](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。
  
## <a name="line-of-business-lob-application"></a>列的業務 (LOB) 應用程式

圖 3 是在 Azure IaaS 中執行的伺服器端 LOB 應用程式的設定。
  
**圖 3： 在 Azure IaaS 的 LOB 應用程式**

![Azure IaaS 中的伺服器型 LOB 應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
圖 3-內部網路主控身分識別基礎結構與使用者。所連接的網站 VPN 或 ExpressRoute 連線的 Azure IaaS 閘道。Azure IaaS 主控的 LOB 應用程式伺服器所在的虛擬網路。
  
您可以建立 Azure Vm，位於子網路的 Azure VNet 在 Azure 資料中心內 （又稱為位置） 上執行的 LOB 應用程式。
  
因為您基本上以 Azure 擴充您的內部部署基礎結構，您必須將唯一的私人位址空間指派給您 VNets 及更新您的內部路由表以確保能夠連接至每個 VNet。
  
一旦連線，可以管理這些 Vm 與遠端桌面連線和您的系統管理軟體，就像是您的內部伺服器。
  
透過設定公開公開的連接埠，這些 Vm 也可從網際網路行動裝置或遠端使用者。
  
驗證概念來設定，請參閱[Simulated 跨部署在 Azure 虛擬網路](simulated-cross-premises-virtual-network-in-azure.md)。
  
Azure Vm 上裝載的 LOB 應用程式的屬性如下所示：
  
- 多層
    
    典型的 LOB 應用程式使用分層的方法。設定伺服器的員工或客戶存取提供身分識別、 資料庫處理、 應用程式及邏輯處理與前端網頁伺服器。 
    
- 高可用性
    
    典型的 LOB 應用程式提供高可用性使用多部伺服器的每一層。Azure IaaS 提供 99.9%執行時間 SLA Azure 可用性設定中的伺服器。 
    
- 負載分散
    
    若要散佈層內的多部伺服器之間的網路流量的負載，您可以使用網際網路或內部 Azure 負載平衡器。或者，您可以使用可用的專用的負載平衡器 appliance 從 Azure marketplace。
    
- 安全性
    
    若要從網際網路的來路不明傳入流量保護伺服器，您可以使用 Azure 網路安全性群組。您可以定義允許或拒絕的子網路或個別的虛擬機器的網路介面的流量。
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>SharePoint Server 2016 Azure 中的伺服器陣列

多層的範例，Azure 中高度可用的 LOB 應用程式是 SharePoint Server 2016 伺服器陣列，如圖 4 所示。
  
**圖 4： 在高可用性 SharePoint 伺服器 2016年伺服器陣列中 Azure IaaS**

![Azure IaaS 中高可用性的 SharePoint Server 2016 伺服器陣列](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
圖 4] 中的內部網路主控身分識別基礎結構與使用者。所連接的網站 VPN 或 ExpressRoute 連線的 Azure IaaS 閘道。Azure VNet 包含 SharePoint Server 2016 伺服器陣列，其中包含前端伺服器、 應用程式伺服器、 SQL Server 叢集，並在網域控制站的不同層的伺服器。
  
此設定包含在 Azure 中 LOB 應用程式的下列屬性： 
  
- 各層
    
    伺服器陣列內執行不同的角色的伺服器建立在各層和每一層有自己的子網路。
    
- 高可用性
    
    可達到每一層中使用多部伺服器，並在相同的可用性一組中放入層的所有伺服器。
    
- 負載分散
    
    內部 Azure 負載平衡器散佈傳入的用戶端 web 流量 （WEB1 和 WEB2） 與前端伺服器和 SQL Server 叢集 （SQL1、 SQL2、 和 MN1） 的接聽程式 IP 位址。
    
- 安全性
    
    每個子網路的網路安全性群組可讓您設定允許輸入和輸出的流量。
    
請遵循成功採用此路徑：
  
1. 評估及試驗
    
    請參閱[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)了解 SharePoint Server 2016 執行 Azure 中的優點。
    
    請參閱[在 Azure 的開發人員測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)建置模擬的開發人員測試環境
    
2. 設計
    
    請參閱逐一檢視程序，以決定 Azure IaaS 網路、 compute、 及儲存項目來架設在伺服器陣列和其設定一組[設計 Azure 中的 SharePoint Server 2016 伺服器陣列](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)。
    
3. 部署
    
    請參閱[使用 SQL Server AlwaysOn 可用性群組 Azure 中部署 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)逐一檢視端對端陣列的設定高可用性的五個階段。
    
## <a name="federated-identity-for-office-365-in-azure"></a>在 Azure 中的 Office 365 同盟身分識別

在 Azure 中的多層、 高度可用 LOB 應用程式的另一個例子是 Office 365 同盟身分識別。
  
**圖 5： 在高可用性同盟身分識別基礎結構的 Azure IaaS 中的 Office 365**

![高可用性 Office 365 同盟 Azure 中的驗證基礎結構](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
圖 5-內部網路主控身分識別基礎結構與使用者。所連接的網站 VPN 或 ExpressRoute 連線的 Azure IaaS 閘道。Azure VNet 包含 web proxy 伺服器、 Active Directory Federation Services (AD FS) 伺服器及 Windows Server Active Directory (AD) 的網域控制站。
  
此設定包含在 Azure 中 LOB 應用程式的下列屬性：
  
- **層：** 有各層的 web proxy 伺服器、 AD FS 伺服器及 Windows Server AD 網域控制站。
    
- **載入通訊：** 外部 Azure 負載平衡器將傳入用戶端驗證要求的 web proxy 至和內部 Azure 負載平衡器散佈 AD FS 伺服器的驗證要求。
    
請遵循成功採用此路徑：
  
1. 評估及試驗
    
    請參閱建立 Office 365 同盟驗證的模擬的開發人員測試環境[的 Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)。
    
2. 部署
    
    請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)逐一檢視五個階段中的 [AD FS 基礎結構的高可用性的端對端設定。
    
    
## <a name="see-also"></a>請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)


