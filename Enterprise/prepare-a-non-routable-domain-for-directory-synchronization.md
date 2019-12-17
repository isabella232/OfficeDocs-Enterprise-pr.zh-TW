---
title: 準備目錄同步處理的非路由傳送的網域
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: 了解要執行如果您有非 routale 網域，再進行同步處理與 Office 365 與內部部署使用者相關聯的動作。
ms.openlocfilehash: 013d29acdd3761793a93dab1eb8583324ba08591
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072415"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>準備目錄同步處理的非路由傳送的網域
當您同步處理您的內部部署目錄與 Office 365，您必須要有 Azure Active Directory 中的已驗證的網域。 僅限使用者主要名稱 (UPN) 相關聯的內部部署網域同步處理。 不過，任何 UPN 包含非路由傳送的網域，例如.local （例如 billa@contoso.local)，將會同步處理到。 onmicrosoft.com 網域 （例如 billa@contoso.onmicrosoft.com)。 

如果您目前使用.local 網域，建議您變更他們才能正確地同步處理與您的 Office 365 網域使用驗證的網域 （例如 billa@contoso.com) 在 Active Directory 使用者帳戶。
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>如果僅有.local 內部網域？

您可以使用同步處理您的 Active Directory 至 Azure Active Directory 的最新工具是名為 Azure AD Connect。 如需詳細資訊，請參閱[將內部部署識別與 Azure Active Directory 整合](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。
  
Azure AD Connect 進行同步處理使用者的 UPN 與密碼，讓使用者可以登入相同的認證他們使用內部部署。 不過，Azure AD Connect 只會同步處理至 Office 365 所驗證的網域的使用者。 這表示，網域也驗證 Azure Active directory 因為由 Azure Active Directory 管理 Office 365 身分識別。 換句話說，網域必須是有效的網際網路網域 （例如，.com、.org、.net、.us 等等）。 如果您內部部署 Active Directory 只使用非路由傳送的網域 (例如.local)，這可能無法符合您有 Office 365 的已驗證的網域。 若要修正此問題，您可以藉由變更您在您內部部署 Active Directory 中的主要網域，或藉由新增一或多個 UPN 尾碼。
  
### <a name="change-your-primary-domain"></a>**變更主要網域**

變更至您已在 Office 365，例如，contoso.com 中驗證網域的主要網域。 每個使用者都會具有網域 contoso.local 再將更新為 contoso.com。 如需相關指示，請參閱[網域重新命名的運作方式](https://go.microsoft.com/fwlink/p/?LinkId=624174)。 這是非常複雜的過程中，不過，與下一節說明簡單的解決方案。
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**新增的 UPN 尾碼和這些更新您的使用者**

您可以解決.local 問題您在 Office 365 中要比對 （或多個網域） 的 Active Directory 中註冊新的 UPN 尾碼驗證。 註冊新的尾碼之後，您會更新使用者以新的網域名稱，例如.local 取代，因此，使用者帳戶看起來像 billa@contoso.com Upn。
  
您已更新若要使用的已驗證的網域 Upn 之後，您已準備好將您的內部部署 Active Directory 與 Office 365 同步處理。
  
 **步驟 1： 將新的 UPN 尾碼新增**
  
1. 在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory 網域及信任**。
    
    **或者，如果您不需要 Windows Server 2012**
    
    若要開啟 [**執行**] 對話方塊中，然後輸入 Domain.msc，在按下**Windows 鍵 + R** ，然後選擇 [**確定]**。
    
    ![選擇 [Active Directory 網域及信任]。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. 在 [ **Active Directory 網域及信任**] 視窗中，以滑鼠右鍵按一下 [ **Active Directory 網域及信任**，，然後選擇**屬性**。
    
    ![ActiveDirectory 網域及信任上按一下滑鼠右鍵，然後選擇 [屬性](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. 在 [ **UPN 尾碼**] 索引標籤，在**替代的 UPN 尾碼**] 方塊中，輸入您新的 UPN 尾碼或尾碼，，然後選擇 [ **Add** \> **套用**。
    
    ![新增新的 UPN 尾碼](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    當您完成新增尾碼，請選擇 [**確定]** 。 
    
 **步驟 2： 變更現有使用者的 UPN 尾碼**
  
1. 在 [伺服器管理員在伺服器上執行 Active Directory 網域服務 (AD DS) 上，選擇**工具** \> **Active Directory Active Directory 使用者和電腦**。
    
    **或者，如果您不需要 Windows Server 2012**
    
    以開啟 [**執行**] 對話方塊中，，然後輸入 [Dsa.msc，在按下**Windows 鍵 + R** ，然後按一下 [**確定]**
    
2. 選取 [使用者]，按一下滑鼠右鍵，然後選擇 [**內容**。
    
3. 在 [**帳戶**] 索引標籤中，在 [UPN 尾碼] 下拉式清單中，選擇新的 UPN 尾碼，，然後選擇 [**確定]**。
    
    ![新增新使用者的 UPN 尾碼](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 完成下列步驟，將每一位使用者。
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼**

如果您有大量的使用者更新時，會比較容易使用 Windows PowerShell。 下列範例會使用的指令程式，[取得 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312)和[設定 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313)若要將所有 contoso.local 尾碼都變更為 contoso.com。 

執行下列 Windows PowerShell 命令，以更新為 contoso.com 的所有 contoso.local 尾碼：
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

若要深入了解在 Active Directory 中使用 Windows PowerShell，請參閱[Active Directory Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=624314)。 

