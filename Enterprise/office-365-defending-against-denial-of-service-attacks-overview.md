---
title: 防禦 Microsoft 365 中的拒絕服務攻擊
ms.author: josephd
author: JoeDavies-MSFT
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
description: 拒絕服務（DoS）攻擊的概覽。
ms.openlocfilehash: 2cbe5eb86402fd7b7888f39440a58935604c90eb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998417"
---
# <a name="defend-against-denial-of-service-attacks-in-microsoft-365"></a>防禦 Microsoft 365 中的拒絕服務攻擊

## <a name="introduction"></a>簡介

Microsoft 為超過100個資料中心的全球雲端基礎結構中所主控的超過200雲端服務提供信賴的基礎結構。 包括：

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft 365 和 Office 365
- Microsoft OneDrive
- Skype
- Xbox Live

作為具有大量 Internet 平臺的全球性組織，以及提供雲端服務的許多醒目 Internet 屬性，Microsoft 是駭客和其他惡意人員的大型常見目標。 用戶端與 Microsoft 雲端之間的網路通訊層是最大的惡意攻擊目標之一。 實際上，Microsoft 會持續而且持久地以某種形式的網路 cyberattack 為基礎。 根據此，Microsoft 會使用深層防禦安全性原則來保護其雲端服務和網路。 若沒有防禦這些攻擊的可靠且持久的緩解系統，則 Microsoft 的雲端服務會離線且無法供客戶使用。

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>拒絕服務攻擊的定義和徵兆

攻擊網路服務的其中一種方法，就是針對服務主機建立許多要求，讓網路和伺服器不堪重負，以拒絕對合法使用者的服務。 這稱為「拒絕服務」（DoS）攻擊。 當多個主角、端點和/或向量執行攻擊時，會將其稱為「分散式阻斷服務」（DDoS）攻擊。 雖然這種方式不同，但 DoS 和 DDoS 攻擊通常是為了避免網際網路網站或服務無法正常運作，或暫時或無限的努力所組成。

[美國電腦緊急就緒小組](https://www.us-cert.gov/)（US CERT）定義要包含的 DoS 攻擊的徵兆：

- 網路效能緩慢（開啟檔案或存取網際網路網站時）
- 網站不可用
- 無法存取網站
- 收到的垃圾郵件大幅增加
- 斷開無線或有線網際網路連線
- 長期失去存取網頁或任何網際網路服務的許可權

## <a name="related-topics"></a>相關主題

- [防禦阻斷服務攻擊的核心原則](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Microsoft 的拒絕服務防禦策略](office-365-microsoft-dos-defense-strategy.md)
- [防禦拒絕服務攻擊的 Microsoft 雲端服務](office-365-defending-cloud-services-against-dos-attacks.md)
