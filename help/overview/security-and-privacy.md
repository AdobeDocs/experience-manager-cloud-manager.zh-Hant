---
title: 安全性和隱私權
description: 瞭解Adobe Cloud Manager中程式碼和成品資產的安全性和隱私權。
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# 安全性和隱私權 {#security-and-privacy}

瞭解Adobe Cloud Manager中程式碼和成品資產的安全性和隱私權。

## 角色和權限 {#roles}

Cloud Manager 已預先設定角色，賦予適當權限。

若要了解有關您在 Admin Console 中可指派的角色以及使用者角色權限，請參閱[角色型權限](/help/requirements/role-based-permissions.md)。

## 資源隔離 {#resource-isolation}

Cloud Manager客戶需要他們的IMS憑證來進行身分驗證，因為所有繫結至Cloud Manager的許可權都與其IMS組織連結。 在上線流程中，布建團隊會確保在Cloud Manager中執行資源隔離。

## 資料安全性 {#data-security}

傳輸中會將Cloud Manager程式碼加密。 Cloud Manager會建置二進位檔，這些二進位檔也會在傳輸期間加密，並以加密格式儲存。

每個客戶都會有自己的Git存放庫，因此程式碼是安全的，不會與任何其他組織共用。

## 資料隱私權 {#data-privacy}

Cloud Manager會遵守由Adobe定義的隱私原則。 開發人員會經由 HTTPS 將程式碼安全地推送到 Git 存放庫中。

Cloud Manager的使用者介面會使用符合Adobe通用控制架構的服務。 Cloud Manager的使用者介面會使用來自數個雲端提供者的安全服務。
