---
title: 評估階段
seo-title: Evaluation Phase
description: 了解產品更新精靈的評估階段如何使用模式偵測器來評估升級複雜性。
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 59%

---

# 評估階段 {#evaluation}

產品更新精靈的第一階段是&#x200B;**[!UICONTROL 評估]**&#x200B;階段。 它會在精靈中執行模式偵測器，以評估升級複雜性。 在此步驟結束時，您可以檢視評估報告。

該報告會透過偵測以下模式，來檢查作者執行個體的升級整備程度：

* 受升級影響或覆寫的區域中的規則違規。
* 此版本使用的AEM 6.x功能或API無法回溯相容，且升級後可能會失效。

此報表有助於估計升級至Adobe Experience Manager (AEM) 6.5所需的開發工作。

>[!NOTE]
>
>若要了解更多有關模式偵測器的詳細資訊，請參閱「[使用模式偵測器評估升級複雜性](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector)」。

## 執行評估報告 {#running}

此模式偵測器可在任何環境中執行。 但是，為了提高偵測率並避免影響業務關鍵執行個體的運作速度，Cloud Manager 會在作者實例的中繼環境中執行偵測器。

**若要執行評估報告：**

1. 依照以下[產品更新精靈](/help/product-update-wizard/overview.md)文件中的說明啟動精靈。

1. 按一下「**[!UICONTROL 執行評估]**」。

   ![執行評估](/help/assets/Run-Evaluation.png)

1. 精靈會通知您操作狀態。 當產生評估報告時，依據適用情形，您會注意到「**進行中」**&#x200B;或「**已完成**」狀態。

1. 報告產生後，您可以按一下「**[!UICONTROL 下載報告]**」儲存副本。

   ![報告已建立](/help/assets/Evaluation-1.png)

Cloud Manager中目前的產品更新精靈僅支援&#x200B;**評估**&#x200B;階段。 即將推出其他四個階段，分別為&#x200B;**修復**、**執行**、**驗證**&#x200B;以及&#x200B;**完成**。
