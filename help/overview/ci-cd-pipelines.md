---
title: CI/CD 管道
description: 了解 CI/CD 管道以及這些管道如何在 Cloud Manager 中處理至中繼和生產環境的部署。
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 59%

---


# CI/CD管道 {#ci-cd-pipeline}

了解 CI/CD 管道以及這些管道如何在 Cloud Manager 中處理至中繼和生產環境的部署。

## 概觀 {#overview}

[!UICONTROL Cloud Manager]包含持續整合/持續傳遞(CI/CD)架構，此架構讓實作團隊可快速測試並傳遞新的或更新的程式碼。 實作團隊可以設定、設定和啟動自動化的CI/CD管道。 此管道遵循Adobe編碼最佳實務，以執行全面的程式碼掃描並確保最高的程式碼品質。

CI/CD 管道還會自動化單位和效能測試流程，以提高部署效率並主動識別部署後修復成本高昂的嚴重問題。如果將程式碼部署到生產環境，實作團隊即可存取完整的程式碼效能報告，以了解對 KPI 和關鍵安全驗證的潛在影響。

## 關於配管流程 {#pipeline-process}

下圖說明使用管道在[!UICONTROL Cloud Manager]中觸發發行時會發生什麼情況。

![管道流程](/help/assets/screen_shot_2018-05-30at82457pm.png)

| 管道步驟 | 說明 |
| --- | --- |
| 1. 啟動版本 | 部署管理員觸發版本的方式包括手動、使用Git認可，或根據定期排程。 |
| 2.建立版本標籤 | [!UICONTROL Cloud Manager]會建立Git標籤，以使用自動產生的版本編號（例如`2018.531.245527.0000001222`）來標示版次。 |
| 3. 使用自動產生的版本編號建置版次 | [!UICONTROL Cloud Manager]會以新指派的版本編號建置應用程式。 |
| 4. 評估程式碼品質 | [!UICONTROL Cloud Manager]會先掃描原始程式碼並提供摘要，然後才能將程式碼部署到中繼環境。 |
| 5.已建立版本的成品已儲存 | 儲存發行成品以供稍後在部署步驟中使用。 |
| 6.自動將成品部署至AMS AEM中繼環境 | 將發行成品部署至中繼環境。 |
| 7. 觸發自動化測試 | [!UICONTROL Cloud Manager] 會在成品上執行效能和安全測試。 |
| 8. 生產觸發部署 | 完成自動化測試後，[!UICONTROL Cloud Manager] 會展開對生產環境的部署。 |
| 9. [!UICONTROL Cloud Manager] 取得要部署的成品 | [!UICONTROL Cloud Manager] 提取已儲存的發行成品。 |
| 10.將成品部署至生產環境 | 將發行成品部署至生產環境。 |

### 如何設定CI/CD管道 {#how-to-setup-a-ci-cd-pipeline}

若要了解有關管道設定的詳細資訊，請參閱文件[設定生產管道](/help/using/production-pipelines.md)和[設定非生產管道](/help/using/non-production-pipelines.md)。

## 品質閘道 {#quality-gates}

CI/CD 管道會提供品質閘道或驗收標準，在將程式碼從中繼環境移動到部署環境之前必須滿足這些要求。在管道內有三個閘道：

* 程式碼品質
* 效能測試
* 安全測試

對於這些閘道中的每一個，可識別三個層級的問題：

* **嚴重** - 閘道識別出的嚴重問題，並會導致管道立即失敗。
* **重要** - 閘道識別出的重要問題，並會導致管道進入暫停狀態。部署管理員、專案管理員或企業所有者可以覆寫此問題，讓管道繼續。 或者，他們可以接受問題，導致管道因失敗而停止。
* **資訊** - 閘道識別出的資訊問題，且純粹是為了參考目的而提供，對管道執行沒有影響。

以下是識別出問題的程式碼掃描範例。

![程式碼掃描範例](/help/assets/quality-gate-failed.png)

### 如何設定閘道 {#how-to-setup-gates}

如需有關設定程式碼、品質和效能閘道的詳細資訊，請參閱文件：[設定生產管道](/help/using/production-pipelines.md)。
