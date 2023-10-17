---
share: "true"
---

## Install

```bash
brew install mariadb
cd /usr/local/Cellar/mariadb/{설치한 버전}/bin
sudo ./mariadb-secure-installation
```

- 설치 과정

```
...
Enter current password for root (enter for none): {root password 입력}
...
Switch to unix_socket authentication [Y/n] n
...
Change the root password? [Y/n] Y
...
Remove anonymous users? [Y/n] Y
...
disallow root login remotely? [Y/n] n
...
Remove test database and access to it? [Y/n] n
...
Reload privilege tables now? [Y/n] Y
```

## 접속

```bash
mysql -u root -p
```

- u: user name 지정
- -p: password를 통해 접속

## 명령어 간단하게 살펴보기

#### 1. 버전확인

```mysql
select version();
```

#### 2. 데이터베이스 확인

```mysql
show databases;
```

#### 3. 데이터베이스 선택

```mysql
use {database name}
```

#### 4. 현재 데이터베이스의 테이블 확인

```mysql
show tables;
```

## 원격 접속 설정

#### 1. 외부 IP 접속 설정

```bash
find / -name my.cnf
sudo vi my.cnf
```

아래의 내용을 추가

```
[mysqld]
bind-address: 0.0.0.0
```

#### 2. 접속 계정 설정

- 접속

```bash
mysql -u root -p
```

- DB 선택 후 계정 확인
	- Host가 모두 localhost로 지정되어있는 것을 확인

```mysql
use mysql;
select Host, User, Password from user;
```

- 계정 추가
	- Host를 '%'로 지정하여 외부 Host에서 접속 가능하도록 설정

```mysql
create user 'root'@'%' identified by '{username}';
grant all privileges on root.* to 'root'@'%' identified by '{username}';
flush privileges;
```
