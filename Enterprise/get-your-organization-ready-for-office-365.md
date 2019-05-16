---
title: 準備讓您的組織使用 Office 365 企業版
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: 如果您已選擇退出 FastTrack 部署，並不尋找您需要在我們的基本部署步驟中，這是可以從這裡開始。
ms.openlocfilehash: 90cf7cda7070c626579389f8122cdc438d88abe0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067539"
---
# <a name="get-your-organization-ready-for-office-365-enterprise"></a>準備讓您的組織使用 Office 365 企業版

## <a name="what-do-you-need-to-do-to-get-ready-for-office-365"></a>您要如何準備好 Office 365？

大部份組織不需要執行任何動作來準備 Office 365。 在 [web 應用程式和人都可以使用它，只要他們擁有的帳戶。 其他組織有多個位置、 安全性作法或其他需求，建立需要更進一步規劃。 針對企業層級的組織，請遵循下面的 < 開始使用 Office 365 的檢查清單項目。
  
若您需要取得 Office 365 設定的協助，[FastTrack](https://fasttrack.microsoft.com/office) 是部署 Office 365 的最簡單方法，您也可以登入並使用 [Office 365 服務的部署建議](deployment-advisors-for-office-365.md)。
  
|**選擇一個或多個若要開始使用：**||
|:-----|:-----|
| [Office 的系統需求](https://products.office.com/office-system-requirements) |-Microsoft Office 專業版、 Office 365、 Office 365 專業增強版，和 Windows、 Mac、 iOS 和 Android 所有的每個 Office 應用程式會有特定的系統需求。 確定您的硬體和軟體符合最低的系統需求。|
|**大多數**客戶連線到 Office 365 其內部部署目錄。 取得由[安裝及執行 IdFix 您網路上](https://www.microsoft.com/download/details.aspx?id=36832)的目錄準備好的開始。 <br> 您可以使用[AAD Connect 顧問](https://aka.ms/aadconnectpwsync)與[Azure AD Premium 設定指南](https://aka.ms/aadpguidance)來取得自訂的設定指導方針。 <br> |-自動化對您的目錄來檢查[驗證人民帳戶將正確同步處理](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e)。 <br> -建議變更目錄物件，並提供您自動化所做的變更。 <br> - [使用 IdFix 工具的詳細](prepare-directory-attributes-for-synch-with-idfix.md)解說。 |
|**閱讀**我們的[網路效能指引](https://aka.ms/tune)和使用我們的工具，以確保您已連線能力與效能的必要設定為人員提供最佳的體驗。  <br> | -確認您可以連線至 Office 365，如果您篩選或掃描輸出流量，您會想要了解[管理 Office 365 端點](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a)哪些表示為您的組織。  <br>  - [模型，並測試您的網路容量](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132)或移至[Office 365 Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)線路更能預測。   |
|我們[規劃檢查清單](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0)作為起點來建置您自己的部署計劃**使用**。  <br> | -深入概觀可能領域需要計劃，以協助您規劃的參照或相關資訊連結。 |
|**使用** [Exchange Server 大型項目指令碼](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6)來尋找郵件項目可能太大，無法移轉。  <br> | -使用 Exchange Web 服務模擬、 存取、 掃描您指定的檔案大小和傾印 CSV 檔案中的結果的信箱。 閱讀[如何使用指令碼的詳細的指示](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx)。 |
|[Microsoft 部署專家](https://go.microsoft.com/fwlink/?LinkId=517115)可協助您從規劃時，協助每個人都**需要**優點開始使用新的服務和應用程式。  <br> 使用[Office 365 服務的部署精靈](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2)] 來取得自訂的設定指導方針。  <br> | -在上架中心適用於直接與客戶和合作夥伴組織。 請授與呼叫今天。 |
|**使用**[範本與 Office 365 成功中心中的資源](https://www.microsoft.com/fasttrack/resources)以共用您的部署和上架計劃與您組織中的人員。  <br> | -與所有人之前、 期間和之後轉換至 Office 365 通訊非常重要。  <br> -使用我們的範本、 輔助線和講義來改善您的通訊。 |
|**閱讀**本文以了解安全地管理 Office 365 流量，並取得獲得最佳效能的連線能力原則的[Office 365 網路連線原則](https://aka.ms/o365networkingprinciples)。  <br> | -這篇文章可協助您了解安全地最佳化 Office 365 網路連線的最新的指引。 |
   
需要更多的資源可協助您 Office 365 與您更廣泛的雲端策略整合？ 以下是[Microsoft cloud IT 架構資源](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources)。
  
## <a name="want-to-talk-with-support"></a>要與支援？

我們會協助，請[連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)商務產品的。
