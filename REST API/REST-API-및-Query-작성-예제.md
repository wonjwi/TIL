> 2021년 7월 23일 - REST API 및 Query 작성 예제

## REST API 및 Query 작성 예제

- 포인트 추가 및 내역 조회에 대한 예제 [📄](files/rest_api_point.xlsx)

- 저장된 Database

  <img src="images/image-20210724193011885.png" alt="image-20210724193011885" style="zoom: 50%;" /> 

| Explanation                                | Method | Request                                                      | Response                                                     | Query                                                        |
| :----------------------------------------- | :----- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 모든 point 기록 조회                       | Get    | api/point                                                    | <img src="images/image-20210724184633794.png" alt="image-20210724184633794" style="zoom:;" /> | `select * from point`                                        |
| 특정 point 기록 조회                       | Get    | api/point?id=3                                               | <img src="images/image-20210724184705026.png" alt="image-20210724184705026"  /> | `select * from point where id=3`                             |
| 특정 사용자의 point 기록 조회              | Get    | api/point?user_id=34                                         | <img src="images/image-20210724184800431.png" alt="image-20210724184800431"  /> | `select * from point where user_id=34`                       |
| 특정 사용자의 point 지출 기록 조회         | Get    | api/point?user_id=34&lt-point=0<br /><br />api/point?user_id=34&point={'lt' :0} | <img src="images/image-20210724184806961.png" alt="image-20210724184806961"  /> | `select * from point where user_id=34 and point < 0`         |
| 특정 사용자의 30 point 이내 지출 기록 조회 | Get    | api/point?user_id=34&lt-point=0&gt-point=-30<br /><br />api/point?user_id=34&point={'lt' :0, 'gt':-30} | <img src="images/image-20210724184813168.png" alt="image-20210724184813168"  /> | `select * from point where user_id=3 and point < 0 and point > -30` |
| 특정 사용자에게 point 추가                 | Post   | api/point<br />{<br />&nbsp;&nbsp;user_id:3,<br />&nbsp;&nbsp;point:10<br />} | <img src="images/image-20210724184818135.png" alt="image-20210724184818135"  /> | `insert into point(user_id, point) values(3, 10)`            |
| 월별 point 조회                            | Get    | api/point/monthly                                            | ![image-20210724191136773](images/image-20210724191136773.png) | `select user_id, sum(point) as month_point, year(created_at), month(created_at) from point group by user_id, year(created_at), month(created_at)` |
| 특정 사용자의 월별 point 조회              | Get    | api/point/monthly?user_id=34                                 | ![image-20210724191147557](images/image-20210724191147557.png) | `select user_id, sum(point) as month_point, year(created_at), month(created_at) from point group by user_id, year(created_at), month(created_at) where user_id=34` |
| 특정 사용자의 잔여 point 조회              | Get    | api/point/balance?user_id=34                                 | ![image-20210724191157564](images/image-20210724191157564.png) | `select user_id, sum(point) as balance from point group by user_id where user_id=34` |

- 사용한 포인트를 음수로 표시하기 때문에 0보다 작다는 조건을 이용해서 지출 기록 조회 가능