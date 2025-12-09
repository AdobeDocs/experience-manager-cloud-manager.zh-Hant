---
title: GitHub 檢查附註
description: 了解 GitHub 檢查如何為您的私人存放庫加上 PR 附註，以便為您提供有用的意見回饋。
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 75baacd1fd6f36ca1d6ea5c1993516569ab6ef47
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 92%

---


# GitHub 檢查附註 {#github-annotations}

了解 GitHub 檢查如何為您的私人存放庫加上 PR 附註，以便為您提供有用的意見回饋。

## 概觀 {#overview}

如果您的Cloud Manager程式使用[私人存放庫](private-repositories.md)，請為每個提取請求自動簽入GitHub。 這些檢查會附註實用資訊，以協助您盡快了解程式碼的任何問題。

![GitHub 檢查附註範例](assets/github-check-annotations.png)

[SonarQube](/help/using/custom-code-quality-rules.md) 檢測到的[程式碼品質](/help/using/code-quality-testing.md)問題會清楚列出。

![程式碼問題附註範例](assets/github-check-annotations-example.png)

系統會提供出現問題的確切程式碼，您可以按一下以顯示相關程式碼。這些附註是提供給所有程式碼問題，而不只是在提取請求中變更的問題。

![程式碼問題附註範例](assets/github-check-annotations-example-code.png)

所有附註行都彙總在 GitHub 拉取請求的「**已更改檔案**」索引標籤上。提取請求中未更改的檔案附註會顯示在檔案所屬的部分中。

![已更改檔案索引標籤上的附註範例](assets/github-check-annotations-files-changed.png)

## 程式碼品質管道 {#code-quality-pipelines}

[程式碼品質](/help/using/code-quality-testing.md)結果也會顯示在管道中；此管道會在「**檢查**」索引標籤底部由 Cloud Manager 自動觸發。這也可以從提取請求的檢查「**詳情**」中存取。

![附註範例](assets/github-check-annotations-code-quality.png)

![附註範例](assets/github-check-annotations-code-quality-2.png)

您也可以在 CSV 表單中以視覺化呈現問題。這方法可以透過[查看 Cloud Manager 中的管道執行詳細資訊](/help/using/managing-pipelines.md)來擷取。
