---
title: "Microsoft 365 Enterprise 開發人員/測試環境的 MAM 原則"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "摘要： 使用此測試實驗室指南新增至 Microsoft 365 開發人員/測試環境的 EMS 行動應用程式管理 (MAM) 原則。"
ms.openlocfilehash: cd5a9801ec7cc5c8fe287fa65015fcb02dd542bf
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="26c88-103">Microsoft 365 Enterprise 開發人員/測試環境的 MAM 原則</span><span class="sxs-lookup"><span data-stu-id="26c88-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="26c88-104">**摘要：**使用此測試實驗室指南新增至 Microsoft 365 開發人員/測試環境的 EMS 行動應用程式管理 (MAM) 原則。</span><span class="sxs-lookup"><span data-stu-id="26c88-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="26c88-p101">Microsoft Enterprise 行動性 + 安全性 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="26c88-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="26c88-107">使用本文中的指示，您可以將行動應用程式管理 (MAM) 原則新增至 Microsoft 365 開發人員/測試環境。</span><span class="sxs-lookup"><span data-stu-id="26c88-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="26c88-108">階段 1： 建立您的 Microsoft 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="26c88-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="26c88-109">遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="26c88-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="26c88-110">階段 2：建立和部署 iOS 和 Android 的裝置的 MAM 原則</span><span class="sxs-lookup"><span data-stu-id="26c88-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="26c88-111">在此階段中，您會建立和部署兩個不同的 MAM 原則：一個適用於 iOS 裝置，另一個適用於 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="26c88-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="26c88-112">移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="26c88-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="26c88-113">在瀏覽器的新] 索引標籤上開啟 Azure 入口網站 ([https://azure.portal.com](https://azure.portal.com)) 並使用您的 Office 365 全域管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="26c88-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="26c88-114">Azure 入口網站] 索引標籤上的 Internet Explorer 中，在功能窗格] 中按一下 [**更多服務**（或右邊的箭號）、 並輸入**Intune**，然後按一下 [ **Intune**。</span><span class="sxs-lookup"><span data-stu-id="26c88-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="26c88-115">在左側瀏覽窗格中，按一下 [群組]****。</span><span class="sxs-lookup"><span data-stu-id="26c88-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="26c88-116">按一下 [**使用者和群組所有群組**blade、 的 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="26c88-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="26c88-117">在**群組**blade 中，輸入**Managed iOS 裝置的使用者****名稱**] 中選取**已指派]**中的**成員資格類型**，請選取**[是]**的**啟用 Office 功能吗？**，然後按一下 [**建立**。</span><span class="sxs-lookup"><span data-stu-id="26c88-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="26c88-118">關閉**群組**blade。</span><span class="sxs-lookup"><span data-stu-id="26c88-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="26c88-119">按一下 [**使用者和群組所有群組**blade、 的 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="26c88-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="26c88-120">在**群組**blade 中，輸入**受管理的 Android 裝置的使用者****名稱**] 中選取**已指派]**中的**成員資格類型**，請選取**[是]**的**啟用 Office 功能吗？**，然後按一下 [**建立**。</span><span class="sxs-lookup"><span data-stu-id="26c88-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="26c88-121">關閉**使用者和群組所有群組**blade。</span><span class="sxs-lookup"><span data-stu-id="26c88-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="26c88-122">在**Intune** blade、**快速工作**清單中，按一下 [**建立規範原則**。</span><span class="sxs-lookup"><span data-stu-id="26c88-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="26c88-123">在**規範原則設定檔**blade 中，按一下 [**建立原則**。</span><span class="sxs-lookup"><span data-stu-id="26c88-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="26c88-p102">在**建立原則**blade，在 [**名稱**] 輸入**iOS**。在**平台**，選取**iOS**、 上**iOS 規範原則**blade 中，按一下 [**確定]**和 [**建立**。</span><span class="sxs-lookup"><span data-stu-id="26c88-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="26c88-126">在**規範原則設定檔**blade 中，按一下 [**建立原則**。</span><span class="sxs-lookup"><span data-stu-id="26c88-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="26c88-p103">在**建立原則**blade，在 [**名稱**] 中，輸入**Android**。在**平台**，選取**Android**、 在**Android 規範原則**blade 中，按一下 [**確定]**和 [**建立**。</span><span class="sxs-lookup"><span data-stu-id="26c88-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="26c88-129">按一下 [**規範原則設定檔**blade、 **Android**原則名稱。</span><span class="sxs-lookup"><span data-stu-id="26c88-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="26c88-130">**Android-屬性**blade 的左方導覽，按一下 [**工作分派**，和 [**選取群組**。</span><span class="sxs-lookup"><span data-stu-id="26c88-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="26c88-131">在 [**選取群組**blade、 [**受管理的 Android 裝置 users**群組，和 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="26c88-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="26c88-132">按一下 [**儲存**]，然後關閉 [ **Android-工作分派**blade。</span><span class="sxs-lookup"><span data-stu-id="26c88-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="26c88-133">按一下 [**規範原則設定檔**blade、 **iOS**原則名稱。</span><span class="sxs-lookup"><span data-stu-id="26c88-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="26c88-134">**IOS-屬性**blade 的左方導覽，按一下 [**工作分派**，和 [**選取群組**。</span><span class="sxs-lookup"><span data-stu-id="26c88-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="26c88-135">在 [**選取群組**blade、 [**受管理 iOS 裝置 users**群組，和 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="26c88-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="26c88-136">按一下 [**儲存**]，然後關閉 [ **iOS-工作分派**blade。</span><span class="sxs-lookup"><span data-stu-id="26c88-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="26c88-137">關閉**規範原則設定檔**blade。</span><span class="sxs-lookup"><span data-stu-id="26c88-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="26c88-138">在**Intune** blade 中，按一下 [在左側導覽中的**管理應用程式**。</span><span class="sxs-lookup"><span data-stu-id="26c88-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="26c88-139">在**行動應用程式**blade 中，按一下 [**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="26c88-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="26c88-140">在 [應用程式] 清單中按一下 [ **PowerPoint**</span><span class="sxs-lookup"><span data-stu-id="26c88-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="26c88-p104">在**PowerPoint 概觀 （英文)** blade 中，按一下 [**指派 > 選取群組 > 受管理的 iOS 裝置 > 選取**。在 [**類型**] 選取 [**線上**] 和 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="26c88-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="26c88-143">針對下列應用程式重複步驟 28：</span><span class="sxs-lookup"><span data-stu-id="26c88-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="26c88-144">Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="26c88-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="26c88-145">Word for iOS</span><span class="sxs-lookup"><span data-stu-id="26c88-145">Word for iOS</span></span>
    
  - <span data-ttu-id="26c88-146">iOS 版 Excel</span><span class="sxs-lookup"><span data-stu-id="26c88-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="26c88-147">iOS 版 Outlook</span><span class="sxs-lookup"><span data-stu-id="26c88-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="26c88-148">iOS 版 Microsoft Dynamics CRM (適用於 iPad)</span><span class="sxs-lookup"><span data-stu-id="26c88-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="26c88-149">iOS 版 Microsoft Dynamics CRM (適用於 iPhone)</span><span class="sxs-lookup"><span data-stu-id="26c88-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="26c88-150">Android 版 Dynamics CRM (適用於手機)</span><span class="sxs-lookup"><span data-stu-id="26c88-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="26c88-151">Android 版 Dynamics CRM (適用於平板電腦)</span><span class="sxs-lookup"><span data-stu-id="26c88-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="26c88-152">Android 版 Excel</span><span class="sxs-lookup"><span data-stu-id="26c88-152">Excel for Android</span></span>
    
  - <span data-ttu-id="26c88-153">Android 版 Word</span><span class="sxs-lookup"><span data-stu-id="26c88-153">Word for Android</span></span>
    
  - <span data-ttu-id="26c88-154">iOS 版的 OneNote</span><span class="sxs-lookup"><span data-stu-id="26c88-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="26c88-155">關閉**行動應用程式-應用程式**blade。</span><span class="sxs-lookup"><span data-stu-id="26c88-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="26c88-156">在**行動應用程式**blade 中，按一下 [**應用程式保護原則**。</span><span class="sxs-lookup"><span data-stu-id="26c88-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="26c88-157">在**應用程式保護原則**blade 中，按一下 [**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="26c88-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="26c88-158">在 [**新增原則**blade 中，輸入**iOS**，和 [**選取所需的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="26c88-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="26c88-159">在**應用程式**blade、 [ **PowerPoint**、 **IPhone 上的 Microsoft Dynamics CRM**、 **Excel**、 **IPhone 上的 Microsoft Dynamics CRM**、 **Word**、 **OneNote**、 及**Outlook**] 和 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="26c88-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="26c88-160">按一下 [**新增原則**blade、 的 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="26c88-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="26c88-161">在**應用程式保護原則**blade 中，按一下 [**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="26c88-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="26c88-162">在**新增原則**blade 中，輸入**Android**、 選取 [ **Android** **平台**，及 [**選取所需的應用程式**。</span><span class="sxs-lookup"><span data-stu-id="26c88-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="26c88-163">在**應用程式**blade 中，按一下 [ **PowerPoint**、**平板電腦的 Dynamics CRM**、 **Excel**、 **Word**、 **Outlook**和**Dynamics CRM 電話**、 及 [**選取**。</span><span class="sxs-lookup"><span data-stu-id="26c88-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="26c88-164">按一下 [**新增原則**blade、 的 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="26c88-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="26c88-165">您現在有兩個 MAM 原則，一個適用於 iOS 裝置，另一個適用於 Android 裝置，並且都已準備好對選取的應用程式使用測試設定進行試驗。</span><span class="sxs-lookup"><span data-stu-id="26c88-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="26c88-166">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="26c88-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26c88-167">請參閱</span><span class="sxs-lookup"><span data-stu-id="26c88-167">See Also</span></span>

[<span data-ttu-id="26c88-168">Microsoft 365 Enterprise 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="26c88-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="26c88-169">註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="26c88-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="26c88-170">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="26c88-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="26c88-171">Enterprise 行動性 + 安全性 （EMS）</span><span class="sxs-lookup"><span data-stu-id="26c88-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


