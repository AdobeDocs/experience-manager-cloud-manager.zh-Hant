---
title: 使用多個Git存放庫
description: 瞭解如何使用自己的Git存放庫或多個Git存放庫，而不是直接使用Cloud Manager的Git存放庫。
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 6%

---

# 使用多個來源Git存放庫 {#working-with-multiple-source-git-repos}

瞭解如何使用自己的Git存放庫或多個Git存放庫，而不是直接使用Cloud Manager的Git存放庫。

## 同步客戶管理的Git存放庫 {#syncing-customer-managed-git-repositories}

若要保持Cloud Manager的Git存放庫為最新狀態，請設定自動同步程式（如果您使用自己的存放庫或存放庫）。

根據代管Git存放庫的位置，可以使用GitHub操作或Jenkins等持續整合解決方案來設定自動化。 建立自動化後，可將每次到您自己的存放庫的推送自動轉寄到Cloud Manager的Git存放庫。

雖然對單一客戶擁有的Git存放庫而言，這類自動化很簡單，但若為多個存放庫設定，則需要更複雜的初始設定。 需要將來自多個Git存放庫的內容對應到單一Cloud Manager的Git存放庫中不同的目錄。 Cloud Manager的Git存放庫需要布建根Maven `pom.xml`，在模組區段中提供不同子專案的清單

以下是兩個客戶自有Git存放庫的範例`pom.xml`。 第一個專案被放入名為`project-a`的目錄中，而第二個專案則被放入名為`project-b`的目錄中。

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

這類根`pom.xml`會推送到Cloud Manager的Git存放庫中的某個分支。 然後必須設定這兩個專案以自動將變更轉寄到Cloud Manager的Git存放庫。

例如，推送至專案A中的分支可能會觸發GitHub動作。 此動作會簽出專案A和Cloud Manager Git存放庫。 它將專案A中的所有內容複製到Cloud Manager的Git存放庫的`project-a`目錄中。 然後它會認可並推送變更。

例如，會將專案A中`main`分支上的變更自動推送到Cloud Manager的Git存放庫中的`main`分支。 當然，分支之間可能會進行對應，例如，會將對專案A中名為`dev`分支的推送推到Cloud Manager Git存放庫中名為`development`的分支。 專案 B 需要類似的步驟。

根據分支策略和工作流程，可以為不同的分支設定同步。如果使用的Git存放庫不提供類似GitHub動作的概念，則也有可能透過Jenkins （或類似方法）進行整合。 在這種情況下，webhook會觸發進行這項工作的Jenkins作業。

執行以下操作以新增新的（第三個）來源或存放庫：

1. 將新的GitHub動作新增至新存放庫，以便將該存放庫中的變更推送至Cloud Manager的Git存放庫。
1. 至少執行一次該操作，以確保專案計畫碼在Cloud Manager的Git存放庫中。
1. 在Cloud Manager Git存放庫的根Maven `pom.xml`中新增對新目錄的參考。

## GitHub動作範例 {#sample-github-action}

推送至`main`分支會觸發此範例GitHub動作，然後推送至Cloud Manager的Git存放庫的子目錄。 需要對該GitHub動作提供兩個秘密： `MAIN_USER`和`MAIN_PASSWORD`，才能連線並推送至Cloud Manager的Git存放庫。

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

如上所示，使用GitHub動作相當靈活。 Git存放庫的分支之間可執行的任何對應，以及單獨的Git專案到主專案的目錄版面中的任何對應。

>[!NOTE]
>
>上述指令碼使用`git add`更新存放庫，並假設已包含移除。 根據Git的預設設定，此需求可能需要替換為`git add --all`。

## Jenkins作業範例 {#sample-jenkins-job}

此指令碼為範例，可用於Jenkins作業或類似操作。 Git存放庫中的變更就會觸發它。 Jenkins 作業會檢查該專案或分支的最新狀態，然後觸發此指令碼。

此指令碼會依次檢查Cloud Manager的Git存放庫並將專案程式碼認可到子目錄。

需要對該Jenkins作業提供兩個秘密： `MAIN_USER`和`MAIN_PASSWORD`，才能連線並推送至Cloud Manager的Git存放庫。

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

如上所示，使用 Jenkins 作業非常靈活。Git存放庫的分支之間可執行的任何對應，以及單獨的Git專案到主專案的目錄版面中的任何對應。

>[!NOTE]
>
>上述指令碼使用`git add`更新存放庫，並假設已包含移除。 根據Git的預設設定，`git add`可能需要取代為`git add --all`。
