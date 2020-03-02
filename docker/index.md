# docker 관련

목차

[기본적으로 알아야 할것들](#기본적으로-알아야-할것들)  
[node.js 웹 앱의 도커라이징](#node.js-웹-앱의-도커라이징)  

---

## 기본적으로 알아야 할것들

docker를 전반적으로 파악 할려면 [여기](http://pyrasis.com/private/2014/11/30/publish-docker-for-the-really-impatient-book)로..

1. image 만들기  
**Dockerfile** 파일에 스크립트를 작성하여야 함.  
(Dockerfile 기본 작성 방법은 [여기](http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter04/02) 참조)  
**.dockerignore** 파일에는 복사 할때 제외할 목록 추가 가능  
(git의 .gitignore와 사용법이 비슷함)  
코드 작성이 완료되면 아래와 같이 build 하면 됨

    ``` bash
    #명령어 사용법
    docker build [OPTIONS] PATH | URL | -

    #예시
    docker -t <name>:<tag> <image name> .
    ```

    옵션 설명  
    -t, --tag : image 이름 지정  
    뒤에 tag는 생략가능 (기본 latest)  

2. image 실행  
image를 실행 하면 container가 생성됨

    ``` bash
    #명령어 사용법
    docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

    #예시1 - 백그라운드 실행
    docker run --name <별칭> -p <host port>:<container port> -d <image name>

    #예시2 - 컨테이너 내부 bash 접속 실행
    docker run -i -t <image name> /bin/bash
    ```

    옵션 설명 (자세한건 [여기](http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter20/28))  
    **--name** : container 이름 지정 (안하면 랜덤으로 지정됨)  
    **-p, --publish-all** : container port를 host에 연결  
    **-d, --detach** : container를 백그라운드로 실행  
    **-i, --interactive** : 표준 입력(stdin)을 활성화하며 컨테이너와 연결(attach)되어 있지 않더라도 표준 입력을 유지합니다.  
    보통 이 옵션을 사용하여 Bash에 명령을 입력합니다.  
    **-t, --tty** : TTY 모드(pseudo-TTY)를 사용합니다. Bash를 사용하려면 이 옵션을 설정해야 합니다.  
    이 옵션을 설정하지 않으면 명령을 입력할 수는 있지만 셸이 표시되지 않습니다.  

3. docker log 확인

    ``` bash
    #명령어 사용법
    docker logs [OPTIONS] CONTAINER

    #예시
    docker logs <continer id or name>
    ```

4. 실행되어 있는 container 직접 접속  
container가 실행되어 있어야 사용할 수 있다.

    ``` bash
    #명령어 사용법
    docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

    #예시
    docker exec -i -t <container id or name> /bin/bash
    ```

    **-i, --interactive** : 표준 입력(stdin)을 활성화하며 컨테이너와 연결(attach)되어 있지 않더라도 표준 입력을 유지합니다.  
    보통 이 옵션을 사용하여 Bash에 명령을 입력합니다.  
    **-t, --tty** : TTY 모드(pseudo-TTY)를 사용합니다. Bash를 사용하려면 이 옵션을 설정해야 합니다.  
    이 옵션을 설정하지 않으면 명령을 입력할 수는 있지만 셸이 표시되지 않습니다.  

---

## node.js 웹 앱의 도커라이징

기본적인 방법은 [여기](https://nodejs.org/ko/docs/guides/nodejs-docker-webapp/) 참조

위 링크에 있는 방법을 요약 하면

1. nodejs 코드작성
2. docker image 생성
3. docker container 실행

으로 요약 됨
