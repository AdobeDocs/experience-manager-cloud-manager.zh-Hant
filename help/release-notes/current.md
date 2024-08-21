---
title: Cloud Manager 2024.8.0 版發行說明
description: 了解 Cloud Manager 2024.8.0 的發行說明。
feature: Release Information
source-git-commit: 5ced643fabe0a670e456cbea72f9da8196ac774a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 24%

---


# Cloud Manager 2024.8.0版發行說明 {#release-notes}

本頁記錄了 [!UICONTROL Cloud Manager] 2024.8.0 版的發行說明。

>[!NOTE]
>
>如需AEM as a Cloud Service中Cloud Manager的最新發行說明，請參閱AEM as a Cloud Service目前發行說明中的[Cloud Manager](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.8.0的發行日期為2024年8月14日。 下一個版本規劃於 2024 年 9 月 14 日發行。

## 新增功能 {#what-is-new}

* 對於階段專用和生產專用管道（可作為[早期採用者方案](#staging-production-only-pipelines)的一部分提供），您現在可以在[緊急模式，](/help/using/stage-prod-only.md#emergency-mode)略過階段測試中執行這些管道。

## 早期採用方案 {#early-adoption}

成為Cloud Manager早期採用計畫的一部分，並有機會測試一些即將推出的功能。

### 僅限中繼和僅限生產的管道 {#staging-production-only-pipelines}

Adobe很高興宣佈推出[僅限中繼及僅限生產管道](/help/using/stage-prod-only.md)的支援。 此新功能可讓您將完整棧疊生產部署管道劃分為更小、更專業的部署。

如果您想要測試此功能並提供意見回饋，請使用與您的Adobe ID相關聯的電子郵件地址來傳送電子郵件`Grp-cloudmanager_splitpipelines@adobe.com`。

## 錯誤修正

* 已修正在管道刪除後發現管道步驟仍在執行的罕見問題。
* 重新執行管道現在可在第一次嘗試時運作，以修正必須多次開始重新執行的罕見問題。
* 完整棧疊管道的已排程部署步驟現在遵循所選的已排程日期，並且不會恢復為&#x200B;**現在**。
* 失敗的複製內容任務狀態現在已正確反映，在極少數情況下不再錯誤地顯示`In Progress`狀態。

## 已知問題 {#known-issues}

{{content-copy-known-issues}}
