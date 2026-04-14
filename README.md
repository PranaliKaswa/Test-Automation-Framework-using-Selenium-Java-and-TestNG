Test Automation Framework using Selenium Java and TestNG building by Pranali Kaswa
💥Important: when clone this repo, you should select 'Recursive' to get all submodules
🔆 SOME FEATURES IN FRAMEWORK

Run the parallel test case
Read Config from Properties file
Extent Report
Allure Report
Send Mail after the run test (Report information and HTML file attachment)
Write Log to file
Record video and Screenshot test case
Read data test from Excel file (xlsx, csv, json,...)
Base function in the package: utils, helpers
Read data test from Json file
Main Keyword: WebUI (call common function)
Sample test all function in WebUI keyword
Send message/report to Telegram Bot
Run Selenium Grid (remote)
Use DataFaker and JavaFaker to generate data
Retry Failed Test in TestNG with IRetryAnalyzer and IAnnotationTransformer
Javadoc for this source
✳️ SYSTEM REQUIREMENTS
Install Java JDK (recommend JDK >= 17)

Install Chrome Browser, Edge Browser, Firefox Browser

Run well on the Windows platform

Setup Allure ENV: https://mvnrepository.com/artifact/io.qameta.allure/allure-java-commons Download jar and setting Variable Environment as Java JDK

image

Use IntelliJ IDEA is the best choice (easy change the JDK version)

image

✳️ HOW TO USE
1. Run parallel the test case

Run test cases in suite XML (src/test/resources/suites/)

Run test cases from Maven with setup in the pom.xml file (mvn clean test)

image

2. Read Config from Properties file

image

3. Extent Report

Insert "FrameworkAnnotation" as sample or None:
image

The base value read from Enums (src/main/java/com/automation/framework/enums)
Setup on TestListener and BaseTest
image

Pdf Report
image image image

4. Allure Report

Open Terminal: allure serve target/allure-results
or command: allure generate --single-file target/allure-results --clean
image

Insert @Step("title/message") above @Test or any Method in the project
(As sample picture above step 3)
image

image

5. Send Mail after the run test

Config true/false in config.properties (src/test/resources/config/config.properties)
send_email_to_users=true is enable send mail
Config mail with email and password in src/main/java/com/automation/framework/mail/EmailConfig.java
Note: if Gmail, you use App Password
image

image

6. Write Logs to file

Call class: LogUtils.info(), LogUtils.pass(), LogUtils.error(),... (LogUtils is a custom global class from Log4j2) (import com.automation.framework.utils.LogUtils;)
image

7. Record video and Screenshot

Setup in config.properties file (src/test/resources/config/config.properties)

screenshot_passed_steps=yes or no

screenshot_failed_steps=yes or no

screenshot_skipped_steps=yes or no

screenshot_all_steps=yes or no

image

8. Read data test from Excel file

Create function with annotation DataProvider on src/test/java/kaswapranali/com/projects/website/crm/dataprovider/DataProviderManager.java
Read Excel file with Map and Hashtable
9. Base function in the package

src/main/java/kaswapranali/com/utils
src/main/java/kaswapranali/com/helpers
10. Read data test from JSON file

JsonUtils class selects the JSON file path and calls "get" method with key
11. Main Keyword: WebUI

WebUI class is the main keyword in Framework. It contains common functions
How to use: WebUI.function_name
Example: WebUI.setWindowSize(1024, 768), WebUI.screenshotElement(By by, String elementName),...
12. Call function to using sample

All in one package: src/test/java/com/automation/framework/projects/website/crm/testcases
+ ClientTest
+ SignInTest
+ TestHandle
+ TestSimpleCode
13. Send message/report to Telegram Bot

Setup in src/main/java/kaswapranali/com/report/TelegramManager.java
Example: src/test/java/kaswapranali/com/projects/website/crm/testcases/TestSimpleCode.java
Call in TestListener at onFinish TelegramManager.sendReportPath()
===How to get Token and start Bot===

Read blog: https://blog.devgenius.io/automation-of-reporting-2abe7f101801
Copy Token of your Bot ⇒ Paste to TelegramManager class
Click your Bot ⇒ input /start to start your Bot
===How to get ChatID===

After starting your Bot, you use Postman tools and using your Token: Get: https://api.telegram.org/bot{token}/getUpdates ⇒ chat.id
Example: https://api.telegram.org/bot19468772:AAHtlc_BH8zlJAGDHuTJy3J72XumY5LxWcE/getUpdates
"chat": {
    "id": 123456789,
    "first_name": "Pranali Kaswa",
    "username": "kaswapranali",
    "type": "private"
}
14. Use Selenium Grid

Download and Install
Download Selenium Grid 4: https://www.selenium.dev/downloads/
(Download Latest stable version)

