---
title: Office 365 資源限制
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
f1.keywords:
- NOCSH
description: 摘要： Office 365 中各種應用程式的資源限制的相關資訊。
ms.openlocfilehash: 55fa8d90c6f83c84a1e43f32cf7cd0eeafbf1274
ms.sourcegitcommit: ed4482ad35274b79d44d0f9a17be3e52d5ad0492
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "43666324"
---
# <a name="resource-limits"></a>資源限制

使用配額（限制）和節流來強制執行資源限制。 Azure Active Directory 和個別的 Office 365 服務會同時使用這兩者。 限制是服務特有的，而且隨時間而變更會隨著新功能的增加而變更。 如需各種服務目前限制的詳細資訊，請參閱下列主題：

- [Azure Active Directory 服務限制和限制](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits)
- [Exchange Online 限制](https://technet.microsoft.com/library/exchange-online-limits.aspx)
- [Exchange Online Protection 限制](https://technet.microsoft.com/library/exchange-online-protection-limits.aspx)
- [SharePoint 線上軟體界限和限制](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [商務用 Skype 限制](https://technet.microsoft.com/library/skype-for-business-online-limits.aspx)
- [Yammer REST API 和速率限制](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Sway 中的檔案大小限制](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

除了這些限制以外，還會在整個 Azure Active Directory 和 Office 365 中使用多個節流機制。 在服務內節流尤其重要，因為 Microsoft 資料中心的網路資源已針對使用服務的廣泛客戶進行優化。 節流機制包括：

- Azure Active Directory 和 Office 365 功能的使用者層級節流，它會限制單一使用者可以執行的交易或並行通話數目（按腳本或程式碼）。
- 在建立承租人時，會將預設的 PowerShell 節流原則指派給每個承租人。 這些設定會影響其他專案，例如可由單一系統管理員開啟的最大併發 PowerShell 會話數目。
- 每個 Exchange Online 客戶都有一個預設 Exchange Web 服務（EWS）原則，針對 EWS 用戶端作業進行調整，以及適用于所有 Outlook 用戶端的節流。
