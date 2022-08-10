# Realm, Basic, Bearer

##### [RFC 7235: Hypertext Transfer Protocol (HTTP/1.1): Authentication](https://www.rfc-editor.org/rfc/rfc7235)

##### [RFC 7616: HTTP Digest Access Authentication](https://www.rfc-editor.org/rfc/rfc7616)
  - old version [RFC 2069](https://www.w3.org/Protocols/rfc2069/rfc2069)

##### [About WWW-Authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/WWW-Authenticate)

##### [RFC 7617: The Basic HTTP Authentication Scheme](https://www.rfc-editor.org/rfc/rfc7617)

##### [RFC 6750: The OAuth 2.0 Authorization Framework: Bearer Token Usage](https://datatracker.ietf.org/doc/html/rfc6750)


<br><br><br><br><br><hr>

# What is RFC 7235

RFC 7235

<br><br><br><br><br><hr>

# RFC-7616 

(WWW-Authentication에 대한 Digest Scheme 표준을 명시한 문서)

## Digest Access Authentication Scheme

`challenge-response 패러다임`에 기반을 둡니다.

Challenge는 인증을 받으려는 기관(서버)이 인증 요청 대상(클라이언트)에게 보내는 것이고, nonce를 활용합니다.

Digest의 길이는 어떤 알고리즘을 사용하는가에 따라 달라집니다(SHA-256, MD-5(32바이트) 등. MD-5는 추천되지 않는다.)

만일, 서버가 보호된 자원에 접근 요청을 받았고, 이 때 어떠한 Authorization 헤더를 받지 못했다면,  서버는 `401 Unauthorized`라는 상태 코드와 함께 `WWW-Authentication` 헤더를 보냅니다.

인증 스킴(`<auth-scheme>`)은 아래와 같이 여러가지 존재합니다.

 - `Basic` (RFC 7617를 보십시오. base64-encoded credentials.),
 - `Bearer` (RFC 6750를 보십시오. bearer tokens to access OAuth 2.0-protected resources),
 - `Digest` (RFC 7616를 보십시오. Firefox에서는 md5 해싱만 지원합니다. SHA 암호화 지원을 위하여 bug 472823을 확인하십시오.),
 - `HOBA` (RFC 7486 (draft)를 보십시오. HTTP Origin-Bound Authentication, digital-signature-based),
 - `Mutual` (draft-ietf-httpauth-mutual를 참조하십시오),
 - `AWS4-HMAC-SHA256` (AWS docs를 참조하십시오).

### - Request From Server

`WWW-Authentication: <auth-scheme> <auth-param>` (인증 요구: Challenge)

 - realm: 보안 영역, 보호되는 영역을 설명하거나 보호의 범위를 알리는데 사용
 - domain: 공백(space)으로 구분되어있는 URI 리스트. protection space.
 - nonce: 매 요청마다 다른 String 값(Base64 || Hex).
    - Example: `Base64<timestamp H(timestamp ":" ETag ":" secret-data)>`
    - ETag HTTP 응답해더는 리소스를 식별하는 식별자. 웹 서버가 내용을 확인하고 변하지 않았으면, 웹 서버로 full 요청을 보내지 않기 때문에, 캐쉬가 더 효율적이게 되고, 대역폭도 아낄 수 있습니다. `"33a64df551425fcc55e4d42a148795d9f25f89d4"`
    - timestamp is a server-generated time
 - opaque: 서버에 의해 지정한 반환해야 하는 데이터 문자열. Base64나 Hex데이터 추천
    - 외부 라이브러리나 API에서 제공하는 함수 사용 시 활용되는 자료형들이 어떤 멤버로 구성되어 있는지 알 방법이 없어 Opaque Type이라고도 한다.
 - stale: nonce값이 오래되었을 때 응답.
 - algorithm
 - qop: `quality of protection`
    - `auth`: indicates authentication
    - `auth-int`: indicates authentication with integrity protection
 - charset: 오직 "UTF-8"만 허용됨
 - userhash: Default is `false`. does it support username hashing?

### - Response To Server

`Authorization: <type> <credentials>` (인증 확인: Response)

 - response
 - username
 - realm
 - uri
 - qop
 - cnonce
 - nc: nonce count
 - userhash

```
         response = <"> < KD ( H(A1), unq(nonce)
                                      ":" nc
                                      ":" unq(cnonce)
                                      ":" unq(qop)
                                      ":" H(A2)
                             ) <">
```

만일 algorithm 파라미터가 SHA-256이면

```
unq(username) ":" unq(realm) ":" passwd
```

<br><br><br><br><br><hr>

# Basic Scheme: RFC 7617

`WWW-Authentication: <auth-scheme:Basic> <auth-param:realm,charset>`

## In Challenges

```
HTTP/1.1 401 Unauthorized
Date: Mon, 04 Feb 2014 16:50:53 GMT
WWW-Authenticate: Basic realm="foo", charset="UTF-8"
```

## Response

 - Base64`<user-id:password>`

```
Authorization: Basic dGVzdDoxMjPCow==
```

<br><br><br><br><br><hr>

# Bearer Scheme: RFC 6750

