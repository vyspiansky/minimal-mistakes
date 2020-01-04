---
title: Extra Ukrainian letters are not sorted well
categories: [MySQL]
tags: [collation, utf8_unicode_ci, Cyrillic, ORDER BY]
---

The problem is that Ukrainian letters are not sorted correctly by the alphabet, ie "і" and "є" are preceded by "а", "б", while using the `ORDER BY` operator in MySQL.

The possible reason is that a mistaken collation value has been used. To correctly sort the Ukrainian letters, the value must be `utf8_unicode_ci`.

**Note!** It’s worth pointing out that `utf8_unicode_ci` is more accurate than `utf8_general_ci` for Bulgarian, Belarusian, Macedonian, Russian, Serbian and Ukrainian languages. While `utf8_general_ci` is fine only for Russian and Bulgarian subset of Cyrillic.

We can specify the collation directly in a query

```sql
SELECT *
FROM <table_name>
ORDER BY <column_name>
COLLATE utf8_unicode_ci;
```

or change it  permanently.


1) Сhange column collation:

```sql
ALTER TABLE <table_name>
MODIFY <column_name> VARCHAR(255)
CHARACTER SET utf8
COLLATE utf8_unicode_ci;
```

2) Change table collation:

```sql
ALTER TABLE <table_name>
CONVERT TO
CHARACTER SET utf8
COLLATE utf8_unicode_ci;
```

3) Change database collation:

```sql
ALTER DATABASE <db_name>
CHARACTER SET utf8
COLLATE utf8_unicode_ci;
```
