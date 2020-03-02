# typescript 관련

목차

[tsc 빌드된 파일,폴더 삭제 방법](#tsc-빌드된-파일,폴더-삭제-방법)  
[path 요약 기능](#path-요약-기능)  

---

## tsc 빌드된 파일,폴더 삭제 방법

typescript로 build 하면 js 파일을 만들어주는데  
만약 typescript 작성한 파일을 삭제하거나 폴더를 바꾸게 되면 찌거기가 남게 된다.  

visual studio에 있는 정리 하는 기능이 있을거 같아서  
찾아보니 **tsc --build --clean** 옵션이 있긴 하다...  
하지만 생각하곤 다르게 동작 하였다.  

실재로 build되는 파일만 삭제 되는것을 확인하였다.  
폴더는 지워지지 않는다.  
또한 체크되지 않은 파일은 지워지지 않았다.  
구글에 찾아보니 build된 모든 파일, 폴더를 지워주는 기능은 기본으로 제공해 주지 않는거 같다.  

그래서 build된 파일, 폴더를 모두 삭제 할려면 직접해야 한다.  
일단 OS별로 파일 폴더 삭제 명령어가 다르기에 어디서든  
동일하게 삭제 하는 방법을 찾아야 했다.  
구글에 찾아보니 [rimraf](../npm/modules/rimraf.md) 모듈을 이용해서 삭제 하는게 가장 좋아보였다.  
npm으로 별로 설치를 해야하지만 뭐 그정도는 감수할수 있으니  
build된 파일을 삭제하는건 script 명령으로 만들어서 사용하니 모두 해결되었다.

---

## path 요약 기능

[module-alias](../npm/modules/module-alias.md) 모듈 처럼 경로를 요약해주는 기능을 쓰면  
typescript에서는 인식을 못하게 된다.  
하지만 그것과 동일한 기능을 tsconfig.json에 정의해서 이용 할수가 있었다.  
아래는 그것의 사용 방법이다.

tsconfig.json

``` json
{
  ... 코드 생략
  "baseUrl": "./",
  "paths": {
    "@deep/*": ["some/very/deep/*"]
  }
  ... 코드 생략
}
```
