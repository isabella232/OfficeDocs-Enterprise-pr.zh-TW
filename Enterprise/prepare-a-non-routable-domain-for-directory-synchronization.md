---
title: 為目錄同步處理準備不可路由的網域
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
description: 如果您在與 Office 365 同步處理之前, 您有與內部部署使用者相關聯的非 routale 網域, 請瞭解要執行的操作。
ms.openlocfilehash: cf7b901c3aaf6f49e4ecd92d27b9a6d9b8951d40
ms.sourcegitcommit: b4c82c0bf61f50386e534ad23479b5cf84f4e2ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "35203632"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>為目錄同步處理準備不可路由的網域
當您將內部部署目錄與 Office 365 同步處理時, 您必須在 Azure Active Directory 中有一個已驗證的網域。 只會同步處理與內部部署網域相關聯的使用者主體名稱 (UPN)。 不過, 任何包含非可路由傳送網域的 UPN, 例如, 本機 (如 billa @ contoso) 將會同步到 onmicrosoft.com 網域 (例如 billa@contoso.onmicrosoft.com)。 

如果您目前在 Active Directory 中為使用者帳戶使用的是本機網域, 建議您將其變更為使用驗證的網域 (例如 billa@contoso.com), 以便正確地與 Office 365 網域進行同步處理。
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>如果我只有內部部署網域, 該怎麼辦？

您可以用來將 Active Directory 同步處理至 Azure Active Directory 的最新工具, 稱為 Azure AD Connect。 如需詳細資訊，請參閱[將內部部署識別與 Azure Active Directory 整合](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。
  
Azure AD Connect 會同步處理您的使用者的 UPN 和密碼, 讓使用者可以使用內部部署所使用的相同認證來登入。 不過, Azure AD Connect 只會同步處理使用者至 Office 365 所驗證的網域。 這表示網域也會由 Azure Active Directory 驗證, 因為 Office 365 identity 是由 Azure Active Directory 來管理。 換句話說, 網域必須是有效的網際網路網域 (例如, .com、org、.net、us 等等)。 如果您的內部 Active Directory 只使用不可路由的網域 (例如, local), 則這不可能符合您在 Office 365 上已驗證的網域。 您可以在內部部署 Active Directory 中變更您的主要網域, 或新增一或多個 UPN 尾碼, 以修正此問題。
  
### <a name="change-your-primary-domain"></a>**變更您的主要網域**

將您的主要網域變更為您在 Office 365 中驗證的網域, 例如 contoso.com。 擁有網域 contoso 的每個使用者都會更新為 contoso.com。 如需相關指示, 請參閱[網域重新命名的運作方式](https://go.microsoft.com/fwlink/p/?LinkId=624174)。 這是一個非常相關的程式, 但下一節將說明更簡單的解決方案。
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**新增 UPN 尾碼並更新您的使用者**

您可以在 Active Directory 中註冊新的 UPN 尾碼或尾碼, 以符合您在 Office 365 中驗證的網域 (或網域), 解決本機問題。 註冊新的尾碼後, 請更新使用者 Upn 以將 local 取代為新的功能變數名稱 (例如, 讓使用者帳戶看起來像 billa@contoso.com)。
  
將 Upn 更新為使用驗證過的網域之後, 就可以將您的內部部署 Active Directory 與 Office 365 同步處理。
  
 **步驟 1: 新增 UPN 尾碼**
  
1. 在 Active Directory 網域服務 (AD DS) 執行所在的伺服器上, 于 [伺服器管理員] 中選擇 [**工具** \> ] [ **Active Directory 網域及信任**]。
    
    **或者, 如果您沒有 Windows Server 2012**
    
    按**Windows 鍵 + R**以開啟 [**執行**] 對話方塊, 然後在 [services.msc] 中輸入, 然後選擇 **[確定]**。
    
    ![選擇 [Active Directory 網域及信任]。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. 在 [ **Active Directory 網域及信任**] 視窗中, 以滑鼠右鍵按一下 [ **active Directory 網域及信任**], 然後選擇 [**屬性**]。
    
    ![以滑鼠右鍵按一下 [ActiveDirectory 網域及信任], 然後選擇 [屬性]](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. 在 [ **UPN 尾碼**] 索引標籤的 [**替代 upn 尾碼**] 方塊中, 輸入新的 upn 尾碼或尾碼**** \> ** **, 然後選擇 [新增]。
    
    ![新增 UPN 尾碼](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    完成新增尾碼後, 請選擇 **[確定]** 。 
    
 **步驟 2: 變更現有使用者的 UPN 尾碼**
  
1. 在 Active directory 網域服務 (AD DS) 執行所在的伺服器上, 于 [伺服器管理員] 中選擇 [**工具** \> ] [active directory**使用者和電腦**]。
    
    **或者, 如果您沒有 Windows Server 2012**
    
    按**Windows 鍵 + R**以開啟 [**執行**] 對話方塊, 然後在 [dsa.msc] 中輸入, 然後按一下 **[確定]**
    
2. 選取使用者, 按一下滑鼠右鍵, 然後選擇 [**屬性**]。
    
3. 在 [**帳戶**] 索引標籤的 [UPN 尾碼] 下拉式清單中, 選擇新的 upn 尾碼, 然後選擇 **[確定]**。
    
    ![為使用者新增 UPN 尾碼](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 針對每位使用者完成這些步驟。
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**您也可以使用 Windows PowerShell 來變更所有使用者的 UPN 尾碼**

如果您有大量使用者需要更新, 則使用 Windows PowerShell 會比較容易。 下列範例使用 Cmdlet [microsoft.rtc.management.adconnect.schema.aduser](https://go.microsoft.com/fwlink/p/?LinkId=624312)和[microsoft.rtc.management.adconnect.schema.aduser](https://go.microsoft.com/fwlink/p/?LinkId=624313)將所有 contoso. 本機尾碼變更為 contoso.com。 

執行下列 Windows PowerShell 命令, 以將所有 contoso. 本機尾碼更新為 contoso.com:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
若要深入瞭解如何在 Active Directory 中使用 Windows PowerShell, 請參閱[Active Directory Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=624314)。 

