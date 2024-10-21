---
title: 角色型權限
description: 了解 Cloud Manager 預先設定的角色型權限以管理對您的雲端資源的存取。
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 682b142f35bc233bad82b0ddfa69bc0f2d5b5fdb
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 100%

---


# 角色型權限 {#role-based-permissions}

[!UICONTROL Cloud Manager] 具有擁有適當權限的預先設定的角色。例如，開發人員會開發程式碼，並擁有將程式碼推送到 Git 存放庫的權限。企業所有者擁有不同的權限，讓他們能夠定義關鍵績效指標 (KPI) 及核准部署。

>[!NOTE]
>
>本文件旨在說明用於 Adob&#x200B;&#x200B;e Managed Services (AMS) 的 Cloud Manager 以角色為主的權限。
>
>AEM as a Cloud Service 同效文件可以在 AEM as a Cloud Service 文件的「[Cloud Manager 簡介](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions)」一文中找到。

## 使用者角色 {#user-roles}

[!UICONTROL Cloud Manager] 的角色管理可使用 [Admin Console](https://helpx.adobe.com/tw/enterprise/using/admin-console.html) 完成。[!UICONTROL Cloud Manager] 的任何使用者都必須是客戶的 IMS 組織成員，並擁有 Adobe Managed Services 產品內容。透過在 Admin Console 中將使用者新增到 [!UICONTROL Cloud Manager] 產品設定檔，可提供特定的角色會籍。

若要了解更多關於如何設定角色，請參閱「[設定使用者和角色](/help/requirements/users-and-roles.md)」。

下表列出您可以在 Admin Console 中指派的角色。

| [!UICONTROL Cloud Manager] 角色 | 說明 |
|---|---|
| 業務負責人 | 完成初始 [!UICONTROL Cloud Manager] 設定的主要使用者，而且負責定義 KPI、核准生產部署，並在必要時覆寫重要的 3 層級失敗。 |
| 內容作者 | 此使用者通常不會和 Cloud Manager 互動，但可能會使用 Cloud Manager 方案切換工具 (從 Experience Cloud 瀏覽過來) 來存取 Adobe Experience Manager (AEM)。 |
| 客戶成功工程師 | 此使用者主要支援 AMS 客戶成功，並與 [!UICONTROL Cloud Manager] 互動來執行部署。這些部署需要有 Adobe 客戶成功工程師 (CSE) 的監督。 |
| 部署管理員 | 此使用者會使用 [!UICONTROL Cloud Manager] 來管理部署操作，以執行中繼和生產部署，必要時可核准重要的 3 層級失敗，並可存取 Git 存放庫。 |
| 開發人員 | 此使用者會開發和測試自訂應用程式的程式碼，主要利用 [!UICONTROL Cloud Manager] 來檢視部署狀態，並擁有 Git 存放庫的認可存取權。 |
| 方案管理員 | 此使用者會使用 [!UICONTROL Cloud Manager] 來執行團隊設定、審查狀態、檢視 KPI，並在必要時核准重要的 3 層級失敗。 |

## 使用者權限 {#user-permissions}

每個角色都有其特定、相關聯的預先設定權限。下表列出可用權限，以及可執行這些權限的角色。

| 權限 | 說明 | 業務負責人 | 部署管理員 | 方案管理員 | 開發人員 | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| 讀取應用程式 | 讀取方案 KPI | x | x | x | x | x |
| 寫入應用程式 | 方案設定或編輯 | x | | | | |
| 新增方案 | 選取新方案 | x |  |  |  |  |
| 讀取環境 | 請參閱環境詳細資料 | x | x | x | x | x |
| 建立執行 | 啟動管道 | x | x | x | | |
| 讀取執行 | 啟動執行狀態 | x | x | x | x | x |
| 恢復執行 | 暫停狀態下恢復執行的能力 | x | x | x | | x |
| 執行核准部署至生產環境 | 提供上線核准 | x | x | x | | |
| 執行排程部署至生產環境 | 生產部署排程 | x | x | x | | x |
| 執行部署至生產環境 | 在因 CSE 監督而暫停時將應用程式部署到生產環境 |  |  |  |  | x |
| 執行取消 | 取消目前的執行 |  |  | x |  |  |
| 執行覆寫品質閘道失敗 | 核准重要品質閘道失敗 | x | x | x |  |  |
| 管道建立 | 設定 / 編輯管道 |  | x |  |  |  |
| 管道讀取 | 查看管道詳情 | x | x | x | x | x |
| 管道寫入 | 設定 / 編輯管道 |  | x |  |  |  |
| 管道修改核准 | 允許編輯企業所有者選項 |  | x |  |  |  |
| 管道修改受管理的部署 | 允許 CSE 監督選項的編輯 |  | x |  |  |  |
| 管道刪除 | 勇許管道刪除 |  | x |  |  |  |
| 步驟讀取 | 查看步驟品質量度結果 | x | x | x | x | x |
| 產生個人存取權杖 | 存取 Git |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

若要了解更多關於如何設定使用者，請參閱「[設定使用者和角色](/help/requirements/users-and-roles.md)」。

>[!TIP]
>
>也可以使用具有可設定設權限的自訂權限設定檔。如需更多詳細資訊，請參閱[自訂權限](/help/using/custom-permissions.md)。
