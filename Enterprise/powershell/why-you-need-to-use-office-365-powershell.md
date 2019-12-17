---
title: 為什麼要使用 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 摘要：了解為何您必須使用 Office 365 PowerShell 來管理 Office 365，在某些情況下更有效率，在另一些情況則是必然。
ms.openlocfilehash: ecf386e39c9610f0444789cdc11441be545ea814
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072425"
---
# <a name="why-you-need-to-use-office-365-powershell"></a>為什麼要使用 Office 365 PowerShell

使用 Microsoft 365 系統管理中心，您可以不只管理您的 Office 365 使用者帳戶和授權，但您也可以管理您的 Office 365 服務，例如 Exchange Online、 microsoft Teams，和 SharePoint Online。 不過，您也可以使用 Office 365 PowerShell 命令來管理這些元素 (利用命令列與指令碼語言環境，可獲得速度、自動化和其他功能等優勢)。
  
在本文中，我們會顯示您在其中您可以使用 Office 365 PowerShell 管理 Office 365 的方法：
  
- 揭露您無法看到使用 Microsoft 365 系統管理中心的其他資訊
    
- 設定功能和唯一可能的設定與 Office 365 PowerShell
    
- 執行大量作業
    
- 篩選資料
    
- 列印或儲存資料
    
- 管理整個服務
    
在您開始之前，請了解 Office 365 PowerShell 是 Windows PowerShell (Windows 服務和平台的命令列環境) 的一組模組。此環境會建立可透過其他模組擴充的命令殼層語言，並提供方法來執行簡單或複雜的命令或指令碼。例如，在您安裝 Office 365 PowerShell 模組並連線至 Office 365 訂閱之後，可以執行此命令來列出 Microsoft Exchange Online 的所有使用者信箱：
  
```powershell
Get-Mailbox
```

取得清單中的信箱可以也能輕鬆地完成使用 Microsoft 365 系統管理中心中，但計數中的所有 web 應用程式的所有網站的所有清單的項目數無法輕鬆完成。
  
請注意，Office 365 PowerShell 設計來增強和增強您能夠管理 Office 365，無法以取代 Microsoft 365 系統管理中心。 身為 Office 365 系統管理員，您至少必須熟悉如何使用 Office 365 PowerShell，因為有一些組態程序只能使用 Office 365 PowerShell 命令完成。 在這些情況下，您必須了解如何：
  
- 安裝 Office 365 PowerShell 模組 (每部系統管理員電腦都會執行一次)。
    
- 連線至 Office 365 訂閱 (每個 PowerShell 工作階段都會執行一次)。
    
- 收集執行必要 Office 365 PowerShell 命令所需的資訊。
    
- 已順利執行 Office 365 PowerShell 命令。
    
了解這些基本技術之後，您不需要使用 **Get-mailbox** 命令列出信箱使用者，也不需要了解如何建立新命令 (例如前一個命令來計算所有 Web 應用程式之所有網站的所有清單中的所有項目)。Microsoft 和 Office 365 系統管理員社群可視需要協助您使用該作業。
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>Office 365 PowerShell 可以揭露使用 Microsoft 365 系統管理中心無法看到的其他資訊

在 Microsoft 365 系統管理中心會顯示很多有用的資訊，但這並不表示它會顯示 Office 365 會儲存在使用者、 授權、 信箱和站台的所有可能資訊。 以下是**使用者和群組**中的 Microsoft 365 系統管理中心的範例：
  
![顯示在 Microsoft 365 系統管理中心中使用者和群組的範例。](media/o365-powershell-users-and-groups.png)
  
在許多用途中，這會顯示您需要知道的資訊。 不過，您有時需要更多的資訊。 例如，Office 365 授權 （和使用者提供的 Office 365 功能） 部份取決於該使用者的地理位置。 您可延伸到美國使用者的原則和功能，與您可延伸到印度或比利時使用者的原則和功能可能不大一樣。 您可以使用 Microsoft 365 系統管理中心來判斷使用者的地理位置，使用下列步驟：
  
