---
title: 在 Microsoft Azure 中部署 Office 365 目錄同步作業
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 摘要：在 Azure 中的虛擬機器上部署 Azure AD Connect，以同步處理內部部署目錄和您 Office 365 訂閱下 Azure AD 租用戶之間的帳戶。
ms.openlocfilehash: 01dede756142c08722e3cf21d91a0028eb815051
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915638"
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="7c832-103">在 Microsoft Azure 中部署 Office 365 目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="7c832-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="7c832-104">**摘要：** 在 Azure 中的虛擬機器上部署 Azure AD Connect，以同步處理內部部署目錄和您 Office 365 訂閱下 Azure AD 租用戶之間的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7c832-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="7c832-p101">Azure Active Directory (AD) Connect (先前稱為目錄同步作業工具、目錄同步處理工具或 DirSync.exe 工具) 是一個在已加入網域之伺服器上安裝的伺服器型應用程式，可同步處理您的內部部署 Windows Server Active Directory 使用者以及與您 Office 365 訂閱的 Azure Active Directory。您可以在內部部署伺服器上安裝 Azure AD Connect，也可以在 Azure 中的虛擬機器上安裝它，原因如下：</span><span class="sxs-lookup"><span data-stu-id="7c832-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="7c832-107">您可以更快速地佈建和設定雲端架構伺服器，以便讓您的使用者可以更早使用服務。</span><span class="sxs-lookup"><span data-stu-id="7c832-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="7c832-108">Azure 以更輕鬆的方式提供更佳的網站可用性。</span><span class="sxs-lookup"><span data-stu-id="7c832-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="7c832-109">您可以減少組織中的內部部署伺服器數目。</span><span class="sxs-lookup"><span data-stu-id="7c832-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="7c832-p102">本解決方案需要內部部署網路與 Azure 虛擬網路之間的連線。如需詳細資訊，請參閱＜[使內部部署網路與 Microsoft Azure 虛擬網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="7c832-p103">本文說明單一樹系中單一網域的同步處理。Azure AD Connect 會將 Active Directory 樹系中的所有 Windows Server AD 與 Office 365 同步。如果您有多個 Active Directory 樹系要與 Office 365 進行同步處理，請參閱＜[使用單一登入的多樹系目錄同步案例](https://go.microsoft.com/fwlink/p/?LinkId=393091)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7c832-p104">Office 365 使用 Azure Active Directory (Azure AD) 作為其目錄的服務。此 Office 365 訂閱包含 Azure AD 租用戶。此租用戶也可用於管理組織中具有其他雲端工作負載的身分，包括其他 SaaS 應用程式和 Azure 中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c832-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="7c832-118">在 Azure 中部署 Office 365 目錄同步作業的概觀</span><span class="sxs-lookup"><span data-stu-id="7c832-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>

