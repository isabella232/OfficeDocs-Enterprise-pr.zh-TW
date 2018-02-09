---
title: "在 Microsoft Azure 中部署 Office 365 目錄同步作業 (DirSync)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: "摘要： 在同步處理您的內部部署目錄與 Office 365 訂閱的 Azure AD 租用戶之間的帳戶的 Azure 虛擬機器上部署 Azure AD Connect (DirSync)。"
ms.openlocfilehash: 496dca01d8478c693cb983adefe9e663d2285279
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure"></a><span data-ttu-id="6f430-103">在 Microsoft Azure 中部署 Office 365 目錄同步作業 (DirSync)</span><span class="sxs-lookup"><span data-stu-id="6f430-103">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>

 <span data-ttu-id="6f430-104">**摘要：**若要同步處理您的內部部署目錄與 Office 365 訂閱的 Azure AD 租用戶之間的帳戶 Azure 中的虛擬機器上部署 Azure AD Connect (DirSync)。</span><span class="sxs-lookup"><span data-stu-id="6f430-104">**Summary:** Deploy Azure AD Connect (DirSync) on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="6f430-p101">Azure Active Directory (AD) 連線 （前身為目錄同步作業工具、 目錄同步作業工具或 DirSync.exe 工具） 已加入網域的伺服器安裝的伺服器型應用程式同步處理您的內部 Windows 伺服器Active Directory 使用者至 Office 365 訂閱的 Azure Active Directory 租用戶。您可以安裝 Azure AD 連接內部部署伺服器上，但您也可以安裝它在 Azure 虛擬機器上的原因如下：</span><span class="sxs-lookup"><span data-stu-id="6f430-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="6f430-107">您可以更快速地佈建和設定雲端架構伺服器，以便讓您的使用者可以更早使用服務。</span><span class="sxs-lookup"><span data-stu-id="6f430-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="6f430-108">Azure 提供以較少的改善網站可用性。</span><span class="sxs-lookup"><span data-stu-id="6f430-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="6f430-109">您可以減少組織中的內部部署伺服器數目。</span><span class="sxs-lookup"><span data-stu-id="6f430-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="6f430-p102">此解決方案所需的內部網路與 Azure 虛擬網路之間的連線。如需詳細資訊，請參閱[Microsoft Azure 虛擬網路的內部網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="6f430-p103">本文說明在單一樹系中的單一網域的同步處理。Azure AD 連線同步與 Office 365 的 Active Directory 樹系中所有的 Windows Server AD 網域。如果您有多個 Active Directory 樹系同步處理與 Office 365，請參閱[使用單一登入案例的多樹系目錄同步處理](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="6f430-p104">Office 365 使用 Azure Active Directory (Azure AD) 及其目錄服務。您的 Office 365 訂閱包括 Azure AD 租用戶。此租用戶也用於您組織的身分識別與其他雲端工作量，包括在 Azure 中的其他 saas 和應用程式和應用程式的管理。</span><span class="sxs-lookup"><span data-stu-id="6f430-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="6f430-118">在 Azure 中部署 Office 365 目錄同步作業的概觀 </span><span class="sxs-lookup"><span data-stu-id="6f430-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="6f430-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="6f430-119"></span></span>

<span data-ttu-id="6f430-120">下圖顯示在 Azure (DirSync server) 同步處理至 anOffice 365 訂閱內部部署 Windows Server AD 樹系中的虛擬機器上執行的 Azure AD 連線。</span><span class="sxs-lookup"><span data-stu-id="6f430-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the DirSync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Azure 同步處理內部部署帳戶中虛擬機器上的 Azure AD Connect 工具，至具有流量之 Office 365 訂閱的 Azure AD 租用戶](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="6f430-p105">在圖表中，有兩個連接至網站 VPN 或 ExpressRoute 連接所連接的網路。沒有其中 Windows Server AD 網域控制站，且沒有 DirSync 伺服器，這是在虛擬機器與 Azure 虛擬網路的內部網路執行[Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)。有兩個主要的流量流程源自 DirSync 伺服器：</span><span class="sxs-lookup"><span data-stu-id="6f430-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a DirSync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the DirSync server:</span></span>
  
-  <span data-ttu-id="6f430-125">Azure AD Connect 將內部部署網路上的網域控制器排入佇列，來處理帳戶和密碼的變更。</span><span class="sxs-lookup"><span data-stu-id="6f430-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="6f430-p106">Azure AD 連線將變更傳送至帳戶及密碼到您的 Office 365 訂閱 Azure AD 執行個體。由於 DirSync 伺服器是在您的內部網路延伸部分，透過內部網路的 proxy 伺服器傳送這些變更。</span><span class="sxs-lookup"><span data-stu-id="6f430-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the DirSync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="6f430-p107">此解決方案說明單一 Active Directory 網域的單一 Active Directory 樹系中的同步處理。Azure AD 連線同步與 Office 365 的 Active Directory 樹系中所有的 Active Directory 網域。如果您有多個 Active Directory 樹系同步處理與 Office 365，請參閱[使用單一登入案例的多樹系目錄同步處理](https://go.microsoft.com/fwlink/p/?LinkId=393091)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="6f430-p108">在這兩種情況下，源自由 Azure 虛擬機器上執行的 Azure AD 連線的流量會轉接至閘道在 Azure，然後將流量轉送跨網站 VPN 或 ExpressRoute 連線 VPN 閘道裝置的虛擬網路上在內部網路。在內部網路的路由基礎結構然後轉寄才到達目的地，例如在網域控制站或 proxy 伺服器的流量。</span><span class="sxs-lookup"><span data-stu-id="6f430-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="6f430-133">部署此解決方案有兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="6f430-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="6f430-p109">建立 Azure 虛擬網路，並建立網站 VPN 連線至您的內部網路。如需詳細資訊，請參閱[Microsoft Azure 虛擬網路的內部網路連線](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="6f430-p110">[Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)已加入網域的虛擬機器上安裝在 Azure，並同步處理至 Office 365 內部部署 Windows Server AD。這包括：</span><span class="sxs-lookup"><span data-stu-id="6f430-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="6f430-138">建立執行 Azure AD Connect Azure 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="6f430-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="6f430-139">安裝及設定[Azure AD 連線](https://www.microsoft.com/download/details.aspx?id=47594)。</span><span class="sxs-lookup"><span data-stu-id="6f430-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="6f430-p111">設定 Azure AD 連線需要 Azure AD 管理員帳戶及 Windows Server AD 企業系統管理員帳戶的認證 （使用者名稱和密碼）。Azure AD 連線執行立即並持續供同步處理至 Office 365 的內部部署 Windows Server AD 樹系。</span><span class="sxs-lookup"><span data-stu-id="6f430-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="6f430-142">您此解決方案在生產環境中的部署之前，請使用[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示以這種組態設定概念證明、 試驗或的示範。</span><span class="sxs-lookup"><span data-stu-id="6f430-142">Before you deploy this solution in production, use the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="6f430-143">當 Azure AD Connect 組態完成時，它不會儲存 Windows Server AD 企業系統管理員帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="6f430-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="6f430-p112">此解決方案說明同步處理至 Office 365 的單一 Windows Server AD 樹系。本文所討論的拓撲代表只有一個方法可以實作此解決方案。貴組織的拓撲可能會根據您唯一的網路需求及安全性考量而有所不同。</span><span class="sxs-lookup"><span data-stu-id="6f430-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-dirsync-server-for-office-365-in-azure"></a><span data-ttu-id="6f430-147">Azure 中 Office 365 DirSync 伺服器的主控方案</span><span class="sxs-lookup"><span data-stu-id="6f430-147">Plan for hosting a DirSync server for Office 365 in Azure</span></span>
<span data-ttu-id="6f430-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="6f430-148"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="6f430-149">必要條件</span><span class="sxs-lookup"><span data-stu-id="6f430-149">Prerequisites</span></span>

<span data-ttu-id="6f430-150">開始之前，請先檢閱本解決方案的下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="6f430-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="6f430-151">檢閱中[規劃 Azure 虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)的相關規劃內容。</span><span class="sxs-lookup"><span data-stu-id="6f430-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="6f430-152">請確定您符合設定 Azure 虛擬網路的所有[必要軟體](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="6f430-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="6f430-p113">具有 Office 365 訂閱包括 Active Directory 的整合功能。如需 Office 365 訂閱，移至[Office 365 訂閱 」 頁面](https://go.microsoft.com/fwlink/p/?LinkId=394278)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="6f430-155">佈建執行 Azure AD 連線至與 Office 365 同步處理內部部署 Windows Server AD 樹系的一個 Azure 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="6f430-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="6f430-156">您必須在 Windows Server AD 企業系統管理員帳戶和 Azure Active Directory 管理員帳戶的認證 （名稱與密碼）。</span><span class="sxs-lookup"><span data-stu-id="6f430-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="6f430-157">解決方案架構設計假設</span><span class="sxs-lookup"><span data-stu-id="6f430-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="6f430-158">下列清單描述此解決方案所做的設計選擇。</span><span class="sxs-lookup"><span data-stu-id="6f430-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="6f430-p114">此解決方案使用單一 Azure 虛擬網路與網站 VPN 連線的情況。Azure 虛擬網路主控包含一部伺服器的單一子網路、 目錄同步伺服器執行 Azure AD 連線。</span><span class="sxs-lookup"><span data-stu-id="6f430-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the DirSync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="6f430-161">在內部部署網路上會有網域控制站 和 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6f430-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="6f430-p115">Azure AD 連線執行而不是單一登入的密碼同步處理。您沒有部署 Active Directory Federation Services (AD FS) 基礎結構。若要深入了解密碼同步處理與單一登入選項，請參閱[決定要使用哪些目錄整合案例](https://go.microsoft.com/fwlink/p/?LinkId=393094)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p115">Azure AD Connect performs password synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password synchronization and single sign-on options, see [Determine which directory integration scenario to use](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span></span>
    
<span data-ttu-id="6f430-p116">在您的環境中部署此解決方案時，您可能會考慮的其他設計選擇。其中包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="6f430-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="6f430-167">如果那里現有的 DNS 伺服器中的現有 Azure 虛擬網路，決定您是否要用於而不是在內部網路上的 DNS 伺服器的名稱解析您 DirSync 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6f430-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your DirSync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="6f430-p117">如果現有的 Azure 虛擬網路中有網域控制站，判斷是否設定 Active Directory 站台及服務可能會較佳的選項。DirSync 伺服器可以查詢中的帳戶和密碼，而不是在內部網路上的網域控制站中變更 Azure 虛擬網路網域控制站。</span><span class="sxs-lookup"><span data-stu-id="6f430-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The DirSync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="6f430-170">部署藍圖</span><span class="sxs-lookup"><span data-stu-id="6f430-170">Deployment roadmap</span></span>
<span data-ttu-id="6f430-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="6f430-171"></span></span>

<span data-ttu-id="6f430-172">部署在 Azure 虛擬機器上的 Azure AD 連接包含三個階段：</span><span class="sxs-lookup"><span data-stu-id="6f430-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="6f430-173">階段 1：建立及設定 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="6f430-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="6f430-174">階段 2：建立及設定 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="6f430-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="6f430-175">階段 3：安裝及設定 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="6f430-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="6f430-176">部署之後，您也必須在 Office 365 中指派位置和新的使用者帳戶的授權。</span><span class="sxs-lookup"><span data-stu-id="6f430-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="6f430-177">[DirSync Server Azure 部署套件中](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)包含所有的來取出此解決方案、 Microsoft PowerPoint 與 Visio 格式、 圖表及產生 Azure PowerShell 的 Microsoft Excel 設定活頁簿建立 Azure PowerShell 區塊針對您的設定自訂命令區塊。</span><span class="sxs-lookup"><span data-stu-id="6f430-177">The [DirSync Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="6f430-178">階段 1：建立及設定 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="6f430-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="6f430-179">若要建立及設定 Azure 虛擬網路，完成[階段 1： 準備您的內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1)和[階段 2： 在 Azure 中建立跨內部虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2)部署中的[藍圖連線至內部網路Microsoft Azure 虛擬網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="6f430-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="6f430-180">這是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="6f430-180">This is your resulting configuration.</span></span>
  
![裝載於 Azure 中 Office 365 目錄同步伺服器的階段 1](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="6f430-182">本圖顯示使用站台對站台 VPN 或 ExpressRoute 連線方式，連線到 Azure 虛擬網路的內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="6f430-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="6f430-183">階段 2：建立及設定 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="6f430-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="6f430-p118">在 Azure 中使用的指示[建立您第一部 Windows 的虛擬機器在 Azure 的入口網站中](https://go.microsoft.com/fwlink/p/?LinkId=393098)建立虛擬機器。使用下列設定：</span><span class="sxs-lookup"><span data-stu-id="6f430-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="6f430-p119">在 [**基礎**] 窗格中選取相同的訂閱、 位置及資源群組為虛擬網路。安全的位置記錄的使用者名稱和密碼。您將需要這些稍後來連線至虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="6f430-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="6f430-189">在 [**選擇大小**] 窗格中，選擇 [ **A2 標準**大小。</span><span class="sxs-lookup"><span data-stu-id="6f430-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="6f430-p120">在 [**設定**] 窗格中 [**儲存**] 區段中選取的**標準**儲存類型。在 [**網路**] 區段中選取主控 DirSync 伺服器 (不 GatewaySubnet) 虛擬網路和子網路的名稱。保留所有其他設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="6f430-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the DirSync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="6f430-193">驗證 DirSync 伺服器正確使用 DNS，檢查內部 DNS 以確定已使用其 IP 位址，新增虛擬機器的位址 (A) 記錄。 </span><span class="sxs-lookup"><span data-stu-id="6f430-193">Verify that your DirSync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="6f430-p121">使用中[連線至虛擬機器和登入](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)的指示來連線到遠端桌面連線使用 DirSync 伺服器。登入之後, 加入內部部署 Windows Server AD 網域中的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="6f430-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the DirSync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="6f430-p122">若要讓 Azure AD Connect 取得存取網際網路資源的權限，您必須設定 DirSync 伺服器來使用內部部署網路的 Proxy 伺服器。您應該連絡您的網路系統管理員，以取得需要執行的其他設定步驟。</span><span class="sxs-lookup"><span data-stu-id="6f430-p122">For Azure AD Connect to gain access to Internet resources, you must configure the DirSync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="6f430-198">這是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="6f430-198">This is your resulting configuration.</span></span>
  
![裝載於 Azure 中 Office 365 目錄同步伺服器的階段 2](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="6f430-200">本圖顯示在跨部署 Azure 虛擬網路中的 DirSync 伺服器虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="6f430-200">This figure shows the DirSync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="6f430-201">階段 3：安裝及設定 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="6f430-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="6f430-202">完成下列程序：</span><span class="sxs-lookup"><span data-stu-id="6f430-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="6f430-p123">連線至遠端桌面連線使用具有本機系統管理員權限的 Windows Server AD 網域帳戶 DirSync 伺服器。請參閱[連線至虛擬機器和登入](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="6f430-p123">Connect to the DirSync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="6f430-205">從 DirSync 伺服器上，開啟 [[設定 Office 365 中目錄同步作業](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)文章並遵循使用密碼同步處理的目錄同步作業的指示。</span><span class="sxs-lookup"><span data-stu-id="6f430-205">From the DirSync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="6f430-p124">安裝在本機使用者組織單位 (OU) 中建立**AAD_xxxxxxxxxxxx**帳戶。無法移動或移除此帳戶或同步處理將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6f430-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="6f430-208">這是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="6f430-208">This is your resulting configuration.</span></span>
  
![裝載於 Azure 中 Office 365 目錄同步伺服器的階段 3](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="6f430-210">本圖顯示在跨部署 Azure 虛擬網路中的 Azure AD Connect DirSync 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6f430-210">This figure shows the DirSync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="6f430-211">在 Office 365 中指派位置及授權給使用者</span><span class="sxs-lookup"><span data-stu-id="6f430-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="6f430-p125">Azure AD Connect 會從內部部署 Windows Server AD 新增帳戶至您的 Office 365 訂閱，但為了讓使用者登入 Office 365 並使用其服務，帳戶必須已設定位置及授權。若要新增位置，並啟用適當的使用者帳戶的授權，請執行下列步驟︰</span><span class="sxs-lookup"><span data-stu-id="6f430-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="6f430-214">登入[Office 365 入口網站頁面](https://portal.office.com)，並按一下 [**管理**。</span><span class="sxs-lookup"><span data-stu-id="6f430-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="6f430-215">在左導覽列中，按一下 [**使用者 > 作用中使用者**。</span><span class="sxs-lookup"><span data-stu-id="6f430-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="6f430-216">在使用者帳戶清單中，選取您要啟動使用者旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6f430-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="6f430-217">在 [使用者] 頁面上按一下 [**產品授權**的 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="6f430-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="6f430-218">在 [**產品授權**] 頁面上的**位置**，選取使用者的位置並啟用適當的授權使用者。</span><span class="sxs-lookup"><span data-stu-id="6f430-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="6f430-219">完成後，按一下 [**儲存**] 和 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="6f430-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="6f430-220">針對其他使用者請回到步驟 3。</span><span class="sxs-lookup"><span data-stu-id="6f430-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="6f430-221">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f430-221">See Also</span></span>

<span data-ttu-id="6f430-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="6f430-222"></span></span>

[<span data-ttu-id="6f430-223">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="6f430-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="6f430-224">在內部網路連線到 Microsoft Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="6f430-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="6f430-225">下載 Azure AD 連線</span><span class="sxs-lookup"><span data-stu-id="6f430-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="6f430-226">設定 Office 365 中目錄同步作業</span><span class="sxs-lookup"><span data-stu-id="6f430-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="6f430-227">DirSync 伺服器在 Azure 部署套件 （英文）</span><span class="sxs-lookup"><span data-stu-id="6f430-227">DirSync Server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



