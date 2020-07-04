---
title: Office 365 的外部網域名稱系統記錄
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 摘要：規劃 Office 365 部署時使用的 DNS 記錄參考清單。
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996537"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Office 365 的外部網域名稱系統記錄

|||
|:-----|:-----|
|![網域](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **回到** [Office 365 的網路規劃和效能調整](https://aka.ms/tune)。  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Office 365 (核心服務) 所需的外部 DNS 記錄
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**DNS 記錄** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**CNAME** <br/> **(套裝軟體)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **注意：** 此 CNAME 僅適用於 21Vianet 運作的 Office 365。   |**別名：** msoid  <br/> **目標：** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(網域驗證)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**主機：**@ (或者對某些 DNS 主機服務提供者來說是您的網域名稱)  <br/> **TXT 值：** _下者提供的文字字串：_ Office 365  <br/> Office 365 [網域設定]**** 精靈提供用來建立此項記錄的值。  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Office 365 中電子郵件所需的外部 DNS 記錄 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **自動探索記錄**允許用戶端電腦自動尋找 Exchange 並正確地設定用戶端。

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
您只想將一小部分的電子郵件地址切換至 Office 365？ 您可以[使用自訂網域的多個電子郵件地址來試驗 Office 365](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7)。

- **SPF 的 TXT 記錄**：供收件者電子郵件系統用來驗證傳送您電子郵件的伺服器是否經過您的核准。 這有助於防範電子郵件詐騙和網路釣魚這類問題。 請參閱本文中的 [SPF 所需的外部 DNS 記錄](external-domain-name-system-records.md#BKMK_SPFrecords)，協助您了解記錄中要包括的內容。

使用 Exchange 同盟的電子郵件客戶也必須擁有列在表格底部的額外 CNAME 和 TXT 記錄。
  
||||
|:-----|:-----|:-----|
|**DNS 記錄** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**別名：** 自動探索  <br/> **目標：** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |將網域的內送郵件傳送到 Office 365 中的 Exchange Online 服務。  <br/> [!NOTE] 一旦電子郵件流向 Exchange Online，您應該移除指向舊系統的 MX 記錄。   |**網域：** 例如，contoso.com  <br/> **目標電子郵件伺服器：** \<MX token\> 。mail.protection.outlook.com  <br/> **喜好設定/優先順序：** 低於其他任何 MX 記錄 (這可確保已傳遞郵件至 Exchange Online) - 如 1 或「低」  <br/>  請 \<MX token\> 遵循下列步驟來尋找：  <br/>  登入 Office 365，前往 Office 365 系統管理員\>網域。  <br/>  在您網域的 [動作] 欄中選擇「修正問題」。  <br/>  在 [MX 記錄] 區段中，選擇「我要修正什麼？」  <br/>  遵循此頁面上的指示更新您的 MX 記錄。  <br/> [什麼是 MX 優先順序？](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[SPF 所需的外部 DNS 記錄](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange 同盟)** <br/> |用於混合部署的 Exchange 同盟。  <br/> |**TXT 記錄 1：** 例如，contoso.com 和自訂產生的相關網域證明雜湊文字 (如 Y96nu89138789315669824)  <br/> **TXT 記錄 2：** 例如，exchangedelegation.contoso.com 和自訂產生的相關網域證明雜湊文字 (如 Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange 同盟)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**別名：** 例如， Autodiscover.service.contoso.com  <br/> **目標：** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>商務用 Skype Online 所需的外部 DNS 記錄
<a name="BKMK_ReqdCore"> </a>

當您使用 [Office 365 URL 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) (英文) 時，需採取特定的步驟以確認您的網路已正確設定。

> [!NOTE]
> 這些 DNS 記錄也適用於 Teams，特別是在混合式 Teams 和商務用 Skype Online 案例中，其中可能會發生某些同盟問題。
  
||||
|:-----|:-----|:-----|
|**DNS 記錄** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**SRV** <br/> **(商務用 Skype Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**服務：** sipfederationtls  <br/> **通訊協定：** TCP  <br/> **優先順序：** 100  <br/> **加權：** 1  <br/> **連接埠：** 5061  <br/> **目標：** sipfed.online.lync.com  <br/> **注意：** 如果防火牆或 Proxy 伺服器封鎖外部 DNS 的 SRV 查閱，您應將此記錄新增至內部 DNS 記錄。   |
|**SRV** <br/> **(商務用 Skype Online)** <br/> |商務用 Skype 會使用它來協調 Lync 用戶端之間的資訊流程。  <br/> |**服務：** sip  <br/> **通訊協定：** TLS  <br/> **優先順序：** 100  <br/> **加權：** 1  <br/> **連接埠：** 443  <br/> **目標：** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(商務用 Skype Online)** <br/> |Lync 用戶端會使用它來協助尋找商務用 Skype Online 服務並登入。  <br/> |**別名：** sip  <br/> **目標：** sipdir.online.lync.com  <br/> 如需詳細資訊，請參閱 [Office 365 URL 和 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) (英文)。  <br/> |
|**CNAME** <br/> **(商務用 Skype Online)** <br/> |Lync 行動用戶端會使用它來協助尋找商務用 Skype Online 服務並登入。  <br/> |**別名：** lyncdiscover  <br/> **目標：** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Office 365 單一登入所需的外部 DNS 記錄
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**DNS 記錄** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**主機 (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**目標：** 例如，sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF 所需的外部 DNS 記錄
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>SPF 記錄的結構

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

如果電子郵件系統收到來自您網域的電子郵件，該系統便會查看 SPF 記錄，如果傳送郵件的電子郵件伺服器是 Office 365 伺服器，則系統就會接受電子郵件。 舉例來說，如果傳送郵件的伺服器是您的舊郵件系統或網際網路上的惡意系統，則 SPF 檢查可能會失敗，就無法傳遞郵件。 這類檢查可協助防範詐騙和網路釣魚郵件。
  
### <a name="choose-the-spf-record-structure-you-need"></a>選擇您所需要的 SPF 記錄結構

在您不只使用 Office 365 的 Exchange Online 電子郵件的情況下，(例如，當您也使用來自 SharePoint Online 的電子郵件時)，使用下表來決定要包含在記錄值中的內容。
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||如果您正在使用...  <br/> |用途  <br/> |新增這些包含項目  <br/> |
|1   <br/> |所有的電子郵件系統 (必要)  <br/> |以此值開頭的所有 SPF 記錄  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (普遍)  <br/> |僅搭配使用 Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |協力廠商電子郵件系統 (較不普遍)  <br/> ||包含：\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |內部部署郵件系統 (較不普遍)  <br/> |如果您正在使用 Exchange Online Protection 或 Exchange Online 加上另一個郵件系統，則請使用  <br/> |ip4：\<0.0.0.0\>  <br/> ip6：\< : : \>  <br/> 包含：\<mail.contoso.com\>  <br/> 括號中的值 (\<\>) 應為可傳送電子郵件的其他郵件系統。  <br/> |
|5   <br/> |所有的電子郵件系統 (必要)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>範例：新增至現有的 SPF 記錄
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

現在您正在更新 Office 365 的 SPF 記錄。 您將會編輯您的目前記錄，讓您有包括所需值的 SPF 記錄。 若為 Office 365，則為 "spf.protection.outlook.com"。
  
正確：
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

不正確：
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>常見 SPF 值的更多範例
<a name="bkmk_addtospf"> </a>

如果您使用完整的 Office 365 套件，且使用 MailChimp 代表您傳送行銷電子郵件，則 contoso.com 中的 SPF 記錄看起來可能如下所示，它會使用上表中的資料列1、3和5。 請記住，第1列和第5列是必要的。
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

或者，如果您擁有 Exchange 混合式組態，其中電子郵件的傳送來源為 Office 365 及您的內部部署郵件系統，您在 contoso.com 的 SPF 記錄看起來可能如下：
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
您可以使用下列短連結返回這裡：[https://aka.ms/o365edns](https://aka.ms/o365edns)
