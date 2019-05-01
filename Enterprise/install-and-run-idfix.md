---
title: 安裝和執行 Office 365 IdFix 工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何安裝和執行 Office 365 IdFix 工具，您將它同步處理至 Office 365 之前清除您的 active directory 幫助。
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487991"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="afe04-103">安裝和執行 Office 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="afe04-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="afe04-104">IdFix 識別錯誤，例如重複項目及格式化您的目錄中的問題，再進行同步處理至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="afe04-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="afe04-105">若要順利完成此工作，您應該滿意與使用者、 群組及 Active Directory 中的連絡人物件。</span><span class="sxs-lookup"><span data-stu-id="afe04-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="afe04-106">如果您無法完成此工作，有幾個可以執行其他作業。</span><span class="sxs-lookup"><span data-stu-id="afe04-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="afe04-107">這些方法可能比較方便，但他們也可能需要花費更多或有其他缺點。</span><span class="sxs-lookup"><span data-stu-id="afe04-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="afe04-108">其為：</span><span class="sxs-lookup"><span data-stu-id="afe04-108">They are:</span></span>
  
- <span data-ttu-id="afe04-109">**未執行 IdFix 執行目錄同步處理。**</span><span class="sxs-lookup"><span data-stu-id="afe04-109">**Run directory synchronization without running IdFix.**</span></span> <span data-ttu-id="afe04-110">您可以將您的目錄同步處理未執行 IdFix 工具，但我們不建議此做法。</span><span class="sxs-lookup"><span data-stu-id="afe04-110">You can synchronize your directory without running the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="afe04-111">修正錯誤再進行同步處理會採用較少的時間，並通常提供更順暢地轉換至雲端。</span><span class="sxs-lookup"><span data-stu-id="afe04-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="afe04-112">**雇用顧問。**</span><span class="sxs-lookup"><span data-stu-id="afe04-112">**Hire a consultant.**</span></span> <span data-ttu-id="afe04-113">取得專家說明可以開始您的使用者，並快速地執行與您的目錄同步處理。</span><span class="sxs-lookup"><span data-stu-id="afe04-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="afe04-114">您必須執行 IdFix</span><span class="sxs-lookup"><span data-stu-id="afe04-114">What you need to run IdFix</span></span>

<span data-ttu-id="afe04-115">最簡單方式以取得 IdFix 和執行是安裝在已加入網域的電腦上。</span><span class="sxs-lookup"><span data-stu-id="afe04-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="afe04-116">您可以執行它在網域控制站如果您想，但這不是必要。</span><span class="sxs-lookup"><span data-stu-id="afe04-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="afe04-117">IdFix 硬體需求</span><span class="sxs-lookup"><span data-stu-id="afe04-117">IdFix hardware requirements</span></span>

<span data-ttu-id="afe04-118">安裝 IdFix 的電腦必須符合下列基本硬體需求：</span><span class="sxs-lookup"><span data-stu-id="afe04-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="afe04-119">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="afe04-119">4 GB RAM</span></span>
- <span data-ttu-id="afe04-120">2 GB 的硬碟空間</span><span class="sxs-lookup"><span data-stu-id="afe04-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="afe04-121">IdFix 軟體需求</span><span class="sxs-lookup"><span data-stu-id="afe04-121">IdFix software requirements</span></span>

<span data-ttu-id="afe04-122">安裝 IdFix 的電腦必須加入至您要使用者同步處理至 Office 365 的同一個 Active Directory 網域。</span><span class="sxs-lookup"><span data-stu-id="afe04-122">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365.</span></span> <span data-ttu-id="afe04-123">電腦也必須已安裝的.NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="afe04-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="afe04-124">如果您執行 Windows Server 2008 或 Windows Server 2012，是可能已經安裝.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="afe04-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="afe04-125">如果不是，您可以[下載從下載中心.NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475)或透過 Windows Update。</span><span class="sxs-lookup"><span data-stu-id="afe04-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="afe04-126">IdFix 權限需求</span><span class="sxs-lookup"><span data-stu-id="afe04-126">IdFix permissions requirements</span></span>

