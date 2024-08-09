---
title: 存放庫存取資訊
description: 了解如何使用 Cloud Manager 中的自助 Git 帳戶管理存取和管理您的 Adobe 託管 Git 存放庫。
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 82%

---

# 存放庫存取資訊 {#accessing-repos}

了解如何使用 Cloud Manager 中的自助 Git 帳戶管理存取和管理您的 Adobe 託管 Git 存放庫。

## 從概觀頁面存取存放庫資訊 {#overview-page}

Cloud Manager 可以使用管道資訊卡上顯眼的&#x200B;**存取存放庫資訊**&#x200B;按鈕，輕鬆針對 Adobe 託管的存放庫擷取您的存放庫資訊。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織和方案。

1. 從&#x200B;**方案概觀**&#x200B;頁面導覽至&#x200B;**管道資訊**&#x200B;卡。

   ![環境卡片上的存取存放庫資訊按鈕](assets/pipelines-card.png)

1. 按一下&#x200B;**存取存放庫資訊**&#x200B;按鈕，開啟&#x200B;**存放庫資訊**&#x200B;對話方塊並檢視：

   * Git 使用者名稱。
   * Git 密碼。
   * Cloud Manager Git 存放庫的 URL。
   * 預先建立 Git 指令可快速新增遠端連線至 Git 存放庫並推送程式碼。

   ![存放庫資訊視窗](assets/access-repo-info.png)

1. 若要存取密碼，必須產生新密碼。若要這麼做，請按一下&#x200B;**產生密碼**&#x200B;按鈕。

1. 按一下&#x200B;**產生密碼**，在&#x200B;**對話方塊中確認產生密碼。**

   ![確認產生密碼](assets/confirm-password-generation.png)

1. 密碼已產生，並會顯示在「**密碼**」欄位中供複製。

   * 產生密碼後，先前的密碼即會失效。
   * Cloud Manager 不會儲存密碼。您有責任以安全方式儲存該密碼。
   * 由於 Cloud Manager 不會儲存密碼，因此如果遺失密碼，您就必須重新產生新密碼。

   ![產生的密碼範例](assets/generated-password.png)

若使用這些憑證，您可以複製存放庫的本機副本，並在該本機存放庫中進行變更，且在準備好後可以將任何程式碼變更提交回 Cloud Manager 中的遠端程式碼存放庫。

>[!NOTE]
>
>* 擁有&#x200B;**開發人員**&#x200B;或&#x200B;**部署管理員**&#x200B;角色的使用者可看見該&#x200B;**存取存放庫資訊**&#x200B;選項。
>* 「**Access 存放庫資訊**」按鈕只會顯示 Adob&#x200B;&#x200B;e 託管存放庫的存放庫存取資訊。Cloud Manager 不會提供[私人存放庫](private-repositories.md) 的存取資訊。

## 從「存放庫視窗」存取存放庫資訊 {#repositories-window}

[**存放庫**&#x200B;視窗](managing-repositories.md)的工具列中也提供&#x200B;**存取存放庫資訊**&#x200B;按鈕，它顯示有關存取Adobe管理的存放庫的相同資訊。

## 撤銷存取密碼 {#revoke-password}

您可以隨時撤銷存取密碼。若要這麼做，[為此要求](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)建立支援票證。

此服務單將會獲得最優先處理，並應該會在一天內撤銷。
