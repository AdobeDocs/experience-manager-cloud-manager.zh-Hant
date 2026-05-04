---
title: 管理環境
description: 了解如何使用 Cloud Manager 來管理您的環境。
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 275
ht-degree: 100%

---

# 管理環境 {#managing-environments}

了解如何使用 Cloud Manager 來管理您的環境。

## 概觀頁面 {#overview-page}

**Cloud Manager 的概觀**&#x200B;頁面包括&#x200B;**環境**&#x200B;圖磚，上面會提供所有受管理的 AEM 環境清單。

此環境清單中的每一項都會顯示其相關的狀態。

![概觀頁面](/help/assets/Manage-Environ-Overview.png)

## 環境圖磚 {#environments-tile}

此&#x200B;**環境**&#x200B;圖磚會顯示在您的方案中佈建的生產和中繼環境以及狀態。

此狀態指依據以下優先順序跨越環境中的節點彙總的電源狀態。

* 綠色 - 所有節點運作中
* 紅色 - 一或更多節點已停止。
* 藍色 - 一或更多節點將啟動。
* 黃色 - 一或更多節點無法提供電源狀態。

![環境圖磚](/help/assets/Environments-card-new.png)

## 管理環境 {#managing-environments-with-cloud-manager}

在「**環境**」圖磚上，按一下任何環境列，即可顯示「**環境**」畫面。

「**環境**」畫面會顯示程式中的各個生產和中繼環境。 每張卡片的上方都會顯示環境名稱。 卡片會包括環境中的節點表以及 CPU 的 T 恤尺寸、儲存空間、區域和狀態。

>[!NOTE]
>
>節點的&#x200B;**狀態**&#x200B;並不表示 VM 的電源狀態，且不反映伺服器上 AEM 的狀態。 該狀態有可能是：

* 綠色 - 運作中
* 紅色 - 已停止
* 藍色 - 即將啟動
* 黃色 - 無法提供

![「環境」索引標籤](/help/assets/Environments-tab.png)

>[!NOTE]
>
>環境詳細資訊 (例如名稱) 一旦佈建後就無法變更。

>[!NOTE]
>
>透過客戶成功工程師請求提供您的環境記錄。

## 教學課程影片 {#video-tutorial}

此影片會概觀由 AEM 編寫、發佈以及 Dispatcher 執行個體組成的 Cloud Manager 環境。

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

*(3 分鐘、1 秒)*
