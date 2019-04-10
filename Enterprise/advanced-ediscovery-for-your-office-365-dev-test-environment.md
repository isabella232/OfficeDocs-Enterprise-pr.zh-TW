---
title: 適用於 Office 365 開發/測試環境的進階電子文件探索
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 摘要： 設定並示範 Office 365 進階 eDiscovery 與 Office 365 開發/測試環境中的範例資料。
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741450"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="8611d-103">適用於 Office 365 開發/測試環境的進階電子文件探索</span><span class="sxs-lookup"><span data-stu-id="8611d-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="8611d-104">**摘要：** 設定並示範 Office 365 進階 eDiscovery 與 Office 365 開發/測試環境中的範例資料。</span><span class="sxs-lookup"><span data-stu-id="8611d-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="8611d-105">Office 365 進階電子文件可讓您快速地尋找和分析跨 Office 365，包括電子郵件和文件中儲存資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8611d-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="8611d-106">這可以儲存龐大的時間量和費用，特別是在訴訟資料暫留情況。</span><span class="sxs-lookup"><span data-stu-id="8611d-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="8611d-107">如需詳細資訊，請參閱 [Office 365 進階電子搜索](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。</span><span class="sxs-lookup"><span data-stu-id="8611d-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="8611d-108">透過本文中的指示，您可以建立一小群的虛構合約爭議資料及分析使用進階電子文件。</span><span class="sxs-lookup"><span data-stu-id="8611d-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="8611d-109">按一下[這裡](http://aka.ms/catlgstack)取得 Office 365 測試實驗室指南堆疊中所有文章的視覺對應。</span><span class="sxs-lookup"><span data-stu-id="8611d-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="8611d-110">階段 1：建立 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8611d-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="8611d-111">如果您只想以具有最小需求的輕量型方式測試進階電子文件，請依照下列階段 2 和階段 3 中的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="8611d-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="8611d-112">如果您想要在模擬的企業中測試進階電子文件，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="8611d-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="8611d-113">測試進階電子文件不需要模擬的企業環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理的 Active Directory 網域服務 (AD DS) 樹系。</span><span class="sxs-lookup"><span data-stu-id="8611d-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="8611d-114">它提供了此選項，讓您可以代表典型組織環境中執行測試與試驗。</span><span class="sxs-lookup"><span data-stu-id="8611d-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="8611d-115">階段 2： 建立進階電子文件探索的範例資料</span><span class="sxs-lookup"><span data-stu-id="8611d-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="8611d-116">在此程序，您會建立電子郵件在進階電子文件探索案例中分析稍後將您的郵件。</span><span class="sxs-lookup"><span data-stu-id="8611d-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="8611d-117">開啟 Internet Explorer 並登入在[https://outlook.com](https://outlook.com)您在[Office 365 開發/測試](office-365-dev-test-environment.md)環境的階段 2 中建立的 Outlook 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8611d-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="8611d-118">如果您使用輕量型開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從您本機電腦登入。</span><span class="sxs-lookup"><span data-stu-id="8611d-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="8611d-119">如果您使用模擬的企業版開發/測試環境，使用 Azure 入口網站 ([https://portal.azure.com](https://portal.azure.com)) 來連接到 CLIENT1 虛擬機器，然後從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="8611d-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="8611d-120">在 [ **Outlook 郵件**] 索引標籤上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="8611d-121">在 [**至**] 輸入您試用版訂閱中 User6 帳戶的電子郵件地址 ( \*\* user6@。\*\*</span><span class="sxs-lookup"><span data-stu-id="8611d-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**</span></span><organization name> <span data-ttu-id="8611d-122">**。 onmicrosoft.com**)。</span><span class="sxs-lookup"><span data-stu-id="8611d-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="8611d-123">主旨請輸入**測試電子郵件 1**。</span><span class="sxs-lookup"><span data-stu-id="8611d-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="8611d-124">在本文中，輸入**Tailspin 合約草稿**]，然後按一下 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="8611d-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="8611d-125">在 [ **Outlook 郵件**] 索引標籤上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="8611d-126">在 [**至**] 輸入您試用版訂閱中 User6 帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8611d-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="8611d-127">主旨請輸入**測試電子郵件 2**。</span><span class="sxs-lookup"><span data-stu-id="8611d-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="8611d-128">在本文中，輸入**Tailspin 啟動會議**，，然後按一下 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="8611d-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="8611d-129">在 [ **Outlook 郵件**] 索引標籤上按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="8611d-130">在 [**至**] 輸入您試用版訂閱中 User6 帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8611d-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="8611d-131">主旨請輸入**測試電子郵件 3**。</span><span class="sxs-lookup"><span data-stu-id="8611d-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="8611d-132">在本文中，輸入**Tailspin 合約爭議**，，然後按一下 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="8611d-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="8611d-133">按一下右上角的使用者圖示，然後按一下 [**登出]**。</span><span class="sxs-lookup"><span data-stu-id="8611d-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="8611d-134">開啟新的索引標籤，然後登入 Office 365 入口網站 ([https://www.office.com](https://www.office.com)) 帳戶名稱與試用版訂閱中 User6 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="8611d-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="8611d-135">**Office 365 入口網站**索引標籤上，按一下 [**郵件**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="8611d-136">在 [**郵件-User6-Outlook** ] 索引標籤上，檢查 User6 收到所有三封電子郵件從 Outlook 電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="8611d-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="8611d-137">User6 切換到**Office 365 入口網站索引標籤**。</span><span class="sxs-lookup"><span data-stu-id="8611d-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="8611d-138">按一下右上角的使用者圖示，然後按一下**登出。**</span><span class="sxs-lookup"><span data-stu-id="8611d-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="8611d-139">在此程序，您建立兩個 Word 文件的就是您稍後會分析進階電子文件探索案例中。</span><span class="sxs-lookup"><span data-stu-id="8611d-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="8611d-140">在 [ **Office** ] 頁面上，按一下 [**登入，** 登入您的全域系統管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="8611d-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="8611d-141">新索引標籤上，存取生產 SharePoint 網站的 URL: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="8611d-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="8611d-142">在**實際執行網站集合**] 索引標籤上，[**文件**，按一下 [**新 > Word 文件**。</span><span class="sxs-lookup"><span data-stu-id="8611d-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="8611d-143">在**Word Online** ] 頁面上，輸入**Tailspin 草稿合約**，等到標題中顯示**已儲存**，然後關閉**Word Online 中**的 [頁面] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8611d-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="8611d-144">在**實際執行網站集合**] 索引標籤上，[**文件**，按一下 [**新 > Word 文件**。</span><span class="sxs-lookup"><span data-stu-id="8611d-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="8611d-145">在**Word Online** ] 索引標籤中，輸入**Tailspin 合約爭議附註**，等到標題中顯示**已儲存**，然後關閉 [ **Word Online** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8611d-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="8611d-146">在**實際執行網站集合**] 索引標籤中，您應該會看到**文件**和**文件 1**的文件清單中。</span><span class="sxs-lookup"><span data-stu-id="8611d-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="8611d-147">關閉 [**生產環境網站集合**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8611d-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="8611d-148">階段 3： 針對法律爭議使用進階的 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="8611d-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="8611d-149">不幸的是，您的組織和 Tailspin Toys 之間的合約爭議已達到法律巨集指令的點。</span><span class="sxs-lookup"><span data-stu-id="8611d-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="8611d-150">在此程序，您可以建立及設定進階的 eDiscovery 案例來搜尋並分析電子郵件和文件包含文字 「 Tailspin 合約 」。</span><span class="sxs-lookup"><span data-stu-id="8611d-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="8611d-151">使用進階電子文件的程序如下：</span><span class="sxs-lookup"><span data-stu-id="8611d-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="8611d-152">建立 「 搜尋 」 安全性&amp;合規性中心，分析其結果，然後準備用於進階電子文件探索的結果。</span><span class="sxs-lookup"><span data-stu-id="8611d-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="8611d-153">建立和設定進階電子文件中的案例，分析搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="8611d-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="8611d-154">在此程序，您可以建立安全性搜尋&amp;合規性管理中心的 「 Tailspin 合約 」，查看在結果中，然後準備用於進階電子文件探索的結果。</span><span class="sxs-lookup"><span data-stu-id="8611d-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="8611d-155">從**Office 365 入口網站**] 索引標籤上，按一下 [**系統**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="8611d-156">在 [系統管理中心] 索引標籤的左方導覽，按一下 [**系統管理中心 > 合規性**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="8611d-157">在**安全性&amp;規範**索引標籤上，按一下 [**權限**。</span><span class="sxs-lookup"><span data-stu-id="8611d-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="8611d-158">在 [**權限**] 清單中，按兩下 [**組織管理**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="8611d-159">在 [**角色群組**] 視窗中，[**成員**] 下方按一下加號。</span><span class="sxs-lookup"><span data-stu-id="8611d-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="8611d-160">在 [**選取成員**] 視窗中，按兩下 [系統管理員帳戶的名稱，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="8611d-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="8611d-161">在 [**角色群組**] 視窗中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="8611d-162">在 [**權限**] 清單中，按兩下 [ **eDiscovery 管理員**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="8611d-163">在**角色群組**] 視窗中，[ **eDiscovery 系統管理員**]，按一下 [加號] 圖示。</span><span class="sxs-lookup"><span data-stu-id="8611d-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="8611d-164">在 [**選取成員**] 視窗中，按兩下 [系統管理員帳戶的名稱，然後按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="8611d-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="8611d-165">在 [**角色群組**] 視窗中，按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="8611d-166">在左側導覽中，按一下 [**搜尋&amp;調查 > 內容搜尋**。</span><span class="sxs-lookup"><span data-stu-id="8611d-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="8611d-167">按一下加號圖示以新增搜尋。</span><span class="sxs-lookup"><span data-stu-id="8611d-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="8611d-168">在 [**新搜尋**] 視窗中，輸入**Tailspin 合約搜尋**的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="8611d-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="8611d-169">在 [**您希望在哪裡我們在哪裡？**，按一下 [**搜尋各處，** 選取 [ **Exchange**、 **SharePoint**和**公用資料夾**]，然後按一下**下一步。**</span><span class="sxs-lookup"><span data-stu-id="8611d-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="8611d-170">在 [**什麼您希望我們要尋找的？**，輸入**Tailspin 合約**，然後按一下 [**搜尋**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="8611d-171">在 [搜尋] 清單中按一下 [ **Tailspin 合約搜尋**名稱。</span><span class="sxs-lookup"><span data-stu-id="8611d-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="8611d-172">在 [ **Tailspin 合約搜尋**] 窗格中，按一下 [**預覽搜尋結果\*\*\*\*的結果**下。</span><span class="sxs-lookup"><span data-stu-id="8611d-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="8611d-173">您應該會看到列出在實際執行 SharePoint 網站 （**文件**和**文件 1**）] 和 [User6**測試電子郵件 1**和**測試電子郵件 3**電子郵件的兩個文件視窗。</span><span class="sxs-lookup"><span data-stu-id="8611d-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="8611d-174">關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="8611d-174">Close the window.</span></span>
    
19. <span data-ttu-id="8611d-175">在 [**內容搜尋**] 窗格中，[**進階電子文件探索分析結果**，請按一下 [**預覽結果進行分析**。</span><span class="sxs-lookup"><span data-stu-id="8611d-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="8611d-176">在 [**準備搜尋結果 Tailspin 合約搜尋**] 視窗中，按一下 [**準備**並等待其完成。</span><span class="sxs-lookup"><span data-stu-id="8611d-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="8611d-177">在此程序，您可以建立進階電子文件的新案件並分析 Tailspin 合約搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="8611d-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="8611d-178">在左導覽中，按一下 [ **eDiscovery**下**搜尋&amp;調查**。</span><span class="sxs-lookup"><span data-stu-id="8611d-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="8611d-179">在 [ **eDiscovery** ] 窗格中，按一下 [**移至進階電子文件**。</span><span class="sxs-lookup"><span data-stu-id="8611d-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="8611d-180">在 [**進階電子文件探索**] 索引標籤中，按一下加號圖示以新增案例。</span><span class="sxs-lookup"><span data-stu-id="8611d-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="8611d-181">在**新增案例**] 窗格中，在 [**名稱**] 中，輸入**Tailspin 合約爭議**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8611d-181">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**.</span></span> <span data-ttu-id="8611d-182">等待要建立的案例。</span><span class="sxs-lookup"><span data-stu-id="8611d-182">Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="8611d-183">連按兩下清單中的**Tailspin 合約爭議**案例。</span><span class="sxs-lookup"><span data-stu-id="8611d-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="8611d-184">在 [**容器**] 清單中，按一下 [ **Tailspin 合約搜尋**] 容器中，，，然後按一下 [**程序**。</span><span class="sxs-lookup"><span data-stu-id="8611d-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="8611d-185">等待完成處理。</span><span class="sxs-lookup"><span data-stu-id="8611d-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="8611d-186">當**程序： 完成**會出現在視窗的底部，按一下 [**程序摘要**在左側導覽中查看摘要。</span><span class="sxs-lookup"><span data-stu-id="8611d-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="8611d-187">在上方導覽列中，按一下 [**分析**]。</span><span class="sxs-lookup"><span data-stu-id="8611d-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="8611d-188">在**安裝程式**] 頁面的 [**佈景主題**]，輸入**3**中**的佈景主題的最大數目**。</span><span class="sxs-lookup"><span data-stu-id="8611d-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="8611d-189">按一下 [**分析]** 並等候完成分析。</span><span class="sxs-lookup"><span data-stu-id="8611d-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="8611d-190">您應該會看到一系列的帶有子橫條圖具有目標母體、 文件、 電子郵件，以及附件的分析。</span><span class="sxs-lookup"><span data-stu-id="8611d-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="8611d-191">如需詳細資訊，請參閱 <<c0>檢視分析結果。</span><span class="sxs-lookup"><span data-stu-id="8611d-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="8611d-192">您現在可以使用此環境建立新的內容、 新的搜尋情況下，並進一步與 Office 365 進階電子文件。</span><span class="sxs-lookup"><span data-stu-id="8611d-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8611d-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8611d-193">See Also</span></span>

[<span data-ttu-id="8611d-194">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="8611d-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="8611d-195">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8611d-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="8611d-196">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8611d-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="8611d-197">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="8611d-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="8611d-198">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="8611d-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="8611d-199">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="8611d-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="8611d-200">Office 365 進階電子文件探索</span><span class="sxs-lookup"><span data-stu-id="8611d-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


