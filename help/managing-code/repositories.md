---
title: Cloud Manager 存放庫
description: 了解如何為您的 Cloud Manager 方案存取、建立和編輯存放庫。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 1d4ab9704fdb743b097e24be335fbf069d1e78bd
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 98%

---


# Cloud Manager 存放庫 {#cloud-manager-repos}

存放庫指您使用 Git 管理程式碼的地方。了解如何為您的 Cloud Manager 方案建立存放庫。

## 存取存放庫 {#accessing-repos}

您可以從 Cloud Manager 自助存取和管理您的 Git 存放庫。

若要存取您的存放庫，請使用 Cloud Manager 中提供的&#x200B;**存取存放庫資訊**&#x200B;按鈕，該按鈕位於管道卡上最顯眼的位置。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織和方案。

1. 瀏覽至&#x200B;**管道**&#x200B;卡 (從&#x200B;**方案總覽**&#x200B;頁面)，您將看到&#x200B;**存取存放庫資訊**&#x200B;選項，即可存取和管理您的 Git 存放庫[ (以此管道設定)。](/help/using/production-pipelines.md)

   ![存取存放庫資訊按鈕](/help/assets/access-repo1.png)

1. 點選或按一下 **存取存放庫資訊** 按鈕來開啟對話方塊，其中顯示：

   * 至 Git 存放庫的 URL
   * 使用者名稱
   * 密碼
   * 執行 Git 命令以在本機複製存放庫

   ![存放庫資訊對話框](/help/assets/access-repo-create.png)

使用所提供的資訊在本機複製存放庫，以便您可以開始本機開發。

>[!NOTE]
>
>**開發人員**&#x200B;或&#x200B;**部署管理員**&#x200B;角色的使用者看得見該&#x200B;**存取存放庫資訊**&#x200B;選項。

## 新增存放庫 {#add-repos}

依照這些步驟操作即可在 Cloud Manager 中新增存放庫：

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，按一下&#x200B;**存放庫**&#x200B;索引標籤，並瀏覽至&#x200B;**存放庫**&#x200B;頁面。

1. 按一下&#x200B;**新增存放庫**，即可啟動精靈。

   >[!NOTE]
   >
   >您必須具備&#x200B;**部署管理員**&#x200B;或&#x200B;**企業所有者**&#x200B;角色才能新增存放庫。

   ![新增存放庫](/help/assets/create-repo2.png)

1. 依照要求輸入名稱和說明，然後按一下&#x200B;**儲存**。

   ![存放庫詳細資料](/help/assets/repo-1.png)

1. 選取&#x200B;**儲存**。

將隨即顯示您新建的存放庫。

以下情況下，在 Cloud Manager 中建立的存放庫可供您選取：[建立您的管道時。](/help/overview/ci-cd-pipelines.md)

## 檢視和編輯存放庫 {#edit-repos}

依照下列步驟操作，即可在 Cloud Manager 中編輯和檢視存放庫：

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，按一下&#x200B;**存放庫**&#x200B;索引標籤，並瀏覽至&#x200B;**存放庫**&#x200B;頁面。您可以在此檢視您現有存放庫的詳細資料。

1. 選取存放庫並按一下表格最右側的省略符號按鈕，即可&#x200B;**複製存放庫 URL** 或&#x200B;**檢視和更新**&#x200B;您的存放庫。

![編輯存放庫](/help/assets/create-repo3.png)

## 刪除存放庫 {#delete-repos}

若要刪除存放庫，請執行相同的步驟以[檢視和編輯存放庫](#edit-repos)，但在&#x200B;**存放庫**&#x200B;頁面上，從要刪除之存放庫的省略號按鈕選取&#x200B;**刪除**。

請注意，在 Cloud Manager 刪除存放庫時，它會被標記為已刪除，使用者無法再存取，但它會保留在系統中以用於恢復目的。

如果您在刪除存放庫後嘗試使用相同名稱建立新的存放庫，您將收到錯誤訊息「嘗試建立存放庫時發生錯誤。請聯絡您的 CSE 或 Adobe 支援。」

如果您收到此錯誤訊息，請聯絡 Adobe 支援，如此他們可協助重新命名已刪除的存放庫，或為新的存放庫選擇不同的名稱。

## Git 子模組支援 {#git-submodule-support}

Git 子模組可用於在建置時間時跨越 Git 存放庫合併多個分支的內容。

當 Cloud Manager 的建置流程執行時，複製為管道設定的存放庫並簽出已設定的分支後，如果該分支包含根目錄中的 `.gitmodules` 檔案，則執行命令。

```
$ git submodule update --init
```

這會將每個子模組簽出至適當的目錄中。對於習慣於使用 Git 子模組並且不想管理外部合併流程的組織來說，這種技術有可能成為[使用多個原始程式碼 Git 存放庫](/help/managing-code/multiple-git-repos.md)的備用方法。

例如，我們假設有三個存放庫，每個都包含名為 `main` 的單一分支。在「主要」存放庫中 (即在管道中設定的那個)，`main` 分支有一個 `pom.xml` 檔案，宣告包含在其他兩個存放庫中的專案：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

然後，您將為其他兩個存放庫新增子模組：

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

這會導致 `.gitmodules` 檔案，如下所示：

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

有關 Git 子模組的更多資訊可以在 [Git 參考手冊](https://git-scm.com/book/en/v2/Git-Tools-Submodules)中找到。

### 限制 {#limitations}

使用 Git 子模組時，請留意：

* Git URL 必須完全符合上述語法。
* 由於安全理由，請勿在這些 URL 中嵌入憑證。
* 僅支援分支根部的子模組。
* 會將 Git 子模組參考資料儲存到特定的 Git 認可。
   * 因此，若對子模組存放庫進行變更，需要更新引用的認可，例如，透過使用 `git submodule update --remote`。
* 除非另有必要，否則強烈建議使用「淺」子模組。
   * 為此，需對每個子模組執行 `git config -f .gitmodules submodule.<submodule path>.shallow true`。
