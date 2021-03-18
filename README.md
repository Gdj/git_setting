# GIT 설치 & 사용법
----

## Git 설치 세팅
1. OS버젼에 맞게 설치 : [git download](https://git-scm.com/downloads)
2. 사용자정보 변경
	- 프로젝트 홀더에서 "--global"을 빼면 프로젝트마다 설정 할수있다. 
    ```
	git config --global user.name '이름'
	git config --global user.email '메일주소@example.com'
    ```
    
	- 편집기 연결 (에디터플러스)
    ```
	git config --global core.editor "'C:/Program Files/EditPlus/editplus.exe' -multiInst -nosession"
    ```
    
	- 설정 확인
    ```
	git config --list
    ```
    
    - git commit 상태확인
    ```
    git log
    ```

    - git commit 변경 상세 확인
    ```
    git log -p
    ```
      
    
    - 원격 저장소 확인
    ```
    git remote -v 
    ```
    
    
    
## 저장소 만들기
1. 로컬 디렉토리 저장소 만들어 원격저장소에 올리기
    
    ```
    git init        
	git add --all (git add .)	
	git commit -m "커밋 내용"
	git remote add origin '원격저장소 주소'
	git push -u origin master
	```


2. 기존 원격 저장소 clone하기
    
    ```
	git clone '원격저장소 주소'
    ```
    
    - mac
    ```
    sudo xcodebuild -license
    sudo git clone '원격저장소 주소'
    ```
    
3. 기존 원격 저장소 계정으로 clone하기
    ```
    git clone --recursive '계정메일주소:원격저장소 주소'
    ```
    
## 원격 저장소에서 받아오기 
1. 다른 작업자가 올린 작업파일 받기
    ```
    git pull
    ```
2. master 브런치 받기 (git pull 저장소 브런치)
    ```
    git pull origin master
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
    
3. 1,2 번동작 한번에 하기 (새로만든 파일은 커밋 되지 않는다)
    ```
    git commit -am "커밋 내용"
    ```

4. stage파일을 git에 서버에 (origin 원격저장소)  master branch로 올린다.  
    - `-u`옵션을 사용하면 최초 한번만 (저장소명, 브랜치명)을 넘기고 이후는 `git push` 하면 동일 저장소, 브랜치명으로 push 된다.
    ```
    git push -u origin master   
    ```
    


## 가지치기 (branch) 기본 브랜치는 master
1. 가지 만들기
    ```
    git branch '가지이름'
    ```
2. 가지 이동
    ```
    git checkout '가지이름'
    ```
3. 1,2 가지만들고 이동 동시에
    ```
    git checkout -b '가지이름'
    ```

4. 현재 가지 확인
    ```
    git branch
    ```
5. 모든 브랜치 / 가지이름 / 그래프로 / 간결하게 확인
    ```
    git log --branches --decorate --graph --oneline
    q
    ```
6. GUI Tool로 보기 (소스트리 설치후)
    ```
    stree
    ```
    
7. master가지와 다른가지의 차이 비교
    - master는 없고 다른 가지에 있는거비교
    ```
    git log master..'가지이름'
    ```
    
    - 소스코드 확인 비교
    ```
    git log -p master..'가지이름'
    ```
    
    - 프랜치의 현재 상태 비교
    ```
    git diff master..'가지이름'
    ```

    -- 프랜지의 파일 상태 비교
    ```
    git diff --name-status branch1..branch2
    ```

    -- 프랜지의 특정파일 비교
    ```
    git diff branch1:file.txt branch2:file.txt
    ```

7. 가지 삭제
    - 가지 삭제 (머지되면 그냥 지워진다)
    ```
    git branch -d '가지이름'
    ```
    - 가지 강제 삭제 (머지되지 않아도 그냥 지워진다.)
    ```
    git branch -D '가지이름'
    ```

## 가지 합치기 (merge)
1. master로 가지 병합하기
    - 마스터로 이동후 변경된 가지를 병합
    ```
    git checkout master 
    git merge '가지이름'
    ```

## 가지 되돌리기 (rest) 프랜치에 commit 이동
1. commit id로 되돌리기
    ```
    git reset --hard 'commit id'
    ```
2. reset 취소
    ```
    git reset --hard ORIG_HEAD
    ```
3. 로그 보기
    ```
    git reflog 
    ```
4. 로그 보고 되돌리기
    ```
    git reset 'id값'
    ```
    
## 커밋 되돌리기 (checkout) 
1. commit id로 되돌리기 (HEAD는 "refs/heads/master"를 가르키지 않고 commit id로 변경된다.)
    ```
    git checkout 'commit id'
    ```
2. checkout 취소 master 프랜치 로 되돌아 가기
    ```
    git checkout master
    ```
    
  
## 파일되돌리기 되돌리기 (checkout) 
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
    
## 충돌 해결하기
1. 합치기 
    ```
    git merge '가지 이름'
    ```
2. 충돌 내용 보기
    ```
    git status
    ```

3. 출돌 소스 열어서 확인
    ```
    <<<<<<< HEAD
    마스터계정 소스코드
    =======
    적용하려는 가지 소스코드
    <<<<<<< '가지이름'
    ```
4. 직접 수정하여 다시 올린다.
    ```
    git add '수정파일'
    git common 
    ```
    
    

  
## 버전관리 에서 제외하기 (Ignore) 
1. .git있는 디렉토리 (최상위 폴더)에 가서 ".gitignore" 파일을 만든다.
    ```
    fsutil file createnew .gitignore 1    
    ```

2. 특정 확장자 제외하기, 홀더 제외하기 파일에 아래내용 적용.
    ```
    *.bak
    node_modules/
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

    
