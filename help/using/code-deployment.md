---
title: 程式碼部署
description: 了解如何部署您的程式碼以及部署時 Cloud Manager 中會發生什麼情況。
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 97%

---


# 程式碼部署 {#code-deployment}

了解如何部署您的程式碼以及部署時 Cloud Manager 中會發生什麼情況。

## 使用Cloud Manager部署程式碼 {#deploying-code-with-cloud-manager}

設定好生產管道 (包括必要的存放庫和環境) 後，便是準備好可以部署程式碼。

1. 從 Cloud Manager 按一下&#x200B;**部署**，即可開始部署流程。

   ![部署按鈕](/help/assets/Deploy1.png)

1. 會顯示&#x200B;**管道執行**&#x200B;畫面。按一下&#x200B;**建置**，即可開始流程。

   ![建置按鈕](/help/assets/Deploy2.png)

建置流程會啟動程式碼部署流程，包括以下步驟：

* 中繼部署
* 中繼測試
* 生產部署

您可以透過檢視記錄或檢閱測試標準的結果來查看各種部署流程的步驟。

## 部署步驟 {#deployment-steps}

在部署的每個步驟中都會進行許多操作，本區段將說明相關內容。如需有關如何在幕後部署程式碼本身的技術細節，請參閱「[部署流程詳細資訊](#deployment-process)」。

### 中繼部署步驟 {#stage-deployment}

此&#x200B;**中繼部署**&#x200B;步驟包括下列操作：

* **驗證**：此步驟確保管道設定為使用目前可用的資源。例如，設定的分支是否存在以及環境是否可用。
* **建置及單位測試**：此步驟會執行容器化的建置流程。如需詳細資訊，請參閱「[建置環境](/help/getting-started/build-environment.md)」。
* **程式碼掃描**：此步驟會評估應用程式程式碼的品質。如需有關測試流程的詳細資訊，請參閱「[了解測試結果](/help/using/code-quality-testing.md)」。
* **部署至中繼**

![中繼部署](/help/assets/Stage_Deployment1.png)

### 中繼測試步驟 {#stage-testing}

此&#x200B;**中繼測試**&#x200B;步驟包括下列操作：

* **安全測試**：此步驟會評估您的程式碼對 AEM 環境的安全影響。如需有關測試流程的詳細資訊，請參閱文件：[了解測試結果](/help/using/code-quality-testing.md)。
   * **效能測試**：此步驟會評估程式碼的效能。如需有關測試流程的詳細資訊，請參閱「[了解測試結果](/help/using/code-quality-testing.md)」。

### 生產部署步驟 {#production-deployment}

**生產部署**&#x200B;步驟包括下列動作：

* **申請核准**
   * 設定管道時會啟用此選項。
   * 使用此選項，您可以進行生產部署的排程或按一下&#x200B;**現在**，以立即執行生產部署。
* **生產部署排程**
   * 設定管道時會啟用此選項。
   * 排程的日期和時間會根據使用者的時區指定。
     ![排程部署](/help/assets/Production_Deployment1.png)
* **CSE 支援** (如啟用)
* **部署至生產環境**

![生產部署](/help/assets/Prod_Deployment1.png)

部署完成後，您的程式碼將在其目標環境中，而且您可以檢視紀錄。

![部署完成](/help/assets/Production_Deployment2.png)

## 逾時 {#timeouts}

如果久候使用者的意見回饋，以下步驟會逾時：

| 步驟 | 逾時 |
|--- |--- |
| 程式碼品質測試 | 7 天 |
| 安全測試 | 7 天 |
| 效能測試 | 7 天 |
| 申請核准 (階段) | 7 天 |
| 申請核准 (生產) | 14 天 |
| 生產部署排程 | 14 天 |
| 管理生產部署 | 14 天 |

## 部署流程詳細資料 {#deployment-process}

Cloud Manager 會將建置流程產生的所有 target/*.zip 檔案上傳到儲存位置。這些成品是在管道的部署階段從該位置擷取的。

當 Cloud Manager 部署到非生產拓撲時，目標是盡快完成部署，因此會將成品同時部署到所有節點，如下所示：

1. Cloud Manager 會決定每個成品是 AEM 或是 Dispatcher 套件。
1. Cloud Manager 會從負載平衡器中移除所有 Dispatcher，以在部署期間隔離環境。

   * 除非另有設定，否則您可以在開發和中繼部署中跳過負載平衡器變更。也就是說，對於開發環境，分離和附加兩個非生產管道中的步驟，對於中繼環境，則分離和附加生產管道中的步驟。

   ![跳過負載平衡器](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >預計 1-1-1 客戶將使用此功能。

1. 每個 AEM 成品都會透過封裝管理程式 API 部署到每個 AEM 執行個體，並由封裝相依性決定部署順序。

   * 若要了解更多如何使用套件安裝新功能、在執行個體之間傳輸內容以及將存放庫內容備份的詳細資訊，請參閱「[封裝管理程式](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-cloud-service/content/implementing/developer-tools/package-manager)」。

   >[!NOTE]
   >
   >所有 AEM 成品都會部署給作者和發佈者。當需要節點特定的設定時，應利用運行模式。若要了解有關運行模式如何讓您能夠針對特定目的調整 AEM 執行個體的詳細資訊，請參閱[「部署到 AEM as a Cloud Service」文件的「運行模式」一節](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-cloud-service/content/implementing/deploying/overview#runmodes)。

1. Dispatcher 成品會依照以下方式部署到每個 Dispatcher：

   1. 會將目前設定備份並複製到暫時的位置。
   1. 除不可變檔案外，所有設定都將遭到刪除。如需更多詳細資訊，請參閱 [Dispatcher 設定](/help/getting-started/dispatcher-configurations.md)。此方式會清除目錄以確保沒有遺留孤立的檔案。
   1. 成品會被擷取至 `httpd` 目錄。不可變檔案並不會被覆寫。您對 Git 存放庫中不可變檔案所進行的任何變更會在部署時被忽略。這些檔案為 AMS Dispatcher 架構的核心，且無法變更。
   1. Apache 會執行設定測試。如果未發現錯誤，則會重新載入服務。如果發生錯誤，則從備份中還原設定，重新載入服務，並將錯誤回報 Cloud Manager。
   1. 管道設定中指定的每個路徑都會無效或從 Dispatcher 快取中清除。

   >[!NOTE]
   >
   >Cloud Manager 期望 Dispatcher 成品包含完整的檔案集。所有 Dispatcher 設定檔案都必須在 Git 存放庫中。遺漏檔案或檔案夾會導致部署失敗。

1. 將所有 AEM 和 Dispatcher 套件成功部署到所有節點後，會將 Dispatcher 加回負載平衡器，部署即告完成。

   >[!NOTE]
   >
   >您可以在開發和中繼部署中跳過負載平衡器變更。也就是說，對於開發環境，分離和附加兩個非生產管道中的步驟，對於中繼環境，則分離和附加生產管道中的步驟。

### 部署至生產階段 {#deployment-production-phase}

為了將對 AEM 網站訪客的影響降至最低，部署到生產拓撲的流程會略有不同。

生產部署通常會遵循和上述相同的步驟，但採用滾動方式：

1. 將 AEM 套件部署給作者。
1. 將 Dispatcher1 和負載平衡器分離。
1. 將 AEM 套件部署到 Publish1 並同時將 Dispatcher 套件部署到 Dispatcher1，清除 Dispatcher 快取。
1. 將 Dispatcher1 放回負載平衡器中。
1. 一旦 Dispatcher1 重新投入使用，即會將 Dispatcher2 和負載平衡器分離。
1. 將 AEM 套件部署到 Publish2 並同時將 Dispatcher 套件部署到 Dispatcher2，清除 Dispatcher 快取。
1. 將 Dispatcher2 放回負載平衡器中。

本流程會一直持續到部署已經觸及拓撲中的所有發佈者和 Dispatcher 為止。

## 緊急管道執行模式 {#emergency-pipeline}

在關鍵情況下，Adobe Managed Services 客戶可能需要立即將程式碼變更部署至其中繼和生產環境。此能力使他們能夠繞過完整的 Cloud Manager 週期。

為了解決這些情況，可在緊急模式下執行 Cloud Manager 生產管道。使用此模式時，不執行安全性和效能測試步驟。所有其他步驟 (包括任何已設定的核准步驟) 都會按照正常管道執行模式執行。

>[!NOTE]
>
>緊急管道執行模式功能會依逐個方案啟動。由客戶成功工程師完成啟用。

### 使用緊急管道執行模式 {#using-emergency-pipeline}

當您開始執行生產管道時，可以從對話框中選擇正常模式或緊急模式。如果方案已啟用緊急管道執行模式功能，則此選項可用。當該功能啟用後，此選項便可用。

![執行管道選項](/help/assets/execution-emergency1.png)

以緊急模式檢視管道執行詳細資訊頁面以進行執行時，畫面最上方的階層連結會顯示指示器，表示管道正以緊急模式執行。

![緊急模式階層連結](/help/assets/execution-emergency2.png)

以緊急模式執行管道也能透過 Cloud Manager API 或 CLI 完成。若要以緊急模式開始執行，請使用查詢參數 `?pipelineExecutionMode=EMERGENCY` 向管道的執行端點提交 `PUT` 請求，或者在使用 CLI 時：

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## 重新執行生產部署 {#reexecute-deployment}

在極少數情況下，生產部署步驟可能會因暫時原因而失敗。在這些情況下，只要生產部署步驟已完成，您就可以重新執行該步驟，無論其為成功、取消或不成功。使用由以下三個步驟組成的相同管道，即支援重新執行：

1. **驗證步驟** - 與在正常管道執行期間發生的驗證相同。
1. **建置步驟** - 在重新執行的內容中，建置步驟會複製成品，實際上並非執行新的建置程序。
1. **生產部署步驟** - 使用和正常管道執行中之生產部署步驟相同的設定和選項。

在可以重新執行的情況下，生產管道狀態頁會提供「**重新執行**」選項 (在一般「**下載建置記錄**」選項旁)。

![管道概觀視窗中的重新執行選項](/help/assets/re-execute.png)

>[!NOTE]
>
>在重新執行中，UI 會標示建置步驟，以反映這是在複製成品，而不是重新建置。

### 限制 {#limitations}

* 重新執行生產部署步驟僅適用於最後執行。
* 重新執行不適用於復原執行或「推送更新」執行。
* 如果最後執行在生產部署步驟之前的任何時候失敗，則無法重新執行。


### 重新執行API {#reexecute-api}

除了可在 UI 中使用之外，您還可以使用 [Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) 觸發重新執行，並識別已作為重新執行來觸發的執行。

#### 觸發重新執行 {#triggering}

若要觸發重新執行，需要向生產部署步驟狀態的 HAL 連結 `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` 發出 `PUT` 請求。

* 如果此連結存在，則可以從該步驟重新開始執行。
* 如果不存在，則無法從該步驟重新開始執行。

此連結僅適用於生產部署步驟。

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

HAL 連結 `href` 值的語法只是一個範例，實際值應隨時從 HAL 連結讀取而不是由產生取得。

向此端點提交一個 `PUT` 請求，若成功會導致 `201` 回應。該回應主體是新執行的表示方式。此功能類似於透過 API 啟動常規執行。

#### 識別重新執行的執行 {#identifying}

系統透過觸發欄位中的 `RE_EXECUTE` 值來識別重新執行的執行。