---
title: 在Cloud Manager中管理存取權杖
description: 瞭解如何在Adobe Managed Services上檢視、編輯和刪除用於在Cloud Manager中自攜Git的存取權杖。
badge: label="私人測試版" type="Positive" url="/help/release-notes/current.md#access-tokens"
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
source-git-commit: 254ad0ac77e793657292e34ae4a6bf3baecea8d5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 3%

---

# 管理外部存放庫的存取權杖 {#manage-access-tokens}

Cloud Manager使用存取權杖來管理託管於外部Git平台上的存放庫。 先前，如果權杖過期，關聯的存放庫必須重新上線才能保持運作。

現在，**管理存取權杖**&#x200B;功能可讓您更有效率地管理權杖。 您可以檢視、重新命名或移除連線至受支援外部Git提供者（包括GitHub Enterprise、GitLab、Bitbucket和Azure DevOps）的Token。

另請參閱[在Cloud Manager中新增外部存放庫](/help/managing-code/external-repositories.md)。

>[!NOTE]
>
>本文所述的功能只能透過私人測試版計畫取得。 如需詳細資訊以及註冊私人測試版，請參閱[管理存取權杖](/help/release-notes/current.md#access-tokens)。

## 檢視存取權杖 {#view-access-tokens}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 登入 Cloud Manager 並選取適當的組織。
1. 在&#x200B;**[我的程式](/help/getting-started/navigation.md#my-programs-console)**&#x200B;主控台上，選取您要管理其「自攜Git」存取權杖的程式。
1. 在側邊功能表的&#x200B;**方案**&#x200B;下，按一下![資料夾大綱圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **存放庫**。
1. 在頁面的右上角附近，按一下&#x200B;**管理存取權杖**。

   **管理存取權杖**&#x200B;按鈕僅在您的程式使用自攜Git功能時可見。

   ![管理存取權杖對話方塊列出一個使用中的權杖和一個使用中的權杖](/help/managing-code/assets/access-tokens-manage.png)

1. 在&#x200B;**管理存取權杖**&#x200B;對話方塊中：
   * 所有存取權杖都會列出。
   * 您可以&#x200B;**編輯**&#x200B;任何權杖。
   * 您只能&#x200B;**刪除** *目前未使用*&#x200B;的權杖。 如果語彙基元正在使用中，![刪除大綱圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)按鈕會停用。

## 編輯存取權杖 {#edit-access-tokens}

1. 在&#x200B;**管理存取權杖**&#x200B;對話方塊中，在權杖名稱的右側，按一下![編輯圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg)。
1. 在&#x200B;**編輯存取權杖**&#x200B;對話方塊中，更新&#x200B;**權杖名稱**&#x200B;或&#x200B;**存取權杖**&#x200B;值，或兩者皆更新。

   ![編輯存取權杖對話方塊](/help/managing-code/assets/access-tokens-edit.png)

1. 如果&#x200B;**存取Token**&#x200B;目前正在使用中，則會出現通知警告您，所有關聯的存放庫都會在更新後自動重新驗證。

1. 按一下&#x200B;**更新**&#x200B;以儲存變更。

## 刪除存取權杖 {#delete-access-token}

1. 在&#x200B;**管理存取權杖**&#x200B;對話方塊中，在權杖名稱的右側，按一下![刪除圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   目前使用中的權杖的圖示已停用（![刪除大綱圖示](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)）。

1. 在&#x200B;**刪除存取權杖**&#x200B;對話方塊中，按一下&#x200B;**刪除**&#x200B;以永久移除權杖。
