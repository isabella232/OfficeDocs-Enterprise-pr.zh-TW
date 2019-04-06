---
title: Exchange 多地理位置
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解多地理位置功能在 Exchange Online。
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931772"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="f28cb-103">Exchange Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="f28cb-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="f28cb-104">在多地理位置環境中，您可以根據每位使用者選取 Exchange Online 信箱內容 （靜態資料） 的位置。</span><span class="sxs-lookup"><span data-stu-id="f28cb-104">In a multi-geo environment, you can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="f28cb-105">您可以將信箱置於由衛星位置：</span><span class="sxs-lookup"><span data-stu-id="f28cb-105">You can place mailboxes in satellite locations by:</span></span>

- <span data-ttu-id="f28cb-106">直接在衛星位置中建立新的 Exchange Online 信箱</span><span class="sxs-lookup"><span data-stu-id="f28cb-106">Creating a new Exchange Online mailbox directly in a satellite location</span></span>

- <span data-ttu-id="f28cb-107">將現有的 Exchange Online 信箱移至衛星位置中，藉由變更使用者的慣用的資料位置</span><span class="sxs-lookup"><span data-stu-id="f28cb-107">Moving an existing Exchange Online mailbox to a satellite location by changing the user's preferred data location</span></span>

- <span data-ttu-id="f28cb-108">上架的信箱從內部部署 Exchange 組織直接將衛星位置</span><span class="sxs-lookup"><span data-stu-id="f28cb-108">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="f28cb-109">信箱位置及移動</span><span class="sxs-lookup"><span data-stu-id="f28cb-109">Mailbox placement and moves</span></span>
<span data-ttu-id="f28cb-110">Microsoft 完成必要的多地理位置的設定步驟之後，Exchange Online 會受限於使用者物件上的**PreferredDataLocation**屬性在 Azure AD 中。</span><span class="sxs-lookup"><span data-stu-id="f28cb-110">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="f28cb-111">Exchange Online 會同步處理從 Azure AD 的**PreferredDataLocation**屬性到 Exchange Online 的目錄服務中的**MailboxRegion**屬性。</span><span class="sxs-lookup"><span data-stu-id="f28cb-111">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service.</span></span> <span data-ttu-id="f28cb-112">**MailboxRegion**的值會決定要放置使用者信箱和任何相關聯的封存信箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="f28cb-112">The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed.</span></span> <span data-ttu-id="f28cb-113">您不能設定使用者的主要信箱和封存信箱位於不同地理位置。</span><span class="sxs-lookup"><span data-stu-id="f28cb-113">It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations.</span></span> <span data-ttu-id="f28cb-114">只有一個地理位置可能會設定每個使用者物件。</span><span class="sxs-lookup"><span data-stu-id="f28cb-114">Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="f28cb-115">當**PreferredDataLocation**設定與現有信箱使用者時，信箱將會放入佇列中重新配置，而且會自動移至指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="f28cb-115">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="f28cb-116">當**PreferredDataLocation**設定上沒有現有的信箱，使用者佈建信箱時，將會佈建到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="f28cb-116">When **PreferredDataLocation** is configured on a user without an existing mailbox, when you provision the mailbox, it will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="f28cb-117">當**PreferredDataLocation**上未指定一位使用者，當您佈建信箱時，將會佈建中央位置中。</span><span class="sxs-lookup"><span data-stu-id="f28cb-117">When **PreferredDataLocation** is not specified on a user, when you provision the mailbox, it will be provisioned in the central location.</span></span>

- <span data-ttu-id="f28cb-118">如果是不正確的**PreferredDataLocation**程式碼 （例如類型而不是北美洲 NAN），該信箱佈建中央位置中。</span><span class="sxs-lookup"><span data-stu-id="f28cb-118">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be provisioned in the central location.</span></span>

<span data-ttu-id="f28cb-119">**附註**： 在多地理位置功能與 Skype for Business Online 主辦的會議這兩個使用者物件上使用**PreferredDataLocation**屬性來尋找服務。</span><span class="sxs-lookup"><span data-stu-id="f28cb-119">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services.</span></span> <span data-ttu-id="f28cb-120">如果您的地區主辦裝載會議的使用者物件上設定**PreferredDataLocation**值，這些使用者的信箱將會自動移至指定的地理位置之後的 Office 365 租用戶上啟用多地理位置。</span><span class="sxs-lookup"><span data-stu-id="f28cb-120">If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="f28cb-121">Exchange Online 中的多地理功能會受到限制</span><span class="sxs-lookup"><span data-stu-id="f28cb-121">Feature limitations for multi-geo in Exchange Online</span></span>

1. <span data-ttu-id="f28cb-122">安全性與合規性功能 （例如，稽核和 eDiscovery） 可供使用 Exchange 系統管理中心 (EAC) 中無法使用多地理位置組織中。</span><span class="sxs-lookup"><span data-stu-id="f28cb-122">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations.</span></span> <span data-ttu-id="f28cb-123">相反地，您需要使用[Office 365 安全性 & 合規性中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)來設定安全性與合規性功能。</span><span class="sxs-lookup"><span data-stu-id="f28cb-123">Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

2. <span data-ttu-id="f28cb-124">當您將信箱移至新的地理位置，outlook for Mac 使用者可能會遇到暫時遺失其線上封存資料夾存取權。</span><span class="sxs-lookup"><span data-stu-id="f28cb-124">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location.</span></span> <span data-ttu-id="f28cb-125">此條件可發生於使用者的主要和封存信箱皆位於不同地理位置，因為跨地理信箱移動可能會在不同的時間完成。</span><span class="sxs-lookup"><span data-stu-id="f28cb-125">This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-geo mailbox moves may complete at different times.</span></span>

3. <span data-ttu-id="f28cb-126">使用者無法跨 （先前稱為 Outlook Web App 或 OWA） 網頁型 Outlook 中的地理位置間共用*信箱資料夾*。</span><span class="sxs-lookup"><span data-stu-id="f28cb-126">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA).</span></span> <span data-ttu-id="f28cb-127">例如，在歐盟地區的使用者無法用於網頁型 Outlook 開啟的共用的資料夾位於美國境內的信箱中。</span><span class="sxs-lookup"><span data-stu-id="f28cb-127">For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States.</span></span> <span data-ttu-id="f28cb-128">不過，Outlook 網頁使用者可以開啟*其他信箱*中不同 Geos 藉由使用不同的瀏覽器視窗中[開啟另一個人的信箱在 Outlook Web App 中的另一個瀏覽器視窗中](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)所述。</span><span class="sxs-lookup"><span data-stu-id="f28cb-128">However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="f28cb-129">**附註**： 在 Windows 上的 Outlook 中支援跨地理信箱資料夾共用。</span><span class="sxs-lookup"><span data-stu-id="f28cb-129">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

