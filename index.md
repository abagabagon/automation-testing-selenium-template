[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![Maven Central](https://img.shields.io/maven-central/v/com.github.abagabagon/verifico.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22com.github.abagabagon%22%20AND%20a:%22verifico%22)

### **Background**
One of the disadvantages of Selenium and Appium is the steep learning curve required for users to be able to implement it. One also have to go over issues such as automation test flakiness, unhandled exceptions, etc. so they could learn how to properly implement commands of Selenium and Appium. The project is built in order to eliminate this issue.

### **Components**

| Component         | Java API                                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Web Automation    | [Selenium](https://www.seleniumhq.org/download/)                                                                               |
| Mobile Automation | [Appium](http://appium.io/)                                                                                                    |
| Logging Tool      | [Log4J2](https://logging.apache.org/log4j/2.0/download.html)                                                                   |
| Reporting Tool    | [ExtentReports](http://relevantcodes.com/extentreports-for-selenium/)                                                          |
| Excel             | [Apache POI](https://poi.apache.org/download.html)                                                                             |
| MySQL             | [MySQL Connector](https://dev.mysql.com/doc/connectors/en/)                                                                    |
| MSSQL             | [MSSQL Connector](https://docs.microsoft.com/en-us/sql/connect/jdbc/microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)|

### **Java Dependency**

#### **Maven**

```xml
<!-- https://mvnrepository.com/artifact/com.github.abagabagon/verifico -->
<dependency>
    <groupId>com.github.abagabagon</groupId>
    <artifactId>verifico</artifactId>
    <version>1.0.4</version>
</dependency>
```

### **Usage**

#### **Web Automation**

For Web Application Automation, create an instance of the `WebAutomation` Object which is shown below:

```java
Browser browser = Browser.CHROME;
boolean isHeadless = false;

Verifico verifico = new Verifico();
WebAutomation I = verifico.getWebAutomation(browser, isHeadless);
```

Web Application Automation on Mobile Devices is also supported. Same as above, an instance of the `WebAutomation` Object will need to be created but with different parameters:

```java
String deviceName = "YT9117XT7C";
Mobile mobile = Mobile.Android
String platformVersion = "6.0.1";
Browser browser = Browser.CHROME;
URL appiumServerUrl = new URL("http://127.0.0.1:4723/wd/hub");

Verifico verifico = new Verifico();
WebAutomation I = verifico.getWebAutomation(deviceName, mobile, platformVersion, browser, appiumServerUrl);
```

```java
I.openBrowser();
I.goTo("http://www.somewebsite.com/");
I.type(PageLogin.EMAIL_ADDRESS_TEXTBOX, "abagabagon@yopmail.com");
I.type(PageLogin.PASSWORD_TEXTBOX, "ABCabc123");
I.click(PageLogin.LOGIN_BUTTON);
```

#### **Excel Data**

```java
Excel excelType = Excel.XLS;
String filePath = "./src/resources/data/excel/staff-accounts.XLS";

Verifico verifico = new Verifico();
ExcelData excelData = verifico.getExcelData(excelType, filePath);
```

#### **SQL Data**

```java
SQL sqlType = "MySQL";
String dbServer = "127.0.0.1";
String dbName = "northwind";
String user = "abagabagon";
String password = "ABCabc123";

Verifico verifico = new Verifico();
SQLData sqlData = verifico.getSQLData(sqlType, dbServer, dbName, user, password);
```
