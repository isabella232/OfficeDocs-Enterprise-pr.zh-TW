---
title: 使用 IdFix 工具準備目錄屬性以與 Office 365 進行同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: 使用 IdFix 準備並清除內部目錄，再同步處理至 Office 365 提供的指示。
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540184"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>使用 IdFix 工具準備目錄屬性以與 Office 365 進行同步處理
本主題包含執行 IdFix 工具的詳細的指示一些常見的錯誤可能會發生，建議的修正程式、 範例和最佳作法如果您有大量的錯誤。
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>使用 IdFix GUI 修正您目錄中的錯誤
[執行 Office 365 IdFix 工具](install-and-run-idfix.md)來搜尋您目錄中的問題，然後修正錯誤的 GUI 本主題所述。若此工具會傳回空白表格、 所不發現任何錯誤。如果有許多的您的目錄中的問題，很多得難以時工具會傳回錯誤。若要解決此的其中一個方法是先在修正的一種類型的所有錯誤及然後移至下一個類型。 
  
1. 在您開始進行變更之前，請查看 IdFix 所呈現的建議。
    
2. 請再次查看 IdFix 已傳回的錯誤清單。按一下列出錯誤類型的資料行頂端的 [ERROR]****，即可依錯誤類型來排序錯誤。如果有多個錯誤與單一屬性相關聯，則會將這些錯誤合併為一個資料列。IdFix 會盡可能在 [UPDATE]**** 資料行中呈現修正程式的建議。此修正程式是根據與物件相關聯的其他屬性的檢查。雖然這些通常會比目錄中的現有項目還好，但是只有您才能決定哪個正確無誤。 
    
3. 如果 IdFix 的修正重複錯誤的建議，修正可識別的其中一個 [**更新**] 欄中值的開頭的三個旗標例如`[E]john.doe@contoso.com`。如果您接受建議時套用標幟就不會插入目錄中的變更。只有下列旗標會套用，例如建議值`john.doe@contoso.com`。如果您想要接受建議，請從 [**動作**] 欄選取相符的動作。旗標會指出動作，如下所示： 
    
 - **[C]** 建議的動作 **COMPLETE**。您不需要編輯值。
    
 - **[E]** 建議的動作 **EDIT**。您應該變更此值，避免與目錄中的另一個值衝突。
    
 - **[R]** 建議的動作 **REMOVE**。此值是非擁有郵件物件上的 SMTP Proxy，而且可能可以安全地予以移除。
    
4. 一次您已閱讀並瞭解錯誤、 使用您的變更，更新 [**更新**] 欄中的項目，然後在**巨集指令**欄選取您想要實作變更執行 IdFix。例如，可能會有兩個使用者`proxyAddress`會被識別為重複。只有一位使用者可以使用`proxyAddress`郵件傳遞的。若要修正此問題，標示與正確的值，為使用者的 [**動作**] 欄**完成**並標示 [**動作**] 欄**中移除**其他使用者。這會移除`proxyAddress`屬性從使用者其這`proxyAddress`不屬於和其讓使用者不變更其這`proxyAddress`是否正確。
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>IdFix 偵測到的常見錯誤和修正程式
下表描述 IdFix 偵測到的錯誤、提供工具最常建議的修正程式，以及在某些情況下，提供如何修正它們的範例。

|**錯誤**|**錯誤類型描述**|**建議的修正程式**|**範例**|
|:-----|:-----|:-----|:-----|
|**character** | 不合法的字元。值包含無效的字元。 | [UPDATE]**** 資料行中所顯示錯誤的建議修正程式會顯示已移除無效字元的值。  <br/> | 行尾的空格結尾處的有效郵件地址是不合法的字元，例如：  <br/> " `user@contoso.com` "  <br/> 有效的郵件地址開頭的前置空間是不合法的字元，例如：  <br/> " ` user@contoso.com `"  <br/>  `ú`字元是不合法的字元。 |
|**duplicate** | 重複的項目。值在查詢範圍內有重複項目。所有重複值都會顯示為錯誤。 | 編輯或移除值，以排除重複項目。此工具不提供重複項目的建議修正程式。而是，您必須選擇兩個以上重複項目的哪一個是正確項目，並刪除一個以上的重複項目。 ||
|**格式** | 格式錯誤。值違反屬性使用方式的格式需求。 | 建議的「更新」將會顯示已移除任何無效字元的值。如果沒有任何無效字元，則「更新」和「值」將會相同。您必須判斷「更新」中他們實際想要的內容。此工具不提供所有格式錯誤的建議修正程式。 | 例如 SMTP 位址必須符合 RFC 2822，而且 mailNickName 無法啟動或結尾是句點。如需目錄屬性的格式需求的詳細資訊，請參閱[＜ Prepare to 佈建使用者透過目錄同步處理至 Office 365](prepare-for-directory-synchronization.md)中的 「 目錄物件和屬性準備 」。 |
|topleveldomain  <br/> |最上層網域。這適用於受限於[RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464)格式設定的值。如果最上層網域不是網際網路可路由這將會被識別為錯誤。例如結束.local 中的 SMTP 地址不是網際網路路由傳送，將會導致此錯誤。 |例如： 將值變更為網際網路路由傳送的網域`.com`或`.net`。 | 變更`myaddress@fourthcoffee.local`至`fourthcoffee.com`或另一個網際網路路由傳送的網域。  <br/> 指示，請參閱[如何準備非-路由傳送的網域 （例如.local 網域） 進行目錄同步作業](prepare-a-non-routable-domain-for-directory-synchronization.md)。 |
|**domainpart** | 網域部分錯誤。這適用於受限於 RFC 2822 格式的值。如果值的網域部分無效，而且不符合 RFC 2822，則會產生此錯誤。 | 變更此值符合 RFC 2822。例如，請確定以至於不含任何空格或不合法的字元。 | 變更`myaddress@fourth coffee.com`至`myaddress@fourthcoffee.com`。 |
|**domainpart_localpart** | 本機部分錯誤。這適用於受限於 RFC 2822 格式的值。如果值的本機部分無效，而且不符合 RFC 2822，則會產生此錯誤。 |變更此值符合 RFC 2822。例如，請確定以至於不含任何空格或不合法的字元。 |變更`my"work"address@fourthcoffee.com`至`myworkaddress@fourthcoffee.com`。 |
|**length** | 長度錯誤。值違反屬性的長度限制。這是已變更目錄結構描述時最常遇到的問題。  | IdFix 所建議的更新會將值截斷為可接受的長度。  <br/> 請注意，這可能會產生令人失望的結果。您應該檢閱建議的修正程式，並視需要在按一下 [套用]**** 之前進行變更。 ||
|**空白**  | 空白或 Null 錯誤。值違反要同步處理之屬性的 Null 限制。只有少數屬性才必須包含值。 | 建議的更新會盡可能利用其他屬性值，來產生可能的替代項目。 ||
|**mailmatch** | 這僅適用於 Office 365 專用。值不符合 mail 屬性。 | 建議的更新將會是郵件屬性值開頭加上"SMTP:"。 ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>您可以使用 IdFix 執行的作業
若要可修正錯誤，您可從 [**動作**] 下拉式清單選取選項。下表說明您可以使用 IdFix 工具的屬性執行的**動作**作業。如果 [**動作**] 欄保留空白，IdFix 工具不需要任何動作上的目錄中的特定錯誤。 

