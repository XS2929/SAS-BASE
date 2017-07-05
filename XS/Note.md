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
