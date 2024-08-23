---
title: 設定分支
description: 瞭解如何在Git中設定您的第一個分支，以及CI/CD管道如何使用它來部署您的應用程式程式碼。
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 4%

---


# 設定分支 {#configuring-branches}

瞭解如何在Git中設定您的第一個分支，以及CI/CD管道如何使用它來部署您的應用程式程式碼。

## 在Git中設定您的第一個分支 {#setting-up-your-first-branch-in-git}

已為Cloud Manager中上線的每個方案布建一個最初為空白的Git存放庫[](/help/requirements/environment-provisioning.md)。 此存放庫可包含的分支數量依您的開發流程的要求而定，但必須至少有一個分支可供CI/CD管道用於將應用程式程式碼部署到中繼和生產環境。 最佳做法是將 `main` 用作此分支的名稱。方便的是，此方法是Git使用者端在設定新專案時的預設行為。

例如，在設定新專案時，您會執行一組類似下列的命令。

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>不需要使用命令列使用者端。 有多種圖形Git使用者端可作為獨立應用程式或作為諸如Eclipse或IntelliJ等整合式開發環境(IDE)的一部分提供。 只要使用者端應用程式支援使用HTTPS的Git，就應該與[!UICONTROL Cloud Manager]相容。

## 推送您的第一個分支 {#pushing-your-first-branch}

當您認可至少一個修訂時，您可以將[!UICONTROL Cloud Manager]存放庫新增為遠端，然後將您的認可推送過去。

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>您的AdobeCSE （客戶成功工程師）在[!UICONTROL Cloud Manager]上線期間會提供特定URL以及您的認證。

## 其他分支 {#additional-branches}

對於非常簡單的專案，單一`main`分支可能就足夠了，但在大多數情況下，需要更複雜的分支策略。 許多客戶會遵循在名為`develop`的分支上執行日常開發活動的程式。 然後，在需要部署時，開發分支會合併到`main`分支中。

>[!TIP]
>
>若要檢視常用的Git命令，請參閱[Git速查表](https://training.github.com/downloads/github-git-cheat-sheet)。
