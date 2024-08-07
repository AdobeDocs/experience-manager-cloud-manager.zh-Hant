---
title: 導覽 Cloud Manager UI
description: 了解 Cloud Manager UI 的組織方式以及如何導覽以管理您的程式和環境。
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: d4d9a9f38c5a969f276140dca98731c670547a3d
workflow-type: ht
source-wordcount: '1439'
ht-degree: 100%

---


# 導覽 Cloud Manager UI {#navigation}

了解 Cloud Manager UI 的組織方式以及如何導覽以管理您的程式和環境。

Cloud Manager UI 主要由兩個圖形介面組成：

* [「我的程式」控制台](#my-programs-console)，您可以在其中檢視和管理所有程式。
* [「程式概觀」視窗](#program-overview)，您可以在其中管理個別程式並查看詳細資訊。

## 我的程式控制台 {#my-programs-console}

當您透過 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織時，您將看到「**我的程式**」控制台。

![我的程式控制台](assets/my-programs-console.png)

「我的程式」控制台提供您在所選組織中有權存取之所有程式的概觀。它由幾個部分組成。

1. [工具列](#toolbars-my-programs-toolbars)：提供組織選擇、警示和帳戶設定
1. 標籤：可讓您切換程式的目前檢視。
   * **首頁**&#x200B;檢視 (預設)：選取了「**我的程式**」檢視，其中包含所有程式的概觀
   * **授權**：用於存取授權儀表板授權儀表板僅適用於 AEM as a Cloud Service 程式，不適用於 AMS 程式。
      * 若要確定您的程式所提供的服務類型 (AMS 或 AEMaaCS)，請參閱本文件的[程式卡章節](#program-cards)。
   * 請注意，標籤預設為關閉狀態，可使用 [Cloud Manager 標頭](#cloud-manager-header)中的漢堡選單來顯示
1. [行動號召和統計資料](#cta-statistics)：提供您最近的活動概觀
1. [**我的程式**&#x200B;區段](#my-programs-section)：包含您所有程式的概觀
1. [快速連結](#quick-links)：用於輕鬆存取相關資源

>[!TIP]
>
>有關程式的詳細資訊，請參閱文件：[程式和程式類型](/help/getting-started/program-setup.md)。

### 工具列 {#my-programs-toolbars}

有兩個相互重疊的工具列。

#### Cloud Manager 標頭 {#cloud-manager-header}

第一個是 Cloud Manager 標頭，當您瀏覽 Cloud Manager 時會持續出現。它是一個錨點，可讓您存取適用於 Cloud Manager 程式的設定和資訊。

![Experience Cloud 標頭](assets/experience-cloud-header.png)

1. 漢堡選單提供了對標籤的存取，這些標籤可帶您前往個別程式的特定部分，或在「授權儀表板」和「**[我的程式](#my-programs-console)**」控制台之間切換 (視內容而定)。
   * 授權儀表板僅適用於 AEM as a Cloud Service 程式，不適用於 AMS 程式。
   * 若要確定您的程式所提供的服務類型 (AMS 或 AEMaaCS)，請參閱本文件的[程式卡章節](#program-cards)。
1. 無論您位於 Cloud Manager 中的哪個位置，Cloud Manager 按鈕都會將您帶回 Cloud Manager 的「我的程式」控制台。
1. 點選或按一下「意見回饋」按鈕，即可向 Adobe 提供有關 Cloud Manager 的意見回饋。
1. 組織選擇器會顯示您目前登入的組織 (在本例中為 Foundation Internal)。如果您的 Adobe ID 與多個組織關聯，可點選或按一下以切換到另一個組織。
1. 點選或按一下解決方案切換器可讓您快速跳轉到其他 Experience Cloud 解決方案。
1. 說明圖示可快速存取學習和支援資源。
1. 通知圖示標有目前已指派之未完成的[通知](/help/using/notifications.md)數量。
1. 選取代表您使用者的圖示以存取您的使用者設定。如果您沒有設定使用者圖片，則會隨機分配圖示。

#### 程式工具列 {#program-toolbar}

程式工具列提供了在 Cloud Manager 程式與內容相關的動作之間切換的連結。

![程式工具列](assets/program-toolbar.png)

1. 程式選擇器將會開啟一個下拉式選單，您可以在其中快速選取其他程式或採取內容相關動作，例如建立新程式
1. 透過入門連結，您可以存取[上線文件歷程](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/journey/overview)以幫助您順利執行 Cloud Manager。
   * 請注意，上線歷程是針對 AEM as a Cloud Service 而不是針對 Cloud Service for AMS 而設計的，但許多概念是相同的。
1. 動作按鈕提供內容相關動作，例如建立新程式。

### 行動號召和統計資料 {#cta-statistics}

「行動號召和統計資料」區段為您的組織提供了彙總資料，例如，如果您已成功設定程式，則可能會顯示過去 90 天內的活動統計資料，包括：

* [部署](/help/using/code-deployment.md)數量
* 已識別的[程式碼品質問題](/help/using/code-quality-testing.md)數量
* 組建數量

或者，如果您剛開始設定您的組織，可能會有關於後續步驟或文件資源的提示。

### 我的程式區段 {#my-programs-section}

「我的程式」控制台的主要內容是「**我的程式**」區段，該區段會以個別卡片的形式列出您的程式。點選或按一下卡片即可存取該程式的「**程式概觀**」頁面，以了解有關該程式的詳細資訊。

>[!NOTE]
>
>視您的權限而定，您可能無法選取某些程式。

使用排序選項可以進一步找到您需要的程式。

![排序選項](assets/my-programs-sorting.png)

* 排序依據
   * 建立日期 (預設)
   * 程式名稱
   * 狀態
* 升序 (預設) / 降序
* 格點檢視 (預設)
* 清單檢視

#### 程式卡片 {#program-cards}

每個程式都由一張卡片 (或表格中的列) 表示，提供該程式的概觀以及採取行動的快速連結。

![程式卡片](assets/program-card.png)

* 程式映像 (若已設定)
* 程式名稱
* 服務類型：
   * 適用於 AMS 程式的 **Experience Manager**
   * 適用於 [AEM as a Cloud Service 程式](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/implementing/home)的 **Experience Manager Cloud**
* 狀態
* 設定的解決方案:
* 建立日期

透過資訊圖示，還可以快速存取有關程式的其他資訊 (在清單檢視中很實用)。

![資訊](assets/information-view.png)

透過省略符號圖示，您可以存取可對程式執行的其他動作。

![程式的省略符號按鈕](assets/program-ellipsis.png)

* 瀏覽至程式的特定[環境](/help/using/managing-environments.md)
* 開啟[程式概觀](#program-overview)
* [編輯程式](/help/getting-started/program-setup.md)
* 顯示監視

### 快速連結 {#quick-links}

透過快速連結區段，您可以存取常用的相關資源。

## 程式概觀視窗 {#program-overview}

在&#x200B;[**我的程式**&#x200B;控制台](#my-programs-console)中選取程式後，您將進入「程式概觀」。

![程式概觀](assets/program-overview.png)

透過程式概觀，您可以存取 Cloud Manager 程式的所有詳細資訊。與「我的程式」控制台一樣，它由多個部分組成。

1. [工具列](#program-overview-toolbar)可快速跳回「我的程式」控制台以及導覽程式
1. [索引標籤](#program-tabs)可在程式的不同方面之間切換
1. 根據程式最後動作的[行動號召](#cta) 
1. 程式的[環境概觀](#environments)
1. 程式的[管道概觀](#pipelines)
1. [實用資源](#useful-resources)的連結

### 工具列 {#program-overview-toolbar}

程式概觀的工具列非常相似於[我的程式控制台。](#my-programs-toolbars)唯一的差別說明如下。

#### Cloud Manager 標頭 {#cloud-manager-header-2}

Cloud Manager 標頭有一個漢堡選單，會自動開啟以顯示程式概觀的可導覽索引標籤。

![Cloud Manager 漢堡選單](assets/cloud-manager-hamburger.png)

點選或按一下漢堡選單圖示即可隱藏索引標籤。

#### 程式工具列 {#program-toolbar-2}

程式工具列仍能讓您快速切換到其他程式，而且還可讓您執行內容相關動作，例如新增和編輯程式。

![程式工具列](assets/cloud-manager-program-toolbar.png)

此外，如果您選擇使用漢堡選單來隱藏索引標籤，工具列始終會提供您所在的索引標籤。

### 程式索引標籤 {#program-tabs}

每個程式都有許多與之相關的選項和資料。這些資料會收集到索引標籤中，以方便導覽程式。這些索引標籤可讓您存取：

* 概觀 - 目前文件中所述的程式概觀
* [活動](/help/using/managing-pipelines.md#activity) - 程式的管道執行歷史記錄
* [管道](/help/using/managing-pipelines.md#pipelines) - 為程式設定的所有管道
* [存放庫](/help/managing-code/managing-repositories.md) - 為程式設定的所有存放庫
* [報告](/help/using/monitoring-environments.md#system-monitoring-overview) - SLA 資料等量度
* [環境](/help/using/managing-environments.md) - 為程式設定的所有環境
* [內容集](/help/using/content-copy.md) - 為複製目的而建立的內容集合
* [複製內容活動](/help/using/content-copy.md) - 內容複製活動
* 學習路徑 - 有關 Cloud Manager 的其他學習資源

預設情況下，當您開啟程式時，您會到達「**概觀**」索引標籤。會醒目提示目前的索引標籤。選取另一個索引標籤即可顯示其詳細資訊。

使用 [Cloud Manager 標頭](#cloud-manager-header-2)中的漢堡選單即可隱藏索引標籤。

### 行動號召 {#cta}

行動號召區段將根據您的程式狀態為您提供有用的資訊。對於新程式，您可能會看到提供的後續步驟以及上線日期的提醒，這是[在程式建立期間設定。](/help/getting-started/program-setup.md)

對於即時程式，會看到上次部署的狀態以及詳細資訊和開始新部署的連結。

![行動號召](assets/info-banner.png)

### 環境卡片 {#environments}

「**環境**」卡片為您提供環境的概觀以及快速動作的連結。

「**環境**」卡片只會列出三個環境。按一下「**全部顯示**」按鈕即可查看程式的所有環境。

請參閱文件：[管理環境](/help/using/managing-environments.md)，了解有關如何管理環境的詳細資訊。

### 管道卡片 {#pipelines}

「**管道**」卡片為您提供管道的概觀以及快速動作的連結。

「**管道**」卡片只列出了三個管道。按一下「**全部顯示**」按鈕即可查看程式的所有管道。

請參閱文件：[管理管道](/help/using/managing-pipelines.md)，了解有關如何管理管道的詳細資訊。

### 實用資源 {#useful-resources}

「**實用資源**」區段提供了 Cloud Manager 的其他學習資源的連結。
