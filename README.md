# xss-note

# 보안

# Authentication

Improved&Advanced

![Untitled](./%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202022-06-06%20%EC%98%A4%ED%9B%84%2012.59.32.png)

XSS Attack

Cross-Site Scripting Attack

사용자가 모르게 스크립트를 심어놓고 중요한 정보를 가져가는 방식

OWASP

[https://owasp.org/](https://owasp.org/)

방법 1 

memory

- 페이지 전환시 로그아웃이 됨

방법2 

Cookies/Http Only

- 웹클라이언트라 모바일을 못사용
- Scsceptible to CSRF attack

https://bughunters.google.com/learn


1. 사용자가 받아오는 스크립트에 따로 입력을 못하도록 막아준다
2. HTTP Only - 적용

Node cooki 

npm i cookie-parser

app.use(cookiePaser)

const corsOption → credentials : true // allow the Access-Control-Allow-Credentials

// cooke header → 브라우저에만 사용되는 것 

signup, login

```jsx
setToken(res,token)
function setToken(res,token){
	const option = {
		maxAge:config.jwt.exppiresInSec * 1000,
		httpOnly:true,
		sameSite:'none'
		secure:true,

	}
	res.cooke('token',token,)//HTTP-ONLY
}
```

middleware

```jsx
// 1. Cooke(for Browser)
// 2. header(for Non-Browder Client)

let token;
//check ther header first
const authHeader = req.get('Ahthorization');
if(authHeader && authHeader.startsWith('Bearer')){
	token = ahthHeader.split(' ')[1];
}
// if no token in the header, check the cookie
if(!token){
	token = req.cookies['token'];
}
if(!token){
return res.status(401).json(AUTH_ERROR);
```


ver 1
var 2