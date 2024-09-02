---
title: 評估階段
seo-title: Evaluation Phase
description: 了解產品更新精靈的評估階段如何使用模式偵測器來評估升級複雜性。
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: ht
source-wordcount: '279'
ht-degree: 100%

---


# 評估階段 {#evaluation}

產品更新精靈的第一階段為&#x200B;**[!UICONTROL 評估]**&#x200B;階段，該階段會直接在精靈中使用模式偵測器來評估升級複雜性。在此步驟結束時，您可以存取評估報告。

所產生的報告可讓您透過偵測以下模式來檢查作者實例的升級資格：

* 違反關於受升級影響或覆寫之區域的特定規則。

* 使用 AEM 6.x 功能，或和新版本 AEM 無法回溯相容且升級後可能會中斷的 API。

該報告可用於評估升級到 Adobe Experience Manager (AEM) 6.5 所需的開發工作。

>[!NOTE]
>
>若要了解更多有關模式偵測器的詳細資訊，請參閱「[使用模式偵測器評估升級複雜性](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-65/content/implementing/deploying/upgrading/pattern-detector)」。

## 執行評估報告 {#running}

此模式偵測器可在任何環境中執行。但是，為了提高偵測率並避免影響業務關鍵執行個體的運作速度，Cloud Manager 會在作者實例的中繼環境中執行偵測器。

**若要執行評估報告：**

1. 依照以下[產品更新精靈](/help/product-update-wizard/overview.md)文件中的說明啟動精靈。

1. 按一下「**[!UICONTROL 執行評估]**」。

   ![執行評估](/help/assets/Run-Evaluation.png)

1. 精靈會通知您操作狀態。當產生評估報告時，依據適用情形，您會注意到「**進行中」**&#x200B;或「**已完成**」狀態。

1. 報告產生後，您可以按一下「**[!UICONTROL 下載報告]**」儲存副本。

   ![報告已建立](/help/assets/Evaluation-1.png)

Cloud Manager 中最新版本的產品更新精靈目前僅支援&#x200B;**評估**&#x200B;階段。即將推出其他四個階段，分別為&#x200B;**修復**、**執行**、**驗證**&#x200B;以及&#x200B;**完成**。
