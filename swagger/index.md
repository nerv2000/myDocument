# swagger 관련

## swagger 코드 작성

아래 코드는 swagger [공홈](https://editor.swagger.io/)에서 샘플을 요약한 내용이다.  
코드 작성은 json, YAML로 보통 하는데 YAML이 좀더 보기 좋아 YAML 샘플로 설명하겠다.  
그리고 아래 코드는 swagger : 2.0 기반으로 설명 한다.  
(공홈에 샘플이 swagger 2.0 기반이라..)  
swagger 외에도 openapi로도 작성 할수 있는데.. 문법(?)이 조금씩 다르고 기능도 조금씩 다르다.

크게 카테고리를 보면 아래와 같다.

``` YAML
swagger:
info:
host:
basePath:
schemes:
tags:
paths:
definitions:
securityDefinitions:
externalDocs:
```

각 카테고리를 간단 하게 설명하면 아래와 같다.  
(자세한 설명은 [공홈](https://swagger.io/docs/specification/2-0/basic-structure/) 참조)

* **swagger**  
swagger 인식하는 코드 버전에 대해서 정의  
openapi로 작성 한다면 openapi로 바꿔서 사용해야 한다.  

* **info**  
swagger UI의 기본 정보를 세팅한다.  

* **host**  
swagger가 url 테스트 할때 접속하는 domain 주소 입력 부분

* **basePath**  
web의 시작 path  
보통 rest api를 작성하면 제일 처음에 버전을 넣기에  
그런게 없다면 '/'로 보통 세팅한다.

* **tags**  
rest api를 그룹으로 묶을때 사용한다.

* **schemes**  
http, https 으로 접속에 관한 세팅을 하는듯

* **paths**  
rest api 정의

* **definitions**  
api에서 사용하는 데이터 구조체 정의

* **securityDefinitions**  
swagger ui 접속할때 계정을 사용하여 보안적인것을 정의  
(써보지 않아서 정확하겐 모르겠다.)

* **externalDocs**  
외부 문서를 정의 하는거 같은데 써보지 않았다.
