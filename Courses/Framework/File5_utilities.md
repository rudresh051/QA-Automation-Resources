# Utilities

Utilities as the name, are the libraries of code which act as a reusable code for the whole framework

These Utilities act as a shared libraries for all the code within our framework and project which refers them

THE FIRST 90 PERCENT OF THE CODE ACCOUNTS
FOR THE FIRST 90 PERCENT OF THE DEVELOPMENT
TIME...THE REMAINING 10 PERCENT OF THE CODE
ACCOUNTS FOR THE OTHER 90 PERCENT OF THE
DEVELOPMENT TIME.

Plan - 
* CucumberUtil
* DatabaseUtil
* ExcelUtil
* LogUtil
* ReportingUtil

## Developing Excel Utility
EXCEL HELPER ACT AS LIBRARY TO READ
DATA FROM EXCEL SHEET, PARSE DATA
AND STORE DATA IN-MEMORY
COLLECTIONS

![alt text](image-8.png)

### JXL

Java Excel API is a mature, open source java API enabling developers
to read, write, and modifiy Excel spreadsheets dynamically. Now java
developers can read Excel spreadsheets, modify them with a
convenient and simple API, and write the changes to any output
stream
We can add the reference of JXL from Maven Repo

### In-memory collection

We will be storing all the Excel data read from excel sheet into
HashTable of Java, so that we don't end up with lot of read/write IO
operation while executing automation code. (this will end up in slow
execution of automation script)

![alt text](image-9.png)