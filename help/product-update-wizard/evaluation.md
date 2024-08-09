---
title: 評估階段
seo-title: Evaluation Phase
description: 了解產品更新精靈的評估階段如何使用模式偵測器來評估升級複雜性。
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 85%

---


# 評估階段 {#evaluation}

產品更新精靈的第一階段是&#x200B;**[!UICONTROL 評估]**&#x200B;階段，該階段會直接在精靈中使用模式偵測器來評估升級複雜性。在此步驟結束時，您將可存取評估報告。

所產生的報告可讓您透過偵測以下模式來檢查作者執行個體的升級資格：

* 違反關於將受升級影響或覆寫的區域的特定規則。

* 使用 AEM 6.x 功能或和新版本 AEM 無法回溯相容且升級後可能會中斷的 API。

該報告可用於評估升級到 Adob&#x200B;&#x200B;e Experience Manager (AEM) 6.5 所需的開發工作。

>[!NOTE]
>
>若要深入瞭解模式偵測器，請參閱[使用模式偵測器評估升級複雜性](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=zh-Hant)。

## 執行評估 {#running}

此模式偵測器可在任何環境中執行。但是，為了提高偵測率並避免對業務關鍵執行個體造成任何減速，Cloud Manager 將在作者執行個體的中繼環境中執行。

請依照下列步驟產生評估報告：

1. 啟動精靈，如檔案[產品更新精靈](/help/product-update-wizard/overview.md)中所述。

1. 按一下&#x200B;**[!UICONTROL 執行評估]**。

   ![執行評估](/help/assets/Run-Evaluation.png)

1. 精靈會通知您操作狀態。當產生評估時，依適用狀態，您將會注意到&#x200B;**進行中**&#x200B;或&#x200B;**已完成**。

1. 報告產生後，您可以按一下&#x200B;**[!UICONTROL 下載報告]**&#x200B;以儲存副本。

   ![報告已建立](/help/assets/Evaluation-1.png)

Cloud Manager 中最新版本的產品更新精靈僅支援&#x200B;**評估**&#x200B;階段。即將推出其他四個分別為&#x200B;**修復**、**執行**、**驗證**&#x200B;以及&#x200B;**完成**&#x200B;的階段。
