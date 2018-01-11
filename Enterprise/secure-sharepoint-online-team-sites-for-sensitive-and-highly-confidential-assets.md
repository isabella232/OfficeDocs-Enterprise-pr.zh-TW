---
title: "保護敏感和最高機密資產的 SharePoint Online 小組網站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "摘要： 如何 Contoso 變得容易實作機密保護和高度機密的 SharePoint Online 的小組網站，尚未安全、 高階主管的共同作業和其參考資料中心。"
ms.openlocfilehash: 062238bd301200e388ba9d4f6d24503d33046f50
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>保護敏感和最高機密資產的 SharePoint Online 小組網站

 **摘要：**如何實作的 Contoso 機密保護和高度機密 SharePoint Online 小組高階主管和其參考資料中心的更容易，尚未安全共同作業的網站。
  
Contoso executive 領導想要使用 Office 365 和其檔案儲存在單一位置進行共同作業，不論可能主管。同樣地，Contoso 的研究 （英文） 部門 — 搭配中 Paris、 莫斯科、 紐約、 北京及班加羅爾部門 — 想要轉換至更輕鬆地存取與更多 open 共同作業雲端其內部部署數位資產跨小組。
  
不過，在兩個這種情況下，這些資源的存取權必須受限的人員，他們可以檢視或變更，以進行中的權限由 IT 人員管理網站的子集。此外，即使一些資源有意或無意分散式，他們必須加密且可防止使用者可以使用沒有權限來檢視或變更其內容的權限。
  
安全性與 SharePoint 管理員可以在 Contoso 的 IT 部門決定要使用機密保護和高度機密的 SharePoint Online 小組網站，如圖 1 所示。
  
**圖 1： 比較的機密保護和高度機密的 SharePoint Online 小組網站**

![敏感性保護和高度機密的 SharePoint Online 小組網站](images/Contoso_Poster/SP_Solution.png)
  
Contoso 為其行政人員及的研究小組建立安全的 SharePoint Online 小組網站使用下列步驟：
  
1. 建立**高階主管**機密 SharePoint Online 小組網站
    
    新的小組網站的編輯 SharePoint 權限層級與 SharePoint 系統管理員帳戶一小群為完全控制 」 權限等級的擁有者的成員身分的高階主管使用現有的 Azure Active Directory (AD) 群組。
    
2. 移轉高階主管檔案
    
    將現有的內部部署 executive 檔案及資料夾移至新的高階主管 SharePoint Online 小組網站。
    
3. 建立**[參考資料**高度機密 SharePoint Online 小組網站
    
    新的小組網站會使用現有的 Azure AD 研究小組群組做為完全控制 」 權限等級的擁有者的編輯權限等級與 SharePoint 系統管理員帳戶一小群成員。指派給研究檔案 AIP 標籤確保他們會加密和只有研究 （英文） 群組的成員可以開啟它們。
    
4. 移轉參考資料檔案
    
    將現有的研究小組內部檔案及資料夾至新的研究 SharePoint Online 小組網站。
    
結果是兩個共同作業網站的安全性與 SharePoint 管理員緊密控制其存取。具有高度機密 AIP 標籤檔案，即使其分散外研究小組網站上，會加密且只可以開啟由的研究小組成員。
  
如需詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)。
  
 若要將此以為示範、 概念證明或開發人員/測試，請參閱 ＜[保護 SharePoint Online 開發人員/測試環境中的網站](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)。
  
## <a name="see-also"></a>請參閱

[Contoso Corporation 的企業案例](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft Cloud 中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

[伸展資料庫](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源](https://sway.com/FJ2xsyWtkJc2taRD)




