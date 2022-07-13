# HTTPS

Hypertext Transfer Protocol Secure

## 프로세스

 - 이해관계자: `서버`, `클라이언트`, `CA`

 1. `서버`: 비대칭키 생성
 2. `서버` -> `CA`: `서버`(**Public Key**, 관련 정보)
 3. `CA`: `서버`(**Public Key**, 관련 정보) -> **SSL 인증서** -> 암호화`CA`<**Private Key**>(**SSL 인증서**)