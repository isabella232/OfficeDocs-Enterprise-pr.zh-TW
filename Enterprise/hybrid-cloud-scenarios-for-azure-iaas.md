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
description: 摘要： 了解混合式架構與案例適用於 Microsoft 的基礎結構即服務 (IaaS)-以 Azure 中的雲端供應項目。
ms.openlocfilehash: d3f4b4ccbc9dbfa54e6f1d0988624aeb71f27106
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487624"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Azure IaaS 的混合式雲端案例

 **摘要：** 了解混合式架構與案例適用於 Microsoft 的基礎結構即服務 (IaaS)-以 Azure 中的雲端供應項目。
  
擴充您的內部運算，到依主控 IT 工作負載中執行雲端的身分識別基礎結構跨單位 Azure 虛擬網路 (Vnet)。 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Azure IaaS 混合案例結構

圖 1 顯示在 Azure 中的 Microsoft IaaS 型混合式案例的架構。
  
**圖 1: Microsoft IaaS 型混合式案例，在 Azure 中**

![Azure 中的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
每個圖層的架構：
  
- 應用程式和案例
    
    IT 工作負載通常是多層式、 高度可用的應用程式是由 Azure 虛擬機器 (Vm) 所組成。
    
- 身分識別
    
    將身分識別伺服器，例如 Active Directory 網域服務 (AD DS) 網域控制站，新增至 Azure Vnet 中執行本機驗證伺服器的設定。
    
- 網路
    
    使用在網際網路上的站台對站 VPN 連線或是 ExpressRoute 連線到 Azure IaaS 的私用對等。
    
- 內部部署
    
    包含身分識別伺服器與在 Azure 中執行的身分識別伺服器同步。 也可以包含在 Azure 中執行的 Vm 可以存取，例如儲存和系統管理基礎結構的資源。
    
## <a name="directory-synchronization-server-for-office-365"></a>Office 365 的目錄同步處理伺服器

圖 2 所示，從 Azure VNet，執行您的目錄同步處理伺服器會延伸至雲端運算及身分識別基礎結構的範例。
  
**Azure IaaS 中的 Office 365 的圖 2： 目錄同步處理伺服器**

![Azure IaaS 中 Office 365 的目錄同步處理伺服器](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
圖 2 內部部署網路主控 AD DS 基礎結構，配合 proxy 伺服器及在其邊緣路由器。 路由器請連接至位於與站台對站台 VPN 或 ExpressRoute 連線，Azure VNet 的緣 Azure 閘道。 VNet 內的目錄同步處理伺服器會執行 Azure AD Connect。
  
Office 365 目錄同步處理伺服器與 Office 365 訂閱下 Azure AD 租用戶同步處理帳戶在 AD DS 中的清單。
  
目錄同步處理伺服器是 Windows 為主的伺服器，執行 Azure AD Connect。 更快的佈建或要減少您組織中的內部部署伺服器的數目，部署在 Azure IaaS 中的虛擬網路 (VNet) 中您的目錄同步處理伺服器。
  
目錄同步處理伺服器輪詢 AD DS 的變更，並再將其同步處理與 Office 365 訂閱。
  
如需詳細資訊，請參閱 <<c0>在 Microsoft Azure 中部署 Office 365 目錄同步。
  
## <a name="line-of-business-lob-application"></a>營運 (LOB) 應用程式

圖 3 顯示在 Azure IaaS 中執行的伺服器型 LOB 應用程式的組態。
  
**圖 3： 在 Azure IaaS 中的 LOB 應用程式**

![Azure IaaS 中的伺服器型 LOB 應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
圖 3 中，在內部部署網路主控身分識別基礎結構和使用者。 它會連線至 Azure IaaS 閘道與站台對站台 VPN 或 ExpressRoute 連線。 Azure IaaS 主控一個包含的 LOB 應用程式伺服器的虛擬網路。
  
您可以建立 Azure Vm，在 Azure 的資料中心 （也稱為位置） 位於 Azure VNet 的子網路上執行的 LOB 應用程式。
  
因為您基本上將您的內部部署基礎結構延伸到 Azure，您必須將唯一的私人位址空間指派給您的 Vnet，並更新內部路由的資料表，以確保能夠連接至每個 VNet。
  
連線之後，就可以管理這些 Vm 使用的遠端桌面連線或您的系統管理軟體，就像您的內部部署伺服器。
  
藉由設定之可公開公開的連接埠，這些 Vm 可也是從網際網路存取行動裝置或遠端使用者。
  
概念證明的設定，請參閱 < <b0>Simulated 跨單位 azure 虛擬網路</b0>。
  
裝載於 Azure Vm 的 LOB 應用程式的屬性如下所示：
  
- 多個層級
    
    一般的 LOB 應用程式使用的分層的方法。 一組伺服器員工或客戶存取提供身分識別、 資料庫處理、 應用程式與邏輯處理和前端網頁伺服器。 
    
- 高可用性
    
    一般的 LOB 應用程式提供高可用性使用每一層中的多部伺服器。 Azure IaaS 提供高達 99.9%執行時間 SLA 的 Azure 可用性設定組中的伺服器。 
    
- 負載分散
    
    若要將負載分散給層中的多個伺服器之間的網路流量，您可以使用的網際網路對向或內部 Azure 負載平衡器。 或者，您可以使用可用的專用的負載平衡器 appliance 從 Azure marketplace。
    
- 安全性
    
    若要保護伺服器免於來路不明從網際網路傳入的流量，您可以使用 Azure 網路安全性群組。 您可以定義允許或拒絕子網路或個別的虛擬機器的網路介面的流量。
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure 中的 SharePoint Server 2016 伺服器陣列

多層的範例，請在 Azure 中的高可用性 LOB 應用程式是 SharePoint Server 2016 伺服器陣列圖 4 所示。
  
**圖 4: 高可用性 SharePoint Server 2016 伺服器陣列 Azure IaaS 中**

![Azure IaaS 中的高可用性 SharePoint Server 2016 伺服器陣列](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
圖 4 」 中的內部網路可主控身分識別基礎結構與使用者。 它會連線至 Azure IaaS 閘道與站台對站台 VPN 或 ExpressRoute 連線。 Azure VNet 包含 SharePoint Server 2016 伺服器陣列，包括前端伺服器、 應用程式伺服器、 SQL Server 叢集，並在網域控制站的不同層的伺服器。
  
此設定在 Azure 中具有 LOB 應用程式的下列屬性： 
  
- 層級
    
    在伺服器陣列內執行不同的角色的伺服器建立層級和每一層有自己的子網路。
    
- 高可用性
    
    在每一層中使用多部伺服器，並將層的所有伺服器都放在相同的可用性設定組來達成。
    
- 負載分散
    
    內部 Azure 負載平衡器分散傳入的用戶端 web 流量的前端伺服器 （WEB1 與 WEB2），並 （SQL1、 SQL2 和 MN1） 的 SQL Server 叢集接聽程式 IP 位址。
    
- 安全性
    
    網路安全性群組的每個子網路可讓您設定允許的輸入和輸出流量。
    
請依照下列成功採用此路徑：
  
1. 評估並試驗
    
    請參閱[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)以了解在 Azure 中執行 SharePoint Server 2016 的優點。
    
    請參閱[Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)以建立模擬的開發/測試環境
    
2. 設計
    
    請參閱 <<c0>設計 SharePoint Server 2016 伺服器陣列在 Azure 中的逐步執行程序來判斷 Azure IaaS 的網路、 計算，並儲存項目，以裝載您的伺服器陣列，其設定的集合。
    
3. 部署
    
    請參閱[Deploying SharePoint Server 2016 with SQL Server AlwaysOn 可用性群組在 Azure 中](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)逐步執行五個階段中的高可用性伺服器陣列的端對端組態。
    
## <a name="federated-identity-for-office-365-in-azure"></a>Azure 中 Office 365 的同盟身分識別

在 Azure 中的多層式、 高可用性 LOB 應用程式的另一個例子是 Office 365 的同盟身分識別。
  
**圖 5: 高可用性同盟身分識別基礎結構的 Azure IaaS 中 Office 365**

![Office 365 的高可用性同盟驗證基礎結構，在 Azure 中](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
圖 5-內部部署網路主控身分識別基礎結構和使用者。 它會連線至 Azure IaaS 閘道與站台對站台 VPN 或 ExpressRoute 連線。 Azure VNet 包含 web proxy 伺服器、 Active Directory Federation Services (AD FS) 伺服器及 Active Directory 網域服務 (AD DS) 網域控制站。
  
此設定在 Azure 中具有 LOB 應用程式的下列屬性：
  
- **層：** 有 web proxy 伺服器、 AD FS 伺服器和 AD DS 網域控制站的層級。
    
- **載入通訊：** 外部 Azure 負載平衡器分散的傳入用戶端驗證要求的 web proxy，並內部 Azure 負載平衡器散發 AD FS 伺服器的驗證要求。
    
請依照下列成功採用此路徑：
  
1. 評估並試驗
    
    請參閱[Office 365 開發/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)來建立模擬的開發/測試環境與 Office 365 同盟驗證。
    
2. 部署
    
    請參閱 < <b0>Azure 中 Office 365 的部署高可用性同盟的驗證</b0>逐步執行五個階段中之高可用性 AD FS 基礎結構的端對端組態。
    
    
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)


