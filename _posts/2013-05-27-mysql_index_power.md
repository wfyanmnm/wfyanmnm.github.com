---
layout: post
title: "mysql索引的威力"
description: ""
category: mysql
tags: [mysql, index]
---
对mysql索引这块儿一直不了解，今天看了一下，拿自己机器上一个测试数据库试了下，发现真的很强大。

没用索引时的执行情况

    mysql> select result_id, do_id, result_value from result where owner_id = 58022337304;
    +-----------+-----------+--------------+
    | result_id | do_id     | result_value |
    +-----------+-----------+--------------+
    |    468601 | 22102233415 |           30 |
    +-----------+-----------+--------------+
    1 row in set (0.36 )

给owner_id加上索引

    mysql> alter table result add index owner(owner_id);
    Query OK, 462581 rows affected (1 min 17.91 )
    Records: 462581  Duplicates: 0  Warnings: 0

再执行前边的命令

    mysql> select result_id, do_id, result_value from result where owner_id = 58022337304;
    +-----------+-----------+--------------+
    | result_id | do_id     | result_value |
    +-----------+-----------+--------------+
    |    468601 | 22102233415 |           30 |
    +-----------+-----------+--------------+
    1 row in set (0.03 )

执行时间一下子从`0.36`缩短到`0.03`
再执行一遍

    mysql> select result_id, do_id, result_value from result where owner_id = 58022337304;
    +-----------+-----------+--------------+
    | result_id | do_id     | result_value |
    +-----------+-----------+--------------+
    |    468601 | 22102233415 |           30 |
    +-----------+-----------+--------------+
    1 row in set (0.00 )

执行时间更短
{% include JB/setup %}
