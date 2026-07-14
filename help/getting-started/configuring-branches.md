---
title: 設定分支
description: 了解如何設定您在 Git 中的第一個分支，以及 CI/CD 管道如何運用該分支部署您的應用程式程式碼。
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
TQID: https://experienceleague.adobe.com/Mxmx725a6m7J9UtwkI5o3tJGzZ7O3c3Bgv-fF393sZg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 1692390e24f8fa7d719bd8293a99586ec4ec36d4
workflow-type: tm+mt
source-wordcount: 314
ht-degree: 47%

---

# 設定分支 {#configuring-branches}

瞭解如何在Git中設定您的第一個分支，以及CI/CD管道如何使用它來部署您的應用程式程式碼。

## 設定您在 Git 中的第一個分支 {#setting-up-your-first-branch-in-git}

在 Cloud Manager 中上線的每個方案都會[佈建](/help/requirements/environment-provisioning.md)一個初始為空白的 Git 存放庫。 此存放庫可包含的分支數量依您的開發流程的要求而定，但CI/CD管道必須至少使用一個分支將應用程式程式碼部署到中繼和生產環境。 最佳做法是將 `main` 用作此分支的名稱。 此方法是Git使用者端在設定新專案時的預設行為。

例如，在設定新專案時，您會執行一組類似下列內容的命令。

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
>使用命令列用戶端並非必要。 有多種圖形化 Git 用戶端可供使用，無論是獨立應用程式或做為整合式開發環境 (IDE) (如 Eclipse 或 IntelliJ) 之一部分。 只要使用者端應用程式支援使用HTTPS的Git，就與[!UICONTROL Cloud Manager]相容。

## 推送您的第一個分支 {#pushing-your-first-branch}

當您認可至少一個修訂版本，就可以新增遠端的 [!UICONTROL Cloud Manager] 存放庫，然後將您的認可推送過去。

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
>您的Adobe CSE （客戶成功工程師）在[!UICONTROL Cloud Manager]上線期間提供特定URL以及您的認證。

## 額外的分支 {#additional-branches}

`main`分支僅夠用於簡單專案，但建議使用更複雜的分支策略。 許多客戶會遵循在名為`develop`的分支上執行例行開發活動的程式。 然後，當需要部署時，`develop`分支會合併到`main`分支中。

>[!TIP]
>
>若要檢視常用的Git命令，請參閱[Git參考指南](https://training.github.com/downloads/github-git-cheat-sheet/)。
