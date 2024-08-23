---
title: Git 和 Adobe Cloud Manager 整合
description: 本影片系列會逐步引導您設定客戶管理的（內部部署） Git存放庫並與AdobeCloud Manager整合。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 17%

---


# Git與Adobe Cloud Manager整合

Adobe Cloud Manager布建了一個Git存放庫，用於使用Cloud Manager的CI/CD管道部署計畫碼。 您可以直接使用Cloud Manager的Git存放庫，也可以選擇將內部部署或客戶管理的Git存放庫與Cloud Manager整合。

## Git整合總覽

>[!VIDEO](https://video.tv.adobe.com/v/28710/) （3分鐘、11秒）

本影片系列會介紹幾個整合客戶管理的Git存放庫與Cloud Manager的使用案例。

* [初始同步](#initial-sync)
* [基本分支原則](#branching-strategy)
* [功能分支開發](#feature-development)
* [生產部署](#production-deployment)
* [同步版本標記](#sync-tags)

本影片系列會假定您具備Git和原始檔控制管理的基本知識。 如需有關Git的更多詳細資訊，請參閱下列[其他資源](#additional-resources)。

本影片系列中概述的步驟和命名慣例代表使用客戶管理的Git存放庫和Cloud Manager的一些最佳做法。 預計所描述的慣例和工作流程將適用於個別開發團隊。

有關 Cloud Manager 的完整概觀，請參閱 [Cloud Manager 簡介](/help/introduction.md)。

## 初始同步 {#initial-sync}

將客戶管理的Git存放庫和Cloud Manager的Git存放庫同步處理的第一步。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12) （8分鐘）

## 基本分支策略 {#branching-strategy}

設定基本分支策略以利用Cloud Manager的[生產](/help/using/production-pipelines.md)和[非生產管道](/help/using/non-production-pipelines.md)。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12) （3分鐘，48秒）

## 功能分支開發 {#feature-development}

使用功能分支隔離客戶管理的Git存放庫中的計畫碼變更並與Cloud Manager的Git存放庫同步，以使用非生產管道進行計畫碼品質和驗證測試。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12) （9分鐘）

## 生產部署 {#production-deployment}

在客戶管理的Git存放庫中為生產版本準備程式碼，並與Cloud Manager的Git存放庫同步，以部署到中繼和生產環境。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12) （6分鐘6秒）

## 同步版本標籤 {#sync-tags}

您可以將Cloud Manager Git存放庫中的版本標籤同步到客戶管理的Git存放庫中。 此功能可讓您檢視哪些程式碼已部署到中繼和生產環境。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12) （2分鐘、57秒）

## 其他資源 {#additional-resources}

* [Cloud Manager 簡介](/help/introduction.md)
* [GitHub 資源](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Atlassian Git 教學課程](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 速查表](https://education.github.com/git-cheat-sheet-education.pdf)
