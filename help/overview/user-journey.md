---
title: 使用者上線
description: 了解不同的上線情境，以及開始使用 Cloud Manager。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# 使用者上線 {#user-journey}

身為AEM (Adobe Experience Manager)使用者，您符合下列其中一種情況：

* 您是 AEM 新手。
* 您目前正在使用 AEM 6.x。
* 您需要升級至 AEM 6.5 才能使用 [!UICONTROL Cloud Manager]。

本檔案說明這三個案例，並說明開始使用[!UICONTROL Cloud Manager]的程式。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 僅供使用 AEM 6.4 或以上版本的 Adobe Managed Services (AMS) 客戶使用。

## 上線 {#onboarding}

此上線流程會依據您是 AMS 新手或是現有的 AMS 客戶而不同。

### Adobe Managed Services 的新手 {#new-to-ams}

新客戶已加入[!UICONTROL Cloud Manager]，這屬於Adobe Managed Services上線流程的一部分。

在上線流程中，您會收到一封歡迎電子郵件，其中包含以下內容：

* 存取 [!UICONTROL Cloud Manager] 的 URL。
* 登入至 [!UICONTROL Experience Cloud] 的說明。
* 使用Admin Console來管理您的使用者和他們個別許可權的說明，讓他們在需要時能夠存取Cloud Manager 。

### 目前的 Adobe Managed Services 客戶 {#existing-customer}

由於您是現有的 AMS 客戶，首先必須將現有的生產和非生產環境升級到 AEM 6.4 或更高版本。

升級過程中，系統會讓您開始使用 Cloud Manager 並提供存取 [!UICONTROL Cloud Manager] 的 URL。 此外，若使用者需要存取 [!UICONTROL Cloud Manager]，您必須開始使用 Admin Console 來管理他們及其個別權限。

您現有的AEM專案也必須符合建議的作法，因為您開始使用[!UICONTROL Cloud Manager]，將新的程式碼變更部署至AEM環境。

若要取得更多資訊以了解升級至 AEM 6.5 的好處，請參閱「[升級至 AEM 6.5](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)」。

## 存取 [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

使用您的 Adobe Identity Management 憑證登入 [!UICONTROL Experience Cloud] 的登陸頁面。 從解決方案切換器中選取AEM以存取[!UICONTROL Cloud Manager]和您的AEM環境。

第一次登入 [!UICONTROL Cloud Manager] 後，您可直接從 [!UICONTROL Cloud Manager] UI 存取您的 AEM 環境。 此時，您已準備就緒，可使用[!UICONTROL Cloud Manager]的所有功能，並為您將部署至中繼和生產環境的第一個程式碼預做準備。

若要開始使用 [!UICONTROL Cloud Manager]，請參閱「[第一次登入](/help/getting-started/first-time-login.md)」。

如需更多有關 AEM 的資訊，請參閱「[部署和維護](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)」。

## 開始使用 [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

登入 [!UICONTROL Cloud Manager] 之後，您可以透過執行以下操作來開始使用您的 AEM 專案：

1. 設定您的程式碼存放庫環境。
1. 設定您的團隊和角色。 透過使用 Admin Console 將使用者新增到 [!UICONTROL Cloud Manager] 設定檔來指派角色會籍。
1. 在 Git 存放庫中設定您的原始程式碼分支。
1. 定義您的載入和效能KPI （關鍵績效指標）。
1. 當所有的品質檢查都成功通過後，定義測試情境以將程式碼成功部署到中繼和生產環境。

## 程式概述 {#end-to-end-journey}

下圖總結了使用[!UICONTROL Cloud Manager] CI/CD管道將程式碼變更部署到中繼和生產環境時的程式。

![加入Cloud Manager的客戶歷程，透過環境布建或升級、使用者和角色管理、專案實作，以及CI/CD管道，顯示新客戶和現有客戶的路徑。](/help/assets/screen_shot_2018-05-15at124004pm.png)
