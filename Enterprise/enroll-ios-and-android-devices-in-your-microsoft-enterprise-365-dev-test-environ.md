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
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置

 **摘要：** 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。
  
Microsoft Enterprise 行動性套件 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
如果您要套用安全性層級的裝置，您必須將 Microsoft Intune 註冊裝置。裝置註冊不只可協助您管理組織擁有的裝置，但也個人 (BYOD) 與共用的裝置，視組織而定的法律原則。
  
遵循本文中提供的指示，您將能夠註冊並在 Microsoft 365 開發人員/測試環境中測試 iOS 及 Android 裝置的基本的行動裝置管理功能。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>階段 1： 建立 Microsoft 365 開發人員/測試環境

遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>階段 2： 註冊 iOS 及 Android 裝置

首先，使用中的指示[安裝並登入的公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)來自訂 Microsoft Intune 的公司入口網站應用程式開發人員/測試租用。

接下來，使用中[設定您的公司資源的存取權](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)的指示以註冊 iOS 裝置。

接下來，用於指示中[註冊您的 Intune 的 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)註冊 Android 裝置。

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>階段 2： IOS 及 Android 裝置從遠端管理

Microsoft Intune 提供遠端鎖定和密碼重設功能。如果有人遺失他們的裝置，您可以從遠端鎖定裝置。如果有人忘記他們的密碼，您可以從遠端移除密碼。
  
若要從遠端鎖定 iOS 裝置︰
  
1.  開啟 [新增] 索引標籤，並移至http://manage.microsoft.com（如果需要）。 

2.  從 Microsoft Intune 管理主控台的瀏覽器中按一下左方導覽中的 [**群組**]。

3. 在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。
    
4. 在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。
    
5. 在裝置清單中，按一下您的 iOS 裝置。  
    
6. 透過您的 iOS 裝置，確定裝置位於主畫面。  
    
7. 從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。觀看 iOS 裝置將它會切換至 [鎖定] 畫面。
    
若要移除密碼︰
  
1. 從系統管理電腦中**的所有直接受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。
    
2. 在清單中，按一下 [iOS 裝置]。在工作列上，按一下 [**遠端工作 > 密碼重設**。靜待一分鐘。
    
3. 從您的 iOS 裝置解除鎖定其並注意到已不再密碼。若要變更密碼後，移至 [**設定**]，然後**密碼**。
    
若要從遠端鎖定 Android 裝置︰
  
1. 從 Microsoft Intune 管理主控台的瀏覽器中按一下左方導覽中的 [**群組**]。
    
2. 在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。
    
3. 在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。
    
4. 在裝置清單中，按一下您的 Android 裝置。  
    
5. 透過您的 Android 裝置，確定裝置位於主畫面。  
    
6. 從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。出現提示時，按一下 [**是**]。
    
7. 當 Android 裝置切換至鎖定畫面時，即可觀看您的 Android 裝置。
    
Android 裝置密碼重設時, Intune 系統管理入口網站，就會產生並設定強式密碼。
  
若要從遠端重設密碼︰
  
1. 從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中的**所有直接的受管理的裝置**] 窗格中，按一下 [在 Android 裝置。
    
2. 在工作列上，按一下 [**遠端工作 > 密碼重設**。
    
3. 在**遠端工作： 密碼重設**提示、 按一下 [**是]**。靜待一分鐘。
    
4. 在**所有直接的受管理的裝置**] 窗格中，按一下 [**檢視屬性**。
    
5. 在**密碼重設**，記下新的密碼。
    
6. 在 Android 裝置的鎖定畫面上輸入新密碼。  
    
7. 若要變更密碼後，移到**設定**、 點選**裝置**、 點選 [**鎖定] 畫面上**，輸入新的密碼再次、 點選 [**螢幕鎖定**及您所選擇的密碼。
    

> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="see-also"></a>請參閱

[Microsoft 365 企業版開發/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 企業版開發/測試環境的 MAM 原則](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise 行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


