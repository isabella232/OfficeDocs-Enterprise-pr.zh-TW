---
title: 下載並執行 Microsoft 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何在將 Active Directory 網域服務（AD DS）同步處理至 Microsoft 365 之前，下載並執行 Microsoft 365 IdFix 工具以協助清除 Active Directory 網域服務。
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502658"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="3268a-103">下載並執行 Microsoft 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="3268a-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="3268a-104">*本文適用於 Microsoft 365 企業版和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="3268a-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="3268a-105">IdFix 會先識別錯誤 (如您的 Active Directory 網域 (AD DS) 服務中的重複和格式問題)，然後再同步處理至 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="3268a-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="3268a-106">要順利完成這項工作，您應習慣在 AD DS 中使用使用者、群組和連絡人物件。</span><span class="sxs-lookup"><span data-stu-id="3268a-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="3268a-107">如果您無法完成這項工作，您可以執行其他您能完成的動作。</span><span class="sxs-lookup"><span data-stu-id="3268a-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="3268a-108">這些方法可能會比較容易，但可能會花費更長的時間，或有其他缺點。</span><span class="sxs-lookup"><span data-stu-id="3268a-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="3268a-109">其中包括：</span><span class="sxs-lookup"><span data-stu-id="3268a-109">They are:</span></span>
  
- <span data-ttu-id="3268a-110">**在未執行 IdFix 的情況下執行目錄同步作業**</span><span class="sxs-lookup"><span data-stu-id="3268a-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="3268a-111">您可以在未使用 IdFix 工具的情況下同步處理目錄，但我們並不建議。</span><span class="sxs-lookup"><span data-stu-id="3268a-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="3268a-112">先修正錯誤再同步處理所需的時間較少，而且通常可以更平穩地轉換至雲端。</span><span class="sxs-lookup"><span data-stu-id="3268a-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="3268a-113">**聘用顧問**</span><span class="sxs-lookup"><span data-stu-id="3268a-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="3268a-114">取得專家協助可以快速地啟動並執行您的使用者，以及同步處理您的目錄。</span><span class="sxs-lookup"><span data-stu-id="3268a-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="3268a-115">執行 IdFix 所需的項目</span><span class="sxs-lookup"><span data-stu-id="3268a-115">What you need to run IdFix</span></span>

<span data-ttu-id="3268a-116">啟動並執行 IdFix 的最簡單方式是將它下載到已加入您 AD DS 網域的電腦上。</span><span class="sxs-lookup"><span data-stu-id="3268a-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="3268a-117">若您想要，您可以在網域控制站上執行它，但這非必要動作。</span><span class="sxs-lookup"><span data-stu-id="3268a-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="3268a-118">IdFix 硬體需求</span><span class="sxs-lookup"><span data-stu-id="3268a-118">IdFix hardware requirements</span></span>

<span data-ttu-id="3268a-119">您下載 IdFix 的電腦必須符合這些最低硬體需求：</span><span class="sxs-lookup"><span data-stu-id="3268a-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="3268a-120">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="3268a-120">4 GB RAM</span></span>
- <span data-ttu-id="3268a-121">2 GB 的硬碟空間</span><span class="sxs-lookup"><span data-stu-id="3268a-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="3268a-122">IdFix 軟體需求</span><span class="sxs-lookup"><span data-stu-id="3268a-122">IdFix software requirements</span></span>

<span data-ttu-id="3268a-123">您下載 IdFix 的電腦必需聯結到您要將使用者同步處理至 Microsoft 365 的相同 AD DS 網域。</span><span class="sxs-lookup"><span data-stu-id="3268a-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="3268a-124">電腦也需要安裝 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="3268a-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="3268a-125">如果您執行的是 Windows Server 2008 或更新版本，則可能已經安裝了 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="3268a-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="3268a-126">如果不是，您可以 [從下載中心下載 .NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 或使用 Windows Update 下載。</span><span class="sxs-lookup"><span data-stu-id="3268a-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="3268a-127">IdFix 權限需求</span><span class="sxs-lookup"><span data-stu-id="3268a-127">IdFix permissions requirements</span></span>

<span data-ttu-id="3268a-128">您用來執行 IdFix 的使用者帳戶必須具有 AD DS 網域的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="3268a-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="3268a-129">如果您不確定您的使用者帳戶是否符合這些需求，且不確定如何檢查，您仍然可以下載並執行 IdFix。</span><span class="sxs-lookup"><span data-stu-id="3268a-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="3268a-130">如果您的使用者帳戶沒有正確權限，則 IdFix 只是會在您嘗試執行它時顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="3268a-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="3268a-131">下載並解壓 IdFix</span><span class="sxs-lookup"><span data-stu-id="3268a-131">Download and extract IdFix</span></span>

