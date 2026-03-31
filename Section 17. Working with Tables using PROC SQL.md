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























## 85. Inserting Rows with a Query and Set Statement

















