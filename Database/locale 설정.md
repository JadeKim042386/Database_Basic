---
share: "true"
---

## local 확인

```mysql
SELECT @@lc_time_names;
```
```
+-----------------+ 
| @@lc_time_names | 
+-----------------+ 
| en_US           | 
+-----------------+
```

## local 변경

```mysql
SET lc_time_names = 'ko_KR';
```

국가별 `Locale Value`는 아래 참조 링크를 통해 확인 할 수 있다.

[reference]
https://dev.mysql.com/doc/refman/8.0/en/locale-support.html