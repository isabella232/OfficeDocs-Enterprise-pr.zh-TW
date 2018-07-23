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
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>在您的 Microsoft 365 企業版開發/測試環境中註冊 iOS 和 Android 裝置

 **摘要：** 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。
  
Microsoft Enterprise 行動性套件 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
如果您要套用安全性層級的裝置，您必須將 Microsoft Intune 註冊裝置。裝置註冊不只可協助您管理組織擁有的裝置，但也個人 (BYOD) 與共用的裝置，視組織而定的法律原則。
  
遵循本文中提供的指示，您將能夠註冊並在 Microsoft 365 開發人員/測試環境中測試 iOS 及 Android 裝置的基本的行動裝置管理功能。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>階段 1： 建立 Microsoft 365 開發人員/測試環境

遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>階段 2： 註冊 iOS 及 Android 裝置

首先，使用中的指示[安裝並登入的公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)自訂您的測試環境的 Microsoft Intune 的公司入口網站應用程式。

接下來，使用中[設定您的公司資源的存取權](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)的指示以註冊 iOS 裝置。

接下來，用於指示中[註冊您的 Intune 的 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)註冊 Android 裝置。

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>階段 3： IOS 及 Android 裝置從遠端管理

Microsoft Intune 提供遠端鎖定及密碼重設功能。如果某人失去使用者的裝置，您可以從遠端鎖定裝置。如果有人忘記其密碼，您可以從遠端重。
  
若要從遠端鎖定 iOS 或 Android 裝置：

1. 在 Azure 入口網站登入[https://portal.azure.com](https://portal.azure.com)以全域管理員帳戶的認證。
2. 按一下 [**所有服務**，並輸入**Intune**，然後按一下都 [ **Intune**。
3. 按一下 [**裝置 > 所有裝置**。
4. 在裝置的清單中，按一下 iOS 或 Android 裝置和 [**遠端鎖定**巨集指令。

    
若要從遠端重設密碼︰

1. 必要時，在 Azure 的入口網站登入[https://portal.azure.com](https://portal.azure.com)以全域管理員帳戶的認證。
2. 按一下 [**所有服務**，並輸入**Intune**，然後按一下都 [ **Intune**。
3. 按一下 [**裝置 > 所有裝置**。
4. 從裝置清單您可以管理、 按一下 iOS 或 Android 裝置，並選擇 **...]更多**。然後選擇 [**移除密碼**裝置遠端巨集指令。

如其他試驗，請參閱[可用的裝置動作](https://docs.microsoft.com/intune/device-management#available-device-actions)。

    

> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="see-also"></a>請參閱

[Microsoft 365 企業版開發/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 企業版開發/測試環境的 MAM 原則](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise 行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


