---
title: 非路由傳送的網域準備目錄同步作業
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: 了解新如果有非 routale 網域與 Office 365 同步處理之前與您的內部部署使用者相關聯。
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674437"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>非路由傳送的網域準備目錄同步作業
當您與 Office 365 同步處理您的內部部署目錄必須有 Azure Active Directory 中的已驗證的網域。僅限使用者主體名稱 (UPN) 相關聯的內部部署網域進行同步處理。不過，包含非路由傳送的網域，例如.local （例如 billa@contoso.local)、 任何 UPN 會同步處理至。 onmicrosoft.com 網域 （例如 billa@contoso.onmicrosoft.com)。 

如果您目前使用.local 網域在 Active Directory 中的使用者帳戶的建議變更他們能夠使用才能正確同步處理您的 Office 365 網域與已驗證的網域 （例如 billa@contoso.com)。
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>如果僅有.local 內部網域吗？

您可以使用 Azure Active directory Active Directory 同步處理的最新工具名為 Azure AD 連線]。如需詳細資訊，請參閱[您的內部部署身分識別與 Azure Active Directory 的整合](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。
  
Azure AD 連線同步處理使用者的 UPN 和密碼，讓使用者可以登入使用的相同認證他們使用內部部署。不過，Azure AD 連接僅同步處理至 Office 365 檢定的網域的使用者。這表示該網域也會通過 Azure Active Directory 因為 Azure Active Directory 管理 Office 365 身分識別。換句話說，網域必須為有效的網際網路網域 （例如.com、.org、.net、.us 等等）。如果您內部部署 Active Directory 僅使用非路由傳送的網域 (例如.local)，這可能是不能符合 Office 365 中有已驗證的網域。您可以透過變更主要在您內部部署 Active Directory 網域或新增一或多個 UPN 尾碼來修正此問題。
  
### <a name="change-your-primary-domain"></a>**變更主要網域**

變更至您已在 Office 365，例如，contoso.com 中驗證網域的主要網域。每個使用者而言具有網域 contoso.local 然後更新為 contoso.com。指示，請參閱[網域重新命名的運作方式](https://go.microsoft.com/fwlink/p/?LinkId=624174)。這是非常相關的程序，但並更輕鬆地解決方案是若要[新增的 UPN 尾碼並更新其使用者](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register)下, 一節所示。
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**新增的 UPN 尾碼並更新其使用者**

您可以解決.local 問題您在 Office 365 中所要比對 （或多個網域） 的 Active Directory 中註冊新的 UPN 尾碼驗證。註冊新的後置詞後，您會更新使用者以.local 取代新網域名稱的範例會使起來 billa@contoso.com 的使用者帳戶的 Upn。
  
您已更新 Upn 来使用的已驗證的網域之後，您就可以與 Office 365 同步處理您的內部部署 Active Directory。
  
 **步驟 1： 將新的 UPN 尾碼新增**
  
1. 在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory 網域及信任**。
    
    **或者，您不需要 Windows Server 2012**
    
    若要開啟 [**執行**] 對話方塊，然後輸入 Domain.msc，在按**Windows 鍵 + R** ，然後選擇 **[確定]**。
    
    ![選擇 [Active Directory 網域及信任]。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. 在 [ **Active Directory 網域及信任**] 視窗中，以滑鼠右鍵按一下 [ **Active Directory 網域及信任**、，然後選擇**屬性**。
    
    ![ActiveDirectory 網域及信任上按一下滑鼠右鍵並選擇屬性](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. 在 [ **UPN 尾碼**] 索引標籤上 [**替用的 UPN 尾碼**] 方塊中輸入新的 UPN 尾碼或尾碼，然後按**新增** \> **套用**。
    
    ![將新的 UPN 尾碼新增](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    選擇 **[確定]** 完成新增尾碼時。 
    
 **步驟 2： 變更現有使用者的 UPN 尾碼**
  
1. 在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory 的 Active Directory 使用者及電腦**。
    
    **或者，您不需要 Windows Server 2012**
    
    若要開啟 [**執行**] 對話方塊，然後輸入 [dsa.msc]，在按**Windows 鍵 + R** ，然後按一下 [**確定]**
    
2. 選取 [使用者] 中，按一下滑鼠右鍵，然後選擇 [**內容**。
    
3. 在**帳戶**] 索引標籤的 [UPN 尾碼下拉式清單中，選擇新的 UPN 尾碼，然後再選擇 **[確定]**。
    
    ![新增新使用者的 UPN 尾碼](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 完成這些步驟的每位使用者。
    
    或者您可以大量更新 UPN 尾碼[您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh)。
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼**

如果您有許多使用者更新的很容易使用 Windows PowerShell。下列範例會使用[Get ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312)與[組 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313)指令程式來變更為 contoso.com 的所有 contoso.local 尾碼。 

執行下列 Windows PowerShell 命令來更新為 contoso.com 的所有 contoso.local 尾碼：
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
若要深入了解在 Active Directory 中使用 Windows PowerShell 查看[Active Directory Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=624314)。 

