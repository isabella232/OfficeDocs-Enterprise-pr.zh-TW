---
title: "Office 365 和 Dynamics 365 開發人員/測試環境的 Exchange Online 整合"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- mar17entnews
- Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "摘要： 使用此測試實驗室指南啟用 Exchange Online 的 Office 365 試用版訂閱中的 Dynamics 365 整合。"
ms.openlocfilehash: 9cecd13f0ffc3c2822ac6c66a3bde9c9e6a3c798
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="c192f-103">Office 365 和 Dynamics 365 開發人員/測試環境的 Exchange Online 整合</span><span class="sxs-lookup"><span data-stu-id="c192f-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="c192f-104">**摘要：**使用此測試實驗室指南，讓您的 Office 365 試用版訂閱中的 Dynamics 365 整合的 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c192f-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="c192f-p101">Microsoft Dynamics 365 價值使用，以儲存集中一處的所有客戶通訊，因此具備適當權限的任何人都可以看到所有相關的客戶記錄。例如，檢視與特定連絡人、 帳戶、 商機、 或案例相關聯的所有電子郵件。</span><span class="sxs-lookup"><span data-stu-id="c192f-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="c192f-p102">若要儲存電子郵件及其他訊息記錄 Dynamics 365，您需要與 Dynamics 365 同步處理您的電子郵件系統。伺服器端同步處理是一種選擇電子郵件同步處理的方法。</span><span class="sxs-lookup"><span data-stu-id="c192f-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="c192f-109">使用此測試實驗室指南設定與示範 Exchange Online 與 Outlook Online 用戶端可以運用 Dynamics 365 中儲存的資訊。</span><span class="sxs-lookup"><span data-stu-id="c192f-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="c192f-110">階段 1： 建立 Office 365 和 Dynamics 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="c192f-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="c192f-111">使用[Office 365 和 Dynamics 365 開發人員/測試環境](office-365-and-dynamics-365-dev-test-environment.md)中的指示來建立 Office 365 和 Dynamics 365 開發人員/測試環境的任一輕量型或模擬的企業版。</span><span class="sxs-lookup"><span data-stu-id="c192f-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c192f-p103">本文中的設定不需要模擬的 enterprise 開發人員/測試環境中，其中包含連線至網際網路模擬內部網路和 Windows Server Active Directory (AD) 樹系目錄同步處理。它會提供這裡是做為選項，讓您可以代表的典型組織的環境中與 Office 365 和 Dynamics 365 試驗</span><span class="sxs-lookup"><span data-stu-id="c192f-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="c192f-114">階段 2： 設定與示範 Dynamics 365 整合在 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c192f-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="c192f-115">使用下列步驟來設定 Dynamics 365 和 Exchange Online 的整合全域系統管理員的信箱：</span><span class="sxs-lookup"><span data-stu-id="c192f-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="c192f-116">使用的私用的工作階段的瀏覽器，前往[http://portal.office.com](http://portal.office.com)並使用您的 Office 365 全域管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c192f-116">Using a private session of your browser, go to [http://portal.office.com](http://portal.office.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="c192f-117">按一下 [ **Microsoft Office Home** ] 索引標籤的 [**郵件**並排顯示]。</span><span class="sxs-lookup"><span data-stu-id="c192f-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="c192f-118">在 [新**郵件**] 索引標籤在瀏覽器中按一下 [**新增**]，請注意的輸入訊息方塊下方窗格下方角落的 「 我的範本所包含的圖示。</span><span class="sxs-lookup"><span data-stu-id="c192f-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![不與 Dynamics 365 整合的全新空白電子郵件訊息。](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="c192f-120">按一下 [**放棄**，[**郵件**] 索引標籤保持在開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="c192f-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="c192f-121">[在瀏覽器中的 [ **Microsoft Office Home** ] 索引標籤和 [**系統管理**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="c192f-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="c192f-122">在 [ **Office 系統管理中心**] 索引標籤的左方導覽，按一下 [**系統中心 > Dynamics 365**。</span><span class="sxs-lookup"><span data-stu-id="c192f-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="c192f-123">在瀏覽器上 Dynamics 365 執行個體的清單中新增的**Dynamics 365** ] 索引標籤上按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="c192f-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="c192f-124">新的 [**管理**] 索引標籤中瀏覽器中的導覽列上，按一下 [**設定**] 旁的向下箭頭和 [**電子郵件設定下**系統**。**</span><span class="sxs-lookup"><span data-stu-id="c192f-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="c192f-125">在 [**電子郵件設定**] 頁面上按一下 [**電子郵件設定**]。</span><span class="sxs-lookup"><span data-stu-id="c192f-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="c192f-126">在 [**電子郵件**] 索引標籤上 [**系統設定**] 對話方塊中**伺服器端同步處理**，以變更**約會、 連絡人及工作**並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="c192f-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="c192f-127">按一下 [**電子郵件設定**] 頁面的 [**信箱**]。</span><span class="sxs-lookup"><span data-stu-id="c192f-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="c192f-128">選取左邊的核取記號表示] 欄中的 Office 365 全域管理員名稱、 按一下 [工具] 列中的 [**套用預設的電子郵件設定**，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="c192f-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="c192f-129">按一下 [工具] 列中的 [**核准電子郵件**並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="c192f-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="c192f-130">選取 [Office 365 全域管理員名稱左側的核取記號表示] 欄中，按一下 [**測試&amp;啟用信箱**工具中長條，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="c192f-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="c192f-131">按一下 [開啟**郵件**] 索引標籤並確認 [全域管理員接收測試郵件。</span><span class="sxs-lookup"><span data-stu-id="c192f-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="c192f-p104">在瀏覽器中的 [**我作用中信箱的信箱**] 索引標籤會傳回與重新整理頁面。**內送電子郵件狀態**] 和 [**外寄電子郵件狀態**欄應設為**成功**的全域管理員帳戶名稱。請注意其可能需要 15 分鐘的時間才能完成這兩個測試。</span><span class="sxs-lookup"><span data-stu-id="c192f-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="c192f-135">使用下列步驟安裝 Dynamics 365 Outlook 的應用程式及示範 Dynamics 365 全域管理員的信箱內的功能：</span><span class="sxs-lookup"><span data-stu-id="c192f-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="c192f-136">在瀏覽器中的 [**我作用中信箱的信箱**] 索引標籤上按一下 [**設定**] 旁的向下箭頭和 [ **Dynamics 365 Outlook 的應用程式**下**系統**。</span><span class="sxs-lookup"><span data-stu-id="c192f-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="c192f-p105">在**開始使用 Outlook 的 Microsoft Dynamics 365 應用程式**] 頁面上按一下 [全域管理員名稱] 中，和 [**新增至 Outlook 的應用程式**。[**狀態**] 欄變更為**擱置**。</span><span class="sxs-lookup"><span data-stu-id="c192f-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="c192f-p106">直到狀態變更為 [**已新增至 Outlook**重新整理頁面。請注意其可能需要 15 分鐘的時間才能完成此設定。</span><span class="sxs-lookup"><span data-stu-id="c192f-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="c192f-141">按一下 [在瀏覽器中的 [**郵件**] 索引標籤，然後關閉它。</span><span class="sxs-lookup"><span data-stu-id="c192f-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="c192f-142">[在瀏覽器中的 [ **Microsoft Office Home** ] 索引標籤和 [**郵件**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="c192f-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="c192f-p107">在 [新**郵件**] 索引標籤在瀏覽器中按一下 [**新增]**。注意到的現在輸入訊息方塊下方窗格下方角落的 Dynamics 365 包含圖示。</span><span class="sxs-lookup"><span data-stu-id="c192f-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![與 Dynamics 365 整合的全新空白電子郵件訊息，顯示新的圖示。](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="c192f-p108">按一下 [Dynamics 365 圖示。您應該會看到 [ **Dynamics 365** ] 窗格中，您可以從中追蹤此電子郵件或 access 範本、 銷售文獻或文章。</span><span class="sxs-lookup"><span data-stu-id="c192f-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="c192f-p109">**以**欄位中的電子郵件訊息，輸入**alex.y.wu@outlook.com**，和 [**重試** **Dynamics 365**窗格中。您應該會看到的資訊**Dynamics 365**窗格中**的收件者**] 區段上 Alex Wu、 銷售應用程式的範例資料提供給您的試用版訂閱的連絡人。</span><span class="sxs-lookup"><span data-stu-id="c192f-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![儲存於 Dynamics 365 中銷售連絡人的 Dynamics 365 資訊窗格。](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="c192f-151">按一下 [**放棄**。</span><span class="sxs-lookup"><span data-stu-id="c192f-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="c192f-152">按一下[這裡](http://aka.ms/catlgstack)一個 Microsoft Cloud 測試實驗室指南堆疊中的文章的所有視覺地圖。</span><span class="sxs-lookup"><span data-stu-id="c192f-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="c192f-153">See Also</span><span class="sxs-lookup"><span data-stu-id="c192f-153">See Also</span></span>

[<span data-ttu-id="c192f-154">Office 365 和 Dynamics 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="c192f-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="c192f-155">雲端採用測試實驗室指南 (Tlg)</span><span class="sxs-lookup"><span data-stu-id="c192f-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c192f-156">基本組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="c192f-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="c192f-157">Office 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="c192f-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c192f-158">Office 365 開發人員/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="c192f-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="c192f-159">訂閱管理 Dynamics 365 （線上）</span><span class="sxs-lookup"><span data-stu-id="c192f-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="c192f-160">管理 Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c192f-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


