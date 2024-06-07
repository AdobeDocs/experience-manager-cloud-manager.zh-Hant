---
title: 2024.6.0 版發行說明
description: 以下是 Cloud Manager 2024.6.0 版的發行說明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 55%

---


# Cloud Manager 2024.6.0 版的發行說明 {#release-notes}

本頁記錄 [!UICONTROL Cloud Manager] 2024.6.0 版的發行說明。

>[!NOTE]
>
>如需 AEM as a Cloud Service 中 Cloud Manager 的最新發行說明，請參閱 [AEM as a Cloud Service 中 Cloud Manager 的最新發行說明。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=zh-Hant)

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.6.0 版的發行日期為 2024 年 6 月 6 日。下一版本預計於 2024 年 7 月 11 日發行。

## 新增功能 {#what-is-new}

* 您現在可以 [使用您自己的GitHub存放庫](/help/managing-code/private-repositories.md) 作為完整棧疊和前端管道的來源。
   * 此外，您還可以充分利用GitHub存放庫， [Git子模組，](/help/managing-code/git-submodules.md) 提供對用於提取請求驗證的自動產生管道的增強控制，並允許您在計畫碼掃描階段定義關鍵量度的行為。
   * [您也可以選擇](/help/managing-code/github-check-config.md) 若要保留GitHub上的報表歷史記錄，請命名管道，並設定管道變數以符合您的需求。
* 新的OakPal規則已新增至 [Cloud Manager程式碼品質掃描。](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * 自2024年6月起新增的每個新規則都是不中斷的變更。
   * 強烈建議您儘快解決這些問題，因為從2024年8月發行的Cloud Manager版本開始，這些新規則會導致管道失敗。

## 早期採用計劃 {#early-adoption}

參加我們的早期採用計劃，即有機會測試一些即將推出的功能。

### 僅限中繼和僅限生產管道 {#staging-production-only-pipelines}

已引進[僅限中繼和僅限生產管道](/help/using/stage-prod-only.md)的支援，讓您將全端生產部署管道分割為更小的專門部署。

如果您有興趣測試此新功能並分享您的意見反饋，請使用和您的 Adobe ID 相關聯的電子郵件傳送一封電子郵件至 `Grp-cloudmanager_splitpipelines@adobe.com`。
