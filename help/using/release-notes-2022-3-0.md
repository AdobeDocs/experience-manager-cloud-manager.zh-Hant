---
title: 2022.3.0 版發行說明
description: 這些是Cloud Manager 2022.3.0版的發行說明。
feature: Release Information
source-git-commit: f1d359921a11ab8a6117a15cd5eb72362bbb8360
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 4%

---


# Cloud Manager版本2022.3.0的發行說明 {#release-notes}

此頁記錄的發行說明 [!UICONTROL Cloud Manager] 2022.3.0版。

>[!NOTE]
>
>有關as a Cloud Service中Cloud Manager的最新發AEM行說明，請參閱 [Cloud Manager(在AEMas a Cloud Service的當前發行說明中)。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 發行日期 {#release-date}

發放日期 [!UICONTROL Cloud Manager] 2022.3.0版為2022年3月10日。 下一版計畫於2022年4月7日發行。

## 新增功能 {#what-is-new}

* 來自資產test的出站HTTP請求現在將來自固定IP範圍。


## 錯誤修正 {#bug-fixes}

* 的 **跳過負載平衡器更改** 無法禁用。
* 的 **跳過負載平衡器更改** 選項未顯示在AMS上。開發部署 **編輯管道工作流**。
* 手動建立的Git儲存庫的子集具有不正確的名稱值，這防止了生成項目重用功能的有效性。 這些資料庫的名稱已更改，用戶將在Cloud Manager API/UI中看到更正的名稱。
* 來自非生產管道的生成工件在生產完整堆棧管道上被不恰當地重複使用。
* 添加或編輯代碼質量管道時，不再顯示處理度量失敗的選項。
* 生成步驟中可能會導致某些意外的管道變數配置。