1. 連按兩下使用者的 **[顯示名稱]** 。
    
2. 在使用者內容顯示窗格中，按一下 **[詳細資料]** 。
    
3. 在詳細資料顯示中，按一下 **[其他詳細資料]** 。
    
4. 向下捲動，直到您看到 **[國家或地區]** 標題為止。
    
     ![在 Microsoft 365 系統管理中心中的使用者的地區資訊的範例。](media/o365-powershell-usage-location.png)
  
5. 在一張紙上寫下使用者的顯示名稱和位置，或複製並貼到 [記事本]。 
    
您必須為每位使用者重複此程序。對於許多使用者，這可能是冗長乏味的工作。使用 Office 365 PowerShell，您可以透過下列命令，針對所有使用者顯示這項資訊：
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

以下是顯示範例：
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有使用者 ( **Get-MsolUser** )，但只顯示每位使用者的名稱和位置 ( **Select DisplayName, UsageLocation** )。
  
因為 Office 365 PowerShell 支援命令殼層語言，所以您可以進一步處理透過 **Get-MSolUser** 命令取得的資訊。例如，您可能會想要按使用者的位置來排序使用者、將所有巴西使用者群組在一起、將所有美國使用者群組在一起等等。命令如下：
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

以下是顯示範例：
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有使用者，但只顯示每位使用者的名稱和位置，並依序按其位置和名稱來進行排序 ( **Sort UsageLocation, DisplayName** )。
  
您也可以使用其他篩選。例如，如果您只想看到巴西使用者的資訊，請使用這個命令：
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

以下是顯示範例：
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得位置是巴西的目前 Office 365 訂閱中的所有使用者 ( **Where {$\_.UsageLocation -eq "BR"}** )，然後顯示每位使用者的名稱和位置。
  
 **與較大型網域相關的備註**
  
如果您有超大型的網域 (擁有數萬名的使用者)，嘗試我們在本文中所示範的部分範例可能會走向「節流」。這表示根據如運算能力和可用網路頻寬等項目，您可能一次做太多事情。因此，較大型組織可能會想要將這些 Office 365 PowerShell 命令分割成兩個命令。例如，此命令會傳回所有使用者帳戶，並顯示每位使用者的名稱和位置：
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

該命令非常適合較小型的網域。然而，在大型組織中，您可能需要將它分割成兩個命令：一個命令用來將使用者帳戶資訊儲存至變數中，而另一個命令用來顯示所需的資訊。範例如下：
  
```powershell
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```

這組 Office 365 PowerShell 命令的解譯如下：
- 取得目前 Office 365 訂閱中的所有使用者，並將資訊儲存至名為 $x 的變數 ( **$x = Get-MsolUser** )。
- 顯示變數 $x 的內容，但只會包括每位使用者的名稱和位置 ( **$x | Select DisplayName, UsageLocation** )。
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a>Office 365 具有的功能，僅供您搭配 Office 365 PowerShell 所設定

在 Microsoft 365 系統管理中心被預定用於提供給最常見或有意義的系統管理任務適用於大部分的人的存取。 換句話說，在 Microsoft 365 系統管理中心設計被為了讓一般的系統管理員可以使用工具來執行的最常見的管理工作。 根據此定義，這表示有無法使用 Microsoft 365 系統管理中心完成某些工作。
  
例如，商務用 Skype Online 系統管理中心提供一些選項來建立自訂會議邀請：
  
![在商務用 Skype Online 系統管理中心內，自訂會議邀請顯示方式的範例。](media/o365-powershell-meeting-invitation.png)
  
使用這些設定，您可以新增會議邀請的一些個人化和專門技術。不過，這不只是建立自訂會議邀請，還會進行其他會議組態設定。例如，會議預設允許：
  
- 匿名使用者自動進入每個會議。
    
- 出席者記錄會議。
    
- 您組織的所有使用者在加入會議時都會指定為主持人。
    
