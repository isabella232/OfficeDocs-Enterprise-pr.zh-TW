---
title: 註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 摘要： 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。
ms.openlocfilehash: 8765a7ffb1bff1f257d7cd1ce5181561c2cf0080
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="ef920-103">註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="ef920-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="ef920-104">**摘要：** 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。</span><span class="sxs-lookup"><span data-stu-id="ef920-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="ef920-p101">Microsoft Enterprise 行動性套件 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="ef920-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="ef920-p102">如果您要套用安全性層級的裝置，您必須將 Microsoft Intune 註冊裝置。裝置註冊不只可協助您管理組織擁有的裝置，但也個人 (BYOD) 與共用的裝置，視組織而定的法律原則。</span><span class="sxs-lookup"><span data-stu-id="ef920-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="ef920-109">遵循本文中提供的指示，您將能夠註冊並在 Microsoft 365 開發人員/測試環境中測試 iOS 及 Android 裝置的基本的行動裝置管理功能。</span><span class="sxs-lookup"><span data-stu-id="ef920-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="ef920-110">階段 1： 建立 Microsoft 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="ef920-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="ef920-111">遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ef920-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="ef920-112">階段 2： 註冊 iOS 及 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="ef920-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="ef920-113">首先，使用中的指示[安裝並登入的公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)來自訂 Microsoft Intune 的公司入口網站應用程式開發人員/測試租用。</span><span class="sxs-lookup"><span data-stu-id="ef920-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="ef920-114">接下來，使用中[設定您的公司資源的存取權](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)的指示以註冊 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="ef920-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="ef920-115">接下來，用於指示中[註冊您的 Intune 的 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)註冊 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="ef920-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="ef920-116">階段 2： IOS 及 Android 裝置從遠端管理</span><span class="sxs-lookup"><span data-stu-id="ef920-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="ef920-p103">Microsoft Intune 提供遠端鎖定和密碼重設功能。如果有人遺失他們的裝置，您可以從遠端鎖定裝置。如果有人忘記他們的密碼，您可以從遠端移除密碼。</span><span class="sxs-lookup"><span data-stu-id="ef920-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="ef920-120">若要從遠端鎖定 iOS 裝置︰</span><span class="sxs-lookup"><span data-stu-id="ef920-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="ef920-121">開啟 [新增] 索引標籤，並移至http://manage.microsoft.com（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="ef920-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="ef920-122">從 Microsoft Intune 管理主控台的瀏覽器中按一下左方導覽中的 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="ef920-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="ef920-123">在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。</span><span class="sxs-lookup"><span data-stu-id="ef920-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="ef920-124">在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ef920-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="ef920-125">在裝置清單中，按一下您的 iOS 裝置。 </span><span class="sxs-lookup"><span data-stu-id="ef920-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="ef920-126">透過您的 iOS 裝置，確定裝置位於主畫面。 </span><span class="sxs-lookup"><span data-stu-id="ef920-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="ef920-p104">從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。觀看 iOS 裝置將它會切換至 [鎖定] 畫面。</span><span class="sxs-lookup"><span data-stu-id="ef920-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="ef920-129">若要移除密碼︰</span><span class="sxs-lookup"><span data-stu-id="ef920-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="ef920-130">從系統管理電腦中**的所有直接受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ef920-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="ef920-p105">在清單中，按一下 [iOS 裝置]。在工作列上，按一下 [**遠端工作 > 密碼重設**。靜待一分鐘。</span><span class="sxs-lookup"><span data-stu-id="ef920-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="ef920-p106">從您的 iOS 裝置解除鎖定其並注意到已不再密碼。若要變更密碼後，移至 [**設定**]，然後**密碼**。</span><span class="sxs-lookup"><span data-stu-id="ef920-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="ef920-136">若要從遠端鎖定 Android 裝置︰</span><span class="sxs-lookup"><span data-stu-id="ef920-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="ef920-137">從 Microsoft Intune 管理主控台的瀏覽器中按一下左方導覽中的 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="ef920-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="ef920-138">在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。</span><span class="sxs-lookup"><span data-stu-id="ef920-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="ef920-139">在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ef920-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="ef920-140">在裝置清單中，按一下您的 Android 裝置。 </span><span class="sxs-lookup"><span data-stu-id="ef920-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="ef920-141">透過您的 Android 裝置，確定裝置位於主畫面。 </span><span class="sxs-lookup"><span data-stu-id="ef920-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="ef920-p107">從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。出現提示時，按一下 [**是**]。</span><span class="sxs-lookup"><span data-stu-id="ef920-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="ef920-144">當 Android 裝置切換至鎖定畫面時，即可觀看您的 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="ef920-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="ef920-145">Android 裝置密碼重設時, Intune 系統管理入口網站，就會產生並設定強式密碼。</span><span class="sxs-lookup"><span data-stu-id="ef920-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="ef920-146">若要從遠端重設密碼︰</span><span class="sxs-lookup"><span data-stu-id="ef920-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="ef920-147">從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中的**所有直接的受管理的裝置**] 窗格中，按一下 [在 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="ef920-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="ef920-148">在工作列上，按一下 [**遠端工作 > 密碼重設**。</span><span class="sxs-lookup"><span data-stu-id="ef920-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="ef920-p108">在**遠端工作： 密碼重設**提示、 按一下 [**是]**。靜待一分鐘。</span><span class="sxs-lookup"><span data-stu-id="ef920-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="ef920-151">在**所有直接的受管理的裝置**] 窗格中，按一下 [**檢視屬性**。</span><span class="sxs-lookup"><span data-stu-id="ef920-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="ef920-152">在**密碼重設**，記下新的密碼。</span><span class="sxs-lookup"><span data-stu-id="ef920-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="ef920-153">在 Android 裝置的鎖定畫面上輸入新密碼。 </span><span class="sxs-lookup"><span data-stu-id="ef920-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="ef920-154">若要變更密碼後，移到**設定**、 點選**裝置**、 點選 [**鎖定] 畫面上**，輸入新的密碼再次、 點選 [**螢幕鎖定**及您所選擇的密碼。</span><span class="sxs-lookup"><span data-stu-id="ef920-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="ef920-155">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="ef920-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ef920-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="ef920-156">See Also</span></span>

[<span data-ttu-id="ef920-157">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="ef920-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="ef920-158">Microsoft 365 企業版開發/測試環境的 MAM 原則</span><span class="sxs-lookup"><span data-stu-id="ef920-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="ef920-159">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="ef920-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="ef920-160">Enterprise 行動性 + 安全性 （EMS）</span><span class="sxs-lookup"><span data-stu-id="ef920-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


