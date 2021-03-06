---
title: 配置生產管線
description: 瞭解如何使用雲管理器建立和配置生產管道以部署代碼。
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---


# 配置生產管線 {#configuring-production-pipelines}

瞭解如何使用雲管理器建立和配置生產管道以部署代碼。 如果您首先希望對管道在Cloud Manager中的工作方式進行更概念性的概述，請參閱文檔 [CI/CD管道。](/help/overview/ci-cd-pipelines.md)

## 概觀 {#overview}

使用 **管道設定** 平鋪 [!UICONTROL Cloud Manager] 可建立兩種不同類型的管線。

* **生產管線**  — 生產管道是專門構建的管道，由一系列精心策劃的步驟組成，從您的git儲存庫將原始碼一直帶到生產中。
* **非生產管道**  — 非生產管道主要用於運行代碼質量掃描或將原始碼部署到開發環境中。

本文檔重點介紹生產管線。 有關如何配置非生產管線的詳細資訊，請參閱文檔 [配置非生產管道。](/help/using/non-production-pipelines.md)

的 **部署管理器** 角色負責設定管道。 管道配置包括：

1. 定義將啟動管線的觸發器。
1. 定義控制生產部署的參數。
1. 配置效能test參數。

>[!NOTE]
>
>在其關聯的Git儲存庫具有至少一個分支和 [程式設定](/help/getting-started/program-setup.md) 完成。

## 視頻教程 {#video-tutorial-one}

此視頻提供了管道建立過程的概述，該過程在本文檔中進行了詳細介紹。

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## 添加新生產管道 {#adding-production-pipeline}

一旦你用了 [!UICONTROL Cloud Manager] UI設定程式並至少有一個環境，您已準備好添加生產管道。

