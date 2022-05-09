---
title: 2021.11.0 版發行說明
description: 按照本頁獲取Cloud Manager 2021.11.0版的資訊
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 3%

---

# 2021.11.0 版發行說明 {#release-notes-for}

以下部分概述了有關 [!UICONTROL Cloud Manager] 2021.11.0版。

>[!NOTE]
>請參閱 [當前發行說明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) 查看as a Cloud Service中Cloud Manager的最新發行說明AEM。

## 發行日期 {#release-date}

發放日期 [!UICONTROL Cloud Manager] 版本2021.11.0為2021年11月4日。
下一版計畫於2021年12月16日發行。

## 新增功能 {#whats-new}

* Git提交ID現在將顯示在管道執行詳細資訊中，使跟蹤生成的代碼更容易。

* 的 `x-request-id` 響應標頭現在可在上的API Ploagn中看到 [www.adobe.io](https://www.adobe.io/)。 此標題在提交客戶關心問題以進行故障排除時非常有用。

* 作為用戶，我看到零管線的管線卡為我提供了適當的指導。

* 現在可以使用新的「活動」頁，其中可以查看諸如管道和代碼執行等活動及其關聯的詳細資訊。 隨著時間的推移，此頁中列出的活動將擴展範圍以及提供的詳細資訊。

* 現在可以使用一個新的「管線」(Pipelines)頁面，該頁面具有懸停時的狀態跨距，以便輕鬆查看詳細資訊摘要。 可以查看管道執行及其關聯的詳細資訊。

* Edit Pipeline API現在支援設定調度程式失效和刷新路徑。

* 「編輯管道API」現在支援更改部署階段中使用的環境。

* 介紹了OakPal掃描過程中對大包裝的優化。

* 質量問題CSV檔案現在將包含每個質量問題的時間戳。

* 「環境」頁中的「管理」按鈕在UI中不再可見。

## 錯誤修正 {#bug-fixes}

* 某些非常規的生成配置導致不必要的檔案儲存在管道的Maven項目快取中，這導致在啟動和停止生成容器時產生額外的網路I/O。

* 如果部署階段不存在，管道PATCHAPI將失敗。

* 的 `ClientlibProxyResourceCheck` 當存在具有共同基本路徑的客戶端庫時，質量規則會產生誤報問題。

* 達到最大資料庫數時的錯誤消息未指定錯誤原因。

* 在少數情況下，管道由於某些響應代碼的重試處理不當而失敗。