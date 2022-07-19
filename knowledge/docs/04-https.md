# HTTPS

Hypertext Transfer Protocol Secure

## 프로세스

 - 이해관계자: `서버`, `클라이언트`, `CA`

 1. `서버`: 비대칭키 생성
 2. `서버` -> `CA`: `서버`(**Public Key**, 관련 정보)
 3. `CA`: `서버`(**Public Key**, 관련 정보) -> **SSL 인증서** -> 암호화`CA`<**Private Key**>(**SSL 인증서**) -> 공개(WEB)
 4. `CA` -> `서버`: Encrypted<**SSL인증서**>CA
 5. `클라이언트`: 접속할 서버의 `CA` 리스트 검색(브라우저 및 모바일에 내장)
 6. `클라이언트` -> `CA`: Encrypted<**SSL 인증서**>CA 검증(By `CA`<**Public Key**>)
 7. `클라이언트` -> `서버`: Hello(Session ID, Ciper Suite List, SSL Version)
 8. `서버` -> `클라이언트`: Hello(Selected Cipter Suite, Encrypted<**SSL 인증서**>CA)
 9. `클라이언트` -> `서버`: 암호화 `서버`<**Public Key**>(Secret Key)
 10. `서버`: Get Secret Key
 11. Finish SSL Handshake