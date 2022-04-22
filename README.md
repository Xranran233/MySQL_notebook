# MySQL_notebook
## 一. 关于时间日期
1. DATEDIFF(day1,day2) 计算两个日期相差天数,day1大于day2,结果为正
```
DATEDIFF('2007-12-31','2007-12-30');   #  1
DATEDIFF('2010-12-30','2010-12-31');   # -1
```
2. TIMESTAMPDIFF(day/hour/second,time1,time2), 计算时间差
```
#计算相差天数：
select TIMESTAMPDIFF(DAY,'2019-05-20', '2019-05-21'); # 1

#计算相差小时数：
select TIMESTAMPDIFF(HOUR, '2015-03-22 07:00:00', '2015-03-22 18:00:00'); # 11

#计算相差秒数：
select TIMESTAMPDIFF(SECOND, '2015-03-22 07:00:00', '2015-03-22 7:01:01'); # 61
```
3. 从日期减去指定的时间间隔 DATE_SUB(), 将时间/日期间隔添加到日期 adddate()
```
DATE_SUB("2008-12-29",INTERVAL 2 DAY) # 2008-12-27
adddate("2015-01-03",INTERVAL 1 day)  # 2015-01-04
```
