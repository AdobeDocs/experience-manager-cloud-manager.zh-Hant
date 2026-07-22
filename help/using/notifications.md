---
title: 通知
description: 了解 Cloud Manager 如何通知您重要事件。
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
TQID: https://experienceleague.adobe.com/WBAHeIAH1XL6oVy342wLaUAoAHkUoN1AbcAl2Erkte4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 65b260abe417925f26d647fb9857d32c30455f9b
workflow-type: tm+mt
source-wordcount: 562
ht-degree: 52%

---

# 通知 {#notifications}

了解 Cloud Manager 如何通知您重要事件。

## Cloud Manager 中的通知 {#cloud-manager-notifications}

在生產部署期間，當生產管道啟動和完成（成功或失敗）時會傳送通知。 以及，在達到&#x200B;**上線核准**&#x200B;和&#x200B;**排程**&#x200B;步驟時亦發送通知。 上述通知會經由 [!UICONTROL Experience Cloud] 通知系統傳送。

>[!NOTE]
>
>系統只會將核准和已排程通知傳送給角色為&#x200B;**企業所有者**、**方案管理員**&#x200B;以及&#x200B;**部署管理員**&#x200B;的使用者。

通知會顯示在 [!UICONTROL Cloud Manager] 內的側邊欄中並遍及整個 Adobe [!UICONTROL Experience Cloud]。

當您有新通知時，標題中的鈴鐺圖示會顯示指示器。

![通知圖示](/help/assets/notifications-bell-badged.png)

按一下該鈴鐺圖示，即可開啟側邊欄並檢視通知。 該側邊欄中的&#x200B;**通知**&#x200B;索引標籤即會顯示最新通知的清單，例如部署確認。 通知內容和您的環境有關。

![通知側邊欄](/help/assets/notifications-activities.png)

**公告**&#x200B;索引標籤會包括 Adobe 產品的公告。 公告會提供產品的相關資訊。

![通知側邊欄](/help/assets/notificaitons-announcements.png)

按一下通知或公告，即可檢視其詳細內容。 連結至管道部署等活動的通知會導覽至該活動的詳細資訊，例如管道執行視窗。

按一下面板底部的&#x200B;**檢視全部**&#x200B;選項，即可檢視收件匣中的所有宣告。

按一下面板底部的&#x200B;**全部標籤為已讀**&#x200B;選項，將所有未讀通知標籤為已讀，並從鈴鐺圖示中移除徽章。

## 通知設定 {#configuration}

您可以自訂接收通知的方式以及要接收哪些通知。

按一下通知側邊欄頂端的齒輪圖示。

![通知設定圖示](/help/assets/notifications-configuration.png)

**Experience Cloud偏好設定**&#x200B;視窗會開啟，您可以在其中定義通知訂閱及接收通知的方式。

### 訂閱 {#subscriptions}

訂閱會定義您收到通知的產品以及您收到的通知。

![通知訂閱](/help/assets/notifications-subscriptions.png)

預設情況下，您接收所有產品的所有通知。 若要定義您收到的產品通知型別，請按一下旁邊的&#x200B;**自訂**。

![通知訂閱自訂](/help/assets/notifications-subscriptions-customize.png)

### 優先順序 {#priority}

優先警報會標示「**HIGH**」標記。 您可以將它們設定為僅作為通知傳送。 在&#x200B;**優先順序**&#x200B;部份中，您可以定義哪些類別符合優先通知的條件。

![通知優先順序](/help/assets/notifications-priority.png)

使用下拉式選單，以新增到符合優先條件類別的清單中。 按一下類別名稱旁的刪除圖示即可刪除。

### 警示 {#alerts}

警示會出現在視窗右上角幾秒鐘。 使用&#x200B;**警示**&#x200B;區段來定義您接收警示的通知。

![通知警示](/help/assets/notifications-alerts.png)

您可以定義警示的行為。

* **顯示**&#x200B;的警示 — 定義會觸發警示的通知型別。
* **警示會一直顯示在畫面上，直到您將其關閉為止** — 控制警示是否持續存在，除非您主動將其關閉。
* **持續時間** — 定義警示在熒幕上停留的時間長度（如果您尚未選擇警示在熒幕上）。

### 電子郵件 {#emails}

在所有 Adobe [!UICONTROL Experience Cloud] 解決方案的 Web 使用者介面中都可看到通知。 若要透過電子郵件接收這些通知，請在&#x200B;**電子郵件**&#x200B;區段中選擇加入。

![通知電子郵件](/help/assets/notifications-emails.png)

預設情況下不會傳送電子郵件。 您可以選擇以下列方式接收電子郵件：

* 即時
* 每日
* 每週

若選擇「**即時通知**」，則每個通知都會立即傳送電子郵件。 對於「**每日摘要**」和「**每週摘要**」，您可以選擇在什麼時間接收每日摘要，以及在星期幾和什麼時間接收每週摘要。
