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