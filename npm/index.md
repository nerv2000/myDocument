# npm 관련

목록

[명령어 정리](#명령어-정리)  
[모듈 외부 실행 파일 만들기](#모듈-외부-실행-파일-만들기)  
[module 정리](#module-정리)  

---

## 명령어 정리

### command 종류 (주로 사용하는것만...)

* **install** or **i** - module 설치 할때 사용
* **uninstall** or **un** - module 삭제 할때 사용
* **run-script** - package.json에 script에 정의된 명령 실행
* **list** or **ls** - 설치된 module 보기

### common option

* **--global** or **-g** - 전역에 module 설치
* **--save-prod** or **--save** or **-S** - 로컬에 module 설치  
(package.json에서 dependencies에 추가 됨)
* **--save-dev** or **-D** - 로컬에 dev module 설치  
(package.json에서 devDependencies에 추가 됨)
* **--depth=0** - list command 사용시 최상위에 있는 module만 보고 싶을때 사용..

---

## 모듈 외부 실행 파일 만들기

node가 설치 되어있는 상태에서 모듈을 command로 실행 할수 있다.

package.json에 아래와 같이 작성

``` json
{
  ... 코드 생략
  "bin": {
    "<실행할이름>": "<실행시불러올js파일>"
  }
  ... 코드 생략
}
```

실행할 코드 상단에 아래 코드 추가

``` bash
#!/usr/bin/env node
```

### 예시

코드는 아래와 같은 폴더 구성

``` bash
start # 최상단 폴더
|   app.js
|   package.json
|
\---bin # bin 폴더
        start.js
```

app.js 파일 - 코드 실행시 동작하는 파일

``` javascript
console.log('hello world');
```

start.js 외부에서 실행하는 파일 코드

``` javascript
#!/usr/bin/env node

require('./app');
```

package.json 파일

``` json
{
  ... 코드 생략
  "bin": {
    "start": "./bin/start.js"
  },
  ... 코드 생략
}
```

위와 같이 코드를 작성하였으면 global로 모듈을 설치 해야함.

``` bash
npm -g install start
```

설치가 완료되었으면 어디서든 실행 가능

``` bash
> start
hello world
```

참고로 javascript를 node로 실행하기에 node 설치는 무조껀 되어있어야 한다.

---

## module 정리

* [app-root-path](./modules/app-root-path.md) - app root path를 고정으로 사용
* [commander](./modules/commander.md) - cli 쉽게 만들어 주는 모듈
* [jest](./modules/jest.md) - JavaScript Testing
* [module-alias](./modules/module-alias.md) - module 파일 경로 별칭 해주는 모듈
* [rimraf](./modules/rimraf.md) - 파일 삭제 모듈
* [supertest](./modules/supertest.md) - url 통신 모듈
* [swagger-ui-express](./modules/swagger-ui-express) - swagger ui 생성 모듈

---
