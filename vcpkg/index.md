# vcpkg 사용법

c++로 코드 작성 할때 라이브러리를 command로 자동 설치 해주는 프로그램  
MS의 공식적인 설명은 [여기](https://docs.microsoft.com/ko-kr/cpp/build/vcpkg) 참조  

일단 장점은 라이브러리를 사용하는데 자동으로 해주니 편함  
업그레이드 역시 명령어를 통해 손쉽게 할 수 있음

## 설치 방법

1. GitHub에서 vcpkg 리포지토리(<https://github.com/Microsoft/vcpkg>)를 복제  
   나는 c:\vcpkg 폴더에 복제함  

2. bootstrap-vcpkg.bat(Windows) 파일을 실행해서 vcpkg.exe 생성  
   윈도우에서는 최소 vs2015 update3 설치되어있어야 함  
   리눅스나 mac은 ./bootstrap-vcpkg.sh 실행해서 생성  
   리눅스나 mac에는 추가로 설치되어있어야 하는건 뭐가 있어야 하는지는 안해봐서 잘 모르겠음.

## 사용방법

- vcpkg search pkgName - 설치가능한 라이브러리 찾기(pkgname 없음 전부 나옴)

- vcpkg install pkgName - 라이브러리 설치  
  기본적으로 32bit로 설치
  vcpkg install pkgName:x64-window 뒤에 써줘야 64bit 라이브러리로 설치됨

- vcpkg remove pkgName - 라이브러리 삭제

- vcpkg list - 설치된 라이브러리 표시

- vcpkg integrate install - 설치된 패키지 라이브러리 등록  
  (이것 까지 해야 정상적으로 라이브러리 이용가능)

- vcpkg integrate remove - 설치된 패키지 라이브러리 해제

## 참고 사항

- 라이브러리 설치시 문제가 발생하는건 메시지로 나오니 잘 읽고 따라해보면 됨

- 모든 라이브러리가 설치되는것은 아님 OS에 따라 설치 안되는 라이브러리도 있음  

- 설치시 기본으로 32bit로 설치됨 64bit나 static 으로 설치할려면 뒤에 옵션 더 붙쳐야함.  
  (x64-windows-static, x64-windows, x86-windows 이것 외에도 여러가지 옵션이 있으니 참고)
