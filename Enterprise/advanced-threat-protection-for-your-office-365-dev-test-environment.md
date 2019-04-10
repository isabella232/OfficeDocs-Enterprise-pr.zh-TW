---
title: 用於 Office 365 開發/測試環境的進階威脅防護
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
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 摘要：設定並示範 Office 365 開發/測試環境中的 Office 365 進階威脅防護。
ms.openlocfilehash: 53bff386490ed9647a511f75c997cb91b0acc181
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741339"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="16716-103">用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="16716-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="16716-104">**摘要：** 設定並示範 Office 365 開發/測試環境中的 Office 365 進階威脅防護。</span><span class="sxs-lookup"><span data-stu-id="16716-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="16716-105">Office 365 進階威脅防護 (ATP) 是Exchange Online Protection (EOP) 的一項功能，可協助防止惡意軟體攻擊您的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="16716-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="16716-106">您可以使用 ATP，建立原則來在 Exchange 系統管理中心 (EAC) 或安全性&amp;協助確保您的使用者存取只有連結或附件會被識別為不是惡意的電子郵件中的合規性中心。</span><span class="sxs-lookup"><span data-stu-id="16716-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="16716-107">如需詳細資訊，請參閱[安全附件和安全連結的進階威脅防護](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="16716-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="16716-108">透過本文中的指示，您會設定並測試您 Office 365 試用版訂閱中的 ATP。</span><span class="sxs-lookup"><span data-stu-id="16716-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="16716-109">階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="16716-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="16716-110">如果您只想以具有最小需求的輕量型方式測試 ATP，請遵循指示，以在階段 2 和 3 的[Office 365 開發/測試環境](office-365-dev-test-environment.md)中。</span><span class="sxs-lookup"><span data-stu-id="16716-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="16716-111">如果您想要在模擬的企業中測試 ATP，請遵循[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="16716-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="16716-112">測試 ATP 不需要模擬的企業版開發/測試環境，其中包含連線至網際網路的模擬內部網路和目錄同步處理的 Active Directory 網域服務 (AD DS) 樹系。</span><span class="sxs-lookup"><span data-stu-id="16716-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="16716-113">它在這裡提供作為選項，讓您可以在代表典型組織的環境中測試和試驗 ATP。</span><span class="sxs-lookup"><span data-stu-id="16716-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="16716-114">階段 2： 展示 Office 365 的預設電子郵件傳遞行為</span><span class="sxs-lookup"><span data-stu-id="16716-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="16716-115">在此階段中，您會示範未建立 ATP 原則時，潛在惡意電子郵件如何在沒有檢測或緩和措施的情況下傳遞至 Office 365 信箱。</span><span class="sxs-lookup"><span data-stu-id="16716-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="16716-116">開啟 Internet Explorer 並登入您的[Office 365 開發/測試環境](office-365-dev-test-environment.md)的階段 2 中建立的 Outlook 帳戶。</span><span class="sxs-lookup"><span data-stu-id="16716-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="16716-117">如果您使用輕量型 Office 365 開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從本機電腦登入。</span><span class="sxs-lookup"><span data-stu-id="16716-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="16716-118">如果您使用模擬的企業 Office 365 開發/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線至 CLIENT1 虛擬機器，然後從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="16716-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="16716-119">執行「記事本」並輸入一些文字。</span><span class="sxs-lookup"><span data-stu-id="16716-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="16716-120">將檔案儲存為 **getKeys.js** 並放置於「文件」資料夾。</span><span class="sxs-lookup"><span data-stu-id="16716-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="16716-121">從 Internet Explorer 的 [Outlook 郵件] 索引標籤中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="16716-122">在 [收件者]\*\*\*\* 中輸入 Office 365 試用版訂閱中全域管理員名稱的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="16716-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="16716-123">主旨請輸入**您的新金鑰**。</span><span class="sxs-lookup"><span data-stu-id="16716-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="16716-124">在本文中輸入**檔案在此**。</span><span class="sxs-lookup"><span data-stu-id="16716-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="16716-125">按一下 [附加檔案]\*\*\*\*，然後在「文件」資料夾中的 **getKeys.js** 上連按兩下，並按一下 [附加為副本]\*\*\*\*，然後按一下 [傳送]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="16716-126">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="16716-126">Click **New**.</span></span>
    
