






```
data lengthfunctions;
one = 'ABC       ';
two = ' ';
three = 'ABC   XYZ';
length_one = lengthn(one);
length_two = length(two);
length_three = length(three);
run;
 
proc print data = lengthfunctions; run;
```
