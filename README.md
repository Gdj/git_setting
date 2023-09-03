# GIT 설치 & 사용법
----
  - [Git 설치 세팅](#_git_설치_세팅) 
  - [저장소 만들기](#_저장소_만들기) 
    + [깃허브 저장소 만들기](#_깃허브_저장소_만들기) 
    + [로컬 저장소 만들기](#_로컬_저장소_만들기) 
  - [깃 기본작업](#_깃_기본작업) 
  - [branch](#_branch) 
    + [가지치기 (branch) 기본기능](#_가지치기_(branch)_기본기능) 


## Git 계정 확인및 병경
- `git config --global` 로하면 전역 으로 확인 변경할 수 있다.
- 유저이름 확인
    `git config user.name`
- 유저이름 변경
    `git config user.name "변경할 유저 네임"`
- 계정 이메일 확인
    `git config user.email`
- 계정 이메일 변경
    `git config user.email "변경하고자하는 깃헙 이메일 주소"`    
- 계정 정오
  `git config --list`

- ssh agent에 등록
  `ssh-add 파일명` or `ssh-add ~/.ssh` 다른디렉토리에서 접근하여 실행
  `Could not open a connection to your authentication agent.` 메시지가 뜨면
  `eval $(ssh-agent)` 실행후 재시도
- ssh agent 등록 확인
  `ssh-add -l`
- github 사이트 이동 > 로그인후 우측상단 내아이콘 클릭 > settings > 왼쪽메뉴 > SSH and GPG keys > .pub 파일 내용을 "key" 영역에 붙여넣기
  


## Git 설치 세팅
1. OS버젼에 맞게 설치 : [git download](https://git-scm.com/downloads)
2. 사용자정보 등록
	- 프로젝트 홀더에서 "--global"을 빼면 프로젝트마다 설정 할수있다. 
    ```
	git config --global user.name '이름'
	git config --global user.email '메일주소@example.com'
    ```
    
	- 편집기 연결 (에디터플러스)
    ```
	git config --global core.editor "'C:/Program Files/EditPlus/editplus.exe' -multiInst -nosession"
    ```
    
	- 설정 확인 : 축약 `git config -l`
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

### 깃허브 저장소 만들기
  #### 1. 깃허브 로그인후 : 우측상단 "+" 클릭 > repository
  #### 2. `Repository name` : 저장소 이름생성 
  `Description`     : 저장소 설명
  `Public` or `Private` : 공개 여부 (호스팅 할경우 Public 으로해함)
  `Add a README file` : 리드미 파일 생성여부
  `Add .gitignore`    : 저장소에 동기화 되지 않을 파일, 패턴등록
  `Choose a license`  : 라이센스 등록  
  > `GNU General Public License(GPL) 2.0` 
    - 소프트웨어를 배포하는 경우 저작권 표시, 보증책임이 없다는 표시 및 GPL에 의해 배포된다는 사실 명시
    - 소프트웨어를 수정하거나 새로운 소프트웨어를 병합(Dynamic linking 포함)시키는 경우 GPL에 의해 소스 코드 제공
    - GPL 소프트웨어를 배포하는 경우, 소스 코드 그 자체를 함께 배포하거나 또는 소스코드를 제공받을 수 있는 방법에     대한 정보를 함께 제공

  > `MIT License` 
    - 라이센스와 저작권 관련 명시만 지켜주면 되는 라이센스이다.
    - 이 소프트웨어를 누구라도 무상으로 제한없이 취급해도 좋다.
    - 저자 또는 저작권자는 소프트웨어에 관해서 아무런 책임을 지지 않는다.
    
  #### 3. `Create repository` 완료~
  ``` bash
    git init
    git add README.md
    git commit -m "커밋 내용"
    git branch -M main
    git remote add origin <저장소 주소>
    git push -u origin main
  ```
#### 깃허브 호스팅 (github page)
  - 프로젝트 텝메뉴 에서: `Settings` 
  - 왼쪽메뉴 : pages > Branch > None | main (서비스할 브런치 선택) > save
  - 반영 시간이 필요함 진행 상황 보기 에서 확인할 수 있음.
  - 진행 상황 보기 : 프로젝트 텝메뉴에서 `Actions` > pages build and deployment


#### 깃허브 공유 받기
  - 프로젝트 텝메뉴 에서: `Settings` 
  - 왼쪽메뉴 : `Collaborators` > Manage access : `Add people` 버튼 > 깃허브 가입 메일 주소
  - 공유 받은 사람은 메일에서 초대장에 승인 해야함. "View invitation"

    
### 로컬 저장소 만들기
  #### 로컬 디렉토리 저장소 만들어 원격저장소에 올리기
  ``` bash
  git init        
  git add --all (git add .)	
  git commit -m "커밋 내용"
  git remote add origin <저장소 주소>
  git push -u origin main
  ```
  - add 목록 보기 : `git status` 

  #### 기존 원격 저장소 clone하기
  - 저장소이름과 동일하게 클론하기
    ``` bash
    git clone '원격저장소 주소'
    ```
  - 새로운 이름에 폴더에 클론하기
    ``` bash
    git clone '원격저장소 주소' './폴더명'`
    ```
  - 특정 브런치만 새로운 폴더로 클론하기
    ``` bash
    git clone -b '브런치이름' --single-branch '원격저장소 주소'
    ```
  - 특정폴더만 클론
    a. 저장소 초기 화 :   `git init`
    b. Git 저장소 주소 추가 : `git remote add origin '원격저장소 주소'`
    c. git sparse Checkout  활성화 하도록 config 수정 : 
      `git config core.sparsecheckout true` 
    d. clone 할 폴더이름(원격저장소 이후경로)에 하위더까지 명시 
      `echo '폴더경로'/* >> ./.git/info/sparse-checkout`
    e. "프랜치명"으로 pull해서 가져오기.
      `git pull origin main`


  - mac
    ``` bash
    sudo xcodebuild -license
    sudo git clone '원격저장소 주소'
    ```
      
  #### 기존 원격 저장소 계정으로 clone하기
  ``` bash
  git clone --recursive '계정메일주소:원격저장소 주소'
  ```
    

## 깃 기본작업

### 원격 저장소에서 받아오기 
  #### 1. 다른 작업자가 올린 작업파일 받기
    ``` bash
    git pull
    ```
  #### 2. master 브런치 받기 (git pull 저장소 브런치)
    ``` bash
    git pull origin master
    ```

### 파일 추가 & 변경 원격 저장소 올리기
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
    


## branch
### 가지치기 (branch) 기본기능
  #### 0. 가지 업데이트 
  - 원격 프랜치 정보 업데이트
  ``` bssh
  git remote update
  ```

  #### 1. 가지 만들기
  ``` bash
  git branch '가지이름'
  ```

  #### 2. 가지 이동
  ``` bash
  git checkout '가지이름'
  ```

  #### 3. 1,2 가지만들고 이동 동시에
  ``` bash
  git checkout -b '가지이름'
  ```

  #### 4. 현재 가지 확인
  ``` bash
  git branch
  ```

  #### 5. 모든 브랜치 / 가지이름 / 그래프로 / 간결하게 확인
  ``` bash
  git log --branches --decorate --graph --oneline
  q
  ```

  #### 6. GUI Tool로 보기 (소스트리 설치후)
  ``` bash
  stree
  ```

  #### 7. main가지와 다른가지의 차이 비교
  - master는 없고 다른 가지에 있는거비교
    ``` bash
    git log master..'가지이름'
    ```
    
  - 소스코드 확인 비교
    ``` bash
    git log -p master..'가지이름'
    ```
  
  - 프랜치의 현재 상태 비교
    ``` bash
    git diff master..'가지이름'
    ```

  - 프랜지의 파일 상태 비교
    ``` bash
    git diff --name-status branch1..branch2
    ```

  - 프랜지의 특정파일 비교
    ``` bash
    git diff branch1:file.txt branch2:file.txt
    ```

  #### 8. 가지 삭제
  - 가지 삭제 (머지되면 그냥 지워진다)
    ``` bash
    git branch -d '가지이름'
    ``` 
  - 가지 강제 삭제 (머지되지 않아도 그냥 지워진다.)
    ``` bash
    git branch -D '가지이름'
    ```

### 가지 합치기 (merge)
  #### 1. main로 가지 병합하기
  - 마스터로 이동후 변경된 가지를 병합
    ``` bast
    git checkout master 
    git merge '가지이름'
    ```



### 가지 되돌리기 (rest) 프랜치에 commit 이동
#### option 
    - hard : 돌아가려는 이력이후의 모든 내용을 지워 버립니다. 
    - soft : 돌아가려 했던 이력으로 되돌아 갔지만, 이후의 내용이 지워지지 않안음.
    - mixed : (기본값) 이력은 되돌려집니다. 이후에 변경된 내용에 대해서는 남아있지만, 인덱스는 초기화 됩니다.
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
    
### 커밋 되돌리기 (checkout) 
1. commit id로 되돌리기 (HEAD는 "refs/heads/master"를 가르키지 않고 commit id로 변경된다.)
    ```
    git checkout 'commit id'
    ```
2. checkout 취소 master 프랜치 로 되돌아 가기
    ```
    git checkout master
    ```
    
  
### 파일되돌리기 되돌리기 (checkout) 
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
    
### 충돌 해결하기
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
    
    

  
### 버전관리 에서 제외하기 (Ignore) 
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

    
