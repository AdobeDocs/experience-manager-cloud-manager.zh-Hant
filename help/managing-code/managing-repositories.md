---
title: 管理 Cloud Manager 中的存放庫
description: 瞭解如何在Cloud Manager中檢視、新增和刪除您的Git存放庫。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: ee84c682b6bd2b9144b3f75d544dea33a5ad944b
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 22%

---


# 在Cloud Manager中管理存放庫 {#cloud-manager-repos}

瞭解如何在Cloud Manager中檢視、新增和刪除Git存放庫。

## 概觀 {#overview}

Cloud Manager中的存放庫是用來透過Git儲存和管理您的專案計畫碼。 對於您新增的每個&#x200B;*程式*，都會自動建立Adobe管理的存放庫。

此外，您可以選擇建立更多Adobe管理的存放庫，或新增您自己的專用存放庫。 可以在&#x200B;**存放庫**&#x200B;頁面上檢視連結到您方案的所有存放庫。

新增或編輯管道時，也可以選擇在Cloud Manager中建立的存放庫。 如需設定管道的詳細資訊，請參閱[CI-CD管道](/help/overview/ci-cd-pipelines.md)。

每個管道都連結到主要存放庫或分支。 不過，透過[Git子模組支援](/help/managing-code/git-submodules.md)，可以在建置程式期間包含多個次要分支。

## 檢視存放庫頁面 {#repositories-window}

在&#x200B;**存放庫**&#x200B;頁面上，您可以檢視所選存放庫的詳細資料。 此資訊包括使用的存放庫型別。 如果儲存庫標示為&#x200B;**Adobe**，表示它是Adobe管理的儲存庫。 如果標示為&#x200B;**GitHub**，則表示它是您管理的私人GitHub存放庫。 此外，頁面還提供詳細資訊，例如建立存放庫的時間以及與之關聯的管道。

若要對選取的存放庫執行動作，您可以按一下存放庫，並使用![更多圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)開啟下拉式功能表。 對於Adobe管理的存放庫，您可以&#x200B;**[檢查分支/建立專案](#check-branches)**。

![存放庫動作](assets/repository-actions.png)
*存放庫頁面上的下拉式功能表。*

下拉式功能表上的其他可用動作包括&#x200B;**[複製存放庫URL](#copy-url)**、**[檢視和更新](#view-update)**&#x200B;以及&#x200B;**[刪除](#delete)**&#x200B;存放庫。

**若要檢視存放庫頁面：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，按一下側邊功能表上的![資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **存放庫**。

1. **存放庫**&#x200B;頁面會顯示與您所選方案關聯的所有存放庫。

   ![存放庫頁面](assets/repositories.png)
   *Cloud Manager中的存放庫頁面。*


## 新增存放庫 {#adding-repositories}

使用者必須具有&#x200B;**部署管理員**&#x200B;或&#x200B;**企業所有者**&#x200B;角色才能新增存放庫。

在&#x200B;**存放庫**&#x200B;頁面的右上角，按一下&#x200B;**新增存放庫**

![新增存放庫對話方塊。](assets/repository-add.png)
*新增存放庫對話方塊。*

Cloud Manager支援兩種型別的存放庫：Adobe管理的存放庫(**Adobe存放庫**)和自行管理的存放庫（**私人存放庫**）。 視您選擇新增的存放庫型別而定，設定所需的欄位會有所不同。 如需詳細資訊，請參閱下列內容：

* [在 Cloud Manager 中新增 Adobe 存放庫](/help/managing-code/adobe-repositories.md)
* [在 Cloud Manager 中新增私人存放庫](/help/managing-code/private-repositories.md)

任何指定公司或 IMS 組織中的所有計畫都存在 300 個存放庫的限制。

## 存取存放庫資訊 {#repo-info}

在「**存放庫**」視窗中查看存放庫時，您可以按一下工作列的「**存取存放庫資訊**」按鈕，以檢視有關如何以程式設計方式存取 Adobe 託管的存放庫詳細資訊。

![存放庫資訊](assets/repository-access-repo-info2.png)

「**存放庫資訊**」視窗會開啟，並且內含詳細資訊。有關存取存放庫資訊的更多資訊，請參閱文件「[存取存放庫資訊](/help/managing-code/accessing-repositories.md)」。

## 檢查分支/建立專案 {#check-branches}

在&#x200B;**AEM Cloud Manager**&#x200B;中，**檢查分支/建立專案**&#x200B;動作有兩個用途，視存放庫的目前狀態而定。

* 如果是新建立的存放庫，此動作會使用[AEM專案原型](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/developing/archetype/overview)產生範例專案。
* 如果範例專案已建立在存放庫中，該動作會檢查存放庫及其分支的狀態，提供範例專案是否已存在的意見回饋。

  ![檢查分支動作](assets/check-branches.png)

## 複製存放庫 URL {#copy-url}

**複製存放庫URL**&#x200B;動作會將&#x200B;**存放庫**&#x200B;頁面中選取之存放庫的URL複製到剪貼簿，以供其他位置使用。

## 檢視和更新存放庫 {#view-update}

**檢視和更新**&#x200B;動作會開啟&#x200B;**更新存放庫**&#x200B;對話方塊，您可以在此檢視存放庫的&#x200B;**名稱**&#x200B;和&#x200B;**存放庫URL預覽**。 此外，它可讓您更新存放庫的&#x200B;**描述**。

![查看和更新&#x200B;&#x200B;存放庫資訊](assets/repository-view-update.png)

## 刪除存放庫 {#delete}

「**刪除**」操作會從您的專案中刪除存放庫。如果存放庫與管道有關聯，則無法刪除。

![正在刪除存放庫](assets/delete.png)

在 Cloud Manager 中刪除存放庫時，它會被標記為已刪除；使用者不能再存取。但是，它會保留在系統中以利日後還原。

如果您嘗試在刪除具有相同名稱的存放庫後建立新的存放庫，您會收到以下錯誤訊息：

`An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

如果您收到此錯誤訊息，請聯絡Adobe支援。 它們可協助您重新命名已刪除的存放庫或為新存放庫選擇不同的名稱。
