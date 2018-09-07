---
title: 監控 Office 365 連線能力
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
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
ms.openlocfilehash: 80e1f56ed3ef7ae2e013239ac286e2a804bd9696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539916"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="858d4-105">監控 Office 365 連線能力</span><span class="sxs-lookup"><span data-stu-id="858d4-105">Office 365 connectivity limits</span></span>

<span data-ttu-id="858d4-p102">完成 Office 365 部署後，您就可以使用下列某些工具和技巧來維護 Office 365 連線能力。建議您了解官方[服務健康狀態與持續性](https://technet.microsoft.com/library/office-365-service-health.aspx)指導方針，以及[在網路緩慢的情況下使用 Office 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。也建議您取得 [Office 365 Admin App](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) 並將[商務用 Office 365 - 系統管理說明](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)加入瀏覽器書籤中。</span><span class="sxs-lookup"><span data-stu-id="858d4-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://technet.microsoft.com/library/office-365-service-health.aspx) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="858d4-109">監控 Office 365 連線能力</span><span class="sxs-lookup"><span data-stu-id="858d4-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="858d4-110">**取得 Office 365 新端點的通知**</span><span class="sxs-lookup"><span data-stu-id="858d4-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="858d4-p103">如果您[管理 Office 365 端點](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)，且想要收到新端點的發佈通知，您可以使用您最愛的 RSS 閱讀器來訂閱 RSS 摘要。這裡有[透過 Outlook 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=532416)的方法，或者您也可以[要求透過電子郵件將 RSS 摘要更新傳送給您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。</span><span class="sxs-lookup"><span data-stu-id="858d4-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="858d4-113">**使用 System Center 監控 Office 365**</span><span class="sxs-lookup"><span data-stu-id="858d4-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="858d4-p104">如果您使用 Microsoft System Center，您可以下載 [Office 365 的 System Center 管理套件](https://www.microsoft.com/download/details.aspx?id=43708)，立即開始監控 Office 365。如需詳細指導方針，請參閱管理套件操作指南，或是這篇部落格文章[使用 System Centre Operations Manager 監控 Office 365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="858d4-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="858d4-116">**監控 Azure ExpressRoute 的健康情況**</span><span class="sxs-lookup"><span data-stu-id="858d4-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="858d4-117">如果您使用 Azure ExpressRoute for Office 365 連線到 Office 365，建議您確認已同時採用 Office 365 服務健康情況儀表板並[利用 Azure 資源健康狀態減少疑難排解的時間](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)。</span><span class="sxs-lookup"><span data-stu-id="858d4-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="858d4-118">**使用 Azure AD Connect Health 搭配 AD FS**</span><span class="sxs-lookup"><span data-stu-id="858d4-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="858d4-119">如果您的 Office 365 單一登入採用 AD FS，建議您開始[使用 Azure AD Connect Health 來監控 AD FS 基礎結構](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)。</span><span class="sxs-lookup"><span data-stu-id="858d4-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="858d4-120">**透過程式設計的方式監控 Office 365**</span><span class="sxs-lookup"><span data-stu-id="858d4-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="858d4-121">請參閱 [Office 365 管理 API](https://msdn.microsoft.com/library/jj984343%28v=office.15%29.aspx) 中的指導方針。</span><span class="sxs-lookup"><span data-stu-id="858d4-121">Refer to our guidance on the [Office 365 Management API](https://msdn.microsoft.com/library/jj984343%28v=office.15%29.aspx).</span></span>  <br/> |

<span data-ttu-id="858d4-122">您可以使用下列短連結返回這裡：[hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="858d4-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="858d4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="858d4-123">See also</span></span>

[<span data-ttu-id="858d4-124">設定 Office 365 企業版服務和應用程式</span><span class="sxs-lookup"><span data-stu-id="858d4-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="858d4-125">準備讓您的組織使用 Office 365 企業版</span><span class="sxs-lookup"><span data-stu-id="858d4-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="858d4-126">Office 365 的網路規劃和效能調整</span><span class="sxs-lookup"><span data-stu-id="858d4-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
<span data-ttu-id="858d4-127">[Office 365 與內部部署環境整合](office-365-integration.md)</span><span class="sxs-lookup"><span data-stu-id="858d4-127">Your existing active directory [Office 365 integration with on-premises environments](office-365-integration.md) or</span></span>
  
[<span data-ttu-id="858d4-128">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="858d4-128">Office 365 Germany endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
