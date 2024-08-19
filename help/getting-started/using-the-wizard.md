---
title: 使用新增專案精靈
description: 依照本頁面的說明進行，即可了解如何使用精靈來建立 AEM 應用程式專案。
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 36%

---


# 使用新增專案精靈 {#using-the-wizard}

當您加入Cloud Manager成為新客戶時，系統已為您提供一個空白的Git存放庫。 為協助您開始使用，Cloud Manger 會提供精靈，以根據 [AEM 專案原型](https://github.com/adobe/aem-project-archetype)來建立最低限度的 AEM 專案作為起點。

依照下列步驟操作，即可使用精靈來建立 AEM 專案。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織。

1. 如果您尚未建立方案，可[建立您的方案](program-setup.md)。建立方案時，Cloud Manager會偵測存放庫尚未設定。 然後，**總覽**&#x200B;畫面上會顯示特殊的召喚行動卡。

   ![建立專案 CTA](/help/assets/image2018-10-3_14-29-44.png)

1. 按一下&#x200B;**建立**，即可啟動精靈並提供重要的值。

   * **標題** — 專案標題。 依預設，它會設定為方案的名稱。
   * **新分支名稱** - Git存放庫的初始分支。 預設為`main`。

   ![專案值](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 此對話方塊有一個抽屜，按一下朝向底部的控點即可開啟此抽屜。 此對話方塊在其展開形式中會顯示AEM專案原型的所有設定引數。 這些引數具有根據您已提供的&#x200B;**標題**&#x200B;產生的預設值，不需要修改。 此處提供說明，以供您參考。

   ![詳細的原型參數](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 按一下&#x200B;**建立**，以使用原型建立入門專案並認可已命名的 Git 分支。

您現在有基礎專案了。 是時候設定您的管道了。

## 現有或移轉的客戶 {#existing-migrating}

如果您目前是Managed Services (AMS)Adobe客戶或正要移轉至的內部部署AEM客戶，您可能已在Git或其他版本控制系統中擁有專案程式碼。

在這種情況下，您可以將專案匯入Cloud Manager Git存放庫。
