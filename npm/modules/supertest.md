# supertest

url를 코드에서 호출시 사용

|구분|url|
|---|---|
| npm | <https://www.npmjs.com/package/supertest> |
| homepage | <https://github.com/visionmedia/supertest> |
| Repository | <https://github.com/visionmedia/supertest> |

---

## typescript 지원 여부

|구분|지원 여부|비고|
|:---|:---:|:---|
|typescript| O | @types/supertest|

---

## 추가 설명

rest api를 작성한 코드를 호출 하여 테스트 하기위해 사용한다.  
보통 코드 테스트는 jest를 사용 하기에 같이 연동해서 쓴다고 보면 될듯...  

---

## 사용법

### javascript

모듈 설치

``` bash
npm i -S supertest
```

코드 작성 - [공홈](https://github.com/visionmedia/supertest) Example 참조

``` javascript
const request = require('supertest');
const express = require('express');

const app = express();

app.get('/user', (req, res) => {
  res.status(200).json({ name: 'john' });
});

request(app)
  .get('/user')
  .expect('Content-Type', /json/)
  .expect('Content-Length', '15')
  .expect(200)
  .end(function(err, res) {
    if (err) throw err;
  });
```

### typescript

모듈설치

``` bash
npm i -S supertest @types/supertest
```

코드 작성

``` typescript
import request from 'supertest';
import express from 'express');

const app = express();

app.get('/user', (req, res) => {
  res.status(200).json({ name: 'john' });
});

request(app)
  .get('/user')
  .expect('Content-Type', /json/)
  .expect('Content-Length', '15')
  .expect(200)
  .end(function(err, res) {
    if (err) throw err;
  });
```
