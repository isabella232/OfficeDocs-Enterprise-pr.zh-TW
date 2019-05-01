---
title: Office 365 開發/測試環境中的資料分類和標示
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 摘要： 設定並示範資料分類和標記您的 Office 365 開發/測試環境中使用 Azure 資訊保護 (AIP) 用戶端。
ms.openlocfilehash: 66bdbb74ae88e10d5aa4fce2173f9a2b88a15e9b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490061"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Office 365 開發/測試環境中的資料分類和標示

 **摘要：** 設定並示範資料分類和標記您的 Office 365 開發/測試環境中使用 Azure 資訊保護 (AIP) 用戶端。
  
Azure 資訊保護用戶端可讓您之前您將其上傳至 Office 365 中的 SharePoint Online 資料夾分類文件。 透過本文中的指示，您可以安裝 Azure 資訊保護用戶端，並示範資料分類。 如需詳細資訊，請參閱[Azure 資訊保護](https://www.microsoft.com/cloud-platform/azure-information-protection)。
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>階段 1： 建置 Office 365 開發/測試環境

請遵循[Office 365 開發/測試環境](office-365-dev-test-environment.md)中的指示。
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>階段 2： 新增 Azure 資訊保護試用版訂閱

在這個階段，您新增至您的 Office 365 開發/測試環境的 Azure 資訊保護，並啟用的使用者帳戶。 如果您已設定的[Office 365 和 EMS 開發/測試環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，請跳過這個階段中。 Enterprise Mobility Suite 試用版訂閱包含 Azure 資訊保護授權。
  
首先，登入 Azure 資訊保護試用訂用帳戶。
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Azure 資訊保護試用訂用帳戶註冊

1. 在 Internet Explorer 或您的瀏覽器中，移至[http://admin.microsoft.com](http://admin.microsoft.com)並以您的 Office 365 全域系統管理員帳戶登入。
    
2. 在**Microsoft Office 的首頁**] 索引標籤上，按一下 [**管理**] 磚。
    
3. 在 Office 365 系統管理員] 索引標籤的 [在左側導覽中，按一下 [**帳單 > 購買服務**]。
    
4. 在 [**購買服務**] 頁面上，尋找 [ **Azure 資訊保護高階 P2**項目]。 將滑鼠游標，然後按一下 [**開始免費試用版**。
    
5. 在 [確認訂單]**** 頁面上，按一下 [立即試用]****。
    
6. 在 [訂單收據]**** 頁面上，按一下 [繼續]****。
    
接下來，您可以啟用所有使用者帳戶的 Azure 資訊保護授權。
  
1. 在 Microsoft 365 系統管理中心] 索引標籤上按一下 [**使用者**]。
    
2.  在使用者帳戶的清單中，選取您的全域系統管理員帳戶，然後按一下**編輯****產品**授權。
    
3. 開啟產品授權的**Azure 資訊保護高階 P2**到**上**按一下 [**儲存]** ，然後按兩次 [**關閉**。
    
4. 針對其他使用者帳戶 (使用者 1 到使用者 5) 重複步驟 2 和 3。
    
Office 365 開發/測試環境現在擁有：
  
- Office 365 E5 Enterprise 和 Azure 資訊保護試用訂閱。
    
- 您的所有使用者帳戶啟用，可使用 Office 365 E5 Enterprise 和 Azure 資訊保護。
    
## <a name="phase-3-demonstrate-data-classification"></a>階段 3： 展示資料分類

在這個階段，您會示範使用 Azure 資訊保護用戶端及預設的 Azure 資訊保護原則的資料分類。
  
如果您使用模擬的企業 Office 365 開發/測試環境，您必須先在 CLIENT1 上安裝 Office 2016。
  
1. 使用您的瀏覽器並移至[Azure 入口網站](http://portal.azure.com)。
    
2. 按一下 [**資源群組 >** [您的資源群組名稱] **> CLIENT1 > 連線**]。
    
3. 從 CLIENT1，執行 [Internet Explorer，請移至 Office 入口網站，網址[http://admin.microsoft.com](http://admin.microsoft.com)，然後使用 User5 帳戶名稱和密碼登入。
    
4. 在 [Microsoft Office 首頁]**** 索引標籤上，按一下 [安裝 Office 2016]****。
    
5. 執行時出現提示，請按一下 [ **]** 時提示使用者帳戶控制下載。 等待安裝 Office。 完成後，按一下 [**關閉**兩次。
    
接下來，您安裝 Azure 資訊保護用戶端。
  
1. 在瀏覽器或 Internet Explorer 中，移至[Microsoft Azure 資訊保護下載頁面](https://www.microsoft.com/download/details.aspx?id=53018)。
    
  - 如果您使用 Office 365 開發/測試環境的輕量版本，請在本機電腦上使用瀏覽器。
    
  - 如果您使用模擬的企業 Office 365 開發/測試環境，請從 CLIENT1 執行 Internet Explorer。
    
2. 在**Microsoft Azure 資訊保護**下載頁面上，按一下 [**下載**] 按一下 [ **AzInfoProtection.exe**，，然後按 [**下一步**。
    
3. 出現提示時，執行 AzInfoProtection.exe。
    
4. 在 [**安裝 Azure 資訊保護**用戶端中，按一下 [**我同意**]，然後按一下 **[是]** 時提示使用者帳戶控制。
    
5. 在 [**成功**] 方塊中，按一下 [ **] [關閉。**
    
接下來，您會示範在文件分類。
  
1. 按一下 [在工作列上的 [ **Word** ] 圖示。
    
2. 出現提示時，使用 User5 帳戶名稱和密碼登入。
    
3. 如果您剛安裝 Office 2016 在 CLIENT1 中，在**第一件事第一個**方塊中，按一下 [**接受**]。
    
4. 按一下 [**空白文件**。 
    
    請注意 [**保護**] 區段中的功能區上 [**首頁**] 索引標籤和文件分類的資料列。
    
5. 在空白的文件中，輸入一些文字。
    
6. 按一下 [**儲存檔案 >**，輸入名稱**BeforeAIP**，，然後按一下 [**確定]**。 
    
7. 在文件類別的列中，按一下向下箭號的**密碼**，，，然後按一下 [**所有公司**。
    
8. 按一下 [**另存新檔的檔案 >**，輸入名稱**AfterAIP**，，然後按一下 [**確定]**。
    
9. 在工作列上，按一下 [**檔案總管]** ，然後開啟 [**文件**] 資料夾。
    
    請注意**BeforeAIP**和**AfterAIP**文件的不同的檔案大小。 AfterAIP 文件是較大，因為它已分類資訊。
    
接下來，您允許所有人都支援網站集合的存取。
  
1. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [ **SharePoint**]。
    
2. 從**SharePoint** ] 索引標籤上，按一下 [**支援網站集合**]。
    
3. 在右上方，按一下 [**設定**] 圖示，然後按一下**與共用]**。
    
4. 在 [**共用 '支援網站集合]**，按一下 [**進階**]。
    
5. 在 SharePoint 群組的清單中，按一下 [**支援網站集合的成員**。
    
6. 在 [人員與群組]**** 頁面上，按一下 [新增]****。
    
7. 在 [**共用 '支援網站集合]**，輸入**所有人**，請按一下 [**外部使用者以外的所有人**，和 [**共用。**
    
8. 關閉 [**人員與群組**] 索引標籤。
    
接下來，您使用 User5 帳戶登入，並將 AIP 受保護的文件上傳至支援網站集合的文件資料夾。
  
1. 在**Microsoft Office 的首頁**] 索引標籤右上方，按一下 [使用者] 圖示，然後按一下 [**登出]**。
    
2. 請移至 [http://admin.microsoft.com](http://admin.microsoft.com)。
    
3. 在**Office 365 登入**頁面上，按一下 User5 帳戶名稱和登入。
    
4. 在 [ **Microsoft Office 的首頁**] 索引標籤中，按一下 [ **SharePoint > 支援網站集合**。
    
5. 按一下 [**文件**，按一下 [**上傳**、 按一下**AfterAIP**文件，，然後按一下 [**開啟**。
    
    您應該支援網站集合上看到 AfterAIP.docx Documents 資料夾中。
    
## <a name="see-also"></a>另請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 和 EMS 開發/測試環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure 資訊保護](https://www.microsoft.com/cloud-platform/azure-information-protection)


