# DataWorks

DataWorks专有版使用笔记

1.类似"2024/7/12 12:3:4" 这种字符串转化时间格式，使用to_date没法直接转换，需要先使用 正则替换函数进行替换成'yyyy/mm/dd hh:mi:ss'，在使用 to_date函数进行时间转化

  1).select REGEXP_REPLACE(REGEXP_REPLACE(REGEXP_REPLACE(REGEXP_REPLACE(REGEXP_REPLACE('2024/5/5 2:1:7','/(\\d)/', '/0\\1/'), '/(\\d) ', '/0\\1 '), ' (\\d):', ' 0\\1:'),':(\\d):',':0\\1:'),':(\\d)$',':0\\1')
  
  2).to_date(filed,'yyyy/mm/dd hh:mi:ss')

  

2.LATERAL VIEW EXPLODE() 爆裂函数使用，类似UDTF,将一行记录变成多行记录

select *  from table a LATERAL VIEW EXPLODE(SPLIT(filed, separator)) exploded_table AS xx
