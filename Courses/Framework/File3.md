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
from one class to another by the means of constructors or passing it  
as a parameter in the method where it require driver instance.

It's always a good idea in Programming to **Stop and Think for a second, to do it right**

How?

* Java
  * Create a static base class
  * Create a static property (for WebDriver)
  * Try to use that property for framework life cycle

## Page Navigation in Page Object Model

Using Page Navigation we can establish relationship between each  
pages, so that, anytime while an operation is performed on one  
method it mayor maynot(depends) returns a page object

This will ensure the business logic embedded in our test code and won't loose the behavior of our application.

## Page Navigation without Generics


## Lectur 19 - Page Navigation with Generics

What does it really means?

We are going to address the problem which we faced with **types** in previous lecture

WE WILL FIX ALL THE BOXING AND
UNBOXING ISSUES USING GENERICS

GENERICS?

### Generics in Java 

JDK 5.0 introduces several new extensions to the Java programming
language. One of these is the introduction of generics.

Generics allow you to abstract over types meaning generics
enable types (classes and interfaces) to be parameters when defining
classes, interfaces and methods.

Much like the more familiar formal parameters used in method
declarations, type parameters provide a way for you to re-use the
same code with different inputs. The difference is that the inputs to
formal parameters are values, while the inputs to type parameters are
types.

In test automation, we often create methods that work with **different types of web elements** (buttons,   
text fields, dropdowns). Instead of writing separate methods for each element type, generics allow us   
to write a single method that works for all elements dynamically.

```java
public <T> void clickElement(T element) {
    element.click();
}
```

Here, **<T>** is a generic type, meaning this method can work with **any element type**—whether it’s a 
WebElement, Button, or TextField. This makes our automation code **cleaner, reusable, and maintainable.**

* Without generics

```java
List list = new ArrayList();
list.add("Hello");
String s = (String) list.get(0); // Requires explicit casting
```

* With generics

```java
List<String> list = new ArrayList<>();
list.add("Hello");
String s = list.get(0); // No casting needed, type safety ensured
```

* you can define a generic method that works with any data type.

Here, <T> represents a type parameter, allowing the method to handle any type.
```
public class GenericMethodExample {
    public static <T> void printItem(T item) {
        System.out.println(item);
    }

    public static void main(String[] args) {
        printItem(100);       // ✅ Works with Integer
        printItem("Hello");   // ✅ Works with String
        printItem(10.5);      // ✅ Works with Double
    }
}
```

* Generic Class

```java
class Box<T> {
    private T item;

    public void setItem(T item) {
        this.item = item;
    }

    public T getItem() {
        return item;
    }
}

public class GenericClassExample {
    public static void main(String[] args) {
        Box<String> stringBox = new Box<>();
        stringBox.setItem("Hello");
        System.out.println(stringBox.getItem()); // ✅ Output: Hello

        Box<Integer> intBox = new Box<>();
        intBox.setItem(100);
        System.out.println(intBox.getItem()); // ✅ Output: 100
    }
}
```