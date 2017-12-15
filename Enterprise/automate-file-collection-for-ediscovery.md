---
title: "自動化檔案集合 ediscovery （英文）"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
description: "摘要： 了解如何自動化 ediscovery （英文） 的使用者電腦從檔案集合。"
ms.openlocfilehash: 2c2a3d5d217203bb608fcb48f9cc1da8d4b49213
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="82e1a-103">自動化檔案集合 ediscovery （英文）</span><span class="sxs-lookup"><span data-stu-id="82e1a-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="82e1a-104">**摘要：**了解如何自動化 ediscovery （英文） 的使用者電腦從檔案集合。</span><span class="sxs-lookup"><span data-stu-id="82e1a-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="82e1a-p101">所有的公司正面可能會訴訟或其他類型的法律巨集指令。雖然法務部門可以使用，以減少的曝光度、 訴訟暫止的商務循環之事實。當公司朝法律巨集指令時，為必要項目，透過的法律調查，以提供所有相關的記錄運送巷以及一顧問程序。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="82e1a-p102">eDiscovery 是依據公司清查、 搜尋、 識別、 保留、 篩選和提供存在於相關記錄運送電子表單中的程序。SharePoint 2013、 Exchange Server 2013、 Lync Server 2013、 SharePoint Online 和 Exchange Online 可以保留大量的記錄的內容。根據版本，這些產品可能支援 eDiscovery 及就地保留 (透過 Exchange Server Lync)，讓更容易編製索引，法律小組的識別、 按住並篩選特定案例最相關的內容。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="82e1a-p103">許多文件會儲存在使用者電腦 (Custodians) 上本機電腦] 不在集中位置。這讓 SharePoint 2013 搜尋，基本上無法運用和無法搜尋，如果它不能包含 eDiscovery。此解決方案會示範如何使用登入指令碼、 System Center Orchestrator 2012 R2 和 Windows PowerShell for Exchange Server 自動化的識別資料及記錄資料從使用者電腦的集合。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="82e1a-114">此解決方案的沒有</span><span class="sxs-lookup"><span data-stu-id="82e1a-114">What this solution does</span></span>

