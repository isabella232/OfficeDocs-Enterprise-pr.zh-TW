---
title: 權限存取 Office 365 中的管理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: 若要深入了解 Office 365 中的權限的存取管理功能使用本主題
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915388"
---
# <a name="privileged-access-management-in-office-365"></a>權限存取 Office 365 中的管理

> [!IMPORTANT]
> 本主題涵蓋 beta 公開功能僅在 Office 365 E5 和進階規範 Sku 中目前可用的部署和設定指導。

特殊存取權限管理 Office 365 中讓更精細的存取權限的管理工作的控制權。 它可協助保護您的組織中可以使用現有的權限的管理員帳戶具有出位置的存取權機密資料或重要的組態設定的存取權的缺口。啟用權限的存取管理、 之後使用者需要要求剛剛-時間存取完成核准工作流程高度範圍且時間繫結到提高權限與權限工作。這提供使用者剛-充份-存取可執行工作，反之，而不致洩露機密資料或重要的組態設定。啟用 Office 365 中的權限的存取管理可讓您的組織操作以零出位置的權限，並提供一層的防禦措施弱點引起因為這類出位置管理存取。 

本主題將引導您透過啟用及設定 Office 365 組織中的權限的存取管理並做為參考指南要求、 核准、 和管理功能。 

## <a name="before-you-begin"></a>開始之前

### <a name="limited-functionality"></a>有限的功能
Beta 公開期間特殊權限存取管理功能可用只能透過 Office 365 中的[Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) 。權限存取管理涵蓋之 Exchange 管理指令程式層級的工作定義。在未來 Office 365 發行、 權限的存取功能可透過系統入口網站與會涵蓋其他 Office 365 工作負載服務。

### <a name="connecting-to-exchange-online-powershell"></a>連線至 Exchange Online PowerShell
本主題中的設定步驟會引導您透過啟用及使用 Office 365 使用 Exchange Online PowerShell 中的權限的存取。 

請遵循步驟來啟用及設定貴組織的權限的存取 Office 365 認證以連線至 Exchange Online PowerShell[連線至 Exchange Online PowerShell 中使用多重要素驗證](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps)。

> [!NOTE]
> 您不需要啟用的 Office 365 組織使用的步驟來連線至 Exchange Online PowerShell 時啟用權限的存取多重要素驗證。以多重要素驗證連線建立簽署您要求的權限存取所使用的 OAuth 權杖。

## <a name="enable-and-configure-privileged-access-management"></a>啟用並設定權限的存取管理

### <a name="step-1---create-an-approvers-group"></a>步驟 1-建立核准者群組
從 Office 365 系統管理入口網站，選取 [**群組** > **加入群組**]，然後建立啟用郵件功能的安全性群組的預設權限存取核准者。完成後，選取 [**新增**] 以建立並儲存核准者群組。

