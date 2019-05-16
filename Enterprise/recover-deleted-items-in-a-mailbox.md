---
title: 復原使用者信箱中刪除的郵件 - 系統管理說明
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: '本文適用於系統管理員。 沒有使用者永久刪除項目從其 Outlook 信箱嗎？ 使用者想要他們回，但無法加以復原。 您可能無法復原的已清除的項目，如果它們尚未從使用者的信箱永久移除。 '
ms.openlocfilehash: 5ec1ba41924d773859d742bc06bbfe76582072c1
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071209"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="fbcb4-106">復原使用者信箱中刪除的郵件 - 系統管理說明</span><span class="sxs-lookup"><span data-stu-id="fbcb4-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="fbcb4-107">**本文適用於系統管理員。您嘗試復原刪除的項目在您自己的信箱？**</span><span class="sxs-lookup"><span data-stu-id="fbcb4-107">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?**</span></span> <span data-ttu-id="fbcb4-108">請嘗試下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fbcb4-108">Try one of the following:</span></span>
- [<span data-ttu-id="fbcb4-109">在 Windows 版 Outlook 復原已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="fbcb4-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="fbcb4-110">復原 Outlook Web App 中刪除的郵件或電子郵件</span><span class="sxs-lookup"><span data-stu-id="fbcb4-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="fbcb4-111">網頁型 Outlook 中還原已刪除電子郵件</span><span class="sxs-lookup"><span data-stu-id="fbcb4-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="fbcb4-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="fbcb4-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="fbcb4-113">沒有使用者永久刪除項目從其 Outlook 信箱嗎？</span><span class="sxs-lookup"><span data-stu-id="fbcb4-113">Did a user permanently delete items from their Outlook mailbox?</span></span> <span data-ttu-id="fbcb4-114">使用者想要他們回，但無法加以復原。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-114">The user wants them back but can't recover them.</span></span> <span data-ttu-id="fbcb4-115">您可能無法復原的已清除的項目，如果它們尚未從使用者的信箱永久移除。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-115">You may be able recover the purged items if they haven't been permanently removed from the user's mailbox.</span></span> <span data-ttu-id="fbcb4-116">您執行這項操作 Exchange Online 中使用就地 eDiscovery 工具來搜尋已刪除的電子郵件和其他項目 — 例如連絡人、 行事曆約會和工作和-使用者的信箱中。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-116">You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox.</span></span> <span data-ttu-id="fbcb4-117">如果您發現已刪除的項目，您可以將其匯出至 PST 檔案 （也稱為 Outlook 資料檔），使用者可以使用回他們的信箱還原項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-117">If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="fbcb4-118">以下是使用者的信箱中復原刪除的項目的步驟。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-118">Here are the steps for recovering deleted items in a user's mailbox.</span></span> <span data-ttu-id="fbcb4-119">將這需要花費多少時間？</span><span class="sxs-lookup"><span data-stu-id="fbcb4-119">How long will this take?</span></span> <span data-ttu-id="fbcb4-120">第一次可能需要 20 封或 30 分鐘才能完成所有步驟，根據您的多少項目正在嘗試復原。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-120">The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="fbcb4-121">您必須是**Exchange 系統管理員**或 Office 365 中的**全域系統管理員**或是 「 組織管理 」 角色群組的成員在 Exchange Online 來執行本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-121">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article.</span></span> <span data-ttu-id="fbcb4-122">如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-122">For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="fbcb4-123">步驟 1： 將自己指派 eDiscovery 權限</span><span class="sxs-lookup"><span data-stu-id="fbcb4-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="fbcb4-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="fbcb4-124"></span></span>

<span data-ttu-id="fbcb4-125">第一個步驟是您自己的必要權限 Exchange Online 中指派，您可以使用就地電子文件探索工具來搜尋使用者的信箱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-125">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox.</span></span> <span data-ttu-id="fbcb4-126">您只需要執行這項操作一次。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-126">You only have to do this once.</span></span> <span data-ttu-id="fbcb4-127">如果您有在未來搜尋另一個信箱，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-127">If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="fbcb4-128">找不到您要的 App 嗎？請從應用程式啟動器選取 [所有 App] 以查看依字母順序排序的可用 Office 365 App 清單。您可從該處搜尋特定的 App。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="fbcb4-129">選取 [應用程式啟動器圖示![Office 365 中的應用程式啟動器圖示](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中左上角，按一下 [**系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="fbcb4-130">在 Office 365 系統管理中心左側導覽中，依序展開 [**系統管理中心**，，，然後按一下 [ **Exchange**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![系統中心清單](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="fbcb4-132">在 Exchange 系統管理中心中，按一下 [**權限**，，然後按一下 [**系統管理員角色**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="fbcb4-133">在清單檢視中，選取 [**探索管理**]，然後按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![將自己新增至探索管理角色群組，在 EAC 中](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="fbcb4-135">在**角色群組**中，[**成員**] 下方按一下 [**新增**![加入圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="fbcb4-136">在 [**選取成員**，自行從清單中選取的名稱按一下 [**新增**]，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="fbcb4-137">您也可以新增，您必須是的例如組織管理 」 或 「 TenantAdmins 成員的群組。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-137">You can also add a group that you are a member of, such as Organization Management or TenantAdmins.</span></span> <span data-ttu-id="fbcb4-138">如果您新增群組，群組的其他成員會被指派執行就地 eDiscovery 工具的必要權限。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-138">If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="fbcb4-139">在**角色群組**中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="fbcb4-140">登出 Office 365。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="fbcb4-141">必須先登出，才能讓新的權限將會生效，啟動下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="fbcb4-142">探索管理角色群組的成員可存取機密訊息內容。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-142">Members of the Discovery Management role group can access sensitive message content.</span></span> <span data-ttu-id="fbcb4-143">這包括在組織中搜尋所有信箱、 預覽搜尋結果 （和其他信箱項目），將結果複製到探索信箱，以及將搜尋結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-143">This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="fbcb4-144">回到頁首</span><span class="sxs-lookup"><span data-stu-id="fbcb4-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="fbcb4-145">步驟 2： 搜尋使用者的信箱已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="fbcb4-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="fbcb4-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="fbcb4-146"></span></span>

<span data-ttu-id="fbcb4-147">當您執行就地 eDiscovery 搜尋時，您所搜尋的信箱中的 [可復原的項目] 資料夾會自動包含在搜尋]。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-147">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search.</span></span> <span data-ttu-id="fbcb4-148">[可復原的項目] 資料夾是永久刪除的項目儲存位置之前他們正在清除 （永久移除） 從信箱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-148">The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox.</span></span> <span data-ttu-id="fbcb4-149">因此，如果項目尚未清除，您應該能夠使用就地 eDiscovery 工具來尋找。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-149">So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="fbcb4-150">找不到您要的 App 嗎？請從應用程式啟動器選取 [所有 App] 以查看依字母順序排序的可用 Office 365 App 清單。您可從該處搜尋特定的 App。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="fbcb4-151">選取 [應用程式啟動器圖示![Office 365 中的應用程式啟動器圖示](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中左上角，按一下 [**系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="fbcb4-152">在 Office 365 系統管理中心左側導覽中，展開 [**系統管理員**，，，然後按一下 [ **Exchange**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="fbcb4-153">在 Exchange 系統管理中心中，按一下 [**規範管理]**，然後**就地 eDiscovery&amp;保留**，然後按一下 [**新增**![加入圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![在 EAC 中，在 [規範管理] 頁面上，按一下 [就地 eDiscovery 和保留](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="fbcb4-155">在 [**名稱與描述**] 頁面上輸入的名稱 （例如，您正在復原的電子郵件的使用者名稱） 搜尋選擇性描述，，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="fbcb4-156">在 [**信箱**] 頁面上，按一下 [**指定信箱進行搜尋**，，然後按一下 [**新增**![加入圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![按一下 [指定信箱進行搜尋來說信箱搜尋](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="fbcb4-158">尋找和選取您要復原已刪除的電子郵件的使用者名稱按一下 [**新增**]，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="fbcb4-159">按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-159">Click **Next**.</span></span>
    
    <span data-ttu-id="fbcb4-160">**搜尋查詢**頁面隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-160">The **Search query** page is displayed.</span></span> <span data-ttu-id="fbcb4-161">這是用來定義可協助您在使用者的信箱中尋找遺失的項目搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-161">This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="fbcb4-162">在 [**搜尋查詢**] 頁面上，完成下列欄位：</span><span class="sxs-lookup"><span data-stu-id="fbcb4-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="fbcb4-163">**包含所有內容**選取此選項可在搜尋結果中的使用者信箱中包含的所有內容。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-163">**Include all content** Select this option to include all content in the user's mailbox in the search results.</span></span> <span data-ttu-id="fbcb4-164">如果選取這個選項，便無法指定其他搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-164">If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="fbcb4-165">**篩選依據準則**選取此選項以指定搜尋準則，包含關鍵字、 開始和結束日期、 寄件者和收件者地址，而且郵件類型。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![建立搜尋，根據準則，例如關鍵字、 日期範圍、 收件者，以及訊息類型](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="fbcb4-167">**Field**</span><span class="sxs-lookup"><span data-stu-id="fbcb4-167">**Field**</span></span>|<span data-ttu-id="fbcb4-168">**使用此選項，即可...]**</span><span class="sxs-lookup"><span data-stu-id="fbcb4-168">**Use this to...**</span></span>|
