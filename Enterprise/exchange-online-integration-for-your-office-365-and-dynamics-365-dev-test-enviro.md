---
title: 適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: 摘要：使用此測試實驗室指南，在 Office 365 試用版訂閱中啟用適用於 Exchange Online 的 Dynamics 365 整合。
ms.openlocfilehash: be79f58f448799bba9c4a9ee51350f198d721e0d
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574017"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="03503-103">適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合</span><span class="sxs-lookup"><span data-stu-id="03503-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="03503-104">**摘要：** 使用此測試實驗室指南，在 Office 365 試用版訂閱中啟用適用於 Exchange Online 的 Dynamics 365 整合。</span><span class="sxs-lookup"><span data-stu-id="03503-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="03503-p101">Microsoft Dynamics 365 的重要用途是將所有的客戶通訊儲存在同一個位置，以便有適當的權限任何人都可以查看所有的相關客戶記錄。例如，檢視與特定連絡人、帳戶、機會或案例相關聯的所有電子郵件。</span><span class="sxs-lookup"><span data-stu-id="03503-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="03503-p102">若要在 Dynamics 365 中儲存電子郵件和其他訊息記錄，您必須將電子郵件系統與 Dynamics 365 進行同步。伺服器端同步處理就是電子郵件同步處理的選擇方法。</span><span class="sxs-lookup"><span data-stu-id="03503-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="03503-109">使用這項測試實驗室指南來設定及說明 Exchange Online 和 Outlook Online 用戶端可以如何利用 Dynamics 365 中儲存的資訊。</span><span class="sxs-lookup"><span data-stu-id="03503-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="03503-110">階段 1：建置 Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="03503-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="03503-111">請使用 [Office 365 和 Dynamics 365 開發/測試環境](office-365-and-dynamics-365-dev-test-environment.md)中的指示，建立 Office 365 和 Dynamics 365 開發/測試環境的輕量型或模擬企業版本。</span><span class="sxs-lookup"><span data-stu-id="03503-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="03503-p103">這篇文章中的組態不需要模擬的企業開發/測試環境，其中包括模擬的內部網路 (連線到網際網路) 和 Windows Server Active Directory (AD) 樹系中的目錄同步處理。它在這裡提供作為選項，讓您可以在代表典型組織的環境中試驗 Office 365 和 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="03503-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="03503-114">階段 2：在 Exchange Online 中設定及示範 Dynamics 365 整合</span><span class="sxs-lookup"><span data-stu-id="03503-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="03503-115">若要設定全域系統管理員的信箱將 Dynamics 365 與 Exchange Online 整合，請使用這些步驟：</span><span class="sxs-lookup"><span data-stu-id="03503-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="03503-116">使用瀏覽器的私人工作階段移至[http://admin.microsoft.com](http://admin.microsoft.com)並使用您的 Office 365 全域系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="03503-116">Using a private session of your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="03503-117">在 [Microsoft Office Home]\*\*\*\* 頁面上，按一下 [郵件]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="03503-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="03503-118">在 [新**郵件**] 索引標籤瀏覽器中，按一下 [**新增**]，請注意的方塊中輸入訊息] 下的窗格的右下角的 「 我的範本所具有的圖示。</span><span class="sxs-lookup"><span data-stu-id="03503-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message has an icon for My Templates.</span></span>
    
     ![不與 Dynamics 365 整合的全新空白電子郵件訊息。](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="03503-120">按一下 [捨棄]\*\*\*\*，並將 [郵件]\*\*\*\* 索引標籤保持開啟。</span><span class="sxs-lookup"><span data-stu-id="03503-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="03503-121">按一下瀏覽器中的 [Microsoft Office Home]\*\*\*\* 索引標籤，然後按一下 [系統管理員]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="03503-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="03503-122">在 [Office 系統管理中心]\*\*\*\* 索引標籤的左側導覽窗格中，按一下 [系統管理中心 > Dynamics 365]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="03503-123">在瀏覽器中新 [Dynamics 365]\*\*\*\* 索引標籤的 Dynamics 365 執行個體清單中，按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="03503-124">在瀏覽器中新 [管理]\*\*\*\* 索引標籤的瀏覽列上，按一下 [設定]\*\*\*\* 旁的向下箭號，然後按一下 [系統]\*\*\*\* 下的 [電子郵件設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="03503-125">在 [電子郵件設定]\*\*\*\* 頁面上，按一下 [電子郵件設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="03503-126">在 [系統設定]\*\*\*\* 對話方塊的 [電子郵件]\*\*\*\* 索引標籤上，將 [約會、連絡人及工作]\*\*\*\* 變更為 [伺服器端同步處理]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="03503-127">在 [電子郵件設定]\*\*\*\* 頁面上，按一下 [信箱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="03503-128">選取左側核取記號欄中的 Office 365 全域系統管理員名稱，按一下工具列中的 [套用預設的電子郵件設定]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="03503-129">在工具列中按一下 [核准電子郵件]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="03503-130">選取左側核取記號欄中的 Office 365 全域系統管理員名稱，按一下工具列中的 [測試及啟用信箱]**&amp;**，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="03503-131">按一下 [開啟郵件]\*\*\*\* 索引標籤，並確認全域管理員接收到測試訊息。</span><span class="sxs-lookup"><span data-stu-id="03503-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="03503-p104">在瀏覽器中返回 [信箱 > 我的作用中信箱]\*\*\*\* 索引標籤，然後重新整理頁面。全域系統管理員帳戶名稱的 [內送電子郵件狀態]\*\*\*\* 與 [外寄電子郵件狀態]\*\*\*\* 欄應設定為 [成功]\*\*\*\* 。請注意，需花費 15 分鐘的時間才能完成這兩個測試。</span><span class="sxs-lookup"><span data-stu-id="03503-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="03503-135">使用下列步驟，在全域系統管理員的信箱中安裝 Dynamics 365 App for Outlook，並示範 Dynamics 365 的功能：</span><span class="sxs-lookup"><span data-stu-id="03503-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="03503-136">在瀏覽器的 [信箱 > 我的作用中信箱]\*\*\*\* 索引標籤上，按一下 [設定]\*\*\*\* 旁的向下箭號，然後按一下 [系統]\*\*\*\* 下的 [Dynamics 365 App for Outlook]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="03503-p105">在 [開始使用 Microsoft Dynamics 365 App for Outlook]\*\*\*\* 頁面中，按一下全域系統管理員名稱，然後按一下 [將應用程式新增至 Outlook]\*\*\*\*。[狀態]\*\*\*\* 欄會變更為 [擱置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="03503-p106">重新整理頁面，直到狀態變更為 [已新增至 Outlook]\*\*\*\* 為止。請注意，需花費 15 分鐘的時間才能完成這項設定。</span><span class="sxs-lookup"><span data-stu-id="03503-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="03503-141">按一下瀏覽器中的 [郵件]\*\*\*\* 索引標籤，然後將其關閉。</span><span class="sxs-lookup"><span data-stu-id="03503-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="03503-142">按一下瀏覽器中的 [Microsoft Office Home]\*\*\*\* 索引標籤，然後按一下 [郵件]\*\*\*\* 磚。</span><span class="sxs-lookup"><span data-stu-id="03503-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="03503-143">在新**郵件**] 索引標籤瀏覽器中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="03503-143">On the new **Mail** tab in your browser, click **New**.</span></span> <span data-ttu-id="03503-144">請注意現在輸入一個訊息方塊下方窗格的右下角的 Dynamics 365 有圖示。</span><span class="sxs-lookup"><span data-stu-id="03503-144">Notice that the bottom corner of the pane below the box for typing a message now has an icon for Dynamics 365.</span></span>
    
     ![與 Dynamics 365 整合的全新空白電子郵件訊息，顯示新的圖示。](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="03503-p108">按一下 [Dynamics 365] 圖示。您應該會看到 [Dynamics 365]\*\*\*\* 窗格，可從這裡追蹤此電子郵件或存取範本、銷售資料或文章。</span><span class="sxs-lookup"><span data-stu-id="03503-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="03503-p109">在電子郵件訊息的 [收件者]\*\*\*\* 欄位中，輸入 **alex.y.wu@outlook.com**，然後按一下 [Dynamics 365]\*\*\*\* 窗格中的 [重試]\*\*\*\*。您應該會在 [Dynamics 365]\*\*\*\* 窗格中看到包含 Alex Wu 相關資訊的 [收件者]\*\*\*\* 區段，這是銷售應用程式中的連絡人，隨試用版訂閱的範例資料所提供。</span><span class="sxs-lookup"><span data-stu-id="03503-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![儲存於 Dynamics 365 中銷售連絡人的 Dynamics 365 資訊窗格。](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="03503-151">按一下 [捨棄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03503-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="03503-152">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="03503-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="03503-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="03503-153">See Also</span></span>

[<span data-ttu-id="03503-154">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="03503-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="03503-155">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="03503-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="03503-156">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="03503-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="03503-157">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="03503-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="03503-158">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="03503-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="03503-159">Dynamics 365 訂閱管理 (線上)</span><span class="sxs-lookup"><span data-stu-id="03503-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="03503-160">管理 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="03503-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


