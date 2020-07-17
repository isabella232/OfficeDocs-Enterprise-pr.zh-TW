---
title: 自動化 eDiscovery 的檔收集
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要：瞭解如何從使用者電腦自動化檔收集以進行 eDiscovery。
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997974"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="9d18d-103">自動化 eDiscovery 的檔收集</span><span class="sxs-lookup"><span data-stu-id="9d18d-103">Automate file collection for eDiscovery</span></span>

<span data-ttu-id="9d18d-104">所有公司都面臨訴訟或其他類型法律行動的潛力。</span><span class="sxs-lookup"><span data-stu-id="9d18d-104">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="9d18d-105">雖然法律部門可用於減少這種風險，但訴訟是指的是生命週期的事實。</span><span class="sxs-lookup"><span data-stu-id="9d18d-105">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="9d18d-106">當公司面臨法律行動時，必須透過法律查詢的程式，向法院和相反的法律顧問提供所有相關的單印刷材料。</span><span class="sxs-lookup"><span data-stu-id="9d18d-106">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="9d18d-107">eDiscovery 是指公司清查、搜尋、識別、保留、篩選，並提供電子形式的相關單印刷材料的程式。</span><span class="sxs-lookup"><span data-stu-id="9d18d-107">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="9d18d-108">SharePoint 2013、Exchange Server 2013、Lync Server 2013、SharePoint 線上和 Exchange Online 都可以保留大量的帶序內容。</span><span class="sxs-lookup"><span data-stu-id="9d18d-108">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="9d18d-109">視版本而定，這些產品可能支援 eDiscovery 和就地保留（Lync 透過 Exchange Server），讓法律團隊可更輕鬆地編制索引、識別、保留及篩選特定案例中最相關的內容。</span><span class="sxs-lookup"><span data-stu-id="9d18d-109">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="9d18d-110">許多檔都是儲存在使用者（保管人）本機電腦上，而不是集中位置。</span><span class="sxs-lookup"><span data-stu-id="9d18d-110">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="9d18d-111">這使 SharePoint 2013 無法進行搜尋，而且如果無法搜尋，便無法包含在 eDiscovery 中。</span><span class="sxs-lookup"><span data-stu-id="9d18d-111">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="9d18d-112">此解決方案顯示如何使用登入腳本（System Center Orchestrator 2012 R2 和 Windows PowerShell for Exchange Server），以自動化使用者電腦上的序材料識別及集合。</span><span class="sxs-lookup"><span data-stu-id="9d18d-112">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="9d18d-113">此解決方案的用途</span><span class="sxs-lookup"><span data-stu-id="9d18d-113">What this solution does</span></span>

