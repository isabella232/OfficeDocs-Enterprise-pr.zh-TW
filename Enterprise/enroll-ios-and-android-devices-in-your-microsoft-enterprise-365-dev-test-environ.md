---
title: "註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置"
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "摘要： 使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。"
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>註冊 iOS 和 Microsoft 企業 365 開發人員/測試環境中的 Android 裝置

 **摘要：**使用此測試實驗室指南註冊 Microsoft 365 開發人員/測試環境中的裝置並從遠端管理它們。
  
Microsoft Enterprise 行動性套件 (EMS) 可協助您的員工提高工作效率使用其最愛的應用程式和裝置的保護組織的資料。如需詳細資訊，請參閱[企業行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
如果您需要在裝置層級套用安全性作業，您必須在 Microsoft Intune 中註冊裝置。裝置註冊不只可協助您管理公司擁有的裝置，也可管理個人 (BYOD) 及共用的裝置 (視您組織的法規政策而定)。
  
遵循本文中提供的指示，您將能夠註冊並在 Microsoft 365 開發人員/測試環境中測試 iOS 及 Android 裝置的基本的行動裝置管理功能。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>階段 1： 建立 Microsoft 365 開發人員/測試環境

遵循[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)中的指示。
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>階段 2：自訂 Microsoft Intune 公司入口網站應用程式

使用以下步驟自訂您虛構公司的 Microsoft Intune 公司入口網站：
  
1. 在 [新增] 索引標籤上開啟 Microsoft Intune 管理主控台 ([https://manage.microsoft.com](https://manage.microsoft.com))。
    
2. 在功能窗格] 中按一下 [**管理**和在 [**管理**] 窗格中 [**行動裝置管理**。
    
3. 在 [**工作**] 清單中選取 [**設定行動裝置管理授權**。請確定它設為**Microsoft Intune**。
    
4. 在 [**管理**] 窗格中，按一下 [**公司入口網站**。
    
5. 在**公司入口網站**] 窗格中，設定下列設定：
    
  - 公司名稱：\<虛構公司名稱 >
    
  - IT 部門連絡人名稱： **User5**
    
  - IT 部門電話號碼： **555-1234**
    
  - IT 部門電子郵件地址： **User5 @**\<虛構的組織名稱 > **。 onmicrosoft.com** （User5 帳戶的電子郵件地址）
    
6. 在**自訂**、 選取**佈景主題**色彩的**綠色**。
    
7. 按一下 [**儲存**]。
    
下一步，您將安裝 Microsoft Intune 公司入口網站應用程式並註冊 iOS 或 Android 裝置，然後從 Microsoft Intune 管理主控台測試基本管理功能。
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>階段 3 (僅適用於 iOS 裝置)：註冊並管理 iOS 裝置

若要註冊 iOS 裝置以透過 Intune 進行管理，您需要下列項目：
  
- Apple iPad 或 iPhone 等 iOS 裝置。
    
- IOS 裝置密碼的知識。
    
- Apple 識別碼 （帳戶名稱和密碼）。如果您已經沒有，前往[Apple 識別碼網站](https://appleid.apple.com/#!&amp;page=signin)並按一下 [**建立 Apple 識別碼**。建立 Apple 識別碼對應至您的 Office 365 訂閱的全域管理員帳戶。安全的位置記錄您的新 Apple ID 帳戶名稱和密碼。
    
需要 Apple Push Notification Service (APNs) 的憑證，Intune 才能管理 iOS 和 Mac 裝置。一旦將憑證新增到 Intune，使用者就可以安裝 Microsoft Intune 公司入口網站應用程式來註冊他們的裝置，或管理員可以為公司擁有的 iOS 裝置設定管理作業。
  
您將需要憑證簽署要求檔案來要求 Apple Push Certificates 入口網站的信任關係憑證。若要取得憑證簽署要求檔案：
  
1. 在 Microsoft Intune 管理主控台中，按一下 [功能窗格中的**管理**。
    
    在 [**管理**] 窗格中，開啟 [**行動裝置管理 > iOS 和 Mac OS X**，然後按一下 [**上傳 APNs 憑證**中**的工作**。 
    
2. 在**APNs 憑證上傳**] 窗格中，按一下 [**下載 APNs 憑證要求**。儲存的憑證簽署要求 (.csr) 檔案在本機名稱**開發人員測試**。
    
若要取得 Apple Push Notification Service 憑證：
  
1. 開啟 [新增] 索引標籤、 移至 [ [Apple 推入憑證入口網站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)，並使用 Apple 識別碼登入
    
2. 在 [**開始**] 頁面上，按一下 [**建立憑證**。
    
3. 在 [**使用**] 頁面上選取 [**我已閱讀並同意這些條款和條件**] 和 [**接受**。
    
4. 在 [**建立新的推入憑證**] 頁面上按一下 [**瀏覽**和選取在前一步驟中儲存的**開發人員 test.csr**檔案和 [**上傳**。出現提示時若要開啟 [json 檔案，請將它儲存到相同的開發人員 test.csr 檔案儲存所在的資料夾。
    
5. 開啟[Apple 推入憑證入口網站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)中的不同的索引標籤及**協力廠商伺服器的憑證**，按一下 [**下載**。
    
6. 出現提示時若要開啟 [.pem 檔案，請將其儲存至相同的開發人員 test.csr 檔案儲存所在的資料夾名稱**test.pem 開發人員**使用。這是 APNs 憑證。
    
若要將 APNs 憑證上傳到 Intune：
  
1. 在 [Microsoft Intune 管理主控台] 索引標籤上**APNs 憑證上傳**] 頁面上按一下 [ **APNs 憑證上傳**]。
    
2. 按一下 [**瀏覽**並指定**開發 test.pem**檔案。
    
3. 按一下 [**開啟]**、 輸入 Apple ID 帳戶名稱，和 [**上傳**。您應該會看到**已準備好用於註冊**郵件**iOS 與 MaxOS X 行動裝置管理安裝**] 頁面上。
    
安裝 APNs 憑證後，Intune 現在可以透過將原則推播至註冊的行動裝置來註冊並管理 iOS 裝置。
  
若要下載 Microsoft Intune 公司入口網站應用程式並註冊 iOS 裝置︰
  
1. 在您的 iOS 裝置中使用 Apple ID 登入。
    
2. 開啟 [ **Apple 市集**應用程式]。
    
3. 在 [搜尋] 方塊中輸入**intune**並點選 [ **Microsoft Intune 的公司入口網站**，則**取得**，然後**安裝**。
    
4. 它會在安裝之後，點選 [**開啟**]。
    
5. 在 [ **Intune 的公司入口網站**] 畫面上使用登入您的 Office 365 全域管理員帳戶。
    
6. 在**公司 Access 安裝**] 畫面上，點選 [**開始**，然後再點選 [**繼續]**兩次。
    
7. 在**接下來是什麼？**螢幕、 點選**註冊**。
    
8. 在**啟動裝置管理員吗？**螢幕、 點選 [**啟動**。
    
9. 在 [**管理設定檔**] 畫面中，點選 [**安裝**]。
    
10. 在 [**輸入密碼**，輸入您 iOS 裝置密碼。
    
11. 在**接下來是什麼**] 畫面中，點選 [**註冊**]。
    
12. 在**安裝設定檔**，點選 [**安裝**]。
    
13. 點選 [**警告**] 頁面的 [**安裝**]。
    
14. 在 [**遠端管理**，點選 [**信任**]。
    
15. 點選 [完成註冊程序的 [**完成**]。
    
16. 當系統提示時**開啟"Comp Portal"中的此頁面？**，點選 [**開啟**。
    
17. 在**公司 Access 安裝**] 畫面上，點選 [**開始**，然後再點選 [**完成**。
    
18. 在 Microsoft Intune 公司入口網站應用程式的主畫面中，您應該會看到︰
    
  - 綠色的橫幅。
    
  - 您的虛擬公司名稱會在左上方。
    
  - 您的 iOS 裝置名稱列在**「 我的裝置**。
    
  - 在 [**服務台**] 區段中，按一下 [ **User5**與**555-1234年**與**連絡人電子郵件**] 按鈕的電話號碼的**連絡人名稱**。
    
Microsoft Intune 提供遠端鎖定和密碼重設功能。如果有人遺失他們的裝置，您可以從遠端鎖定裝置。如果有人忘記他們的密碼，您可以從遠端移除密碼。
  
若要從遠端鎖定 iOS 裝置︰
  
1. 從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中，按一下左方導覽中的 [**群組**]。
    
2. 在 [**群組**] 窗格中，開啟 [**所有裝置 > 所有的行動裝置 > 所有直接的受管理的裝置**。
    
3. 在**所有直接的受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。
    
4. 在裝置清單中，按一下您的 iOS 裝置。  
    
5. 透過您的 iOS 裝置，確定裝置位於主畫面。  
    
6. 從 [系統管理電腦，在工作列上，按一下 [**遠端工作 > 遠端鎖定**。觀看 iOS 裝置將它會切換至 [鎖定] 畫面。
    
若要移除密碼︰
  
1. 從系統管理電腦中**的所有直接受管理的裝置**] 窗格中，按一下 [**裝置**] 索引標籤。
    
2. 在清單中，按一下 [iOS 裝置]。在工作列上，按一下 [**遠端工作 > 密碼重設**。靜待一分鐘。
    
3. 從您的 iOS 裝置解除鎖定其並注意到已不再密碼。若要變更密碼後，移至 [**設定**]，然後**密碼**。
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>階段 3 (僅適用於 Android 裝置)：註冊並管理 Android 裝置

若要註冊 Android 裝置以透過 Intune 進行管理，您需要下列項目：
  
- Android 裝置。
    
- 裝置密碼的知識。
    
若要下載 Intune 公司入口網站應用程式並註冊 Android 裝置︰
  
1. 從您 Android 裝置移至**Google 播放存放區**中，然後再點選 [**開始**。
    
2. 在 [搜尋] 方塊中輸入**intune**並再點選 [搜尋結果中的**intune 的公司入口網站**。
    
3. 點選 [ **Intune 的公司入口網站**項目，然後點選 [**安裝**。
    
4. 點選**的完整帳戶設定**] 畫面上的 [**繼續**，然後按一下 [**略過**]。
    
5. 在**Intune 的公司入口網站**，點選 [**接受**]。應用程式安裝中。
    
6. 點選 [**開啟**]，然後點選 [**登入**。
    
7. 在 [ **Intune 的公司入口網站**] 畫面上使用登入您的 Office 365 全域管理員帳戶。
    
8. 在**公司 Access 安裝**] 畫面上，點選 [**開始**，然後**繼續**按兩次。
    
9. 在**接下來是什麼？**螢幕、 點選**註冊**。
    
10. 在**啟動裝置管理員吗？**螢幕、 點選**Activate。**
    
11. 在**具有隱私權原則**] 畫面上，選取 [**我確認**，然後點選 [**確認**。等候註冊程序來完成。
    
12. 在**公司 Access 安裝**] 畫面上，點選 [**繼續**，然後再點選 [**完成**。
    
13. 在 Microsoft Intune 公司入口網站應用程式的主畫面中，您應該會在左上方看到綠色的橫幅和您在虛構公司的名稱。
    
14. 點選 [**我的裝置**。您應該會看到您 Android 裝置的名稱清單中。
    
15. 點選**連絡人 IT**。您應該會看到**555-1234年**、**連絡電子郵件**] 按鈕的電話號碼和 IT 連絡人的**User5**。
    
Microsoft Intune 提供遠端鎖定和密碼重設功能。如果有人遺失他們的裝置，您可以從遠端鎖定裝置。如果有人忘記他們的密碼，您可以從遠端重設密碼。
  
若要從遠端鎖定 Android 裝置︰
  
1. 從您的系統管理電腦、 Microsoft Intune 管理主控台] 索引標籤上的瀏覽器中，按一下左方導覽中的 [**群組**]。
    
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

[Microsoft 365 Enterprise 開發人員/測試環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Enterprise 開發人員/測試環境的 MAM 原則](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Enterprise 行動性 + 安全性 （EMS）](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


