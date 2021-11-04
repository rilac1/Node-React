# Node-React
## package.json
#### npm package
- npm package 생성
  ```zsh
  npm init
  ```
#### 동작 명령어
`npm run [...]`의 동작방식을 지정해 줌.
```js
  "scripts": {
    "start": "node index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  }
```

#### 설치할 패키지 목록 (설치하면 "dependecies"에 항목 추가됨)
  - express js (node js의 프레임 워크)
    ```zsh
    npm install expree --save
    ```
  - Mongoose (몽고DB를 편하게 쓸 수 있는 Object Modeling Tool)
    ```zsh
    npm install mongoose --save
    ```

## index.js
백엔드 시작점
- 기본 코드 
  ```js
  const express = require('express')
  const app = express()
  const port = 3000

  app.get('/', (req,res) => res.send('Hello World!'))

  app.listen(port, () => console.log(`Example app listening on port ${port}!`))
  ```
- 몽고DB 연동
  ```js
  const mongoose = require('mongoose')
  mongoose.connect('mongodb://localhost:27017/boiler-plate', {
      useNewUrlParser:true,
      useUnifiedTopology: true, 
      useCreateIndex: true,
      useFindAndModifiy: false
      }
  ).then(
    () => console.log('MongoDB Connected...')
  ).catch(err => console.log(err))
  ```

## node_modules
  - npm 등으로 다운받은 모듈들을 관리하는 폴더