<span data-ttu-id="afe04-127">執行 IdFix 所使用的使用者帳戶必須具有讀取/寫入存取的目錄。</span><span class="sxs-lookup"><span data-stu-id="afe04-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="afe04-128">如果您不確定您的使用者帳戶符合這些需求，而且您不確定如何檢查，但您仍會安裝，並執行 IdFix。</span><span class="sxs-lookup"><span data-stu-id="afe04-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix.</span></span> <span data-ttu-id="afe04-129">如果您的使用者帳戶沒有適當的權限，IdFix 只會顯示錯誤時您嘗試執行它。</span><span class="sxs-lookup"><span data-stu-id="afe04-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="afe04-130">安裝 IdFix</span><span class="sxs-lookup"><span data-stu-id="afe04-130">Install IdFix</span></span>

<span data-ttu-id="afe04-131">若要安裝 IdFix，下載並解壓縮**IdFix.exe**:</span><span class="sxs-lookup"><span data-stu-id="afe04-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="afe04-132">登入您要安裝 IdFix 工具的電腦。</span><span class="sxs-lookup"><span data-stu-id="afe04-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="afe04-133">請移至 Microsoft 下載網站[IdFix DirSync 錯誤補救工具](https://go.microsoft.com/fwlink/?linkid=867219)。</span><span class="sxs-lookup"><span data-stu-id="afe04-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="afe04-134">選擇 [**下載**]。</span><span class="sxs-lookup"><span data-stu-id="afe04-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="afe04-135">出現提示時，選擇 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="afe04-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="afe04-136">在 [ **WinZip Self-extractor** ] 對話方塊中 [**解壓縮到資料夾**] 文字方塊中，輸入或瀏覽至您要安裝 IdFix 工具的位置。</span><span class="sxs-lookup"><span data-stu-id="afe04-136">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool.</span></span> <span data-ttu-id="afe04-137">根據預設，安裝 IdFix `C:\Deployment Tools\`。</span><span class="sxs-lookup"><span data-stu-id="afe04-137">By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="afe04-138">選擇 [**解壓縮**]。</span><span class="sxs-lookup"><span data-stu-id="afe04-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="afe04-139">執行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="afe04-139">Run the IdFix tool</span></span>

<span data-ttu-id="afe04-140">安裝 IdFix 之後，請執行工具來搜尋您目錄中的問題：</span><span class="sxs-lookup"><span data-stu-id="afe04-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="afe04-141">使用具有目錄讀/寫存取權的帳戶，登入安裝 IdFix 的電腦。</span><span class="sxs-lookup"><span data-stu-id="afe04-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="afe04-142">在檔案總管] 中，移至您安裝 IdFix 的位置。</span><span class="sxs-lookup"><span data-stu-id="afe04-142">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="afe04-143">如果您在安裝期間選擇的預設資料夾，請移至`C:\Deployment Tools\IdFix`。</span><span class="sxs-lookup"><span data-stu-id="afe04-143">If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="afe04-144">按兩下 [ **IdFix.exe**]。</span><span class="sxs-lookup"><span data-stu-id="afe04-144">Double-click **IdFix.exe**.</span></span> 
    
    ![選擇 [IdFix.exe 檔案。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="afe04-146">依預設，IdFix 會使用多重租用戶規則設定為在您的目錄中測試項目。</span><span class="sxs-lookup"><span data-stu-id="afe04-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="afe04-147">這是正確的規則集對於大多數的 Office 365 客戶。</span><span class="sxs-lookup"><span data-stu-id="afe04-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="afe04-148">不過，如果您是 Office 365 專用或 ITAR （國際流量武器法規） 客戶，您可以設定要使用的專用的規則集改為 IdFix。</span><span class="sxs-lookup"><span data-stu-id="afe04-148">However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="afe04-149">如果您不確定哪種您的客戶，您可以放心地略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="afe04-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="afe04-150">若要設定設定為專用的規則，按一下功能表列中的齒輪圖示，然後選擇 [**專用**。</span><span class="sxs-lookup"><span data-stu-id="afe04-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="afe04-151">選擇 [**查詢**]。</span><span class="sxs-lookup"><span data-stu-id="afe04-151">Choose **Query**.</span></span>
    
    ![在 IdFix 中，選擇 [查詢。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="afe04-153">根據預設，IdFix 會搜尋整個目錄中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe04-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="afe04-154">根據您目錄的大小，執行查詢可能需要一段時間。</span><span class="sxs-lookup"><span data-stu-id="afe04-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="afe04-155">您可以查看在工具主視窗底部的進度。</span><span class="sxs-lookup"><span data-stu-id="afe04-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="afe04-156">如果您按一下 [**取消**]，您需要重新啟動從頭開始。</span><span class="sxs-lookup"><span data-stu-id="afe04-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix 查詢與錯誤計數。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="afe04-158">IdFix 完成查詢之後，您可以繼續並同步處理您的目錄，如果沒有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe04-158">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors.</span></span> <span data-ttu-id="afe04-159">如果您的目錄中有錯誤，則建議，您修正它們，再進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="afe04-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="afe04-160">如果您想要更具體資訊類型的錯誤和修正這些項目的的最佳方式的相關建議，請參閱本主題結尾處的連結。</span><span class="sxs-lookup"><span data-stu-id="afe04-160">If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="afe04-161">雖然並非必要修正錯誤再進行同步處理，我們強烈建議您至少檢閱 IdFix 所傳回的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe04-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="afe04-162">每個錯誤都會顯示在工具主視窗中的個別資料列。</span><span class="sxs-lookup"><span data-stu-id="afe04-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="afe04-163">如果您同意 [**更新**] 欄中所建議的變更，請在 [**動作**] 欄中選取您要如何實作變更 IdFix，然後按一下 [**套用]**。</span><span class="sxs-lookup"><span data-stu-id="afe04-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="afe04-164">當您按一下 [**套用]** 時，此工具會在目錄中進行的變更。</span><span class="sxs-lookup"><span data-stu-id="afe04-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="afe04-165">您不需要在每個更新之後，按一下 [**套用]** 。</span><span class="sxs-lookup"><span data-stu-id="afe04-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="afe04-166">相反地，您可以修正幾個錯誤，再按一下 [**套用]** ，並 IdFix 會將它們變更所有在同一時間。</span><span class="sxs-lookup"><span data-stu-id="afe04-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="afe04-167">您可以藉由按一下**錯誤**頂端列出的錯誤類型的資料行的排序依錯誤類型的錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe04-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="afe04-168">其中一個策略是類型的修正的相同; 所有錯誤例如，第一次，修正所有重複項目，並將它們套用。</span><span class="sxs-lookup"><span data-stu-id="afe04-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="afe04-169">接下來，修正字元格式錯誤，依此類推。</span><span class="sxs-lookup"><span data-stu-id="afe04-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="afe04-170">每次您套用變更，IdFix 工具建立不同的記錄檔可用來復原您的變更，以防發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="afe04-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="afe04-171">[交易記錄檔](idfix-transaction-log.md)會儲存在您安裝 IdFix 中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="afe04-171">The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.</span></span>  <span data-ttu-id="afe04-172">根據預設_C:\Deployment Tools\IdFix_ 。</span><span class="sxs-lookup"><span data-stu-id="afe04-172">_C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![在 IdFix 中補救錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="afe04-174">完成所有的變更都會套用至執行一次，以確保您所做的修正程式並未引進新的錯誤 IdFix 的目錄。</span><span class="sxs-lookup"><span data-stu-id="afe04-174">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="afe04-175">您可以重複這些步驟，為您需要的次數。</span><span class="sxs-lookup"><span data-stu-id="afe04-175">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="afe04-176">它是不錯的選項以通過程序多次再進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="afe04-176">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="afe04-177">我想要精簡搜尋或深入探討錯誤，我可以使用 IdFix 來做什麼？</span><span class="sxs-lookup"><span data-stu-id="afe04-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="afe04-178">更深入的資訊會提供從下列主題：</span><span class="sxs-lookup"><span data-stu-id="afe04-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="afe04-179">[同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="afe04-179">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span></span> <span data-ttu-id="afe04-180">您已安裝的工具，跳至本主題的詳細說明執行工具之後, 會遇到的常見錯誤的建議修正程式、 範例，以及當您有大量錯誤時，該怎麼辦的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="afe04-180">After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="afe04-181">參照：IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="afe04-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="afe04-182">參照：Office 365 IdFix 交易記錄</span><span class="sxs-lookup"><span data-stu-id="afe04-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="afe04-183">影片訓練課程</span><span class="sxs-lookup"><span data-stu-id="afe04-183">Video training</span></span>

<span data-ttu-id="afe04-184">如需詳細資訊，請參閱 < 課程中<b0>安裝及使用 IDFix 工具</b0>，由 LinkedIn Learning 帶您。</span><span class="sxs-lookup"><span data-stu-id="afe04-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