1. 登錄到Cloud Manager(位於 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 並選擇相應的組織和程式。

1. 導航到 **管線** 卡 **計畫概述** 的 **+添加** 選擇 **添加生產管道**。

   ![添加生產管道](/help/assets/configure-pipelines/add-prod1.png)

1. 的 **添加生產管道** 對話框 **配置** 的子菜單。 這些選項被分為可折疊的部分，並在以下步驟中進行說明。

   1. 提供管道的描述性名稱 **管道名稱** 的子菜單。

   1. 在 **原始碼** 部分，定義管線檢索其將處理的代碼的位置。

      * **儲存庫**  — 此選項定義管道應從哪個git回購中檢索代碼。
      >[!TIP]
      >
      >查看文檔 [程式設定](/help/getting-started/program-setup.md) 瞭解如何在雲管理器中添加和管理儲存庫。

      * **Git分支**  — 此選項定義管線中應從哪個分支檢索代碼。
      * **代碼位置**  — 此選項定義選定回購的分支中的路徑，管道應從中檢索代碼。

      ![定義管線的回報](/help/assets/configure-pipelines/add-prod2.png)

   1. 在 **環境** 部分，定義觸發部署的觸發器以及應如何按環境展開部署。

      1. 在 **舞台** 段中，可定義管線如何展開到過渡環境。

         * **部署觸發器**  — 您有以下選項來定義啟動管道的部署觸發器。

            * **手動**  — 使用此選項可使用Cloud Manager UI手動啟動管道。
            * **Git更改**  — 只要將提交添加到配置的git分支中，此選項就啟動CI/CD管道。 使用此選項，您仍可根據需要手動啟動管線。
         * **重要度量故障行為**  — 在管線設定或編輯期間，當在任何質量門中遇到重要故障時，「部署管理器」(Deployment Manager)具有定義管線行為的選項。 可用選項包括：

            * **每次詢問**  — 這是預設設定，需要對任何重要故障進行手動干預。
            * **立即失敗**  — 如果選中此選項，則每當發生重要故障時，管線將被取消。 這實質上是模擬用戶手動拒絕每個故障。
            * **立即繼續**  — 如果選中此選項，則每當發生重要故障時，管線將自動繼續。 這實質上是模擬用戶手動批准每個故障。

         ![部署觸發器](/help/assets/configure-pipelines/add-prod3.png)

         * **部署選項**  — 您可以加快某些部署任務。

            * **階段部署後批准**  — 在完成任何測試之前，在部署到登台環境後進行此批准。 否則，在完成所有測試後完成生產部署之前進行審批。

            * **跳過負載平衡器更改**  — 未更改負載平衡器。

         ![暫存部署選項](/help/assets/configure-pipelines/add-prod4.png)

         * **調度程式配置** - **部署管理器** 角色可以配置一組內容路徑，這些路徑在管道運行時將失效或從AEMDispatcher快取中刷新。 這些快取操作將作為部署管道步驟的一部分執行，即在部署任何內容包之後。 這些設定使用標準AEMDispatcher行為。 配置：

            1. 下 **路徑** 提供內容路徑。
            1. 下 **類型**，選擇要在該路徑上執行的操作。
            * **刷新**  — 執行快取無效，類似於內容從創作實例激活到發佈實例時。
            * **失效**  — 執行快取刪除。
            1. 按一下 **添加路徑** 來添加指定的路徑。 每個環境最多可以添加100條路徑。

         ![調度程式配置](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >通常，最好使用失效操作，但可能存在需要刷新的情況，尤其是在使用HTML客戶端庫AEM時。

      1. 在 **生產** 節中，可定義管線如何展開到生產環境。

         * **部署選項**  — 您可以定義控制生產部署的參數。

            * **使用Go Live批准**  — 部署必須由用戶手動批准 **業務所有者**。 **項目經理**&#x200B;或 **部署管理器** 角色 [!UICONTROL Cloud Manager] UI。
            * **計畫**  — 此選項在生產部署之前暫停管道，以允許其計畫。 如果選擇此選項，則管道將在部署到暫存環境後停止，並提示用戶執行操作。
               * **現在**  — 此選項可立即部署到生產環境，有效地完成管道。
               * **日期**  — 此選項允許用戶安排完成部署的時間。
               * **停止執行**  — 此選項將中止部署到生產。

            >[!TIP]
            >
            >請參閱文檔 [代碼部署，](/help/using/code-deployment.md) 瞭解如何設定部署計畫或立即執行管道。

            * **使用CSE監督**  — 如果選擇此選項，則使用CSE來實際啟動部署。 在啟用此選項時建立或編輯管線時， **部署管理器** role具有以下選項。

               * **任何CSE**  — 此選項允許任何可用的CSE啟動部署。
               * **我的CSE**  — 此選項僅允許分配給客戶的特定CSE啟動部署。 如果分配的CSE不可用，則這也適用於CSE的指定備份。

            ![生產部署選項](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **調度程式配置**  — 為生產環境定義調度程式配置。 這些選項與登台環境的選項相同。











1. 按一下 **繼續** 向 **階段測試** 頁籤，根據您已許可的產品，您可以在此配置AEM Sites和AEM Assets效能測試。

   >[!TIP]
   >
   >請參閱文檔 [代碼質量測試](/help/using/code-quality-testing.md#performance-testing) 的子菜單。 **階段測試** 頁籤。

   1. 在 **站點內容交付/分佈式負載權重** 部分，根據三個頁集之間頁請求的權重定義如何配置站點效能測試，這些頁集可以啟用或禁用。

      * **熱門即時頁面**
      * **其他即時頁**
      * **新建頁面**

      ![站點負荷重量](/help/assets/configure-pipelines/add-prod5.png)

   1. 在 **資產效能測試分佈** 部分，定義影像和PDF的test分佈，並定義自己的test資產。

      * **影像**  — 調整滑塊以調整影像和test之間的PDF分割。
      * **PDF**  — 調整滑塊以調整影像和test之間的PDF分割。

      * 通過上載自定義資產來定義自己的自定義資產。

         1. **格式**  — 選擇自定義資產是否是影像的PDF。
         1. **檔案名**  — 使用檔案瀏覽器按鈕從本地電腦中選擇影像。
         1. **添加Test檔案**  — 按一下以上載所選資產。

      ![資產測試分配](/help/assets/configure-pipelines/add-prod6.png)



1. 按一下 **保存** 完成添加生產管道。

## 後續步驟 {#the-next-steps}

配置管道後，需要部署代碼。 請參閱文檔 [代碼部署](/help/using/code-deployment.md) 的子菜單。
