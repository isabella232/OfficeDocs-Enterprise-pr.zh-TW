---
title: Office 365 技術控制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 摘要： Microsoft 技術控制項做法的 Office 365 的概觀。
ms.openlocfilehash: 3063bcaca85d529885fbafddda88f61325b2b83c
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031138"
---
# <a name="office-365-technology-controls"></a>Office 365 技術控制 

Microsoft 會使用數種工具與技術來控制、 管理和對應地稽核存取客戶資料中其線上服務。 這些適用於 Exchange Online、 SharePoint Online、 加密箱與客戶加密箱、 多重要素驗證，以及更多。 Yammer 使用[Yammer 企業存取控制](office-365-yammer-enterprise-access-controls.md)所述的類似控制項。

Office 365 工程師有零的常設存取 Office 365 客戶資料。 工程師必須經過 Microsoft 核准程序，才能存取客戶資料的服務作業，就會發生。 如果客戶授權 Exchange Online 和 SharePoint Online 客戶加密箱功能，客戶資料的存取權要求客戶核准。 核准之後，服務相關的管理帳戶會佈建剛-階段存取的服務要求所需的工作。

## <a name="lockbox-and-customer-lockbox"></a>加密箱和客戶加密箱

雖然罕見，客戶可以從公開至 Microsoft 工程師的客戶內容的 Microsoft 要求協助。 若要控制存取 Exchange Online，Microsoft 會使用稱為 Lockbox 的存取控制系統。 任何 Microsoft 工程師存取所有的 Exchange Online 或 SharePoint Online 的系統或資料之前，他們必須送出使用加密箱存取要求。 Exchange Online 和 SharePoint Online 的所有服務要求是由加密箱系統都處理。 加密箱與客戶加密箱，所有核准的存取是唯一的使用者，讓工程師負責其處理客戶資料可進行追蹤。

> [!NOTE]
> Exchange Online 包含商務資料儲存在使用者信箱中任何商務用 Skype。 Skype 商務涵蓋範圍不包含 Skype 會議廣播錄製或由使用者上傳至會議的內容。 SharePoint Online 包含商務用 OneDrive。

加密箱處理要求的權限，授與工程師執行服務內的作業及系統管理功能的能力。 透過加密箱和 Microsoft 主管工程師送出要求必須核准要求，才能讓工程師存取客戶資料。 管理員核准之後，工程師會有時間限制及範圍限制存取客戶資料處理客戶問題。

Office 365 客戶加密箱可協助您符合規範，如果您需要在進行中的程序進行明確資料的存取授權。 這是有些合規性標準，例如 FedRAMP 和 HIPAA 的需求。 客戶加密箱您插入 Lockbox 核准程序，並提供讓您能夠控制 Microsoft access 在您 Exchange Online 或 SharePoint Online 內容的服務作業的授權。

在極罕見的執行個體時的 Microsoft 服務工程師需要存取您的資料，您授與存取權才能解決此問題： 所需的資料和有限的時間。 如果您拒絕存取要求時，Microsoft 工程師不需要存取您的內容，並將無法完成服務作業。 如果您核准要求，Microsoft 工程師已透過內容提供有限的剛時間存取監控和限制管理介面。

支援工程師所採取的動作用途的稽核記錄，並可透過[Office 365 管理活動 API](https://msdn.microsoft.com/library/office/dn707383.aspx)和[安全性與合規性中心](https://protection.office.com/)。

>[!NOTE]
> 客戶加密箱是在[Office 365 企業版 E5](https://products.office.com/business/office-365-enterprise-e5-business-software)作為附加元件形式購買。 如需詳細資訊，請參閱 [Office 365 Customer Lockbox 要求](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)。

## <a name="just-in-time-access"></a>剛-階段存取

Microsoft 會使用剛-時間 (JIT) 存取原則的 Office 365 來減輕竄改的風險和側面攻擊的認證。 JIT 移除服務持續性系統管理存取權，並取代，視需要提升到這些角色的權利。 從系統管理員移除常設存取權限，可確保認證可用，只有當他們所需並減少認證遭竊的風險。

JIT access 模型需要工程師要求提升的權限來執行系統管理職責劃分有限的一段。 此外，工程師會使用暫時帳戶機器所產生的複雜密碼以建立，並授與只允許他們能執行的必要工作的角色。 例如，系統管理存取權授與的加密箱時間繫結，且的時間存取權授與量取決於要求的角色。 工程師指定加密箱系統要求中所需的時間存取權的持續的時間。 加密箱系統拒絕要求時所要求的時間超過最大允許提高權限的時間。 到期後移除系統管理存取權及暫時帳戶過期。

當授權並核准存取，工程師就會收到授權系統所產生的一次性使用系統管理密碼。 核准提高權限的存取要求每次時，會產生新密碼。 密碼複製到安全密碼、 是不同於 Microsoft 公司環境中，工程師的認證，而且僅適合核准提高權限的存取工作階段。

## <a name="constrained-management-interfaces"></a>限制的管理介面

工程師使用兩個管理介面來執行系統管理工作： 透過安全的終端機服務閘道 (TSGs) 和遠端 PowerShell 的遠端桌面。 這些管理介面，在軟體原則和存取控制進行重大限制有哪些應用程式會執行哪些命令和指令程式可供使用。

Office 365 伺服器將並行工作階段限制一工作階段的每個服務小組系統管理員，每個伺服器。 TSGs 讓使用者只會在單一的並行工作階段，並不允許多個工作階段。 使用每個伺服器的單一工作階段，TSGs 允許連線至多部伺服器同時讓系統管理員可以有效地負有他們的 Office 365 服務小組系統管理員。 服務小組系統管理員沒有 TSGs 本身的任何權限。 TSG 僅用於強制執行多重要素驗證 (MFA) 和加密的需求。 一旦服務小組管理員連線到 TSG 透過特定伺服器，特定伺服器強制執行系統管理員每一個工作階段的限制。

流量限制和 Office 365 人員的連線及設定需求的 Active Directory 群組原則所建立。 這些原則包含下列特性：

- TSGs 使用[FIPS](https://www.microsoft.com/TrustCenter/Compliance/FIPS) 140-2 驗證的加密。
- 30 分鐘一段時間之後中斷 TSG 工作階段。
- TSG 工作階段會自動登出 24 小時之後。

連線至 TSGs 也需要使用不同的實體智慧卡及從工程師 Microsoft 公司認證的帳戶不同的 MFA。 工程師會發出不同智慧卡進行各種平台和密碼管理平台確保安全認證儲存。 TSGs 使用 Active Directory 群組原則以控制可以登入遠端伺服器，允許工作階段及閒置逾時設定的數目。 其他原則限制存取允許應用程式，並限制網際網路存取。

除了使用特別設定的 TSGs 遠端存取 Exchange Online 可讓服務工程師作業角色具有存取特定系統管理功能，使用遠端 PowerShell 的實際執行伺服器上的使用者。 若要這麼做，使用者必須針對 Office 365 實際執行環境的唯讀 （偵錯） 存取權限。 權限提升已啟用它已啟用 TSGs 使用的加密箱程序的方式相同。

遠端存取的每個資料中心會具有負載平衡虛擬 IP 中做為存取的單一資料點。 取得在驗證期間存取宣告中所識別的特殊權限層級根據可用的遠端 PowerShell cmdlet。 這些 cmdlet 提供連線使用此方法的使用者可存取僅系統管理功能。 遠端 PowerShell 限制命令提供給工程師範圍，並根據透過加密箱程序授與的存取層級。 例如，在 Exchange Online 中，Get-mailbox 可能會提供，但不是會將 Set-mailbox。