<span data-ttu-id="82e1a-p104">此解決方案會使用通用安全群組，群組原則和 Windows PowerShell 指令碼來找出、 清查，及從使用者本機電腦收集的內容及 Outlook 個人存放區 (PST) 檔案到隱藏的檔案共用。從該處、 PST 檔案可以匯入 Exchange Server 2013 或 Exchange Online。所有檔案會再都移到另一個檔案共用 System Center Orchestrator 2012 R2 runbook in Microsoft Azure 至長期儲存區及索引如使用 SharePoint 2013。然後您使用 eDiscovery 中心在內部部署 SharePoint 2013 部署或 SharePoint Online 中一樣定期才能執行 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="82e1a-p105">此解決方案使用 robocopy 檔案複製至集中的檔案共用 okay 的電腦。因為 robocopy 不會複製檔案開啟或鎖定，任何檔案，包括 okay 已開啟的 PST 檔案系統不會收集。您必須以手動方式加以收集。此解決方案沒有提供給您明確地識別它不能將複製的檔案清單與每個檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="82e1a-123">下圖會帶領您完成所有步驟及的解決方案項目。</span><span class="sxs-lookup"><span data-stu-id="82e1a-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![自動化檔案收集解決方案的概觀](images/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="82e1a-125">圖例 * * *</span><span class="sxs-lookup"><span data-stu-id="82e1a-125">****Legend****</span></span>||
|:-----|:-----|
|![洋紅色圖說文字 1](images/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="82e1a-127">建立群組原則物件 (GPO)，並將其關聯集合登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="82e1a-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![洋紅色圖說文字 2](images/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="82e1a-129">設定 GPO 僅套用至 Custodians 群組的 GPO 安全性篩選。</span><span class="sxs-lookup"><span data-stu-id="82e1a-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![洋紅色圖說文字 3](images/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="82e1a-131">Okay 登入並執行 GPO，呼叫集合登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="82e1a-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![洋紅色圖說文字 4](images/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="82e1a-133">集合登入指令碼清查搜尋您想將的檔案及記錄其位置 Custodians 電腦上的所有附加在本機磁碟機。</span><span class="sxs-lookup"><span data-stu-id="82e1a-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![洋紅色圖說文字 5](images/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="82e1a-135">集合登入指令碼會將清查的檔案複製到臨時伺服器上的隱藏的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![洋紅色圖說文字 6](images/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="82e1a-137">（選項的）手動執行要收集的 PST 檔案匯入 Exchange Server 2013 的 PST 匯入指令碼。</span><span class="sxs-lookup"><span data-stu-id="82e1a-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![洋紅色圖說文字 7](images/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="82e1a-139">（選項 B）使用 Office 365 匯入工具及程序，匯入收集的 PST 檔案 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="82e1a-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![洋紅色圖說文字 8](images/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="82e1a-141">將所有收集的檔案移至長期儲存與 MoveToColdStorage System Center Orchestrator 2012 R2 runbook Azure 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![洋紅色圖說文字 9](images/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="82e1a-143">索引中與 SharePoint 2013 的寒冷儲存檔案共用的檔案。</span><span class="sxs-lookup"><span data-stu-id="82e1a-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![洋紅色圖說文字 10](images/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="82e1a-145">執行 eDiscovery 寒冷儲存區與內部部署 Exchange Server 2013 中的內容。</span><span class="sxs-lookup"><span data-stu-id="82e1a-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![洋紅色圖說文字 11](images/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="82e1a-147">在 Office 365 中的內容上執行 eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="82e1a-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="82e1a-148">必要條件</span><span class="sxs-lookup"><span data-stu-id="82e1a-148">Prerequisites</span></span>

<span data-ttu-id="82e1a-p106">此解決方案的設定需要許多元素最其中您可能已經備妥及設定若您的想法有關 eDiscovery。元素可能沒有或類需要特定設定，我們將會提供您下列連結，您需要建立取出您基底的設定。您必須基本組態備妥之前設定本身的解決方案。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="82e1a-152">基本組態</span><span class="sxs-lookup"><span data-stu-id="82e1a-152">Base configuration</span></span>

|<span data-ttu-id="82e1a-153">**項目**</span><span class="sxs-lookup"><span data-stu-id="82e1a-153">**Element**</span></span>|<span data-ttu-id="82e1a-154">**連結**</span><span class="sxs-lookup"><span data-stu-id="82e1a-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="82e1a-155">Active Directory 網域服務 (AD DS) 網域</span><span class="sxs-lookup"><span data-stu-id="82e1a-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="82e1a-156">從內部網路的網際網路連線能力</span><span class="sxs-lookup"><span data-stu-id="82e1a-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="82e1a-157">SQL Server 2012 支援 SharePoint 2013 和 System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="82e1a-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="82e1a-158">部署 System Center Orchestrator-2012</span><span class="sxs-lookup"><span data-stu-id="82e1a-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="82e1a-159">內部部署或 Azure 基礎 SharePoint 2013 的 eDiscovery （所需的選項的）</span><span class="sxs-lookup"><span data-stu-id="82e1a-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="82e1a-160">內部檔案共用伺服器的臨時</span><span class="sxs-lookup"><span data-stu-id="82e1a-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="82e1a-161">內部部署 Exchange Server 2013 選項 PST 匯入</span><span class="sxs-lookup"><span data-stu-id="82e1a-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="82e1a-162">CU5 (15.913.22) 位於[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="82e1a-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="82e1a-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="82e1a-164">部署 System Center Orchestrator-2012</span><span class="sxs-lookup"><span data-stu-id="82e1a-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="82e1a-165">Office 365 （E3 規劃） 與 Exchange Online 和 SharePoint Online （所需的選項 B）</span><span class="sxs-lookup"><span data-stu-id="82e1a-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="82e1a-166">若要註冊 Office 365 E3 訂閱，請參閱[Office 365 E3 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=613504)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="82e1a-167">Azure 虛擬機器與訂閱</span><span class="sxs-lookup"><span data-stu-id="82e1a-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="82e1a-168">若要註冊 Azure，請參閱[訂閱至 Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="82e1a-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="82e1a-169">在內部網路和 Azure 訂閱間 VPN 連線</span><span class="sxs-lookup"><span data-stu-id="82e1a-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="82e1a-170">若要設定在 Azure 的訂閱與您的內部網路之間 VPN 通道，請參閱[Connect Microsoft Azure 虛擬網路的內部網路](https://go.microsoft.com/fwlink/p/?LinkId=613507)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="82e1a-171">SharePoint 2013 的 eDiscovery 來搜尋整個 SharePoint 與 Exchange Server 2013 與 Lync Server 2013 （選用） 設定</span><span class="sxs-lookup"><span data-stu-id="82e1a-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="82e1a-172">若要設定的 eDiscovery 這種方式，請參閱[Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508)和[Test Lab Guide: Exchange、 Lync、 SharePoint 及 Windows 檔案共用測試實驗室中設定 eDiscovery](https://go.microsoft.com/fwlink/p/?LinkId=393130)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="82e1a-173">Office 365 中的 SharePoint Online 和 Exchange Online 的 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="82e1a-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="82e1a-174">若要在 Office 365 中設定 eDiscovery，請參閱[設定 eDiscovery 中心 SharePoint Online 中](https://go.microsoft.com/fwlink/p/?LinkId=613628)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="82e1a-175">設定環境</span><span class="sxs-lookup"><span data-stu-id="82e1a-175">Configure the environment</span></span>

<span data-ttu-id="82e1a-176">既然您已經備妥的基底的設定，您可以移動預先設定本身的解決方案。</span><span class="sxs-lookup"><span data-stu-id="82e1a-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="82e1a-177">臨時檔案共用</span><span class="sxs-lookup"><span data-stu-id="82e1a-177">Staging file share</span></span>

1. <span data-ttu-id="82e1a-178">在內部部署網域中建立通用安全性群組名為 Custodians。</span><span class="sxs-lookup"><span data-stu-id="82e1a-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="82e1a-p107">建立從 Custodians 電腦收集的檔案隱藏的檔案共用。這應該是在內部部署伺服器上。例如，在呼叫臨時伺服器上建立的檔案共用呼叫的情況下 $。**$** ，才能將此設為隱藏的共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="82e1a-183">設定下列共用權限：</span><span class="sxs-lookup"><span data-stu-id="82e1a-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="82e1a-184">Custodians： 變更，請閱讀</span><span class="sxs-lookup"><span data-stu-id="82e1a-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="82e1a-185">系統管理員：完全控制</span><span class="sxs-lookup"><span data-stu-id="82e1a-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="82e1a-186">Exchange 信任的子系統： 變更，請閱讀</span><span class="sxs-lookup"><span data-stu-id="82e1a-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="82e1a-p108">開啟 [**安全性**] 索引標籤、 新增 Custodians] 群組中，並按一下 [**進階**]。設定 [Custodians 群組中的下列權限：</span><span class="sxs-lookup"><span data-stu-id="82e1a-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="82e1a-189">**類型： 拒絕**</span><span class="sxs-lookup"><span data-stu-id="82e1a-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="82e1a-190">**適用於： 這個資料夾、 子資料夾和檔案**</span><span class="sxs-lookup"><span data-stu-id="82e1a-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="82e1a-191">按一下 [**進階權限**並選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="82e1a-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="82e1a-192">**讀取屬性**</span><span class="sxs-lookup"><span data-stu-id="82e1a-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="82e1a-193">**讀取擴充屬性**</span><span class="sxs-lookup"><span data-stu-id="82e1a-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="82e1a-194">**讀取權限**</span><span class="sxs-lookup"><span data-stu-id="82e1a-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="82e1a-195">測試共用的存取權的情況下 $ 檔案執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="82e1a-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="82e1a-196">將使用者新增至 Custodians 群組。</span><span class="sxs-lookup"><span data-stu-id="82e1a-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="82e1a-197">將檔案的情況下 $ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="82e1a-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="82e1a-p109">為使用者、 瀏覽至臨時伺服器，例如瀏覽至\\\\臨時查看哪些共用所提供的共用。您不應該會看到所列的**情況下 $**共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="82e1a-p110">手動輸入瀏覽器的情況下 $ 共用的完整路徑。這應該會開啟的情況下 $ 共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="82e1a-p111">嘗試開啟之前放在共用的檔案。這應該會失敗。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="82e1a-204">登入指令碼</span><span class="sxs-lookup"><span data-stu-id="82e1a-204">Logon script</span></span>

1. <span data-ttu-id="82e1a-205">複製並貼入 [記事本] 中的此 Windows PowerShell 指令碼：</span><span class="sxs-lookup"><span data-stu-id="82e1a-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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
    $TargetFileCheck = Test-Path $TargetPath\\$FileName

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
$CaseRootLocation = "\\\\staging\\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_Log"
$CasePSTLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\\\\$_.xml -Force
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

2. <span data-ttu-id="82e1a-206">為 CollectionScript.ps1 更容易找到，例如 c： 的位置中儲存上面的指令碼\\AFCScripts。</span><span class="sxs-lookup"><span data-stu-id="82e1a-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="82e1a-p112">在 [記事本] 中使用移至] 功能。視需要進行變更如下：</span><span class="sxs-lookup"><span data-stu-id="82e1a-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="82e1a-209">**線條 #**</span><span class="sxs-lookup"><span data-stu-id="82e1a-209">**Line #**</span></span>|<span data-ttu-id="82e1a-210">**您需要變更**</span><span class="sxs-lookup"><span data-stu-id="82e1a-210">**What you need to change**</span></span>|<span data-ttu-id="82e1a-211">**所需/選用**</span><span class="sxs-lookup"><span data-stu-id="82e1a-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="82e1a-212">71</span><span class="sxs-lookup"><span data-stu-id="82e1a-212">71</span></span>  <br/> |<span data-ttu-id="82e1a-p113">**$FileTypes**變數。包含您想要清查並收集陣列變數中的指令碼的所有檔案類型副檔名。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="82e1a-215">選用</span><span class="sxs-lookup"><span data-stu-id="82e1a-215">Optional</span></span>  <br/> |
|<span data-ttu-id="82e1a-216">76 和 77</span><span class="sxs-lookup"><span data-stu-id="82e1a-216">76 and 77</span></span>  <br/> |<span data-ttu-id="82e1a-p114">變更的方式**$CaseNo**變數內建以符合您的需求。指令碼擷取目前的日期及時間並將它附加的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="82e1a-219">選用</span><span class="sxs-lookup"><span data-stu-id="82e1a-219">Optional</span></span>  <br/> |
|<span data-ttu-id="82e1a-220">80</span><span class="sxs-lookup"><span data-stu-id="82e1a-220">80</span></span>  <br/> |<span data-ttu-id="82e1a-221">**$CaseRootLocation**變數必須設為您的臨時伺服器集合檔案共用，例如**\\\\臨時\\情況下 $**。</span><span class="sxs-lookup"><span data-stu-id="82e1a-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="82e1a-222">必要</span><span class="sxs-lookup"><span data-stu-id="82e1a-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="82e1a-223">CollectionScript.ps1 檔案放在網域控制站的 Netlogon 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="82e1a-224">設定 GPO 登入指令碼和 Custodians 群組</span><span class="sxs-lookup"><span data-stu-id="82e1a-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="82e1a-225">遵循下列主題，[使用啟動、 關閉、 登入和登出指令碼在群組原則中](https://go.microsoft.com/fwlink/p/?LinkId=614844)的"如何指派使用者登入指令碼 」 一節中設定 Custodians 群組的登入指令碼。</span><span class="sxs-lookup"><span data-stu-id="82e1a-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="82e1a-226">移除已驗證的使用者**安全性篩選**，並新增 Custodians 群組。</span><span class="sxs-lookup"><span data-stu-id="82e1a-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="82e1a-227">PST 匯入選項 A、 Exchange Server 2013 的指令碼</span><span class="sxs-lookup"><span data-stu-id="82e1a-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="82e1a-228">複製並貼入 [記事本] 中的下列 Windows PowerShell 指令碼：</span><span class="sxs-lookup"><span data-stu-id="82e1a-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\\PSTImport.ps1 \\\\FileShare\\PSTFiles jdoe

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

2. <span data-ttu-id="82e1a-p115">將指令碼儲存為 PSTImportScript.ps1 中更容易尋找的位置。範例和方便使用，建立資料夾呼叫臨時伺服器上\\\\臨時\\AFCScripts，並將其儲存到那里。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="82e1a-231">使用 [記事本] 中移至功能並視需要進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="82e1a-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="82e1a-232">**線條 #**</span><span class="sxs-lookup"><span data-stu-id="82e1a-232">**Line #**</span></span>|<span data-ttu-id="82e1a-233">**您需要變更**</span><span class="sxs-lookup"><span data-stu-id="82e1a-233">**What you need to change**</span></span>|<span data-ttu-id="82e1a-234">**所需/選用**</span><span class="sxs-lookup"><span data-stu-id="82e1a-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="82e1a-235">12</span><span class="sxs-lookup"><span data-stu-id="82e1a-235">12</span></span>  <br/> |<span data-ttu-id="82e1a-p116">**$FolderIdentifier** tags Pst 所匯入的信箱資料夾。這在必要時變更。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="82e1a-238">選用</span><span class="sxs-lookup"><span data-stu-id="82e1a-238">Optional</span></span>  <br/> |
|<span data-ttu-id="82e1a-239">第 17</span><span class="sxs-lookup"><span data-stu-id="82e1a-239">17</span></span>  <br/> |<span data-ttu-id="82e1a-240">**$ConnectionUri**必須設為您自己的伺服器。</span><span class="sxs-lookup"><span data-stu-id="82e1a-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="82e1a-p117">> [!IMPORTANT]> 確定您**$ConnectionUri**指引的 http 位置，而不是 https。將不會使用 https:。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="82e1a-243">必要</span><span class="sxs-lookup"><span data-stu-id="82e1a-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="82e1a-244">確認 Exchange 受信任子系統帳戶是否有讀取、 寫入、 和執行權限\\\\臨時\\的情況下 $ 共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="82e1a-245">PST 匯入指令碼需要下列兩個輸入的參數：</span><span class="sxs-lookup"><span data-stu-id="82e1a-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="82e1a-246">**$SourcePath**要匯入，例如 PST 檔案的位置\\\\臨時\\情況下 $。</span><span class="sxs-lookup"><span data-stu-id="82e1a-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="82e1a-247">**$MailboxAlias**將會收到匯入的電子郵件項目的目標信箱的別名。</span><span class="sxs-lookup"><span data-stu-id="82e1a-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="82e1a-248">例如，如果您想要匯入所有 PST 檔案的路徑\\\\臨時\\轉換與別名 eDiscoveryMailbox 信箱的情況下 $、 您可執行類似的指令碼`\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`。</span><span class="sxs-lookup"><span data-stu-id="82e1a-248">For example, if you want to import all the PST files from the path \\\\Staging\\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="82e1a-249">Exchange Online 的 PST 匯入選項 B</span><span class="sxs-lookup"><span data-stu-id="82e1a-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="82e1a-p118">建立信箱結構放入的匯入的 PST 檔案。如需如何在 Exchange Online 中建立使用者信箱的詳細資訊，請參閱[Exchange Online 中建立使用者信箱](https://go.microsoft.com/fwlink/p/?LinkId=615118)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="82e1a-252">冷存放區</span><span class="sxs-lookup"><span data-stu-id="82e1a-252">Cold storage</span></span>

1. <span data-ttu-id="82e1a-253">建立的檔案共用上 Azure 虛擬機器，所有收集的檔案放置，例如\\ \\AZFile1\\ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="82e1a-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="82e1a-p119">至少授與預設內容存取帳戶的讀取權限的共用和所有子資料夾和檔案。如需設定 SharePoint 2013 搜尋的詳細資訊，請參閱[建立及設定 SharePoint Server 2013 中的 Search service 應用程式](https://go.microsoft.com/fwlink/p/?LinkId=614940)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="82e1a-256">如果您預期匯入 PST 檔案從\\ \\AZFile1\\ContentColdStorage，授與 Exchange 受信任的子系統讀取、 寫入及執行之共用的權限。</span><span class="sxs-lookup"><span data-stu-id="82e1a-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="82e1a-257">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="82e1a-257">Orchestrator</span></span>

1. <span data-ttu-id="82e1a-258">從 Microsoft 下載中心下載[MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 。</span><span class="sxs-lookup"><span data-stu-id="82e1a-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="82e1a-p120">開啟**Runbook 設計工具**] 的 [**連線**] 窗格中，按一下您要匯入到 runbook 的資料夾。按一下 [**動作**] 功能表，然後按一下 [**匯入**]。**匯入**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="82e1a-262">在 [**檔案位置**] 方塊中輸入您想要匯入 runbook 的路徑和檔案名稱或按一下 [瀏覽至您要匯入檔案的省略符號 （ **...**）。</span><span class="sxs-lookup"><span data-stu-id="82e1a-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="82e1a-p121">選取 [**匯入 runbooks**和**匯入 Orchestrator 加密資料**。清除**計數器**、**排程**、**變數**、 **Computer Groups**、**匯入通用設定**，以及**要覆寫現有的全域設定**。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="82e1a-265">按一下 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="82e1a-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="82e1a-266">編輯**MoveFilesToColdStorage** runbook，如下所示：</span><span class="sxs-lookup"><span data-stu-id="82e1a-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="82e1a-p122">**移動檔案**活動-設定的**來源檔案**路徑為集合檔案共用，例如\\\\臨時\\情況下 $。設定要寒冷儲存檔案的**目的資料夾**中的共用 Azure，例如\\ \\AZFile1\\ContentColdStorage。選取 [**建立的檔案使用唯一的名稱**。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="82e1a-270">**刪除資料夾**活動-設定**路徑：**集合檔案共用，例如\\\\臨時\\情況下 $\\*，然後選取 [**刪除所有檔案及子資料夾**。</span><span class="sxs-lookup"><span data-stu-id="82e1a-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="82e1a-271">部署使用本節的程序中[部署 Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120) **MoveToColdStorage** runbook。</span><span class="sxs-lookup"><span data-stu-id="82e1a-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="82e1a-272">SharePoint 內部部署搜尋寒冷存放區</span><span class="sxs-lookup"><span data-stu-id="82e1a-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="82e1a-p123">例如在 Azure、 寒冷儲存共用的 SharePoint 2013 伺服器陣列中建立新的內容來源\\ \\AZFile1\\ContentColdStorage。如需管理內容來源的詳細資訊，請參閱[新增、 編輯或刪除 SharePoint Server 2013 中的內容來源](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="82e1a-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="82e1a-p124">開始完整編目。如需詳細資訊，請參閱[開始、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目](https://go.microsoft.com/fwlink/p/?LinkId=615005)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="82e1a-277">使用解決方案</span><span class="sxs-lookup"><span data-stu-id="82e1a-277">Using the solution</span></span>

<span data-ttu-id="82e1a-p125">使用此解決方案假設您不想將 PST 檔案匯入 Exchange Server 2013 和 Exchange Online 中有五個主要步驟。本節提供本節的程序的所有這些。您解決方案的主要互動將處於執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="82e1a-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="82e1a-281">管理使用者 Custodians 群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="82e1a-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="82e1a-p126">檢閱登入指令碼所產生的記錄檔。FileCopyErrors.log 列出所有不成功複製的檔案。您必須決定您要執行操作</span><span class="sxs-lookup"><span data-stu-id="82e1a-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="82e1a-285">管理 PST 匯入程序。</span><span class="sxs-lookup"><span data-stu-id="82e1a-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="82e1a-286">將集合檔案移至寒冷存放區。</span><span class="sxs-lookup"><span data-stu-id="82e1a-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="82e1a-p127">所有其他步驟不專屬於此解決方案。可讓您執行 SharePoint 2013 與 Office 365 和 Azure 中的標準系統管理工作。有此解決方案未提供任何您將需要合作根據公司的需求，例如的指導的項目：</span><span class="sxs-lookup"><span data-stu-id="82e1a-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="82e1a-290">追蹤您的 eDiscovery 案例和 Custodians 相關聯這種情況。</span><span class="sxs-lookup"><span data-stu-id="82e1a-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="82e1a-291">追蹤的一組檔案集合所使用的 eDiscovery 案例的關聯。</span><span class="sxs-lookup"><span data-stu-id="82e1a-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="82e1a-292">協調匯入及移至寒冷儲存步驟的時機。</span><span class="sxs-lookup"><span data-stu-id="82e1a-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="82e1a-293">管理 Azure 中使用的檔案空間。</span><span class="sxs-lookup"><span data-stu-id="82e1a-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="82e1a-294">管理 Pst 所匯入至信箱。</span><span class="sxs-lookup"><span data-stu-id="82e1a-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="82e1a-295">備份及還原的內部部署的所有資料。</span><span class="sxs-lookup"><span data-stu-id="82e1a-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="82e1a-296">Okay 管理</span><span class="sxs-lookup"><span data-stu-id="82e1a-296">Custodian management</span></span>

- <span data-ttu-id="82e1a-p128">若要啟動個別使用者的自動化的檔案集合程序，將其新增至 Custodians 群組。使用者登入時，下一次登入指令碼指定給 Custodians 群組透過群組原則將會執行。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="82e1a-299">監視收集的檔案及檢閱記錄檔</span><span class="sxs-lookup"><span data-stu-id="82e1a-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="82e1a-p129">觀賞集合檔案共用，例如\\\\臨時\\情況下 $\\*，從使用者的集合資料夾。資料夾的名稱將格式設定如下： *yyyyMMddHHmm_UserName* 。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="82e1a-p130">集合完成時，開啟集合資料夾，並瀏覽至 [_Log] 資料夾。在 [_Log] 資料夾中，您會看到下列項目：</span><span class="sxs-lookup"><span data-stu-id="82e1a-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="82e1a-p131">每個使用者的電腦，例如**A.xml**、 **C.xml**上的本機磁碟機的一個 XML 檔案。這些檔案包含的庫存磁碟機之後，名為並使用 robocopy 作業。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="82e1a-p132">集合指令碼僅會在本身的指令碼中所定義的檔案類型的庫存檔案中建立項目。它將不會建立使用者的電腦上每個檔案的詳細目錄項目。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="82e1a-p133">一個記錄檔名為 FileCopyErrors.log 執行每個集合。這個檔案包含的檔案清單該 robocopy 可能無法複製到檔案集合共用，例如\\\\臨時\\情況下 $\\*。您必須檢閱這並決定這些未接的檔案需要採取的動作。通常，您其中一個需要收集這些手動如果您想讓他們，或您可能會決定他們不需要與因此可以省略集合中。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="82e1a-312">PST 匯入] 選項的 Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="82e1a-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="82e1a-p134">登入伺服器主控集合檔案共用，例如**臨時**，並開啟 Windows PowerShell。如需啟動 Windows PowerShell 的詳細資訊，請參閱 ＜[Windows Server 上啟動 Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=615115)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="82e1a-p135">將執行原則設定為 [沒有限制。類型`Set-ExecutionPolicy Unrestricted -Scope Process`到 Windows PowerShell]，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="82e1a-p136">執行 PSTImportScript.ps1 檔，並提供**$SourcePath**與**$MailboxAlias**參數。如需執行 Windows PowerShell 指令碼的詳細資訊，請參閱[執行指令碼](https://go.microsoft.com/fwlink/p/?LinkID=615117)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="82e1a-319">檢閱錯誤的輸出。</span><span class="sxs-lookup"><span data-stu-id="82e1a-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="82e1a-p137">您嘗試同名具名的 PST 檔案匯入至相同信箱，您必須先移除信箱匯入要求。執行下列命令以這樣： `Get-MailboxImportRequest | Remove-MailboxImportRequest`。系統會提示您從佇列移除每個個別的要求。視回應。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="82e1a-324">Exchange online 的 PST 匯入選項 B</span><span class="sxs-lookup"><span data-stu-id="82e1a-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="82e1a-325">若要將收集的 PST 檔案放入 Exchange Online，遵循匯入檔案中的程序到 Office 365 透過網路上傳] 區段中的[Office 365 匯入服務](https://go.microsoft.com/fwlink/p/?LinkId=614938)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="82e1a-326">移至寒冷存放區</span><span class="sxs-lookup"><span data-stu-id="82e1a-326">Move to cold storage</span></span>

1. <span data-ttu-id="82e1a-327">執行使用本節的程序中[執行 Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123) **MoveToColdStorage** runbook。</span><span class="sxs-lookup"><span data-stu-id="82e1a-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="82e1a-p138">觀賞 Azure 檔案共用您用於長字詞儲存區，例如\\ \\AZFile1\\ContentColdStorage 與內部部署集合檔案共用，例如\\\\臨時\\情況下 $。您應該會看到檔案及資料夾會出現在寒冷儲存的檔案共用及消失從集合檔案共用。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="82e1a-330">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="82e1a-330">eDiscovery</span></span>

1. <span data-ttu-id="82e1a-p139">可允許寒冷儲存的檔案共用作為排程執行完整編目或啟動編目。如需有關啟動完整或累加編目的詳細資訊，請參閱 ＜[啟動、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目](https://go.microsoft.com/fwlink/p/?LinkId=615005)。</span><span class="sxs-lookup"><span data-stu-id="82e1a-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="82e1a-333">如果您使用 PST 檔案匯入] 選項的 SharePoint 2013 中建立 eDiscovery 案例或建立在 SharePoint Online 中的 eDiscovery 案例如果您是使用選項 b。</span><span class="sxs-lookup"><span data-stu-id="82e1a-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

