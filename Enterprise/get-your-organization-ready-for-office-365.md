---
title: 規劃 Office 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: 存取資源以規劃 Office 365 企業版部署。
ms.openlocfilehash: d35bba7940f549d7b39e3cf75c3e659daa4e1d33
ms.sourcegitcommit: bb5b7bd241f58491198de2d74dbdce76f7bb8f62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419351"
---
# <a name="plan-for-office-365-enterprise"></a>規劃 Office 365 Enterprise

當您將企業組織移至 Office 365 時，請務必預先規劃並進行重要設計決策，以簡化 IT 部署和使用者採用。 

## <a name="planning-with-office-365-fasttrack"></a>使用 Office 365 FastTrack 規劃

[FastTrack For office 365](https://docs.microsoft.com/fasttrack/O365-fasttrack-benefit-for-office-365)是取得 Microsoft 的協助，以規劃 office 365 部署的最佳方法。 FastTrack 可協助您完成最常見的設計考慮，也可以在方法中解答問題。 

>[!Note]
>您也可以從[Microsoft 合作夥伴](https://www.microsoft.com/solution-providers/home)取得協助。
>

## <a name="do-it-yourself-planning-for-office-365"></a>自行規劃 Office 365

若要自行規劃 Office 365，請逐步完成下列方面的規劃與設計決策：

- 您的 Office 365 租用戶

  包括對網際網路的網路連線、Office 365 身分識別的規劃，以及與應用程式、內部部署、Azure 及其他元素的整合。 從[這裡](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)開始。

- 用戶端支援

  包括憑證型驗證、行動裝置管理、驗證選項及承租人間共同作業。 從[這裡](office-365-client-support-certificate-based-authentication.md)開始。

- 支援混合式新式驗證

  包括使用主要 Office 365 工作負載的混合式設定時，規劃新式驗證。 從[這裡](hybrid-modern-auth-overview.md)開始。

- 舊版 Office 用戶端和伺服器

  包括 Office 2007 和 Office 2010 用戶端和伺服器產品的遷移資訊。 從[這裡](plan-upgrade-previous-versions-office.md)開始。

>[!Note]
>您也可以針對[Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)訂閱使用此程式。
>

您也可以登入 Office 365 訂閱，並使用[office 365 服務的設定指南](setup-guides-for-office-365.md)。



<!--

This checklist will help your organization as you plan and prepare for a migration to Office 365. The phases and steps in the checklist are aligned with the guidance provided by the [Onboarding Center](https://go.microsoft.com/fwlink/?LinkId=517115). Feel free to adapt this checklist to your organization's needs.

Most organizations don't need to do anything to prepare for Office 365. It's an application on the web and people are able to use it as soon as they have an account. Other organizations have more locations, security practices, or other requirements that create the need for more planning. For enterprise-level organizations, follow the checklist items below to get started with Office 365.
  
If you want help getting Office 365 set up, [FastTrack](https://fasttrack.microsoft.com/office) is the easiest way to deploy Office 365, you can also sign in and use the [Setup guides for Office 365 services](setup-guides-for-office-365.md).
  
|**Choose one or more to get started:**||
|:-----|:-----|
| [System requirements for Office](https://products.office.com/office-system-requirements) |- Microsoft Office 365 ProPlus, Office 365, Office 365 ProPlus, and each Office application for Windows, Mac, iOS, and Android all have specific system requirements. Ensure your hardware and software meet the minimum system requirements.|
|**Most** customers connect their on-premises directory to Office 365. Get a head start on directory preparation by [installing and running IdFix on your network](https://www.microsoft.com/download/details.aspx?id=36832). <br> Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium set up guide](https://aka.ms/aadpguidance) to get customized set up guidance. <br> |- Automated checks against your directory to [validate people's accounts will properly synchronize](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> - Recommends changes to directory objects and offers to automate the changes for you. <br> - [More details on using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Read** our [network performance guidance](https://aka.ms/tune) and use our tools to ensure you have the connectivity and performance configuration necessary to provide people with the best experience.  <br> | - Ensure you can connect to Office 365, if you filter or scan outbound traffic, you'll want to understand what [managing Office 365 endpoints](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) means for your organization.  <br>  - [Model and test your network capacity](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) or move to an [Azure ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) circuit for a more predictable experience.   |
|**Use** our [planning checklist](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) as a starting place for building your own deployment plan.  <br> | - In-depth overview of possible areas you'll need to plan for with links to reference or how-to information to help you plan. |
|**Use** the [Exchange Server Large Item Script](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) to find mail items that may be too large to migrate.  <br> | - Uses Exchange Web Services to impersonate, access, scan the mailbox for file sizes you specify, and dumps the results in a CSV file. Read the [detailed instructions on how to use the script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**Take** advantage of [Microsoft deployment experts](https://go.microsoft.com/fwlink/?LinkId=517115) who can help you from planning to helping everyone start using the new services and applications.  <br> Use the [Deployment wizards for Office 365 services](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) to get customized set up guidance.  <br> | - The Onboarding center works directly with customers and with partner organizations. Give them a call today. |
|**Use** the [templates and resources in the Office 365 success center](https://www.microsoft.com/fasttrack/resources) to share your deployment and onboarding plans with the people in your organization.  <br> | - Communication with everyone before, during, and after the transition to Office 365 is critical.  <br> - Use our templates, guides, and handouts to improve your communications. |
|**Read** the article [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.  <br> | - This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity. |
   
Want more resources to help you integrate Office 365 with your broader cloud strategy? Here are the [Microsoft cloud IT architecture resources](https://docs.microsoft.com/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## Want to talk with support?

We're here to help, [contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products.


--> 