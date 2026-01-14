# git START

## 명령줄에서 새 저장소 만들기
``` bash
  echo "# terms" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git branch -M main
  git remote add origin https://github.com/[주소]/[폴더명].git
  git push -u origin main
```

## 명령줄에서 기존 저장소를 푸시
``` bash
  git remote add origin https://github.com/[주소]/[폴더명].git
  git branch -M main
  git push -u origin main
```

## SSH 사용법
### SSH 키 생성
  - window 기준 : C:\Users\당신의_사용자_이름\.ssh
  - 없으면 Git Bash, PowerShell 에서 `ssh-keygen` 명령어실행
  - 키생성 
    + t ed25519 → 최신 암호화 방식 (권장)     
    + C → 키에 대한 주석 (이메일 등)   
    `ssh-keygen -t ed25519 -C "your_email@example.com"`  
  - 아래처럼 나옴 성공 
    ``` bash
    Generating public/private ed25519 key pair.
    Enter file in which to save the key (/c/Users/사용자이름/.ssh/id_ed25519):
    ```
    + 그냥 Enter 키 누르세요, passphrase(암호)도 처음엔 비워두고 Enter 누르셔도 됩니다.
    + 완료되면 아래처럼 나옴
    ``` bash
    C:\Users\<사용자이름>\.ssh\id_ed25519        ← 개인키
    C:\Users\<사용자이름>\.ssh\id_ed25519.pub    ← 공개키
    ```
  - SSH 에이전트 등록
    + 다음입력
    ``` bash
    eval "$(ssh-agent -s)"
    ```
    + 결과 
    ``` bash
    Agent pid 1234
    ```
    + 키를 에이전트에 추가
    ``` bash
    ssh-add ~/.ssh/id_ed25519
    ```
### github 에 SSH 키등록    
  - 공개키내용확인
  ``` bash
  cat ~/.ssh/id_ed25519.pub
  ```
  - github 접속
  - 오른쪽 상단 프로필 > Settings > SSH and GPG keys 이동
  - New SSH key 클릭
  - Title: "My Windows PC" 등
  - Key: 위에서 복사한 공개키 내용 붙여넣기
  - Save
  
### SSH 연결 테스트  
  - SSH 키를 사용하여 GitHub에 제대로 연결되는지 확인
    ``` bash
    ssh -T git@github.com
    ```
    ``` bash
    This key is not known by any other names
    Are you sure you want to continue connecting (yes/no/[fingerprint])?
    ```
    + yes 
    ``` bash
    Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
    Hi CrossHitters! You've successfully authenticated, but GitHub does not provide shell access.
    ```
  - 완료!

## git 협업자 추가
  - Settings > Access > Collaborators and teams 
  - Manage access : 협업자 추가
  - 협업자가 메일에서 승인
    