<span data-ttu-id="3268a-132">按照下列指示進行。</span><span class="sxs-lookup"><span data-stu-id="3268a-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="3268a-133">登入您想要執行 IdFix 工具的電腦。</span><span class="sxs-lookup"><span data-stu-id="3268a-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="3268a-134">移至 [IdFix DirSync 錯誤修正工具](https://github.com/microsoft/idfix) 網站。</span><span class="sxs-lookup"><span data-stu-id="3268a-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="3268a-135">在 **[ClickOnce 啟動]** 區段中，按一下 **[啟動]** 以下載壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="3268a-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="3268a-136">開啟壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="3268a-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="3268a-137">在 **[IdFix]** 視窗中，選擇 **[解壓縮]**，然後 **[全部解壓縮]**。</span><span class="sxs-lookup"><span data-stu-id="3268a-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="3268a-138">根據預設，IdFix 會解壓至 `C:\Users\<your user name>\Documents\IdFix`。</span><span class="sxs-lookup"><span data-stu-id="3268a-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="3268a-139">選擇 **[解壓縮]**。</span><span class="sxs-lookup"><span data-stu-id="3268a-139">Choose **Extract**.</span></span>

<span data-ttu-id="3268a-140">您的步驟可能會根據您的 Windows 版本和網路瀏覽器而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3268a-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="3268a-141">執行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="3268a-141">Run the IdFix tool</span></span>

<span data-ttu-id="3268a-142">下載並解壓 IdFix 之後，請執行 IDFix 以搜尋您 AD DS 網域中的問題。</span><span class="sxs-lookup"><span data-stu-id="3268a-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="3268a-143">使用具有您的 AD DS 網域讀取/寫入權限的帳戶，以登入您下載 IdFix 的電腦。</span><span class="sxs-lookup"><span data-stu-id="3268a-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="3268a-144">在 [檔案總管] 中，移至已解壓 IdFix 的位置。</span><span class="sxs-lookup"><span data-stu-id="3268a-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="3268a-145">如果您在解壓過程中選擇預設資料夾，請移至 `C:\Users\<your user name>\Documents\IdFix`。</span><span class="sxs-lookup"><span data-stu-id="3268a-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="3268a-146">按兩下 **IdFix.exe**。</span><span class="sxs-lookup"><span data-stu-id="3268a-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="3268a-147">IdFix 預設會使用「多租用戶」規則集，測試您目錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="3268a-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="3268a-148">這是大部分 Microsoft 365 客戶的正確規則集。</span><span class="sxs-lookup"><span data-stu-id="3268a-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="3268a-149">不過，如果您是 Microsoft 365 專屬或 International Traffic in Arms Regulations (ITAR)) 客戶，則可以設定 IdFix 以改用 [專屬] 規則集。</span><span class="sxs-lookup"><span data-stu-id="3268a-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="3268a-150">如果不確定您是哪種類型的客戶，則可以放心地略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="3268a-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="3268a-151">若要將規則集設定為 [專屬]，請按一下功能表列中的齒輪圖示，然後按一下 **[專屬]**。</span><span class="sxs-lookup"><span data-stu-id="3268a-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="3268a-152">選擇 **[查詢]**。</span><span class="sxs-lookup"><span data-stu-id="3268a-152">Choose **Query**.</span></span>
    
    ![選擇 IdFix 中的 [查詢]。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="3268a-154">IdFix 預設會搜尋整個目錄中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3268a-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="3268a-155">根據您目錄的大小，執行查詢可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="3268a-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="3268a-156">您可以在工具主視窗底部觀看進度。</span><span class="sxs-lookup"><span data-stu-id="3268a-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="3268a-157">如果您按一下 **[取消]**，則需要從頭重新開始。</span><span class="sxs-lookup"><span data-stu-id="3268a-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="3268a-158">在 IdFix 完成查詢之後，如果沒有錯誤，則可以同步處理您的目錄。</span><span class="sxs-lookup"><span data-stu-id="3268a-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="3268a-159">如果您的目錄中有錯誤，則建議您先修正它們，再進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="3268a-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="3268a-160">如需詳細資訊，請參閱 [準備目錄屬性以便與 Microsoft 365 進行同步處理](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="3268a-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="3268a-161">雖然不需要先修正錯誤再進行同步處理，但是強烈建議您至少檢閱 IdFix 所傳回的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="3268a-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="3268a-162">每個錯誤都會在工具主視窗中以獨立一列的方式顯示。</span><span class="sxs-lookup"><span data-stu-id="3268a-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="3268a-163">如果您同意 **[更新]** 資料行中建議變更，請在 **[動作]** 資料行中選取您想要 IdFix 執行以實作變更的作業，然後按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="3268a-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="3268a-164">按一下 **[套用]** 後，工具就會在目錄中進行變更。</span><span class="sxs-lookup"><span data-stu-id="3268a-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="3268a-165">在每次更新之後，您不需要按 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="3268a-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="3268a-166">而是，您可以先修正數個錯誤，再按一下 **[套用]**，而且 IdFix 會同時變更它們。</span><span class="sxs-lookup"><span data-stu-id="3268a-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="3268a-167">您可以按一下錯誤類型欄頂端的 **[錯誤]** 來根據錯誤類型排序錯誤。</span><span class="sxs-lookup"><span data-stu-id="3268a-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="3268a-168">其中一個策略是修正同一類型的所有錯誤；例如，先修正所有重複項目，並套用它們。</span><span class="sxs-lookup"><span data-stu-id="3268a-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="3268a-169">接下來，修正字元格式錯誤，依此類推。</span><span class="sxs-lookup"><span data-stu-id="3268a-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="3268a-170">每次套用變更時，IdFix 工具都會建立個別記錄檔，以在您出錯時用來復原變更。</span><span class="sxs-lookup"><span data-stu-id="3268a-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="3268a-171">[交易記錄](idfix-transaction-log.md) 儲存在您解壓 IdFix 的資料夾中，預設為_C:\Users\<your user name>\Documents\IdFix_。</span><span class="sxs-lookup"><span data-stu-id="3268a-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![在 IdFix 修正錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="3268a-173">在您對目錄進行所有變更之後，請重新執行 IdFix，以確保您進行的修正並未產生新的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3268a-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="3268a-174">您可以依需要的次數重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="3268a-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="3268a-175">最好多次執行此程序，再進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="3268a-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="3268a-176">IdFix 上的其他資源</span><span class="sxs-lookup"><span data-stu-id="3268a-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="3268a-177">IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="3268a-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="3268a-178">Microsoft 365 IdFix 交易記錄</span><span class="sxs-lookup"><span data-stu-id="3268a-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
