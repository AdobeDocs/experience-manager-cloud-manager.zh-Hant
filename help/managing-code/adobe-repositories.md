---
title: 在Cloud Manager中新增Adobe存放庫
description: 瞭解如何在Cloud Manager中新增Adobe管理的存放庫。
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
source-git-commit: 675568426df0df5890dd8c72bfb53c24a4c5d666
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# 在Cloud Manager中新增Adobe存放庫 {#adobe-repositories}

瞭解如何在Cloud Manager中新增Adobe管理的存放庫。

**存放庫**&#x200B;頁面可讓您輕鬆將其他Adobe管理的存放庫新增至選取的方案。

**若要在Cloud Manager中新增Adobe存放庫：**

1. 在[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)登入Cloud Manager，並選取適當的組織以及您要新增Adobe管理存放庫的程式。

1. 從&#x200B;**方案總覽**&#x200B;頁面，按一下側邊功能表中的![資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **存放庫**&#x200B;索引標籤。

1. 在&#x200B;**存放庫**&#x200B;頁面右上角附近，按一下&#x200B;**新增存放庫**。

   ![新增存放庫按鈕](/help/managing-code/assets/repositories-tab.png)

1. 在&#x200B;**新增存放庫**&#x200B;對話方塊中，確定已選取&#x200B;**Adobe存放庫**&#x200B;作為存放庫型別。

1. 在個別文字欄位中輸入下列內容：

   * **存放庫名稱** — 您新存放庫的表達式名稱。
   * **存放庫URL預覽** — 您不需要輸入URL路徑或編輯現有路徑，因為存放庫基礎結構已經就位，並已完全整合併由Adobe管理。
   * **描述（選擇性）** — 存放庫的詳細描述。

   ![新增存放庫對話方塊](/help/managing-code/assets/repository-add-adobe.png)

1. 按一下&#x200B;**儲存**。
您的新存放庫會顯示在**存放庫**&#x200B;頁面的表格中。

您現在可以將[CI/CD管道](/help/overview/ci-cd-pipelines.md)與其建立關聯，或在&#x200B;[**存放庫**&#x200B;頁面](/help/managing-code/managing-repositories.md)中管理它。

>[!TIP]
>
>您也可以新增自己管理的 GitHub 存放庫，以此作為[私人存放庫](/help/managing-code/private-repositories.md)。
