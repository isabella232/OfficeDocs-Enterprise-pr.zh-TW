---
title: Office 365 的網路規劃和效能調整
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
description: 可協助您規劃 Microsoft Office 365 的網路頻寬需求。 一旦您部署後，請回到這裡來微調，並疑難排解 Office 365 的效能。
ms.openlocfilehash: c7ea169fbb39a16612c957f0d0275de60c83de1e
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616736"
---
# <a name="network-planning-and-performance-tuning-for-office-365"></a>Office 365 的網路規劃和效能調整
在首次部署或移轉至 Office 365 前，您可使用這些主題中的資訊來預估所需頻寬，然後測試並確認您有足夠的頻寬以部署或移轉至 Office 365。 如需概觀，請參閱 [Office 365 的網路和移轉規劃](network-and-migration-planning.md)。
  
|||||
|:-----|:-----|:-----|:-----|
|**網路規劃** <br/> ![網路](media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |想要加快連線速度和頁面的載入速度嗎？  <br/> 請參閱[在 Office 365 中獲得最佳連線及效能](https://aka.ms/o365perfprinciples) (英文) <br/> 請參閱 [Office 365 網路連線概觀](https://docs.microsoft.com/en-us/office365/enterprise/office-365-networking-overview) (部分機器翻譯) 以了解概念。  <br/> |**測量您的網路** <br/> ![計算器](media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |請參閱[使用基準與效能歷程記錄調整 Office 365 效能](performance-tuning-using-baselines-and-history.md) (部分機器翻譯)，以及 [Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md) (部分機器翻譯)。  <br/> 使用這些工具來[評估您現有的網路](network-and-migration-planning.md#calculators)。  <br/> |
|**最佳作法** <br/> ![最佳作法](media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[Office 365 的網路規劃和移轉效能改善最佳作法](network-and-migration-planning.md#BestPractices)。 想立即開始協助您的使用者嗎？ 參閱[在網路緩慢的情況下使用 Office 365 的最佳作法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) (機器翻譯)。  <br/> [Office 365 網路連線能力原則](https://aka.ms/o365networkingprinciples) (機器翻譯) 將會協助您了解關於安全最佳化 Office 365 網路連線的最新指引。  <br/> |**參照** <br/> ![書籍或期刊](media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |想要如 IP 位址和連接埠清單的詳細資料嗎？ 請參閱 [Office 365 的網路規劃參考](network-and-migration-planning.md#NetReference)。  <br/> |
|![請參閱適用於企業架構的 Microsoft 雲端網路海報](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |如需了解針對 Office 365 和其他 Microsoft 雲端平台及服務最佳化網路的步驟，請參閱[適用於企業架構的 Microsoft 雲端網路](https://aka.ms/cloudarchnetworking)海報。  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-office-365"></a>Office 365 的效能調整和疑難排解資源
<a name="apptuning"> </a>

一旦部署了 Office 365，您就可以使用本節中的主題將效能最佳化。 若遇到效能降低情形，您也可以使用這些主題來疑難排解問題。
  
 **[調整 Office 365 效能](tune-office-365-performance.md)**：如需有關搭配 Office 365 使用網路位址轉譯的資訊，請參閱 [Office 365 的 NAT 支援](nat-support-with-office-365.md) (部分機器翻譯)。 也請參閱 Paul Collinge 的 [最佳化及疑難排解 Office 365 網路連線的十大祕訣](https://blogs.technet.com/b/onthewire/archive/2014/06/18/top-10-tips-for-optimising-amp-troubleshooting-your-office-365-network-connectivity.aspx) (英文)。 
  
 **[調整 Exchange Online 的效能](tune-exchange-online-performance.md)**：使用這些文章的資訊，微調 Exchange Online 的效能。 
  
 **[調整商務用 Skype Online 的效能](tune-skype-for-business-online-performance.md)**：使用這些文章的資訊，微調商務用 Skype Online 的效能。 
  
 **[調整 SharePoint Online 的效能](tune-sharepoint-online-performance.md)**：使用這些文章的資訊，微調 SharePoint Online 的效能。 
  
 **[調整 Project Online 的效能](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**：使用這些文章的資訊，微調 Project Online 的效能。 
  

