---
title: Git 和 Adobe Cloud Manager 整合
description: 本影片系列會逐步介紹客戶管理的 (內部部署) Git 存放庫與 Adobe Cloud Manager 的設定和整合。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
TQID: https://experienceleague.adobe.com/fyGrLuc1bIBY9ZAgYiULxxJQy-ZZBLYtAAdYgqzSLAM
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2011f63c513689f571d21772752348388c2f342a
workflow-type: tm+mt
source-wordcount: 356
ht-degree: 76%

---

# Git 和 Adobe Cloud Manager 整合

Adobe Cloud Manager 隨附已佈建好的一個 Git 存放庫，方便使用 Cloud Manager 的 CI/CD 管道部署程式碼。 您可以依提供方式使用Cloud Manager的Git存放庫，或選擇將內部部署或客戶管理的Git存放庫與Cloud Manager整合。

## Git 整合概觀

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

本影片系列會介紹幾個有關客戶管理的 Git 存放庫與 Adobe Cloud Manager 整合的使用案例。

* [初始同步](#initial-sync)
* [基本分支策略](#branching-strategy)
* [功能分支開發](#feature-development)
* [生產部署](#production-deployment)
* [同步版本標記](#sync-tags)

此影片系列需要具備Git和原始檔控制管理的基本知識。 如需 Git 的更多詳細資訊，請參閱[下列附加資源](#additional-resources)。

本影片系列中概述的步驟和命名慣例代表使用客戶管理的 Git 存放庫和 Cloud Manager 的一些最佳實務。 所描述的慣例和工作流程適用於個別開發團隊。

有關 Cloud Manager 的完整概觀，請參閱 [Cloud Manager 簡介](/help/introduction.md)。

## 初始同步 {#initial-sync}

將客戶管理的 Git 存放庫和 Cloud Manager 的 Git 存放庫同步處理的第一步。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 基本分支策略 {#branching-strategy}

設定基本分支策略以使用Cloud Manager的[生產](/help/using/production-pipelines.md)和[非生產管道](/help/using/non-production-pipelines.md)。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 功能分支開發 {#feature-development}

使用功能分支隔離客戶管理的 Git 存放庫中的程式碼變更並和 Cloud Manager 的 Git 存放庫同步，以便使用非生產管道進行程式碼品質和驗證測試。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 生產部署 {#production-deployment}

在客戶管理的 Git 存放庫中準備生產版本的程式碼，並與 Cloud Manager 的 Git 存放庫同步，以便部署至中繼和生產環境。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## 同步版本標記 {#sync-tags}

您可以將版本標記從 Cloud Manager Git 存放庫同步到客戶管理的 Git 存放庫。 您可以透過此功能了解哪些程式碼已部署到中繼和生產環境。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## 其他資源 {#additional-resources}

* [Cloud Manager 簡介](/help/introduction.md)
* [GitHub資源](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Atlassian Git教學課程](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git速查表](https://education.github.com/git-cheat-sheet-education.pdf)
