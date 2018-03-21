---
layout: post
title: Mysql explain 中 key_len 的计算
date: 2018-3-8 10:21:45 +0800
categories: Mysql
tag: Mysql
description: Mysql执行计划key_len的计算规则，通过key_len查看联合索引使用情况 
keywords: java mysql key_len 联合索引
---
* content
{:toc}

`Mysql` 执行计划中 `key_len` 字段的计算规则，通过 `key_len` 值分析联合索引使用情况。

<!-- more -->

<!-- TOC -->

- [Mysql key_len 计算规则](#mysql-key_len-计算规则)

<!-- /TOC -->

## Mysql key_len 计算规则

* 所有的索引字段，如果没有设置not null，则需要加一个字节。
* 定长字段，int占四个字节、date占三个字节、char(n)占n个字符。
* 对于变成字段varchar(n)，则有n个字符+两个字节。
* 不同的字符集，一个字符占用的字节数不同。latin1编码的，一个字符占用一个字节，gbk编码的，一个字符占用两个字节，utf8编码的，一个字符占用三个字节。

> 示例：

| 列类型 | KEY_LEN | 备注 | 
| - | :-: | -: | 
| id int | key_len = 4+1 = 5| 允许NULL，加1-byte | 
| id int not null | key_len = 4 | 不允许NULL | 
| user char(30) utf8 | key_len = 30*3+1 | 允许NULL |
| user varchar(30) not null utf8 | key_len = 30*3+2 | 动态列类型，加2-bytes |
| user varchar(30) utf8 | key_len = 30*3+2+1 | 动态列类型，加2-bytes；允许NULL，再加1-byte |
| detail text(10) utf8 | key_len = 30*3+2+1 | TEXT列截取部分，被视为动态列类型，加2-bytes；且允许NULL |

> ![#1589F0](https://placehold.it/15/DC143C/000000?text=+) `key_len` 只指示了 `WHERE` 中用于条件过滤时被选中的索引列，是不包含 `ORDER BY/GROUP BY` 这部分被选中的索引列。