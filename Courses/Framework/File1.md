# Automation Framework Development with Selenium Java

## What is an Automation Framework?
* In a simple sense, Automation Testing Framework is a way to organize the code as much as possible

That's it?

* BUT IT SHOULD BE 
    * Reusable
    * Scalable
    * Maintainable
    * Understandable
    * Workable

1. REUSABLE - A framework once written, should be used by multiple people across same or multiple
team meaning it should be used across **multiple** proiects, not limiting to one single
proiect
* Using framework one can reduce the effort spent on 'A' component (library of code)
which is **already** written or available

* Using the **existing** code (reusing the code) will require **less** or **no testing** since the
existing code is not new and its already in use.

* This will save much of team time instead of reinventing the wheel !!!

2. SCALABLE - 
* Frameworks written should be scalable, meaning it should be used from small to
bigger proiect
* Framework should be scaled to support multiple technologies and tools.
* Technologies can be web or windows or even service based

3. MAINTAINABLE - 

* Framework should be easily maintainable, meaning, the code need to be segregated
as a logical groups of same type (classes) and functionalities (methods)
    * Something like commenting on each codes
* Each and every code in framework should be documented, so that, duplicate code
should will not emerge as a result lack of knowledge on existing code.
* Framework should be different entity from that of test proiect, so that, changes to
framework will go to framework proiect whereas changes to test goes to test proiect.

4. WORKABLE -  

* Framework should be usable by the team.
* Framework should be pluggable and even less knowledge automation test engineer
should work with code using the framework methods


## TYPES OF FRAMEWORK

There are different types of framework available and some of the most commonly  
used automation testing  
* Data Driven Framework
* Keyword Driven Framework
* Hybrid Framework

BPT, which is most common in QTP world

### DATA DRIVEN FRAMEWORK

Data Driven framework are used where testing relies on large data set.  

E.g. Online Candidate Form, which requires lot of input data to be supplied by user  
(tester in our case) with different combination (permutations gnd combinations).  

These different combinations of data cannot be hardcoded in our Java class files,  
hence they need to be pulled from external data sources. 

The data source can be xml, excel or SQL database tables. 

Hence data driven framework will have code to pull data from any of the data  
source, which can then be used to populate data on application IJI during data entry  
operations

### KEYWORD DRIVEN FRAMEWORK
In Keyword driven frameworks both the applications UI object and test data are
coded within C# class files.  
Here each and every operations are represented as keywords e.g. SendEmail(),
RegisterUser(), Logout().  

New test cases can reuse the existing keyword very easily.

Easy to modify and maintain the code

But require more programming knowledge.

### HYBRID FRAMEWORK

Hybrid framework are the combination of Keyword driven and data driven framework.

Hybrid framework will pull data from external data sources and also it uses keyword to perform operation such as RegisterUser(), SendEmail() etc.



## AUTOMATION TESTING MODEL

There are different models available which can be used while designing a framework, some of the most commonly used are

1. BDD - Behavioral Driven Development Model
2. POM - Page Object Model

### BEHAVIORAL DRIVEN DEVELOPMENT

BDD - Behavioral Driven Development is based on Test Driven Development (TDD)
and it aims to bridge the gap between Business analyst and developers.

BDD not only bridges the gap between business analyst and developers but also
between
✅ Manual QA with Automation testers (who write BDD)
✅ Manual QA with Developers

BDD seems to be like a plain text, but they have their own syntax based on certain
tools (which we will discuss next)

### BDD SUPPORTED TOOLS

There are many tools available to support BDD, some most famous tools are 

* Cucumber (Ruby) /Freshen (PHP)
* Jbehave (Java) /Nbehave (C#)
* SpecFlow (C#)

All the above tools are used in conjunction with many different platforms and  
languages like JAVA, C#, Ruby, Python, Jruby etc

But all the above tools has one language in common (at least as one of the) which is
Gherkin (which we will discuss next)

### PAGE OBJECT MODEL
Each webpage Ul Will have different obiects (Ul Elements) to interact.

These obiects are identified and written in the code (Java or along with their identification
property.

A Page Object simply models the obiects within the test code. This reduces the amount of  
duplicated code and means that if the UI changes, the fix need only be applied in one place.