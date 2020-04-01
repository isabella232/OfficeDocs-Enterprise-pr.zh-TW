---
title: 下載並執行 Office 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
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
description: 如何在將 Active Directory 網域服務（AD DS）同步處理至 Office 365 之前，下載並執行 Office 365 IdFix 工具，以協助清理您的 Active Directory 網域服務（AD DS）。
ms.openlocfilehash: d816abe8e93830832077c614e496576d42890d50
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068775"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="ca9e3-103">下載並執行 Office 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="ca9e3-103">Download and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="ca9e3-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="ca9e3-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="ca9e3-105">IdFix 會在您同步處理至 Office 365 之前，識別您的 Active Directory 網域服務（AD DS）網域中的重複和格式化問題等錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="ca9e3-106">若要順利完成這項工作，您應該舒適使用 AD DS 中的使用者、群組和連絡人物件。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="ca9e3-107">如果您無法完成這項工作，還有其他幾項您可以執行的動作。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="ca9e3-108">這些方法可能較為簡單，但也可能需要較長的時間，否則會有其他缺點。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="ca9e3-109">其中包括：</span><span class="sxs-lookup"><span data-stu-id="ca9e3-109">They are:</span></span>
  
- <span data-ttu-id="ca9e3-110">**執行目錄同步處理但不執行 IdFix**</span><span class="sxs-lookup"><span data-stu-id="ca9e3-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="ca9e3-111">您可以同步處理您的目錄，而不需要使用 IdFix 工具，但我們不建議您這樣做。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="ca9e3-112">在同步處理之前修正錯誤所需的時間較少，且通常會提供更順暢的轉換至雲端。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="ca9e3-113">**雇用顧問**</span><span class="sxs-lookup"><span data-stu-id="ca9e3-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="ca9e3-114">取得專家協助可讓您的使用者快速啟動並執行，並同步處理您的目錄。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="ca9e3-115">您需要執行的 IdFix</span><span class="sxs-lookup"><span data-stu-id="ca9e3-115">What you need to run IdFix</span></span>

<span data-ttu-id="ca9e3-116">若要執行 IdFix，最簡單的方法是將它下載到已加入 AD DS 網域的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="ca9e3-117">您可以視需要在網域控制站上執行它，但這不是必要的。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="ca9e3-118">IdFix 硬體需求</span><span class="sxs-lookup"><span data-stu-id="ca9e3-118">IdFix hardware requirements</span></span>

<span data-ttu-id="ca9e3-119">您下載 IdFix 需要符合這些最低硬體需求的電腦：</span><span class="sxs-lookup"><span data-stu-id="ca9e3-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="ca9e3-120">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="ca9e3-120">4 GB RAM</span></span>
- <span data-ttu-id="ca9e3-121">2 GB 的硬碟空間</span><span class="sxs-lookup"><span data-stu-id="ca9e3-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="ca9e3-122">IdFix 軟體需求</span><span class="sxs-lookup"><span data-stu-id="ca9e3-122">IdFix software requirements</span></span>

<span data-ttu-id="ca9e3-123">您要在其中下載 IdFix 的電腦必須加入您要將使用者同步處理至 Office 365 的相同 AD DS 網域。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Office 365.</span></span> 

