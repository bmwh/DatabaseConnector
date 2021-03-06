DatabaseConnector
=================

Introduction
============
This R package is a wrapper around RJDBC containing drivers for various DBMSs. 

Features
========
- Create connections to the various database platforms:
  - SQL Server
  - Oracle
  - Postgres
  - Amazon Redshift
  - MySQL
  - Netezza (driver not included)
- Statements for executing queries with 
  - Error reporting to file
  - Progress reporting
  - Multiple statements per query
- Support for fetching data to ffdf objects

Examples
========
```r
connectionDetails <- createConnectionDetails(dbms="mysql", 
                                             server="localhost",
                                             user="root",
                                             password="blah",
                                             schema="cdm_v4")
conn <- connect(connectionDetails)
querySql(conn,"SELECT COUNT(*) FROM person")
dbDisconnect(conn)
```

Technology
============
DatabaseConnector is an R package using Java's JDBC drivers. 

System Requirements
===================
Requires R. Also requires Java 1.6 or higher (Oracle Java is recommended. [Issues](https://github.com/OHDSI/DatabaseConnector/issues/8) have been reported when using GCJ.) 

Dependencies
============
Please note that this package requires Java to be installed. If you don't have Java already intalled on your computed (on most computers it already is installed), go to [java.com](http://java.com) to get the latest version.

To be able to use Windows authentication for SQL Server, you have to install the JDBC driver. Download the .exe from [Microsoft](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=11774) and run it, thereby extracting its contents to a folder. In the extracted folder you will find the file sqljdbc_4.0/enu/auth/x64/sqljdbc_auth.dll (64-bits) or sqljdbc_4.0/enu/auth/x86/sqljdbc_auth.dll (32-bits), which needs to be moved to location on the system path, for example to c:/windows/system32.

In order to enable Netezza support, place your Netezza jdbc driver at `inst/java/nzjdbc.jar` in this package.


Getting Started
===============
Use the following commands in R to install the DatabaseConnector package:

  ```r
  install.packages("devtools")
  library(devtools)
  install_github("ohdsi/DatabaseConnector") 
  library(DatabaseConnector)
  ```

Getting Involved
=============
* Package manual: [DatabaseConnector manual](https://raw.githubusercontent.com/OHDSI/DatabaseConnector/master/man/DatabaseConnector.pdf) 
* Developer questions/comments/feedback: <a href="http://forums.ohdsi.org/c/developers">OHDSI Forum</a>
* We use the <a href="../../issues">GitHub issue tracker</a> for all bugs/issues/enhancements

License
=======
DatabaseConnector is licensed under Apache License 2.0. The JDBC drivers fall under their own respective licenses.

Development
===========
DatabaseConnector is being developed in R Studio.

###Development status
Stable. The code is actively being used in several projects.


# Acknowledgements
- This project is supported in part through the National Science Foundation grant IIS 1251151.

