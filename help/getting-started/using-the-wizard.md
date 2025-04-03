---
title: 使用新專案精靈
description: 依照本頁面的說明，了解如何使用精靈來建立 AEM 應用程式專案。
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: f3617eb50147f5af33282cb0f25ada7dc423d434
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 92%

---


# 使用新增專案精靈 {#using-the-wizard}

當您加入Cloud Manager成為新客戶時，系統已為您提供一個空白的Git存放庫。 為協助您開始使用，Cloud Manger 會提供精靈，以根據 [AEM 專案原型](https://github.com/adobe/aem-project-archetype)來建立最低限度的 AEM 專案作為起點。

依照下列步驟操作，即可使用精靈來建立 AEM 專案。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織。

1. 如果您尚未建立方案，可[建立您的方案](program-setup.md)。建立方案時，Cloud Manager 偵測到存放庫尚未設定。隨後，會有一張特殊的行動召喚卡片出現於「**概觀**」畫面中。

   ![建立專案 CTA](/help/assets/image2018-10-3_14-29-44.png)

1. 按一下&#x200B;**建立**，即可啟動精靈並提供重要的值。

   * **標題** - 專案的標題。預設會設定為方案名稱。
   * **新分支名稱** - Git 存放庫的初始分支。預設情況下，設定為 `main`。

   ![專案值](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 該對話框有一個抽屜，按一下朝向底部的把手即可開啟。該對話框在展開之後會顯示 AEM 專案原型的所有設定參數。這些參數具有根據您已提供之「**標題**」產生的預設值，並不需要修改。此處提供說明，以供您參考。

   ![詳細的原型參數](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 按一下「**建立**」，以使用原型建立入門專案並認可已命名的 Git 分支。

您現在有基礎專案了。接下來可以設定您的管道。

## 現有或遷移的客戶 {#existing-migrating}

如果您目前是 Adobe Managed Services (AMS) 客戶，或是正要遷移的內部部署 AEM 客戶，您可能已經在 Git 或其他版本控制系統中擁有專案程式碼。

在這種情況下，您可以將專案匯入 Cloud Manager Git 存放庫中。
