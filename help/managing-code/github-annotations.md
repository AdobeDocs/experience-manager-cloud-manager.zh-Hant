---
title: GitHub 檢查附註
description: 了解 GitHub 檢查如何為您的私人存放庫加上 PR 附註，以便為您提供有用的意見回饋。
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 147eec6368875aabb252d759909c0309a82ef3db
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 32%

---


# GitHub 檢查附註 {#github-annotations}

瞭解GitHub如何檢查私人存放庫的註釋PR，以提供意見回饋。

## 概觀 {#overview}

如果您的Cloud Manager程式使用[私人存放庫](private-repositories.md)，請為每個提取請求自動簽入GitHub。 這些檢查帶有資訊的註釋，可幫助您儘快識別計畫碼的任何問題。

![GitHub 檢查附註範例](assets/github-check-annotations.png)

[SonarQube](/help/using/custom-code-quality-rules.md) 檢測到的[程式碼品質](/help/using/code-quality-testing.md)問題會清楚列出。

![程式碼問題附註範例](assets/github-check-annotations-example.png)

已提供問題的確切程式碼行，您可以選取它以檢視相關程式碼。 這些註解適用於所有程式碼問題，而不僅僅是提取請求中的問題。

![程式碼問題附註範例](assets/github-check-annotations-example-code.png)

所有附註行都彙總在 GitHub 拉取請求的「**已更改檔案**」索引標籤上。 提取請求中未變更之檔案的註解會出現在另一個區段中。

![已更改檔案索引標籤上的附註範例](assets/github-check-annotations-files-changed.png)

## 程式碼品質管道 {#code-quality-pipelines}

[程式碼品質](/help/using/code-quality-testing.md)結果也會顯示在&#x200B;**檢查**&#x200B;索引標籤底部的Cloud Manager自動觸發的管道中。 您也可以從提取要求檢查的&#x200B;**詳細資料**&#x200B;存取它。

![附註範例](assets/github-check-annotations-code-quality.png)

![附註範例](assets/github-check-annotations-code-quality-2.png)

您也可以以CSV檔案的形式檢視問題。 您可以透過[檢視Cloud Manager](/help/using/managing-pipelines.md)中管道執行的詳細資訊來存取此資訊。
