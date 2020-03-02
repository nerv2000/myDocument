# module-alias

접근 경로를 줄여준다.

|구분|url|
|---|---|
| npm | <https://www.npmjs.com/package/module-alias> |
| homepage | <https://github.com/ilearnio/module-alias> |
| Repository | <https://github.com/ilearnio/module-alias> |

---

## typescript 지원 여부

|구분|지원 여부|비고|
|:---|:---:|:---|
|typescript| O | @types/module-alias|

---

## 추가 설명

예를 들어 아래와 같이 경로를 사용한다면

``` javascript
require('../../../../some/very/deep/module')
```

아래와 같이 변경 가능

``` javascript
require('@deep/module')
```

>이것을 사용 하게 되면 다른 모듈(?)을 사용할때 문제가 발생한다.  
예를 들면 typescript, jest, webpack 경우 줄어든 경로에 대해서 알지 못하는 문제가 발생한다.  
위에 언급한것들은 비슷한 기능이 있으니 세팅 해주면 된다.  
[공홈](https://github.com/ilearnio/module-alias)에 가보면 jest, webpack에 대한 언급이 있으니 참고 할것.  

---

## 사용법

일단 package.json에 경로 세팅 해야함.  
([공홈](https://github.com/ilearnio/module-alias)에 나와있는 걸 봐선 파일도 지정 가능 한듯.. 하지만 써보진 않았다.)

### package.json 설정

``` json
{
  "_moduleAliases": {
    "@deep" : "src/some/very/deep"
  }
}
```

### javascript

모듈 설치

``` bash
npm i -S module-alias
```

코드 작성  
자세한건 [여기](https://github.com/ilearnio/module-alias)로 가서 **Advanced usage** 참조

``` javascript
const moduleAlias = require('module-alias');
modualeAlias();
```

---

### typescript

모듈 설치

``` bash
npm i -S module-alias
npm i -D @types/module-alias
```

코드 작성

``` typescript
import 'module-alias/register';
```
