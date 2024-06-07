---
title: 在Cloud Manager中管理存放庫
description: 瞭解如何在Cloud Manager中建立、檢視和編輯Git存放庫。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: b15ef71ae24f51811798d2d25c8f75320e21c01f
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 27%

---


# Cloud Manager 存放庫 {#cloud-manager-repos}

瞭解如何在Cloud Manager中建立、檢視和編輯Git存放庫。

## 概觀 {#overview}

存放庫是用來透過Git儲存和管理您的專案計畫碼。 您在Cloud Manager中建立的每個計畫都有為其建立的Adobe管理的存放庫。

您可以選擇建立其他Adobe管理的存放庫，並新增您自己的專用存放庫。 您可在「 」中檢視與您的方案相關聯的所有存放庫 **存放庫** 視窗。

在新增或編輯管道時，您也可以選擇在 Cloud Manager 中建立的存放庫。如需更多資訊，請參閱 [CI-CD 管道](/help/overview/ci-cd-pipelines.md)。

任何指定管道都有一個主要存放庫或一個分支。替換為 [Git子模組支援，](git-submodules.md) 建置時可以包含許多次要分支。

## 存放庫視窗 {#repositories-window}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從 **計畫總覽** 頁面，選取 **存放庫** 標籤以切換至 **存放庫** 頁面。

1. 此 **存放庫** 視窗會顯示與您的方案相關聯的所有存放庫。

   ![存放庫視窗](assets/repositories.png)

此 **存放庫** 視窗提供有關存放庫的詳細資訊：

* 存放庫型別
   * **Adobe** 表示Adobe管理的存放庫
   * **私人** 表示您管理的GitHub存放庫
* 建立時間
* 與存放庫關聯的管道

您可以在視窗中選取存放庫，然後按一下省略符號按鈕，對選取的存放庫執行動作。

* **[檢查分支/建立專案](#check-branches)** (僅適用於Adobe存放庫)
* **[複製存放庫URL](#copy-url)**
* **[檢視和更新](#view-update)**
* **[刪除](#delete)**

![存放庫動作](assets/repository-actions.png)

## 新增存放庫 {#adding-repositories}

點選或按一下 **新增存放庫** 中的按鈕 **存放庫** 視窗啟動 **新增存放庫** 精靈。

![新增存放庫精靈](assets/add-repository-wizard.png)

Cloud Manager支援兩個由Adobe(**Adobe存放庫**)以及您自己的自行管理存放庫(**私人存放庫**)。 視您選擇新增的存放庫型別而定，必填欄位會有所不同。 如需更多詳細資訊，請參閱下列檔案。

* [在Cloud Manager中新增Adobe存放庫](adobe-repositories.md)
* [在Cloud Manager中新增私有存放庫](private-repositories.md)

>[!NOTE]
>
>* 使用者必須具備&#x200B;**部署管理員**&#x200B;或&#x200B;**業務負責人**&#x200B;角色才能新增存放庫。
>* 任何指定公司或 IMS 組織中的所有計畫都存在 300 個存放庫的限制。

## 存取存放庫資訊 {#repo-info}

在中檢視您的存放庫時 **存放庫** 視窗中，您可以點選或按一下「 」，以程式設計方式檢視Adobe管理的存放庫的詳細資訊 **存取存放庫資訊** 按鈕。

![存放庫資訊](assets/access-repo-info.png)

此 **存放庫資訊** 視窗會開啟，其中包含詳細資訊。 如需有關存取存放庫資訊的詳細資訊，請參閱檔案 [存取存放庫資訊。](accessing-repositories.md)

## 檢查分支 {#check-branches}

## 複製存放庫 URL {#copy-url}

此 **複製存放庫URL** 動作會複製所選存放庫的URL **存放庫** 視窗到剪貼簿以用於其他地方。

## 檢視和更新 {#view-update}

此 **檢視和更新** 動作開啟 **更新存放庫** 對話方塊。 使用它可以檢視 **名稱** 和 **存放庫URL預覽** 以及更新 **說明** 存放庫的。

![檢視和更新存放庫資訊](assets/update-repository.png)

## 刪除 {#delete}

此 **刪除** 動作會將存放庫從專案中移除。 如果存放庫與管道相關聯，則無法刪除存放庫。

![刪除](assets/delete.png)

請注意，在 Cloud Manager 刪除存放庫時，它會被標記為已刪除，使用者無法再存取，但它會保留在系統中以用於恢復目的。

如果您在刪除同名的存放庫後嘗試建立新的存放庫，您會收到錯誤訊息 `An error has occurred while trying to create repository. Please contact your CSE or Adobe Support.`

如果您收到此錯誤訊息，請聯絡 Adobe 支援，如此他們可協助重新命名已刪除的存放庫，或為新的存放庫選擇不同的名稱。