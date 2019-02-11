---
title: 使用雲端採用測試實驗室指南 (TLG) 測試 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/23/2018
ms.audience: ITPro
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
description: 摘要：使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365、Dynamics 365 和 Office Server 產品的展示版本、概念證明或開發/測試環境。
ms.openlocfilehash: df4729c93f3665bdfe072102f2952d7432ad22f0
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897236"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="e70f6-103">使用雲端採用測試實驗室指南 (TLG) 測試 Office 365</span><span class="sxs-lookup"><span data-stu-id="e70f6-103">Test Office 365 with cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="e70f6-104">**摘要：** 使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365、Dynamics 365 和 Office Server 產品的展示版本、概念證明或開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="e70f6-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration, proof of concept, or dev/test environments for Office 365, Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="e70f6-p101">TLG 可協助您快速學習 Microsoft 各項產品。它們非常適合在決定是否適合您使用或將其推廣給使用者之前，用來評估技術或組態的情況。「我自己建置它且可以運作」的實際經驗有助您了解新產品或解決方案的部署需求，因此您可以更妥善地規劃在生產環境中進行裝載。</span><span class="sxs-lookup"><span data-stu-id="e70f6-p101">TLGs help you quickly learn about Microsoft products. They're great for situations where you need to evaluate a technology or configuration before you decide whether it's right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="e70f6-108">TLG 也會針對應用程式開發和測試建立具有代表性的環境，亦稱為開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="e70f6-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="e70f6-110">請在深入之前參閱這些額外資源：</span><span class="sxs-lookup"><span data-stu-id="e70f6-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="e70f6-111">檢視[使用雲端採用測試實驗室指南來體驗 Microsoft Cloud](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy 工作階段 (只要 22 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="e70f6-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="e70f6-112">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="e70f6-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="e70f6-113">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-113">Office 365 dev/test environment</span></span>

<span data-ttu-id="e70f6-114">使用這些文章來建置您的 Office 365 開發/測試環境︰</span><span class="sxs-lookup"><span data-stu-id="e70f6-114">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="e70f6-115">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-115">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-p102">建立在 Microsoft Azure 基礎結構服務中執行的簡化內部網路。如果您想要建置模擬的企業組態，這是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="e70f6-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="e70f6-118">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-118">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-119">建立 Office 365 企業版 E5 試用訂閱，該訂閱可從您的電腦，或從在 Azure 基礎結構服務中執行的簡化內部網路來建立。</span><span class="sxs-lookup"><span data-stu-id="e70f6-119">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="e70f6-120">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="e70f6-120">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-p103">安裝和設定 Azure AD Connect 以進行目錄同步作業及密碼同步化。如果您想要建置模擬的企業組態，這是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="e70f6-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="e70f6-123">針對 Office 365 開發/測試環境，使用這些文章來示範 Office 365 的企業版功能︰</span><span class="sxs-lookup"><span data-stu-id="e70f6-123">For your Office 365 dev/test environment, use these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="e70f6-124">適用於您的 Office 365 開發/測試環境的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="e70f6-124">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-125">使用傳送至您智慧型手機的簡訊為您的 Office 365 訂閱帳戶設定並測試次要驗證。</span><span class="sxs-lookup"><span data-stu-id="e70f6-125">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="e70f6-126">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="e70f6-126">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-127">以 Windows Server Active Directory 網域的帳戶設定並示範同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="e70f6-127">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="e70f6-128">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="e70f6-128">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-129">設定並示範 Office 365 雲端應用程式安全性，它可讓您建立原則來監視並通知 Office 365 訂閱中的可疑活動。</span><span class="sxs-lookup"><span data-stu-id="e70f6-129">Configure and demonstrate Office 365 Cloud App Security, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="e70f6-130">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="e70f6-130">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-131">設定並示範進階威脅防護，這是 Exchange Online Protection (EOP) 的一個功能，可協助防止惡意軟體攻擊您的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="e70f6-131">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="e70f6-132">適用於 Office 365 開發/測試環境的進階電子文件探索</span><span class="sxs-lookup"><span data-stu-id="e70f6-132">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-133">新增範例資料並示範進階電子文件探索，它可讓您快速地尋找和分析 Office 365 中儲存的資料，包括電子郵件和文件。</span><span class="sxs-lookup"><span data-stu-id="e70f6-133">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="e70f6-134">Office 365 開發/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="e70f6-134">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-135">示範如何使用 Office 365 資訊版權管理保護機密文件中的資料，即使資料不小心張貼在錯誤的文件資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e70f6-135">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="e70f6-136">Office 365 開發/測試環境中的資料分類和標示</span><span class="sxs-lookup"><span data-stu-id="e70f6-136">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-137">示範 Azure 資訊保護 (AIP) 用戶端如何用來分類不同安全性等級的文件。</span><span class="sxs-lookup"><span data-stu-id="e70f6-137">Demonstrate how the Azure Information Protection (AIP) client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="e70f6-138">獨立的 SharePoint Online 小組網站開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-138">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-139">示範如何建立 SharePoint Online 小組網站，該網站針對高度機密的資源，獨立於組織的其他網站。</span><span class="sxs-lookup"><span data-stu-id="e70f6-139">Demonstrate how to create a SharePoint Online team site that is isolated from the rest of the organization for sensitive or highly confidential resources.</span></span>
    
## <a name="the-microsoft-365-enterprise-test-environment"></a><span data-ttu-id="e70f6-140">Microsoft 365 企業版測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-140">The Microsoft 365 Enterprise test environment</span></span>

<span data-ttu-id="e70f6-141">使用[以下文章](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)，建立 [Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365-enterprise/)的測試環境。</span><span class="sxs-lookup"><span data-stu-id="e70f6-141">Create a test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) with [these articles](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).</span></span>
 
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="e70f6-142">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-142">Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="e70f6-143">透過這些文章，新增 Dynamics 365 試用版訂閱，並測試 Office 365 和 Dynamics 365 整合式功能與案例︰</span><span class="sxs-lookup"><span data-stu-id="e70f6-143">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="e70f6-144">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-144">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="e70f6-145">將 Dynamics 365 試用版訂閱以及 Dynamics 365 授權和權限新增至您的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e70f6-145">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="e70f6-146">適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合</span><span class="sxs-lookup"><span data-stu-id="e70f6-146">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="e70f6-147">設定然後示範 Office 365 與 Dynamics 365 如何在 Exchange Online 信箱中共同運作。</span><span class="sxs-lookup"><span data-stu-id="e70f6-147">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="e70f6-148">One Microsoft Cloud 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-148">The One Microsoft Cloud dev/test environment</span></span>

<span data-ttu-id="e70f6-p104">建立開發/測試環境，其中包含所有 Microsoft 的雲端供應項目：Office 365、Azure、EMS 及 Dynamics 365。請參閱 [One Microsoft Cloud 開發/測試環境](the-one-microsoft-cloud-dev-test-environment.md)以取得逐步指示。</span><span class="sxs-lookup"><span data-stu-id="e70f6-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="e70f6-151">模擬的跨單位部署開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-151">Simulated cross-premises dev/test environments</span></span>

<span data-ttu-id="e70f6-152">透過這些文章，您可以建立一個跨單位部署開發/測試環境，它包含 Azure 虛擬網路和模擬的內部部署網路︰</span><span class="sxs-lookup"><span data-stu-id="e70f6-152">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="e70f6-153">Azure 中模擬的跨單位部署虛擬網路</span><span class="sxs-lookup"><span data-stu-id="e70f6-153">Simulated cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="e70f6-154">在混合雲端組態中，建立連線到 Azure 虛擬網路的模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="e70f6-154">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="e70f6-155">Azure 開發/測試環境中的內部網路 SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="e70f6-155">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="e70f6-156">在 Azure 虛擬網路中建立單一伺服器 SharePoint Server 2016 陣列，並從模擬的內部部署網路測試連線能力和管理。</span><span class="sxs-lookup"><span data-stu-id="e70f6-156">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="e70f6-157">其他雲端式開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-157">Additional cloud-based dev/test environments</span></span>

<span data-ttu-id="e70f6-158">以下是您可以在 Azure 基礎結構服務中建立的其他雲端式開發/測試環境︰</span><span class="sxs-lookup"><span data-stu-id="e70f6-158">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="e70f6-159">Azure 中的 SharePoint Server 2016 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-159">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="e70f6-160">在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="e70f6-160">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="e70f6-161">Azure 中的 Exchange 2016 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-161">Exchange 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="e70f6-162">在 Azure 基礎結構服務中建置單一的 Exchange 2016 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e70f6-162">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="e70f6-163">Azure 中的 SharePoint Server 2013 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e70f6-163">SharePoint Server 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="e70f6-164">在 Azure 基礎結構服務中建置基本和高可用性的 SharePoint Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="e70f6-164">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e70f6-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e70f6-165">See Also</span></span>

[<span data-ttu-id="e70f6-166">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="e70f6-166">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="e70f6-167">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="e70f6-167">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="e70f6-168">適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型</span><span class="sxs-lookup"><span data-stu-id="e70f6-168">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="e70f6-169">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="e70f6-169">Hybrid solutions</span></span>](hybrid-solutions.md)


