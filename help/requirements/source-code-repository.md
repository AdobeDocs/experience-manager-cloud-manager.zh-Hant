---
title: 原始程式碼存放庫
description: 了解為您在 Cloud Manager 中擁有的每個方案佈建的 Git 存放庫。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 32%

---


# Source程式碼存放庫 {#source-code-repository}

了解為您在 Cloud Manager 中擁有的每個方案佈建的 Git 存放庫。

## Cloud Manager存放庫 {#cloud-manager-repository}

您的 [!UICONTROL AEM Managed Services] 訂閱包括由 Adobe 佈建和管理的原始程式碼存放庫。每個方案都分配有一個唯一的Git存放庫，您可在此處儲存和保護相關程式碼。

您應一律使用Cloud Manager的Git存放庫，該存放庫會是空白的，沒有設定任何分支或範例專案。 Cloud Manager為其Git存放庫提供私人存取權杖，讓您使用任何Git使用者端來建立分支、管理程式碼、擷取認可歷史記錄等。

如需有關如何在Git中設定分支的詳細資訊，請參閱[設定版本分支](/help/getting-started/configuring-branches.md)。

如需有關如何將 Cloud Manager 的 Git 存放庫和 CI/CD 管道一起使用的詳細資訊，請參閱[設定生產管道](/help/using/production-pipelines.md)和[設定非生產管道](/help/using/non-production-pipelines.md)，了解更多詳細資訊。

## 內部部署存放庫 {#on-premise-repository}

您可能有一個現有的Git存放庫並希望繼續使用它，在這種情況下，您可以將Git的功能用於多個遠端存放庫。 日常開發將繼續在您的Git存放庫中進行。 當版本分支準備好要部署到生產環境時，您可以將最新的程式碼推送到Cloud Manager的Git存放庫並觸發Cloud Manager CI/CD管道。

若要檢視常用的Git命令，請參閱[Git速查表](https://education.github.com/git-cheat-sheet-education.pdf)。
