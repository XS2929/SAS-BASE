继续

列出一个library的所含内容, prints a summary of all files stored in the library named sashelp

PROC CONTENTS DATA = SASHELP._all_ nods;
RUN;
----------------------------------------------------
列出一个library里面某set的内容， 指令
PROC CONTENTS DATA = SASHELP.CARS;
RUN;
-----------------------------------------------------

如果用listing, 可以控制输出，显示line size, page size, page numbers, data and time

listing frequency by one of the column. 

FREQ

option date;
proc freq data=sashelp.cars;
tables make;
run;


----------------------------------------------------

用firstobs obs 定义要显示的行（observation）


options firstobs=8 obs=26;
proc print data = sashelp.cars;
run;


-----------------------------------------------------

显示数据集信息， 两者基本一样

proc datasets;
contents data = sashelp.cars;
run;


proc contents data = sashelp.cars;
run;
 -------------------------------------------------------

 options data nodate number nonumber pageno=value pagesize=value(the value includes the lines used by the title, data and so on) linesize = value (specifies the width of the print line)



----------------------------------------------------------

The value of YEARCUTOFF only affects 2-digit year value

Example YEARCUTOFF = 1950

1950 <- 100 years -> 2049

Date expression             Interpreted as

_12/07/41                   _12/07/2041
_18Dec15                    _18Dec2015
_04/15/30                   _04/15/2030
_15Apr95                    _15Apr1995

-----------------------------------------------------------




QUIZ note

1. print all contents of a library called sashelp

proc contents data = sashelp._all_ nods;


2. Librefs can not last from one SAS section to another


3. libname osiris spss 'c:\myfiles\doc\data.spss'

This defines a library called osiris using spss engine

---------------------------------------------------------












