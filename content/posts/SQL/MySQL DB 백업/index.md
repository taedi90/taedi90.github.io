---
title: "[mysqldump] MySQL DB 백업 및 복구"
date: 2021-11-29T00:00:00+09:00
lastmod: 2021-12-08T11:27:00+09:00
hero: images/hero/sql.png
url: /mysql-dump/
description: 
tags: 
menu:
  sidebar:
    name: MySQL DB 백업
    identifier: SQL-MySQL DB 백업
    parent: SQL
    weight: 
---


## 백업

```bash
# mysqldump -u root -p --databases [DB명] > [저장경로/파일명]
mysqldump -u root -p --databases [DB명] > /var/lib/mysql/project_2021-12-07.sql
```

## 복원

```bash
# mysqldump -u root -p [DB명] < [저장경로/파일명]
mysql -u root -p project < /var/lib/mysql/project_2021-12-07.sql
```

## 참고

- [https://code-factory.tistory.com/21](https://code-factory.tistory.com/21)