---
title: Cloud Manager 2026.11.0版發行說明
description: 瞭解關於Adobe Managed Services中的Cloud Manager 2026.11.0版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 10%
---

# Adobe Managed Services中Cloud Manager 2026.11.0的發行說明 {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

瞭解關於Adobe Managed Services中[!UICONTROL Cloud Manager] 2026.11.0版的資訊。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.11.0的發行日期為2026年11月5日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2026年12月3日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新功能 {#new-features}

### AEM Managed Services的Web層管道 {#web-tier-pipelines}

Cloud Manager現在支援AMS程式的專用Web層級管道，讓團隊可部署Dispatcher和Web層設定，而不受完整棧疊部署的影響。 如此可加快網頁層級變更的疊代，同時減少不必要的完整管道執行。

設定Web層管道時，完整棧疊管道會自動跳過該環境的Web層部署，以防止部署衝突。 移除網頁層級管道會自動復原預設部署行為。<!-- CMGR-27553 -->

請參閱[Web層設定管道](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines)。

## Beta 版方案 {#beta-program}

目前沒有可用的測試版計畫機會。

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## 錯誤修正 {#bug-fixes}


* 程式碼品質掃描在大型專案上失敗。 計畫碼品質(SonarQube)掃描會產生多GB的偵錯記錄，並在掃描某些套件式程式庫（導致組建失敗）時終止。 已更正掃描，因此會在受影響的專案上正常完成。 (CMGR-80025)

* 網站使用CSV匯出會顯示月份標籤移動一個月。 在「授權>網站使用詳細資訊」頁面上，CSV匯出會針對UTC之後時區的使用者，顯示一個月前已移動的標籤。 現在，無論使用者的時區為何，匯出都會顯示正確的月份標籤。 (CMGR-80903)

* 重複使用存取權杖名稱不再覆寫現有的權杖。 在程式中重複使用現有的存取權杖名稱會覆寫共用權杖並建立重複的存取密碼。 Cloud Manager現在可以正確處理權杖名稱重複使用，防止意外覆寫和重複。 (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
