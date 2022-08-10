# JWT

## What is JWT
JWTs represent a set of claims as a JSON object that is encoded in a JWS and/or JWE structure.

Use URL-safe Base64

## 용어정리

- `JWT` ( JSON Web Token )
- `JWS` ( JSON Web Signature )
- JWE ( JSON Web Encryption )
- `JWA` ( JSON Web Algorithm )
- `JWK` ( JSON Web Key ) : JWK is a JSON data structure that contains information about hashing function's cryptographic key. It's a way to store your hashing key in JSON format.

```json
{
    "kty":"EC",
    "crv":"P-256",
    "x":"f83OJ3D2xF1Bg8vub9tLe1gHMzV76e8Tus9uPHvRVEU",
    "y":"x_FEzRu9m36HLN_tue659LNpXW6pCyStikYjKIWI5a0",
    "kid":"Public key used in JWS spec Appendix A.3 example"
}
```

- `JOSE` ( Javascript Object Signing and Encryption )

### - 구성
 - header + Payload + signature


### - Example (JWS)

 - JWT : `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c`



<br><br><br><br><br><hr>

## JWS 분석

JWS consists of 3 parts: the JOSE header, payload, and signature.

### - header

```json
{
    "typ":"JWT",
    "alg":"HS256" --> JWA
}
```

### - Payload - Claims

 - "iss" (Issuer) Claim
 - "sub" (Subject) Claim
 - "aud" (Audience) Claim
 - "exp" (Expiration Time) Claim
 - "nbf" (Not Before) Claim
 - "iat" (Issued At) Claim
 - "jti" (JWT ID) Claim

### - Signature

 - HMAC-SHA-256(Base64`header`"."Base64`payload`, pri_key as byte) = signature

 - Token 시 Server Side의 Private Key 활용

<br><br><br><br><br><hr>

## JWE 분석

unlike JWS, encrypts its content using an encryption algorithm. The only one that can see what is inside the JWT is the one with the key.

The structure of JWE compact serialization is as follows:

```
BASE64URL(UTF8(JWE Protected Header)) || ’.’ ||
BASE64URL(JWE Encrypted Key) || ’.’ ||
BASE64URL(JWE Initialization Vector) || ’.’ ||
BASE64URL(JWE Ciphertext) || ’.’ ||
BASE64URL(JWE Authentication Tag)
```

 - JWE: 

```
eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMTI4Q0JDLUhTMjU2In0.

RD09fEltrYPVNoGt2KY1Odv_5eDxkU4VX1f__P8b9zl9uzh5bmvvJy35dL-hYlUib1g63qnWBEfeSyDk5cAIQiMt6PZCBQzuWQJQlQtuo2UPLZznmLPqah37uHKB4a57q_lWf_W9soyZbO7Zj7QRNz4ZR4s5ozRHArSZcc1pAL-pYuHKyeh6Ey8t4bk66wkthjjfOjXvIfOlgbemhibegmE4GpQL6F-m0teqcAE-OxkaBRTmmb4AD5HdrCJWCIIuC52fzuWrhcoNmHM74ggtWUUjlHaKpwcVE-IWINTFaz5Pi9u4U3vnVNOZwDwB0TLSQvqnPwTZ-bYWNj8vH4TS_w.

Pjo5QK1u1otxgcuBR7e8ew.

_OElhHugS2L6Kp04HhbFt6dLij_KXhO654RmT4JKyswYBX0wqRWt7ZzAE6eCHfJSJdMQYxqVSNloGb4OSIzYcTEo174lBZBINkHW-w2K6E0.

QBDgBFizm80HLVkZvfBPCg
```