![Office 365 系統入口網站的權限的存取核准者畫面](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> 在此階段中，只有系統管理存取權的使用者可以核准來自 Office 365 造就存取要求。在未來任何已核准者的群組之一部分的使用者將能夠核准存取要求。

### <a name="step-2---enable-privileged-access-in-office-365"></a>步驟 2-啟用 Office 365 中的權限的存取
權限的存取必須明確開啟與預設核准者群組且包含一組您想要排除的權限的存取管理存取控制的系統帳戶。 

若要啟用權限的存取及核准者群組指派 Exchange Online PowerShell 中執行下列命令：
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
範例：
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> 功能可供以確保您的組織內特定 automations 系統帳戶可以不相依性運作權限存取、 但還是建議也是這類排除是例外以及那些允許應該核准和稽核定期。

### <a name="step-3---create-an-approval-policy"></a>步驟 3-建立核准原則
核准原則可讓您定義在個別工作設定範圍的特定核准需求。核准類型選項會**自動**或**手動**。 

執行下列命令在 Exchange Online PowerShell 來定義核准原則：
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
範例：
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>在 Office 365 組織中使用特殊權限的存取

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>若要執行的工作要求的權限提高授權
一次啟用的權限存取需要核准在執行任何具有相關聯的核准原則所定義的工作。使用者執行工作包含在需要核准原則必須要求並以具有執行工作所需的權限授與存取權核准。

執行下列命令在 Exchange Online PowerShell 建立並送出至核准者群組核准要求：
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
範例：
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>檢視權限提高要求的狀態
建立核准要求之後，可以要求識別碼使用關聯檢閱提高權限要求狀態

執行下列命令在 Exchange Online PowerShell 來檢視特定要求識別碼核准要求狀態：
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
範例：
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>核准權限提高授權要求
相關的核准者群組的成員時建立核准要求時，會收到的電子郵件通知與可核准要求識別碼相關聯的要求 

執行下列命令在 Exchange Online PowerShell 核准權限提高授權要求：
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
範例：
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>拒絕權限提高授權要求
當建立核准要求時，相關的核准者群組的成員可以拒絕要求識別碼相關聯的要求 

執行下列命令在 Exchange Online PowerShell 拒絕權限提高授權要求：
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
範例：
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>執行工作
會授與核准之後，要求使用者可執行預定的工作及權限的存取將授權及使用者代理執行工作。核准保持有效的要求期間 （預設持續時間為 4 小時） 的期間要求者可執行預定的任務多次。所有這類執行記錄且可供安全性及規範稽核。 

### <a name="disable-privileged-access-in-office-365"></a>停用 Office 365 中的權限的存取
必要時，您可以停用 Office 365 中的權限的存取管理。停用權限存取不會刪除任何相關聯的核准原則或核准者群組。

執行下列命令在 Exchange Online Powershell 來停用權限的存取：

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>受管理的 Microsoft Graph in Microsoft Azure 存取

> [!IMPORTANT]
> 本節涵蓋有關目前只適用於預覽功能的詳細資訊。

受管理的存取權 Microsoft Graph in Microsoft Azure 是可幫助組織執行控制其 Office 365 資料細微層級的服務。此 system 允許應用程式開發人員創造見解與該資料。 

此系統使用特殊權限的 Office 365 存取來判斷提示透過其核准工作流程、 允許範圍與管理負責監督的 Office 365 資料存取其資料的控制權。應用程式在安裝好且需要存取 Office 365 資料甚至要求的資料。

### <a name="view-request-details"></a>檢視要求詳細資料
檢視 Office 365 資料存取權要求的詳細資料。

執行下列命令在 Exchange Online Powershell 來檢視資料要求：
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
範例輸出：
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>核准資料存取權要求
所有的資料存取權要求可以核准透過標準的權限的存取核准指令程式。

執行下列命令在 Exchange Online Powershell 核准所有資料要求特定的地方：

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
範例：
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>取得說明並提供意見反應
我們意識期間 beta 公開您可能會無意中偶發性的 bug 或有意見反應及建議在我們可以提升權限的存取管理的方式。我們值意見反應及鼓勵您與我們分享：
- 張貼意見反應 ad 建議[Office 預覽 Yammer 群組](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)中。
- 檔案[Office 預覽 VSO](https://office-previews.visualstudio.com/previews)區域路徑的 「 Office 365 權限存取管理 」 下您錯誤報告。

## <a name="frequently-asked-questions"></a>常見問題集

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>我需要哪些 Sku 使用特殊權限的存取 Office 365？
特殊權限存取 Office 365 中的管理只有目前客戶 E5 和進階規範 Sku。

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>何時將權限的存取可供使用 Office 365 工作負載超過 Exchange？
我們想要推出提供這項功能的其他 Office 365 工作負載。當我們已經準備好要共用時間表時，它會提供透過 Office 365 藍圖。

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>如何這是否為 Azure Active Directory 的權限的身分識別管理不同？
權限存取 Office 365 和[Azure AD 權限的身分識別管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)互補彼此提供存取控制中管理位於不同範圍的剛剛-時間存取權。一起提供強大的一組控制項為保護您的資料。

特殊權限存取 Office 365 中的管理可定義及 Azure AD 權限的身分識別管理層級的角色適用於與能夠執行多個工作時在任務層級設定範圍。 Azure AD 的權限身分識別管理主要是可讓管理 AD 角色和權限時的角色群組的存取 Office 365 中的存取管理會在任務層級套用。

 - **啟用權限存取 Office 365 中的管理已使用 Azure AD 權限的身分識別管理時：** 在 Office 365 中新增權限的存取管理可提供其他細微的圖層的保護及稽核功能的權限存取 Office 365 資料。

- **已經使用時啟用 Azure AD 權限的身分識別管理特殊權限存取管理 Office 365 中：** 新增至權限的 Azure AD 權限的身分識別管理存取管理 Office 365 中的可以擴充主要使用者的角色或身分識別所定義的 Office 365 外部資料的權限的存取。 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>是否需要是來管理 Office 365 中的權限的存取的全域系統管理員吗？
預覽期間您必須具備全域管理員能夠管理 Office 365 中的權限的存取的最低權限。包含在核准者群組的使用者不需要是檢閱和核准要求的全域系統管理員。 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>如何為客戶 Lockbox 相關的 Office 365 中的權限的存取管理？
[客戶 Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)允許存取控制組織依其服務提供者，例如 Microsoft 資料存取層級。特殊權限存取 Office 365 中的管理允許所有的特殊權限的 Office 365 工作的組織內的更精細的存取控制。