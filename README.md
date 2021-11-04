# Node-React

#### 용어 정리
- `package.json`
  - npm package
  - "scripts" 부분에서 `npm run [...]`의 동작방식을 지정해 줌
- `index.js`
  - 백엔드 시작점
  ```js
  const express = require('express')
  const app = express()
  const port = 3000

  app.get('/', (req,res) => res.send('Hello World!'))

  app.listen(port, () => console.log(`Example app listening on port ${port}!`))
  ```
- **express js**
  - node js의 프레임워크
  - 설치하면 package.json에 의존성 추가됨
- `node_modules`
  - 다운받은 dependencies들을 관리하는 폴더

#### npm package 생성
```zsh
npm init
```
#### express js 다운
```zsh
npm install expree --save
```

#### EL 표현
jsp에서의 EL 표현식은 리터럴이 따옴표(`'`,`"`)가 아닌 억음부호(**`**)를 사용해야한다.

#### Mongoose
몽고DB를 편하게 쓸 수 있는 Object Modeling Tool

다운로드
```sh
npm install mongoose --save
```