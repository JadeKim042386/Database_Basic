---
share: "true"
---

- 단일행 함수: 함수의 입력값이 단일행 값이 입력
	- 문자형 함수: 문자를 입력하면 문자나 숫자 값을 반환
	- 숫자형 함수: 숫자를 입력하면 숫자 값을 반환
	- 날짜형 함수: DATE 타입의 값을 연산
	- 변환형 함수: 문자, 숫자, 날짜형 값의 데이터 타입을 변환
	- NULL 관련 함수: NULL을 처리하기 위한 함수
- 다중행 함수: 함수의 입력값이 여러행 값이 입력 (집계 함수, 그룹 함수 등)

### 특정 문자열 길이까지 추출

```mysql
select member_type, user_id, password, name,
	substring(password, 1, 2)
from member;
```
![Pasted image 20231027100247.png](./imgs/Pasted%20image%2020231027100247.png)

### 2개 이상의 문자열 결합

```mysql
select member_type, user_id, password, name,
	concat(substring(password, 1, 2), '**') as password_concat
from member;
```
![Pasted image 20231027100508.png](./imgs/Pasted%20image%2020231027100508.png)

>[!NOTE]
>Oracle에서는 문자열 결합을 `||`을 사용하여 할 수 있지만 `concat()`함수도 제공

### 문자열 길이

```mysql
select member_type, user_id, password, name
	,concat(substring(password, 1, 2), '**') as password_concat
	,length(password) as password_length
from member;
```
![Pasted image 20231027100650.png](./imgs/Pasted%20image%2020231027100650.png)

### 여러 조건에 따른 값 반환

```mysql
select member_type, user_id, password, name
,
CASE
	when length(password) > 2 then concat(substring(password, 1, 2), '**')
	else ''
END as password_concat
from member;
```
![Pasted image 20231027100938.png](./imgs/Pasted%20image%2020231027100938.png)

>[!NOTE]
>```mysql
>CASE
>	WHEN 조건1 THEN 결과1
>	WHEN 조건2 THEN 결과2
>	WHEN 조건3 THEN 결과3
>	ELSE 결과
>END
>```


그 외의 함수들은 공식 문서에서 찾아 사용할 수 있다.
https://dev.mysql.com/doc/refman/8.0/en/functions.html


