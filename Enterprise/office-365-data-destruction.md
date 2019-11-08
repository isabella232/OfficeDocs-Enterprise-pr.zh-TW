---
title: Office 365 資料毀損
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
description: 回收、 處置或損毀的 Office 365 資料中心的磁碟機和伺服器相關的 Microsoft 原則的概觀。
ms.openlocfilehash: 1fca278dd23e84db2c6591eefc45d0b75265cf17
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032088"
---
# <a name="office-365-data-destruction"></a>Office 365 資料毀損

## <a name="physical-data-destruction"></a>實體資料毀損

Microsoft 的資料處理標準的原則可能會位址回收和處置的磁碟機和失敗或淘汰的伺服器。 之前重複使用任何 Office 365 磁碟機，Microsoft 會執行與國家標準與技術 Special Publication 800-88 （[媒體病毒掃描的 NIST SP 800-88 Guidelines](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf)） 一致的實體的病毒掃描程序。 由於 Office 365 中的所有磁碟機都加密使用 BitLocker 磁碟區層級加密，NIST SP 800-88-相容清除技術上不需要。 不過，Microsoft 會執行此程序。

無法在 Office 365 資料中心實體損毀及稽核透過 ISO 程序中使用的磁碟。 資產類型會決定適當的處理方式。 Microsoft 無法抹除的硬碟，摧毀媒體並呈現資訊的復原無法使用毀損程序。 例如，磁碟是實體損毀、 pulverized，或 incinerated。 Microsoft 會保留毀損的所有記錄，並重複使用 Office 365 內的伺服器上執行類似的病毒掃描程序。 這些指導方針包含電子版與實體的病毒掃描。

每個資料中心棄置其磁碟使用現場實際銷毀程序。 安全的紙匣的磁碟處置指定的儲存媒體都是在每個區域中的資料中心。 每個安全 bin 站台具有視訊監視監視。 一旦處置 bin 達到大約 50%容量，網站服務小組連絡人實體安全性小組，以協調移除。 網站服務人員及安全性 Office 移除的安全處置筒，並將它放在指定的安全的存放區中。 原則和控管自己期間處置具有裝置資料的處理程序會定期測試，包括程序，確保機器核准毀損的條件。

資料毀損程序，磁碟清除與 NIST 800-88 相容的方式 （如果可以的話） 並放置於工業碎機且實體摧毀。 Microsoft 的維護離開使用 NIST SP 800-88 一致清除/清除、 資產毀損、 加密、 準確清查、 追蹤，以及傳輸期間保護的監管鏈，資料中心資產的責任。 此程序透過關閉電路電視監視及毀損憑證發行完成時。

Microsoft 會使用資料清除單位，從[極端的通訊協定解決方案](https://www.enterprisedataerasure.com/)(EPS)。 EPS 軟體支援 NIST SP 800-88 需求清除和清除/安全清除。 之前清除或損毀，詳細目錄是由 Microsoft 資產管理員所建立。 如果廠商用於毀損，廠商所提供毀損的損毀，每個資產來驗證的資產管理員的憑證。

## <a name="virtual-data-destruction"></a>虛擬資料毀損

Microsoft 有資料處理原則和程序，能解決有效的虛擬損毀的資料進行保護，以在服務中實刪除之後不當共用服務租用戶或之間正在存取資料的可能性。 即使任何基礎的實體儲存裝置已重新指派，也無法存取另一個服務租用戶，從一個租用戶中的服務中刪除的資料。 這是用來擴充虛擬環境的多個虛擬化及分散情形技術的效果，計算結果、 作用中刪除內每個服務租用戶 （例如[分頁清空](https://docs.microsoft.com/office365/securitycompliance/office-365-exchange-online-data-deletion#page-zeroing)），和必要的應用程式的行為媒體和應用程式的內容加密程序。