selenium-server-4.22.0.jar (updated 24/06/2024)

Set PATH for driver in Environment variables:
Follow with link: https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/#2-the-path-environment-variable

🔆 selenium-server-4.22.0.jar

Run default 1 node
✅ (port 4444)

java -jar selenium-server-4.22.0.jar standalone

Run multi Node
java -jar selenium-server-4.22.0.jar hub

java -jar selenium-server-4.22.0.jar node --port 5556

java -jar selenium-server-4.22.0.jar node --port 6667

java -jar selenium-server-4.22.0.jar node --port 7778

Edit Grid in Config.properties
TARGET=remote

REMOTE_URL=192.168.1.13 (url Grid của bạn)

REMOTE_PORT=4444 (port của Grid)

image

image

image

15. Use DataFaker and JavaFaker to generate data

Document DataFaker: https://www.datafaker.net/documentation/getting-started/

🔆 Project structure
📦AutomationFrameworkSelenium
 ┣ 📂.github
 ┃ ┗ 📂workflows
 ┃ ┃ ┗ 📜maven.yml
 ┣ 📂src
 ┃ ┣ 📂main
 ┃ ┃ ┣ 📂java
 ┃ ┃ ┃ ┗ 📂com
 ┃ ┃ ┃ ┃ ┗ 📂automation
 ┃ ┃ ┃ ┃ ┃ ┗📂framework
 ┃ ┃ ┃ ┃ ┃ ┣ 📂annotations
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜FrameworkAnnotation.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂config
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ConfigFactory.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜Configuration.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂constants
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜FrameworkConstants.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂driver
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserFactory.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DriverManager.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TargetFactory.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂enums
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜AuthorType.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜Browser.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜CategoryType.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜FailureHandling.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜Platform.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜Project.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜Target.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂exceptions
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜FrameworkException.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜HeadlessNotSupportedException.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidPathForExcelException.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidPathForExtentReportFileException.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidPathForFilesException.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidRemoteWebDriverURLException.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TargetNotValidException.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂helpers
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜CaptureHelpers.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DatabaseHelpers.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ExcelHelpers.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜FileHelpers.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜Helpers.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜PropertiesHelpers.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ScreenRecoderHelpers.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂keywords
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜WebUI.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂mail
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜EmailAttachmentsSender.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜EmailConfig.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂report
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜AllureManager.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ExtentReportManager.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ExtentTestManager.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TelegramManager.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📂utils
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserInfoUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DataFakerUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DataGenerateUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DateUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DecodeUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜EmailSendUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜IconUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜JsonUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜LanguageUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜LocalStorageUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜LogUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ObjectUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ReportUtils.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ZipUtils.java
 ┃ ┃ ┗ 📂resources
 ┃ ┃ ┃ ┣ 📂META-INF
 ┃ ┃ ┃ ┃ ┗ 📂services
 ┃ ┃ ┃ ┃ ┃ ┗ 📜io.qameta.allure.listener.TestLifecycleListener
 ┃ ┃ ┃ ┗ 📜log4j2.properties
 ┃ ┗ 📂test
 ┃ ┃ ┣ 📂java
 ┃ ┃ ┃ ┗ 📂kaswapranali
 ┃ ┃ ┃ ┃ ┗ 📂com
 ┃ ┃ ┃ ┃ ┃ ┣ 📂common
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜BaseTest.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂dataprovider
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜DataProviderAddProduct.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜DataProviderManager.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📂listeners
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜AllureListener.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TestListener.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📂projects
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂cms
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂admin
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂model
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂pages
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂brands
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜BrandPage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂category
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜CategoryPage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂logins
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜LoginPageCMS.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂products
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜AddProductPage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂testcases
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜AddProductTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜CategoryTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜LoginTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜OrderTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ProductInfoTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProfileTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂users
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂model
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂pages
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂dashboard
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜DashboardPage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂logins
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂order
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜OrderPage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂products
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProductInfoPageCMS.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂profiles
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProfilePage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜CommonPageCMS.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂crm
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂models
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ClientModel.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜SignInModel.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂pages
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Clients
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ClientPageCRM.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Dashboard
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜DashboardPageCRM.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Projects
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProjectPageCRM.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂SignIn
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜SignInPageCRM.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Tasks
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TaskPage.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜CommonPageCRM.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂testcases
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ClientTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜SignInTest.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜TestHandle.java
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TestSimpleCode.java
 ┃ ┃ ┗ 📂resources
 ┃ ┃ ┃ ┣ 📂config
 ┃ ┃ ┃ ┃ ┣ 📜allure.properties
 ┃ ┃ ┃ ┃ ┣ 📜config.json
 ┃ ┃ ┃ ┃ ┣ 📜config.properties
 ┃ ┃ ┃ ┃ ┗ 📜data.properties
 ┃ ┃ ┃ ┣ 📂objects
 ┃ ┃ ┃ ┃ ┗ 📜crm_locators.properties
 ┃ ┃ ┃ ┣ 📂suites
 ┃ ┃ ┃ ┃ ┣ 📜Clients-parallel.xml
 ┃ ┃ ┃ ┃ ┣ 📜Clients-simple.xml
 ┃ ┃ ┃ ┃ ┣ 📜Clients-testAddClient.xml
 ┃ ┃ ┃ ┃ ┣ 📜Clients-testSearch.xml
 ┃ ┃ ┃ ┃ ┣ 📜SignIn-parallel-methods.xml
 ┃ ┃ ┃ ┃ ┣ 📜SignIn-simple.xml
 ┃ ┃ ┃ ┃ ┗ 📜SuiteAll.xml
 ┃ ┃ ┃ ┣ 📂testdataCMS
 ┃ ┃ ┃ ┃ ┣ 📜Book1.xlsx
 ┃ ┃ ┃ ┃ ┣ 📜ChocoPie.jpg
 ┃ ┃ ┃ ┃ ┣ 📜CMS_DATA.xlsx
 ┃ ┃ ┃ ┃ ┣ 📜CocaCola.png
 ┃ ┃ ┃ ┃ ┣ 📜Cosy.png
 ┃ ┃ ┃ ┃ ┣ 📜GetProductInfo.xlsx
 ┃ ┃ ┃ ┃ ┣ 📜Login.xlsx
 ┃ ┃ ┃ ┃ ┣ 📜Nabati.jpg
 ┃ ┃ ┃ ┃ ┗ 📜quatet.jpg
 ┃ ┃ ┃ ┣ 📂testdataCRM
 ┃ ┃ ┃ ┃ ┣ 📜ClientsDataExcel.xlsx
 ┃ ┃ ┃ ┃ ┣ 📜DOCX_File_01.docx
 ┃ ┃ ┃ ┃ ┣ 📜LoginCSV.csv
 ┃ ┃ ┃ ┃ ┗ 📜TxtFileData.txt
 ┃ ┃ ┃ ┗ 📜pdf-config.json
 ┣ 📂target
 ┃ ┣ 📂classes
 ┃ ┃ ┣ 📂kaswapranali
 ┃ ┃ ┃ ┗ 📂com
 ┃ ┃ ┃ ┃ ┣ 📂annotations
 ┃ ┃ ┃ ┃ ┃ ┗ 📜FrameworkAnnotation.class
 ┃ ┃ ┃ ┃ ┣ 📂config
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ConfigFactory.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜Configuration.class
 ┃ ┃ ┃ ┃ ┣ 📂constants
 ┃ ┃ ┃ ┃ ┃ ┗ 📜FrameworkConstants.class
 ┃ ┃ ┃ ┃ ┣ 📂driver
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserFactory$1.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserFactory$2.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserFactory$3.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserFactory$4.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserFactory.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DriverManager.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜TargetFactory.class
 ┃ ┃ ┃ ┃ ┣ 📂enums
 ┃ ┃ ┃ ┃ ┃ ┣ 📜AuthorType.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Browser.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜CategoryType.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜FailureHandling.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Platform.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Project.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜Target.class
 ┃ ┃ ┃ ┃ ┣ 📂exceptions
 ┃ ┃ ┃ ┃ ┃ ┣ 📜FrameworkException.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜HeadlessNotSupportedException.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidPathForExcelException.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidPathForExtentReportFileException.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidPathForFilesException.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜InvalidRemoteWebDriverURLException.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜TargetNotValidException.class
 ┃ ┃ ┃ ┃ ┣ 📂helpers
 ┃ ┃ ┃ ┃ ┃ ┣ 📜CaptureHelpers.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DatabaseHelpers.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ExcelHelpers.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜FileHelpers.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Helpers.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜PropertiesHelpers.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜ScreenRecoderHelpers.class
 ┃ ┃ ┃ ┃ ┣ 📂keywords
 ┃ ┃ ┃ ┃ ┃ ┗ 📜WebUI.class
 ┃ ┃ ┃ ┃ ┣ 📂mail
 ┃ ┃ ┃ ┃ ┃ ┣ 📜EmailAttachmentsSender$1.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜EmailAttachmentsSender.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜EmailConfig.class
 ┃ ┃ ┃ ┃ ┣ 📂report
 ┃ ┃ ┃ ┃ ┃ ┣ 📜AllureManager.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ExtentReportManager.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ExtentTestManager.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜TelegramManager.class
 ┃ ┃ ┃ ┃ ┗ 📂utils
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BrowserInfoUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DataFakerUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DataGenerateUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DateUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DecodeUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜EmailSendUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜IconUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜JsonUtils$1.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜JsonUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜LanguageUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜LocalStorageUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜LogUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ObjectUtils.class
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ReportUtils.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜ZipUtils.class
 ┃ ┃ ┣ 📂META-INF
 ┃ ┃ ┃ ┗ 📂services
 ┃ ┃ ┃ ┃ ┗ 📜io.qameta.allure.listener.TestLifecycleListener
 ┃ ┃ ┗ 📜log4j2.properties
 ┃ ┣ 📂generated-sources
 ┃ ┃ ┗ 📂annotations
 ┃ ┣ 📂generated-test-sources
 ┃ ┃ ┗ 📂test-annotations
 ┃ ┗ 📂test-classes
 ┃ ┃ ┣ 📂kaswapranali
 ┃ ┃ ┃ ┗ 📂com
 ┃ ┃ ┃ ┃ ┣ 📂common
 ┃ ┃ ┃ ┃ ┃ ┗ 📜BaseTest.class
 ┃ ┃ ┃ ┃ ┣ 📂dataprovider
 ┃ ┃ ┃ ┃ ┃ ┣ 📜DataProviderAddProduct.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜DataProviderManager.class
 ┃ ┃ ┃ ┃ ┣ 📂listeners
 ┃ ┃ ┃ ┃ ┃ ┣ 📜AllureListener.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📜TestListener.class
 ┃ ┃ ┃ ┃ ┗ 📂projects
 ┃ ┃ ┃ ┃ ┃ ┣ 📂cms
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂admin
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂model
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂pages
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂brands
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜BrandPage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂category
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜CategoryPage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂logins
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜LoginPageCMS.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂products
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜AddProductPage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂testcases
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜AddProductTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜CategoryTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜LoginTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜OrderTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ProductInfoTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProfileTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂users
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂model
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂pages
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂dashboard
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜DashboardPage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂logins
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂order
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜OrderPage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂products
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProductInfoPageCMS.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂profiles
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProfilePage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜CommonPageCMS.class
 ┃ ┃ ┃ ┃ ┃ ┗ 📂crm
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂models
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ClientModel.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜SignInModel.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂pages
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Clients
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ClientPageCRM.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Dashboard
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜DashboardPageCRM.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Projects
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜ProjectPageCRM.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂SignIn
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜SignInPageCRM.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📂Tasks
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TaskPage.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜CommonPageCRM.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📂testcases
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜ClientTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜SignInTest.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┣ 📜TestHandle.class
 ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┗ 📜TestSimpleCode.class
 ┃ ┃ ┣ 📂config
 ┃ ┃ ┃ ┣ 📜allure.properties
 ┃ ┃ ┃ ┣ 📜config.json
 ┃ ┃ ┃ ┣ 📜config.properties
 ┃ ┃ ┃ ┗ 📜data.properties
 ┃ ┃ ┣ 📂objects
 ┃ ┃ ┃ ┗ 📜crm_locators.properties
 ┃ ┃ ┣ 📂suites
 ┃ ┃ ┃ ┣ 📜Clients-parallel.xml
 ┃ ┃ ┃ ┣ 📜Clients-simple.xml
 ┃ ┃ ┃ ┣ 📜Clients-testAddClient.xml
 ┃ ┃ ┃ ┣ 📜Clients-testSearch.xml
 ┃ ┃ ┃ ┣ 📜SignIn-parallel-methods.xml
 ┃ ┃ ┃ ┣ 📜SignIn-simple.xml
 ┃ ┃ ┃ ┗ 📜SuiteAll.xml
 ┃ ┃ ┣ 📂testdataCMS
 ┃ ┃ ┃ ┣ 📜Book1.xlsx
 ┃ ┃ ┃ ┣ 📜ChocoPie.jpg
 ┃ ┃ ┃ ┣ 📜CMS_DATA.xlsx
 ┃ ┃ ┃ ┣ 📜CocaCola.png
 ┃ ┃ ┃ ┣ 📜Cosy.png
 ┃ ┃ ┃ ┣ 📜GetProductInfo.xlsx
 ┃ ┃ ┃ ┣ 📜Login.xlsx
 ┃ ┃ ┃ ┣ 📜Nabati.jpg
 ┃ ┃ ┃ ┗ 📜quatet.jpg
 ┃ ┃ ┣ 📂testdataCRM
 ┃ ┃ ┃ ┣ 📜ClientsDataExcel.xlsx
 ┃ ┃ ┃ ┣ 📜DOCX_File_01.docx
 ┃ ┃ ┃ ┣ 📜LoginCSV.csv
 ┃ ┃ ┃ ┗ 📜TxtFileData.txt
 ┃ ┃ ┗ 📜pdf-config.json
 ┣ 📜.gitignore
 ┣ 📜pom.xml
 ┗ 📜README.md
