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
ms.openlocfilehash: c615280d39117f68515fb13d4ba83428d73e4fd3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="4960f-103">保護敏感和最高機密資產的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="4960f-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="4960f-104">**摘要：**如何實作的 Contoso 機密保護和高度機密 SharePoint Online 小組高階主管和其參考資料中心的更容易，尚未安全共同作業的網站。</span><span class="sxs-lookup"><span data-stu-id="4960f-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="4960f-p101">Contoso executive 領導想要使用 Office 365 和其檔案儲存在單一位置進行共同作業，不論可能主管。同樣地，Contoso 的研究 （英文） 部門 — 搭配中 Paris、 莫斯科、 紐約、 北京及班加羅爾部門 — 想要轉換至更輕鬆地存取與更多 open 共同作業雲端其內部部署數位資產跨小組。</span><span class="sxs-lookup"><span data-stu-id="4960f-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="4960f-p102">不過，在兩個這種情況下，這些資源的存取權必須受限的人員，他們可以檢視或變更，以進行中的權限由 IT 人員管理網站的子集。此外，即使一些資源有意或無意分散式，他們必須加密且可防止使用者可以使用沒有權限來檢視或變更其內容的權限。</span><span class="sxs-lookup"><span data-stu-id="4960f-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="4960f-109">安全性與 SharePoint 管理員可以在 Contoso 的 IT 部門決定要使用機密保護和高度機密的 SharePoint Online 小組網站，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="4960f-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="4960f-110">**圖 1： 比較的機密保護和高度機密的 SharePoint Online 小組網站**</span><span class="sxs-lookup"><span data-stu-id="4960f-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![敏感性保護和高度機密的 SharePoint Online 小組網站](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="4960f-112">Contoso 為其行政人員及的研究小組建立安全的 SharePoint Online 小組網站使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4960f-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="4960f-113">建立**高階主管**機密 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="4960f-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="4960f-114">新的小組網站的編輯 SharePoint 權限層級與 SharePoint 系統管理員帳戶一小群為完全控制 」 權限等級的擁有者的成員身分的高階主管使用現有的 Azure Active Directory (AD) 群組。</span><span class="sxs-lookup"><span data-stu-id="4960f-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="4960f-115">移轉高階主管檔案</span><span class="sxs-lookup"><span data-stu-id="4960f-115">Migrate executives files</span></span>
    
    <span data-ttu-id="4960f-116">將現有的內部部署 executive 檔案及資料夾移至新的高階主管 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="4960f-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="4960f-117">建立**[參考資料**高度機密 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="4960f-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="4960f-p103">新的小組網站會使用現有的 Azure AD 研究小組群組做為完全控制 」 權限等級的擁有者的編輯權限等級與 SharePoint 系統管理員帳戶一小群成員。指派給研究檔案 AIP 標籤確保他們會加密和只有研究 （英文） 群組的成員可以開啟它們。</span><span class="sxs-lookup"><span data-stu-id="4960f-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="4960f-120">移轉參考資料檔案</span><span class="sxs-lookup"><span data-stu-id="4960f-120">Migrate research files</span></span>
    
    <span data-ttu-id="4960f-121">將現有的研究小組內部檔案及資料夾至新的研究 SharePoint Online 小組網站。</span><span class="sxs-lookup"><span data-stu-id="4960f-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="4960f-p104">結果是兩個共同作業網站的安全性與 SharePoint 管理員緊密控制其存取。具有高度機密 AIP 標籤檔案，即使其分散外研究小組網站上，會加密且只可以開啟由的研究小組成員。</span><span class="sxs-lookup"><span data-stu-id="4960f-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="4960f-124">如需詳細資訊，請參閱[Secure SharePoint Online 網站及檔案](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)。</span><span class="sxs-lookup"><span data-stu-id="4960f-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="4960f-125">若要將此以為示範、 概念證明或開發人員/測試，請參閱 ＜[保護 SharePoint Online 開發人員/測試環境中的網站](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)。</span><span class="sxs-lookup"><span data-stu-id="4960f-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4960f-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="4960f-126">See Also</span></span>

[<span data-ttu-id="4960f-127">Contoso Corporation 的企業案例</span><span class="sxs-lookup"><span data-stu-id="4960f-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="4960f-128">Microsoft Cloud 中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="4960f-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="4960f-129">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="4960f-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="4960f-130">伸展資料庫</span><span class="sxs-lookup"><span data-stu-id="4960f-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="4960f-131">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="4960f-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




