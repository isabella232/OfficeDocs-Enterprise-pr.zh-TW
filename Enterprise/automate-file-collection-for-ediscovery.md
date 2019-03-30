---
title: EDiscovery 的自動化檔案收集
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要： 了解如何自動化檔案收集從使用者電腦 ediscovery （英文）。
ms.openlocfilehash: bfbe3b9218ed81727f2cc6ad9fabcb02e76d486b
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001606"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="ac694-103">EDiscovery 的自動化檔案收集</span><span class="sxs-lookup"><span data-stu-id="ac694-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="ac694-104">**摘要：** 了解如何自動化檔案收集從使用者電腦 ediscovery （英文）。</span><span class="sxs-lookup"><span data-stu-id="ac694-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="ac694-105">所有公司都面臨潛在訴訟或其他類型的法律巨集指令。</span><span class="sxs-lookup"><span data-stu-id="ac694-105">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="ac694-106">雖然法務部門可以使用，以減少的曝光度，訴訟資料暫留是商務生命週期的事實。</span><span class="sxs-lookup"><span data-stu-id="ac694-106">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="ac694-107">當公司朝法律行動時，它們是必要的透過法律探索，以提供巷以及對手顧問所有相關的記錄資料的程序。</span><span class="sxs-lookup"><span data-stu-id="ac694-107">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="ac694-108">eDiscovery 是依據公司清查、 搜尋、 識別、 保留、 篩選和提供相關的記錄資料存在的電子表單中的程序。</span><span class="sxs-lookup"><span data-stu-id="ac694-108">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="ac694-109">SharePoint 2013、 Exchange Server 2013、 Lync Server 2013、 SharePoint Online 和 Exchange Online 可以保留大量記錄的內容。</span><span class="sxs-lookup"><span data-stu-id="ac694-109">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="ac694-110">根據版本，這些產品可能支援 eDiscovery 及就地保留概觀 (Lync 透過 Exchange 伺服器)，以便輕鬆編製索引，法律 teams 識別、 按住並篩選的特定案例的最相關內容。</span><span class="sxs-lookup"><span data-stu-id="ac694-110">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="ac694-111">許多文件會儲存在使用者 (Custodians) 上本機電腦，而不是以在集中式位置。</span><span class="sxs-lookup"><span data-stu-id="ac694-111">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="ac694-112">這使得基本上是針對 SharePoint 2013 搜尋，並無法搜尋，如果它不能包含 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="ac694-112">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="ac694-113">這個解決方案示範如何使用登入指令檔，System Center 協調 2012 R2 和 Exchange Server 的 Windows PowerShell 自動化的識別資料及記錄資料從使用者電腦的集合。</span><span class="sxs-lookup"><span data-stu-id="ac694-113">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="ac694-114">此解決方案的用途</span><span class="sxs-lookup"><span data-stu-id="ac694-114">What this solution does</span></span>

