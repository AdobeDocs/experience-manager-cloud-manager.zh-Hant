---
title: Git 子模組支援
description: 瞭解如何使用Git子模組，在建置時間時跨Git存放庫合併多個分支的內容。
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 20%

---

# Adobe存放庫的Git子模組支援 {#git-submodule-support}

Git子模組可用於在建置時間時跨Git存放庫合併多個分支的內容。

Cloud Manager的建置流程執行時，會先複製管道的存放庫並簽出已設定的分支。 如果分支在根目錄中包含`.gitmodules`檔案，則會執行命令。

```
$ git submodule update --init
```

此程式會將每個子模組簽出至適當的目錄中。 對於習慣使用Git子模組並且不想管理外部合併流程的組織來說，此技巧是[使用多個來源Git存放庫](/help/managing-code/multiple-git-repos.md)的潛在替代方法。

例如，我們假設有三個存放庫，每個都包含名為 `main` 的單一分支。在「主要」存放庫中（即在管道中設定的那個），`main`分支有一個`pom.xml`檔案，宣告包含在其他兩個存放庫中的專案：

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

然後為其他兩個存放庫新增子模組：

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

`.gitmodules`檔案中的結果如下所示：

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

如需有關Git子模組的詳細資訊，請參閱[Git參考手冊](https://git-scm.com/book/en/v2/Git-Tools-Submodules)。

## 限制 {#limitations}

使用Git子模組時，請注意下列事項：

* Git URL必須完全遵循上述語法。
* 由於安全理由，請勿在這些 URL 中嵌入憑證。
* 僅支援分支根部的子模組。
* 會將Git子模組參考資料儲存到特定的Git認可。 因此，若對子模組存放庫進行變更，需要更新引用的認可。 例如，使用`git submodule update --remote`。
* 除非另有必要，否則Adobe建議您對每個子模組執行`git config -f .gitmodules submodule.<submodule path>.shallow true`，以使用「淺」子模組。


## 私人存放庫的Git子模組支援 {#private-repositories}

使用[私人存放庫](private-repositories.md)時，對Git子模組的支援與使用Adobe存放庫時大致相同。

但是，設定完您的 `pom.xml` 檔案並執行 `git submodule` 命令後，您必須新增一個 `.gitmodules` 檔案到彙總器存放庫的根目錄，以便 Cloud Manager 偵測子模組設定。

![.gitmodules 檔案](assets/gitmodules.png)

![彙總器](assets/aggregator.png)

### 限制和建議 {#limitations-recommendations-private-repos}

搭配私人存放庫使用Git子模組時，請注意下列限制。

* 子模組的Git URL可以是HTTPS或SSH格式，但必須連結至Github.com存放庫。 無法將Adobe存放庫子模組新增至GitHub彙總存放庫，反之亦然。
* Adobe GitHub 應用程式必須可以存取 GitHub 子模組。
* [搭配Adobe管理的存放庫使用Git子模組的限制](#limitations-recommendations)也適用。
