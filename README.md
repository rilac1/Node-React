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

## models
#### User.js
```js
const mongoose = require('mongoose');

// 스키마 생성
const userSchema = mongoose.Schema({
  email: {
    type: String,
    maxlength: 50,
    trim: true,   // trim: Space를 없애줌
    unique: 1     // 중복 허용X
  },
  role: {
    type: Number,
    default: 0
  },
  image: String
})

// 스키마 모델로 감싸기
const User = mongoose.model('User', userSchema)

// 해당 모델을 다른곳에 쓸 수 있게 export 해줌
module.exports = {}
```

## node_modules
  - npm 등으로 다운받은 모듈들을 관리하는 폴더

