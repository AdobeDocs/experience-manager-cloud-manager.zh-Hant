---
title: 私人存放庫的 GitHub 檢查設定
description: 了解如何控制自動建立的管道以驗證對私人存放庫的每個提取請求。
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# 適用於私人存放庫的GitHub檢查設定 {#github-check-config}

了解如何控制自動建立的管道以驗證對私人存放庫的每個提取請求。

## GitHub檢查設定 {#configuration}

使用[私人存放庫](private-repositories.md#using)時，會自動建立[完整棧疊計畫碼品質管道](/help/overview/ci-cd-pipelines.md)。 此管道在每次提取要求更新時啟動。

您可以透過建立一個 `.cloudmanager/pr_pipelines.yml` 檔案 (位於私有存放庫的預設分支中) 來控制這些檢查。

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| 參數 | 可能的值 | 預設 | 說明 |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` 或 `false` | `false` | 是隻保留此GitHub提取請求上程式碼掃描結果的最後一個註解，還是保留全部。 |
| `type` | `CI_CD` | N/A | 定義CI/CD管道的行為。 |
| `template.programID` | 整數 | 沒有重複使用管道變數 | 您可以重複使用在每個PR自動建立的現有管道上設定的[管道變數](/help/getting-started/build-environment.md#pipeline-variables)。 |
| `template.pipelineID` | 整數 | 沒有重複使用管道變數 | 您可以重複使用在每個PR自動建立的現有管道上設定的[管道變數](/help/getting-started/build-environment.md#pipeline-variables)。 |
| `namePrefix` | 字串 | `Full Stack Code Quality Pipeline for PR` | 用於設定自動建立的管道名稱。 |
| `importantMetricsFailureBehavior` | `CONTINUE` 或 `FAIL` 或 `PAUSE` | `CONTINUE` | 設定管道的重要量度行為<br>`CONTINUE` =如果重要量度失敗，則管道會自動前進<br>`FAIL` =如果重要量度失敗，則管道會以「失敗」狀態結束<br>`PAUSE` =當重要量度失敗時，程式碼掃描步驟會收到「等待」狀態，且必須手動繼續。 |
