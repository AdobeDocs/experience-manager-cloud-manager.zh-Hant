---
title: Cloud Manager 2025.1.0 版發行說明
description: 了解 Adobe Managed Services 上的 Cloud Manager 2025.1.0 版。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
source-git-commit: 434740b5ad2dafd5a6c55d0272cf5effdfa6baac
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 31%

---

# Adobe Managed Services 上的 Cloud Manager 2025.1.0 版發行說明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

了解 Adobe Managed Services 上的 [!UICONTROL Cloud Manager] 2025.1.0 版。

>[!NOTE]
>
>請參閱 [Adobe Experience Manager as a Cloud Service 最新發行說明](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/home)。

## 發行日期 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2025.1.0的發行日期為2024年1月22日星期三。

下一個預計發行日期為2025年2月13日星期四。

## 新增功能 {#what-is-new}

**程式碼品質規則 — Sonar Cube升級：** Cloud Manager程式碼品質步驟將開始使用SonarQube Server 9.9搭配Cloud Manager 2025.2.0版本，預計於2025年2月13日星期四推出。

若要準備，更新的SonarQube規則現在可在[程式碼品質規則](/help/using/code-quality-testing.md#code-quality-testing-step)取得。

您可以設定以下管道文字變數（請參閱底下的熒幕擷圖），「提前檢查」新規則：

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

此外，設定下列變數，以確保程式碼品質步驟會針對相同的認可執行（通常針對相同的`commitId`略過）：

`CM_DISABLE_BUILD_REUSE` = `true`

![變數設定頁面](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe建議建立新的CI/CD程式碼品質管道，並設定至與您的主要生產管道相同的分支。 在2025年2月13日發行版本之前&#x200B;*設定適當的變數*，以驗證新的強制規則不會引入封鎖程式。

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
