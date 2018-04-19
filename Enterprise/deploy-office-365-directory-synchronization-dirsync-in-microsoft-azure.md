---
title: 部署 Microsoft Azure 中的 Office 365 目錄同步作業
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 摘要： 部署中要同步處理您的內部部署目錄與 Office 365 訂閱的 Azure AD 租用戶之間的帳戶 Azure 虛擬機器上的 Azure AD 連線。
ms.openlocfilehash: 31a72d027acd274c9908a7e63e83843bce9cec71
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a>部署 Microsoft Azure 中的 Office 365 目錄同步作業

 **摘要：**部署 Azure AD 連線中要同步處理您的內部部署目錄與 Office 365 訂閱的 Azure AD 租用戶之間的帳戶 Azure 虛擬機器上。
  
Azure Active Directory (AD) 連線 （前身為目錄同步作業工具、 目錄同步作業工具或 DirSync.exe 工具） 已加入網域的伺服器安裝的伺服器型應用程式同步處理您的內部 Windows 伺服器Active Directory 使用者至 Office 365 訂閱的 Azure Active Directory 租用戶。您可以安裝 Azure AD 連接內部部署伺服器上，但您也可以安裝它在 Azure 虛擬機器上的原因如下：
  
- 您可以更快速地佈建和設定雲端架構伺服器，以便讓您的使用者可以更早使用服務。
    
- Azure 提供以較少的改善網站可用性。
    
- 您可以減少組織中的內部部署伺服器數目。
    
