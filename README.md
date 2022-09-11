# Reference: https://medium.com/@sonaldwivedi/allure-reporting-in-selenium-using-testng-and-maven-8a3a5ff07856

1. Add new test cases under
   - `./src/test/java/com/testcases`
2. Update TestNG config XML with the new test cases
   - `testng.xml`
3. Execute the test cases
   - `mvn clean test`
4. Generate allure test results (use clean to delete any existing allure-report directory)
   - `allure generate --clean`
5. View the allure results
   - `allure open`

## Selenium Drivers

https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/

## Allure download

Go to the Releases section of Allure on its GitHub page https://github.com/allure-framework/allure2/releases

### Annotations in Allure:

First, let us get familiar with the annotations.

- @Epic
- @Features
- @Stories/@Story
- @Severity
- @Description
- @Step
- @Attachment

Though this list is long, I would be explaining only a few Allure annotations that are used widely.

- `@Severity`: We can define any @Test with @Severity annotation with any of these values like BLOCKER, CRITICAL, NORMAL, MINOR, and TRIVIAL. By looking at this, we can understand the severity of the test if failed

- `@Description`: We can add a detailed description for each test method. Remember that this is different from the TestNG description attribute of @test annotation. Will see the difference in Allure reports later.

- `@Step`: In order to define steps in Java code, you need to annotate the respective methods with @Step annotation. When not specified, the step name is equal to the annotated method name.

- `@Attachments`: An attachment in Java code is simply a method annotated with @Attachment that returns either a String or byte[], which should be added to the report
