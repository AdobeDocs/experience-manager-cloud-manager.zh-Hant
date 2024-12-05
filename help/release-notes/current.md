---
title: Cloud Manager 2024.12.0 版發行說明
description: 瞭解關於Adobe Managed Services的Cloud Manager 2024.12.0版。
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
source-git-commit: e266a4192e2a897f142a6c83ae5766483946320d
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 70%

---

# Adobe Managed Services上Cloud Manager 2024.12.0的發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

瞭解關於Adobe Managed Services的[!UICONTROL Cloud Manager] 2024.12.0版本。

>[!NOTE]
>
>請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.12.0的發行日期為2024年12月5日。

下一個預計發行日期為2025年1月23日。

<!-- ## What's new {#what-is-new} -->

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

## 早期採用方案 {#early-adoption}

成為 Cloud Manager 早期採用方案的一部分，並有機會測試即將推出的功能。

### 自備 Git - 現在支援 GitLab 和 Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**自備Git**&#x200B;功能已擴充為包含對外部存放庫（例如GitLab和Bitbucket）的支援。 這項新的支援功能是對私人和企業 GitHub 存放庫現有支援的補充。當您新增這些新存放庫時，也可以將它們直接連結到您的管道。您可以將這些存放庫託管在公有雲平台上或私有雲或基礎架構內。這項整合也消除了與 Adobe 存放庫持續進行代碼同步的需求，並提供了在提取請求合併到主分支之前，驗證提取請求的功能。

使用外部存放庫（不包括GitHub託管的存放庫）且&#x200B;**部署觸發程式**&#x200B;設為&#x200B;**在Git變更上**&#x200B;的管道現在會自動啟動。

請查看[在 Cloud Manager 中新增外部存放庫](/help/managing-code/external-repositories.md)。

![新增存放庫對話框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，立即可用的提取請求代碼品質檢查僅限於 GitHub 託管的存放庫，但我們正在進行一項更新以將此功能擴展到其他 Git 供應商。

如果您有興趣測試此新功能並分享您的意見回饋，請使用與您的 Adobe ID 關聯的電子郵件地址向 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) 傳送電子郵件。請務必包含您要使用的 Git 平台以及您是否使用私人/公開或企業存放庫結構。


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