<span data-ttu-id="ac694-115">此解決方案會使用通用的安全性，群組原則] 和 Windows PowerShell 指令碼來尋找、 清查，並從使用者本機電腦收集內容和 Outlook 個人存放區 (PST) 檔案，隱藏的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-115">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="ac694-116">從該處的 PST 檔案可以匯入 Exchange Server 2013 或 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="ac694-116">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="ac694-117">所有檔案會接著都移在 Microsoft Azure 中使用 System Center 協調 2012 R2 runbook 到另一個檔案共用長期儲存與 SharePoint 2013 所編製索引。</span><span class="sxs-lookup"><span data-stu-id="ac694-117">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="ac694-118">然後您使用 eDiscovery center 在內部部署 SharePoint 2013 部署或 SharePoint Online 中一樣定期執行 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="ac694-118">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="ac694-119">此解決方案使用 robocopy 檔案複製到集中式的檔案共用的 custodian 的電腦。</span><span class="sxs-lookup"><span data-stu-id="ac694-119">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="ac694-120">因為 robocopy 不會複製檔案開啟或鎖定，任何檔案，包括 custodian 已開啟的 PST 檔案將不會收集。</span><span class="sxs-lookup"><span data-stu-id="ac694-120">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="ac694-121">您必須以手動方式收集它們。</span><span class="sxs-lookup"><span data-stu-id="ac694-121">You will have to collect them manually.</span></span> <span data-ttu-id="ac694-122">此解決方案並提供您明確地識別它不能複製檔案的清單與每個檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ac694-122">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="ac694-123">下圖引導您逐步完成所有步驟和解決方案的元素。</span><span class="sxs-lookup"><span data-stu-id="ac694-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![自動化檔案收集解決方案的概觀](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="ac694-125">圖例 \* \* \*</span><span class="sxs-lookup"><span data-stu-id="ac694-125">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![洋紅色圖說文字 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="ac694-127">建立群組原則物件 (GPO)，並將它與集合登入指令檔。</span><span class="sxs-lookup"><span data-stu-id="ac694-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![洋紅色圖說文字 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="ac694-129">設定只對 Custodians 群組套用到 GPO 的 GPO 安全性篩選。</span><span class="sxs-lookup"><span data-stu-id="ac694-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![洋紅色圖說文字 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="ac694-131">Custodian 登入並 GPO 執行時，呼叫集合登入指令檔。</span><span class="sxs-lookup"><span data-stu-id="ac694-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![洋紅色圖說文字 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="ac694-133">集合登入指令檔清查 Custodians 電腦，搜尋想要的檔案並錄製其位置上的所有本機連接磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ac694-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![洋紅色圖說文字 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="ac694-135">集合登入指令碼會複製清查的檔案預備伺服器上的隱藏的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![洋紅色圖說文字 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="ac694-137">（選項的）以手動方式執行 PST 匯入指令碼，以收集的 PST 檔案匯入 Exchange Server 2013。</span><span class="sxs-lookup"><span data-stu-id="ac694-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![洋紅色圖說文字 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="ac694-139">（選項 B）使用 Office 365 匯入工具及程序，匯入的收集的 PST 檔案 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="ac694-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![洋紅色圖說文字 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="ac694-141">將所有收集到的檔案移至長期儲存與 MoveToColdStorage System Center 協調 2012 R2 runbook Azure 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![洋紅色圖說文字 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="ac694-143">索引中與 SharePoint 2013 的冷儲存檔案共用的檔案。</span><span class="sxs-lookup"><span data-stu-id="ac694-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![洋紅色圖說文字 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="ac694-145">執行 eDiscovery 在冷儲存區和內部部署 Exchange Server 2013 中的內容。</span><span class="sxs-lookup"><span data-stu-id="ac694-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![洋紅色圖說文字 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="ac694-147">在 Office 365 中的內容上執行 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="ac694-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="ac694-148">必要條件</span><span class="sxs-lookup"><span data-stu-id="ac694-148">Prerequisites</span></span>

<span data-ttu-id="ac694-149">此解決方案的組態最需要許多項目，，其中您可能有，並設定如果您的想法有關 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="ac694-149">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="ac694-150">針對您不一定或該地需要特定設定，我們將提供您具有連結的項目中，您需要組建出您的基底組態。</span><span class="sxs-lookup"><span data-stu-id="ac694-150">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="ac694-151">設定本身的解決方案之前，您必須具有就地基底組態。</span><span class="sxs-lookup"><span data-stu-id="ac694-151">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="ac694-152">基本設定</span><span class="sxs-lookup"><span data-stu-id="ac694-152">Base configuration</span></span>

|<span data-ttu-id="ac694-153">**元素**</span><span class="sxs-lookup"><span data-stu-id="ac694-153">**Element**</span></span>|<span data-ttu-id="ac694-154">**連結**</span><span class="sxs-lookup"><span data-stu-id="ac694-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ac694-155">Active Directory 網域服務 (AD DS) 網域</span><span class="sxs-lookup"><span data-stu-id="ac694-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="ac694-156">從您的內部網路的網際網路連線能力</span><span class="sxs-lookup"><span data-stu-id="ac694-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="ac694-157">若要支援 SharePoint 2013 和 System Center 協調 2012 R2 的 SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="ac694-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="ac694-158">部署 System Center 協調-2012</span><span class="sxs-lookup"><span data-stu-id="ac694-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="ac694-159">內部部署或 Azure 根據 SharePoint 2013 ediscovery （英文） （所需的選項 A）</span><span class="sxs-lookup"><span data-stu-id="ac694-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="ac694-160">內部檔案共用伺服器上的臨時</span><span class="sxs-lookup"><span data-stu-id="ac694-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="ac694-161">內部部署 Exchange Server 2013 的選項 PST 匯入</span><span class="sxs-lookup"><span data-stu-id="ac694-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="ac694-162">CU5 (15.913.22) 位於[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)。</span><span class="sxs-lookup"><span data-stu-id="ac694-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="ac694-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ac694-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="ac694-164">部署 System Center 協調-2012</span><span class="sxs-lookup"><span data-stu-id="ac694-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="ac694-165">Office 365 （方案 E3） 與 Exchange Online 和 SharePoint Online （所需的選項 B）</span><span class="sxs-lookup"><span data-stu-id="ac694-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="ac694-166">若要註冊 Office 365 E3 訂用帳戶，請參閱 < <b0>Office 365 E3 訂閱</b0>。</span><span class="sxs-lookup"><span data-stu-id="ac694-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="ac694-167">使用虛擬機器的 azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="ac694-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="ac694-168">若要註冊 Azure，請參閱[Windows Azure 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="ac694-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="ac694-169">您的內部網路與您 Azure 訂用帳戶之間的 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="ac694-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="ac694-170">若要設定您 Azure 訂用帳戶和內部部署網路間的 VPN 通道，請參閱[連線到 Microsoft Azure 虛擬網路的內部網路](https://go.microsoft.com/fwlink/p/?LinkId=613507)。</span><span class="sxs-lookup"><span data-stu-id="ac694-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="ac694-171">若要搜尋 SharePoint 和 Exchange Server 2013 和 Lync Server 2013 （選用） 設定 SharePoint 2013 的 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ac694-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="ac694-172">若要以這種方式設定電子文件探索，請參閱 <<c0>在 SharePoint Server 2013 中的設定 eDiscovery和<b1>測試實驗室指南： Exchange、 Lync、 SharePoint 及 Windows 檔案共用測試實驗室中設定 eDiscovery</b1>。</span><span class="sxs-lookup"><span data-stu-id="ac694-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="ac694-173">在 SharePoint Online 和 Exchange Online 的 Office 365 中的 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ac694-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="ac694-174">若要在 Office 365 中設定電子文件探索，請參閱 <<c0>設定 SharePoint Online 中的 eDiscovery 中心。</span><span class="sxs-lookup"><span data-stu-id="ac694-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="ac694-175">設定環境</span><span class="sxs-lookup"><span data-stu-id="ac694-175">Configure the environment</span></span>

<span data-ttu-id="ac694-176">現在，您有基底組態中的位置，您可以設定解決方案本身向前移動。</span><span class="sxs-lookup"><span data-stu-id="ac694-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="ac694-177">臨時檔案共用</span><span class="sxs-lookup"><span data-stu-id="ac694-177">Staging file share</span></span>

1. <span data-ttu-id="ac694-178">在內部部署網域中，建立名為 Custodians 通用安全性群組。</span><span class="sxs-lookup"><span data-stu-id="ac694-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="ac694-179">建立的檔案，從 Custodians 電腦收集的隱藏的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-179">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="ac694-180">這應該是在內部部署伺服器上。</span><span class="sxs-lookup"><span data-stu-id="ac694-180">This should be on an on-premises server.</span></span> <span data-ttu-id="ac694-181">比方說，在名為臨時伺服器上，建立名為的情況下 $ 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-181">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="ac694-182">**$** ，才能將此位址設隱藏的共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-182">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="ac694-183">設定下列共用權限：</span><span class="sxs-lookup"><span data-stu-id="ac694-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="ac694-184">Custodians： 變更，請閱讀</span><span class="sxs-lookup"><span data-stu-id="ac694-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="ac694-185">系統管理員：完全控制</span><span class="sxs-lookup"><span data-stu-id="ac694-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="ac694-186">Exchange 受信任的子系統： 變更，請閱讀</span><span class="sxs-lookup"><span data-stu-id="ac694-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="ac694-187">開啟 [**安全性**] 索引標籤，新增 [Custodians] 群組中，按一下 [**進階**]。</span><span class="sxs-lookup"><span data-stu-id="ac694-187">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="ac694-188">設定 Custodians 群組的下列權限：</span><span class="sxs-lookup"><span data-stu-id="ac694-188">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="ac694-189">**類型： 拒絕**</span><span class="sxs-lookup"><span data-stu-id="ac694-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="ac694-190">**適用於： 這個資料夾、 子資料夾及檔案**</span><span class="sxs-lookup"><span data-stu-id="ac694-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="ac694-191">按一下 [**進階權限**，然後選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="ac694-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="ac694-192">**讀取屬性**</span><span class="sxs-lookup"><span data-stu-id="ac694-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="ac694-193">**閱讀延伸的屬性**</span><span class="sxs-lookup"><span data-stu-id="ac694-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="ac694-194">**讀取權限**</span><span class="sxs-lookup"><span data-stu-id="ac694-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="ac694-195">測試存取的情況下 $ 檔案共用，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac694-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="ac694-196">將使用者新增至 Custodians 群組。</span><span class="sxs-lookup"><span data-stu-id="ac694-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="ac694-197">位置的情況下 $ 資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="ac694-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="ac694-198">為使用者、 瀏覽至預備伺服器，例如瀏覽至\\\\分段執行若要查看哪些共用可用的共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-198">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="ac694-199">您不應該會看到所列的**情況下 $** 共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-199">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="ac694-200">手動輸入瀏覽器的情況下 $ 共用的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ac694-200">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="ac694-201">這應該會開啟的情況下 $ 共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-201">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="ac694-202">嘗試開啟先前放在共用的檔案。</span><span class="sxs-lookup"><span data-stu-id="ac694-202">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="ac694-203">這應該會失敗。</span><span class="sxs-lookup"><span data-stu-id="ac694-203">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="ac694-204">登入指令檔</span><span class="sxs-lookup"><span data-stu-id="ac694-204">Logon script</span></span>

1. <span data-ttu-id="ac694-205">複製並貼入 [記事本] 中的這個 Windows PowerShell 指令碼：</span><span class="sxs-lookup"><span data-stu-id="ac694-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="ac694-206">將上面的指令碼儲存為 CollectionScript.ps1 中的位置並讓您輕鬆地尋找，例如 c:\\AFCScripts。</span><span class="sxs-lookup"><span data-stu-id="ac694-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="ac694-207">在 [記事本] 使用 [移至] 功能。</span><span class="sxs-lookup"><span data-stu-id="ac694-207">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="ac694-208">視需要請進行下列變更:</span><span class="sxs-lookup"><span data-stu-id="ac694-208">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="ac694-209">**行號**</span><span class="sxs-lookup"><span data-stu-id="ac694-209">**Line #**</span></span>|<span data-ttu-id="ac694-210">**您需要變更**</span><span class="sxs-lookup"><span data-stu-id="ac694-210">**What you need to change**</span></span>|<span data-ttu-id="ac694-211">**所需/選用**</span><span class="sxs-lookup"><span data-stu-id="ac694-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ac694-212">71</span><span class="sxs-lookup"><span data-stu-id="ac694-212">71</span></span>  <br/> |<span data-ttu-id="ac694-213">**$FileTypes**變數。</span><span class="sxs-lookup"><span data-stu-id="ac694-213">**$FileTypes** variable.</span></span> <span data-ttu-id="ac694-214">包含您想要的指令碼來清查並收集陣列變數中的所有檔案類型副檔名。</span><span class="sxs-lookup"><span data-stu-id="ac694-214">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="ac694-215">選用</span><span class="sxs-lookup"><span data-stu-id="ac694-215">Optional</span></span>  <br/> |
|<span data-ttu-id="ac694-216">76 及 77</span><span class="sxs-lookup"><span data-stu-id="ac694-216">76 and 77</span></span>  <br/> |<span data-ttu-id="ac694-217">變更的方式 **$CaseNo**變數是內建符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="ac694-217">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="ac694-218">指令碼會擷取目前的日期和時間，並附加至它的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="ac694-218">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="ac694-219">選用</span><span class="sxs-lookup"><span data-stu-id="ac694-219">Optional</span></span>  <br/> |
|<span data-ttu-id="ac694-220">80</span><span class="sxs-lookup"><span data-stu-id="ac694-220">80</span></span>  <br/> |<span data-ttu-id="ac694-221">**$CaseRootLocation**變數必須設定為臨時伺服器集合檔案共用，例如**\\\\臨時\\情況下 $**。</span><span class="sxs-lookup"><span data-stu-id="ac694-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="ac694-222">必要</span><span class="sxs-lookup"><span data-stu-id="ac694-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="ac694-223">將 CollectionScript.ps1 檔案放置在網域控制站的 Netlogon 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="ac694-224">設定 GPO 的登入指令碼和 Custodians 群組</span><span class="sxs-lookup"><span data-stu-id="ac694-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="ac694-225">下列主題，<b0>使用啟動、 關閉、 登入和登出指令碼在群組原則中</b0>的 < 如何指派使用者登入指令檔 > 一節，以設定 Custodians 群組的登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="ac694-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="ac694-226">移除已驗證的使用者**安全性篩選**，並新增 Custodians 群組。</span><span class="sxs-lookup"><span data-stu-id="ac694-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="ac694-227">PST 匯入選項 A、 Exchange Server 2013 的指令碼</span><span class="sxs-lookup"><span data-stu-id="ac694-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="ac694-228">複製並貼入 [記事本] 中的下列 Windows PowerShell 指令碼：</span><span class="sxs-lookup"><span data-stu-id="ac694-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
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
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. <span data-ttu-id="ac694-229">將指令碼儲存為 PSTImportScript.ps1 是讓您輕鬆地找到的位置。</span><span class="sxs-lookup"><span data-stu-id="ac694-229">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="ac694-230">範例和使用者更方便使用，請在您呼叫的臨時伺服器中建立資料夾\\\\臨時\\AFCScripts，並將其儲存到那里。</span><span class="sxs-lookup"><span data-stu-id="ac694-230">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="ac694-231">在 [記事本]，使用 [移至] 功能，並視需要進行下列變更:</span><span class="sxs-lookup"><span data-stu-id="ac694-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="ac694-232">**行號**</span><span class="sxs-lookup"><span data-stu-id="ac694-232">**Line #**</span></span>|<span data-ttu-id="ac694-233">**您需要變更**</span><span class="sxs-lookup"><span data-stu-id="ac694-233">**What you need to change**</span></span>|<span data-ttu-id="ac694-234">**所需/選用**</span><span class="sxs-lookup"><span data-stu-id="ac694-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ac694-235">12 </span><span class="sxs-lookup"><span data-stu-id="ac694-235">12</span></span>  <br/> |<span data-ttu-id="ac694-236">**$FolderIdentifier**標記 Pst 匯入至信箱資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac694-236">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="ac694-237">如有必要，請變更此選項。</span><span class="sxs-lookup"><span data-stu-id="ac694-237">Change this if necessary.</span></span> <br/> |<span data-ttu-id="ac694-238">選用</span><span class="sxs-lookup"><span data-stu-id="ac694-238">Optional</span></span>  <br/> |
|<span data-ttu-id="ac694-239">17 </span><span class="sxs-lookup"><span data-stu-id="ac694-239">17</span></span>  <br/> |<span data-ttu-id="ac694-240">**$ConnectionUri**必須設為您自己的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ac694-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="ac694-241">> [!IMPORTANT]> 請確定您 **$ConnectionUri**點至 http 位置，而不是 https。</span><span class="sxs-lookup"><span data-stu-id="ac694-241">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="ac694-242">它不適用於 https:。</span><span class="sxs-lookup"><span data-stu-id="ac694-242">It won't work with https:.</span></span>          |<span data-ttu-id="ac694-243">必要</span><span class="sxs-lookup"><span data-stu-id="ac694-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="ac694-244">確認 Exchange 受信任子系統帳戶具有讀取、 寫入和 Execute 權限\\\\臨時\\的情況下 $ 共用。</span><span class="sxs-lookup"><span data-stu-id="ac694-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="ac694-245">PST 匯入指令碼需要下列兩個輸入的參數：</span><span class="sxs-lookup"><span data-stu-id="ac694-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="ac694-246">**$SourcePath**要匯入，例如 PST 檔案的位置\\\\臨時\\情況下 $。</span><span class="sxs-lookup"><span data-stu-id="ac694-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="ac694-247">**$MailboxAlias**將會收到的匯入電子郵件項目目標信箱的別名。</span><span class="sxs-lookup"><span data-stu-id="ac694-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="ac694-248">例如，如果您想要所有 PST 檔案匯都入從路徑\\Staging\Cases$ 到別名 eDiscoveryMailbox 信箱，您可執行類似的指令碼`\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。</span><span class="sxs-lookup"><span data-stu-id="ac694-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="ac694-249">Exchange Online 的 PST 匯入選項 B</span><span class="sxs-lookup"><span data-stu-id="ac694-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="ac694-250">建立要放入的匯入的 PST 檔案的信箱結構。</span><span class="sxs-lookup"><span data-stu-id="ac694-250">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="ac694-251">如需有關如何在 Exchange Online 中建立使用者信箱的詳細資訊，請參閱 <<c0>Exchange Online 中建立使用者信箱。</span><span class="sxs-lookup"><span data-stu-id="ac694-251">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="ac694-252">冷儲存體</span><span class="sxs-lookup"><span data-stu-id="ac694-252">Cold storage</span></span>

1. <span data-ttu-id="ac694-253">建立檔案共用上 Azure 虛擬機器，其中所有收集到的檔案放置位置，例如， \\ \\AZFile1\\ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="ac694-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="ac694-254">至少授與預設內容存取帳戶的讀取權限的共用和所有子資料夾及檔案。</span><span class="sxs-lookup"><span data-stu-id="ac694-254">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="ac694-255">如需設定 SharePoint 2013 搜尋的詳細資訊，請參閱[建立及設定 SharePoint Server 2013 中的 Search service 應用程式](https://go.microsoft.com/fwlink/p/?LinkId=614940)。</span><span class="sxs-lookup"><span data-stu-id="ac694-255">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="ac694-256">如果您預期匯入 PST 檔案從\\ \\AZFile1\\ContentColdStorage，授與 Exchange 受信任的子系統讀取、 寫入及執行共用的權限。</span><span class="sxs-lookup"><span data-stu-id="ac694-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="ac694-257">協調</span><span class="sxs-lookup"><span data-stu-id="ac694-257">Orchestrator</span></span>

1. <span data-ttu-id="ac694-258">從 Microsoft 下載中心下載[MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 。</span><span class="sxs-lookup"><span data-stu-id="ac694-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="ac694-259">開啟**Runbook 設計工具**，在 [**連線**] 窗格中，按一下您要匯入到 runbook 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac694-259">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="ac694-260">按一下 [**動作**] 功能表，然後按一下 [**匯入**]。</span><span class="sxs-lookup"><span data-stu-id="ac694-260">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="ac694-261">**匯入**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ac694-261">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="ac694-262">在 [**檔案位置**] 方塊中，輸入您要匯入、 runbook 路徑和檔案名稱，或按一下以瀏覽至您要匯入檔案的省略符號 （ **...**）。</span><span class="sxs-lookup"><span data-stu-id="ac694-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="ac694-263">選取 [**匯入 runbook**和**匯入協調加密的資料**。</span><span class="sxs-lookup"><span data-stu-id="ac694-263">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="ac694-264">清除**計數器**、**排程**、**變數**、**電腦群組**、**匯入全域設定**，並**覆寫現有的全域設定**。</span><span class="sxs-lookup"><span data-stu-id="ac694-264">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="ac694-265">按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ac694-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="ac694-266">編輯**MoveFilesToColdStorage** runbook，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac694-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="ac694-267">**移動檔案**活動的**來源檔案**將路徑設定為集合檔案共用，例如\\\\臨時\\情況下 $。</span><span class="sxs-lookup"><span data-stu-id="ac694-267">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="ac694-268">設定要冷儲存檔案的**目的資料夾**，例如共用 azure \\ \\AZFile1\\ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="ac694-268">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="ac694-269">選取 [**建立具有唯一名稱的檔案**。</span><span class="sxs-lookup"><span data-stu-id="ac694-269">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="ac694-270">**刪除資料夾**活動-設定**路徑：** 集合檔案共用，例如\\\\臨時\\情況下 $\\*，然後選取 [**刪除所有檔案及子資料夾**。</span><span class="sxs-lookup"><span data-stu-id="ac694-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="ac694-271">部署使用的程序中[部署 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120) **MoveToColdStorage** runbook。</span><span class="sxs-lookup"><span data-stu-id="ac694-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="ac694-272">SharePoint 內部部署搜尋冷儲存體</span><span class="sxs-lookup"><span data-stu-id="ac694-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="ac694-273">在 Azure 中冷儲存共用的 SharePoint 2013 伺服器陣列中建立新的內容來源，例如\\ \\AZFile1\\ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="ac694-273">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="ac694-274">如需管理內容來源的詳細資訊，請參閱[新增、 編輯或刪除 SharePoint Server 2013 中的內容來源](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="ac694-274">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="ac694-275">開始完整編目。</span><span class="sxs-lookup"><span data-stu-id="ac694-275">Start a full crawl.</span></span> <span data-ttu-id="ac694-276">如需詳細資訊，請參閱[啟動、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目](https://go.microsoft.com/fwlink/p/?LinkId=615005)。</span><span class="sxs-lookup"><span data-stu-id="ac694-276">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="ac694-277">使用解決方案</span><span class="sxs-lookup"><span data-stu-id="ac694-277">Using the solution</span></span>

<span data-ttu-id="ac694-278">使用此解決方案中，假設您不想要將 PST 檔案匯入 Exchange Server 2013 和 Exchange Online 中有五個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="ac694-278">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="ac694-279">本章節提供您的程序的全部。</span><span class="sxs-lookup"><span data-stu-id="ac694-279">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="ac694-280">您與解決方案的主要互動會處於執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac694-280">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="ac694-281">管理使用者 Custodians 群組的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ac694-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="ac694-282">檢閱登入指令碼所產生的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ac694-282">Review the log files generated by the logon script.</span></span> <span data-ttu-id="ac694-283">FileCopyErrors.log 列出所有未成功複製的檔案。</span><span class="sxs-lookup"><span data-stu-id="ac694-283">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="ac694-284">您必須先決定您想要與其做什麼</span><span class="sxs-lookup"><span data-stu-id="ac694-284">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="ac694-285">管理 PST 匯入程序。</span><span class="sxs-lookup"><span data-stu-id="ac694-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="ac694-286">將集合檔案移至冷儲存空間。</span><span class="sxs-lookup"><span data-stu-id="ac694-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="ac694-287">所有其他的步驟沒有特定此解決方案。</span><span class="sxs-lookup"><span data-stu-id="ac694-287">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="ac694-288">它們是您執行 SharePoint 2013 和 Office 365 和 Azure 中的標準系統管理工作。</span><span class="sxs-lookup"><span data-stu-id="ac694-288">They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure.</span></span> <span data-ttu-id="ac694-289">有此解決方案不會提供您想要計算出根據貴公司的需求，例如任何指引的項目：</span><span class="sxs-lookup"><span data-stu-id="ac694-289">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="ac694-290">追蹤您的 eDiscovery 案例，以及哪些 Custodians 相關聯這種情況。</span><span class="sxs-lookup"><span data-stu-id="ac694-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="ac694-291">追蹤的一組檔案集合所使用的 eDiscovery 案例的關聯。</span><span class="sxs-lookup"><span data-stu-id="ac694-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="ac694-292">協調匯入及移至冷儲存步驟的時間。</span><span class="sxs-lookup"><span data-stu-id="ac694-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="ac694-293">管理 Azure 中使用的檔案空間。</span><span class="sxs-lookup"><span data-stu-id="ac694-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="ac694-294">管理 Pst 匯入至信箱。</span><span class="sxs-lookup"><span data-stu-id="ac694-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="ac694-295">備份與還原作業的內部部署的所有資料。</span><span class="sxs-lookup"><span data-stu-id="ac694-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="ac694-296">Custodian 管理</span><span class="sxs-lookup"><span data-stu-id="ac694-296">Custodian management</span></span>

- <span data-ttu-id="ac694-297">若要啟動的個別使用者是自動化的檔案收集程序，請將其新增至 Custodians 群組。</span><span class="sxs-lookup"><span data-stu-id="ac694-297">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="ac694-298">下次登入時，會執行指派給透過群組原則 Custodians 群組的登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="ac694-298">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="ac694-299">監視收集到的檔案，然後檢閱記錄檔</span><span class="sxs-lookup"><span data-stu-id="ac694-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="ac694-300">觀賞集合檔案共用，例如\\\\臨時\\情況下 $\\*，從使用者的 [集合] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac694-300">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="ac694-301">資料夾的名稱會格式化像這樣： *yyyyMMddHHmm_UserName* 。</span><span class="sxs-lookup"><span data-stu-id="ac694-301">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="ac694-302">集合完成時，開啟集合資料夾，並瀏覽至 [_Log] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac694-302">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="ac694-303">在 [_Log] 資料夾中，您會看到下列訊息：</span><span class="sxs-lookup"><span data-stu-id="ac694-303">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="ac694-304">每個使用者的電腦，例如**A.xml**， **C.xml**上的本機磁碟機的一個 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ac694-304">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="ac694-305">這些檔案包含的庫存磁碟機之後，名為，它們會用於 robocopy 作業。</span><span class="sxs-lookup"><span data-stu-id="ac694-305">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="ac694-306">集合指令碼只會在本身的指令碼中所定義的檔案類型的庫存檔案中建立項目。</span><span class="sxs-lookup"><span data-stu-id="ac694-306">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="ac694-307">它不會建立使用者的電腦上的每個檔案的詳細目錄項目。</span><span class="sxs-lookup"><span data-stu-id="ac694-307">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="ac694-308">一個記錄檔名為 FileCopyErrors.log 執行每個集合。</span><span class="sxs-lookup"><span data-stu-id="ac694-308">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="ac694-309">此檔案包含的檔案清單該 robocopy 找不到檔案集合的複本共用，例如， \\\\臨時\\情況下 $\\*。</span><span class="sxs-lookup"><span data-stu-id="ac694-309">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="ac694-310">您必須檢閱這，並決定這些未接的檔案需要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ac694-310">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="ac694-311">通常，其中必須以手動方式收集它們，如果您希望他們，或您可能會決定他們不需要，因此可以省略從集合。</span><span class="sxs-lookup"><span data-stu-id="ac694-311">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="ac694-312">Exchange Server 2013 的 PST 匯入選項 A</span><span class="sxs-lookup"><span data-stu-id="ac694-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="ac694-313">登入伺服器主控集合檔案共用，例如**臨時**，並開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ac694-313">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="ac694-314">如需有關啟動 Windows PowerShell 的詳細資訊，請參閱 <<c0>Windows 伺服器上啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ac694-314">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="ac694-315">執行原則設為 Unrestricted。</span><span class="sxs-lookup"><span data-stu-id="ac694-315">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="ac694-316">型別`Set-ExecutionPolicy Unrestricted -Scope Process`到 Windows PowerShell]，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="ac694-316">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="ac694-317">執行 PSTImportScript.ps1 檔案，並提供的 **$SourcePath**和 **$MailboxAlias**參數。</span><span class="sxs-lookup"><span data-stu-id="ac694-317">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="ac694-318">如需有關執行 Windows PowerShell 指令碼的詳細資訊，請參閱 <<c0>執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="ac694-318">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="ac694-319">檢閱錯誤的輸出。</span><span class="sxs-lookup"><span data-stu-id="ac694-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="ac694-320">您嘗試同名的 PST 檔案匯入至同一個信箱之前，您必須先移除信箱匯入要求。</span><span class="sxs-lookup"><span data-stu-id="ac694-320">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="ac694-321">執行下列命令，以執行這項作業： `Get-MailboxImportRequest | Remove-MailboxImportRequest`。</span><span class="sxs-lookup"><span data-stu-id="ac694-321">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="ac694-322">系統會提示您從佇列中移除每個個別的要求。</span><span class="sxs-lookup"><span data-stu-id="ac694-322">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="ac694-323">視回應。</span><span class="sxs-lookup"><span data-stu-id="ac694-323">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="ac694-324">PST 匯入選項 B，Exchange Online</span><span class="sxs-lookup"><span data-stu-id="ac694-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="ac694-325">若要將收集的 PST 檔案放到 Exchange Online，請遵循到 Office 365 匯入檔案中的程序透過網路上傳] 區段中的[Office 365 匯入服務](https://go.microsoft.com/fwlink/p/?LinkId=614938)。</span><span class="sxs-lookup"><span data-stu-id="ac694-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="ac694-326">移至冷儲存體</span><span class="sxs-lookup"><span data-stu-id="ac694-326">Move to cold storage</span></span>

1. <span data-ttu-id="ac694-327">執行使用的程序中[執行 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123) **MoveToColdStorage** runbook。</span><span class="sxs-lookup"><span data-stu-id="ac694-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="ac694-328">監看式 Azure 檔案共用您用於長期存放區，例如\\ \\AZFile1\\ContentColdStorage 和內部集合檔案共用，例如\\\\臨時\\情況下 $。</span><span class="sxs-lookup"><span data-stu-id="ac694-328">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="ac694-329">您應該會看到檔案和資料夾會出現在冷儲存檔案共用，而且會從集合檔案共用中消失。</span><span class="sxs-lookup"><span data-stu-id="ac694-329">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="ac694-330">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="ac694-330">eDiscovery</span></span>

1. <span data-ttu-id="ac694-331">允許完整編目排程，以執行的冷儲存檔案共用，或啟動編目。</span><span class="sxs-lookup"><span data-stu-id="ac694-331">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="ac694-332">如需有關啟動完整或累加編目的詳細資訊，請參閱 <<c0>啟動、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目。</span><span class="sxs-lookup"><span data-stu-id="ac694-332">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="ac694-333">在 SharePoint 2013 中建立的 eDiscovery 案例，如果您使用選項的 PST 檔案匯入或 SharePoint Online 中建立 eDiscovery 案例，如果您使用選項 b。</span><span class="sxs-lookup"><span data-stu-id="ac694-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

