> 2021년 7월 19일 - REST API와 HTTP Method

## REST API와 HTTP Method

### HTTP Method 구분

- Method를 구분해서 사용할 것
- URL에 Method에 해당하는 값이 들어가면 안 됨

#### 나쁜 설계 ❌

- URL에 insert, delete, update와 같은 Method에 해당하는 값이 포함

| Method | URL                      | Query                               |
| ------ | ------------------------ | ----------------------------------- |
| GET    | /api/article?id=3        | select * from article where id = 3  |
| POST   | /api/article/insert      | insert ... into article             |
| PUT    | /api/article/update?id=3 | update article set ... where id = 3 |
| DELETE | /api/article/delete?id=3 | delete from article where id = 3    |

#### 좋은 설계 👌

- URL은 동일하지만 Method를 구분해서 사용

| Method | URL               | Query                               |
| ------ | ----------------- | ----------------------------------- |
| GET    | /api/article?id=3 | select * from article where id = 3  |
| POST   | /api/article      | insert ... into article             |
| PUT    | /api/article?id=3 | update article set ... where id = 3 |
| DELETE | /api/article?id=3 | delete from article where id = 3    |

### Parameter

- REST API에서 Parameter는 조건 (쿼리문의 where 절) 에 해당

| Method | URL                                   | Query                                                        |
| ------ | ------------------------------------- | ------------------------------------------------------------ |
| GET    | /api/article?userID=5                 | select * from article inner join user<br />on ... where user.id = 5 |
| GET    | /api/article?userID=5&start=156060... | select * from article inner join user<br />on ... where user.id = 5 and<br />article.created > 156060... |

- 모든 값을 가져오는 REST API URL은 where 절이 없어야 하므로, Parameter 또한 없음

| Method | URL                         | Query                                        |
| ------ | --------------------------- | -------------------------------------------- |
| GET    | ~~/api/article/all~~        | select * from article inner join user on ... |
| GET    | ~~/api/article?userID=-1~~  | select * from article inner join user on ... |
| GET    | ~~/api/article?userID=all~~ | select * from article inner join user on ... |
| GET    | /api/article                | select * from article inner join user on ... |
