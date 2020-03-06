---
title: 使用受管理來賓建立 B2B 外部網路
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: 了解如何建立 B2B 外部網路網站或小組，並提出從夥伴組織的受管理的來賓使用者。
ms.openlocfilehash: cdf4470920a307d569fcfd650f40c77f4a5423a4
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549062"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>使用受管理來賓建立 B2B 外部網路

若要建立外部網路 B2B 共同作業與夥伴組織使用 Azure Active Directory，您可以使用[Azure Active Directory 權益 Management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) 。 這可讓使用者自行註冊在外部網路網站或小組及接收存取方式核准工作流程。

使用此方法的共用資源進行共同作業時，是指夥伴組織可協助維護及核准來賓使用者在其結束時，降低您的 IT 部門的負擔，並且讓這些最熟悉管理使用者共同作業協議存取。

本文會逐步完成步驟來建立套件 （在此情況下、 網站或小組） 您可以透過自助服務存取註冊模型夥伴組織與共用的資源。 

開始之前，請建立網站或小組，您想要與夥伴組織共用，並啟用的來賓共用。 如需詳細資訊，請參閱[共同作業與網站中的來賓](collaborate-in-a-site.md)或[小組中的來賓與共同作業](collaborate-as-a-team.md)。 我們也建議您檢閱[建立安全的來賓共用環境](create-a-secure-guest-sharing-environment.md)的安全性與合規性功能，您可用於協助維護與來賓控管原則時進行共同作業的相關資訊。

## <a name="connect-the-partner-organization"></a>連線到夥伴組織

若要邀請來賓從夥伴組織，您必須新增為連結的組織在 Azure Active Directory 中的協力廠商的網域。

若要新增的已連線的組織
1. 在[Azure Active Directory](https://aad.portal.azure.com)中，按一下 [**身分識別管理**]。
2. 按一下 [**連線的組織**。
4. 按一下 [**新增連線組織**。
5. 輸入的名稱和描述組織，然後再按一下**下一步： 目錄 + 網域**。
6. 按一下 [**新增目錄 + 網域**]。
7. 輸入您想要連線，請在組織的網域，然後按一下 [**新增]**。
8. 按一下 [**連線**]，然後按一下 [**下一步： 贊助者**。
9. 從您的組織或您要連接至您想要核准來賓使用者的存取權的使用者的組織新增人員。
10. 按一下 [**下一步： 檢閱 + 建立**。
11. 檢閱您選擇，然後按一下 [**建立**的設定。

    ![Azure Active Directory 中的 [連線的組織] 頁面的螢幕擷取畫面](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>選擇要共用的資源

選取要與夥伴組織的共用資源的第一個步驟是建立來包含這些目錄。

若要建立目錄
1. 在[Azure Active Directory](https://aad.portal.azure.com)中，按一下 [**身分識別管理**]。
2. 按一下 [**目錄**]。
3. 按一下 [**新增目錄**]。
4. 輸入的名稱和描述目錄的應用程式，並確定， **Enabled**並**已啟用的外部使用者**都設定為 **[是]**。
5. 按一下 **[建立]**。

   ![在 [Azure Active Directory 身分識別管理 [目錄] 頁面的螢幕擷取畫面](media/identity-governance-catalogs.png)

一旦建立目錄的應用程式之後，您可以新增 SharePoint 網站或小組，您想要與夥伴組織共用。

若要將資源新增至目錄
1. 在 Azure AD Identity 控管，按一下 [**目錄**]，，然後按一下您要將資源新增型的錄。
2. 按一下 [**資源**]，然後按一下 [**新增資源**。
3. 選取的小組或您想要包含在您網路中的 SharePoint 網站，然後按一下 [**新增]**。

   ![Azure Active Directory 身分識別管理目錄資源] 頁面的螢幕擷取畫面](media/identity-governance-catalog-resource.png)

一旦您已經定義您想要共用的資源下, 一步是建立 access 封裝，它所定義的授與協力廠商使用者存取類型和新的合作夥伴使用者要求存取權的核准程序。

若要建立 access 封裝
1. 在 Azure AD Identity 控管，按一下 [**目錄**，，然後按一下 [您要建立 access 封裝的目錄。
2. 按一下 [ **Access 套件**]，然後按一下 [**新的 access 封裝**。
3. 輸入的名稱和描述 access 封裝，然後再按一下**下一步： 資源角色**。
4. 選擇您想要用於您網路的目錄資源。
5. 針對每個資源，在 [**角色**] 欄中，選擇您想要授與使用外部網路的來賓使用者的使用者角色。
6. 按一下 [**下一步： 要求**。
7. 在 [**可以要求存取的使用者**，選擇 [**不在您的目錄中的使用者**。
8. 確定**特定的連接的組織**選項已選取，然後按一下 [**新增目錄**。
9. 選擇您稍早，新增連接的組織，然後按一下 [**選取**
10. 在 [**核准**] 下選擇 [針對**需要核准**的 [**是**]。
11. 在 [**第一位核准者**，選擇下列其中一個之前加入贊助者或選擇特定的使用者。
12. 按一下 [**新增後援**，然後選取 [後援核准者。
13. [**啟用**，請選擇 [**是**]。
14. 按一下 [**下一步： 生命週期**。
15. 選擇 [到期日及存取檢閱 [設定您想要使用，然後按一下 [**下一步： 檢閱 + 建立**。
16. 檢閱設定，然後再按一下 [**建立**。

    ![在 Azure Active Directory 身分識別管理的存取套件畫面的螢幕擷取畫面](media/identity-governance-access-packages.png)

如果您正在與大型組織合作，您可能想要隱藏存取套件。 如果已隱藏封裝，然後夥伴組織中的使用者不會看到封裝其 *「 我的存取*入口網站上。 相反地，他們必須傳送註冊套件的直接連結。 隱藏存取套件可以降低不適當的存取要求的數目，也可協助保護組織的夥伴組織的入口網站中的可用的存取套件。

若要將存取套件屬性設定為隱藏
1. 在 Azure AD Identity 控管，按一下 [ **Access 套件**]，然後按一下您存取的套件。
2. 在 [**概觀**] 頁面上，按一下 [**編輯**]。
3. 在 [**屬性**] 下的**隱藏**，選擇 [**是]** ，然後按一下 [**儲存**。

   ![編輯存取套件內容] 畫面的螢幕擷取畫面](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>邀請合作夥伴使用者

如果您將 access 封裝為隱藏，您需要的直接連結傳送到夥伴組織，以便他們可以要求存取網站或小組。

若要尋找存取入口網站連結
1. 在 Azure AD Identity 控管，按一下 [ **Access 套件**]，然後按一下您存取的套件。
2. 在 [**概觀**] 頁面上，按一下**複製到剪貼簿**連結**我存取入口網站連結**。

   ![使用存取入口網站連結即可存取套件屬性的螢幕擷取畫面](media/identity-governance-access-portal-link.png)

一旦您已複製連結，您可以將它共用與您的夥伴組織的連絡人，他們可以將它傳送給上共同作業小組的使用者。

## <a name="see-also"></a>另請參閱

[建立安全的來賓共用環境](create-a-secure-guest-sharing-environment.md)

