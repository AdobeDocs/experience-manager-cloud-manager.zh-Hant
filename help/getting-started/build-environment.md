---
title: 組建環境
description: 了解 Cloud Manager 使用者用於建置和測試程式碼的專用組建環境。
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 98%

---


# 建置環境 {#build-environment}

了解 Cloud Manager 使用者用於建置和測試程式碼的專用建置環境。

## 環境詳細資訊 {#details}

Cloud Manager 的建置環境有下列屬性。

* 建置環境以 Linux 為基礎，衍生自 Ubuntu 22.04。
* 已安裝 Apache Maven 3.9.4。
   * Adobe 建議使用者[更新其 Maven 存放庫以使用 HTTPS 而非 HTTP](#https-maven)。
* 已安裝的 Java 版本為 Oracle JDK 8u401 和 Oracle JDK 11.0.22。
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* 在預設的情況下，`JAVA_HOME` 環境變數設定為 `/usr/lib/jvm/jdk1.8.0_401`，其中包含 Oracle JDK 8u401。如需更多詳細資訊，請參閱[備用的 Maven 執行 JDK 版本](#alternate-maven) 部份。
* 安裝了一些必要的附加系統套件。
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* 在建置時間可安裝其他套件，如[安裝附加系統套件](#installing-additional-system-packages)部份中所述。
* 每項建置都是在原始環境中完成的。組建容器在執行之間不保留任何狀態。
* 一直使用下列三個命令執行 Maven：
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* 在系統層級使用 `settings.xml` 檔案設定 Maven，其會利用名為 `adobe-public` 的設定檔自動納入公共 Adobe 成品存放庫。如需更多詳細資訊，請參閱 [Adobe 公共 Maven 存放庫](https://repo1.maven.org/)。
* Node.js 18 可用於[前端管道](/help/overview/ci-cd-pipelines.md)。

>[!NOTE]
>
>雖然 Cloud Manager 並未定義 `jacoco-maven-plugin` 的特定版本，但使用的版本必須至少為 `0.7.5.201505241946`。

>[!TIP]
>
>請參閱以下更多資源，以了解如何使用 Cloud Manager API：
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [建立 API 整合](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API 權限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## HTTPS Maven 存放庫 {#https-maven}

Cloud Manager [2023.10.0 版](/help/release-notes/2023/2023-10-0.md)開始推出建置環境的更新 (在 2023.12.0 版時完成)，其中包含 Maven 3.8.8 的更新。Maven 3.8.1 引入的一項重大變更是旨在減少潛在漏洞的一項安全性增強。具體而言，Maven 現在預設停用所有不安全的 `http://*` 鏡像，如 [Maven 發行說明](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)中所述。

由於此安全性增強，某些使用者可能會在建置步驟中遇到問題，特別是從使用不安全 HTTP 連線的 Maven 存放庫下載成品時。

為了確保更新的版本有流暢的使用體驗，Adobe 建議使用者更新其 Maven 存放庫以使用 HTTPS 而非 HTTP。這項調整符合產業日益轉向使用安全通訊協定的趨勢，有助於維持安全可靠的建置程序。

## 使用特定 Java 版本 {#using-java-version}

在預設情況下，由 Cloud Manager 建置程序建置的專案使用 Oracle 8 JDK。希望使用備用 JDK 的客戶有兩種選擇。

* [Maven 工具鏈](#maven-toolchains)
* [如需全部 Maven 執行流程，可選取備用 JDK 版本。](#alternate-maven)

### Maven 工具鏈 {#maven-toolchains}

此 [Maven 工具鏈外掛程式](https://maven.apache.org/plugins/maven-toolchains-plugin/)讓專案可選取特定 JDK (或工具鏈)，在工具鏈感知的 Maven 外掛程式中使用。透過指定廠商和版本值，在專案的 `pom.xml` 檔案中完成這個程序。在 `pom.xml` 檔案中的範例區段如下：

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

此流程致使所有工具鏈感知的 Maven 外掛程式使用 Oracle JDK 版本 11。

採用此方法時，Maven 本身仍使用預設的 JDK (Oracle 8) 執行，並且 `JAVA_HOME` 環境變數並未變更。因此，透過 [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) 之類的外掛程式來檢查或強制執行 Java 版本並不可行，且不得使用這類外掛程式。

目前可提供的廠商/版本組合為：

| 廠商 | 版本 |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| Sun | 1.8 |
| Sun | 1.11 |
| Sun | 11 |

>[!NOTE]
>
>從 2022 年 4 月開始，Oracle JDK 會成為 AEM 應用程式開發和運作的預設 JDK。Cloud Manager 的建置程序自動切換成使用 Oracle JDK，即使在 Maven 工具鏈中已明確選取替代選項。如需詳細資訊，請參閱 [4 月發行說明](/help/release-notes/2022/2022-4-0.md)。

### 備用 Maven 執行 JDK 版本 {#alternate-maven}

也可以選取 Oracle 8 或 Oracle 11 做為整個 Maven 執行的 JDK。和工具鏈選項不同，這會變更適用於所有外掛程式的 JDK，除非同時設定工具鏈設定，若是這種情況，則工具鏈設定仍適用於工具鏈感知的 Maven 外掛程式。於是，利用 [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) 來檢查和強制執行 Java 版本變成有效的方法。

若要執行此程式，請在管道使用的Git存放庫分支中建立名為`.cloudmanager/java-version`的檔案。 本檔案可能有的內容為 `11` 或 `8`。任何其他值會受到忽略。若指定 `11`，會使用 Oracle 11，而 `JAVA_HOME` 環境變數會設為 `/usr/lib/jvm/jdk-11.0.22`。若指定 `8`，會使用 Oracle 8，而 `JAVA_HOME` 環境變數會設為 `/usr/lib/jvm/jdk1.8.0_401`。

## 環境變數 {#environment-variables}

### 標準環境變數 {#standard-environ-variables}

在部分情況下，您可能會發現有必要根據關於方案或管道的資訊來改變建置程序。

例如，當透過 gulp 之類的工具進行 JavaScript 縮製時，您可能會比較希望針對開發環境，而不是中繼和生產環境來使用不同的縮製程度。

為了支援這一點，Clo&#x200B;&#x200B;ud Manager 會在每次執行時將標準環境變數新增到組建容器中。

| 變數名稱 | 說明 |
|---|---|
| `CM_BUILD` | 需永遠設為 `true` |
| `BRANCH` | 為執行設定的分支 |
| `CM_PIPELINE_ID` | 數值的管道識別碼 |
| `CM_PIPELINE_NAME` | 管道名稱 |
| `CM_PROGRAM_ID` | 數值的方案識別碼 |
| `CM_PROGRAM_NAME` | 方案名稱 |
| `ARTIFACTS_VERSION` | 對於中繼或生產管道，由 Cloud Manager 產生的綜合版本 |

### 標準環境變數可用性 {#availability}

標準環境變數可以用在很多地方。

#### 作者、預覽和發佈環境 {#author-preview-publish}

一般環境變數和密碼均可用於編寫、預覽和發佈環境。

#### Dispatcher {#dispatcher}

[Dispatcher](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-dispatcher/using/dispatcher) 只能使用一般環境變數。不能使用密碼。

但不能在 `IfDefine` 指令中使用環境變數。

>[!TIP]
>
>在部署之前，請透過[本機使用 Dispatcher](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) 驗證您所使用的環境變數。

#### OSGi 設定 {#osgi}

一般環境變數和密碼都可以在 [OSGi 設定](https://experienceleague.adobe.com/zh-hant/docs/ experience-manager-65/content/implementing/deploying/configuring/configuring-osgi)中使用。

### 管道變數 {#pipeline-variables}

在某些情況下，您的建置程序可能要依據特定設定變數而定，這類變數不適合放入 Git 存放庫中，或者在使用同一分支執行的管道之間需要使用不同變數。

Cloud Manager 讓這些變數能夠經由 Cloud Manager API 或 Cloud Manager CLI 依據每個管道來設定。變數可能以純文字或加密待用的方式儲存。在任何一種情況下，都能在建置環境中以環境變數的形式使用變數，然後可以從 `pom.xml` 檔案或其他建置指令碼中進行參照。

若要使用 CLI 設定變數，請執行類似下列的命令。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

可以使用類似下列的命令提供目前的變數清單。

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

變數必須遵守某些限制。

* 變數名稱只能包含字母數字構成的字元和底線 (`_`)。
   * 按照慣例，上述名稱應全部大寫。
* 每個管道限制為 200 個變數。
* 每個名稱的長度都必須少於 100 個字元。
* 每個字串值都必須少於 2048 個字元。
* 每個 `secretString` 值都必須少於 500 個字元。

在 Maven `pom.xml` 檔案中使用時，透過類似下列的語法將這些變數對應到 Maven 屬性通常會有幫助。

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## 安裝其他系統套件 {#installing-additional-system-packages}

要能發揮完整功能，部分建置需要安裝其他系統套件。例如，建置可能會叫用 Python 或 Ruby 指令碼，因此需要安裝適當的語言解譯器。此情境可透過呼叫 [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) 以叫用 APT 來完成。這項執行通常應包裝在 Cloud Manager 特定的 Maven 設定檔中。例如，若要安裝 Python，您可以執行以下操作：

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

此技術也可用於安裝特定語言套件。意即，RubyGems 使用 `gem`，或 Python 套件使用 `pip`。

>[!NOTE]
>
>以這種方式安裝系統套件不會將其安裝在用於執行 Adobe&#x200B; Experience Manager 的執行階段環境中。如果您需要在 AEM 環境中安裝系統套件，請和您的 Adob&#x200B;&#x200B;e 代表聯絡。
