---
title: 復原使用者信箱中刪除的郵件 - 系統管理說明
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
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
description: '本文適用於系統管理員。沒有使用者永久刪除項目從其 Outlook 信箱吗？使用者想它們後，但不能復原這些。您可以復原已清除的項目如果他們尚未從使用者的信箱永久移除。 '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539992"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="98e51-106">復原使用者信箱中刪除的郵件 - 系統管理說明</span><span class="sxs-lookup"><span data-stu-id="98e51-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="98e51-p102">**本文為系統管理員。您嘗試要復原刪除的項目在您自己的信箱吗？** 請嘗試下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="98e51-p102">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?** Try one of the following:</span></span>
- [<span data-ttu-id="98e51-109">在 Windows 版 Outlook 復原已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="98e51-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="98e51-110">復原 Outlook Web App 中刪除的郵件或電子郵件</span><span class="sxs-lookup"><span data-stu-id="98e51-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="98e51-111">在網路上的 Outlook 中還原已刪除電子郵件</span><span class="sxs-lookup"><span data-stu-id="98e51-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="98e51-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="98e51-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="98e51-p103">沒有使用者永久刪除項目從其 Outlook 信箱吗？使用者想它們後，但不能復原這些。您可以復原已清除的項目如果他們尚未從使用者的信箱永久移除。達成此目的 Exchange Online 中使用就地 eDiscovery 工具來搜尋的已刪除的電子郵件及其他項目 — 例如連絡人、 行事曆約會和工作和 — 在使用者的信箱。如果您發現已刪除的項目時，您可以將其匯出至 PST 檔案 （也稱為 Outlook 資料檔案），該使用者接著可以使用回復到其信箱還原項目。</span><span class="sxs-lookup"><span data-stu-id="98e51-p103">Did a user permanently delete items from their Outlook mailbox? The user wants them back but can't recover them. You may be able recover the purged items if they haven't been permanently removed from the user's mailbox. You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox. If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="98e51-p104">以下是使用者的信箱中復原刪除的項目使用的步驟。將此時間？第一次可能需要完成所有步驟，視您的多少項目正在嘗試復原 20 或 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="98e51-p104">Here are the steps for recovering deleted items in a user's mailbox. How long will this take? The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="98e51-p105">您必須是**Exchange 系統管理員**或**全域管理員**Office 365 中也是組織管理角色群組的成員在 Exchange Online 才能執行本文中的步驟。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="98e51-p105">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article. For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="98e51-123">步驟 1： 指派自行 eDiscovery 權限</span><span class="sxs-lookup"><span data-stu-id="98e51-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="98e51-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="98e51-124"></span></span>

<span data-ttu-id="98e51-p106">第一個步驟是您自己的必要權限 Exchange Online 中指派讓您可以使用就地 eDiscovery 工具來搜尋使用者的信箱。您只能有一次執行這項作業。如果您有未來搜尋另一個信箱，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="98e51-p106">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox. You only have to do this once. If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="98e51-128">使用工作或學校帳戶[登入 Office 365 企業版的位置](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="98e51-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="98e51-129">選取 [應用程式啟動器圖示![Office 365 中的應用程式啟動器圖示](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中左上角按一下 [**系統管理**。</span><span class="sxs-lookup"><span data-stu-id="98e51-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="98e51-130">在 Office 365 系統管理中心的左方導覽，依序展開 [**系統置中**，] 和 [ **Exchange**。</span><span class="sxs-lookup"><span data-stu-id="98e51-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![Admin center 清單](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="98e51-132">在 Exchange 系統管理中心中，按一下 [**權限**，和 [**系統管理角色**。</span><span class="sxs-lookup"><span data-stu-id="98e51-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="98e51-133">在清單檢視中，選取 [**探索管理**，並按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)。</span><span class="sxs-lookup"><span data-stu-id="98e51-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![將您新增至探索管理角色群組在 EAC 中](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="98e51-135">在**角色群組**中，[**成員**、 按一下 [**新增**![新增圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="98e51-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="98e51-136">在 [**選取成員]** 中，即可從清單中選取的名稱、 按一下 [**新增**] 和 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="98e51-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="98e51-p107">您也可以新增您是的例如組織管理或 TenantAdmins 成員的群組。如果您將群組新增其他群組的成員會指派執行就地 eDiscovery 工具的必要權限。</span><span class="sxs-lookup"><span data-stu-id="98e51-p107">You can also add a group that you are a member of, such as Organization Management or TenantAdmins. If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="98e51-139">在**角色群組**中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="98e51-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="98e51-140">不在 Office 365 登入。</span><span class="sxs-lookup"><span data-stu-id="98e51-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="98e51-141">您必須登出您才能啟動下一個步驟如此新的權限才會生效。</span><span class="sxs-lookup"><span data-stu-id="98e51-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="98e51-p108">探索管理角色群組的成員可存取機密訊息內容。這包括搜尋組織中所有信箱、 預覽搜尋結果 （和其他信箱項目）、 將結果複製到探索信箱，並將搜尋結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-p108">Members of the Discovery Management role group can access sensitive message content. This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="98e51-144">回到頁首</span><span class="sxs-lookup"><span data-stu-id="98e51-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="98e51-145">步驟 2： 搜尋使用者的信箱已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="98e51-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="98e51-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="98e51-146"></span></span>

<span data-ttu-id="98e51-p109">當您執行就地 eDiscovery 搜尋時，搜尋信箱的可復原的項目資料夾自動隨附於搜尋。可復原的項目] 資料夾是永久刪除的項目儲存直到他們正在清除 （永久移除） 從信箱。因此，如果項目尚未清除，您應該能夠找到使用就地 eDiscovery 工具。</span><span class="sxs-lookup"><span data-stu-id="98e51-p109">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search. The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox. So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="98e51-150">使用工作或學校帳戶[登入 Office 365 企業版的位置](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="98e51-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="98e51-151">選取 [應用程式啟動器圖示![Office 365 中的應用程式啟動器圖示](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中左上角按一下 [**系統管理**。</span><span class="sxs-lookup"><span data-stu-id="98e51-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="98e51-152">在 Office 365 系統管理中心的左方導覽，依序展開 [**系統**] 和 [ **Exchange**。</span><span class="sxs-lookup"><span data-stu-id="98e51-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="98e51-153">在 Exchange 系統管理中心中，依序按一下 [**規範管理**、**就地 eDiscovery&amp;保留**，然後按一下 [**新增**![新增圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="98e51-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![在 EAC 中，在 [規範管理] 頁面上按一下 [就地 eDiscovery 和保留](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="98e51-155">在 [**名稱與描述**] 頁面上輸入的名稱 （例如您要復原的電子郵件的使用者名稱） 搜尋、 選擇性描述，以及然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="98e51-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="98e51-156">在 [**信箱**] 頁面上 [**搜尋指定信箱**] 和 [**新增**![新增圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="98e51-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![按一下 [指定信箱搜尋報的信箱搜尋](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="98e51-158">尋找並選取您要復原已刪除的電子郵件的使用者名稱、 按一下 [**新增**]，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="98e51-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="98e51-159">按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="98e51-159">Click **Next**.</span></span>
    
    <span data-ttu-id="98e51-p110">會顯示 [**搜尋查詢**] 頁面。這是用來定義可協助您尋找遺失的項目在使用者的信箱中的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="98e51-p110">The **Search query** page is displayed. This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="98e51-162">在 [**搜尋查詢**] 頁面上完成下列欄位：</span><span class="sxs-lookup"><span data-stu-id="98e51-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="98e51-p111">**包含的所有內容**選取此選項可在使用者的信箱搜尋結果中包含的所有內容。如果您選取這個選項，您無法指定其他搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="98e51-p111">**Include all content** Select this option to include all content in the user's mailbox in the search results. If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="98e51-165">**篩選依據準則**選取此選項可指定搜尋準則，包含關鍵字、 開始時間和結束日期、 寄件者和收件者的地址和訊息類型。</span><span class="sxs-lookup"><span data-stu-id="98e51-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![建立根據例如關鍵字、 日期範圍、 收件者] 和訊息類型的準則搜尋](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="98e51-167">**欄位**</span><span class="sxs-lookup"><span data-stu-id="98e51-167">**Field**</span></span>|<span data-ttu-id="98e51-168">**使用此選項，即可...]**</span><span class="sxs-lookup"><span data-stu-id="98e51-168">**Use this to...**</span></span>|
|:-----|:-----|
|![粉紅色圓形中的號碼 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="98e51-170">指定的關鍵字、 日期範圍、 收件者及訊息類型。</span><span class="sxs-lookup"><span data-stu-id="98e51-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![數個粉紅色圓形有兩個字。](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="98e51-172">搜尋郵件關鍵字或關鍵詞，並使用如**AND**或**OR**邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="98e51-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![數字三粉紅色圓形中。](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="98e51-174">搜尋傳送或接收的日期範圍內的郵件。</span><span class="sxs-lookup"><span data-stu-id="98e51-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![數字 4 粉紅色圓形中。](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="98e51-176">搜尋郵件從接收或傳送給特定的人。</span><span class="sxs-lookup"><span data-stu-id="98e51-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![編號的粉紅色圓形 5。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="98e51-178">搜尋的所有郵件類型或選取特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="98e51-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="98e51-p112">**就地保留設定**] 頁面上按一下 [**完成**] 以啟動搜尋]。若要復原已刪除的電子郵件，沒有使用者的信箱置於保留理由。</span><span class="sxs-lookup"><span data-stu-id="98e51-p112">On the **In-Place Hold settings** page, click **Finish** to start the search. To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="98e51-181">在您開始搜尋之後，Exchange 會顯示的估計項目總大小和根據您指定的準則搜尋將傳回的項目數。</span><span class="sxs-lookup"><span data-stu-id="98e51-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="98e51-p113">選取您剛建立的搜尋並按一下 [**重新整理**![重新整理](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)要更新的詳細資料窗格中顯示的資訊。**評估順利完成**狀態表示已完成搜尋。Exchange 也會顯示評估會有項目 （和其大小） 根據您在步驟 9 中指定的搜尋準則搜尋所找到的總數。</span><span class="sxs-lookup"><span data-stu-id="98e51-p113">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane. The status of **Estimate Succeeded** indicates that the search has finished. Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="98e51-p114">在 [詳細資料] 窗格中，按一下 [**預覽搜尋結果**來檢視所找到的項目。這可能會協助您識別您要尋找的項目。如果您尋找您嘗試復原的項目，請前往步驟 4 至搜尋結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-p114">In the details pane, click **Preview search results** to view the items that were found. This might help you identify the item(s) that you're looking for. If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![按一下 [檢視您嘗試復原的項目預覽搜尋結果](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="98e51-p115">如果您找不到您要尋找項目，您可以修改您的搜尋準則選取 [搜尋] 按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)，然後按一下 [**搜尋查詢**。變更的搜尋準則，然後重新執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="98e51-p115">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**. Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="98e51-191">回到頁首</span><span class="sxs-lookup"><span data-stu-id="98e51-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="98e51-192">（選用）步驟 3： 將搜尋結果複製到探索信箱</span><span class="sxs-lookup"><span data-stu-id="98e51-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="98e51-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="98e51-193"></span></span>

<span data-ttu-id="98e51-p116">如果您找不到項目來預覽搜尋結果或您想要查看使用者的 [可復原的項目] 資料夾中有哪些項目，然後您可以將搜尋結果複製到特殊信箱 （稱為 「 探索信箱），然後 t 在 web 上的 Outlook 中開啟該信箱o 檢視實際的項目。複製搜尋結果的最佳原因會讓您可以檢視使用者的 [可復原的項目] 資料夾中的項目。多個有可能您嘗試復原的項目位於清除子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="98e51-p116">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items. The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder. More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="98e51-197">在 Exchange 系統管理中心，移至 [**相符性管理** \> **就地 eDiscovery&amp;保留**。</span><span class="sxs-lookup"><span data-stu-id="98e51-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="98e51-198">在 [搜尋] 清單中選取您在步驟 2 中建立的搜尋。</span><span class="sxs-lookup"><span data-stu-id="98e51-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="98e51-199">按一下 [**搜尋**]![搜尋](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)，然後從下拉式清單中按一下 [**複製搜尋結果**。</span><span class="sxs-lookup"><span data-stu-id="98e51-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![按一下 [搜尋] 和 [複製搜尋結果](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="98e51-201">在**複製搜尋結果**] 頁面上，按一下 [**瀏覽**]。</span><span class="sxs-lookup"><span data-stu-id="98e51-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![保留未選取時復原刪除的項目] 核取方塊](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="98e51-203">**顯示名稱**] 下按一下 [**探索搜尋信箱**，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="98e51-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![將搜尋結果複製到預設的探索搜尋信箱](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="98e51-205">[探索搜尋信箱會自動建立 Office 365 組織中的預設探索信箱。</span><span class="sxs-lookup"><span data-stu-id="98e51-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="98e51-206">在**複製搜尋結果**] 頁面上，按一下 [**複製**到啟動程序來將搜尋結果複製到 [探索搜尋信箱]。</span><span class="sxs-lookup"><span data-stu-id="98e51-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![按一下 [複製到搜尋結果複製到 [探索搜尋信箱](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="98e51-208">按一下 [**重新整理**![重新整理](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)來更新顯示在 [詳細資料] 窗格中的複製狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="98e51-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="98e51-209">複製完成後，請按一下 [開啟探索搜尋信箱來檢視搜尋結果的 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="98e51-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![按一下 [開啟] 以移至要檢視搜尋結果的探索搜尋信箱](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="98e51-p117">搜尋結果複製到 [探索搜尋信箱會放在具有相同名稱為 「 就地 eDiscovery 搜尋的資料夾中。您可以按一下 [顯示資料夾中的項目] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="98e51-p117">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search. You can click a folder to display the items in that folder.</span></span>
    
    ![在 [探索搜尋信箱 ； 搜尋結果[清除] 資料夾中的項目僅可復原的系統管理員](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="98e51-p118">當您執行搜尋時，也會搜尋使用者的 [可復原的項目] 資料夾。這表示如果可復原的項目] 資料夾中的項目符合搜尋準則，其內含搜尋結果中。在 [刪除] 資料夾中項目是使用者永久刪除 （從 [刪除郵件] 資料夾刪除項目或選取它，並按下**Shift + Delete**項目。使用者可以使用 Outlook 或 Outlook web 上的復原刪除的郵件工具復原刪除資料夾中的項目。[清除] 資料夾中的項目是使用者使用復原刪除的郵件工具將清除的項目或其已自動清除套用至信箱原則的項目。不論執行哪項中的系統管理員可以復原 [清除] 資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="98e51-p118">When you run a search, the user's Recoverable Items folder is also searched. That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results. Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**. A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder. Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox. In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="98e51-p119">如果使用者找不到使用可復原的項目工具、 刪除項目但仍可復原的項目 （亦即它尚未永久移除從信箱），它是以上可能位於 [清除] 資料夾。因此，請務必在您嘗試復原使用者的刪除項目清除資料夾中尋找。</span><span class="sxs-lookup"><span data-stu-id="98e51-p119">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder. So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="98e51-222">回到頁首</span><span class="sxs-lookup"><span data-stu-id="98e51-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="98e51-223">步驟 4： 將搜尋結果匯出至 PST 檔</span><span class="sxs-lookup"><span data-stu-id="98e51-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="98e51-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="98e51-224"></span></span>

<span data-ttu-id="98e51-p120">尋找您嘗試為使用者復原的項目之後下, 一步是匯出至 PST 檔案已執行步驟 2 中的搜尋結果。使用者將會使用此 PST 檔案在下一個步驟中的還原刪除的項目至其信箱。</span><span class="sxs-lookup"><span data-stu-id="98e51-p120">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file. The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="98e51-227">在 Exchange 系統管理中心，移至 [**相符性管理** \> **就地 eDiscovery&amp;保留**。</span><span class="sxs-lookup"><span data-stu-id="98e51-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="98e51-228">在 [搜尋] 清單中選取您在步驟 2 中建立的搜尋。</span><span class="sxs-lookup"><span data-stu-id="98e51-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="98e51-229">按一下 [**匯出至 PST 檔案**。</span><span class="sxs-lookup"><span data-stu-id="98e51-229">Click **Export to a PST file**.</span></span>
    
    ![按一下 [匯出至 PST 檔](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="98e51-231">如果系統提示您安裝 eDiscovery 匯出工具，請按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="98e51-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="98e51-232">在 [eDiscovery PST 匯出工具中，按一下 [**瀏覽]** 以指定您要下載 PST 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="98e51-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![EDiscovery PST 匯出工具](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="98e51-234">您可以略過選項以啟用 deduplication 及包含無法搜尋的項目。</span><span class="sxs-lookup"><span data-stu-id="98e51-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="98e51-235">按一下 [**開始**PST 檔案下載到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="98e51-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="98e51-p121">**EDiscovery PST 匯出工具**會顯示匯出程序的狀態資訊。在匯出完成時，您可以存取下載位置的位置中的檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-p121">The **eDiscovery PST Export Tool** displays status information about the export process. When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="98e51-238">回到頁首</span><span class="sxs-lookup"><span data-stu-id="98e51-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="98e51-239">步驟 5： 還原至使用者的信箱已復原的項目</span><span class="sxs-lookup"><span data-stu-id="98e51-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="98e51-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="98e51-240"></span></span>

<span data-ttu-id="98e51-p122">最後一個步驟是使用在步驟 4 到使用者的信箱還原已復原的項目已匯出的 PST 檔案。您傳送給使用者的 PST 檔案之後，此步驟的其餘部分是由使用者開啟 PST 檔案，然後再將已復原的項目移至另一個資料夾信箱中執行。如需逐步說明，您也可以傳送使用者連結至本主題：[開啟及關閉 Outlook 資料檔 (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。或您可以使用者連結傳送[還原刪除的信箱使用 PST 檔案的項目](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)] 區段下，他可執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="98e51-p122">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox. After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox. For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2). Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="98e51-245">**將 PST 檔案傳送給使用者**</span><span class="sxs-lookup"><span data-stu-id="98e51-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="98e51-p123">您必須執行的最後一個步驟在步驟 4 中傳送已匯出的 PST 檔案給使用者。有幾種執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="98e51-p123">The final step that you need to perform is sending the PST file that was exported in step 4 to the user. There are a few ways to do this:</span></span>
  
- <span data-ttu-id="98e51-p124">附加至電子郵件訊息的 PST 檔案。如果 Outlook 設定為封鎖 PST 檔案，您會擁有 zip 檔案並再將它附加到郵件。以下是如何：</span><span class="sxs-lookup"><span data-stu-id="98e51-p124">Attach the PST file to an email message. If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message. Here's how:</span></span>
    
1. <span data-ttu-id="98e51-251">在 Windows 檔案總管或檔案總管] 中，瀏覽至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="98e51-p125">以滑鼠右鍵按一下檔案，然後選取 [**傳送至** \> **Compressed (zip) 的資料夾**。Windows 會建立新的 zip 檔案，並為其為 PST 檔案的相同名稱。</span><span class="sxs-lookup"><span data-stu-id="98e51-p125">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**. Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="98e51-254">附加至電子郵件訊息的壓縮的 PST 檔案並將其傳送給使用者，然後按一下滑鼠左鍵來解壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="98e51-255">將 PST 檔案複製到使用者可以存取並擷取它的共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="98e51-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="98e51-256">還原刪除的項目至其信箱之使用者所執行的下一步] 區段中的步驟。</span><span class="sxs-lookup"><span data-stu-id="98e51-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <span data-ttu-id="98e51-257">**若要使用 PST 檔案的信箱還原刪除的項目**</span><span class="sxs-lookup"><span data-stu-id="98e51-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="98e51-p126">您必須使用 Outlook 桌面應用程式使用 PST 檔案還原已刪除的項目。您無法使用 Outlook Web App 或 Outlook web 上的開啟 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-p126">You have to use the Outlook desktop app to restore a deleted item by using a PST file. You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="98e51-260">在 Outlook 2013 或 Outlook 2016 中，按一下 [**檔案**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="98e51-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="98e51-261">按一下 [**開啟&amp;匯出**，然後按一下 [**開啟 Outlook 資料檔案**。</span><span class="sxs-lookup"><span data-stu-id="98e51-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="98e51-262">瀏覽至您儲存您的系統管理員傳送 PST 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="98e51-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="98e51-263">選取 PST，然後按一下 [**開啟**。</span><span class="sxs-lookup"><span data-stu-id="98e51-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="98e51-264">PST 檔案會出現在 Outlook 中的左巡覽列。</span><span class="sxs-lookup"><span data-stu-id="98e51-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST 檔案會出現在 Outlook 中的左巡覽列](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="98e51-266">按一下箭頭以展開 [PST 檔案及資料夾下它找到您想要復原的項目。</span><span class="sxs-lookup"><span data-stu-id="98e51-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![在您想要復原的項目清除資料夾中尋找](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="98e51-p127">尋找您想要復原的項目清除資料夾中。這是隱藏的資料夾清除的項目移到。可能是您復原的系統管理員會在此資料夾中的項目。</span><span class="sxs-lookup"><span data-stu-id="98e51-p127">Look in the Purges folder for the item you want to recover. This is a hidden folder that purged items are moved to. It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="98e51-271">以滑鼠右鍵按一下您想要復原，然後按一下 [**移動**項的目\>**其他資料夾**。</span><span class="sxs-lookup"><span data-stu-id="98e51-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![按一下 [移動，然後選取 [其他] 資料夾](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="98e51-273">若要將項目移至 [收件匣，請按一下 [**收件匣**，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="98e51-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="98e51-274">**提示：** 若要復原其他類型的項目，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="98e51-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="98e51-275">若要復原的行事曆項目，以滑鼠右鍵按一下，] 和 [**移動** \> **其他資料夾** \> **行事曆**。</span><span class="sxs-lookup"><span data-stu-id="98e51-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="98e51-276">若要復原連絡人，以滑鼠右鍵按一下，] 和 [**移動** \> **其他資料夾** \> **連絡人**。</span><span class="sxs-lookup"><span data-stu-id="98e51-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="98e51-277">若要復原工作，以滑鼠右鍵按一下，] 和 [**移動** \> **其他資料夾** \> **工作**。</span><span class="sxs-lookup"><span data-stu-id="98e51-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![選取要移動其他類型的項目資料夾](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="98e51-279">完成作業後復原刪除的項目，以滑鼠右鍵按一下左巡覽列並選取 [**關閉"PST 檔案的名稱"** 的 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="98e51-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="98e51-280">回到頁首</span><span class="sxs-lookup"><span data-stu-id="98e51-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="98e51-281">其他資訊</span><span class="sxs-lookup"><span data-stu-id="98e51-281">More information</span></span>
<span data-ttu-id="98e51-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="98e51-282"></span></span>

- <span data-ttu-id="98e51-p128">您可能可能復原永久刪除的項目如果尚未過期的項目已刪除的項目保留期間的使用者。為您可能需要的系統管理員可復原的項目] 資料夾中的指定時間項目可用來復原。例如，可能會有已在 30 天內，使用者的已刪除的項目] 資料夾刪除任何項目的原則和其他原則，可讓使用者復原至另一個 14 天的可復原的項目資料夾中的項目。不過，此的 14 天後您可能仍能復原使用者的信箱中的項目使用本主題中的程序。</span><span class="sxs-lookup"><span data-stu-id="98e51-p128">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired. As an admin you may have specified how long items in the Recoverable Items folder are available for recovery. For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days. However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="98e51-p129">如果尚未被清除，如果尚未過期的項目已刪除的項目保留期間的使用者可以復原刪除的項目。若要可協助使用者復原已刪除的信箱中的項目，其指向其中一個下列主題：</span><span class="sxs-lookup"><span data-stu-id="98e51-p129">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="98e51-289">在 Windows 版 Outlook 復原已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="98e51-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="98e51-290">Outlook 2010 中復原刪除的郵件</span><span class="sxs-lookup"><span data-stu-id="98e51-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="98e51-291">復原 Outlook Web App 中刪除的郵件或電子郵件</span><span class="sxs-lookup"><span data-stu-id="98e51-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="98e51-292">在網路上的 Outlook 中還原已刪除電子郵件</span><span class="sxs-lookup"><span data-stu-id="98e51-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="98e51-293">復原已刪除的連絡人中的 Outlook</span><span class="sxs-lookup"><span data-stu-id="98e51-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="98e51-294">在 Outlook.com 中還原已刪除電子郵件</span><span class="sxs-lookup"><span data-stu-id="98e51-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="98e51-295">回到頁首</span><span class="sxs-lookup"><span data-stu-id="98e51-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

