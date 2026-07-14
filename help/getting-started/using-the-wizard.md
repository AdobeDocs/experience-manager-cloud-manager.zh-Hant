---
title: 使用新專案精靈
description: 依照本頁面的說明，了解如何使用精靈來建立 AEM 應用程式專案。
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# 使用新增專案精靈 {#using-the-wizard}

當您加入Cloud Manager成為新客戶時，會為您提供一個空白的Git存放庫。 為協助您開始使用，Cloud Manager提供精靈，以根據[AEM專案原型](https://github.com/adobe/aem-project-archetype)來建立最低限度的AEM專案作為起點。

**若要使用新專案精靈：**

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 登入 Cloud Manager 並選取適當的組織。

1. 如果您尚未建立方案，可[建立您的方案](program-setup.md)。 建立方案時，Cloud Manager會偵測存放庫尚未設定。 然後，**總覽**&#x200B;熒幕上會出現特殊的提示卡。

   ![建立專案 CTA](/help/assets/image2018-10-3_14-29-44.png)

1. 按一下&#x200B;**建立**，即可啟動精靈並提供重要的值。

   * **標題** - 專案的標題。 預設會設定為方案名稱。
   * **新分支名稱** - Git存放庫的初始分支。 預設情況下，設定為 `main`。

   ![專案值](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 此對話方塊有一個區段，按一下底部附近的圖示即可顯示這個區段。 該對話框在展開之後會顯示 AEM 專案原型的所有設定參數。 這些參數具有根據您已提供之「**標題**」產生的預設值，並不需要修改。 此處提供說明，以供您參考。

   ![詳細的原型參數](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 按一下「**建立**」，以使用原型建立入門專案並認可已命名的 Git 分支。

您現在有基礎專案了。 您現在可以設定您的管道。

## 現有或遷移的客戶 {#existing-migrating}

如果您目前是Adobe Managed Services (AMS)客戶或正在移轉的內部AEM客戶，表示您的專案程式碼已在Git或其他版本控制系統中。

在這種情況下，您可以將專案匯入 Cloud Manager Git 存放庫中。
