---
title: 安裝和執行 Office 365 IdFix 工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何安裝和執行 Office 365 IdFix 工具可協助清除您的 active directory 同步處理至 Office 365 之前。
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539949"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="18cc3-103">安裝和執行 Office 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="18cc3-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="18cc3-104">再進行同步處理至 Office 365 IdFix 會識別錯誤例如重複項目與您的目錄中的格式設定問題。</span><span class="sxs-lookup"><span data-stu-id="18cc3-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="18cc3-105">若要順利完成此工作，您應該滿意使用使用者、 群組及 Active Directory 中的連絡人物件。</span><span class="sxs-lookup"><span data-stu-id="18cc3-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="18cc3-p101">如果您無法完成此工作，有一些其他您所能做的事項。這些方法可能比較容易，但可能也會更久或有其他缺點。他們是：</span><span class="sxs-lookup"><span data-stu-id="18cc3-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="18cc3-p102">**執行目錄同步處理，而不執行 IdFix。** 您可以將您的目錄同步處理不執行 IdFix 工具，但是我們並不建議使用它。修正錯誤再進行同步處理需要很少的時間和常可以提供更順暢地呈現轉換至雲端。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="18cc3-p103">**雇用一位顧問。** 取得專家協助可以快速地啟動並執行您的使用者，以及同步處理您的目錄。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="18cc3-114">執行 IdFix 所需的項目</span><span class="sxs-lookup"><span data-stu-id="18cc3-114">What you need to run IdFix</span></span>

<span data-ttu-id="18cc3-p104">最簡單方式以取得 IdFix 並執行已安裝已加入網域的電腦上。您可以執行該網域控制站上如果您想要但不需要。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want to, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="18cc3-117">IdFix 硬體需求</span><span class="sxs-lookup"><span data-stu-id="18cc3-117">IdFix hardware requirements</span></span>

<span data-ttu-id="18cc3-118">安裝 IdFix 的電腦必須符合下列硬體需求：</span><span class="sxs-lookup"><span data-stu-id="18cc3-118">The computer where you install IdFix needs to meet these hardware requirements:</span></span>
  
- <span data-ttu-id="18cc3-119">4 GB RAM (最少)</span><span class="sxs-lookup"><span data-stu-id="18cc3-119">4 GB RAM (minimum)</span></span>
- <span data-ttu-id="18cc3-120">2 GB 的硬碟空間 (最少)</span><span class="sxs-lookup"><span data-stu-id="18cc3-120">2 GB of hard disk space (minimum)</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="18cc3-121">IdFix 軟體需求</span><span class="sxs-lookup"><span data-stu-id="18cc3-121">IdFix software requirements</span></span>

<span data-ttu-id="18cc3-p105">安裝 IdFix 必須電腦必須加入至您要使用者同步處理至 Office 365 的同一個 Active Directory 網域。電腦也必須安裝.NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p105">The computer where you install IdFix needs to needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="18cc3-p106">如果您執行 Windows Server 2008 或 Windows Server 2012，是可能已經安裝.NET Framework。如果您不可以[下載從下載中心.NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475)或使用 Windows Update。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or by using Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="18cc3-126">IdFix 權限需求</span><span class="sxs-lookup"><span data-stu-id="18cc3-126">IdFix permissions requirements</span></span>

<span data-ttu-id="18cc3-127">您用來執行 IdFix 的使用者帳戶需要有目錄的讀寫權限。</span><span class="sxs-lookup"><span data-stu-id="18cc3-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="18cc3-p107">如果您不確定您的使用者帳戶符合這些需求，而且您不確定如何檢查，您仍然可以安裝並繼續執行 IdFix。如果您的使用者帳戶沒有正確的權限，IdFix 只會顯示錯誤當您嘗試執行它。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix anyway. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="18cc3-130">安裝 IdFix</span><span class="sxs-lookup"><span data-stu-id="18cc3-130">Install IdFix</span></span>

<span data-ttu-id="18cc3-131">若要安裝 IdFix，請下載並解壓縮 **IdFix.exe** (如這些步驟所述)：</span><span class="sxs-lookup"><span data-stu-id="18cc3-131">To install IdFix, you download and unzip **IdFix.exe** as described in these steps:</span></span> 
  
1. <span data-ttu-id="18cc3-132">登入您想要安裝 IdFix 工具的電腦。</span><span class="sxs-lookup"><span data-stu-id="18cc3-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="18cc3-133">移至 Microsoft 下載網站[IdFix DirSync 錯誤補救工具](https://go.microsoft.com/fwlink/?linkid=867219)。</span><span class="sxs-lookup"><span data-stu-id="18cc3-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="18cc3-134">選擇 [下載]****。</span><span class="sxs-lookup"><span data-stu-id="18cc3-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="18cc3-135">出現提示時，選擇 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="18cc3-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="18cc3-p108">在 [ **WinZip Self-extractor** ] 對話方塊的 [**解壓縮至資料夾**] 文字方塊中輸入或瀏覽至您要安裝 IdFix 工具的位置。依預設，將 C:\Deployment 工具安裝 IdFix\.</span><span class="sxs-lookup"><span data-stu-id="18cc3-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into C:\Deployment Tools\.</span></span> 
    
6. <span data-ttu-id="18cc3-138">選擇 [**解壓縮**]。</span><span class="sxs-lookup"><span data-stu-id="18cc3-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="18cc3-139">執行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="18cc3-139">Run the IdFix tool</span></span>

