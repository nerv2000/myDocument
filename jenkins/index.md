# Jenkins 관련

목차

[windows에서](#window에서)  
[mac에서](#mac에서)  
[공통](#공통)  

---

## window에서

나중에 업데이트 예정..

---

## mac에서

mac에서 설치 방법으로는 homebrew를 이용해서 설치  
(homebrew 설치는 [여기](https://brew.sh/index_ko) 참조)  

homebrew 설치후

``` bash
brew install jenkins
```

설치하다 보면 추가로 설치해야 할것을 친절하게 알려주니 그대로 하면됨.  
내 경우는 javasdk를 추가로 설치 하는것을 알려줬음

---

jenkins 설치후 기본 workspace는 아래와 같음

``` bash
/Users/<사용계정>/.jenkins/workspace
```

---

docker 자동화 할때 docker 실행파일을 못찾아서 경로 지정을 따로 해줬음.  
(해결 방법 : <https://stackoverflow.com/questions/40043004/docker-command-not-found-mac-mini-only-happens-in-jenkins-shell-step-but-wo/58688536#58688536>)

위 링크의 내용 요약하면

``` bash
/usr/local/Cellar/jenkins-lts/<설치된 버전>/homebrew.mxcl.jenkins-lts.plist
```

파일을 열여서 아래 내용을 추가하면 됨

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    ...
    코드생략
    ...
    <key>EnvironmentVariables</key>
    <dict>
      <key>PATH</key>
      <string>/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/Applications/Docker.app/Contents/Resources/bin/:/Users/Kh0a/Library/Group\ Containers/group.com.docker/Applications/Docker.app/Contents/Resources/bin</string>
    </dict>
  </dict>
</plist>
```

---

## 공통

sh 스크립트 실행(Excute shell) 방법

``` bash
sh <스크립트파일명>.sh
```

파일 경로는 절대경로로 지정 해주면 됨  
현재 작업 폴더 위치는 ${WORKSPACE}로 지정 할 수 있음

---
