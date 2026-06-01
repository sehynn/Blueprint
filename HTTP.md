# HTTP Status Code

## 상태 코드란?

HTTP 상태 코드는 클라이언트가 보낸 요청(Request)에 대해 서버가 처리 결과를 알려주는 3자리 숫자 코드이다.

클라이언트는 상태 코드를 통해 요청이 성공했는지, 인증에 실패했는지, 잘못된 요청인지, 서버에 문제가 발생했는지 등을 확인할 수 있다.

예시:

```http
GET /users/1
```

```http
HTTP/1.1 200 OK
```

위 응답은 서버가 요청을 정상적으로 처리했음을 의미한다.

---

## 상태 코드 분류

| 범위 | 의미 |
|--------|--------|
| 1xx | 정보 응답 |
| 2xx | 성공 |
| 3xx | 리다이렉트 |
| 4xx | 클라이언트 오류 |
| 5xx | 서버 오류 |

---

# 2xx Success

## 200 OK

조회 성공

```http
GET /users/1
→ 200 OK
```

## 201 Created

생성 성공

```http
POST /users
→ 201 Created
```

## 204 No Content

성공했지만 응답 Body 없음

```http
DELETE /users/1
→ 204 No Content
```

---

# 3xx Redirection

## 301 Moved Permanently

영구 이동

- URL이 영구적으로 변경됨

## 302 Found

임시 이동

- URL이 일시적으로 변경됨

---

# 4xx Client Error

## 400 Bad Request

잘못된 요청

```text
필수 파라미터 누락
잘못된 요청 형식
```

---

## 401 Unauthorized

인증 실패

```text
JWT 없음
JWT 만료
```

### 핵심

인증(Authentication) 문제

---

## 403 Forbidden

권한 없음

```text
일반 사용자가 관리자 API 호출
```

### 핵심

인증은 되었지만 권한(Authorization)이 없음

---

## 404 Not Found

리소스를 찾을 수 없음

```text
존재하지 않는 회원
존재하지 않는 API
```

---

## 409 Conflict

현재 상태와 충돌

```text
중복 이메일 가입
이미 처리된 주문
```

---

## 422 Unprocessable Entity

요청 형식은 맞지만 비즈니스 검증 실패

```text
비밀번호 길이 부족
이메일 형식 오류
```

### 400 vs 422

```text
400
요청 자체가 잘못됨

422
요청 형식은 맞음
비즈니스 규칙 위반
```

---

## 429 Too Many Requests

요청 과다

```text
Rate Limit 초과
```

---

# 5xx Server Error

## 500 Internal Server Error

서버 내부 오류

```text
예상하지 못한 예외
DB 오류
```

---

## 502 Bad Gateway

서버 간 통신 실패

```text
Nginx → API 서버 오류
```

---

## 503 Service Unavailable

일시적으로 서비스 불가

```text
서버 점검
서버 과부하
```

---

## 504 Gateway Timeout

서버 간 통신 시간 초과

```text
외부 API 응답 지연
```

---

# 면접 단골 질문

## 401 vs 403

401

- 인증 실패
- 로그인 필요

403

- 인증 성공
- 권한 없음

---

## 400 vs 422

400

- 요청 자체가 잘못됨

422

- 요청 형식은 맞음
- 비즈니스 검증 실패

---

## 500 vs 503

500

- 서버 코드 문제

503

- 서버는 정상
- 점검 또는 과부하

---

# 이것만 외우면 됨

- 200 OK
- 201 Created
- 204 No Content

- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 409 Conflict
- 422 Unprocessable Entity
- 429 Too Many Requests

- 500 Internal Server Error
- 502 Bad Gateway
- 503 Service Unavailable
- 504 Gateway Timeout
