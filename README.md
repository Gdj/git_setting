# GIT 설치 & 사용법
----

## Git 설치 세팅
1. OS버젼에 맞게 설치 : [git download](https://git-scm.com/downloads)
2. 사용자정보 변경
	- 프로젝트 홀더에서 "--global"을 빼면 프로젝트마다 설정 할수있다. 
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
	git add --all 
	git add LICENSE
	git commit -m '커밋 내용'
	git remote add origin 원격저장소 주소
	git push -u origin master
	```


2. 기존 원격 저장소 clone하기
    ```
	git clone 원격저장소 주소
    ```
    
## 원격 저장소에서 받아오기 
1. 다른 작업자가 올린 작업파일 받기
    ```
    git pull
    ```

## 파일 추가 & 변경 원격 저장소 올리기
1. 작업홀더 새로운파일, 수정파일 stage올리기
    ```
    git add .                       
    ```
    
2. stage올린 파일을commit한다 , -m 옆에는 메세지를 작성할수있다.
    ```
    git commit -m "커밋 내용"      
    ```
    
3. 1,2 번동작 한번에 하기
    ```
    git commit -am "커밋 내용"
    ```

4. stage파일을 git에 서버에 (origin 원격저장소)  master branch로 올린다.
    ```
    git push -u origin master   
    ```
    
  
## 되돌리기
1. commit 이전으로 되돌리기 (stage 복구)
    ```
    git rest -- '파일이름'
    ```
    
2. add 이전으로 되돌리기(Working directory 복구) 
    ```
    git checkout -- '파일이름'
    ```
    
3. 1,2 한꺼번에 돌리 복구
    ```
    git checkout HEAD -- '파일이름'
    ```
    
  
## 버전관리 에서 제외하기 (Ignore) 
1. .git있는 디렉토리 (최상위 폴더)에 가서 ".gitignore" 파일을 만든다.

2. 특정 확장자 제외하기, 홀더 제외하기 파일에 아래내용 적용.
    ```
    *.bak
    /node_modules
    ```

3. ignore파일 직접 편집
    - ignore 패턴 사이트 참고 [itignore.io](https://www.gitignore.io)
    - glob programming 으로 제외 패던 만들기 [glob](https://en.wikipedia.org/wiki/Glob_(programming))

4. 이미올라간 파일 추가 시키기
    - .gitignore 에 "*.log"추가 하고
    - 제외 시키고 싶은 "*.log"파일 리스트 보기
    ```
    git rm --dry-run *.log
    ```
    - 버젼 컨트롤에서 제외하고 삭제
    ```
    git rm *.log
    ```
    - 버젼 컨트롤에서 제외하고 파일 남기기
    ```
    git rm --cached *.log
    ```

    
## 작업순서
1. pull -> work -> commit -> pull -> push 