這些設定無法從 商務用 Skype Online 系統管理中心取得。不過，您可以透過 Office 365 PowerShell 控制它們。以下是停用這三項設定的命令：
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> 這個命令需要您安裝 [商務用 Skype Online PowerShell 模組](https://www.microsoft.com/download/details.aspx?id=39366)。 
  
> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：對於新商務用 Skype Online 會議的設定 ( **Set-CsMeetingConfiguration** )，停用允許匿名使用者自動進入會議 ( **-AdmitAnonymousUsersByDefault $False** )、停用出席者錄製會議的功能 ( **-AllowConferenceRecording $False** )，但不會將您組織的所有使用者都指定為簡報者 ( **-DesignateAsPresenter "None"** )。
  
如果您改變主意想要還原這些預設設定 (全部都已啟用)，請執行這個命令：
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

這只是其中一個範例。還有其他範例，這就是為什麼您身為 Office 365 系統管理員必須熟悉如何執行 Office 365 PowerShell 命令。
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a>Office 365 PowerShell 十分適合執行大量作業

在過去，像在 Microsoft 365 系統管理中心的視覺介面是最有價值，當您有執行單一作業。 例如，如果您要停用某個使用者帳戶，您可用於 Microsoft 365 系統管理中心快速找出並清除核取方塊。 這可能會比在 Office 365 PowerShell 中執行類似作業還要簡單。
  
但如果您有許多事項或其他方面的一大組內所選的一些變更，在 Microsoft 365 系統管理中心可能不適合使用您的時間。 例如，如果必須變更在數千個電話號碼的前置詞，或是您需要從所有 SharePoint Online 網站中都移除特定使用者，Ken Myer，要如何，在 Microsoft 365 系統管理中心？
  
對於後面的範例，您有數百個 SharePoint Online 網站，而且甚至不知道 Ken Meyer 所屬的網站。 這表示您必須在 Microsoft 365 系統管理中心開頭，並再執行此程序的每個網站：
  
1. 按一下網站的 **URL** 。
    
2. 在 [網站集合內容] 方塊中，按一下 [網站位址] 連結以開啟網站。
    
3. 在網站上，按一下 [共用]。
    
4. 在 [共用] 對話方塊中，按一下連結，以顯示所有具有網站權限的使用者：
    
     ![在 SharePoint Online 系統管理中心內，檢視 SharePoint Online 網站成員的範例。](media/o365-powershell-view-permissions.png)
  
5. 在 [共用對象] 對話方塊中，按一下 [進階]。
    
6. 捲動使用者清單，並尋找和選取 Ken Myer (假設他具有網站權限)，然後按一下 [移除使用者權限]。
    
因為有數百個網站，所以這可能需要很長的時間。
  
另一種方法是使用 Office 365 PowerShell 和下列命令，從所有網站中移除 Ken Myer：
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> 此命令需要您安裝[SharePoint Online PowerShell 模組](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。 
  
> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有 SharePoint 網站 ( **Get-SPOSite** )，並且針對每個網站，從可存取它的使用者清單中移除 Ken Meyer ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** )。
  
因為我們告訴 Office 365 移除每個網站中的 Ken Meyer (包括他沒有存取權的網站)，所以針對他目前沒有存取權的網站，此命令會顯示錯誤。 我們可以在此命令上使用其他條件，只從登入清單中有 Key Meyer 的網站中移除 Key Meyer，但列出的錯誤不會傷害網站本身。 此命令，可能需要幾分鐘數百個站台，針對執行，而不是直接透過 Microsoft 365 系統管理工作時數置中。
  
以下是另一個大量作業範例。使用此命令將 Bonnie Kearney (新的 SharePoint 系統管理員) 新增至組織中的所有網站：
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有 SharePoint 網站，並針對每個網站，將 Bonnie Kearney 的登入名稱新增至網站的 [成員] 群組來允許她的存取權 ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** )。
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a>Office 365 PowerShell 十分適合篩選資料

