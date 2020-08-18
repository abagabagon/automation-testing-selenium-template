[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![Maven Central](https://img.shields.io/maven-central/v/com.github.abagabagon/verifico.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22com.github.abagabagon%22%20AND%20a:%22verifico%22)

### **Background**
One of the disadvantages of Selenium and Appium is the steep learning curve required for users to be able to implement it. One also have to go over issues such as automation test flakiness, unhandled exceptions, etc. so they could learn how to properly implement commands of Selenium and Appium. The project is built in order to eliminate this issue.

### **Components**

| Component         | Java API                                                                                                      | Version     |
| ----------------- | ------------------------------------------------------------------------------------------------------------- | ----------- |
| Web Automation    | [Selenium](https://www.seleniumhq.org/download/)                                                              | 3.141.59    |
| Mobile Automation | [Appium](http://appium.io/)                                                                                   | 7.3.0       |
| Logging Tool      | [Log4J2](https://logging.apache.org/log4j/2.0/download.html)                                                  | 2.13.3      |
| Reporting Tool    | [ExtentReports](http://relevantcodes.com/extentreports-for-selenium/)                                         | 5.0.1       |
| Excel             | [Apache POI](https://poi.apache.org/download.html)                                                            | 4.1.2       |
| MySQL             | [MySQL Connector](https://dev.mysql.com/doc/connectors/en/)                                                   | 8.0.21      |
| MSSQL             | [MSSQL Connector](https://docs.microsoft.com/en-us/sql/connect/sql-connection-libraries?view=sql-server-ver15)| 8.2.2.jre8  |

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

The created `WebAutomation` instance would be able to access Browser and User Action Commands.

```java
I.openBrowser();
I.goTo("http://www.somewebsite.com/");
I.type(PageLogin.EMAIL_ADDRESS_TEXTBOX, "abagabagon@yopmail.com");
I.type(PageLogin.PASSWORD_TEXTBOX, "ABCabc123");
I.click(PageLogin.LOGIN_BUTTON);
```

##### **Web Automation Commands**

###### **Browser Actions**

| Command               | Description                                          |
| --------------------- | ---------------------------------------------------- |
| openBrowser           | Opens Web Browser                                    |
| openTab               | Opens Tab                                            |
| goTo                  | Navigate to the Url specified                        |
| switchTabByTitle      | Switch to a Tab based on Page Title                  |
| switchTabByURL        | Switch to a Tab based on Page URL                    |
| switchTabToOriginal   | Switch back to Original Tab                          |
| back                  | Navigate one item back from the browser's history    |
| forward               | Navigate one item forward from the browser's history |
| refresh               | Refresh current page                                 |
| maximizeBrowserWindow | Maximizes Browser Window                             |
| deleteAllCookies      | Deletes all cookies                                  |
| scroll                | Scrolls Page                                         |
| closeTab              | Closes Tab of a Web Browser                          |
| closeBrowser          | Closes Web Browser                                   |

###### **User Actions**

| Command                               | Description                                                                                                       |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| point                                 | Point mouse to the specified Web Element                                                                          |
| click                                 | Clicks the specified Web Element. Used for Elements that are clickable                                            |
| clickJS                               | Clicks the specified Web Element (utilizing Javascript). Used for Elements that are clickable                     |
| clickAndHold                          | Clicks and holds the specified Web Element. Used for Elements that are clickable                                  |
| clickFromObjectListBasedOnText        | Clicks the specified Web Element from an Object List based on text value                                          |
| clickFromTableBasedOnText             | Clicks the specified Web Element from a row in a table based on text value from the same row                      |
| doubleClick                           | Double clicks the specified Web Element. Used for Elements that are clickable                                     |
| doubleClickFromObjectListBasedOnText  | Double clicks the specified Web Element from an Object List based on text value                                   |
| doubleClickFromTableBasedOnText       | Clicks the specified Web Element from a row in a table based on text value from the same row                      |
| dragAndDrop                           | Drags a specified Web Element and drops it at target element. Used for Elements that can be dragged               |
| type                                  | Simulates typing into a text box/area Web Element                                                                 |
| typeJS                                | Simulates typing into a text box/area Web Element (utilizing Javascript)                                          |
| typeFromTableBasedOnText              | Type input text at the specified Web Element from a row in a table based on text value from the same row          |
| press                                 | Simulates pressing of characters into a text box/area Web Element                                                 |
| pressFromTableBasedOnText             | Press specified keys at the specified Web Element from a row in a table based on text value from the same row     |
| clear                                 | Clears value of a text box/area Web Element                                                                       |
| clearFromTableBasedOnText             | Clears value of the specified Web Element from a row in a table based on text value from the same row             |
| select                                | Selects a Drop-down/Multi-select List Web Element Option                                                          |
| deselect                              | Deselects a Multi-select Web Element Option                                                                       |
| getText                               | Get the visible innerText of this Web Element, including sub-elements, without any leading or trailing whitespace |
| getTextFromTableBasedOnText           | Get text of the specified Web Element from a row in a table based on text value from the same row                 |
| getValue                              | Gets the value of the INPUT and TEXTAREA Web Element                                                              |
| getValueFromTableBasedOnText          | Get value of the specified Web Element from a row in a table based on text value from the same row                |
| getAttributeValue                     | Get the value of the specified attribute of the Web Element                                                       |
| getAttributeValueFromTableBasedOnText | Get value of the specified Web Element from a row in a table based on text value from the same row                |
| getDropDownListValue                  | Gets the selected option of the Drop-down List Web Element                                                        |
| wait                                  | Waits for a specific time (Seconds)                                                                               |

###### **Verifications**

| Command                 | Description                                                                                  |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| verifyUrl               | Verifies Page URL of Web Page if equal to the expected URL                                   |
| verifyTitle             | Verifies Page Title of Web Page if equal to the expected Title                               |
| verifyPartialUrl        | Verifies Page URL of Web Page if partially equal to the expected URL                         |
| verifyClickable         | Verifies if the Web Element is clickable or not                                              |
| verifyValue             | Verifies the value of INPUT or TEXTAREA Web Elements if equal to the expected value          |
| verifyAttributeValue    | Verifies the value of the specified attribute if equal to the expected value                 |
| verifyDropDownListValue | Verifies Drop-down List Web Element Value if equal to expected text value                    |
| verifyText              | Verifies Web Element with text if equal to expected text value                               |
| verifyDisplayed         | Verifies if Web Element is displayed on Web Page                                             |
| verifyNotDisplayed      | Verifies Web Element is not displayed on the Web Page                                        |
| verifyEnabled           | Verifies Web Element is enabled on the Web Page                                              |
| verifyDisabled          | Verifies Web Element is disabled on the Web Page                                             |
| verifySelected          | Verifies Web Element is selected on the Web Page. Used for Check Boxes and Radio Buttons     |
| verifyNotSelected       | Verifies Web Element is not selected on the Web Page. Used for Check Boxes and Radio Buttons |
| verifyAlertMessage      | Verifies Javascript Alert Message displayed if equal to expected message                     |

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
