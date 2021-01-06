# Node-Express
https://www.youtube.com/watch?v=pKd0Rpw7O48&ab_channel=ProgrammingwithMosh

## 시작하며
요새 마음도 좀 싱숭생숭하고 해서 좀 재밌는것들, 마음에 부담없이 해보려고 Express 궁금해서 보려고 한다!!!

마음 답답할땐 역시 그냥 튜토리얼 따라하는거지. 

- [express docs](https://expressjs.com/)

## express 사용이유(inside expressTutorial)
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

## 후기
생각보다 뭔가 대단한 무언가는 없는거같아서 더 심화로 어떻게 쓰는지 한번 보려고 한다! 나의 경우엔 간단하게 API 만들어 쓸 정도면 되서(당분간은...! 서버개발자가 될줄알았는데, 어쩌다보니 Frontend 에 한동안 집중할거니까...!) 좀 더 다른것들을 한번 살펴보면서 정신적 휴식을 취해볼려고 한다!

## [MERN stack](https://www.youtube.com/watch?v=7CqJlxBYj-M&ab_channel=freeCodeCamp.org)
음 오랜만에 좀 재밌는거 하고싶어서 그냥 생각없이 따라할 수 있을 튜토리얼 한번 해보려고 한다! 한동안 진짜 딥한 내용만 주구장창 보다보니까 살짝 부담스러웟..

가끔은 생각없이 따라하기도해야지.. 안그러면 너무 정이없다. 

- topic: exercise tracker app
  - Application will contain
    - exercies
    - users
  - Every exercise has one user
- MERN stack: MongoDB(noSQL-not only sql), Express, React, Node.js, Mongoose

- MongoDB 용어 정리
    <img src="assets/1.png" width=400>

    - MongoDB saves data as BSON types(Binary JSON)
    - [MongoDB 설치가이드-docker](https://mytutorials.tistory.com/205)
    - [mongo db 란?](https://velopert.com/436)
    - objectId is generated by mongodb driver


- React app: mern-exercise-tracker
    - 다소 귀찮은 감이 있어... 언젠가 하겠지 하는 마음으로 떠나겠다. 

- backend:
  - to simpify things, make `backend` folder inside `mern-exercies-tracker`
  - inside `backend` folder: `npm install express cors mongoose dotenv`
  - `npm install -g nodemon`
  - make `server.js`
  - mongoose 설정
    - `.env`:(도커로 mongodb를 올린 경우) MONGO_URI='mongodb://root:mongodb@localhost:27017'
    - 설정 예시
    ```javascript
    const uri = process.env.MONGO_URI;
    mongoose.connect(uri, { useNewUrlParser: true, useCreateIndex: true});

    const connection = mongoose.connection;
    connection.once('open', () => {
        console.log("MongoDB database connection established successfully");
    })
    ```

## MERN stack 후기
재미있었던 것 같다. 오래만에 도커 설정 관련해서 이슈도 만나보고 재밌네. Django로 개발할때랑은 다르게 확실히 nodejs는 rest api를 개발하는 것에만 집중할 수 있을 것 같아, 간단한 토이 프로젝트를 할때 부담없이 다룰 수 있을 것 같다!(보안 이슈 등에 대한것은 차차 공부해야하는 것이겠지만...!)

mongodb는 처음 다뤄보는데, 여기서는 간단한것만 다루긴했지만, 뭔가 신기하긴하다. 아직 낯선 개념이긴한데, 간단히 블로그 글만 찾아봐도 join이 없이 하도록 해라고 하는게 신기한것 같다. 유튜브 영상에서도 그냥 진짜 join이런거 없이 뭔가 처리한다. 다음에 좀더 심도있게 다뤄봐야겠지만, 간단하게 mongoose라는 라이브러리고 mongodb를 node환경에서 쉽게 다룰 수 있다는 것을 배워서 좋은 것 같다. 

next js에서도 mongoose로 데이터를 보여주면 좋겠단 생각을 했는데, [역시나 그렇다](https://stackoverflow.com/questions/60660488/is-it-possible-to-run-mongoose-inside-next-js-api) 

## Express 공부 마무리!
재밌었다~ 

