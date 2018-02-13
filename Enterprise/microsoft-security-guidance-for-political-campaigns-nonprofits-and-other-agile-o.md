---
title: "Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 10d1004b-42b6-4e2b-aaa2-18ddd9118f64
description: "摘要： 規劃和實作指引 fast 移動增加的威脅設定檔的組織。"
ms.openlocfilehash: 30a45cfa521c73689afa7481cbe7ba9637b97617
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a><span data-ttu-id="8450c-103">Microsoft 安全性指導政治活動、 非營利機構，以及其他靈活的組織</span><span class="sxs-lookup"><span data-stu-id="8450c-103">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>

 <span data-ttu-id="8450c-104">**摘要：**規劃及實作指導 fast 移動增加的威脅設定檔的組織。</span><span class="sxs-lookup"><span data-stu-id="8450c-104">**Summary:** Planning and implementation guidance for fast-moving organizations that have an increased threat profile.</span></span>
  
<span data-ttu-id="8450c-p101">如果您的組織很靈活、 擁有小型的 IT 小組、，您的威脅設定檔是高於平均本指南旨在協助您。此解決方案示範如何快速建立具有包含從開始安全控制項的基本雲端服務的環境。本指南包含保護資料、 身分識別、 電子郵件、 及 access 從行動裝置的規定安全性建議。</span><span class="sxs-lookup"><span data-stu-id="8450c-p101">If your organization is agile, you have a small IT team, and your threat profile is higher than average, this guidance is designed for you. This solution demonstrates how to quickly build an environment with essential cloud services that include secure controls from the start. This guidance includes prescriptive security recommendations for protecting data, identities, email, and access from mobile devices.</span></span>
  
## <a name="security-solution-guidance"></a><span data-ttu-id="8450c-108">解決方案的安全性指導</span><span class="sxs-lookup"><span data-stu-id="8450c-108">Security solution guidance</span></span>

<span data-ttu-id="8450c-p102">本指南說明如何實作安全的雲端環境。解決方案的指引可使用的任何組織。將包含靈活的組織具有 BYOD 存取和 guest 帳戶的額外協助。您可以使用為起點的這份指導來設計您自己的環境。我們在[CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com)歡迎您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="8450c-p102">This guidance describes how to implement a secure cloud environment. The solution guidance can be used by any organization. It includes extra help for agile organizations with BYOD access and guest accounts. You can use this guidance as a starting-point for designing your own environment. We welcome your feedback at [CloudAdopt@microsoft.com](mailto:CloudAdopt@microsoft.com).</span></span> 
  
|||
|:-----|:-----|
|<span data-ttu-id="8450c-114">**項目**</span><span class="sxs-lookup"><span data-stu-id="8450c-114">**Item**</span></span> <br/> |<span data-ttu-id="8450c-115">**描述**</span><span class="sxs-lookup"><span data-stu-id="8450c-115">**Description**</span></span> <br/> |
|<span data-ttu-id="8450c-116">**政治活動的 Microsoft 安全性指導**</span><span class="sxs-lookup"><span data-stu-id="8450c-116">**Microsoft Security Guidance for Political Campaigns**</span></span> <br/> <span data-ttu-id="8450c-117">[![浮動海報縮圖應該要充分設定。](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span><span class="sxs-lookup"><span data-stu-id="8450c-117">[![Thumb nail for mini poster set.](images/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)</span></span> <br/> <span data-ttu-id="8450c-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf) \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="8450c-118">[PDF](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.pdf)  \| [Visio](http://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security for political campaigns.vsdx)</span></span> <br/> |<span data-ttu-id="8450c-p103">這份指導做為範例使用政治 campaign 組織。任何環境中使用這份指導為起點。</span><span class="sxs-lookup"><span data-stu-id="8450c-p103">This guidance uses a political campaign organization as an example. Use this guidance as a starting point for any environment.</span></span>  <br/> |
|<span data-ttu-id="8450c-121">**Microsoft 安全性指導非營利機構**</span><span class="sxs-lookup"><span data-stu-id="8450c-121">**Microsoft Security Guidance for Nonprofits**</span></span> <br/> <span data-ttu-id="8450c-122">[![可下載的檔案的縮圖影像](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span><span class="sxs-lookup"><span data-stu-id="8450c-122">[![Thumnail image for downloadable file](images/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)</span></span> <br/> <span data-ttu-id="8450c-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf) \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)  </span><span class="sxs-lookup"><span data-stu-id="8450c-123">[PDF](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.pdf)  \| [Visio](http://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud Architecture_Security for Nonprofits.vsdx)</span></span> <br/> |<span data-ttu-id="8450c-p104">本指南稍微修訂非營利組織。例如，它會參照非營利 Office 365 計劃。技術指南是政治 campaign 解決方案指南相同。</span><span class="sxs-lookup"><span data-stu-id="8450c-p104">This guide is slightly revised for nonprofit organizations. For example, it references Office 365 Nonprofit plans. The technical guidance is the same as the political campaign solution guide.</span></span>  <br/> |
   
## <a name="test-lab-guides"></a><span data-ttu-id="8450c-127">測試實驗室指南</span><span class="sxs-lookup"><span data-stu-id="8450c-127">Test Lab Guides</span></span>

<span data-ttu-id="8450c-128">若要建立此解決方案的開發人員/測試環境，請使用下列測試實驗室指南：</span><span class="sxs-lookup"><span data-stu-id="8450c-128">To create a dev/test environment for this solution, use the following test lab guides:</span></span> 
  
- [<span data-ttu-id="8450c-129">設定群組及使用者政治 campaign 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8450c-129">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
    
     <span data-ttu-id="8450c-130">建立 Office 365 和 EMS 試用版訂閱，然後建立 [群組及使用者的代表性政治行銷活動。</span><span class="sxs-lookup"><span data-stu-id="8450c-130">Create trial subscriptions for Office 365 and EMS and then create groups and users for a representative political campaign.</span></span>
    
- [<span data-ttu-id="8450c-131">政治 campaign 開發/測試環境中建立小組網站</span><span class="sxs-lookup"><span data-stu-id="8450c-131">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
    
    <span data-ttu-id="8450c-132">使用內部、 私人、 機密、 和高度機密的安全性層級建立四個 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="8450c-132">Create four SharePoint Online team sites with Internal, Private, Sensitive, and Highly Confidential levels of security.</span></span>
    
<span data-ttu-id="8450c-133">示範或概念證明的其他安全性功能，請參閱[Office 365 測試實驗室指南](http://aka.ms/o365tlgs)。</span><span class="sxs-lookup"><span data-stu-id="8450c-133">For additional security features for demonstration or proof of concept, see [Office 365 Test Lab Guides](http://aka.ms/o365tlgs).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8450c-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="8450c-134">See Also</span></span>

[<span data-ttu-id="8450c-135">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="8450c-135">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="8450c-136">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="8450c-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="8450c-137">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="8450c-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



