### **Background**
One of the disadvantages of Selenium and Appium is the steep learning curve required for users to be able to implement it. One also have to go over issues such as automation test flakiness, unhandled exceptions, etc. so they could learn how to properly implement commands of Selenium and Appium. The project is built in order to eliminate this issue.

### **Components**

| Component         | Java API                                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Web Automation    | [Selenium](https://www.seleniumhq.org/download/)                                                                               |
| Mobile Automation | [Appium](http://appium.io/)                                                                                                    |
| Test Framework    | [TestNG](http://testng.org/doc/download.html)                                                                                  |
| Logging Tool      | [Log4J2](https://logging.apache.org/log4j/2.0/download.html)                                                                   |
| Reporting Tool    | [ExtentReports](http://relevantcodes.com/extentreports-for-selenium/)                                                          |
| Excel             | [Apache POI](https://poi.apache.org/download.html)                                                                             |
| MySQL             | [MySQL Connector](https://dev.mysql.com/doc/connectors/en/)                                                                    |
| MSSQL             | [MSSQL Connector](https://docs.microsoft.com/en-us/sql/connect/jdbc/microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)|

### **Usage**
#### **Web Automation**
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

#### **Mobile Automation**
1. **Appium** (Development In-progress)

#### **Excel Data**

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

#### **SQL Data**

```java
String sqlType = "MySQL";
String dbServer = "127.0.0.1";
String dbName = "northwind";
String user = "abagabagon";
String password = "ABCabc123";

SQLData sqlData = new SQLData(sqlType, dbServer, dbName, user, password);
```
