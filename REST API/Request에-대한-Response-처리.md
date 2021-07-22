> 2021년 7월 22일 - Request에 대한 Response 처리

# REST API

## 성공/실패 여부 정의

- REST API request에 대한 response를 보낼 때, 성공/실패를 판단하는 여부는 status code를 사용할 것

### 나쁜 예

- Request

  - /api/article&id=3

- Response

  - Success

  ```json
  code: 200
  
  body:
  {
  	"result": true,
  	"data": {
  		"title": "sample",
  		"content": "Hello World"
  	}
  }
  ```

  - Failed

  ```json
  code: 200
  
  body:
  {
  	"result": false,
  	"msg": "no Authentication"
  }
  ```

### 좋은 예

- Request

  - /api/article&id=3

- Response

  - Success

  ```json
  code : 200
  
  body :
  {
  	"title": "sample",
  	"content": "Hello World"
  }
  ```

  - Failed

  ```json
  code : 401
  
  body :
  {
  	"msg": "no Authentication"
  }
  ```

- 이미 정의된 기능들을 활용하는 방향으로 설계

  - 이미 정의 되어있는 코드 활용
  - 성공/실패 케이스를 나눠서~

  - [HTTP 상태 코드 - 위키백과, 우리 모두의 백과사전](https://ko.wikipedia.org/wiki/HTTP_상태_코드)

## 데이터가 없는 경우 처리

- data가 없을 때 (empty일 때) response 처리
- empty일 경우 json을 `[]` 또는 `{}` 형태로 처리한다.
  - empty는 error가 아님

### 나쁜 예

- Request
  - /api/comment&articleID=3
- Response

```json
code: 404

body:
{
	"msg": "no comments"
}
```

### 좋은 예

- Request
  - /api/comment&articleID=3
- Response

```json
code: 200

body:
[]
```

