---
title: 管理管道
description: 了解如何管理現有管道，包括執行、編輯它們，並將其刪除。
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: d4a7d9ab72947b97b0dabb2f822ef268e4972685
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 59%

---


# 管理管道 {#managing-pipelines}

了解如何管理現有管道，包括執行、編輯它們，並將其刪除。

## 管道資訊卡 {#pipeline-card}

此&#x200B;**管道**&#x200B;卡位於 Cloud Manager 中的&#x200B;**方案總覽**&#x200B;頁面上，可讓您總覽您所有的管道及其目前狀態。

![Cloud Manager 中的管道卡](/help/assets/configure-pipelines/pipelines-card.png)

按一下每個管道旁的![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，您就可以執行下列動作：

* [執行管道](#running-pipelines)。
* [編輯管道](#editing-pipelines)。
* [刪除管道](#deleting-pipelines)。
* [檢視詳細資料](#view-details)。

在管道清單底部，有以下一般選項。

* **新增** - [新增生產管道](/help/using/production-pipelines.md)或是[新增非生產管道](/help/using/non-production-pipelines.md)。
* **顯示全部** - 將使用者帶到「**管道**」畫面，透過更詳細的表格檢視所有管道。
* **存取存放庫資訊** - 顯示要存取 Cloud Manager Git 存放庫所需的資訊。
* **了解更多** - 瀏覽至 CI/CD 管道文件資源。

## 管道頁面 {#pipelines}

**管道**&#x200B;頁面顯示所選方案所有管道的完整清單。此清單很實用，因其提供的資訊比[管道資訊卡](#pipeline-card)所提供的更完整。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從&#x200B;**方案概觀**&#x200B;頁面，按一下&#x200B;**管道**&#x200B;標籤，以切換到&#x200B;**管道**&#x200B;頁面。

1. 在這裡，您可以看到方案所有管道的清單，並啟動和停止管道執行，就像在&#x200B;**管道卡**&#x200B;中一樣。

按一下 `i` 圖示，便會顯示有關管道上次或目前執行的詳細資訊。

![管道執行詳細資訊](/help/assets/configure-pipelines/pipeline-status.png)

按一下&#x200B;**檢視詳細資訊**，即可前往[管道執行詳細資訊](#view-details)。

## 活動頁面 {#activity}

**活動**&#x200B;頁面顯示所選方案所有管道執行的完整清單。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從&#x200B;**方案概觀**&#x200B;頁面，按一下&#x200B;**活動**&#x200B;標籤，以切換到&#x200B;**活動**&#x200B;頁面。

1. 在這裡，您可以看到方案所有管道執行的清單，包括目前和歷史執行。

按一下 `i` 圖示，便會顯示有關所選管道執行的執行詳細資訊。

![管道執行詳細資訊](/help/assets/configure-pipelines/pipeline-activity.png)

按一下「**檢視詳細資訊**」查看[管道執行的詳細資訊](#view-details)。

## 執行管道 {#run-one-pipeline}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。
1. 瀏覽至「**管道**」卡片 (在「**方案概觀**」頁面)。
1. 按一下您執行的管道旁的![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，然後按一下&#x200B;**執行**。

   管道執行開始時，會於狀態欄顯示。

   您可以按一下![更多圖示，再按一下省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)並按一下&#x200B;**[檢視詳細資料](#view-details)**，以檢視執行的詳細資料。

   視管道型別而定，您可以按一下![更多圖示、省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)再按一下&#x200B;**取消**&#x200B;來取消執行。

## 執行多個管道 {#run-multiple-pipelines}

有了Cloud Manager，您可以同時執行多個管道，改善Adobe Managed Services (AMS)客戶的部署效率。 **執行選取的**&#x200B;功能可讓您選取多個管道並觸發它們一次執行。 它可減少個別執行管道的手動工作量，並最佳化建置和部署工作流程。

**若要執行多個管道：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。
1. 從左側功能表，按一下![工作流程圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **管道**。
1. 在&#x200B;**管道**&#x200B;頁面的表格中，選取您要執行管道旁的核取方塊。
如有必要，請按一下![篩選圖示、漏斗](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg) **篩選**，依名稱、環境、已部署的程式碼型別或這三個專案的組合來排序管道。
1. 在頁面的右上角附近，按一下&#x200B;**執行選取的專案(x)**。
1. 在&#x200B;**執行選取的管道(x)**&#x200B;對話方塊中，按一下&#x200B;**執行(x)**。

   **執行**&#x200B;按鈕反映了可繼續的管道數。 例如，您可能選取了四個管道，但其中一個已經在執行。 或者，連結至所選管道的環境已不存在。 在這種情況下，系統會進行相應的調整。 按鈕更新為「執行(3)」，表示三個管道可以繼續。

1. 管道開始執行，且已在&#x200B;**管道**&#x200B;清單中更新其狀態。

## 編輯管道 {#editing-pipelines}

您無法編輯正在執行的管道。

**若要編輯管道：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，瀏覽至&#x200B;**管道**&#x200B;卡。

1. 按一下您要編輯的管道旁的![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，然後按一下&#x200B;**編輯**。

1. 在&#x200B;**編輯生產管道**&#x200B;或&#x200B;**編輯非生產管道**&#x200B;對話方塊中，您可以編輯您在管道建立期間輸入的相同詳細資料。

   有關管道可用欄位及設定選項的詳細資訊，請參閱「[設定生產管道](/help/using/production-pipelines.md)」和「[設定非生產管道](/help/using/non-production-pipelines.md)」。

1. 完成時，按一下&#x200B;**更新**。

## 刪除管道 {#deleting-pipelines}

您無法刪除執行中的管道。

**若要刪除管道：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，瀏覽至&#x200B;**管道**&#x200B;卡。

1. 按一下您執行的管道旁的![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，然後按一下&#x200B;**刪除**。


## 檢視管道詳細資料 {#view-details}

您只能查看正在執行或已執行至少一次的管道的詳細資訊。

**若要檢視管道詳細資料：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，並選取適當的組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，瀏覽至&#x200B;**管道**&#x200B;卡。

1. 按一下您執行的管道旁的![更多圖示，省略符號](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，然後按一下&#x200B;**檢視詳細資料**。

1. 系統將會帶您前往執行中管道的詳細資訊頁面。

![管道詳情](/help/assets/configure-pipelines/pipeline-running-details.png)

從這裡，您可以查看管道各個步驟的狀態，並擷取建置記錄以進行診斷。如需詳細資訊，請參閱文件「[程式碼部署](/help/using/code-deployment.md)」。

管道執行中的所有步驟都會顯示，尚未開始的步驟會顯示為灰色。已完成的步驟會顯示其持續時間。

管道步驟完成後，會顯示摘要。

![步驟摘要](/help/assets/configure-pipelines/pipeline-step.png)

按一下&#x200B;**檢視詳細資訊**&#x200B;連結，以顯示&#x200B;**持續時間**&#x200B;部份。此區段包含該管道的平均持續時間，以該方案的歷史趨勢為根據。

![持續時間](/help/assets/configure-pipelines/duration.png)

如果您的管道包含&#x200B;**程式碼掃描**&#x200B;步驟而發生問題，您可以按一下&#x200B;**下載詳細資料**&#x200B;以檢視未通過的[程式碼品質測試](/help/using/code-quality-testing.md)清單。

![程式碼品質問題](assets/managing-pipelines-code-quality-issues.png)

CSV 檔案中有「**專案檔案位置**」欄，會指出違規程式碼的位置。此欄是專案相對路徑，而「**檔案位置**」欄是 Maven 產生。

![專案程式碼掃描問題詳細資訊](assets/managing-pipelines-code-quality-details.png)
