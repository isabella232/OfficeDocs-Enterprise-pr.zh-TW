---
title: "部署三層的保護的 SharePoint Online 的網站"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "摘要： 建立及設定的不同層級的資訊保護的 SharePoint Online 小組網站。"
ms.openlocfilehash: 0b0c6541f05499526dc472e4e724472d943607ef
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a>部署三層的保護的 SharePoint Online 的網站

 **摘要：**建立及設定的不同層級的資訊保護的 SharePoint Online 小組網站。
  
使用本文中的步驟來設計及部署比較基準 」、 機密、 和高度機密 SharePoint Online 小組網站。如需保護這些三層的詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)。
  
## <a name="baseline-sharepoint-online-team-sites"></a>[比較基準 SharePoint Online 小組網站

[比較基準保護包含這兩個公用及私人小組網站。可以探索和組織中的任何人存取公用小組網站。私用網站可以只探索和存取小組網站相關聯的 Office 365 群組的成員。這兩個小組網站這類允許成員與其他人] 共用網站。
  
### <a name="public"></a>公用

若要建立基準 SharePoint Online 小組網站與公用存取和權限，執行下列動作：
  
1. Office 365 入口網站也可用於管理 SharePoint Online 小組網站 （SharePoint Online 系統管理員） 帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**站台名稱**] 中，輸入公用小組網站的名稱。 
    
6. 在**小組網站描述**] 中，輸入網站的用途說明。
    
7. **隱私權設定**] 中選取**公用位在組織中的任何人都可以存取此站台**，並再按 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，按一下 [**完成]**。
    
以下是您產生的組態。
  
![適用於公用 SharePoint Online 小組網站的基準層級保護。](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a>私人

若要建立基準 SharePoint Online 小組網站與私人 access 和權限，執行下列動作：
  
1. Office 365 入口網站也可用於管理 SharePoint Online 小組網站 （SharePoint Online 系統管理員） 帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 在 [新增**SharePoint** ] 索引標籤在瀏覽器中按一下 [ **+ 建立網站**。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**站台名稱**] 中輸入私人小組網站的名稱。 
    
6. 在**小組網站描述] 中，**輸入網站的用途說明。
    
7. **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，在**新增成員**中，輸入能夠存取這私人小組網站的使用者帳戶的名稱。
    
9. 當您完成初始組成員新增至網站，按一下 [**完成時間**
    
以下是您產生的組態。
  
![適用於私人 SharePoint Online 小組網站的基準層級保護。](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a>機密的 SharePoint Online 小組網站

機密的 SharePoint Online 小組網站是隔離的小組網站] 表示權限所控制透過而不是在小組網站相關聯的 Office 365 群組的成員資格的 SharePoint 群組的成員資格。
  
若要建立的隔離的小組網站，有兩個主要步驟。
  
### <a name="step-1-design-your-isolated-site"></a>步驟 1： 設計在隔離的網站

若要設計隔離的小組網站，您需要決定：
  
- 您的 SharePoint 群組和權限層級。
    
- 將您的 SharePoint 群組的成員存取群組的屬性集。
    
     存取群組的建議的設定是一個網站成員，一個網站檢視者另一個網站管理員。
    
- 您是否要使用的巢狀存取群組內的群組。
    
例如，建議的群組結構和權限層級看起來如下：
  
|**SharePoint 群組**|**權限層級**|**存取群組 （範例）**|
|:-----|:-----|:-----|
|[網站名稱]成員  <br/> |編輯  <br/> |[網站名稱]成員  <br/> |
|[網站名稱]訪客  <br/> |讀取  <br/> |[網站名稱]檢視程式  <br/> |
|[網站名稱]擁有者  <br/> |完全控制  <br/> |[網站名稱]系統管理員  <br/> |
   
小組網站的預設會建立 SharePoint 群組與權限層級。您需要確定您的存取群組的名稱。
  
如需設計程序的詳細資訊，請參閱 ＜ [Design 隔離的 SharePoint Online 小組網站](design-an-isolated-sharepoint-online-team-site.md)。
  
### <a name="step-2-deploy-your-isolated-site"></a>步驟 2： 部署隔離的網站

若要部署在隔離的網站，您必須先：
  
- 決定使用者帳戶和群組新增至每個存取群組。
    
- 建立存取群組並新增使用者和群組的成員。
    
如需詳細的步驟，請參閱 ＜**階段 1**的[部署隔離的 SharePoint Online 小組網站](deploy-an-isolated-sharepoint-online-team-site.md)。
  
接下來，您可以建立的 SharePoint Online 小組網站進行這些步驟。
  
1. Office 365 入口網站也可用於管理 SharePoint Online 小組網站 （SharePoint Online 系統管理員） 帳戶登入。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在 [並排顯示] 清單中按一下 [ **SharePoint**]。
    
3. 新**SharePoint**索引標籤中的瀏覽器中，按一下 [ **+ 建立網站**]。
    
4. 在 [**建立網站**] 頁面上，按一下 [**小組網站**。
    
5. 在**站台名稱**] 中輸入私人小組網站的名稱。
    
6. 在**小組網站描述**] 中，輸入的選用描述。
    
7. **隱私權設定**] 中選取 [**私人-只有成員可以存取此站台**，然後按一下 [**下一步**。
    
8. 在**您要新增誰？** ] 窗格中，按一下 [**完成]**。
    
下一步] 從新的 SharePoint Online 小組網站，請使用下列步驟設定權限。
  
1. 決定使用者主體名稱 (UPN) 的 IT 管理員或其他負責回應及位址的網站的存取權要求的人員 （belindan@contoso.com 是 UPN 的範例）。寫入該的 UPN： ___。
    
