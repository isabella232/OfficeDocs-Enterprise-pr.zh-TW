---
title: Azure 中的 Office 365 高可用性同盟驗證
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 摘要：在 Microsoft Azure 中設定 Office 365 訂用帳戶的高可用性同盟驗證。
ms.openlocfilehash: 9ab2cf992a0170e8b6528c74c868f0db5feeb6e1
ms.sourcegitcommit: e334616f1b357365b380990eda63f6e63d52ec5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2018
ms.locfileid: "26024655"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="a5dba-103">Azure 中的 Office 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="a5dba-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="a5dba-104">**摘要：** 在 Microsoft Azure 中設定 Office 365 訂用帳戶的高可用性同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="a5dba-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="a5dba-105">本文包含的逐步指示，說明如何使用這些虛擬機器在 Azure 基礎結構服務中的 Microsoft Office 365 部署高可用性聯盟的驗證：</span><span class="sxs-lookup"><span data-stu-id="a5dba-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="a5dba-106">兩個 Web 應用程式 Proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="a5dba-107">兩個 Active Directory Federation Services (AD FS) 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="a5dba-108">兩個複本網域控制站</span><span class="sxs-lookup"><span data-stu-id="a5dba-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="a5dba-109">執行 Azure AD Connect 的同步處理 (DirSync) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a5dba-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="a5dba-110">組態如下，包含每部伺服器的預留位置名稱。</span><span class="sxs-lookup"><span data-stu-id="a5dba-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="a5dba-111">**Azure 中適用於 Office 365 基礎結構的高可用性同盟驗證**</span><span class="sxs-lookup"><span data-stu-id="a5dba-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 同盟驗證基礎結構的最後設定](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="a5dba-113">所有虛擬機器位於單一跨單位 Azure 虛擬網路中 (VNet)。</span><span class="sxs-lookup"><span data-stu-id="a5dba-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="a5dba-p101">個別使用者的聯盟驗證不會仰賴任何內部部署資源。不過，如果跨單位連線無法使用，VNet 中的網域控制站就不會收到使用者帳戶和群組在內部部署 Windows Server AD 中的更新。若要確保不會發生這個情況，您可以設定跨場所連線的高可用性。如需詳細資訊，請參閱＜[高度可用的跨單位和 VNet-VNet 連線](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)＞。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="a5dba-118">特定角色的每個虛擬機器配對都是位於它自己的子網路和可用性設定組中。</span><span class="sxs-lookup"><span data-stu-id="a5dba-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a5dba-p102">因為此 VNet 會連線到內部部署網路，所以此組態不包含管理子網路上的 Jumpbox 或監視虛擬機器。如需詳細資訊，請參閱＜[執行 N 層架構的 Windows VM](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)＞。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="a5dba-p103">這項設定的結果是，您所有的 Office 365 使用者都將會有聯盟驗證，他們可以在其中使用其 Windows 伺服器 Active Directory 憑證，而不是其 Office 365 帳戶登入。聯盟驗證基礎結構會使用一組多餘的伺服器，能更輕鬆部署在 Azure 基礎結構服務而不是內部部署邊緣網路中。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="a5dba-123">物料單</span><span class="sxs-lookup"><span data-stu-id="a5dba-123">Bill of materials</span></span>

<span data-ttu-id="a5dba-124">此基準組態需要下列 Azure 服務和元件集合：</span><span class="sxs-lookup"><span data-stu-id="a5dba-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="a5dba-125">九部虛擬機器</span><span class="sxs-lookup"><span data-stu-id="a5dba-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="a5dba-126">具有四個子網路的一個跨單位虛擬網路</span><span class="sxs-lookup"><span data-stu-id="a5dba-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="a5dba-127">四個資源群組</span><span class="sxs-lookup"><span data-stu-id="a5dba-127">Four resource groups</span></span>
    
- <span data-ttu-id="a5dba-128">三個可用性設定組</span><span class="sxs-lookup"><span data-stu-id="a5dba-128">Three availability sets</span></span>
    
- <span data-ttu-id="a5dba-129">一個 Azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="a5dba-129">One Azure subscription</span></span>
    
<span data-ttu-id="a5dba-130">以下是此組態的虛擬機器與其預設大小。</span><span class="sxs-lookup"><span data-stu-id="a5dba-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="a5dba-131">**項目**</span><span class="sxs-lookup"><span data-stu-id="a5dba-131">**Item**</span></span>|<span data-ttu-id="a5dba-132">**虛擬機器描述**</span><span class="sxs-lookup"><span data-stu-id="a5dba-132">**Virtual machine description**</span></span>|<span data-ttu-id="a5dba-133">**Azure 圖庫影像**</span><span class="sxs-lookup"><span data-stu-id="a5dba-133">**Azure gallery image**</span></span>|<span data-ttu-id="a5dba-134">**預設大小**</span><span class="sxs-lookup"><span data-stu-id="a5dba-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a5dba-135">1.</span><span class="sxs-lookup"><span data-stu-id="a5dba-135">1.</span></span>  <br/> |<span data-ttu-id="a5dba-136">第一個網域控制站</span><span class="sxs-lookup"><span data-stu-id="a5dba-136">First domain controller</span></span>  <br/> |<span data-ttu-id="a5dba-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-138">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-138">D2</span></span>  <br/> |
|<span data-ttu-id="a5dba-139">2.</span><span class="sxs-lookup"><span data-stu-id="a5dba-139">2.</span></span>  <br/> |<span data-ttu-id="a5dba-140">第二個網域控制站</span><span class="sxs-lookup"><span data-stu-id="a5dba-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="a5dba-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-142">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-142">D2</span></span>  <br/> |
|<span data-ttu-id="a5dba-143">3.</span><span class="sxs-lookup"><span data-stu-id="a5dba-143">3.</span></span>  <br/> |<span data-ttu-id="a5dba-144">Azure AD Connect 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="a5dba-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-146">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-146">D2</span></span>  <br/> |
|<span data-ttu-id="a5dba-147">4.</span><span class="sxs-lookup"><span data-stu-id="a5dba-147">4.</span></span>  <br/> |<span data-ttu-id="a5dba-148">第一個 AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="a5dba-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-150">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-150">D2</span></span>  <br/> |
|<span data-ttu-id="a5dba-151">5.</span><span class="sxs-lookup"><span data-stu-id="a5dba-151">5.</span></span>  <br/> |<span data-ttu-id="a5dba-152">第二個 AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="a5dba-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-154">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-154">D2</span></span>  <br/> |
|<span data-ttu-id="a5dba-155">6.</span><span class="sxs-lookup"><span data-stu-id="a5dba-155">6.</span></span>  <br/> |<span data-ttu-id="a5dba-156">第一個 Web 應用程式 Proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="a5dba-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-158">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-158">D2</span></span>  <br/> |
|<span data-ttu-id="a5dba-159">7.</span><span class="sxs-lookup"><span data-stu-id="a5dba-159">7.</span></span>  <br/> |<span data-ttu-id="a5dba-160">第二個 Web 應用程式 Proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="a5dba-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="a5dba-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a5dba-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a5dba-162">D2</span><span class="sxs-lookup"><span data-stu-id="a5dba-162">D2</span></span>  <br/> |
   
<span data-ttu-id="a5dba-163">若要計算此組態的估計成本，請參閱 [Azure 價格計算機](https://azure.microsoft.com/pricing/calculator/)</span><span class="sxs-lookup"><span data-stu-id="a5dba-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="a5dba-164">部署階段</span><span class="sxs-lookup"><span data-stu-id="a5dba-164">Phases of deployment</span></span>

<span data-ttu-id="a5dba-165">您可以在下列階段部署此工作負載：</span><span class="sxs-lookup"><span data-stu-id="a5dba-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="a5dba-p104">[階段 1：設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。建立資源群組、儲存體帳戶、可用性設定組和跨單位虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="a5dba-p105">[階段 2：設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。建立和設定複本 Windows Server Active Directory (AD) 網域控制站和 DirSync 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="a5dba-p106">[階段 3：設定 AD FS 伺服器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。建立並設定兩個 AD FS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="a5dba-p107">[階段 4：設定 Web 應用程式 Proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。建立並設定兩個 Web 應用程式 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="a5dba-p108">[階段 5：設定 Office 365 同盟的驗證](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。設定 Office 365 訂用帳戶的聯盟驗證。</span><span class="sxs-lookup"><span data-stu-id="a5dba-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="a5dba-p109">這些文章是預先定義之架構的引導式、階段式指引，用以在 Azure 基礎結構服務中建立功能性、高可用性的 Office 365 聯盟驗證。請記住下列事項：</span><span class="sxs-lookup"><span data-stu-id="a5dba-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="a5dba-178">如果您是有經驗的 AD FS 實作者，請自行適應階段 3 至 4 中的指示，並建置最符合您需求的伺服器組。</span><span class="sxs-lookup"><span data-stu-id="a5dba-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="a5dba-179">如果您已擁有的現有 Azure 混合式雲端部署具有現有跨單位虛擬網路，請依需要調整或略過階段 1 和 2 中的指示，並將 AD FS 和 Web 應用程式 Proxy 伺服器置於適當的子網路中。</span><span class="sxs-lookup"><span data-stu-id="a5dba-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="a5dba-180">若要建置此組態的開發/測試環境或概念證明，請參閱＜[Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a5dba-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="a5dba-181">下一步</span><span class="sxs-lookup"><span data-stu-id="a5dba-181">Next step</span></span>

<span data-ttu-id="a5dba-182">使用＜[高可用性同盟驗證階段 1：設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)＞開始設定此工作負載。</span><span class="sxs-lookup"><span data-stu-id="a5dba-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="a5dba-183">如需更快速地在 Azure 中部署您 Office 365 的高可用性聯盟驗證檔案集合，請參閱＜[Azure 部署套件中的 Office 365 聯盟驗證](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)＞。</span><span class="sxs-lookup"><span data-stu-id="a5dba-183">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
 

