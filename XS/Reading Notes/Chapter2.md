继续

列出一个library的所含内容，指令

PROC CONTENTS DATA = SASHELP._all_ nods;
RUN;
-------------------------------------------
列出一个library里面某set的内容， 指令
PROC CONTENTS DATA = SASHELP.CARS;
RUN;
--------------------------------------

listing frequency by one of the column. 


option date;
proc freq data=sashelp.cars;
tables make;
run;


-------------------------------------------

p65

