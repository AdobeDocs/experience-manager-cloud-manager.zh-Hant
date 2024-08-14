---
title: 用於 AMS 的 Cloud Manager 的簡介
description: 從這裡開始了解用於 Adobe​ Managed Services (AMS) 的 Cloud Manager 以及它如何讓組織能夠在雲端中自助管理 Adobe​ Experience Manager。
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 8e2c57d2594691e7fb18d8a538caa9b54a26b6bb
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 56%

---


# 用於 AMS 的 [!UICONTROL Cloud Manager] 的簡介 {#introduction-to-cloud-manager}

從這裡開始瞭解適用於AMS (AdobeManaged Services)的Cloud Manager，以及它如何讓組織能夠在雲端中自行管理Adobe Experience Manager。

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="用於 AMS 的 Cloud Manager 的簡介"
>abstract="讓組織能夠在雲端中自助管理 Adobe Experience Manager。其內容包含持續整合與持續傳遞 (CI/CD) 架構，可讓 IT 團隊與實作合作夥伴加速自訂項目或更新的傳遞，而不會影響效能或安全性。"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="建立方案"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="建立環境"

## 簡介 {#introduction}

Adobe Experience Manager 的 [!UICONTROL Cloud Manager] 使開發人員能夠透過以 Adob&#x200B;&#x200B;e Experience Manager 最佳做法為基礎所建置的精簡工作流程建立有影響力的客戶體驗。針對Adobe Experience Manager最佳化的CI/CD管道可讓您輕鬆合併開發工作流程，只需簽入程式碼即可，然後可以一路移至生產就緒。 在建置階段，您的自訂程式碼更新會根據最佳做法進行完整測試，以便為您的客戶提供可靠的應用程式。Cloud Manager 會使用開放式 API 方法，讓您能夠在不中斷現有流程和工具的情況下與您的系統整合。

>[!NOTE]
>
>本文件專門說明用於 Adob&#x200B;&#x200B;e Managed Services (AMS) 的 Cloud Manager 的特性和功能。
>
>您可以在[AEM as a Cloud Service檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/implementing/home)中找到AEM as a Cloud Service的同等檔案。

藉由 Cloud Manager，您的開發團隊將受益於以下功能：

* 持續整合/持續傳遞 (CI/CD) 程式碼，將上市時間從數月/數週縮短至數天/數小時。

* 程式碼檢查、效能測試和安全性驗證會根據最佳做法進行，然後再推送至生產環境，將生產中斷的情況降至最低

* API 連線以補足現有的 DevOps 流程

* 自動縮放功能會聰明地偵測增加容量的需求，並自動將其他 Dispatcher/發佈區段上線。

下圖會說明在 [!UICONTROL Cloud Manager] 中使用的 CI/CD 流程：

![CI/CD 流程](/help/assets/screen_shot_2018-05-12at73843pm.png)

## [!UICONTROL Cloud Manager]中的重要功能 {#key-features-in-cloud-manager}

以下是對 Cloud Manager 選定的重要功能的深入探討。

### 自助服務介面 {#self-service-interface}

適用於[!UICONTROL Cloud Manager]的使用者介面(UI)可讓您輕鬆存取和管理雲端環境，以及輕鬆為Adobe Experience Manager應用程式使用CI/CD管道。

您可以定義應用程式專用的關鍵績效指標(KPI)，例如每分鐘尖峰頁面檢視次數，或預期的頁面載入回應時間。 這些KPI可作為衡量部署成功與否的基礎。 您可以輕鬆定義不同團隊成員的角色和權限。自助服務介面可讓您完全控制。 它還提供最佳做法資源的連結，並可在需要時聯絡Adobe專家以尋求指導。

若要探索並開始使用[!UICONTROL Cloud Manager]的UI，請參閱[首次登入](/help/getting-started/first-time-login.md)。

### CI/CD 管道 {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] 的一項重要功能是運用最佳化 CI/CD 管道的能力，以便加速自訂程式碼或更新的傳送，例如在網站上新增元件。

透過 [!UICONTROL Cloud Manager] UI，您可以設定並啟動您的 CI/CD 管道。此管道的部分作業會執行完整的程式碼掃描，以確保只有高品質的應用程式才能傳遞至生產環境。

若要深入瞭解如何從[!UICONTROL Cloud Manager]的UI設定管道，請參閱[設定生產管道](/help/using/production-pipelines.md)和[設定非生產管道](/help/using/non-production-pipelines.md)。

### 靈活的部署模式 {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] 會提供靈活且可設定的部署模式，讓您因此能夠根據不斷變化的業務需求實現體驗。

