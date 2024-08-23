---
title: 環境佈建
description: 了解如何將您的環境佈建為 Cloud Manager 上線流程的一部分。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 36%

---


# 環境布建 {#environments-provisioning}

了解如何將您的環境佈建為 Cloud Manager 上線流程的一部分。

## 佈建 {#provisioning}

在上線流程中，Adobe會自動布建您購買的所有AEM雲端環境，並在[!UICONTROL Cloud Manager]中將它們連結至您的方案。 每個Managed ServicesAdobe訂閱都包含AEM雲端環境。 這些環境通常包括至少一個生產環境和一個中繼環境。 或者，您也可以選擇包含一或多個開發或測試環境。

## 歡迎電子郵件 {#welcome-email}

完成環境布建程式後，指定的客戶管理員會收到一封歡迎電子郵件，確認已授予他們對Adobe[!UICONTROL Experience Cloud]的存取權。 此歡迎電子郵件列有相關的詳細資訊，包括如何開始使用 [!UICONTROL Experience Cloud] 服務、[!UICONTROL AEM Managed Services] 雲端環境及 [!UICONTROL Cloud Manager] 自助服務入口網站。此外，該電子郵件還會包含一些重要資訊，例如客戶成功工程師 (CSE) 聯絡資訊、何處可取得支援資源、論壇、常見問題集等。在電子郵件中提供的資源清單中，您也會取得有關如何為您的AEM雲端環境存取[!UICONTROL Cloud Manager]的詳細資訊。

## 後續步驟 {#next-steps}

在收到歡迎電子郵件後，您就能使用您的 Adobe IMS 憑證，以系統管理員的身分登入 [!UICONTROL Cloud Manager]。登入後，您可以檢查您的AEM雲端生產和非生產環境是否可用並可順暢運作。

[!UICONTROL Cloud Manager]使用這些AEM雲端環境來執行CI/CD管道。 它將計畫碼從其Git存放庫部署到中繼環境。 然後它會將此程式碼部署到您的AEM生產環境。 當您準備好要開始建立Web屬性的數位體驗時，您也可以直接從[!UICONTROL Cloud Manager]存取您的AEM雲端環境。
