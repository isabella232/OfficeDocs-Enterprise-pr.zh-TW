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
description: '本文適用於系統管理員。 使用者是否永久刪除其 Outlook 信箱中的專案？ 使用者想要回復但無法復原。 如果已清除的專案尚未從使用者的信箱中永久移除, 您可能會將它們復原。 '
ms.openlocfilehash: d4be48d6166d970572dd1cb343ccd83f22330e12
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203652"
---
<a name="__top"></a>
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a><span data-ttu-id="6e246-106">復原使用者信箱中刪除的郵件 - 系統管理說明</span><span class="sxs-lookup"><span data-stu-id="6e246-106">Recover deleted items in a user mailbox - Admin Help</span></span>

<span data-ttu-id="6e246-107">**本文適用于系統管理員。您是否嘗試復原您自己信箱中已刪除的郵件？**</span><span class="sxs-lookup"><span data-stu-id="6e246-107">**This article is for administrators. Are you trying to recover deleted items in your own mailbox?**</span></span> <span data-ttu-id="6e246-108">請嘗試下列其中一項:</span><span class="sxs-lookup"><span data-stu-id="6e246-108">Try one of the following:</span></span>
- [<span data-ttu-id="6e246-109">在 Windows 版 Outlook 復原已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="6e246-109">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [<span data-ttu-id="6e246-110">復原 Outlook Web App 中刪除的郵件或電子郵件</span><span class="sxs-lookup"><span data-stu-id="6e246-110">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [<span data-ttu-id="6e246-111">在網頁版 Outlook 中還原已刪除的電子郵件</span><span class="sxs-lookup"><span data-stu-id="6e246-111">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [<span data-ttu-id="6e246-112">Outlook.com</span><span class="sxs-lookup"><span data-stu-id="6e246-112">Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
<span data-ttu-id="6e246-113">使用者是否永久刪除其 Outlook 信箱中的專案？</span><span class="sxs-lookup"><span data-stu-id="6e246-113">Did a user permanently delete items from their Outlook mailbox?</span></span> <span data-ttu-id="6e246-114">使用者想要回復但無法復原。</span><span class="sxs-lookup"><span data-stu-id="6e246-114">The user wants them back but can't recover them.</span></span> <span data-ttu-id="6e246-115">如果已清除的專案尚未從使用者的信箱中永久移除, 您可能會將它們復原。</span><span class="sxs-lookup"><span data-stu-id="6e246-115">You may be able recover the purged items if they haven't been permanently removed from the user's mailbox.</span></span> <span data-ttu-id="6e246-116">您可以在 Exchange Online 中使用就地 eDiscovery 工具, 搜尋使用者信箱中已刪除的電子郵件和其他專案, 例如連絡人、行事曆約會及工作。</span><span class="sxs-lookup"><span data-stu-id="6e246-116">You do this by using the In-Place eDiscovery tool in Exchange Online to search for deleted email and other items—and such as contacts, calendar appointments, and tasks—in a user's mailbox.</span></span> <span data-ttu-id="6e246-117">如果您發現已刪除的專案, 您可以將其匯出至 PST 檔案 (也稱為 Outlook 資料檔案), 使用者可以使用該檔案將專案還原回其信箱。</span><span class="sxs-lookup"><span data-stu-id="6e246-117">If you find the deleted items, you can export them to a PST file (also called an Outlook Data File), which the user can then use to restore the items back to their mailbox.</span></span>
  
<span data-ttu-id="6e246-118">以下是復原使用者信箱中已刪除郵件的步驟。</span><span class="sxs-lookup"><span data-stu-id="6e246-118">Here are the steps for recovering deleted items in a user's mailbox.</span></span> <span data-ttu-id="6e246-119">這會花費多久時間？</span><span class="sxs-lookup"><span data-stu-id="6e246-119">How long will this take?</span></span> <span data-ttu-id="6e246-120">第一次可能需要20或30分鐘, 以完成所有步驟, 視您嘗試復原的專案數而定。</span><span class="sxs-lookup"><span data-stu-id="6e246-120">The first time might take 20 or 30 minutes to complete all the steps, depending on how many items you're trying to recover.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6e246-121">您必須是 Office 365 中的**Exchange 系統管理員**或**全域系統管理員**, 或是 Exchange Online 中的組織管理角色群組的成員, 才可執行本文中的步驟。</span><span class="sxs-lookup"><span data-stu-id="6e246-121">You have to be an **Exchange administrator** or **Global administrator** in Office 365 or be a member of the Organization Management role group in Exchange Online to perform the steps in this article.</span></span> <span data-ttu-id="6e246-122">如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="6e246-122">For more information, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span> 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a><span data-ttu-id="6e246-123">步驟 1: 指派自己的 eDiscovery 許可權</span><span class="sxs-lookup"><span data-stu-id="6e246-123">Step 1: Assign yourself eDiscovery permissions</span></span>
<span data-ttu-id="6e246-124"><a name="step1"> </a></span><span class="sxs-lookup"><span data-stu-id="6e246-124"></span></span>

<span data-ttu-id="6e246-125">第一步是在 Exchange Online 中為自己指派必要的許可權, 讓您可以使用就地 eDiscovery 工具來搜尋使用者的信箱。</span><span class="sxs-lookup"><span data-stu-id="6e246-125">The first step is to assign yourself the necessary permissions in Exchange Online so you can use the In-Place eDiscovery tool to search a user's mailbox.</span></span> <span data-ttu-id="6e246-126">您只需執行這項操作一次。</span><span class="sxs-lookup"><span data-stu-id="6e246-126">You only have to do this once.</span></span> <span data-ttu-id="6e246-127">如果您必須在未來搜尋其他信箱, 您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="6e246-127">If you have to search another mailbox in the future, you can skip this step.</span></span>
  
1. <span data-ttu-id="6e246-128">找不到您要的 App 嗎？請從應用程式啟動器選取 [所有 App] 以查看依字母順序排序的可用 Office 365 App 清單。您可從該處搜尋特定的 App。</span><span class="sxs-lookup"><span data-stu-id="6e246-128">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="6e246-129">在左上方的 Office ![365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中選取應用程式啟動器圖示, 然後按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-129">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="6e246-130">在 Office 365 系統管理中心的左側導覽中, 展開 [系統**管理中心**], 然後按一下 [ **Exchange**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-130">In the left navigation in the Office 365 admin center, expand **Admin centers**, and then click **Exchange**.</span></span>
    
    ![系統管理中心清單](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. <span data-ttu-id="6e246-132">在 Exchange 系統管理中心, 按一下 [**許可權**], 然後按一下 [**管理角色**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-132">In the Exchange admin center, click **Permissions**, and then click **Admin roles**.</span></span>
    
5. <span data-ttu-id="6e246-133">在清單視圖中, 選取 [**探索管理**], 然後按一下 [**編輯**![編輯圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)]。</span><span class="sxs-lookup"><span data-stu-id="6e246-133">In the list view, select **Discovery Management**, and then click **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).</span></span>
    
    ![將自己新增至 EAC 中的 [探索管理] 角色群組](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. <span data-ttu-id="6e246-135">在 **[角色群組**] 的 [**成員**] 下,](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)按一下 [**新增**![] 圖示。</span><span class="sxs-lookup"><span data-stu-id="6e246-135">In **Role Group**, under **Members**, click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
7. <span data-ttu-id="6e246-136">在 [**選取成員**] 中, 從名稱清單中選取您自己, 然後按一下 [**新增**], 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-136">In **Select Members**, select yourself from the list of names, click **Add**, and then click **OK**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="6e246-137">您也可以新增您是其成員的群組, 例如「組織管理」或「TenantAdmins」。</span><span class="sxs-lookup"><span data-stu-id="6e246-137">You can also add a group that you are a member of, such as Organization Management or TenantAdmins.</span></span> <span data-ttu-id="6e246-138">如果您新增群組, 將會為群組的其他成員指派執行就地 eDiscovery 工具所需的許可權。</span><span class="sxs-lookup"><span data-stu-id="6e246-138">If you add a group, other members of the group will be assigned the necessary permissions to run the In-Place eDiscovery tool.</span></span> 
  
8. <span data-ttu-id="6e246-139">在 [**角色群組**] 中, 按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-139">In **Role Group**, click **Save**.</span></span>
    
9. <span data-ttu-id="6e246-140">登出 Office 365。</span><span class="sxs-lookup"><span data-stu-id="6e246-140">Sign out of Office 365.</span></span>
    
    <span data-ttu-id="6e246-141">您必須先登出, 才可開始下一個步驟, 讓新許可權生效。</span><span class="sxs-lookup"><span data-stu-id="6e246-141">You have to sign out before you start the next step so the new permissions will take effect.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="6e246-142">探索管理角色群組的成員可存取機密訊息內容。</span><span class="sxs-lookup"><span data-stu-id="6e246-142">Members of the Discovery Management role group can access sensitive message content.</span></span> <span data-ttu-id="6e246-143">這包括搜尋組織中的所有信箱、預覽搜尋結果 (和其他信箱專案)、將結果複製到探索信箱, 以及將搜尋結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e246-143">This includes searching all mailboxes in your organization, previewing the search results (and other mailbox items), copying the results to a discovery mailbox, and exporting the search results to a PST file.</span></span> 
  
[<span data-ttu-id="6e246-144">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6e246-144">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a><span data-ttu-id="6e246-145">步驟 2: 在使用者的信箱中搜尋刪除的專案</span><span class="sxs-lookup"><span data-stu-id="6e246-145">Step 2: Search the user's mailbox for deleted items</span></span>
<span data-ttu-id="6e246-146"><a name="step2"> </a></span><span class="sxs-lookup"><span data-stu-id="6e246-146"></span></span>

<span data-ttu-id="6e246-147">當您執行就地 eDiscovery 搜尋時, 您搜尋的信箱中的 [可復原的專案] 資料夾會自動包含在搜尋中。</span><span class="sxs-lookup"><span data-stu-id="6e246-147">When you run an In-Place eDiscovery search, the Recoverable Items folder in the mailbox that you search is automatically included in the search.</span></span> <span data-ttu-id="6e246-148">[可復原的專案] 資料夾會儲存永久刪除的專案, 直到清除 (永久移除) 信箱為止。</span><span class="sxs-lookup"><span data-stu-id="6e246-148">The Recoverable Items folder is where permanently deleted items are stored until they're purged (permanently removed) from the mailbox.</span></span> <span data-ttu-id="6e246-149">因此, 如果專案尚未清除, 您應該可以使用就地 eDiscovery 工具來找到。</span><span class="sxs-lookup"><span data-stu-id="6e246-149">So, if an item hasn't been purged, you should be able to find it by using the In-Place eDiscovery tool.</span></span>
  
1. <span data-ttu-id="6e246-150">找不到您要的 App 嗎？請從應用程式啟動器選取 [所有 App] 以查看依字母順序排序的可用 Office 365 App 清單。您可從該處搜尋特定的 App。</span><span class="sxs-lookup"><span data-stu-id="6e246-150">[Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your work or school account.</span></span> 
    
2. <span data-ttu-id="6e246-151">在左上方的 Office ![365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)中選取應用程式啟動器圖示, 然後按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-151">Select the app launcher icon ![The app launcher icon in Office 365](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) in the upper-left and click **Admin**.</span></span>
    
3. <span data-ttu-id="6e246-152">在 Office 365 系統管理中心的左側導覽中, 展開 [**管理員**], 然後按一下 [ **Exchange**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-152">In the left navigation in the Office 365 admin center, expand **Admin**, and then click **Exchange**.</span></span>
    
4. <span data-ttu-id="6e246-153">在 Exchange 系統管理中心中, 按一下 [**規範管理**], 按一下 [**就地&amp; eDiscovery 保留**], 然後按一下 [**新增**![] 圖示](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。</span><span class="sxs-lookup"><span data-stu-id="6e246-153">In the Exchange admin center, click **Compliance management**, click **In-Place eDiscovery &amp; Hold**, and then click **New**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![在 EAC 的 [規範管理] 頁面上, 按一下 [就地 eDiscovery 和保留]](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. <span data-ttu-id="6e246-155">在 [**名稱與描述**] 頁面上, 輸入搜尋的名稱 (例如您要復原電子郵件的使用者名稱), 選擇性描述, 然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-155">On the **Name and description** page, type a name for the search (such as the name of the user you're recovering email for), an optional description, and then click **Next**.</span></span>
    
6. <span data-ttu-id="6e246-156">在 [**信箱**] 頁面上, 按一下 [**指定要搜尋的信箱**], 然後](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)按一下 [**新增**![] 圖示。</span><span class="sxs-lookup"><span data-stu-id="6e246-156">On the **Mailboxes** page, click **Specify mailboxes to search**, and then click **Add**![Add icon](media/8ee52980-254b-440b-99a2-18d068de62d3.gif).</span></span>
    
    ![按一下 [指定要搜尋的信箱] 搜尋 specifc 信箱](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. <span data-ttu-id="6e246-158">尋找並選取您要復原已刪除電子郵件的使用者名稱, 然後按一下 [**新增**], 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-158">Find and select the name of the user that you're recovering the deleted email for, click **Add**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="6e246-159">按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6e246-159">Click **Next**.</span></span>
    
    <span data-ttu-id="6e246-160">隨即會顯示 [**搜尋查詢**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6e246-160">The **Search query** page is displayed.</span></span> <span data-ttu-id="6e246-161">您可以在這裡定義搜尋準則, 以協助您找出使用者信箱中遺失的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-161">This is where you define the search criteria that will help you find the missing items in user's mailbox.</span></span> 
    
9. <span data-ttu-id="6e246-162">在 [**搜尋查詢**] 頁面上, 完成下欄欄位:</span><span class="sxs-lookup"><span data-stu-id="6e246-162">On the **Search query** page, complete the following fields:</span></span> 
    
  - <span data-ttu-id="6e246-163">**包含所有內容**選取此選項可將使用者信箱中的所有內容包含在搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="6e246-163">**Include all content** Select this option to include all content in the user's mailbox in the search results.</span></span> <span data-ttu-id="6e246-164">如果選取這個選項，便無法指定其他搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="6e246-164">If you select this option, you can't specify additional search criteria.</span></span> 
    
  - <span data-ttu-id="6e246-165">**根據準則篩選**選取此選項以指定搜尋準則, 包括關鍵字、開始與結束日期、寄件者和收件者位址, 以及郵件類型。</span><span class="sxs-lookup"><span data-stu-id="6e246-165">**Filter based on criteria** Select this option to specify the search criteria, including keywords, start and end dates, sender and recipient addresses, and message types.</span></span> 
    
    ![根據諸如關鍵字、日期範圍、收件者和郵件類型之類的準則建立搜索](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|<span data-ttu-id="6e246-167">**Field**</span><span class="sxs-lookup"><span data-stu-id="6e246-167">**Field**</span></span>|<span data-ttu-id="6e246-168">**使用此 .。。**</span><span class="sxs-lookup"><span data-stu-id="6e246-168">**Use this to...**</span></span>|
|:-----|:-----|
|![粉紅色圓圈中的數字 1](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |<span data-ttu-id="6e246-170">指定關鍵字、日期範圍、收件者和郵件類型。</span><span class="sxs-lookup"><span data-stu-id="6e246-170">Specify keywords, date range, recipients, and message types.</span></span>  <br/> |
|![粉紅色圓圈中的數字 2。](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |<span data-ttu-id="6e246-172">搜尋含有關鍵詞或片語的郵件, 並使用邏輯運算子 (例如**and**或**or**)。</span><span class="sxs-lookup"><span data-stu-id="6e246-172">Search for messages with keywords or phrases, and use logical operators such as **AND** or **OR**.</span></span>  <br/> |
|![粉紅色圓圈中的數字 3。](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |<span data-ttu-id="6e246-174">搜尋在日期範圍內傳送或接收的郵件。</span><span class="sxs-lookup"><span data-stu-id="6e246-174">Search for messages sent or received within a date range.</span></span>  <br/> |
|![粉紅色圓圈中的數字 4。](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |<span data-ttu-id="6e246-176">搜尋收到或傳送給特定人員的郵件。</span><span class="sxs-lookup"><span data-stu-id="6e246-176">Search for messages received from or sent to specific people.</span></span>  <br/> |
|![粉紅色圓圈中的數位5。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |<span data-ttu-id="6e246-178">搜尋所有郵件類型或選取特定的郵件類型。</span><span class="sxs-lookup"><span data-stu-id="6e246-178">Search for all message types or select specific ones.</span></span>  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. <span data-ttu-id="6e246-179">在 [**就地保留設定**] 頁面上, 按一下 **[完成]** 以啟動搜尋。</span><span class="sxs-lookup"><span data-stu-id="6e246-179">On the **In-Place Hold settings** page, click **Finish** to start the search.</span></span> <span data-ttu-id="6e246-180">若要復原已刪除的電子郵件, 沒有理由將使用者的信箱保留在暫止狀態。</span><span class="sxs-lookup"><span data-stu-id="6e246-180">To recover deleted email, there's no reason to place the user's mailbox on hold.</span></span> 
    
    <span data-ttu-id="6e246-181">開始搜尋之後, Exchange 會根據您指定的準則, 顯示搜尋所傳回的總大小和專案數。</span><span class="sxs-lookup"><span data-stu-id="6e246-181">After you start the search, Exchange will display an estimate of the total size and number of items that will be returned by the search based on the criteria you specified.</span></span>
    
11. <span data-ttu-id="6e246-182">選取您剛建立的搜尋, 然後\*\*\*\*![按一下 [](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)重新整理重新整理] 以更新顯示在詳細資料窗格中的資訊。</span><span class="sxs-lookup"><span data-stu-id="6e246-182">Select the search you just created and click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information displayed in the details pane.</span></span> <span data-ttu-id="6e246-183">[**評估成功**] 的狀態表示已完成搜尋。</span><span class="sxs-lookup"><span data-stu-id="6e246-183">The status of **Estimate Succeeded** indicates that the search has finished.</span></span> <span data-ttu-id="6e246-184">Exchange 也會根據您在步驟9中指定的搜尋準則, 來顯示搜尋所找到的總專案數 (及其大小)。</span><span class="sxs-lookup"><span data-stu-id="6e246-184">Exchange also displays an estimate of the total number of items (and their size) found by the search based on the search criteria you specified in step 9.</span></span> 
    
12. <span data-ttu-id="6e246-185">在詳細資料窗格中, 按一下 [**預覽搜尋結果**] 以查看找到的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-185">In the details pane, click **Preview search results** to view the items that were found.</span></span> <span data-ttu-id="6e246-186">這可能會協助您識別所要尋找的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-186">This might help you identify the item(s) that you're looking for.</span></span> <span data-ttu-id="6e246-187">如果您發現要嘗試復原的專案, 請移至步驟 4, 將搜尋結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e246-187">If you find the item(s) you're trying to recover, go to step 4 to export the search results to a PST file.</span></span> 
    
    ![按一下 [預覽搜尋結果] 以查看您要嘗試復原的專案](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. <span data-ttu-id="6e246-189">如果您找不到所要尋找的專案, 可以選取搜尋, 按一下 [**編輯**![編輯] 圖示](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), 然後按一下 [**搜尋查詢**], 以修正您的搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="6e246-189">If you don't find what you're looking for, you can revise your search criteria by selecting the search, clicking **Edit**![Edit icon](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif), and then clicking **Search query**.</span></span> <span data-ttu-id="6e246-190">變更搜尋準則, 然後重新執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="6e246-190">Change the search criteria and then rerun the search.</span></span>
    
[<span data-ttu-id="6e246-191">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6e246-191">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a><span data-ttu-id="6e246-192">步驟步驟 3: 將搜尋結果複製到探索信箱</span><span class="sxs-lookup"><span data-stu-id="6e246-192">(Optional) Step 3: Copy the search results to a discovery mailbox</span></span>
<span data-ttu-id="6e246-193"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="6e246-193"></span></span>

<span data-ttu-id="6e246-194">如果您無法透過預覽搜尋結果找到專案, 或想要查看使用者的 [可復原的專案] 資料夾中的專案, 則可以將搜尋結果複製到特殊信箱 (稱為探索信箱), 然後在 web 的 Outlook 中開啟該信箱o 查看實際專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-194">If you can't find an items by previewing the search results or if you want to see which items are in the user's Recoverable Items folder, then you can copy the search results to a special mailbox (called a discovery mailbox) and then open that mailbox in Outlook on the web to view the actual items.</span></span> <span data-ttu-id="6e246-195">複製搜尋結果的最佳原因是, 您可以在使用者的 [可復原的專案] 資料夾中查看專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-195">The best reason to copy the search results is so you can view the items in the user's Recoverable Items folder.</span></span> <span data-ttu-id="6e246-196">您嘗試復原的專案可能會位於 [清除] 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6e246-196">More than likely, the item you're trying to recover is located in the Purges subfolder.</span></span> 
  
1. <span data-ttu-id="6e246-197">在 Exchange 系統管理中心, 移至 [**規範管理** \>就地**eDiscovery &amp;保留**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-197">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="6e246-198">在搜尋清單中, 選取您在步驟2中建立的搜尋。</span><span class="sxs-lookup"><span data-stu-id="6e246-198">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="6e246-199">按一下\*\*\*\*![[搜尋](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)搜尋], 然後按一下下拉式清單中的 [**複製搜尋結果**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-199">Click **Search**![search](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png), and then click **Copy search results** from the drop-down list.</span></span> 
    
    ![按一下 [搜尋], 然後按一下 [複製搜尋結果]。](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. <span data-ttu-id="6e246-201">在 [**複製搜尋結果**] 頁面上, 按一下 **[流覽]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-201">On the **Copy Search Results** page, click **Browse**.</span></span>
    
    ![復原刪除的郵件時, 保持核取方塊為未選取狀態](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. <span data-ttu-id="6e246-203">在 [**顯示名稱**] 下, 按一下 [**探索搜尋信箱**], 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-203">Under **Display Name**, click **Discovery Search Mailbox**, and then click **OK**.</span></span>
    
    ![將搜尋結果複製到預設的探索搜尋信箱](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > <span data-ttu-id="6e246-205">探索搜尋信箱是在您的 Office 365 組織中自動建立的預設探索信箱。</span><span class="sxs-lookup"><span data-stu-id="6e246-205">The Discovery Search Mailbox is a default discovery mailbox that is automatically created in your Office 365 organization.</span></span> 
  
6. <span data-ttu-id="6e246-206">回到 [**複製搜尋結果**] 頁面上, 按一下 [**複製**] 以開始將搜尋結果複製到 [探索搜尋信箱] 的程式。</span><span class="sxs-lookup"><span data-stu-id="6e246-206">Back on the **Copy Search Results** page, click **Copy** to start the process to copy the search results to the Discovery Search Mailbox.</span></span> 
    
    ![按一下 [複製], 將搜尋結果複製到探索搜尋信箱](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. <span data-ttu-id="6e246-208">按一下 [重新](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)整理重新整理] 以更新詳細資料窗格中所顯示之複製狀態的相關資訊。 \*\*\*\* ![</span><span class="sxs-lookup"><span data-stu-id="6e246-208">Click **Refresh**![refresh](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) to update the information about the copying status that is displayed in the details pane.</span></span> 
    
8. <span data-ttu-id="6e246-209">當複製完成時, 按一下 [**開啟**] 以開啟 [探索搜尋] 信箱以查看搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="6e246-209">When the copying is complete, click **Open** to open the Discovery Search Mailbox to view the search results.</span></span> 
    
    ![按一下 [開啟] 以移至探索搜尋信箱以查看搜尋結果](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    <span data-ttu-id="6e246-211">複製到探索搜尋信箱的搜尋結果, 會放在與就地 eDiscovery 搜尋具有相同名稱的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6e246-211">The search results copied to the Discovery Search Mailbox are placed in a folder that has the same name as the In-Place eDiscovery search.</span></span> <span data-ttu-id="6e246-212">您可以按一下資料夾, 以顯示該資料夾中的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-212">You can click a folder to display the items in that folder.</span></span>
    
    ![搜尋搜尋信箱中的搜尋結果;[清除] 資料夾中的專案只能由系統管理員復原](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    <span data-ttu-id="6e246-214">當您執行搜尋時, 也會搜尋使用者的 [可復原的專案] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e246-214">When you run a search, the user's Recoverable Items folder is also searched.</span></span> <span data-ttu-id="6e246-215">這表示, 如果 [可復原的專案] 資料夾中的專案符合搜尋準則, 則會包含在搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="6e246-215">That means if items in the Recoverable Items folder meet the search criteria, they are included in the search results.</span></span> <span data-ttu-id="6e246-216">[刪除專案] 資料夾中的專案是指使用者會永久刪除的專案 (透過從 [刪除的郵件] 資料夾中刪除專案, 或選取並按下**Shift + Delete**即可)。</span><span class="sxs-lookup"><span data-stu-id="6e246-216">Items in the Deletions folder are items that the user permanently deleted (by deleting an item from the Deleted Items folder or by selecting it and pressing **Shift+Delete**.</span></span> <span data-ttu-id="6e246-217">使用者可以使用 Outlook 或 Outlook 網頁版中的 [復原刪除的郵件] 工具, 復原 [刪除] 資料夾中的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-217">A user can use the Recover Deleted Items tool in Outlook or Outlook on the web to recover items in the Deletions folder.</span></span> <span data-ttu-id="6e246-218">[清除] 資料夾中的專案是指使用者使用 [復原刪除的郵件] 工具清除的專案, 或已套用至信箱的原則所自動清除的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-218">Items in the Purges folder are items that the user purged by using the Recover Deleted Items tool or items they were automatically purged by a policy applied to the mailbox.</span></span> <span data-ttu-id="6e246-219">在這兩種情況下, 只有系統管理員可以復原 [清除] 資料夾中的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-219">In either case, only an admin can recover items in the Purges folder.</span></span> 
    
    > [!TIP]
    > <span data-ttu-id="6e246-220">如果使用者無法使用 [可復原的專案] 工具找到已刪除的專案, 但該專案仍可復原 (表示尚未從信箱中永久移除), 則它很可能是位於 [清除] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6e246-220">If a user can't find a deleted item using the Recoverable Items tool, but that item is still recoverable (meaning that it hasn't been permanently removed from the mailbox), it's more than likely located in the Purges folder.</span></span> <span data-ttu-id="6e246-221">因此, 請務必在 [清除] 資料夾中尋找您要為使用者復原的已刪除專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-221">So, be sure to look in the Purges folder for the deleted item you're trying to recover for a user.</span></span> 
  
[<span data-ttu-id="6e246-222">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6e246-222">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a><span data-ttu-id="6e246-223">步驟 4: 將搜尋結果匯出至 PST 檔案</span><span class="sxs-lookup"><span data-stu-id="6e246-223">Step 4: Export the search results to a PST file</span></span>
<span data-ttu-id="6e246-224"><a name="step4"> </a></span><span class="sxs-lookup"><span data-stu-id="6e246-224"></span></span>

<span data-ttu-id="6e246-225">在您找到您要為使用者復原的專案之後, 下一步是從您在步驟2中執行的搜尋, 將結果匯出至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e246-225">After you find the item you're trying to recover for a user, the next step is to export the results from the search you ran in Step 2 to a PST file.</span></span> <span data-ttu-id="6e246-226">使用者會在下一個步驟中使用此 PST 檔案, 將刪除的專案還原至其信箱。</span><span class="sxs-lookup"><span data-stu-id="6e246-226">The user will use this PST file in the next step to restore the deleted item to their mailbox.</span></span>
  
1. <span data-ttu-id="6e246-227">在 Exchange 系統管理中心, 移至 [**規範管理** \>就地**eDiscovery &amp;保留**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-227">In the Exchange admin center, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.</span></span>
    
2. <span data-ttu-id="6e246-228">在搜尋清單中, 選取您在步驟2中建立的搜尋。</span><span class="sxs-lookup"><span data-stu-id="6e246-228">In the list of searches, select the search that you created in Step 2.</span></span>
    
3. <span data-ttu-id="6e246-229">按一下 [**匯出為 PST**檔案]。</span><span class="sxs-lookup"><span data-stu-id="6e246-229">Click **Export to a PST file**.</span></span>
    
    ![按一下 [匯出為 PST 檔案]](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. <span data-ttu-id="6e246-231">如果系統提示您安裝 eDiscovery 匯出工具, 請按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-231">If you're prompted to install the eDiscovery Export Tool, click **Run**.</span></span>
    
5. <span data-ttu-id="6e246-232">在 [eDiscovery PST 匯出工具] 中, 按一下 **[流覽]** 以指定您要下載 PST 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="6e246-232">In the eDiscovery PST Export Tool, click **Browse** to specify the location where you want to download the PST file.</span></span> 
    
    ![EDiscovery PST 匯出工具](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    <span data-ttu-id="6e246-234">您可以忽略選項啟用重復資料刪除, 並包含無法搜尋的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-234">You can ignore the options to enable deduplication and include unsearchable items.</span></span>
    
6. <span data-ttu-id="6e246-235">按一下 [**開始**], 將 PST 檔案下載至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="6e246-235">Click **Start** to download the PST file to your computer.</span></span> 
    
    <span data-ttu-id="6e246-236">**EDISCOVERY PST 匯出工具**會顯示匯出程式的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="6e246-236">The **eDiscovery PST Export Tool** displays status information about the export process.</span></span> <span data-ttu-id="6e246-237">匯出完成時, 您可以在下載檔案的位置存取該檔案。</span><span class="sxs-lookup"><span data-stu-id="6e246-237">When the export is complete, you can access the file in the location where it was downloaded.</span></span> 
    
[<span data-ttu-id="6e246-238">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6e246-238">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a><span data-ttu-id="6e246-239">步驟 5: 將復原的專案還原至使用者的信箱</span><span class="sxs-lookup"><span data-stu-id="6e246-239">Step 5: Restore the recovered items to the user's mailbox</span></span>
<span data-ttu-id="6e246-240"><a name="step5"> </a></span><span class="sxs-lookup"><span data-stu-id="6e246-240"></span></span>

<span data-ttu-id="6e246-241">最後一個步驟是使用在步驟4中匯出的 PST 檔案, 將復原的專案還原至使用者的信箱。</span><span class="sxs-lookup"><span data-stu-id="6e246-241">The final step is to use the PST file that was exported in step 4 to restore the recovered items to the user's mailbox.</span></span> <span data-ttu-id="6e246-242">在您將 PST 檔案傳送給使用者之後, 這個步驟的其餘部分是由使用者執行, 以開啟 PST 檔案, 然後將復原的專案移至其信箱中的另一個資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e246-242">After you send the PST file to the user, the remainder of this step is performed by the user to open the PST file and then move the recovered items to another folder in their mailbox.</span></span> <span data-ttu-id="6e246-243">如需逐步指示, 您也可以將本主題的連結傳送給使用者:[開啟和關閉 Outlook 資料檔案 (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。</span><span class="sxs-lookup"><span data-stu-id="6e246-243">For step-by-step instructions, you can also send the user a link to this topic: [Open and close Outlook Data Files (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2).</span></span> <span data-ttu-id="6e246-244">或者, 您可以使用下面的 [PST 檔案] 區段, 將 [[還原已刪除的郵件](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)] 連結傳送至信箱, 並要求他們執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="6e246-244">Or you can send the user a link to the [Restore deleted items to a mailbox using a PST file](recover-deleted-items-in-a-mailbox.md#restoredeleteditems) section below and ask them to perform these steps.</span></span> 
  
 <span data-ttu-id="6e246-245">**將 PST 檔案傳送給使用者**</span><span class="sxs-lookup"><span data-stu-id="6e246-245">**Send the PST file to the user**</span></span>
  
<span data-ttu-id="6e246-246">您需要執行的最後一個步驟是將在步驟4中匯出的 PST 檔案傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="6e246-246">The final step that you need to perform is sending the PST file that was exported in step 4 to the user.</span></span> <span data-ttu-id="6e246-247">有幾種方式可以這麼做:</span><span class="sxs-lookup"><span data-stu-id="6e246-247">There are a few ways to do this:</span></span>
  
- <span data-ttu-id="6e246-248">將 PST 檔案附加到電子郵件。</span><span class="sxs-lookup"><span data-stu-id="6e246-248">Attach the PST file to an email message.</span></span> <span data-ttu-id="6e246-249">如果 Outlook 設定為封鎖 PST 檔案, 您必須先壓縮該檔案, 然後將它附加至郵件。</span><span class="sxs-lookup"><span data-stu-id="6e246-249">If Outlook is configured to block PST files, then you will have to zip the file and then attach it to the message.</span></span> <span data-ttu-id="6e246-250">方法如下：</span><span class="sxs-lookup"><span data-stu-id="6e246-250">Here's how:</span></span>
    
1. <span data-ttu-id="6e246-251">在 [Windows Explorer] 或 [檔案瀏覽器] 中, 流覽至 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e246-251">In Windows Explorer or File Explorer, browse to the PST file.</span></span>
    
2. <span data-ttu-id="6e246-252">以滑鼠右鍵按一下檔案, 然後選取 [**傳送至** \> **壓縮 (zipped) 資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-252">Right-click the file, and then select **Send to** \> **Compressed (zipped) folder**.</span></span> <span data-ttu-id="6e246-253">Windows 會建立新的 zip 檔案, 並將其命名為與 PST 檔案相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e246-253">Windows creates a new zip file and gives it an identical name as the PST file.</span></span>
    
3. <span data-ttu-id="6e246-254">將壓縮的 PST 檔案附加到電子郵件, 並將其傳送給使用者, 然後按一下該檔案即可將檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="6e246-254">Attach the compressed PST file to an email message and send it to the user, who can then decompress the file just by clicking it.</span></span>
    
- <span data-ttu-id="6e246-255">將 PST 檔案複製到使用者可以存取及取得的共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e246-255">Copy the PST file to a shared folder that the user can access and retrieve it.</span></span>
    
<span data-ttu-id="6e246-256">下一節中的步驟是由使用者執行, 以將刪除的專案還原至其信箱。</span><span class="sxs-lookup"><span data-stu-id="6e246-256">The steps in the next section are performed by the user to restore the deleted items to their mailbox.</span></span>
  
 <a name="restoredeleteditems"></a>
<span data-ttu-id="6e246-257">**使用 PST 檔案將刪除的郵件還原至信箱**</span><span class="sxs-lookup"><span data-stu-id="6e246-257">**Restore deleted items to a mailbox using a PST file**</span></span>
  
<span data-ttu-id="6e246-258">您必須使用 Outlook 桌面應用程式, 以使用 PST 檔案還原已刪除的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-258">You have to use the Outlook desktop app to restore a deleted item by using a PST file.</span></span> <span data-ttu-id="6e246-259">您不能在網頁上使用 Outlook Web App 或 Outlook 來開啟 PST 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e246-259">You can't use Outlook Web App or Outlook on the web to open a PST file.</span></span>
  
1. <span data-ttu-id="6e246-260">在 Outlook 2013 或 Outlook 2016 中, 按一下\*\*\*\* [檔案] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6e246-260">In Outlook 2013 or Outlook 2016, click the **File** tab.</span></span> 
    
2. <span data-ttu-id="6e246-261">按一下 **[ &amp;開啟匯出**], 然後按一下 [**開啟 Outlook 資料檔案**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-261">Click **Open &amp; Export**, and then click **Open Outlook Data File**.</span></span>
    
3. <span data-ttu-id="6e246-262">流覽至您儲存系統管理員傳送的 PST 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="6e246-262">Browse to the location where you saved the PST file that your administrator sent.</span></span>
    
4. <span data-ttu-id="6e246-263">選取 PST, 然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-263">Select the PST and then click **Open**.</span></span>
    
    <span data-ttu-id="6e246-264">PST 檔案會出現在 Outlook 的左巡覽列中。</span><span class="sxs-lookup"><span data-stu-id="6e246-264">The PST file appears in the left-nav bar in Outlook.</span></span>
    
    ![PST 檔案會出現在 Outlook 的左導覽列中](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. <span data-ttu-id="6e246-266">按一下箭頭以展開 PST 檔案及其下的資料夾, 以找出您想要復原的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-266">Click the arrows to expand the PST file and the folders under it to locate the item you want to recover.</span></span>
    
    ![在 [清除] 資料夾中, 尋找您要復原的專案](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > <span data-ttu-id="6e246-268">在 [清除] 資料夾中, 尋找您要復原的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-268">Look in the Purges folder for the item you want to recover.</span></span> <span data-ttu-id="6e246-269">這是已清除專案移至的隱藏資料夾。</span><span class="sxs-lookup"><span data-stu-id="6e246-269">This is a hidden folder that purged items are moved to.</span></span> <span data-ttu-id="6e246-270">您的系統管理員可能會在此資料夾中復原您的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-270">It's likely the item that your administrator recovered is in this folder.</span></span> 
  
6. <span data-ttu-id="6e246-271">以滑鼠右鍵按一下您要復原的專案, 然後按一下 [**移動** \> **其他資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-271">Right-click the item you want to recover and then click **Move** \> **Other Folder**.</span></span>
    
    ![按一下 [移動], 然後選取 [其他資料夾]](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. <span data-ttu-id="6e246-273">若要將專案移到收件匣, 請按一下 [**收件**匣], 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-273">To move the item to your inbox, click **Inbox**, and then click **OK**.</span></span>
    
    <span data-ttu-id="6e246-274">**秘訣:** 若要復原其他類型的專案, 請執行下列其中一項操作:</span><span class="sxs-lookup"><span data-stu-id="6e246-274">**Tip:** To recover other types of items, do one of the following:</span></span> 
    
  - <span data-ttu-id="6e246-275">若要復原行事曆專案, 請以滑鼠右鍵按一下它, 然後按一下 [**移動** \> **其他資料夾** \>行事**曆**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-275">To recover a calendar item, right-click it, and then click **Move** \> **Other Folder** \> **Calendar**.</span></span>
    
  - <span data-ttu-id="6e246-276">若要復原連絡人, 請以滑鼠右鍵按一下該連絡人, 然後按一下 [**移動** \> **其他資料夾** \> **連絡人**]。</span><span class="sxs-lookup"><span data-stu-id="6e246-276">To recover a contact, right-click it, and then click **Move** \> **Other Folder** \> **Contacts**.</span></span>
    
  - <span data-ttu-id="6e246-277">若要復原任務, 請以滑鼠右鍵按一下它, 然後按一下 [**移動** \> **其他資料夾** \> \*\*\*\* 工作]。</span><span class="sxs-lookup"><span data-stu-id="6e246-277">To recover a task, right-click it, and then click **Move** \> **Other Folder** \> **Tasks**.</span></span>
    
![選取資料夾以移動其他類型的專案](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. <span data-ttu-id="6e246-279">當您已完成復原刪除的專案時, 請以滑鼠右鍵按一下左導覽列中的 PST 檔案, 然後選取 **[關閉] [pst 檔案名稱]**。</span><span class="sxs-lookup"><span data-stu-id="6e246-279">When you're finished recovering deleted items, right-click the PST file in the left-nav bar and select **Close "name of PST file"**.</span></span>
    
[<span data-ttu-id="6e246-280">回到頁首</span><span class="sxs-lookup"><span data-stu-id="6e246-280">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a><span data-ttu-id="6e246-281">其他資訊</span><span class="sxs-lookup"><span data-stu-id="6e246-281">More information</span></span>
<span data-ttu-id="6e246-282"><a name="moreinfo"> </a></span><span class="sxs-lookup"><span data-stu-id="6e246-282"></span></span>

- <span data-ttu-id="6e246-283">如果專案的已刪除專案保留期間尚未過期, 則使用者可能會復原永久刪除的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-283">It might be possible for a user to recover a permanently deleted item if the deleted item retention period for the item hasn't expired.</span></span> <span data-ttu-id="6e246-284">以系統管理員身分, 您可能會指定 [可復原的專案] 資料夾中的專案可用於復原的時間。</span><span class="sxs-lookup"><span data-stu-id="6e246-284">As an admin you may have specified how long items in the Recoverable Items folder are available for recovery.</span></span> <span data-ttu-id="6e246-285">例如, 可能會有一項原則可刪除在使用者的 [刪除的郵件] 資料夾中有30天的任何專案, 以及可讓使用者將 [可復原的專案] 資料夾中的專案復原至其他14天的其他原則。</span><span class="sxs-lookup"><span data-stu-id="6e246-285">For example, there might be a policy that deletes anything that's been in a user's Deleted Items folder for 30 days, and another policy that lets users recover items in the Recoverable Items folder for up to another 14 days.</span></span> <span data-ttu-id="6e246-286">不過, 在這14天之後, 您可以使用本主題中的程式, 復原使用者信箱中的專案。</span><span class="sxs-lookup"><span data-stu-id="6e246-286">However, after this 14 days, you may still be able to recover an item in a user's mailbox by using the procedures in this topic.</span></span>
    
- <span data-ttu-id="6e246-287">使用者可以復原已刪除的專案 (如果尚未清除), 以及該專案的已刪除專案保留期間尚未過期。</span><span class="sxs-lookup"><span data-stu-id="6e246-287">Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired.</span></span> <span data-ttu-id="6e246-288">若要協助使用者復原其信箱中已刪除的郵件, 請指向下列其中一個主題:</span><span class="sxs-lookup"><span data-stu-id="6e246-288">To help users recover deleted items in their mailbox, point them to one of the following topics:</span></span>
    
  - [<span data-ttu-id="6e246-289">在 Windows 版 Outlook 復原已刪除的項目</span><span class="sxs-lookup"><span data-stu-id="6e246-289">Recover deleted items in Outlook for Windows</span></span>](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [<span data-ttu-id="6e246-290">復原 Outlook 2010 中已刪除的專案</span><span class="sxs-lookup"><span data-stu-id="6e246-290">Recover deleted items in Outlook 2010</span></span>](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [<span data-ttu-id="6e246-291">復原 Outlook Web App 中刪除的郵件或電子郵件</span><span class="sxs-lookup"><span data-stu-id="6e246-291">Recover deleted items or email in Outlook Web App</span></span>](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [<span data-ttu-id="6e246-292">在網頁版 Outlook 中還原已刪除的電子郵件</span><span class="sxs-lookup"><span data-stu-id="6e246-292">Restore deleted email messages in Outlook on the web</span></span>](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [<span data-ttu-id="6e246-293">在 Outlook 中復原刪除的連絡人</span><span class="sxs-lookup"><span data-stu-id="6e246-293">Recover a deleted contact in Outlook</span></span>](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [<span data-ttu-id="6e246-294">還原 Outlook.com 中已刪除的電子郵件</span><span class="sxs-lookup"><span data-stu-id="6e246-294">Restore deleted email messages in Outlook.com</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[<span data-ttu-id="6e246-295">返回頁首</span><span class="sxs-lookup"><span data-stu-id="6e246-295">Return to top</span></span>](recover-deleted-items-in-a-mailbox.md#__top)
  

