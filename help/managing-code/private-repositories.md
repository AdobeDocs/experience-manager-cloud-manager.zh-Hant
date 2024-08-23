---
title: 在Cloud Manager中新增私人存放庫
description: 了解如何設定 Cloud Manager 以搭配使用您自己的私人 GitHub 存放庫。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 45%

---


# 在Cloud Manager中新增私人存放庫 {#private-repositories}

了解如何設定 Cloud Manager 以搭配使用您自己的私人 GitHub 存放庫。

## 概觀 {#overview}

使用您的私人GitHub存放庫設定Cloud Manager，可讓您直接在GitHub中驗證程式碼，而不需經常與Adobe存放庫同步。

>[!NOTE]
>
>這是公開 GitHub 的專屬功能。不支援自行託管的 GitHub。

## 設定 {#configuration}

設定包括兩個主要步驟：

1. [新增存放庫](#add-repo)
1. [私人存放庫所有權驗證](#validate-ownership)

### 新增存放庫 {#add-repo}

1. 在 Cloud Manager 中，從&#x200B;**方案概觀**&#x200B;頁面，按一下 **存放庫** 標籤以切換到&#x200B;**存放庫**&#x200B;頁面，並按一下&#x200B;**新增存放庫**。

1. 在&#x200B;**新增存放庫**&#x200B;對話方塊中，選取&#x200B;**私人存放庫**&#x200B;作為存放庫型別。

1. 提供存放庫的詳細資訊

   * **存放庫名稱** - 讓人易懂的名稱
   * **存放庫 URL** - 存放庫的 URL，必須以 `.git` 結尾
   * **說明** (選擇性) - 必要時提供存放庫更長的說明

   ![新增自己的存放庫](/help/assets/repositories/add-own-github.png)

1. 按一下&#x200B;**儲存**。

>[!TIP]
>
>如需在Cloud Manager中管理存放庫的詳細資訊，請參閱[Cloud Manager存放庫](/help/managing-code/managing-repositories.md)。

### 私人存放庫所有權驗證 {#validate-ownership}

Cloud Manager 現在知道您的 GitHub 存放庫，但仍然需要存取它。若要授予存取權，您需要安裝 Adobe GitHub 應用程式並驗證您擁有指定的存放庫。

1. 新增您自己的存放庫後，會顯示&#x200B;**私人存放庫所有權驗證**&#x200B;對話方塊。

   ![私人存放庫所有權驗證](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager使用GitHub應用程式與存放庫安全地互動。

   您GitHub組織的所有者必須安裝位於`https://github.com/apps/cloud-manager-for-aem`的應用程式並授與存放庫的存取權。 如需詳細資訊，請參閱GitHub的檔案。

1. 若要增強安全性，請在存放庫的預設分支中建立機密檔案。 按一下&#x200B;**產生**。

1. 按一下&#x200B;**確認**，確認產生密碼檔案。

   ![確認密碼產生](/help/assets/repositories/confirm-generation.png)

1. 返回&#x200B;**私人存放庫所有權驗證**&#x200B;對話方塊，Cloud Manager已在&#x200B;**機密檔案內容**&#x200B;欄位中產生內容。 複製該欄位中的內容。

   機密檔案的內容只會顯示一次。 如果您在關閉此視窗之前沒有複製內容，則必須重新產生密碼。

   ![複製密碼檔案內容](/help/assets/repositories/new-secret.png)

1. 在 GitHub 存放庫的預設分支中建立一個名為 `.well-known/adobe/cloud-manager-challenge` 的新檔案，並將密碼檔案內容貼到該檔案並儲存。

1. 安裝應用程式且存放庫中存在密碼檔之後，您可以在&#x200B;**私人存放庫所有權驗證**&#x200B;對話方塊中按一下&#x200B;**驗證**。

您可以安裝應用程式，並依任何順序產生機密檔案。 不過，必須先完成這兩個步驟才能進行驗證。

在驗證之前，存放庫將以紅色圖示列出，表示它尚未驗證且尚無法使用。

![未經驗證的存放庫](/help/assets/repositories/unvalidated-repo.png)

請注意，**類型**&#x200B;欄可以輕鬆識別 Adobe 提供的存放庫 (**Adobe**) 和您自己的 GitHub 存放庫 (**GitHub**)。

若要稍後返回存放庫並完成驗證，請移至&#x200B;**存放庫**&#x200B;頁面。 按一下您新增的GitHub存放庫旁邊的省略符號按鈕，然後從下拉式選單中選取「**所有權驗證**」。

## 搭配Cloud Manager使用私人存放庫 {#using}

在Cloud Manager中驗證GitHub存放庫後，整合即已完成，您可以將存放庫與Cloud Manager搭配使用。

1. 當您建立提取請求時，GitHub檢查會自動啟動。

   ![GitHub 檢查](/help/assets/repositories/github-checks.png)

1. 對於每個提取請求，都會自動建立[完整棧疊計畫碼品質管道](/help/using/managing-pipelines.md)。 此管道在每次提取要求更新時啟動。

1. GitHub檢查會維持在執行狀態，直到程式碼品質檢查完成為止。 然後程式碼品質結果會傳播至GitHub檢查。

   ![GitHub 程式碼品質檢查](/help/assets/repositories/github-code-quality.png)

當提取要求關閉或合併時，建立的全端程式碼品質管道將自動刪除。

>[!TIP]
>
>有關執行提取請求檢查時透過 GitHub 提供的資訊詳情，請參閱文件「[GitHub 檢查附註](github-annotations.md)」。

>[!TIP]
>
>您可以控制自動建立的管道以驗證對私人存放庫的每個提取請求。請參閱[私人存放庫的 GitHub 檢查設定](github-check-config.md)，了解更多資訊。

## 將私有存放庫與管道相關聯 {#pipelines}

經驗證的私人存放庫可以與[全端管道](/help/overview/ci-cd-pipelines.md)建立關聯。

## 限制 {#limitations}

將私人存放庫與 Cloud Manager 搭配使用時會有某些限制。

* 您無法使用Cloud Manager的GitHub檢查來暫停提取請求驗證。 如果已在Cloud Manager中驗證GitHub存放庫，Cloud Manager會嘗試驗證為該存放庫建立的提取請求。
* 如果AdobeGitHub應用程式已從您的GitHb組織移除，此動作會移除所有存放庫的提取請求驗證功能。
* 在生產完整棧疊管道上使用私人存放庫時，不會建立和推送Git標籤。
* 當新提交被推送到所選分支時，使用私人存放庫和提交建置觸發器的管道不會自動啟動。
* [成品重複使用功能](/help/getting-started/project-setup.md#build-artifact-reuse)不適用於私人存放庫。
