---
title: Office 365 身分識別模型和 Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: 了解如何在 Office 365 中管理使用者身分識別。
ms.openlocfilehash: 0cc40323d978fe9ab13e3326dac183143a014406
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40071875"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a>Office 365 身分識別模型和 Azure Active Directory

*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*

Office 365 使用 Azure Active Directory (Azure AD)、 隨附於 Office 365 訂閱，來管理身分識別和驗證 Office 365 雲端型使用者身分識別與驗證服務。 取得您正確設定的身分識別基礎結構是管理 Office 365 使用者存取權和權限為您的組織很重要。

開始之前，請觀賞這段影片的身分識別模型的概觀和 Office 365 和 Microsoft 365 的驗證。

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Office 365 身分識別模型是您第一個的規劃選擇。

## <a name="office-365-identity-models"></a>Office 365 身分識別模型

若要規劃使用者帳戶，必須先了解 Microsoft 365 中的兩種身分識別模型。 您可以維護貴組織的雲端設定身分識別只，或您可以維護您的內部部署 Active Directory 網域服務 (AD DS) 身分識別，並將其用於驗證的使用者存取 Microsoft 365 雲端服務時。  

以下是兩種類型的身分識別和其最佳配合及福利。

|||
|:-------|:-----|:-----|
|  | **僅限雲端身分識別** | **混合式身分識別** |
| **定義** | 使用者帳戶只存在於 Microsoft 365 訂用帳戶的 Azure Active Directory (Azure AD) 租用戶。 | 在 AD DS 中有使用者帳戶和複本也是在您的 Microsoft 365 訂閱的 Azure AD 租用戶中。 在 Azure AD 中的使用者帳戶也可能包含使用者帳戶密碼雜湊的版本。 |
| **Microsoft 365 如何驗證使用者認證** | Microsoft 365 訂用帳戶的 Azure AD 租用戶會執行與雲端身分識別帳戶驗證。 | Microsoft 365 訂用帳戶的 Azure AD 租用戶處理的驗證程序，或是將使用者重新導向至另一個身分識別提供者。 |
| **適用** | 組織沒有或不需要內部部署 AD DS。 | 使用 AD DS 或另一個身分識別提供者的組織。 |
| **最大優點** | 易於使用。 沒有額外的目錄工具或所需的伺服器。 | 存取內部部署或雲端式資源時，使用者可以使用相同的認證。 |
||||

## <a name="cloud-only-identity"></a>僅限雲端身分識別

僅限雲端身分識別使用只能在 Azure AD 中存在的使用者帳戶。 不需要在內部部署伺服器或不使用 AD DS 管理本機的身分識別的小型組織通常會使用雲端身分識別。 

以下是僅限雲端身分識別的基本元件。
 
![僅限雲端身分識別的基本元件](./media/about-office-365-identity/cloud-only-identity.png)

在內部和遠端 （線上） 的使用者使用其 Azure AD 使用者帳戶和密碼來存取 Office 365 雲端服務。 Azure AD 驗證根據其儲存的使用者帳戶和密碼的使用者認證。

### <a name="administration"></a>系統管理
因為使用者帳戶只會儲存在 Azure AD 中，您可以管理雲端身分識別，例如[Microsoft 365 系統管理中心](https://admin.microsoft.com)和 Windows PowerShell 與 PowerShell 的 Azure Active Directory 針對 Graph 模組的工具。 

## <a name="hybrid-identity"></a>混合式身分識別

混合式身分識別使用的帳戶，源自內部部署 AD DS 並在 Microsoft 365 訂閱下 Azure AD 租用戶中有複本。 不過，大多數變更僅流程其中一種方式。 您所做變更 AD DS 使用者帳戶同步處理至其複本在 Azure AD 中。 但是，在 Azure AD，新的使用者帳戶，例如至雲端架構帳戶所做的變更不會與 AD DS 同步。

Azure AD Connect 提供持續的帳戶同步處理。 它會在內部部署伺服器上，檢查有變更在 AD DS 中，執行，並將這些變更轉寄到 Azure AD。 Azure AD Connect 提供要篩選已同步處理的帳戶，以及是否要同步處理的使用者密碼，又稱為密碼雜湊同步處理 (PHS) 雜湊的版本的能力。

當您實作混合式身分識別，您內部部署 AD DS 是帳戶資訊的授權來源。 這表示您執行管理工作大部分內部，它會再同步到 Azure AD。 

以下是混合式身分識別的元件。

![混合式身分識別的元件](./media/about-office-365-identity/hybrid-identity.png)

Azure AD 租用戶都有一份 AD DS 帳戶。 在此組態中，在內部和遠端使用者存取 Microsoft 365 雲端服務驗證 Azure AD rms。

>[!Note]
>您一定要使用 Azure AD Connect 同步處理的混合式身分識別的使用者帳戶。 您需要的同步處理的使用者帳戶以執行授權工作分派和群組管理、 設定權限，並包含使用者帳戶的其他管理工作的 Azure AD 中。
>

### <a name="administration"></a>系統管理

因為原始與授權的使用者帳戶儲存在內部部署 AD DS 管理 AD DS 中，例如 [Active Directory 使用者及電腦] 工具為相同的工具與您設定身分識別。 

您不使用 Microsoft 365 系統管理中心或 Windows PowerShell 管理 Azure AD 中的同步處理的使用者帳戶。

## <a name="next-step"></a>下一步

如果您需要的僅限雲端身分識別模型，請參閱[僅限雲端身分識別](cloud-only-identities.md)。

如果您需要的混合式身分識別模型，請參閱[目錄同步處理](plan-for-directory-synchronization.md)。
  

## <a name="video-training"></a>影片訓練課程

請參閱影片課程[Office 365： 管理身分識別使用 Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)，由 LinkedIn Learning 帶您。

## <a name="see-also"></a>另請參閱

[Microsoft 365 企業版概觀](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
