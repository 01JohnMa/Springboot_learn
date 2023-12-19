笛卡尔积的错误会在下面条件下产生：
  省略多个表的连接条件（或关联条件）
  连接条件（或关联条件）无效
  所有表中的所有行互相连接
  为了避免笛卡尔积， 可以在 WHERE 加入有效的连接条件。
  
【 强制 】对于数据库中表记录的查询和变更，只要涉及多个表，都需要在列名前加表的别名（或
表名）进行限定。
说明 ：对多表进行查询记录、更新记录、删除记录时，如果对操作列没有限定表的别名（或表
名），并且操作列在多个表中存在时，就会抛异常。
正例 ：select t1.name from table_first as t1 , table_second as t2 where t1.id=t2.id;
反例 ：在某业务中，由于多表关联查询语句没有加表的别名（或表名）的限制，正常运行两年
后，最近在 某个表中增加一个同名字段，在预发布环境做数据库变更后，线上查询语句出现出
1052 异常：Column 'name' in field list is ambiguous。
总结：连接 n个表,至少需要n-1个连接条件。比如，连接三个表，至少需要两个连接条件。(where)

😁
可以使用GROUP BY子句将表中的数据分成若干组
明确：WHERE一定放在FROM后面
在SELECT列表中所有未包含在组函数中的列都应该包含在 GROUP BY子句中，where
使用 WITH ROLLUP 关键字之后，在所有查询出的分组记录之后增加一条记录，该记录计算查询出的所
有记录的总和，

过滤分组：HAVING子句
1. 行已经被分组。
2. 使用了聚合函数。
3. 满足HAVING 子句中条件的分组将被显示。
4. HAVING 不能单独使用，必须要跟 GROUP BY 一起使用。和where区别 

WHERE 先筛选数据再关联，执行效率高 不能使用分组中的计算函数进行筛选
HAVING 可以使用分组中的计算函数 在最后的结果集中进行筛选，执行效率较低

查询结构
#方式1：
SELECT ...,....,...
FROM ...,...,....
WHERE 多表的连接条件
AND 不包含组函数的过滤条件
GROUP BY ...,...
HAVING 包含组函数的过滤条件
ORDER BY ... ASC/DESC
LIMIT ...,...
#方式2：
SELECT ...,....,...
FROM ... JOIN ...
ON 多表的连接条件
JOIN ...
ON ...
WHERE 不包含组函数的过滤条件
AND/OR 不包含组函数的过滤条件
GROUP BY ...,...
HAVING 包含组函数的过滤条件
ORDER BY ... ASC/DESC


顺序
SELECT DISTINCT player_id, player_name, count(*) as num # 顺序 5
FROM player JOIN team ON player.team_id = team.team_id # 顺序 1
WHERE height > 1.80 # 顺序 2
GROUP BY player.team_id # 顺序 3
HAVING num > 2 # 顺序 4
ORDER BY num DESC # 顺序 6
LIMIT 2 # 顺序 7













LIMIT ...,...
