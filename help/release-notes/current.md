---
title: Cloud Manager 2026.3.0版發行說明
description: 瞭解如何在Adobe Managed Services上發行Cloud Manager 2026.3.0。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9ce8a2ca2117992421052b76b0f5c7c9c5a6195b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 19%

---

# Adobe Managed Services上Cloud Manager 2026.3.0的發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

瞭解如何在Adobe Managed Services上發行[!UICONTROL Cloud Manager] 2026.3.0。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.3.0的發行日期為2026年3月5日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2026年4月2日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

* **支援AEM Experience Hub中的UI擴充功能**
[AEM Experience Hub](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/experience-hub/experience-hub)中的UI擴充功能支援現已啟用，讓開發人員得以使用Adobe App Builder建立的自訂功能和Widget來擴充介面。

  若要進一步瞭解，請參閱[AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/)。

* **設定管道現在支援受管理的密碼**

  使用者現在可以直接在Cloud Manager設定管道中新增和管理秘密。 這些秘密會安全地覆寫管道設定規格中的值，並支援彈性、特定於環境的部署。

  所選管道的下拉式選單上的![檢視/編輯變數選項](/help/release-notes/assets/view-edit-variables-option.png)
  所選管道的下拉式選單上的&#x200B;*檢視/編輯變數選項。*

  ![變數設定對話方塊&#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*變數設定對話方塊。*

* **改善穩定性、效能和可靠性**

  此版本包含最佳化和維護更新，改善了Cloud Manager的穩定性、效能和可靠性。


## Beta 版方案 {#beta-program}

參與Cloud Manager的Beta計畫，在即將推出的功能正式發行前取得獨家存取權。

目前提供下列機會：

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### 模組快取能加快建置速度 {#quick-build-cm-pipelines}

新的建置模型會使用模組層級快取來編譯已變更的模組 (而非整個存放庫)，藉此縮短建置時間。 此建置模型適用於程式碼品質、完整堆疊和僅限中繼管道。

![編輯非生產管道對話方塊，其中顯示兩個建置策略選項，即Full Build和Smart Build](/help/release-notes/assets/non-production-pipeline-edit.png)
*編輯非生產管道對話方塊，其中顯示兩個建置策略選項：完整建置和智慧型建置。*

在&#x200B;**新增/編輯管道**&#x200B;對話方塊的&#x200B;**Source程式碼**&#x200B;索引標籤下方，新的&#x200B;**建置策略**&#x200B;區段可讓您選擇下列其中一個建置選項：

* **完整組建** — 每次執行都會建置存放庫中的所有模組。
* **智慧型組建** — 僅建置自上次認可後變更的模組，這會縮短整體建置時間。

您控制哪些管道使用&#x200B;**智慧型組建**。 在Beta版期間，此選項僅針對&#x200B;**程式碼品質**&#x200B;和&#x200B;**開發部署**&#x200B;管道顯示。

感興趣嗎？ 請寄送電子郵件至 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)，並附上您的 Adobe OrgID 和方案 ID。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## 錯誤修正 {#bug-fixes}

2026年3月AMS版本的Cloud Manager沒有重大錯誤修正。

<!--
Known Issues {#known-issues}

* A -->
