---
title: 下載並執行 Microsoft 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
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
description: 如何在將 Active Directory 網域服務（AD DS）同步處理至 Microsoft 365 之前，下載並執行 Microsoft 365 IdFix 工具，以協助清理您的 Active Directory 網域服務（AD DS）。
ms.openlocfilehash: c4df63e6162b1d53cb7a45f046542443177b25ff
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774858"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>下載並執行 Microsoft 365 IdFix 工具

*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*

IdFix 會在您同步處理至 Microsoft 365 之前，識別您的 Active Directory 網域服務（AD DS）網域中的重複和格式化問題等錯誤。 
  
若要順利完成這項工作，您應該舒適使用 AD DS 中的使用者、群組和連絡人物件。
  
如果您無法完成這項工作，還有其他幾項您可以執行的動作。 這些方法可能較為簡單，但也可能需要較長的時間，否則會有其他缺點。 其中包括：
  
- **執行目錄同步處理但不執行 IdFix** 

  您可以同步處理您的目錄，而不需要使用 IdFix 工具，但我們不建議您這樣做。 在同步處理之前修正錯誤所需的時間較少，且通常會提供更順暢的轉換至雲端。 

- **雇用顧問** 

  取得專家協助可讓您的使用者快速啟動並執行，並同步處理您的目錄。 
    
## <a name="what-you-need-to-run-idfix"></a>您需要執行的 IdFix

若要執行 IdFix，最簡單的方法是將它下載到已加入 AD DS 網域的電腦上。 您可以視需要在網域控制站上執行它，但這不是必要的。
  
### <a name="idfix-hardware-requirements"></a>IdFix 硬體需求

您下載 IdFix 需要符合這些最低硬體需求的電腦：
  
- 4 GB RAM
- 2 GB 的硬碟空間
   
### <a name="idfix-software-requirements"></a>IdFix 軟體需求

您要在其中下載 IdFix 的電腦必須加入您要將使用者同步處理至 Microsoft 365 的相同 AD DS 網域。 

電腦也需要安裝 .NET Framework 4.0。 如果您執行的是 Windows Server 2008 或更新版本，.NET Framework 可能已經安裝。 如果不是，您可以從下載中心或使用 Windows Update[下載 .net 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 許可權需求

您用來執行 IdFix 的使用者帳戶必須具有 AD DS 網域的讀取和寫入權限。
  
如果您不確定您的使用者帳戶是否符合這些需求，而且不確定如何檢查，您仍然可以下載並執行 IdFix。 如果您的使用者帳戶沒有正確的許可權，IdFix 會在您嘗試執行它時，只會顯示錯誤。
  
## <a name="download-and-extract-idfix"></a>下載和解壓縮 IdFix

請遵循這些指示。 
  
1. 登入您要執行 IdFix 工具的電腦。
    
2. 移至[IdFix DirSync 錯誤修正工具](https://github.com/microsoft/idfix)網站。
    
3. 按一下 [ **ClickOnce 啟動**] 區段中的 [**啟動**]，下載 zip 檔案。 開啟 zip 檔案。
    
4. 在 [ **IdFix** ] 視窗中，選擇 [**解壓縮**]，然後**全部解壓縮**。 依預設，IdFix 會解壓縮至 `C:\Users\<your user name>\Documents\IdFix` 。 
    
5. 選擇 [解壓縮]****。

您的步驟可能會根據您的 Windows 和網際網路瀏覽器的版本而有所不同。
    
## <a name="run-the-idfix-tool"></a>執行 IdFix 工具

下載並解壓縮 IdFix 之後，請執行此程式，以搜尋 AD DS 網域中的問題。
  
1. 使用具有您 AD DS 網域之讀取/寫入權限的帳戶，登入您已下載 IdFix 的電腦。
    
2. 在檔案瀏覽器中，移至您解壓縮 IdFix 的位置。 如果您在解壓縮期間選擇預設資料夾，請移至 `C:\Users\<your user name>\Documents\IdFix` 。 
    
3. 按兩下 [ **IdFix.exe**]。 
  
4. 根據預設，IdFix 會使用多租使用者規則集來測試目錄中的專案。 這是大多數 Microsoft 365 客戶的正確規則集。 不過，如果您是「Arm 規章」（ITAR）客戶的 Microsoft 365 專屬或國際流量，您可以設定 IdFix 改為使用專用規則集。 如果您不確定您是哪種類型的客戶，可以放心地略過此步驟。 若要將規則集設定為專屬，請按一下功能表列中的齒輪圖示，然後選擇 [**專屬**]。
    
5. 選擇 [**查詢**]。
    
    ![在 IdFix 中選擇 [查詢]。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 根據預設，IdFix 會搜尋整個目錄中是否有錯誤。
    
    執行查詢時，可能需要一段時間，視目錄的大小而定。 您可以在工具的主視窗底部觀賞進度。 如果您按一下 [**取消**]，則需要從頭開始重新開始。
  
7. IdFix 完成查詢之後，如果沒有任何錯誤，您可以同步處理您的目錄。 如果您的目錄中有錯誤，建議您在同步處理之前先加以修正。 如需詳細資訊，請參閱[準備目錄屬性以與 Microsoft 365 同步處理](prepare-directory-attributes-for-synch-with-idfix.md)。
    
    雖然不需要在同步處理之前修正錯誤，但強烈建議您至少檢查 IdFix 所傳回的所有錯誤。
    
    每個錯誤都顯示在工具主視窗中的個別列。 
    
8. 如果您同意 [**更新**] 欄中的 [建議變更]，請在 [**動作**] 欄中，選取您要 IdFix 執行變更的專案，**然後按一下 [** 套用]。 當您按一下**Apply**時，工具會在目錄中進行變更。
    
    在每次更新後，您不必按**Apply** 。 相反地，您可以在按一下**Apply**之前修正數個錯誤，IdFix 會同時變更所有錯誤。 您可以在列出錯誤類型的欄位頂端按一下 [**錯誤**]，依錯誤類型排序錯誤。 
    
    一個策略是修正所有相同類型的錯誤;例如，先修正所有重複專案，然後加以套用。 接下來，修正字元格式錯誤等等。 每次套用變更時，IdFix 工具都會建立個別的記錄檔，您可以用來復原您的變更，以防您犯錯誤。 [交易記錄](idfix-transaction-log.md)會儲存在您解壓縮 IdFix 的資料夾中，預設為_C:\Users \<your user name> \Documents\IdFix_ 。 
    
    ![在 IdFix 修正錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 對目錄進行所有變更之後，請再次執行 IdFix，以確保您所進行的修復程式未引入新的錯誤。 您可以視需要重複執行這些步驟。 建議您在同步處理之前，先完成此程式。
    
## <a name="additional-resources-on-idfix"></a>IdFix 的其他資源 

- [IdFix 已排除和支援的物件和屬性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Microsoft 365 IdFix 交易記錄檔](idfix-transaction-log.md)
    
