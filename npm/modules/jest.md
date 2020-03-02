# jest

javascript Testing tool - 작성한 javascript 코드를 테스트 자동화 할 때 사용

|구분|url|
|---|---|
| npm | <https://www.npmjs.com/package/jest> |
| homepage | <https://jestjs.io/> |
| Repository | <https://github.com/facebook/jest> |

---

## typescript 지원 여부

|구분|지원 여부|비고|
|:---|:---:|:---|
|typescript| O | @types/jest|

---

## 사용법

### javascript 세팅

모듈 설치

``` bash
npm install -S jest
```

package.json에 jest 관련 내용 세팅

``` json
{
  ... 코드 생략
  "scripts": {
  "test": "jest --detectOpenHandles --forceExit"
  },
  "jest": {
    "testRegex": "\\.test\\.js$",
    "moduleFileExtensions": [
      "js"
    ]
  }
  ... 코드 생략
}
```

---

### typescript 세팅

모듈 설치

``` bash
npm install -S jest @types/jest ts-jest typescript
```

기본적으로 4개의 모듈 설치가 필요

1. **jest** : jest를 써야하니..  
2. **@types/jest** : typescript가 jest모듈을 인식해야 하니..  
3. **ts-jest** : typescript로 작성된 테스트 파일을 읽기 위해서..  
4. **typescript** : 글로벌로 설치하면 path를 지정 하면 될꺼 같은데 일단 ts-jset에 필요해서 설치

package.json에 jest 관련 내용 세팅

``` json
{
  ... 코드 생략
  "scripts": {
    "test": "jest --detectOpenHandles --forceExit"
  },
  "jest": {
    "transform": {
      "^.+\\.ts$": "ts-jest"
    },
    "testRegex": "\\.test\\.ts$",
    "moduleFileExtensions": [
      "ts",
      "js"
    ],
    "globals": {
      "ts-jest": {
        "diagnostics": true
      }
    }
  }
  ... 코드 생략
}
```

typescript로 작성된 테스트 파일은 ts-jest가 처리하기에  
추가로 설정을 해줘야 하는듯..  
(jset 세팅은 인터넷 검색해서 찾은건데 어디서 찾았는지는 기억이...)

---

### jest 실행

jest 실행은 **npm test**로 실행 할수 있음  
package.json에서 scripts -> test로 jset 실행내용  
packege.json에서 jest 부분은 jset 실행에 필요한 세팅  

테스트 코드는 아래와 같이 작성 하면 됨  
**파일명 - <파일명>.test.<사용언어확장자>**  
>예시  
javascript 일 경우 - temp.test.**js**  
typescript 일 경우 - temp.test.**ts**  

간단한 테스트 코드 샘플  
(js, ts는 문법 작성은 동일하다.)  

``` javascript
describe('main test', () => {
  test('test 1', (done) => {
    var val = 0;
    expect(val).toBe(0);
    done();
  });
});
```

작성후 실행 하면 아래와 같이 됨

``` bash
npm test

jest --detectOpenHandles --forceExit

PASS  ./temp.test.<js or ts>
  main test
    √ test 1 (3ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        1.562s
Ran all test suites.
```

### jset 경로 단축

module-alias에서도 언급 하였지만 module-alias를 사용한다면  
jest에도 동일한 세팅을 해줘야 한다.  
아래와 같이 package.json에 세팅한 jset 부분에 추가 해주면 된다.

``` json
  {
    ... 내용 생략
    "jest": {
      ... 내용생략
      "moduleNameMapper": {
        "@deep/(.*)" : "<rootDir>/src/some/very/deep/",
      }
    }
  }
```

module-alias에 설정한 내용데로 동일하게 세팅 해줌 됨
