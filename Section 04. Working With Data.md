## 12. Data set options

```
data salaryemp (keep = salary rename=salary=salaryemp);
infile '/home/u62043935/Dedic/salary.txt';
input year salary;
run;

proc print data=salaryemp;
run;
```

<img width="129" height="174" alt="image" src="https://github.com/user-attachments/assets/093edeb8-9b14-4379-a4b5-4f4c61686d80" />


### limit printing to only 4 observations

```
data salaryemp (keep = salary rename=salary=salaryemp);
infile '/home/u62043935/Dedic/salary.txt';
input year salary;
run;

proc print data=salaryemp(obs=4);
run;
```

<img width="133" height="134" alt="image" src="https://github.com/user-attachments/assets/3fa88187-72dd-4037-8a19-07c2855024fb" />



### limit printing to a range of observations
```
data salaryemp (keep = salary rename=salary=salaryemp);
infile '/home/u62043935/Dedic/salary.txt';
input year salary;
run;

proc print data=salaryemp(firstobs=3 obs=4);
run;
```

<img width="139" height="84" alt="image" src="https://github.com/user-attachments/assets/c6ca08ce-8bab-4467-b2cb-dc0ea9e3637c" />


## 13. what if your data is separated by a dot or something else? Delimiters

if your text file uses non space delimiter, you must specific it with DLM option

```
data salary;
infile '/home/u62043935/Dedic/salary_dot_delimiter.txt' DLM=".";
input year salary;
run;

proc print data=salary;
run;
```

<img width="142" height="182" alt="image" src="https://github.com/user-attachments/assets/c7e8645e-d69f-40b1-9e6e-a4ca37b6d692" />

## 14. Reading data instream in data step (typing data right into coding area)

### Free formatted

```
data beer;
input brand$ origin$ price;
cards;
budweiser USA 14.99
Heineken NED 13.99
Corona MEX 12.99
SamAdams USA 14.79
Guiness IRE 17.99
;
run;

proc print data=beer;
run;
```

<img width="236" height="158" alt="image" src="https://github.com/user-attachments/assets/d4ed3a57-6e4b-496b-9b1d-7ddbba259c64" />

### Fixed formatted
```
data beer;
input brand$ 1-9 origin$ 10-12 price 13-17;
cards;
budweiserUSA14.99
Heineken NED13.99
Corona   MEX12.99
SamAdams USA14.79
Guiness  IRE17.99
;
run;

proc print data=beer;
run;
```

<img width="236" height="158" alt="image" src="https://github.com/user-attachments/assets/d4ed3a57-6e4b-496b-9b1d-7ddbba259c64" />


##14. Reading Dates in Data

```
data dates;
input name$ bday date11.;
cards;
Eric 4 Mar 1985
Doug 15 Feb 1976
Sean 14 Jun 1975
Lisa 5 Jan 1988
;
run;

proc print data=dates; run;
```

<img width="153" height="135" alt="image" src="https://github.com/user-attachments/assets/b803b10e-5ca0-4d11-9a2d-a6037e1c2d56" />

you can see the dates are the number of dates from 1960-01-01.

we need to change the format in the PROC PRINT statement

```
data dates;
input name$ bday date11.;
cards;
Eric 4 Mar 1985
Doug 15 Feb 1976
Sean 14 Jun 1975
Lisa 5 Jan 1988
;
run;

proc print data=dates;
format bday date9.;
run;
```

<img width="189" height="133" alt="image" src="https://github.com/user-attachments/assets/e69813ab-49ea-4a2b-be75-fbc0be82546f" />


## 16. Creating variables and calculations

```
data houseprice;
infile '/home/u62043935/Dedic/houseprice.txt';
input type$ price tax;
Actualamountoftax = round( price * tax);
run;

proc print data=houseprice; run;
```

<img width="343" height="113" alt="image" src="https://github.com/user-attachments/assets/6ee0321e-6b4d-4033-a306-5f1869f407f6" />


### using datalines / cards statement

```
data houseprice;
input type$ price tax;
Actualamountoftax = round( price * tax);
datalines;
Single 300000 0.20
Single 250000 0.25
Duplex 175000 0.15
run;

proc print data=houseprice; run;
```


## 17 more on creating variables

```
data sales;
input Name$ Sales_1-Sales_4;
Cards;
Greg 10 2 40 0
John 15 5 10 100
Lisa 50 10 15  50
Mark 50 0 5 20
;
run;
```















































































































