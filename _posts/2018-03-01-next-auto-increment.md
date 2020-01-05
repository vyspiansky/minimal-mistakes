---
title: Next AUTO_INCREMENT value
categories: [MySQL]
tags: [AUTO_INCREMENT]
---

To get the next `AUTO_INCREMENT` value from a table run the following query:

```sql
SELECT AUTO_INCREMENT
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "databaseName"
AND TABLE_NAME = "tableName"
```