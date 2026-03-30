## 77. How to Perform an Inner Join

```
data humanresources;
input empid $ title $ gender $;
datalines;
000123 Sales Male
000124 Sales Female
000125 Marketing Female
000126 Finance Female
000127 HR Male
000128 Sales Female
Run;

data contactinfo;
input empid $ fname $ phone email $50.;
datalines;
000123 Larry 4554545 larry@email.com
000124 Susan 123407 Susan@email.com
000125 Jen 125123 Jen@email.com
000126 Gloria 6343245 Gloria@email.com
000127 James 1236345 James@email.com
000128 Sharon 62345 Sharon@email.com
run;

proc sql;
select hr.*, fname, phone, email
from humanresources as hr
inner join contactinfo as ci
on hr.empid = ci.empid
order by hr.empid;
quit;
```

<img width="430" height="176" alt="image" src="https://github.com/user-attachments/assets/a978edc9-d502-408e-8736-2c656fd6b757" />



## 78. How to Join Three Tables












