> [!IMPORTANT]
> 此解決方案所需的內部網路與 Azure 虛擬網路之間的連線。如需詳細資訊，請參閱[Microsoft Azure 虛擬網路的內部網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。 
  
> [!IMPORTANT]
> 本文說明在單一樹系中的單一網域的同步處理。Azure AD 連線同步與 Office 365 的 Active Directory 樹系中所有的 Windows Server AD 網域。如果您有多個 Active Directory 樹系同步處理與 Office 365，請參閱[使用單一登入案例的多樹系目錄同步處理](https://go.microsoft.com/fwlink/p/?LinkId=393091)。 
  
> [!NOTE]
> Office 365 使用 Azure Active Directory (Azure AD) 及其目錄服務。您的 Office 365 訂閱包括 Azure AD 租用戶。此租用戶也用於您組織的身分識別與其他雲端工作量，包括在 Azure 中的其他 saas 和應用程式和應用程式的管理。 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>在 Azure 中部署 Office 365 目錄同步作業的概觀 
<a name="Overview"> </a>

下圖顯示在 Azure （目錄同步處理伺服器） 同步處理至 anOffice 365 訂閱內部部署 Windows Server AD 樹系中的虛擬機器上執行的 Azure AD 連線。
  
![Azure 同步處理內部部署帳戶中虛擬機器上的 Azure AD Connect 工具，至具有流量之 Office 365 訂閱的 Azure AD 租用戶](images/CP_DirSyncOverview.png)
  
在圖表中，有兩個連接至網站 VPN 或 ExpressRoute 連接所連接的網路。沒有其中 Windows Server AD 網域控制站，且沒有目錄同步處理伺服器，這是在虛擬機器與 Azure 虛擬網路的內部網路執行[Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)。有兩個主要的流量流程源自目錄同步處理伺服器：
  
-  Azure AD Connect 將內部部署網路上的網域控制器排入佇列，來處理帳戶和密碼的變更。
    
-  Azure AD 連線將變更傳送至帳戶及密碼到您的 Office 365 訂閱 Azure AD 執行個體。因為您的內部網路延伸部分為目錄同步處理伺服器，透過內部網路的 proxy 伺服器傳送這些變更。
    
> [!NOTE]
> 此解決方案說明單一 Active Directory 網域的單一 Active Directory 樹系中的同步處理。Azure AD 連線同步與 Office 365 的 Active Directory 樹系中所有的 Active Directory 網域。如果您有多個 Active Directory 樹系同步處理與 Office 365，請參閱[使用單一登入案例的多樹系目錄同步處理](https://go.microsoft.com/fwlink/p/?LinkId=393091)。 
  
在這兩種情況下，源自由 Azure 虛擬機器上執行的 Azure AD 連線的流量會轉接至閘道在 Azure，然後將流量轉送跨網站 VPN 或 ExpressRoute 連線 VPN 閘道裝置的虛擬網路上在內部網路。在內部網路的路由基礎結構然後轉寄才到達目的地，例如在網域控制站或 proxy 伺服器的流量。
  
部署此解決方案有兩個主要步驟：
  
1. 建立 Azure 虛擬網路，並建立網站 VPN 連線至您的內部網路。如需詳細資訊，請參閱[Microsoft Azure 虛擬網路的內部網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。
    
2. [Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)已加入網域的虛擬機器上安裝在 Azure，並同步處理至 Office 365 內部部署 Windows Server AD。這包括：
    
    建立執行 Azure AD Connect Azure 虛擬機器。
    
    安裝及設定[Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)。
    
    設定 Azure AD 連線需要 Azure AD 管理員帳戶及 Windows Server AD 企業系統管理員帳戶的認證 （使用者名稱和密碼）。Azure AD 連線執行立即並持續供同步處理至 Office 365 的內部部署 Windows Server AD 樹系。
    
您在實際執行此解決方案部署之前，請使用[目錄同步處理 Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示以這種組態設定概念證明、 試驗或的示範。
  
> [!IMPORTANT]
> 當 Azure AD Connect 組態完成時，它不會儲存 Windows Server AD 企業系統管理員帳戶認證。 
  
> [!NOTE]
> 此解決方案說明同步處理至 Office 365 的單一 Windows Server AD 樹系。本文所討論的拓撲代表只有一個方法可以實作此解決方案。貴組織的拓撲可能會根據您唯一的網路需求及安全性考量而有所不同。 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a>規劃架設在 Azure 中的 Office 365 的目錄同步處理伺服器
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>必要條件

開始之前，請先檢閱本解決方案的下列必要條件：
  
- 檢閱中[規劃 Azure 虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)的相關規劃內容。
    
- 請確定您符合設定 Azure 虛擬網路的所有[必要軟體](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites)。
    
- 具有 Office 365 訂閱包括 Active Directory 的整合功能。如需 Office 365 訂閱，移至[Office 365 訂閱 」 頁面](https://go.microsoft.com/fwlink/p/?LinkId=394278)。
    
- 佈建執行 Azure AD 連線至與 Office 365 同步處理內部部署 Windows Server AD 樹系的一個 Azure 虛擬機器。
    
    您必須在 Windows Server AD 企業系統管理員帳戶和 Azure Active Directory 管理員帳戶的認證 （名稱與密碼）。
    
### <a name="solution-architecture-design-assumptions"></a>解決方案架構設計假設

下列清單描述此解決方案所做的設計選擇。
  
- 此解決方案使用單一 Azure 虛擬網路與網站 VPN 連線的情況。Azure 虛擬網路主控包含一部伺服器的單一子網路、 目錄同步處理伺服器執行 Azure AD 連線。 
    
- 在內部部署網路上會有網域控制站 和 DNS 伺服器。
    
- Azure AD 連線執行而不是單一登入的密碼雜湊同步處理。您沒有部署 Active Directory Federation Services (AD FS) 基礎結構。若要深入了解密碼雜湊同步處理與單一登入選項，請參閱[選擇 Azure Active Directory 混合式身分識別解決方案正確的驗證方法](http://aka.ms/auth-options)。
    
在您的環境中部署此解決方案時，您可能會考慮的其他設計選擇。其中包含下列各項：
  
- 如果那里現有的 DNS 伺服器中的現有 Azure 虛擬網路，決定是否要讓您要用於名稱解析，而不是在內部網路上的 DNS 伺服器的目錄同步處理伺服器。
    
- 如果現有的 Azure 虛擬網路中有網域控制站，判斷是否設定 Active Directory 站台及服務可能會較佳的選項。目錄同步處理伺服器可以查詢中的帳戶和密碼，而不是在內部網路上的網域控制站中變更 Azure 虛擬網路網域控制站。
    
## <a name="deployment-roadmap"></a>部署藍圖
<a name="DeploymentRoadmap"> </a>

部署在 Azure 虛擬機器上的 Azure AD 連接包含三個階段：
  
- 階段 1：建立及設定 Azure 虛擬網路
    
- 階段 2：建立及設定 Azure 虛擬機器
    
- 階段 3：安裝及設定 Azure AD Connect
    
部署之後，您也必須在 Office 365 中指派位置和新的使用者帳戶的授權。
  
> [!TIP]
> [Azure 部署套件中的目錄同步處理伺服器](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)」 會包含所有建置取出此解決方案、 Microsoft PowerPoint 與 Visio 格式、 圖表及 Microsoft Excel 設定活頁簿所產生的 Azure PowerShell 組塊針對您的設定自訂 azure PowerShell 命令區塊。
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>階段 1：建立及設定 Azure 虛擬網路

若要建立及設定 Azure 虛擬網路，完成[階段 1： 準備您的內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1)和[階段 2： 在 Azure 中建立跨內部虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2)部署中的[藍圖連線至內部網路Microsoft Azure 虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。
  
這是您產生的組態。
  
![階段 1 Azure 中主控的 Office 365 的目錄同步處理伺服器](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
本圖顯示使用站台對站台 VPN 或 ExpressRoute 連線方式，連線到 Azure 虛擬網路的內部部署網路。
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>階段 2：建立及設定 Azure 虛擬機器

在 Azure 中使用的指示[建立您第一部 Windows 的虛擬機器在 Azure 的入口網站中](https://go.microsoft.com/fwlink/p/?LinkId=393098)建立虛擬機器。使用下列設定：
  
- 在 [**基礎**] 窗格中選取相同的訂閱、 位置及資源群組為虛擬網路。安全的位置記錄的使用者名稱和密碼。您將需要這些稍後來連線至虛擬機器。
    
- 在 [**選擇大小**] 窗格中，選擇 [ **A2 標準**大小。
    
- 在 [**設定**] 窗格中 [**儲存**] 區段中選取的**標準**儲存類型。在 [**網路**] 區段中選取主控目錄同步處理伺服器 (不 GatewaySubnet) 虛擬網路和子網路的名稱。保留所有其他設定的預設值。
    
確認您的目錄同步處理伺服器使用 DNS 正常檢查您的內部 DNS 以確定地址 (A) 記錄已新增其 IP 位址的虛擬機器。 
  
使用中[連線至虛擬機器和登入](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)的指示來連線至遠端桌面連線的目錄同步處理伺服器。登入之後, 加入內部部署 Windows Server AD 網域中的虛擬機器。
  
對於 Azure AD 連線至網際網路資源的存取，您必須設定為使用內部網路的 proxy 伺服器的目錄同步處理伺服器。您應該連絡任何其他設定步驟來執行網路的管理員。
  
這是您產生的組態。
  
![階段 2 Azure 中主控的 Office 365 的目錄同步處理伺服器](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
此圖顯示目錄同步處理伺服器虛擬機器跨部署在 Azure 虛擬網路。
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>階段 3：安裝及設定 Azure AD Connect

完成下列程序：
  
1. 連線到目錄同步處理伺服器使用遠端桌面連線與 Windows Server AD 網域帳戶具有本機系統管理員權限。請參閱[連線至虛擬機器和登入](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)。
    
2. 從目錄同步處理伺服器，開啟 [[設定 Office 365 中目錄同步作業](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)文章並遵循與密碼雜湊同步處理的目錄同步作業的指示。
    
> [!CAUTION]
> 安裝在本機使用者組織單位 (OU) 中建立**AAD_xxxxxxxxxxxx**帳戶。無法移動或移除此帳戶或同步處理將會失敗。
  
這是您產生的組態。
  
![階段 3 架設在 Azure 中的 Office 365 的目錄同步處理伺服器](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
此圖顯示 Azure AD 連線的目錄同步處理伺服器跨部署在 Azure 虛擬網路。
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>在 Office 365 中指派位置及授權給使用者

Azure AD Connect 會從內部部署 Windows Server AD 新增帳戶至您的 Office 365 訂閱，但為了讓使用者登入 Office 365 並使用其服務，帳戶必須已設定位置及授權。若要新增位置，並啟用適當的使用者帳戶的授權，請執行下列步驟︰
  
1. 登入[Office 365 入口網站頁面](https://portal.office.com)，並按一下 [**管理**。
    
2. 在左導覽列中，按一下 [**使用者 > 作用中使用者**。
    
3. 在使用者帳戶清單中，選取您要啟動使用者旁的核取方塊。
    
4. 在 [使用者] 頁面上按一下 [**產品授權**的 [**編輯**]。
    
5. 在 [**產品授權**] 頁面上的**位置**，選取使用者的位置並啟用適當的授權使用者。
    
6. 完成後，按一下 [**儲存**] 和 [**關閉**兩次。
    
7. 針對其他使用者請回到步驟 3。
    
## <a name="see-also"></a>概念

<a name="DeploymentRoadmap"> </a>

[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
  
[在內部網路連線到 Microsoft Azure 虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[下載 Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)
  
[設定 Office 365 中目錄同步作業](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[Azure 部署套件中的目錄同步處理伺服器](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



