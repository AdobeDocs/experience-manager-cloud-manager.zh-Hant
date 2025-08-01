---
title: 自訂程式碼品質規則
description: 探索 Cloud Manager 在程式碼品質測試過程中執行的自訂程式碼品質規則的具體細節。這些規則以 AEM Engineering 的最佳實務為基礎。
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '3636'
ht-degree: 95%

---


# 自訂程式碼品質規則 {#custom-code-quality-rules}

根據來自 AEM 工程團隊的最佳做法，了解 Cloud Manager 在[程式碼品質測試過程](/help/using/code-quality-testing.md)中執行的自訂程式碼品質規則的詳細資訊。

>[!NOTE]
>
>在此提供的程式碼範例僅供說明用途。請參閱 [SonarQube 的概念文件說明](https://docs.sonarsource.com/sonarqube-server/latest/)以了解其中的概念和品質規則。

由於 Adobe 專屬資訊，完整的 SonarQube 規則無法下載。若要下載完整的規則清單，可[使用此連結](/help/assets/CodeQuality-rules-latest-AMS.xlsx)。繼續閱讀本文件以取得規則的說明和範例。

>[!IMPORTANT]
>
>從 2025 年 2 月 13 日 (星期四) (Cloud Manager 2025.2.0) 開始，Cloud Manager 程式碼品質將使用更新後的 SonarQube 9.9 版本和更新後的規則清單 (可[在此處下載](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx))。

## SonarQube 規則 {#sonarqube-rules}

下節會詳細介紹由 Cloud Manager 執行的 SonarQube 規則。

### 請勿使用有潛在危險的功能 {#do-not-use-potentially-dangerous-functions}

* **索引碼**：CQRules:CWE-676
* **類型**：漏洞
* **嚴重度**：重大
* **始自**：2018.4.0 版本

方法 `Thread.stop()` 和 `Thread.interrupt()` 可能產生難以重現的問題，有時還可能產生安全性漏洞。它們的使用應受到嚴密監控和驗證。總的來說，傳遞資訊是實現類似目標的更安全的方式。

#### 不符合規範的程式碼 {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### 符合規範的程式碼 {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### 請勿使用可能受外部控制的格式字串 {#do-not-use-format-strings-which-may-be-externally-controlled}

* **索引碼**：CQRules:CWE-134
* **類型**：漏洞
* **嚴重度**：重大
* **始自**：2018.4.0 版本

使用來自外部來源的格式字串 (例如請求參數或使用者產生的內容) 可能會讓應用程式面臨阻絕服務攻擊。在某些情況下，格式字串可能會受到外部控制，但是僅限受信任的來源。

#### 不符合規範的程式碼 {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 要求始終都應該有通訊端和連線逾時 {#http-requests-should-always-have-socket-and-connect-timeouts}

* **索引碼**：CQRules:ConnectionTimeoutMechanism
* **類型**：錯誤
* **嚴重度**：嚴重
* **始自**：2018.6.0 版本

從 AEM 應用程式內部執行 HTTP 要求時，務必要設定適當的逾時，以避免不必要的執行緒消耗。很遺憾，Java™ 的預設 HTTP 用戶端 (`java.net.HttpUrlConnection`) 和廣泛使用的 Apache HTTP Components 用戶端都沒有預設逾時。因此必須明確設定逾時。依據最佳實務的要求，這些逾時不應超過 60 秒。

#### 不符合規範的程式碼 {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### 符合規範的程式碼 {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### `ResourceResolver` 物件應保持關閉 {#resourceresolver-objects-should-always-be-closed}

* **索引碼**：CQRules:CQBP-72
* **類型**：`Code Smell`
* **嚴重度**：重大
* **始自**：2018.4.0 版本

`ResourceResolver` 物件 (取自 `ResourceResolverFactory`) 會消耗系統資源。儘管現有一些措施可供不再使用 `ResourceResolver` 時回收這些資源，但透過呼叫 `close()` 方法明確關閉任何開啟的 `ResourceResolver` 物件會更有效率。

有一個常見的誤解，以為不應該明確關閉使用現有 JCR 工作階段建立的 `ResourceResolver` 物件。另一個常見誤解是，關閉這些物件會關閉底層的 JCR 工作階段。情況並非如此。無論如何開啟 `ResourceResolver`，不使用時都應關閉。由於 `ResourceResolver` 實施 `Closeable` 介面，也有可能使用 `try-with-resources` 語法，而不是明確地叫用 `close()`。

#### 不符合規範的程式碼 {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### 符合規範的程式碼 {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### 請勿使用 Sling Servlet 路徑註冊 Servlet {#do-not-use-sling-servlet-paths-to-register-servlets}

* **索引碼**：CQRules:CQBP-75
* **類型**：`Code Smell`
* **嚴重度**：重大
* **始自**：2018.4.0 版本

如[Sling檔案](https://sling.apache.org/documentation/the-sling-engine/servlets.html)中所述，不建議按路徑繫結servlet。 路徑繫結的 servlet 不能使用標準的 JCR 存取控制，因此需要額外嚴格的安全性。建議不要使用路徑繫結的 servlet，而是在存放庫中建立節點並按資源類型註冊 servlet。

#### 不符合規範的程式碼 {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### 應記錄或擲回攔截到的例外狀況，而非執行兩者。 {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **索引碼**：CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

一般而言，應該只記錄一次例外狀況。多次記錄例外狀況可能會造成混淆，因為不清楚發生過多少次例外狀況。造成這個問題的最常見模式是記錄並擲回所發現的例外狀況。

#### 不符合規範的程式碼 {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### 符合規範的程式碼 {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### 避免 Log 陳述式後馬上接著 Throw 陳述式 {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **索引碼**：CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

另一個要避免的常見模式是記錄一則訊息後立即擲回例外狀況。此問題通常表示記錄檔案中有重複的例外狀況訊息。

#### 不符合規範的程式碼 {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### 符合規範的程式碼 {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### 處理 GET 或 HEAD 要求時避免在 INFO 上進行記錄 {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **索引碼**：CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **類型**：`Code Smell`
* **嚴重度**：輕微

一般而言，應該使用 INFO 紀錄層級來區分重要操作，並且預設情況下，會將 AEM 設定為在 INFO 或以上層級記錄。GET 和 HEAD 方法應僅能唯讀操作，因此不構成重要操作。在 INFO 層級記錄以回應 GET 或 HEAD 要求可能會產生大量記錄雜訊，而使得在記錄檔中識別有用資訊變得更加困難。處理 GET 或 HEAD 要求時，如果出現問題，記錄應位在 WARN 或 ERROR 層級。若需要更深入的疑難排解資訊，記錄應設在 DEBUG 或 TRACE 層級。

>[!NOTE]
>
>此工作流程不適用於每個要求的 access.log-type 記錄。

#### 不符合規範的程式碼 {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### 符合規範的程式碼 {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### 請勿使用 `Exception.getMessage()` 作為記錄陳述式的第一個參數 {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **索引碼**：CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

依據最佳做法的要求，紀錄訊息應提供有關應用程式中發生例外狀況的位置的內容相關資訊。雖然也可以透過使用堆疊追蹤來確定內容，但記錄訊息通常將更容易讀取和理解。因此，在記錄例外狀況時，將例外狀況的訊息當成記錄訊息來使用是不好的做法。例外狀況訊息應詳細說明發生什麼問題。相反地，記錄訊息應通知讀者，在例外狀況發生時應用程式正在執行哪些作業。例外狀況訊息仍會記錄。透過指定您自己的訊息，更容易理解這些紀錄。

#### 不符合規範的程式碼 {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### 符合規範的程式碼 {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Catch 區塊中的記錄應在 WARN 或 ERROR 層級進行 {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **索引碼**：CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

顧名思義，在例外情況下，始終都應該使用 Java™ 例外狀況。因此，當發現例外狀況時，確保將記錄訊息記錄在以下的適當層級：WARN 或 ERROR。這麼做可確保這些訊息在記錄中正確地顯示。

#### 不符合規範的程式碼 {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### 符合規範的程式碼 {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 不可將堆疊追蹤列印到控制台 {#do-not-print-stack-traces-to-the-console}

* **索引碼**：CQRules:CQBP-44---ExceptionPrintStackTrace
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

在了解紀錄訊息時，內容極為重要。使用 `Exception.printStackTrace()` 只會導致堆疊追蹤輸出至標準錯誤串流，而遺失所有內容。此外，在像 AEM 這類多執行緒應用程式中，如果使用此方法同時列印多個例外狀況，其堆疊追蹤可能會重疊，進而產生嚴重的混亂。僅能透過記錄架構記錄例外狀況。

#### 不符合規範的程式碼 {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### 符合規範的程式碼 {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 不可輸出到標準輸出或標準錯誤 {#do-not-output-to-standard-output-or-standard-error}

* **索引碼**：CQRules:CQBP-44—LogLevelConsolePrinters
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

應該永遠都透過紀錄架構 SLF4J 完成登入 AEM。直接輸出到標準輸出或標準錯誤串流會遺失紀錄架構提供的結構和相關內容資訊，而且有時還可能導致效能問題。

#### 不符合規範的程式碼 {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### 符合規範的程式碼 {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 避免用硬式編碼寫入 `/apps` 和 `/libs` 路徑 {#avoid-hardcoded-apps-and-libs-paths}

* **索引碼**：CQRules:CQBP-71
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2018.4.0 版本

以 `/libs` 和 `/apps` 開頭的路徑通常不應使用硬式編碼。這些路徑通常會相對於`Sling`搜尋路徑（預設為`/libs,/apps`）儲存。 使用絕對路徑可能會產生難以察覺的缺陷，而且後期才會在專案生命週期中顯現。

#### 不符合規範的程式碼 {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### 符合規範的程式碼 {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### 不應使用 Sling 排程器 {#sonarqube-sling-scheduler}

* **索引碼**：CQRules:AMSCORE-554
* **類型**： `Code Smell` /雲端服務相容性
* **嚴重度**：輕微
* **始自**：2020.5.0 版本

請勿將Sling排程器用於需要保證執行的任務。 Sling 已排程的作業可保證執行並更適合叢集和非叢集環境。

若要了解如何在叢集環境中處理 Sling 作業的詳細資訊，請參閱 [Apache Sling 事件和作業處理文件](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html)。

### 不應使用 AEM 已過時的 API {#sonarqube-aem-deprecated}

* **索引碼**：AMSCORE-553
* **類型**： `Code Smell` /雲端服務相容性
* **嚴重度**：輕微
* **始自**：2020.5.0 版本

AEM API 表面經過不斷修正，以識別不鼓勵使用並因此被視為已過時的 API。

通常，會使用標準 Java™ *@Deprecated* 註解來取代這些 API，而且會由 `squid:CallToDeprecatedMethod` 進行識別。

但是，在某些情況下，API 在 AEM 的內容中會遭到取代，但在其他內容中卻可能不會。此規則會識別此第二分類。

## OakPAL 內容規則 {#oakpal-rules}

下節會詳細介紹由 Cloud Manager 執行的 OakPAL 檢查。

>[!NOTE]
>
>OakPAL 是一種架構，會使用獨立的 Oak 存放庫來驗證內容套件。由 AEM 合作夥伴以及 2019 年北美洲 AEM Rock Star 獎得主開發。

### 客戶不應實施或擴展有 @ProviderType 註解的產品 API {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **索引碼**：CQBP-84
* **類型**：錯誤
* **嚴重度**：嚴重
* **始自**：2018.7.0 版本

AEM API 包含僅能由自訂程式碼使用而不能實作的 Java™ 介面和類別。例如，只有 AEM 實施介面 `com.day.cq.wcm.api.Page`。

在這些介面中新增方法不會影響現有程式碼，使得新增的新方法可回溯相容。但是，如果自訂程式碼實施其中一個介面，該自訂程式碼會給客戶帶來回溯相容性的風險。

AEM 使用 `org.osgi.annotation.versioning.ProviderType` 或偶爾使用舊註解 `aQute.bnd.annotation.ProviderType` 來註解僅供實施使用的介面和類別。此規則會偵測自訂程式碼實施此類介面或擴充類別的實例。

#### 不符合規範的程式碼 {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 客戶套件不應在 `/libs` 下面建立或修改節點 {#oakpal-customer-package}

* **索引碼**：BannedPath
* **類型**：錯誤
* **嚴重度**：阻斷因素
* **始自**：2019.6.0 版本

客戶應將 AEM 內容存放庫中的 `/libs` 內容樹視為唯讀，這是一個存在已久的最佳做法。修改 `/libs` 下的節點和屬性都會對大幅和小幅更新產生顯著風險。對 `/libs` 的編輯只可由 Adobe 透過正式管道進行。

### 套件不應包含重複的 OSGi 設定 {#oakpal-package-osgi}

* **索引碼**：DuplicateOsgiConfigurations
* **類型**：錯誤
* **嚴重度**：重大
* **始自**：2019.6.0 版本

複雜專案中經常出現的一個問題是多次設定同一個 OSGi 元件。這個問題會使人無法確定哪個是可操作的設定。此規則為「執行模式感知」，只會識別在同一執行模式或多個執行模式的組合中多次設定相同元件的問題。

#### 不符合規範的程式碼 {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 符合規範的程式碼 {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### 設定和安裝資料夾應只包含 OSGi 節點 {#oakpal-config-install}

* **索引碼碼**：ConfigAndInstallShouldOnlyContainOsgiNodes
* **類型**：錯誤
* **嚴重度**：重大
* **始自**：2019.6.0 版本

由於安全的理由，包含 `/config/` 和 `/install/` 的路徑只有 AEM 中的管理員使用者可讀取，並且僅能用於 OSGi 設定和 OSGi 套裝。將其他類型的內容放在包含這些區段的路徑下，會導致應用程式行為在管理員使用者和非管理員使用者之間無意中產生差異。

有個常見問題是，在多個元件對話框中或指定內嵌編輯的 RTF 文字編輯器設定時，使用名為 `config` 的節點。若要解決此問題，應將違規節點重新命名為合規名稱。對於 RTF 文字編輯器設定，請使用 `configPath` 屬性 (在 `cq:inplaceEditing` 節點上) 來指定新位置。

#### 不符合規範的程式碼 {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 符合規範的程式碼 {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### 套件不應重疊 {#oakpal-no-overlap}

* **索引碼**：PackageOverlaps
* **類型**：錯誤
* **嚴重度**：重大
* **始自**：2019.6.0 版本

類似[套件不應包含重複的 OSGi 設定規則](#oakpal-package-osgi)，這是複雜專案中常見的問題，即多個不同的內容套件寫入相同的節點路徑。雖然使用內容套件相依性可以確保結果一致，但最好還是完全避免重疊。

### 預設的製作模式不應該是 Classic UI {#oakpal-default-authoring}

* **索引碼**：ClassicUIAuthoringMode
* **類型**： `Code Smell` /雲端服務相容性
* **嚴重度**：輕微
* **始自**：2020.5.0 版本

OSGi 設定 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` 會定義 AEM 中的預設撰寫模式。由於從 AEM 6.4 起，Classic UI 就已被取代，若將預設的撰寫模式設定為 Classic UI，將會產生問題。

### 包含對話框的元件應該有 Touch UI 對話框 {#oakpal-components-dialogs}

* **索引碼**：ComponentWithOnlyClassicUIDialog
* **類型**： `Code Smell` /雲端服務相容性
* **嚴重度**：輕微
* **始自**：2020.5.0 版本

有 Classic UI 對話框的 AEM 元件亦應該具有 Touch UI 對話框，以便達到最好的製作效能以及與 Cloud Service 部署模式的相容性，因為後者不支援 Classic UI。本規則可證實以下情境：

* 具有 Classic UI 對話框 (即 `dialog` 子節點) 的元件必須具有相對應的 Touch UI 對話框 (即 `cq:dialog` 子節點)。
* 具有 Classic UI 設計對話框 (即 `design_dialog` 節點) 的元件必須具有相對應的 Touch UI 對話框 (即 `cq:design_dialog` 子節點)。
* 同時具有 Classic UI 對話框以及 Classic UI 設計對話框的元件必須同時有相對應的 Touch UI 對話框以及相對應的 Touch UI 設計對話框。

AEM 現代化工具文件提供了有關如何將元件從 Classic UI 轉換為 Touch UI 的詳細資訊和工具。如需更多詳細資訊，請參閱 [AEM 現代化工具文件](https://opensource.adobe.com/aem-modernize-tools/)。

### 不應使用反向複寫代理程式 {#oakpal-reverse-replication}

* **索引碼**：ReverseReplication
* **類型**： `Code Smell` /雲端服務相容性
* **嚴重度**：輕微
* **始自**：2020.5.0 版本

雲端服務部署中不支援反向複寫，如下[發行說明：移除複寫代理程式](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents)所述。

使用反向複寫的客戶應和 Adobe 聯絡，以取得替代解決方案。

### 已啟用 Proxy 的用戶端資料庫中所包含的資源應位於名為資源的資料夾中 {#oakpal-resources-proxy}

* **索引碼**：ClientlibProxyResource
* **類型**：錯誤
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM 用戶端資料庫可能包含影像和字體之類的靜態資源如[使用用戶端資料庫文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors)所述，使用經 Proxy 處理的用戶端資料庫時，這些靜態資源必須包含在名為 `resources` 的子檔案夾中，以便在發布實例上有效地參考。

#### 不符合規範的程式碼 {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 符合規範的程式碼 {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Cloud Service 的使用與工作流程不相容 {#oakpal-usage-cloud-service}

* **索引碼**：CloudServiceIncompatibleWorkflowProcess
* **類型**：`Code Smell`
* **嚴重度**：阻斷因素
* **始自**：2021.2.0 版本

隨著在 AEM Cloud Service 上移動到資產微服務以進行資產處理，在 AEM 的內部部署和 AMS 版本中使用的多個工作流程已經不受支援或變成非必要。

您可以使用 [AEM Assets as a Cloud Service GitHub 存放庫](https://github.com/adobe/aem-cloud-migration)中的移轉工具，在移轉至 AEM as a Cloud Service 期間更新工作流程模式。

### 不建議使用靜態範本而支持可編輯範本 {#oakpal-static-template}

* **索引碼**：StaticTemplateUsage
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

雖然靜態範本的使用歷來常見於 AEM 專案，但強烈建議使用可編輯範本，因為它們可提供最大的靈活度並支援靜態範本中不存在的附加功能。以下連結中可找到更多資訊：[頁面範本 - 可編輯文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable)。

使用 [AEM 現代化工具](https://opensource.adobe.com/aem-modernize-tools/)可將靜態範本到可編輯範本的遷移大幅自動化。

### 不建議使用舊版基礎元件 {#oakpal-usage-legacy}

* **索引碼**：LegacyFoundationComponentUsage
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

舊版基礎元件 (即 `/libs/foundation` 下的元件) 已在多個 AEM 版本中遭取代，改為採用[核心元件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-core-components/using/introduction)。不建議使用舊版基礎元件作為自訂元件的基礎 (無論是透過覆蓋還是繼承)，並應轉換為相對應的核心元件。

[AEM 現代化工具](https://opensource.adobe.com/aem-modernize-tools/)可促進這種轉換。

### 自訂搜尋索引定義節點必須是 `/oak:index` 的直接子節點 {#oakpal-custom-search}

* **索引碼**：OakIndexLocation
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM Cloud Service 要求自訂搜尋索引定義 (即類型 `oak:QueryIndexDefinition` 的節點) 是 `/oak:index` 的直接下層節點。必須移動其他位置中的索引才能和 AEM Cloud Service 相容。有關搜尋索引的更多資訊，可在[內容搜尋和索引文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing)中找到。

### 自訂搜尋索引定義節點的 compatVersion 必須為 2 {#oakpal-custom-search-compatVersion}

* **索引碼**：IndexCompatVersion
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM Cloud Service 要求自訂搜尋索引定義 (即類型 `oak:QueryIndexDefinition` 的節點) 必須將 `compatVersion` 屬性設定為 `2`。AEM Cloud Service 不支援其他值。有關搜尋索引的更多資訊，可在[內容搜尋和索引文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing)中找到。

### 自訂搜尋索引定義節點的子孫節點必須屬於 `nt:unstructured` 類型 {#oakpal-descendent-nodes}

* **索引碼**：IndexDescendantNodeType
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

當自訂搜尋索引定義節點具有無序子節點時，可能會出現難以解決的問題。若要避免出現這類節點，Adobe 建議 `oak:QueryIndexDefinition` 節點的所有子孫節點應是 `nt:unstructured` 類型。

### 自訂搜尋索引定義節點必須包含名為 `indexRules` 並有下層的下層節點 {#oakpal-custom-search-index}

* **索引碼**：IndexRulesNode
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

正確定義的自訂搜尋索引定義節點必須包含一個名為 `indexRules` 的下層節點，且這個子節點必須至少有一個下層。以下連結中可找到更多資訊：[Oak 文件。](https://jackrabbit.apache.org/oak/docs/query/lucene.html)。

### 自訂搜尋索引定義節點必須遵循命名慣例 {#oakpal-custom-search-definitions}

* **索引碼**：IndexName
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM Cloud Service 要求自訂搜尋索引定義 (即 `oak:QueryIndexDefinition` 類型的節點) 必須按照以下說明的特定模式命名：[內容搜尋和索引](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)。

### 自訂搜尋索引定義節點必須使用索引類型 lucene {#oakpal-index-type-lucene}

* **索引碼**：IndexType
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM Cloud Service 要求自訂搜尋索引定義 (即類型 `oak:QueryIndexDefinition` 的節點) 必須具備 `type` 屬性，且值設定為 `lucene`。在遷移到 AEM Cloud Service 之前，必須更新使用舊式索引類型的索引。如需詳細資訊，請參閱[內容搜尋和索引文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)。

### 自訂搜尋索引定義節點不得包含名為 `seed` 的屬性 {#oakpal-property-name-seed}

* **索引碼**：IndexSeedProperty
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM Cloud Service 禁止自訂搜尋索引定義 (即 `oak:QueryIndexDefinition` 類型的節點) 包含名為 `seed` 的屬性。在遷移到 AEM Cloud Service 之前，必須更新使用此屬性的索引。如需詳細資訊，請參閱[內容搜尋和索引文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)。

### 自訂搜尋索引定義節點不得包含名為 `reindex` 的屬性 {#oakpal-reindex-property}

* **索引碼**：IndexReindexProperty
* **類型**：`Code Smell`
* **嚴重度**：輕微
* **始自**：2021.2.0 版本

AEM Cloud Service 禁止自訂搜尋索引定義 (即 `oak:QueryIndexDefinition` 類型的節點) 包含名為 `reindex` 的屬性。在遷移到 AEM Cloud Service 之前，必須更新使用此屬性的索引。如需詳細資訊，請參閱[內容搜尋和索引文件](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)。

### 索引定義節點不得部署在 UI 內容套件中 {#oakpal-ui-content-package}

* **金鑰**：IndexNotUnderUIContent
* **類型**：改善
* **嚴重度**：重大
* **始自**：2024.6.0 版本

AEM Cloud Service 禁止將自訂搜尋索引定義 (`oak:QueryIndexDefinition` 類型的節點) 部署在 UI 內容套件中。

>[!WARNING]
>
>請您盡快解決此問題，因為從 [Cloud Manager 2024 年 8 月版本](/help/release-notes/current.md)開始，這麼做可能導致管道無法開始。

### `damAssetLucene` 類型的自訂全文索引定義必須正確新增前置詞 `damAssetLucene` {#oakpal-dam-asset-lucene}

* **金鑰**：CustomFulltextIndexesOfTheDmAssetCheck
* **類型**：改善
* **嚴重度**：重大
* **始自**：2024.6.0 版本

AEM Cloud Service 禁止 `damAssetLucene` 類型的自訂全文索引定義使用 `damAssetLucene` 以外的任何內容作為前置詞。

>[!WARNING]
>
>請您盡快解決此問題，因為從 [Cloud Manager 2024 年 8 月版本](/help/release-notes/current.md)開始，這麼做可能導致管道無法開始。

### 索引定義節點不得包含同名的屬性 {#oakpal-index-property-name}

* **金鑰**：DuplicateNameProperty
* **類型**：改善
* **嚴重度**：重大
* **始自**：2024.6.0 版本

AEM as a Cloud Service 禁止自訂搜尋索引定義 (即 `oak:QueryIndexDefinition` 類型的節點) 包含有同名的屬性。

>[!WARNING]
>
>請您盡快解決此問題，因為從 [Cloud Manager 2024 年 8 月版本](/help/release-notes/current.md)開始，這麼做可能導致管道無法開始。

### 禁止自訂某些現成可用的索引定義 {#oakpal-customizing-ootb-index}

* **金鑰**：RestrictIndexCustomization
* **類型**：改善
* **嚴重度**：重大
* **始自**：2024.6.0 版本

AEM Cloud Service 禁止對以下 OOTB 索引進行未經授權的修改：

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>請您盡快解決此問題，因為從 [Cloud Manager 2024 年 8 月版本](/help/release-notes/current.md)開始，這麼做可能導致管道無法開始。

### 分析工具內的 Tokenizer 設定應使用名稱 `tokenizer` 建立 {#oakpal-tokenizer}

* **金鑰**：AnalyzerTokenizerConfigCheck
* **類型**：改善
* **嚴重度**：輕微
* **始自**：2024.6.0 版本

AEM Cloud Service 禁止在分析工具中建立名稱不正確的 tokenizer。tokenizer 應始終定義為 `tokenizer`。

### 索引定義的設定不應包含空格 {#oakpal-indexing-definitions-spaces}

* **索引鍵**：PathSpacesCheck
* **類型**：改善
* **嚴重度**：輕微
* **始自**：2024.7.0 版本

AEM Cloud Service 禁止建立屬性含空格的索引定義。

### 索引定義的設定不應包含 haystack0 屬性 {#oakpal-indexing-haystack0-property}

* **金鑰**：HayStackPropertyCheck
* **類型**：改善
* **嚴重度**：輕微
* **始自**：2024.12.0 版本

AEM Cloud Service 禁止建立包含 haystack 屬性的索引定義。

### 索引定義的設定不應包含以下屬性：async-previous {#oakpal-indexing-unsupported-async-properties}

* **Key**： IndexUnsupportedAsyncPropertiesCheck
* **類型**：改善
* **嚴重度**：輕微
* **始自**：2025.3.0 版本

AEM Cloud Service禁止以不支援的非同步屬性建立索引定義。

### 索引定義的設定在多個索引中不應有相同的標籤 {#oakpal-indexing-same-tag-multiple-indexes}

* **索引鍵**： SameTagInMultipleIndexes
* **類型**：改善
* **嚴重度**：輕微
* **始自**：2025.3.0 版本

AEM Cloud Service禁止在多個索引中建立包含相同標籤的索引定義。

### 索引定義的設定不應包含禁用路徑的模式取代 {#oakpal-xml-mode-analysis}

* **索引鍵**： FilterXmlModeAnalysis
* **類型**：改善
* **嚴重度**：重大
* **始自**：2025.4.0 版本

`/content`以下的路徑不允許在檔案儲存庫中使用「取代」模式；它不應該用於低於`/etc`與`/var.`的路徑。 「取代」模式會以來自封裝的內容覆寫現有的存放庫內容。 透過Cloud Manager部署的套件不應包含觸發此動作的套件。

## Dispatcher 最佳化工具 {#dispatcher-optimization-tool-rules}

下節會包含由 Cloud Manager 執行的 Dispatcher 最佳化工具 (DOT) 檢查清單。請依照每個檢查的連結查看其 GitHub 定義和詳細資訊。

* [Dispatcher 設定非預期 Token](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Dispatcher 設定引述不相符](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Dispatcher 設定遺漏大括弧](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Dispatcher 設定額外大括弧](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Dispatcher 設定遺漏強制屬性](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Dispatcher 設定過時的屬性](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [未找到 Dispatcher 設定](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [未找到 Httpd 設定包含檔案](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcher 設定一般](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Dispatcher 發佈伺服器陣列快取應已啟用 `serveStaleOnError` ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Dispatcher 發佈伺服器陣列篩選器應包含來自 AEM 原型 6.x.x 版本的預設拒絕規則](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [Dispatcher 發佈伺服器陣列快取 `statfileslevel` 屬性應為 >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [Dispatcher 發佈伺服器陣列 `gracePeriod` 屬性應為 >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [每個 Dispatcher 伺服器陣列都應該有唯一名稱](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Dispatcher 發佈伺服器陣列快取應以允許清單的方式設定其 `ignoreUrlParams` 規則](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Dispatcher 發佈伺服器陣列篩選器應以允許清單的方式指定允許的 Sling 選取器](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Dispatcher 發佈伺服器陣列篩選器應以允許清單的方式指定允許的 Sling 尾碼模式](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [請勿在具有根目錄路徑的 VirtualHost Directory 部份中使用「要求所有被授予」指令](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
