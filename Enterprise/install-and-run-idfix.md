---
title: 安裝和執行 Office 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何安裝和執行 Office 365 IdFix 工具，您將它同步處理至 Office 365 之前清除您的 active directory 幫助。
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067289"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>安裝和執行 Office 365 IdFix 工具

IdFix 識別錯誤，例如重複項目及格式化您的目錄中的問題，再進行同步處理至 Office 365。 
  
若要順利完成此工作，您應該滿意與使用者、 群組及 Active Directory 中的連絡人物件。
  
如果您無法完成此工作，有幾個可以執行其他作業。 這些方法可能比較方便，但他們也可能需要花費更多或有其他缺點。 其為：
  
- **未執行 IdFix 執行目錄同步處理。** 您可以將您的目錄同步處理未執行 IdFix 工具，但我們不建議此做法。 修正錯誤再進行同步處理會採用較少的時間，並通常提供更順暢地轉換至雲端。 
- **雇用顧問。** 取得專家說明可以開始您的使用者，並快速地執行與您的目錄同步處理。 
    
## <a name="what-you-need-to-run-idfix"></a>您必須執行 IdFix

最簡單方式以取得 IdFix 和執行是安裝在已加入網域的電腦上。 您可以執行它在網域控制站如果您想，但這不是必要。
  
### <a name="idfix-hardware-requirements"></a>IdFix 硬體需求

安裝 IdFix 的電腦必須符合下列基本硬體需求：
  
- 4 GB RAM
- 2 GB 的硬碟空間
    
### <a name="idfix-software-requirements"></a>IdFix 軟體需求

安裝 IdFix 的電腦必須加入至您要使用者同步處理至 Office 365 的同一個 Active Directory 網域。 電腦也必須已安裝的.NET Framework 4.0。 
  
如果您執行 Windows Server 2008 或 Windows Server 2012，是可能已經安裝.NET Framework。 如果不是，您可以[下載從下載中心.NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475)或透過 Windows Update。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 權限需求

執行 IdFix 所使用的使用者帳戶必須具有讀取/寫入存取的目錄。
  
如果您不確定您的使用者帳戶符合這些需求，而且您不確定如何檢查，但您仍會安裝，並執行 IdFix。 如果您的使用者帳戶沒有適當的權限，IdFix 只會顯示錯誤時您嘗試執行它。
  
## <a name="install-idfix"></a>安裝 IdFix

若要安裝 IdFix，下載並解壓縮**IdFix.exe**: 
  
1. 登入您要安裝 IdFix 工具的電腦。
    
2. 請移至 Microsoft 下載網站[IdFix DirSync 錯誤補救工具](https://go.microsoft.com/fwlink/?linkid=867219)。
    
3. 選擇 [**下載**]。
    
4. 出現提示時，選擇 [**執行**]。
    
5. 在 [ **WinZip Self-extractor** ] 對話方塊中 [**解壓縮到資料夾**] 文字方塊中，輸入或瀏覽至您要安裝 IdFix 工具的位置。 根據預設，安裝 IdFix `C:\Deployment Tools\`。 
    
6. 選擇 [**解壓縮**]。
    
## <a name="run-the-idfix-tool"></a>執行 IdFix 工具

安裝 IdFix 之後，請執行工具來搜尋您目錄中的問題：
  
1. 使用具有目錄讀/寫存取權的帳戶，登入安裝 IdFix 的電腦。
    
2. 在檔案總管] 中，移至您安裝 IdFix 的位置。 如果您在安裝期間選擇的預設資料夾，請移至`C:\Deployment Tools\IdFix`。
    
3. 按兩下 [ **IdFix.exe**]。 
    
    ![選擇 [IdFix.exe 檔案。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. 依預設，IdFix 會使用多重租用戶規則設定為在您的目錄中測試項目。 這是正確的規則集對於大多數的 Office 365 客戶。 不過，如果您是 Office 365 專用或 ITAR （國際流量武器法規） 客戶，您可以設定要使用的專用的規則集改為 IdFix。 如果您不確定哪種您的客戶，您可以放心地略過此步驟。 若要設定設定為專用的規則，按一下功能表列中的齒輪圖示，然後選擇 [**專用**。
    
5. 選擇 [**查詢**]。
    
    ![在 IdFix 中，選擇 [查詢。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 根據預設，IdFix 會搜尋整個目錄中的錯誤。
    
    根據您目錄的大小，執行查詢可能需要一段時間。 您可以查看在工具主視窗底部的進度。 如果您按一下 [**取消**]，您需要重新啟動從頭開始。
    
    ![IdFix 查詢與錯誤計數。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. IdFix 完成查詢之後，您可以繼續並同步處理您的目錄，如果沒有任何錯誤。 如果您的目錄中有錯誤，則建議，您修正它們，再進行同步處理。 如果您想要更具體資訊類型的錯誤和修正這些項目的的最佳方式的相關建議，請參閱本主題結尾處的連結。 
    
    雖然並非必要修正錯誤再進行同步處理，我們強烈建議您至少檢閱 IdFix 所傳回的所有錯誤。
    
    每個錯誤都會顯示在工具主視窗中的個別資料列。 
    
8. 如果您同意 [**更新**] 欄中所建議的變更，請在 [**動作**] 欄中選取您要如何實作變更 IdFix，然後按一下 [**套用]**。 當您按一下 [**套用]** 時，此工具會在目錄中進行的變更。
    
    您不需要在每個更新之後，按一下 [**套用]** 。 相反地，您可以修正幾個錯誤，再按一下 [**套用]** ，並 IdFix 會將它們變更所有在同一時間。 您可以藉由按一下**錯誤**頂端列出的錯誤類型的資料行的排序依錯誤類型的錯誤。 
    
    其中一個策略是類型的修正的相同; 所有錯誤例如，第一次，修正所有重複項目，並將它們套用。 接下來，修正字元格式錯誤，依此類推。 每次您套用變更，IdFix 工具建立不同的記錄檔可用來復原您的變更，以防發生錯誤。 [交易記錄檔](idfix-transaction-log.md)會儲存在您安裝 IdFix 中的資料夾。  根據預設_C:\Deployment Tools\IdFix_ 。 
    
    ![在 IdFix 中補救錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 完成所有的變更都會套用至執行一次，以確保您所做的修正程式並未引進新的錯誤 IdFix 的目錄。 您可以重複這些步驟，為您需要的次數。 它是不錯的選項以通過程序多次再進行同步處理。
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>我想要精簡搜尋或深入探討錯誤，我可以使用 IdFix 來做什麼？

更深入的資訊會提供從下列主題：
  
- [同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)。 您已安裝的工具，跳至本主題的詳細說明執行工具之後, 會遇到的常見錯誤的建議修正程式、 範例，以及當您有大量錯誤時，該怎麼辦的最佳做法。 
- [參照：IdFix 已排除和支援的物件和屬性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [參照：Office 365 IdFix 交易記錄](idfix-transaction-log.md)
    
## <a name="video-training"></a>影片訓練課程

如需詳細資訊，請參閱 < 課程中<b0>安裝及使用 IDFix 工具</b0>，由 LinkedIn Learning 帶您。
  

