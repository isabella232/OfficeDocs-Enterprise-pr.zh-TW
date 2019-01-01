---
title: 使用 Office 365 PowerShell 檢視授權與服務
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/31/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 說明如何使用 Office 365 PowerShell 檢視授權的計劃、 服務及 Office 365 組織中可用的授權的相關資訊。
ms.openlocfilehash: dab6b8f1828c6be4d32bb2432437d23328653560
ms.sourcegitcommit: 6dd4ac5808d72406578fcc7be6590dd7a99cebea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2018
ms.locfileid: "27466872"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 檢視授權與服務

**摘要：** 說明如何使用 Office 365 PowerShell 檢視授權的計劃、 服務及 Office 365 組織中可用的授權的相關資訊。
  
每個 Office 365 訂閱包含下列元素：

- **授權計劃**這些也稱為是授權方案或 Office 365 計劃。授權方案定義使用者可用的 Office 365 服務。您的 Office 365 訂閱可能包含多個授權方案。範例的授權方案就是 Office 365 企業版 E3。
    
- **服務**這些也稱為是服務計劃。服務是 Office 365 產品、 功能及可用功能的每個授權的計畫，例如 Exchange Online 與 Office Professional Plus。使用者可以從不同的授權方案所授與不同的服務權限指派給他們的多個授權。
    
- **授權**每個授權方案包含您所購買的授權數。指派授權給使用者，以便他們可以使用 Office 365 服務授權方案所定義。每個使用者帳戶需要從一個授權計劃至少一個授權，讓他們可以登入 Office 365 並使用的服務。
    
您可以使用 Office 365 PowerShell Office 365 組織中檢視可用的授權方案、 授權及服務的相關的詳細資料。如需產品、 功能及不同 Office 365 訂閱中可用的服務的詳細資訊，請參閱[Office 365 計劃選項](https://go.microsoft.com/fwlink/p/?LinkId=691147)。

## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>檢視關於授權計劃與可用授權的資訊

若要檢視目前的授權方案和每種計劃可用授權的摘要資訊，請在 Office 365 PowerShell 中執行下列命令：
  
```
Get-MsolAccountSku
```

結果包含下列資訊：
  
- **AccountSkuId:** 使用下列的語法來顯示您的組織可用的授權方案`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_ 為您提供當您在 Office 365 中註冊並為您的組織是唯一的值。_<LicensingPlan>_ 值是每個人都相同。例如，在此值`litwareinc:ENTERPRISEPACK`、 公司名稱是`litwareinc`、 和授權的計劃名稱`ENTERPRISEPACK`，這是 Office 365 企業版 E3 系統名稱。
    
- **ActiveUnits:** 您已針對特定的授權方案購買的授權數目。
    
- **WarningUnits:** 您尚未已更新，並將期限 30 天的寬限期期間的授權方案中的授權數目。
    
- **ConsumedUnits:** 您已從特定的授權方案指派給使用者的授權數目。
    
若要檢視關於所有授權計劃中都可用的 Office 365 服務的詳細資訊，請執行下列命令：
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

下表顯示 Office 365 服務計劃和最常見的服務及其易記名稱。您的服務計劃清單可能會不同。 
  
|**服務計劃**|**描述**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 版權管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office 專業增強版  <br/> |
| `MCOSTANDARD` <br/> |商務用 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
如需授權計劃 （也稱為產品名稱）、 其包含的服務計劃和其對應的易記名稱的完整清單，請參閱[產品名稱和授權的服務計劃識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

若要檢視特定的授權方案中可用的 Office 365 服務相關的詳細資訊，請使用下列語法。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

此範例會顯示 litwareinc: enterprisepack (Office 365 企業版 E3) 的授權方案中可用的 Office 365 服務。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>第一次使用 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>另請參閱

- [使用 Office 365 PowerShell 檢視經授權與未經授權的使用者](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料](view-account-license-and-service-details-with-office-365-powershell.md)
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