|:-----|:-----|
|![粉紅色圓圈中的數字 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="fbcb4-170">指定的關鍵字、 日期範圍、 收件者，以及訊息類型。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![粉紅色圓圈中的數字 2。](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="fbcb4-172">搜尋關鍵字或片語的郵件，並使用邏輯運算子，例如**AND**或**OR**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![粉紅色圓圈中的數字 3。](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="fbcb4-174">搜尋的郵件傳送或接收的日期範圍內。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![粉紅色圓圈中的數字 4。](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="fbcb4-176">搜尋從接收或傳送給特定人員的郵件。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![數字粉紅色圓圈中的第五個。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="fbcb4-178">搜尋所有郵件類型，或選擇特定信箱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="fbcb4-179">在**就地保留設定]** 頁面上，按一下 [**完成**] 以啟動搜尋。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-179">On the **In-Place Hold settings** page, click **Finish** to start the search.</span></span> <span data-ttu-id="fbcb4-180">若要復原已刪除的電子郵件，沒有要就地保留使用者信箱的理由。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-180">To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="fbcb4-181">啟動搜尋之後，Exchange 會顯示的估計項目總大小和項，將會根據您指定的準則搜尋所傳回的項目數。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="fbcb4-182">選取您剛建立的搜尋，然後按一下 [**重新整理**![重新整理](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)以更新詳細資料窗格中顯示的資訊。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-182">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane.</span></span> <span data-ttu-id="fbcb4-183">**預估成功**的狀態指出後搜尋。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-183">The status of **Estimate Succeeded** indicates that the search has finished.</span></span> <span data-ttu-id="fbcb4-184">Exchange 也會顯示的項目 （和其大小） 找到您在步驟 9 中指定的搜尋準則為基礎的搜尋總數預估。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-184">Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="fbcb4-185">在 [詳細資料] 窗格中，按一下 [**預覽搜尋結果**，以檢視所找到的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-185">In the details pane, click **Preview search results** to view the items that were found.</span></span> <span data-ttu-id="fbcb4-186">這可能會協助您找出您要尋找的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-186">This might help you identify the item(s) that you're looking for.</span></span> <span data-ttu-id="fbcb4-187">如果您找出您想要復原的項目，請移至步驟 4，將搜尋結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-187">If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![按一下 [預覽搜尋結果，以檢視您嘗試復原的項目](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="fbcb4-189">如果您找不到您要尋找您可以修改您的搜尋準則選取搜尋]，按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)，然後按一下 [**搜尋查詢**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-189">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**.</span></span> <span data-ttu-id="fbcb4-190">變更搜尋準則，然後重新執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-190">Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="fbcb4-191">回到頁首</span><span class="sxs-lookup"><span data-stu-id="fbcb4-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="fbcb4-192">（選用）步驟 3： 將搜尋結果複製到探索信箱</span><span class="sxs-lookup"><span data-stu-id="fbcb4-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="fbcb4-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="fbcb4-193"></span></span>

<span data-ttu-id="fbcb4-194">如果您找不到項目來預覽搜尋結果，或是您想要查看哪些項目位於使用者 [可復原的項目] 資料夾，然後您可以將搜尋結果複製到特殊的信箱 （稱為 「 探索信箱），然後開啟該信箱 t 網頁型 Outlook 中o 檢視的實際項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-194">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items.</span></span> <span data-ttu-id="fbcb4-195">複製搜尋結果的最佳原因會讓您可以檢視使用者的 [可復原的項目] 資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-195">The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder.</span></span> <span data-ttu-id="fbcb4-196">多個可能正在嘗試復原的項目位於清除] 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-196">More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="fbcb4-197">在 Exchange 系統管理中心，移至 [**規範管理** \> **就地 eDiscovery&amp;保留**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="fbcb4-198">在 [搜尋] 清單中選取您在步驟 2 中建立的搜尋。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="fbcb4-199">按一下 [**搜尋**![搜尋](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)，然後從下拉式清單中按一下 [**複製搜尋結果**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![按一下 [搜尋]，然後按一下 [複製搜尋結果](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="fbcb4-201">在**複製搜尋結果**頁面上，按一下 [**瀏覽**]。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![保留復原刪除的項目時，未選取] 核取方塊](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="fbcb4-203">在 [**顯示名稱**] 中，按一下 [**探索搜尋信箱**，然後再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![將搜尋結果複製到預設的探索搜尋信箱](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="fbcb4-205">[探索搜尋信箱會自動建立 Office 365 組織中的預設探索信箱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="fbcb4-206">回在**複製搜尋結果**頁面上，按一下 [**複製**] 以開始程序，將搜尋結果複製到 [探索搜尋信箱]。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![按一下 [複製]，將搜尋結果複製到 [探索搜尋信箱](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="fbcb4-208">按一下 [**重新整理**![重新整理](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)以更新詳細資料窗格中顯示的複製狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="fbcb4-209">複製完成時，請按一下 [**開啟**] 以開啟要檢視搜尋結果的探索搜尋信箱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![按一下 [開啟] 以移至要檢視搜尋結果的探索搜尋信箱](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="fbcb4-211">具有相同名稱為 「 就地 eDiscovery 搜尋的資料夾中放置搜尋結果複製到 [探索搜尋信箱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-211">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search.</span></span> <span data-ttu-id="fbcb4-212">您可以按一下該資料夾中顯示的項目] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-212">You can click a folder to display the items in that folder.</span></span>
    
    ![探索搜尋信箱; 中的搜尋結果[清除] 資料夾中的項目可以只復原由系統管理員](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="fbcb4-214">當您執行搜尋時，也會搜尋使用者的 [可復原的項目] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-214">When you run a search, the user's Recoverable Items folder is also searched.</span></span> <span data-ttu-id="fbcb4-215">這表示如果 [可復原的項目] 資料夾中的項目符合搜尋準則，它們包含在搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-215">That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results.</span></span> <span data-ttu-id="fbcb4-216">在 [刪除] 資料夾中的項目是項目使用者永久刪除 （藉由從 [刪除的項目] 資料夾刪除項目或選取它，然後按下**Shift + Delete**鍵。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-216">Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**.</span></span> <span data-ttu-id="fbcb4-217">使用者可以使用 Outlook 或網頁型 Outlook 中復原刪除的項目工具復原 [刪除] 資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-217">A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder.</span></span> <span data-ttu-id="fbcb4-218">[清除] 資料夾中的項目會使用 [復原刪除的項目工具來清除使用者的項目或他們所自動清除對信箱套用原則的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-218">Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox.</span></span> <span data-ttu-id="fbcb4-219">在任一情況中，只有系統管理員可以復原 [清除] 資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-219">In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="fbcb4-220">如果使用者找不到已刪除的項目，使用 「 可復原的項目 」 工具，但仍可復原項目 （表示它尚未已永久移除的信箱），它是多個可能位於 [清除] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-220">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder.</span></span> <span data-ttu-id="fbcb4-221">因此，務必要刪除之項目的您嘗試復原使用者的 [清除] 資料夾中尋找。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-221">So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="fbcb4-222">回到頁首</span><span class="sxs-lookup"><span data-stu-id="fbcb4-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="fbcb4-223">步驟 4： 將搜尋結果匯出至 PST 檔案</span><span class="sxs-lookup"><span data-stu-id="fbcb4-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="fbcb4-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="fbcb4-224"></span></span>

<span data-ttu-id="fbcb4-225">找到您想要使用者復原的項目後下, 一步是將結果匯出從搜尋您在步驟 2 中執行至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-225">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file.</span></span> <span data-ttu-id="fbcb4-226">使用者會使用下一個步驟中的此 PST 檔案還原至其信箱的刪除項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-226">The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="fbcb4-227">在 Exchange 系統管理中心，移至 [**規範管理** \> **就地 eDiscovery&amp;保留**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="fbcb4-228">在 [搜尋] 清單中選取您在步驟 2 中建立的搜尋。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="fbcb4-229">按一下 [**匯出至 PST 檔案**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-229">Click **Export to a PST file**.</span></span>
    
    ![按一下 [匯出成 PST 檔案](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="fbcb4-231">如果系統提示您安裝 eDiscovery 匯出工具，請按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="fbcb4-232">在 eDiscovery PST 匯出工具中，按一下 [**瀏覽]** 以指定您要下載 PST 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![EDiscovery PST 匯出工具](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="fbcb4-234">您可以略過的選項以啟用重複資料刪除，並包含無法搜尋的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="fbcb4-235">按一下 [**啟動**] 以將 PST 檔案下載到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="fbcb4-236">**EDiscovery PST 匯出工具**會顯示在匯出程序的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-236">The **eDiscovery PST Export Tool** displays status information about the export process.</span></span> <span data-ttu-id="fbcb4-237">匯出完成時，您可以存取它已下載的所在位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-237">When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="fbcb4-238">回到頁首</span><span class="sxs-lookup"><span data-stu-id="fbcb4-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="fbcb4-239">步驟 5： 還原復原的項目至使用者的信箱</span><span class="sxs-lookup"><span data-stu-id="fbcb4-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="fbcb4-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="fbcb4-240"></span></span>

<span data-ttu-id="fbcb4-241">最後一個步驟是使用步驟 4，以還原復原的項目至使用者的信箱中匯出的 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-241">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox.</span></span> <span data-ttu-id="fbcb4-242">您將 PST 檔案傳送給使用者之後，是由使用者開啟 PST 檔案，並再將復原的項目移至其信箱中的另一個資料夾執行此步驟的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-242">After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox.</span></span> <span data-ttu-id="fbcb4-243">如需逐步指示，您也可以傳送使用者連結到此主題：[開啟和關閉 Outlook 資料檔 (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-243">For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span></span> <span data-ttu-id="fbcb4-244">或者，您可以傳送給使用者] 連結，以[還原已刪除的信箱，使用 PST 檔案項目](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)] 區段下方，並請他們才能執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-244">Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="fbcb4-245">**將 PST 檔案傳送給使用者**</span><span class="sxs-lookup"><span data-stu-id="fbcb4-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="fbcb4-246">您需要執行的最後一個步驟在步驟 4 中傳送已匯出的 PST 檔案給使用者。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-246">The final step that you need to perform is sending the PST file that was exported in step 4 to the user.</span></span> <span data-ttu-id="fbcb4-247">有幾種方法來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="fbcb4-247">There are a few ways to do this:</span></span>
  
- <span data-ttu-id="fbcb4-248">將 PST 檔案附加到電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-248">Attach the PST file to an email message.</span></span> <span data-ttu-id="fbcb4-249">如果 Outlook 設定為封鎖 PST 檔案，您會有 zip 檔案並再將它附加到郵件。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-249">If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message.</span></span> <span data-ttu-id="fbcb4-250">方法如下：</span><span class="sxs-lookup"><span data-stu-id="fbcb4-250">Here's how:</span></span>
    
1. <span data-ttu-id="fbcb4-251">在 Windows 檔案總管或檔案總管] 中，瀏覽至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="fbcb4-252">以滑鼠右鍵按一下 [檔案]，然後選取 [**傳送至** \> **壓縮 (zipped) 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-252">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**.</span></span> <span data-ttu-id="fbcb4-253">Windows 會建立新的 zip 檔案，並讓它為 PST 檔案的相同名稱。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-253">Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="fbcb4-254">壓縮的 PST 檔案附加到電子郵件訊息，並將它傳送給使用者，然後按一下滑鼠左鍵來解壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="fbcb4-255">將 PST 檔案複製到使用者可以存取，並擷取它的共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="fbcb4-256">還原刪除的項目至其信箱之使用者所執行下一節中的步驟。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="fbcb4-257">**還原刪除的項目至信箱，使用 PST 檔案**</span><span class="sxs-lookup"><span data-stu-id="fbcb4-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="fbcb4-258">您必須使用 Outlook 桌面應用程式使用 PST 檔案還原已刪除的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-258">You have to use the Outlook desktop app to restore a deleted item by using a PST file.</span></span> <span data-ttu-id="fbcb4-259">您無法使用 Outlook Web App 或 Outlook web 上的開啟 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-259">You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="fbcb4-260">在 Outlook 2013 或 Outlook 2016 中，按一下 [**檔案**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="fbcb4-261">按一下 [**開啟&amp;匯出**，然後按一下 [**開啟 Outlook 資料檔**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="fbcb4-262">瀏覽至您儲存您的系統管理員傳送的 PST 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="fbcb4-263">選取 PST，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="fbcb4-264">在左導覽列中，在 Outlook 中，顯示 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST 檔案會出現在 Outlook 中的左導覽列](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="fbcb4-266">按一下箭頭以展開 PST 檔案及其下找出您想要復原的項目資料夾。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![在您想要復原的項目 [清除] 資料夾中尋找](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="fbcb4-268">在您想要復原的項目 [清除] 資料夾中尋找。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-268">Look in the Purges folder for the item you want to recover.</span></span> <span data-ttu-id="fbcb4-269">這是隱藏的資料夾中清除項目會移至。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-269">This is a hidden folder that purged items are moved to.</span></span> <span data-ttu-id="fbcb4-270">它可能是您復原的系統管理員是此資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-270">It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="fbcb4-271">以滑鼠右鍵按一下您想要復原，然後按一下 [**移動**項的目\>**其他資料夾**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![按一下 [移動]，然後選取 [其他] 資料夾](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="fbcb4-273">若要將項目移至 [收件匣，請按一下 **[收件匣**，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="fbcb4-274">**提示：** 若要復原其他類型的項目，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="fbcb4-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="fbcb4-275">要復原的行事曆項目，以滑鼠右鍵按一下，，然後按一下 [**移動** \> **其他資料夾** \> **行事曆**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="fbcb4-276">復原連絡人，以滑鼠右鍵按一下，，然後按一下 [**移動** \> **其他資料夾** \> **連絡人**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="fbcb4-277">要修復工作，以滑鼠右鍵按一下，，然後按一下 [**移動** \> **其他資料夾** \> **工作**。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![選取要移動其他類型的項目資料夾](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="fbcb4-279">當您完成時復原刪除的項目，以滑鼠右鍵按一下在左導覽列] 和 [select**關閉 「 PST 檔案名稱 」** 的 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="fbcb4-280">回到頁首</span><span class="sxs-lookup"><span data-stu-id="fbcb4-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="fbcb4-281">其他資訊</span><span class="sxs-lookup"><span data-stu-id="fbcb4-281">More information</span></span>
<span data-ttu-id="fbcb4-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="fbcb4-282"></span></span>

- <span data-ttu-id="fbcb4-283">它可能會讓使用者以復原永久刪除項目，如果尚未過期的項目已刪除的項目保留期間。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-283">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired.</span></span> <span data-ttu-id="fbcb4-284">身為系統管理員，您可能會有 [可復原的項目] 資料夾中的指定時間長度項目均可用於復原。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-284">As an admin you may have specified how long items in the Recoverable Items folder are available for recovery.</span></span> <span data-ttu-id="fbcb4-285">例如，有可能已在 30 天，使用者的 [刪除的項目] 資料夾中刪除任何項目原則與其他原則，可讓使用者復原在最多個其他的 14 天的 [可復原的項目資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-285">For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days.</span></span> <span data-ttu-id="fbcb4-286">不過，此 14 天之後，您可能仍然能夠使用本主題中的程序來復原使用者信箱中的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-286">However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="fbcb4-287">如果尚未已清除，並且尚未過期的項目已刪除的項目保留期間，使用者可以復原已刪除的項目。</span><span class="sxs-lookup"><span data-stu-id="fbcb4-287">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired.</span></span> <span data-ttu-id="fbcb4-288">若要協助復原刪除的項目在其信箱的使用者，其指向下列其中一個下列主題：</span><span class="sxs-lookup"><span data-stu-id="fbcb4-288">To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="fbcb4-289">在 Windows 版 Outlook 復原已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="fbcb4-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="fbcb4-290">在 Outlook 2010 中復原刪除的郵件</span><span class="sxs-lookup"><span data-stu-id="fbcb4-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="fbcb4-291">復原 Outlook Web App 中刪除的郵件或電子郵件</span><span class="sxs-lookup"><span data-stu-id="fbcb4-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="fbcb4-292">網頁型 Outlook 中還原已刪除電子郵件</span><span class="sxs-lookup"><span data-stu-id="fbcb4-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="fbcb4-293">復原已刪除的連絡人在 Outlook 中</span><span class="sxs-lookup"><span data-stu-id="fbcb4-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="fbcb4-294">在 Outlook.com 中還原已刪除電子郵件</span><span class="sxs-lookup"><span data-stu-id="fbcb4-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="fbcb4-295">返回頁首</span><span class="sxs-lookup"><span data-stu-id="fbcb4-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

