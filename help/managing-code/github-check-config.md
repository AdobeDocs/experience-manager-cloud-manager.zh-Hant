---
title: 私人存放庫的 GitHub 檢查設定
description: 了解如何控制自動建立的管道以驗證對私人存放庫的每個提取請求。
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: ht
source-wordcount: '255'
ht-degree: 100%

---

# 私人存放庫的 GitHub 檢查設定 {#github-check-config}

了解如何控制自動建立的管道以驗證對私人存放庫的每個提取請求。

## GitHub 檢查配定 {#configuration}

使用[私人存放庫時，將自動建立](private-repositories.md#using)[全端程式碼品質管道](/help/overview/ci-cd-pipelines.md)。此管道在每次提取要求更新時啟動。

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
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` 或 `false` | `false` | 是否僅保留此 GitHub 提取請求上程式碼掃描結果的最後一則評論或保留全部 |
| `type` | `CI_CD` | N/A | 定義 CI/CD 管道的行為 |
| `template.programID` | 整數 | 沒有重複使用管道變數 | 可用來重複使用[管道變數](/help/getting-started/build-environment.md#pipeline-variables)；這些變數是設定在由每個 PR 自動建立的現有一個管道上。 |
| `template.pipelineID` | 整數 | 沒有重複使用管道變數 | 可用來重複使用[管道變數](/help/getting-started/build-environment.md#pipeline-variables)；這些變數是設定在由每個 PR 自動建立的現有一個管道上。 |
| `namePrefix` | 字串 | `Full Stack Code Quality Pipeline for PR` | 用來設定自動建立的管道名稱 |
| `importantMetricsFailureBehavior` | `CONTINUE` 或 `FAIL` 或 `PAUSE` | `CONTINUE` | 設定管道的重要指標行為<br>`CONTINUE` = 如果某個重要指標失敗，管道就會自動向前移動<br>`FAIL` = 如果重要指標失敗，管道將以「失敗」狀態結束<br>`PAUSE` = 當重要指標失敗且必須手動恢復時，程式碼掃描步驟將收到「等待」狀態 |
