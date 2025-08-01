---
title: 監視環境
description: 了解如何在 Cloud Manager 中監視環境。
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 75%

---


# 監視環境 {#monitoring-environments}

了解如何在 Cloud Manager 中監視環境。

## 量度臨界值 {#thresholds}

可透過觀察環境中的個別執行個體並追蹤每個執行個體的各種量度來完成 [!UICONTROL Cloud Manager] 中的系統監視。每個量度都有兩個已定義的臨界值：*警告*&#x200B;臨界值以及&#x200B;*嚴重*&#x200B;臨界值。

如果量度超越其警告臨界值 (但低於其嚴重臨界值)，即被視為處於警告狀態。

如果量度超越其嚴重臨界值，即被視為處於嚴重狀態。

Adobe Managed Services 會設定臨界值，您可以在 [!UICONTROL Cloud Manager] 中檢視該資訊。在大多數情況下，客戶之間會保持一致的臨界值，但在某些情況下，Adobe Managed Services 會針對特定的客戶需求編輯臨界值。如有任何關於臨界值的問題，請直接向您的客戶成功工程師 (CSE) 洽詢。

## 存取系統監視 {#accessing-system-monitoring}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織和方案。

1. 按一下要監視的方案的![「更多」圖示 (省略符號)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)。
1. 在功能表的&#x200B;**管理**&#x200B;下方，按一下&#x200B;**顯示監視**&#x200B;以開啟顯示系統監視資訊的&#x200B;**報告**&#x200B;頁面。

   ![設定](/help/assets/first-timea1.png)

.

## 系統監視概觀 {#system-monitoring-overview}

「**系統監視**」區段 (在「**報告**」頁面中) 會列出方案內受監視的環境。並報告四個不同類別中的高層級健康狀況：

* 主機
* 儲存空間
* 網路
* 應用程式

每個類別中的狀態是個別量度的摘要。如果某個類別中的任何量度處於嚴重狀態，則概觀頁面上的整個類別都會處於嚴重狀態。在環境層級和執行個體層級可檢視相同的摘要。

![系統監視概觀](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>預設情況下，瀏覽至此頁面時，可看見生產環境執行個體，但也可檢視其他環境。

## 系統監視詳細資訊 {#system-monitoring-detail}

若要檢視特定量度的詳細資訊，請按一下特定實例的其中一個類別欄或左側導覽中的類別標題。每個詳細資訊頁面都會顯示該類別中量度的一系列圖表。您可以檢視環境中所有執行個體或特定執行個體的量度。您可以使用右上角的下拉式方框在環境和執行個體之間進行切換。

![選取環境](/help/assets/System_Monitoring1.png)

左側的導覽會顯示目前所選類別中的可用量度，其中包含目前所選環境和執行個體的資料。

一張獨立的圖表顯示狀態，以及一張圖表顯示隨時間變化的資料及其臨界值。如果顯示多個執行個體，則每個執行個體的資料會依個別系列顯示。

![量度圖表](/help/assets/Monitoring_Graphs1.png)

按一下圖例中的系列，即可將圖表上的個別系列隱藏。
例如，如果您按一下警告臨界值系列，只會看到嚴重臨界值。

![修改圖表](/help/assets/Monitoring_Graphs2.png)

### 量度定義 {#metric-definitions}

#### 主機 {#host}

* **`Load Per Core`**： CPU正在執行的處理序數目。 或者，在一分鐘 (load1)、五分鐘 (load5) 和十五分鐘 (load15) 期間平均處於等待狀態的佇列程序數。
* **P`rocess Count`**：目前開啟的處理序數目。
* **`User Count`**：具有使用中殼層工作階段的使用者數目。
* **`Memory Usage`**：目前已配置的系統記憶體的百分比。
* **`JVM Memory`**：已配置之Java棧積的大小（以MB為單位）。
* **`Old Generation Space`**：目前已配置的JVM舊世代記憶體的百分比。

#### 網路 {#network}

* **`CQ Port Check`**：存取AEM或Dispatcher連線埠的回應時間（秒）。 作者、發佈和 Dispatcher 有不同的量度。

#### 儲存空間 {#storage}

* **`Disk Space`**：主機上每個掛接點已使用的磁碟空間（以MB為單位）。 每個掛接點都有不同的量度。至少會有 `/` 和 `/mnt` 的量度，但如要更多掛接點量度，可能需視特定執行個體設定而定。
* **`Folder Size`**
* **`AEM Segment Store`**： AEM區段存放區已使用的磁碟空間（以GB為單位）。

#### 應用程式 {#application}

* **`Replication Agent`**：測試復寫事件所需的時間（以秒為單位）
   * 每個複寫代理程式都有單獨的量度。
* **`Dispatcher Flush`**：目前在Dispatcher排清佇列中的專案數

## SLA 報告 {#sla-reporting}

您可以查看生產 AEM 環境相對於您簽訂的服務等級協定 (SLA) 的效能。

下圖會顯示 2019 年每月的 SLA 實現情況。

![SLA 2018 圖表](/help/assets/SLA-Reports-one.png)

和系統監視圖一樣，將資料點翻轉會顯示該月的特定值。

![資料點翻轉](/help/assets/SLA-Reports-two.png)

此圖表下的「**事件分析**」區段會顯示在目前選定年度期間該方案發生的事故組合。每個事故都有一個時間範圍、一個原因和一連串評論。

![事件分析](/help/assets/sla-reporting3.png)

## SLA 量度 {#sla-metrics}

* **`Author Contract`**：您與Adobe Managed Services的合約中為製作層級定義的SLA。
* **`AMS Author SLA`**：測量到的生產製作層級運作時間，因廠商或Adobe引起的客製化事件。
* **`Author SLA`**：測量出的製作層級運作時間，忽略已排程的停工期，例如維護期。
* **`End User Contract`**：您和Adobe Managed Services的合約中為發佈層級定義的SLA。
* **`AMS End User SLA`**：測量到的生產發佈層級運作時間，因廠商或Adobe引起的客製化事件。
* **`End User SLA`**：測量到的發佈層級運作時間，忽略已排程的停工期，例如維護期。

## 教學課程影片 {#video-tutorial}

本影片概觀如何使用 Cloud Manager Reports 產生的圖表來檢視您的方案環境。

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
