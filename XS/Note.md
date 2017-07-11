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

mmddyy10.
01/01/2001

官网有好多种， google sas data format


--------------------------------------------------------

Tasks and Utilities -> Statistics -> Summary Statustics

选定column, 就可以得到一个统计摘要

Variable  Label  Mean  Std Dev  Minimum  Maximum  N(记录数)

--------   ----   ---   -----   -----     -----   -



--------------------------------------------------------

data string_example;

LENGTH string1 $ 13 string2 $ 5 string4 $ 22;
string1 = 'hello';
string2 = 'world';
string3 = string1 || string2;
substring1 = substrn(string1,2,2);
substring3 = substrn(string3,5);
substring4 = substrn(substring3,1,10);

string4 = 'hello fucking world  ';
string4_c = lengthc(string4);

string5_c = lengthc(trim(string4));


run;

proc print data = string_example noobs;
run;


/*在SAS里string的index值没有0，从1开始计
noobs 很好用， 不会显示observation number
|| 同python里set的相加， 而且保留前一个string后面的所有blank space
substrn 有三个输入值， 第一个是要做截取处理的string, 第二个是起始位，第三个是要取几个
TRIMN 去掉一个string末尾的空格
*/

--------------------------------------------------

/*关于数组 数组 array
 输入datalines时候
 分号一定要在新一行
 OF 与 MEAN, MAX, MIN, SUM 等一起用很方便 
 初次在SAS里面用if else，和sql一样蠢
 
 */
DATA ABOUT_ARRAY;
INPUT a1 $ a2 $ a3 $ a4 $ a5 $;
ARRAY AGE[10] (1 2 3 4 5 6 7 8 9 10);
age_mean = MEAN(OF AGE(*));
age_min = MIN(OF AGE(*));
age_max = MAX(OF AGE(*));
age_sum = SUM(OF AGE(*));
*ARRAY STR(0:4) $ a1-a5 Same;
ARRAY STR(*) $ a1-a5;
*ARRAY STR(5) $ a1-a5 Same;
mix = STR[1]||' '|| STR[4];
IF 'mo' in STR THEN MOO ='TRUE'; ELSE MOO = 'FALSE';
DATALINES;
ij ao mo gmm rt
sa wew rr y dv
we er tt qw rr
sf ee 12 55
;


RUN;

PROC PRINT DATA = about_array;
RUN;

--------------------------------------------------