|**巨集指令**|**動作描述**|**範例**|
|:-----|:-----|:-----|
|**COMPLETE** | 原始值是可接受的，而且，雖然識別為錯誤，但不應該進行變更。 | 兩位使用者擁有視為重複的 proxyAddress。只有一位使用者才能使用此值進行郵件傳遞。將具有正確值的使用者標記為 [COMPLETE]****。 |
|**移除** | 會從來源物件中刪除的屬性值。但如果是多重值屬性，例如`proxyAddresses`，只顯示個別值會被刪除。 | 兩位使用者擁有視為重複的 proxyAddress。只有一位使用者才能使用此值進行郵件傳遞。將具有重複值的使用者標記為 [REMOVE]****。 |
|**編輯** | 在 [**更新**] 欄中的資訊將用來修改屬性值。如果有已 IdFix 所建議有效**更新**值，然後從 [**動作**] 欄中，選取 [**編輯**並前往下一個錯誤。如果您不想要的建議，輸入一個新 [**更新**] 欄中的與然後，從 [**動作**] 欄中選取 [**編輯**。 ||
|**復原** | 只有在您已從交易記錄中還原時，才能使用此選項。如果您選取 [UNDO]****，屬性值將會還原為原始值。 ||
|**FAIL** | 如果**更新**值具有 AD DS 規則未知的衝突，只會傳回此值。在此例中，您可以編輯 [**更新**] 欄中的值再次如果您知道失敗的功能。可能需要分析使用 ADSI 編輯物件中的值。如需詳細資訊，請參閱[ADSI 編輯 (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170)。 ||

選擇一個錯誤或一批錯誤的 [ACTION]**** 之後，請按一下 [套用]****。當您按一下 [套用]**** 時，工具會在目錄中進行變更。您可以先提供多個錯誤的修正程式，再按一下 [套用]****，而且 IdFix 會同時變更它們。

執行 IdFix 一次以確保您所做的修正程式沒有引進新的錯誤。您可以重複這些步驟您需要的次數。它是不錯的選項以移到程序一些時間再進行同步處理。
    
## <a name="changing-the-rule-set-used-by-idfix"></a>變更 IdFix 所使用的規則集
IdFix 預設會使用的多租用戶規則集來測試您的目錄中的項目。這是正確的規則集大部分的 Office 365 = 客戶。不過，如果您是 Office 365 專用或 ITAR （國際流量召集令規定） 客戶，您可以設定要使用的專用的規則集而 IdFix。如果您不確定您的客戶的類型，您可以放心地略過此步驟。若要設定設為專用的規則，請按一下功能表列的齒輪圖示和 [**專用**。
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>變更 IdFix 所使用搜尋的範圍
IdFix 預設會搜尋整個目錄。如果想要，您可以設定工具改為搜尋特定樹狀子目錄。若要這樣做，請按一下功能表列中的 [篩選] 圖示，然後輸入有效的樹狀子目錄。
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>使用 IdFix GUI 回復變更
按一下 [**套用**] 以套用變更，每次 IdFix 工具會建立名列出您剛才做的變更交易記錄檔的不同檔案。您可以使用的交易記錄檔回復的最新的記錄檔中，以免讓錯誤只是這些變更。如果您要更新時進行錯誤，您可以藉由按一下 **[復原**復原最近套用的變更。當您按一下 [**復原**時] IdFix 會使用的交易記錄檔回復只會在最新的交易記錄檔的變更。如需使用的交易記錄檔的詳細資訊，請參閱[參照： Office 365 IdFix 交易記錄檔](idfix-transaction-log.md)。