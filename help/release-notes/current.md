---
title: Cloud Manager 2026.7.0版發行說明
description: 瞭解關於Adobe Managed Services中的Cloud Manager 2026.7.0版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: acd33650c938d49bac5c319f8c938202fe543bbd
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 14%

---


# Adobe Managed Services中Cloud Manager 2026.7.0的發行說明 {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

瞭解關於Adobe Managed Services中[!UICONTROL Cloud Manager] 2026.6.0版的資訊。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.7.0的發行日期為2026年7月9日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2026年8月6日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **模組快取改善組建效能**
新的建置模型使用模組層級快取來改善建置效能，只會編譯已變更的模組（而非整個存放庫）。 其適用於生產管道。 您控制哪些生產管道使用**智慧型組建**。

  如需詳細資訊，請參閱下列內容：

   * [關於在生產管道中使用Smart Build](/help/using/production-pipelines.md#about-smart-build)和[關於在非生產管道中使用Smart Build](/help/using/non-production-pipelines.md#about-smart-build)
   * [新增生產管道](/help/using/production-pipelines.md##adding-production-pipeline)和[新增非生產管道](/help/using/non-production-pipelines.md#add-non-production-pipeline)。

## Beta 版方案 {#beta-program}

參與 Cloud Manager 的 Beta 版方案享有獨家存取權，在即將推出的功能正式發佈之前搶先體驗。

>[!IMPORTANT]
>
>Beta發行版本包含瑕疵，並「按原樣」提供，並無任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援（透過Adobe支援服務或其他方式）測試版。 客戶自行承擔使用測試版的風險，不應仰賴測試版的正確功能或效能，或任何隨附的檔案或資料。 Beta版中的功能和API可能會有所變更，恕不另行通知。 任何使用測試版的風險完全由客戶自行承擔。

目前提供下列Beta版計畫機會：

### AEM Managed Services的Web層管道 {#web-tier-pipelines}

Cloud Manager現在支援AMS程式的專用Web層級管道，讓團隊可部署Dispatcher和Web層設定，而不受完整棧疊部署的影響。 如此可加快網頁層級變更的疊代，同時減少不必要的完整管道執行。 設定Web層管道時，完整棧疊管道會自動跳過該環境的Web層部署，以防止部署衝突。 移除網頁層級管道會自動復原預設部署行為。

若要加入Beta，請聯絡您的Adobe客戶成功工程師以瞭解更多資訊。




## 錯誤修正 {#bug-fixes}

2026年7月AMS版本的Cloud Manager沒有重大錯誤修正。

<!--
Known Issues {#known-issues}

* A 
-->
