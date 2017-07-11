用Snippets导入和导出csv更有效率

#create new column
DATA OUTPUT;
	SET SASHELP.CARS;
	MARKUP=MSRP-INVOICE;
RUN;
PROC PRINT DATA=output;
RUN;

#import csv
data test;
	infile '/folders/myfolders/sasuser.v94/TEST.csv' dlm=',' firstobs=2;
	input address $;
run;


#use data from work library 
data output;
set work.import;
where origin='Asia' and type='SUV';
run;

proc print data=output;
run;

#if else if else then do end in SAS
data output;
	set sashelp.cars;
	length cat$ 10;
	length todo$ 10;
	if origin = 'Asia' then 
		do; 
		cat = 'cheap';
		todo='buy';
		end;
	else if origin = 'USA' then 
		do;
		cat = 'medium';
		todo='nvm';
		end;
	else do;
		cat = 'expensive';
		todo='nvm';
		end;
run;

proc print data=output;
run;
-----------------------------------------------------------
列出一个library所含内容

PROC CONTENTS DATA = SASHELP._all_ nods;
RUN;

-----------------------------------------------------------

用LABEL 

options LABEL;
data work.temp;
input ID $ name $ salary department $;
comm = salary*0.25;
LABEL ID = 'employee id' 
	  comm = 'commisions';
DATALINES;
1 A 4590 IT
2 B 23432 HR
3 C 23    OP
4 D 5000   FI
;
run;
proc print data = work.temp;
run;

proc contents data = work.temp;
run;
-----------------------------------------------------------
注释行

单行注释
多行注释
messge类型注释

/*This is a mutiple
line
commnet*/

*This is a single line comment;



*This is a two-line comment
*weird syntax;
-----------------------------------------------------------

Date 的不同种类

DATE9.
02APR2001

MONYY.
JAN49

--------------------------------------------------------

Tasks and Utilities -> Statistics -> Summary Statustics

选定column, 就可以得到一个统计摘要

Variable  Label  Mean  Std Dev  Minimum  Maximum  N(记录数)

--------   ----   ---   -----   -----     -----   -














