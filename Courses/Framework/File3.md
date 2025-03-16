# Developing Base components

LoginTest.java
```java
package Features.SeleniumTest;

import io.github.bonigarcia.wdm.WebDriverManager;
import org.junit.Before;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;


public class LoginTest {
    private WebDriver driver; // Declare WebDriver instance

    @Before
    public void Initialize(){
        // Setup ChromeDriver using WebDriverManager
        WebDriverManager.chromedriver().setup();

//      Method1 - Skip SSL warnings entirely, you can configure ChromeOptions:
        ChromeOptions options = new ChromeOptions();
        options.addArguments("--ignore-certificate-errors"); // Ignore SSL warnings

        driver = new ChromeDriver(options);

        driver.navigate().to("Enter URL");


        // Method2 - Handle SSL warning if present
//        try {
//            driver.findElement(By.id("details-button")).click(); // Click on "Advanced"
//            driver.findElement(By.id("proceed-link")).click();   // Click on "Proceed to site"
//        } catch (Exception e) {
//            System.out.println("SSL Warning not present, continuing...");
//        }

    }

    @Test
    public void login(){
        driver.findElement(By.xpath("//input[@placeholder='Username']")).sendKeys("Enter your username");
        driver.findElement(By.xpath("//input[@placeholder='Password']")).sendKeys("Enter your password");
        driver.findElement(By.xpath("//div[contains(text(),'Sign in')]")).click();
    }
}

```

## Page Object Model (POM)

POM is mainly used to  

* Reduce the number of duplicate code which does same operation
* Maintain object in separate class file  
* Improved readability of code (as objects will have their identification attribute set)
* Will have handle of each page using its instance
* Establish the relation between each pages directly in code, so that performing an operation in one  
page will return another page (which is expected) can be maintained in POM
* In order to support POM pattern, Web driver support library classes called PageFactory

### Setting up Project ready with POM

* Creating our first Page Object Class
* Creating objects for the page UI
* Initialize the PageFactory()

## Page Object Model Simplicity

A Good way to stay flexible is to write less code. -- Pragmatic Programmer

### Page Initialization with Base Class

Instead of initializing page in each class lets try to create a **base abstract class**

This makes code much simpler and easier to understand. At the same  
times, we introduce some standard to be followed in our code while  
starting to code with page object model.

## Handling WebDriver Instance Object

Why do we never have time to do it right, but always have time to do it over?

### Webdriver Object

Many times, we try to pass the WebDriver object over and over again  
from one c/assto another by the means of constructors or passing it  
as a parameter in the method where it require driver instance.

It's always a good idea in Programming to **Stop and Think for a second, to do it right**

How?

* Java
  * Create a static base class
  * Create a static property (for WebDriver)
  * Try to use that property for framework life cycle