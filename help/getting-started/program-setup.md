---
title: 計劃設定
description: 上線後，企業所有者必須對方案進行一些初始設定。
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 49%

---


# 計畫設定 {#program-setup}

上線後，企業所有者透過新增說明和定義關鍵績效指標(KPI)來設定計畫。 然後這些KPI會用於效能測試。

## 使用[!UICONTROL Cloud Manager]的方案設定 {#program-setup-cloud-manager}

依照下列步驟設定方案並定義 KPI。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織。

1. 按一下&#x200B;**設定方案**，即可開始設定流程。

   ![設定計劃](/help/assets/set-up-program/setup1.png)

1. 在&#x200B;**設定程式**&#x200B;對話方塊中，您可以在三個索引標籤中輸入程式資訊：

   * **一般**
   * **KPI**
   * **佈建**

1. 在&#x200B;**一般**&#x200B;索引標籤上，為您的方案新增說明，並可按一下&#x200B;**變更相片**，選擇上傳縮圖。

   ![「一般」索引標籤](/help/assets/Setup_Program-General.png)

1. 在 **KPI** 索引標籤上，定義您的 KPI。在此範例中，分別為 **AEM Sites** 和 **AEM Assets** 定義了單獨的 KPI。 為您已授權的產品指定KPI。

   請參閱 [KPI](#kpis) 一節，以取得有關如何在 Cloud Manager 中測量 KPI 的更多詳細資訊。

   ![定義 KPI](/help/assets/Setup_Program-KPIs.png)

1. 如果您的方案啟用了自動縮放，您可以在&#x200B;**佈建**&#x200B;索引標籤上為您的環境定義隨選縮放選項。

   自動縮放僅適用於生產環境，而且可能不適用於所有客戶計畫。

   ![佈建選項](/help/assets/Setup_Program-Provisioning.png)

1. 按一下&#x200B;**儲存**。

您的程式已建立。 在方案就緒可供使用之前，可能需要幾分鐘的時間來佈建資源。

## 編輯方案 {#editing-program}

您可以在方案完成設定後進行編輯。請依照以下步驟編輯方案。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織。

1. 從 Cloud Manager 首頁畫面瀏覽至該方案。

1. 按一下&#x200B;**編輯程式**，從&#x200B;**總覽**&#x200B;頁面更新或修改您的程式。

   ![編輯方案選項](/help/assets/set-up-program/edit-program1.png)

1. 會顯示&#x200B;**編輯方案**&#x200B;對話框，讓您能夠更新方案。請參閱[使用 Cloud Manager 的方案設定](#program-setup-cloud-manager)一節，以取得有關可用欄位的詳細資訊。

   ![編輯方案對話框](/help/assets/set-up-program/edit-program-general.png)

1. 按一下&#x200B;**更新**&#x200B;以儲存變更。

變更會立即儲存至Cloud Manager，但在下次管道執行前不會反映在您的環境中。

如果您尚未建立管道，請參閱[設定生產管道](/help/using/production-pipelines.md)和[設定非生產管道](/help/using/non-production-pipelines.md)。

## 在程式之間切換 {#swithing-programs}

在處理一個方案時，您可以快速切換到另一個方案，而無需返回 Cloud Manager 概觀頁面。

使用動作列切換到另一個方案、編輯目前的方案或新增方案。

![計劃切換器](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

對網站KPI的測量會依據在中繼環境中執行的測試。 通常，這些 KPI 會按比例縮小以適合中繼環境的功能。

例如，一個使用者若期望在其生產環境中每分鐘平均有1000次頁面檢視，並在生產環境中有四個Dispatcher/發佈伺服器，應將此情境調整為每分鐘250次頁面檢視。 此案例假設他們的中繼環境僅包含單一Dispatcher/發佈伺服器配對。

Assets效能測試涉及在30分鐘期間內重複上傳資產。 整個測試都會測量每個資產的處理時間及各種系統層級量度。

您的生產環境前面可能有一個內容傳遞網路 (CDN)，例如 Akamai 或 CloudFront。由於[!UICONTROL Cloud Manager]直接針對中繼環境進行測試，因此KPI應僅反映預期會通過CDN的流量。 也就是說，快取遺漏。 一般而言，此體驗是總生產流量的一個相對較小的子集。

## 影片概觀 {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
