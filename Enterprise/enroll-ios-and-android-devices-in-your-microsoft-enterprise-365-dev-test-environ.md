---
title: 在您的 Microsoft 365 企業版開發/測試環境中註冊 iOS 和 Android 裝置
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 摘要： 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720409"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="8565c-103">在您的 Microsoft 365 企業版開發/測試環境中註冊 iOS 和 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="8565c-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="8565c-104">**摘要：** 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。</span><span class="sxs-lookup"><span data-stu-id="8565c-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="8565c-p101">Microsoft Enterprise 行動性套件 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="8565c-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="8565c-p102">如果您要套用安全性層級的裝置，您必須將 Microsoft Intune 註冊裝置。裝置註冊不只可協助您管理組織擁有的裝置，但也個人 (BYOD) 與共用的裝置，視組織而定的法律原則。</span><span class="sxs-lookup"><span data-stu-id="8565c-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="8565c-109">遵循本文中提供的指示，您將能夠註冊並在 Microsoft 365 開發人員/測試環境中測試 iOS 及 Android 裝置的基本的行動裝置管理功能。</span><span class="sxs-lookup"><span data-stu-id="8565c-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="8565c-110">階段 1： 建立 Microsoft 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="8565c-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="8565c-111">遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="8565c-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="8565c-112">階段 2： 註冊 iOS 及 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="8565c-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="8565c-113">首先，使用中的指示[安裝並登入的公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)自訂您的測試環境的 Microsoft Intune 的公司入口網站應用程式。</span><span class="sxs-lookup"><span data-stu-id="8565c-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="8565c-114">接下來，使用中[設定您的公司資源的存取權](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)的指示以註冊 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="8565c-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="8565c-115">接下來，用於指示中[註冊您的 Intune 的 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)註冊 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="8565c-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="8565c-116">階段 3： IOS 及 Android 裝置從遠端管理</span><span class="sxs-lookup"><span data-stu-id="8565c-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="8565c-p103">Microsoft Intune 提供遠端鎖定及密碼重設功能。如果某人失去使用者的裝置，您可以從遠端鎖定裝置。如果有人忘記其密碼，您可以從遠端重。</span><span class="sxs-lookup"><span data-stu-id="8565c-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="8565c-120">若要從遠端鎖定 iOS 或 Android 裝置：</span><span class="sxs-lookup"><span data-stu-id="8565c-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="8565c-121">在 Azure 入口網站登入[https://portal.azure.com](https://portal.azure.com)以全域管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="8565c-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="8565c-122">按一下 [**所有服務**，並輸入**Intune**，然後按一下都 [ **Intune**。</span><span class="sxs-lookup"><span data-stu-id="8565c-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="8565c-123">按一下 [**裝置 > 所有裝置**。</span><span class="sxs-lookup"><span data-stu-id="8565c-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="8565c-124">在裝置的清單中，按一下 iOS 或 Android 裝置和 [**遠端鎖定**巨集指令。</span><span class="sxs-lookup"><span data-stu-id="8565c-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="8565c-125">若要從遠端重設密碼︰</span><span class="sxs-lookup"><span data-stu-id="8565c-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="8565c-126">必要時，在 Azure 的入口網站登入[https://portal.azure.com](https://portal.azure.com)以全域管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="8565c-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="8565c-127">按一下 [**所有服務**，並輸入**Intune**，然後按一下都 [ **Intune**。</span><span class="sxs-lookup"><span data-stu-id="8565c-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="8565c-128">按一下 [**裝置 > 所有裝置**。</span><span class="sxs-lookup"><span data-stu-id="8565c-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="8565c-p104">從裝置清單您可以管理、 按一下 iOS 或 Android 裝置，並選擇 **...]更多**。然後選擇 [**移除密碼**裝置遠端巨集指令。</span><span class="sxs-lookup"><span data-stu-id="8565c-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="8565c-131">如其他試驗，請參閱[可用的裝置動作](https://docs.microsoft.com/intune/device-management#available-device-actions)。</span><span class="sxs-lookup"><span data-stu-id="8565c-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="8565c-132">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="8565c-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8565c-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="8565c-133">See Also</span></span>

[<span data-ttu-id="8565c-134">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8565c-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="8565c-135">Microsoft 365 企業版開發/測試環境的 MAM 原則</span><span class="sxs-lookup"><span data-stu-id="8565c-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="8565c-136">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="8565c-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="8565c-137">Enterprise 行動性 + 安全性 （EMS）</span><span class="sxs-lookup"><span data-stu-id="8565c-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


