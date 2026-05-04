---
title: CI/CD 管道
description: 了解 CI/CD 管道以及這些管道如何在 Cloud Manager 中處理至中繼和生產環境的部署。
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754bid: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2: id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 639
ht-degree: 81%

---

# CI/CD 管道 {#ci-cd-pipeline}

了解 CI/CD 管道以及這些管道如何在 Cloud Manager 中處理至中繼和生產環境的部署。

## 概觀 {#overview}

[!UICONTROL Cloud Manager] 包括持續整合/持續傳遞 (CI/CD) 架構，此架構讓實作團隊可快速測試並傳遞新的或更新的程式碼。 實施團隊可以設定、配置和開始自動化 CI/CD 管道。 該管道執行全面的程式碼掃描時遵循 Adobe 程式碼編寫最佳實務，並確保最高的程式碼品質。

CI/CD 管道還會自動化單位和效能測試流程，以提高部署效率並主動識別部署後修復成本高昂的嚴重問題。 如果將程式碼部署到生產環境，實作團隊即可存取完整的程式碼效能報告，以了解對 KPI 和關鍵安全驗證的潛在影響。

## 關於管道流程 {#pipeline-process}

以下圖表說明當使用管道在 [!UICONTROL Cloud Manager] 中觸發某個版本時會發生什麼情況。

![管道流程](/help/assets/screen_shot_2018-05-30at82457pm.png)

| 管道步驟 | 說明 |
| --- | --- |
| &#x200B;1. 開始發行 | 部署管理員觸發版本的方式包括手動、使用 Git 認可，或按照定期排程。 |
| &#x200B;2. 建立版本標籤 | [!UICONTROL Cloud Manager] 會建立 Git 標記，以使用自動產生的版本編號 (例如 `2018.531.245527.0000001222`) 來標示版本。 |
| &#x200B;3. 使用自動產生的版本建置為版本 | [!UICONTROL Cloud Manager] 會使用新指派的版本編號建置應用程式。 |
| &#x200B;4. 評估程式碼品質 | [!UICONTROL Cloud Manager] 會掃描原始程式碼並提供摘要，然後再將程式碼部署到中繼環境。 |
| &#x200B;5. 已建立版本的成品已儲存 | 儲存發佈內容成品以供稍後在部署步驟中使用。 |
| &#x200B;6. 自動將成品部署至AMS AEM中繼環境 | 將發行成品部署至中繼環境。 |
| &#x200B;7. 觸發自動化測試 | [!UICONTROL Cloud Manager] 會在成品上執行效能和安全測試。 |
| &#x200B;8. 生產觸發部署 | 完成自動化測試後，[!UICONTROL Cloud Manager] 會展開對生產環境的部署。 |
| &#x200B;9. [!UICONTROL Cloud Manager]取得要部署的成品 | [!UICONTROL Cloud Manager] 提取已儲存的發行成品。 |
| &#x200B;10. 將成品部署至生產環境 | 將發佈內容成品部署至生產環境。 |

### 使用Smart Build更快建置 {#use=smart-build}

Cloud Manager現在使用名為&#x200B;**Smart Build**&#x200B;的最佳化建置策略，該策略使用模組層級的快取來加速建置流程。 在每次建置期間，只會重建已變更的模組，而未變更的模組則會從快取中重複使用。

智慧型組建僅適用於計畫碼品質和開發完整棧疊部署管道。

請參閱[新增非生產管道](/help/using/non-production-pipelines.md#add-non-production-pipeline)和[關於在非生產管道中使用Smart Build](/help/using/non-production-pipelines.md#about-smart-build)。


### 如何設定 CI/CD 管道 {#how-to-setup-a-ci-cd-pipeline}

若要了解更多有關管道設定的詳細資訊，請參閱文件「[設定生產管道](/help/using/production-pipelines.md)」和「[設定非生產管道](/help/using/non-production-pipelines.md)」。

## 品質閘道 {#quality-gates}

CI/CD 管道會提供品質閘道或驗收標準，在將程式碼從中繼環境移動到部署環境之前必須滿足這些要求。 在管道內有三個閘道：

* 程式碼品質
* 效能測試
* 安全測試

對於這些閘道中的每一個，可識別三個層級的問題：

* **嚴重** - 閘道識別出的嚴重問題，並會導致管道立即失敗。
* **重要** - 閘道識別出的重要問題，並會導致管道進入暫停狀態。 部署管理員、專案管理員或企業所有者可以覆寫此問題，讓管道繼續作業。 或者，他們可以接受這些問題，導致管道因失敗而停止。
* **資訊** - 由閘道指出的資訊問題僅供參考，對管道執行沒有影響。

以下為發現有問題的程式碼掃描範例。

![程式碼掃描範例](/help/assets/quality-gate-failed.png)

### 如何設定閘道 {#how-to-setup-gates}

如需設定程式碼、品質和效能閘道的詳細資訊，請參閱文件「[設定生產管道](/help/using/production-pipelines.md)」。
