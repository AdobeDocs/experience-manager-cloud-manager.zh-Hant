---
title: 2024.7.0 版發行說明
description: 瞭解Cloud Manager 2024.7.0的發行說明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Cloud Manager 2024.7.0版發行說明 {#release-notes}

本頁會記錄[!UICONTROL Cloud Manager] 2024.7.0的發行說明。

>[!NOTE]
>
>如需AEM as a Cloud Service中Cloud Manager的最新發行說明，請參閱AEM as a Cloud Service目前發行說明中的[Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0的發行日期為2024年7月18日。 下一版本計畫於2024年8月13日發行。

## 新增功能 {#what-is-new}

* [生產管道](/help/using/production-pipelines.md#adding-production-pipeline)和[非生產管道](/help/using/non-production-pipelines.md#adding-non-production-pipeline)在Git變更上&#x200B;**觸發**&#x200B;以在認可上啟動管道，現在可供[私人存放庫](/help/managing-code/private-repositories.md)使用。
* 生產前管道只能手動觸發，並且不能在Git變更&#x200B;**上設定為**。
* 對於僅限生產的管道，可升級的執行清單包括其成品版本大於在生產環境中部署的成品版本的執行。
* [AEM專案原型](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/developing/archetype/overview)已更新為[版本49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)。

## 早期採用計畫 {#early-adoption}

成為Cloud Manager早期採用計畫的一部分，並有機會測試一些即將推出的功能

### 僅限中繼和僅限生產環境的管道 {#staging-production-only-pipelines}

現已推出對[僅限中繼及僅限生產的管道的支援](/help/using/stage-prod-only.md)，讓您可將完整棧疊生產部署管道分割成較小且專業的部署。

如果您有興趣測試這項新功能並分享您的回饋意見，請從與Adobe ID相關聯的電子郵件地址傳送電子郵件至`Grp-cloudmanager_splitpipelines@adobe.com`。
