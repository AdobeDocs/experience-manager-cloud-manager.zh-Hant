---
title: 私人存放庫的 GitHub 檢查設定
description: 了解如何控制自動建立的管道以驗證對私人存放庫的每個提取請求。
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---

# 私人存放庫的 GitHub 檢查設定 {#github-check-config}

了解如何控制自動建立的管道以驗證對私人存放庫的每個提取請求。

## GitHub 檢查的設定 {#configuration}

使用[私人存放庫時](private-repositories.md#using)，其會自動建立[全端程式碼品質管道](/help/overview/ci-cd-pipelines.md)。此管道在每次提取要求更新時啟動。

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
| `shouldDeletePreviousComment` | `true` 或 `false` | `false` | 是否僅保留此 GitHub 提取請求上程式碼掃描結果的最後一則註解或保留全部。 |
| `type` | `CI_CD` | N/A | 定義 CI/CD 管道的行為。 |
| `template.programID` | 整數 | 沒有重複使用管道變數 | 您可以重複使用每個 PR 自動建立的現有管道上所設定的[管道變數](/help/getting-started/build-environment.md#pipeline-variables)。 |
| `template.pipelineID` | 整數 | 沒有重複使用管道變數 | 您可以重複使用每個 PR 自動建立的現有管道上所設定的[管道變數](/help/getting-started/build-environment.md#pipeline-variables)。 |
| `namePrefix` | 字串 | `Full Stack Code Quality Pipeline for PR` | 用來設定自動建立的管道之名稱。 |
| `importantMetricsFailureBehavior` | `CONTINUE` 或 `FAIL` 或 `PAUSE` | `CONTINUE` | 設定管道的重要量度行為<br>`CONTINUE` = 如果某個重要量度失敗，管道會自動向前移動<br>`FAIL` = 如果重要量度失敗，管道將以「FAILED」狀態結束<br>`PAUSE` = 當重要量度失敗且必須手動恢復時，程式碼掃描步驟將收到「WAITING」狀態。 |
