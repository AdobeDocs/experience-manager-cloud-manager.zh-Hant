---
title: Cloud Manager 2025.10.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.10.0 版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 03fc811a1a617263efd0f1d5667bba6975826a0e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 55%

---

# Adobe Managed Services 上的 Cloud Manager 2025.10.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.10.0 版。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.10.0的發行日期為2025年10月2日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2025年11月6日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}







## Beta 版方案 {#beta-program}

參與Cloud Manager的Beta計畫，在即將推出的功能正式發行前取得獨家存取權。

目前提供下列機會：

### Experience Hub的可擴充性和自訂 {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub)是您進入AEM的入口點，並根據您組織的需求進行自訂。 告訴Adobe您現有的AEM UI擴充功能，協助您只需最省力就能在Experience Hub中啟用它們。

![Experience Hub擴充性與自訂工作流程圖表](/help/release-notes/assets/experience-hub-extensibility-customization.png)

在Experience Hub中內嵌自訂體驗，以擴充及個人化您的組織控制面板。 除了Adobe的內建Widget，請使用[UI擴充性](https://developer.adobe.com/uix/docs/)架構新增您自己的。 建置以JavaScript為基礎的UI應用程式，並將其呈現給您的使用者，以符合特定業務的需求和工作流程。

對Beta版感興趣嗎？ 請傳送電子郵件給[beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com)，其中包含您的Adobe OrgID以及您打算建立的自訂專案的簡短說明。

### 模組快取可加快組建速度 {#quick-build-cm-pipelines}

新的建置模型會使用模組層級快取來編譯已變更的模組（而非整個存放庫），以縮短建置時間。 它適用於計畫碼品質、完整棧疊和僅限階段的管道。

對Beta版感興趣嗎？ 使用您的Adobe OrgID和方案ID以電子郵件傳送[beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)。

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

10月發行的Cloud Manager沒有重大錯誤修正。

<!--
Known Issues {#known-issues}

* A -->
