---
title: 隔離的 SharePoint Online 小組網站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: 摘要： 了解隔離的 SharePoint Online 小組網站的用途。
ms.openlocfilehash: 358bb16c01c51a76da6557091dacca75e317bf92
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="e187d-103">隔離的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="e187d-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="e187d-104">**摘要：**了解隔離的 SharePoint Online 小組網站的用途。</span><span class="sxs-lookup"><span data-stu-id="e187d-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="e187d-p101">SharePoint Online 小組網站是簡單的方法來快速建立 Microsoft Office 365 中的 [共同作業的備忘稿、 文件、 文章、 行事曆及其他資源的空間。SharePoint Online 小組網站的 Office 365 群組為基礎且允許開啟的共同作業與私人設定的群組成員或整個組織的簡化的管理模型。預設的 SharePoint Online 小組網站可讓邀請其他使用者並控制的權限設定 Office 365 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e187d-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="e187d-p102">不過，在某些情況下，您想要建立 SharePoint Online 小組網站的共同作業出該網站的權限更緊密控制透過群組成員資格和 SharePoint Online 只會依 SharePoint 受管理的權限等級系統管理員。我們會呼叫這是一組使用者包括共同作業、 檢視其內容或管理網站的隔離隔離站台。您可能需要隔離的網站下列：</span><span class="sxs-lookup"><span data-stu-id="e187d-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="e187d-111">在組織內秘密專案。</span><span class="sxs-lookup"><span data-stu-id="e187d-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="e187d-112">高度機密或價值財產組織的位置。</span><span class="sxs-lookup"><span data-stu-id="e187d-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="e187d-113">法律所組織或要所以所必須採取的資源。</span><span class="sxs-lookup"><span data-stu-id="e187d-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="e187d-114">若要共用多個的組織有某些重疊，但通常存在於為不同的商務實體之間的 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="e187d-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="e187d-115">以下是隔離的站台的需求：</span><span class="sxs-lookup"><span data-stu-id="e187d-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="e187d-116">只有 SharePoint Online 系統管理員可以執行網站管理] 包含的存取權的網站和設定自訂權限的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="e187d-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="e187d-117">網站的成員不能邀請其他至小組網站的成員。</span><span class="sxs-lookup"><span data-stu-id="e187d-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="e187d-p103">不是隔離的站台之成員的使用者無法要求網站的存取權。時，會收到當他們嘗試存取與網站相關聯的任何 URL 拒絕網頁上存取。</span><span class="sxs-lookup"><span data-stu-id="e187d-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="e187d-p104">需要集中式的存取控制及自訂 SharePoint Online 系統管理員權限的取捨是一段時間內網站保持隔離。例如，目前成員無法、 有意或無意、 邀請或設定在 Office 365 訂閱不應成員之站台內的其他使用者的自訂權限。</span><span class="sxs-lookup"><span data-stu-id="e187d-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="e187d-122">隔離的網站可以用於與其他功能，例如：</span><span class="sxs-lookup"><span data-stu-id="e187d-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="e187d-123">若要確保保持在網站上的資源的資訊版權管理加密，即使在本機上下載及上傳至另一個網站可供整個組織。</span><span class="sxs-lookup"><span data-stu-id="e187d-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="e187d-124">若要防止使用者傳送的資源之站台，如檔、 電子郵件中的資料遺失保護。</span><span class="sxs-lookup"><span data-stu-id="e187d-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="e187d-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e187d-125">Next steps</span></span>

<span data-ttu-id="e187d-126">若要嘗試出隔離的 SharePoint Online 小組網站中試用訂閱，請參閱[隔離 SharePoint Online 小組網站的開發人員/測試環境](isolated-sharepoint-online-team-site-dev-test-environment.md)中的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="e187d-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e187d-127">當您準備好要部署在生產環境中的隔離的 SharePoint Online 小組網站時，請參閱[設計隔離的 SharePoint Online 小組網站](design-an-isolated-sharepoint-online-team-site.md)中的逐步說明設計考量。</span><span class="sxs-lookup"><span data-stu-id="e187d-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e187d-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="e187d-128">See Also</span></span>

[<span data-ttu-id="e187d-129">設計隔離的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="e187d-129">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="e187d-130">管理隔離的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="e187d-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="e187d-131">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="e187d-131">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="e187d-132">部署隔離的 SharePoint Online 小組網站</span><span class="sxs-lookup"><span data-stu-id="e187d-132">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)


