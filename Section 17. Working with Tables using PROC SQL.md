## 83. How to Create a Table using SAS SQL

```
data info;
input empid $ fname $ height;
datalines;
123 John 175
124 Mary 155
125 Lisa 190
126 Joseph 187
run;

data info2;
input empidd $ weight;
datalines;
123 150
124 120
125 180
126 160
run;

proc sql;
    title 'Final Table';
    create table final as
    select 
        i.empid label='Employ ID' format=$6.,
        i.fname,
        i.height,
        ii.weight
    from info as i 
    full join info2 as ii
        on i.empid = ii.empidd
    ;
    select * from final;
quit;
```

<img width="225" height="138" alt="image" src="https://github.com/user-attachments/assets/38844bdb-2343-4486-8ae0-55043d951a83" />





## 84. Altering Columns (add, modify, delete + adding values to column)


```
data info;
input empid $ fname $ salary;
datalines;
123 John 50000
124 Mary 65000
125 Lisa 95000
126 Joseph 43000
run;

data info2;
input empidd $ bonus;
datalines;
123 2500
124 4500
125 100000
126 1700
run;

proc sql;
    title 'Final Table';
    create table final as
    select 
        i.empid label='Employ ID' format=$6.,
        i.fname,
        i.salary,
        ii.bonus
    from info as i 
    full join info2 as ii
        on i.empid = ii.empidd
    ;
    select * from final;
quit;

proc sql;
alter table final
add totalcomp num label='Total Compensation' format=dollar8.;
select * from final;
quit;

proc sql;
update final
set totalcomp=salary+bonus;

select empid, fname, salary, bonus, totalcomp
from final;
```

<img width="478" height="699" alt="image" src="https://github.com/user-attachments/assets/3406686d-3cba-404d-abfd-c5e7b9a99992" />





## 85. Inserting Rows with a Query and Set Statement

### using INSERT INTO

```
data info;
input empid $ fname $ height;
datalines;
123 John 175
124 Mary 155
125 Lisa 190
126 Joseph 187
run;

data info2;
input empidd $ weight;
datalines;
123 150
124 120
125 180
126 160
run;

proc sql;
    title 'Final Table';
    create table final as
    select 
        i.empid label='Employ ID' format=$6.,
        i.fname,
        i.height,
        ii.weight
    from info as i 
    full join info2 as ii
        on i.empid = ii.empidd
    ;
    select * from final;
quit;

proc sql;
title 'New Final';
create table newfinal
		like final;
		quit;
		
		
proc sql;
insert into newfinal
select * from final;

select * from newfinal;
quit;
```

<img width="306" height="449" alt="image" src="https://github.com/user-attachments/assets/3ff8fff2-7623-4597-b3c7-348aed15d545" />

### Using SET statement

```
 data info;
input empid $ fname $ height;
datalines;
123 John 175
124 Mary 155
125 Lisa 190
126 Joseph 187
run;

data info2;
input empidd $ weight;
datalines;
123 150
124 120
125 180
126 160
run;

proc sql;
    title 'Final Table';
    create table final as
    select 
        i.empid label='Employ ID' format=$6.,
        i.fname,
        i.height,
        ii.weight
    from info as i 
    full join info2 as ii
        on i.empid = ii.empidd
    ;
    select * from final;
quit;

proc sql;
title 'New Final';
create table newfinal
		like final;
		quit;
		
		
proc sql;
insert into newfinal
select * from final;

proc sql;
insert into newfinal
set empid='127',
	fname = 'John',
	height = 175,
	weight = 152;

	select * from newfinal;
quit;
```

<img width="394" height="483" alt="image" src="https://github.com/user-attachments/assets/f57696a8-3218-4d1a-b8e1-2b5f1cfdc9f0" />


### Deleting a row

```
data info;
input empid $ fname $ height;
datalines;
123 John 175
124 Mary 155
125 Lisa 190
126 Joseph 187
run;

data info2;
input empidd $ weight;
datalines;
123 150
124 120
125 180
126 160
run;

proc sql;
    title 'Final Table';
    create table final as
    select 
        i.empid label='Employ ID' format=$6.,
        i.fname,
        i.height,
        ii.weight
    from info as i 
    full join info2 as ii
        on i.empid = ii.empidd
    ;
    select * from final;
quit;

proc sql;
delete from final
where fname like 'M%';

select * from final;
quit;
```


<img width="315" height="434" alt="image" src="https://github.com/user-attachments/assets/37711ee5-cdc3-4ad2-bd10-aa53e4fdd309" />









