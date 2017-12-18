# GIT 설치 & 사용법
----

## Git 설치 세팅
1. OS버젼에 맞게 설치 : [git download](https://git-scm.com/downloads)
2. 사용자정보 변경
	- "--global"을 빼면 프로젝트마다 설정 할수있다.
    ```
	git config --global user.name "이름"
	git config --global user.email 메일주소@example.com
    ```
    
	- 편집기 연결 (에디터플러스)
    ```
	git config --global core.editor "'C:/Program Files/EditPlus/editplus.exe' -multiInst -nosession"
    ```
    
	- 설정 확인
    ```
	git config --list
    ```

## 저장소 만들기
1. 로컬 디렉토리 저장소 만들어 원격저장소에 올리기
    ```
	git add *.*
	git add LICENSE
	git commit -m '커밋 내용'
	git remote add origin 원격저장소 주소
	git push -u origin master
	```

2. 1-2. 기존 원격 저장소 clone하기
    ```
	git clone 원격저장소 주소
    ```

## 파일 추가 & 변경 원격 저장소 올리기
1. 작업홀더 새로운파일, 수정파일 stage올리기
    ```
    git add add --all                        
    ```
    
2. stage올린 파일을commit한다 , -m 옆에는 메세지를 작성할수있다.
    ```
    git commit -m '커밋 내용'      
    ```

3. stage파일을 git에 서버에 master branch로 올린다.
    ```
    git push -u origin master   
    ```
    