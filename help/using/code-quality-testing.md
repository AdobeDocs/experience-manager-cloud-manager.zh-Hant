---
title: 程式碼品質測試
description: 了解管道程式碼品質測試如何運作及如何提高部署品質。
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: fadcf560f08bf16d0d18172c620a450d0cb06225
workflow-type: tm+mt
source-wordcount: '2778'
ht-degree: 61%

---


# 程式碼品質測試 {#code-quality-testing}

了解管道程式碼品質測試如何運作及如何提高部署品質。

## 簡介 {#introduction}

在管道執行期間，軟體會擷取多個量度。 這些量度接著會與企業所有者定義的關鍵績效指標(KPI)比較。 或者，這些量度會與AdobeManaged Services所設定的標準進行比較。

這些結果會使用三層級評等系統報告。

## 三層級評等 {#three-tiered-ratings}

在管道內有三個閘道：

* 程式碼品質
* 效能測試
* 安全測試

對於這些閘道中的每一個，閘道識別的問題都有一個三層結構。

* **嚴重** — 導致管道立即失敗的問題。
* **重要** — 導致管道進入暫停狀態的問題。 部署管理員、專案管理員或企業所有者可以覆寫問題。 如果它們這樣做，則管道會按預期進行。 或者，他們可以接受問題，導致管道因失敗而停止。 覆寫重要失敗時不得超過[逾時](/help/using/code-deployment.md#timeouts)。
* **資訊** — 純粹為了參考目的而提供，對管道執行沒有影響的問題。

>[!NOTE]
>
>在僅限程式碼品質的管道中，不能覆寫程式碼品質閘道中的重要失敗，因為程式碼品質測試步驟是管道中的最後一步。

## 程式碼品質測試 {#code-quality-testing-step}

此測試步驟會評估應用程式程式碼的品質，這是僅限程式碼品質管道的主要用途。 它會在所有非生產和生產管道中的建置步驟之後立即執行。 若要深入瞭解，請前往[設定非生產管道](/help/using/non-production-pipelines.md)。

計畫碼品質測試會掃描原始計畫碼以確保其符合特定的品質標準。

軟體會使用SonarQube分析、OakPAL的內容套件層級檢查和使用Dispatcher最佳化工具的Dispatcher驗證的組合來實作它。

有100多條規則結合了通用Java規則和AEM特定規則。 部分 AEM 特定規則是根據 AEM 工程團隊的最佳做法建立的，並被稱為[自訂程式碼品質規則。](/help/using/custom-code-quality-rules.md)

>[!TIP]
>
>若要下載完整的規則清單，可[使用此連結。](/help/assets/CodeQuality-rules-latest-AMS.xlsx)

程式碼品質測試的結果會以此表格中總結的評分提供。

| 名稱 | 定義 | 類別 | 失敗臨界值 |
|--- |--- |--- |--- |
| 安全評等 | A = 無漏洞<br/>B = 至少 1 個輕微漏洞<br/>C = 至少 1 個重大漏洞<br/>D = 至少 1 個嚴重漏洞<br/>E = 至少 1 個阻斷式漏洞 | 嚴重 | &lt; B |
| 可靠度評等 | A = 無錯誤<br/>B = 至少 1 個輕微錯誤<br/>C = 至少 1 個重大錯誤<br/>D = 至少 1 個嚴重錯誤<br/>E = 至少 1 個阻斷式錯誤 | 重要 | &lt; C |
| 可維護性評等 | 由程式碼異味的待處理修復成本定義為已進入應用程式的時間的百分比<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | 重要 | &lt; A |
| 適用範圍 | 使用以下公式將單位測試行適用範圍和條件適用範圍混合後定義：<br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = 在執行單位測試時已經至少一次評估為 `true` 的條件</li><li>`CF` = 在執行單位測試時已經至少一次評估為 `false` 的條件</li><li>`LC` = 適用行數 = lines_to_cover - uncovered_lines</li><li>`B` = 條件總數</li><li>`EL` = 可執行行的總數 (lines_to_cover)</li></ul> | 重要 | &lt; 50% |
| 略過的單位測試 | 略過的單位測試總數 | 資訊 | > 1 |
| 未解決的問題 | 整體問題類型 - 漏洞、錯誤和程式碼異味 | 資訊 | > 0 |
| 重複的行 | 定義為重複區塊中包含的行數。在以下條件下，會將程式碼區塊視為重複。<br>非 Java 專案：<ul><li>應該至少有 100 個連續和重複的權杖。</li><li>這些權杖應至少分佈在： </li><li>COBOL 的 30 行程式碼 </li><li>ABAP 的 20 行程式碼 </li><li>其他語言的 10 行程式碼</li></ul>Java 專案：<ul></li><li> 無論權杖和行的數量如何，應至少有 10 個連續和重複的陳述式。</li></ul>偵測重複時會忽略縮排和字串常值中的差異。 | 資訊 | > 1% |
| 雲端服務相容性 | 識別出的雲端服務相容性問題的數量 | 資訊 | > 0 |

>[!NOTE]
>
>如需詳細資訊，[SonarQube的量度定義](https://docs.sonarsource.com/sonarqube/latest/user-guide/code-metrics/metrics-definition/)。

>[!NOTE]
>
>若要了解由 [!UICONTROL Cloud Manager] 執行的自訂程式碼品質規則的詳細資訊，請參閱文件：[自訂程式碼品質規則。](custom-code-quality-rules.md)

### 處理誤判 {#dealing-with-false-positives}

品質掃描流程並非完美無瑕，有時會錯誤地識別出實際上不構成問題的問題。 這種情況稱為誤判。

在這些情況下，可以使用標準 Java `@SuppressWarnings` 註解來標註原始程式碼，將規則 ID 指定為註解屬性。例如，一種常見的誤判是用於偵測硬式編碼密碼的 SonarQube 規則可能對如何識別硬式編碼密碼過於積極。

以下程式碼在 AEM 專案中相當常見，其中包含連接到某些外部服務的程式碼。

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube因此提出阻斷式漏洞。 但在檢視程式碼後，您會發現此問題並非漏洞，然後可以使用適當的規則ID標註程式碼。

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

不過，如果程式碼實際為下列專案：

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

則正確的解決方案是移除硬式編碼的密碼。

>[!NOTE]
>
>最佳實務是儘可能使`@SuppressWarnings`註解具體。 也就是說，僅標註導致問題的特定陳述式或區塊。 但是，可以在類別層級進行註解。 這麼做可更廣泛地隱藏警告。

## 安全測試 {#security-testing}

[!UICONTROL Cloud Manager] 會在部署後在中繼環境上執行現有 AEM 安全性的健康情況檢查並透過 UI 報告狀態。該結果會由環境中的所有 AEM 執行個體彙總而成。

上述相同的健康情況檢查可隨時透過 Web 控制台或操作儀表板執行。

如果任何執行個體報告特定的健康情況檢查出現失敗，則整個環境即無法通過該健康情況檢查。和程式碼品質和效能測試一樣，這些健康情況檢查會被歸類並使用三層級閘道系統進行報告。唯一的區別是，如果有安全性測試，則沒有臨界值。 所有的健康情況檢查結果都會是成功或失敗。

下表為健康情況檢查的清單。

| 名稱 | 健康情況檢查實作 | 類別 |
|---|---|---|
| 還原序列化防火牆附加 API 整備處於可接受的狀態。 | [還原序列化防火牆附加 API 整備](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | 嚴重 |
| 還原序列化防火牆可正常運作。 | [還原序列化防火牆正常運作](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | 嚴重 |
| 載入還原序列化防火牆。 | [還原序列化防火牆已載入](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | 嚴重 |
| `AuthorizableNodeName` 實作不會在節點名稱/路徑中揭露可授權 ID。 | [可授權節點名稱產生](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/security/security-checklist#security) | 嚴重 |
| 已變更預設密碼。 | [預設登入帳戶](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security#users-and-groups-in-aem) | 嚴重 |
| Sling 預設的 GET servlet 受到保護，免於 DOS 攻擊。 | Sling Get Servlet | 嚴重 |
| Sling JavaScript處理常式已正確設定。 | Sling JavaScript處理常式 | 嚴重 |
| 已正確設定 Sling JSP 指令碼處理常式。 | Sling JSP 指令碼處理常式 | 嚴重 |
| 已正確設定 SSL。 | SSL 設定 | 嚴重 |
| 未找到明顯不安全的使用者設定檔原則。 | 使用者設定檔預設存取 | 嚴重 |
| Sling查閱者篩選器已設定為防止CSRF攻擊。 | [Sling 查閱者篩選器](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/security/security-checklist#security) | 重要 |
| 已正確設定 Adobe Granite HTML 資料庫管理員。 | CQ HTML 資料庫管理員組態 | 重要 |
| 已停用 CRXDE 支援套裝。 | CRXDE 支援 | 重要 |
| 已停用 Sling DavEx 套裝和 servlet。 | DavEx 健康情況檢查 | 重要 |
| 未安裝樣本內容。 | 範例內容套件 | 重要 |
| 已停用 WCM 請求篩選器和 WCM 偵錯篩選器。 | [WCM 篩選器設定](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/osgi-configuration-settings#configuring) | 重要 |
| 已正確設定 Sling WebDAV 套裝和 servlet。 | WebDAV 健康情況檢查 | 重要 |
| 已設定 Web 伺服器來預防 clickjacking。 | Web 伺服器組態 | 重要 |
| 複寫並非使用 `admin` 使用者。 | 複寫及傳輸使用者 | 資訊 |

## 效能測試 {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager 會執行 AEM Sites 的效能測試。效能測試會透過旋轉虛擬使用者 (容器) 來執行大約 30 分鐘，這些虛擬使用者 (容器) 會模擬實際使用者來存取中繼環境中的頁面以模擬流量。這些頁面是使用編目程式找到的。

#### 虛擬使用者 {#virtual-users}

Cloud Manager會根據&#x200B;**企業所有者**&#x200B;角色所設定的KPI （回應時間和每分鐘的頁面檢視次數），旋轉虛擬使用者或容器。 這些KPI是在[建立或編輯方案](/help/getting-started/program-setup.md)時設定的。

根據定義的KPI，最多會旋轉十個模擬實際使用者的容器。 為了進行測試所選取的頁面將被分割並分配給每個虛擬使用者。

#### 編目程式 {#crawler}

在30分鐘測試期開始之前，Cloud Manager會使用客戶成功工程師設定的一組一或多個種子URL來耙梳中繼環境。 從這些 URL 開始，請檢查每個頁面的 HTML，並以廣度優先方式點選所有連結。

* 預設情況下，此耙梳流程的上限為 5000 個頁面。
* 透過設定[管道變數](/help/getting-started/build-environment.md#pipeline-variables)`CM_PERF_TEST_CRAWLER_MAX_PAGES`，可覆寫要測試的最大頁數。
   * 允許值為 `2000` - `7000`。
* 來自編目程式的請求固定逾時時間為 10 秒。

#### 測試的頁面集 {#page-sets}

三個頁面集可選取頁面。 Cloud Manager 會使用來自生產和中繼環境中的 AEM 執行個體的存取紀錄來決定以下貯體。

* **熱門的即時頁面** — 確保對線上客戶所存取的最受歡迎頁面進行測試。 Cloud Manager會讀取存取記錄檔並決定線上客戶存取次數最多的前25個頁面，以產生前`Popular Live Pages`個頁面的清單。 然後在中繼環境中對也出現在中繼環境中的這些頁面的交集進行耙梳。

* **其他即時頁面** — 確保對可能不受歡迎但對測試卻很重要的前25個熱門即時頁面以外的頁面進行測試。 和熱門的即時頁面類似，這些頁面都是從存取記錄檔擷取的，而且也必定會出現在中繼環境中。

* **新頁面** — 測試新頁面，這些新頁面可能僅部署到中繼環境，但尚未部署到生產環境，但必須進行測試。

##### 跨所選頁面組的流量分佈 {#distribution-of-traffic}

您可以在[管道設定的&#x200B;**測試**&#x200B;索引標籤上從一組到全部三組中進行選擇。](/help/using/production-pipelines.md) 流量的分佈會根據所選的組數。也就是說，如果選取全部三組，則會將總頁面檢視次數的33%放入每組。 如果選取兩組，則 50% 流向每組。如果選取了一組，則 100% 的流量將流向該組。

讓我們考慮以下範例。

* 熱門的即時頁面和新頁面組之間的比例為 50/50。
* 不使用其他即時頁面。
* 新頁面組包含 3000 頁。
* 每分鐘&#x200B;*的KPI*&#x200B;頁面檢視次數設為200。

超過 30 分鐘測試期：

* 熱門即時頁面組中的25頁的每一頁都有120次點選： `((200 * 0.5) / 25) * 30 = 120`
* 新頁面組中的3000頁的每一頁都會被點選一次： `((200 * 0.5) / 3000) * 30 = 1`

#### 測試與報告 {#testing-reporting}

Cloud Manager 會在中繼發佈伺服器上以預設的未經驗證使用者的身分來請求頁面，從而執行 AEM Sites 方案的效能測試，測試期為 30 分鐘。它會測量每個頁面的虛擬使用者產生的測量結果（回應時間、錯誤率、每分鐘的檢視次數等等），以及所有執行個體的各種系統層級測量結果（CPU、記憶體、網路資料）。

下表會概述使用三層級閘道系統的效能測試矩陣。

| 量度 | 類別 | 失敗臨界值 |
|---|---|---|
| 頁面請求錯誤率 | 嚴重 | >= 2% |
| CPU 使用情況 | 嚴重 | >= 80% |
| 磁碟 IO 等候時間 | 嚴重 | >= 50% |
| 第 95 百分位數的回應時間 | 重要 | >= 方案層級 KPI |
| 尖峰回應時間 | 重要 | >= 18 秒 |
| 每分鐘的頁面檢視次數 | 重要 | &lt; 方案層級 KPI |
| 磁碟頻寬使用率 | 重要 | >= 90% |
| 網路頻寬使用率 | 重要 | >= 90% |
| 每分鐘的請求次數 | 資訊 | >= 6000 |

如需有關使用基本驗證對網站和資產進行效能測試的更多詳細資訊，請參閱[已驗證的效能測試](#authenticated-performance-testing)一節。

>[!NOTE]
>
>在測試期間會監控作者和發佈執行個體。 如果未取得某個執行個體的任何量度，則會將該量度報告為未知，且對應的步驟會失敗。

#### 已驗證的效能測試 {#authenticated-performance-testing}

如有必要，擁有已驗證網站的AMS客戶可以指定Cloud Manager在網站效能測試期間用於存取網站的使用者名稱和密碼。

可將使用者名稱和密碼指定為名為 `CM_PERF_TEST_BASIC_USERNAME` 和 `CM_PERF_TEST_BASIC_PASSWORD` 的管道變數。

使用者名稱儲存在`string`變數中，而密碼儲存在`secretString`變數中。 如果同時指定這兩個變數，則來自效能測試編目程式和測試虛擬使用者的每個請求都包含這些認證作為HTTP基本驗證。

若要使用 Cloud Manager CLI 設定這些變數，請執行：

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

若要瞭解如何使用API，請參閱[修補程式使用者管道變數](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) API檔案。

### AEM Assets {#aem-assets}

Cloud Manager會透過重複上傳資產達30分鐘來執行AEM Assets方案的效能測試。

#### 上線要求 {#onboarding-requirement}

針對Assets效能測試，您的客戶成功工程師會在作者加入中繼環境期間建立`cloudmanager`使用者及密碼。 效能測試步驟需要名為`cloudmanager`的使用者以及由您的CSE設定的相關密碼。

此方法應保留在作者執行個體中，其許可權不變。 變更或移除此功能可能會導致Assets效能測試失敗。

#### 測試的影像和資產 {#assets-for-testing}

客戶可上傳他們自己的資產供測試。此程式可以從&#x200B;**管道設定**&#x200B;或&#x200B;**編輯**&#x200B;畫面完成。 支援 JPEG、PNG、GIF 和 BMP 等常見影像格式以及 Photoshop、Illustrator 和 Postscript 檔案。

如果未上傳任何影像，Cloud Manager會使用預設的影像和PDF檔案進行測試。

#### 測試的資產分佈 {#distribution-of-assets}

在&#x200B;**管道設定**&#x200B;或&#x200B;**編輯**&#x200B;畫面中設定了每分鐘上傳的每種類型的資產數量分佈。

例如，如果使用70/30分割法，且每分鐘上傳10個資產，則每分鐘會上傳7個影像和3個檔案。

#### 測試與報告 {#testing-and-reporting}

Cloud Manager會使用CSE設定的使用者名稱和密碼在作者執行個體上建立資料夾。 然後使用開放原始程式碼資料庫將資產上傳到檔案夾。資產測試步驟執行的測試會使用[開放原始程式碼資料庫編寫。](https://github.com/adobe/toughday2) 在 30 分鐘的測試期間內會對每個資產的處理時間以及各種系統層級量度進行測量。此功能可上傳影像和 PDF 文件。

>[!TIP]
>
>請參閱[設定生產管道](/help/using/production-pipelines.md)以瞭解更多資訊。 請參閱[方案設定](/help/getting-started/program-setup.md)，瞭解如何設定方案並定義您的KPI。

### 效能測試結果圖 {#performance-testing-results-graphs}

在&#x200B;**效能測試對話框**&#x200B;中可提供幾種量度

![量度清單](/help/assets/understand_test-results-screen1.png)

可將量度面板展開以顯示圖表、提供下載連結或兩者同時進行。

![展開為圖表的量度](/help/assets/screen_shot_2018-09-05at83933pm.png)

此功能適用於以下量度。

* **CPU 使用情況** - 測試期間 CPU 使用率的圖表

* **磁碟 I/O 等候時間** - 測試期間磁碟 I/O 等候時間圖

* **頁面錯誤率** - 測試期間每分鐘頁面錯誤數量圖
   * CSV檔案包含在測試期間產生錯誤的頁面清單

* **磁碟頻寬使用情況** - 測試期間磁碟頻寬使用情況的圖表

* **網路頻寬使用情況** - 測試期間網路頻寬使用情況的圖表

* **尖峰回應時間** - 測試期間每分鐘尖峰回應時間圖

* **第 95 百分位數的回應時間** - 測試期間每分鐘第 95 百分位數回應時間的圖表
   * CSV 檔案包含第 95 百分位數回應時間已超過定義的 KPI 的頁面清單

## 掃描最佳化的內容套件 {#content-package-scanning-optimization}

在品質分析流程中，Cloud Manager 會對 Maven 組建產生的內容套件進行分析。Cloud Manager提供最佳化功能，可加速此流程，若需遵守某些套件限制，前述功能即有助益。

主要最佳化是針對輸出單一「全」套件的專案，其中會包含由組建產生並標籤為已略過的其他內容套件。 當 Cloud Manager 偵測到這種情況時，會直接掃描個別內容套件並根據相依性進行排序，而不是將「全」套件解除封裝。例如，考慮以下組建輸出。

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

如果 `myco-all-1.0.0-SNAPSHOT.zip` 內的項目只有兩個已略過的內容套件，則掃描這兩個嵌入的套件而不是「所有」內容套件。

對於產生數十個嵌入套件的專案，已證明這種最佳化將在每次管道執行節省 10 分鐘以上的時間。

當「全」內容套件包含已略過的內容套件和 OSGi 套裝的組合時，可能會出現一種特殊情況。例如，如果 `myco-all-1.0.0-SNAPSHOT.zip` 包含前面提到的兩個嵌入套件以及一個或多個 OSGi 套裝，則會建構出一個全新、最小的內容套件，且僅包含 OSGI 套裝。此套件一律名為 `cloudmanager-synthetic-jar-package`，而且會將所包含的套裝放在 `/apps/cloudmanager-synthetic-installer/install` 中。

>[!NOTE]
>
>* 此最佳化不會影響部署至AEM的套件。
>* 內嵌和略過的內容套件之間的比對是根據檔案名稱。 如果多個已略過的內容套件共用相同的檔案名稱，或檔案名稱在內嵌期間有所變更，此最佳化則會失敗。
