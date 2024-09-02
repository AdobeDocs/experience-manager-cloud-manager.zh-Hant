---
title: 環境佈建
description: 了解如何將您的環境佈建為 Cloud Manager 上線流程的一部分。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# 環境佈建 {#environments-provisioning}

了解如何將您的環境佈建為 Cloud Manager 上線流程的一部分。

## 佈建 {#provisioning}

於上線流程中，Adobe 會自動佈建您購買的所有 AEM 雲端環境，並將其連結至您在 [!UICONTROL Cloud Manager] 中的方案。每項 Adobe Managed Services 訂閱都包含 AEM 雲端環境。其通常會包括至少一種生產環境和一種中繼環境。或者，還可能包括一種或多種開發或測試環境。

## 歡迎電子郵件 {#welcome-email}

完成環境佈建流程後，指定的客戶管理員即會收到一封歡迎電子郵件，確認已授予他們對 Adobe [!UICONTROL Experience Cloud] 的存取權。此歡迎電子郵件列有相關的詳細資訊，包括如何開始使用 [!UICONTROL Experience Cloud] 服務、[!UICONTROL AEM Managed Services] 雲端環境及 [!UICONTROL Cloud Manager] 自助服務入口網站。此外，該電子郵件還會包含一些重要資訊，例如客戶成功工程師 (CSE) 聯絡資訊、何處可取得支援資源、論壇、常見問題集等。在電子郵件所提供的資源清單中，您還會取得有關如何為 AEM 雲端環境存取 [!UICONTROL Cloud Manager] 的詳細資訊。

## 後續步驟 {#next-steps}

在收到歡迎電子郵件後，您就能使用 Adobe IMS 憑證，以系統管理員的身分登入 [!UICONTROL Cloud Manager]。登入後，您可以確認 AEM 雲端生產環境及非生產環境是否可用且順暢運作。

[!UICONTROL Cloud Manager] 使用這些 AEM 雲端環境來執行 CI/CD 管道。它將 Git 存放庫中的程式碼部署至中繼環境。然後將程式碼部署至您的 AEM 生產環境。當您準備就緒要開始建立 Web 屬性的數位體驗時，也可以直接從 [!UICONTROL Cloud Manager] 存取您的 AEM 雲端環境。
