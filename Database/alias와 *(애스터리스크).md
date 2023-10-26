---
share: "true"
---

## alias

- 별명을 뜻하면 말그대로 부르기 쉽게 하기위함
- 테이블에 대한 별명은 테이블명 바로 뒤에 위치
- 칼럼에 대한 별명은 칼럼 바로 뒤에 위치
- AS 키워드를 이용해서 사용

```mysql
SELECT m.name AS "이름"
	, m.email AS "이메일"
	, m.password AS "비밀번호"
FROM test_member AS m
;
```
![Pasted image 20231026110135.png](./imgs/Pasted%20image%2020231026110135.png)
## * (애스터리스크)

- 모든 칼럼을 의미
- 연산에 사용될때는 곱하기를 의미

```mysql
SELECT * FROM test_member;
```
![Pasted image 20231026110212.png](./imgs/Pasted%20image%2020231026110212.png)