<span data-ttu-id="9d18d-114">此解決方案使用通用安全性群組、群組原則和 Windows PowerShell 腳本，以在使用者本機電腦上尋找、清查及收集內容和 Outlook 個人存放區（PST）檔案至隱藏的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-114">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="9d18d-115">在此，PST 檔案可匯入至 Exchange Server 2013 或 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="9d18d-115">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="9d18d-116">然後，使用 System Center Orchestrator 2012 R2 runbook 將所有檔案移至 Microsoft Azure 中的另一個檔案共用，以進行長期儲存，並 SharePoint 2013 來編制索引。</span><span class="sxs-lookup"><span data-stu-id="9d18d-116">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="9d18d-117">然後，您可以使用內部部署 SharePoint 2013 部署中的 eDiscovery 中心，或是您定期執行 eDiscovery 的 SharePoint 線上。</span><span class="sxs-lookup"><span data-stu-id="9d18d-117">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="9d18d-118">此解決方案使用 robocopy，將檔案從保管人的電腦複製到集中的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-118">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="9d18d-119">因為 robocopy 不會複製開啟或鎖定的檔案，所以不會收集保管人已開啟的任何檔案（包括 PST 檔案）。</span><span class="sxs-lookup"><span data-stu-id="9d18d-119">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="9d18d-120">您必須手動收集這些檔案。</span><span class="sxs-lookup"><span data-stu-id="9d18d-120">You will have to collect them manually.</span></span> <span data-ttu-id="9d18d-121">此方案為您提供清單，明確識別出它無法複製的檔案，以及每個檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9d18d-121">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="9d18d-122">下列圖表會逐步引導您完成解決方案的所有步驟和元素。</span><span class="sxs-lookup"><span data-stu-id="9d18d-122">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![自動化檔案收集解決方案的概觀](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="9d18d-124">圖例 \* \* \* \*</span><span class="sxs-lookup"><span data-stu-id="9d18d-124">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![洋紅色圖說文字 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="9d18d-126">建立群組原則物件（GPO），並將它與集合登入腳本建立關聯。</span><span class="sxs-lookup"><span data-stu-id="9d18d-126">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![洋紅色圖說文字 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="9d18d-128">設定 GPO 安全性篩選器，只將 GPO 套用至保管人群組。</span><span class="sxs-lookup"><span data-stu-id="9d18d-128">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![洋紅色圖說文字 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="9d18d-130">保管人會登入，然後 GPO 即會執行，呼叫集合登入腳本。</span><span class="sxs-lookup"><span data-stu-id="9d18d-130">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![洋紅色圖說文字 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="9d18d-132">集合登入腳本會清查保管人電腦上所有在本機上附加的磁片磁碟機、搜尋您想要的檔案，並記錄其位置。</span><span class="sxs-lookup"><span data-stu-id="9d18d-132">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![洋紅色圖說文字 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="9d18d-134">集合登入腳本會將清查過的檔案複製到暫存伺服器上的隱藏檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-134">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![洋紅色圖說文字 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="9d18d-136">（選項 A）手動執行 PST 匯入腳本，將收集的 PST 檔案匯入 Exchange Server 2013。</span><span class="sxs-lookup"><span data-stu-id="9d18d-136">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![洋紅色圖說文字 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="9d18d-138">（選項 B）使用 Microsoft 365 Import 工具和進程，將收集的 PST 檔案匯入 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="9d18d-138">(Option B) Using the Microsoft 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![洋紅色圖說文字 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="9d18d-140">使用 MoveToColdStorage System Center Orchestrator 2012 R2 runbook，將所有收集的檔案移至 Azure 檔案共用，以進行長期儲存體存放。</span><span class="sxs-lookup"><span data-stu-id="9d18d-140">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![洋紅色圖說文字 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="9d18d-142">使用 SharePoint 2013，為 cold 儲存檔共用中的檔案編制索引。</span><span class="sxs-lookup"><span data-stu-id="9d18d-142">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![洋紅色圖說文字 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="9d18d-144">對冷存放區中的內容及內部部署 Exchange Server 2013 執行 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="9d18d-144">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![洋紅色圖說文字 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="9d18d-146">在 Microsoft 365 的內容中執行 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="9d18d-146">Perform eDiscovery on content in Microsoft 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="9d18d-147">必要條件</span><span class="sxs-lookup"><span data-stu-id="9d18d-147">Prerequisites</span></span>

<span data-ttu-id="9d18d-148">設定此解決方案時，需要許多元素，多數是您在考慮 eDiscovery 時可能已就緒並加以設定。</span><span class="sxs-lookup"><span data-stu-id="9d18d-148">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="9d18d-149">針對您可能不需要特定設定的元素，我們會為您提供您要組建基本設定的連結。</span><span class="sxs-lookup"><span data-stu-id="9d18d-149">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="9d18d-150">您必須先就地設定基本設定，才能設定解決方案本身。</span><span class="sxs-lookup"><span data-stu-id="9d18d-150">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="9d18d-151">基本設定</span><span class="sxs-lookup"><span data-stu-id="9d18d-151">Base configuration</span></span>

|<span data-ttu-id="9d18d-152">**元素**</span><span class="sxs-lookup"><span data-stu-id="9d18d-152">**Element**</span></span>|<span data-ttu-id="9d18d-153">**連結**</span><span class="sxs-lookup"><span data-stu-id="9d18d-153">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9d18d-154">Active Directory 網域服務（AD DS）網域</span><span class="sxs-lookup"><span data-stu-id="9d18d-154">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="9d18d-155">從您的內部部署網路的網際網路連線能力</span><span class="sxs-lookup"><span data-stu-id="9d18d-155">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="9d18d-156">SQL Server 2012 可支援 SharePoint 2013 和 System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d18d-156">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="9d18d-157">部署 System Center Orchestrator-2012</span><span class="sxs-lookup"><span data-stu-id="9d18d-157">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="9d18d-158">電子檔探索的內部部署或 Azure SharePoint 2013 （選項 A 所需）</span><span class="sxs-lookup"><span data-stu-id="9d18d-158">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="9d18d-159">用於暫存的內部部署檔案共用伺服器</span><span class="sxs-lookup"><span data-stu-id="9d18d-159">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="9d18d-160">內部部署 Exchange Server 2013 用於選項 PST 匯入</span><span class="sxs-lookup"><span data-stu-id="9d18d-160">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="9d18d-161">CU5 （15.913.22）可從[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)取得。</span><span class="sxs-lookup"><span data-stu-id="9d18d-161">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="9d18d-162">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d18d-162">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="9d18d-163">部署 System Center Orchestrator-2012</span><span class="sxs-lookup"><span data-stu-id="9d18d-163">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="9d18d-164">Microsoft 365 E3 搭配 Exchange Online 和 SharePoint 線上（選項 B 所需）</span><span class="sxs-lookup"><span data-stu-id="9d18d-164">Microsoft 365 E3 with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="9d18d-165">若要註冊 Microsoft 365 E3 訂閱，請參閱[microsoft 365 e3 訂閱](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-165">To sign up for a Microsoft 365 E3 subscription, see [Microsoft 365 E3 subscription](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab).</span></span>  <br/> |
|<span data-ttu-id="9d18d-166">使用虛擬機器的 Azure 訂閱</span><span class="sxs-lookup"><span data-stu-id="9d18d-166">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="9d18d-167">若要註冊 Azure，請參閱[訂閱 Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="9d18d-167">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="9d18d-168">您的內部部署網路與您的 Azure 訂閱之間的 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="9d18d-168">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="9d18d-169">若要在您的 Azure 訂閱和內部部署網路之間設定 VPN 隧道，請參閱[Connect a 內部部署網路與 Microsoft Azure 虛擬網路](https://go.microsoft.com/fwlink/p/?LinkId=613507)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-169">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="9d18d-170">SharePoint 2013 eDiscovery 設定為跨 SharePoint 和 Exchange Server 2013 和選擇性的 Lync Server 2013 進行搜尋</span><span class="sxs-lookup"><span data-stu-id="9d18d-170">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="9d18d-171">若要以這種方式設定 eDiscovery，請參閱[Configure ediscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508)及[Test Lab Guide： configure Ediscovery for a Exchange，Lync，SharePoint 與 Windows 檔案共用測試實驗室](https://go.microsoft.com/fwlink/p/?LinkId=393130)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-171">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="9d18d-172">Microsoft 365 中的 eDiscovery，供 SharePoint 線上和 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9d18d-172">eDiscovery in Microsoft 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="9d18d-173">若要在 Microsoft 365 中設定 eDiscovery，請參閱[在 SharePoint Online 中設定 Ediscovery 中心](https://go.microsoft.com/fwlink/p/?LinkId=613628)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-173">To configure eDiscovery in Microsoft 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="9d18d-174">設定環境</span><span class="sxs-lookup"><span data-stu-id="9d18d-174">Configure the environment</span></span>

<span data-ttu-id="9d18d-175">現在，您已準備好基本設定，您可以向前移動以設定解決方案本身。</span><span class="sxs-lookup"><span data-stu-id="9d18d-175">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="9d18d-176">暫存檔共用</span><span class="sxs-lookup"><span data-stu-id="9d18d-176">Staging file share</span></span>

1. <span data-ttu-id="9d18d-177">在內部部署網域中，建立名為保管人的全域安全性群組。</span><span class="sxs-lookup"><span data-stu-id="9d18d-177">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="9d18d-178">為從保管人電腦收集的檔案建立隱藏的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-178">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="9d18d-179">這應該是在內部部署伺服器上。</span><span class="sxs-lookup"><span data-stu-id="9d18d-179">This should be on an on-premises server.</span></span> <span data-ttu-id="9d18d-180">例如，在名為「暫存」的伺服器上，建立名為案例 $ 的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-180">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="9d18d-181">**$** 需要將此共用設為隱藏共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-181">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="9d18d-182">設定下列共用許可權：</span><span class="sxs-lookup"><span data-stu-id="9d18d-182">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="9d18d-183">保管人：變更、讀取</span><span class="sxs-lookup"><span data-stu-id="9d18d-183">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="9d18d-184">系統管理員：完全控制</span><span class="sxs-lookup"><span data-stu-id="9d18d-184">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="9d18d-185">Exchange 受信任子系統：變更、讀取</span><span class="sxs-lookup"><span data-stu-id="9d18d-185">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="9d18d-186">開啟 [**安全性**] 索引標籤，新增保管人群組，然後按一下 [**高級**]。</span><span class="sxs-lookup"><span data-stu-id="9d18d-186">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="9d18d-187">為保管人群組設定下列許可權：</span><span class="sxs-lookup"><span data-stu-id="9d18d-187">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="9d18d-188">**類型：拒絕**</span><span class="sxs-lookup"><span data-stu-id="9d18d-188">**Type: Deny**</span></span>
    
  - <span data-ttu-id="9d18d-189">**適用于：此資料夾、子資料夾及檔案**</span><span class="sxs-lookup"><span data-stu-id="9d18d-189">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="9d18d-190">按一下 [**高級許可權**]，然後選取下列各項：</span><span class="sxs-lookup"><span data-stu-id="9d18d-190">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="9d18d-191">**讀取屬性**</span><span class="sxs-lookup"><span data-stu-id="9d18d-191">**Read attributes**</span></span>
    
  - <span data-ttu-id="9d18d-192">**讀取擴充屬性**</span><span class="sxs-lookup"><span data-stu-id="9d18d-192">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="9d18d-193">**讀取權限**</span><span class="sxs-lookup"><span data-stu-id="9d18d-193">**Read permissions**</span></span>
    
6. <span data-ttu-id="9d18d-194">執行下列動作，以測試對事例 $ file 共用的存取：</span><span class="sxs-lookup"><span data-stu-id="9d18d-194">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="9d18d-195">將使用者新增至保管人群組。</span><span class="sxs-lookup"><span data-stu-id="9d18d-195">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="9d18d-196">將檔案放在案例 $ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9d18d-196">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="9d18d-197">以使用者的身分流覽至暫存伺服器，例如流覽至「暫存」 \\ \\ 共用，以查看有哪些共用可供使用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-197">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="9d18d-198">您不應該看到列出的**案例 $** [共用]。</span><span class="sxs-lookup"><span data-stu-id="9d18d-198">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="9d18d-199">手動輸入案例 $ 共用到瀏覽器的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9d18d-199">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="9d18d-200">這應該會開啟案例 $ 共用。</span><span class="sxs-lookup"><span data-stu-id="9d18d-200">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="9d18d-201">嘗試開啟您先前放入共用中的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d18d-201">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="9d18d-202">這應該會失敗。</span><span class="sxs-lookup"><span data-stu-id="9d18d-202">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="9d18d-203">登入腳本</span><span class="sxs-lookup"><span data-stu-id="9d18d-203">Logon script</span></span>

1. <span data-ttu-id="9d18d-204">在 [記事本] 中複製並貼上此 Windows PowerShell 腳本：</span><span class="sxs-lookup"><span data-stu-id="9d18d-204">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="9d18d-205">在便於您尋找的位置（例如，C： AFCScripts）中，將上述腳本儲存為 CollectionScript.ps1 \\ 。</span><span class="sxs-lookup"><span data-stu-id="9d18d-205">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="9d18d-206">使用 [記事本] 中的 [移至] 功能。</span><span class="sxs-lookup"><span data-stu-id="9d18d-206">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="9d18d-207">請視需要進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="9d18d-207">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="9d18d-208">**行號**</span><span class="sxs-lookup"><span data-stu-id="9d18d-208">**Line #**</span></span>|<span data-ttu-id="9d18d-209">**您需要變更的專案**</span><span class="sxs-lookup"><span data-stu-id="9d18d-209">**What you need to change**</span></span>|<span data-ttu-id="9d18d-210">**必要/選用**</span><span class="sxs-lookup"><span data-stu-id="9d18d-210">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9d18d-211">71</span><span class="sxs-lookup"><span data-stu-id="9d18d-211">71</span></span>  <br/> |<span data-ttu-id="9d18d-212">**$FileTypes**變數。</span><span class="sxs-lookup"><span data-stu-id="9d18d-212">**$FileTypes** variable.</span></span> <span data-ttu-id="9d18d-213">在陣列變數中包含您想要腳本清查及收集的所有檔案類型副檔名。</span><span class="sxs-lookup"><span data-stu-id="9d18d-213">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="9d18d-214">選用</span><span class="sxs-lookup"><span data-stu-id="9d18d-214">Optional</span></span>  <br/> |
|<span data-ttu-id="9d18d-215">76和77</span><span class="sxs-lookup"><span data-stu-id="9d18d-215">76 and 77</span></span>  <br/> |<span data-ttu-id="9d18d-216">變更建立 **$CaseNo**變數以符合您的需求的方式。</span><span class="sxs-lookup"><span data-stu-id="9d18d-216">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="9d18d-217">腳本會捕獲目前的日期和時間，並附加使用者名稱給它。</span><span class="sxs-lookup"><span data-stu-id="9d18d-217">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="9d18d-218">選用</span><span class="sxs-lookup"><span data-stu-id="9d18d-218">Optional</span></span>  <br/> |
|<span data-ttu-id="9d18d-219">80</span><span class="sxs-lookup"><span data-stu-id="9d18d-219">80</span></span>  <br/> |<span data-ttu-id="9d18d-220">**$CaseRootLocation**變數必須設定為您的暫存伺服器集合檔案共用，例如， \*\* \\ \\ 暫存 \\ 案例 $\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d18d-220">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="9d18d-221">必要</span><span class="sxs-lookup"><span data-stu-id="9d18d-221">Required</span></span>  <br/> |
   
4. <span data-ttu-id="9d18d-222">將 CollectionScript.ps1 檔案放在網域控制站上的 Netlogon 檔案共用中。</span><span class="sxs-lookup"><span data-stu-id="9d18d-222">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="9d18d-223">為登入腳本和保管人群組設定 GPO</span><span class="sxs-lookup"><span data-stu-id="9d18d-223">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="9d18d-224">遵循主題中的「如何指派使用者登入腳本」一節，[使用群組原則中](https://go.microsoft.com/fwlink/p/?LinkId=614844)的「啟動」、「關機」、「登入」和「登出」腳本，設定保管人群組的登入腳本。</span><span class="sxs-lookup"><span data-stu-id="9d18d-224">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="9d18d-225">從**安全性篩選**移除已驗證的使用者，並新增保管人群組。</span><span class="sxs-lookup"><span data-stu-id="9d18d-225">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="9d18d-226">適用于 Exchange Server 2013 的 PST 匯入選項 A、腳本</span><span class="sxs-lookup"><span data-stu-id="9d18d-226">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="9d18d-227">將下列 Windows PowerShell 腳本複製並貼到 [記事本] 中：</span><span class="sxs-lookup"><span data-stu-id="9d18d-227">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="9d18d-228">在便於您尋找的位置中，將腳本儲存為 PSTImportScript.ps1。</span><span class="sxs-lookup"><span data-stu-id="9d18d-228">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="9d18d-229">例如，便於使用，請在暫存的伺服器上建立一個名為「暫存 AFCScripts」的資料夾 \\ \\ \\ ，並將它儲存到該資料夾。</span><span class="sxs-lookup"><span data-stu-id="9d18d-229">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="9d18d-230">使用 [記事本] 中的 [移至] 功能，並視需要進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="9d18d-230">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="9d18d-231">**行號**</span><span class="sxs-lookup"><span data-stu-id="9d18d-231">**Line #**</span></span>|<span data-ttu-id="9d18d-232">**您需要變更的專案**</span><span class="sxs-lookup"><span data-stu-id="9d18d-232">**What you need to change**</span></span>|<span data-ttu-id="9d18d-233">**必要/選用**</span><span class="sxs-lookup"><span data-stu-id="9d18d-233">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9d18d-234">12 </span><span class="sxs-lookup"><span data-stu-id="9d18d-234">12</span></span>  <br/> |<span data-ttu-id="9d18d-235">**$FolderIdentifier**標記 pst 所匯入的信箱資料夾。</span><span class="sxs-lookup"><span data-stu-id="9d18d-235">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="9d18d-236">視需要變更此。</span><span class="sxs-lookup"><span data-stu-id="9d18d-236">Change this if necessary.</span></span> <br/> |<span data-ttu-id="9d18d-237">選用</span><span class="sxs-lookup"><span data-stu-id="9d18d-237">Optional</span></span>  <br/> |
|<span data-ttu-id="9d18d-238">17 </span><span class="sxs-lookup"><span data-stu-id="9d18d-238">17</span></span>  <br/> |<span data-ttu-id="9d18d-239">**$ConnectionUri**必須設定為您自己的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9d18d-239">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="9d18d-240">> [!IMPORTANT]> 請確定 **$ConnectionUri**指向 HTTP 位置，而不是 HTTPs。</span><span class="sxs-lookup"><span data-stu-id="9d18d-240">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="9d18d-241">它不會搭配使用 HTTPs：。</span><span class="sxs-lookup"><span data-stu-id="9d18d-241">It won't work with https:.</span></span>          |<span data-ttu-id="9d18d-242">必要</span><span class="sxs-lookup"><span data-stu-id="9d18d-242">Required</span></span>  <br/> |
   
4. <span data-ttu-id="9d18d-243">確認 Exchange 受信任子系統帳戶具有「暫存案例」的「讀取」、「寫入」和「執行」許可權 \\ \\ \\ 。</span><span class="sxs-lookup"><span data-stu-id="9d18d-243">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="9d18d-244">PST 匯入腳本需要下列兩個輸入參數：</span><span class="sxs-lookup"><span data-stu-id="9d18d-244">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="9d18d-245">**$SourcePath**要匯入之 PST 檔案的位置，例如「 \\ \\ 暫存 \\ 案例」。</span><span class="sxs-lookup"><span data-stu-id="9d18d-245">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="9d18d-246">**$MailboxAlias**將接收匯入電子郵件專案之目標信箱的別名。</span><span class="sxs-lookup"><span data-stu-id="9d18d-246">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="9d18d-247">例如，如果您想要將路徑 Staging\Cases $ 中的所有 PST 檔案匯入 \\ 至具有別名 eDiscoveryMailbox 的信箱中，您可以執行腳本，如下所示 `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox` 。</span><span class="sxs-lookup"><span data-stu-id="9d18d-247">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="9d18d-248">適用于 Exchange Online 的 PST 匯入選項 B</span><span class="sxs-lookup"><span data-stu-id="9d18d-248">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="9d18d-249">建立要將匯入 PST 檔案放入的信箱結構。</span><span class="sxs-lookup"><span data-stu-id="9d18d-249">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="9d18d-250">如需如何在 Exchange Online 中建立使用者信箱的詳細資訊，請參閱[在 Exchange online 中建立使用者](https://go.microsoft.com/fwlink/p/?LinkId=615118)信箱。</span><span class="sxs-lookup"><span data-stu-id="9d18d-250">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="9d18d-251">冷藏</span><span class="sxs-lookup"><span data-stu-id="9d18d-251">Cold storage</span></span>

1. <span data-ttu-id="9d18d-252">在 Azure 虛擬機器上建立檔案共用，將在其中放置所有收集的檔案，例如 \\ \\ AZFile1 \\ ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="9d18d-252">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="9d18d-253">授與預設的內容存取帳戶，至少要有共用及所有子資料夾及檔案的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="9d18d-253">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="9d18d-254">如需設定 SharePoint 2013 搜尋的詳細資訊，請參閱[在 SharePoint Server 2013 中建立及設定 Search service 應用程式](https://go.microsoft.com/fwlink/p/?LinkId=614940)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-254">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="9d18d-255">如果您想要從 AZFile1 ContentColdStorage 匯入 PST 檔案 \\ \\ \\ ，請將 Exchange 受信任的子系統授與共享的「讀取」、「寫入」和「執行」許可權。</span><span class="sxs-lookup"><span data-stu-id="9d18d-255">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="9d18d-256">協調</span><span class="sxs-lookup"><span data-stu-id="9d18d-256">Orchestrator</span></span>

1. <span data-ttu-id="9d18d-257">從 Microsoft 下載中心下載[MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 。</span><span class="sxs-lookup"><span data-stu-id="9d18d-257">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="9d18d-258">開啟**Runbook Designer**，**在 [連線**] 窗格中，按一下您要匯入 Runbook 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9d18d-258">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="9d18d-259">按一下 [**動作**] 功能表，然後按一下 [匯**入**]。</span><span class="sxs-lookup"><span data-stu-id="9d18d-259">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="9d18d-260">[匯**入**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="9d18d-260">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="9d18d-261">在 [檔案**位置**] 方塊中，輸入您要匯入之 runbook 的路徑和檔案名，或按一下省略號（ **...**）流覽至您要匯入的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d18d-261">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="9d18d-262">選取 [匯**入 runbook** ] 和 [匯**入 Orchestrator 加密資料**]。</span><span class="sxs-lookup"><span data-stu-id="9d18d-262">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="9d18d-263">清除**計數器**、**時程表**、**變數**、**電腦群組**、匯**入全域**設定，以及**覆寫現有的全域**設定。</span><span class="sxs-lookup"><span data-stu-id="9d18d-263">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="9d18d-264">按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d18d-264">Click **Finish**.</span></span>
    
6. <span data-ttu-id="9d18d-265">編輯**MoveFilesToColdStorage** runbook，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9d18d-265">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="9d18d-266">**移動**檔案活動-將**來原始檔案**路徑設定為集合檔案共用，例如「 \\ \\ 暫存 \\ 案例」。</span><span class="sxs-lookup"><span data-stu-id="9d18d-266">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="9d18d-267">將**目的地資料夾**設定為 Azure 中的 cold 儲存檔共用，例如 \\ \\ AZFile1 \\ ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="9d18d-267">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="9d18d-268">選取 [**建立具有唯一名稱**的檔案]。</span><span class="sxs-lookup"><span data-stu-id="9d18d-268">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="9d18d-269">**刪除資料夾**活動-將**路徑：** 設定為集合檔案共用（例如， \\ \\ 暫存 \\ 案例 $ \\ \*），然後選取 [**刪除所有檔案與子資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="9d18d-269">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="9d18d-270">使用[部署 runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120)中的程式部署**MoveToColdStorage** runbook。</span><span class="sxs-lookup"><span data-stu-id="9d18d-270">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="9d18d-271">SharePoint 冷儲存體的內部部署搜尋</span><span class="sxs-lookup"><span data-stu-id="9d18d-271">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="9d18d-272">在您的 SharePoint 2013 伺服器陣列中建立新的內容來源，以用於 Azure 中的冷存放區共用，例如 \\ \\ AZFile1 \\ ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="9d18d-272">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="9d18d-273">如需管理內容來源的詳細資訊，請參閱[在 SharePoint Server 2013 中新增、編輯或刪除內容來源](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="9d18d-273">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="9d18d-274">開始完整編目。</span><span class="sxs-lookup"><span data-stu-id="9d18d-274">Start a full crawl.</span></span> <span data-ttu-id="9d18d-275">如需詳細資訊，請參閱[SharePoint Server 2013 中的編目、啟動、暫停、繼續或停止](https://go.microsoft.com/fwlink/p/?LinkId=615005)編目。</span><span class="sxs-lookup"><span data-stu-id="9d18d-275">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="9d18d-276">使用方案</span><span class="sxs-lookup"><span data-stu-id="9d18d-276">Using the solution</span></span>

<span data-ttu-id="9d18d-277">使用此解決方案有五個主要步驟，假設您不想要將 PST 檔案匯入 Exchange Server 2013 和 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="9d18d-277">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="9d18d-278">本節為您提供所有這些程式的程式。</span><span class="sxs-lookup"><span data-stu-id="9d18d-278">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="9d18d-279">您與解決方案的主要互動將會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9d18d-279">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="9d18d-280">管理保管人群組中的使用者成員資格。</span><span class="sxs-lookup"><span data-stu-id="9d18d-280">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="9d18d-281">檢查登入腳本所產生的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9d18d-281">Review the log files generated by the logon script.</span></span> <span data-ttu-id="9d18d-282">FileCopyErrors 會列出所有未順利複製的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d18d-282">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="9d18d-283">您必須決定要使用的方式</span><span class="sxs-lookup"><span data-stu-id="9d18d-283">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="9d18d-284">管理 PST 匯入程式。</span><span class="sxs-lookup"><span data-stu-id="9d18d-284">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="9d18d-285">將集合檔案移至冷存放區。</span><span class="sxs-lookup"><span data-stu-id="9d18d-285">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="9d18d-286">其他所有步驟並非此解決方案特有的步驟。</span><span class="sxs-lookup"><span data-stu-id="9d18d-286">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="9d18d-287">它們是您在 SharePoint 2013、Microsoft 365 和 Azure 中執行的標準管理工作。</span><span class="sxs-lookup"><span data-stu-id="9d18d-287">They are standard administrative tasks that you perform in SharePoint 2013, Microsoft 365, and Azure.</span></span> <span data-ttu-id="9d18d-288">此解決方案中的專案不會提供任何指引，您必須根據公司的需求來完成工作，例如：</span><span class="sxs-lookup"><span data-stu-id="9d18d-288">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="9d18d-289">追蹤您的 eDiscovery 案例，以及哪些保管人與哪一種情況相關聯。</span><span class="sxs-lookup"><span data-stu-id="9d18d-289">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="9d18d-290">追蹤哪組檔集合會與 eDiscovery 案例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9d18d-290">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="9d18d-291">協調匯入和移至冷儲存步驟的時間。</span><span class="sxs-lookup"><span data-stu-id="9d18d-291">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="9d18d-292">管理 Azure 中使用的檔空間。</span><span class="sxs-lookup"><span data-stu-id="9d18d-292">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="9d18d-293">管理 Pst 所匯入的信箱。</span><span class="sxs-lookup"><span data-stu-id="9d18d-293">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="9d18d-294">所有內部部署資料的備份及還原。</span><span class="sxs-lookup"><span data-stu-id="9d18d-294">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="9d18d-295">保管人管理</span><span class="sxs-lookup"><span data-stu-id="9d18d-295">Custodian management</span></span>

- <span data-ttu-id="9d18d-296">若要為個別使用者啟動自動化檔收集程式，請將其新增至保管人群組。</span><span class="sxs-lookup"><span data-stu-id="9d18d-296">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="9d18d-297">使用者下一次登入時，系統會執行透過「群組原則」指派給保管人群組的登入腳本。</span><span class="sxs-lookup"><span data-stu-id="9d18d-297">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="9d18d-298">監視收集的檔案並複查記錄檔</span><span class="sxs-lookup"><span data-stu-id="9d18d-298">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="9d18d-299">針對使用者的集合資料夾，觀賞集合檔案共用（例如， \\ \\ 暫存 \\ 案例 $ \\ \*）。</span><span class="sxs-lookup"><span data-stu-id="9d18d-299">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="9d18d-300">資料夾的名稱會以如下格式格式化： *yyyyMMddHHmm_UserName* 。</span><span class="sxs-lookup"><span data-stu-id="9d18d-300">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="9d18d-301">完成集合後，請開啟集合資料夾，然後流覽至 [_Log] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9d18d-301">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="9d18d-302">在 [_Log] 資料夾中，您將會看到下列專案：</span><span class="sxs-lookup"><span data-stu-id="9d18d-302">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="9d18d-303">使用者電腦上的每個本機磁片磁碟機都有一個 XML 檔案，例如**A.xml**， **C.xml**。</span><span class="sxs-lookup"><span data-stu-id="9d18d-303">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="9d18d-304">這些檔案包含的清查磁片磁碟機會在其後命名，並用於 robocopy 作業。</span><span class="sxs-lookup"><span data-stu-id="9d18d-304">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="9d18d-305">集合腳本只會在清單檔中為您在腳本中定義的檔案類型建立專案。</span><span class="sxs-lookup"><span data-stu-id="9d18d-305">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="9d18d-306">它不會為使用者電腦上的每個檔案建立庫存專案。</span><span class="sxs-lookup"><span data-stu-id="9d18d-306">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="9d18d-307">每個集合執行的一個名為 FileCopyErrors 的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9d18d-307">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="9d18d-308">此檔案包含 robocopy 無法複製至檔案集合共用的檔案清單，例如， \\ \\ 暫存 \\ 案例 $ \\ \*。</span><span class="sxs-lookup"><span data-stu-id="9d18d-308">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="9d18d-309">您必須複查此專案，並決定要對這些未錯過的檔案採取的動作。</span><span class="sxs-lookup"><span data-stu-id="9d18d-309">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="9d18d-310">通常，您必須以手動方式收集這些檔案，否則您可能會決定不需要該集合，也可以忽略集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="9d18d-310">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="9d18d-311">Exchange Server 2013 的 PST 匯入選項 A</span><span class="sxs-lookup"><span data-stu-id="9d18d-311">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="9d18d-312">登入裝載集合檔案共用的伺服器，例如，**暫存**及開啟的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9d18d-312">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="9d18d-313">如需啟動 Windows PowerShell 的詳細資訊，請參閱[Windows Server 上的啟動 windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=615115)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-313">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="9d18d-314">設定執行原則為無限制。</span><span class="sxs-lookup"><span data-stu-id="9d18d-314">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="9d18d-315">輸入 `Set-ExecutionPolicy Unrestricted -Scope Process` Windows PowerShell，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="9d18d-315">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="9d18d-316">執行 PSTImportScript.ps1 檔，並提供 **$SourcePath**和 **$MailboxAlias**參數。</span><span class="sxs-lookup"><span data-stu-id="9d18d-316">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="9d18d-317">如需執行 Windows PowerShell 腳本的詳細資訊，請參閱執行[腳本](https://go.microsoft.com/fwlink/p/?LinkID=615117)。</span><span class="sxs-lookup"><span data-stu-id="9d18d-317">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="9d18d-318">檢查輸出中是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d18d-318">Review the output for errors.</span></span>
    
5. <span data-ttu-id="9d18d-319">嘗試將同名的 PST 檔案匯入相同的信箱之前，您必須移除信箱匯入要求。</span><span class="sxs-lookup"><span data-stu-id="9d18d-319">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="9d18d-320">執行下列命令以執行： `Get-MailboxImportRequest | Remove-MailboxImportRequest` 。</span><span class="sxs-lookup"><span data-stu-id="9d18d-320">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="9d18d-321">系統會提示您從佇列中移除每個個別要求。</span><span class="sxs-lookup"><span data-stu-id="9d18d-321">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="9d18d-322">視需要回應。</span><span class="sxs-lookup"><span data-stu-id="9d18d-322">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="9d18d-323">適用于 Exchange Online 的 PST 匯入選項 B</span><span class="sxs-lookup"><span data-stu-id="9d18d-323">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="9d18d-324">若要將收集的 PST 檔案放入 Exchange Online，請遵循透過[網路上傳](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)將檔案匯入 Microsoft 365 中的程式。</span><span class="sxs-lookup"><span data-stu-id="9d18d-324">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Microsoft 365 through [network upload](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="9d18d-325">移至冷存放區</span><span class="sxs-lookup"><span data-stu-id="9d18d-325">Move to cold storage</span></span>

1. <span data-ttu-id="9d18d-326">使用執行[runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123)中的程式執行**MoveToColdStorage** runbook。</span><span class="sxs-lookup"><span data-stu-id="9d18d-326">Run the **MoveToColdStorage** runbook using the procedures in [Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="9d18d-327">觀賞用於長期儲存體的 Azure 檔案共用，例如 \\ \\ AZFile1 \\ ContentColdStorage 和內部部署集合檔案共用（例如， \\ \\ 暫存 \\ 案例 $）。</span><span class="sxs-lookup"><span data-stu-id="9d18d-327">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="9d18d-328">您應該會看到檔案和資料夾出現在 cold 儲存檔共用中，並從集合檔案共用中消失。</span><span class="sxs-lookup"><span data-stu-id="9d18d-328">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="9d18d-329">電子文件探索</span><span class="sxs-lookup"><span data-stu-id="9d18d-329">eDiscovery</span></span>

1. <span data-ttu-id="9d18d-330">允許完整編目冷儲存體檔案共用以排程的方式執行，或啟動編目。</span><span class="sxs-lookup"><span data-stu-id="9d18d-330">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="9d18d-331">如需啟動完整或累加編目的詳細資訊，請參閱[SharePoint Server 2013 中的開始、暫停、繼續或停止](https://go.microsoft.com/fwlink/p/?LinkId=615005)編目。</span><span class="sxs-lookup"><span data-stu-id="9d18d-331">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="9d18d-332">如果您在使用選項 B 的情況下，在 SharePoint Online 中使用選項 A 來進行 PST 檔案匯入或建立 eDiscovery 案例，請在 SharePoint 2013 中建立電子檔探索案例。</span><span class="sxs-lookup"><span data-stu-id="9d18d-332">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

