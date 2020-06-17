---
title: 使用 IdFix 工具，準備用於與 Microsoft 365 同步處理的目錄屬性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: 提供使用 IdFix 在同步處理至 Microsoft 365 之前準備及清除內部部署目錄的指示。
ms.openlocfilehash: cae1df048e58c65a3203ea39df18beb986adb0c8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736001"
---
# <a name="prepare-directory-attributes-for-synchronization-with-microsoft-365-by-using-the-idfix-tool"></a>使用 IdFix 工具，準備用於與 Microsoft 365 同步處理的目錄屬性

*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*

本主題包含有關執行 IdFix 工具的詳細指示、您可能會遇到的一些常見錯誤、建議的修正程式、範例，以及如何處理大量錯誤的最佳作法。
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>使用 IdFix GUI 修正目錄中的錯誤

[執行 Microsoft 365 IdFix 工具](install-and-run-idfix.md)來搜尋目錄中的問題，然後修正 GUI 中的錯誤（如本主題所述）。 如果空白表格是由工具傳回，則不會發現任何錯誤。 如果您的目錄中有許多問題，當工具傳回錯誤時，可能會變得很複雜。 若要解決此問題，一種方法是先修正一個類型的所有錯誤，然後再移至下一個類型。 
  
1. 開始進行變更之前，請先查看 IdFix 所呈現的建議。
    
2. 查看 IdFix 傳回的錯誤清單。 您可以在列出錯誤類型的欄位頂端按一下 [**錯誤**]，依錯誤類型排序錯誤。 如果有一個以上的錯誤與單一屬性相關聯，錯誤會合並成一列。 在可能的情況下，IdFix 會在 [**更新**] 欄中提出修正建議。 修正是以檢查與物件相關聯之其他屬性的方式所組成。 雖然這些通常比目錄中的內容更好，但只有您可以決定實際的準確性。 
    
3. 如果 IdFix 對修正重複發生錯誤有建議，則會在 [**更新**] 欄中的值開頭，以三個旗標之一來識別修正。例如， `[E]john.doe@contoso.com` 。 如果您接受建議，當您套用變更時，就不會在目錄中插入旗標。 只會套用建議旗標之後的值，例如 `john.doe@contoso.com` 。 若要接受建議，請從 [**動作**] 欄中選取對應的動作。 旗標表示動作如下： 
    
 - **[C]** 建議的動作**完成**。 不需要編輯此值。
    
 - **[E]** 建議的動作**編輯**。 應該變更此值，以避免與目錄中的其他值發生衝突。
    
 - **[R]** 建議**移除**動作。 此值是非郵件啟用物件上的 SMTP proxy，而且可能會安全移除。
    
4. 閱讀並瞭解錯誤之後，請以您的變更更新 [**更新**] 欄中的專案，然後在 [**動作**] 欄中，選取您要 IdFix 執行變更的專案。 例如，兩位使用者可能會 `proxyAddress` 辨識為重複。 只有一個使用者可以使用 `proxyAddress` 來傳遞郵件。 若要修正此問題，請使用正確的值標示使用者的 [**動作**] 欄**完成**，並為其他使用者標示 [**移除****動作**] 欄。 這樣做會 `proxyAddress` 從使用者移除屬性，但不會變更其正確的使用者 `proxyAddress` `proxyAddress` 。
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>IdFix 偵測到的常見錯誤和修正程式
下表說明 IdFix 所偵測到的錯誤，提供從工具中最常建議的修正程式，而且在某些情況下提供如何修正這些錯誤的範例。

|**錯誤**|**錯誤類型描述**|**建議的修正**|**範例**|
|:-----|:-----|:-----|:-----|
|**字元** | 非法字元。 值包含不正確字元。 | [**更新**] 欄中所顯示之錯誤的建議修正會顯示已移除無效字元的值。  <br/> | 有效郵寄地址結尾的尾隨空格是不合法的字元，例如：  <br/> " `user@contoso.com` "  <br/> 有效郵寄地址開頭的前置空格是非法字元，例如：  <br/> " ` user@contoso.com `"  <br/>  `ú`字元是非法字元。 |
|**重複** | 重複的專案。 值在查詢的範圍內重複。 所有重複值都會顯示為錯誤。 | 編輯或移除值，以消除重複。 工具不會提供建議的重複專案修正。 相反地，您必須選擇兩個或多個重複專案中的哪一個是正確的重複專案，然後刪除重複的專案。 ||
|**format** | 格式化錯誤。 值違反屬性使用狀況的格式需求。 | 建議的更新會顯示已移除任何無效字元的值。 如果沒有無效字元，則 Update 和 Value 會出現相同。 您需要判斷您在更新中的實際需要。 工具不會提供所有格式化錯誤的建議修正。 | 例如，SMTP 位址必須符合 RFC 2822，且 mailNickName 不能以句點開始或結束。 如需目錄屬性之格式需求的詳細資訊，請參閱「目錄物件及屬性準備」，以[準備透過目錄同步作業將使用者布建至 Microsoft 365](prepare-for-directory-synchronization.md)。 |
|topleveldomain  <br/> |最上層網域。 這適用于由[RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464)格式設定所制約的值。 如果最上層網域不是透過網際網路路由傳送，則會將此範圍識別為錯誤。 例如，以中結尾的 SMTP 位址不會路由傳送，也就是導致此錯誤。 |將值變更為網際網路可路由的網域，例如 `.com` 或 `.net` 。 | 變更 `myaddress@fourthcoffee.local` 為 `fourthcoffee.com` 或另一個網際網路可路由網域。  <br/> 如需相關指示，請參閱 how [to prepare a 不可路由的網域（例如，local domain）進行目錄同步](prepare-a-non-routable-domain-for-directory-synchronization.md)處理。 |
|**domainpart** | 網域部分錯誤。 這適用于由 RFC 2822 格式設定所制約的值。 如果此值的網域部分無效，且不符合 RFC 2822，將會產生此值。 | 將值變更為符合 RFC 2822 的值。 例如，請確定它不含任何空格或非法字元。 | 變更 `myaddress@fourth coffee.com` 為 `myaddress@fourthcoffee.com` 。 |
|**domainpart_localpart** | 本機部分錯誤。 這適用于由 RFC 2822 格式設定所制約的值。 如果值的本機部分無效，且不符合 RFC 2822，將會產生此值。 |將值變更為符合 RFC 2822 的值。 例如，請確定它不含任何空格或非法字元。 |變更 `my"work"address@fourthcoffee.com` 為 `myworkaddress@fourthcoffee.com` 。 |
|**length** | 長度錯誤。 值違反屬性的長度限制。 當目錄架構變更時，通常會發生這種情況。  | IdFix 建議的更新會將值截斷為可接受的長度。  <br/> 請注意，這可能會產生不想要的結果。 您應查看建議的修正，並視需要加以變更，然後**按一下 [** 套用]。 ||
|**空白**  | 空白或 null 錯誤。 該值違反要同步處理之屬性的 null 限制。 只有少數幾個屬性必須包含值。 | 如果可能的話，建議的更新會利用其他屬性值，以產生可能的替代。 ||
|**mailmatch** | 這適用于僅限 Microsoft 365 專用。 值不符合 mail 屬性。 | 建議的更新將會是首碼為 "SMTP：" 的郵件屬性值。 ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>您可以使用 IdFix 執行的作業
若要修正錯誤，請從 [**動作**] 下拉式清單中選取選項。 下表說明使用 IdFix 工具可以對屬性執行的**動作**作業。 如果 [**動作**] 欄保留空白，IdFix 工具將不會對目錄中的特定錯誤採取任何動作。 

