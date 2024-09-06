---
title: CI/CD 管道
description: 了解 CI/CD 管道以及這些管道如何在 Cloud Manager 中處理至中繼和生產環境的部署。
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '562'
ht-degree: 100%

---


# CI/CD 管道 {#ci-cd-pipeline}

了解 CI/CD 管道以及這些管道如何在 Cloud Manager 中處理至中繼和生產環境的部署。

## 概觀 {#overview}

[!UICONTROL Cloud Manager] 包括持續整合/持續傳遞 (CI/CD) 架構，此架構讓實作團隊可快速測試並傳遞新的或更新的程式碼。實施團隊可以設定、配置和開始自動化 CI/CD 管道。該管道執行全面的程式碼掃描時遵循 Adobe 程式碼編寫最佳實務，並確保最高的程式碼品質。

CI/CD 管道還會自動化單位和效能測試流程，以提高部署效率並主動識別部署後修復成本高昂的嚴重問題。如果將程式碼部署到生產環境，實作團隊即可存取完整的程式碼效能報告，以了解對 KPI 和關鍵安全驗證的潛在影響。

## 關於管道流程 {#pipeline-process}

以下圖表說明當使用管道在 [!UICONTROL Cloud Manager] 中觸發某個版本時會發生什麼情況。

![管道流程](/help/assets/screen_shot_2018-05-30at82457pm.png)

| 管道步驟 | 說明 |
| --- | --- |
| 1. 啟動版本 | 部署管理員觸發版本的方式包括手動、使用 Git 認可，或按照定期排程。 |
| 2. 建立版本標記 | [!UICONTROL Cloud Manager] 會建立 Git 標記，以使用自動產生的版本編號 (例如 `2018.531.245527.0000001222`) 來標示版本。 |
| 3. 使用自動產生的版本編號建置版本 | [!UICONTROL Cloud Manager] 會使用新指派的版本編號建置應用程式。 |
| 4. 評估程式碼品質 | [!UICONTROL Cloud Manager] 會掃描原始程式碼並提供摘要，然後再將程式碼部署到中繼環境。 |
| 5. 已建立版本的成品已儲存 | 儲存發佈內容成品以供稍後在部署步驟中使用。 |
| 6. 將成品自動部署至 AMS 的 AEM 中繼環境 | 將發行成品部署至中繼環境。 |
| 7. 觸發自動化測試 | [!UICONTROL Cloud Manager] 會在成品上執行效能和安全測試。 |
| 8. 生產觸發部署 | 完成自動化測試後，[!UICONTROL Cloud Manager] 會展開對生產環境的部署。 |
| 9. [!UICONTROL Cloud Manager] 取得要部署的成品 | [!UICONTROL Cloud Manager] 提取已儲存的發行成品。 |
| 10. 將成品部署至生產環境 | 將發佈內容成品部署至生產環境。 |

### 如何設定 CI/CD 管道 {#how-to-setup-a-ci-cd-pipeline}

若要了解更多有關管道設定的詳細資訊，請參閱文件「[設定生產管道](/help/using/production-pipelines.md)」和「[設定非生產管道](/help/using/non-production-pipelines.md)」。

## 品質閘道 {#quality-gates}

CI/CD 管道會提供品質閘道或驗收標準，在將程式碼從中繼環境移動到部署環境之前必須滿足這些要求。在管道內有三個閘道：

* 程式碼品質
* 效能測試
* 安全測試

對於這些閘道中的每一個，可識別三個層級的問題：

* **嚴重** - 閘道識別出的嚴重問題，並會導致管道立即失敗。
* **重要** - 閘道識別出的重要問題，並會導致管道進入暫停狀態。部署管理員、專案管理員或企業所有者可以覆寫此問題，讓管道繼續作業。或者，他們可以接受這些問題，導致管道因失敗而停止。
* **資訊** - 由閘道指出的資訊問題僅供參考，對管道執行沒有影響。

以下為發現有問題的程式碼掃描範例。

![程式碼掃描範例](/help/assets/quality-gate-failed.png)

### 如何設定閘道 {#how-to-setup-gates}

如需設定程式碼、品質和效能閘道的詳細資訊，請參閱文件「[設定生產管道](/help/using/production-pipelines.md)」。
