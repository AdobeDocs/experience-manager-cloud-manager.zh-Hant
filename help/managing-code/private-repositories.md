---
title: 在 Cloud Manager 中新增私人存放庫
description: 了解如何設定 Cloud Manager 與您自己的私人 GitHub 存放庫搭配使用。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 5090d7ee9a6742d71122acda9901d074bc254305
workflow-type: ht
source-wordcount: '818'
ht-degree: 100%

---


# 在 Cloud Manager 中新增私人存放庫 {#private-repositories}

了解如何設定 Cloud Manager 以搭配使用您自己的私人 GitHub 存放庫。

## 概觀 {#overview}

使用私人 GitHub 存放庫設定 Cloud Manager，讓您可以直接在 GitHub 內驗證程式碼，而無需頻繁與 Adobe 存放庫進行同步。

>[!NOTE]
>
>這是公開 GitHub 的專屬功能。不支援自行託管的 GitHub。

## 設定 {#configuration}

設定包括兩個主要步驟：

1. [新增存放庫](#add-repo)
1. [私人存放庫所有權驗證](#validate-ownership)



### 新增存放庫 {#add-repo}

1. 在 Cloud Manager 中，於「**方案概觀**」頁面按一下「**存放庫**」標籤，切換到「**存放庫**」頁面，再按一下「**新增存放庫**」。

1. 在「**新增存放庫**」對話框內，選取「**私人存放庫**」作為存放庫類型。

1. 提供存放庫的詳細資訊

   * **存放庫名稱** - 讓人易懂的名稱
   * **存放庫 URL** - 存放庫的 URL，必須以 `.git` 結尾
   * **說明** (選擇性) - 必要時提供存放庫更長的說明

   ![新增自己的存放庫](/help/assets/repositories/add-own-github.png)

1. 按一下&#x200B;**儲存**。

>[!TIP]
>
>如需關於在 Cloud Manager 管理存放庫的詳細資訊，請參閱「[Cloud Manager 存放庫](/help/managing-code/managing-repositories.md)」。



### 驗證私人存放庫的擁有權 {#validate-ownership}

Cloud Manager 現在知道您的 GitHub 存放庫，但仍然需要存取它。若要授予存取權，您需要安裝 Adobe GitHub 應用程式並驗證您擁有指定的存放庫。

1. 新增您自己的存放庫後，便會顯示「**私人存放庫所有權驗證**」對話框。

   ![私人存放庫所有權驗證](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager 使用 GitHub 應用程式安全地與您的存放庫互動。

   您 GitHub 組織的所有者必須安裝位於 `https://github.com/apps/cloud-manager-for-aem` 的應用程式，並授予存放庫的存取權。詳情請參閱 GitHub 的文件。

1. 為了提高安全性，請在存放庫的預設分支中建立密碼檔案。按一下&#x200B;**產生**。

1. 按一下&#x200B;**確認**，確認產生密碼檔案。

   ![確認密碼產生](/help/assets/repositories/confirm-generation.png)

1. 回到「**私人存放庫所有權驗證**」對話框內，Cloud Manager 已產生「**密碼檔案內容**」欄位中的內容。複製該欄位中的內容。

   密碼檔案的內容只會顯示一次。如果您在關閉此視窗之前未複製內容，則必須重新產生密碼。

   ![複製密碼檔案內容](/help/assets/repositories/new-secret.png)

1. 在 GitHub 存放庫的預設分支中建立一個名為 `.well-known/adobe/cloud-manager-challenge` 的新檔案，並將密碼檔案內容貼到該檔案並儲存。

1. 安裝好應用程式且存放庫中已有密碼檔案之後，您可以按一下「**驗證**」(在「**私人存放庫所有權驗證**」對話框中)。

可以依照任何順序安裝應用程式及產生密碼檔案。不過，必須先完成這兩個步驟才能進行驗證。

在驗證之前，存放庫會以紅色圖示列出，表示其尚未驗證且不能使用。

![未經驗證的存放庫](/help/assets/repositories/unvalidated-repo.png)

請注意，**類型**&#x200B;欄可以輕鬆識別 Adobe 提供的存放庫 (**Adobe**) 和您自己的 GitHub 存放庫 (**GitHub**)。

若稍後要返回存放庫並完成驗證，請前往「**存放庫**」頁面。按一下您新增之 GitHub 存放庫旁的省略符號按鈕，然後從下拉式選單中選取「**所有權驗證**」。



## 將私人存放庫與 Cloud Manager 搭配使用 {#using}

在 Cloud Manager 中驗證完 GitHub 存放庫後，整合即完成，您便可以在 Cloud Manager 中使用該存放庫。

**若要透過 Cloud Manager 使用私人存放庫：**

1. 當您建立提取請求時，會自動啟動 GitHub 檢查。

   ![GitHub 檢查](/help/assets/repositories/github-checks.png)

1. 對於每個提取請求，皆會自動建立[全端程式碼品質管道](/help/using/managing-pipelines.md)。此管道會在每次提取請求更新時啟動。

1. GitHub 檢查會維持運作狀態，直到程式碼品質檢查完成。程式碼品質結果隨後會傳播至 GitHub 檢查。

   ![GitHub 程式碼品質檢查](/help/assets/repositories/github-code-quality.png)

當提取要求關閉或合併時，建立的全端程式碼品質管道將自動刪除。

>[!TIP]
>
>有關執行提取請求檢查時透過 GitHub 提供的資訊詳情，請參閱文件「[GitHub 檢查附註](github-annotations.md)」。

>[!TIP]
>
>您可以控制自動建立的管道以驗證對私人存放庫的每個提取請求。請參閱[私人存放庫的 GitHub 檢查設定](github-check-config.md)，了解更多資訊。



## 將私人存放庫與管道建立關聯 {#pipelines}

經過驗證的私人存放庫可以與[全端和前端管道相關聯](/help/overview/ci-cd-pipelines.md)。



## 限制 {#limitations}

將私人存放庫與 Cloud Manager 搭配使用時會有某些限制。

* 私人存放庫不支援 Web 層和設定管道。
* 在生產全端管道上使用私人存放庫時，不會建立和推送 Git 標記。
* 如果您的 GitHb 組織已移除 Adobe GitHub 應用程式，此動作會移除所有存放庫的提取請求驗證功能。
* 當新提交被推送到所選分支時，使用私人存放庫和提交建置觸發器的管道不會自動啟動。
* [成品重複使用功能](/help/getting-started/project-setup.md#build-artifact-reuse)不適用於私人存放庫。
* 您無法使用 Cloud Manager 的 GitHub 檢查來暫停提取請求驗證。如果 GitHub 存放庫在 Cloud Manager 中已驗證，Cloud Manager 會驗證為該存放庫建立的提取請求。
