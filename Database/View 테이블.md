---
share: "true"
---
- 실질적으로 존재하는 테이블이 아닌 정의만 가지고 있는 가상의 `READ ONLY` 테이블
- 장점
	- **독립성**: 테이블 구조가 변경되어도 뷰를 사용하는 응용프로그램은 변경하지 않아도 된다.
	- **편리성**: 복잡한 쿼리를 뷰로 생성함으로써 관련 질의를 단순하게 작성할 수 있음
	- **보안성**: 권한에 따로 표시하지 않아야하는 칼럼의 경우 숨길 수 있음

## 뷰 생성

```mysql
create view {TABLE NAME} as
	{query}
;
```

#### 실습
```mysql
create view v_memeber as
SELECT m.member_type , m.user_id , m.password , m.name
	, md.phone , md.marketing_yn , md.register_date
from member m
join member_detail md on md.member_type = m.member_type and md.user_id = m.user_id
;
```
![Pasted image 20231028093015.png](./imgs/Pasted%20image%2020231028093015.png)
```mysql
select * from v_memeber;
```
![Pasted image 20231028093133.png](./imgs/Pasted%20image%2020231028093133.png)

## 뷰 삭제

```mysql
drop view {TABLE NAME}
;
```

#### 실습

```mysql
drop view v_memeber;
```
