---
title: Office 365 IP 位址和 URL Web 服務中未包含的其他端點
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/23/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 摘要：新端點 Web 服務不包含特定案例的少量端點。
hideEdit: true
ms.openlocfilehash: 1d551f8757464aa1336bc351de8689c103f0a54f
ms.sourcegitcommit: d93f7a51e8cdefdfc9933cdf1f9e413b013bb367
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "25719007"
---
# <a name="additional-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Office 365 IP 位址和 URL Web 服務中未包含的其他端點

某些網路端點之前已經發佈，而且尚未包含在 [Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)中。Web 服務範圍是從 Office 365 使用者到整個企業周邊網路之連線能力所需的網路端點。這目前未包含：

1. 從 Microsoft 資料中心到客戶網路可能需要的網路連線 (內送混合式伺服器網路流量)。
2. 從客戶網路上的伺服器到整個企業周邊的網路連線能力 (外寄伺服器網路流量)。
3. 使用者網路連線能力需求的另類案例。
4. DNS 解析連線能力需求 (以下未列出)。
5. Internet Explorer 或 Microsoft Edge 信任的網站。

除了 DNS 以外，對大多數客戶來說，這些全都是選用，除非您需要所述的特定案例。

|||||
|:-----|:-----|:-----|:-----|
| **列** | **用途** | **目的地** | **類型** |
| 1  | PST 的[匯入服務](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)和檔案擷取 | 如需其他需求的資訊，請參閱[匯入服務](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)。 | 另類外寄範例 |
| 2  | [適用於 Office 365 的 Microsoft 支援及修復小幫手](https://diagnostics.office.com/#/) - 驗證單一登入使用者認證。來源：<br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | 內部部署安全性權杖服務 | 內送伺服器流量 |
| 3  | Azure AD Connect (含 SSO 選項) – WinRM 和遠端 PowerShell | 客戶 STS 環境 (AD FS 伺服器和 AD FS Proxy) \| TCP 通訊埠 80 和 443 | 內送伺服器流量 |
| 4  | STS，例如 AD FS Proxy 伺服器 (僅適用於同盟客戶) | 客戶 STS (例如 AD FS Proxy) \| 通訊埠 TCP 443 或 TCP 49443 (含 ClientTLS) | 內送伺服器流量 |
| 5  | [Exchange Online 整合通訊/SBC 整合](https://technet.microsoft.com/library/jj673565.aspx) | 在內部部署工作階段邊界控制器與 *.um.outlook.com 之間為雙向 | 僅限外寄伺服器的流量 |
| 6  | [Exchange 混合式](https://docs.microsoft.com/exchange/exchange-deployment-assistant)共存功能，例如空閒/忙碌共用。 | 客戶內部部署 Exchange 伺服器 | 內送伺服器流量 |
| 7  | [Exchange 混合式](https://docs.microsoft.com/exchange/exchange-deployment-assistant) Proxy 驗證 | 客戶內部部署 STS | 內送伺服器流量 |
| 8  | 用來設定 [Exchange 混合式](https://docs.microsoft.com/exchange/exchange-deployment-assistant)，使用 Exchange 混合式組態精靈。 <br> 附註：只有在設定 Exchange 混合式時，才需要這些端點  | TCP 通訊埠 80 和 443 上的 ```domains.live.com```，只有 Exchange 2010 SP3 混合式組態精靈才需要。 | 僅限外寄伺服器的流量 |
| 9  | 自動偵測服務用於 [Exchange 混合式](https://docs.microsoft.com/exchange/exchange-deployment-assistant)案例，搭配 [iOS 版 Outlook 和 Android 的混合式新式驗證](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <BR> <BR> ```*.acompli.net``` <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | 客戶在 TCP 443 上內部部署 Exchange 伺服器 | 內送伺服器流量 |
| 10  | Office 2016 中的商務用 Skype 包含使用 UDP 通訊埠根據螢幕共用的視訊。Office 2013 及較舊版本中的商務用 Skype 用戶端在 TCP 通訊埠 443 上使用 RDP。 | TCP 通訊埠 443 開放給 52.112.0.0/14 | Office 2013 及較舊版本中的商務用 Skype 更舊用戶端版本 |
| 11  | 商務用 Skype 混合式內部部署伺服器連線至商務用 Skype Online | 13.107.64.0/18, 52.112.0.0/14 UDP 通訊埠 50,000-59,999 <BR>  TCP 通訊埠 50,000-59,999 | 商務用 Skype 內部部署伺服器輸出連線 |
| 12  | 具有內部部署混合式連線的 Cloud PSTN 要求開啟內部部署主機的網路連線。如需商務用 Skype Online 混合式設定的詳細資料，  | 請參閱[商務用 Skype 混合式解決方案](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/skype-for-business-hybrid-solutions) | 商務用 Skype 內部部署混合式輸入 |
| 13  | **驗證與身分識別 FQDN** <br> FQDN ```secure.aadcdn.microsoftonline-p.com``` 必須在您用戶端的 Internet Explorer (IE) 或 Microsoft Edge 信任的網站區域中才能正常運作。 |  | 信任的網站 |
| 14  |  **Microsoft Teams FQDN** <br> 如果您使用的是 Internet Explorer 或 Microsoft Edge，您需要啟用第一和第三方 Cookie，並將 Teams 的 FQDN 新增到您的 [信任的網站] 中。這是上述所列之跨套件 FQDN、CDN 和遙測之外的項目。如需詳細資訊，請參閱 [Microsoft Teams 的已知問題](https://docs.microsoft.com/microsoftteams/known-issues)。 |  | 信任的網站 |
| 15  |  **SharePoint Online 和商務用 OneDrive FQDN** <br> 所有 FQDN 中含有 '\<租用戶>' 的 '.sharepoint.com' FQDN 都必須在您用戶端的 IE 或 Microsoft Edge 信任的網站區域中才能正常運作。除了上述列出的跨套件 FQDN、CDN 和遙測，您也必須新增這些端點。 |  | 信任的網站 |
| 16  | **Yammer**  <br> Yammer 僅可於瀏覽器中使用，且必須透過 Proxy 傳遞已驗證的使用者。所有 Yammer FQDN 都必須在用戶端的 IE 或 Microsoft Edge 的信任的網站區域中才能正常運作。 |  | 信任的網站 |

## <a name="related-topics"></a>相關主題

[管理 Office 365 端點](managing-office-365-endpoints.md)
  
[Office 365 連線能力疑難排解](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[用戶端連線](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[內容傳遞網路](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure Datacenter IP 範圍](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公用 IP 空間](https://www.microsoft.com/download/details.aspx?id=53602)

