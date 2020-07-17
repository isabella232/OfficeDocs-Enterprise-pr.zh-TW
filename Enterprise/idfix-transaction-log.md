---
title: Microsoft 365 IdFix 交易記錄檔
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
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
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: 提供範例，並說明 Microsoft 365 IdFix 交易記錄檔的命名慣例和預設記錄層級。
ms.openlocfilehash: 199d765d640a30fa163f74e6b6029b228b41a63d
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774508"
---
# <a name="microsoft-365-idfix-transaction-log"></a><span data-ttu-id="bf956-103">Microsoft 365 IdFix 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="bf956-103">Microsoft 365 IdFix transaction log</span></span>

<span data-ttu-id="bf956-104">*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="bf956-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="bf956-105">提供範例，並說明 Microsoft 365 IdFix 交易記錄檔的命名慣例和預設記錄層級。</span><span class="sxs-lookup"><span data-stu-id="bf956-105">Provides an example and describes the naming convention and default log level of the Microsoft 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="bf956-106">IdFix 交易記錄位置</span><span class="sxs-lookup"><span data-stu-id="bf956-106">IdFix transaction log location</span></span>

<span data-ttu-id="bf956-107">當您在 IdFix 中按一下 [套用]**並將變更**套用至 Active Directory 樹系時，Microsoft 365 IdFix 工具會建立新的交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bf956-107">The Microsoft 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="bf956-108">交易記錄會儲存在您安裝 IdFix 所在的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bf956-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="bf956-109">根據預設，此資料夾為 C:\Deployment Tools\IDFix。</span><span class="sxs-lookup"><span data-stu-id="bf956-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="bf956-110">交易記錄檔名稱使用日期和時間戳記格式，例如，Verbose 6-1-2018 6-17-22 PM 表示在 6:17:22 2018 的晚上6月1日產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="bf956-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="bf956-111">詳細指出記錄等級。</span><span class="sxs-lookup"><span data-stu-id="bf956-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="bf956-112">IdFix 交易記錄檔記錄層級</span><span class="sxs-lookup"><span data-stu-id="bf956-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="bf956-113">交易記錄檔名稱中的 [文字詳細資訊] 表示檔中的記錄層級。</span><span class="sxs-lookup"><span data-stu-id="bf956-113">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="bf956-114">詳細表示記錄中所捕獲的資訊數目上限。</span><span class="sxs-lookup"><span data-stu-id="bf956-114">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="bf956-115">這是預設的記錄等級。</span><span class="sxs-lookup"><span data-stu-id="bf956-115">This is the default logging level.</span></span> <span data-ttu-id="bf956-116">此時，您無法變更記錄等級。</span><span class="sxs-lookup"><span data-stu-id="bf956-116">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="bf956-117">IdFix 事務歷史記錄格式</span><span class="sxs-lookup"><span data-stu-id="bf956-117">IdFix transaction log format</span></span>

<span data-ttu-id="bf956-118">IdFix 會將每個**更新**動作的結果寫入交易記錄檔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bf956-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE
```