在 Microsoft 365 系統管理中心提供數種不同的方式，快速地篩選您的資料，並輕鬆地找到目標的資訊子集。 例如，Exchange 可輕鬆篩選使用者信箱的任何內容。 例如，以下是住在布魯民頓市中所有使用者的信箱清單：
  
![進階以進行搜尋 Microsoft 365 系統管理中心中的信箱清單的所有使用者住在布魯民頓市/鎮的範例。](media/o365-powershell-advanced-search.png)
  
Exchange 系統管理中心也可讓您合併篩選準則。例如，您可以找到住在布魯民頓市並且在財務部門工作之所有人的信箱。 
  
不過，在 Exchange 系統管理中心內有一些限制。例如，您可能想要找到住在布魯民頓市或聖地牙哥市之人員的信箱，或不住在布魯民頓市之所有人員的信箱。 
  
使用 Office 365 PowerShell，您可以透過此命令來取得住在布魯民頓市或聖地牙哥市之所有人員的信箱清單：
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

以下是顯示範例：
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中具有布魯民頓市或聖地牙哥市信箱的所有使用者 ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** )，然後顯示每個人員的名稱和城市 ( **Select DisplayName, City** )。
  
若要列出不住在布魯民頓市之人員的所有信箱，則命令如下：
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

以下是顯示範例：
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中信箱不在布魯民頓市的所有使用者 ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** )，然後顯示每個使用者的名稱和城市。
  
您也可以在 Office 365 PowerShell 篩選中使用萬用字元，來比對局部名稱。例如，假設您正在尋找一個使用者帳戶，而且您只記得姓氏是 Anderson 或 Henderson，也可能是 Jorgenson。
  
您可以追蹤該使用者在 Microsoft 365 系統管理中心中，使用搜尋工具並執行三種不同搜尋：
  
- 一個用於  *Anderson* 
    
- 一個用於  *Henderson* 
    
- 一個用於  *Jorgenson* 
    
因為這三個名稱的結尾都是 "son"，所以您可以告訴 Office 365 PowerShell 顯示名稱結尾為 "son" 的所有使用者。命令如下：
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有使用者，但使用只會列出姓氏結尾為 "son" 之使用者的篩選器 ( **-Filter '{LastName -like "\*son"}'** )。\* 代表任何字元集 (即使用者姓氏中的字母)。
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a>Office 365 PowerShell 可讓您輕鬆地列印或儲存資料

在 Microsoft 365 系統管理中心可讓您檢視資料的清單。 以下是商務用 Skype Online 系統管理中心範例，其中顯示已啟用商務用 Skype Online 的使用者清單：
  
![商務用 Skype Online 系統管理中心，顯示商務用 Skype Online 已啟用的使用者清單的範例。](media/o365-powershell-lync-users.png)
  
若要將該資訊儲存至檔案，您必須複製該資訊，並將它貼到文件或 Excel。 在任一情況下，複本可能都需要進行其他格式設定。 此外，在 Microsoft 365 系統管理中心不提供方法，可以直接列印所顯示的清單。
  
幸運的是，您可以使用 Office 365 PowerShell，這不只會顯示清單，還會將它儲存至可輕鬆地匯入至 Excel 的檔案。以下範例命令可將 商務用 Skype Online 使用者資料儲存為逗點分隔值 (CSV) 檔案，而這是可輕鬆地匯入為 Excel 工作表中的資料表的檔案：
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

以下是顯示範例：
  
![儲存成逗點分隔值 (CSV) 檔案的商務用 Skype Online 使用者資料表，匯入到 Excel 工作表中的範例。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有商務用 Skype Online 使用者 ( **Get-CsOnlineUser** )、只取得使用者名稱、UPN 和位置 ( **Select DisplayName, UserPrincipalName, UsageLocation** )，然後將資訊儲存至名稱為 C:\\Logs\\SfBUsers.csv 的 CSV 檔案中 ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** )。
  
您也可以使用選項，將此清單儲存為 XML 檔案或 HTML 頁面。事實上，使用其他 PowerShell 命令，您可以直接將它儲存為 Excel 檔 (內含任何您想要的自訂格式)。 
  
