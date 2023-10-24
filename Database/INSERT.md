---
share: "true"
---

```mysql
INSERT INTO {TABLE NAME}(COLUMN1, COLUMN2, ...) VALUES (VALUE1, VALUE2, ...);
```

### 1. 현재 테이블 확인

```
select * from test_member;
```
![Pasted image 20231024110336.png](./imgs/Pasted%20image%2020231024110336.png)

### 2. 데이터 추가

```
insert into test_member
(name, email, phone, password, marketing_yn, register_date)
values
('joo', 'joo@gmail.com', '01000000000', '1234', true, now())
;
```
![Pasted image 20231024110611.png](./imgs/Pasted%20image%2020231024110611.png)

### 3. 중복 데이터 추가

- 한 번 더 같은 데이터를 추가하면 다음과 같이 중복되어 추가된다.

![Pasted image 20231024112110.png](./imgs/Pasted%20image%2020231024112110.png)

### 4. 중복 데이터 처리

- 우선 `drop table` 또는 중복된 데이터를 삭제

![Pasted image 20231024112246.png](./imgs/Pasted%20image%2020231024112246.png)
![Pasted image 20231024112330.png](./imgs/Pasted%20image%2020231024112330.png)

- `primary key` 지정

```
alter table test_member
add constraint primary key pk_test_memeber(email);
```
![Pasted image 20231024112652.png](./imgs/Pasted%20image%2020231024112652.png)

>[!NOTE]
>일반적으로 id를 `primary key`로 지정하고 email과 같이 중복을 허용하지 않는 attribute는 `unique key`로 지정한다.

