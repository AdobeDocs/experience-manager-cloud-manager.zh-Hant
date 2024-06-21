---
title: Git 子模組支援
description: 了解如何使用 Git 子模組以便在建置時間時跨越 Git 存放庫合併多個分支的內容。
source-git-commit: aa30c0024e422c96f0dfbaa2804e75143faf14dc
workflow-type: ht
source-wordcount: '417'
ht-degree: 100%

---


# Adobe 存放庫的 Git 子模組支援 {#git-submodule-support}

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

## 限制 {#limitations}

使用 Git 子模組時，請留意：

* Git URL 必須完全符合上述語法。
* 由於安全理由，請勿在這些 URL 中嵌入憑證。
* 僅支援分支根部的子模組。
* 會將 Git 子模組參考資料儲存到特定的 Git 認可。
   * 因此，若對子模組存放庫進行變更，需要更新引用的認可，例如，透過使用 `git submodule update --remote`。
* 除非另有必要，否則強烈建議使用「淺」子模組。
   * 為此，需對每個子模組執行 `git config -f .gitmodules submodule.<submodule path>.shallow true`。


## 對私人存放庫的 Git 子模組支援 {#private-repositories}

使用[私人存放庫](private-repositories.md)時，對 Git 子模組的支援與使用 Adob&#x200B;&#x200B;e 存放庫時基本相同。

但是，設定完您的 `pom.xml` 檔案並執行 `git submodule` 命令後，您必須新增一個 `.gitmodules` 檔案到彙總器存放庫的根目錄，以便 Cloud Manager 偵測子模組設定。

![.gitmodules 檔案](assets/gitmodules.png)

![彙總器](assets/aggregator.png)

### 限制和建議 {#limitations-recommendations-private-repos}

透過私人存放庫使用 Git 子模組時，請留意以下限制：

* 子模組的 Git URL 可以是 HTTPS 或 SSH 格式，但必須連結到 github.com 存放庫
   * 將 Adob&#x200B;&#x200B;e 存放庫子模組新增至 GitHub 彙總器存放庫 (反之亦然) 將無法運作。
* Adobe GitHub 應用程式必須可以存取 GitHub 子模組。
* [透過 Adob&#x200B;&#x200B;e 託管的存放庫使用 Git 子模組的限制](#limitations-recommendations)也適用。