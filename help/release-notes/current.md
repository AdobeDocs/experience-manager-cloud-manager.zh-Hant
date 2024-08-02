---
title: 2024.7.0 版發行說明
description: 以下是 Cloud Manager 2024.7.0 版的發行說明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 87c603a89b99f6984828280cba2041da8c72e839
workflow-type: ht
source-wordcount: '238'
ht-degree: 100%

---


# Cloud Manager 2024.7.0 版的發行說明 {#release-notes}

本頁記錄 [!UICONTROL Cloud Manager] 2024.7.0 版的發行說明。

>[!NOTE]
>
>如需 AEM as a Cloud Service 中 Cloud Manager 的最新發行說明，請參閱 [AEM as a Cloud Service 中 Cloud Manager 的最新發行說明。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0 版的發行日期為 2024 年 7 月 18 日。下一版本計畫於 2024 年 8 月 8 日發行。

## 新增功能 {#what-is-new}

* [生產管道](/help/using/production-pipelines.md#adding-production-pipeline)和[非生產管道](/help/using/non-production-pipelines.md#adding-non-production-pipeline)觸發器「**在 Git 變更**」現在可用於[私人存放庫](/help/managing-code/private-repositories.md)，在提交時啟動管道。
* 預生產管道只能手動觸發，不能設定為&#x200B;**在 Git 變更**。
* 對於僅限生產管道，可提升執行清單包括那些成品版本高於部署在生產環境之成品版本的執行。
* [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 已更新至 [49 版](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)。


## 早期採用計劃 {#early-adoption}

參加我們的早期採用計劃，即有機會測試一些即將推出的功能。

### 僅限中繼和僅限生產管道 {#staging-production-only-pipelines}

已引進[僅限中繼和僅限生產管道](/help/using/stage-prod-only.md)的支援，讓您將全端生產部署管道分割為更小的專門部署。

如果您有興趣測試此新功能並分享您的意見反饋，請使用和您的 Adobe ID 相關聯的電子郵件傳送一封電子郵件至 `Grp-cloudmanager_splitpipelines@adobe.com`。
