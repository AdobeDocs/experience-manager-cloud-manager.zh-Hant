---
title: Cloud Manager 2025.9.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.9.0 版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 24ec1d82f9a700b57cd74c2c83c8d9d00b8bece1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 68%

---

# Adobe Managed Services 上的 Cloud Manager 2025.9.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.9.0 版。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.9.0的發行日期為2025年9月4日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2025年10月2日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新增功能 {#what-is-new}

* **現在已新增Azure DevOps （私人存放庫）的支援**

  檔案更新包含使用Azure DevOps自攜Git和提取請求驗證的設定步驟。 請參閱[在Cloud Manager中新增外部存放庫](/help/managing-code/external-repositories.md)。

* **將您自己的Git (BYOG)支援延伸至設定管道（私人存放庫）**

  Cloud Manager現在支援在GitHub、Bitbucket、Azure DevOps和GitLab中使用私人存放庫來設定管道。 此支援可進一步加快開發週期。 檢視私人存放庫的![提取要求檢查](/help/managing-code/github-check-config.md)。

## Beta 版方案 {#beta-program}

參與Cloud Manager的Beta計畫，在即將推出的功能正式發行前取得獨家存取權。

目前提供下列機會：


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

8月的Cloud Manager發行版本沒有重大錯誤修正。

<!--
Known Issues {#known-issues}

* A -->
