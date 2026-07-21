---
title: 原始程式碼存放庫
description: 了解針對您在 Cloud Manager 中擁有的每個方案所佈建的 Git 存放庫。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# 原始程式碼存放庫 {#source-code-repository}

了解針對您在 Cloud Manager 中擁有的每個方案所佈建的 Git 存放庫。

## Cloud Manager 存放庫 {#cloud-manager-repository}

您的 [!UICONTROL AEM Managed Services] 訂閱包括由 Adobe 佈建和管理的原始程式碼存放庫。 每個方案都分配有一個唯一的Git存放庫，您可在此儲存和保護您的相關程式碼。

依據最佳做法的要求，請一律使用Cloud Manager Git存放庫，該存放庫會是空的，沒有設定任何分支或範例專案。 Cloud Manager 為其 Git 存放庫提供私人的存取權杖，讓您可以透過任何 Git 用戶端來建立分支、管理程式碼、擷取認可歷史記錄等。

如需有關如何在 Git 中設定分支的詳細資訊，請參閱「[設定版本分支](/help/getting-started/configuring-branches.md)」。

若要進一步瞭解如何將Cloud Manager Git存放庫與CI/CD管道搭配使用，請參閱[設定生產管道](/help/using/production-pipelines.md)和[設定非生產管道](/help/using/non-production-pipelines.md)。

## 內部部署存放庫 {#on-premise-repository}

如果您有現有的Git存放庫並希望繼續使用它，請將Git的功能用於多個遠端存放庫。 開發會在您的Git存放庫中繼續。 當版本分支準備好要部署到生產環境時，您可以將最新的程式碼推送到Cloud Manager Git存放庫並觸發Cloud Manager CI/CD管道。

若要檢視常用的Git命令，請參閱[Git參考指南](https://education.github.com/git-cheat-sheet-education.pdf)。
