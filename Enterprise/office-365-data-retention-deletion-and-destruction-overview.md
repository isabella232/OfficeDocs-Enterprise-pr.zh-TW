---
title: Office 365 中的資料保留、刪除及毀損
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Office 365 的相關資料保留、 刪除及毀損的 Microsoft 原則概觀。
ms.openlocfilehash: 08b04e4fec762249208acb626fa20562ffecb82f
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067321"
---
# <a name="data-retention-deletion-and-destruction-in-office-365"></a>Office 365 中的資料保留、刪除及毀損

Microsoft 已指定客戶資料刪除後，要保留多久的 Office 365 的資料處理標準的原則。 通常有兩個客戶資料都會被刪除的案例：

- **作用中刪除：** 租用戶都有作用中的訂閱和使用者刪除資料，或系統管理員刪除使用者所提供的資料。
- **被動刪除：** 租用戶訂閱結束。

## <a name="data-retention"></a>資料保留

針對每個這些案例中刪除下, 表顯示的最大資料保留期間，資料分類和分類：

| 資料分類 | 資料分類 | 描述 | 範例 | 保留期間 |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| 客戶資料 | 客戶內容| 直接提供/建立由系統管理員和使用者的內容 <br><br> 包含所有的文字、 音效、 視訊、 影像檔案及建立的軟體，且儲存在 Microsoft 資料中心時使用 Office 365 中的服務 | 範例的最常用的 Office 365 應用程式，可讓作者資料的使用者包括 Word、 Excel、 PowerPoint、 Outlook 和 OneNote <br><br> 客戶內容也包含客戶擁有/提供機密資料 （密碼、 憑證、 加密金鑰、 存放裝置金鑰） | **作用中刪除案例：** 最多 30 天 <br><br> **被動刪除案例：** 最 180 天 |
| 客戶資料 | 使用者識別資訊 (EUII) | 識別或無法用來識別使用者的 Microsoft 服務的資料。 EUII 不包含客戶內容 | 使用者名稱或顯示名稱 （網域 \ 使用者名稱） <br><br> 使用者主要名稱 (name@domain) <br><br>  使用者特定 IP 位址 | **作用中刪除案例：** 最 180 天 （僅限租用戶系統管理員動作） <br><br> **被動刪除案例：** 最 180 天 |
| 個人資料 <br> （未包含客戶資料中的資料） | 使用者假名化識別碼 (EUPI) | Microsoft 繫結至 Microsoft 服務的使用者所建立的識別碼。 EUPI 結合其他資訊，例如對應表格時, 識別使用者 <br><br> EUPI 不包含上傳，或是建立由客戶資訊 | 使用者的 Guid、 PUIDs 或 Sid <br><br> 工作階段識別碼 | **作用中刪除案例：** 最多 30 天 <br><br> **被動刪除案例：** 最 180 天 |

## <a name="subscription-retention"></a>訂閱保留

中之字詞的使用中的訂閱，訂閱者可以存取、 擷取，或刪除 Office 365 中儲存的客戶資料。 如果付費的訂閱結束或已終止，Microsoft 保留在 90 天的時間可以啟用 「 訂閱者 」 來擷取資料的有限函數帳戶儲存在 Office 365 的客戶資料。 90 天保留期間結束後，Microsoft 會停用帳戶，並刪除客戶資料。 不能超過 180 天之後到期或 Office 365 訂閱的終止 Microsoft 停用帳戶，並從該帳戶刪除所有客戶資料。 一旦經過任何資料的最長保留期間，資料會呈現商業無法復原。

免費試用版，您的帳戶會移到寬限期狀態 30 天中大部分的國家和地區。 這段期間寬限期，您可以購買 Office 365。 如果您決定不要購買 Office 365，您可以取消試用版，或讓在寬限期到期，並刪除您的試用帳戶資訊及資料。

## <a name="expedited-deletion"></a>快速的刪除

任何訂閱，訂閱者可以連絡 Microsoft 支援服務和要求快速訂閱不支援。 在此程序，刪除三天後系統管理員進入 Microsoft 所提供的鎖定程式碼所有使用者資料。 這包含 SharePoint Online 和 Exchange Online 中的資料，在 [保留] 下，或儲存在非使用中信箱。

如需有關快速取消佈建的詳細資訊，請參閱[取消 Office 365](https://support.office.com/article/Cancel-Office-365-for-business-b1bc0bef-4608-4601-813a-cdd9f746709a)。

## <a name="related-links"></a>相關連結
- [資料毀損](office-365-data-destruction.md)
- [Office 365 中的不變性](office-365-data-immutability.md)
- [Exchange Online 資料刪除](office-365-exchange-online-data-deletion.md)
- [SharePoint Online 資料刪除](office-365-sharepoint-online-data-deletion.md)
- [商務用 Skype 資料刪除](office-365-skype-data-deletion.md)