---
title: 安裝和執行 Office 365 IdFix 工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何安裝和執行 Office 365 IdFix 工具可協助清除您的 active directory 同步處理至 Office 365 之前。
ms.openlocfilehash: c485d8397aa32005a34b77f886b9bc8f4e857f1b
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674427"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>安裝和執行 Office 365 IdFix 工具

再進行同步處理至 Office 365 IdFix 會識別錯誤例如重複項目與您的目錄中的格式設定問題。 
  
若要順利完成此工作，您應該滿意使用使用者、 群組及 Active Directory 中的連絡人物件。
  
如果您無法完成此工作，有一些其他您所能做的事項。這些方法可能比較容易，但可能也會更久或有其他缺點。他們是：
  
- **執行目錄同步處理，而不執行 IdFix。** 您可以將您的目錄同步處理不執行 IdFix 工具，但是我們並不建議使用它。修正錯誤再進行同步處理需要很少的時間和常可以提供更順暢地呈現轉換至雲端。 
- **雇用一位顧問。** 取得專家協助可以快速地啟動並執行您的使用者，以及同步處理您的目錄。 
    
## <a name="what-you-need-to-run-idfix"></a>執行 IdFix 所需的項目

最簡單方式以取得 IdFix 並執行已安裝已加入網域的電腦上。您可以執行該網域控制站上如果您想，但不需要。
  
### <a name="idfix-hardware-requirements"></a>IdFix 硬體需求

安裝 IdFix 的電腦必須符合下列基本硬體需求：
  
- 4 GB RAM
- 2 GB 的硬碟空間
    
### <a name="idfix-software-requirements"></a>IdFix 軟體需求

安裝 IdFix 的電腦必須加入至您要使用者同步處理至 Office 365 的同一個 Active Directory 網域。電腦也必須安裝.NET Framework 4.0。 
  
如果您執行 Windows Server 2008 或 Windows Server 2012，是可能已經安裝.NET Framework。如果您不可以[下載從下載中心.NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475)或透過 Windows Update。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 權限需求

您用來執行 IdFix 的使用者帳戶需要有目錄的讀寫權限。
  
如果您不確定您的使用者帳戶符合這些需求，而且您不確定如何檢查，仍可安裝及執行 IdFix。如果您的使用者帳戶沒有正確的權限，IdFix 只會顯示錯誤當您嘗試執行它。
  
## <a name="install-idfix"></a>安裝 IdFix

若要安裝 IdFix，請下載並解壓縮**IdFix.exe**： 
  
1. 登入您想要安裝 IdFix 工具的電腦。
    
2. 移至 Microsoft 下載網站[IdFix DirSync 錯誤補救工具](https://go.microsoft.com/fwlink/?linkid=867219)。
    
3. 選擇 [下載]****。
    
4. 出現提示時，選擇 [**執行**]。
    
5. 在 [ **WinZip Self-extractor** ] 對話方塊的 [**解壓縮至資料夾**] 文字方塊中輸入或瀏覽至您要安裝 IdFix 工具的位置。依預設，將安裝 IdFix `C:\Deployment Tools\`。 
    
6. 選擇 [**解壓縮**]。
    
## <a name="run-the-idfix-tool"></a>執行 IdFix 工具

安裝 IdFix 之後，請執行工具來搜尋您目錄中的問題：
  
1. 使用具有目錄讀寫權限的帳戶，登入已安裝 IdFix 的電腦。
    
2. 在檔案總管] 中，移至您安裝 IdFix 的位置。如果您選擇在安裝期間的預設資料夾，請移至`C:\Deployment Tools\IdFix`。
    
3. 連按兩下 [IdFix.exe]****。 
    
    ![選擇 [IdFix.exe 檔案。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. IdFix 預設會使用的多租用戶規則集來測試您的目錄中的項目。這是設為最多的 Office 365 客戶的右規則。不過，如果您是 Office 365 專用或 ITAR （國際流量召集令規定） 客戶，您可以設定要使用的專用的規則集而 IdFix。如果您不確定您的客戶的類型，您可以放心地略過此步驟。若要設定設為專用的規則，請按一下功能表列的齒輪圖示，，然後選擇 [**專用**。
    
5. 選擇 [**查詢**]。
    
    ![選擇在 IdFix 中的 [查詢]。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. IdFix 預設會搜尋整個目錄中的錯誤。
    
    根據您的目錄的大小、 執行查詢可能需要一段。您可以觀看在工具主視窗的底端的進度。如果您按一下 [**取消**]，您需要重新啟動一開始。
    
    ![IdFix 查詢和錯誤計數。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. IdFix 完成查詢之後，您可以繼續進行並同步處理您的目錄如果沒有任何錯誤。如果您的目錄中有錯誤，建議的您修正其再進行同步處理。如果您想更詳細的錯誤類型資訊和有關修正這些項目的的最佳方式的建議，請參閱本主題結尾處的連結。 
    
    雖然不需要先修正錯誤再進行同步處理，但是強烈建議您至少檢閱 IdFix 所傳回的所有錯誤。
    
    每個錯誤都會顯示在工具主視窗中的個別資料列。 
    
8. 如果您同意 [UPDATE]**** 資料行中建議的變更，請在 [ACTION]**** 資料行中選取您想要 IdFix 執行以實作變更的作業，然後按一下 [套用]****。當您按一下 [套用]**** 時，工具會在目錄中進行變更。
    
    您不需要在每次更新後按一下 [**套用]** 。而您可以修正數個錯誤再按一下 [**套用]** 並 IdFix 會將它們變更所有在同一時間。您可以按一下**錯誤**頂端列出的錯誤類型的資料行的排序錯誤類型所發生之錯誤。 
    
    一個策略是依修正相同的類型 ； 所有錯誤例如，先修正所有重複項目並套用。接下來，修正字元格式錯誤、 等等。套用變更，每次 IdFix 工具建立不同的記錄檔可用來復原變更以防進行錯誤。[交易記錄檔](idfix-transaction-log.md)會儲存在已安裝 IdFix 中的資料夾中。 根據預設_C:\Deployment Tools\IdFix_ 。 
    
    ![在 IdFix 中補救錯誤。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 完成所有的變更會對執行一次以確保您所做的修正程式沒有引進新的錯誤 IdFix 的目錄。您可以重複這些步驟您需要的次數。它是不錯的選項以移到程序一些時間再進行同步處理。
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>我想要精簡搜尋或深入探討錯誤，那麼我還可以使用 IdFix 來執行其他作業嗎？

您可以從下列主題取得更深入資訊：
  
- [同步處理與 Office 365 使用 IdFix 工具準備目錄屬性](prepare-directory-attributes-for-synch-with-idfix.md)。您已安裝的工具，跳至本主題的相關執行工具的詳細指示之後會遇到的常見錯誤的建議修正程式、 範例和不具有大量的錯誤時的最佳作法。 
- [參照：IdFix 已排除和支援的物件和屬性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [參照：Office 365 IdFix 交易記錄](idfix-transaction-log.md)
    
## <a name="video-training"></a>影片訓練課程

如需詳細資訊，請參閱致力提供依 LinkedIn 學習課程[安裝及使用 IDFix 工具](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)。
  

