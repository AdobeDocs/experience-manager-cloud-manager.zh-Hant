---
title: Cloud Manager 2026.9.0版發行說明
description: 瞭解關於Adobe Managed Services中的Cloud Manager 2026.9.0版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: e10c3c15c01c28f6bad0a9cf0464288937402cb7
workflow-type: tm+mt
source-wordcount: 403
ht-degree: 8%

---


# Adobe Managed Services中Cloud Manager 2026.9.0的發行說明 {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

瞭解關於Adobe Managed Services中[!UICONTROL Cloud Manager] 2026.9.0版的資訊。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.9.0的發行日期為2026年9月3日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2026年10月1日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

2026年9月Cloud Manager的AMS版本沒有重大新功能。


## Beta 版方案 {#beta-program}

若要在即將發行的功能正式發行前以獨家方式存取這些功能，請參與Cloud Manager的Beta版計畫。

>[!IMPORTANT]
>
>Beta發行版本包含瑕疵，且不含任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援（透過Adobe支援服務或其他方式）測試版。 客戶自行承擔使用Beta版的風險。 請勿仰賴測試版正確運作或效能，或仰賴任何隨附的檔案或材料。 Beta版中的功能和API可能會有所變更，恕不另行通知。 任何使用測試版的風險完全由客戶自行承擔。

目前提供下列Beta版計畫機會：

### AEM Managed Services的Web層管道 {#web-tier-pipelines}

Cloud Manager現在支援AMS程式的專用Web層級管道，讓團隊可部署Dispatcher和Web層設定，而不受完整棧疊部署的影響。 如此可加快網頁層級變更的疊代，同時減少不必要的完整管道執行。 設定Web層管道時，完整棧疊管道會自動跳過該環境的Web層部署，以防止部署衝突。 移除網頁層級管道會自動復原預設部署行為。

若要加入Beta，請聯絡您的Adobe客戶成功工程師以瞭解更多資訊。


## 錯誤修正 {#bug-fixes}

* 重新產生存放庫存取密碼現在會使舊密碼失效。 先前，重新產生Git存放庫存取密碼不會立即讓先前的密碼失效，使舊認證可用。 重新產生密碼現在會立即讓舊密碼失效，確保無法再使用先前的認證。 (CMGR-41820)

* 已更新許可權檢查以強制執行資源所有權。 已解決如何評估許可權檢查，以便一律根據擁有計畫的組織驗證計畫存取權的問題。 這加強了組織之間許可權閘道操作的隔離。 (CMGR-79156)

<!--
Known Issues {#known-issues}
-->
