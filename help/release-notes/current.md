---
title: Cloud Manager 2025.12.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.12.0 版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 36711ce7a186a67a10dc641541f0645c540e3825
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 69%

---

# Adobe Managed Services 上的 Cloud Manager 2025.12.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.12.0 版。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.12.0的發行日期為2025年12月4日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2026年1月22日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

* **改善穩定性、效能和可靠性**

  此版本包含最佳化和維護更新，改善了Cloud Manager的穩定性、效能和可靠性。

## Beta 版方案 {#beta-program}

參與Cloud Manager的Beta計畫，在即將推出的功能正式發行前取得獨家存取權。

目前提供下列機會：

### Experience Hub 的擴展性和自訂 {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/experience-hub/experience-hub) 是您存取 AEM 的入口點，並可根據組織需求進行自訂。告知 Adobe 您現有的 AEM 使用者介面擴充功能，以便協助您花最少的力氣便能在 Experience Hub 中啟用這些功能。

![Experience Hub 擴展性與自訂工作流程的圖表](/help/release-notes/assets/experience-hub-extensibility-customization.png)

在 Experience Hub 中嵌入自訂體驗，以擴充組織儀表板的功能以及進行個人化設定。除了 Adobe 的內建小工具之外，您可以使用[使用者介面擴展性](https://developer.adobe.com/uix/docs/)框架自行新增小工具。建置以 JavaScript 為基礎的使用者介面應用程式，並將其呈現給您的使用者，以滿足特定業務需求和工作流程。

有興趣使用 Beta 版嗎？請寄送電子郵件至 [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com)，附上您的 Adobe OrgID 並簡短說明您想要算建立的自訂內容。

### 模組快取能加快建置速度 {#quick-build-cm-pipelines}

新的建置模型會使用模組層級快取來編譯已變更的模組 (而非整個存放庫)，藉此縮短建置時間。此建置模型適用於程式碼品質、完整堆疊和僅限中繼管道。

![編輯非生產管道對話方塊，其中顯示兩個建置策略選項，即Full Build和Smart Build](/help/release-notes/assets/non-production-pipeline-edit.png)
*編輯非生產管道對話方塊，其中顯示兩個建置策略選項：完整建置和智慧型建置。*

在&#x200B;**新增/編輯管道**&#x200B;對話方塊的&#x200B;**Source程式碼**&#x200B;索引標籤下方，新的&#x200B;**建置策略**&#x200B;區段可讓您選擇下列其中一個建置選項：

* **完整組建** — 每次執行都會建置存放庫中的所有模組。
* **智慧型組建** — 僅建置自上次認可後變更的模組，這會縮短整體建置時間。

您控制哪些管道使用&#x200B;**智慧型組建**。 在Beta版期間，此選項僅針對&#x200B;**程式碼品質**&#x200B;和&#x200B;**開發部署**&#x200B;管道顯示。

感興趣嗎？請寄送電子郵件至 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)，並附上您的 Adobe OrgID 和方案 ID。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


### 自備 Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

客戶現在可以將其 Azure DevOps Git 存放庫加入 Cloud Manager 中，並同時支援現代 Azure DevOps 和舊版 VSTS (Visual Studio Team Services) 存放庫。

* Edge Delivery Services 使用者可以使用所加入的存放庫來同步處理及部署網站程式碼。
* AEM as a Cloud Service 和 Adobe Managed Services (AMS) 使用者可以將此存放庫連結至全堆疊以及前端管道。

即將推出對更多管道類型的支援以及透過程式碼品質管道驗證提取要求的功能。

請查看[在 Cloud Manager 中新增外部存放庫](/help/managing-code/external-repositories.md)。

![Add Repository dialog box](/help/release-notes/assets/azure-repo.png)

如果您有興趣測試此新功能並分享您的意見回饋，請使用與您的 Adobe ID 關聯的電子郵件地址向 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) 傳送電子郵件。請務必包含您要使用的 Git 平台以及您是否使用私人/公開或企業存放庫結構。

#### 管理存取權杖{#manage-access-tokens}

使用 Cloud Manager 中的&#x200B;**管理存取權杖**，檢視、重新命名及刪除與外部 BYOG 存放庫 (例如 GitHub Enterprise、GitLab、Bitbucket 和 Azure DevOps) 關聯的存取權杖。

請參閱[管理存取權杖](/help/managing-code/manage-access-tokens.md)。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## 錯誤修正 {#bug-fixes}

2025年12月Cloud Manager的AMS版本沒有重大錯誤修正。

<!--
Known Issues {#known-issues}

* A -->
