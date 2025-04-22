---
title: Cloud Manager 2025.4.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.4.0 版。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b46cb7fb178fc0e63fdc0c04239f461cb206802b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 88%

---

# Adobe Managed Services 上的 Cloud Manager 2025.4.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.4.0 版。

另請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.4.0的發行日期為2025年4月10日星期四。

下一個預計發行日期為2025年5月8日星期四。

<!--
## What's new {#what-is-new}

* 
-->


## 早期採用方案 {#early-adoption}

參與Cloud Manager的搶先採用計畫，在即將推出的功能正式發行前取得獨家存取權。

目前提供下列早期採用機會：

### 自備 Git - 現在支援 GitLab 和 Bitbucket {#gitlab-bitbucket}

**自備 Git** 功能已擴充，以納入對 GitLab 和 Bitbucket 等外部存放庫的支援。這項新的支援功能是對私人和企業 GitHub 存放庫現有支援的補充。當您新增這些新存放庫時，也可以將它們直接連結到您的管道。您可以將這些存放庫託管在公有雲平台上或私有雲或基礎架構內。這項整合也消除了與 Adobe 存放庫持續進行代碼同步的需求，並提供了在提取請求合併到主分支之前，驗證提取請求的功能。

對於使用外部存放庫 (不包括 GitHub 託管的存放庫) 且&#x200B;**部署觸發程序**&#x200B;設定為「**在 Git 變更時**」的管道，現在會自動啟動。

請查看[在 Cloud Manager 中新增外部存放庫](/help/managing-code/external-repositories.md)。

![新增存放庫對話框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，立即可用的提取請求代碼品質檢查僅限於 GitHub 託管的存放庫，但我們正在進行一項更新以將此功能擴展到其他 Git 供應商。

如果您有興趣測試此新功能並分享您的意見回饋，請使用與您的 Adobe ID 關聯的電子郵件地址向 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) 傳送電子郵件。請務必包含您要使用的 Git 平台以及您是否使用私人/公開或企業存放庫結構。

### 僅限中繼和僅限生產的管道 {#staging-production-only-pipelines}

Adobe 宣布推出對[僅階段和僅生產管道](/help/using/stage-prod-only.md)的支援。 這項新功能可讓您將全端生產部署管道劃分為更小、更專業的部署。

如果您想要測試此新功能並提供意見回饋，請使用與您的 Adobe ID 關聯的電子郵件地址向 [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) 傳送電子郵件。



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->


<!--
## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
