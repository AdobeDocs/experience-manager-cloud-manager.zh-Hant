---
title: 新增非生產管道
description: 了解如何使用 Cloud Manager 建立和設定非生產管道以部署代碼。
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 261c4334a514ee2101444e83a559d300bba3d507
workflow-type: tm+mt
source-wordcount: '1994'
ht-degree: 22%

---

# 新增非生產管道 {#configuring-non-production-pipelines}

了解如何使用 Cloud Manager 建立和設定非生產管道以部署程式碼。 如果您想先了解有關在 Cloud Manager 中管道如何運作的更多概念性概觀，請參閱[CI/CD 管道](/help/overview/ci-cd-pipelines.md)。

## 概觀 {#overview}

使用&#x200B;**管道**&#x200B;圖磚 (在 [!UICONTROL Cloud Manager] 中)，**部署管理員**&#x200B;可建立兩個不同類型的管道。

* **生產管道** — 生產管道是一個專門建置的管道，由一系列精心安排的步驟組成，以將原始程式碼一路帶入生產環境。
* **非生產管道** - 非生產管道主要用於執行程式碼品質掃描或將原始程式碼部署到開發環境中。

本文件會專注於非生產管道。 如需有關如何設定生產管道的詳細資訊，請參閱文件[設定生產管道](/help/using/production-pipelines.md)。

有兩種類型的非生產管道：

* **程式碼品質管道** - 這些管道會對 Git 分支中的程式碼執行程式碼品質掃描，並執行建置和程式碼品質步驟。
* **部署管道** - 除了執行程式碼品質管道之類的建置和程式碼品質步驟，這些管道還會將程式碼部署到非生產環境。

>[!NOTE]
>
>您必須等到與管道相關的Git存放庫具有至少一個分支且[程式設定](/help/getting-started/program-setup.md)完成時，才能設定管道。 如欲了解如何在 Cloud Manager 中新增和管理存放庫，請參閱 [Cloud Manager 存放庫](/help/managing-code/managing-repositories.md)。

## 新增一個全新非生產管道 {#add-non-production-pipeline}

