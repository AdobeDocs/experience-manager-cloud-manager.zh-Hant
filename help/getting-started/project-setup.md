---
title: 設定您的專案
description: 了解如何設定您的專案，以便您可以使用 Cloud Manager 對其進行管理和部署。
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 54%

---


# 設定您的專案 {#setting-up-your-project}

了解如何設定您的專案，以便您可以使用 Cloud Manager 對其進行管理和部署。

## 編輯現有專案 {#modifying-project-setup-details}

現有的AEM專案必須遵循一些基本規則，才能使用Cloud Manager成功建置和部署。

* 必須使用 Apache Maven 建置專案。
* 在 Git 存放庫的根目錄中必須有一個 `pom.xml` 檔案。
   * 如有必要，此 `pom.xml` 檔案可參照的子模組 (這些子模組又可能有其他子模組) 數量並無限制。
   * 您可在您的 `pom.xml` 檔案中新增對其他 Maven 成品存放庫的參照。
   * 設定後，可支援對[受密碼保護的成品存放庫](#password-protected-maven-repositories)的存取權。但是，不支援對受網路保護的成品存放庫的存取權。
* 透過掃描在名為 `target` 的目錄中所包含的內容套件 .zip 檔案來探索可部署的內容套件。
   * 任何數量的子模組都可產生內容套件。
* 透過掃描 `zip` 檔案 (包含 `target` 的子目錄，名為 `conf` 和 `conf.d`) 探索可部署 Dispatcher 成品。
* 如果有超過一個內容套件，則不保證套件部署的排序。
* 如果需要特定的順序，可以使用內容套件相依性來定義順序。
* 部署時可能會[略過](#skipping-content-packages)套件。

## 在Cloud Manager中啟動Maven設定檔 {#activating-maven-profiles-in-cloud-manager}

在某些有限的情況下，當您在 Cloud Manager 中執行而不是在開發人員工作站上執行時，可能需要稍微改變建置流程。對於這些情況，[Maven 設定檔](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)可用於定義組建在不同環境中應如何不同，包括 Cloud Manager。

在Cloud Manager組建環境中啟動Maven設定檔應透過尋找`CM_BUILD` [環境變數](/help/getting-started/build-environment.md#environment-variables)來完成。 相反地，僅供在 Cloud Manager 組建環境之外使用的設定檔應透過尋求不存在此變數來完成。

例如，如果您只想在Cloud Manager內執行組建時輸出一則簡單的訊息，可採取下列步驟：

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>若要在開發人員工作站上測試此設定檔，您可在命令列 (包含 `-PcmBuild`) 上或在您的整合式開發環境 (IDE) 中將其啟用。

而如果您只想在Cloud Manager外部執行組建時輸出一則簡單的訊息，您可以採取下列步驟：

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## 受密碼保護的Maven存放庫支援 {#password-protected-maven-repositories}

對於來自受密碼保護的Maven存放庫的成品，應謹慎使用，因為以這種方式部署的程式碼不會完全受到Cloud Manager品質閘道強制的品質檢查的約束。 Adobe也建議您同時部署Java原始程式碼和整個專案的原始程式碼以及二進位。

>[!TIP]
>
>受密碼保護的 Maven 存放庫中的成品應僅在極少數情況下才用於未繫結至 AEM 的程式碼。

若要使用Cloud Manager中受密碼保護的Maven存放庫，請指定密碼（也可選擇指定使用者名稱）作為秘密[管道變數](/help/getting-started/build-environment.md#pipeline-variables)，然後在Git存放庫中名為`.cloudmanager/maven/settings.xml`的檔案內參照該秘密。 此檔案會遵循 [Maven 設定檔](https://maven.apache.org/settings.html)結構描述。

Cloud Manager建置程式啟動時，會將此檔案中的`<servers>`元素合併至Cloud Manager提供的預設`settings.xml`檔案中。 自訂伺服器不應使用以`adobe`和`cloud-manager`開頭的伺服器ID。 此類ID會視為保留的ID。 Cloud Manager只會映象符合其中一個指定首碼或預設ID `central`的伺服器ID。

備妥這個檔案後，將從 `<repository>` 內部和/或 `<pluginRepository>` 元素 (在 `pom.xml` 檔案內) 參照伺服器 ID。一般來說，這些 `<repository>` 和/或 `<pluginRepository>` 元素將包含在 [Cloud Manager 的特定設定檔](#activating-maven-profiles-in-cloud-manager)內，不過這並非絕對必要。

例如，假設存放庫位於`https://repository.myco.com/maven2`，Cloud Manager應使用的使用者名稱為`cloudmanager`，密碼為`secretword`。

首先，在管道上將密碼設為秘密：

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

然後從`.cloudmanager/maven/settings.xml`檔案參考下列內容：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

而且最後需在 `pom.xml` 檔案內參照伺服器 ID：

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### 部署來源 {#deploying-sources}

同時部署 Java 原始程式碼以及二進位至 Maven 存放庫是建議的做法。

在您的專案中設定 `maven-source-plugin`：

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### 部署專案來源 {#deploying-project-sources}

同時部署整個專案的原始程式碼以及二進位至Maven存放庫是建議的做法。 如此可重新建置精確的成品。

在您的專案中設定 `maven-assembly-plugin`：

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## 跳過內容封裝 {#skipping-content-packages}

在 Cloud Manager 中，組建可能會產生任何數量的內容套件。由於各種原因，可能需要產生內容套件但不將其部署。例如，當您僅為了測試而建置內容套件，或建置流程中的另一個步驟重新封裝內容套件時，此方法會很有用。 亦即，作為另一個封裝的子封裝。

為了適應這些情況，Cloud Manager 會在內建內容套件的屬性中查找名為 `cloudManagerTarget` 的屬性。如果此屬性設定為`none`，則會略過該套件且不部署。 設定此屬性的機製取決於建立內容封裝的方式。 例如，使用`filevault-maven-plugin`時，您可以像這樣設定外掛程式：

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

使用`content-package-maven-plugin`時，會類似：

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## 組建成品重複使用 {#build-artifact-reuse}

在許多情況下，會將相同的程式碼部署到多個 AEM 環境中。在可能的情況下，Cloud Manager在偵測到多個全棧疊管道執行中使用了相同的Git認可時，會避免重建程式碼基底。

開始執行時，將擷取分支管道的最新 HEAD 認可。在UI中以及透過API可以看到認可雜湊。 當建置步驟成功完成時，所產生的成品將根據該認可雜湊進行儲存，並可能在後續管道執行中重複使用。

如果套件在同一個計畫中，可跨管道重複使用。在尋找可重複使用的套件時，AEM 會忽略分支並且會跨分支重複使用成品。

當發生重複使用時，將以原始執行的結果有效地取代建置和程式碼品質步驟。建置步驟的記錄檔會列出成品以及最初用於建置這些成品的執行資訊。

以下是這類紀錄輸出的範例。

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

計畫碼品質步驟的紀錄包含類似的資訊。

### 範例 {#example-reuse}

#### 範例 1 {#example-1}

假定您的計畫有兩個開發管道：

* 管道 1 在分支 `foo` 上
* 管道 2 在分支 `bar` 上

兩個分支都在相同的認可 ID 上。

1. 執行管道1會先正常建置套件。
1. 接著執行管道2會重複使用管道1建立的套件。

#### 範例 2 {#example-2}

假設您的程式有兩個分支：分支`foo`和分支`bar`。

兩個分支的認可 ID 相同。

1. 會建置開發管道並執行 `foo`。
1. 隨後，生產管道建置並執行`bar`。

在此情況下，來自`foo`的成品會重複用於生產管道，因為已識別相同的認可雜湊。

### 選擇退出 {#opting-out}

如有需要，可透過將管道變數 `CM_DISABLE_BUILD_REUSE` 設定為 `true` 來停用特定管道的重複使用行為。如果設定此變數，則仍會擷取認可雜湊。 產生的成品會儲存以供稍後使用，但不會重複使用任何先前儲存的成品。 若要瞭解此行為，請考量下列案例：

1. 已建立新管道。
1. 執行管道 (執行 #1)，且目前的 HEAD 認可為 `becdddb`。此執行成功完成，並儲存產生的成品。
1. 設定 `CM_DISABLE_BUILD_REUSE` 變數。
1. 在不變更程式碼的情況下重新執行管道。雖然有和 `becdddb` 相關的已儲存成品，但由於 `CM_DISABLE_BUILD_REUSE` 變數，並不會重新使用它們。
1. 會變更程式碼並重新執行管道。該 HEAD 認可現在是 `f6ac5e6`。此執行成功完成，並儲存產生的成品。
1. 已刪除 `CM_DISABLE_BUILD_REUSE` 變數。
1. 在不變更該程式碼的情況下重新執行管道。因為有與`f6ac5e6`相關的已儲存成品，所以會重新使用這些成品。

### 警告 {#caveats}

* 無論認可雜湊是否相同，都不會在不同的計畫中重新使用組建成品。
* 即使分支和/或管道不同，在相同方案中會重新使用組建成品。
* [Maven 版本處理](/help/managing-code/maven-project-version.md)只有在生產管道中才會取代專案版本。如果開發和生產管道使用相同的認可，且開發管道先執行，則版本會部署到中繼和生產環境且不會變更。 不過，在此情況下仍會建立標籤。
* 如果無法擷取已儲存的成品，則會執行建置步驟，就像未儲存任何成品一樣。
* 當 Cloud Manager 決定重新使用之前已建立的組件成品時，不會考慮 `CM_DISABLE_BUILD_REUSE` 以外的管道變數。

## 根據最佳實務開發程式碼 {#develop-your-code-based-on-best-practices}

Adobe工程和諮詢團隊已為AEM開發人員開發一組[完整的最佳實務](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices)。
