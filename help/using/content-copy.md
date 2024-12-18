---
title: 維持環境一致性的內容複製功能
description: 使用者可以使用 Cloud Manager 中的內容複製功能，依需求將可變內容從 Adobe Managed Services 託管的 Adobe Experience Manager 6.x 生產環境複製到低階環境以進行測試。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 96%

---


# 維持環境一致性的內容複製功能 {#content-copy}

使用者可以使用 Cloud Manager 中的內容複製功能，依需求將可變內容從 Adobe Managed Services 託管的 Adobe Experience Manager 6.x 生產環境複製到低階環境以進行測試。

## 關於內容複製功能 {#introduction}

目前，真實資料對於測試、驗證和達成使用者接受度均很重要。您可以使用內容複製功能，把 AMS 託管的 AEM 6.x 生產環境的內容複製到中繼或開發環境中。此工作流程支援各種測試場景。

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

如果您在目標環境中編輯內容，於路徑符合的情況下，來源內容會將其覆蓋。

如果路徑不同，來源中的內容會與目標中的內容合併。

### 權限 {#permissions}

若要使用內容複製功能，使用者必須在來源和目標環境中獲指派為&#x200B;**部署管理員**&#x200B;角色。

## 建立內容集 {#create-content-set}

在複製任何內容之前，必須定義一個內容集。定義後，內容集就可以重複使用來複製內容。請依照下列步驟，建立新的內容集。

