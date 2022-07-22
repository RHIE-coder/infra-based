# HTTP 상태 코드

 - 1xx (정보): 요청을 받았으며 프로세스를 계속 처리중
 - 2xx (성공): 요청을 성공적으로 처리
 - 3xx (리다이렉션): 요청 완료를 위해 웹브라우저에 추가 작업 조치가 필요
 - 4xx (클라이언트 오류): 요청 문법이 잘못되었거나 요청을 처리할 수 없음
 - 5xx (서버 오류): 서버가 정상 요청을 처리하지 못함

## 1xx
### - 100 Continue
### - 101 Swiching Protocol
### - 102 Processing

<br><br><br>

## 2xx
### - 200 OK 
요청 성공

### - 201 Created
요청 성공해서 새로운 리소스가 생성됨, 주로 POST 요청, 일부 PUT 요청 이후에 따라옴

### - 202 Accepted
요청을 수신했지만 아직 처리가 완료안됨
ex) 1시간 뒤 Batch 프로세스

### - 204 No Content
요청 성공 But, 응답 Payload에 보낼 데이터가 없음


<br><br><br>

## 3xx

브라우저는 3xx 응답 결과에 Location 헤더가 있으면 Location 위치로 자동 이동

### - 301 Moved Permanently + 308 Permanent Redirect
특정 리소스의 URI가 영구적으로 이동


### - 302 Found + 303 See Other + 307 Temporary Redirect
일시적인 변경

### - 304 Not Modified
결과 대신 캐시를 사용


<br><br><br>

## 4xx
API 스팩에 맞지않게 요청한 경우임

### - 400 Bad Request
잘못된 문법이나 메시지를 요청해서 서버가 이해할 수 없음.

### - 401 Unauthorized
클라이언트가 리소스에 대한 인증이 필요함(로그인)

### - 403 Forbidden
서버가 요청을 이해했지만 승인을 거부함
인증은 되었지만(로그인) 접근 권한이 불충분(인가)

### - 404 Not Found
요청 리소스를 찾을 수 없음

<br><br><br>

## 5xx

### - 500 Internal Server Error
서버 내부 문제로 오류 발생

### - 502 Bad Gateway
서버간의 유요하지 않은 응답을 받은 경우

### - 503 Service Unavailable
서버가 일시적을 요청을 처리할 준비가 되지 않음.
유지보스를 위한 작동이 중단되거나 과부하가 걸림
