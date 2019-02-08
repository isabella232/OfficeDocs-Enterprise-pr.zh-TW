---
title: 測試實驗室指南設定整合式的 Exchange、 Lync 和 SharePoint 測試實驗室
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: 摘要： 了解如何建立包含執行 Exchange Server 2013 的伺服器、 執行 Lync Server 2013 的伺服器與執行 SharePoint Server 2013 伺服器的整合式的測試實驗室。
ms.openlocfilehash: b5d4527c063b0bfbac205007a9642b8edafd813b
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897046"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="aa9ac-103">Test Lab Guide: Configure 整合了的 Exchange、 Lync 和 SharePoint 測試實驗室</span><span class="sxs-lookup"><span data-stu-id="aa9ac-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="aa9ac-104">**摘要：** 了解如何建立包含執行 Exchange Server 2013 的伺服器、 執行 Lync Server 2013 的伺服器與執行 SharePoint Server 2013 伺服器的整合式的測試實驗室。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="aa9ac-105">**觀賞整合式的 Exchange、 Lync 和 SharePoint 測試實驗室指南概觀影片**</span><span class="sxs-lookup"><span data-stu-id="aa9ac-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="aa9ac-106">結果包含三種伺服器之間的伺服器對伺服器驗證，此設定的測試實驗室可用來建立及示範多產品案例與解決方案使用執行 Exchange Server 2013 的伺服器執行 Lync Server 2013 伺服器與執行 SharePoint Server 2013 的伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="aa9ac-107">本文件包含的指示：</span><span class="sxs-lookup"><span data-stu-id="aa9ac-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="aa9ac-108">設定 Windows Server 2012 基本設定測試實驗室。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="aa9ac-109">安裝及設定名為 SQL1 的新伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="aa9ac-110">在 SQL1 伺服器上安裝 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="aa9ac-111">安裝及設定新的用戶端電腦名為 CLIENT2。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="aa9ac-112">安裝及設定 Exchange Server 2013 EX1 上。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="aa9ac-113">安裝及設定新的伺服器名稱為 LYNC1。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="aa9ac-114">安裝 Lync Server 2013 Standard Edition 上 LYNC1。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="aa9ac-115">安裝 SharePoint Server 2013 SP1 上。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="aa9ac-116">設定 EX1、 LYNC1、 與 SP1 之間的整合。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="aa9ac-117">如需如何在 HYPER-V 中設定此測試實驗室中的資訊，請參閱[主控整合式的 Exchange、 Lync 和 SharePoint 測試實驗室與 Windows Server 2012 HYPER-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)。</span><span class="sxs-lookup"><span data-stu-id="aa9ac-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="aa9ac-118">下載測試實驗室指南</span><span class="sxs-lookup"><span data-stu-id="aa9ac-118">Download the test lab guide</span></span>

<span data-ttu-id="aa9ac-119">[測試實驗室指南： 設定整合式的 Exchange、 Lync 和 SharePoint 測試實驗室](https://go.microsoft.com/fwlink/p/?LinkId=313670)(https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="aa9ac-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aa9ac-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa9ac-120">See Also</span></span>

[<span data-ttu-id="aa9ac-121">測試實驗室指南</span><span class="sxs-lookup"><span data-stu-id="aa9ac-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




