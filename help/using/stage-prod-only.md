---
title: 僅限中繼和僅限生產管道
description: 了解如何使用專用管道分割中繼和生產部署。
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: c238caa22fdd71ae6aefd098331b626b9b951a0f
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 100%

---

# 僅限中繼和僅限生產管道 {#stage-prod-only}

了解如何使用專用管道分割中繼和生產部署。

>[!NOTE]
>
>此功能僅適用於[早期採用者方案。](/help/release-notes/current.md#early-adoption)

## 概觀 {#overview}

中繼環境和生產環境緊密耦合。依預設，其部署連結到單一管道。這是部署到該方案中的中繼環境和生產環境的部署管道。雖然這種耦合通常是合適的，但對某些使用案例會有缺點：

* 如果您想要部署到僅限中繼環境，則只能透過拒絕管道中的&#x200B;**提升至生產環境**&#x200B;步驟來實現。但是，執行將被標記為已取消。
* 如果您想要將中繼環境中的最新程式碼部署到生產環境中，則需要重新部署整個管道，包括中繼管道，即使其中的程式碼未變更。
* 由於部署期間無法更新環境，因此如果您想在提升至生產環境之前，在中繼環境中暫停並測試多天，即無法更新生產環境。這使得無相依性的工作 (例如更新[環境變數](/help/getting-started/build-environment.md#environment-variables)) 變得不可能。

僅限中繼和僅限生產管道透過提供專用部署選項為這些使用案例提供解決方案。

* **僅限中繼部署管道**&#x200B;僅部署到中繼環境，在部署和測試完成後，執行即完成。
   * 僅限中繼管道的行為與標準耦合全端生產管道相同，但沒有生產部署步驟 (核准、排程、部署)。
* **僅限生產部署管道**&#x200B;僅部署到生產環境，並可選取在中繼環境已成功完成和經驗證的執行，並將其成品部署到生產環境。
   * 僅限生產管道將重複使用中繼部署中的成品，跳過建置階段。

當全端生產管道執行時，僅限中繼管道和僅限生產管道不會執行，反之亦然。如果僅限階段和全端生產管道都設定了「**進行 Git 變更**」觸發程序，並且指向相同的分支和存放庫，則只有僅限階段管道會自動啟動。僅限生產管道不會啟動「**進行 Git 變更**」，因為這些管道沒有直接連結到存放庫。

這些專用管道提供更大的彈性，但請注意以下操作細節和建議。

>[!NOTE]
>
>僅限生產管道將始終使用僅限中繼管道中的成品，無論同時透過標準耦合生產管道在中繼環境部署了什麼。
>
>* 這可能會導致不必要的程式碼回復。
>* Adobe 建議在開始使用僅限生產和僅限中繼管道後，停止使用標準耦合生產管道。
>* 如果您仍然決定執行標準耦合管道和僅限中繼/僅限生產管道，請記住重複使用成品以避免程式碼回復。

## 管道建立 {#pipeline-creation}

僅限生產和僅限中繼管道的建立方式類似於標準耦合[生產管道](/help/using/production-pipelines.md)和[非生產管道](/help/using/non-production-pipelines.md)。請參閱這些文件以了解詳細資訊。

1. 在&#x200B;**管道**&#x200B;視窗中，點選或按一下&#x200B;**新增管道**。

   * 選取&#x200B;**新增非生產管道**&#x200B;以建立僅限中繼管道。
   * 選取&#x200B;**新增僅限生產管道**&#x200B;以建立僅限生產管道。

   ![建立僅限生產/中繼管道](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>如果對應的管道已存在，特定選項可能會呈現灰色。
>
>* 如果僅限中繼管道尚不存在，則&#x200B;**新增僅限生產管道**&#x200B;將無法使用。
>* 如果標準耦合管道已存在，則&#x200B;**新增生產管道**&#x200B;將無法使用。
>* 每個方案僅允許一個僅限生產管道和一個僅限中繼管道。

### 僅限中繼管道 {#stage-only}

1. 選取&#x200B;**新增非生產管道**&#x200B;選項後，**新增非生產管道**&#x200B;對話方塊將會開啟。
1. 若要建立僅限中繼管道，請在管道的&#x200B;**合格的部署環境**&#x200B;欄位中選取中繼環境。完成其餘欄位，然後點選或按一下&#x200B;**繼續**。

   ![建立僅限中繼管道](/help/assets/configure-pipelines/stage-only.png)

1. 在&#x200B;**中繼測試**&#x200B;標籤，您可以定義應該在中繼環境中執行的測試。點選或按一下&#x200B;**儲存**&#x200B;以儲存新管道。

   ![僅限中繼管道的測試參數](/help/assets/configure-pipelines/stage-only-test.png)

### 僅限生產管道 {#prod-only}

1. 選取&#x200B;**新增僅限生產管道**&#x200B;選項後，**新增僅限生產管道**&#x200B;對話方塊將會開啟。
1. 提供&#x200B;**管道名稱**。此對話方塊的其餘選項和功能與標準耦合管道建立對話方塊中的選項和功能相同。點選或按一下「**儲存**」，以儲存管道。

   ![建立僅限生產管道](/help/assets/configure-pipelines/prod-only-pipeline.png)

## 執行僅限生產和僅限中繼管道 {#running}

僅限生產和僅限中繼管道的執行方式相同於[所有其他管道的執行方式](/help/using/managing-pipelines.md#running-pipelines)。如需詳細資訊，請查看文件。

此外，僅限生產管道的執行可以直接從僅限中繼管道的執行詳細資訊觸發。

### 僅限中繼管道 {#stage-only-run}

僅限中繼管道的執行方式與標準耦合管道幾乎相同。然而，在執行結束時，在測試步驟之後，**提升組建版本**&#x200B;按鈕可讓您啟動僅限生產管道執行，該執行使用此執行部署在中繼環境中的成品，並將其部署到生產環境中。

![僅限中繼管道執行](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

只有當您處於最新成功的僅限中繼管道執行時，**提升組建版本**&#x200B;按鈕才會出現。點選或按一下後，它將要求您確認僅限生產管道的執行，或建立僅限生產管道 (如果尚未存在)。

### 僅限生產管道 {#prod-only-run}

對於僅限生產管道，識別要部署到生產環境的來源成品非常重要。這些詳細資訊可以在&#x200B;**成品準備**&#x200B;步驟中找到。您可以導覽到這些執行以獲取更多詳細資訊和記錄。

![成品詳細資訊](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