10. <span data-ttu-id="16716-127">在 [收件者]\*\*\*\* 中輸入 Office 365 試用版訂閱中全域管理員名稱的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="16716-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="16716-128">主旨請輸入**新的旅遊網站**。</span><span class="sxs-lookup"><span data-stu-id="16716-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="16716-129">在本文中輸入**有人轉寄此網站給我**。</span><span class="sxs-lookup"><span data-stu-id="16716-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="16716-130">選取本文中的「**此網站**」文字，然後按一下工具列中的超連結按鈕。</span><span class="sxs-lookup"><span data-stu-id="16716-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="16716-131">在 [ **URL**] 中，輸入**http://www.spamlink.contoso.com/**，按一下 [**確定**]，然後按一下 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="16716-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="16716-132">開啟 Internet Explorer 的私用瀏覽模式中的個別執行個體移至 Microsoft 365 系統管理中心 ([https://admin.microsoft.com](https://admin.microsoft.com))，並登入 Office 365 試用訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="16716-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="16716-133">在主要入口網站頁面上按一下應用程式磚，然後按一下 [郵件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="16716-134">在收件匣中，按一下主旨為**您的新金鑰**的訊息。</span><span class="sxs-lookup"><span data-stu-id="16716-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="16716-135">在「垃圾郵件」資料夾中，按一下主旨為**新的旅遊網站**的訊息。</span><span class="sxs-lookup"><span data-stu-id="16716-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="16716-136">按一下訊息中的「**此網站**」連結。</span><span class="sxs-lookup"><span data-stu-id="16716-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="16716-137">您應該會看到 「 Oops ！</span><span class="sxs-lookup"><span data-stu-id="16716-137">You should see a "Oops!</span></span> <span data-ttu-id="16716-138">Internet Explorer 找不到 spamlink.contoso.com。 」</span><span class="sxs-lookup"><span data-stu-id="16716-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="16716-139">頁面。</span><span class="sxs-lookup"><span data-stu-id="16716-139">page.</span></span> <span data-ttu-id="16716-140">這是正確的結果，因為此位置上並沒有網頁。</span><span class="sxs-lookup"><span data-stu-id="16716-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="16716-p104">請注意，這些潛在惡意電子郵件皆已傳遞成功。**您的新金鑰**電子郵件可能包含未偵測到的惡意軟體，且使用者可以點按**新的旅遊網站**電子郵件中的潛在惡意連結。</span><span class="sxs-lookup"><span data-stu-id="16716-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="16716-143">階段 3：設定 ATP 的安全附件和安全連結原則</span><span class="sxs-lookup"><span data-stu-id="16716-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="16716-144">在此階段中，您會建立並設定安全附件原則來阻止傳遞包含惡意附件的電子郵件，以及建立和設定連結原則來防止使用者瀏覽可能不安全的 URL。</span><span class="sxs-lookup"><span data-stu-id="16716-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="16716-145">在 Internet Explorer 的 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [**管理**] 磚。</span><span class="sxs-lookup"><span data-stu-id="16716-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="16716-146">在左側導覽窗格中按一下 [系統管理中心]\*\*\*\*，然後按一下 [Exchange]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="16716-147">在 Exchange 系統管理中心的導覽窗格中，按一下 [進階威脅]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="16716-148">按一下 [安全附件]\*\*\*\* 索引標籤，然後按一下加號。</span><span class="sxs-lookup"><span data-stu-id="16716-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="16716-149">在**新的安全附件原則**] 視窗中，在 [**名稱**] 中輸入**安全附件原則-區塊**。</span><span class="sxs-lookup"><span data-stu-id="16716-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="16716-150">**安全附件的未知惡意程式碼回應**，按一下 [**封鎖**]。</span><span class="sxs-lookup"><span data-stu-id="16716-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="16716-151">對於**偵測時重新導向附件**，按一下 [啟用重新導向]\*\*\*\*，然後輸入您 Office 365 全域管理員帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="16716-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="16716-152">對於**套用至**，按一下向下箭頭，然後按一下 [收件者的網域是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="16716-153">在視窗中，按一下您的組織名稱 （例如，contoso.onmicrosoft.com)，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="16716-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="16716-154">按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-154">Click **Save**.</span></span> <span data-ttu-id="16716-155">之後更新，您應該會看到新，而且可啟用**安全附件原則-區塊**。</span><span class="sxs-lookup"><span data-stu-id="16716-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="16716-156">按一下 [安全連結]\*\*\*\* 索引標籤，然後按一下加號。</span><span class="sxs-lookup"><span data-stu-id="16716-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="16716-157">在 [新增安全連結原則]\*\*\*\* 視窗中，在 [名稱]\*\*\*\* 中輸入**安全連結原則**。</span><span class="sxs-lookup"><span data-stu-id="16716-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="16716-158">對於**針對訊息中的未知潛在惡意 URL 選取動作**，按一下 [開啟]\*\*\*\* 並選取 [不允許使用者點按原始 URL]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="16716-159">對於**套用至**，按一下向下箭頭，然後按一下 [收件者的網域是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="16716-160">在視窗中，按一下您的組織名稱 （例如，contoso.onmicrosoft.com)，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="16716-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="16716-p108">按一下 [儲存]\*\*\*\*。您應該會看到新的且已啟用的**安全連結原則**。</span><span class="sxs-lookup"><span data-stu-id="16716-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="16716-163">階段 4：顯示作用中的 ATP</span><span class="sxs-lookup"><span data-stu-id="16716-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="16716-164">在這個階段中，您可以試做 ATP 處理潛在惡意電子郵件的方式。</span><span class="sxs-lookup"><span data-stu-id="16716-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="16716-165">從您用來傳送電子郵件在階段 2 中，在左側導覽中的 Internet Explorer 的執行個體，按一下 [**傳送項目。**</span><span class="sxs-lookup"><span data-stu-id="16716-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="16716-166">按一下標題為**您的新金鑰**的電子郵件、 按一下向下箭號圖示，，然後按一下 [**正向**。</span><span class="sxs-lookup"><span data-stu-id="16716-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="16716-167">在新訊息中的 [收件者]\*\*\*\* 中輸入 Office 365 試用版訂閱中全域管理員名稱的電子郵件地址，然後按一下 [傳送]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="16716-168">按一下標題為**新的旅遊網站**的電子郵件，按一下向下箭號圖示，按一下 [**全部回覆**，，然後按一下 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="16716-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="16716-p109">從您用來設定階段 3 中 ATP 原則的 Internet Explorer 執行個體，按一下 Exchange 系統管理中心索引標籤，再按一下應用程式磚，然後按一下 [郵件]\*\*\*\*。您應該會看到收件匣中有兩則新的電子郵件訊息：</span><span class="sxs-lookup"><span data-stu-id="16716-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="16716-171">一個名為**轉寄：您的新金鑰**</span><span class="sxs-lookup"><span data-stu-id="16716-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="16716-172">一個名為**轉寄：新的旅遊網站**</span><span class="sxs-lookup"><span data-stu-id="16716-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="16716-173">開啟電子郵件訊息標題為**Fw： 新的旅遊網站**，按一下 [**此網站**] 連結。</span><span class="sxs-lookup"><span data-stu-id="16716-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="16716-174">您應該會看到 「 這個網站被分類為惡意。 」</span><span class="sxs-lookup"><span data-stu-id="16716-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="16716-175">頁面。</span><span class="sxs-lookup"><span data-stu-id="16716-175">page.</span></span> <span data-ttu-id="16716-176">此示範 ATP 會使得您無法存取潛在的惡意的網站。</span><span class="sxs-lookup"><span data-stu-id="16716-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="16716-177">在 Internet Explorer 的 Exchange 系統管理中心索引標籤中，按一下 [郵件流程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="16716-178">按一下 [訊息追蹤]\*\*\*\* 索引標籤，然後按一下 [搜尋]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="16716-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="16716-179">在 [郵件追蹤結果]\*\*\*\* 視窗中，連按兩下主旨為**您的新金鑰**的訊息。</span><span class="sxs-lookup"><span data-stu-id="16716-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="16716-180">此郵件已成功傳遞至收件匣。</span><span class="sxs-lookup"><span data-stu-id="16716-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="16716-181">關閉此視窗。</span><span class="sxs-lookup"><span data-stu-id="16716-181">Close this window.</span></span>
    