使用自動觸發模式時，程式碼會根據特定事件 (例如程式碼認可) 自動部署至環境。您也可以在指定的時間範圍內，甚至在工作時間以外，進行程式碼部署排程。

與部署觸發無關，每次觸發部署時都一定會執行品質檢查，這是 CI/CD 管道執行的一部分。品質檢查包括程式碼檢查、安全性測試和效能測試，全都是現成可用的功能，您或您的合作夥伴無需執行任何設定。

若要進一步瞭解部署程式碼和品質檢查，請參閱[部署程式碼](/help/using/code-deployment.md)。

## Cloud Manager 中的選用功能 {#optional-features-in-cloud-manager}

Cloud Manager提供額外的進階功能，依據您的特定環境設定和需求，這些功能可能對您的專案會有助益。 如果您對這些功能感興趣，請聯絡您的客戶成功工程師(CSE)或Adobe代表以進一步討論。

### 自動縮放 {#autoscaling}

當生產環境承受異常高的負載時，[!UICONTROL Cloud Manager] 會偵測對額外容量的需求並使用其自動縮放功能自動將額外容量上線。

在自動縮放的事件中，[!UICONTROL Cloud Manager] 會自動觸發自動縮放佈建流程，傳送自動縮放事件的通知，並在數分鐘內將額外容量上線。額外容量會布建在相同地區的生產環境中，並採用與執行Dispatcher/發佈節點相同的系統規格。

自動縮放功能適用於Dispatcher/發佈階層，可使用水平縮放功能，新增Dispatcher/發佈配對的一至十個區段。 布建的任何額外容量會在十個工作天的期間內以手動縮放，實際時間長短由AdobeCSE （客戶成功工程師）決定。

>[!NOTE]
>
>如果您想探索自動縮放是否適合您的應用程式，請聯絡您的CSE或Adobe代表。

### 藍綠色部署 {#blue-green}

藍綠色部署是一種透過執行稱為藍色和綠色的兩個相同的生產環境來減少停機時間和風險的技術。

在任何時候，只有一個環境在線上，由線上環境支援所有生產流量。一般來說，藍色會是目前在線上的環境，而綠色則處於閒置狀態。

* 藍綠色部署是 Cloud Manager CI/CD 管道的附加元件，在其中會建立第二組發佈和 Dispatcher 執行個體 (綠色) 並用於部署。然後會將綠色執行個體附加到生產負載平衡器，並移除和終止舊的執行個體（藍色）。
* 此藍綠色的實作會將執行個體視為暫時性，藍綠色管道的每次循環都會建立一組新的發佈和Dispatcher伺服器。
* 在設定過程中會建立一個綠色負載平衡器。 此負載平衡器絕不會變更，因此您應該將您的綠色或「測試」URL指向它。
* 在藍綠色部署期間，會建立現有Dispatcher/發佈階層的精確復本。

#### 藍綠色部署流程 {#flow}

啟用藍綠色部署時，該部署流程和標準雲端服務部署流程不同。

| 步驟 | 藍綠色部署 | 標準部署 |
|---|---|---|
| 1 | 部署給作者 | 部署給作者 |
| 2 | 暫停測試 | - |
| 3 | 建立綠色基礎架構 | - |
| 4 | 部署至綠色發佈/Dispatcher 層級 | 部署給發佈者 |
| 5 | 暫停測試 (最長 24 小時) | - |
| 6 | 將綠色基礎架構新增至生產負載平衡器 | - |
| 7 | 從生產負載平衡器移除綠色基礎架構- |
| 8 | 暫停以進行最終簽核 (最長需要 24 小時) | - |
| 9 | 自動結束藍色基礎架構 | - |
| 10 | 管道已完成 | - |

#### 實作藍綠色 {#implementing}

所有使用Cloud Manager進行生產部署的AMS使用者都有資格使用藍綠色部署。 但是，使用藍綠色部署需要對您的環境進行額外驗證，並由AdobeCSE進行設定。

如果您對藍綠色部署感興趣，請考慮以下要求和限制並聯絡您的CSE。

#### 要求和限制 {#limitations}

* 藍綠色僅適用於Dispatcher/發佈者配對。
* 預覽 Dispatcher/發佈配對不屬於藍綠色部署的一部分。
* 每個Dispatcher/發佈配對都和其他所有的Dispatcher/發佈者配對相同。
* 藍綠色只在生產環境中提供。
* 藍綠色在AWS和Azure中可用。
* 藍綠色不適用於僅限Assets的客戶。
