---
title: 導覽 Cloud Manager UI
description: 了解 Cloud Manager UI 的組織方式以及如何導覽此 UI 來管理您的方案和環境。
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: b98e1711f1f98f52977dd6cb4cd2bc834d81a360
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 52%

---


# 導覽Cloud Manager UI {#navigation}

了解 Cloud Manager UI 的組織方式以及如何導覽此 UI 來管理您的方案和環境。

Cloud Manager UI 主要由兩個圖形介面組成：

* [「我的方案」控制台](#my-programs-console)，您可以在其中檢視和管理所有方案。
* [「方案概觀」視窗](#program-overview)，您可以在其中管理個別方案並查看詳細資訊。

## 「我的方案」控制台 {#my-programs-console}

當您在[experience.adobe.com](https://experience.adobe.com/experiencemanager)登入Cloud Manager並選取適當的組織時，就會進入&#x200B;**我的程式**&#x200B;主控台。

![我的方案控制台](/help/getting-started/assets/cloud-manager-my-programs-console.png)

**我的程式**&#x200B;主控台提供您在所選組織中有權存取的所有程式的總覽。 它由幾個部分組成。

|   | 區域 | 描述 |
| --- | --- | --- |
| 1 | [工具列](#toolbars-my-programs-toolbars) | 用於組織選擇、警示和帳戶設定。 |
| 2 | 左側面板索引標籤 | 可讓您切換程式目前檢視的各種標籤，包括下列專案：<br><ul><li>**Experience Manager**&#x200B;會開啟各種AEM解決方案的首頁</li><li>**所有程式**&#x200B;會顯示所有可用的程式。</li><li>**授權**&#x200B;開啟授權儀表板。 授權儀表板僅適用於&#x200B;*AEM as a Cloud Service計畫* (AEMaaCS)，不適用於Adobe Managed Services計畫，例如AEM 6.5和AEM 6.5 LTS。 若要判斷您的程式具有的服務型別（AEMaaCS或AMS），請參閱本文的[程式卡片區段](#program-cards)。 索引標籤預設為關閉，並可使用位於![Cloud Manager標題](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)左側的[顯示功能表圖示（漢堡](#cloud-manager-header)）下拉式功能表來顯示。</li></ol> |
| 3 | [我的程式](#my-programs-section) | 列出您可以選取的所有可用程式。<br>如需有關程式的詳細資訊，請參閱[程式和程式型別](/help/getting-started/program-setup.md)。 |
| 4 | [行動號召與統計資料](#cta-statistics) | 提供您最近活動的概覽。 |
| 5 | [快速連結](#quick-links) | 快速存取相關資源。 |


### 工具列 {#my-programs-toolbars}

有兩個相互重疊的工具列。

#### Cloud Manager 標頭 {#cloud-manager-header}

第一個是 Cloud Manager 標頭。當您瀏覽 Cloud Manager 時標頭會持續顯示。它是一個錨點，可讓您存取適用於 Cloud Manager 方案的設定和資訊。

![Experience Cloud 標頭](/help/getting-started/assets/cloud-manager-header-toolbar.png)

| 區域 | 說明 |
| --- | --- |
| ![顯示功能表圖示，漢堡](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) | 一個下拉式功能表，可讓您存取個別程式特定部分的索引標籤。<br>若要判斷您的程式具有的服務型別（AMS或AEMaaCS），請參閱本檔案的[程式卡片區段](#program-cards)。 |
| ![Adobe紅白圖示](/help/getting-started/assets/AdobeLogoWhiteOnRed.svg) Cloud Manager | 按一下以開啟Cloud Manager的&#x200B;**我的程式**&#x200B;主控台，無論您身在Cloud Manager何處。 |
| *`Name of selected organization`* | 組織選擇器會顯示您目前登入的組織（在此範例中為&#x200B;*Foundation Internal*）。 如果您的Adobe ID與多個組織相關聯，請按一下以切換至其他組織。 |
| ![意見回饋圖示](/help/getting-started/assets/AppComment.svg)意見 | 按一下「 」，向Adobe提供有關Cloud Manager的意見回饋。 |
| ![AI助理圖示](/help/getting-started/assets/AIChat.svg) | AI Assistant提供對話式介面，旨在簡化為AEM相關查詢尋找答案的程式。 檢視[AI小幫手](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/ai-in-aem/ai-assistant/ai-assistant-in-aem#) |
| ![說明圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_HelpOutline_18_N.svg) | 按一下以提供學習與支援資源的快速存取權。 |
| ![白鈴圖示](/help/getting-started/assets/Bell.svg) | 按一下以檢視目前指派的不完整[通知數目](/help/using/notifications.md) |
| ![應用程式圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) | 按一下以在AEM首頁和AEM解決方案之間快速移動 |
| *`Dynamic Account icon`* | 按一下您的使用者圖片以存取您的&#x200B;**帳戶設定**&#x200B;和&#x200B;**程式設定**，或者登出。<br>如果您選擇不新增使用者圖片，圖示會隨機指派（如上方工具列影像所示）。 |

<!--
1. The ![Show menu icon, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) icon on the left side of the header is  
   * The License Dashboard only applies to AEM as a Cloud Service programs, not AMS programs.
   * To determine the type of service your program has (AMS or AEMaaCS), see the [Program Cards section](#program-cards) of this document.
1. The **Adobe Cloud Manager** button takes you back to the **My Programs** console of Cloud Manager no matter where you are in Cloud Manager.
1. Click **Feedback** to provide feedback to Adobe about Cloud Manager.
1. The organization selector displays the organization that you are currently signed into (in this example, Foundation Internal). Click to switch to another organization if your Adobe ID is associated with multiple.
1. Clicking the solutions switcher lets you quickly jump to other Experience Cloud solutions.
1. The Help icon provides quick access to learning and support resources.
1. The notifications icon is badged with the number of currently assigned incomplete [notifications](/help/using/notifications.md)
1. Select the icon representing your user to access your user settings. If you do not select a user picture, an icon is randomly assigned. -->

#### 方案工具列 {#program-toolbar}

方案工具列提供了在 Cloud Manager 方案與內容相關的動作之間切換的連結。

![Cloud Manager程式工具列](/help/getting-started/assets/cloud-manager-programs-toolbar.png)

|   | 區域 | 描述 |
| --- | --- | --- |
| 1 | 我的方案 | 按一下以開啟下拉式清單，您可在其中選擇新增方案、選取其他現有方案或返回Experience Manager首頁。 |
| 2 | ![資訊圖示](/help/getting-started/assets/Info.svg)快速入門 | 按一下以存取[上線檔案歷程](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/journey/overview)，讓您快速上手Cloud Manager。<br>入門歷程是針對Adobe Experience Manager as a Cloud Service (AEMaaCS)上的Cloud Manager而設計，而非針對Adobe Managed Services (AMS)上的Cloud Manager。 不過，有許多概念都是相同的。 |
| 3 | *`Dynamic action button`* | 動作按鈕提供適合內容的動作，您可以按一下，例如&#x200B;**新增程式** （如上例所示）或新增網域。 |

### 行動號召和統計資料 {#cta-statistics}

「行動號召和統計資料」部份為您的組織提供了彙總資料，例如，如果您已成功設定方案，則可能會顯示過去 90 天內的活動統計資料，包括：

* [部署](/help/using/code-deployment.md)數量
* 已識別的[程式碼品質問題](/help/using/code-quality-testing.md)數量
* 組建數量

或者，如果您剛開始設定您的組織，可能會有關於後續步驟或文件資源的提示。

### 我的方案 {#my-programs-section}

「我的方案」控制台的主要內容為「**我的方案**」區段，該區段會以個別卡片的形式列出您的方案。按一下卡片即可存取該方案的「**方案概觀**」頁面，了解有關該方案的詳細資訊。

依您的權限而定，您可能無法選取某些方案。

您可以使用下列排序選項來快速尋找您想要的程式：

![排序選項](/help/getting-started/assets/cloud-manager-my-programs-sorting.png)

* 排序方式：
   * 建立日期
   * 方案名稱
   * 狀態
* ![向下排序圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) / ![向上排序圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg)分別向下或向上排序程式。
* ![傳統格線檢檢視示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) / ![文字專案符號圖示或清單](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TextBulleted_18_N.svg)分別以格線表單或清單表單檢視程式。

#### 方案卡片 {#program-cards}

每個方案都以一張卡片或表格中的一列來呈現，提供該方案的概觀以及採取動作的快速連結。

![方案卡片](/help/getting-started/assets/cloud-manager-program-card.png)

* 程式影像 (若已設定)
* 程式名稱（在上述範例中，*WKND Magazine*）
* 服務類型：
   * 適用於 AMS 方案的 **Experience Manager**
   * 適用於 [AEM as a Cloud Service 方案](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/implementing/home)的 **Experience Manager Cloud**
* 狀態（在上述範例中，*就緒*）
* 設定的解決方案:
* 建立日期

按一下「![資訊」圖示](/help/getting-started/assets/Info.svg)即可快速存取此程式的額外資訊（在清單檢視中很有用）。

在Cloud Manager AMS中![資訊快顯功能表](/help/getting-started/assets/cloud-manager-information-view.png)

按一下![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)可讓您存取可以對程式執行的其他動作。

![方案的省略符號按鈕](/help/getting-started/assets/cloud-manager-program-ellipsis.png)

* Experience Manager首頁
* 瀏覽至方案的特定[環境](/help/using/managing-environments.md)
* 開啟[方案概觀](#program-overview)
* [編輯方案](/help/getting-started/program-setup.md)
* 顯示監視

### 快速連結 {#quick-links}

透過快速連結區段，您可以存取實用的相關資源。

## 「方案概觀」視窗 {#program-overview}

在「[**我的方案**」控制台](#my-programs-console)中選取一項方案後，您會進入「**方案概觀**」頁面。

![方案概觀](/help/getting-started/assets/cloud-manager-program-overview.png)

**計畫總覽**&#x200B;可讓您存取Cloud Manager計畫的所有詳細資料。 與&#x200B;**我的程式**&#x200B;類似，它由幾個部分組成。

1. [工具列](#program-overview-toolbar)可快速跳回「**我的方案**」控制台並瀏覽方案。
1. [索引標籤區域](#program-tabs)可在程式的不同方面之間切換。
1. [行動號召](#cta)以方案的最後動作為依據。
1. 與程式的[環境](#environments)相關聯。
1. 已關聯方案的[管道](#pipelines)。

### 工具列 {#program-overview-toolbar}

「方案概觀」的工具列與[「我的方案」控制台](#my-programs-toolbars)工具列相似。此處圖解僅說明差異部分。

#### Cloud Manager 標頭 {#cloud-manager-header-2}

Cloud Manager標題有一個![顯示功能表圖示，漢堡](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)下拉式功能表，會自動開啟以顯示計畫總覽的可導覽標籤。

按一下![顯示功能表圖示，漢堡](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以隱藏標籤。

#### 方案工具列 {#program-toolbar-2}

方案工具列同樣能讓您快速切換到其他方案，而且還可讓您執行內容相關動作，例如新增和編輯方案。

![方案工具列](assets/cloud-manager-program-toolbar.png)

此外，如果您使用![顯示功能表圖示（漢堡](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)）隱藏標籤，工具列仍會顯示您目前所在的標籤。

### 方案標籤 {#program-tabs}

每個方案都有許多相關聯的選項和資料。這些資料會收集到索引標籤中，以方便導覽方案。這些索引標籤可讓您存取：

* 概觀 - 目前文件中所述的方案概觀
* [活動](/help/using/managing-pipelines.md#activity) - 方案的管道執行歷史記錄
* [管道](/help/using/managing-pipelines.md#pipelines) - 為方案設定的所有管道
* [存放庫](/help/managing-code/managing-repositories.md) - 為方案設定的所有存放庫
* [報告](/help/using/monitoring-environments.md#system-monitoring-overview) - SLA 資料等量度
* [環境](/help/using/managing-environments.md) - 為方案設定的所有環境
* [內容集](/help/using/content-copy.md) - 為複製目的而建立的內容集合
* [複製內容活動](/help/using/content-copy.md) - 內容複製活動
* 學習路徑 - 有關 Cloud Manager 的其他學習資源

預設情況下，當您開啟方案時，您會到達「**概觀**」索引標籤。會醒目提示目前的索引標籤。選取另一個索引標籤即可顯示其詳細資訊。

使用![Cloud Manager標題](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)中的[顯示功能表圖示，漢堡](#cloud-manager-header-2)來隱藏標籤。

### 行動號召 {#cta}

行動號召區段會根據您的方案狀態為您提供有用的資訊。對於新方案，您可能會看到建議後續步驟和上線日期提醒，[均於方案建立期間設定](/help/getting-started/program-setup.md)。

對於即時方案，會看到上次部署的狀態以及詳細資訊和開始新部署的連結。

![行動號召](assets/info-banner.png)

### 環境卡片 {#environments}

「**環境**」卡片為您提供環境的概觀和快速動作的連結。

「**環境**」卡片只會列出三個環境。按一下「**全部顯示**」按鈕即可查看方案的所有環境。

請參閱「[管理環境](/help/using/managing-environments.md)」，了解有關如何管理環境的詳細資訊。

### 管道資訊卡 {#pipelines}

「**管道**」卡片為您提供管道的概觀和快速動作的連結。

「**管道**」卡片只列出了三個管道。按一下「**全部顯示**」按鈕即可查看方案的所有管道。

請參閱「[管理管道](/help/using/managing-pipelines.md)」，了解有關如何管理管道的詳細資訊。

### 實用資源 {#useful-resources}

「**實用資源**」區段提供 Cloud Manager 的其他學習資源連結。
