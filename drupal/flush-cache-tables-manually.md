# Flush Cache Tables Manually (Drupal)

For those times when Drupal is being a punk and not truly flushing the cache.

```
SELECT concat('TRUNCATE TABLE ', TABLE_NAME, ';')  FROM INFORMATION_SCHEMA.TABLES  WHERE TABLE_NAME LIKE 'cache%';
```

[Source](https://stackoverflow.com/a/1575435)
