---
title: 新增生產管道
description: 了解如何使用 Cloud Manager 建立和設定生產管道，以部署程式碼。
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 4c73ab16ff7eab406c31a6d26cdd09360a94b3ea
workflow-type: tm+mt
source-wordcount: 2101
ht-degree: 58%

---

# 新增生產管道 {#configuring-production-pipelines}

了解如何使用 Cloud Manager 建立和設定生產管道，以部署程式碼。 如果您想先了解有關在 Cloud Manager 中管道如何運作的更多概念性概觀，請參閱[CI/CD 管道](/help/overview/ci-cd-pipelines.md)。

## 概觀 {#overview}

使用&#x200B;**管道設定**&#x200B;圖磚 (在 [!UICONTROL Cloud Manager] 中)，您可建立兩種不同類型的管道。

* **生產管道** - 生產管道是一個專門建置的管道，由一系列精心安排的步驟組成，從您的 Git 存放庫取出原始程式碼再一路帶入生產環境。
* **非生產管道** - 非生產管道主要用於執行程式碼品質掃描或將原始程式碼部署到開發環境中。

本文件會專注於生產管道。 如需有關如何設定非生產管道的詳細資訊，請參閱文件[設定非生產管道](/help/using/non-production-pipelines.md)。

**部署管理員**&#x200B;的角色即負責設定管道。 管道設定包括：

1. 定義啟動管道的觸發程序。
1. 定義控制生產部署的參數。
1. 設定效能測試參數。

>[!NOTE]
>
>與管道相關的 Git 存放庫必須具有至少一個分支，且已完成[方案設定](/help/getting-started/program-setup.md)，才能進行管道設定。

## 新增生產管道 {#adding-production-pipeline}

使用 [!UICONTROL Cloud Manager] UI 設定完成方案並擁有至少一個環境後，您便可以著手新增生產管道了。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 瀏覽至「**管道**」卡片 (在「**方案概觀**」頁面)。

1. 按一下「**+ 新增**」，然後選取「**新增生產管道**」。

   ![新增生產管道](/help/assets/configure-pipelines/add-prod7.png)

