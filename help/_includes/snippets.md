---
source-git-commit: 9d910e1b1a4aad000a8389ddc22ce380bbccd4ef
workflow-type: tm+mt
source-wordcount: '57'
ht-degree: 0%

---
# 代碼片段(#snippets)

## 內容複製已知問題 {#content-copy-known-issues}

使用[內容複製功能](/help/using/content-copy.md)時，如果重新命名來源環境中的資源，可能會導致內容復製作業因目標環境中的UUID衝突而失敗。

為避免此錯誤，請首先刪除資源，然後使用所需的新資源名稱重新建立，而不是重新命名資源。