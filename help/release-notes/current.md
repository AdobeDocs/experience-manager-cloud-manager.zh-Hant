---
title: Cloud Manager 2025.2.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.2.0 版。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 88%

---

# Adobe Managed Services 上的 Cloud Manager 2025.2.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.2.0 版。

另請參閱Adobe Experience Manager as a Cloud Service ](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)的[最新發行說明。

## 發行日期 {#release-date}

*二月發行的Cloud Manager沒有重大錯誤或功能。*

[!UICONTROL Cloud Manager] 2025.2.0的發行日期為2025年2月13日星期四。

下一個預計發行日期為2025年3月13日星期四。

## 新增功能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* 從 2025 年 2 月 13 日 (星期四) 開始，Cloud Manager 程式碼品質步驟現在使用已升級的 SonarQube 版本 9.9.5.90363。

  更新後的規則 (可透過[此連結](/help/using/code-quality-testing.md#code-quality-testing-step)供 AMS 使用) 會決定 Cloud Manager 管道的安全性評分和程式碼品質。此更新可能會影響您的品質門檻，也可能會阻礙部署。

## 早期採用方案 {#early-adoption}

成為 Cloud Manager 早期採用方案的一部分，並有機會測試即將推出的功能。

### 自備 Git - 現在支援 GitLab 和 Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**自備 Git** 功能已擴充，以納入對 GitLab 和 Bitbucket 等外部存放庫的支援。這項新的支援功能是對私人和企業 GitHub 存放庫現有支援的補充。當您新增這些新存放庫時，也可以將它們直接連結到您的管道。您可以將這些存放庫託管在公有雲平台上或私有雲或基礎架構內。這項整合也消除了與 Adobe 存放庫持續進行代碼同步的需求，並提供了在提取請求合併到主分支之前，驗證提取請求的功能。

對於使用外部存放庫 (不包括 GitHub 託管的存放庫) 且&#x200B;**部署觸發程序**&#x200B;設定為「**在 Git 變更時**」的管道，現在會自動啟動。

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
