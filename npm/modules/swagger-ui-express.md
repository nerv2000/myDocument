# swagger-ui-express

swagger-ui 생성 API

|구분|url|
|---|---|
| npm | <https://www.npmjs.com/package/swagger-ui-express> |
| homepage | <https://github.com/scottie1984/swagger-ui-express> |
| Repository | <https://github.com/scottie1984/swagger-ui-express> |

## typescript 지원 여부

|구분|지원 여부|비고|
|:---|:---:|:---|
|typescript| O | @types/swagger-ui-express|

---

## 추가 모듈

### swagger-jsdoc

swagger-ui-express와 연동해서 사용하는 api

|구분|url|
|---|---|
| npm | <https://www.npmjs.com/package/swagger-jsdoc> |
| homepage | <https://github.com/Surnet/swagger-jsdoc> |
| Repository | <https://github.com/Surnet/swagger-jsdoc> |

---

### swagger-jsdoc - typescript 지원 여부

|구분|지원 여부|비고|
|:---|:---:|:---|
|typescript| O | @types/swagger-jsdoc|

---

## 추가 설명

rest api를 사용하면 유용하다.  
별도의 테스트 툴이 필요 없고 바로 웹에서 rest api를 사용해 볼 수 있다.  
따로 문서화 할 필요도 없어진다.  

swagger 사용 편의성을 위해 여러 추가 모듈이 있지만 swagger-jsdoc를 사용하였다.  
swagger-jsdoc 모듈도 typescript를 지원 한다.  
아래 설명할 내용은 swagger-ui-express, swagger-jsdoc를 사용하는걸 기준으로 설명한다.

---

## 사용법

### javascript

모듈 설치

``` bash
npm install -S swagger-ui-express swagger-jsdoc
```

코드 작성

``` javascript
var express = require('express');
var swaggerUi = require('swagger-ui-express');
var swaggerJSDoc = require('swagger-jsdoc');

const swaggerDefinition = {
  info: {
    title: 'test',
    version: '1.0.0',
    description: '테스트 api'
  },
  host: 'localhost:4000',
  basePath: '/',
}

const opetions = {
  swaggerDefinition: swaggerDefinition,
  apis: [
    'app.js',           // 특정 파일의 JsDoc를 읽을 경우
    './src/**/*.js',    // 특정 폴더에 파일들의 JsDoc를 읽을 경우
    './YAML/**/*.yaml'  // 특정 폴더에 yaml 파일을 읽을 경우
  ],
}

const swaggerSpec = swaggerJSDoc(opetions);

var app = express();
app.use(express.urlencoded({extended: true}))
app.use(express.json());
app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerSpec));
/**
 *  @swagger
 *  paths:
 *    /:
 *      get:
 *        summary: 'main'
 *        description: ''
 *        consumes:
 *        - "application/json"
 *        produces:
 *        - "application/json"
 *        responses:
 *          '200':
 *            description: '정상'
 */
app.get('/', (req, res) => {
  res.send("hello world");
})

app.listen(4000, () => console.log(`Server app listening on port 4000`));
```

### typescript

모듈 설치

``` bash
npm install -S swagger-ui-express swagger-jsdoc
npm install -D @types/swagger-ui-express @types/swagger-jsdoc
```

코드 작성

``` typescript
import express from 'express';
import swaggerUi from 'swagger-ui-express';
import swaggerJSDoc from 'swagger-jsdoc';

const swaggerDefinition = {
  info: {
    title: 'test',
    version: '1.0.0',
    description: '테스트 api'
  },
  host: 'localhost:4000',
  basePath: '/',
}

const opetions = {
  swaggerDefinition: swaggerDefinition,
  apis: [
    'app.ts',           // 특정 파일의 JsDoc를 읽을 경우
    './src/**/*.ts',    // 특정 폴더에 파일들의 JsDoc를 읽을 경우
    './YAML/**/*.yaml'  // 특정 폴더에 yaml 파일을 읽을 경우
  ],
}

const swaggerSpec = swaggerJSDoc(opetions);

var app = express();
app.use(express.urlencoded({extended: true}))
app.use(express.json());
app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerSpec));
/**
 *  @swagger
 *  paths:
 *    /:
 *      get:
 *        summary: 'main'
 *        description: ''
 *        consumes:
 *        - "application/json"
 *        produces:
 *        - "application/json"
 *        responses:
 *          '200':
 *            description: '정상'
 */
app.get('/', (req, res) => {
  res.send("hello world");
})

app.listen(4000, () => console.log(`Server app listening on port 4000`));
```

### 코드에 관한 설명

일단 swagger 가 어떤것인지 이해가 필요하다.  
기본 지식은 [여기](../../swagger/index.md)서 확인  

코드에서  
swaggerDefinition 변수에는 기본 swagger 정보를 세팅 한다.  

opetions 변수는 swagger-jsdoc 모듈에 세팅하는 값이다.  
opetions에 swaggerDefinition는 위의 swaggerDefinition 변수를 넣으면 된다.  
opetions에 apis에는 swagger코드를 읽어오기 위한 경로나 파일을 지정한다.  

위에서 설정한 옵션은 swaggerSpec 으로 만든다.

express 세팅에 아래와 같이 코드를 추가 한다.

``` javascript
app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerSpec));
```

express 서버를 띄우고 도메인/api-docs로 접속 하면 swagger UI 가 나온다.

코드에 jsDoc로 tag, paths, definitions을 작성하면  
자동으로 파싱해서 swagger UI에 만들어 표시해 준다.  
하지만 코드에는 paths만 작성하고  
tag, definitions는 별도의 파일로 관리하는걸 추천한다.  

jsDoc로 swagger 코드 작성은 아래와 같다.  

``` javascript
/**
 *  @swagger <- 이것을 맨 처음 써줘야 한다.
 *  (swagger-JsDoc가 인식을 하기 위해서..)
 *  아래 부터는 YAML 형식으로 코드 작성을 하면 된다.
 *  paths:
 *    ... 코드 생략
 */
```