您也可以傳送 Office 365 PowerShell 命令的輸出，而此命令會直接將清單顯示在 Windows 的預設印表機中。範例命令如下：
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

以下是您將列印出的文件樣貌：
  
![Office 365 PowerShell 命令直接列在 Windows 預設印表機上，所輸出的列印文件範例。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有商務用 Skype Online 使用者、只取得使用者名稱、UPN 和位置，然後將該資訊傳送至預設 Windows 印表機 ( **Out-Printer** )。
  
列印出的文件與 Office 365 PowerShell 命令視窗內所顯示的內容，具有相同的簡單格式，但建立 Office 365 PowerShell 命令來列出您需要的內容之後，只要將 **| Out-Printer** 新增至命令的結尾，即可取得可使用的複本。
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a>Office 365 PowerShell 可讓您管理數個伺服器產品

構成 Office 365 的不同元件是設計為一起使用。例如，假設您新增 Office 365 的新使用者，並在新增時指定使用者部門和電話號碼之類的資訊。如果您使用任何 Office 365 伺服器產品存取使用者的資訊，即可使用這些資訊。商務用 Skype Online、Exchange 或 SharePoint Online。
  
不過，這是對跨越產品系列的一般資訊而言。產品特定資訊 (例如，使用者的 Exchange 信箱相關資訊) 通常不會跨系列提供。例如，如果您想要知道是否已啟用使用者的信箱，則只能在 Exchange 系統管理中心內取得該資訊。 
  
假設您想要製作一份報告，顯示所有使用者的下列資訊：
  
- 使用者的顯示名稱
    
- 使用者是否獲得 Office 365 的授權
    
- 使用者的 Exchange 信箱是否已啟用
    
- 是否已對使用者啟用商務用 Skype Online
    
您目前無法使用 Microsoft 365 系統管理中心輕鬆地產生此類報表。 相反地，您必須建立不同的文件來儲存的資訊，例如 Excel 工作表，並取得所有的使用者名稱及授權資訊從 Microsoft 365 系統管理中心中，從 Exchange 系統管理中心取得信箱資訊、 取得商務用 SkypeSkype 商務 Online 系統管理中心，從商務 Online 資訊然後 collate，並將該資訊合併。
  
另一種方法是使用 Office 365 PowerShell 指令碼來編譯該報告。
  
下列範例指令碼會比目前為止在本文中看過的命令還要複雜。但是，它示範可能可以使用 Office 365 PowerShell 建立很難做到的資訊檢視。以下指令碼可以編譯並顯示所需的清單：
  
```powershell
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

以下是顯示範例：
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

此 Office 365 PowerShell 指令碼的解譯如下：  
- 取得目前 Office 365 訂閱中的所有使用者，並將資訊儲存至名為 $x 的變數 ( **$x = Get-MsolUser** )。
- 開始迴圈，而迴圈會對名稱為 $x 之變數中的所有使用者執行 ( **foreach ($i in $x)** )。  
- 定義名稱為 $y 的變數，並在其中儲存使用者的信箱資訊 ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** )。
- 將新的屬性新增至名稱為 IsMailBoxEnabled 的使用者資訊，並將它設定為使用者信箱的 IsMailBoxEnabled 屬性值 ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** )。
- 定義名稱為 $y 的變數，並在其中儲存使用者的商務用 Skype Online 資訊 ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** )。
- 將新的屬性新增至名稱為 EnabledForSfB 的使用者資訊，並將它設定為使用者之商務用 Skype Online 資訊的 Enabled 屬性值 ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** )。
- 顯示使用者清單，但只包括其名稱、是否獲得授權，以及指出是否已啟用其信箱以及其是否已啟用商務用 Skype Online 的兩個新屬性 ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** )。
  
## <a name="see-also"></a>另請參閱

[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Windows PowerShell 在 Office 365 中建立報告](use-windows-powershell-to-create-reports-in-office-365.md)

