---
title: Cloud Manager 常見問題集
description: 了解 AMS 客戶提出有關 Cloud Manager 的常見問題的解答。
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: e7e9844b5f06552fc2104584c63935dee7a9fa89
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 100%

---


# Cloud Manager 常見問題集 {#cloud-manager-faqs}

本文件為 AMS 客戶提供有關 Cloud Manager 最常見問題的解答。

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). -->

## 從 Java 8 切換到 Java 11 後，我的組建失敗並出現有關 maven-scr-plugin 的錯誤。該怎麼辦？ {#maven-src-plugin}

嘗試將組建從 Java 8 切換到 11 時，您的 AEM Cloud Manager 組建可能會失敗。如果您遇到下列錯誤，則需要移除 `maven-scr-plugin` 並將所有 OSGi 註解轉換成 OSGi R6 註解。

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

如需有關如何移除此外掛程式的說明，請[參閱此處](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/)。

## 從 Java 8 切換到 Java 11 後，我的組建失敗並出現有關 RequireJavaVersion 的錯誤。該怎麼辦？ {#requirejavaversion}

對於 Cloud Manager 組建，`maven-enforcer-plugin` 可能由於此錯誤而失敗。

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

此已知問題的原因在於 Cloud Manager 使用不同版本的 Java 來執行 Maven 命令而不是編譯程式碼。請忽略 `requireJavaVersion` (於您的 `maven-enforcer-plugin` 設定中)。

## 程式碼品質檢查失敗，目前部署無法進行。是否有辦法略過這項檢查？ {#deployment-stuck}

可以。除了安全評等之外，所有程式碼品質失敗都是非關鍵性量度。因此，在結果 UI 中展開項目，即可視為部署管道的一部分而略過。

擁有[部署管理員、專案管理員或企業所有者](/help/requirements/users-and-roles.md#role-definitions)角色的使用者可以覆寫此問題。在這種情況下，管道會繼續進行。或者，他們可以接受這些問題，則在此情況下管道會因失敗而停止。

如需更多詳細資料，請參閱以下文件：[執行管道時的三層級閘道](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline)以及[設定非生產管道](/help/using/non-production-pipelines.md#understanding-the-flow)。

## Cloud Manager 部署在 Adobe Managed Services 環境中的效能測試步驟失敗。如何對此問題進行偵錯以通過關鍵性量度？ {#debug-critical-metrics}

於這個問題沒有單一解答。但是，以下有關效能測試步驟的幾項說明可能對您有幫助：

* 此步驟為網路效能步驟。也就是關於使用網頁瀏覽器載入頁面的時間。
* 在測試期間，結果 .csv 檔案中列出的 URL 會在 Cloud Manager 基礎結構的 Chrome 瀏覽器中載入。
* 一個常見的失敗量度是錯誤率。因此，為了讓 URL 通過，主要 URL 必須以 `200` 狀態載入，並且必須在 `20` 秒內完成。如果頁面載入超過 `20` 秒，會被標記為 `504` 錯誤。
* 如果您的網站要求使用者驗證，請參閱「[了解您的測試結果](/help/using/code-quality-testing.md#authenticated-performance-testing)」，以便設定您可以驗測自己網站的測試。

如需關於品質檢查的詳細資訊，請參閱「[了解測試結果](/help/using/code-quality-testing.md)」。

## 我是否能將 SNAPSHOT 用於 Maven 專案的版本？ {#snapshot}

可以。對於開發人員的部署，Git 分支 `pom.xml` 檔案必須包含 `-SNAPSHOT` (在 `<version>` 值的結尾)。

此方法使版本未變更時仍可安裝後續部署。在開發人員部署中，不會為 Maven 組建新增或產生自動版本。

您還可以將版本設定為 `-SNAPSHOT`，以用於測試和生產組建或部署。Cloud Manager 會自動設定適當的版本編號並在 Git 中為您建立標記。如有需要，稍後可以參照此標記。

有關版本處理的進一步詳細資訊[記錄在此處](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling)。

## 套件和套裝的版本設定如何用於中繼和生產部署？ {#staging-production}

在中繼和生產部署中，會產生自動化版本，如[此處的紀錄](/help/managing-code/maven-project-version.md)。

對於測試和生產部署中的自訂版本設定，請設定適當的三部分 Maven 版本，例如 `1.0.0`。每次部署到生產時，都需增加版本。

Cloud Manager 會自動將其版本新增到中繼和生產建置，並建立 Git 分支。不需要特別設定。如果您並未依照之前的說明設定 Maven 版本，部署仍會成功，並會自動設定版本。

## 對於 Cloud Manager 部署，我的 Maven 組建失敗，但它在本機建置且沒有出現錯誤。有什麼問題嗎？ {#maven-build-fail}

如需更多詳細資訊，請參閱此「[Git 資源](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)」。

## 我無法使用 aio 命令設定變數。該怎麼辦？ {#set-variable}

嘗試透過 `aio` 命令列出或設定管道變數時，您可能會收到類似以下的 403 錯誤。

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

這種情況下，需要將執行這些命令的使用者新增到 Admin Console 中的&#x200B;**部署管理員**&#x200B;角色。

如需更多詳細資訊，請參閱 [API 權限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)。
