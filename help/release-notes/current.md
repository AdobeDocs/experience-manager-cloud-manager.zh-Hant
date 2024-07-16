---
title: 2024.6.0 版發行說明
description: 以下是 Cloud Manager 2024.6.0 版的發行說明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851b556c0917d9f6d97d958a0c8e8aeff4141079
workflow-type: ht
source-wordcount: '288'
ht-degree: 100%

---


# Cloud Manager 2024.6.0 版的發行說明 {#release-notes}

本頁記錄 [!UICONTROL Cloud Manager] 2024.6.0 版的發行說明。

>[!NOTE]
>
>如需 AEM as a Cloud Service 中 Cloud Manager 的最新發行說明，請參閱 [AEM as a Cloud Service 中 Cloud Manager 的最新發行說明。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=zh-Hant)

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.6.0 版的發行日期為 2024 年 6 月 6 日。下一版本預計於 2024 年 7 月 18 日發行。

## 新增功能 {#what-is-new}

* 您現在可以[使用自己的 GitHub 存放庫](/help/managing-code/private-repositories.md)，做為全端管道的來源。
   * 此外，您還可以透過有 [Git 子模組](/help/managing-code/git-submodules.md)的 GitHub 存放庫，對用於驗證提取請求的自動產生的管道增強控制，並定義程式碼掃描階段中關鍵指標的行為。
   * [您也可以選擇](/help/managing-code/github-check-config.md) 在 GitHub 上保留報告歷史記錄、命名管道，以及按照您的需求設定管道變數。
* 新的 OakPal 規則已新增至 [Cloud Manager 程式碼品管掃描](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)。
   * 截至 2024 年 6 月新增的每項新規則都是非重大變更。
   * 建議您盡快解決這些問題，因為這些新規則將會導致 Cloud Manager 2024 年 8 月版本無法啟動管道。

## 早期採用計劃 {#early-adoption}

參加我們的早期採用計劃，即有機會測試一些即將推出的功能。

### 僅限中繼和僅限生產管道 {#staging-production-only-pipelines}

已引進[僅限中繼和僅限生產管道](/help/using/stage-prod-only.md)的支援，讓您將全端生產部署管道分割為更小的專門部署。

如果您有興趣測試此新功能並分享您的意見反饋，請使用和您的 Adobe ID 相關聯的電子郵件傳送一封電子郵件至 `Grp-cloudmanager_splitpipelines@adobe.com`。
