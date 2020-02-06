---
title: 監控 Office 365 連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: 完成 Office 365 部署後，您就可以使用下列某些工具和技巧來維護 Office 365 連線能力。建議您了解官方服務健康狀態與持續性指導方針，以及在網路緩慢的情況下使用 Office 365 的最佳做法。也建議您取得 Office 365 Admin App 並將商務用 Office 365 - 系統管理說明加入瀏覽器書籤中。
ms.openlocfilehash: 93fbc9448ce25ef3d5d3f1d577c6d1c23ae4472a
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721964"
---
# <a name="monitor-office-365-connectivity"></a>監控 Office 365 連線能力

完成 Office 365 部署後，您就可以使用下列某些工具和技巧來維護 Office 365 連線能力。建議您了解官方[服務健康狀態與持續性](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)指導方針，以及[在網路緩慢的情況下使用 Office 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。也建議您取得 [Office 365 Admin App](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) 並將[商務用 Office 365 - 系統管理說明](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)加入瀏覽器書籤中。
  
## <a name="monitoring-office-365-connectivity"></a>監控 Office 365 連線能力

|||
|:-----|:-----|
|**取得 Office 365 新端點的通知** <br/> |如果您[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)，且想要收到新端點的發佈通知，您可以使用您最愛的 RSS 閱讀器來訂閱 RSS 摘要。這裡有[透過 Outlook 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=532416)的方法，或者您也可以[要求透過電子郵件將 RSS 摘要更新傳送給您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。<br/> |
|**使用 System Center 監控 Office 365** <br/> |如果您使用 Microsoft System Center，您可以下載 [Office 365 的 System Center 管理套件](https://www.microsoft.com/download/details.aspx?id=43708)，立即開始監控 Office 365。如需詳細指導方針，請參閱管理套件操作指南，或是這篇部落格文章[使用 System Centre Operations Manager 監控 Office 365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)。 <br/> |
|**監控 Azure ExpressRoute 的健康情況** <br/> |如果您使用 Azure ExpressRoute for Office 365 連線到 Office 365，建議您確認已同時採用 Office 365 服務健康情況儀表板並[利用 Azure 資源健康狀態減少疑難排解的時間](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)。 <br/> |
|**使用 Azure AD Connect Health 搭配 AD FS** <br/> |如果您的 Office 365 單一登入採用 AD FS，建議您開始[使用 Azure AD Connect Health 來監控 AD FS 基礎結構](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)。  <br/> |
|**透過程式設計的方式監控 Office 365** <br/> |請參閱 [Office 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) 中的指導方針。  <br/> |

您可以使用下列短連結返回這裡：[https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>另請參閱

[設定 Office 365 企業版服務和應用程式](configure-services-and-applications.md)
  
[準備讓您的組織使用 Office 365 企業版](get-your-organization-ready-for-office-365.md)
  
[Office 365 的網路規劃和效能調整](network-planning-and-performance.md)
  
[Office 365 與內部部署環境整合](office-365-integration.md)
  
[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
