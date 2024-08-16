---
title: 使用者旅程圖
description: 瞭解不同的上線案例和開始使用Cloud Manager。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 21%

---


# 使用者歷程 {#user-journey}

身為AEM (Adobe Experience Manager)使用者，您可能會符合下列其中一種情況：

* 您為AEM的新手。
* 您目前正在使用AEM 6.x。
* 您必須升級至AEM 6.5才能使用[!UICONTROL Cloud Manager]。

本檔案會展示這三個案例，並說明您的[!UICONTROL Cloud Manager]入門旅程。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 僅供使用 AEM 6.4 或以上版本的 Adobe Managed Services (AMS) 客戶使用。

## 上線 {#onboarding}

此上線流程會依據您是 AMS 新手或是現有的 AMS 客戶而不同。

### Adobe Managed Services 的新手 {#new-to-ams}

您的新客戶即將加入[!UICONTROL Cloud Manager]，這屬於AdobeManaged Services上線流程的一部分。

在上線流程中，您會收到一封歡迎電子郵件，其中包括以下內容：

* 存取[!UICONTROL Cloud Manager]的URL。
* 登入[!UICONTROL Experience Cloud]的指示。
* 使用 Admin Console 來管理您的使用者和他們個別權限的說明，讓他們在需要時能夠存取 [!UICONTROL Cloud Manager]。

### 目前AdobeManaged Services客戶 {#existing-customer}

作為現有的AMS客戶，您必須先將現有的生產和非生產環境升級到AEM 6.4或更高版本。

在升級期間，您已加入Cloud Manager並獲得存取[!UICONTROL Cloud Manager]的URL。 此外，若使用者需要存取[!UICONTROL Cloud Manager]，您必須開始使用Admin Console來管理他們以及他們的個別許可權。

您現有的AEM專案也必須符合建議的最佳做法，因為您開始使用[!UICONTROL Cloud Manager]將新的程式碼變更部署至AEM環境。

若要取得更多有關升級至AEM 6.5的優勢的資訊，請參閱[升級至AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)。

## 存取[!UICONTROL Cloud Manager] {#accessing-cloud-manager}

使用您的AdobeIdentity Management憑證登入[!UICONTROL Experience Cloud]登陸頁面。 從該處，從解決方案切換器選取AEM以存取[!UICONTROL Cloud Manager]和您的AEM環境。

第一次登入[!UICONTROL Cloud Manager]後，您將可直接從[!UICONTROL Cloud Manager] UI存取您的AEM環境。 此時，您已準備就緒，可探索 [!UICONTROL Cloud Manager] 的所有可能性，並為您將部署至中繼和生產環境的第一個程式碼預做準備。

若要開始使用[!UICONTROL Cloud Manager]，請參閱[首次登入](/help/getting-started/first-time-login.md)。

如需有關AEM的其他資訊，請參閱[部署與維護](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)。

## 開始使用[!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

登入[!UICONTROL Cloud Manager]後，您可以透過下列方式開始使用AEM專案：

1. 設定您的程式碼存放庫環境。
1. 設定您的團隊和角色。 透過使用 Admin Console 將使用者新增到 [!UICONTROL Cloud Manager] 設定檔來指派角色會籍。
1. 在Git存放庫中設定原始程式碼分支。
1. 根據載入和效能KPI （關鍵績效指標）定義您的目標。
1. 定義測試案例，在所有品質檢查都通過後，將程式碼成功部署到中繼和生產環境。

## 端對端歷程 {#end-to-end-journey}

此圖表會說明使用用於將程式碼變更部署到中繼和生產環境的[!UICONTROL Cloud Manager] CI/CD管道時高層級的客戶歷程。

![端對端旅程圖](/help/assets/screen_shot_2018-05-15at124004pm.png)
