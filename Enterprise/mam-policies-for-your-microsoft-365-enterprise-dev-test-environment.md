---
title: Microsoft 365 Enterprise 開發人員/測試環境的 MAM 原則
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
description: 摘要： 使用此測試實驗室指南新增至 Microsoft 365 開發人員/測試環境的 EMS 行動應用程式管理 (MAM) 原則。
ms.openlocfilehash: 1d4ede9b5757d4adce8909586790bcad51f7433f
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 開發人員/測試環境的 MAM 原則

 **摘要：** 使用此測試實驗室指南新增至 Microsoft 365 開發人員/測試環境的 EMS 行動應用程式管理 (MAM) 原則。
  
Microsoft Enterprise 行動性 + 安全性 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
使用本文中的指示，您可以將行動應用程式管理 (MAM) 原則新增至 Microsoft 365 開發人員/測試環境。
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>階段 1： 建立您的 Microsoft 365 開發人員/測試環境

遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>階段 2：建立和部署 iOS 和 Android 的裝置的 MAM 原則

在此階段中，您會建立和部署兩個不同的 MAM 原則：一個適用於 iOS 裝置，另一個適用於 Android 裝置。
  
1. 移至 Office 365 入口網站 ([https://portal.office.com](https://portal.office.com)) 並登入您的 Office 365 試用版訂閱以全域管理員帳戶。
    
2. 在瀏覽器的新] 索引標籤上開啟 Azure 入口網站 ([https://azure.portal.com](https://azure.portal.com)) 並使用您的 Office 365 全域管理員帳戶登入。
    
3. Azure 入口網站] 索引標籤上的 Internet Explorer 中，在功能窗格] 中按一下 [**所有服務**、 並輸入**Intune**，然後按一下都 [ **Intune**。
    
4. 在左側瀏覽窗格中，按一下 [群組]****。
    
5. 在**群組所有群組**blade 中，按一下 [ **+ 新群組**。
    
6. 在**群組**blade 中，選取 [ **Office 365** **群組類型？**、 在 [**名稱**] 中輸入 [**受管理的 iOS 裝置使用者****成員資格類型**] 中選取 [**已指派**] 和 [**建立**。 
    
7. 關閉**群組**blade。
    
8. 在**群組所有群組**blade 中，按一下 [**新增]**。
    
9. 在**群組**blade 中，選取 [ **Office 365** **群組類型？**、 在 [**名稱**] 中輸入**受管理的 Android 裝置使用者****成員資格類型**] 中選取 [**已指派**] 和 [**建立**。
    
10. 關閉**群組所有群組**blade。
    
11. 在**Intune** blade、**快速工作**清單中，按一下 [**建立規範原則**。
    
12. 在**規範原則設定檔**blade 中，按一下 [**建立原則**。
    
13. 在**建立原則**blade，在 [**名稱**] 輸入**iOS**。在**平台**，選取**iOS**、 上**iOS 規範原則**blade 中，按一下 [**確定]** 和 [**建立**。
    
14. 在**規範原則設定檔**blade 中，按一下 [**建立原則**。
    
15. 在**建立原則**blade，在 [**名稱**] 中，輸入**Android**。在**平台**，選取**Android**、 在**Android 規範原則**blade 中，按一下 [**確定]** 和 [**建立**。
    
16. 按一下 [**規範原則設定檔**blade、 **Android**原則名稱。
    
17. **Android-屬性**blade 的左方導覽，按一下 [**工作分派**，和 [**選取群組**。
    
18. 在 [**選取群組**blade、 [**受管理的 Android 裝置 users**群組，和 [**選取**。
    
19. 按一下 [**儲存**]，然後關閉 [ **Android-工作分派**blade。
    
20. 按一下 [**規範原則設定檔**blade、 **iOS**原則名稱。
    
21. **IOS-屬性**blade 的左方導覽，按一下 [**工作分派**，和 [**選取群組**。
    
22. 在 [**選取群組**blade、 [**受管理 iOS 裝置 users**群組，和 [**選取**。
    
23. 按一下 [**儲存**]，然後關閉 [ **iOS-工作分派**blade。
    
24. 關閉**規範原則設定檔**blade。
    
25. 在**Intune** blade 中，按一下 [在左側導覽中的**管理應用程式**。
    
26. 在**行動應用程式**blade 中，按一下 [**應用程式**。
    
27. 在 [應用程式] 清單中按一下 [ **PowerPoint** 
    
28. 在**PowerPoint 概觀 （英文)** blade 中，按一下 [**指派 > 選取群組 > 受管理的 iOS 裝置 > 選取**。在 [**類型**] 選取 [**線上**] 和 [**儲存**。
    
29. 針對下列應用程式重複步驟 28：
    
  - Outlook for Android
    
  - Word for iOS
    
  - iOS 版 Excel
    
  - iOS 版 Outlook
    
  - iOS 版 Microsoft Dynamics CRM (適用於 iPad)
    
  - iOS 版 Microsoft Dynamics CRM (適用於 iPhone)
    
  - Android 版 Dynamics CRM (適用於手機)
    
  - Android 版 Dynamics CRM (適用於平板電腦)
    
  - Android 版 Excel
    
  - Android 版 Word
    
  - iOS 版的 OneNote
    
30. 關閉**行動應用程式-應用程式**blade。
    
31. 在**行動應用程式**blade 中，按一下 [**應用程式保護原則**。
    
32. 在**應用程式保護原則**blade 中，按一下 [**新增原則**。
    
33. 在 [**新增原則**blade 中，輸入**iOS**，和 [**選取所需的應用程式**。
    
34. 在**應用程式**blade、 [ **PowerPoint**、 **IPhone 上的 Microsoft Dynamics CRM**、 **Excel**、 **IPhone 上的 Microsoft Dynamics CRM**、 **Word**、 **OneNote**、 及**Outlook**] 和 [**選取**。
    
35. 按一下 [**新增原則**blade、 的 [**建立**]。
    
36. 在**應用程式保護原則**blade 中，按一下 [**新增原則**。
    
37. 在**新增原則**blade 中，輸入**Android**、 選取 [ **Android** **平台**，及 [**選取所需的應用程式**。
    
38. 在**應用程式**blade 中，按一下 [ **PowerPoint**、**平板電腦的 Dynamics CRM**、 **Excel**、 **Word**、 **Outlook**和**Dynamics CRM 電話**、 及 [**選取**。
    
39. 按一下 [**新增原則**blade、 的 [**建立**]。
    
您現在有兩個 MAM 原則，一個適用於 iOS 裝置，另一個適用於 Android 裝置，並且都已準備好對選取的應用程式使用測試設定進行試驗。
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="see-also"></a>請參閱

[Microsoft 365 企業版開發/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[在您的 Microsoft 365 企業版開發/測試環境中註冊 iOS 和 Android 裝置](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise 行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


