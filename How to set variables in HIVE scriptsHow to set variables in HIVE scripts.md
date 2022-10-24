# How to set variables in HIVE scripts

Kita bisa menggunakan hiveconf khusus sebagai substitusi variabel. misalnya
```
hive> set CURRENT_DATE='2012-09-16';
hive> select * from foo where day >= ${hiveconf:CURRENT_DATE}
```

Demikian juga kita dapat menggunakannya pada command line:
```
% hive -hiveconf CURRENT_DATE='2012-09-16' -f test.hql
```

Pada hiveql script:
```
SELECT * FROM foo WHERE day >= '${hivevar:CURRENT_DATE}'
```

Untuk mengeksekusinya seperti dibawah ini:
```
hive --hivevar CURRENT_DATE="2012-09-16" -f hive_query.sql
```


Referensi:
https://stackoverflow.com/questions/12464636/how-to-set-variables-in-hive-scripts

State: need to test
