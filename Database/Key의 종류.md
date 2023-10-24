---
share: "true"
---

![Pasted image 20231024113029.png](./imgs/Pasted%20image%2020231024113029.png)
### super key

- relation에서 tuples를 unique하게 식별할 수 있는 attrubutes set
- 예를 들어 User(id, name, email, phone)의 super key는 {id, name, email, phone}, {id, name}, {name, email} 등이 된다. {name}과 같은 경우에는 동명이인과 같은 상황이 발생할 수 있기때문에 superkey가 될 수 없다.

### candidate key

- 어느 한 attrubute라도 제거하면 unique하게 tuples를 식별할 수 없는 super key
- super key 중 가장 최소한의 attribute를 가지는 key
- 예를 들어 위 super key 예시에서 {id, name, email, phone}는 email과 phone이 없어도 unique하게 tuple을 식별할 수 있으므로 candidate key가 될 수 없다.

### primary key

- relation에서 tuples를 unique하게 식별하기 위해 선택된 candidate key
- candidate key 중 대표할 수 있는 키
- 예를 들어 User(id, name, email, phone)에서 {id}를 primary key로 사용하는 것을 선택했다면 {id}가 primary key가 된다. 보통 attribute 수가 적은 key를 primary key로 사용된다.

### unique key

- primary key로 선택되지 않은 candidate key
- alternate key라고도 부름
- 예를 들어 User(id, name, email, phone)에서 {id}를 primary key로 선택했을때 {name, email} 과 같은 key가 unique key가 될 수 있다.

### foreign key

- 다른 relation의 PK를 참조하는 attributes set
- 예를 들어 User(id, name, email, phone)와 Order(id, user_id, price) 이 있다면 foreign key는 Order의 {user_id} 가 된다. 즉, User relation의 PK인 id를 참조한 attribute인 user_id가 foreign key이다.