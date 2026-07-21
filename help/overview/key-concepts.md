---
title: 重要概念
description: 像所有強大的工具一樣，Cloud Manager 包含了許多概念和術語。 本文件會概述您開始使用 Cloud Manager 時最重要的一些內容。
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
TQID: https://experienceleague.adobe.com/usnXqDujeZ04U5hOtiI76aemlj-ceToAOtAYS9U0UuM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 628eceafe63153d64151937df85937135bdc8e7b
workflow-type: tm+mt
source-wordcount: 421
ht-degree: 60%

---

# 重要概念 {#key-concepts}

Cloud Manager包含許多概念和術語。 本文會概述您開始使用Cloud Manager時最重要的一些概念。

## 應用程式 {#application}

應用程式是由客戶建立的一組自訂項目和設定，根據其特定使用案例和需求來調整基礎的[解決方案](#solution) (例如 AEM Sites 或 AEM Assets)。 應用程式是包含多個[成品](#artifact)的邏輯單位。

一個應用程式範例是虛構的 [WKND 生活方式應用程式。](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview)

## 成品 {#artifact}

成品是可部署的單位，而且是將原始程式碼轉換為單一單位的建置流程的結果。 例如，.zip 檔案就包含了原始程式碼。

## 成品存放庫 {#artifact-repository}

成品存放庫是儲存和保護客戶特定[成品](#artifact)的儲存位置。

## 環境 {#environment}

環境指[方案](#program)中的單一叢集虛擬機器。 對於 AEM，此環境由一個製作執行個體 (可選擇外加一個冷待命製作執行個體)、零個或多個發佈執行個體、一個或多個 Dispatcher 執行個體和一個負載平衡器組成。

## Git 存放庫 {#git-repository}

Git 存放庫是儲存客戶特定原始程式碼的位置，並可[使用 Git](https://git-scm.com) 存取。

## 執行個體 {#instance}

執行個體是一種特定的虛擬伺服器，會執行 AEM [解決方案](#solution)。 從部署的角度來看，執行個體代表單一邏輯單位。

## 組織 {#organization}

組織指代表企業客戶的 Adobe&#x200B; 建構。 視在Adobe的Identity Management系統(IMS)中的布建方式而定，公司可以有多個組織。

## 管道 {#pipeline}

管道是一組按順序執行的部署步驟。

## 產品 {#product}

產品指獲組織授權的[解決方案](#solution)中的一組特定功能。 組織內的不同[方案](#program)有權使用不同的產品集，例如AEM Sites、AEM Assets或AEM Forms。

## 方案 {#program}

方案指一組支援客戶方案邏輯分組的環境，通常會對應到已購買的service level agreement (SLA)。 每個計畫只會有一個生產環境和許多非生產環境。

## 解決方案 {#solution}

解決方案指 Adobe [!UICONTROL Experience Cloud] 解決方案的其中一種。 例如，Adobe Experience Manager、Adobe Target 或 Adobe Analytics。

## 步驟 {#step}

步驟是已設定的指令集，會完成作為[管道](#pipeline)元件的某些工作單位。
