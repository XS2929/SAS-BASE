This files contains my chapter one reading notes

基本语义

DATA: put your data into a SAS data set
      compute values
      check for and correct errors in your data
      produce  new SAS data sets by subsetting, supersetting, merging and updating existing data sets. 

PROC: create a report that lists the data
      produce descriptive statistics
      create a summary report 
      produce plots and charts
DROP=
KEEP=
SET
BY
RUN

实例：
DATA sasuser.admit2;
    set sasuser.admit;
    where age > 39;
RUN;
PROC print data = sasuser.admit2;
RUN;

关于sas文件起名字： 
                1-32 characters long
                begins with a letter or underscore
                continues with any combination of numbers, variables or underscore


关于 Data Portion

Observations (Rows)

Variables (Columns)

关于 Data Type

character, 可以包含任意值, a blank represents a missing value

numeric， 1-9 . - + E 意味着支持科学计数法, a period represents a missing value

一般都有 length

关于 variable

can be 1 to 32 characters long
must begin with a letter or an underscore
can continue with any combination of numbers, letters and underscores



Quiz notes: 

When encounters a DATA, PROC or RUN statement, SAS stops reading and executes the previous step in the program.

The default length for numeric variable is 8, 8 bytes. 

To reference a temporary SAS data set:    Work.name name



















