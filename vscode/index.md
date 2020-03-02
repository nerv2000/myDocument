# vscode 관련

vscode랑 관련 있는 내용 정리

vscode 설치파일 [다운로드](https://code.visualstudio.com)

목차

[확장 기능](#확장-기능)  
[설정 관련](#설정-관련)  
[vscode에서 typescript 사용법](#vscode에서-typescript-사용법)  

---

## 확장 기능

### 기본 추천

* [Active File In statusBar](https://marketplace.visualstudio.com/items?itemName=RoscoP.ActiveFileInStatusBar)  
  아래 하단에 현재 작업중인 파일의 전체 경로 표시  
* [Korean Language Pack for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko)  
  vscode 한글화  
* [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)  
  vscode에 설치된 확장기능 설정등을 github에 동기화 해줌  
  여러곳에서 vscode 작업을 한다면 하나의 세팅을 유지 해줌  
* [Visual Studio Keymap](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vs-keybindings)  
  visual stuido 키 세팅을 거의 동일하게 사용하게 해줌  
  (visual stuido 단축키에 익숙한 분이라면 강력 추천)  
* [vscode-icons](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons)  
  vscode 안에 탐색기 아이콘을 바꿔줌  
  (일단 깔면 이뻐진다...)  

### 사용하면 유용한 기능  

* [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)  
git의 log를 이쁘게 볼수 있다.  
* [JSON5 syntax](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-json5)  
JSON5를 쓴다면 필수...  
* [Rainbow Brackets](https://marketplace.visualstudio.com/items?itemName=2gua.rainbow-brackets)  
코드의 괄호 표시를 색으로 표현 (짝을 맞춰준다.)  
* [Trailing Spaces](https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces)  
코드 작성시 뒷쪽의 공백을 빨간색으로 표시 해줌...  
* [Shell launcher](https://marketplace.visualstudio.com/items?itemName=Tyriar.shell-launcher)  
shell을 여러개 사용한다면 (cmd, git bash, node 등등등..)  
좀더 편하게 shell을 실행 할 수 있도록 해줌  

### markdown 관련

* [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)  
markdown 문서 작성시 잘못된 사용법에 대해 알려줌  
(markdown 문서를 작성한다면 필수..)  

### swagger 관련

* [OpenAPI (Swagger) Editor](https://marketplace.visualstudio.com/items?itemName=42Crunch.vscode-openapi)  
swagger 설정을 작성하는데 도움을 줌...  
(하지만 좋은 느낌은 아니였다. 그러나 visual 한건 이것밖에...)  
* [openapi-lint](https://marketplace.visualstudio.com/items?itemName=mermade.openapi-lint)  
swagger 설정 작성시 작성을 편하게 해주는 intellisense  
* [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)  
swagger 설정은 json, YAML 작성 가능하지만  
YAML이 좀 더 보기 좋아서 자동으로 추천 해서 설치..  

---

## 설정 관련

vscode의 기능 설정은 별도의 settings.json으로 저장됨  
만약 작업하는 폴더에만 설정 하고 싶다면 .vscode 폴더에  
settings.json을 만들어서 설정 하면 됨  

* 문서의 저장시 뒷쪽 공백 자동 제거 방법 (아래 json 참조)  
파일의 종류 별로 세팅도 가능 (아래는 markdown 파일은 제외한것)  
(폴더나 특정파일명으로 하는건 모르겠음)  

  ``` json
  {
    "files.trimTrailingWhitespace": true
    "[markdown]": {
          "files.trimTrailingWhitespace": false
    }
  }
  ```

---

## vscode에서 typescript 사용법

[이쪽으로](./typescriptSetting.md)
