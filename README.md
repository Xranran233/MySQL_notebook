# MySQL_notebook
## 一. 关于日期时间
### POINT1.1. 关于计算日期时间差
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
4. interval()
```
"2015-01-03"+interval'1' day #2015-01-04
```
5. 返回从0000年到现在的天数
```
TO_DAYS("2017-06-20")        #736865
```
### POINT1.2. 转换日期格式
1. DATE_FORMAT()函数

DATE_FORMAT(date,format) 函数用于将指定的日期格式化为给定的格式值，即将给出一个日期，该函数将该日期格式化为指定的格式参数。
![image](https://user-images.githubusercontent.com/79103918/204432760-1d6a174f-1b52-4cd2-9aab-7b354d811795.png)

2. STR_TO_DATE()函数

STR_TO_DATE(str,format)函数是将时间格式的字符串（str），按照所提供的显示格式（format）转换为DATETIME类型的值。
```
SELECT STR_TO_DATE('30Apr19','%d%b%y')      #2019-04-30
SELECT STR_TO_DATE('21,5,2022','%d,%m,%Y');    #2022-05021
SELECT STR_TO_DATE("2022,6,14 10,40,10", "%Y,%m,%d %h,%i,%s")      #2022-06-14  10:40:10
```

## 一. 排序函数
1. rank()      并列跳跃排名，并列即相同的值，相同的值保留重复名次，遇到下一个不同值时，跳跃到总共的排名

2. dense_rank()   并列连续排序，并列即相同的值，相同的值保留重复名次，遇到下一个不同值时，依然按照连续数字排名

3. row_number()   连续排名，即使相同的值，依旧按照连续数字进行排名

Example:
| Value | rank | dense_rank | row_number |
|-------|------|------------|------------|
|  30   |   1  |     1      |     1      |
|  30   |   1  |     1      |     2      |
|  40   |   3  |     2      |     3      |
|  50   |   4  |     3      |     4      |
|  60   |   5  |     4      |     5      |

