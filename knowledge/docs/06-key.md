# 암호키 관리 포맷

인증서나 개인키를 인코딩하는 방식은 `PEM`과 `DER`방식이 있음
 - `PEM`: header + base64 encoding + foot
 - `DER`: `asn.1`로 확인 가능한 Binary

## `PKCS#1`

RSA 개인키를 PEM 형태로 인코딩한 상태( 비밀번호로 암호화 되지 않은 상태 )

```pem
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQDBZaDenaPpRrP3LIfnYpFLJPA7zsSD5aYdp7dkaymRvJo5SW+h
srvfpz67mwE5oIkUA8sXWAGdZAmY32tYffVFfl+vo9dPi9Zw9USQOGIl4Lty39WM
...............중략................
0+5kshrC0BmPqNzTqbUCQCBEWR5AMTxJSdQHhd2TV/+nvTR3HhN42KTNszk5pH+t
qi3iuxVVz3Qz339C8SmHW7sxw6wyjMaCuS8Uu3B+jQU=
-----END RSA PRIVATE KEY-----
```

## `PKCS#8`

RSA 개인키를 PKCS#8 저장 포맷(PEM)에 따라 비밀번호로 암호화된 상태

```pem
-----BEGIN ENCRYPTED PRIVATE KEY-----
MIICoTAbBgkqhkiG9w0BBQMwDgQI4tuYpxEXhUYCAggABIICgJIcNl+c77/iXF42
Hslk71keSSas51tSoSHB3acowpjMAWOLwAtHmNS9mnpozvLc6F+47USVuYRChw0+
...............중략................
2nyrrN6DpI44Ar+SHhn5MtRWSnz1QuEcw1+0PtVjxrFaTt2YCrJLSnpgunGR0Z6U
w+n6pPk=
-----END ENCRYPTED PRIVATE KEY-----
```