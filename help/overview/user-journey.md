---
title: 使用者歷程
description: 了解不同的上線情境，以及開始使用 Cloud Manager。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 95%

---


# 使用者歷程 {#user-journey}

身為 AEM (Adobe Experience Manager) 使用者，您可能會遇到以下其中一個情境：

* 您是 AEM 新手。
* 您目前正在使用 AEM 6.x。
* 您需要升級至 AEM 6.5 才能使用 [!UICONTROL Cloud Manager]。

本文件列出這三種情境，並說明您開始使用 [!UICONTROL Cloud Manager] 的歷程。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 僅供使用 AEM 6.4 或以上版本的 Adobe Managed Services (AMS) 客戶使用。

## 上線 {#onboarding}

此上線流程會依據您是 AMS 新手或是現有的 AMS 客戶而不同。

### Adobe Managed Services 的新手 {#new-to-ams}

如果您是新客戶，您將透過 Adobe Managed Services 的上線流程而開始使用 [!UICONTROL Cloud Manager]。

在上線流程中，您會收到一封歡迎電子郵件，其中包含以下內容：

* 存取 [!UICONTROL Cloud Manager] 的 URL。
* 登入至 [!UICONTROL Experience Cloud] 的說明。
* 使用 Admin Console 來管理您的使用者及其個別權限的說明，讓他們在需要時能夠存取 [!UICONTROL Cloud Manager]。

### 目前的 Adobe Managed Services 客戶 {#existing-customer}

由於您是現有的 AMS 客戶，首先必須將現有的生產和非生產環境升級到 AEM 6.4 或更高版本。

升級過程中，系統會讓您開始使用 Cloud Manager 並提供存取 [!UICONTROL Cloud Manager] 的 URL。此外，若使用者需要存取 [!UICONTROL Cloud Manager]，您必須開始使用 Admin Console 來管理他們及其個別權限。

您現有的 AEM 專案也需要符合建議的最佳實務，因為您開始使用 [!UICONTROL Cloud Manager] 對 AEM 環境部署新程式碼變更。

若要取得更多資訊以了解升級至 AEM 6.5 的好處，請參閱「[升級至 AEM 6.5](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-65/content/implementing/deploying/upgrading/upgrade)」。

## 存取 [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

使用您的 Adobe Identity Management 憑證登入 [!UICONTROL Experience Cloud] 的登陸頁面。於該頁面上，從解決方案切換器中選取 AEM 以存取 [!UICONTROL Cloud Manager] 以及您的 AEM 環境。

第一次登入[!UICONTROL Cloud Manager]後，您就可以直接從[!UICONTROL Cloud Manager] UI存取您的AEM環境。 此時，您已準備就緒，可探索 [!UICONTROL Cloud Manager] 的所有可能性，並為您將部署至中繼和生產環境的第一個程式碼預做準備。

若要開始使用 [!UICONTROL Cloud Manager]，請參閱「[第一次登入](/help/getting-started/first-time-login.md)」。

如需更多有關 AEM 的資訊，請參閱「[部署和維護](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-65/content/implementing/deploying/deploying/deploy)」。

## 開始使用 [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

登入 [!UICONTROL Cloud Manager] 之後，您可以透過執行以下操作來開始使用您的 AEM 專案：

1. 設定您的程式碼存放庫環境。
1. 設定您的團隊和角色。透過使用 Admin Console 將使用者新增到 [!UICONTROL Cloud Manager] 設定檔來指派角色會籍。
1. 在 Git 存放庫中設定您的原始程式碼分支。
1. 根據負載和效能關鍵績效指標 (KPI) 定義您的目標。
1. 當所有的品質檢查都成功通過後，定義測試情境以將程式碼成功部署到中繼和生產環境。

## 端對端歷程 {#end-to-end-journey}

使用將程式碼變更部署到中繼和生產環境的 [!UICONTROL Cloud Manager] CI/CD 管道時，以高層級方式在此圖表中呈現所經歷的客戶歷程。

![端對端歷程](/help/assets/screen_shot_2018-05-15at124004pm.png)
