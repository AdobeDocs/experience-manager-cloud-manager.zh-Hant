---
title: 在 Cloud Manager 中新增 Adobe 存放庫
description: 了解如何在 Cloud Manager 中新增 Adobe 託管的存放庫。
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
source-git-commit: 675568426df0df5890dd8c72bfb53c24a4c5d666
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---

# 在 Cloud Manager 中新增 Adobe 存放庫 {#adobe-repositories}

了解如何在 Cloud Manager 中新增 Adobe 託管的存放庫。

「**存放庫**」頁面讓您輕鬆地將其他 Adobe 託管的存放庫新增至選定的方案。

**若要在 Cloud Manager 中新增 Adobe 存放庫：**

1. 透過 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager，然後選取要新增 Adobe 託管存放庫的相關組織和方案。

1. 在&#x200B;**方案概觀**&#x200B;頁面 (位於側邊選單內)，按一下 ![資料夾圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg)「**存放庫**」標籤。

1. 在&#x200B;**存放庫**&#x200B;頁面 (位於右上角附近)，按一下「**新增存放庫**」。

   ![新增存放庫按鈕](/help/managing-code/assets/repositories-tab.png)

1. 在「**新增存放庫**」對話框中，確保選取 **Adobe 存放庫**&#x200B;作為存放庫類型。

1. 在各別的文字欄位中，輸入以下內容：

   * **存放庫名稱** - 新存放庫使用表達清楚的名稱。
   * **存放庫 URL 預覽**  - 您無需輸入 URL 路徑或編輯現有路徑，因為存放庫已有所需的基礎架構且由 Adobe 完全整合和管理。
   * **說明 (選項)** - 存放庫的詳細說明。

   ![新增存放庫對話框](/help/managing-code/assets/repository-add-adobe.png)

1. 按一下「**儲存**」。
您的新存放庫將顯示在「**存放庫**」頁面的表格中。

您現在可以將 [CI/CD 管道](/help/overview/ci-cd-pipelines.md)與存放庫建立關聯，或在&#x200B;[**存放庫**&#x200B;頁面](/help/managing-code/managing-repositories.md)中管理存放庫。

>[!TIP]
>
>您也可以新增自己管理的 GitHub 存放庫，以此作為[私人存放庫](/help/managing-code/private-repositories.md)。