**若要建立內容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 在頁面左上角，按一下![顯示選單圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側選單。

1. 在左側選單的「**服務**」頁面下方，按一下![方塊圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg)「**內容集**」。

1. 在頁面的右上角附近，按一下「**新增內容集**」。

   ![內容集](/help/assets/content-sets.png)

1. 在「**`Add Content Set`**」對話框中，於「**詳細資料**」標籤上的「**名稱**」和「**說明**」欄位，輸入內容集的名稱和選填的說明，然後按一下「**繼續**」。

   ![內容集詳細資料](/help/assets/add-content-set-details.png)

1. 在「**內容路徑**」標籤的「**路徑**」文字欄位中，指定可變更內容的路徑且應包含在內容集中。

   只有以 `/content`、`/conf`、`/etc`、`/var/workflow/models` 或 `/var/commerce` 開頭的路徑才可以包含在內。

1. 按一下&#x200B;**![新增資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg)「新增路徑**」來新增 (或包含) 內容集的路徑。

1. (選用) 如有必要，請重複前兩個步驟，並視需要新增其他路徑 (最多 50 個)。否則，請繼續下一步。

   ![新增路徑至內容集](/help/assets/add-content-set-paths.png)

1. (選用) 若要縮小內容集的範圍，您可以選擇性指定已包含內容路徑中應排除的子路徑。

   1. 在您要限制的已包含內容路徑的右側，按一下![刪除資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)。
   1. 在文字欄位中，輸入在對話框中顯示的根路徑之相對路徑。
   1. 按一下![刪除資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)「**排除路徑**」。
   1. 如有必要，請重複上方步驟 i 至 iii以新增更多排除路徑；沒有限制。否則，請繼續下一步。

   ![排除路徑](/help/assets/add-content-set-paths-excluded.png)

1. (選用) 執行以下任一操作：

   1. 按一下已排除子路徑右側的![十字大小 500 圖示](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg)將其刪除。
   1. 按一下已包含內容路徑右側的![更多圖示](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然後按一下「**編輯**」或「**刪除**」。

   ![編輯路徑清單](/help/assets/add-content-set-excluded-paths.png)

1. 按一下「**建立**」。您現在可以使用內容集複製各個環境之間的內容。

## 編輯或刪除內容集 {#edit-content-set}

編輯內容集時，您可能需要展開設定的路徑以顯示已排除的子路徑。

**若要編輯或刪除內容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 在頁面左上角，按一下![顯示選單圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側選單。

1. 在左側選單的「**服務**」下方，按一下![方塊圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg)「**內容集**」。

1. 在「**內容集**」頁面的表格中，按一下已包含內容路徑右側的![更多圖示](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然後按一下「**編輯**」或「**刪除**」。

![編輯內容集](/help/assets/edit-content-set.png)

## 複製內容 {#copy-content}

建立內容集後，您可以使用它來複製內容。

如果符合以下任一條件，則您可以無法選擇該環境：

* 使用者缺乏所需的權限。
* 環境中有正在執行的管道或複製內容作業。

**若要複製內容：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 在頁面左上角，按一下![顯示選單圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側選單。

1. 在左側選單的「**服務**」下方，按一下![方塊圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg)「**內容集**」。

1. 在「**內容集**」頁面上的表格中，在要複製的已包含內容路徑的右側，按一下![更多圖示](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然後按一下「**複製內容**」。

   ![內容複製](/help/assets/copy-content.png)

1. 在「**複製內容**」對話框中，選取內容複製動作的&#x200B;**來源**&#x200B;環境和&#x200B;**目標**&#x200B;環境。

   * 目的地環境中的區域必須是來源環境中區域的子集。
   * 系統會在執行內容複製動作之前檢查相容性問題。您選取&#x200B;**目標**&#x200B;環境時，系統會自動驗證來源環境和目標環境。如果驗證失敗，程序就會停止，並在對話框中顯示錯誤訊息，說明失敗的原因。

     ![複製內容](/help/assets/copying-content.png)

1. (選用) 執行以下任一操作：

   1. 若要&#x200B;*保留*&#x200B;目標環境中f已排除的路徑，請勾選 **`Do not delete exclude paths from destination`**。此設定會使內容集中指定的已排除路徑保持不變。
   1. 若要&#x200B;*移除*&#x200B;目標環境中的已排除路徑，請取消勾選 **`Do not delete exclude paths from destination`**。此設定將刪除內容集中指定的已排除路徑。
   1. 若要將路徑的版本歷史記錄從來源環境複製到目標環境，請勾選「**複製版本**」。*不*&#x200B;複製版本歷史記錄時，內容複製程序會大幅加快。

1. 按一下「**複製**」。複製程序的狀態會反映在所選內容集的控制台中。

## 檢查內容副本的狀態 {#copy-activity}

您可以在「**複製內容活動**」頁面中監視複製程序的狀態。

**若要檢查內容副本的狀態：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 在頁面左上角，按一下![顯示選單圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側選單。

1. 在左側選單的「**服務**」下，按一下![歷史記錄圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg)「**複製內容活動**」。

   ![內容複製活動](/help/assets/copy-content-activity.png)

   內容復製程式可以有下列其中一種狀態：

   | 狀態 | 說明 |
   | --- | --- |
   | 進行中 | 內容復製程式正在進行中。 |
   | 已完成 | 內容復製程式已成功完成。 |
   | 失敗 | 內容復製程式失敗。 |

## 內容複製的限制 {#limitations}

* 無法將較低環境的內容複製到較高環境。
* 內容複製僅能於同一層級內執行。也就是「作者對作者」或「發佈對發佈」。
* 無法跨方案及跨區域進行內容複製。
* 唯有在來源和目標環境位於相同雲端提供者及區域時，才能對基於雲端資料存放區的拓撲執行內容複製。
* 無法於同一環境中執行並行的內容複製作業。
* 如果在目標或來源環境 (例如 CI/CD 管道) 上有任何作用中的作業正在執行中，則無法執行內容複製。
* 內容複製功能不應用作原地複製或鏡像工具，因為它無法追蹤來源上被移動或刪除的內容。
* 內容複製一旦開始，就無法暫停或取消。
* 內容複製會將資產及 Dynamic Media 中繼資料從高階環境複製到選取的低階環境。接著，必須在低階環境中透過 [DAM 流程資產工作流程](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/assets/using/assets-workflow)對已複製的資產進行再處理，才能使用各自的 Dynamic Media 設定。
* 不支援[啟用資產大小超過 2 GB 的 Dynamic Media 設定](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)。
* 目標環境的區域必須與來源環境的區域相同，或者是來源環境區域的子集。

## 內容副本的已知問題 {#known-issues}

{{content-copy-known-issues}}
