---
title: 原始程式碼存放庫
description: 瞭解為您在Cloud Manager中擁有的每個方案布建的Git存放庫。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 75%

---


# 原始程式碼存放庫 {#source-code-repository}

瞭解為您在Cloud Manager中擁有的每個方案布建的Git存放庫。

## Cloud Manager 存放庫 {#cloud-manager-repository}

您的 [!UICONTROL AEM Managed Services] 訂閱包括由 Adobe 佈建和管理的原始程式碼存放庫。每個方案都分配到一個唯一的 Git 存放庫，可以把相關的程式碼安全地儲存在這裡。

依照最佳實務的要求，您應始終使用 Cloud Manager 的 Git 存放庫，該存放庫一開始是空白的，沒有設定任何分支或範例專案。Cloud Manager 為其 Git 存放庫提供私人的存取權杖，讓您可以透過任何 Git 用戶端來建立分支、管理程式碼、擷取認可歷史記錄等。

如需有關如何在 Git 中設定分支的詳細資訊，請參閱「[設定版本分支](/help/getting-started/configuring-branches.md)」。

如需有關如何將Cloud Manager的Git存放庫與CI/CD管道搭配使用的詳細資訊，請參閱[設定生產管道](/help/using/production-pipelines.md)和[設定非生產管道](/help/using/non-production-pipelines.md)以瞭解更多資訊。

## 內部部署存放庫 {#on-premise-repository}

您可能有一個現有的 Git 存放庫並希望繼續使用它，在這個情況下，您可以使用 Git 的功能建立多個遠端存放庫。日常開發會繼續在您的 Git 存放庫中進行。當版本分支已準備好可以部署到生產環境時，您可以將最新的程式碼推送到 Cloud Manager 的 Git 存放庫並觸發 Cloud Manager CI/CD 管道。

若要檢視常用的 Git 命令，請參閱「[Git 速查表](https://education.github.com/git-cheat-sheet-education.pdf)」。
