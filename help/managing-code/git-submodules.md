---
title: Git 子模組支援
description: 了解如何使用 Git 子模組在建置期間將橫跨多個不同 Git 存放庫的多個分支內容合併。
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---

# Adobe 存放庫的 Git 子模組支援 {#git-submodule-support}

可使用 Git 子模組在建置期間將橫跨不同 Git 存放庫的多個分支內容合併。

在執行 Cloud Manager 的建置過程時，首先會原地複製管道的存放庫並檢查已設定的分支。如果分支在根目錄中包含 `.gitmodules` 檔案，便會執行該命令。

```
$ git submodule update --init
```

此程序會將各個子模組簽出並存至適當的目錄中。對於習慣使用 Git 子模組並且不想管理外部合併流程的組織來說，此技術有可能成為[使用多個原始程式碼 Git 存放庫](/help/managing-code/multiple-git-repos.md)的替代方法。

例如，假設有三個存放庫，每個都包含名為 `main` 的單一分支。於「主要」存放庫 (即在管道內設定的存放庫) 中，`main` 分支有一個 `pom.xml` 檔案，宣告包含在其他兩個存放庫中的專案：

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

接著，您對其他兩個存放庫新增子模組：

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

`.gitmodules` 檔案中的結果如下所示：

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

如欲了解 Git 子模組的詳細資訊，請參閱 [Git 參考手冊](https://git-scm.com/book/en/v2/Git-Tools-Submodules)。

## 限制 {#limitations}

使用 Git 子模組時，請留意以下事項：

* Git URL 必須完全符合上述語法。
* 由於安全理由，請勿在這些 URL 中嵌入憑證。
* 僅支援分支根部的子模組。
* Git 子模組參考資料會儲存至特定的 Git 認可。因此，若對子模組存放庫進行變更，便需要更新所參考的認可。例如，透過使用 `git submodule update --remote`。
* 除非另有必要，Adobe 建議您透過為每個子模組執行 `git config -f .gitmodules submodule.<submodule path>.shallow true` 來使用「淺」子模組。


## 私人存放庫的 Git 子模組支援 {#private-repositories}

使用[私人存放庫](private-repositories.md)時，對 Git 子模組的支援與使用 Adobe 存放庫時基本相同。

但是，設定完您的 `pom.xml` 檔案並執行 `git submodule` 命令後，您必須新增一個 `.gitmodules` 檔案到彙總器存放庫的根目錄，以便 Cloud Manager 偵測子模組設定。

![.gitmodules 檔案](assets/gitmodules.png)

![彙總器](assets/aggregator.png)

### 限制和建議 {#limitations-recommendations-private-repos}

透過私人存放庫使用 Git 子模組時，請留意以下限制：

* 子模組的 Git URL 可以是 HTTPS 或 SSH 格式，但必須連結至 Github.com 存放庫。無法將 Adobe 存放庫子模組新增至 GitHub 彙總器存放庫，反之亦然。
* Adobe GitHub 應用程式必須可以存取 GitHub 子模組。
* [透過 Adobe 託管的存放庫使用 Git 子模組的限制](#limitations-recommendations)也適用。
