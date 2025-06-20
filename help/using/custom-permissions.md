---
title: 自訂權限
description: 了解如何使用自訂權限建立新的自訂權限設定檔並內含可設定的權限，以便限制 Cloud Manager 使用者對方案、管道和環境的存取。
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 98%

---

# 自訂權限 {#custom-permissions}

了解如何使用自訂權限建立新的自訂權限設定檔並內含可設定的權限，以便限制 Cloud Manager 使用者對方案、管道和環境的存取

## 簡介 {#introduction}

Cloud Manager 有一組預先定義的角色，用於管理 Cloud Manager 各項功能的存取權：

* 企業所有者
* 方案管理員
* 部署管理員
* 開發人員

自訂權限可讓使用者建立新的自訂權限設定檔並內含可設定的權限，以便限制 Cloud Manager 使用者對方案、管道和環境的存取。

>[!TIP]
>
>如需深入了解預先定義的角色，請參閱[角色型權限](/help/requirements/role-based-permissions.md)。

## 使用自訂權限 {#using}

建立及使用您自己的自訂權限需要進行以下三個步驟：

1. [建立新的產品設定檔](#create)。
1. [將自訂權限指派到新的產品設定檔](#assign-permissions)。
1. [將使用者指派到新的產品設定檔](#assign-users)。

本節會詳細介紹這些步驟。在建立自己的自訂權限時，可參考「[詞彙](#terms)」和「[可設定的權限](#configurable-permissions)」小節的實用內容。

>[!NOTE]
>
>您必須在 Admin Console 中擁有產品管理員權限，才能建立新的設定檔及管理 Cloud Manager 權限。

### 建立新的產品設定檔 {#create}

先建立一個新的產品設定檔，讓您可以對其指派自訂權限。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager。

1. 選取產品 **AEM Managed Services**。

1. 搜尋名稱與模式 `*-cloud-manager` 相符的執行個體，然後點選或按一下以管理使用者和權限。

1. 您會被重新導向至 Admin Console 的「**產品**」標籤，您可以在那裡管理 Cloud Manager 的使用者和權限。在 Admin Console 中，按一下「**新增設定檔**」。

![新設定檔按鈕](/help/assets/admin-console-new-profile.png)

1. 提供設定檔的一般詳細資訊。

   * **產品設定檔名稱**- 設定檔的說明性名稱
   * **顯示名稱** - 在使用者介面顯示的縮寫名稱 (選項)
   * **說明** - 設定檔用來解釋其用途的資訊性說明 (選用)
   * **透過電子郵件通知使用者** - 選取此選項後，當使用者被新增至此設定檔或從中刪除時，會透過電子郵件通知使用者。

1. 按一下「**儲存**」。

新的產品設定檔已儲存並出現在 Admin Console 的產品設定檔清單中。

### 將自訂權限指派到新的產品設定檔 {#assign-permissions}

現在您有新的產品設定檔，可以對其指派自訂權限。

1. 在 Admin Console 中，按一下[您剛建立的新產品設定檔](#create)名稱。

1. 在開啟的視窗中，選取&#x200B;**權限**&#x200B;標籤可檢視可編輯的權限清單。

   ![可編輯的權限](/help/assets/permissions-tab.png)

1. 按一下權限的「**編輯**」連結即可編輯權限。

1. **編輯權限**&#x200B;視窗隨即開啟。
   * 您在上一個步驟中選取的權限將在左側欄中呈現已選取狀態。
   * 標示為「**可用權限項目**」的中間欄包含此權限可指派的權限項目。
   * 標示為&#x200B;**包含的權限項目**&#x200B;的右側欄包含已指派的權限項目。

   ![編輯權限項目](/help/assets/edit-permission-items.png)

1. 按一下權限項目旁的加號 (`+`) 圖示，將其新增至「**包含的權限項目**」欄位中。如有需要，按一下權限項目旁的 `i` 圖示可了解更多。

1. 於「**可用權限項目**」欄位的頂端按一下「**全部新增**」，即可新增所有權限。同樣地，按一下「**全部移除**」，即可移除所有先前選取的權限。

1. 當您完成新產品設定檔的權限項目定義後，請按一下「**儲存**」。

您的新產品設定檔及其自訂權限均已儲存。

### 將使用者指派到新的產品設定檔 {#assign-users}

現在您可以將使用者指派至您建立的含有自訂權限的新產品設定檔。

1. 在 Admin Console 中，按一下[您剛指派自訂權限的新產品設定檔](#assign-permissions)名稱。

1. 在開啟的視窗中，選取&#x200B;**使用者**&#x200B;標籤。

1. 按一下「**新增使用者**」，將使用者指派至含有自訂權限的新產品設定檔。

請參閱「**將使用者和使用者群組新增至產品設定檔**」的內容，其載於「[管理企業使用者的產品設定檔](https://helpx.adobe.com/tw/enterprise/using/manage-product-profiles.html)」文件中，深入了解如何使用 Admin Console。

## 可設定的權限 {#configurable-permissions}

以下權限可用於建立自訂設定檔。

| 權限 | 說明 |
| --- | --- |
| `Program Access` | 允許使用者存取方案 |
| `Program Edit` | 允許使用者編輯方案 |
| `Pipeline Create` | 允許使用者建立新管道 |
| `Pipeline Delete` | 允許使用者刪除管道 |
| `Pipeline Edit` | 允許使用者編輯管道 |
| `Production Deployments Approve/Reject` | 允許使用者核准或拒絕生產部署步驟 |
| `Pipeline Executions Cancel` | 允許使用者取消管道執行 |
| `Pipeline Executions Start` | 允許使用者啟動新的管道執行 |
| `Override/Reject Important Metric Failures` | 允許使用者覆寫/拒絕重要量度失敗 |
| `Production Deployments Schedule` | 允許使用者排程生產部署步驟 |
| `Repository Info Access` | 允許使用者存取存放庫資訊並產生存取密碼 |
| `Repository Create` | 允許使用者建立新的 Git 存放庫 |
| `Repository Delete` | 允許使用者刪除 Git 存放庫 |
| `Repository Edit` | 允許使用者編輯 Git 存放庫 |
| `Repository Code Generate` | 允許使用者從原型版本產生專案 |
| `Content Copy Manage` | 允許使用者管理內容複製作業 |

### 組織層級權限 {#organization-level}

組織層級權限一律適用於組織內的所有方案。

**存放庫資訊存取**&#x200B;便是 Cloud Manager 其中一種組織層級權限。此權限允許使用者產生使用者名稱、密碼和存放庫 URL，以利存取客戶專案並為專案貢獻內容。雖然組織內所有存放庫採用的使用者名稱及密碼皆是相同的，但每個方案都有唯一的存放庫 URL。

如需詳細資訊請參閱「[原始程式碼存放庫](/help/requirements/source-code-repository.md)」。

## 詞彙 {#terms}

以下詞彙用於建立和管理自訂權限和預先定義的角色。

| 術語 | 說明 |
| --- | --- |
| 預先定義的權限 | 預先定義的角色，例如&#x200B;**企業所有者**、**部署管理員**&#x200B;等等。管理 Cloud Manager 的各項功能。如需深入了解預先定義的角色，請參閱[角色型權限](/help/requirements/role-based-permissions.md)。 |
| 自訂權限 | Cloud Manager 的功能，允許使用者建立權限設定檔來定義角色以管理 Cloud Manager 的支援功能 |
| 權限設定檔 | 在 Admin Console 中建立，用於管理可設定的權限，而這些權限適用於權限設定檔所包含的使用者 |
| 可設定的權限 | 可在權限設定檔中設定 Cloud Manager 權限 |
| 權限項目 | 可以套用權限的方案、環境或管道資源 |

權限項目是指權限所適用的範圍。通常是以下其中一項：

| 權限項目類型 | 範例 | 說明 |
| --- | --- | --- |
| 組織 | 組織：公司 A | 組織的所有適用資源。資源可以是方案、環境或管道。如果使用者在任何權限中新增一個組織，則該組織中所有新資源也具有該權限。 |
| 方案 | 方案 A | 方案的所有適用資源。 |
| 環境 | 方案 A：環境 | 適用於特定環境。 |
| 管道 | 方案 A：管道 | 適用於特定管道。 |

## 限制 {#limitations}

使用自訂權限時，請記住以下限制：

* [只有一小組權限](#configurable-permissions)可用於建立自訂設定檔。
* 方案、環境、管道等資源。在 Cloud Manager 中建立，可能需要兩分鐘才會出現在 Admin Console 以進行權限設定。
* 若發生自訂權限服務無法回應的罕見情境時，預先定義的設定檔仍然可用，且預先定義的設定檔中的使用者仍具有適當存取權。

## 常見問題 {#faq}

### 哪些權限設定檔是預先定義的權限設定檔？

* 企業所有者
* 方案管理員
* 部署管理員
* 開發人員

如需深入了解預先定義的角色，請參閱[角色型權限](/help/requirements/role-based-permissions.md)。

### 引入自訂設定檔後，預先定義的權限設定檔會發生什麼情況？

預設之產品設定檔和 Cloud Manager 角色的運作方式不會改變。

### 我可以編輯預先定義的權限設定檔嗎？

不可以，預設設定檔不可編輯。您無法在預設的權限設定檔中新增或移除權限。您只能在預先定義的設定檔中新增或移除使用者。

### 由於現在可以使用自訂設定檔，我是否應該刪除預先定義的權限設定檔？

不可以從 Admin Console 刪除預先定義的權限設定檔。

### 我可以將使用者新增至多個權限設定檔嗎？

可以，一個使用者可以屬於多個設定檔，包括預先定義和自訂權限設定檔。當使用者被指派至多個設定檔時，該使用者可使用所有被指派權限設定檔的合併權限。

### 如果使用者擁有編輯環境/管道的權限，但無權存取包含該環境/管道的方案，會發生什麼情況？

在這個情境下，如果使用者沒有包含環境或管道的&#x200B;**方案存取**&#x200B;權限，則無法存取環境或管道。

### 如果我在同一個 IMS 組織中同時擁有 AEM as a Cloud Service 和 AMS 方案，會發生什麼事？我可以透過一個設定檔管理權限嗎？ {#ams-and-aemaacs}

為每個產品類型建立個別的設定檔。意即，建立一個用於 AEM as Cloud Service 的設定檔，再建立另一個用於 Adobe Managed Services 或 AMS 的設定檔。
