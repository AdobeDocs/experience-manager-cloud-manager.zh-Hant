---
title: 開發環境的Service Pack更新 — 早期採用者
description: 瞭解您現在如何透過Cloud Manager使用者介面為開發環境啟動Service Pack更新。
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 91691878a2c135cc9fe123c06afcf775a962a2e0
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# 開發環境的Service Pack更新（早期採用者） {#stage-prod-only}

瞭解如何透過Cloud Manager使用者介面為開發環境啟動Service Pack更新。

>[!NOTE]
>
>此功能僅適用於[早期採用者計劃](/help/release-notes/current.md#early-adoption)。

## 概觀 {#service-pack-updates-overview}

您可以透過Cloud Manager使用者介面啟動開發環境的Service Pack更新。 此功能可讓您檢查可用的Service Pack更新，並獨立管理安裝過程。

**主要優點**

* 加強控制Cloud Manager Service Pack更新。
* 減少對Adobe客戶成功工程師(CSE)起始更新的相依性。
* 透過Cloud Manager追蹤整個更新程式。

**目前的限制**

* 自助更新選項僅適用於開發環境。
* 失敗的更新有有限的錯誤報告功能。
* 如果發生問題，您必須聯絡Adobe CSE以便進一步調查。

## 啟動Service Pack更新

1. 使用部署管理員許可權登入Cloud Manager。
1. 導覽至方案概觀頁面。
1. 在「環境」區段下，按一下![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)。

   ![在下拉式功能表中檢查Service Pack更新](/help/using/assets/service-pack-check-for-updates.png)

1. 從下拉式功能表，按一下![以光源圖示開啟](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **檢查更新**&#x200B;以掃描可用的Service Pack更新。

   ![會顯示可用的更新清單](/help/using/assets/service-pack-versions.png)

1. 從清單中按一下所需的Service Pack版本。
1. 按一下&#x200B;**更新Service Pack**&#x200B;以開始更新程式。
1. 在確認對話方塊中，檢閱詳細資料並確認更新。

   確認後，安裝程式就會開始，而且可以在Cloud Manager中追蹤進度。

## 追蹤服務套件更新

啟動更新後，您可以在Cloud Manager的活動頁面中監視進度。

**若要追蹤Service Pack更新：**

1. 從Cloud Manager儀表板導覽至活動頁面。
1. 尋找Service Pack安裝專案。

   ![Service Pack安裝](/help/using/assets/service-pack-installation.png)

1. 按一下專案可檢視類似下列的詳細進度和狀態更新：

   ![Service Pack安裝進度](/help/using/assets/service-pack-progression.png)

### 疑難排解安裝失敗

* 如果安裝失敗，Cloud Manager會自動觸發復原至先前的狀態。
* 如果問題仍然存在，請按一下&#x200B;**下載記錄**&#x200B;以收集錯誤記錄，然後聯絡Adobe支援以進行疑難排解。

## 核准或拒絕服務套件執行

安裝完成後，您需要核准（或拒絕）才能完成更新。

**若要核准或拒絕Service Pack執行：**

1. 在Cloud Manager中開啟「活動」頁面。
1. 尋找Service Pack更新的擱置核准要求。

   ![拒絕或核准Service Pack更新](/help/using/assets/service-pack-reject-approve.png)

1. 執行下列任一項：

   * 若要完成更新，請按一下[核准]。****

   ![核准Service Pack](/help/using/assets/service-pack-approve.png)

   * 若要取消更新，請按一下&#x200B;**拒絕**。
Service Pack安裝已取消，且不會套用任何變更。

   ![拒絕Service Pack](/help/using/assets/service-pack-reject.png)
