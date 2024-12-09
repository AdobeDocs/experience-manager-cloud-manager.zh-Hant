---
title: 環境一致性的內容複製
description: Cloud Manager中的內容複製可讓使用者隨選從AdobeManaged Services託管的Adobe Experience Manager 6.x生產環境複製可變內容，以便用於測試的較低環境。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 228006b424504306e916014bbe8543dc41ba43b5
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 33%

---


# 內容復本，維持環境一致性 {#content-copy}

Cloud Manager中的內容複製可讓使用者隨選從AdobeManaged Services託管的Adobe Experience Manager 6.x生產環境複製可變內容，以便用於測試的較低環境。

## 關於內容複製 {#introduction}

目前的真實資料對於測試、驗證和使用者接受度很有價值。內容複製可讓您將內容從生產AMS代管的AEM 6.x環境複製到中繼或開發環境。 此工作流程支援各種測試場景。

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

若要使用內容複製功能，必須將使用者指派給來源和目標環境中的&#x200B;**部署管理員**&#x200B;角色。

## 建立內容集 {#create-content-set}

在複製任何內容之前，必須定義一個內容集。定義後，內容集就可以重複使用來複製內容。請依照下列步驟，建立新的內容集。

**若要建立內容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 在頁面的左上角，按一下[顯示]功能表圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側功能表。![

1. 從左側功能表的&#x200B;**服務**&#x200B;頁面下方，按一下![方塊圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **內容集**。

1. 在頁面的右上角附近，按一下&#x200B;**新增內容集**。

   ![內容集](/help/assets/content-sets.png)

1. 在&#x200B;**`Add Content Set`**&#x200B;對話方塊的&#x200B;**詳細資料**&#x200B;索引標籤的&#x200B;**名稱**&#x200B;和&#x200B;**描述**&#x200B;欄位中，輸入內容集的名稱和選擇性描述，然後按一下&#x200B;**繼續**。

   ![內容詳細資料](/help/assets/add-content-set-details.png)

1. 在&#x200B;**內容路徑**&#x200B;索引標籤的&#x200B;**路徑**&#x200B;文字欄位中，指定可變更且應包含在內容集中的內容路徑。

   只有以`/content`、`/conf`、`/etc`、`/var/workflow/models`或`/var/commerce`開頭的路徑才符合納入的條件。

1. 按一下&#x200B;**![資料夾新增圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg)新增路徑**&#x200B;以新增（或包含）內容集的路徑。

1. （選擇性）如有需要，重複前兩個步驟，視需要新增額外路徑（最多50個）。 否則，請繼續進行下一個步驟。

   ![新增路徑至內容集](/help/assets/add-content-set-paths.png)

1. （選用）若要縮小內容集的範圍，您可以選擇在應排除的包含內容路徑中指定子路徑。

   1. 在您要限制的內含內容路徑右側，按一下![資料夾刪除圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)。
   1. 在文字欄位中，輸入對話方塊中所見根路徑的相對路徑。
   1. 按一下![資料夾刪除圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **排除路徑**。
   1. 如有必要，請重複步驟i到iii。 以上以增加更多排除路徑；沒有限制。 否則，請繼續進行下一個步驟。

   ![排除路徑](/help/assets/add-content-set-paths-excluded.png)

1. （可選）執行下列任一項作業：

   1. 按一下排除的子路徑右邊的![跨大小500圖示](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg)以刪除它。
   1. 按一下包含的內容路徑右邊的![更多圖示](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然後按一下&#x200B;**編輯**&#x200B;或&#x200B;**刪除**。

   ![正在編輯路徑清單](/help/assets/add-content-set-excluded-paths.png)

1. 按一下「**建立**」。您現在可以使用內容集在環境之間複製內容。

## 編輯或刪除內容集 {#edit-content-set}

編輯內容集時，您可能需要展開已設定的路徑以顯示排除的子路徑。

**若要編輯或刪除內容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 在頁面的左上角，按一下[顯示]功能表圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側功能表。![

1. 從左側功能表的&#x200B;**服務**&#x200B;下方，按一下![方塊圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **內容集**。

1. 在&#x200B;**內容集**&#x200B;頁面的表格中，按一下包含的內容路徑右邊的![更多圖示](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然後按一下&#x200B;**編輯**&#x200B;或&#x200B;**刪除**。

![編輯內容集](/help/assets/edit-content-set.png)


## 複製內容 {#copy-content}

建立內容集後，您就可以用它來複製內容。

如果符合下列任一條件，環境可能無法供選取：

* 使用者缺少必要的許可權。
* 環境中目前正在執行管道或內容複製操作。

**複製內容：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 在頁面的左上角，按一下[顯示]功能表圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側功能表。![

1. 從左側功能表的&#x200B;**服務**&#x200B;下方，按一下![方塊圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **內容集**。

1. 在&#x200B;**內容集**&#x200B;頁面的表格中，在您要複製的包含內容路徑右側，按一下![更多圖示](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然後按一下&#x200B;**複製內容**。

   ![內容複製](/help/assets/copy-content.png)

1. 在&#x200B;**複製內容**&#x200B;對話方塊中，選取內容複製動作的&#x200B;**Source**&#x200B;環境和&#x200B;**目的地**&#x200B;環境。

   * 目的地環境中的區域必須是來源環境中的區域子集。
   * 在執行內容複製動作之前，會檢查相容性問題。 當您選取&#x200B;**目的地**&#x200B;環境時，系統會自動驗證來源和目的地環境。 如果驗證失敗，程式將停止，並在說明失敗原因的對話方塊中顯示錯誤訊息。

     ![正在複製內容](/help/assets/copying-content.png)

1. （可選）執行下列任一項作業：

   1. 若要&#x200B;*保留*&#x200B;目的地環境中排除的路徑，請核取&#x200B;**`Do not delete exclude paths from destination`**。 此設定會保持內容集中指定的排除路徑不變。
   1. 若要&#x200B;*移除*&#x200B;目的地環境中排除的路徑，請取消核取&#x200B;**`Do not delete exclude paths from destination`**。 此設定會刪除內容集中指定的排除路徑。
   1. 若要從來源環境複製路徑的版本記錄到目的地環境，請核取&#x200B;**復製版本**。 當版本歷程記錄為&#x200B;*而非*&#x200B;時，內容復製程式會快速許多。



1. 按一下&#x200B;**複製**。 複製過程的狀態反映在所選內容集的控制台中。

## 監視內容複製狀態 {#copy-activity}

您可以在「**複製內容活動**」頁面中監視複製過程的狀態。

**監視內容副本狀態：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 在頁面的左上角，按一下[顯示]功能表圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以開啟左側功能表。![

1. 從左側功能表的&#x200B;**服務**&#x200B;下方，按一下![歷程記錄圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **複製內容活動**。

   ![內容複製活動](/help/assets/copy-content-activity.png)

   內容復製程式可以有下列其中一種狀態：

   | 狀態 | 說明 |
   | --- | --- |
   | 進行中 | 內容復製作業正在進行中。 |
   | 完成 | 內容復製作業已順利完成。 |
   | 已失敗 | 內容復製作業失敗。 |


## 內容副本的限制 {#limitations}

* 無法將較低環境的內容複製到較高環境。
* 內容複製僅能於同一層級內執行。也就是「作者對作者」或「發佈對發佈」。
* 無法跨方案及跨區域進行內容複製。
* 唯有在來源和目標環境位於相同雲端提供者及區域時，才能對基於雲端資料存放區的拓撲執行內容複製。
* 無法於同一環境中執行並行的內容複製作業。
* 如果在目標或來源環境 (例如 CI/CD 管道) 上有任何作用中的作業正在執行中，則無法執行內容複製。
* 內容副本不應作為複製或映象工具使用，因為它無法追蹤來源上已移動或刪除的內容。
* 內容複製一旦開始就不能暫停或取消。
* 內容複製會將資產和Dynamic Media中繼資料從較高的環境複製到選取的低層環境。 然後需要在較低的環境中透過 [DAM 流程資產工作流程](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/assets/using/assets-workflow)對已複製的資產進行再處理，才能使用各自的 Dynamic Media 設定。
* 不支援[啟用之資產大小超過 2 GB 的 Dynamic Media 設定](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)。
* 目標環境的區域必須與來源環境的區域相同，或是來源環境區域的子集。

## 已知問題 {#known-issues}

{{content-copy-known-issues}}
