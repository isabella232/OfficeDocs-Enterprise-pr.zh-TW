---
title: "資料分類和 Office 365 開發人員/測試環境中顯示標籤"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "摘要： 設定與示範資料分類和 Office 365 開發人員/測試環境中使用 Azure 資訊保護 (AIP) 用戶端顯示標籤。"
ms.openlocfilehash: 06f7ebefad8b4d622ab225298155b4f117ff2b75
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>資料分類和 Office 365 開發人員/測試環境中顯示標籤

 **摘要：**設定與示範資料分類和 Office 365 開發人員/測試環境中使用 Azure 資訊保護 (AIP) 用戶端顯示標籤。
  
Azure 資訊保護用戶端可讓您將分類文件之前您將其上傳至 Office 365 中的 SharePoint Online 資料夾。使用本文中的指示、 安裝 Azure 資訊保護用戶端及示範資料分類。如需詳細資訊，請參閱[Azure 資訊保護](https://www.microsoft.com/cloud-platform/azure-information-protection)。
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>階段 1： 建立 Office 365 開發人員/測試環境

遵循在[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)中的指示。
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>階段 2： 新增 Azure 資訊保護試用訂閱

在此階段中，您可以新增至 Office 365 開發人員/測試環境的 Azure 資訊保護及啟用的使用者帳戶。如果您已設定的[Office 365 和 EMS 開發/測試環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，請略過此階段中。Enterprise 行動性套件試用訂閱包括 Azure Information Protection 授權。
  
首先，註冊 Azure 資訊保護試用訂閱。
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>註冊 Azure 資訊保護試用訂閱

1. 在 Internet Explorer 或瀏覽器中，移至[http://portal.office.com](http://portal.office.com)並使用您的 Office 365 全域管理員帳戶登入。
    
2. 在 [ **Microsoft Office Home** ] 索引標籤上按一下**系統管理**磚。
    
3. 在 Office 365 系統管理員] 索引標籤的 [在左導覽列中，按一下 [**帳務 > 購買服務**。
    
4. 在 [**購買服務**] 頁面上尋找**Azure 資訊保護 Premium P2**項目。將滑鼠停留並按一下 [**開始免費試用版**。
    
5. 在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。
    
6. 在 [**順序回條**] 頁面上按一下 [**繼續**]。
    
接下來，您可讓所有使用者帳戶的 Azure 資訊保護授權。
  
1. 在 [Office 365 系統管理中心] 索引標籤上按一下 [**使用者**]。
    
2.  在 [使用者帳戶] 清單選取您的全域管理員帳戶] 和 [**編輯****產品**授權。
    
3. 開啟以**在** **Azure 資訊保護 Premium P2**產品授權、 按一下 [**儲存]**和 [**關閉**兩次。
    
4. 針對其他使用者帳戶 (使用者 1 到使用者 5) 重複步驟 2 和 3。
    
Office 365 開發人員/測試環境現在有：
  
- Office 365 E5 企業版及 Azure 資訊保護試用版訂閱。
    
- 所有的使用者帳戶能夠使用 Office 365 E5 Enterprise 和 Azure 資訊保護。
    
## <a name="phase-3-demonstrate-data-classification"></a>階段 3： 示範資料分類

在此階段中，您會示範使用 Azure 資訊保護用戶端及預設 Azure 資訊保護原則的資料分類。
  
如果您使用模擬的企業版 Office 365 開發人員/測試環境，所以您必須先在 CLIENT1 上安裝 Office 2016。
  
1. 使用您的瀏覽器，並移至[Azure 入口網站](http://portal.azure.com)。
    
2. 按一下 [**資源群組 >** [您資源群組名稱] **> CLIENT1 > Connect**。
    
3. 在 CLIENT1 中，執行 Internet Explorer、 移至[http://portal.office.com](http://portal.office.com)、 Office 入口網站並再登入 User5 帳戶名稱及密碼。
    
4. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [**安裝 Office 2016**。
    
5. 執行時提示並且**是**由使用者帳戶控制提示時按一下下載。等候安裝 Office。完成後，按一下 [**關閉**兩次。
    
下一步] 安裝 Azure 資訊保護用戶端。
  
1. 在瀏覽器或 Internet Explorer 中，移至[Microsoft Azure 資訊保護下載頁面](https://www.microsoft.com/download/details.aspx?id=53018)。
    
  - 如果您使用 Office 365 開發人員/測試環境的輕量型版本，請在您的本機電腦上使用瀏覽器。
    
  - 如果您使用模擬的企業版 Office 365 開發人員/測試環境，請從 CLIENT1 執行 Internet Explorer。
    
2. 在**Microsoft Azure 資訊保護**下載] 頁面上，按一下 [**下載**]、 按一下**AzInfoProtection.exe**、，然後按 [**下一步**。
    
3. 出現提示時，執行 AzInfoProtection.exe。
    
4. 在 [**安裝 Azure 資訊保護**用戶端] 方塊中，按一下 [**我同意**] 並再按一下**[是]**的使用者帳戶控制提示時。
    
5. 在 [**成功**] 方塊中按一下 [ **Close。**
    
接下來，您會示範文件分類。
  
1. 按一下工作列上的**Word**圖示。
    
2. 出現提示時，使用 User5 帳戶名稱和密碼登入。
    
3. 如果您只是安裝在 CLIENT1 中，Office 2016**第一個事項第一個**] 方塊中，按一下 [**接受**]。
    
4. 按一下 [**空白文件**。 
    
    請注意 [**保護**] 區段中的功能區的 [**首頁**] 索引標籤和文件分類的資料列。
    
5. 在空白的文件中，輸入一些文字。
    
6. 按一下 [**檔 > 儲存**且輸入名稱**BeforeAIP**，然後按一下 [**確定]**。 
    
7. 在文件類別的資料列的**密碼**，按一下向下箭頭和 [**全部公司**。
    
8. 按一下 [**檔 > 另存新檔**且輸入名稱**AfterAIP**，然後按一下 [**確定]**。
    
9. 在工作列上，按一下 [**檔案總管]** ，然後開啟 [**文件**] 資料夾。
    
    請注意**BeforeAIP**和**AfterAIP**文件不同的檔案大小。因為包含分類資訊，AfterAIP 文件是更大。
    
接下來，您讓所有人存取支援網站集合。
  
1. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **SharePoint**]。
    
2. 從**SharePoint** ] 索引標籤上，按一下 [**支援網站集合**]。
    
3. 在右上方，按一下 [**設定**] 圖示，和 [**共用對象**。
    
4. 在**共用 '支援網站集合'**，按一下 [**進階**]。
    
5. 在 SharePoint 群組的清單中，按一下**支援網站集合的成員**。
    
6. 在 [**人員與群組**] 頁面上按一下 [**新增**]。
    
7. 在**共用 '支援網站集合 」**，輸入**所有人**、 [**所有人以外的外部使用者**，和 [**共用。**
    
8. 關閉 [**人員與群組**] 索引標籤。
    
接著，您使用 User5 帳戶登入並將 AIP 受保護文件上傳至支援網站集合的文件] 資料夾。
  
1. 在 [ **Microsoft Office Home** ] 索引標籤中右上方，按一下 [使用者] 圖示及 [**登出**。
    
2. 移至[http://portal.office.com](http://portal.office.com)。
    
3. 在 * * Office 365 登入 * *] 頁面上，按一下 User5 帳戶名稱及登入。
    
4. 在 [ **Microsoft Office Home** ] 索引標籤上按一下 [ **SharePoint > 支援網站集合**。
    
5. 按一下 [**文件**、 按一下 [**上載**]、 [ **AfterAIP**文件和 [**開啟**。
    
    您應該會看到 [文件] 資料夾中的 AfterAIP.docx 支援網站集合中。
    
## <a name="see-also"></a>請參閱

[雲端採用測試實驗室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 和 EMS 開發/測試環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure 的資訊保護](https://www.microsoft.com/cloud-platform/azure-information-protection)


