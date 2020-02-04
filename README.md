# JWT Parser

## Installation

```bash
npm install @samox/jwt-parse
```

or

```bash
yarn add @samox/jwt-parse
```

**IMPORTANT**: This library doesn't validate the token, any well formed JWT can be decoded. You should validate the token in your server-side logic by using something like express-jwt, koa-jwt, Owin Bearer JWT, etc.

## Usage

```ts
import { parseJWT } from "@samox/jwt-parse";

const JWT =
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c";

type JWTPayload = { sub: string; name: string; iat: number };
type JWTHeader = { alg: string; typ: string };

const { payload, header } = parseJWT<JWTPayload, JWTHeader>(JWT);

console.log("Payload :", payload.name);
console.log("Header :", header);
```
