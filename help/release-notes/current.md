---
title: 2024.7.0 版發行說明
description: 以下是 Cloud Manager 2024.7.0 版的發行說明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d536cd96d135e48039f94fd01142a63305b6eeae
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 65%

---


# Cloud Manager 2024.7.0 版的發行說明 {#release-notes}

本頁記錄 [!UICONTROL Cloud Manager] 2024.7.0 版的發行說明。

>[!NOTE]
>
>如需 AEM as a Cloud Service 中 Cloud Manager 的最新發行說明，請參閱 [AEM as a Cloud Service 中 Cloud Manager 的最新發行說明。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=zh-Hant)

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0版的發行日期為2024年7月18日。 下一版本計畫於 2024 年 8 月 8 日發行。

## 新增功能 {#what-is-new}

* [生產管道](/help/using/production-pipelines.md#adding-production-pipeline)和[非生產管道](/help/using/non-production-pipelines.md#adding-non-production-pipeline)在Git變更上&#x200B;**觸發**&#x200B;以在認可上啟動管道，現在可供[私人存放庫使用。](/help/managing-code/private-repositories.md)
* 生產前管道只能手動觸發，並且不能在Git變更&#x200B;**上設定為**。
* 對於僅限生產的管道，可升級的執行清單包括具有高於在生產環境中部署的成品版本的成品版本。

## 早期採用計劃 {#early-adoption}

參加我們的早期採用計劃，即有機會測試一些即將推出的功能。

### 僅限中繼和僅限生產管道 {#staging-production-only-pipelines}

已引進[僅限中繼和僅限生產管道](/help/using/stage-prod-only.md)的支援，讓您將全端生產部署管道分割為更小的專門部署。

如果您有興趣測試此新功能並分享您的意見反饋，請使用和您的 Adobe ID 相關聯的電子郵件傳送一封電子郵件至 `Grp-cloudmanager_splitpipelines@adobe.com`。