10. <span data-ttu-id="16716-182">連按兩下主旨為**新的旅行網站**的訊息。</span><span class="sxs-lookup"><span data-stu-id="16716-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="16716-183">此郵件已成功傳遞至收件匣。</span><span class="sxs-lookup"><span data-stu-id="16716-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="16716-184">關閉此視窗。</span><span class="sxs-lookup"><span data-stu-id="16716-184">Close this window.</span></span>
    
11. <span data-ttu-id="16716-185">連按兩下主旨為**轉寄：您的新金鑰**的訊息。</span><span class="sxs-lookup"><span data-stu-id="16716-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="16716-186">請注意此郵件已由 ATP 處理，再傳遞到收件匣如何。</span><span class="sxs-lookup"><span data-stu-id="16716-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="16716-187">關閉此視窗。</span><span class="sxs-lookup"><span data-stu-id="16716-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="16716-188">安全附件原則的目的是為了開始掃描附件的惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="16716-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="16716-189">因為它不被判定為惡意，已允許 getKeys.js 附件。</span><span class="sxs-lookup"><span data-stu-id="16716-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="16716-190">此步驟會顯示 ATP 並未執行掃描的附件。</span><span class="sxs-lookup"><span data-stu-id="16716-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="16716-191">連按兩下主旨為**轉寄：新的旅遊網站**的訊息。</span><span class="sxs-lookup"><span data-stu-id="16716-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="16716-192">請注意，此郵件已成功傳遞至收件匣。</span><span class="sxs-lookup"><span data-stu-id="16716-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="16716-193">您現在可以使用此環境建立新的原則並試驗 ATP。</span><span class="sxs-lookup"><span data-stu-id="16716-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="16716-194">按一下[這裡](http://aka.ms/catlgstack)取得 Office 365 測試實驗室指南堆疊中所有文章的視覺對應。</span><span class="sxs-lookup"><span data-stu-id="16716-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="16716-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16716-195">See Also</span></span>

[<span data-ttu-id="16716-196">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="16716-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="16716-197">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="16716-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="16716-198">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="16716-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="16716-199">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="16716-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="16716-200">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="16716-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="16716-201">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="16716-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="16716-202">安全附件和安全連結的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="16716-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


