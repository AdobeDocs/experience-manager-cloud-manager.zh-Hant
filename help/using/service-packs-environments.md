---
title: 開發環境的Service Pack更新 — 私人測試版
description: 了解如何立即透過 Cloud Manager 使用者介面，啟用開發環境的 Service Pack 更新。
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 94%

---

# 開發環境的Service Pack更新（私人測試版） {#stage-prod-only}

了解如何透過 Cloud Manager 使用者介面，啟用開發環境的 Service Pack 更新。

>[!NOTE]
>
>此功能僅適用於[私人測試版計畫](/help/release-notes/current.md#beta-program)。

## 概觀 {#service-pack-updates-overview}

您可以透過 Cloud Manager 使用者介面啟用開發環境的 Service Pack 更新。您可以利用這項功能檢查可用的 Service Pack 更新，並分別管理安裝程序。

**主要優勢**

* 為 Cloud Manager Service Pack 更新提供更完善的控制功能
* 減少依賴 Adobe 客戶成功工程師 (CSE) 啟用更新的情形。
* 透過 Cloud Manager 追蹤整個更新程序。

**目前限制**

* 自助更新選項僅適用於開發環境。
* 更新失敗時提供有限的錯誤報告。
* 如果發生問題，需聯絡 Adobe CSE 進行進一步調查。

## 啟用 Service Pack 更新

1. 使用部署管理員權限登入 Cloud Manager。
1. 導覽至「方案概觀」頁面。
1. 在「環境」區段下，按一下![「更多」圖示 (省略符號)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)。

   ![檢查下拉式選單中的 Service Pack 更新](/help/using/assets/service-pack-check-for-updates.png)

1. 在下拉式選單中按一下「![在新視窗開啟的圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg)**檢查更新**」，掃描可用的 Service Pack 更新。

   ![顯示可用更新的清單](/help/using/assets/service-pack-versions.png)

1. 在清單上按一下所需的 Service Pack 版本。
1. 按一下「**更新 Service Pack**」來開始更新程序。
1. 在確認對話框中，檢視詳細資訊並確認此更新。

   確認後便會開始安裝程序，並且可在 Cloud Manager 中追蹤進度。

## 追蹤 Service Pack 更新

啟用更新後，您可以在 Cloud Manager 的「活動」頁面監視進度。

**若要追蹤 Service Pack 更新：**

1. 從 Cloud Manager 儀表板導覽至「活動」頁面。
1. 搜尋 Service Pack 安裝項目。

   ![Service Pack 安裝](/help/using/assets/service-pack-installation.png)

1. 按一下該項目來檢視詳細進度和狀態更新，與下圖類似：

   ![Service Pack 安裝進度](/help/using/assets/service-pack-progression.png)

### 安裝失敗疑難排解

* 如果安裝失敗，Cloud Manager 會自動觸發復原至以前的狀態。
* 如果問題仍無法解決，按一下「**下載記錄**」來收集錯誤記錄，然後聯絡 Adobe 支援進行疑難排解。

## 核准或拒絕執行 Service Pack

安裝完成後，需予以核准或拒絕才能完成更新。

**若要核准或拒絕執行 Service Pack：**

1. 在 Cloud Manager 中開啟「活動」頁面。
1. 找到 Service Pack 更新的待核准請求。

   ![拒絕或核准 Service Pack 更新](/help/using/assets/service-pack-reject-approve.png)

1. 執行下列其中一項：

   * 若要完成更新，按一下「**核准**」。

   ![核准 Service Pack](/help/using/assets/service-pack-approve.png)

   * 若要取消更新，按一下「**拒絕**」。
如此將會取消 Service Pack 安裝，且不套用任何變更。

   ![拒絕 Service Pack](/help/using/assets/service-pack-reject.png)
