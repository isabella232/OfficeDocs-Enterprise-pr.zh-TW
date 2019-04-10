---
title: Microsoft SaaS (Office 365) 混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 摘要： 瞭解混合式架構與案例的 Microsoft 的 SaaS 型雲端供應項目 (Office 365)。
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741389"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Microsoft SaaS (Office 365) 混合式雲端案例

 **摘要：** 了解混合式架構與案例的 Microsoft 的 SaaS 型雲端供應項目 (Office 365)。
  
合併與與其對應雲端移轉或長期的整合策略的一部分的 Office 365 中的內部部署的 Exchange、 SharePoint 或商務用 Skype。
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Microsoft SaaS 混合案例結構

圖 1 顯示 Office 365 的 Microsoft Iaas 型混合式案例的架構。
  
**圖 1: Office 365 的 Microsoft Iaas 型混合式案例**

![Office 365 的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
每個圖層的架構：
  
- 應用程式和案例
    
    有各種 SaaS 為基礎的混合式案例，對齊繞 Office Server 產品和其 Office 365 對應項目：
    
  - Exchange 伺服器組合與 Exchange Online （Exchange Server 混合式）
    
  - Skype 商務 Server 結合 Skype 商務線上和新的雲端 PBX 與雲端連接器 Edition 案例
    
  - SharePoint Server 2019、 SharePoint Server 2016 或 SharePoint Server 2013 結合使用 SharePoint Online （多個案例）
    
    另外還有 Exchange Online 與 Skype Business Server 內部部署，跨產品混合式案例。
    
- 身分識別
    
    可以包含您內部部署 Active Directory 網域服務 (AD DS) 與目錄同步處理。 或者，您可以設定 Azure AD 以使用協力廠商身分識別提供者同盟。
    
- 工作列最右邊的網路
    
    與 Microsoft Office 365 或 Dynamics 365 對等包含您現有的網際網路管道或 ExpressRoute 連線。
    
- 內部部署
    
    可以包含現有的伺服器的 Exchange、 SharePoint 和 Skype for Business，應該更新至最新的版本。 您可以結合其與 Office 365 與對應的混合式案例。
    
設定您的 Office 365 開發/測試環境，請參閱[Office 365 測試實驗室指南](cloud-adoption-test-lab-guides-tlgs.md)。
  
## <a name="skype-for-business-hybrid"></a>混合式商務用 Skype

混合式商務用 Skype 可讓您結合現有內部部署與 Skype for Business Online。 某些使用者為隸屬於內部部署和部分使用者位於線上使用，但使用者共用相同的工作階段初始通訊協定 (SIP) 網域，例如 contoso.com。 您可以使用此混合式組態移轉從內部部署到 Office 365 一段時間，在您的排程。 商務用 Skype 也可以與[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)整合。
  
**圖 2: 商務用 Skype 商務混合式組態**

![Skype 商務混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
圖 2 顯示商務用 Skype 商務混合式組態，商務前端集區與 edge 伺服器通訊與 Skype for Business Online 在 Office 365 中內部部署商務用 Skype 所組成。
  
如需詳細資訊，請參閱 <<c0>規劃 Skype for Business Server 與 Skype for Business Online 之間的混合式連線。
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>含商務用 Skype Server 的雲端 PBX

雲端 PBX 與 Skype for Business Server 可讓您轉換 Business Server 內部部署的拓樸現有商務用 Skype 內部部署公用交換電話網路 (PSTN) 連線。 
  
**圖 3: Cloud PBX 與 Skype for Business Server**

![含商務用 Skype Server 的雲端 PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
圖 3 顯示商務伺服器組態，組成內部現有的 PBX 或電信公司閘道、 Skype for Business 伺服器和 PSTN 連線至 Microsoft Cloud PBX，在 Office 365 中，其中包含商務用 Skype 用 Skype 雲端 PBX線上。
  
隸屬於雲端組織中的使用者可以從 Microsoft cloud 包含訊號和語音信箱，會收到專用交換機 (pbx) 服務，但 PSTN 連線能力 （撥號音） 透過 Enterprise Voice 提供從內部Skype 商務伺服器部署。
  
這是混合式組態，可讓您逐步移轉至雲端式服務的絕佳範例。 當您開始將它們移至 Skype for Business Online，您可以保留使用者的語音功能。 您可以移動您的使用者，在您自己的步調，了解其語音功能仍無專家所隸屬的位置。 
  
如需詳細資訊，請參閱 <<c0>規劃 Skype for Business Server 與 Skype for Business Online 之間的混合式連線。
  
如果您還沒有現有的 Lync Server 或 Skype for Business 伺服器部署，您可以使用 Skype 版商務雲端連接器，一組封裝的虛擬機器 (Vm) 中實作 Cloud pbx 的內部部署 PSTN 連線能力。
  
如需詳細資訊，請參閱 < <b0>skype for Business 雲端連接器版計劃</b0>。

  
## <a name="sharepoint-hybrid"></a>SharePoint 混合式

SharePoint 混合式結合了 Office 365 中 SharePoint Online 與內部部署 SharePoint 伺服器陣列的最佳運用這兩者的已連線的體驗。
  
**圖 4: SharePoint 混合式組態**

![SharePoint 混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
圖 4 顯示 SharePoint 混合式設定，與 Office 365 中 SharePoint Online 進行通訊的內部部署 SharePoint 伺服器陣列所組成。
  
SharePoint 混合式案例：
  
- [混合式商務用 OneDrive](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [混合式外部網路 B2B](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [混合式搜尋](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [混合式設定檔](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [混合式選擇器](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    很容易啟用混合式案例使用自動化可從 Office 365 中 SharePoint Online 系統管理中心的混合式組態精靈。
    
- [可延伸混合式 App 啟動器](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    可讓使用者檢視和使用 Office 365 影片和 Delve 應用程式和其內部部署 SharePoint 伺服器陣列的網頁中體驗。
    
所有這些 SharePoint 混合式案例中，除了可延伸混合式 app 啟動器，可供 SharePoint 2016 和 SharePoint 2013 的使用者。
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 混合式

使用 Exchange Server 2016 混合式，您可以實現 online 使用者的 Office 365 中的 Exchange Online 優勢，同時讓內部部署使用者繼續使用現有的 Exchange 伺服器基礎結構。 
  
**圖 5: Exchange 2016 混合式組態**

![Exchange 2016 混合式組態](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
圖 5 顯示 Exchange 2016 混合式組態，與 Exchange Online Protection 和 Office 365 中的信箱進行通訊的內部部署 Exchange 信箱伺服器所組成。
  
部分使用者擁有內部部署電子郵件伺服器和某些使用者使用 Exchange Online 中，但所有使用者都共用相同的電子郵件地址空間。 
  
此混合式組態：
  
- 當您移轉至 Exchange Online 一段時間，在您的排程時，會運用您現有的 Exchange 伺服器基礎結構。
    
- 可讓您沒有投資分公司的基礎結構支援遠端站台。
    
- 可讓您在 Office 365 中路由傳送到 Exchange Online Protection 的內送網際網路電子郵件。
    
- 只用來跨國子公司需要資料至位於內部部署組織的需求。
    
您也可以與其他 Microsoft Office 365 應用程式，包括 Skype for Business Online 和 SharePoint Online 整合此混合式組態。
  
如需詳細資訊，請參閱 < <b0>Exchange Server Hybrid Deployments</b0>。
  
## <a name="see-also"></a>另請參閱

[Microsoft Hybrid Cloud for Enterprise Architects](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft Cloud IT 架構資源](microsoft-cloud-it-architecture-resources.md)

