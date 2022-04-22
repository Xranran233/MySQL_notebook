# MySQL_notebook
## 一. 关于时间日期
1. DATEDIFF(day1,day2) 计算两个日期相差天数,day1大于day2,结果为正
```
DATEDIFF('2007-12-31','2007-12-30');   #  1
DATEDIFF('2010-12-30','2010-12-31');   # -1
```
2. TIMESTAMPDIFF
```
#计算相差天数：
select TIMESTAMPDIFF(DAY,'2019-05-20', '2019-05-21'); # 1

#计算相差小时数：
select TIMESTAMPDIFF(HOUR, '2015-03-22 07:00:00', '2015-03-22 18:00:00'); # 11

#计算相差秒数：
select TIMESTAMPDIFF(SECOND, '2015-03-22 07:00:00', '2015-03-22 7:01:01'); # 61
```
