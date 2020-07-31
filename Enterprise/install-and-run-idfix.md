---
title: 下載並執行 Microsoft 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何在將 Active Directory 網域服務（AD DS）同步處理至 Microsoft 365 之前，下載並執行 Microsoft 365 IdFix 工具以協助清除 Active Directory 網域服務。
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502658"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>下載並執行 Microsoft 365 IdFix 工具

*本文適用於 Microsoft 365 企業版和 Office 365 企業版。*

IdFix 會先識別錯誤 (如您的 Active Directory 網域 (AD DS) 服務中的重複和格式問題)，然後再同步處理至 Microsoft 365。 
  
要順利完成這項工作，您應習慣在 AD DS 中使用使用者、群組和連絡人物件。
  
如果您無法完成這項工作，您可以執行其他您能完成的動作。 這些方法可能會比較容易，但可能會花費更長的時間，或有其他缺點。 其中包括：
  
- **在未執行 IdFix 的情況下執行目錄同步作業** 

  您可以在未使用 IdFix 工具的情況下同步處理目錄，但我們並不建議。 先修正錯誤再同步處理所需的時間較少，而且通常可以更平穩地轉換至雲端。 

- **聘用顧問** 

  取得專家協助可以快速地啟動並執行您的使用者，以及同步處理您的目錄。 
    
## <a name="what-you-need-to-run-idfix"></a>執行 IdFix 所需的項目

啟動並執行 IdFix 的最簡單方式是將它下載到已加入您 AD DS 網域的電腦上。 若您想要，您可以在網域控制站上執行它，但這非必要動作。
  
### <a name="idfix-hardware-requirements"></a>IdFix 硬體需求

您下載 IdFix 的電腦必須符合這些最低硬體需求：
  
- 4 GB RAM
- 2 GB 的硬碟空間
   
### <a name="idfix-software-requirements"></a>IdFix 軟體需求

您下載 IdFix 的電腦必需聯結到您要將使用者同步處理至 Microsoft 365 的相同 AD DS 網域。 

電腦也需要安裝 .NET Framework 4.0。 如果您執行的是 Windows Server 2008 或更新版本，則可能已經安裝了 .NET Framework。 如果不是，您可以 [從下載中心下載 .NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 或使用 Windows Update 下載。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 權限需求

您用來執行 IdFix 的使用者帳戶必須具有 AD DS 網域的讀取和寫入權限。
  
如果您不確定您的使用者帳戶是否符合這些需求，且不確定如何檢查，您仍然可以下載並執行 IdFix。 如果您的使用者帳戶沒有正確權限，則 IdFix 只是會在您嘗試執行它時顯示錯誤。
  
## <a name="download-and-extract-idfix"></a>下載並解壓 IdFix

按照下列指示進行。 
  
1. 登入您想要執行 IdFix 工具的電腦。
    
2. 移至 [IdFix DirSync 錯誤修正工具](https://github.com/microsoft/idfix) 網站。
    
3. 在 **[ClickOnce 啟動]** 區段中，按一下 **[啟動]** 以下載壓縮檔案。 開啟壓縮檔案。
    
4. 在 **[IdFix]** 視窗中，選擇 **[解壓縮]**，然後 **[全部解壓縮]**。 根據預設，IdFix 會解壓至 `C:\Users\<your user name>\Documents\IdFix`。 
    
5. 選擇 **[解壓縮]**。

您的步驟可能會根據您的 Windows 版本和網路瀏覽器而有所不同。
    
## <a name="run-the-idfix-tool"></a>執行 IdFix 工具

下載並解壓 IdFix 之後，請執行 IDFix 以搜尋您 AD DS 網域中的問題。
  
1. 使用具有您的 AD DS 網域讀取/寫入權限的帳戶，以登入您下載 IdFix 的電腦。
    
2. 在 [檔案總管] 中，移至已解壓 IdFix 的位置。 如果您在解壓過程中選擇預設資料夾，請移至 `C:\Users\<your user name>\Documents\IdFix`。 
    
3. 按兩下 **IdFix.exe**。 
  
4. IdFix 預設會使用「多租用戶」規則集，測試您目錄中的項目。 這是大部分 Microsoft 365 客戶的正確規則集。 不過，如果您是 Microsoft 365 專屬或 International Traffic in Arms Regulations (ITAR)) 客戶，則可以設定 IdFix 以改用 [專屬] 規則集。 如果不確定您是哪種類型的客戶，則可以放心地略過此步驟。 若要將規則集設定為 [專屬]，請按一下功能表列中的齒輪圖示，然後按一下 **[專屬]**。
    
5. 選擇 **[查詢]**。
    
    ![選擇 IdFix 中的 [查詢]。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. IdFix 預設會搜尋整個目錄中的錯誤。
    
    根據您目錄的大小，執行查詢可能需要一些時間。 您可以在工具主視窗底部觀看進度。 如果您按一下 **[取消]**，則需要從頭重新開始。
  
7. 在 IdFix 完成查詢之後，如果沒有錯誤，則可以同步處理您的目錄。 如果您的目錄中有錯誤，則建議您先修正它們，再進行同步處理。 如需詳細資訊，請參閱 [準備目錄屬性以便與 Microsoft 365 進行同步處理](prepare-directory-attributes-for-synch-with-idfix.md)。
    
    雖然不需要先修正錯誤再進行同步處理，但是強烈建議您至少檢閱 IdFix 所傳回的所有錯誤。
    
    每個錯誤都會在工具主視窗中以獨立一列的方式顯示。 
    
8. 如果您同意 **[更新]** 資料行中建議變更，請在 **[動作]** 資料行中選取您想要 IdFix 執行以實作變更的作業，然後按一下 **[套用]**。 按一下 **[套用]** 後，工具就會在目錄中進行變更。
    
    在每次更新之後，您不需要按 **[套用]**。 而是，您可以先修正數個錯誤，再按一下 **[套用]**，而且 IdFix 會同時變更它們。 您可以按一下錯誤類型欄頂端的 **[錯誤]** 來根據錯誤類型排序錯誤。 
    
    其中一個策略是修正同一類型的所有錯誤；例如，先修正所有重複項目，並套用它們。 接下來，修正字元格式錯誤，依此類推。 每次套用變更時，IdFix 工具都會建立個別記錄檔，以在您出錯時用來復原變更。 [交易記錄](idfix-transaction-log.md) 儲存在您解壓 IdFix 的資料夾中，預設為_C:\Users\<your user name>\Documents\IdFix_。 
    
    ![在 IdFix 修正錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 在您對目錄進行所有變更之後，請重新執行 IdFix，以確保您進行的修正並未產生新的錯誤。 您可以依需要的次數重複這些步驟。 最好多次執行此程序，再進行同步處理。
    
## <a name="additional-resources-on-idfix"></a>IdFix 上的其他資源 

- [IdFix 已排除和支援的物件和屬性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Microsoft 365 IdFix 交易記錄](idfix-transaction-log.md)
    
