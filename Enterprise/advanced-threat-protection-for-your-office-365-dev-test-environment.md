---
title: "用於 Office 365 開發/測試環境的進階威脅防護"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- TLG
- Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "摘要： 設定及示範 Office 365 開發人員/測試環境中的 Office 365 進階威脅保護。"
ms.openlocfilehash: 00b1fc8fea930346f082d3d2302a14dea7ad4309
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="4f451-103">用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="4f451-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="4f451-104">**摘要：**設定與示範 Office 365 進階威脅保護 Office 365 開發人員/測試環境中。</span><span class="sxs-lookup"><span data-stu-id="4f451-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="4f451-p101">Office 365 進階威脅保護 (ATP) 是一種功能的 Exchange Online Protection (EOP) 可協助保留惡意程式碼不在您的電子郵件。您可以使用 ATP、 建立原則來在 Exchange 系統管理中心 (EAC) 或安全性&amp;規範中心有助於確保您的使用者存取僅或連結會被識別為不是惡意的電子郵件中的附件。如需詳細資訊，請參閱 ＜[進階的威脅保護安全附件及安全的連結](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4f451-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="4f451-108">透過本文中的指示，您會設定並測試您 Office 365 試用版訂閱中的 ATP。</span><span class="sxs-lookup"><span data-stu-id="4f451-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="4f451-109">階段 1：建置輕量型或模擬的企業 Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="4f451-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="4f451-110">如果您只想要測試 ATP 的基本需求的輕量型方式，請在階段 2 和 3 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="4f451-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="4f451-111">如果您想要測試 ATP 模擬 enterprise 中，請遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4f451-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4f451-p102">測試 ATP 不需要模擬的企業開發/測試環境，其中包括模擬的內部網路 (連線到網際網路) 和 Windows Server AD 樹系中的目錄同步處理。它在這裡提供作為選項，讓您可以在代表典型組織的環境中測試和試驗 ATP。</span><span class="sxs-lookup"><span data-stu-id="4f451-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="4f451-114">階段 2： 示範 Office 365 的預設電子郵件傳遞行為</span><span class="sxs-lookup"><span data-stu-id="4f451-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="4f451-115">在此階段中，您會示範未建立 ATP 原則時，潛在惡意電子郵件如何在沒有檢測或緩和措施的情況下傳遞至 Office 365 信箱。</span><span class="sxs-lookup"><span data-stu-id="4f451-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="4f451-116">開啟 Internet Explorer 並登入您在階段 2 的[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中建立的 Outlook 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4f451-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="4f451-117">如果您使用輕量型 Office 365 開發/測試環境，請開啟 Internet Explorer 的私密工作階段，並從本機電腦登入。</span><span class="sxs-lookup"><span data-stu-id="4f451-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="4f451-118">如果您使用模擬的企業版 Office 365 開發人員/測試環境，使用[Azure 入口網站](https://portal.azure.com)連線到 CLIENT1 虛擬機器，並從 CLIENT1 登入。</span><span class="sxs-lookup"><span data-stu-id="4f451-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="4f451-119">執行「記事本」並輸入一些文字。</span><span class="sxs-lookup"><span data-stu-id="4f451-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="4f451-120">將檔案儲存為**getKeys.js**文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f451-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="4f451-121">從 Internet Explorer 的 [Outlook 信箱] 索引標籤中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="4f451-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="4f451-122">在 [**至**] 輸入您的試用版訂閱 Office 365 全域管理員名稱的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="4f451-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="4f451-123">主旨中，輸入**新的金鑰**。</span><span class="sxs-lookup"><span data-stu-id="4f451-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="4f451-124">本文中，輸入**以下是檔案**。</span><span class="sxs-lookup"><span data-stu-id="4f451-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="4f451-125">按一下 [**附加**、 連按兩下 [文件] 資料夾中的**getKeys.js** 、 按一下 [**附加複本**，和 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="4f451-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="4f451-126">按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="4f451-126">Click **New**.</span></span>
    
10. <span data-ttu-id="4f451-127">在 [**至**] 輸入您的試用版訂閱 Office 365 全域管理員名稱的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="4f451-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="4f451-128">主旨中，輸入**新旅行社網站**。</span><span class="sxs-lookup"><span data-stu-id="4f451-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="4f451-129">本文中，輸入**某人轉寄我這個網站**。</span><span class="sxs-lookup"><span data-stu-id="4f451-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="4f451-130">本文中，選取 [**此網站**文字並按一下工具列中的 [超連結] 圖示。</span><span class="sxs-lookup"><span data-stu-id="4f451-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="4f451-131">在**URL**] 中輸入**http://www.spamlink.contoso.com/**、 按一下 [**確定**] 和 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="4f451-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="4f451-132">在私人的瀏覽模式中開啟 Internet Explorer 的個別執行個體、 移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="4f451-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="4f451-133">從主要的入口網站] 頁面上，按一下 [應用程式] 磚和 [**郵件**。</span><span class="sxs-lookup"><span data-stu-id="4f451-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="4f451-134">收件匣] 中按一下 [主旨**您新機碼**的郵件。</span><span class="sxs-lookup"><span data-stu-id="4f451-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="4f451-p103">在 [垃圾郵件] 資料夾中，按一下 [**新增旅行社網站**主旨的郵件。在郵件中按一下**此網站**連結。您應該會看到 「 Oops ！Internet Explorer 找不到 spamlink.contoso.com。 」 頁面。這會是正確的結果是因為在該位置上沒有任何網頁。</span><span class="sxs-lookup"><span data-stu-id="4f451-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="4f451-p104">請注意兩個這些可能的惡意的電子郵件已傳遞成功。**新的金鑰**電子郵件可能包含未偵測到惡意程式碼和允許使用者已按一下 [**新增旅行社網站**電子郵件中的可能的惡意連結。</span><span class="sxs-lookup"><span data-stu-id="4f451-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="4f451-143">階段 3：設定 ATP 的安全附件和安全連結原則</span><span class="sxs-lookup"><span data-stu-id="4f451-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="4f451-144">在此階段中，您會建立並設定安全附件原則來阻止傳遞包含惡意附件的電子郵件，以及建立和設定連結原則來防止使用者瀏覽可能不安全的 URL。</span><span class="sxs-lookup"><span data-stu-id="4f451-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="4f451-145">在 Internet Explorer 的 [ **Microsoft Office Home** ] 索引標籤中，按一下 [**系統**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="4f451-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="4f451-146">在左導覽列中，按一下 [**系統中心**，然後**Exchange**。</span><span class="sxs-lookup"><span data-stu-id="4f451-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="4f451-147">在 [Exchange 系統管理中心] 索引標籤的左方導覽，按一下 [**進階的威脅**。</span><span class="sxs-lookup"><span data-stu-id="4f451-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="4f451-148">[**安全的附件**] 索引標籤和 [加號。</span><span class="sxs-lookup"><span data-stu-id="4f451-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="4f451-149">在**新的安全附件原則**] 視窗的 [**名稱**] 中輸入 [**安全的附件原則-區塊**。</span><span class="sxs-lookup"><span data-stu-id="4f451-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="4f451-150">針對**安全附件未知的惡意程式碼回應**] 按一下 [**封鎖**]。</span><span class="sxs-lookup"><span data-stu-id="4f451-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="4f451-151">**重新導向附件偵測上的**，按一下 [**啟用重新導向**，輸入您的 Office 365 全域管理員帳戶的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="4f451-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="4f451-p105">針對**適**，按一下向下箭號，和 [**收件者的網域是**。在視窗中，按一下您的組織名稱 （例如 contoso.onmicrosoft.com) 及 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="4f451-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="4f451-p106">按一下 [**儲存**]。更新之後您應該會看見新並啟用**安全的附件原則-區塊**。</span><span class="sxs-lookup"><span data-stu-id="4f451-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="4f451-156">[**安全的連結**] 索引標籤和 [加號。</span><span class="sxs-lookup"><span data-stu-id="4f451-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="4f451-157">在 [**新的安全連結原則**] 視窗的 [**名稱**] 中輸入**安全連結原則**。</span><span class="sxs-lookup"><span data-stu-id="4f451-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="4f451-158">**選取訊息中的未知可能的惡意 url 的巨集指令**，請**上**，按一下 [，然後選取 [**不允許使用者透過按一下以原始 URL**。</span><span class="sxs-lookup"><span data-stu-id="4f451-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="4f451-p107">針對**適**，按一下向下箭號，和 [**收件者的網域是**。在視窗中，按一下您的組織名稱 （例如 contoso.onmicrosoft.com) 及 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="4f451-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="4f451-p108">按一下 [**儲存**]。您應該會看見新並啟用**安全連結原則**。</span><span class="sxs-lookup"><span data-stu-id="4f451-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="4f451-163">階段 4：顯示作用中的 ATP</span><span class="sxs-lookup"><span data-stu-id="4f451-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="4f451-164">在這個階段中，您可以試做 ATP 處理潛在惡意電子郵件的方式。</span><span class="sxs-lookup"><span data-stu-id="4f451-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="4f451-165">從您用來在階段 2，傳送電子郵件的左方導覽中的 Internet Explorer 的執行個體，按一下 [**傳送的項目。**</span><span class="sxs-lookup"><span data-stu-id="4f451-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="4f451-166">按一下標題為**新的金鑰**的電子郵件、 按一下向下箭號圖示，和 [**正向**。</span><span class="sxs-lookup"><span data-stu-id="4f451-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="4f451-167">新郵件，在 [**至**] 輸入您的試用版訂閱 Office 365 全域管理員名稱的電子郵件地址，然後按一下 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="4f451-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="4f451-168">按一下 [電子郵件標題**新增旅行社網站**、 [向下箭號圖示、 按一下 [**全部回覆**，和 [**傳送**。</span><span class="sxs-lookup"><span data-stu-id="4f451-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="4f451-p109">您用來設定 ATP 原則在階段 3 中的 Internet Explorer 的執行個體，從 [Exchange 系統管理中心] 索引標籤、 按一下 [應用程式] 磚和 [**郵件**。您應該會看到兩個新電子郵件訊息收件匣：</span><span class="sxs-lookup"><span data-stu-id="4f451-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="4f451-171">一個名為**Fw： 新的金鑰**</span><span class="sxs-lookup"><span data-stu-id="4f451-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="4f451-172">一個名為**Fw： 新的旅行網站**</span><span class="sxs-lookup"><span data-stu-id="4f451-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="4f451-p110">開啟電子郵件標題**Fw： 新的旅行網站**並按一下 [**此網站**] 連結。您應該會看到 「 這個網站具有已分類為惡意。 」 頁面。此示範 ATP 防止您存取可能的惡意網站。</span><span class="sxs-lookup"><span data-stu-id="4f451-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="4f451-177">Exchange admin center] 索引標籤中的 Internet Explorer 中，在左導覽列中，按一下 [**郵件流程**]。</span><span class="sxs-lookup"><span data-stu-id="4f451-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="4f451-178">[**郵件追蹤**] 索引標籤和 [**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="4f451-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="4f451-p111">在**郵件追蹤結果**視窗中，按兩下 [郵件主旨**新的金鑰**]。此郵件已成功傳遞至收件匣。關閉此視窗。</span><span class="sxs-lookup"><span data-stu-id="4f451-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="4f451-p112">按兩下 [**新增旅行社網站**之主旨的郵件。此郵件已成功傳遞至收件匣。關閉此視窗。</span><span class="sxs-lookup"><span data-stu-id="4f451-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="4f451-p113">按兩下 [郵件主旨**Fw： 新的金鑰**。記下此訊息已由 ATP 處理與然後傳遞至收件匣方式。關閉此視窗。</span><span class="sxs-lookup"><span data-stu-id="4f451-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="4f451-p114">安全的附件原則的目的是以開始掃描附件的惡意程式碼。無法決定要惡意已允許 getKeys.js 附件。此步驟會顯示 ATP 並未執行附件的掃描。</span><span class="sxs-lookup"><span data-stu-id="4f451-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="4f451-p115">按兩下 [郵件主旨**Fw： 新的旅行網站**。請注意此郵件已成功傳遞至收件匣。</span><span class="sxs-lookup"><span data-stu-id="4f451-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="4f451-193">您現在可以使用此環境建立新的原則並試驗 ATP。</span><span class="sxs-lookup"><span data-stu-id="4f451-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="4f451-194">按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。</span><span class="sxs-lookup"><span data-stu-id="4f451-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f451-195">See Also</span><span class="sxs-lookup"><span data-stu-id="4f451-195">See Also</span></span>

[<span data-ttu-id="4f451-196">雲端採用測試實驗室指南 (Tlg)</span><span class="sxs-lookup"><span data-stu-id="4f451-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="4f451-197">基本組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="4f451-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="4f451-198">Office 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="4f451-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="4f451-199">Office 365 開發人員/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="4f451-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4f451-200">Office 365 開發人員/測試環境的雲端應用程式安全性</span><span class="sxs-lookup"><span data-stu-id="4f451-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4f451-201">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="4f451-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="4f451-202">進階的威脅保護安全附件和安全連結</span><span class="sxs-lookup"><span data-stu-id="4f451-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


