# rimraf

파일을 삭제 한다. (The UNIX command rm -rf for node.)

|구분|url|
|---|---|
| npm | <https://www.npmjs.com/package/rimraf> |
| homepage | <https://github.com/isaacs/rimraf> |
| Repository | <https://github.com/isaacs/rimraf> |

---

## typescript 지원 여부

|구분|지원 여부|비고|
|:---|:---:|:---|
|typescript| O | @types/rimraf|

---

## 추가 설명

코드 내부에서 특정 폴더의 파일을 삭제 할 수 있지만...  
외부에서도 사용 가능하다.  

이것을 쓰는 이유는 OS가 다를때 동일한 명령으로  
파일 삭제를 할 수 있기 때문이다.  
typescript를 build 하면 js 파일을 만들어주는데  
파일명이 변경 되거나 폴더가 변경되면 찌꺼기가 남기에  
이것을 이용해서 build된 js 파일을 모두 삭제 한다.  
npm 설치시 global로 설치를 추천 한다.  

---

## 사용법

모듈 설치

``` bash
npm install -g rimraf
```

실행 방법

``` bash
rmiraf <삭제할폴더명>/
```