<span data-ttu-id="ca9e3-124">電腦也需要安裝 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="ca9e3-125">如果您執行的是 Windows Server 2008 或更新版本，.NET Framework 可能已經安裝。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="ca9e3-126">如果不是，您可以從下載中心或使用 Windows Update[下載 .net 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="ca9e3-127">IdFix 許可權需求</span><span class="sxs-lookup"><span data-stu-id="ca9e3-127">IdFix permissions requirements</span></span>

<span data-ttu-id="ca9e3-128">您用來執行 IdFix 的使用者帳戶必須具有 AD DS 網域的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="ca9e3-129">如果您不確定您的使用者帳戶是否符合這些需求，而且不確定如何檢查，您仍然可以下載並執行 IdFix。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="ca9e3-130">如果您的使用者帳戶沒有正確的許可權，IdFix 會在您嘗試執行它時，只會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="ca9e3-131">下載和解壓縮 IdFix</span><span class="sxs-lookup"><span data-stu-id="ca9e3-131">Download and extract IdFix</span></span>

<span data-ttu-id="ca9e3-132">請遵循這些指示。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="ca9e3-133">登入您要執行 IdFix 工具的電腦。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="ca9e3-134">移至[IdFix DirSync 錯誤修正工具](https://github.com/microsoft/idfix)網站。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="ca9e3-135">按一下 [ **ClickOnce 啟動**] 區段中的 [**啟動**]，下載 zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="ca9e3-136">開啟 zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="ca9e3-137">在 [ **IdFix** ] 視窗中，選擇 [**解壓縮**]，然後**全部解壓縮**。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="ca9e3-138">依預設，IdFix 會解壓縮至`C:\Users\<your user name>\Documents\IdFix`。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="ca9e3-139">選擇 [解壓縮]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-139">Choose **Extract**.</span></span>

<span data-ttu-id="ca9e3-140">您的步驟可能會根據您的 Windows 和網際網路瀏覽器的版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="ca9e3-141">執行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="ca9e3-141">Run the IdFix tool</span></span>

<span data-ttu-id="ca9e3-142">下載並解壓縮 IdFix 之後，請執行此程式，以搜尋 AD DS 網域中的問題。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="ca9e3-143">使用具有您 AD DS 網域之讀取/寫入權限的帳戶，登入您已下載 IdFix 的電腦。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="ca9e3-144">在檔案瀏覽器中，移至您解壓縮 IdFix 的位置。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="ca9e3-145">如果您在解壓縮期間選擇預設資料夾，請移`C:\Users\<your user name>\Documents\IdFix`至。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="ca9e3-146">按兩下 [ **IdFix.exe**]。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="ca9e3-147">根據預設，IdFix 會使用多租使用者規則集來測試目錄中的專案。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="ca9e3-148">這是大多數 Office 365 客戶的正確規則集。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-148">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="ca9e3-149">不過，如果您是「Arm 規章」（ITAR）客戶的 Office 365 專屬或國際流量，您可以設定 IdFix 改為使用專用規則集。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-149">However, if you are an Office 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="ca9e3-150">如果您不確定您是哪種類型的客戶，可以放心地略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="ca9e3-151">若要將規則集設定為專屬，請按一下功能表列中的齒輪圖示，然後選擇 [**專屬**]。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="ca9e3-152">選擇 [**查詢**]。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-152">Choose **Query**.</span></span>
    
    ![在 IdFix 中選擇 [查詢]。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="ca9e3-154">根據預設，IdFix 會搜尋整個目錄中是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="ca9e3-155">執行查詢時，可能需要一段時間，視目錄的大小而定。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="ca9e3-156">您可以在工具的主視窗底部觀賞進度。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="ca9e3-157">如果您按一下 [**取消**]，則需要從頭開始重新開始。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="ca9e3-158">IdFix 完成查詢之後，如果沒有任何錯誤，您可以同步處理您的目錄。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="ca9e3-159">如果您的目錄中有錯誤，建議您在同步處理之前先加以修正。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="ca9e3-160">如需詳細資訊，請參閱[準備目錄屬性以與 Office 365 同步處理](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-160">See [prepare directory attributes for synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="ca9e3-161">雖然不需要在同步處理之前修正錯誤，但強烈建議您至少檢查 IdFix 所傳回的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="ca9e3-162">每個錯誤都顯示在工具主視窗中的個別列。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="ca9e3-163">如果您同意 [**更新**] 欄中的 [建議變更]，請在 [**動作**] 欄中，選取您要 IdFix 執行變更的專案，**然後按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="ca9e3-164">當您按一下**Apply**時，工具會在目錄中進行變更。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="ca9e3-165">在每次更新後，您不必按**Apply** 。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="ca9e3-166">相反地，您可以在按一下**Apply**之前修正數個錯誤，IdFix 會同時變更所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="ca9e3-167">您可以在列出錯誤類型的欄位頂端按一下 [**錯誤**]，依錯誤類型排序錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="ca9e3-168">一個策略是修正所有相同類型的錯誤;例如，先修正所有重複專案，然後加以套用。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="ca9e3-169">接下來，修正字元格式錯誤等等。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="ca9e3-170">每次套用變更時，IdFix 工具都會建立個別的記錄檔，您可以用來復原您的變更，以防您犯錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="ca9e3-171">[交易記錄](idfix-transaction-log.md)會儲存在您解壓縮 IdFix 的資料夾中，該資料夾預設會_C:\Users\<您的使用者名稱> \documents\idfix_ 。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![在 IdFix 修正錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="ca9e3-173">對目錄進行所有變更之後，請再次執行 IdFix，以確保您所進行的修復程式未引入新的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="ca9e3-174">您可以視需要重複執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="ca9e3-175">建議您在同步處理之前，先完成此程式。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="ca9e3-176">IdFix 的其他資源</span><span class="sxs-lookup"><span data-stu-id="ca9e3-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="ca9e3-177">IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="ca9e3-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="ca9e3-178">Office 365 IdFix 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="ca9e3-178">Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="ca9e3-179">影片訓練課程</span><span class="sxs-lookup"><span data-stu-id="ca9e3-179">Video training</span></span>

<span data-ttu-id="ca9e3-180">如需詳細資訊，請參閱課程[安裝和使用 IdFix 工具](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)，讓您 LinkedIn 學習。</span><span class="sxs-lookup"><span data-stu-id="ca9e3-180">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

