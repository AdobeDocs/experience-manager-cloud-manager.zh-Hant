---
title: 2022.1.0 版發行說明
description: 這些是Cloud Manager 2022.1.0版的發行說明。
feature: Release Information
exl-id: 9cc40326-cb8e-415f-b2ad-937d42189ee3
source-git-commit: 797731ff0f9a499fe359d2e4e6044877fdcac702
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 6%

---

# Cloud Manager版本2022.1.0的發行說明 {#release-notes}

以下部分概述了 [!UICONTROL Cloud Manager] 2022.1.0版。

>[!NOTE]
>
>有關as a Cloud Service中Cloud Manager的最新發AEM行說明，請參閱 [Cloud Manager(在AEMas a Cloud Service的當前發行說明中)。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 發行日期 {#release-date}

發放日期 [!UICONTROL Cloud Manager] 2022.1.0版為2022年1月20日。 下一版計畫於2022年2月10日發行。

## 新增功能 {#whats-new}

* 雲管理器將 [在檢測到使用了相同的git提交時避免重建代碼庫](/help/using/setting-up-project.md#build-artifact-reuse) 執行多個完整堆棧管道。
* 在生成Git密碼時，將顯示過期日期。

## 錯誤修正 {#bug-fixes}

* 已解決錯誤陽性管道故障的不頻繁發生。
* 對於只有一個儲存庫的程式，管道執行螢幕現在將顯示儲存庫名稱。