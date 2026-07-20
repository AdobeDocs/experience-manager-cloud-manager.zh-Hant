---
title: 在 Cloud Manager 中新增 Adobe 存放庫
description: 了解如何在 Cloud Manager 中新增 Adobe 託管的存放庫。
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
TQID: https://experienceleague.adobe.com/LBI6V07enOlxe8yh-XwlkL-mdMWR0MJyKi1gUQtjtK4
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 036302d4861b59e783ac731da12078be59cdc5c4
workflow-type: tm+mt
source-wordcount: 225
ht-degree: 69%

---

# 在 Cloud Manager 中新增 Adobe 存放庫 {#adobe-repositories}

了解如何在 Cloud Manager 中新增 Adobe 託管的存放庫。

**存放庫**&#x200B;頁面可讓您新增其他Adobe管理的存放庫至選取的方案。

**若要在 Cloud Manager 中新增 Adobe 存放庫：**

1. 透過 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，然後選取要新增 Adobe 託管存放庫的相關組織和方案。

1. 從&#x200B;**方案總覽**&#x200B;頁面，按一下側邊功能表中的![資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **存放庫**&#x200B;索引標籤。

1. 在&#x200B;**存放庫**&#x200B;頁面 (位於右上角附近)，按一下「**新增存放庫**」。

   ![新增存放庫按鈕](/help/managing-code/assets/repositories-tab.png)

1. 在「**新增存放庫**」對話框中，確保選取 **Adobe 存放庫**&#x200B;作為存放庫類型。

1. 在各別的文字欄位中，輸入以下內容：

   * **存放庫名稱** — 新存放庫的描述性名稱。
   * **存放庫URL預覽** — 您不需要輸入URL路徑或編輯現有路徑，因為存放庫基礎結構已由Adobe設定、整合和管理。
   * **說明 (選項)** - 存放庫的詳細說明。

   ![新增存放庫對話框](/help/managing-code/assets/repository-add-adobe.png)

1. 按一下&#x200B;**儲存**。
您的新存放庫會顯示在**存放庫**&#x200B;頁面上的表格中。

您現在可以將 [CI/CD 管道](/help/overview/ci-cd-pipelines.md)與存放庫建立關聯，或在&#x200B;[**存放庫**&#x200B;頁面](/help/managing-code/managing-repositories.md)中管理存放庫。

>[!TIP]
>
>您也可以新增自己管理的 GitHub 存放庫，以此作為[私人存放庫](/help/managing-code/private-repositories.md)。