1. 此&#x200B;**新增生產管道**&#x200B;對話框會開啟&#x200B;**設定**&#x200B;索引標籤，在此會提供幾個必須定義的管道選項。 這些選項會被分組到可摺疊的部份中，並在以下步驟中進行說明。

   1. 在&#x200B;**管道名稱**&#x200B;欄位中為您的管道提供描述性名稱。

   1. 在&#x200B;**環境**&#x200B;部份下，您可以定義部署的觸發器以及應如何在每個環境中推出部署。

      1. 在&#x200B;**中繼**&#x200B;部份中，您可以定義如何將管道推出至您的中繼環境。

         * **部署觸發器** - 您有以下選項可定義部署觸發器，以啟動管道。

            * **手動** - 使用 Cloud Manager UI 手動啟動管道。
            * **在 Git 變更時** - 只要將認可新增到已設定的 Git 分支，就會啟動 CI/CD 管道。 使用此選項，您仍然可以在需要時手動啟動管道。

         * **重要量度失敗行為** - 在管道設定或編輯期間，部署管理員可選擇對任何品質閘道中遭遇重要失敗時的管道行為進行定義。 可使用的選項包括：

            * **每次都詢問** - 預設設定，要求對任何重要失敗進行手動介入。
            * **立即失敗** - 每當重要失敗發生時，便取消管道。 此為模擬使用者手動拒絕每次失敗。
            * **立即持續** - 當重要失敗發生時，管道皆自動繼續。 此為模擬使用者手動核准每次失敗。

         ![部署觸發器](/help/assets/configure-pipelines/add-prod3.png)

         * **部署選項** - 您可加速特定部署任務。

            * **在中繼部署後核准** - 此核准會在部署至中繼環境之後發生，然後才會進行任何測試。 否則就會在生產部署之前進行核准，而這會在完成所有測試後才進行。

            * **略過負載平衡器變更** - 不進行負載平衡器變更。

         ![中繼部署選項](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher 設定** - **部署管理員**&#x200B;角色可設定一組內容路徑，而這組路徑在管道執行時會失效或從 AEM Dispatcher 快取中清除。 在部署任何內容套件後，這些快取動作會視為部署管道步驟一部分來執行。 這些設定使用標準的 AEM Dispatcher 行為。 若要進行設定，請進行以下步驟：

            1. **路徑**&#x200B;下會提供內容路徑。
            1. 在&#x200B;**類型**&#x200B;下，選取在該路徑將採取的操作。

               * **排清** - 執行快取刪除。
               * **失效** - 執行快取失效，類似於將內容從製作執行個體啟動至發佈執行個體的情況。

            1. 按一下&#x200B;**新增路徑**，即可新增您指定的路徑。 您在每個環境最多可新增 100 個路徑。

         ![Dispatcher 設定](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >一般而言，最好使用無效操作，但在某些情況下可能需要排清，尤其是在使用 AEM HTML 用戶端資料庫時。

      1. 在&#x200B;**生產**&#x200B;部份中，您可以定義如何將管道推出至您的生產環境。

         * **部署選項** - 您可定義控制生產部署的參數。

            * **使用上線核准** - 必須由具有&#x200B;**企業所有者**、**專案管理員**&#x200B;或&#x200B;**部署管理員**&#x200B;角色的使用者透過 [!UICONTROL Cloud Manager] UI 手動核准部署。
            * **已排程** - 會在生產部署之前暫停管道，以允許對其進行排程。 如果選取此選項，管道將在部署到中繼環境後暫停，並提示使用者應採取的動作。
               * **`Now`** - 立即部署到生產環境，有效地完成管道。
               * **日期** - 讓使用者安排應完成部署的時間。
               * **停止執行** - 中止到生產環境的部署。

           >[!TIP]
           >
           >請參閱「[程式碼部署](/help/using/code-deployment.md)」，了解如何設定程式碼排程或立即執行管道。

            * **使用 CSE 監督** - 如果選取此選項，則客戶成功工程師 (CSE) 會參與開始實際部署。 在啟用此選項的情況下建立或編輯管道時，**部署管理員**&#x200B;角色會有以下選項。

               * **任何 CSE** - 讓任何有空的 CSE 開始部署。
               * **我的 CSE** - 僅允許指派給客戶的特定 CSE 開始部署。 如果指派的 CSE 沒有空，此選項也適用於 CSE 的指定後援。

           ![生產部署選項](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher 設定** - 定義生產環境的 Dispatcher 設定。 這些選項和中繼環境的選項相同。

1. 按一下[繼續]****&#x200B;以進入&#x200B;**Source程式碼**&#x200B;標籤，您可在其中選取要部署的程式碼型別並設定來源存放庫。

   1. 在&#x200B;**選取要部署的程式碼**&#x200B;下，選擇部署型別：

      * **[完整棧疊程式碼](#full-stack-code)** — 您完整AEM應用程式的程式碼。
      * **[網頁層設定](#web-tier-config)** — 用來儲存、處理及傳送網頁給使用者端的Dispatcher屬性。

      如需這些部署型別的詳細資訊，請參閱[CI/CD管道](/help/overview/ci-cd-pipelines.md#code-sources)。 完成配管設定的剩餘步驟取決於您選取的型別。 按照上面的連結跳到本檔案的相關區段。

1. 按一下「**繼續**」，即可前進到「**中繼測試**」標籤，您可在此設定 AEM Sites 和 AEM Assets 的效能測試 (依您已授權的產品而定)。 {#stage-testing}

   >[!TIP]
   >
   >請參閱「[程式碼品質測試](/help/using/code-quality-testing.md#performance-testing)」，以了解更多有關「**中繼測試**」標籤上可用選項的詳細資訊。

   1. 在「**網站內容傳遞/分散式負載權數**」區段中，您根據三個頁面集之間頁面請求的權重來設定網站效能測試。 您可以根據需要啟用或停用頁面集。

      * **熱門的即時頁面**
      * **其他即時頁面**
      * **新頁面**

      ![網站負載權數](/help/assets/configure-pipelines/add-prod8.png)

   1. 在&#x200B;**資產效能測試分佈**&#x200B;部份下，您可以定義影像和 PDF 的測試分佈並定義您自己的測試資產。

      * **影像** - 調整滑桿即可調整影像和 PDF 之間的測試劃分。
      * **PDF** - 調整滑桿即可調整影像和 PDF 之間的測試劃分。

      * 透過上傳來定義您自己的自訂資產。

         1. **格式** - 選擇您的自訂資產是否為影像的 PDF。
         1. **檔案名稱** - 使用檔案瀏覽器按鈕從您的本機電腦中選取影像。
         1. **新增測試檔案** - 按一下即可上傳您選取的資產。

      ![資產測試分佈](/help/assets/configure-pipelines/add-prod6.png)

1. 按一下&#x200B;**儲存**，即可完成新增生產管道。

### 完整堆疊程式碼 {#full-stack-code}

完整棧疊計畫碼管道部署後端和前端計畫碼構建以及HTTPD/Dispatcher配置。

>[!NOTE]
>
>如果完整棧疊生產管道已存在，則此選項會停用。

**若要設定完整棧疊計畫碼生產管道：**

1. 在&#x200B;**Source程式碼**&#x200B;索引標籤上，定義下列選項。

   * **存放庫** - 定義管道應從哪個 Git 存放庫擷取程式碼。

   >[!TIP]
   >
   >如要了解如何在 Cloud Manager 中新增和管理存放庫，請參閱文件「[方案設定](/help/getting-started/program-setup.md)」。

   * **Git分支** — 定義管道應該從哪個分支擷取程式碼。
   * **忽略 Web 層設定**- 選取後，管道不會部署您的 Web 層設定。 如果相同環境已存在網頁層設定管道，則此核取方塊會自動選取並停用，因為網頁層設定是由該管道管理。 當沒有Web層設定管道時，您可以選取或清除此選項來控制完整棧疊管道是否部署Dispatcher設定。

   ![完整棧疊程式碼來源](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. 按一下&#x200B;**繼續**&#x200B;以進入&#x200B;**階段測試**&#x200B;標籤。 如需詳細資訊，請參閱[中繼測試](#stage-testing)。

### 網頁層設定 {#web-tier-config}

Web層設定管道僅部署HTTPD/Dispatcher設定。 如需此管道型別的詳細資訊，請參閱[CI/CD管道](/help/overview/ci-cd-pipelines.md#deployment-types)。

>[!NOTE]
>
>如果Web層設定生產管道已存在，則此選項會停用。

如果您為具有現有完整棧疊管道的環境建立Web層配置管道，則忽略完整棧疊管道中的Web層配置。 此變更只會影響該環境中的Web層設定。

**若要設定Web層設定生產管道：**

1. 在&#x200B;**Source程式碼**&#x200B;索引標籤上，定義下列選項。

   * **存放庫** — 從下拉式清單中，選取包含網頁層設定的Git存放庫。
   * **Git分支** — 選取Cloud Manager用於部署的所選存放庫中的分支。
   * **程式碼位置** — 在選取的存放庫中輸入包含要部署的Web層組態的路徑。 預設位置是存放庫根目錄(`/`)。

   >[!NOTE]
   >
   >如果程式碼位置未指向Dispatcher程式碼位置，則會將其他應用程式程式碼提取到成品套件中並部署到Dispatcher，導致Apache在重新啟動時失敗，且管道失敗。 請務必為存放庫中的Dispatcher檔案設定正確的路徑。

   ![網頁層設定來源](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. 按一下&#x200B;**繼續**&#x200B;以進入&#x200B;**階段測試**&#x200B;標籤。 如需詳細資訊，請參閱[中繼測試](#stage-testing)。


## 關於在生產管道中使用Smart Build{#about-smart-build}

Cloud Manager中的&#x200B;**智慧型組建**&#x200B;是生產管道的最佳組建策略。 Smart Build會快取模組，並只重新建置自上次成功執行後已變更的模組，藉此縮短建置時間。 未變更的模組會從快取中重複使用，而只會重建已修改的模組及其相依性，進而提高反複開發工作流程的效率。

Smart Build目前可用於下列專案：

* 計畫碼品質管道。
* 開發、測試和生產完整棧疊部署管道。

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

請參閱[新增生產管道](#adding-production-pipeline)以啟用Smart Build。


## 後續步驟 {#the-next-steps}

管道已設定後，請部署您的程式碼。 請參閱「[程式碼部署](/help/using/code-deployment.md)」，了解更多詳細資訊。

## 教學課程影片 {#video-tutorial-one}

本影片將概觀管道建立流程，而本文件中有詳細說明。

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