|**行動**|**動作描述**|**範例**|
|:-----|:-----|:-----|
|**完成** | 原始值是可接受的，但不論識別為錯誤，都不應該加以變更。 | 兩個使用者有識別為重複的 proxyAddress。 只有一個可以使用郵件傳遞的值。 將具有正確值的使用者標示為**完成**。 |
|**刪除** | 屬性值將會從來源物件中刪除。 例如，多重值屬性的情況下， `proxyAddresses` 只有顯示的個別值會被刪除。 | 兩個使用者有識別為重複的 proxyAddress。 只有一個可以使用郵件傳遞的值。 將具有重複值的使用者標示為 [**移除**]。 |
|**編輯** | [**更新**] 欄中的資訊將用於修改屬性值。 如果已 IdFix 建議有效的**更新**值，請在 [**動作**] 欄中，選取 [**編輯**]，然後繼續進行下一個錯誤。 如果您不想要此建議，請在 [**更新**] 欄中輸入新的，然後從 [**動作**] 欄中選取 [**編輯**]。 ||
|**撤銷** | 只有當您已從交易記錄檔還原時，才可使用此選項。 如果您選取 [**復原**]，屬性值將會還原為原始值。 ||
|**FAIL** | 只有在**更新**值與 AD DS 規則有未知衝突時，才會傳回此值。 在此情況下，如果您知道失敗為何，您可以重新編輯 [**更新**] 欄位中的值。 您可能需要使用 ADSI Edit 來分析物件中的值。 如需詳細資訊，請參閱[ADSI Edit （adsi .msc）](https://go.microsoft.com/fwlink/p/?LinkId=401170)。 ||

選擇錯誤或錯誤批次的**動作**後 **，按一下 [** 套用]。 當您按一下**Apply**時，工具會在目錄中進行變更。 您可以在按一下**Apply**之前提供多個錯誤的修復程式，IdFix 將同時變更所有錯誤。

再次執行 IdFix，以確保您所進行的修復程式未引入新的錯誤。 您可以視需要重複執行這些步驟。 建議您在同步處理之前，先完成此程式。
    
## <a name="changing-the-rule-set-used-by-idfix"></a>變更 IdFix 所使用的規則集
根據預設，IdFix 會使用多租使用者規則集來測試目錄中的專案。 這是大多數 Microsoft 365 客戶的正確規則集。 不過，如果您是 Microsoft 365 專屬或 ITAR （跨國流量為 Arm 規章）客戶，您可以設定 IdFix 改為使用專用規則集。 如果您不確定您是哪種類型的客戶，可以放心地略過此步驟。 若要將規則集設定為專屬，請按一下功能表列中的齒輪圖示，然後按一下 [**專用**]。
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>變更 IdFix 所使用的搜尋範圍
根據預設，IdFix 會搜尋整個目錄。 如有需要，您可以設定工具來搜尋特定的子樹。 若要執行此動作，請在功能表列中，按一下 [篩選] 圖示，然後輸入有效的子樹。
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>使用 IdFix GUI 回退變更
每**次按一下 [** 套用] 套用變更時，IdFix 工具都會建立一個稱為交易記錄檔的個別檔案，以列出您剛才所做的變更。 您可以使用交易記錄檔回退最近記錄中所做的變更，以防您犯錯誤。 若您在更新時發生錯誤，您可以按一下 [**復原**]，撤銷最近套用的變更。 當您按一下 [**復原**] 時，IdFix 會使用交易記錄檔回復的是最近的交易記錄檔中所做的變更。 如需使用交易記錄的詳細資訊，請參閱[Microsoft 365 IdFix 交易記錄](idfix-transaction-log.md)檔。

## <a name="next-step"></a>下一步

[設定目錄同步處理](set-up-directory-synchronization.md)
