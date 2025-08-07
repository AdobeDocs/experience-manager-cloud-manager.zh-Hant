---
title: Cloud Manager 2025.8.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.8.0 版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 73a094f47f518e2782ac96357e1adc4e923a0b63
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 71%

---

# Adobe Managed Services 上的 Cloud Manager 2025.8.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.8.0 版。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.8.0的發行日期為2025年8月7日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一個預計發行日期為2025年9月4日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新增功能 {#what-is-new}



* **僅限暫存及僅限生產的管道**

  Cloud Manager現在支援僅限中繼及僅限生產的管道。 此功能可讓您將完整棧疊生產部署分割成較小且專用管道。<!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![已選取「完整棧疊程式碼」選項按鈕並選取「中繼」環境的「新增非生產管道」對話方塊](/help/release-notes/assets/add-non-production-pipeline.png)

  請參閱[僅限階段和僅限生產管道](/help/using/stage-prod-only.md)。

* **最愛管道**

  在此版本中，Cloud Manager引入釘選我的最愛管道的功能，可讓您將特定管道標籤為我的最愛，以便這些管道顯示在&#x200B;**管道**&#x200B;頁面上的清單頂端。 此增強功能讓您能夠更容易找到和執行經常存取的管道。<!-- CMGR-68293 -->

  ![Pipelines marked as favorites](/help/release-notes/assets/pipeline-favorites.png) *兩個管道已標記為我的最愛。*

  請參閱[將管道標記為我的最愛](/help/using/managing-pipelines.md#pipeline-favorites)。


## Beta計畫 {#beta-program}

參與Cloud Manager的Beta計畫，在即將推出的功能正式發行前取得獨家存取權。

目前提供下列機會：


### 自備Git (BYOG) {#gitlab-bitbucket-azure-vsts}

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

如果您有興趣測試此新功能並分享意見回饋，請使用與您的 Adobe ID 相關聯的電子郵件寄送電子郵件至 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)。








**自攜Git** (BYOG)功能已擴充為包含對外部存放庫（例如GitLab和Bitbucket）的支援。 這項新的支援功能是對私人和企業 GitHub 存放庫現有支援的補充。當您新增這些新存放庫時，也可以將它們直接連結到您的管道。您可以將這些存放庫託管在公有雲平台上或私有雲或基礎架構內。這項整合也消除了與 Adobe 存放庫持續進行代碼同步的需求，並提供了在提取請求合併到主分支之前，驗證提取請求的功能。

對於使用外部存放庫 (不包括 GitHub 託管的存放庫) 且&#x200B;**部署觸發程序**&#x200B;設定為「**在 Git 變更時**」的管道，現在會自動啟動。

請查看[在 Cloud Manager 中新增外部存放庫](/help/managing-code/external-repositories.md)。

![新增存放庫對話框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，立即可用的提取請求代碼品質檢查僅限於 GitHub 託管的存放庫，但我們正在進行一項更新以將此功能擴展到其他 Git 供應商。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

#### 管理存取權杖{#access-tokens}

使用BYOG的&#x200B;**管理存取權杖**，以檢視、重新命名和刪除與外部自備Git存放庫關聯的存取權杖，例如GitHub Enterprise、GitLab、Bitbucket和Azure DevOps。

請參閱[管理存取權杖](/help/managing-code/manage-access-tokens.md)。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


## 錯誤修正 {#bug-fixes}

7月發行的Cloud Manager並無重大錯誤修正。

<!--
Known Issues {#known-issues}

* A -->