2. 在 [工具] 列中按一下 [設定] 圖示，和 [**網站權限**。
    
3. 在 [**網站權限**] 窗格中，按一下 [**進階權限設定**。
    
4. 新**的權限**] 索引標籤上的瀏覽器中，按一下 [**存取要求設定**]。
    
5. 在 [**存取要求設定**] 對話方塊中：
    
  - 清除 [**允許成員] 共用網站和個別的檔案及資料夾**和**允許邀請其他人網站成員 」 群組的成員**] 核取方塊。
    
  - 輸入您的 IT 管理員從步驟 1 的 UPN**傳送存取的所有要求**。
    
  - 按一下 [確定]****。
    
6. 在瀏覽器的 [**權限**] 索引標籤中，按一下 [清單中的**[網站名稱] 成員**。
    
7. 在 [**人員與群組**，按一下 [**新增**]。
    
8. 在 [**共用**] 對話方塊中，輸入您的網站成員存取群組此網站的名稱、 選取它，和 [**共用**。
    
9. 按一下瀏覽器上的 [上一頁] 按鈕。
    
10. 按一下**[網站名稱] 擁有者**] 清單中。
    
11. 在 [**人員與群組**，按一下 [**新增**]。
    
12. 在 [**共用**] 對話方塊中，輸入此網站的網站管理員存取群組的名稱、 選取它，和 [**共用**。
    
13. 按一下瀏覽器上的 [上一頁] 按鈕。
    
14. 按一下**[網站名稱] 訪客**] 清單中。
    
15. 在 [**人員與群組**，按一下 [**新增**]。
    
16. 在 [**共用**] 對話方塊中，輸入此網站的網站檢視者存取群組的名稱、 選取它，和 [**共用**。
    
17. 關閉瀏覽器的 [**權限**] 索引標籤。
    
這些權限設定的結果是：
  
- **[網站名稱] 擁有者**SharePoint 群組包含網站管理員存取群組中的所有成員具有 [**完全控制**」 權限層級。
    
- **[網站名稱] 成員**SharePoint 群組包含網站成員存取群組中的所有成員具有**編輯**權限等級。
    
- **[網站名稱] 訪客**SharePoint 群組包含網站檢視者存取群組中的所有成員具有 「**讀取**」 權限等級。
    
- 邀請其他成員的成員的功能已停用。
    
- 非成員要求存取的功能已啟用。
    
以下是您產生的組態。
  
![適用於隔離 SharePoint Online 小組網站的敏感性層級保護。](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
網站透過群組成員資格之一的存取群組的成員可以現在安全地進行共同作業網站的資源。
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a>高度機密的 SharePoint Online 小組網站

高度機密的 SharePoint Online 小組網站是隔離的小組網站] 表示權限所控制透過而不是在小組網站相關聯的 Office 365 群組的成員資格的 SharePoint 群組的成員資格。
  
若要建立高度機密資訊與共同作業的隔離的小組網站，有兩個主要步驟。
  
### <a name="step-1-design-your-isolated-site"></a>步驟 1： 設計在隔離的網站

若要設計隔離的小組網站，您需要決定：
  
- 您的 SharePoint 群組和權限層級。
    
- 將您的 SharePoint 群組的成員存取群組的屬性集。
    
     存取群組的建議的設定是一個網站成員，一個網站檢視者另一個網站管理員。
    
- 您是否要使用的巢狀存取群組內的群組。
    
例如，建議的群組結構和權限層級看起來如下：
  
|**SharePoint 群組**|**權限層級**|**存取群組 （範例）**|
|:-----|:-----|:-----|
|[網站名稱]成員  <br/> |編輯  <br/> |[網站名稱]成員  <br/> |
|[網站名稱]訪客  <br/> |讀取  <br/> |[網站名稱]檢視程式  <br/> |
|[網站名稱]擁有者  <br/> |完全控制  <br/> |[網站名稱]系統管理員  <br/> |
   
小組網站的預設會建立 SharePoint 群組與權限層級。您需要確定您的存取群組的名稱。
  
如需設計程序的詳細資訊，請參閱 ＜ [Design 隔離的 SharePoint Online 小組網站](design-an-isolated-sharepoint-online-team-site.md)。
  
### <a name="step-2-deploy-your-isolated-site"></a>步驟 2： 部署隔離的網站

若要部署在隔離的網站，您必須先：
  
- 決定每個存取群組的使用者與群組成員
    
- 建立存取群組並新增使用者和群組的成員
    
- 建立使用您的存取群組隔離的小組網站
    
如需詳細的步驟，請參閱 ＜ [Deploy 隔離的 SharePoint Online 小組網站](deploy-an-isolated-sharepoint-online-team-site.md)。
  
權限設定的結果是：
  
- **[網站名稱] 擁有者**SharePoint 群組包含網站管理員存取群組中的所有成員具有 [**完全控制**」 權限層級。
    
- **[網站名稱] 成員**SharePoint 群組包含網站成員存取群組中的所有成員具有**編輯**權限等級。
    
- **[網站名稱] 訪客**SharePoint 群組包含網站檢視者存取群組中的所有成員具有 「**讀取**」 權限等級。
    
- 邀請其他成員的成員的功能已停用。
    
- 非成員要求存取的功能已停用。
    
以下是您產生的組態。
  
![適用於隔離 SharePoint Online 小組網站的高度機密層級保護。](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
網站透過群組成員資格之一的存取群組的成員可以現在安全地進行共同作業網站的資源。
  
## <a name="next-step"></a>下一步

[保護 SharePoint Online 與 Office 365 標籤和 DLP 檔案](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a>請參閱

[安全的 SharePoint Online 網站及檔案](secure-sharepoint-online-sites-and-files.md)
  
[安全的開發人員/測試環境中的 SharePoint Online 網站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)




