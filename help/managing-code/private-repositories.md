---
title: 在Cloud Manager中新增私有存放庫
description: 瞭解如何設定Cloud Manager以使用您自己的私人GitHub存放庫。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 84a6d8b7a44af124eb227999ad1cbd1fe14ab7ee
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 68%

---


# 在Cloud Manager中新增私有存放庫 {#private-repositories}

瞭解如何設定Cloud Manager以使用您自己的私人GitHub存放庫。

## 概觀 {#overview}

透過設定Cloud Manager搭配您自己的私人GitHub存放庫，您可以直接透過Cloud Manager在您的GitHub存放庫中驗證您的程式碼，而不需要一致地將您的程式碼與Adobe存放庫同步。

>[!NOTE]
>
>這是公開 GitHub 的專屬功能。不支援自行託管的 GitHub。

## 設定 {#configuration}

設定包括兩個主要步驟：

1. [新增存放庫](#add-repo)
1. [私人存放庫所有權驗證](#validate-ownership)

### 新增存放庫 {#add-repo}

1. 在 Cloud Manager 中，從&#x200B;**方案概觀**&#x200B;頁面，點選或按一下 **存放庫** 標籤以切換到&#x200B;**存放庫**&#x200B;頁面並按一下&#x200B;**新增存放庫**。

1. 在&#x200B;**新增存放庫**&#x200B;對話框，選取&#x200B;**私人存放庫**&#x200B;作為存放庫類型。

1. 提供存放庫的詳細資訊

   * **存放庫名稱** - 讓人易懂的名稱
   * **存放庫 URL** - 存放庫的 URL，必須以 `.git` 結尾
   * **說明** (選擇性) - 必要時提供存放庫更長的說明

   ![新增自己的存放庫](/help/assets/repositories/add-own-github.png)

1. 點選或按一下&#x200B;**儲存**。

>[!TIP]
>
>如需關於在 Cloud Manager 管理存放庫的詳細資訊，請參閱文件[Cloud Manager 存放庫](/help/managing-code/managing-repositories.md)。

### 私人存放庫所有權驗證 {#validate-ownership}

Cloud Manager 現在知道您的 GitHub 存放庫，但仍然需要存取它。若要授予存取權，您需要安裝 Adobe GitHub 應用程式並驗證您擁有指定的存放庫。

1. 新增您自己的存放庫，**私人存放庫所有權驗證**&#x200B;對話框隨即開啟。

   ![私人存放庫所有權驗證](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager 使用 GitHub 應用程式與您的存放庫安全地互動。
   * 您 GitHub 組織的擁有者必須安裝位於 `https://github.com/apps/cloud-manager-for-aem` 的應用程式，並授予存放庫的存取權。
   * 如需深入了解如何完成此操作，請參閱 GitHub 的文件。

1. 為了提高安全性，您必須在存放庫的預設分支中建立密碼檔案。點選或按一下&#x200B;**產生**。

1. 點選或按一下&#x200B;**確認**&#x200B;來確認產生密碼檔案。

   ![確認密碼產生](/help/assets/repositories/confirm-generation.png)

1. 回到&#x200B;**私人存放庫所有權驗證**&#x200B;視窗中，Cloud Manager 已在&#x200B;**密碼檔案內容**&#x200B;欄位產生私人檔案內容。複製該欄位中的內容。

   * 密碼檔案的內容只會顯示一次。如果您在關閉此視窗之前未複製內容，則需要重新產生密碼。

   ![複製密碼檔案內容](/help/assets/repositories/new-secret.png)

1. 在 GitHub 存放庫的預設分支中建立一個名為 `.well-known/adobe/cloud-manager-challenge` 的新檔案，並將密碼檔案內容貼到該檔案並儲存。

1. 當安裝好應用程式且密碼檔案位於存放庫後，您可以點選或按一下&#x200B;**私人存放庫所有權驗證**&#x200B;對話框中的&#x200B;**驗證**。

可以按任何順序安裝應用程式並建立密碼檔案。但是，必須先完成這兩個步驟才能進行驗證。

在驗證之前，存放庫將以紅色圖示列出，表示它尚未驗證且不能使用。

![未經驗證的存放庫](/help/assets/repositories/unvalidated-repo.png)

請注意，**類型**&#x200B;欄可以輕鬆識別 Adobe 提供的存放庫 (**Adobe**) 和您自己的 GitHub 存放庫 (**GitHub**)。

如果您需要日後返回存放庫以完成驗證，請在&#x200B;**存放庫**&#x200B;頁面，在代表剛新增之 GitHub 存放庫的列中，點選或按一下省略符號按鈕，然後從下拉式選單中選取&#x200B;**所有權驗證**。

## 搭配Cloud Manager使用私有存放庫 {#using}

在 Cloud Manager 中驗證 GitHub 存放庫後，整合即完成，您可以在 Cloud Manager 中使用該存放庫。

1. 當您建立提取要求時，GitHub 檢查將自動啟動。

   ![GitHub 檢查](/help/assets/repositories/github-checks.png)

1. 對於每個提取要求，[全端程式碼品質管道](/help/using/managing-pipelines.md)將自動建立。此管道在每次提取要求更新時啟動。

1. GitHub 檢查保持運作狀態，直到程式碼品質檢查完成。然後程式碼品質結果將傳播到 GitHub 檢查。

   ![GitHub 程式碼品質檢查](/help/assets/repositories/github-code-quality.png)

當提取要求關閉或合併時，建立的全端程式碼品質管道將自動刪除。

>[!TIP]
>
>檢視檔案 [GitHub檢查附註](github-annotations.md) 以取得有關執行提取請求檢查時透過GitHub提供的資訊的詳細資訊。

>[!TIP]
>
>您可以控制自動建立的管道，以驗證每個對私有存放庫的提取請求。 請參閱檔案 [適用於私人存放庫的GitHub檢查設定](github-check-config.md) 以取得詳細資訊。

## 將私有存放庫與管道相關聯 {#pipelines}

驗證的私人存放庫可以關聯至 [完整棧疊和前端管道。](/help/overview/ci-cd-pipelines.md)

>[!NOTE]
>
>私有存放庫不支援Web層和設定管道。

## 限制 {#limitations}

某些限制適用於搭配Cloud Manager使用私人存放庫。

* 您無法使用私有存放庫作為您管理的管道的直接存放庫來源。
* 您無法透過Cloud Manager的GitHub檢查暫停提取請求驗證。
   * 如果已在Cloud Manager中驗證GitHub存放庫，Cloud Manager一律會嘗試驗證為該存放庫建立的提取請求。
* 如果您的 GitHb 組織已移除 Adobe GitHub 應用程式，這將移除所有存放庫的提取要求驗證。
* 在生產完整棧疊管道上使用私人存放庫時，不會建立和推送Git標籤。
* 當新認可推送至所選分支時，使用專用存放庫和認可上建置觸發器的管道不會自動啟動。
* [成品重複使用功能](/help/getting-started/project-setup.md#build-artifact-reuse) 不適用於私人存放庫。