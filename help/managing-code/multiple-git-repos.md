---
title: 使用多個 Git 存放庫
description: 了解如何使用您自己的 Git 存放庫或多個 Git 存放庫，而非直接使用 Cloud Manager 的 Git 存放庫。
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
TQID: https://experienceleague.adobe.com/xKzqOfbi12A0POy-C7Gm7-n649DEBX9JP3LfXA5UC3Y
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: a07522b4a3c0619bb57b414de58633c65d9c7b5c
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 60%

---

# 使用多個來源 Git 存放庫 {#working-with-multiple-source-git-repos}

了解如何使用您自己的 Git 存放庫或多個 Git 存放庫，而非直接使用 Cloud Manager 的 Git 存放庫。

## 同步客戶管理的 Git 存放庫 {#syncing-customer-managed-git-repositories}

若您是使用自己的一個或多個存放庫，請設定自動同步流程，讓 Cloud Manager 的 Git 存放庫保持最新狀態。

根據代管Git存放庫的位置，使用GitHub動作或Jenkins等持續整合解決方案來設定自動化。 建立自動化後，可將每次到您自己的存放庫的推送自動轉寄到Cloud Manager的Git存放庫。

雖然對單一客戶擁有的Git存放庫而言，這類自動化很簡單，但若為多個存放庫設定，則需要更複雜的初始設定。 需要將來自多個 Git 存放庫的內容對應到單一 Cloud Manager Git 存放庫中不同的目錄上。 Cloud Manager的Git存放庫需要布建根Maven `pom.xml`，在模組區段中提供不同子專案的清單

以下為兩個客戶自有 Git 存放庫的範例 `pom.xml`。 第一個專案被放進名為 `project-a` 的目錄中，而第二個專案則被放進名為 `project-b` 的目錄。

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

這類根 `pom.xml` 會被推送到 Cloud Manager Git 存放庫中的某個分支。 然後必須設定這兩個專案，將變更自動轉寄到 Cloud Manager 的 Git 存放庫。

舉例來說，推送到專案 A 中分支的動作可以觸發 GitHub 操作。 該操作會簽出專案 A 和 Cloud Manager Git 存放庫， 並將專案 A 中所有內容複製到 Cloud Manager Git 存放庫內的 `project-a` 目錄中。 然後認可並推送更改。

例如，專案 A  `main` 分支上的變更會自動推送到 Cloud Manager Git 存放庫中的 `main` 分支。 當然，分支之間可能會進行對應，例如推送到專案A中名為`dev`的分支會推送到Cloud Manager的Git存放庫中名為`development`的分支。 專案 B 需要類似的步驟。

根據分支原則和工作流程，可以為不同的分支設定同步。 如果使用的Git存放庫不提供類似GitHub動作的概念，則也有可能使用Jenkins （或類似方法）進行整合。 在這種情況下，webhook會觸發執行任務的Jenkins作業。

請依照下列步驟，增加新的 (第三個) 來源或存放庫：

1. 將新的 GitHub 操作加入新的存放庫中，從該存放庫將變更推送至 Cloud Manager 的 Git 存放庫。
1. 為確保專案程式碼位於Cloud Manager的Git存放庫中，請至少執行一次該動作。
1. 在 Cloud Manager Git 存放庫的根 Maven `pom.xml` 中新增新目錄的參考資料。

## GitHub 操作範例 {#sample-github-action}

推送至 `main` 分支會觸發這項 GitHub 操作範例，然後會推送至 Cloud Manager Git 存放庫的子目錄中。 需要對該GitHub動作提供兩個秘密： `MAIN_USER`和`MAIN_PASSWORD`，才能連線並推送至Cloud Manager的Git存放庫。

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

如上所示，可以靈活使用 GitHub 操作。 Git存放庫的分支之間可執行的任何對應，單獨的Git專案到主要專案的目錄版面中的任何對應也是如此。

>[!NOTE]
>
>上述指令碼會使用 `git add` 對假定已納入移除的存放庫進行更新。 根據Git的預設設定，將此需求取代為`git add --all`。

## Jenkins 作業範例 {#sample-jenkins-job}

此指令碼為範例，可用於 Jenkins 作業或類似操作。 Git 存放庫中的變更會觸發之。 Jenkins 作業會簽出該專案或分支的最新狀態，然後觸發此指令碼。

此指令碼會簽出Cloud Manager的Git存放庫並將專案程式碼認可到子目錄。

執行 Jenkins 作業需要搭配兩個密碼：`MAIN_USER` 以及 `MAIN_PASSWORD`，才能連線並推送至 Cloud Manager 的 Git 存放庫。

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

使用 Jenkins 作業非常靈活。 Git存放庫的分支之間可執行的任何對應，單獨的Git專案到主要專案的目錄版面中的任何對應也是如此。

>[!NOTE]
>
>上述指令碼會使用 `git add` 對假定已納入移除的存放庫進行更新。 根據Git的預設設定，將`git add`取代為`git add --all`。