在Cloud Manager UI中設定方案和至少一個環境後，您可以新增非生產管道。 在部署到生產環境之前，使用這些管道來測試計畫碼品質。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從Cloud Manager主畫面中，開啟管道卡並按一下&#x200B;**新增**，然後選取&#x200B;**新增非生產管道**。

   ![新增非生產管道](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. 在&#x200B;**新增非生產管道**&#x200B;對話方塊的&#x200B;**組態**&#x200B;索引標籤上，選取您要建立的管道型別（下列其中一項）：

   * **程式碼品質管道** — 建立管道，在不部署至環境的情況下，建置程式碼、執行單元測試和評估程式碼品質。
   * **部署管道** — 建立管道，用於建置程式碼、執行單元測試、評估程式碼品質，以及部署到環境。

   ![選擇管道類型](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB 程式碼品質管道 — 設定索引標籤]

| 章節 | 選項 | 說明 |
| --- | --- | --- |
| **管道設定** | **非生產管道名稱** | 在&#x200B;**非生產管道名稱**&#x200B;欄位中輸入管道的說明。 |
|  | **正在測試** | 只有在編輯非生產管道時才可見。<br>UI會顯示管道執行的測試類別，做為程式碼品質驗證的一部分。<ul><li>**靜態程式碼測試** — 分析程式碼的品質和正確性問題。<li>**負載/效能測試** — 評估管線測試中與效能相關的行為。<li>**安全性測試** — 檢查程式碼和管道輸出中的安全性相關問題。 |
| **部署選項** | **部署觸發程式** | <ul><li>**手動** - 讓您能手動啟動管道。<li>**在 Git 變更時** - 當認可版本新增到所設定的 Git 分支時啟動管道。 使用此選項，您仍然可以在必要時手動啟動管道。 |
|  | **重要量度失敗行為** | <ul><li>**每次都詢問** - 此行為是預設設定，要求對任何重要失敗進行手動介入。<li>**立即失敗** — 如果選取，則每當重要失敗發生時，就會取消管道。 它基本上會模擬使用者手動拒絕每個失敗。<li>**立即繼續** — 如果選取，則每當重要失敗發生時，管道會自動繼續。 它基本上會模擬使用者手動核准每次失敗。</li></ul> |
|  | **中繼部署後核准**&#x200B;核取方塊 | 只有在編輯非生產管道時才可見。<br>選取此選項要求在部署到中繼環境後，管道才能繼續。 如果未選取此選項，則管道會根據設定的行為繼續。 |

>[!TAB 部署管道 — 設定索引標籤]

| 章節 | 選項 | 說明 |
| --- | --- | --- |
| **管道設定** | **非生產管道名稱** | 在&#x200B;**非生產管道名稱**&#x200B;欄位中輸入管道的說明。 |
|   | **符合資格的部署環境** | 如果您的管道是部署管道，您必須選擇Cloud Manager部署計畫碼的環境。 |
|   | **正在測試** | 只有在編輯非生產管道時才可見。<br>UI會顯示管道執行的測試類別，做為程式碼品質驗證的一部分。<ul><li>**靜態程式碼測試** — 分析程式碼的品質和正確性問題。<li>**負載/效能測試** — 評估管線測試中與效能相關的行為。<li>**安全性測試** — 檢查程式碼和管道輸出中的安全性相關問題。</li></ul> |
| **部署選項** | **部署觸發程式** | <ul><li>**手動** - 讓您能手動啟動管道。<li>**在 Git 變更時** - 當認可版本新增到所設定的 Git 分支時啟動管道。 使用此選項，您仍然可以在必要時手動啟動管道。 |
|   | **重要量度失敗行為** | <ul><li>**每次都詢問** — 預設設定，並提示使用者在重要量度失敗時決定如何繼續。<li>**立即失敗** — 只要重要量度失敗，就會取消管道。 這基本上是模擬使用者手動拒絕每次失敗。<li>**立即繼續** — 每當重要量度失敗時，管道就會自動繼續。 這基本上是模擬使用者手動核准每次失敗。</li></ul> |
|  | **中繼部署後核准**&#x200B;核取方塊 | 只有在編輯非生產管道時才可見。<br>選取此選項要求在部署到中繼環境後，管道才能繼續。 如果未選取此選項，則管道會根據設定的行為繼續。 |
|  | **略過負載平衡器變更**&#x200B;核取方塊 | 選取此選項可防止管道在部署期間進行負載平衡器變更。 |
|  | **Dispatcher設定** | **部署管理員**&#x200B;角色可設定在執行管道時失效或從AEM Dispatcher快取中排清的一組內容路徑。 在部署任何內容套件後，Cloud Manager會在部署管道步驟中執行這些快取動作。 這些設定使用標準的 AEM Dispatcher 行為。 若要設定`Dispatcher`，請執行下列動作：<ul><li>在&#x200B;**PATH**&#x200B;底下，提供您想要管道排清或失效的內容路徑。<li>在&#x200B;**類型**&#x200B;下，選取在該路徑將採取的操作。<ul><li>**排清** — 在指定的路徑上執行快取刪除。</li><li>**失效** - 執行快取失效，類似於將內容從製作執行個體啟動至發佈執行個體的情況。</li><li>按一下&#x200B;**新增路徑**，即可新增您指定的路徑。 您在每個環境最多可新增 100 個路徑。</li></ul> |
| **管道** | **體驗稽核**&#x200B;核取方塊 | 選取此選項可在管道中包含體驗稽核步驟。 啟用後，管道會在Source程式碼索引標籤之後包含體驗稽核步驟。 |

>[!ENDTABS]

1. 在&#x200B;**新增非生產管道**&#x200B;對話方塊的右下角，按一下&#x200B;**繼續**。
1. 選取管道設定為建置和部署的程式碼型別。

>[!BEGINTABS]

>[!TAB Source程式碼標籤 — 完整棧疊程式碼]

部署完整的AEM應用程式，包括應用程式程式碼，以及依預設的Web層設定。

| 章節 | 選項 | 說明 |
| --- | --- | --- |
| **Source代碼** | **存放庫** | 從下拉式清單中，選擇管道用作其來源的Git存放庫。 Cloud Manager會從您在此選擇的存放庫建置程式碼。 |
|   | **Git分支** | 從下拉式清單中，選擇管道應建置的來源（所選存放庫）分支。 預設為 `main`。 管道使用所選分支作為構建和部署的來源。 如有必要，請按一下[重新整理]&#x200B;**&#x200B;**&#x200B;來更新所選存放庫的可用分支清單。 如果最近建立的分支未出現在清單中，請使用此選項。 |
|   | **建置策略** | <ul><li>**完整組建** — 每次都會建置存放庫中的所有模組<li>Beta **智慧型建置** — 僅建置自上次認可以來已變更的模組。<br>深入瞭解[在非生產管道中使用智慧型建置](#about-smart-build)。</li></ol>**重要**： Smart Build僅適用於計畫碼品質管道和開發完整棧疊計畫碼部署管道。 |
|   | **忽略Web層組態**&#x200B;核取方塊 | 選取此選項可跳過在完整棧疊計畫碼管道中部署Web層設定。 取消選取此選項以部署網頁層級設定以及管道的程式碼。 |
| **管道** | **體驗稽核**&#x200B;核取方塊 | 選取此選項可在管道中包含體驗稽核步驟。 啟用後，管道會在Source程式碼索引標籤之後包含體驗稽核步驟。 |

>[!TAB Source程式碼 — Web層設定]

僅部署Web層設定，例如用來儲存、處理網頁以及將網頁傳送給使用者端的Dispatcher屬性。 當您選取&#x200B;**網頁層設定**&#x200B;時，Cloud Manager會建立專用於網頁層設定部署的管道。

如果完整棧疊管道已存在，Cloud Manager會顯示通知，指出建立Web層設定管道會導致現有完整棧疊管道忽略Web層設定。 在您建立網頁層級設定管道後，Cloud Manager會透過該管道（而非完整棧疊管道）管理網頁層級設定部署。

| 章節 | 選項 | 說明 |
| --- | --- | --- |
| **Source代碼** | **存放庫** | 從下拉式清單中，選取包含網頁層設定的Git存放庫。 |
|   | **Git分支** | 在選擇的存放庫中選取Cloud Manager用於部署的分支。 如有必要，請按一下[重新整理]&#x200B;**&#x200B;**&#x200B;來更新所選存放庫的可用分支清單。 如果最近建立的分支未出現在清單中，請使用此選項。 |
|   | **代碼位置** | 在選取的存放庫中輸入包含要部署的Web層設定的路徑。 預設位置是存放庫根目錄(`/`)。 |

>[!ENDTABS]

1. 按一下「**儲存**」。

## 關於在非生產管道中使用Smart Build{#about-smart-build}

Cloud Manager中的&#x200B;**智慧型組建**&#x200B;是非生產管道的最佳組建策略。 Smart Build會快取模組，並只重新建置自上次成功執行後已變更的模組，藉此縮短建置時間。 未變更的模組會從快取中重複使用，而只會重建已修改的模組及其相依性，進而提高反複開發工作流程的效率。

Smart Build目前僅適用於下列專案：

* 計畫碼品質管道。
* 開發完整棧疊部署管道。

>[!NOTE]
>
>啟用Smart Build後的首次執行行為類似於Full Build，因為快取是空的。

發生下列情況時，建議使用Smart Build：
* 您正在積極開發和提交頻繁的增量變更。
* 您的專案包含多個Maven模組。
* 完整組建需要相當長的時間。

有以下情況時，Smart Build並不總是理想的選擇：
* 您的組建嚴重依賴外掛程式，這些外掛程式會在Maven的相依性圖表之外執行操作。
* 每次執行都需要完整重建驗證。

### 瞭解組建效能{#smart-build-performance}

使用Smart Build的效能提升取決於幾個因素，包括：

* 專案中的模組數。
* 程式碼變更的頻率和範圍。
* 跨模組的相依性分佈。

一般而言，具有許多獨立模組的專案可以有最大的改善。

### 每個模組快取選擇退出{#smart-build-cache-optout}

Smart Build提供可讓您停用特定模組快取的精細控制項。 此功能在某些模組中相當實用：

* 使用外掛程式，例如`exec-maven-plugin`或`maven-antrun-plugin`。
* 執行Maven相依性未追蹤的檔案操作。
* 快取時產生不一致的結果。

### 停用模組的快取{#smart-build-disable-caching}

您可以將下列屬性新增至受影響模組的`pom.xml`：

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

此語法會強制模組在每次管道執行時重建，而其他模組會繼續受益於快取。

### 使用Smart Build時的限制和考量{#smart-build-limitations}

使用Smart Build時，請記得下列事項：

* Smart Build仰賴Maven相依性分析。
* 相依性圖表以外的變更可能不會觸發重新建置。
* 有些外掛程式可能與快取不完全相容。
* 您可以透過編輯非生產管道隨時切換回&#x200B;**完整組建**。

如果您遇到非預期的建置行為，請考慮停用特定模組的快取，或暫時將建置策略切換為&#x200B;**完整建置**。

### 疑難排解智慧型組建問題{#smart-build-troubleshoot}

| 問題 | 建議的解決方案 |
| --- | --- |
| 建置結果不一致 | ·停用受影響模組的快取。<br>·驗證外掛程式行為（尤其是`exec`/`antrun`外掛程式）。 |
| 沒有效能改善 | ·確定已發生多次執行（快取熱身）。<br>·檢查大多數模組是否頻繁變更。 |
| 未預期的成品或遺失的變更 | ·檢閱變更是否在Maven相依性追蹤之外。<br>·使用&#x200B;**完整組建**&#x200B;進行驗證。 |

請參閱啟用Smart Build時新增非生產管道[&#128279;](#add-non-production-pipeline)。



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Enter the repository where the pipeline should retrieve the code.

   * **Repository** - Select the Git repository that the pipeline retrieves code from.
   * **Git Branch** - Select the branch in the Git repository that the selected pipeline retrieves code from.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - Cloud Manager cancels the pipeline whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that Cloud Manager invalidates or flushes from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## 後續步驟 {#the-next-steps}

管道設定後，可以部署您的程式碼。 請參閱「[程式碼部署](/help/using/code-deployment.md)」，了解更多詳細資訊。

## 教學課程影片 {#video-tutorial}

本影片將概觀管道建立流程，而本文件中有詳細說明。

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
