---
share: "true"
---

- 2개 이상의 테이블을 연결해 데이터를 출력하는 것
- PK나 FK 값의 연관에 의해 조인이 성립 (특별한 경우 논리적인 값들의 연관만으로 조인 가능)
- 여러 개의 테이블을 조인할 때 먼저 특정 2개의 테이블을 조인하고 그 결과와 나머지 테이블과 조인 (조인 순서는 내부적으로 DBMS 옵티마이저가 결정)

![Pasted image 20231027003835.png](./imgs/Pasted%20image%2020231027003835.png)

>[!NOTE]
>INNER JOIN을 일반적으로 JOIN이라고 함

## 실습

#### 1. 테이블 생성

```mysql
create table member
(
member_type varchar(10) not null comment '회원구분',
user_id varchar(50) not null comment '회원 아이디',
password varchar(50) null comment '비밀번호',
name varchar(20) null comment '이름',
primary key (member_type, user_id)
) comment '회원정보';

create table member_detail
(
member_type varchar(10) not null comment '회원구분',
user_id varchar(50) not null comment '회원 아이디',
phone varchar(12) null comment '휴대폰 번호',
marketing_yn bit null comment '마케팅 수신 여부',
register_date datetime default current_timestamp() null comment '가입일',
primary key (member_type, user_id),
constraint fk_member_detail foreign key (member_type, user_id) references member (member_type, user_id)
) comment '회원상세정보';
```

#### 2. 데이터 추가

```mysql
insert into member(member_type, user_id, password, name) values
("email", "kwon@gmail.com", "7777", "원균"),
("email", "syn@gmail.com", "1234", "이순"),
("email", "test@naver.com", "4312", "박규"),
("kakao", "lyu@gmail.com", null, "류성룡"),
("kakao", "sunsyn@gmail.com", null, "이순신")
;

insert into member_detail(member_type, user_id, phone, marketing_yn, register_date) values
("email", "kwon@gmail.com", "01011111111", true, now()),
("email", "syn@gmail.com", "01022222222", true, now()),
("email", "test@naver.com", "01033333333", false, now())
;
```

#### 3. JOIN

```mysql
SELECT *
from member
	join member_detail
		on member.member_type = member_detail.member_type and member.user_id = member_detail.user_id
;
```
![Pasted image 20231026113659.png](./imgs/Pasted%20image%2020231026113659.png)

- alias 적용

```mysql
SELECT *
from member as m
	join member_detail as md
		on m.member_type = md.member_type and m.user_id = md.user_id
;
```

>[!NOTE]
>`as`  생략 가능

#### 4. LEFT JOIN

```mysql
SELECT *
from member as m
	left join member_detail as md
		on m.member_type = md.member_type and m.user_id = md.user_id
;
```
![Pasted image 20231026114215.png](./imgs/Pasted%20image%2020231026114215.png)
>[!NOTE]
>`LEFT JOIN`은 왼쪽에 위치한 테이블의 모든 내용을 출력하고 `RIGHT JOIN`은 오른쪽에 위치한 테이블의 모든 내용을 출력한다.

#### 5. FULL JOIN

```mysql
SELECT *
from member as m
	join member_detail as md
;
```
![Pasted image 20231026114337.png](./imgs/Pasted%20image%2020231026114337.png)