<span data-ttu-id="7c832-119">下圖顯示 Azure 的虛擬機器 (DirSync 伺服器) 上執行 Azure AD Connect 將 Windows Server AD 樹系同步處理和內部部署至 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="7c832-119">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Azure 同步處理內部部署帳戶中虛擬機器上的 Azure AD Connect 工具，至具有流量之 Office 365 訂閱的 Azure AD 租用戶](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="7c832-p105">在此圖表中，有兩個使用站對站 VPN 或 ExpressRoute 連線連接的網路。有一個其中存在 Windows Server AD 網域控制器的內部部署網路，和一個 Azure 虛擬網路，其中包含目錄同步處理伺服器 (執行 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) 的虛擬機器)。從目錄同步處理伺服器會產生二個主要流量：</span><span class="sxs-lookup"><span data-stu-id="7c832-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="7c832-124">Azure AD Connect 將內部部署網路上的網域控制器排入佇列，來處理帳戶和密碼的變更。</span><span class="sxs-lookup"><span data-stu-id="7c832-124">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="7c832-p106">Azure AD Connect 將帳戶和密碼的變更傳送至 Office 365 訂閱的 Azure AD 執行個體。因為目錄同步處理伺服器是內部部署網路的擴充部分，所以這些變更會透過內部部署網路的 Proxy 伺服器進行傳送。</span><span class="sxs-lookup"><span data-stu-id="7c832-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="7c832-p107">此解決方案說明單一 Active Directory 樹系中單一 Active Directory 網域的同步處理。Azure AD Connect 會將 Active Directory 樹系中的所有 Active Directory 網域與 Office 365 同步處理。如果您有多個 Active Directory 樹系要與 Office 365 進行同步處理，請參閱＜[使用單一登入的多樹系目錄同步案例](https://go.microsoft.com/fwlink/p/?LinkId=393091)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="7c832-p108">在這兩種情況下，在 Azure 虛擬機器上執行 Azure AD Connect 所產生的流量會被轉送至 Azure 虛擬網路上的閘道，此 VPN 閘道會接著將所有站對站 VPN 或 ExpressRoute 連線的流量轉送到內部部署網路上的 VPN 閘道裝置。內部部署網路的路由基礎結構接著會將流量轉送到目的地，例如網域控制站或 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c832-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="7c832-132">部署此解決方案有兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="7c832-132">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="7c832-p109">建立 Azure 虛擬網路，以及建立您的內部部署網路的站對站 VPN 連線。如需詳細資訊，請參閱＜[使內部部署網路與 Microsoft Azure 虛擬網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="7c832-p110">在 Azure 中已加入網域的虛擬機器上，安裝 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)，然後將內部部署 Windows Server AD 與 Office 365 同步處理。這涉及以下步驟：</span><span class="sxs-lookup"><span data-stu-id="7c832-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="7c832-137">建立 Azure 虛擬機器以執行 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="7c832-137">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="7c832-138">安裝及設定 [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)。</span><span class="sxs-lookup"><span data-stu-id="7c832-138">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="7c832-p111">設定 Azure AD Connect 需要 Azure AD 系統管理員帳戶和 Windows Server AD 企業系統管理員帳戶的認證 (使用者名稱和密碼)。Azure AD Connect 會立即執行，並持續將內部部署 Windows Server AD 樹系與 Office 365 進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="7c832-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="7c832-141">在您於生產環境中部署此解決方案之前，請使用＜[適用於 Office 365 開發/測試環境的目錄同步作業](dirsync-for-your-office-365-dev-test-environment.md)＞中的指示，將此組態設定為示範或實驗的概念證明。</span><span class="sxs-lookup"><span data-stu-id="7c832-141">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="7c832-142">當 Azure AD Connect 組態完成時，它不會儲存 Windows Server AD 企業系統管理員帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="7c832-142">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7c832-p112">此解決方案說明單一 Windows Server AD 樹系與 Office 365 的同步處理。本文中所討論的拓樸僅代表一個實作本解決方案的方式。根據特定的網路需求與安全性考量，貴組織的拓樸可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="7c832-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="7c832-146">Azure 中 Office 365 目錄同步處理伺服器的主控方案</span><span class="sxs-lookup"><span data-stu-id="7c832-146">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="7c832-147"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="7c832-147"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="7c832-148">必要條件</span><span class="sxs-lookup"><span data-stu-id="7c832-148">Prerequisites</span></span>

<span data-ttu-id="7c832-149">開始之前，請先檢閱本解決方案的下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="7c832-149">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="7c832-150">檢閱＜[規劃您的 Azure 虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)＞中的相關規劃內容。</span><span class="sxs-lookup"><span data-stu-id="7c832-150">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="7c832-151">確保您符合設定 Azure 虛擬網路的所有[必要條件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="7c832-151">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="7c832-p113">具備包括 Active Directory 整合功能的 Office 365 訂閱。如需 Office 365 訂閱的相關資訊，請前往 [Office 365 訂閱頁面](https://products.office.com/compare-all-microsoft-office-products?tab=2)。</span><span class="sxs-lookup"><span data-stu-id="7c832-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="7c832-154">佈建一個執行 Azure AD Connect 的 Azure 虛擬機器，將您的內部部署 Windows Server AD 樹系與 Office 365 同步。</span><span class="sxs-lookup"><span data-stu-id="7c832-154">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="7c832-155">您必須具有 Windows Server AD 企業系統管理員帳戶和 Azure Active Directory 系統管理員帳戶的認證 (名稱和密碼)。</span><span class="sxs-lookup"><span data-stu-id="7c832-155">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="7c832-156">解決方案架構設計假設</span><span class="sxs-lookup"><span data-stu-id="7c832-156">Solution architecture design assumptions</span></span>

<span data-ttu-id="7c832-157">下列清單描述此解決方案所做的設計選擇。</span><span class="sxs-lookup"><span data-stu-id="7c832-157">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="7c832-p114">本解決方案使用具備站對站 VPN 連線的單一 Azure 虛擬網路。Azure 虛擬網路會裝載單一子網路，內含一部執行 Azure AD Connect 的目錄同步處理伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c832-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="7c832-160">在內部部署網路上會有網域控制站和 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c832-160">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="7c832-p115">Azure AD Connect 會執行密碼雜湊同步處理，而非單一登入。您不需要部署 Active Directory 同盟服務 (AD FS) 基礎結構。若要深入了解密碼雜湊同步處理與單一登入選項，請參閱＜[為您的 Azure Active Directory 混合式識別解決方案選擇正確的驗證方法](http://aka.ms/auth-options)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="7c832-p116">在您的環境中部署此解決方案時，您可能會考慮的其他設計選擇。其中包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="7c832-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="7c832-166">如果現有的 Azure 虛擬網路中有現有的 DNS 伺服器，請判斷您的目錄同步處理伺服器是否要使用它們 (而非使用內部部署網路的 DNS 伺服器) 來進行名稱解析。</span><span class="sxs-lookup"><span data-stu-id="7c832-166">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="7c832-p117">如果現有的 Azure 虛擬網路中有網域控制站，請判斷設定 Active Directory 網站及服務是否是較好的選擇。目錄同步處理伺服器可以將 Azure 虛擬網路的網域控制器排入佇列，來處理帳戶和密碼的變更，而非內部部署網路上的網域控制器。</span><span class="sxs-lookup"><span data-stu-id="7c832-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="7c832-169">部署藍圖</span><span class="sxs-lookup"><span data-stu-id="7c832-169">Deployment roadmap</span></span>

<span data-ttu-id="7c832-170">在 Azure 中的虛擬機器上部署 Azure AD Connect 由三個階段所組成：</span><span class="sxs-lookup"><span data-stu-id="7c832-170">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="7c832-171">階段 1：建立及設定 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="7c832-171">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="7c832-172">階段 2：建立及設定 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="7c832-172">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="7c832-173">階段 3：安裝及設定 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7c832-173">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="7c832-174">部署之後，您也必須在 Office 365 中指派位置和新的使用者帳戶的授權。</span><span class="sxs-lookup"><span data-stu-id="7c832-174">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="7c832-175">[Azure 部署套件中的目錄同步處理伺服器](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)包含建置這個解決方案的所有 Azure PowerShell 區塊、Microsoft PowerPoint 和 Visio 格式的圖表，以及 Microsoft Excel 設定活頁簿，會產生針對您設定所自訂的 Azure PowerShell 命令區塊。</span><span class="sxs-lookup"><span data-stu-id="7c832-175">The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="7c832-176">階段 1：建立及設定 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="7c832-176">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="7c832-177">若要建立及設定 Azure 虛擬網路，請完成＜[使內部部署網路與 Microsoft Azure 虛擬網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)＞中的＜[階段 1：準備內部部署網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network)＞和＜[階段 2：在 Azure 中建立跨單位的虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-177">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="7c832-178">這是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="7c832-178">This is your resulting configuration.</span></span>
  
![裝載於 Azure 中 Office 365 目錄同步處理伺服器的階段 1](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="7c832-180">本圖顯示使用站對站 VPN 或 ExpressRoute 連線方式，連線到 Azure 虛擬網路的內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="7c832-180">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="7c832-181">階段 2：建立及設定 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="7c832-181">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="7c832-p118">使用＜[在 Azure 入口網站中建立第一個 Windows 虛擬機器](https://go.microsoft.com/fwlink/p/?LinkId=393098)＞中的指示，在 Azure 中建立虛擬機器。使用下列設定：</span><span class="sxs-lookup"><span data-stu-id="7c832-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="7c832-p119">在 [基本概念]\*\*\*\* 窗格中，選取相同的訂閱、位置及資源群組做為您的虛擬網路，並在安全位置記錄使用者名稱和密碼。您稍後連線到虛擬機器時會需要這些資訊。</span><span class="sxs-lookup"><span data-stu-id="7c832-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="7c832-187">在 [選擇大小]\*\*\*\* 窗格中，選擇 [A2 標準]\*\*\*\* 大小。</span><span class="sxs-lookup"><span data-stu-id="7c832-187">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="7c832-p120">在 [設定]\*\*\*\* 窗格中，請在 [儲存體]\*\*\*\* 區段中，選取 [標準]\*\*\*\* 儲存體類型。在 [網路]\*\*\*\* 區段中，選取您裝載目錄同步處理伺服器 (不是閘道子網路) 的虛擬網路和子網路名稱。其他所有設定都保留預設值。</span><span class="sxs-lookup"><span data-stu-id="7c832-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="7c832-191">驗證目錄同步處理伺服器正確使用 DNS，檢查內部 DNS 以確定已使用其 IP 位址，新增虛擬機器的位址 (A) 記錄。</span><span class="sxs-lookup"><span data-stu-id="7c832-191">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="7c832-p121">使用＜[連線到虛擬機器並且登入](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)＞中的指示，使用遠端桌面連線以連線到目錄同步處理伺服器。登入之後，將虛擬機器加入到內部部署 Windows Server AD 網域。</span><span class="sxs-lookup"><span data-stu-id="7c832-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="7c832-p122">若要讓 Azure AD Connect 取得存取網際網路資源的權限，您必須設定目錄同步處理伺服器來使用內部部署網路的 Proxy 伺服器。您應該連絡您的網路系統管理員，以取得需要執行的其他設定步驟。</span><span class="sxs-lookup"><span data-stu-id="7c832-p122">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="7c832-196">這是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="7c832-196">This is your resulting configuration.</span></span>
  
![裝載於 Azure 中 Office 365 目錄同步處理伺服器的階段 2](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="7c832-198">本圖顯示在跨部署 Azure 虛擬網路中的目錄同步處理伺服器虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="7c832-198">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="7c832-199">階段 3：安裝及設定 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7c832-199">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="7c832-200">完成下列程序：</span><span class="sxs-lookup"><span data-stu-id="7c832-200">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="7c832-p123">透過具有本機系統管理員權限的 Windows Server AD 網域帳戶使用遠端桌面連線，連線到目錄同步處理伺服器。請參閱＜[連線到虛擬機器並且登入](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)＞。</span><span class="sxs-lookup"><span data-stu-id="7c832-p123">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="7c832-203">從目錄同步處理伺服器，開啟＜[在 Office 365 中設定目錄同步處理](set-up-directory-synchronization.md)＞一文，然後遵循目錄同步處理與密碼雜湊同步處理的指示。</span><span class="sxs-lookup"><span data-stu-id="7c832-203">From the directory sync server, open the [Set up directory synchronization in Office 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="7c832-p124">安裝程式會在本機使用者組織單位 (OU) 中建立 **AAD_xxxxxxxxxxxx** 帳戶。請勿移動或移除此帳戶，否則同步處理將會失敗。</span><span class="sxs-lookup"><span data-stu-id="7c832-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="7c832-206">這是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="7c832-206">This is your resulting configuration.</span></span>
  
![裝載於 Azure 中 Office 365 目錄同步處理伺服器的階段 3](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="7c832-208">本圖顯示在跨部署 Azure 虛擬網路中的 Azure AD Connect 目錄同步處理伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c832-208">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="7c832-209">在 Office 365 中指派位置及授權給使用者</span><span class="sxs-lookup"><span data-stu-id="7c832-209">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="7c832-p125">Azure AD Connect 會從內部部署 Windows Server AD 新增帳戶至您的 Office 365 訂閱，但為了讓使用者登入 Office 365 並使用其服務，帳戶必須已設定位置及授權。若要新增位置，並啟用適當的使用者帳戶的授權，請執行下列步驟︰</span><span class="sxs-lookup"><span data-stu-id="7c832-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="7c832-212">登入 [Office 365 入口網站頁面](https://portal.office.com)，然後按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c832-212">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="7c832-213">在左方的瀏覽區域中，按一下 [使用者] > [作用中的使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c832-213">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="7c832-214">在使用者帳戶清單中，選取您要啟動使用者旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7c832-214">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="7c832-215">在使用者的頁面上，按一下 [產品授權]\*\*\*\* 的 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c832-215">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="7c832-216">在 [產品授權]\*\*\*\* 頁面上，為**位置**的使用者選取一個位置，然後啟用適用的適當授權。</span><span class="sxs-lookup"><span data-stu-id="7c832-216">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="7c832-217">完成時，按一下 [儲存]\*\*\*\*，然後按兩下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c832-217">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="7c832-218">針對其他使用者請回到步驟 3。</span><span class="sxs-lookup"><span data-stu-id="7c832-218">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7c832-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c832-219">See Also</span></span>

[<span data-ttu-id="7c832-220">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="7c832-220">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="7c832-221">使內部部署網路與 Microsoft Azure 虛擬網路連線</span><span class="sxs-lookup"><span data-stu-id="7c832-221">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="7c832-222">下載 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7c832-222">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="7c832-223">設定 Office 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="7c832-223">Set up directory synchronization for Office 365</span></span>](set-up-directory-synchronization.md)
  
[<span data-ttu-id="7c832-224">Azure 部署套件中的目錄同步處理伺服器</span><span class="sxs-lookup"><span data-stu-id="7c832-224">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



