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
