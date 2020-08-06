# **VERIFICO**
Verifico is a Test Automation Library built on top of Selenium and Appium that aims to automate both Web and Mobile Applications.

## **Background**
One of the disadvantages of Selenium and Appium is the steep learning curve required for users to be able to implement it. One also have to go over issues such as automation test flakiness, unhandled exceptions, etc. so they could learn how to properly implement commands of Selenium and Appium. The project is built in order to eliminate this issue.

## **Components**
Test Framework
To eliminate the issue of Selenium/Appium not having its own Testing Framework, the automation tool will be integrated with [TestNG](http://testng.org/doc/download.html).

### **Logging Tool**
Tool to be used is [Log4J2](https://logging.apache.org/log4j/2.0/download.html) which is a Java-based logging utility.

### **Reporting Tool**
Tool to be used is [ExtentReports](http://relevantcodes.com/extentreports-for-selenium/) which is also a Java Library that could produce interactive and detailed reports in HTML Format.

### **Test Management Tool Integration**
As an added reporting capability, it is also planned to integrate [TestRail](https://www.gurock.com/testrail/docs/api/getting-started/binding-java)’s Java API Binding so automated test results can be logged directly to the Test Management Tool in real time.

### **DevOps** 
For the Automation Scripts to be integrated in DevOps, automation project has been created as a [Maven](https://maven.apache.org/download.cgi) project so the tool can be utilized for Build / Dependency Management.

### **Data**

#### **Excel Data**
For providing Test Data, [Apache POI](https://poi.apache.org/download.html) has been integrated so users would be able to retrieve data from external MS Office Files.

#### **SQL Data**
The [MySQL Java API Connector](https://dev.mysql.com/doc/connectors/en/) are being planned to be added as well for querying MySQL Databases. Can be used for verifying Lists and Reports.

## **Usage**
### **Web Automation**
1. **Selenium (Web)**

```java
WebAutomation I = new SeleniumWebAutomation();
```

Available commands require Objects as `By` Objects. So it's recommended to apply Page Object Model for its usage.

```java
I.fill(PageLogin.EMAIL_ADDRESS_TEXTBOX, "abagabagon@yopmail.com");
I.fill(PageLogin.PASSWORD_TEXTBOX, "ABCabc123");
I.click(PageLogin.LOGIN_BUTTON);
```

2. **Appium (Mobile Web)**

```java
URL appiumServer = new URL("http://127.0.0.1:4723/wd/hub");
String platformVersion = "6.0.1";
String deviceName = "YT9117XT7C";

WebAutomation I = new AppiumWebAutomation(Mobile.Android, appiumServer, platformVersion, deviceName);
```

Same with `Selenium`, available commands require Objects as `By` Objects.

### **Mobile Automation**
1. **Appium** (Development In-progress)

### **Excel Data**

1. **XLS Excel Files**

```java
String filePath = "./src/resources/data/excel/staff-accounts.XLS";

ExcelData excelData = new XLSExcelData(filePath);
```

2. **XLSX Excel Files**

```java
String filePath = "./src/resources/data/excel/staff-accounts.XLSX";

ExcelData excelData = new XLSXExcelData(filePath);
```

Originally intended for use in a TestNG Test Framework, it can be used for retrieving test data for tests in a `@DataProvider` Method.

```java
@DataProvider(name = "Accounts")
public Object[][] getAccountsData() {
	ExcelData excelData = new XLSXExcelData("./src/resources/data/excel/staff-accounts.XLSX");
	Object[][] data = excelData.getSheetData("Manager", false);
	return data;
}
```

### **SQL Data**

```java
String sqlType = "MySQL";
String dbServer = "127.0.0.1";
String dbName = "northwind";
String user = "abagabagon";
String password = "ABCabc123";

SQLData sqlData = new SQLData(sqlType, dbServer, dbName, user, password);
```
