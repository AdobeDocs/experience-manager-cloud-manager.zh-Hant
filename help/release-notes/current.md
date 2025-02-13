---
title: Cloud Manager 2025.2.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.2.0 版。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 20%

---

# Adobe Managed Services 上的 Cloud Manager 2025.2.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.2.0 版。

另請參閱Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)的[最新發行說明。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.2.0的發行日期為2025年2月13日星期四。

下一個預計發行日期為2025年3月13日星期四。

## 新增功能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **升級的SonarQube**

  從2025年2月13日星期四開始，Cloud Manager程式碼品質步驟現在使用SonarQube 9.9.5.90363。

  更新的規則適用於AMS，位於[此連結](/help/using/code-quality-testing.md#code-quality-testing-step)，可決定Cloud Manager管道的安全性分數和程式碼品質。

* SonarQube 9.9現在是所有客戶的預設程式碼品質掃描引擎。

* **Java 17和Java 21組建環境支援**

  客戶現在可以選擇使用Java 17或Java 21進行建置，受益於效能改善和新語言功能。 請參閱[建置環境](/help/getting-started/build-environment.md)以取得設定步驟，包括更新您的Maven專案說明和某些程式庫版本。

  >[!NOTE]
  >針對Cloud Service環境，當組建版本設為Java 17或Java 21時，執行階段預設為Java 21。

* **已延伸內容復本驗證**

  已更新內容副本驗證規則。 在此版本中，如果在來源或目標環境中有活動的管道執行，則使用者無法再觸發內容副本。 使用者必須等到所有正在進行的管道執行完成，才能起始內容副本。

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
