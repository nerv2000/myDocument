# npm 관련

목록

[명령어 정리](#명령어-정리)  
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

## module 정리

* [app-root-path](./modules/app-root-path.md) - app root path를 고정으로 사용
* [jest](./modules/jest.md) - JavaScript Testing
* [module-alias](./modules/module-alias.md) - module 파일 경로 별칭 해주는 모듈
* [rimraf](./modules/rimraf.md) - 파일 삭제 모듈
* [supertest](./modules/supertest.md) - url 통신 모듈
* [swagger-ui-express](./modules/swagger-ui-express) - swagger ui 생성 모듈

---
