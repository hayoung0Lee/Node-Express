# Node-Express
https://www.youtube.com/watch?v=pKd0Rpw7O48&ab_channel=ProgrammingwithMosh

## 시작하며
요새 마음도 좀 싱숭생숭하고 해서 좀 재밌는것들, 마음에 부담없이 해보려고 Express 궁금해서 보려고 한다!!!

마음 답답할땐 역시 그냥 튜토리얼 따라하는거지. 

- [express docs](https://expressjs.com/)

## express 사용이유
```javascript
const http = require('http');
const server = http.createServer((req, res) => {
    if(req.url === "url1"){
        res.write("url1");
        res.end();
    }
    if(req.url === "url2"){
        res.write("url2");
        res.end();
    }
    //// 더 많이 나열

    if(req.url === "url(n)"){
        res.write("url(n)");
        res.end();
    }
});

server.listen(3000);

console.log("listening on port 3000....");

```

위의 방법으로도 되긴 되지만, 좀 그렇지 않은가.

express를 통해서 더 구조적으로 편하게 할 수 있다고 한다. 

```javascript
const express = require('express');
const app = express();

// app.get()
// app.post()
// app.put()
// app.delete()

app.get('/', (req, res) => {
    res.send("Hello World!");
})

app.listen(3000, () => console.log("Listening on port 3000"));
```

if를 안써도 된다. 그래서 파일을 나누기가 좋다(구조를 잡기 좋단 말)

## nodemone 이란걸 써봤다
- [nodemone 이란?](https://brunch.co.kr/@topherlee/30#:~:text=Nodemon%EC%9D%80%20Node.js%EC%97%90,%EC%8B%A4%ED%96%89%EB%90%98%EA%B2%8C%20%ED%95%A0%20%EC%88%98%20%EC%9E%88%EB%8B%A4.)
- 설치: `npm install -g nodemon`

신기하구먼


## 환경변수
- `export PORT=5000`
- make `.env`
  
```
NODE_ENV='development'
PORT=5000
```

- index.js
  
```javascript
// PORT
if (process.env.NODE_ENV !== 'production') {
    require('dotenv').config();
}
const port = process.env.PORT|| 3000
app.listen(port , () => console.log(`Listening on port ${port}`));
```
 