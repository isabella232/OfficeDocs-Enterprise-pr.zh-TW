---
title: 雲端採用測試實驗室指南 (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 摘要：使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365 和 Office Server 產品的展示版本、概念證明或開發/測試環境。
ms.openlocfilehash: 87e9be912b7e53dea07915ae236b057273285718
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a><span data-ttu-id="8ce1b-103">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="8ce1b-103">Cloud adoption Test Lab Guides (TLGs)</span></span>

 <span data-ttu-id="8ce1b-104">**摘要：**使用這些雲端採用測試實驗室指南 (TLG) 以設定 Office 365、Enterprise Mobility + Security (EMS)、Dynamics 365 和 Office Server 產品的展示版本、概念證明或開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-104">**Summary:** Use these cloud adoption Test Lab Guides (TLGs) to set up demonstration or dev/test environments for Office 365, the Enterprise Mobility Suite (EMS), Dynamics 365, and Office Server products.</span></span>
  
<span data-ttu-id="8ce1b-p101">TLG 可協助您快速學習 Microsoft 各項產品。它們非常適合在決定是否適合您使用或將其推廣給使用者之前，用來評估技術或組態的情況。「我自己建置它且可以運作」的實際經驗有助您了解新產品或解決方案的部署需求，因此您可以更妥善地規劃在生產環境中進行裝載。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p101">TLGs help you quickly learn about Microsoft products. They’re great for situations where you need to evaluate a technology or configuration before you decide whether it’s right for you or before you roll it out to users. The "I built it out myself and it works" hands-on experience helps you understand the deployment requirements of a new product or solution so you can better plan for hosting it in production.</span></span>
  
<span data-ttu-id="8ce1b-108">TLG 也會針對應用程式開發和測試建立具有代表性的環境，亦稱為開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-108">TLGs also create representative environments for development and testing of applications, also known as dev/test environments.</span></span>
  
![Microsoft Cloud 中的測試實驗室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
<span data-ttu-id="8ce1b-110">請在深入之前參閱這些額外資源：</span><span class="sxs-lookup"><span data-stu-id="8ce1b-110">See these additional resources before diving in:</span></span>
  
- <span data-ttu-id="8ce1b-111">檢視[使用雲端採用測試實驗室指南來體驗 Microsoft Cloud](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy 工作階段 (只要 22 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-111">View the [Experience the Microsoft Cloud with Cloud Adoption Test Lab Guides](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) Microsoft Virtual Academy session (only 22 minutes).</span></span>
    
- <span data-ttu-id="8ce1b-112">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-112">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="office-365-devtest-environment"></a><span data-ttu-id="8ce1b-113">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-113">Office 365 dev/test environment</span></span>
<span data-ttu-id="8ce1b-114"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-114"></span></span>

<span data-ttu-id="8ce1b-115">使用這些文章來建置您的 Office 365 開發/測試環境︰</span><span class="sxs-lookup"><span data-stu-id="8ce1b-115">Use these articles to build your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="8ce1b-116">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-116">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-p102">建立在 Microsoft Azure 基礎結構服務中執行的簡化內部網路。如果您想要建置模擬的企業組態，這是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p102">Create a simplified intranet running in Microsoft Azure infrastructure services. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
- [<span data-ttu-id="8ce1b-119">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-119">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-120">建立 Office 365 企業版 E5 試用訂閱，該訂閱可從您的電腦，或從在 Azure 基礎結構服務中執行的簡化內部網路來建立。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-120">Create an Office 365 Enterprise E5 trial subscription, which you can do from your computer or from  a simplified intranet running in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="8ce1b-121">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="8ce1b-121">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-p103">安裝和設定 Azure AD Connect 以進行目錄同步作業及密碼同步化。如果您想要建置模擬的企業組態，這是選擇性的步驟。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p103">Install and configure Azure AD Connect for directory synchronization with password synchronization. This is an optional step if you want to build a simulated enterprise configuration.</span></span>
    
<span data-ttu-id="8ce1b-124">針對 Office 365 開發/測試環境，使用這些文章來示範 Office 365 的企業版功能︰</span><span class="sxs-lookup"><span data-stu-id="8ce1b-124">For your Office 365 dev/test environment, uses these articles to demonstrate enterprise features of Office 365:</span></span>
  
- [<span data-ttu-id="8ce1b-125">適用於您的 Office 365 開發/測試環境的多重要素驗證</span><span class="sxs-lookup"><span data-stu-id="8ce1b-125">DirSync for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-126">使用傳送至您智慧型手機的簡訊為您的 Office 365 訂閱帳戶設定並測試次要驗證。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-126">Configure and test secondary authentication using a text message sent to your smart phone for an account in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="8ce1b-127">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="8ce1b-127">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-128">以 Windows Server Active Directory 網域的帳戶設定並示範同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-128">Configure and demonstrate federated authentication with the accounts of a Windows Server Active Directory domain.</span></span>
    
- [<span data-ttu-id="8ce1b-129">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="8ce1b-129">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-130">設定並示範 Office 365 雲端 App 安全性，它可讓您建立原則來監視並通知 Office 365 訂閱中的可疑活動。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-130">Configure and demonstrate Advanced Security Management, which allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription.</span></span>
    
- [<span data-ttu-id="8ce1b-131">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="8ce1b-131">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-132">設定並示範進階威脅防護，這是 Exchange Online Protection (EOP) 的一個功能，可協助防止惡意軟體攻擊您的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-132">Configure and demonstrate Advanced Threat Protection, which is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span>
    
- [<span data-ttu-id="8ce1b-133">適用於 Office 365 開發/測試環境的進階電子文件探索</span><span class="sxs-lookup"><span data-stu-id="8ce1b-133">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-134">新增範例資料並示範進階電子文件探索，它可讓您快速地尋找和分析 Office 365 中儲存的資料，包括電子郵件和文件。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-134">Add example data and demonstrate Advanced eDiscovery, which allows you to quickly find and analyze the data that is stored in Office 365, including email and documents.</span></span>
    
- [<span data-ttu-id="8ce1b-135">Office 365 開發/測試環境中的機密檔案保護</span><span class="sxs-lookup"><span data-stu-id="8ce1b-135">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-136">示範如何使用 Office 365 資訊版權管理保護機密文件中的資料，即使資料不小心張貼在錯誤的文件資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-136">Demonstrate how you can use Office 365 Information Rights Management to protect the data in sensitive documents, even when they are accidentally posted in the wrong document folders.</span></span>
    
- [<span data-ttu-id="8ce1b-137">Office 365 開發/測試環境中的資料分類和標示</span><span class="sxs-lookup"><span data-stu-id="8ce1b-137">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-138">示範 Azure 資訊保護 (AIP) 用戶端如何用來分類不同安全性等級的文件。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-138">Demonstrate how the Azure Information Protection client can be used to classify documents with various levels of security.</span></span>
    
- [<span data-ttu-id="8ce1b-139">獨立的 SharePoint Online 小組網站開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-139">Isolated SharePoint Online team site in your Office 365 dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-140">示範如何建立 SharePoint Online 小組網站，該網站針對高度機密的資源，獨立於組織的其他網站。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-140">Demonstrate how to create a SharePoint Online Group site that is isolated from the rest of the organization.</span></span>
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="8ce1b-141">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-141">The Microsoft 365 Enterprise dev/test environment</span></span>
<span data-ttu-id="8ce1b-142"><a name="O365"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-142"></span></span>

<span data-ttu-id="8ce1b-143">使用以下文章，建立 [Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365-enterprise/)案例的開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-143">Create a dev/test environment for [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) scenarios with these articles:</span></span>
  
- [<span data-ttu-id="8ce1b-144">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-144">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-145">建立包含 Office 365 E5、EMS E5 及在 Windows 10 企業版上執行之電腦的初始環境。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-145">Create the initial environment that includes Office 365 E5, EMS E5, and a computer running Windows 10 Enterprise.</span></span>
    
- [<span data-ttu-id="8ce1b-146">Microsoft 365 企業版開發/測試環境的 MAM 原則</span><span class="sxs-lookup"><span data-stu-id="8ce1b-146">MAM policies for your Office 365 and EMS dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-147">建立使用者群組和適用於 iOS 和 Android 裝置的行動應用程式管理 (MAM) 原則。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-147">Create user groups and mobile application management (MAM) policies for ioS and Android devices.</span></span>
    
- [<span data-ttu-id="8ce1b-148">在您的 Microsoft 365 企業版開發/測試環境中註冊 iOS 和 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="8ce1b-148">Enroll iOS and Android devices in your Office 365 and EMS dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    <span data-ttu-id="8ce1b-149">註冊 iOS 或 Android 裝置並從遠端管理。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-149">Enroll iOS or Android devices and manage them remotely.</span></span>
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="8ce1b-150">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-150">Office 365 and Dynamics 365 dev/test environment</span></span>
<span data-ttu-id="8ce1b-151"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-151"></span></span>

<span data-ttu-id="8ce1b-152">透過這些文章，新增 Dynamics 365 試用版訂閱，並測試 Office 365 和 Dynamics 365 整合式功能與案例︰</span><span class="sxs-lookup"><span data-stu-id="8ce1b-152">Add a Dynamics 365 trial subscription and test Office 365 and Dynamics 365 integrated features and scenarios with these articles:</span></span>
  
- [<span data-ttu-id="8ce1b-153">Office 365 和 Dynamics 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-153">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
    <span data-ttu-id="8ce1b-154">將 Dynamics 365 試用版訂閱以及 Dynamics 365 授權和權限新增至您的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-154">Add a Dynamics 365 trial subscription and Dynamics 365 licences and permissions to your user accounts.</span></span>
    
- [<span data-ttu-id="8ce1b-155">適用於 Office 365 和 Dynamics 365 開發/測試環境的 Exchange Online 整合</span><span class="sxs-lookup"><span data-stu-id="8ce1b-155">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    <span data-ttu-id="8ce1b-156">設定然後示範 Office 365 與 Dynamics 365 如何在 Exchange Online 信箱中共同運作。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-156">Configure and then demonstrate how  Office 365 and Dynamics 365 work together in Exchange Online mailboxes.</span></span>
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="8ce1b-157">One Microsoft Cloud 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-157">The One Microsoft Cloud dev/test environment</span></span>
<span data-ttu-id="8ce1b-158"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-158"></span></span>

<span data-ttu-id="8ce1b-p104">建立開發/測試環境，其中包含所有 Microsoft 的雲端供應項目：Office 365、Azure、EMS 及 Dynamics 365。請參閱 [One Microsoft Cloud 開發/測試環境](the-one-microsoft-cloud-dev-test-environment.md)以取得逐步指示。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p104">Create a dev/test environment that includes all of Microsoft's cloud offerings: Office 365, Azure, EMS, and Dynamics 365. See [The One Microsoft Cloud dev/test environment](the-one-microsoft-cloud-dev-test-environment.md) for the step-by-step instructions.</span></span>
  
## <a name="simulated-cross-premises-devtest-environments"></a><span data-ttu-id="8ce1b-161">模擬的跨單位部署開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-161">Simulated cross-premises dev/test environments</span></span>
<span data-ttu-id="8ce1b-162"><a name="O365_D365"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-162"></span></span>

<span data-ttu-id="8ce1b-163">透過這些文章，您可以建立一個跨單位部署開發/測試環境，它包含 Azure 虛擬網路和模擬的內部部署網路︰</span><span class="sxs-lookup"><span data-stu-id="8ce1b-163">You can create a cross-premises dev/test environment, which includes an Azure virtual network and a simulated on-premises network, with these articles:</span></span>
  
- [<span data-ttu-id="8ce1b-164">Azure 中模擬的跨單位部署虛擬網路</span><span class="sxs-lookup"><span data-stu-id="8ce1b-164">Phase 2: Create the cross-premises virtual network in Azure</span></span>](simulated-cross-premises-virtual-network-in-azure.md)
    
    <span data-ttu-id="8ce1b-165">在混合雲端組態中，建立連線到 Azure 虛擬網路的模擬內部網路。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-165">Create a simulated intranet connected to an Azure virtual network in a hybrid cloud configuration.</span></span>
    
- [<span data-ttu-id="8ce1b-166">Azure 開發/測試環境中的內部網路 SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="8ce1b-166">Intranet SharePoint Server 2016 in Azure dev/test environment</span></span>](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    <span data-ttu-id="8ce1b-167">在 Azure 虛擬網路中建立單一伺服器 SharePoint Server 2016 陣列，並從模擬的內部部署網路測試連線能力和管理。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-167">Create a single-server SharePoint Server 2016 farm in the Azure virtual network and test connectivity and administration from the simulated on-premises network.</span></span>
    
## <a name="additional-cloud-based-devtest-environments"></a><span data-ttu-id="8ce1b-168">其他雲端式開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-168">Additional cloud-based dev/test environments</span></span>
<span data-ttu-id="8ce1b-169"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-169"></span></span>

<span data-ttu-id="8ce1b-170">以下是您可以在 Azure 基礎結構服務中建立的其他雲端式開發/測試環境︰</span><span class="sxs-lookup"><span data-stu-id="8ce1b-170">Here are additional cloud-based dev/test environments that you can create in Azure infrastructure services:</span></span>
  
- [<span data-ttu-id="8ce1b-171">Azure 中的 SharePoint Server 2016 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-171">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt723354.aspx)
    
    <span data-ttu-id="8ce1b-172">在 Azure 基礎結構服務中建置單一伺服器 SharePoint Server 2016 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-172">Build a single-server SharePoint Server 2016 farm in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="8ce1b-173">Azure 中的 Exchange 2016 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-173">SharePoint Server 2016 dev/test environment in Azure</span></span>](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    <span data-ttu-id="8ce1b-174">在 Azure 基礎結構服務中建置單一的 Exchange 2016 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-174">Build a single Exchange 2016 server in Azure infrastructure services.</span></span>
    
- [<span data-ttu-id="8ce1b-175">Azure 中的 SharePoint Server 2013 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="8ce1b-175">SharePoint 2013 dev/test environments in Azure</span></span>](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    <span data-ttu-id="8ce1b-176">在 Azure 基礎結構服務中建置基本和高可用性的 SharePoint Server 2013 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-176">Build basic and high-availability SharePoint Server 2013 farms in Azure infrastructure services.</span></span>
    
<span data-ttu-id="8ce1b-177">**參與討論**</span><span class="sxs-lookup"><span data-stu-id="8ce1b-177">**Join the discussion**</span></span>

|<span data-ttu-id="8ce1b-178">**連絡我們**</span><span class="sxs-lookup"><span data-stu-id="8ce1b-178">**Contact us**</span></span>|<span data-ttu-id="8ce1b-179">**描述**</span><span class="sxs-lookup"><span data-stu-id="8ce1b-179">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ce1b-180">**您需要什麼樣的雲端採用內容？**</span><span class="sxs-lookup"><span data-stu-id="8ce1b-180">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="8ce1b-p105">我們正在建立涵蓋多個 Microsoft 雲端平台及服務的雲端採用內容。請傳送電子郵件至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)，讓我們知道您對雲端採用內容的看法或對特定內容的要求。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p105">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="8ce1b-183">**加入雲端採用討論**</span><span class="sxs-lookup"><span data-stu-id="8ce1b-183">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="8ce1b-p106">如果您熱愛雲端解決方案，請考慮加入雲端採用諮詢委員會 (Cloud Adoption Advisory Board，CAAB)，與更大且活躍的 Microsoft 內容開發人員、產業專業人員及全球的客戶接觸。若要加入，請新增為 Microsoft 技術社群 [CAAB (雲端採用諮詢委員會) 空間](https://aka.ms/caab)的成員，並傳送電子郵件給我們，地址為：[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)。所有人都可以在 [CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)上讀取社群相關內容。不過，CAAB 成員可獲得新雲端採用資源和解決方案說明的私人網路研討會邀請。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p106">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="8ce1b-187">**取得您在這裡看到的美工圖案**</span><span class="sxs-lookup"><span data-stu-id="8ce1b-187">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="8ce1b-p107">如果您想要此文章中所看到之美工圖案的可編輯複本，我們很樂於將它傳送給您。請以電子郵件將您的要求 (包括美工圖案的 URL 和標題) 傳送至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="8ce1b-p107">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="8ce1b-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ce1b-190">See Also</span></span>

<span data-ttu-id="8ce1b-191"><a name="ADD_TLGs"> </a></span><span class="sxs-lookup"><span data-stu-id="8ce1b-191"></span></span>

[<span data-ttu-id="8ce1b-192">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="8ce1b-192">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="8ce1b-193">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="8ce1b-193">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="8ce1b-194">適用於 SharePoint、Exchange、商務用 Skype 和 Lync 的架構模型</span><span class="sxs-lookup"><span data-stu-id="8ce1b-194">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="8ce1b-195">混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="8ce1b-195">Hybrid solutions</span></span>](hybrid-solutions.md)


