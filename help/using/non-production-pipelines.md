---
title: 新增非生產管道
description: 了解如何使用 Cloud Manager 建立和設定非生產管道以部署代碼。
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: ht
source-wordcount: '688'
ht-degree: 100%

---

# 新增非生產管道 {#configuring-non-production-pipelines}

了解如何使用 Cloud Manager 建立和設定非生產管道以部署程式碼。如果您想先了解有關在 Cloud Manager 中管道如何運作的更多概念性概觀，請參閱[CI/CD 管道](/help/overview/ci-cd-pipelines.md)。

## 概觀 {#overview}

使用&#x200B;**管道**&#x200B;圖磚 (在 [!UICONTROL Cloud Manager] 中)，**部署管理員**&#x200B;可建立兩個不同類型的管道。

* **生產管道** - 生產管道是一個專門建置的管道，由一系列精心安排的步驟組成，以將原始程式碼一路帶入生產環境。
* **非生產管道** - 非生產管道主要用於執行程式碼品質掃描或將原始程式碼部署到開發環境中。

本文件會專注於非生產管道。如需有關如何設定生產管道的詳細資訊，請參閱文件[設定生產管道](/help/using/production-pipelines.md)。

有兩種類型的非生產管道：

* **程式碼品質管道** - 這些管道會對 Git 分支中的程式碼執行程式碼品質掃描，並執行建置和程式碼品質步驟。
* **部署管道** - 除了執行程式碼品質管道之類的建置和程式碼品質步驟，這些管道還會將程式碼部署到非生產環境。

>[!NOTE]
>
>與管道相關的 Git 存放庫必須具有至少一個分支，且已完成[方案設定](/help/getting-started/program-setup.md)，才能進行管道設定。如欲了解如何在 Cloud Manager 中新增和管理存放庫，請參閱 [Cloud Manager 存放庫](/help/managing-code/managing-repositories.md)。

## 新增一個全新非生產管道 {#add-non-production-pipeline}

設定好方案並擁有至少一個使用 Cloud Manager UI 的環境後，您就可以依照以下步驟著手新增非生產管道了。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從 Cloud Manager 首頁畫面存取管道卡。 按一下「**新增**」，然後選取「**新增非生產管道**」。

   ![新增非生產管道](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. 在&#x200B;**設定**&#x200B;索引標籤 (在&#x200B;**新增非生產管道**&#x200B;對話框中) 上，選取您要建立的管道類型：**程式碼品質管道**&#x200B;或&#x200B;**部署管道**。

   ![選擇管道類型](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. 在&#x200B;**非生產管道名稱**&#x200B;欄位中為您的管道提供說明。

1. 如果您選擇新增&#x200B;**部署管道**，請從&#x200B;**合格的部署環境**&#x200B;下拉式選單中選取目標部署環境。

1. 提供管道應擷取程式碼的存放庫。

   * **存放庫** - 定義管道應該從哪個 Git 存放庫擷取程式碼。
   * **Git 分支** - 定義特定的管道應該從 Git 中的哪個分支擷取程式碼。

1. 定義您的部署選項。

   1. 在&#x200B;**部署觸發程序**&#x200B;下，可定義哪種事件會啟動管道。

      * **手動** - 讓您能手動啟動管道。
      * **在 Git 變更時** - 當認可版本新增到所設定的 Git 分支時啟動管道。使用此選項，您仍然可以在必要時手動啟動管道。

   1. 對於部署管道，在「**重要的量度失敗行為**」下，定義在任何品質閘道中遇到重要失敗時的管道行為。

      * **每次都詢問** - 預設設定，要求對任何重要失敗進行手動介入。
      * **立即失敗** - 每當重要失敗發生時，便取消管道。這基本上是模擬使用者手動拒絕每次失敗。
      * **立即持續** - 當重要失敗發生時，管道皆自動繼續。這基本上是模擬使用者手動核准每次失敗。

   1. **Dispatcher 設定** - **部署管理員**&#x200B;角色可設定一組內容路徑，而這組路徑在管道執行時會失效或從 AEM Dispatcher 快取中清除。在部署任何內容套件後，這些快取動作會視為部署管道步驟一部分來執行。這些設定使用標準的 AEM Dispatcher 行為。進行設定：

      1. **路徑**&#x200B;下會提供內容路徑。
      1. 在&#x200B;**類型**&#x200B;下，選取在該路徑將採取的操作。

         * **排清** - 執行快取刪除。
         * **失效** - 執行快取失效，類似於將內容從製作執行個體啟動至發佈執行個體的情況。

      1. 按一下&#x200B;**新增路徑**，即可新增您指定的路徑。您在每個環境最多可新增 100 個路徑。

1. 按一下「**儲存**」。

## 後續步驟 {#the-next-steps}

管道設定後，可以部署您的程式碼。請參閱「[程式碼部署](/help/using/code-deployment.md)」了解更多詳細資訊。

## 教學課程影片 {#video-tutorial}

本影片將概述管道建立流程，而本文件中有詳細說明。

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
