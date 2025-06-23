---
title: 新增使用者和角色
description: 了解如何使用 Admin Console 新增使用者和角色，並建立設定檔。
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 9ad9af206fafea45f8bbf61b02950de0776b5a9f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 95%

---


# 新增使用者和角色 {#add-users-and-roles}

[!UICONTROL Cloud Manager] 中的許多功能都需要特定權限才能使用。例如，僅允許某些使用者為方案設定關鍵績效指標 (KPI)。這些權限在邏輯上會按角色分組。

[!UICONTROL Cloud Manager] 目前為管控特定功能可用性的使用者定義四種角色：

* 企業所有者
* 方案管理員
* 部署管理員
* 開發人員

>[!NOTE]
>
>若要使用 [!UICONTROL Cloud Manager]，您必須擁有 Adobe ID 以及 Adobe Managed Services 產品內容。

## 角色定義 {#role-definitions}

下表總結 Cloud Manager 中的角色。

| [!UICONTROL Cloud Manager] 角色 | 說明 |
| --- | --- |
| 業務負責人 | 負責定義 KPI、核准生產部署並在必要時覆寫重要的 3 層級失敗。 |
| 方案管理員 | 這類使用者會使用 [!UICONTROL Cloud Manager] 來執行團隊設定、審查狀態、檢視 KPI，並可在必要時核准重要的 3 層級失敗。 |
| 部署管理員 | 管理部署作業，並使用 [!UICONTROL Cloud Manager] 來執行中繼/生產部署、編輯 CI/CD 管道，並在必要時核准關鍵的 3 層級失敗。部署管理員也可以存取 Git 存放庫。 |
| 開發人員 | 開發和測試自訂應用程式的程式碼，且主要使用 [!UICONTROL Cloud Manager] 來檢視部署狀態，且可存取 Git 存放庫取得所認可的程式碼。 |
| 客戶成功工程師 | CSE 通常支援 AMS 客戶的客戶成功。其與 [!UICONTROL Cloud Manager] 互動，以利執行需要 CSE 監督的部署。 |
| 內容作者 | 其通常不會和 [!UICONTROL Cloud Manager] 互動，但可能會使用 [!UICONTROL Cloud Manager] 方案切換器來存取 AEM。 |

>[!NOTE]
>
>Admin Console 中的「開發人員」人物誌和 [!UICONTROL Cloud Manager] 中的「開發人員」角色並無相關。

## 使用Admin Console建立產品設定檔 {#using-admin-console-to-create-a-profile}

從 Admin Console 管理 [!UICONTROL Cloud Manager] 角色。透過將使用者新增到 [!UICONTROL Cloud Manager] 產品設定檔，可提供特定的角色會籍。

Admin Console 是在整個組織中管理 Adobe 權益的中心位置。若要了解關於 Adobe Admin Console 的更多資訊，請參閱「[Admin Console](https://helpx.adobe.com/tw/enterprise/using/admin-console.html)」。

管理員必須在 [!UICONTROL AEM Managed Services] 產品內容下建立新產品設定檔，以便為 [!UICONTROL Cloud Manager] 使用者指派基於角色的權限，對應於四個 [!UICONTROL Cloud Manager] 角色。

* 業務負責人
* 部署管理員
* 開發人員
* 方案管理員

使用Admin Console建立使用者或群組或將其新增到這些產品設定檔。

<!-- CQDOC-22790
>[!IMPORTANT]
>
>Due to a current limitation in the Admin Console and Cloud Manager, profiles cannot be saved with **No permissions** selected. Attempting to do so results in a backend error. This behavior affects the creation of Deployment Manager profiles. As a workaround, select at least one permission when creating a new profile. -->

**若要使用Admin Console建立產品設定檔：**

1. 請在 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) 登入 Admin Console。

1. 按一下「**概觀**」索引標籤，然後在「**產品和服務**」卡片上按一下您要編輯的產品。如果在卡片上的清單中找不到，請使用&#x200B;**產品**&#x200B;索引標籤以找到產品並點選。

   ![Admin Console 概觀索引標籤](/help/assets/admin-console-overview.png)

1. 在&#x200B;**產品**&#x200B;索引標籤上，按一下您要將使用者/群組新增到產品設定檔的環境。

   ![Admin Console 產品索引標籤](/help/assets/admin-console-product.png)

1. 在產品的&#x200B;**產品設定檔**&#x200B;索引標籤上，按一下&#x200B;**新設定檔**，即可新增新設定檔。

   ![新設定檔](/help/assets/admin-console-product-profiles.png)

1. 提供資訊以設定 [!UICONTROL Cloud Manager] 的新角色。

   * **設定檔名稱** - 此&#x200B;**設定檔名稱** 可以為任何值，但為避免混淆，建議使用&#x200B;**建議的設定檔名稱**&#x200B;欄中的值。
   * **顯示名稱** - 此&#x200B;**顯示名稱**&#x200B;必須是由[!UICONTROL Cloud Manager] 定義的技術值 (請參閱下表)。
   * **權限群組** - 您可以為設定檔選擇一個權限群組 (並不一定可提供)。

<!-- CQDOC-22790
      >[!IMPORTANT]
      >
      >Due to a current limitation in the Admin Console and Cloud Manager, profiles cannot be saved with **No permissions** selected. Attempting to do so results in a backend error. This behavior affects the creation of Deployment Manager profiles. As a workaround, select at least one permission when creating a new profile. -->

![建立新設定檔](/help/assets/screen_shot_2018-05-04at171819.png)

| 角色 | 顯示名稱 (必填) | 建議的設定檔名稱 |
|---|---|---|
| 企業所有者 | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 企業所有者角色 |
| 部署管理員 | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 部署管理員角色 |
| 開發人員 | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 開發人員角色 |
| 方案管理員 | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 方案管理員角色 |


1. 按一下&#x200B;**完成**&#x200B;即可儲存新的設定檔。

## 將設定檔指派給使用者或使用者群組 {#assign-profiles}

建立產品設定檔後，您可以指派使用者或使用者群組至設定檔。

1. 請在 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) 登入 Admin Console。

1. 在 Admin Console 中，選擇&#x200B;**使用者**&#x200B;索引標籤。

   ![使用者索引標籤](/help/assets/admin-console-users.png)

1. 在左側導覽面板中按一下&#x200B;**使用者**，然後按一下使用者以進行修改。

1. 在「**產品**」區段按一下![「更多」圖示 (省略符號)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，然後按一下「**編輯**」。

   ![編輯使用者](/help/assets/admin-console-edit-user.png)

1. 在「**編輯產品和使用者群組**」對話框中，按一下![「新增」圖示 (加號)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)，並選取要指派給使用者的設定檔。

   * 如果使用者已指派角色，則此![「新增」圖示 (加號)](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)按鈕會變成編輯按鈕 (鉛筆)，但使用方式相同。

   ![編輯產品和使用者群組](/help/assets/admin-console-edit-products-and-user-groups.png)

1. 按一下&#x200B;**儲存**，即可將設定檔儲存給使用者。

重複相同的步驟即可將設定檔指派給使用者群組，但需從左側導覽面板選取&#x200B;**使用者群組** (位於&#x200B;**使用者**&#x200B;索引標籤上)。按一下使用者群組並選取「**已指派的產品設定檔**」，然後按一下「**指派產品設定檔**」來指派設定檔。

![將設定檔指派至群組](/help/assets/admin-console-edit-user-groups.png)
