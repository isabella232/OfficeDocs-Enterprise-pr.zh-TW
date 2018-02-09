---
title: "使用 PowerShell 來執行完全移轉至 Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "摘要：了解如何使用 Windows PowerShell 來完全移轉至 Office 365。"
ms.openlocfilehash: 8181d59f53464034a584724dcb53956976c917dd
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>使用 PowerShell 來執行完全移轉至 Office 365

 **摘要：**了解如何使用 Windows PowerShell 來完全移轉至 Office 365。
  
您可以使用完全移轉，一次將所有使用者信箱的內容從來源電子郵件系統移轉到 Office 365。本文會引導您使用 Exchange Online PowerShell 來進行電子郵件完全移轉的工作。 
  
您可以檢閱[將電子郵件完全移轉到 Office 365 所需注意的事項](https://go.microsoft.com/fwlink/p/?LinkId=536688)主題以概略了解移轉程序。在熟悉該文章的內容後，請使用此主題來開始在不同電子郵件系統中移轉信箱。
  
> [!NOTE]
> 您也可以使用 Exchange 系統管理中心來執行完全移轉。請參閱[將電子郵件完全移轉到 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

完成此工作的預估時間：2-5 分鐘來建立移轉批次。啟動移轉批次之後，移轉所需的時間會依批次中的信箱數目、每個信箱的大小和可用的網路容量而有所不同。如需關於信箱移轉至 Office 365 時所需時間受其他哪些因素影響的詳細資訊，請參閱[移轉效能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。
  
您必須已獲指派的權限，才能執行此程序。若要查看您需要哪些權限，請參閱[收件者權限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主題中所含表格的「移轉」項目。
  
若要使用 Exchange Online PowerShell Cmdlet，您需要登入系統，並將 Cmdlet 匯入您的本機 Windows PowerShell 工作階段。請參閱[使用遠端 PowerShell 連線到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121) 的指示。
  
若需要移轉命令的完整清單，請參閱[移動與移轉 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
## <a name="migration-steps"></a>移轉步驟

### <a name="step-1-prepare-for-a-cutover-migration"></a>步驟 1：準備完全移轉
<a name="BK_Step1"> </a>

- **將內部部署 Exchange 組織新增為 Office 365 組織的公認網域。**移轉服務會使用內部部署信箱的 SMTP 位址，為新的 Office 365 信箱建立 Microsoft Online Services 使用者識別碼和電子郵件地址。如果 Exchange 網域不是 Office 365 組織的公認網域或主要網域，移轉會失敗。如需詳細資訊，請參閱[在 Office 365 中驗證您的網域](https://go.microsoft.com/fwlink/p/?LinkId=534110)。
    
- **在內部部署 Exchange 伺服器上設定 Outlook 無所不在。**電子郵件移轉服務會使用 RPC over HTTP (或 Outlook 無所不在) 連線至您的內部部署 Exchange 伺服器。如需如何為 Exchange 2010、Exchange 2007 和 Exchange 2003 設定 Outlook 無所不在的相關資訊，請參閱下列主題：
    
  - [Exchange 2010：啟用 Outlook 無所不在](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007：如何啟用 Outlook 無所不在](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003：RPC over HTTP 的部署案例](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [如何使用 Exchange 2003 設定 Outlook 無所不在](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > 您的 Outlook 無所不在組態必須以信任的憑證授權單位 (CA) 所核發的憑證設定。它無法以自我簽署的憑證設定。如需詳細資訊，請參閱[如何為 Outlook 無所不在設定 SSL](https://go.microsoft.com/fwlink/?LinkID=80875)。 
  
- **確認您可以使用 Outlook 無所不在連線至 Exchange 組織。**嘗試下列其中一種方法測試您的連線設定：
    
  - 從公司網路之外使用 Microsoft Outlook 連線至內部部署 Exchange 信箱。
    
  - 使用 Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) 測試連線設定。使用 Outlook 無所不在 (RPC over HTTP) 或 Outlook 自動探索測試。
    
  - 在 Exchange Online PowerShell 中執行下列命令。
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **指派必要權限給內部部署使用者帳戶來存取 Exchange 組織中的信箱。**您用來連線至內部部署 Exchange 組織的內部部署使用者帳戶 (也稱為「移轉系統管理員」)，必須有必要權限可存取您要移轉至 Office 365 的內部部署信箱。此使用者帳戶可用來建立內部部署組織的移轉端點。
    
    下列清單顯示使用完全移轉來移轉信箱時所需的系統管理權限。有三個可能的選項。
    
  - 移轉系統管理員在內部部署組織的 Active Directory 中必須是 **Domain Admins** 群組的成員。
    
    或
    
  - 移轉系統管理員必須具有每個內部部署信箱的 **FullAccess** 權限。
    
    或
    
  - 在儲存使用者信箱的內部部署信箱資料庫上，移轉系統管理員必須具有 **[以下列接收]** 權限。
    
- **停用整合通訊。**如果您要移轉的內部部署信箱已啟用整合通訊 (UM)，則移轉之前必須先在信箱上停用 UM。您可以在移轉完成之後，再於信箱上啟用 UM。
    
- **安全性群組和代理人** 電子郵件移轉服務無法偵測出內部部署 Active Directory 群組是否為安全性群組，因此無法將任何移轉的群組佈建為 Office 365 中的安全性群組。如果您希望 Office 365 租用戶中有安全性群組，則必須先在 Office 365 租用戶中佈建擁有郵件功能的空安全性群組，然後再開始進行完全移轉。此外，此移轉方法只會移動信箱、郵件使用者、郵件連絡人和擁有郵件功能的群組。如果有任何其他 Active Directory 物件 (例如，未移轉至 Office 365 的使用者) 被指派為要移轉之物件的主管或代理人，則必須先從要移轉的物件中加以移除，再進行移轉。
    
### <a name="step-2-create-a-migration-endpoint"></a>步驟 2：建立移轉端點
<a name="BK_Step2"> </a>

若要順利移轉電子郵件，Office 365 必須與來源電子郵件系統連線和通訊。為了這麼做，Office 365 會使用移轉端點。若要建立 Outlook 無所不在移轉端點以進行分段移轉，請先[連線至 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。 
  
若需要移轉命令的完整清單，請參閱[移動與移轉 Cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
在 Exchange Online PowerShell 中執行下列命令：
  
```
$Credentials = Get-Credential
```

此範例使用 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) Cmdlet 來取得並測試內部部署 Exchange 伺服器的連線設定，然後使用那些連線設定來建立名為 "CutoverEndpoint" 的移轉端點。
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> 藉由使用 **-TargetDatabase** 選項，可以使用 **New-MigrationEndpoint** Cmdlet 來指定要使用之服務的資料庫。否則系統會從管理信箱所在的 Active Directory Federation Services (AD FS) 2.0 網站隨機指派資料庫。
  
#### <a name="verify-it-worked"></a>確認是否正常運作

在 Exchange Online PowerShell 中執行下列命令來顯示 "CutoverEndpoint" 移轉端點的資訊：
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>步驟 3：建立完全移轉批次
<a name="BK_Step3"> </a>

您可以在 Exchange Online PowerShell 中使用 **New-MigrationBatch** Cmdlet，為完全移轉建立移轉批次。您可以建立移轉批次，並加上 _AutoStart_ 參數來自動啟動它。或者，您也可以先建立移轉批次，以後再手動使用 **Start-MigrationBatch** Cmdlet 啟動它。本範例會建立名為 "CutoverBatch" 的移轉批次，並使用上一個步驟中建立的移轉端點。
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

本範例也會建立名為 "CutoverBatch" 的移轉批次，並使用上一個步驟中建立的移轉端點。因為其中並未加上  _AutoStart_ 參數，所以需要在移轉儀表板上或使用 **Start-MigrationBatch** Cmdlet 來手動啟動此移轉批次。如前所述，一次只能有一個完全移轉批次。
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>確認是否正常運作

若要確認您已順利為完全移轉建立移轉批次，請在 Exchange Online PowerShell 中執行下列命令來顯示新移轉批次的資訊：
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>步驟 4：啟動完全移轉批次
<a name="BK_Step4"> </a>

若要在 Exchange Online PowerShell 中啟動移轉批次，請執行下列命令。這樣會建立名為 "CutoverBatch" 的移轉批次。
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>確認是否正常運作

如果移轉批次已順利啟動，則其在移轉儀表板上的狀態會指定為「正在同步處理」。若要確認您已使用 Exchange Online PowerShell 成功啟動移轉批次，請執行下列命令：
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>步驟 5：將電子郵件路由傳送至 Office 365
<a name="BK_Step5"> </a>

電子郵件系統使用稱為 MX 記錄的 DNS 記錄來找出要將電子郵件傳遞到哪裡。在電子郵件移轉過程中，您的 MX 記錄指向來源電子郵件系統。既然電子郵件已移轉至 Office 365，現在該將 MX 記錄指向 Office 365。這有助於確保電子郵件會傳遞至您的 Office 365 信箱。藉由移動 MX 記錄，您也可以在準備好時關閉舊的電子郵件系統。 
  
我們針對許多 DNS 提供者提供[變更 MX 記錄](https://go.microsoft.com/fwlink/p/?LinkId=279163)的特定指示。如果您的 DNS 提供者不在其中，或如果您想要了解一般指示，我們也提供[在任一 DNS 主機服務提供者建立 Office 365 的 DNS 記錄](https://go.microsoft.com/fwlink/?LinkId=397449)。
  
您的客戶與合作夥伴的電子郵件系統最多可能需要 72 小時才能辨識已變更的 MX 記錄。請至少等待 72 小時，再繼續進行下一個工作： [步驟 6：刪除完全移轉批次](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>步驟 6：刪除完全移轉批次
<a name="Bk_step6"> </a>

在變更 MX 記錄並確認所有電子郵件會路由傳送到 Office 365 信箱後，通知使用者他們的郵件將移至 Office 365。在此之後，您便可以刪除完全移轉批次。在刪除移轉批次之前，請先確認下列事項。
  
- 所有的使用者都使用 Office 365 信箱。刪除批次之後，傳送到內部部署 Exchange Server 信箱的郵件，就不會複製到對應的 Office 365 信箱。
    
- 郵件開始直接傳送給 Office 365 信箱後，信箱至少已同步一次。若要這麼做，請確定移轉批次的 [上次同步時間] 方塊中的值，比郵件開始直接路由傳送到 Office 365 信箱時更新。
    
若要在 Exchange Online PowerShell 中刪除 "CutoverBatch" 移轉批次，請執行下列命令：
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>第 7 節：指派使用者授權
<a name="BK_Step7"> </a>

 **藉由指派授權，為移轉的帳戶啟動 Office 365 使用者帳戶。**如果您未指派授權，則當寬限期 (30 天) 結束時就會停用信箱。若要在 Office 365 系統管理中心 中指派授權，請參閱[指派或解除指派商務用 Office 365 的授權](https://go.microsoft.com/fwlink/?LinkId=536681)。
  
### <a name="step-8-complete-post-migration-tasks"></a>步驟 8：完成移轉後工作
<a name="BK_Step8"> </a>

- **建立自動探索 DNS 記錄，讓使用者可以輕鬆存取信箱。**將所有內部部署信箱移轉至 Office 365 後，您可以為 Office 365 組織設定自動探索 DNS 記錄，讓使用者能夠以 Outlook 和行動用戶端輕鬆連線至新的 Office 365 信箱。這個新的自動探索 DNS 記錄必須使用和您的 Office 365 組織所用相同的命名空間。舉例來說，如果您的雲端架構命名空間是 cloud.contoso.com，則您需要建立的自動探索 DNS 記錄是 autodiscover.cloud.contoso.com。
    
    如果保留 Exchange Server，您也應該確定自動探索 DNS CNAME 記錄在移轉後必須在內部和外部 DNS 中指向 Office 365，Outlook 用戶端才會連線至正確的信箱。
    
    > [!NOTE]
    >  在 Exchange 2007、Exchange 2010 和 Exchange 2013 中，您也應該將  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 設為 `Null`。 
  
    Office 365 會使用 CNAME 記錄來實作 Outlook 和行動用戶端的自動探索服務。自動探索 CNAME 記錄必須包含下列資訊：
    
  - **別名：**自動探索
    
  - **目標：**autodiscover.outlook.com
    
    如需詳細資訊，請參閱[管理 DNS 記錄時為 Office 365 建立 DNS 記錄](https://go.microsoft.com/fwlink/p/?LinkId=535028)。
    
- **解除委任內部部署 Exchange 伺服器。**確認所有電子郵件會直接路由傳送到 Office 365 信箱後，如果不再需要維護內部部署電子郵件組織，或沒打算實作單一登入 (SSO) 解決方案，您可以從伺服器解除安裝 Exchange，並移除內部部署 Exchange 組織。
    
    如需詳細資訊，請參閱下列各主題：
    
  - [修改及移除 Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [如何移除 Exchange 2007 組織](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [如何解除安裝 Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

