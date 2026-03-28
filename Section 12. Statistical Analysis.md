## 59. Doing an Independent samples t-test analysis
```
data qualitylife;
infile '/home/u62043935/Dedic/qualityoflife.txt';
input socioeconomicstatus$ QLI;
run;

proc print data=qualitylife; run;

proc ttest data = qualitylife;
Title "The impact of SES on QLI";
class socioeconomicstatus;
var QLI;
run;
```

<img width="678" height="1623" alt="image" src="https://github.com/user-attachments/assets/1d5b0b84-ae15-4c05-886d-3973240c9597" />


## 61. Doing a Chi-square (independent groups) analysis
```
data party_affiliation;
input gender$ party$ count;
datalines;
male republican 100
male independent 120
male democrat 60
female republican 350
female independent 200
female democrat 90
;
run;

proc freq data=party_affiliation;
tables  gender*party / chisq;
weight count;
run
```

<img width="458" height="569" alt="image" src="https://github.com/user-attachments/assets/3c982c43-a81d-42da-bea7-db18b03c2a02" />


## 63. Performing the Linear Regression

```
data sevenminscreen;
infile '/home/u62043935/Dedic/7minscreen.csv' DSD Missover firstobs=2;
input x y;
runs;

proc print data=sevenminscreen; run;

proc reg data=sevenminscreen;
model y=x;
run;


data sevenminscreen;
infile '/home/u62043935/Dedic/7minscreen.csv' DSD Missover firstobs=2;
input x y;
runs;

proc reg data=sevenminscreen;
model y=x / all;
run;
```

<img width="872" height="1756" alt="image" src="https://github.com/user-attachments/assets/1cf56f21-8160-4625-b300-1a10e884a0b5" />

<img width="831" height="1241" alt="image" src="https://github.com/user-attachments/assets/ee7756a2-b21f-4b60-9880-6a9263ed3551" />


## 64. Performing Multiple Regression

```
data sevenminscreen;
infile '/home/u62043935/Dedic/7minscreen_multiple.csv' DSD Missover firstobs=2;
input x y z;
runs;

proc print data=sevenminscreen; run;

proc reg data=sevenminscreen;
model z=x y;
run;
```

<img width="423" height="844" alt="image" src="https://github.com/user-attachments/assets/9a534c59-64d0-4eb8-825b-db48561f1540" />
<img width="831" height="1363" alt="image" src="https://github.com/user-attachments/assets/37f3ac71-943a-410f-8668-35dd658fa5ea" />


### Correlation
```
data sevenminscreen;
infile '/home/u62043935/Dedic/7minscreen_multiple.csv' DSD Missover firstobs=2;
input x y z;
runs;

proc print data=sevenminscreen; run;

proc corr data=sevenminscreen;
var x y z;
run;
```

<img width="474" height="735" alt="image" src="https://github.com/user-attachments/assets/8a20e98c-8945-4540-8f7d-1066b281cfbc" />



























