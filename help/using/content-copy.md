---
title: 內容複製工具
description: Cloud Manager 內容複製工具能讓使用者依照需要，將可變內容從 AMS 代管的 AEM 6.x 生產環境複製到較低的環境以進行測試。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '1144'
ht-degree: 100%

---


# 內容複製工具 {#content-copy}

Cloud Manager 內容複製工具能讓使用者依照需要，將可變內容從 AMS 代管的 AEM 6.x 生產環境複製到較低的環境以進行測試。

## 簡介 {#introduction}

目前的真實資料對於測試、驗證和使用者接受度很有價值。內容複製工具讓您能將內容從生產 AMS 代管的 AEM 6.x 環境複製到中繼或開發環境中。此工作流程支援各種測試場景。

要複製的內容由內容集來定義。內容集包含具有要複製之可變內容的 JCR 路徑清單。內容從來源環境移動到目標環境。所有過程都在同一個 Cloud Manager 方案中完成。

內容集中允許使用以下路徑：

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

複製內容時，來源環境是真實的來源。

* 如果您在目標環境中編輯內容，於路徑符合的情況下，來源內容會將其覆蓋。
* 如果路徑不同，來源中的內容會與目標中的內容合併。

## 權限 {#permissions}

若要使用內容複製工具，使用者在來源和目標環境中必須被指派為&#x200B;**部署管理員**&#x200B;角色。

## 建立內容集 {#create-content-set}

在複製任何內容之前，必須定義一個內容集。定義後，內容集就可以重複使用來複製內容。請依照下列步驟，建立新的內容集。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從「**概觀**」頁面，瀏覽到「**環境**」畫面。

1. 從「**環境**」畫面瀏覽至「**內容集**」頁面。

1. 在畫面右上角附近，按一下「**新增內容集**」。

   ![內容集](/help/assets/content-sets.png)

1. 在精靈的&#x200B;**詳細資訊**&#x200B;索引標籤上，為內容集提供名稱和說明，然後按一下&#x200B;**繼續**。

   ![內容詳細資料](/help/assets/add-content-set-details.png)

1. 在精靈上的&#x200B;**內容路徑**&#x200B;索引標籤，指定要包含在內容集中的可變內容路徑。

   1. 在&#x200B;**新增包含路徑**&#x200B;中輸入路徑欄位。
   1. 按一下「**新增路徑**」，將路徑新增至內容集。
   1. 必要時，再按一下「**新增路徑**」。

   ![新增路徑至內容集](/help/assets/add-content-set-paths.png)

1. 如果您需要最佳化或限制您的內容集，可以排除子路徑。

   1. 在包含的路徑列表中，按一下您要限制的路徑旁的&#x200B;**新增排除子路徑**&#x200B;圖示。
   1. 輸入要排除在所選路徑之外的子路徑。
   1. 按一下「**排除路徑**」。
   1. 同樣地，如有必要，按一下「**新增排除子路徑**」，新增要排除的其他路徑。

   ![排除路徑](/help/assets/add-content-set-paths-excluded.png)

1. 如有需要，您可以修改指定的路徑。

   1. 按一下已排除之子路徑旁邊的 `X` 將其刪除。
   1. 按一下路徑旁邊的省略符號按鈕，顯示出「**編輯**」和「**刪除**」選項。

   ![正在編輯路徑清單](/help/assets/add-content-set-excluded-paths.png)

1. 按一下&#x200B;**建立**，以建立內容集。

內容集現在可用於在環境之間複製內容。

>[!NOTE]
>
>您最多可以在一個內容集中新增 50 個路徑。
>排除的路徑沒有數量限制。

## 編輯內容集 {#edit-content-set}

請依循下列與建立新內容時類似的步驟。不要按一下&#x200B;**新增內容集**，而是從控制台選取一個現有集，並從省略號選單選取&#x200B;**編輯**。

![編輯內容集](/help/assets/edit-content-set.png)

編輯內容集時，您可能需要展開設定的路徑以顯示排除的子路徑。

## 複製內容 {#copy-content}

建立內容集後，您可以使用它來複製內容。依照下列步驟複製內容。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從「**概觀**」頁面，瀏覽到「**環境**」畫面。

1. 從「**環境**」畫面瀏覽至「**內容集**」頁面。

1. 從控制台選擇一個內容集，然後從省略號選單選擇&#x200B;**複製內容**。

   ![內容複製](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >在以下情況下可能無法選擇環境：
   >
   >* 使用者沒有適當的權限。
   >* 環境中有正在執行的管道或正在進行的複製內容作業。

1. 在「**複製內容**」對話框中，指定內容複製動作的來源和目標環境。
   * 目標環境的區域必須與來源環境的區域相同，或是來源環境區域的子集。

1. 您可以選擇刪除或保留目標環境中的排除路徑。勾選核取方塊 `Do not delete exclude paths from destination` 以保留內容集中指定的 `exclude paths`。若未勾選核取方塊，則會在目標環境中刪除排除路徑。

1. 您可以選擇複製從來源環境複製到目標環境的路徑版本歷史記錄。如果您想複製所有版本的歷史記錄，請勾選 `Copy Versions` 核取方塊。

   ![正在複製內容](/help/assets/copying-content.png)

1. 按一下&#x200B;**複製**。

複製程序開始。複製過程的狀態反映在所選內容集的控制台中。

## 內容複製活動 {#copy-activity}

您可以在「**複製內容活動**」頁面中監視複製過程的狀態。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，然後選取適當的組織和方案。

1. 從「**概觀**」頁面，瀏覽到「**環境**」畫面。

1. 從「**環境**」畫面瀏覽到「**複製內容活動**」頁面。

![內容複製活動](/help/assets/copy-content-activity.png)

### 內容複製狀態 {#statuses}

開始複製內容後，該過程可能具有以下狀態之一。

| 狀態 | 說明 |
|---|---|
| 進行中 | 內容複製作業正在進行中 |
| 已失敗 | 內容複製作業失敗 |
| 完成 | 內容複製作業成功完成 |

## 限制 {#limitations}

內容複製工具具有以下限制。

* 無法將較低環境的內容複製到較高環境。
* 內容複製僅能於同一層級內執行。也就是「作者對作者」或「發佈對發佈」。
* 無法跨方案及跨區域進行內容複製。
* 唯有在來源和目標環境位於相同雲端提供者及區域時，才能對基於雲端資料存放區的拓撲執行內容複製。
* 無法於同一環境中執行並行的內容複製作業。
* 如果在目標或來源環境 (例如 CI/CD 管道) 上有任何作用中的作業正在執行中，則無法執行內容複製。
* 每個內容集最多可以指定 50 個路徑。排除的路徑沒有數量限制。
* 內容複製工具不應用作複製或鏡像工具，因其無法追蹤來源上移動或刪除的內容。
* 內容複製一旦開始就不能暫停或取消。
* 內容複製工具將資產及 Dynamic Media 中繼資料從較高環境複製到選取的較低環境。然後需要在較低的環境中透過 [DAM 流程資產工作流程](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-65/content/assets/using/assets-workflow)對已複製的資產進行再處理，才能使用各自的 Dynamic Media 設定。
* 不複製版本歷史記錄時，內容複製流程會大幅加快。
* 不支援[啟用之資產大小超過 2 GB 的 Dynamic Media 設定](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)。
* 不複製版本歷史記錄時，內容複製過程會大幅加快。
* 目標環境的區域必須與來源環境的區域相同，或是來源環境區域的子集。

## 已知問題 {#known-issues}

{{content-copy-known-issues}}
