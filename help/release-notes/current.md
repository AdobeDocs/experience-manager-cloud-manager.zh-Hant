---
title: Cloud Manager 2024.10.0 版發行說明
description: 了解 Cloud Manager 2024.10.0 的發行說明。
feature: Release Information
source-git-commit: 94d5f3487408f9d8908bb15221c48ef768390527
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 24%

---

# Cloud Manager 2024.10.0 版發行說明 {#release-notes}

本頁面記錄了 [!UICONTROL Cloud Manager] 2024.10.0 版的發行說明。

>[!NOTE]
>
>如需 AEM as a Cloud Service 中 Cloud Manager 的最新發行說明，請參閱 [AEM as a Cloud Service 中 Cloud Manager 的最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)。



## 發行日期 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.10.0的發行日期為2024年10月3日。

下一版本計畫於2024年11月14日發行。



## 新增功能 {#what-is-new}

* <!-- BOTH CS & AMS --> Cloud Manager中使用的AEM原型版本現在更新至版本26。 請參閱[https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## 早期採用方案 {#early-adoption}

成為Cloud Manager早期採用計畫的一部分，並有機會測試即將推出的功能。

### 自備Git — 現在支援GitLab和Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**自攜Git**&#x200B;功能已擴充為包含對外部存放庫（例如GitLab和Bitbucket）的支援。 除了這項新支援之外，私人和企業GitHub存放庫也提供現有支援。 新增這些新存放庫時，您也可以將其直接連結至您的管道。 您可以在公用雲端平台上或您的私人雲端或基礎架構內託管這些存放庫。 此整合也免除了與Adobe存放庫持續進行程式碼同步的需求，並可讓您在將提取請求合併至主要分支之前先驗證提取請求。

請參閱[在Cloud Manager](/help/managing-code/external-repositories.md)中新增外部存放庫。

![新增存放庫對話方塊](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，GitHub託管的存放庫僅能執行現成可用的提取要求程式碼品質檢查，不過也正在研究更新以將此功能擴充至其他Git廠商。

如果您有興趣測試這項新功能並分享您的意見回饋，請從與Adobe ID相關聯的電子郵件地址傳送電子郵件至[Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)。 請務必加入您要使用的Git平台，以及您是要使用私人/公有或企業存放庫結構。

### 僅限中繼和僅限生產的管道 {#staging-production-only-pipelines}

Adobe宣佈推出[僅限中繼及僅限生產管道](/help/using/stage-prod-only.md)的支援。 這項新功能可讓您將全端生產部署管道劃分為更小、更專業的部署。

如果您想要測試此功能並提供意見回饋，請透過與Adobe ID相關聯的電子郵件地址傳送電子郵件[Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com)。

<!-- ## Bug fixes

* text
-->

## 已知問題 {#known-issues}

{{content-copy-known-issues}}
