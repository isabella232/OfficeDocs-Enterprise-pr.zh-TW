---
title: 使用雲端採用測試實驗室指南 (TLG) 測試 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 摘要：使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365 的展示版本、概念證明或開發/測試環境。
ms.openlocfilehash: a61716ae34d8dbe3f710696570c46cefd0f4aa4c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068139"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="d119e-103">使用雲端採用測試實驗室指南 (TLG) 測試 Office 365</span><span class="sxs-lookup"><span data-stu-id="d119e-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="d119e-104">**摘要：** 使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365 的展示版本、概念證明或開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="d119e-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365.</span></span>
  
<span data-ttu-id="d119e-p101">TLG 可協助您快速學習 Microsoft 各項產品。它們非常適合在決定是否適合您，以及在開始設計、規劃和推出給使用者使用之前，用來評估技術或組態的情況。「我自己建置它且可以運作」的實際經驗有助您了解新產品或解決方案的部署需求，因此您可以更妥善地規劃在生產環境中進行裝載。</span><span class="sxs-lookup"><span data-stu-id="d119e-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you and before you begin the design, planning, and rollout to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="d119e-108">TLG 也會針對應用程式開發和測試建立具有代表性的環境，亦稱為開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="d119e-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="d119e-110">按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="d119e-110">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="d119e-111">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-111">Office 365 dev/test environment</span></span>

<span data-ttu-id="d119e-112">使用這些文章來建置您的 Office 365 開發/測試環境︰</span><span class="sxs-lookup"><span data-stu-id="d119e-112">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="d119e-113">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-113">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="d119e-p102">建立在 Microsoft Azure 基礎結構服務中執行的簡化內部網路。如果您想要建置模擬的企業組態，這是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="d119e-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="d119e-116">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-116">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-117">建立 Office 365 企業版 E5 試用訂閱，該訂閱可從您的電腦，或從在 Azure 基礎結構服務中執行的簡化內部網路來建立。</span><span class="sxs-lookup"><span data-stu-id="d119e-117">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="d119e-118">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="d119e-118">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-p103">安裝和設定 Azure AD Connect 以進行目錄同步作業及密碼雜湊同步化。如果您想要建置模擬的企業組態，這是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="d119e-p103">Install and configure Azure AD Connect for directory synchronization with password hash synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="d119e-121">針對 Office 365 開發/測試環境，使用這些文章來示範 Office 365 的企業版功能︰</span><span class="sxs-lookup"><span data-stu-id="d119e-121">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="d119e-122">適用於您的 Office 365 開發/測試環境的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="d119e-122">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-123">使用傳送至您智慧型手機的簡訊為您的 Office 365 訂閱帳戶設定並測試次要驗證。</span><span class="sxs-lookup"><span data-stu-id="d119e-123">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="d119e-124">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="d119e-124">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-125">使用 Active Directory Domain Services (AD DS) 網域的帳戶設定並示範同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="d119e-125">Configure and demonstrate federated authentication with the accounts of an Active Directory Domain Services (AD DS) domain.</span></span>
    
- [<span data-ttu-id="d119e-126">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="d119e-126">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-127">設定並示範 Office 365 雲端應用程式安全性，它可讓您建立原則來監視並通知 Office 365 訂閱中的可疑活動。</span><span class="sxs-lookup"><span data-stu-id="d119e-127">Configure and demonstrate Office 365 Cloud App Security, which lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="d119e-128">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="d119e-128">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-129">設定並示範進階威脅防護，這是 Exchange Online Protection (EOP) 的一個功能，可協助防止惡意軟體攻擊您的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="d119e-129">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="d119e-130">適用於 Office 365 開發/測試環境的進階電子文件探索</span><span class="sxs-lookup"><span data-stu-id="d119e-130">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-131">新增範例資料並示範進階電子文件探索，它可讓您快速地尋找和分析 Office 365 中儲存的資料，包括電子郵件和文件。</span><span class="sxs-lookup"><span data-stu-id="d119e-131">Add example data and demonstrate Advanced eDiscovery, which lets you quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="d119e-132">Office 365 開發/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="d119e-132">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-133">示範如何使用 Office 365 資訊版權管理保護機密文件中的資料，即使資料不小心張貼在錯誤的文件資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d119e-133">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="d119e-134">Office 365 開發/測試環境中的資料分類和標示</span><span class="sxs-lookup"><span data-stu-id="d119e-134">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="d119e-135">示範 Azure 資訊保護用戶端如何用來分類不同安全性等級的文件。</span><span class="sxs-lookup"><span data-stu-id="d119e-135">Demonstrate how the Azure Information Protection client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="d119e-136">獨立的 SharePoint Online 小組網站開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-136">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="d119e-137">示範如何建立 SharePoint Online 小組網站，該網站針對高度機密的資源，獨立於組織的其他網站。</span><span class="sxs-lookup"><span data-stu-id="d119e-137">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    

## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="d119e-138">模擬的跨單位部署開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-138">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="d119e-139">透過這些文章，您可以建立一個跨單位部署開發/測試環境，它包含 Azure 虛擬網路和模擬的內部部署網路︰</span><span class="sxs-lookup"><span data-stu-id="d119e-139">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="d119e-140">Azure 中模擬的跨單位部署虛擬網路</span><span class="sxs-lookup"><span data-stu-id="d119e-140">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="d119e-141">在混合雲端組態中，建立連線到 Azure 虛擬網路的模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="d119e-141">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="d119e-142">Azure 開發/測試環境中的內部網路 SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="d119e-142">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="d119e-143">在 Azure 虛擬網路中建立單一伺服器 SharePoint Server 2016 陣列，並從模擬的內部部署網路測試連線能力和管理。</span><span class="sxs-lookup"><span data-stu-id="d119e-143">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="sharepoint-server-2016-devtest-environments"></a><span data-ttu-id="d119e-144">SharePoint Server 2016 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-144">SharePoint Server 2016 dev/test environments</span></span>

<span data-ttu-id="d119e-145">以下是您可以在 Azure 基礎結構服務中建立的 SharePoint Server 2016 開發/測試環境︰</span><span class="sxs-lookup"><span data-stu-id="d119e-145">Here are SharePoint Server 2016 dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="d119e-146">Azure 中的 SharePoint Server 2016 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-146">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    <span data-ttu-id="d119e-147">在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="d119e-147">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>

- [<span data-ttu-id="d119e-148">Azure 開發/測試環境中的內部網路 SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="d119e-148">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    <span data-ttu-id="d119e-149">在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列並從模擬的內部網路存取。</span><span class="sxs-lookup"><span data-stu-id="d119e-149">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services and access it from a simulated intranet.</span></span>


## <a name="the-microsoft-365-enterprise-devtest-environments"></a><span data-ttu-id="d119e-150">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="d119e-150">The Microsoft 365 Enterprise dev/test environments</span></span>

<span data-ttu-id="d119e-151">使用[以下文章](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)，建立 [Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365-enterprise/)的開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="d119e-151">Create dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) with [these articles](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="d119e-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d119e-152">See Also</span></span>

[<span data-ttu-id="d119e-153">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="d119e-153">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="d119e-154">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="d119e-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="d119e-155">適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型</span><span class="sxs-lookup"><span data-stu-id="d119e-155">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="d119e-156">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="d119e-156">Hybrid solutions</span></span>](hybrid-solutions.md)
