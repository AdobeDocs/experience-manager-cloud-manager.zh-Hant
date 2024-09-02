---
title: 通知
description: 了解 Cloud Manager 如何通知您重要事件。
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 81%

---


# 通知 {#notifications}

了解 Cloud Manager 如何通知您重要事件。

## Cloud Manager 中的通知 {#cloud-manager-notifications}

[!UICONTROL Cloud Manager]會在生產部署開始時在生產管道啟動和完成（成功或不成功）時傳送通知給您。 而且，當達到&#x200B;**上線核准**&#x200B;和&#x200B;**已排程**&#x200B;步驟時。 上述通知會經由 [!UICONTROL Experience Cloud] 通知系統傳送。

>[!NOTE]
>
>系統只會將核准和已排程通知傳送給角色為&#x200B;**企業所有者**、**方案管理員**&#x200B;以及&#x200B;**部署管理員**&#x200B;的使用者。

通知會顯示在[!UICONTROL Cloud Manager] 內的側邊欄中並遍及整個 Adobe [!UICONTROL Experience Cloud]。

當您有新通知時，標題中的鈴鐺圖示會出現標記。

![通知圖示](/help/assets/notifications-bell-badged.png)

按一下該鈴鐺圖示，即可開啟側邊欄並檢視通知。該側邊欄中的&#x200B;**通知**&#x200B;索引標籤即會顯示最新通知的清單，例如部署確認。通知內容和您的環境有關。

![通知側邊欄](/help/assets/notifications-activities.png)

**公告**&#x200B;索引標籤會包括 Adobe 產品的公告。公告內容和產品有關。

![通知側邊欄](/help/assets/notificaitons-announcements.png)

按一下通知或公告，即可檢視其詳細內容。連結至管道部署等活動的通知將帶您了解該活動的詳細資訊，例如管道執行視窗。

按一下面板底部的「**檢視全部**」選項，即可檢視收件匣中的所有公告。

按一下面板底部的「**全部標記為已讀**」選項，將所有未讀通知標示為已讀並清除鈴鐺圖示標記。

## 通知設定 {#configuration}

您可以自訂接收通知的方式以及要接收哪些通知。

按一下通知側邊欄頂端的齒輪圖示。

![通知設定圖示](/help/assets/notifications-configuration.png)

**Experience Cloud偏好設定**&#x200B;視窗已開啟，您可以在其中定義通知訂閱及接收通知的方式。

### 訂閱 {#subscriptions}

訂閱會定義您要接收哪些產品的通知和哪些通知。

![通知訂閱](/help/assets/notifications-subscriptions.png)

依預設，您會收到所有產品的所有通知。 按一下產品旁的「**自訂**」，定義您希望接收該產品的哪些類型通知。

![通知訂閱自訂](/help/assets/notifications-subscriptions-customize.png)

### 優先順序 {#priority}

優先警示標示為&#x200B;**高**&#x200B;標籤。 您可以將警報設定為僅以警報形式接收。 在&#x200B;**優先順序**&#x200B;部份中，您可以定義哪些類別符合優先通知的條件。

![通知優先順序](/help/assets/notifications-priority.png)

使用下拉式選單，以新增到符合優先條件類別的清單中。按一下類別名稱旁的`X`以移除它們。

### 警示 {#alerts}

警示會出現在視窗右上角幾秒鐘。使用&#x200B;**警示**&#x200B;部份來定義您接收警示的通知。

![通知警示](/help/assets/notifications-alerts.png)

您可以定義警示的行為。

* **顯示警示** - 定義會觸發警示的通知類型
* **警示應該在畫面上持續顯示，直到我將其關閉為止** - 管控警示是否應該持續顯示 (除非您主動將其關閉)
* **持續時間** - 定義警示應該留在畫面上多久時間 (如果您尚未選擇警示應在畫面上持續顯示)。

### 電子郵件 {#emails}

在所有 Adobe [!UICONTROL Experience Cloud] 解決方案的 Web 使用者介面中都可看到通知。您還能選擇透過&#x200B;**電子郵件**&#x200B;部份中的電子郵件傳送這些通知。

![通知電子郵件](/help/assets/notifications-emails.png)

預設情況下並不會傳送電子郵件。您可以選擇按以下週期接收電子郵件：

* 即時
* 每日
* 每週

當選擇&#x200B;**即時通知**&#x200B;時，每個通知都會立即傳送電子郵件。 對於&#x200B;**每日摘要**&#x200B;和&#x200B;**每週摘要**，您可以選擇傳送每日摘要的時間以及在星期幾與何時傳送每週摘要。
