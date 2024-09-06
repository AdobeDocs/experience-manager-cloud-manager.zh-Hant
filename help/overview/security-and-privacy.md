---
title: 安全性和隱私權
description: 了解 Cloud Manager 中程式碼和成品資產的安全性和隱私權。
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '202'
ht-degree: 100%

---


# 安全性和隱私權 {#security-and-privacy}

了解 Cloud Manager 中程式碼和成品資產的安全性和隱私權。

## 角色和權限 {#roles}

[!UICONTROL Cloud Manager] 具有擁有適當權限的預先設定的角色。

若要了解有關您在 Admin Console 中可指派的角色以及使用者角色權限，請參閱[角色型權限](/help/requirements/role-based-permissions.md)。

## 資源隔離 {#resource-isolation}

[!UICONTROL Cloud Manager] 客戶需要他們的 IMS 憑證來進行身分驗證，因為所有繫結至 [!UICONTROL Cloud Manager] 的權限都與其 IMS 組織連結。在上線流程中，佈建團隊會確保在 [!UICONTROL Cloud Manager] 中執行資源隔離。

## 資料安全性 {#data-security}

傳輸中會將 [!UICONTROL Cloud Manager] 中的程式碼加密。Cloud Manager 建置的二進位檔在傳輸過程中會加密，並在儲存時進行加密。

每個客戶都有自己的 Git 存放庫，而且程式碼受到保護，不會和任何其他組織共用。

## 資料隱私權 {#data-privacy}

[!UICONTROL Cloud Manager] 會遵守由 Adobe 定義的隱私權原則。開發人員會經由 HTTPS 將程式碼安全地推送到 Git 存放庫中。

[!UICONTROL Cloud Manager] 的使用者介面建置在符合 Adobe 通用控制框架的服務上。[!UICONTROL Cloud Manager] 的使用者介面會使用來自數個雲端提供者的安全服務。