<span data-ttu-id="18cc3-140">安裝 IdFix 之後，請執行工具來搜尋您目錄中的問題：</span><span class="sxs-lookup"><span data-stu-id="18cc3-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="18cc3-141">使用具有目錄讀寫權限的帳戶，登入已安裝 IdFix 的電腦。</span><span class="sxs-lookup"><span data-stu-id="18cc3-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="18cc3-p109">在 [檔案總管] 中，移至已安裝 IdFix 的電腦。如果您在安裝期間選擇預設資料夾，請移至 C:\Deployment Tools\IdFix。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to C:\Deployment Tools\IdFix.</span></span>
    
3. <span data-ttu-id="18cc3-144">連按兩下 [IdFix.exe]****。</span><span class="sxs-lookup"><span data-stu-id="18cc3-144">Double-click **IdFix.exe**.</span></span> 
    
    ![選擇 [IdFix.exe 檔案。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="18cc3-p110">IdFix 預設會使用的多租用戶規則集來測試您的目錄中的項目。這是設為最多的 Office 365 客戶的右規則。不過，如果您是 Office 365 專用或 ITAR （國際流量召集令規定） 客戶，您可以設定要使用的專用的規則集而 IdFix。如果您不確定您的客戶的類型，您可以放心地略過此步驟。若要設定設為專用的規則，請按一下功能表列的齒輪圖示，，然後選擇 [**專用**。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="18cc3-151">選擇 [**查詢**]。</span><span class="sxs-lookup"><span data-stu-id="18cc3-151">Choose **Query**.</span></span>
    
    ![選擇在 IdFix 中的 [查詢]。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="18cc3-153">IdFix 預設會搜尋整個目錄中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="18cc3-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="18cc3-p111">根據您的目錄的大小、 執行查詢可能需要一段。您可以觀看在工具主視窗的底端的進度。如果您按一下 [**取消**]，您需要重新啟動一開始。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix 查詢和錯誤計數。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="18cc3-p112">IdFix 完成查詢之後，而且，如果您的目錄中沒有錯誤，則可以繼續進行並同步處理您的目錄。如果您的目錄中有錯誤，則建議您先修正它們，再進行同步處理。如果您想要錯誤類型的更特定資訊以及修正所有錯誤之最佳方式的建議，請查看本主題結尾的連結。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p112">After IdFix completes the query, and if there are no errors in your directory, you can go ahead and synchronize your directory. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="18cc3-161">雖然不需要先修正錯誤再進行同步處理，但是強烈建議您至少檢閱 IdFix 所傳回的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="18cc3-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="18cc3-162">每個錯誤都會顯示在工具主視窗中的個別資料列。</span><span class="sxs-lookup"><span data-stu-id="18cc3-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="18cc3-p113">如果您同意 [UPDATE]**** 資料行中建議的變更，請在 [ACTION]**** 資料行中選取您想要 IdFix 執行以實作變更的作業，然後按一下 [套用]****。當您按一下 [套用]**** 時，工具會在目錄中進行變更。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="18cc3-p114">您不需要在每次更新後按一下 [**套用]** 。而您可以修正數個錯誤再按一下 [**套用]** 並 IdFix 會將它們變更所有在同一時間。您可以按一下**錯誤**頂端列出的錯誤類型的資料行的排序錯誤類型所發生之錯誤。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="18cc3-p115">一個策略是依修正相同的類型 ； 所有錯誤例如，先修正所有重複項目並套用。接下來，修正字元格式錯誤、 等等。套用變更，每次 IdFix 工具建立不同的記錄檔可用來復原變更以防進行錯誤。[交易記錄檔](idfix-transaction-log.md)會儲存在已安裝 IdFix 中的資料夾中。 根據預設_C:\Deployment Tools\IdFix_ 。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![在 IdFix 中補救錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="18cc3-p116">完成所有的變更會對執行一次以確保您所做的修正程式沒有引進新的錯誤 IdFix 的目錄。您可以重複這些步驟您需要的次數。它是不錯的選項以移到程序一些時間再進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="18cc3-177">我想要精簡搜尋或深入探討錯誤，那麼我還可以使用 IdFix 來執行其他作業嗎？</span><span class="sxs-lookup"><span data-stu-id="18cc3-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="18cc3-178">您可以從下列主題取得更深入資訊：</span><span class="sxs-lookup"><span data-stu-id="18cc3-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="18cc3-p117">[同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)。您已安裝的工具，跳至本主題的相關執行工具的詳細指示之後會遇到的常見錯誤的建議修正程式、 範例和不具有大量的錯誤時的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="18cc3-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="18cc3-181">參照：IdFix 已排除和支援的物件和屬性</span><span class="sxs-lookup"><span data-stu-id="18cc3-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="18cc3-182">參照：Office 365 IdFix 交易記錄</span><span class="sxs-lookup"><span data-stu-id="18cc3-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="18cc3-183">影片訓練</span><span class="sxs-lookup"><span data-stu-id="18cc3-183">Video training</span></span>

<span data-ttu-id="18cc3-184">如需詳細資訊，請參閱致力提供依 LinkedIn 學習課程[安裝及使用 IDFix 工具](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx)。</span><span class="sxs-lookup"><span data-stu-id="18cc3-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), brought to you by LinkedIn Learning.</span></span>
  

